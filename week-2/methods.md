# Object Instance Methods

A **method** is a *function* attached to an *object* as a *property*. 

We can use objects to represent *things* from real life, 
and we can use their methods to represent *actions* those things can do. 

For example,

```js
dog.speak()
```

---

# You've Already Used Some Methods!

Most things in JavaScript are objects, and many of them have prebuilt methods which we have been utilizing throughout this course.

* `console.log("some message")` `console` is an object, `.log` is a method
* `string.toUpperCase()` strings have a prototype object, that gives them access all the string methods
* `Math.random()` `Math` is a JavaScript class that has a *static method* `.random()`

---

# Code Along: Speaking Dog

Let's set up a simple object, with a method that prints a little message.

* Create an object, and assign it to the variable `dog`
* Give `dog` 3 properties, a `name`, a `color`, and `speak`
  * `name`, and `color` will be strings
  * `speak` will be our method
* When called, `speak` will print `"Bark!"` to the console.

---

# Syntax for Passing Arguments to Methods

Because methods are functions, we use them in the same way.

`objectName.methodName(argument)`

---

# Using Properties

We know we can access values within objects using this syntax:

`objectName.keyName`  

But what if we are still inside the object we are defining? For example,

```js
let human = {
  height: `5'2"`,
  armSpan: /* use height value here */
  noseLength: `3"`,
  earLength: /* use noseLength here */
}
```

---

# `this` Example 

`this` is a magic word that means "this object I'm in *right now*"

```js
let human = {
  height: `5'2"`,
  armSpan: function () { return this.height },
  noseLength: `3"`,
  earLength: function () { return this.noseLength }
}

console.log(human.armSpan)   // `5'2"`
```

---

# `this` Example 2

```js
let rectangle = {
  height: 10,
  width: 8,
  area: function() {
    return this.height * this.width;
  }
}

console.log( rectangle.height )   // 10
console.log( rectangle.area() )   // 80
```

---

# `this` Practice

Let's go back and edit our dog object now to use this skill:

* Where we log `"Bark!"`, change the string to say the *dog's* `name` and `color`.
* Remember to use the `this` key word instead of the object's variable name.

What's the result? Share and compare.

---

# `this` and Binding

The keyword `this` is *bound* to the context in which it is *called*.

Using dot notation to access the method from the object means the context is *that object.*

```js
dog.speak()
//^^^--------------- dog is the context
```

> Note: Arrow functions work differently.

---

# `this` and Binding Cont.

Fat arrow functions `() => { }` bind `this` to the context in which they are *defined*. This can make it easier to know what exactly you're referencing with `this`.

Also remember: "When in doubt, `console.log` it out."

```js
let dog = {
// ^^^--------------- dog is the context
  speak: function () { console.log(`Bark!`) }
}

dog.speak()
```

Understanding the nuance of `this` and binding is not expected right now.

Just be sure `console.log` what `this` is inside your method to be sure of its value.

---

# Adding to the Object After Creating It

We can add methods and properties to objects even after we've already made them.

```js
let rectangle = {
  height: 10,
  width: 8,
}

rectangle.area() //=> TypeError: rectangle.area is not a function

rectangle.area = function() {
  return this.height * this.width;
}

rectangle.area() //=> 80
```

* What is `this` in the above example?
* Does `this.height` on the *inside* of the object mean the same as `rectangle.height` on the *outside*?
