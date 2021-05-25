# Object-Oriented Design

There are quite a few object oriented programming languages out there, and while they don't have the same syntax they all share a common set of design principles which they must adhere to.

JavaScript is not one of these languages, but it does borrow a few things from them so we can use some principles of object oriented design to help make our code more organized, more efficient, and easier to maintain.

Since JS is not a purely object oriented these principles are less like rules and more like guidelines.

While design principles are useful tools don't let them get in they way of making your program work.

---

# Principles of OO Design

Object oriented languages are built on several core principles which we can apply to our JavaScript code

- encapsulation of data and behavior
- pointers
- privacy of data

---

# Encapsulation

"Encapsulation of data and behavior" is really just a fancy way of saying "object"

BUT there are some guidelines we want to keep in mind when creating objects if we're trying to follow OO design principles

---

# The Single Responsibility Principle

Each object should have limited, clearly defined responsibilities.

> Do one thing, and do it well.

This makes it easier to know *where* in the code to look when you want to add a feature or fix a bug.

It helps to *increase cohesion* and *reduce coupling*... If there are two objects with related (but separate) responsibilities, you can change the implementation of one without affecting the other. 

Objects can communicate through the same stable *interface* without regard for the *implementation*.

---

# Shallow Hierarchies

OO systems rely on pointers, so there's a risk of confusing designs, including:

  * deep hierarchies
  * parallel hierarchies
  * cycles

It's best if dependencies are *one-way* and hierarchies are *shallow*.

This means you should try to limit *nesting* and *inheritance* as much as possible, and your objects shouldn't rely on any outside data. They can send and receive messages but shouldn't care where the messages are coming from, or going to.

---

# Classes, Hierarchy, and Inheritance

Classes are a key component of OO Design in JavaScript. They allow you to create many objects with shared behavior, but different data. You can even generate child classes with the `extends` keyword to create children with additional, separate behaviors.

When setting up child classes keep in mind that a child should be able to do anything its parent can do, and then some.

Beware of generating too many children from a single class, or too many generations of children. The computer will understand it just fine, but it will quickly become confusing for our squishy, meat brains.

---

# Privacy of Data

To be truly object oriented an object should be entirely self contained. The only interface it has to the outside world should be in the form of arguments to a method, though it can reference its own properties with the `this` keyword.

Objects should never reference, or access other object's properties in a purely object oriented model.

Unfortunately this is not something JavaScript enforces. So we, as the programmer, need to be disciplined about it when we are writing the code.

---

# Object-Oriented JavaScript

JavaScript is a hybrid of (at least) three styles:

  * procedural
  * functional
  * object-oriented

In this lesson we explore how JavaScript implements *object-oriented* language features.

---

# Definition of an Object

An object...

* *encapsulates* state and behavior
    * *state* aka data, properties, variables
    * *behavior* aka functions, methods, messages
    * *encapsulation* means "put similar things together; keep dissimilar things apart"
* responds to *messages* through an *interface*
  * a *message* corresponds to a *method* (mostly)

---

# Pure Object-Oriented Programming

* In pure OO, a method only directly uses two sources of non-local data
    * parameters of the method
    * properties of the method's own object
    * cf. the Law Of Demeter (more on this later)
* All other data are manipulated via *messages* sent to other objects (aka *method calls*)

---

# Pure Object-Oriented Example

```javascript
let rectangle = {
    height: 10,
    width: 8,
    area: function() {
        return this.height * this.width;
    }
}

let a = rectangle.area()
```

the above code follows OO rules since it only accesses data held inside `rectangle` via the magic pointer `this`, and returns a new value, not a live reference to internal state

---

# Using an Object, But Not Object-Oriented

Using the `rectangle` object from the previous slide, the following code is **not** object-oriented...

```javascript
let p = calculatePerimeter(rectangle);

function calculatePerimeter(rectangle) {
  return rectangle.height * 2 + rectangle.width * 2;
}
```

...since `height` and `width` are owned by `rectangle`, not by the `calculatePerimeter` function

Q: How would an OO design calculate the rectangle's perimeter?

---

# Pure Object-Oriented Example (Cont.)

instead, an OO design would add `perimeter` as a *method*, so `rectangle.perimiter()` would access properties with `this`, perform the calculation, and return the correct value:

```javascript
rectangle.perimeter = function() {
  return this.height * 2 + this.width * 2
}

let p = rectangle.perimeter()
```

---

# Object vs. Object

* In JS, an "object" is just a hash
  * a hash is just an unordered collection
  * not very object-oriented
* To be object-oriented you need to add a few things
  * the "`this`" variable
  * constructors and `new`
  * inheritance (via prototypes (`__proto__` or `Type.prototype` or `class`))
  * privacy (aka *data hiding* or *encapsulation*)

---

# The Linguistic Metaphor for Objects

One way to think about objects: 

Objects are *things* that can be *described* and can *do* things, or...

  * Objects are nouns
    * (things)
  * Methods are verbs
    * (actions, behaviors, or imperative messages ("Sit! Good dog."))
  * Attributes are adjectives
    * (a property that describes a particular thing)
  * Classes are categories
    * (a noun that describes a *type* of thing, not a thing itself)

---

# Creating an object literally

This code 

```js
let dog = {color: "brown"}
```

1. creates a new object
2. gives that object a property named `'color'` whose value is `'brown'`
3. assigns the variable `dog` to point to that object

---

# References and Instances

* Imagine computer memory with two compartments: *references* and *instances*
  * also known as "the scope" and "the heap"
  * also known as "pointers" and "values"
* References include *parameters* and *local variables*
* Instances contain the "real" data
* Each reference points at the location of an instance
  * every reference is the same size (just 32 bits, or maybe 64 bits)

| Stack |     | Heap    |
| ----- | --- | -----   |
| dog   | ->  | {color: "brown"} |

---

# Literals create instances

```js
let abby = {color: "brown"}
let lula = {color: "brown"}
```

* `abby` refers to a new object *instance*
* `lula` refers to a *different*, new object instance with the same *value*

| Stack |     | Heap  |
| ----- | --- | ----- |
| abby  | ->  | {color: "brown"} |
| lula  | ->  | {color: "brown"} |

---

# Side effects

* a variable is a *reference* to an *instance* (persistent location in memory)
* if you have several references to the same instance, odd things can happen

```js
let dog = {color: "brown"}
let abby = dog
let lula = dog

lula.color = "gold"

abby.color // now we think that abby is gold too :-(
```

---

# Encapsulating State

Instance variables are *properties* of the object:

```js
if (abby.color === 'brown') {
  console.log("Abby is a brown dog.");
}
```

the DOT operator here says "get me the `color` that is attached to `abby`"

---

# Encapsulating Behavior

Instance *methods* are also *properties* of the object:

```js
let abby = {color: "brown"};
abby.speak = function() {
  console.log("Bark!")
}
abby.speak()     // prints "Bark!" to console
```

The above is fine as far as it goes, but it's not really object-oriented since `speak` isn't using any *state*...

---

# "this" is it

* `this` is a magic variable that always points to the current object

```javascript
var circle = {radius: 2};
circle.circumference = function() {
    return Math.PI * 2 * this.radius;
}
console.log(circle.circumference()); // 12.566370614359172
```

* `this` allows one function (method) to operate on many states (instances)

```javascript
var biggerCircle = {radius: 4};
biggerCircle.circumference = circle.circumference;
console.log(biggerCircle.circumference()); // 25.132741228718345
```

---

# JS Gotcha: you must remember `this`

Even *inside* an object, you **must** remember to use `this.`, otherwise `radius` becomes a *global variable*, not a property.

```javascript
var circle = {radius: 2};
circle.circumference = function() {
    return Math.PI * 2 * radius;  // Oops! Forgot "this."
}
circle.circumference() // returns NaN
// (or says 'radius is not defined' if you're lucky)
```

---

# JS Gotcha: Fat Arrow and Binding

In most OO languages, the pointer `this` is managed automatically. Any time you're executing code inside class A, `this` is guaranteed to point to an instance of that class.

In JavaScript, `this` needs to be managed more actively. 

Specifically, during *callbacks* `this` still points to the *other* object -- the one that is *calling you back* -- **not** the object where the function is defined!

**One Solution**: the `=>` fat arrow *re-binds* `this` to point to the *current* object immediately before executing the function.

---

# More on "this" and binding

* `this` is only set when you call a function *via* an object

```javascript
circle1.circumference()      // OK -- this = circle1
circle2.circumference()   // OK -- this = circle2
```

* when called *sans* object, `this` points to the **global object** (usually `window`)

```javascript
var g = circle.circumference;
g();                        // BAD -- this = window, so this.radius = undefined, so result is NaN
```

---

# re-binding

* so if you want to use a *method* as a *callback*, you must *bind* it like this:

```javascript
var module = {
  x: 42,
  getX: function() {
    return this.x;
  }
}

var unboundGetX = module.getX;
console.log(unboundGetX());
// expected output: undefined

var boundGetX = unboundGetX.bind(module);
console.log(boundGetX());
// expected output: 42
```

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind