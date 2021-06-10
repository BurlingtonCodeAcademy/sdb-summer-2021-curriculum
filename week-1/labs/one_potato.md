# Potato Poem

## Welcome!

The purpose of this lab is to build a program that uses loops to print the following poem:

1 potato,

2 potato,

3 potato,

4!

5 potato,

6 potato,

7 potato,

More!

Create a new file called `potato.js`. We will be defining a function that will print this poem for us.

To run this file in your terminal, `cd` into the directory containing the file, and enter the command `node potato.js` to run the file in a NodeJS environment.

## Looking at Loops

Loops are a powerful tool in your toolbox as a developer. They allow you to repeat the same block of code over, and over until some condition is met.

There are several ways to create a loop in JavaScript, `while` loops are arguably the most common, but there are also more specialized loops, such as the `for...of` and `for...in` loops, and other ways to create a loop, such as recursion.

Regardless of the type of loop you're using there are a few things to keep in mind:

- loops create a new scope, so any variables defined inside the loop will be inaccessible outside the loop.
- loops should have an exit condition. `for` loops have an implicit exit condition. `while` loops will end if their check evaluates `false`
  - Most types of loops can also be stopped with the `break` keyword

## Building a Counter

At its heart this program is a counting function. It counts from 1 to 8, and prints the correct poem line for the number. Let's start by defining a function, I'm going to call it "potato." Since this function doesn't respond to input we don't need to define any parameters on it.

```js
function potato() {

}
```

Next, let's create a counting loop inside the `potato` function.

- Above the loop set up a variable to check against e.g. `let count = 0`
- Below that initial variable set up a `while` loop that will run until that variable (`count`) is greater than 8 `while(count < 8)`
- Inside the loop increment the value of count by 1 each time you go through `count = count + 1`

## When in Doubt, console.log it out!

It can be difficult to visualize what is happening inside a loop while it's running.  Let's make sure `count` is what we think it is each time through the loop. `console.log` the `count` variable inside the loop to get its value printed to the terminal.

- What's the value of `count` on the first run through oof the loop?
- What about the last run through?
  - Are these the numbers you expect `count` to be?
- Try `console.log`ing `count` both above, and below the reassignment.
  - How does moving the `console.log` effect the value of `count`?
  - To count from 1 to 8 do we need to change our `while` check?
    - If so, how should it change?
    - If no, where should we define the logic for dealing with `count`?

## Dealing with Edge Cases

When we have certain conditions that need *different* actions than the ones you want to take for most cases they are called "edge cases." In this program we have 2 *edge cases*

- When `count` is 4 we want to print the count and an exclamation point: `4!`
- When count is 8 we want to print `More!`

It's often easiest to deal with edge cases first, so write an `if...else if` to deal with the edge cases for this program.

> Keep the `console.log` of `count` for now! It's still useful!

## Dealing with the Base Case

Now that we've dealt with the edge cases let's deal with the standard action (a.k.a. the base case, a.k.a. the happy path)

Add an `else` block to the end of your `if...else if` conditional. The `else` block will handle any cases not defined above it in an `if` or `else if` block. Note that an `else` block doesn't have a check, it just handles everything else!

## Running the Program

Remember, there's always more than one solution to any problem! Don't get fixated on finding the One Right Answer, because there is **no** One Right Answer. Remove the `console.log` of `count` and run your program.

At this point your program might look something like the code block below. Don't worry if it doesn't! If it works (or is close to working) then your code is correct! Don't change it just to match the example solution!

```js
function potato() {
  let count = 0

  while(count < 8) {
    count = count + 1

    if(count === 8) {
      console.log("More!")
    } else if (count === 4) {
      console.log("4!")
    } else {
      console.log(count + " potato,")
    }
  }
}

potato()
```
