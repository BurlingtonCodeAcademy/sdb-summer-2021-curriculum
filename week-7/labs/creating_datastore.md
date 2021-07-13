# Lab: Do it with JavaScript!

Let's make our first Mongo collection! 

**We will insert a *document* into a *collection* that lives in a *database*.**

Start by making new directory, and initializing it as an npm repository and installing the `mongodb` drivers. 

```
mkdir mongo_example
cd mongo_example
npm init -y
npm install mongodb
```

# Do it with JavaScript! cont.

Next, create a file called `mongoClient.js`

This is where we'll configure the *client*, or the *software* that connects to the server

The server, in this case, is `localhost:27017`

in `mongoClient.js`, add:

```javascript
const { MongoClient } = require("mongodb");
const uri = "mongodb://localhost:27017" //mongodb connects to port 27017 by default
const client = new MongoClient(uri)
```

# Do it with JavaScript! cont.

Now, *connect* to the database `library`, and insert a *document* into the `books` *collection*

Let's do this with an *asynchronous* function so we can harness the `await` keyword and keep things in order

like so:

```javascript
async function run() {

    await client.connect()
    const database = client.db('library')
    const collection = database.collection('books')
    await collection.insertOne({ title: "Eloquent Javascript", author: "Marijn Haverbeke" })
    await client.close()

}
run()
```
Note: This is a bare-bones example that does nothing for error handling. It is simply meant to demonstrate the most basic data flow.

<!-- The code above is meant to just run in the terminal as an example of how to connect to the database, we will eventually be using the code below in the "fetching data from the db" lab as an interface between our server and our database. Please remove this comment after editing  -->


# FactStore Walkthrough

The `FactStore` class acts as a repository for facts. It hides the details of connecting and talking to MongoDB from its callers, and exposes methods for adding and searching for facts in the database.

This class is used from both the web app and the command-line app.

# `client`

The `client()` method on FactStore...
 
 * opens a connection to the MongoDB server
 * saves that connection inside an instance variable
 * reuses the saved connection if possible 

> The MongoDB driver calls this connection object a *client*, but it's not a *browser*. The TIL web app is a client of Mongo even while it's a server to other clients. 

```javascript
  async client() {
    if (this.dbClient && this.dbClient.isConnected()) {
      return this.dbClient;
    } else {
      console.log(`Connecting to ${this.dbUrl}...`)
      this.dbClient = await MongoClient.connect(this.dbUrl, { useNewUrlParser: true })
      console.log("Connected to database.");
      return this.dbClient;
    }
  }
```

# closing time

`client.close()` will tell the driver "I'm done with the database for now"

It's good form to close your connection when you're not using it, to free up resources on both computers...

...but a web server will often keep the connection open between requests, so the next web request won't need to wait for the latency of opening a whole new connection.

You can think of `client()` as a one-member connection pool. It keeps the connection open as long as possible, but if it has closed in the meantime, it will create a new one.

# `collection`

The `collection()` method on FactStore...

 * acquires a connection to the MongoDB server
 * asks it for the *database* named `til`
 * then asks for the *collection* of TIL entries named `facts`

```javascript
  async collection() {
    const client = await this.client();
    const db = client.db(this.dbName);
    const collection = db.collection('facts');
    return collection;
  }
```
It is declared `async` (asynchronous) because the database connection might not currently be open, and the `client()` method might take some time to respond.

# `all`

The `all()` method on FactStore...

 * acquires the *collection*
 * asks it for a *cursor*
 
A cursor is like an iterator for databases. 

```javascript
  async all() {
    let collection = await this.collection()
    return collection.find({}).sort([['when', 1]]);
  }

```

If you know you've only got a few results, you can call `cursor.toArray()`, which fetches all the results up front, then puts them all into an array. But it's usually cleaner and safer to use the cursor itself.

# `find`

`collection.find` takes a parameter named `query` listing the *fields and values* to match on. 

For instance, `collection.find({author: 'alex')` returns all entries whose `author` field is the string `alex`

For more complicated queries, you can use operators like `$gte` (greater than or equal) and `$or`, e.g. this would find all items created on January 21, 2012:

```js
collection.find({
 when: {
    '$gte': new Date(2012, 0, 21),
    '$lt': new Date(2012, 0, 22)
 }
})
```

docs here: 
  * <http://mongodb.github.io/node-mongodb-native/3.1/api/Collection.html#find>
  * <https://docs.mongodb.com/manual/tutorial/query-documents/>

# `printAll`

remember, a cursor is an iterator -- an object that keeps track of a position in a collection,, and keeps returning the next item until it's done

`cursor.forEach` takes two parameters:

1. a function to call on each item
2. a function to call when done (which we're ignoring)

```javascript
  // Print all entries, in chronological order,
  // with a headline for each distinct date.
  async printAll() {
    let cursor = await this.all();
    let currentDay;
    await cursor.forEach((fact) => {
      let when = moment(fact.when);
      let startOfDay = when.format('YYYYMMDD');
      if (!currentDay || currentDay != startOfDay) {
        console.log(when.format('MMMM Do, YYYY'));
        currentDay = startOfDay;
      }
      let output = when.format('  hh:mm a - ') + fact.text;
      console.log(output);
      return currentDay;
    })

```

# `addFact`

This function 

1. retrieves the *collection* object
2. inserts a fact entry into it
3. returns the new id that Mongo chose, in case the calling code needs it

```javascript
  async addFact(text) {
    let entry = {
      when: new Date(),
      text: text
    };

    let collection = await this.collection()
    let result = await collection.insertOne(entry)
    assert.equal(1, result.insertedCount); // sanity check
    console.log('Inserted fact as id ' + result.insertedId)

    return {id: result.insertedId};
  }
```

# `_id`

Every time you insert a document into a MongoDB collection, Mongo adds a field named `_id` with a *unique* value.

This id is *not* a normal integer! It's a long string with a hex code inside it. 

Mongo has an algorithm for ensuring that this id is unique across *all other documents* in itself (and probably inside every other MongoDB database in the universe too).

In JavaScript, Mongo defines a *class* named `ObjectId` that encapsulates this string and provides useful methods; that's why in the output of `find` you see the JS code: 

```js
{ "_id" : ObjectId("5b5e27ba44c44608f97083f3"),
 "when" : ISODate("2018-07-29T20:46:50.749Z"), 
 "text" : "dogs like to bark" }
```