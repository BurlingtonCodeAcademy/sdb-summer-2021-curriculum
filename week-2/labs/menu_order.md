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

Let's create a method called `order` on our `menu` object that will take a single array as its argument. This array will be used to pass in an order, and then we will return the total price of the order.

Methods are just *functions attached to objects* and can be defined like any other property on an object. The key is the name of the method, and value of the property is just a function. e.g.

```js
let someObject = {
  stringKey: "value",
  numberKey: 3.57,
  someMethod: function(argument) {

  }
}
```

`someObject` now has a method named `someMethod` attached to it.

## Accessing `this`

To access properties on the object the method is defined in we can use the `this` keyword to reference the object, and then square bracket, or dot notation to access the properties we need.

In the case of this program the "properties we need" will be coming into the method as an array of values, so we will need to iterate over the array, and tracking the sum total of the values for our order.

Remember, when using a variable as a key you **have to use square bracket notation**

## Try It Out

Test out your method by calling it, and `console.log`ing the results. Try passing in a few different orders to make sure it's operating as expected.

## Precise Decimals

When getting a total price for something the number is almost always presented with two decimal places representing te cents. Let's add that bit of functionality to our program.

Take a look at the documentation for the methods on [numbers](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number) to find out how to do this.

## Going Further

Use [ARGV]('/lessons/references/argv') to allow the user to input their order through the command line when they run the file. e.g.

```
node order.js burger burger fries shake
```

would print out: `$14.61` and then exit the program.

How else could we accept user input through the command line?
