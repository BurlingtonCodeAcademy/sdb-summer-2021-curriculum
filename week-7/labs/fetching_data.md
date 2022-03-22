
# LAB: Fetching Data

We will be setting up a front end React application that will allow the user to interact with a database, with a server acting as the interface between the two. We'll be building this off of the code we wrote for our Data Store lab so that we can hook into the functionality of the `DataStore` class.

## Setting up your Directory

Create a new React app named `react-store`. Install mongodb and express. 

At the root level of the directory, create `server.js` and `data-store.js`.

`data-store.js` will be identical to your previously built file.

`server.js` will combine the code written in `mongo-client` with an Express server.

Optionally, create a proxy in `package.json`.


## A Note on Reusing DataStore

It can be tempting to copy and paste when bringing a large file, or chunk of code (such as our `DataStore` class) into a new application. **DON'T!**

Typing the code out will help you remember the code, and it will allow your brain to make new connections between the code you are writing, and what it's telling the computer to do.

Use your old `DataStore` as a reference, but actually type all the code out manually.

**Don't copy and paste!**

## Setting up the Server

The server needs the standard Express boilerplate. It also needs to have `DataStore` imported. You will also need to create a new `DataStore` and name it `collection` just as you did in the previous lab.

Once you have the basic setup for your server you are going to want to set up routes for the following database operations you created in `DataStore`: `find`, `addEntry`, and `update`.

These routes will be correlated with database "jobs", and you will have two kinds: GET jobs and POST jobs.

_All jobs need to be async_.

GET jobs send data TO the client FROM the server (database). 

```js
app.get("/bringmeallthestuff", async (req, res) => {
  //find all the stuff in my database
  
  //send that stuff to the page
});
```
POST jobs send data TO the server (database) FROM the client. You will need to redirect the user back to the page the form is on; if you do not, they will be left on a blank page.

```js
app.post("/addnewstuff", async (req, res) => {
  //create new stuff using user input
  
  //save the new stuff to the database
  
  //redirect the user back to the page they were on
});
```

## Setting up the Front End

In our React front end, let's get the following on the page:

A list of all books currently in our collection. You will need to fetch this from your `find` route and set it to the state `allBooks`. You can use the `map` method on `allBooks` and programmatically place every book on the page.

```js
allBooks.map((book) => {
<h1>{book.title}</h1>
<h2>{book.author}</h2>
}

```

A form that lets the user add a new book with the same `key:value` pairs as the preexisting books. This will need a POST method and an action that matches the route on the server.

A form that lets the user update a specific book's information. This will need a POST method and an action that matches the route on the server.

You will need to connect these front end components to the job routes you previously defined.

## Test It Out!

Use Compass to verify that when the user adds a new book or updates a preexisting one, it changes in the database. You may need to use the refresh feature on Compass, which is a small rotating arrow in the upper left of the side bar.

## Going Further

Add a new method to `DataStore`, `delete`. It will take in an `id` as a parameter. 

On the front end, create a form that allows the user to enter in the TITLE of a book they want to delete. 

Consider this: the method `delete` takes in an `id`, but the user will be inputting a `title`. How would you translate the title to the id to delete the correct book?

