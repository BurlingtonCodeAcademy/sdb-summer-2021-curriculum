# Fibonacci Stack

In this lab we will be building out a program that prints out the first 10 numbers in the [fibonacci sequence](https://en.wikipedia.org/wiki/Fibonacci_number) `0 1 1 2 3 5 8 13 21 34` using an array as a [Stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type)).

The fibonacci sequence is the result of starting with two numbers, zero and one, then adding two numbers to generate the next number in the series.

```js
[0, 1]
0 + 1 = 1

[0, 1, 1]
1 + 1 = 2

[0, 1, 1, 2]
1 + 2 = 3

[0, 1, 1, 2, 3]
2 + 3 = 5

[0, 1, 1, 2, 3, 5]
3 + 5 = 6
```

And so on ... onto infinity.

## Objective

### Learning

In this lab, we will be practicing writing functions using arrays, array methods and loops.

Topics

- Arrays
- `while` loops
- Array methods `.push()`, `.pop()`, and `.length()`

### Achieving

In this lab we will create a piece of software that prints out the first 10 numbers in the Fibonacci sequence `0 1 1 2 3 5 8 13 21 34`.

Your work will result in:

- `fib.js`
- A global variable `series` initialized as an array containing the numbers `0` and `1`
- A `while` loop to hold our logic for adding to the sequence until we reach 10 numbers
- Various array methods to correctly manipulate our array

## Procedure

### Create the `fib.js` file

- [ ] Create a new file named `fib.js` and open it in your editor

### Create the `series` variable

- [ ] Initialize a global variable named `series` and assign it the value of an array containing the first two numbers of the Fibonacci sequence (`0` and `1`).

### Create the `while` loop

- [ ] Set up a `while` loop with the exit condition being that our `series.length` is greater than 10.
- [ ] Within the `while` loop's code block call the `.pop()` method on our array twice and assign each call to `.pop()` to a variable.
- [ ] Within the `while` loop's code block initialize a variable named `sum` which will be the sum of the two values we just popped.
- [ ] Within the `while` loop's code block call the `.push()` method on our array adding back on the two values we popped and their sum.

### Create the `console.log()`

- [ ] After the `while` loop's code block print the value of our `series` array and check that we're getting the Fibonacci sequence

## Review

In this lab, we practiced using arrays, array methods and while loops to write a function which returns the Fibonacci sequence. The software should:

- Begin with an array of 0 and 1.
- Use a `while` loop to continuously manipulate the array using `.push()` and `.pop()`.
- Stop the loop when our array length is greater than 10.
- Print the Fibonacci sequence to the console.

### Going Further

- How could we extend this program so it prints the first 100 numbers of the Fibonacci sequence?
- How could we print the sequence in a nicer format?
- What if we wanted to allow the user do determine how many Fibonacci numbers to calculate?
