# Lab: Creating a JSON file


## Welcome!

In this lab we will be creating a JSON file which we will be using as an api endpoint in a future lab. Our JSON object will hold some data which represents the "correct" answers to a series of questions we will be asking on the client side. We will also be playing around with another JSON object, and looking at ways we can procedurally generate JSON on the server

## Structuring the Directory

- In your Terminal, create a new directory named `json-server` with `mkdir json-server`
- Enter the directory with `cd json-server`
- Inside this directory, create a subdirectory called `api` using `mkdir api`
- Enter the directory using `cd api`
- Inside `api` create a file named `example.json`
- Create another file named `answers.json`

We will be using `example.json` to play around with some different json structures, and look at how we can view it in the browser.

`answers.json` will be used in a later lab to check against a form input, and provide a conditional response.

## Creating JSON

JSON files are easy to create since they are just JS objects that only contain strings.

 - Curly braces hold these objects, unless they are arrays
 - Arrays are held within square brackets

The data inside each JSON object must be written in key: value pairs. **Keep in mind** that the keys need to be double quoted, as they are strings.

  - Template strings do not work!
  - Each `"key": value` pair must be separated by commas.
  - Your JSON also *cannot* include comments.
  - Methods also will not work.
  - Any operation will not work, values *must be* hard coded

## Creating the Example

Let's use our `example.json` file to play around with some different structures for our JSON object.

In `example.json` let's create a JSON collection. To create a JSON collection open up a set of square brackets `[]` but **don't assign it to a variable**. Each JSON file can only contain one main data structure, but this structure can be an array which contains multiple objects.

Inside this collection just add a couple different strings for now.

## Building the JSON Server

Install Express, and set up a simple express server, which I will refer to as `server.js` from now on (though you should feel free to use a different name if you want.). It doesn't need to be a static file server at this point.

In the server set up a route to serve your `example.json` file. Start your server, and visit that route to see the contents of your file. Start the server, and visit the route. What do you see?

If you'd like to look at JSON in a prettier format in Chrome you can install [this extension](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh)

## Extending our Collection

While JSON can be used to send collections of primitive data types it is more commonly used to send across objects.

Let's add an object to our collection with:

- at least one number
- at least one boolean
- a nested object with at least one key/value pair

## Forcing an Error

- What happens if we try to add a key to a JSON object that isn't double quoted?
- What about using a mathematical expression for a value?
- Try adding a method to your JSON object. What does VSCode's linter tell you?

## Generating JSON Server Side

We don't always need to be sending static JSON files from the server. We can also create JavaScript objects on our express server and send them over *as JSON* data.

- Create an object in your `server.js` file
- Set up a route to serve this object
  - for the *response* use the `response.json` method to send the object you just defined over.
- Visit the route in your browser
- Go back to your server file and add a method to your object
- Restart your server and try visiting that route again. What do you see?

## Adding Quest Data

Now let's fill out our `answers.json` file.

- In `answers.json` create a JSON object containing:
  - a name
  - a quest
  - a favorite color
