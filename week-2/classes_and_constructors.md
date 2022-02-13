# Classes

In 2015, JavaScript introduced the `class` keyword.

**Classes** are a [special kind of function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes). Like functions, you can make them using declarations or expressions, but we will focus on the declaration style.

The purpose of a class is to generate a specific object you want.

---

# Class Syntax

```js
class Pizza {
  constructor(diameter, type) {
    this.diameter = diameter;
    this.type = type;
  }

  bake(){
    console.log('Your pizza will be ready in 5 minutes!')
  }
}
```

What about this syntax is familiar? What is new?

---

# Instantiating Classes

To **instantiate** is to create an **instance** of a class. This means we are using the class to construct *one* specific object.

```javascript
let myPepperoniPizza = new Pizza(14, 'pepperoni');  // create a new Pizza instance
myPepperoniPizza.diameter = 16;                     // set its diameter to 2
myPepperoniPizza.bake();                            // call the bake method, which returns 'Your pizza will be ready in 5 minutes!'
                            
```

[MDN: classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

---

# When and Why to Use Classes

Classes *construct* objects.

We use them for repeatedly making the same kind of object where the details might vary.

* A *class* defines a category of object -- all humans.
* An *instance* is *one* object of that type -- one specific human.
* Each instance has *its own* data -- you have unique DNA.

---

# Constructors and `new`

* Using the `new` keyword tells JavaScript to invoke the `constructor` *method* within a *class*.
* This is the method that actually *constructs* the object.

```js
let myPizza = new Pizza(14, 'pepperoni')
```

> [Mozilla Developer Network | new operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new)

---

# Constructors and `new` Cont.

What exactly does `new` do?
  
[Investigate and discuss.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new#description)

---

# Practice: Making a Circle Class

> 1. Use a class to make a circle.  
> 2. Create an instance.
> 3. Log the area and circumference return values.
> 4. When done, submit your answer.

Constraints: Your circle must

* have a radius as its parameter in the constructor.
* have a method of calculating the circumference.
* have a method of calculating the area.

---

# Validating Classes

**Validating** input means making sure the data is acceptable and [throw](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw)ing if it's not.

A good time to validate data is in the constructor, *before* initializing values in `this`.

For example:
```javascript
class MyClassName {
    constructor(parameter) {
        if (parameter !== someValueIWant) {
            throw "Your parameter doesn't equal something I want! Boo hiss!" // sends an "exception"
        }
        this.parameter = parameter;
    }
```

---

# Practice: Validating Your Pizza

> Challenge: Make a pizza class that does *not* allow you to set pineapple as the type.
> You may use the slides and your notes. DM your answer to an instructor via Discord.

---

# Instantiating Classes in Functions

Remember that there are no rules about calling functions within another function's block, even when using special ones like classes.

We can use a function to take data in a different format than the kind our class may need. This allows us to process it accordingly before trying to use it.


```javascript
function circleFromDiameter(diameter) {
    return new Circle(diameter / 2);
}
```

The above is called a **factory function** since starts the *construct*ion process for you, based on your specifications.

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

A `static` property or method is one that we can only use with the class itself, *not instances.*

```javascript
class Circle {
  static createCircleUsingDiameterInfo(diameter) {
    return new Circle(diameter / 2);
  }

  constructor(radius) {
    if (radius <= 0) {
      throw 'Radius must be a positive number';
    }
    this.radius = radius;
  }
}
```

---

# Practice: Static Factory Methods

| Code | Output |
|-|-|
|<img src ="https://res.cloudinary.com/btvca/image/upload/v1644792273/curriculum/factoryMethod_uaawek.png" width="60%" /> |<img src ="https://res.cloudinary.com/btvca/image/upload/v1644792271/curriculum/factoryMethodOutput_iakgju.png" width="60%" />|


---
# When and Why to Use Factory Methods

Factory methods allow us to consistently change the format of the data used to create an instance, like when we want to use a diameter instead of a radius.

You know it's time to use a factory method when you want to create multiple instances from a class using data it does not originally support.

What happens if you try to invoke a static method from an instance instead of the class itself? Try it and see!

---

# Class Inheritance

Classes give their properties and methods to the objects they create. The properties are attached in the constructor.

This means we don't need to rewrite `getArea` or `getCircumference` every time we create a circle object from the Circle class.

Using the `static` keyword to prevents inheritance for properties and methods. 

The circle objects we make do not inherit the `createCircleUsingDiameterInfo` method.