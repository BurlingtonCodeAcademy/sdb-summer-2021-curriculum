# Hello Friend, Go Away Enemy

# Objective

## Learning

In this lab, we will be playing with I/O (input/output). We will be utilizing the Node `process.stdin` property and its `.on` event listener to do so. We will also gain further practice with Boolean operators and conditional statements.

Topics:

- I/O (input/output)
- The Node `process.stdin` property and its `.on` event listener.
- Boolean operators.
- Conditional statements.

## Achieving

In this lab, we will be extending our [Hello Frenemy](https://online.uprighted.com/lessons/lab/hello-frenemy) software. We should achieve a terminal program that waits for user input AND outputs a response to the terminal based on that input.

Your work will result in:

- A file named `helloFrenemyInput.js`
- Within `helloFrenemyInput.js`, a function named `greeter` to handle our greeting logic.
- Within `helloFrenemyInput.js`, a console log that prompts the user "Who are you?"
- Within `helloFrenemyInput.js`, a call to our input device `process.stdin` and a `.on` event listener appended to it.
- Within `process.stdin.on`, a call to `greeter` passing in `data`.
- A program that handles user input and outputs the "correct" response.

# Procedure

## Creating the `helloFrenemyInput.js` file

- [ ] Navigate to your `code` folder in the command line.
- [ ] Use the command `mkdir` to create a new subfolder named `hello-frenemy-input`.
- [ ] `cd` into `hello-frenemy-input`.
- [ ] Use the command `touch` to create a new file named `helloFrenemyInput.js`
- [ ] Open `helloFrenemyInput.js` in your editor.

## Creating the `greeter` function

- [ ] Reference either the [Hello Frenemy](https://online.uprighted.com/lessons/lab/hello-frenemy) instructions or your previously created `helloFrenemy.js` for how to set up the `greeter` function.

## Printing "Who are you?" to the console
- [ ] After `greeter`, place a log that asks the user "Who are you?".

## Creating the `process.stdin.on` property with event listener

- [ ] Within `helloFrenemyInput.js` (but below `greeter`), declare a call to our terminal's input with `process.stdin`.
- [ ] At the end of `process.stdin`, attach the event listener `.on`.
- [ ] Invoke `.on` with parentheses; inside of the parentheses, first: inform the event listener of what we are listening for, 'data'. Second: pass in an anonymous callback function to trigger when the event occurs.
- [ ] Within the callback function's code block, invoke `greeter` and pass in our `data`.
- [ ] On the end of `data`, first call the `.toString()` method to ensure it is a String data type.
- [ ] After `.toString()`, chain `.trim()`. 
- [ ] Add another log to again prompt the user who they are.

# Review

In this lab, we should have increased the complexity of our `Hello Frenemy` software to now utilize I/O (input/output). The software should:

- Accept the user's name input into the terminal and output the correct response based on whether or not they: are a friend, are an enemy, or are saying "bye!".

## Going Further

- Did you complete Going Further on the original [Hello Frenemy](https://online.uprighted.com/lessons/lab/hello-frenemy)?
- Inform users of the "bye!" command to exit the program.
- Continue the conversation. What if the program followed up with "How are you?"
