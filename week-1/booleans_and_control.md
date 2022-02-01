# Null

We briefly discussed _null_ when first learning about [manipulating data](https://online.uprighted.com/lessons/slides/manipulating-data).

Do you remember what it represents?

---

# Synonyms for Null

Null is just one way developers might express the concept of "none".

Here are some you'll come across in your career:

> |           |                                                  |
> | --------- | ------------------------------------------------ |
> | null      | none<br/>nothing<br/><br/>                       |
> | undefined | can't be found<br/>has never been made<br/><br/> |
> | NaN       | **N**ot **A** **N**umber<br/><br/>               |
> | ''        | No response                                      |

[Mozilla Developer Network | null](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null)

---

# Using Null with Conditionals

Null is often used as a default value when storing data on the backend.

For instance, if a user has an account, but doesn't (yet) have a profile picture, `account.profilePic` may be `null`.

This allows us to make decisions based on this knowledge.

```js
if (account.profilePic === null) {
  showDefaultPicture();
} else {
  showAccountPicture(account.profilePic);
}
```

---

# Comparisons

_Comparison operators_ let you compare two values. JavaScript has all the usual suspects...

| Operator | Comparison               |
| -------- | ------------------------ |
| `<`      | less than                |
| `>`      | greater than             |
| `<=`     | less than or equal to    |
| `>=`     | greater than or equal to |
| `==`     | equal to                 |
| `!=`     | not equal                |
| `===`    | _really_ equal to        |
| `!==`    | _really_ not equal to    |

[Comparison operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators) are also called "Boolean operators" after _[George Boole](https://en.wikipedia.org/wiki/George_Boole)_,
a 19th-century mathematician who invented [Boolean algebra](https://en.wikipedia.org/wiki/Boolean_algebra).)

---

# Using If Statements to Set Up Conditions

- If statements follow the typical statement structure covered thus far:
```js
keyword ( expression ) { codeBlock }
```
- Here, the expression is used run the code block _only under certain conditions_
- If the expression is **truthy** or `true`, the code block will happen
- If it is **falsy** or `false`, the computer skips the code block and moves on

```js
if (age < 18) {
  console.log("Sorry, you can't vote yet.");
}
```

[Mozilla Developer Network | if...else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)

---

# Truthy and Falsy

If statements force the computer to decide if a value is `true` or `false`.

But what if you put some other data type? A string, an array, a number, etc.

Then, the computer will figure out if that value is closer to true (_truthy_)
or closer to false (_falsy_)

[Mozilla Developer Network | Truthy](https://developer.mozilla.org/en-US/docs/Glossary/Truthy)

---

# Truthy and Falsy Cont.

Most values are _truthy_, so it's more important to recognize _falsy_ values:

1. `false`
2. `null`
3. `undefined`
4. `0`
5. `NaN`
6. `""`

What do notice about these values?

[Mozilla Developer Network | Falsy](https://developer.mozilla.org/en-US/docs/Glossary/Falsy)

---

# Truthy and Falsy Practice

Are these values _truthy_ or _falsy_?

- `"false"`
- `0`
- `"0"`
- `[]` **\***
- `undefined`

[\* More on this example](https://www.nfriedly.com/techblog/2009/07/advanced-javascript-operators-and-truthy-falsy/)

---

# Using Else Statements

The keyword `else` allows you to run a _code block_ when the conditional _expression_ is _falsy_ or `false`.

```js
if (false) {
  console.log("🍕");
} else {
  console.log("🍔");
}
```

Which code block will _execute_?

---

# Not Using Else Statements

How does this behave differently...

```js
if (false) {
  console.log("🍕");
} else {
  console.log("🍔");
}
```

... from this?

```js
if (false) {
  console.log("🍕");
}

console.log("🍔");
```

---

# Conjunction Junction

You can make more complicated logical expressions using conjunctions:

| Conjunction | Operator                  | Example                       | Meaning                          |
| ----------- | ------------------------- | ----------------------------- | -------------------------------- |
| AND         | `&&`                      | `X && Y`                      | "are both X and Y true?"         |
| OR          | <code>&#124;&#124;</code> | <code>X &#124;&#124; Y</code> | "is at least one of these true?" |
| NOT         | `!`                       | `!X`                          | "is the opposite of X true?"     |

Which code block will _execute_?

```js
if (true || false) {
  console.log("🍕");
} else {
  console.log("🍔");
}
```


<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators">Mozilla Developer Network | Logical Operators</a>


---
