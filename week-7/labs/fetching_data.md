# Searching the Database

## Welcome!

In this lab we will be setting up a front end React application that will allow the user to interact with a database, with a server acting as the interface between the two. We'll be building this off of the code we wrote for our Data Store lab so that we can hook into the functionality of the `DataStore` class.

## Setting up your Directory

* Create a new directory named `react-store` and `cd` into it
* Create a `server.js` file inside this directory
* Get ready to install packages by running `npm init -y`
* install:
  * `create-react-app`
  * `mongodb`
  * `express`
  * Optionally `dotenv` if you want to connect to an Atlas database
* run `npx create-react-app client` to create a new React front end
* `cd` into `client` and run `rm -rf .git` to remove the interior Git repo
* In the `package.json` file that is *inside `client`* add a proxy property pointing to `"http://localhost:5000"`
  * Or whatever port you decide to run your Express server on.
* At the *root level* of your directory create a new `data-store.js` file

## A Note on Reusing DataStore

It can be very tempting to copy and paste when bringing a large file, or chunk of code (such as our `DataStore` class) into a new application. **DON'T!**

Typing the code out will help you remember the code, and it will allow your brain to make new connections between the code you are writing, and what it's telling the computer to do.

Use your old `DataStore` as a reference, but actually type all the code out manually.

**Don't copy and paste!**

## Setting up the Server

Once you've got the `DataStore` recreated you can import it into your server file to more easily connect to, and communicate with the database.

Let's connect our application to the same database we were using in the previous lab, "library" and the collection "books."

We will also want to do our standard Express setup. Since our front end is React we will want our static server to be bound to `"client/public"` (in dev mode at least). If you've set your React front end to proxy requests to "http://localhost:5000" then we'll also need to make sure our server is listening on port 5000.

Once you have the basic setup for your server you are going to want to set up routes for each of your database operations, and you might want to organize these routes by their "jobs."

Some routes (usually listening for `get` requests) are used to send data from the server to the client. These are our API endpoints and we want them to send the data from the database as a *JSON response.*

The other type of backend route will be used to send data from the client to the server (usually, but not always over a `post` request). These routes should accept the data from the client, perform whatever database operation they need to, and then *redirect* the user back to `"/"` so that our React front end will refresh itself.

* routes for reading data send the data as a response
* routes for modifying the documents in our DB redirect to home

## Setting up the Front End

In our React app let's clear out the starter code in `App.js` and start setting up our own front end. Let's put a list of all the books in our library on the page. To do this make sure you have an Express route that uses your `DataStore`'s `.all` method to send over a json formatted list of all the books in your database. On the front end (inside a `useEffect` hook) we can fetch that JSON collection, and store it in state.

In the return statement of our component we will first want to make sure that the array of *book objects* exists, and then we will want to transform it into an array of JSX components and put it on the page.

Think about how you want to perform different operations;

* To add a new entry a form could be useful
  * If you don't handle the submit event it will go to the server as a normal HTML form would
* How to you want to handle deleting an item?
  * By clicking a button?
  * Entering the ID in a form?
* What about modifying an entry?
  * How are you going to determine which document to update?