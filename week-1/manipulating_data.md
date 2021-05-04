# Let's Write Some Code!

Open up your terminal and follow along. Let's play with some data!

![data from Star Trek]()

---

# Values

- A *value* is a location in computer memory that stores *data*.
- There are many kinds of values, including String, Number, Array, Date, ...
- Different flavors of data are referred to as different *Types*

---

# Primitive Data Types

- Numbers
- Strings
- Booleans
- Null
- BigInt
- Symbol

> [Data Types ~MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

---

# A Programmer's Best Friend

- You will often run into problems your not sure how to solve
- Don't be afraid to Google things, we all do it!
- Try to explain the problem with regular words
  - put the question you ask directly into google
  - pay attention to the dates articles were published
  - look for notoriously good sites:
    - MDN
    - Stack Overflow
    - Medium
    - Dev.to
    - ...and many more

> You can't always get what you want, but if you try sometimes you just might find you get what you need ~The Rolling Stones

---

# Numbers

A **number** is what it sounds like -- any integer or decimal.

```js
10
-12
3.14
```

- Many programming languages make a distinction between integers, and decimals
- JavaScript doesn't
- This can lead to some ...odd behaviors

---

# The Math Class

- In JavaSCript there is a class called `Math` (More on classes and Objects later)
- It helps with mathematical operations
- Often used to round numbers, or set them to a certain number of decimal places
- Can be used to generate random numbers

---

# Off by One Errors

- As people we want to start counting from 1
- But computers want to start counting at 0
- One of the most prevalent types of errors in programming is the "off by one" error
- The fix is easy, just add or subtract 1!

---

# Strings

A **string** is an object that's a collection of characters, like a word or a sentence.

```js
"apple"
"banana"
"Cherry Pie"
```

# Slicing and Dicing

Every string is made of lots of other strings.

You can pull out parts of a string with the `slice` method.

```js
// this means "slice from character 0 to character 4"
"blueberry".slice(0, 4) 

// this means "slice from character 4 to the end
"blueberry".slice(4)
```

These start and end numbers are called *indexes* (or *indices* if you're feeling fancy).

[MDN: slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice)

---

# String Indexing

Humans like to start counting at 1, but computers like to start counting at 0.

Think of the indexes as pointing at the *spaces between* characters, as in this diagram:

    | B | L | U | E | B | E | R | R | Y |
    0   1   2   3   4   5   6   7   8   9
     
So with this picture in your mind, `slice`...
  
   * includes the character to the *right* of the start index
   * includes the character to the *left* of the end index...
   * ...but *excludes* the character to the *right* of the end index

Try various start and end values in the console and see what happens!

---

# Booleans

A **boolean** is a value that is either true or false, and is represented in JavaScript with the keywords `true`, and `false`.

- Many operations return booleans and are used to run code conditionally (more on that later)

- Pretty much any data in JavaScript can be evaluated as a boolean

- often we use implicit truthy, or falsy values instead of the actual keywords `true` and `false`

(It's named after *[George Boole](https://en.wikipedia.org/wiki/George_Boole)*, 
a 19th-century mathematician who invented [Boolean algebra](https://en.wikipedia.org/wiki/Boolean_algebra).)

---

# Booleans and Conditionals

Let's look ahead a little bit and use a simple conditional to evaluate various values. A conditional starts with the keyword `if` then takes a check in parentheses `if('some condition')` and finally a block of code defined by curly braces which only runs if the check evaluates to `true`

Don't worry too much about how conditionals work right now, we'll go into a lot more depth in them later on. For now just use the conditional given on the next slide to complete the lab, swapping out the check for different values to answer the questions

---

# Code Along: Is it True?

Given this conditional answer the following questions. If the check (currently the boolean `true`) is true it will print `It is truthy` to the console, otherwise nothing will print.

Give me your best guesses to the questions below!

```js
if(true) {
    console.log('It is truthy')
}
```

* Is the boolean `true` truthy?
    * how about `false`?
* What if we replace the boolean `true` with a string?
    * Is it truthy?
* What if we replace the boolean `true` with a number?
    * Is it true?
    * What about the number `0`?
* What if we replace the boolean `true` with the expression `1 < 2`?
    * What happens if you switch the operator like so `1 > 2`?

---

# Operators

Values can be combined or manipulated using **operators**, like...
 
 * PLUS (`+`)
 * TIMES (`*`)
 * POWER (`**`)
 * DOT (`.`)
 * ASSIGNMENT (`=`)
 * COMPARISON (`===`)

An operator *sends a message* to the value

  * e.g. `1 + 2` sends the number `1` the message `please add 2 to yourself`.

Dot is a special operator that *sends arbitrary messages*; we will learn more about that later.

---

# Types of Operators

Like data there are several different *types* of operators

- Assignment
- Comparison
- Arithmetic
- Logical
- Conditional
- and some [less frequently ones](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)

---

# Comments

When reading JavaScript code, if you ever see two slashes in a row, that means "everything after these slashes is a comment".

```javascript
2 + 2    // makes four
```

A comment is a message for humans. JavaScript ignores everything to the right of the slashes, so you can explain what the nearby code does, or why it does it.

In these lessons, we often use comments to explain the *result* of executing the nearby code. In this case, we sometimes add an arrow to the comment:  

```javascript
2 + 2  //=> 4
3 + 5 // -> 8
```

> JavaScript also has multi-line comments via `/* ... */` but those are less common. They can also be used to comment out a section within a line:  

```javascript
/* This is
 * a multiline
 * comment! */

 console.log(x /*some variable from earlier*/);
 ```

 ---

# Expression Evaluation

A snippet of JavaScript code is called an *expression*.

Whenever JavaScript encounters an expression, it tries to *evaluate* it, which means to convert it into a *value*.

A simple expression (like a plain number or a string) evaluates to just that value.

A more complicated expression with operators keeps applying those operators until it gets down to a single value. 

> You can think of evaluation as *asking and answering* a question.

---

# Expression Examples

```javascript
2 + 2    // Question: What is 2 + 2?
4        // Answer: 4

// Q: What is the all-caps version of the string "apple"?
"apple".toUpperCase()  
// A: the string "APPLE"
"APPLE"
```

We say that a statement **evaluates to** a value, as in
"2 plus 2 *evaluates to* 4". You can also say "the value of 2 + 2 is 4" or "the return value of 2 + 2 is 4".

---

# Return Values

Sometimes the return value is the same as the original value.

```js
4 * 1    // return value: 4
```

Sometimes the return value is a different value.

```js
2 + 3    // return value: 5
```

Sometimes the return value is a different value *and* a different type.

```js
"banana".length  // return value: 6
```

Sometimes the return value is a special value!

```js
(5).length     // return value: undefined
5 / 0          // return value: Infinity
"cookie" * 10  // return value: NaN
```

---

# Sidebar: Expressions vs. Statements

JavaScript (like most languages derived from C) makes a distinction between *expressions* and *statements*.

*expression* means "code that can be evaluated" or "code that has a value", e.g.:

    1 + 1

*statement* means "code that does something", e.g.:

    console.log("hello");

Some statements have values, so `node` will *evaluate* them and *print* those values...

```javascript
> 1 + 1
2
```

...but *some statements have no value* (even though they contain expressions that *do* have value), and this can cause some surprising effects, e.g.:

```javascript
> x = 10
10
> let x = 20
undefined
```

---

# Expression vs Statement Breakdown

|Expression | Statement |
|---|---|
|has a value	| does something |
|can be assigned to a var|	has a semicolon (optionally) |
|		|		contains expressions |



Read more here: (https://medium.com/launch-school/javascript-expressions-and-statements-4d32ac9c0e74)
    
