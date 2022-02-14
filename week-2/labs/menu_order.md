# Menu Order

## Objective

In this lab we will be using an object to represent a restaurant menu, and attaching a method that will take an human user's order and return the total price of items within the order.

We will be represent the following menu within an object:

| Item   | Price |
|--------|-------|
| Burger | $5.00 |
| Fries  | $3.50 |
| Shake  | $1.11 |
| Salad  | $4.25 |

## Learning

In this lab, we will be practicing creating an Object with an attached method. We will also practice with the `for...let` iteration syntax.

Topics:

- Objects.
- Object methods.
- `for...let` Array iteration.

## Achieving

In this lab, we will be creating a piece of software that contains a `menu` object with a `order` method. `order` should print the sum total of our order to the console.

Your work will result in:

- A file named `order.js`.
- Within the `order.js` file, a `menu` Object with `order` method.
- The usage of `for...let` Iteration inside of `order` that prints our order's sum to the console.

## Procedure

### Create an `order.js` file

- [ ] Create a file named `order.js` and open it in your editor.

### Create a `menu` Object

- [ ] Create an Object named `menu`.
- [ ] Inside of `menu`, we will need a series of `key: value` pairs that represent the items on the menu and their cost.
- [ ] _Hint:_ `burger: 5.55`
- [ ] Have at least four entries to represent four different items on your menu. Each should have a different price.

### Create an `order` Method on the `menu` Object

- [ ] After the initial `key: value` pairs inside of `menu`, create a method named `order`.
- [ ] Hint: The key is `order` and the value is the function the method will run.
- [ ] `order`'s anonymous function should take the parameter `orderPlaced`.

### Build the method `order`

- [ ] The `orderPlaced` will be coming in as a String of multiple items. Create a function `orderSplit` to hold the result of splitting `orderPlaced` into an Array with each item its own index.
- [ ] Create a `sum` variable to contain our order sum, starting at `0`.
- [ ] Set up a `for...let` iteration loop. It will need to iterate over every `item` of `orderSplit`.
- [ ] Within the code block of the `for...let` loop, reassign `sum` to be `sum` plus the cost of the item.
- [ ] After the loop completes, print the `sum` variable.

### Call the method `menu.order()`

- [ ] Invoke `order` on menu multiple times, passing in different combinations of menu items to see differing results printed to the console.

## Review

In this lab, we created the `menu` Object that contains multiple menu items and the `order` method to sum up any orders placed to the menu. The software should:

- Be able to print the sum of an order to the console. An order is a String passed as an argument to `menu.order()` that contains multiple items that correlate to keys within the `menu` object.

## Going Further

- What if an order is placed that contains an item not on the menu? Create error handling for this scenario.
