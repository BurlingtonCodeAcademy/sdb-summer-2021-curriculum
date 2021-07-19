# Connecting to a Database

To query a database we first need to set up a connection to our database, that our app can request information, and receive responses over.

MongoDB supports a range of programming languages, so when we want to bring it into our applications we need to choose the appropriate driver for our coding environment.

Because we are programming in a Node.js environment we want to install the Node.js driver, and the easiest way to do this is through npm:

```
npm install mongodb
```

Once we have the driver installed we can import the `MongoClient` class from it, and use that to generate a connection object

---

# Keeping your Connection Secure

To open a connection to your database you need to give your `MongoClient`'s constructor a connection string which, if you're connecting to a production database, will contain your username, and password. We don't really want any sensitive information like passwords stored anywhere they are available to the internet atr large. Like Github...

So we need to hide our password in our *environment variables* and then reference it through `process.env` instead.

---

# Hiding Environment Variables

When operating in a production environment we will define our environment variables on our hosting service.

For this class we are using Heroku as our hosting service, and the environment variables are called *Config Vars* and can be found in the *Settings* tab

In our local environment we need to do a little more setup. We will need two new files, and one new package:

* `npm install dotenv` is a necessary package for accessing `env` variables
  * it will need to be initialized with `require('dotenv').config()`
* A `.env` file will allow us to set up local environment variables
* A `.gitignore` file to make sure we never accidentally push our `.env` to Github

---

# `.env`

The `.env` file is a text only file that allows you to set up new environment variables as `KEY=value` pairs.

Since `.env` is a text only file format all environment variables are *strings* in JavaScript.

---

# `.gitignore`

The `.gitignore` file allows us to specify files and subdirectories that will never be committed to our Git history no matter what. There are two things you are **always** going to want to `.gitignore`

* `node_modules`
* `.env`

As soon as you `.env` file is added to your commit history you should assume it is public data, and change any passwords or API keys stored within.

Even if it's removed in a later commit a savvy hacker can still access your commit history and read the contents of that file. So it's best to just `.gitignore` it right off the bat.

---

# Setting up the Server

To set up Mongo on the server we will need to install all necessary packages, and then:

* Set up the server framework
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

# Writing to the Database

To write to the database let's first set up a little form on the front end that sends a `POST` request to `"/create"`

```html
<form method="POST" action="/create">
  <input type="text" name="userName" />
  <input type="submit" />
</form>
```

---

# Writing to the DB Server Side

On the backend we can set up a route that listens for that request, writes to the database, and then redirects our user back home.

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

# Reading from the Database

To read from the database we can set up a route that performs a database query when it's hit, and sends the results over as a JSON response. This will create an API endpoint.

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

# Using Data on the Client Side

On the client side we can use this data by fetching it from the API endpoint we just set up, and then doing a little DOM scripting to put it on the page.

> Or state manipulation if we're using a React front end.

```js
fetch("/userdata")
  .then(res => res.json())
  .then(jsonRes => {
    jsonRes.forEach(user => {
      //Do what you need to with the data here...
    })
  })
```
