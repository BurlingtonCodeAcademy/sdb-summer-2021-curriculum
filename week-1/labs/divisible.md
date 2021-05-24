# Divisible

## Welcome!

The goal for this lab is to create a function that takes two numbers, and returns the boolean `true` if the first number is evenly divisible by the second, and `false` if they are not evenly divisible. Go ahead and create a file names "divisible.js"

## Define the Function

The first step when building a function is always to define the function. Let's call this one "divisible." It expects 2 arguments, the dividend, and the divisor so let's use those as the names for our parameters.

```js
function divisible(dividend, divisor) {

}
```

If we were to call this function, and `console.log` the results, we would get `undefined` printed to the console because there is currently no return value.

```js
console.log(divisible(25, 5))
```

## The Modulus Operator 

In JavaScript the `%` symbol is referred to as the modulus operator. The modulus operator tells you what the remainder is of dividing the two numbers. If the remainder is 0 the numbers are evenly divisible.

Use the modulus operator to get the remainder of your dividend and divisor, and assign the result to a variable.

`console.log` the remainder so that you can make sure it is what you expect it to be

```js
let remainder = dividend % divisor

console.log(remainder)
```

## Booleans

Ultimately we will want to return a boolean `true` or `false` from this function.

For now let's just have the function always return `true`

## Branching Logic

We can have the function return different values under different circumstances by having some logical statements that return different results.

Directly above your return statement add an `if` statement. If the remainder is not `0` return `false`

> Remember all numbers are *truthy* except 0

## Returning an Expression

We can also return the result of an expression by returning the expression itself. This can allow us to write extremely concise code, such as the last example below, but there is always a trade off.

THe more concise something is, the less readable it is. You should write functions in a way that makes sense to you. Try to find the balance between readable, and concise code that works best for you.

## One Problem, Many Solutions

There are always multiple ways to solve any problem. Here are a few different examples of ways we could define the `divisible` function:

```js
function divisible(dividend, divisor) {
  let remainder = dividend % divisor
  if(remainder) {
    return false
  }

  return true
}

```

```js
function divisible(dividend, divisor) {
  let remainder = dividend % divisor
  if(remainder === 0) {
    return true
  } else {
    return false
  }
}

```

```js
function divisible(dividend, divisor) {
  let division = dividend / divisor
  if(division === Math.floor(division)) {
    return true
  } else {
    return false
  }
  
}

```

```js
function divisible(dividend, divisor) {
  return ! dividend % divisor
}

```

Which of these makes the most sense to you?
Can you think of another way we could solve this problem?
