# Object Instance Methods

A method is a *function* attached to an *object* as a *property*. One of the main benefits of using objects is to create a predictable abstraction. Since objects maintain their own state, and behavior we can 

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
* When called `speak` will print `"Bark!"` to the console

---

# Passing Arguments to Methods

Since methods are just functions we can pass them arguments in the exact same way.

Just pass the argument between the parentheses of the method call as you would for any function

---

# Using Properties

We can access and use our object's properties from inside itself using dot or square bracket notation as we would to access properties from outside the object

While we can call the object by name from inside itself it's not an ideal pattern

* It looks sloppy
* It doesn't preserve encapsulation
* It makes it easier to introduce bugs into your program

It's better to use the keyword `this` to access the object your method's attached to.

---

# Methods Can Access Object State

`this` is a magic word that means "this object I'm in *right now*"

```js
let rectangle = {
  height: 10,
  width: 8,
  area: function() {
    return this.height * this.width;
  }
}

rectangle.height   //=> 10
rectangle.area()   //=> 80
```

---

# Using `this`

Let's go back to our `dog` object and adjust our speak method so that it tells us a little more about our specific object.

- In the console log where we have the string `"Bark!"` let's change the string to say the dog's name and color
  - To reference the object we're on we'll use the `this` keyword, and then access the property we want
  - so if we replace the string `"Bark!"` with `"My name is " + this.name + " and I am a " this.color + " dog."`
  - We now have a talking dog!

---

# `this` and Binding

The keyword `this` is *bound* to the context in which it is *called*. If you're calling the method through the object using dot notation (as you normally would), the context is *that object.*

If you detach the method, then the `this` keyword becomes *unbound*. This can cause issues because the global object usually doesn't have the properties your method is looking for.

---

# Fat Arrow Functions

Fat arrow functions bind `this` to the context in which they are *defined*. This can make it easier to know what exactly you're referencing with `this`

Also remember: "When in doubt `console.log` it out."

If your method is not behaving as expected try `console.log`ing what `this` is inside your method.

---

# Extending objects on the fly

Since JavaScript is a *dynamic* language,
you can add methods to *any object*.


```js
let rectangle = {
    height: 10,
    width: 8,
}
rectangle.area()   //=> TypeError: rectangle.area is not a function

rectangle.area = function() {
     return this.height * this.width;
}
rectangle.area()   //=> 80
```

* remember, `this` means "this object I'm in *right now*" which in this case is the rectangle
* `this.height` on the *inside* of the object means the same as `rectangle.height` on the *outside*
