# Objective

## Learning

In this lab, we will be using the Express Node.js framework to write our first server.

Topics:

- Servers
- Express, a Node.js framework

## Achieving

In this lab, we will creating a basic website with a server.

Your work will result in:

- A website that displays different greetings based on the route.
- A server that sends different HTML dependent upon the route.

# Procedure

## Set up your files

- [ ] In the new directory `hello-express`, run `npm init -y` to create a new `package.json`. You can then install Express.

## Set up your server

- [ ] The first step you will need to do is to import `express`. Node.js imports work differently than JavaScript and React and use the following syntax:
`const example = require('example')`
- [ ] The second step is assigning the invocation of `express` to the variable `app`.
- [ ] The third step is creating a variable to reference the port the app will run on. You will need to use `process.env.PORT` to do this. You will also want to use the logical OR `||` operator to run on 5000 If the computer default is not available.

## Open up the connection to a port

- [ ] You will need to use the `listen` method on `app`.
- [ ] `listen` takes two arguments, the `port` variable, and a callback function.
- [ ] Set up the callback function to print a message to the console that informs the user of which port the server is listening on.

## Set up your first `GET` route

- [ ] The first route we want to set up is for the `/` route (also known as the index route).
- [ ] We want to use a `.get` method, and we want to send the response of "Hello, home!"
- [ ] Reference the following syntax to do so:
```js
app.get('/example', (request, response) => {
    response.send('Hello, example!')
    })
```
- [ ] You can test your route by visiting localhost:5000 in the browser.

## Set up further `GET` routes

- [ ] Set up at least three more GET routes. They should all be different pages, and the response they send should reflect what page the user is on.

## Send HTML on your routes

- [ ] Your `.send` methods can also send HTML. This is a basic example of server-side rendering. Change all of the responses on your routes to utilize HTML. 
```js
response.send("<h1>Hello, <b>example</b>!</h1>")
```

## Set up request params

- [ ] Servers can also utilize params passed in the URL. 
```js
app.get('/:key', (request,response)=>{
  console.log(request.params)
})
```
- [ ] Try visiting an address that does not have a route associated with it and see what prints to the terminal.

## Utilize request params

- [ ] Create a new route with a request param of `:page`. Utilize this to dynamically inform the user of which page they are on instead of hardcoding near-identical responses as you did previously. 

# Review

In this lab, you set up a basic server that sends different HTML as a response, dependent upon the URL in the browser.

The software should:

- Print a listening message to the terminal.
- Serve different pieces of HTML dependent upon the localhost:5000 route in the browser.

## Going Further

- Using conditional logic within your `:page` route, send differently styled HTML responses dependent on the value of `:page`.

- How could you utilize request params to retrieve information from the user to display on another page? _Utilizing server-side rendering_, set up a form that takes in a user's name. This name should then be passed in the URL to another page and used to greet the user there.
