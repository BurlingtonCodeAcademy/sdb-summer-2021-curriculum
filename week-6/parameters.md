# Overview

When sending information to a server, like navigating the web is wont to do, it is important to understand how that information can be sent. As with most things in programming, it isn't a one-size-fits-all approach. 

These are dependent upon the method, like GET or POST, and what you as the programmer prefer.

---

# Passing Parameters

You can pass parameters from the client to the server in a variety of ways.

Some of the most common are:

* on the Path
  * (after a `/`)
* in a GET request's "query" section
  * (after the `?`)
* in a POST request in JSON format
  * (inside the request body)

---

# For Example...

Let's imagine three different ways to send the same information to GitHub.com:

```js
{
  user: "BurlingtonCodeAcademy",
  repo: "til",
  section: "blob",
  branch: "master",
  filepath: "/README.md"
}
```

---

# Path Parameters

path parameters are great for making *legible URLs*. Your URL is part of your user interface; treat it like the address of a resource!

This path:
`http://github.com/BurlingtonCodeAcademy/til/blob/master/README.md`

would match this route in `express`:
```js
app.get('/:user/:repo/:section/:branch/:filepath',(req,res)=>{
  console.log(req.params)
})
```

That is, if GitHub's server was a simple `express` app...

---

# The Path Explained

The path is the part of the URL that comes after the address, and specifies where to look for specific resources on the site.

In the early days of the internet the path was just a file path for the resources, but as time has passed the path has become an abstraction

The URL path *represents a navigation pattern* to help the user locate resources in a logical manner. We can then use express to send the desired information regardless of the *actual* file structure.

---

# Path Parameters Explained

Path Parameters are variable names that will be assigned to the value that was put into the URL when the request was received

so this path: 

```
/BurlingtonCodeAcademy/til/blob/master/README.md
```

Would match this route in Express:

```js
'/:user/:repo/:section/:branch/:filepath'
```

---

# Params Object

The Route on the pervious slide would create a `params` object and interpret the path like this:

```js
{
  user: "BurlingtonCodeAcademy",
  repo: "til",
  section: "blob",
  branch: "master",
  filepath: "README.md"
}
```

---

# Query Parameters

Query Parameters use the same URL slot as normal queries, but use a particular format to encode multiple parameters into a single string. This should sound familiar from our lesson on URLS.

`github.com/file?user=BurlingtonCodeAcademy&repo=til&section=blob&branch=master&filename=README.md`

This would be available to an `express` server like so:

```js
app.get('/',(req,res)=>{
  console.log(req.query)
})
```

This is admittedly a little convoluted to look at. You're sure to have seen it at some point, however, especially in search engines where the long strings of text can be handled by the browser.

---

# Query Parameters Explained

If a URL contains a question mark `?` everything that comes after the question mark is a query parameter

Requests can pass multiple query parameters to the server on a single request separated by ampersands `&` and are accessed through the `request.query` property in express. You don't need to pass the query as part of the route express is listening for when you're setting up your route handler.

Given the example on the last slide the query object in our express server looks like this:

```js
{
  user: "BurlingtonCodeAcademy",
  repo: "til",
  section: "blob",
  branch: "master",
  filename: "README.md"
}
```

---

# Post Parameters

The other HTTP method used for passing parameters is POST. POST is implicitly more secure, as the information isn't sent directly to the server through a super-visible URL. Instead, it is contained in a post *body* where the information is sent to the server in JSON format.

```
POST /file 

{"user":"BurlingtonCodeAcademy","repo":"til","section":"blob","branch":"master","filepath":"/README.md"}
```

assuming the proper middleware is in place, this information would be available in `express` like so:

```js
app.post('/file', (req,res)=>{
  console.log(req.body)
})
```

---

# Body Parameters in Express

`express` comes with a handful of *middleware* options right out of the box, one of which is `express.urlencoded()`, which parses the `request` body for you. 

That data will be available as `request.body`, much like `request.params` and `request.query`. 

The **difference** is that `request.body` doesn't come from the URL like `params` and `query` do.

Let's do a little code along to help visualize it.

---

# Visualize It

Create a new `index.html` file, and add a form with the method of POST, like so:

```html

  <form action="/postroute" method="POST">
    <input type="text" name="first">
    <input type="text" name="last">
    <input type="submit" value="submit">
  </form>

```

In your `server.js` file, set up a route `/postroute`, that when the form SUBMITS,
prints `request.body` to the command line. Be sure to enter data to the form!

> Note: add `express.urlencoded()` as *middleware* by including an `app.use(express.urlencoded()` in your server setup so the body (the form data, in this case) can be parsed and read by the server.

---

# Summary: GET vs POST

All requests are sent from the client to the server, but there are multiple types of request collectively known as request methods

HTTP defines several *methods* (GET, POST, PUT, HEAD, etc...) the most common are `GET` and `POST`

In general:

* `GET` requests are *requesting* data from the server
* `POST` requests are *sending* data to the server

Though we can set up rules on the server to handle these requests any way we want.

---

# GET requests

* Triggered natively by a change to the URL in the browser, or a `fetch` request
* Ask for a specific resource from the server
* Sends over full URL, including path, and query parameters as part of the request
* Expected path parameters should be defined in the server's routes
* Query parameters do **not need** to be defined in the server's routes

---

# POST requests

* Used to send (usually user generated) data to the server
* Often send by a form
* Sends across a `request object` containing data
* Express uses middleware to properly parse POST requests
* POST data in Express can be accessed through `request.body`

---

# REST

The concept of "path parameters" is central to an idea called **RE**presentative **S**tate **T**ransfer.

It argues that people designing web applications should consider their apps URLs to be an essential part of their app's design and functionality, and that those URL paths should follow a convention that exposes parts of the app as *resources* that can be identified and interacted with individually using a common set of *methods* (that happen to be more or less the same as the HTTP methods).
