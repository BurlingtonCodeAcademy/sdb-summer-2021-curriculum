# A Menu Order

## Welcome!

In this lab we will be using an object to represent a restaurant menu, and attaching a method that will take an order and return the price. Create a new file called `order.js`. We will be using the following menu to generate our object:

| Item   | Price |
|--------|-------|
| Burger | $5.00 |
| Fries  | $3.50 |
| Shake  | $1.11 |
| Salad  | $4.25 |

## Define Your Object

Create an object by assigning a variable to an open set of curly braces. Let's name our object `menu` since that's what it represents.

```js
let menu = {

}
```

Add the key/value pairs specified in the menu above with the keys being a lowercase version of the item's name, and the value being the price as a number. Remember keys are separated from their values by colons `:`, and key/value pairs are separated from each other by commas `,` and are usually defined on different lines.

```js
let someObject = {
  stringKey: "value",
  numberKey: 3.57
}
```

## Define a Method

## Accessing `this`

## Try It Out

## Precise Decimals

## Going Further

Use [ARGV]('/lessons/references/argv') to allow the user to input their order through the command line when they run the file. e.g.

```
node order.js burger burger fries shake
```

would print out: `$14.61` and then exit the program.

How else could we accept user input through the command line?
