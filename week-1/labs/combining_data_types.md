# Combining Data Types

## Welcome!

There are six basic data types in JavaScript. So far you've worked a bit with two of the most common data types: strings, and numbers. In JavaScript you can also perform operations on multiple data types at once, though the results aren't always what you expect!

Open your terminal, and enter a node environment with the `node` command. Try to figure out the answers to the following questions by experimenting with different operations in the terminal.

You can always check what the data type of a value is be using the `typeof` keyword.

`typeof 42` would return `"number"`

`typeof 1 + 7` would also return `"number"`

## Addition

The addition operator `+` is very flexible. It can be used to add any two values together, and those values can be of any type, or even different types. Let's see what happens when you add different types of data together.

### With Numbers

- What do you get when you add the string `"cheese"` to the number `42`?
- What do you get when you add the string `"4"` and the number `2`?
- What is the data type of the result when you add a number to a string?

### With Booleans

- What do you get when you add the string `"pie"` to the boolean `true`?
- What do you get when you add the boolean `false` to the number `8`?
  - What if you add `true` instead?
- What is `true` evaluated as when you use it in a mathematical operation?
  - What about `false`?
  - What data type do you get back when you add a string to a boolean?

### With Null Values

In JavaScript there are several null values, also called "empty values" that represent the concept of nothing. We'll be focusing on two of them here: `null` and `undefined`

- What happens when you add `null` to the number `7`?
  - What about `undefined`?
- What do you get when you add `null` to the string `"cat"`?
  - What about `undefined`?

## Subtraction

The addition operator in JavaScript is very flexible. It can be used on any data types in JavaScript, and will do it's best to add them together, though the result might not be what you expect! Let's play around with some different operations.

- What do you get when you subtract a string from a number?
- What do you get when you subtract the boolean `true` from the number `17`?
  - What about `false`?

## Other Arithmetic Operators

- What happens when you try to use strings with other arithmetic operators?
  - division?
  - multiplication?
  - modulus?
- What about booleans?
- What happens when you perform operations with `null` as part of them?
