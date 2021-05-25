# the `class` keyword

In 2015, JavaScript introduced the `class` keyword which is syntactic sugar on top of JavaScript's existing prototype system. 

This new `class` syntax is much easier to understand than the previous system.

```javascript
class Circle {
  circumference() {
    return Math.PI * this.radius * 2;
  }
  area() {
    return Math.PI * this.radius * this.radius;
  }
}
```

---

# Use it like this:

```javascript
let circleInstance = new Circle();  // create a new Circle instance
circleInstance.radius = 2;          // set its radius to 2
circleInstance.area();              // call the area method, which
                            // returns 12.566370614359172 
```

* A Note On Spelling:
  * "Circle" with a capital C is the constructor
  * In JavaScript class names are generally capitalized
  * All other variable names are camel cased
  * This makes it easier for us as the programmer, but the computer doesn't care
  * It's the standard naming convention, so always capitalize your class names

[MDN: classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

---

# Stay classy, JavaScript

This is the first time we've seen classes in JavaScript

Classes are for making lots of objects with the same methods, but different data

* A *class* defines a **type** of object.
* An *instance* is an **individual** object of that type.
* Each instance has *it's own* state

> For example, there are many houses, but my house is yellow.

---

## The Cookie Analogy:

  * class ~= cookie cutter
  * instance ~= cookie
  * instance data ~= icing and sprinkles

---

# Constructors and "new"

* A constructor is a **method on a class** that's called when you use the *new* keyword
* It's the very first method that's ever called on that particular instance

---

## What `new` does, in detail:

  * makes a new empty object
  * sets the object's class
  * sets `this` to point to the new instance
  * calls the constructor function
  * returns a new object instance

---

# Constructors are for Initialization

the principle of *Complete Construction* says that after the constructor executes, the object is in a *valid* state

in practice, this means "pass all initial values into the constructor"

---

## A Better Circle:

```js
class Circle {
  constructor(radius) {
    this.radius = radius;
  }
  circumference() {
    return Math.PI * this.radius * 2;
  }
  area() {
    return Math.PI * this.radius * this.radius;
  }
}
```

Use it like this:

```js
let circle = new Circle(2);  // create a new Circle instance with radius 2
circle.area(); // call the area method, which returns 12.566370614359172
```

---

## Q: Why is this better?

A: because it preserves *encapsulation* -- the idea that an object should be responsible for setting its own properties

Encapsulation:

  * Prevents accidental reassignment
  * Allows consistent and predictable outcomes
  * Preserves the state of the data

---

# Constructors are for Validation

constructors are a great place to *validate* your values 

```javascript
class Circle {
    constructor(radius) {
        if (radius <= 0) {
            throw('radius must be a positive number')
        }
        this.radius = radius;
    }
```

---

# Guard Clauses

* that `if` statement is known as a "guard clause"
  * it guards against bad values entering your algorithm
* validation is a valuable feature in program designs
  * it lets you *write less code* in other methods, confident that you don't have to check for bad data or boundary conditions
  * You can catch bugs when they are introduced rather than waiting for something to go wrong

---

# Factory Town

Sometimes one constructor just isn't enough.

When the constructor accepts different parameters from the ones that you have on hand, you could define a *factory function* like this:

```javascript
function circleFromDiameter(diameter) {
    return new Circle(diameter / 2);
}
```

The above is called a "factory function" since it constructs objects for you, based on your specifications.

---

# Factory Methods

For convenience and code organization, factory functions are often attached to the *class* -- **not the instance** -- of the objects they create.

| Factory Function | Factory Method |
|---|---|
| `let c = circleFromDiameter(2)` | `let c = Circle.fromDiameter(2)` |

The factory method works *exactly the same way* as the factory function, but

* the factory function is in the *global namespace*
* the factory method is in the *class namespace* so it's more clear that it is meant to create one of *this class* of objects

---
 
# Static Factory Methods 

To make a *factory method* attached to a class in JavaScript, use the [`static`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static) keyword:

```javascript
class Circle {
  static fromDiameter(diameter) {
    return new Circle(diameter / 2);
  }
  constructor(radius) {
    if (radius <= 0) {
        throw('radius must be a positive number')
    }
    this.radius = radius;
  }
  
  area() {
    return Math.PI * this.radius * this.radius;
  }
}
```

---

# Using Factory Methods

Factory methods are useful for when you want to be able to generate an object based on different parameters, or if you want to create a default instance if no data is supplied.

We could use the factory method we defined before to generate circles from their diameter, rather than the radius, and call it like this:

```javascript
let diameterCircle = Circle.fromDiameter(4)
```

> Note that (lowercase "c") `circle.fromDiameter()` does **not** work. **Static methods are attached to classes**, not instances.

---

# Class Inheritance

All objects inherit the methods, and properties defined on their class. Usually a constructor will be used to allow you to dynamically assign the values of the properties when you create a new object instance, but if you hard code the values on the class then those properties will be automatically inherited by the class.  This is why object instances have access to all the methods defined on their class.