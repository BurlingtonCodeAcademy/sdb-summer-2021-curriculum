# Cake factory

## Welcome!

In this lab we will be creating a class that generates objects that represent cakes! Our cakes will each have 3 properties, the flavor of the cake, the flavor of the frosting, and what (if any) decorations it has. We'll also be attaching a method to the class so that we can print a description of our cake to the terminal. We'll also be creating a factory function that will generate a default cake. Go ahead and create a new file called `cake.js`

## Setting up the Class

The first thing we'll need to do in cake.js is define our class with the `class` keyword, and give it a name. In JavaScript there is a naming convention that class names are always capitalized. While there is nothing in the language that will prevent lowercase class names it will confuse fellow developers, and may even be the wrong color in your text editor depending on what syntax highlighter you're using. Let's call our class `Cake`

```js
class Cake {

}
```

## Construct It

We want our class to have 3 different properties we can dynamically set on objects. To create *instance data* for our objects we'll need to set up a `constructor` method on our class. This special method will be called when we generate a new object and can be used to set the values of the properties on that object. If we ran the following code:

```js
let myCake = new Cake("chocolate", "caramel", "sprinkles")
```

`myCake` would be an object that looks like this:

```js
myCake = {
  flavor: "chocolate",
  icing: "caramel",
  decoration: "sprinkles"
}
```

We can define a `constructor` method as we would define any other method inside the class, but it **must** be called `constructor`. Also, while methods are just functions, they are not defined with the `function` keyword, just name them

Our `constructor` should take three arguments:
- `flavor`
- `icing`
- `decoration`

Inside the constructor we can assign the arguments to the properties on the objects by using the `this` keyword, and the assignment operator. e.g. `this.flavor = flavor`

## Check Your Object

Now that you've got the constructor set up, let's make sure that the objects have the data we expect them to.

Generate a new object by generating a new instance of the `Cake` class. You can use the `new` keyword to trigger the constructor by calling the class, and passing in any arguments it expects:

```js
let myCake = new Cake("chocolate", "caramel", "sprinkles")
```

If you `console.log` the `myCake` variable defined above it should look something like this:

```
{
  flavor: "chocolate",
  icing: "caramel",
  decoration: "sprinkles"
}
```

## Attaching a Method

Let's create a method that will print a nice description of our cake. Let's name the method `describe`, and when you call it, it should print out a string in the format "It is a FLAVOR cake, with ICING frosting, and DECORATION "

* Given the previously created `myCake` object
  * When calling `myCake.describe()`
  * Then you should get "It is a chocolate cake, with caramel frosting, and sprinkles" printed to the console.

Remember you can access the properties on an object, from inside that object, with the `this` keyword

## Cake Factory

a "factory function" is a function that creates new objects from a class. They are often set up to generate a default instance, or allow a broader variety of inputs to generate a previously set up class.

Factory functions are just normal functions that `return` a `new` instance of a class, passing in modified arguments, or a default set of arguments.  Create a factory function that takes no arguments itself, but always returns a default vanilla cake with chocolate icing, and no decorations.

## Test It Out

Generate a few different cakes with different *instance data* as well as a default cake. Call the `.describe` method on each cake. Do you get what you expect?

## Going Further

- What if someone omitted one of the arguments to the constructor?
  - can you supply a default value?
  - can you warn the user if they don't enter anything, or enter something that's not a string?
- Could you add a method that allows you to (virtually) eat a slice of the cake?
  - and changes the description when there are no slices left?