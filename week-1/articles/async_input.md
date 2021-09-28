# Promises

## Asynchronous Programming

What is asynchronous programming? In short it's any operation that needs to wait for a response.

Any operation that is triggered by, or relies on user input is an asynchronous operation because the program can't just run beginning to end without stopping. Likewise, if we need to get some data from elsewhere (usually elsewhere on the internet) and use that data in our program then we would again be doing asynchronous programming. Because the computer doesn't know when the user will input something, or exactly how long a request for data will take to resolve the operation needs to be taken out of the normal timing flow of the program, and **wait** for a response before it can proceed. Once we have that input the program can continue.

## Callback Functions

The original way of handling asynchronous operations in JavaScript is with callback functions. A callback function is just a function that gets called be another function. To set up a callback function you pass the callback function's definition to another function as the argument. e.g.

```js
//function definition to be used as a callback function
function callbackDef() {
  console.log('Hello')
}

//definition of function that calls a callback function
function caller(callback) {
  callback()
}

//using "caller" to call "callbackDef"
caller(callbackDef)
```

>Note that callback functions *are not called* when we pass them as an argument. The containing function will handle calling the callback *when it needs to.*

Callback functions are most commonly used in modern JavaScript as *event handlers.* We'll be talking more about event listeners, and event handlers as the course progresses, but in summary an *event listener* opens a channel, and waits for a certain action. Then the *event handler* gets called in response to that action whenever it occurs. We've actually already seen an event handler, and event listener in action. Remember this bit of code:

```js
process.stdin.on('data', (chunk) => {
  console.log(chunk.toString())
})
```

Let's break it down:

* `process.stdin` is JavaScript's way of referencing the terminal (It's the **st**an**d**ard **in**put for the default Node.js **process**)
* `.on` is an event listener attached to our terminal
* `'data'` is the *type of event* we're listening for
* `(chunk) => {console.log(chunk.toString())}` is an *anonymous function definition* which is being used as a callback function that prints back whatever data was entered.

The end result of this is that whenever the terminal receives a data entry event (the <kbd>enter</kbd> key is pressed) we will see what ever was entered printed back to us as a string.

Callback functions used to be the only way to deal with asynchronous code in JavaScript, but we now have more tools to help make handling asynchronous operations easier.

## Promises Promises...

While event listeners and callback functions are still a major part of creating user interactions we now have more options available to us with modern JavaScript. One of the big additions to the language in 2013 was the introduction of *promises*. Promises allow you to write code around values that need to be generated asynchronously. A promise is essentially a placeholder for actual data, and we can set things up so that the program waits until that placeholder becomes the actual data, then we use the real data and resume the execution of our program.

"The Promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value." -[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

This means when you look at something that returns a Promise you will see one of 3 things:

* A *Pending Promise* which means it's still waiting for a response
* The *actual data* which means the promise has been resolved successfully
* An *error object* meaning the Promise was unable to be successfully resolved

If our program (or function) is like a food truck, then a promise is like a ticket for your order. It's not the food you ordered, but it's a *promise* that the food will be ready soon. Once you get the actual food (in this metaphor the real data) you can add condiments, and eat the food (resume the program).

## Async/Await

In 2016 the `async` and `await` keywords were added to JavaScript to allow developers to more easily handle promises

To tell our program to wait until a promise has been resolved we can create an `async` function by appending the `async` keyword to the function definition.

```js
async function sayHello() {
 //some asynchronous code
}
```

While we're inside the function we can use the `await` keyword on any operation that returns a Promise to force our program to wait until the Promise is resolved, and then use the result of that Promise.

```js
async function sayHello() {
  //the ask function returns a Promise not a value
  let name = await ask("what is your name?")
  //The await keyword causes the program to use the resolved promise instead of a pending promise
  console.log("Hello " + name)
  //So that we Print "Hello somebody's name" rather than "Hello [Object Promise]"
}
```

It is worth noting that *all async functions return promises by default*

## The `ask` Function

The `ask` function we set up in class uses Promises to ask a question in the command line, and return an answer. Let's break this function down and see how it works.

Our `ask` function is made of a couple different parts. The first thing to recognize is that we are using a library called "readline" that makes reading lines of text easier for your program. Before we even start our ask function we need to configure the library to let it know where the input is coming from, and where the output is going to. For our purposes we want to read input from the terminal, and send output back to the terminal so we configure the Readline Interface like so:

```js
//import the readline library
const readline = require('readline')
//Tell readline where input is coming from, and going to
const interface = readline.createInterface(process.stdin, process.stdout)
```

Readline is a core Node.js library which means we don't have to install anything, but we still do need to import it if we want to use it. `process.stdin` and `process.stdout` are both references to the terminal sa an input, and output device respectively because we're running our process in the terminal, and the standard input, and standard output for the terminal are both the terminal itself.

Once we have our interface we can create our `ask` function.

```js
function ask(questionText) {
  return new Promise(function (resolve, reject) {
    interface.question(questionText, resolve)
  })
}
```

Our `ask` function returns a `Promise` object which we initialize with the `new` keyword. We than give it an anonymous callback function as an argument which sets up what to do for this promise. It's inside the promise initialization that we use the readline interface we created previously. Here we access the `.question` method on our interface and give it two arguments; the question we want to print (in this case `questionText` so we can dynamically generate the question when we call the `ask` function), and how it should handle a response (in this case resolve the promise, which will return whatever the user entered in response to the question)

## Escaping the Promise

Once you start dealing with promises it is very hard to break out of that flow. Whenever you're dealing with promises you will generally only want to do so from inside an asynchronous function (which itself returns a promise) or from within a promise chain. We will be discussing how we can create a promise chain later in the course, but for now remember to `await` your promises otherwise things will not be what you expect them to be!

## Further Readings

[MDN ~ Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

[MDN ~ Using Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)

[MDN ~ async function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)

[MDN ~ Making asynchronous programming easier with async and await](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await)

[NodeJS ~ JavaScript Asynchronous Programming and Callbacks](https://nodejs.dev/learn/javascript-asynchronous-programming-and-callbacks)

[NodeJS ~ Understanding JavaScript Promises](https://nodejs.dev/learn/understanding-javascript-promises)

[NodeJS ~ Readline Docs](https://nodejs.org/api/readline.html#readline_rl_question_query_options_callback)

[Jake Archibald ~ JavaScript Promises: an introduction](https://web.dev/promises/)
