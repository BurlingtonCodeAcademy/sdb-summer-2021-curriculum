# Lab: Hello, Files!

## Welcome!

In this lab we will be creating a server that serves several static HTML files in a multi-page web app. We will be looking at how we can keep our server secure, and focusing on how route matching works.

## Static File Server

Create a new Express project dir called `static-server`

* Create a file called `app.js` and get it ready to serve files with the following setup:

```js
const express = require('express')
const app = express()
const port = process.env.PORT || 5000

app.use(express.static('.'))

app.listen(port, () => console.log(`Example app listeningport ${port}!`))
```

* create a file called `index.html` containing an `h1` element, with the text "Hello, world!"

* in `package.json`, add a start script:

```json
{
  "scripts": {
    "start": "node app.js"
  }
}
```

* launch the web server using `npm start`

* Now open a web browser and visit <http://localhost:5000/>

## The Homepage

You might notice that we haven't set up any routes for our server but it still serves the `index.html` file as our homepage. This is because Express (like many static file servers) if it isn't given a route handler for `"/"` will look for a file named `index.html` in the root level of the directory it's serving from, and send that over by default.

## The Static Directory

The good news: your web server can now serve static files to its clients!

The bad news: Currently we're serving *all* of our files to our web clients, who can now see *any files they like* in your project directory, since we've told our Express app to use the *root level* of our project directory as the static directory.

(This includes your server source code and configuration files, which may include secrets like passwords)

## Hack Your Own Server

open a web browser and visit <http://localhost:5000/package.json>

`package.json` should probably be more secret than that...

You could also see your server file by visiting <https://localhost:5000/app.js>

## Solution: the `public` Directory

To keep server-side code and configuration files secret, most web apps have a *public* directory containing static files.

This is one major difference between *static sites* and full stack *web apps* -- since some of your code runs on your server, and some runs on your client's browser, your project directory structure needs to separate *client-side files* from *server-side files*.

All client-side files, such as HTML, CSS, client-side JavaScript, embedded images, etc. should live in the `public` directory. Any configuration files, server, or database code should exist outside the `public` directory. Furthermore client side JavaScript, and server-side JavaScript operate in different environments (the browser, and Node.js respectively), so some of the options, methods, and functions are different, or don't exist in one environment or the other.

* in your top-level project dir (`static-server`), type `mkdir public` to generate a new subdirectory named `public`
* in your `app.js`, change the `app.use` line to

```js
app.use(express.static('public'))
```

Now you can put HTML, CSS, PNG, and `.js` files inside `/public` where your clients can fetch them as needed, but your users will not be able to access files outside the `public` directory.

* *move* `index.html` from your top-level project dir (`static-server`) to your `public` dir
* restart your server
* Now open a web browser and visit <https://localhost:5000/>

# More Pages

Let's see how we can set up some more routes to serve more pages.

* Inside your `public` directory create two new HTML files
  * `trek.html`
    * Containing an `h1` which says "To boldly go where no one has gone before!"
  * `wars.html`
    * Containing an `h1` which says "May the Force by with you, always...
* Create two `a` tags in `index.html`. One should have an `href` pointing to `"/startrek"` the other should point to `"/starwars"`
  * Don't forget to give the anchor tags a little text content so they show up on the page

# Matching the Route to the File

When setting up your request/response route handler functions previously we used the `response.send` method, however this method only sends text, and cannot be used to send files.

If we want to send a full file as our response we need to use the `response.sendFile` method, and give it the *full file path* of the desired file.

To get the full filepath to the directory our server lives in we can use the special variable `__dirname` (double underscore dirname) and then add the relative file path to our HTML to get the full filepath for the file we want to serve.

```js
response.sendFile(__dirname + "/public/some.html")
```

The above line of code could by used to serve a file named "some.html"

In your server file (`app.js`) set up two new routes listening for `get` requests on the paths you set up on your anchor tags.

* The path `/startrek` should *get* the `trek.html` file as a response
* The path `/starwars` should *get* the `wars.html` file as a response.

# 404 Not Found and other status codes

open a web browser and visit <https://localhost:5000/oops/>

if there is an error loading the file (in this case, there is simply no route defined for that path), the server must send the correct *[status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)*

  * (404 means "not found")

> Note: even though there is an error, the server *still returns a body and content-type* for display to the user.

In this case, we just see Express' boring default error page, but it's possible to get [very creative](https://www.canva.com/learn/404-page-design/) with web site error pages.

* Create a page in your "public" directory named 404.html
* When the user visits any route other than one of your previously assigned routes the 404 page should be displayed.
* Add some styles to your pages. Make them look nice!