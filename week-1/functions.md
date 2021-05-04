# Functions

Remember that a **variable** is a **name** for a piece of data

A **function** is the **name** for a piece of code

---

## Why would you want to name a chunk of code?

Perhaps...

* you have some code you want to run again and again
* you want to do the same operation on different values
* you want to keep your code organized

---

# Function example

Here's an example function:

```js
function add(x, y) {
  let sum = x + y;
  return sum;
}
```

* `function` means "define a function"
* `add` is the *name* of the function
* `x, y` are the *parameters* of the function (also called *arguments*)
* `sum` is a *local variable* of the function
* `sum` is also the function's *return value* because of the magic word *return*

---

# Call Me, Maybe

You call a function by its name, plus parentheses:

```js
function add(x, y) {
  let sum = x + y;
  return sum;
}

add(2, 3)   // returns 5
add(12, 30) // returns 42
```

---

# Shouter

Here is a slightly more complex function that takes some String as input, and as output returns a shouted version of that String.

```js
function shouter(someString) {
  let loudString = someString.toUpperCase();
  return loudString + '!!!';
}

shouter('i like pizza');  => 'I LIKE PIZZA!!!'
```

The variable `loudString` is called a **local variable** and can only be used **inside** the function.

---

# Passing Variables to Functions

When you pass a *variable* to a function, that variable's *value* is assigned to a *parameter*.

> The variable and parameter names **do not** need to match!

```js
function shouter(someString) {
  let loudString = someString.toUpperCase();
  return loudString + '!!!';
}

let feeling = "I feel great";
let strongFeeling = shouter(feeling);
```


| Outside the function | Inside the function | Value               |
|----------------------|---------------------|---------------------|
| `feeling`            | `someString`           | `"I feel great"`    |
|                      | `loudString`     | `"I FEEL GREAT"`    |
| `strongFeeling`      |                     | `"I FEEL GREAT!!!"` |

# Four Function Syntaxes

> **WARNING**: JavaScript has many ways to define a function.

[Function declaration syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)

```js
function add(x,y) { return x + y; }
```

The following are all roughly equivalent to the above:

[Function Expression](https://developer.mozilla.org/en-US/docs/web/JavaScript/Reference/Operators/function)

```js
let add = function(x,y) { return x + y; };
```

[Arrow Function Expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

```js
let add = (x,y) => { return x + y; };
```

[Arrow Function Expression with implicit return value](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#Function_body)

```js
let add = (x,y) => x + y;
```

* Note that these new forms are *anonymous*, meaning there is **no name** between `function` and `(x,y)`
    * the name of the function **is** the name of the variable that points to it
