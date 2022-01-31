# Input and Output

- Computers have many "senses" (ways to take _in_ information).

  - Keyboard, mouse, camera, joystick, etc.
  - Collectively, these are called **input**

- Computers can also express themselves (ways to send _out_ information).

  - Text, graphics, sound, networking, printing, etc.
  - Collectively, these are called **output**.

- Together, they are called **I/O**.

- The CPU and the RAM are the parts of computers that actually do computing.
- All the other parts are technically _I/O_ devices.

---

# Memory vs I/O

- Computers can perform computations and get data from memory within nanoseconds.

- Processing I/O operations, however, takes milliseconds to seconds long.

  - While waiting, Node.js (JavaScript) pauses the program to let the CPU do other tasks.

  - Node.js requires you to define a function to run when the program is ready to move on.

---

# Using I/O Data in the Terminal

Programs in the terminal also have the ability to input and output data.

- To output or display a value, use `console.log();`.

  - e.g. `console.log('Hello world!');`

- To receive input from the terminal, use `process.stdin`:

```js
// Here, we use both together tell the computer, "Show me what input you received."
process.stdin.once("data", (input) => {
  console.log(input.toString());
});
```

[Node.js | process.stdin](https://nodejs.org/api/process.html#processstdin)<br/>[Node.js | emitter.once ](https://nodejs.org/api/events.html#emitteronceeventname-listener)

---

# Using I/O Data in the Terminal Cont.

```js
process.stdin.once("data", (input) => {
  console.log(input.toString());
});
```

<br />
<br />

| JavaScript                        | English                                              |
| --------------------------------- | ---------------------------------------------------- |
| `process.stdin`                   | "Hey terminal input,                                 |
| `.once('data',` ... `)`           | once you get some data...                            |
| `(input)`                         | use it as a parameter called 'input'...              |
| `=>`                              | and send it to this function's block of code...      |
| `{console.log(input.toString())}` | convert it to a string and print it to the terminal" |

---

# Advanced Functions: Event Listeners

`.once` is a special type of function in JavaScript called an _event listener_

Event Listeners are one of the main ways of handling user input for your programs.

- They represent a **function** value that is waiting for something to happen.

- They need to know
  - What they're waiting for: an event with the name **data**
  - What to do _once_ that trigger happens: call a Function with the input String

- This information is provided by you in the form of a _parameter_.

In this case we're waiting for a _data_ event to happen, so we can print what that data is.

---

# Advanced Functions: Callbacks

When an _argument_ is a _function_, we call that argument a **callback function**.

Let's **refactor** (rewrite) the previous example to better see the _callback function_ we pass to `once()`:

```js
// One
process.stdin.once("data", (input) => {
  console.log(input.toString());
});

// Two
function printLine(input) {
  console.log(input.toString());
}

process.stdin.once("data", printLine);
// One and Two do the same thing
```

---

# Advanced Functions: Callbacks Cont.

Here is an example of the syntax:

```js
function useCallback(callback) {
  // calling the function passed as a parameter
  callback();
}

useCallback(function () {
  console.log("Printing to the console from the callback function");
});
```

> Note: Callback functions and regular functions are the same thing. The different terms are for clarity in collaboration.

---

# Advanced Functions: Questions

1. What is the callback function in example Two called?
2. What happens if you omit the `.toString()` call in either example?
3. Is what is printed exactly what is typed? Why or why not?

```js
// One
process.stdin.once("data", (input) => {
  console.log(input.toString());
});
// Two
function printLine(input) {
  console.log(input.toString());
}

process.stdin.once("data", printLine);
```
[Node.js | buffer.toString()](https://nodejs.org/api/buffer.html#buftostringencoding-start-end)<br/>[MDN | String.strip() ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/Trim)

---
