# Connecting to a Database

```
npm install mongodb
```

Once we have the driver installed, we can import the `MongoClient` class from it and use that to generate a connection object.

---

# Keeping your Connection Secure

A new `MongoClient` instance needs a connection string which will contain your username and password. 

We need to hide our password in *environment variables* and reference them through `process.env`. The .env files should be listed in .gitignore

---

# Hiding Environment Variables

* `npm install dotenv` is a necessary package for accessing `env` variables
  * it will need to be initialized with `require('dotenv').config()`
* A `.env` file will allow us to set up local environment variables
* A `.gitignore` file to make sure we never accidentally push our `.env` to Github

> This information is added in your app's settings on a hosting service.

---

# `.env`

The `.env` file is a text only file that allows you to set up new environment variables as `KEY=value` pairs.

Since `.env` is a text only file format all environment variables are *strings* in JavaScript.


---

# Setting up the Server

To set up Mongo on the server we will need to install all necessary packages, and then:

* Set up the express server
* Open a connection to the Database
  * optionally create some helper methods to more easily access the database
* Start setting up routes
  * for the front end
  * and for our API endpoints

---

# Using the MongoDB Drivers

To use our Mongo drivers we first need to import the `MongoClient` class from the `mongodb` package.

```js
const { MongoClient } = require('mongodb')
```

> Note that we *do* need to destructure `MongoClient` out of our `mongodb` package.

---

# Connecting to the Collection

Set up your `client` variable in the root level of your server file so it's accessible from any other functions that need it.

```js
let client = new MongoClient(`mongodb:localhost://localhost:27017`);

async function dbConnect() {

  await client.connect()

  let db = await client.db('test')

  let collection = await db.collection("users");

  return collection
}
```

---


# POSTing to your Database


```js
app.post('/create', async (req, res) => {
  let newUser = req.body
  let userColl = await dbConnect()
  userColl.insertOne(newUser)
  connection.close()
  res.redirect('/')
})
```

---

# GETting from the Database


```js
app.get('/userdata', async (req, res) => {
  let userColl = await dbConnect()
  let results = []

  let userList = await userColl.find({})

  await userList.forEach(userObj => {
    results.push(userObj)
  })

  res.json(results)
})
```

---
