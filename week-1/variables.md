# Variables

- A **variable** is a **name** for a value.
- The **assignment** operator _assigns_ a _variables_ to a value.
  - It looks like an equal sign, but it does not mean "equals".
  - often preceded by `let` as in "Let there be light" or "Let x be assigned to 10".

```js
let color = "blue";
let fruit = "berry";
```

---

# Variables Cont.

Tip: _Anywhere_ you would use a _value_ or _expression_, you can use a variable instead _and vice versa_:

```js
color + fruit;         // "blueberry"
fruit.toUpperCase();   // "BERRY"
"berry".toUpperCase(); // "BERRY"

if (color) {
  // do some stuff here
}

if ("blue") {
  // do some stuff here
}
```

[ Mozilla Developer Network | Declarations ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements#declarations)

---

# Declarations

Declarations are key words we use to say we are creating a variable _for the first time_.

- `let` is the easiest way to **declare** a variable in JavaScript
- `const` and `var` are other **declarations**, but they have specific rules and caveats.
- Without a _declaration_ (`let`, `const`, `var`) the variable becomes **global** (which is dangerous).
- Stick with `let` unless otherwise needed.

_How is declaring a variable different from assigning one?_

[Mozilla Developer Network | Statements and Declarations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements)

---

# Common Declaration Mistake

We can only _declare_ a variable once in each **scope** or code block. Otherwise, you will get an error:

```js
SyntaxError: Identifier 'coolNumber' has already been declared
```

If you see this error then try again without the _declaration_.

```js
let coolNumber = 1;
// => undefined

let coolNumber = coolNumber + 2;
// => SyntaxError: Identifier 'x' has already been declared

coolNumber = coolNumber + 2; // <= no "let", "const", or "var" this time
// => 3 
```

---

# Best Practices when Naming Variables

Which is easier to understand without asking someone else?

This?

```js
60 * 60 * 24;
```

Or this?

```js
let secondsPerMinute = 60;
let minutesPerHour = 60;
let hoursPerDay = 24;
let secondsPerDay = secondsPerMinute * minutesPerHour * hoursPerDay;
```

How can you use this knowledge to be an effective teammate?

---

# The Pointer Metaphor

```js
let snack = "Apple";
```

![snack-apple](https://res.cloudinary.com/btvca/image/upload/v1574445202/curriculum/snack-apple_ltysdv.svg)

Think of a variable as a name that **points** to a value.

> Note: Variables point. Values do not.

---

# Reassigning Variables

We tell variables what to point to when we **assign** and **reassign** them. If we don't assign them, they point to `undefined` by default.

```js
let color;           // declare a variable but never assign it to a value
color = "blue";      // assign the variable to a string values "blue"
let fruit = "berry"; // declare fruit variable and assign to "berry" value
color + fruit;       // combine the variables (and their values) to make "blueberry"

color = "black";     // reassigning again but this time to "black"
color + fruit;       // combining again to now make "blackberry"
```

---

# Assigning Variables to Other Variables

If _variables_ are a kind of _expression_ that will be processed into _values_, what happens in a scenario like this?

```js
let fruit = "Apple";
let snack = fruit;
```

|                                                                                                             | <br/>                                                                                                            |
| ----------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| ![snack-fruit](https://res.cloudinary.com/btvca/image/upload/v1574445202/curriculum/snack-fruit_momdep.svg) | `snack` and `fruit` end up _pointing_ to the same _value_. <br/>This is like placing two labels on the same box. |

---

# Constants: Variables that Aren't Variable

- The keyword `const` is just like `let`, but _prevents reassignment_

```js
const pi = 3.14159;
```

- When using const to declare a variable, the assignment is _constant_.
  - Trying to reassign it will result in a TypeError.

```js
pi = 7;
TypeError: Assignment to constant variable.
```

> WARNING: `const` prevents _reassignment_, but it does not stop a value from changing on its own.

---

# { Scope }

- **Scope** refers to the section of code where a variable can be used, like a territory or jurisdiction.
- A variable's scope is determined when it is _declared_.
- We can identify scopes by looking for `{}`s and indentations. This is why formatting your code really matters.
- Starting a new pair of curly braces `{}` opens a new scope.
- Indented variables, these are in between the `{}`, are located in an _interior_ scope.
- Trying to use a variable outside of its scope results in an error.

> ✨🪞✨<br> _Scope is like a one way mirror:_ <br>
> You can look out (to exterior scopes), <br>
> but you cannot look in (to interior scopes).

---

# { Scope Example }

<figure>
  <img src='https://res.cloudinary.com/btvca/image/upload/v1643917202/curriculum/scopeexample.png' width="70%"/>
  <figcaption>
    <a href="https://developer.mozilla.org/en-US/docs/Glossary/Scope">Mozilla Developer Network | Scope</a><br/>
    <a href="https://www.w3schools.com/js/js_scope.asp">W3 Schools | Scope</a>
  </figcaption>
</figure>

---

# Summary: Variables

- _Variables_ are names for values
- _Declaring_ a variable says what its _scope_ is
- _Assigning_ a variable sets the value it's naming.
- You can have many names for the same value.
