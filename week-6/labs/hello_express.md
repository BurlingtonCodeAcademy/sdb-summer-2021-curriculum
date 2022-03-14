# Hello, Express!

## Welcome!

In this lab you will set up your first server in [Express](https://expressjs.com/).

## Getting Ready for Express!

Express is a JavaScript framework that allows us to build servers a little more easily. To use it we will need to download it from npm. In your Terminal, make a directory called `hello-express` with the command `mkdir hello-express` and `cd` into it. 

Run `npm init -y` to create a fresh `package.json` file, to get your application ready. Then run `npm install express` to download the Express package into this project so we can use it to set up our server.

## Setting up the Server File

Once you've installed Express make a file named `server.js` for us to set up our express server.

When running a server we will be working in a Node environment so we need to use the `require` function to import files and packages.

```javascript
const express = require('express')
```

Then we can initialize our express app, and assign it to a variable. While we're at it let's also set up a variable for the port our app will run on, using the standard port if one is defined or, port 5000 if one is not defined.

```js
const app = express()
const port = process.env.PORT || 5000
```

## Hello, Home Page!

Servers listen for specific routes using specific methods and then determine a response based on the code that you, as the programmer, write. Express has built in methods that correspond to the HTTP methods `GET`, `POST`, `PUT`, `PATCH`, and `DELETE` which take a string that represents a path from the URL, and a callback function that takes two arguments, a *request object* and a *response object*. 

To send a response on a given route we can call the `.send` method on the `response` object passing in the message we want to send.

Most of the time we'll be listening for `GET` requests since that is by far the most common type of request on the internet.

```js
app.get('/', (request, response) => {
  response.send('Hello, World!');
})
```

The final step to getting our server up and running is to tell our express app that it needs to open a connection on a port, and keep it open so it can listen for requests, and send responses. To do this we use our express app's `.listen` method to open a port.

We can optionally pass a callback function as the second argument to the `.listen` method. The callback function will be called when the connection is first established.

```js
app.listen(port, () => console.log(`Listening on port ${port}!`))
```

## Hello, Localhost!

- Go back to the Terminal and run the app with `node server.js`
  - If all goes well you should see the message `Listening on port 5000`, and the cursor should be hanging

- Visit <http://localhost:5000/> in your browser to see it running on your own computer.
  - You can stop the server in the console by using <kbd>Ctrl</kbd> + <kbd>C</kbd> to kill the process


## Hello, Package!

A *package file* contains information about how to build and run your app.

In VSCode, open the file named `package.json`, it will have a section like this:

```json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

Add a start script to start up our server like this:

```json
"scripts": {
    "start": "node server.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

Note that the code after `start` is *exactly* what you typed in the shell to run the app locally. Scripts are a way of setting up short hand commands for running certain processes and files, and web hosting services usually expect a `start` script that will start up your server.

You can test this locally by running `npm start` and visiting `https://localhost:5000`.

## Hello HTML

The `response.send` method can be used to send more than just plain text responses. Any HTML formatted string will be interpreted, and displayed as HTML when it is loaded into the page. Try adding some HTML tags in your response to add a little style to your text. e.g.

```js
response.send("<h1>Hello, <i>World!</i></h1>")
```

## Hello, Routes

We have currently set up a single route for our server on the path `"/"` that sends over the response. This serves as the homepage for our app, but let's add another page. Our homepage greets people so let's set up a route that sends a "farewell" message. Create another route to listen for a `GET` request on the path "/goodbye" that sends a "farewell" message.

## Hello, Request Params!

Express supports variable path parameters which you can define when you are setting up your routes. These *path parameters* look a lot like the path parameters we saw in React Router, and even operate the same way. While path parameters are not a standard part of the internet at large they are a fairly common programming pattern and have been adopted by several frameworks.

In your `server.js` file, set up a route `"/:key"`, that when visited,
prints `request.params` to the command line.

Then visit `http://localhost:5000/value`

You should see the params object printing to the terminal that is running the server.

```javascript
app.get('/:key', (request,response)=>{
  console.log(request.params) // prints {key: 'value'}
})
```

## Hello, You!

Set up a route using path parameters that will display a personalized greeting based on a name entered in the URL as the path.

