# Variables

- A **variable** is a **name** for a value.
- You give a value a name using the **assignment** operator 
    - It looks like an equal sign but is *not* a comparison.
    - often preceded by `let` as in "Let there be light" or "Let X equal 10".

```js
let color = "blue"
let fruit = "berry"
```

* Anywhere you would use a literal value, you can use a variable instead.

```js
color + fruit       // "blueberry"
fruit.toUpperCase() // "BERRY"
```

* ...so pick good names :-)

---

# Let there be confusion

* `let` is just one way to declare a variable in JavaScript
* `var` is a lot like `let` but has wider *scope* which is sometimes bad
* If you don't use either `let` or `var` then the variable becomes *global* (which is dangerous)
* Moral: *always use let* unless you have a good reason not to

---

# Don't let me down 

In JavaScript you can only use `let` once per variable name (in a given *scope*), otherwise you will get an error:

```js
Identifier 'x' has already been declared
```

That means that when you're in the JavaScript console, if you see this error then try again without the `let`

```js
> let x = 1
undefined
> let x = x + 2
SyntaxError: Identifier 'x' has already been declared
> x = x + 2
3
```

* also confusing: the value of a `let` is `undefined`, but the value of a normal assignment is the value being assigned

---

# Variables are documentation

Which is clearer, this:

```js
60 * 60 * 24
```

or this:

```js
let secondsPerMinute = 60
let minutesPerHour = 60
let hoursPerDay = 24
let secondsPerDay = secondsPerMinute * minutesPerHour * hoursPerDay
```

?

---

# The Pointer Metaphor

```js
let snack = "Apple"
```

![snack-apple](https://res.cloudinary.com/btvca/image/upload/v1574445202/curriculum/snack-apple_ltysdv.svg)

Think of a variable as an arrow **pointing** to a value.

---

# Changing Variables

You can assign and reassign variables at will.

```js
let color = "blue"     // assign 'blue' to color
let fruit = "berry"    // assign 'berry' to fruit
color + fruit      // 'blueberry'

color = "black"    // 'black'
color + fruit      // 'blackberry'
```

*Reassignment* only changes the name of an object. It does *not* change the data inside the object.

This is analogous to removing a label from one box and placing it on a different box.

---

# Many pointers can point to the same thing

```js
let fruit = "Apple"
let snack = fruit
```

![snack-fruit](https://res.cloudinary.com/btvca/image/upload/v1574445202/curriculum/snack-fruit_momdep.svg)

After this both `snack` and `fruit` are *pointing* to the same *value*

This is analogous to placing two labels on the same box.

---

# Return Values Are New

Most messages return *new* values:

```js
let fruit = "banana"
let snack = fruit.toUpperCase()
```

![fruit-banana-snack-banana](https://res.cloudinary.com/btvca/image/upload/v1574445175/curriculum/fruit-banana-snack-banana_fbbd8h.svg)

`"banana"` and `"BANANA"` are two *different values* in memory. The value of `fruit` is still "banana".

---

# Changing Values

Most messages do not change the data, instead they return a new piece of data.

```javascript
let color = "blue"
color.toUpperCase()     // "BLUE"
color                   // "blue"
```

This is true for all strings, since strings in JavaScript are *immutable*. Any message that transforms a string will return you an entirely new string.

But some messages **do** change the contents!

---

# Constants: Variables that Aren't Variable

* the keyword `const` is just like `let`, but also *prevents reassignment*

```javascript
const pi = 3.14159;
```

* the value of a `const` is *constant* after it's been set once
  * if you try to change it, you get an error

```javascript
pi = 7;
TypeError: Assignment to constant variable.
```

> WARNING: `const` prevents *reassignment* but does not prevent changing the *insides* of objects or arrays.

---

# Scope

All variables are defined within a certain scope. The easiest way to recognize something is in a different scope is to pay attention to the levels of indentation.

An item that is indented, when your code is properly formatted, is in an *interior* scope. Any time you open a set of curly braces it opens a new scope, and code written inside it should be indented. Remember to format your documents often!

Scope is like a one way mirror; you can always look out, to exterior scopes, but you can never look into interior scopes.

---

# Summary: Variables

* variables are names for memory locations, which hold values
* *declaring* a variable says what its *scope* is
* *assigning* a variable changes which location it points to
* you can have many names for the same location
* sometimes values can change on the inside of a location
  * (which is useful but could cause bugs)
