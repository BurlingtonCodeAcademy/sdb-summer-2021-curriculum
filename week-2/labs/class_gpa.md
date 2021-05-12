# Class GPA

Please create a new file called `gpa.js`, and type in the following code
(which defines a `grades` object and calls a `gpa` function):

```javascript
let grades = {
  midterm: 3.3,
  project: 4.0,
  final: 3.2
}

console.log('The GPA is ' + gpa(grades));
```

In this lab we will be practicing accessing, and using an object's properties by creating a function that takes an object as its argument, and calculates an average GPA based on the values in the object. For now we can assume that the object will only have 3 properties `midterm`, `project`, `final`, the values of which are all numbers, and that all the grades carry equal weight.

## Define the Function

Before we can run this program we'll need to define our `gpa` function. Our function will only expect 1 argument, and it will expect that argument to be an object.

```js
function gpa(object) {

}
```

For now we can assume the properties of that object are `midterm`, `project`, and `final`. Use the `object` to get the average of those three values and `return` it.

Test out the function by running `node gpa.js` in the console.

## Weight the Grades

But what if the grades were not all weighted equally? What if the `final` grade was worth twice as much as the other 2 grades?

Let's change our data structure so that we can add a weight to our grades. To do this we'll change the values of our properties from *numbers* into *objects* each of which will contain a `grade`, and a `weight` property.

Add all the *grades* multiplied by their *weight* together, and then divide by the sum total of the weights to get the weighted average.

## What Keys?

Now I'm going to throw another curve ball at you. You can no longer count on the object being the specific object defined in our program. We need to make a function that can handle *any* object with *any number* of properties.

We can still assume the values of our properties will be objects with `grade` and `weight` properties, but we can no longer assume the top level keys of our object will have the same names

## Object.keys(object)

`Object.keys` is a special method that takes an object as an argument, and returns an array of all the keys on that object. You can *iterate* over this array to access the object *at each key*.

This is a good way of making our programs more flexible so the function isn't tied to a specific object.

## Test It Out

Try defining several different `grades` objects and passing each into your `gpa` function. Run the program, and check your averages.