# Promises

When learning about _I/O_, we learned that JavaScript tells the computer to stop one task in order to complete another.

When something is **asynchronous**, it doesn't happen in realtime. We have to wait, and we often have to wait for software we don't own or control. There's a chance that software doesn't even succeed in completing its programs.

To deal with this uncertainty, we make a **Promise**, a built-in tool in JavaScript.

- Just like in real life, a Promise is not a guarantee.
- It means the what we're waiting for may never happen.
- If it does, a Promise will tell us that it was **resolved**.
- If it does not, a Promise will tell us that it was **rejected**.

[Mozilla Developer Network | Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

---

# Keywords for Promises: async await

We can give any `function` the ability to wait for a Promise (wait for data to finish being sent to us)

- Any function can be made into an async function by putting the `async` keyweord in front of the function definition
  - `async function waitsForSomething(){...}`
- When using `async` and `await`:
  - `await` means "wait for the following thing to happen"
  - when you use `await` inside a function, you must use `async` to define that function
- Async functions make it so we don't have to use callback functions

Note: `async` functions don't work in loops! There are other ways to execute asynchronous functions multiple times in a row if needed.

---

# async await Syntax

The format when using async await is one of the exceptions we discussed in the _statements_ lesson:

- `async`: `async function functionName () {}`
  - Give the function ability to handle waiting
- `await`: `await functionName();`
  - Tell the function when calling it that it will need to wait

```js
async function getDataFromInternet() {
  // some code that asks the internet for data
  return (/* whatever that data is */)
}

await getDataFromInternet();
```

---

# readline

- Node.js is more than a _JavaScript interpreter_
- It's also a collection of _JavaScript libraries_
- One of the libraries is called `readline`
  - `readline` makes it easier to read lines, naturally :-)
  - the "books" in this library are functions
    - (and classes and other things too)

---

# Using readline

> Note: This includes unfamiliar concepts! Don't worry if it doesn't make much sense yet.

To use `readline`, include the following lines in the top of your source file:

```javascript
const readline = require("readline");
const readlineInterface = readline.createInterface(
  process.stdin,
  process.stdout
);

function ask(questionText) {
  return new Promise((resolve, reject) => {
    readlineInterface.question(questionText, resolve);
  });
}
```

---

# Using readline Cont.

| code                                                        | explanation                                                                                                                                                                            |
| ----------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `const readline = require('readline');`                     | load the `readline` package and name it `readline`                                                                                                                                     |
| `const readlineInterface = readline.createInterface({...})` | create an _interface_ to readline using the following settings:                                                                                                                        |
| ` process.stdin,`                                           | for input, use the _standard input stream_ (i.e. terminal keyboard input)                                                                                                              |
| ` process.stdout`                                           | for output, use the _standard output stream_ (i.e. terminal console output)                                                                                                            |
| `function ask(questionText) {...}`                          | a function named _ask_ that uses the [Promise API](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises) to asynchronously ask a question and wait for a reply |

---
