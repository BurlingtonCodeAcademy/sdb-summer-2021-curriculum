# Basic Authentication

## Welcome!

In this lab we'll be creating a simple username and password authentication system, allowing users to access a personalized dashboard. For security reasons we will also be encrypting their passwords on the database using bcrypt so that no one (other than the user) will know what their password is.

## Structuring  the Directory

First create a new directory for this lab. In that directory, which I shall refer to as "basic-auth," run `npm init -y` and then install:

* bcrypt
* express
* mongoose
* dotenv

## Setting up the Server

Set up an express app with as a static file server, serving files from the "public" directory. We'll need to read some form data so we will also want to use the `express.urlencoded()` middleware for reading form bodies.

In the server file we'll also need to import `bcrypt` for encryption, and `mongoose`, to store our valid usernames and passwords. Since we will need some secret data you will also want to configure `dotenv` so we can read our local `.env` file.

Our server will also need several routes defined:

* Two routes for post requests on:
    * `"/login"`
    * `"/signup"`
* A route for serving the dashboard
    * at `"/dashboard/:username"`

## Setting up the `.env` File

We'll store the salt rounds in a `.env` file as the variable `SALT` so it's always completely hidden, and make it even harder for any bad actors to steal our user's passwords. Remember your salt rounds should be a number, so don't forget to `parseInt` it when you bring it into your server.

You'll also want to set up a Mongoose model that defines a `User` schema that takes a `username` and `password` fields, both of which should be strings. You'll also want to use Mongoose to connect to a MongoDB collection called "users"

Don't forget to `.gitignore` the `.env` file!

## Setting up The Front End

Create a "public" directory to house our front end code. On the front end we only need two pages:

* our home page, with a login form, and a sign up form
    * that sends a `POST` request to `"/login"`
    * or a `POST` request to `"/signup"` respectively
* our dashboard that will greet the user by their username
    * bringing the username in from the URL

## Signing Up

When the user signs up for an account we want to take their password, encrypt it, and then write the username and encrypted password to a database collection called "users." 

```javascript
let saltRounds = process.env.SALT

bcrypt.hash(req.body.password, saltRounds, async (err, hash) => {
    let userDoc = {
        username: req.body.username,
        password: hash
    }

    let user = new User(userDoc)

    user.save()

    res.redirect("/")

})
```

## Logging In

Now, after a password hash has been stored in your database, how would you compare it to a user's input, when they log in?

Remember `bcrypt` comes fully prepared to "undo" those rounds of salt for you. We can run our stored password against the password the user entered, and if they match we redirect them to their dashboard

```javascript
let userObj = await User.findOne({username: req.body.username})

bcrypt.compare(req.body.password, userObj.password, (err, result) => {
    if(err) {
        res.status(403).send("Access denied")
    } else {
        res.redirect(`/dashboard/${userObj.username}`)
    }
})
```
