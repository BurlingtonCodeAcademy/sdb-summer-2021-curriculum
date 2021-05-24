# Playing With Numbers

## Welcome!

Numbers are one of the 6 JavaScript primitive types, and are very useful in programming. In general computers understand, and deal with numbers much more cleanly than the do words because to a computer *everything* is represented as numbers.

Open your terminal, and enter a Node environment with the `node` command

## Watch Out for the Holes!

In JavaScript there is only one data type for all numbers. Because there is only a limited amount of room to store an infinite amount of combinations there are a few holes in JavaScript's number system. Try the following operations, and see what you get:

- `0.1 + 0.2`
- `2**53 === 2**53 + 1`
- `(0.8 - 0.7 - 0.1)/(0.5 - 0.4 - 0.1)`
- `0.5 - 0.4 - 0.1`
- `2**10000`

## Arithmetic Operators

In JavaScript we've got all the usual suspects for arithmetic operators:

- addition `+`
- subtraction `-`
- multiplication `*`
- division `/`
- modulus`%`
- exponent `**`

Go ahead and try and use each of these in an operation.

- Were the results what you expected?
- Can we build more complex operations using multiple operators?
- Does JavaScript follow order of operations (PEMDAS)?

## Integers and Decimals

JavaScript makes no distinctions between integers, and decimals.

Does anything odd happen when you mix decimals, and integers in a single operation?

## The Math Class

As well as arithmetic operators JavaSCript also has a `Math` class that contains many useful methods we can use to make math a bit easier. More on classes, constructors, and methods later. For now just know that a method is just a function, but it's attached to some object, and must be called through it.

We could use a method like so:

```js
Math.floor(42.4576)
```

## Math Methods

There are many methods on the `Math` class. Try out a few of the operations listed below and see what you get

- `Math.floor(42.3675)`
- `Math.floor(42)`
- `Math.round(41.756)`
- `Math.round(42.3675)`
- `Math.random()` (try this one a few times)

There are also many methods for more complex operations. For a complete list you can check [the MDN page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)

## Generating a Random Number

We can use our `Math` methods, and our arithmetic operators together to create more powerful functions.

The function defined below can generate a random integer within a range. We'll be covering functions in much more depth in a little bit. For now feel free to type the function definition below into your terminal *exactly as it appears*

```js
function randomNum(min, max) {
  let range = max - min + 1

  return Math.floor(Math.random() * range) + min
}
```

`Math.random()` returns a number between 0 and 1 *inclusive* on the low end, but *exclusive* on the high end. So when we generate the range we have to add 1 to it ot bring our upper bound back in. We multiply that range by `Math.random()` to give us a random number. Then we `Math.floor` that equation to remove the decimal points, and get an integer between 0 and th range. Finally we add the minimum value back on so that it's a random number between the `max` and `min` values.

After it's been defined the function can be used like so:

```js
randomNum(1, 10) // will return a random number between 1 and 10 inclusive on both ends
```