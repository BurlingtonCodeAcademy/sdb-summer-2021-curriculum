# Functions

*Variables* allow us to reuse _values_.

**Functions** allow us to reuse _statements_.

---

## When to Use Functions

JavaScript is a **functional programming language**. _Functions_ are the tools used to organize code blocks into sections.

| When you are...                                    | Use functions to...                            |
| -------------------------------------------------- | ---------------------------------------------- |
| 1. copying and pasting code blocks                 | 1. keep edits in one place                     |
| 2. getting code to affect data in a different file | 2. share logic between files and computers     |
| 3. noticing your file is rather long               | 3. break it apart and make it easier to read.  |
| 4. lost as to what part of your code does what     | 4. label and divide your code into clear steps |

---

# Function Syntax

- Here is the function syntax structure:

```js
keyword functionName ( parameter1, parameter2 ) { code block }
```

In what ways does this look familiar?

```js
function sayHello() {
  console.log("Hello!");
}
```

Why is the _parameter_ an empty expression here?

---

# Function Syntax Cont.

- Functions are often used to make changes to data.
- This means functions need
  - **Parameters**: A way to receive data
  - **Return values**: A way to send data when done

```js
function sayHelloToName(name) {
  return "Hello " + name + "!";
}
```

---

# Calling or Invoking a Function

- We tell a computer to use a function by **invoking** or **calling** it.
- To _call_ a function, we use 2 things:
  - The function's name
  - An expression holding **arguments**
    - _Values_ provided to fill in the expected _parameters_
    - Leave empty if no arguments are needed

```js
function sayHelloToName(name) {
  return "Hello " + name + "!";
}

sayHelloToName("Lemony Snicket");
```

---

# Function Literacy Practice

Can you translate this JavaScript back to English?

```js
function shouter(someString) {
  let loudString = someString.toUpperCase();

  return loudString + "!!!";
}
```

---

# Passing Variables to Functions

When you pass a _variable_ to a function, that variable's _value_ is assigned to a _parameter_.

The variable and parameter names **do not** need to match!

```js
function shouter(someString) {
  let loudString = someString.toUpperCase();
  return loudString + "!!!";
}

let feeling = "I feel great";
let strongFeeling = shouter(feeling);
```

| Outside the function | Inside the function | Value               |
| -------------------- | ------------------- | ------------------- |
| `feeling`            | `someString`        | `"I feel great"`    |
|                      | `loudString`        | `"I FEEL GREAT"`    |
| `strongFeeling`      |                     | `"I FEEL GREAT!!!"` |

---

# Alternative Ways to Write Functions

When defining functions, there are multiple approaches developers can take:

[Function Declaration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)

```js
function add(x, y) {
  return x + y;
}
```

[Function Expression](https://developer.mozilla.org/en-US/docs/web/JavaScript/Reference/Operators/function)

```js
let add = function (x, y) {
  return x + y;
};
```

---

# Alternative Ways to Write Functions Cont.

[Arrow Function Expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

```js
let add = (x, y) => {
  return x + y;
};
```

[Arrow Function Expression Shorthand](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#Function_body)

```js
let add = (x, y) => x + y;
```

---
