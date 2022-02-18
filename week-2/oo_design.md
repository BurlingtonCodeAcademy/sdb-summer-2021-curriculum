# Object-Oriented Design

There are many object-oriented languages. While they differ in their syntax they all share a common set of design principles.

JavaScript is an object-oriented language, and a functional language, and a procedural language. It is known as a multi-paradigm language.

Since JavaScript is not purely object-oriented, these principles act more like guidelines.

---

## Object-Oriented Principles

Object-oriented languages are built on core principles.

- Encapsulation of an Object's **data** and **behavior**, by exposing an interface.
- Inheritance of common behavior, from a **parent Class** that **shares methods**.
- Abstraction of complexity, by hiding **implementation details**.
- Polymorphism of behavior, by responding to **messages by name** and **argument type**.

---

## Encapsulation Definition

Encapsulation is the act of keeping data within an object as properties, and using methods to access that data.

There are some guidelines to keep in mind when using Objects that follow object-oriented design.

---

## Encapsulation Example

By using the `.describe()` method of the `dog`, you are accessing the data within the dog by using its **public API**. This is opposed to going **inside** the dog and getting the data for yourself.

```js
const fido = {
  name: 'fido',
  color: 'brown',
  describe () { 
    return `Hello! My name is ${this.name} and I am ${this.color}.`
  }
}

// RECOMMENDED
console.log(fido.describe());

// DISCOURAGED
console.log(`Hello! My name is ${fido.name} and I am ${fido.color}`);
```

---

## Encapsulation Question

> Why would you want to use the public API of the dog object, instead of reaching inside the object the the data you may need?

Example code from prior slide:

```js
console.log(fido.describe());

console.log(`Hello! My name is ${this.name} and I am ${this.color}`);
```

---

## Inheritance Definition

Classes are a key component of Object-Oriented Design. Child classes **inherit** behavior using the `extends` keyword. This allows objects created from one class to use the behavior of another class.

In this relationship one class is a **child** and the other class is the **parent**.

```js
class Tomato extends Fruit { ... }
```

---

## Inheritance Example

Classes are a key component of Object-Oriented Design. Child classes inherit behavior using the `extends` keyword.

```js
class Animal {
  constructor(name, color) { 
    this.name = name;
    this.color = color; 
  }

  sleep() { return `${name} is going to sleep ... `}

  describe() {
    return `Hi there, I am ${name}, my color is ${color}!`;
  }
}

class Dog extends Animal {
  constructor(name, color) { 
    // uses the parent class constructor
    super(name, color)
  }

  describe() {
    // *overrides* the parent describe method
    return `A ${color} colored dog named ${name} says Woof!`;
  }
}
```

---

## Inheritance Questions

- Why do you think Inheritance may be useful?

- Why do you think Inheritance may be complex?

- What alternatives to Inheritance can you imagine?

---

## Abstraction Definition

Abstraction is the act of hiding complexity, often this is by moving the complexity behind an object's methods.

Ideally, an object only uses two sources of data.

- Parameters to methods when they are invoked
- Properties of the method's own object, meaning the object `this` references
- All processing is performed by sending **messages** to other objects, as collaborators

---

## Abstraction Example

The code uses a method of `rectangle` to access the internal object state.

```js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  area () {
    return this.height * this.width;
  }
}

const shape = new Rectangle(10, 8);

function showArea(shape) {
  return `The shape's area is: ${shape.area()}`;
}
```

---

## Abstraction Counter Example

The following code is **not** Abstracted, complexity is present by manipulating the object directly, instead of using its methods.

```js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  area () {
    return this.height * this.width;
  }
}

const shape = new Rectangle(10, 8)

function showPerimeter(rectangle) {
  return `The perimeter is: ${rectangle.height * 2 + rectangle.width * 2}`;
}
```

---

## Abstraction Questions

- How could a method be created on `Rectangle` to abstract the complexity?

> The `height` and `width` are **owned** by `rectangle`, not by the `showPerimeter` function.

```js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  area () {
    return this.height * this.width;
  }
}

const shape = new Rectangle(10, 8)

function showPerimeter(rectangle) {
  return `The perimeter is: ${rectangle.height * 2 + rectangle.width * 2}`;
}
```

---

## Abstraction Question Solution

Add a `perimeter` **method**, so `rectangle.perimeter()` would access properties with `this`, perform the calculation, and return the value.

```js
class Rectangle {
  constructor (height, width) {
    this.height = height;
    this.width = width;
  }
  area () {
    return this.height * this.width;
  }
  perimeter () {
    return this.height * 2 + this.width * 2;
  }
}

const shape = new Rectangle(10, 8)

console.log(rectangle.perimeter());
```

---

## Polymorphism Definition

**Polymorphism** is a complicated word for a simple idea. It means that Objects should respond to **messages** based on the **messages names** alone.

All **child classes** must respond to all the same **messages** as the **parent class**.

When two objects respond to the same **messages**, meaning the names of **properties** and **methods**, they are said to be **polymorphic**, and therefore share the same **shape**.

## Polymorphism Example

```js
class Fruit {
  constructor (hasSeeds, flavor) {
    this.hasSeeds = hasSeeds; 
    this.flavor = flavor;
  }
  describeFlavor() { ... }
}

class Tomato extends class Fruit { ... }
class Avocado extends class Fruit { ... }

tomato.describeFlavor()  // "tangy and sweet"
tomato.hasSeeds          // true
avocado.describeFlavor() // "rich and savory"
avocado.hasSeeds         // true
```

---

## Polymorphism Question

- Why would it be useful for different objects to respond to the same messages?

- How could you use Polymorphism to make your programs simpler?

- If an object looks like a duck, and quacks like a duck, can we consider it a duck?

---

## The Linguistic Metaphor for Objects

Objects are **data structures** that hold **state** and **behavior** together.

When considering how to name objects, properties, and methods, use the following mental model.

- Objects are nouns, and represent things in the program
- Methods are verbs, and represent actions the objects do
- Properties are adjectives, they describe the object as a **noun**
- Classes are categories, something that describes a **type** of thing, not a thing itself
