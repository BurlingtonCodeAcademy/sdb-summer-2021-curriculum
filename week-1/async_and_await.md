# async/await and Promises

In 2016 promises were introduced to JavaScript. We'll discuss promises in more depth later in the course, but for now know that they make handling asynchronous actions much easier

* A promise is a placeholder for data that doesn't exist yet
* We can deal with promises by using `async` functions
* Any function can be made into an async function by putting the `async` keyweord in front of the function definition
  * `async function waitsForSomething(){...}`
* When using `async` and `await`:
  * `await` means "wait for the following thing to happen"
  * when you use `await` inside a function, you must use `async` to define that function
* Async functions make it so we don't have to use callback functions

> WARNING: `async` functions don't play nicely with `for` loops! (Fortunately, there are other ways to loop that do work well.)

---

# readline

* NodeJS is more than a *JavaScript interpreter*
* It's also a collection of *JavaScript libraries*
* One of the libraries is called `readline`
    * `readline` makes it easier to read lines, naturally :-)
    * the "books" in this library are functions
      * (and classes and other things too)

---

# Using readline

> Warning: this code uses features we have not yet covered! Don't worry if it doesn't make much sense yet, all will be revealed in time.

To use `readline`, include the following lines in the top of your source file:

```javascript
const readline = require('readline');
const readlineInterface = readline.createInterface(process.stdin, process.stdout);

function ask(questionText) {
  return new Promise((resolve, reject) => {
    readlineInterface.question(questionText, resolve);
  });
}
```

---

# using readline - explanation

| code                                                        | explanation                                                                                                                             |
|-------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| `const readline = require('readline');`                     | load the `readline` package and name it `readline`                                                                                      |
| `const readlineInterface = readline.createInterface({...})` | create an *interface* to readline using the following settings:                                                                         |
| `  process.stdin,`                                | for input, use the *standard input stream* (i.e. terminal keyboard input)                                                               |
| `  process.stdout`                               | for output, use the *standard output stream* (i.e. terminal console output)                                                             |
| `function ask(questionText) {...}`                          | a function named *ask* that uses the [Promise API](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises) to asynchronously ask a question and wait for a reply |

(We will cover the Promise API in much more detail later; for now, all you really need to know is that Promises allow us to use `async` and `await` in the next slide.)

---

# Code-Along: Converting Hello Frenemy Input to async/await

Open up your `hello_frenemy_input.js` file, and follow along with your instructor while they convert Hello Frenemy to use an async function.

---

# Code-Along: using readline and await some more

Please follow along with the instructor and create a file named `quest.js`. Add in the ask function:

```javascript
const readline = require('readline');
const readlineInterface = readline.createInterface(process.stdin, process.stdout);

function ask(questionText) {
  return new Promise((resolve, reject) => {
    readlineInterface.question(questionText, resolve);
  });
}

```

---

# Adding functionality

Let's accept a few different inputs, and use them to construct our output

```js
async function start() {
  let name = await ask('What is your name? ');
  let quest = await ask('What is your quest? ');
  let color = await ask('What is your favorite color? ');
  console.log('Hello ' + name + '! ' +
    'Good luck with ' + quest + ', ' +
    'and here is a ' + color + ' flower for you.');
  process.exit();
}


start();
```

* run it from the command line using `node quest.js`
