# Routing

*routing* in web apps is essentially a set of rules to decide...

  * given this request
  * what code do we run?
  
the "code we run" is also called an *endpoint* or a *route* or a *script* or a *handler* or any of a number of different terms. It is generally a callback function with access to a "request" and a "response" object.

The "code we run" doesn't have to be complicated. It could be as simple as sending a file.

---

# Routing Cont.

Many web app server frameworks have complicated systems for routing, but that complexity is not essential.

Routing can be a simple series of `if..else` statements, or a [`switch` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch) 

and most of the fancy framework code is simply to build up a list of matching rules which the server then walks through in first-to-last order.

---

# Routing Cont.

Libraries like Express give you more than the *implementation* of features like routing and parameter passing.

They also give you an *interface* that will make **your** code easier to read.

As well as a shared context of documentation and tutorials so other coders don't have as much to learn before understanding your code.

---

# Express Routing

* supports handling all HTTP methods with the pattern `app.method(path, handler)`

* whenever an incoming request of the given *method* (POST, GET, DELETE...) matches the *path* parameter, Express will invoke the *handler* callback function

* That *handler* has access to the `request` and `response`, and the methods/properties they contain!

---

# Express Routing Example

An Express route set up to listen for a `get` request on the home page, that sends back the text "Hello World!" would look like this:

```js
app.get('/', (request, response) => response.send('Hello World!'))
```

`get` requests are by far the most common type of request you'll be dealing with since it is the method that *requests* new data from the server

`get` requests can be triggered many different ways, such as by entering a URL in the browser, using `fetch` in your client side code, or redirecting to a new router on the server.

---

# Express Routing Breakdown

| code | explanation |
|---|---|
| `app` | my application, the initialized Express app|
| `.get` | when the client sends a `GET` request |
| `(request, response) =>` | will call this *handler* function with a *request* object and a *response* object |
| `response.send` | send a response |
| `('Hello, World')` | with this string as its body | 

---

# Parameters in Express

The special character `:` means "this is a [path parameter](./parameters#path_parameters)"

Example:

|  |  |
|---|---|
| Path:| `/hello/Gandalf` | 
| Route:| `/hello/:friend` | 
| Params:| `{friend: 'Gandalf'}` | 

Express will grab the *value* from the path itself, and assign it to `request.params` for you to use later.

---

# Route Matching 

Express will try to match routes 

- *in the order they are defined* in your JS file.
- Once it finds the matching route 
  - runs the attached request/response callback function
  - and stops looking. 
  - Any other route handlers that could also match don't run

---

# Route Matching Cont. 
```javascript
// POST /login gets urlencoded bodies
app.post('/login', function (req, res) {
  res.send('welcome, ' + req.body.username)
})

// POST /api/users gets JSON bodies
app.post('/api/users',  function (req, res) {
  // create user in req.body
  res.status(200)
})
```


<!--
---

# Express Middleware

* [`express.urlencoded`](https://expressjs.com/en/4x/api.html#express.urlencoded) parses incoming requests with URL-encoded payloads.
* [`express.json`](https://expressjs.com/en/4x/api.html#express.json) parses incoming requests with JSON payloads.
* [`express.static`](http://expressjs.com/en/4x/api.html#express.static) serves static files, and sets restrictions on client-side access
* Tons of 3rd-party and error-handling options
* And the ability to create, and use your own middleware!


 # Middleware Example

Example (from [the express guide](http://expressjs.com/en/resources/middleware/body-parser.html)):

```javascript
// POST /login gets urlencoded bodies
app.post('/login', express.urlencoded(), function (req, res) {
  res.send('welcome, ' + req.body.username)
})

// POST /api/users gets JSON bodies
app.post('/api/users', express.json(), function (req, res) {
  // create user in req.body
})
```

---

# Write your own middleware!

Remember how we said you can create your own middleware? Let's give it a shot!

When doing so, that function will have access to the `request` and `response` objects, AND the callback function `next` that simply tells it to carry on with the route's execution.

```javascript
function logTime(req, res, next) {
    let date = new Date()
    console.log(date.toLocaleDateString()) 
    next()
}

app.get('/route/', logTime, (req,res)=>{
  res.send("All done!")
})
``` -->