# Routing

*routing* in web apps is essentially a set of rules to decide...

  * given this request
  * what code do we run?
  
the "code we run" is also called an *endpoint* or a *route* or a *script* or a *handler* or...

The "code we run" doesn't have to be complicated. It could be as simple as sending a file.

---

# Routing is Simple...

Many web app server frameworks have complicated systems for routing, but that complexity is not essential.

Routing can be a simple series of `if..else` statements, or a [`switch` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch) 

and most of the fancy framework code is simply to build up a list of matching rules which the server then walks through in first-to-last order.

---

# ...but don't reinvent the wheel

Frameworks like Express give you more than the *implementation* of features like routing and parameter passing

they also give you an *interface* that will make **your** calling code easier to read

as well as a shared context of documentation and tutorials so other coders don't have as much to learn before understanding your code

---

# Express Routing

* supports handling all HTTP methods with the pattern `app.method(path, handler)`

* whenever an incoming request of the given *method* (POST, GET, DELETE...) matches the *path* parameter, Express will invoke the *handler* callback function

* That *handler* has access to the `request` and `response`, and the methods/properties they contain!

---

# Express Routing Example

In the [Hello, Express](./hello_express) lesson we saw the following route:

```js
app.get('/', (request, response) => response.send('Hello World!'))
```

---

# Express Routing Breakdown

| code | explanation |
|---|---|
| `app` | my application, |
| `.get` | when the client does a `GET` request |
| `(request, response) =>` | will call this *handler* function with a *request* object and a *response* object |
| `response.send` | send a response |
| `('Hello, World')` | with this string as its body | 

---

# [Express Route Matching Rules](https://expressjs.com/en/guide/routing.html)

* paths can include special characters that are *like* regular expressions

  * `?` "zero or one of these"
  * `+` "one of more of these"
  * `*` "zero or more" (but see below)
  * `()` "these go together"
* ...but are *not* regular expressions
  * `.` and `-` are interpreted literally
  * `:` means "this is a parameter" (see next slide)
  * `*` means "zero or more characters" (which is `.*` in real regexes)
* ...or you can use *actual* [regular expressions](https://en.wikipedia.org/wiki/Regular_expression)

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

# Route Matching is Top-Down

Express will try to match routes *in the order they are defined* in your JS file.

Once it finds the matching route it runs the attached request/response callback function

...and stops looking. So any other route handlers that would also match don't get run.

---

# Express Middleware

* [`express.urlencoded`](https://expressjs.com/en/4x/api.html#express.urlencoded) parses incoming requests with URL-encoded payloads.
* [`express.json`](https://expressjs.com/en/4x/api.html#express.json) parses incoming requests with JSON payloads.
* [`express.static`](http://expressjs.com/en/4x/api.html#express.static) serves static files, and sets restrictions on client-side access
* Tons of 3rd-party and error-handling options

---

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

Remember how we said you can customize your own middleware? Give it a shot!

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
```