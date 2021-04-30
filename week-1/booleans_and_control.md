# Null

*null* is the value that means "there is no value"

> Q: What is the sound of one hand clapping?

> A: `null`

---

# Null Values

JavaScript has several null values (a.k.a. empty values). This can be a bit confusing

* `null` means "nothing"
* `undefined` means "i don't know"
* `NaN` means "not a number"
* `''` means "an empty string"

Docs: [MDN: null](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null)

---

# Null is useful

Null is used in cases where "nothing yet" is a valid scenario.

For instance, if a user has an account, but doesn't (yet) have a profile picture, `account.profilePic` may be `null`.

Then you can test for that case, e.g.

```js
if (account.profilePic === null) {
    showDefaultPicture();
} else {
    showPicture(account.profilePic);
}
```

---

# Null is dangerous

```js
let fruit = null
fruit.toUpperCase()
```

> Let's *Read the error!*

---

# Errors are good

They tell you

* you made a mistake
* what that mistake was
* (sometimes) how to fix it

Please try to interpret this error:

```js
fruit.toUpperCase()
TypeError: Cannot read property 'toUpperCase' of null
```

# TypeError explained

```js
fruit.toUpperCase()
TypeError: Cannot read property 'toUpperCase' of null
```

---

# Error Explained

* "`TypeError`" means "this is an error about data types" -- you thought you were using a string, but you weren't -- you were actually using `null` which is *not* a string

* "`Cannot read property 'toUpperCase'`" means "you asked the value for a property named `toUpperCase` but there was no such property"

* `of null` means "the value you were using was null"

This error is confusing because it *buries the lede* -- you must read all the way to the end before you find the relevant clue ("`null`"), and it *omits* the name of the variable whose value was null ("`fruit`").

Sadly, it is your job as a programmer to translate "TypeError: Cannot read property 'toUpperCase' of null" into "We expected the variable `fruit` to contain a string, but it contained `null` instead."

---

# Null Pointer Errors

* null pointer errors are fairly common
* the trick is reading the error and figuring out
    1. *where* it happened (*which line*)
    2. *which variable* was null
    3. *why* it was null
* often once you know *which*, knowing *why* is obvious
    * but sometimes it's a puzzle and you have to trace back
    * e.g. the original problem was when *fruit was set to `null`*, but the error happened later, when the program tried to *use* `null` as if it were a string

---

# If You're Going To Fail...

Two failure recovery philosophies:

* fail fast, fail hard
* keep calm and carry on

Which idea is better?

Why or why not?

---

# Failure Recovery

*graceful* - generally good for users

  * provide information and context in non-technical language
  * help user accomplish their goal
  * allow user to try again immediately

*fail-fast* - generally good for coders

  * exposes errors early
  * forces you to think through "rainy day" scenarios
  * provides information about the state of the program at the moment the error happened

  ---

# Nulls are falsy

All of the empty values in JavaScript are *falsy*, so they will cause an `if` statement to fall through. This allows the code from the earlier example to be written concisely

```js
if (user.profilePic) {
    showPicture(user.profilePic);
} else {
    showDefaultPicture();
}
```

---

# Truthiness

Computers have a very particular idea of when things are *true* and *false*.

To a computer **everything** is one or the other.

---

# Comparisons

*Comparison operators* let you compare two values. JavaScript has all the usual suspects...

|Operator|Comparison|
|---|---|
| `<` | less than |
| `>` | greater than |
| `<=` | less than or equal to |
| `>=` | greater than or equal to |
| `==` | equal to |
| `!=` | not equal |
| `===` | *really* equal to |
| `!==` | *really* not equal to |

[MDN: comparison operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)

These are also called "Boolean operators" after *[George Boole](https://en.wikipedia.org/wiki/George_Boole)*,
a 19th-century mathematician who invented [Boolean algebra](https://en.wikipedia.org/wiki/Boolean_algebra).)

---

# Conditions

The keyword `if` sets up a *conditional* statement.

The phrase immediately after `if` is a *condition*.

```js
if (age < 18) {
  console.log("Sorry, you can't vote yet.");
}
```

|phrase|meaning|
|---|---|
| `if (` ... `)`      | **if** this condition's value is *truthy* |
| `{` ... `}`         | **then** run this block of code |

Wait a second. "Truthy?"

[MDN: if...else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)

---

# What is truthiness?

![Truthiness](https://res.cloudinary.com/btvca/image/upload/v1574445211/curriculum/truthiness_jhdubk.png)

* in the Colbert Report, [truthiness](https://en.wikipedia.org/wiki/Truthiness) means things we *feel* to be true, even though we know they're probably not

* In JavaScript, **all** values have truthiness **unless** they are defined as falsy.

* [MDN: Truthy](https://developer.mozilla.org/en-US/docs/Glossary/Truthy)

---

# What is falsiness?

`false`, `null`, `undefined`, `0`, `NaN`, and the empty string (`""`) are all falsy values.

These are also the *only* falsy values in JavaScript.

Fortunately, `true` is truthy and `false` is falsy.

Unfortunately, the string `"false"` is truthy, and the string `"0"` is truthy, even though the number `0` is falsy. This is because the string contains a character, and, even though the character is `0`, any string with at least one character is truthy.

[MDN: Falsy](https://developer.mozilla.org/en-US/docs/Glossary/Falsy)

---

# The Tragedy of the Equal Sign

* a single equal sign means ASSIGNMENT
  * `name = "Alice"` -- "assign the value 'Alice' to the variable 'name'"
* two equal signs means COMPARISON
  * `name == "Alice"` -- "does the variable 'name' contain the string 'Alice'?"

> This is confusing! (More about it on the next slide.)

---

# A Notorious Bad Idea

> "A **notorious example for a bad idea** was the choice of the equal sign to denote assignment. It goes back to Fortran in 1957 and **has blindly been copied by armies of language designers**. Why is it a bad idea? Because it overthrows a century old tradition to let "=" denote a comparison for equality, a predicate which is either true or false. But Fortran made it to mean assignment, the **enforcing** of equality... `x = y` does not mean the same thing as `y = x`."
>
> — [Niklaus Wirth](https://en.wikipedia.org/wiki/Niklaus_Wirth), Good Ideas, Through the Looking Glass (2005)

see also http://en.wikipedia.org/wiki/Assignment_%28computer_science%29#Assignment_versus_equality

---

# Condition or Assignment?

> BEWARE of using a single equal sign inside an `if` condition!

* the value of a comparison is either `true` or `false`
  * so `if (x == 2)` means `if x is 2` which changes based on `x`

* the value of an assignment is the *value being assigned*
  * so `if (x = 2)` means `if 2` which is *always truthy*
  * also, the value of `x` will be 2 afterwards, no matter what it was before

---

# The Tragedy of the Threequal Sign

In addition to `=` and `==`, JavaScript also has `===`.

That's three equal signs in a row.

|Operator|Operation|Example|Meaning|
|---|---|---|---|
| `=`   | assignment         | `X = Y`  | let X equal Y |
| `==`  | comparison (fuzzy) | `X == Y` | does X *mostly* equal Y? |
| `===` | comparison (exact) | `X === Y`  | does X *really* equal Y? |

`==` means "does X equal Y, or if not, can Y be *converted* into something that equals X?"

Since the rules for type conversion are confusing, most JavaScript experts recommend:

> always use `===`, never use `==`

> Using `==` can have some very interesting side effects, see [Stackoverflow](https://stackoverflow.com/questions/359494/which-equals-operator-vs-should-be-used-in-javascript-comparisons)

---

# if... then... else...

The magic word `else` allows **BRANCHING**.

```js
if (age >= 18) {
  console.log("allowed");
} else {
  console.log("denied");
}
```

Like a fork in the road, the program chooses one path or the other.

It takes the first path if the condition is truthy, and takes the second path if the condition is falsy.

---

# Conjunction Junction

You can make more complicated logical expressions using conjunctions:

|Conjunction|Operator|Example|Meaning|
|---|---|---|---|
| AND | `&&` | `X && Y` | "are both X and Y true?" |
| OR | <code>&#124;&#124;</code> | <code>X &#124;&#124; Y</code> | "is either X or Y (or both) true?" |
| NOT | `!`  | `!X` | "is X false?" |

For example:

```js
if (age >= 18 || hasPermissionSlip()) {
  console.log("allowed");
} else {
  console.log("denied");
}
```

[MDN: logical operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators)