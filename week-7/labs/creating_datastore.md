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