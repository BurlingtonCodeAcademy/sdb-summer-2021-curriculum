# Hello Friend, Go Away Enemy

## Welcome!

The goal of this lab is to write a program that will accept a name as input. If the name is one of a pre-determined list of enemies the program should tell the enemy to go away, otherwise it should greet the person by name.

Start by creating a new file called "hello_frenemy.js"

To run this file in your terminal, `cd` into the directory containing the file, and enter the command `node hello_frenemy.js` to run the file in a NodeJS environment.

## Core Concept: Conditionals

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

## Define the Function

Let's start by defining the function, I'm going to call it `greeter` but you can use any name you want. We'll use this to greet a user by name so it will need to take an argument representing the user's name.

```js
function greeter(name) {
  //The majority of our code will go here
}
```

## Greet a Single Name

Let's start by greeting whatever name is passed to our function. We can reference data that's passed to our function through the parameter variable(s).

In the function definition above we have a single parameter `name` which we could use inside the function to print a greeting

```js
console.log("Hello, " + name + "!")
```

## Speak Friend, and Enter

Greeting people is all well and good, but what if someone *evil* like Voldemort, Sauron, Humperdinck, Moriarty, or Vader came along? We probably wouldn't want to greet them.

Make a conditional statement so that your program tells any of your enemies to "go away!" and greets anyone else by name.

## Try it Out

Run your function in the terminal by calling it, and passing in a name *in your JavaScript file*. If it doesn't work quite right the first time, don't worry! Debugging is a part of the development process! Read any error messages you're getting, add some `console.log`s throughout your program to check that your data is what you think it is, and try and figure out what went wrong.

Try passing in different names, and see how the output changes

## A Solution

Here's one way we could build this program:

```js
function greeter(name) {
    if (name === "Voldemort" || name === "Sauron" || name === "Humperdinck" || name === "Moriarty" ||name === "Vader"){
      console.log("Go, away!")
      process.exit()
    }  else {
      console.log("Hello, " + name + "!")
    }
}

greeter("Bob")
```

## Make it Better

If you want to take this project further try some of the following challenges:

- Capitalize the names when you greet them
- Don't allow enemies to sneak in by using odd capitalization. e.g. "morIARty"
- What if someone enters their full name?
