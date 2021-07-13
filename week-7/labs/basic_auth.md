# Basic Authentication

## Welcome!

In this lab we'll be creating a simple authentication system, allowing users to access a personalized dashboard. For security reasons we will also be encrypting their passwords on the database using bcrypt so that no one (other than the user) will know what their password is.

## Setting up the Server

Set up an express app

Also install, and import bcrypt

## Setting up the `.env` File

This is where we'll store the `saltRounds` so it's always completely hidden.

Don't forget to `.gitignore` the `.env` file!

## Setting up The Front End

It's two html pages, a dashboard, and a home page.

The home page has a form that allows the user to enter a user name and password

# Hashing, cont.
<!-- Example code; should be removed or significantly modified, we'll be bringing the passwords in from the user input on the front end, and comparing them against hashed passwords stored in a DB-->
```javascript
const bcrypt = require('bcrypt')
const saltRounds = 10
const plainTextPassword = 'password1234'
```
Now, let's take that `plainTextPassword` and *salt* it to return a *hash*, or encrypted string

```javascript
bcrypt.hash(plainTextPassword, saltRounds, (err, hash) => {
    console.log(`unhashed password: ${plainTextPassword}`)
    console.log(`hashed password: ${hash}`)
    //Store hashed password in DB here
})
```
Running this code should show you a before and after:

```javascript
unhashed password: "password1234"
hashed password: "$2b$10$CbPOlQSQhFnz71CrS5h9M.t6IJBOtA3cQaDn/ams1IPTP0ffFPkaO"
```

# Hashing, cont.
Now, after a password hash has been stored in your database, how would you compare it to a user's input?

`bcrypt` comes fully prepared to "undo" those multiple rounds of salt for you!
Simply run it through the `compare` method, like so:

```javascript
    // retrieve stored (and hashed) password from DB
    bcrypt.compare(plainTextPassword, hash, (err, result) => {
        console.log(`Password matches hash: ${result}`) // true
    })
```
The above code will need to be within the previous `hash` method, due to their asynchronous nature.

## 
