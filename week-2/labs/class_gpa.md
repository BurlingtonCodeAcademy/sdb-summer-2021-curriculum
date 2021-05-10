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

## What Keys?

## Object.keys()

## Test It Out