# Capitalize

## Welcome!

In this lab we will be writing a function that takes a string as an argument, and returns a capitalized version of that string.

But before we dig into the lab, let's talk a little bit about strings and functions.

## Strings

Strings are one of the six primitive data types in JavaScript. Take a moment to look back at the "Playing With Strings" lab, and re-familiarize yourself with some of the basic concepts of strings.

Remember:

- You can access individual characters in a string by their *index number*
- Strings have many methods available to them. If you need part of a string you can use the `.slice` method
- Strings are *immutable* so any operation that changes a string will return a **new** string, not modify the existing string.

## Functions

Functions are a way of *encapsulating* sections of code. Calling a function will run the code that is written in the body of the function's definition.

Parameters are used to define the *input* of a function, while the *return statement* specifies the output

```js
function functionName(parameter) {
  //This is the body of the function
  //any actions you want the function to take should be defined here
  return someValue //The result of running the function, expressions will be evaluated before being returned
}

functionName(32) //You call a function by its name followed by open and closed parentheses
//You pass arguments to the function in the parentheses
//Arguments become the values of the parameters
//Not all functions take arguments
```

## Defining the Function

Before building out the functionality we must first define the function.

- Define your function by using the `function` keyword, and giving your function a name
  - The name doesn't matter to the computer, it's just a variable, but it does matter to our human brains. We want it to represent what the function does. Let's name our function "capitalize"
- This function will also take a single argument, so let's define a parameter between the parentheses of your function definition
  - Parameters, like function names, are variables. Let's call this parameter "string" since that's the datatype our function will expect.
- The last part of the function we have to define is the *body.* This is the code that lives between the curly braces of the function definition. For now let's just return the variable `string`

```js
function capitalize(string) {
  return string
}
```

## Test the Function

Let's make sure our function is set up correctly by calling it, and `console.log`ing the result

```js
console.log(capitalize("cheese"))
```

When you add the above line of code, and run the program through the terminal using the command `node capitalize.js` (assuming your file is named "capitalize.js" and you're in the correct directory in the terminal, you should see the output: `"cheese"`

## Setting up Intermediate Variables

So far so good, but we want to do a little more than just echo back the input to the user.  Our goal here is to print out a capitalized version of the input string.

```js
capitalize("cheese")
capitalize("CHEESE")
capitalize("cHEeSe")
capitalize("cheesE")
```

The above function calls should all return the same value: `"Cheese"`

To make this work we will need to pull the word apart, put each part in the correct case, and then put the word back together

Let's assign the different parts of the word to intermediate variables.

- assign the first letter of the parameter `string` to a variable *inside* the body of the function. Let's call it `firstLetter`
- assign the rest of the word to a different variable *inside* the body of the function. Let's call it `restOfWord`

Remember:

- Strings are 0 indexed, meaning the first character is at position 0
- You can `.slice` from a specific index until the end of a word by only giving the `.slice` method one argument
  - e.g. `word.slice(4)` will give you back a string from the 5th letter until the end of the string represented by the variable `word`

## Check the Data

One of the most common causes of errors in programming is the programmer assuming the data is a different shape than it actually is. Go ahead and `console.log` the `firstLetter` and also `console.log` the `restOfWord` variable inside the function.

If you're calling the function, and passing in the string "cheese" the `firstLetter` should be "c" and `restOfWord` should be "heese"

## Return the Value

For the final output we want to return the word with the first letter capitalized, and the rest of the word lower cased.

- capitalize `firstLetter`
- lowercase `restOfWord`
- add `firstLetter` and `restOfWord` together
- return the new string

## Print the Output

To print the output of the program call it from inside a `console.log` just like we did to test that the function runs in the "Test the Function" step

Remove the intermediate `console.log`s for `firstLetter` and `restOfWord` for cleaner output.

## Run the Program

At this point you should have a function that should be able to capitalize any word. Here's one way it could be written:

```js
function capitalize(string) {
  let firstLetter = string[0]

  let restOfWord = string.slice(1)

  return firstLetter.toUpperCase() + restOfWord.toLowerCase()
}

console.log(capitalize("cheese")) // => should print out "Cheese"
```

If your function doesn't look exactly like this don't worry! There's always more than one way to solve any problem with programming. Try running your program in the terminal, if it works it's correct.
