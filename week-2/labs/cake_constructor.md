# Cake factory

## Objective

In this lab we will be creating a class that generate objects that each represent a different cake. The cakes will each have three properties, the flavor of the cake, the flavor of the frosting, and what decorations it has, if any.

## Learning

We will create multiple properties and a method on our new class utilizing a class constructor.

Topics:

- Class and class constructor.
- Creating and using class methods.
- Object construction.

### Links

- [MDN Creating Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
- [MDN Class Tutorial](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Classes_in_JavaScript)

## Achieving

In this lab, we will create a piece of software that creates cakes of the `Cake` class. We will utilize our `describe` `Cake` class method to print information about the cakes to the console.

Your work will result in:

- The `cake.js`file.
- `Cake` class and constructor.
- `describe` `Cake` class method.
- Three new `Cake` objects.
- Multiple invocations of our `describe` method to print information about the cakes to the console.

## Procedure

### Create the `cake.js` file

- [ ] Create a new file named `cake.js` and open it in your editor.

### Construct the `Cake` class

- [ ] Define a class named `Cake`
- [ ] Within Cake's code block, create a constructor that takes `flavor`, `icing`, and `decoration` as its arguments.
- [ ] Within the constructor's code block, map: `this.flavor` to `flavor`, `this.icing` to `icing`, and `this.decoration` to `decoration`.

### Create the `describe` `Cake` class method

- [ ] Outside of the constructor's code block but within the `Cake` class, create a `describe` method.
- [ ] `describe` should contain a console log that utilizes `flavor`, `icing`, and `decoration`, in a description of the cake.

### Define three new `Cake` class objects

- [ ] Create three new Cake objects. Their name and their property values passed to the constructor are your choice, but they should correlate with the keys of the properties (`flavor`, `icing`, `decoration`).

### Invoke the `describe`method

- [ ] Invoke the `describe` method on all three of your new cakes.

## Review

In this lab, we created the `Cake` class and constructor that creates Objects with multiple properties and a method. The software should:

- Have multiple new Objects of the `Cake` class that print their description to the terminal when the software is run.
- The description should utilize `flavor`, `icing`, and `decoration`.

## Going Further

- Create the `eat` method that accepts the `slice` parameter. Print to the console a description that utilizes `flavor` and `slice`. Invoke `eat` beneath the invocations of `describe`.
- What if not every cake had all three properties? Set up error handling to have default values when the values are not given to the constructor and/or method.
