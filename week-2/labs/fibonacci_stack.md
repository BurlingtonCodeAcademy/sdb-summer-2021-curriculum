# Fibonacci Stack

## Welcome!

In this lab we will be building out a program that prints out the first 10 numbers in the fibonacci sequence `0 1 1 2 3 5 8 13 21 34` using an array as a stack. Create a new file called `fib.js`

The fibonacci sequence is the result of adding the first two numbers to generate the third. 0 + 1 = 1; 1 + 1 = 2; 1 + 2 = 3; 2 + 3 = 5; 3 + 5 = 6; and so on, and so forth until infinity.

## Initialize Your Array

The Fibonacci sequence always starts with the numbers "0" and "1" so let's create a starting array *in the global scope* with those two values.

```js
let series = [0, 1];
```

## Repeat Until Complete

Since we want this program to keep building up the array *until it holds 10 values* let's set up a `while` loop with the exit condition being that our `series.length` is greater than 10.

## Take Two Add Three

Inside this loop we'll want the last two items in the array. Two get the last two items in the array we can call `.pop` on the array twice. Assign each call to `.pop` to a variable inside the loop

Since we just popped two items off the array, and we're checking against the length of our array as our loop's exit condition, we'll need to add 3 items back in with `push` otherwise we'll be stuck in an infinite loop.

The three values we want to push back in are the two values we popped out, and the sum of those two values

## Printing the Values

After the loop `console.log` the value of our `series` array. Feel free to mess around with the order you're pushing your values back into the array, and see how the output changes.

## Going Further

- How could we extend this program so it prints the first 100 numbers of the fibonacci sequence?

- How could we print the sequence in a nicer format?

- What if we wanted to allow the *user* do determine how many fibonacci numbers to calculate?
