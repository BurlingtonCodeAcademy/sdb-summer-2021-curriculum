# Lab: Creating a DataStore

We will be creating a `class` that will handle all our database transactions to allow us to interact with a Mongo database more easily, efficiently, and consistently. 

We will be using it to set up a CLI tool that will allow us to **C**reate new documents, **R**ead, and **U**pdate existing documents, and **D**elete previously created entries to track books in a library.

Start by making new directory, and initializing it as an npm repository, and installing the `mongodb` drivers.

## Setting up the Connection

Create a file called `mongo-client.js`

This is where we'll configure the _client_, or the _software_ that connects to the server AKA our `DataStore`

The server, in this case, is `localhost:27017`

in `mongo-client.js`, add:

```javascript
const { MongoClient } = require("mongodb");
const uri = "mongodb://localhost:27017"; //mongodb connects to port 27017 by default
const client = new MongoClient(uri);
```
This is the 'boilerplate' for interacting with MongoDB.


## Test it Out

Now let's _connect_ to the database `library`, and insert a _document_ into the `books` _collection_

Let's do this with an _asynchronous_ function so we can harness the `await` keyword and keep things in order

```javascript
async function run() {
  await client.connect();
  const database = client.db("library");
  const collection = database.collection("books");
  await collection.insertOne({
    title: "Eloquent Javascript",
    author: "Marijn Haverbeke",
    copies: 1,
  });
  await client.close();
}
run();
```

Run this file through your terminal with `node mongo-client.js` to insert a single document into your Database.

_This function has no error handling. How would you flesh it out to prevent malformed documents from being inserted?_

## Building the DataStore

The `DataStore` class acts as a repository for your database. It hides the details of connecting and talking to MongoDB from its callers, and exposes methods for adding and searching for documents in a database.

This class will be able to be used from both a web app and a command-line app, so let's create a new file for it named `data-store.js`. We will need to bring in some mongo drivers for our `DataStore` to use.

```js
const { MongoClient, ObjectId } = require("mongodb");
```

## Setting up the Class

Let's set up the `DataStore` class. This class will need to keep track of where it's connecting, so let's set up a constructor we can use to assign the connection info:

- The connection URL
- The currently connected DB (if any)
- The DB name
- And the Collection name

```js
class DataStore {
  constructor(dbUrl, dbName, collName) {
    this.dbURL = dbUrl;
    this.dbName = dbName;
    this.collName = collName;
    this.dbClient = null;
  }
}
```

## DatsStore's`client` Method

The `client()` method on DataStore:

- opens a connection to the MongoDB server
- saves that connection inside an instance variable
- reuses the saved connection if possible

> The MongoDB driver calls this connection object a _client_, hence why we name this method `client`, but it's not a _browser_. Our server will be a client of Mongo even while it's a server to other clients.

```javascript
  async client() {

    console.log(`Connecting to ${this.dbUrl}...`)
    this.dbClient = await MongoClient.connect(this.dbUrl, { useNewUrlParser: true })
    console.log("Connected to database.");
    return this.dbClient;
  }
```

## DataStore's `collection` Method

The `collection()` method on DataStore:

- acquires a connection to the MongoDB server
- asks it for the _database_ named `til`
- then asks for the _collection_ of TIL entries named `facts`

```javascript
  async collection() {
    const client = await this.client();
    const db = client.db(this.dbName);
    const collection = db.collection(this.collName);
    return collection;
  }
```

It is declared `async` (asynchronous) because the database connection might not currently be open, and the `client()` method might take some time to respond.

## DataStore's`all` Method

The `all()` method on DataStore...

- connects to the _collection_
- asks it for a _cursor_

A cursor is like an iterator for databases.

```javascript
  async all() {
    let collection = await this.collection()
    return collection.find({});
  }

```

If you know you've only got a few results, you can call `cursor.toArray()`, which fetches all the results up front, then puts them all into an array. But it's usually cleaner and safer to use the cursor itself.

## Using our Class

Now that we've got a couple methods set up for connecting to, and reading from our database let's bring it into our `mongo-client.js` file, set it up and use it with JavaScript.

- Import the `DataStore` class from `data-store.js`
  - This is Node.js so we'll need to use the `require` method
  - Don't forget to export your `DataStore` with `module.exports = DataStore`
- Since we are now connecting through our DataStore we no longer need the Mongo drivers in our `mongo-client.js` file
  - Feel free to delete the mongo setup in this file (the import, and connection)

Then we will replace the contents of your run function with code that:

- Creates our new interface for our database and connects to a `"books"` collection

```js
let collection = new DataStore("mongodb://localhost:27017", "library", "books");
```

- Prints to the terminal all the books in our `books` collection

```js
let allBooks = await collection.all();
allBooks.forEach((book) => {
  console.log(book);
});
```

> Note: This will need to happen inside the `run` function, or any other `async` function that you have defined

## DataStore's `.find` Method

Go back to our `DataStore` and add a new method called `.find` that:

- accepts a parameter named `query`
- connects to the _collection_
- returns a cursor with all matching documents

`.find` when it's used takes a parameter named `query` listing the _fields and values_ as a JS object to match on.

For instance in our `mongo-client.js` file, `collection.find({author: 'alex')` returns all entries whose `author` field is the string `alex`

For more complicated queries, you can use operators like `$gte` (greater than or equal) and `$or`, e.g. this would find all items with 1 or more copies left, but less than 5:

```js
collection.find({
  copies: {
    $gte: 1,
    $lt: 5,
  },
});
```

We'll be talking more in depth about query objects a little later this week, but you can get a head start by reading the docs here:

- <http://mongodb.github.io/node-mongodb-native/3.1/api/Collection.html#find>
- <https://docs.mongodb.com/manual/tutorial/query-documents/>

## DataStore's `addEntry` Method

Create a new method on `DataStore` called `addEntry` that:

1. retrieves the _collection_ object
2. inserts a single data entry into it
3. returns the new ID that Mongo chose, in case we need it later

## `_id`

Every time you insert a document into a MongoDB collection, Mongo adds a field named `_id` with a _unique_ value.

This id is _not_ a normal integer! It's a long string with a hex code inside it.

Mongo has an algorithm for ensuring that this id is unique across _all other documents_ in itself (and probably inside every other MongoDB database in the universe too).

In JavaScript, Mongo defines a _class_ named `ObjectId` that takes an ID string, and parses it as a Mongo Object ID.

## DataStore's `.findOne` Method

Create a new method on your `DataStore` that can find a single item by it's ID field. As with all our other methods we will want this to be an `async` method. It should:

- accept a string `id` as a parameter
- turns the string `id` into a Mongo `ObjectId`
- queries the database for _just that document_
- returns _a single document_

## DataStore's `updateEntry` Method

Create a new `async` method on `DataStore` called `updateEntry`. This method will take two parameters:

- The ID of the target document (as a string)
- An update object

The `.updateOne` method on a Mongo collection takes two arguments, the "filter" which is a database query that targets a document, we will be using the ID for this, and a update object. The update object only needs to contain the key/value pairs you want to change. So If we had an object with and ID of `"60f5e2608f5ef1330f9b841e"` we could use MongoDB's `.updateOne` method like so:

```js
collection.updateOne(
  //This is our query to target the document
  { _id: ObjectId("60f5e2608f5ef1330f9b841e") },
  //This variable holds the update to be applied
  updateObj
);
```

**But** you will need to wrap the key/value pair(s) you want to update in an atomic `$set` operator so our `updateObj` would look like this if we wanted to change our document's `name` property to `"New Name"`:

```js
let updateObj = { $set: { name: "New Name" } };
```

## Building Out the Client

Let's extend the `run` function to make it a little more interactive. Let's set it up so we can interact with our application through the command line.

- Define an `ask` function as we did in the first week of this course
- When the `run` function gets called _ask_ the user what they want to do
- Depending on the user input, perform a database operation
  - and ask if they'd like to perform another operation
- Add a section to your logic to handle each of the database operations we set up in our `DataStore`

## Going Further

Currently our DataStore class can handle several read operations, and a single create operation. Build it out more so that there are methods for:

- Inserting several documents at once
- Deleting an existing document

Create sections of your front end logic to handle these operations
