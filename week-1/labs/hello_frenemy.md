# Hello Friend, Go Away Enemy

## Welcome!

The goal of this lab is to write a program that will accept a name as input from the user through the command line. If the name is one of a pre-determined list of enemies the program should tell the enemy to go away, otherwise it should greet the person by name, and ask for another name, until an enemy name is entered or the user says their name is "bye!"

Start by creating a new file called "hello_frenemy.js"

To run this file in your terminal, `cd` into the directory containing the file, and enter the command `node hello_frenemy.js` to run the file in a NodeJS environment.

## Core Concepts:

### Input/Output

Input is the way we interact with our computer, and output is the way it responds to us.

In this lab we will be using the terminal for both input and output. Our goal is to write a program that responds to what we type into the terminal. To do this the program needs to be able to respond asynchronously to our inputs. For now, we're going to use event listeners, and callback functions to do that. However later today we will be learning about some techniques that will make this process significantly easier!

### Conditionals

For this lab we'll want to take certain actions under certain conditions. We'll want to greet most names, but tell others to go away, as well as a special condition that will end the program.

Setting up a huge block of `if...else if...else` is one way you could go about this, however it would be very verbose, and lead to you typing a lot of extra characters.

You will probably need some conditional statements, but you can make your code more concise by using the logical operators to combine multiple checks into a single `if` statement.

The "or" operator `||` allows you to set up multiple conditional statements. If any of them are true the whole the whole statement evaluates `true`.

For example:

```js
if (name === "Picard" || name === "Kirk") {
  console.log("Hello, Captain!");
}
```

would print `"Hello, Captain!"` to the console if the variable `name` had the value `"Picard"` **or** the value `"Kirk"`.

Note that you do need the full comparison on each side of the logical "or" operator. The expression:

```js
name === "Picard" || "Kirk";
```

would always evaluate `true` because `"Kirk"` is a string, and all strings (except empty strings) are truthy. Because one part of the larger logical expression is truthy the whole thing is `true`.

## Break Down the Problem

We want to build a function that does several different things. It accepts input, in the form of typed names, and determines a response to give, then it asks again, until certain exit conditions are reached.

When building a larger function, or program it can be overwhelming to try and think about the whole process at once. Try to break the program down into small, actionable steps, and complete each step in turn.

Let's start by defining the function, I'm going to call it `greeter` but you can use any name you want. We'll use this to deal with any user input so it will need to take in the user input as an argument.

We're also going to be dealing with user input so we will need to set up an event listener on our terminal that listens for a data entry event. Our terminal is our standard input device, and we can reference it with `process.stdin` and we can use it to listen for input by setting up an *event listener method*

```js
function greeter(name) {
  //We'll be writing the majority of our code here
}

process.stdin.once('data', function (data){})
```

`process.stdin.once` is our `event listener` while the string `'data'` represents the type of event we're listening for, and the anonymous callback function will be called when the event is triggered.

## Greet a Single Name

Let's start by greeting a single name. We'll first need to ask a user for their name. Since the computer doesn't know exactly when the user will type their name in we'll need to use a the *callback function* in our event listener to call our `greeter` function, and pass in the name

```js
console.log("Who are you?")

process.stdin.once('data', (data) => {
  greeter(data)
})
```

We can then use the variable defined as the parameter to `greeter` to craft a custom response for the user.

```js
console.log("Hello, " + name + "!");
```

## Speak Friend, and Enter

Greeting people is all well and good, but what if someone _evil_ like Voldemort, Sauron, Humperdinck, Moriarty, or Vader came along? We probably wouldn't want to greet them.

Make a conditional statement so that your program tells any of your enemies to "go away!" and greets anyone else by name.

## When in Doubt `console.log` it Out

If you run into any bugs a `console.log` is quite useful for making sure variables are actually what you expect them to be, or you are getting into a certain logic block. Use `console.log`s liberally, but remember to clean them up after you've built the program to avoid spurious outputs.

## Repeat Until Complete

We want our program to ask for names, until we tell it to stop. We could nest a ton of conditionals inside each other and hope our user gets bored and goes away before they hit the end of our logic chain, but that sounds highly inefficient and extremely tedious so let's just change our event listener from `.once` to `.on`. Now it will call our function on _every_ data entry event, rather than just the first one

## Try it Out

Run your function and try it out. If it doesn't work quite right the first time, don't worry! Debugging is a part of the development process. Read any error messages you're getting, add in some `console.log`s to check your data, and try and figure out what went wrong.

Here's one way we could build this program:

```js
function greeter(name) {
    if (name === "Voldemort" || name === "Sauron" || name === "Humperdinck" || name === "Moriarty" ||name === "Vader"){
      consolo.log("Go, away!")
      process.exit()
    } else if(name === "bye!") {
      console.log("Goodbye!")
      process.exit()
    } else {
      console.log("Hello, " + name.trim() + "!")
    }
}

console.log("Who are you?")

process.stdin.on('data' function(data) {
  greeter(data)
  console.log("Who are you?")
})
```

## Make it Better

If you want to take this project further try some of the following challenges:

- Capitalize the names when you greet them
- Don't allow enemies to sneak in by using odd capitalization. e.g. "morIARty"
- What if someone enters their full name?
