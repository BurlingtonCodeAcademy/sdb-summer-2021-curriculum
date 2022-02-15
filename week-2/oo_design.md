# Object-Oriented Design

There are many object-oriented languages. While they differ in their syntax they all share a common set of design principles.

JavaScript is an object-oriented language, and a functional language, and a procedural language. It is known as a multi-paradigm language.

Since JavaScript is not purely object-oriented, these principles act more like guidelines.

---

## Object-Oriented Principles

Object-oriented languages are built on core principles.

- Encapsulation of an Object's **data** and **behavior**, by exposing an interface.
- Abstraction of complexity, by hiding **implementation details**.
- Inheritance of common behavior, from a **parent Class** that **shares methods**.
- Polymorphism of behavior, by responding to **messages by name** and **argument type**.

---

## Encapsulation

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

## Single Responsibility Principle

Each object should have limited, clearly defined responsibilities.

> Do one thing, and do it well.

This makes it easier to know *where* in the code to look when you want to add a feature or fix a bug.

It helps to *increase cohesion* and *reduce coupling*... If there are two objects with related (but separate) responsibilities, you can change the implementation of one without affecting the other.

Objects can communicate through the same stable *interface* without regard for the *implementation*.

---

## Shallow Hierarchies

Object-Oriented systems can , so there's a risk of confusing designs, including:

- Deep hierarchies
- Parallel hierarchies
- Cycles

It's best if dependencies are *one-way* and hierarchies are *shallow*.

This means you should try to limit *nesting* and *inheritance* as much as possible, and your objects shouldn't rely on any outside data. They can send and receive messages but shouldn't care where the messages are coming from, or going to.

---

## Classes, Hierarchy, and Inheritance

Classes are a key component of OO Design in JavaScript. They allow you to create many objects with shared behavior, but different data. You can even generate child classes with the `extends` keyword to create children with additional, separate behaviors.

When setting up child classes keep in mind that a child should be able to do anything its parent can do, and then some.

Beware of generating too many children from a single class, or too many generations of children. The computer will understand it just fine, but it will quickly become confusing for our squishy, meat brains.

---

## Data Privacy

To be truly object oriented an object should be entirely self contained. The only interface it has to the outside world should be in the form of arguments to a method, though it can reference its own properties with the `this` keyword.

Objects should never reference, or access other object's properties in a purely object oriented model.

Unfortunately this is not something JavaScript enforces. So we, as the programmer, need to be disciplined about it when we are writing the code.

---

## Definition of an Object

An object:

- *Encapsulates* state and behavior
  - *State* aka data, properties, variables
  - *Behavior* aka functions, methods, messages
  - *Encapsulation* means to "put similar things together; keep dissimilar things apart"
- Responds to *messages* through an *interface*
  - a *message* corresponds to a *method* (mostly)

---

## Pure Object-Oriented Programming

In pure object-oriented design, an object only uses two sources of data

- Parameters to methods when they are invoked
- Properties of the method's own object, meaning the object `this` references
- All processing is performed by sending **messages** to other objects, as collaborators

---

## Pure Object-Oriented Example

```js
const rectangle = {
  height: 10,
  width: 8,
  area () {
    return this.height * this.width;
  }
}

function showArea(shape) {
  return `The area is: ${shape.area()}`;
}

console.log(showArea(rectangle));
```

> The above code only accesses data inside `rectangle` using the keyword `this`, and returns a new value, not a reference to the object's state.

---

## Procedures using Objects

The following code is **not** object-oriented, but uses the `rectangle` object

```js
const rectangle = {
  height: 10,
  width: 8,
  area () {
    return this.height * this.width;
  }
}

function showPerimeter(rectangle) {
  return `The perimeter is: ${rectangle.height * 2 + rectangle.width * 2}`;
}

console.log(showPerimeter(rectangle));
```

> The `height` and `width` are **owned** by `rectangle`, not by the `showPerimeter` function

Q: How would an OO design calculate the rectangle's perimeter?

---

## Procedures using Objects Solution

Add a `perimeter` **method**, so `rectangle.perimeter()` would access properties with `this`, perform the calculation, and return the value.

```javascript
const rectangle = {
  height: 10,
  width: 8,
  area () {
    return this.height * this.width;
  }
  perimeter () {
    return this.height * 2 + this.width * 2;
  }
}

console.log(rectangle.perimeter());
```

---

## The Linguistic Metaphor for Objects

Objects are **data structures** that hold **state** and **behavior** together.

- Objects are nouns, and represent things
- Methods are verbs, and represent actions
- Properties are adjectives, they describe the **noun**
- Classes are categories, something that describes a **type** of thing, not a thing itself
