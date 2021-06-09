# Input and Output

* Computers have many senses -- keyboard, mouse, network card, camera, joystick, etc. Collectively, these are called **INPUT**.

* Computers can also express themselves in many ways -- text, graphics, sound, networking, printing, etc. Collectively, these are called **OUTPUT**.

* Input and Output together are called **I/O**.

* the only part of your laptop that is *really* a computer is the CPU and the RAM; all the other parts (keyboard, trackpad, display, disk drive, etc.) are technically I/O devices 

---

# Memory vs I/O

* Performing *calculations* and accessing *memory* is **very fast**
* ...but reading and writing to I/O devices is **slow**
    * (at least as far as the CPU is concerned)
    * I/O operations can take *seconds* or *milliseconds*; CPU operations take *nanoseconds*
* Every time you ask JavaScript to do an I/O operation, it *pauses your program*
  * this allows the CPU to spend time doing other things, not just sitting idle waiting for a key to be pressed or a file to be written
* In NodeJS, you have to write a function for JavaScript to run once it *resumes*
    * this function is named an *asynchronous callback*
    * *asynchronous* is Greek for "out of time" or "not together in time"

---

# Terminal I/O

* In JavaScript,
    * `console.log` means "print a line to the terminal"

* In NodeJS,
    * `process.stdin` means "input coming from the terminal"

    * Reading a line in NodeJS is **weird**; here's one way to do it

```js
process.stdin.once('data', (chunk) => {
  console.log(chunk.toString()) 
})
```

---

# node load code, decoded

Let's break down the code we just wrote

```js
process.stdin.once('data', (chunk) => {
  console.log(chunk.toString()) 
})
```

> `once` is a special type of function, called an event listener, that takes two parameters,
> and its second parameter is **another function**

* `process.stdin` means "hey terminal input," 
* `.once('data',` ... `)`   when you get some data, 
* `(chunk)`               please name it `chunk` 
* ` => ` and send it to this block of code `{console.log(chunk.toString())}`
* which says "convert it to a string and print it to the terminal"

---

# Event Listeners

`.once` is a special type of function in JavaScript called an *event listener*

Event Listeners are one of the main ways of handling user input for your programs. They:

* are attached to a specific element, or interface
  * In this case the terminal
* wait for a specific type of interaction or event
  * represented by the first argument to the function
  * In this case a *data entry* event
* run a function, that is supplied as the second argument to the event listener

---

# Welcome to Callback City!

The previous one-liner code is equivalent to this:

```js
function printLine(chunk) { 
    console.log(chunk) 
}
process.stdin.once('data', printLine);
```

The `printLine` function itself is called a *callback* 
(since you are asking the I/O device to *call you back* when it receives input).

---

# Callbacks, the Original Async

Callback functions are the original way of handling asynchronous programming in JavaScript.

Callback functions take the responsibility of calling the function away from the programmer and puts it on another function. This allows your program to call that callback function *when it's needed*

Functions that take callbacks can look confusing, but at their core all they're doing is this:

```js
function takesACallback(callback) {
  callback()
}
```

---

# Code Along: Madlibs

Let's create a Madlib template! The goal for this program is to ask for certain types of words (noun, verb, adjective, etc.) and once it has recieved a certain number of inputs it will insert those words, in the correct places, into a story which your computer will print to the terminal. We're going to:

* create a story with at least five words omitted (it does not have to be a long story ~1 paragraph)
* set up a function that asks for input for each of the omitted words
* print the story to the console, filling in the blanks with the provided words.
