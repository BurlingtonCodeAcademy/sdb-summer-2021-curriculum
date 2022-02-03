# Loops

Computers are like robots. They are good at doing things over and over and over and over again.

A **loop** is a statement used to repeatedly execute a _code block_. There are different kinds of loops, so we can repeat code blocks in different patterns.

The _expressions_ in loop statements provide information like when to start, stop, and what to do between repetitions.

---

# The While Loop

The simplest loop in JavaScript is `while`. It has the same structure as an `if` statement: `keyword ( Boolean expression ) { code block } `

```js
while (true) {
  someAction();
}
```

Why does a `while` _loop_ need an expression? How does `while` use it?

---

# Common Looping Mistake: Infinite Loops

If the expression never evaluates to `false`, it will run forever:

```js
while (true) {
  console.log("Hello");
}
```

To stop an operation in your terminal, hold down the `control` and `C` keys. Mac/Windows doesn't make a difference in this case.

Is it possible for an expression or variable to result in an infinite loop? What steps can you take to troubleshoot?

---

# Different Kinds of Loops

`while` loops are the simplest type of loop, but it's not the only kind.

Some examples of other loops:

- `for`
- `for...in`
- `do...while`

These other loop options build on the original `while` loop structure.

---

# Different Kinds of Loops Cont.

Let's use the most common loop, a `while` loop and a `for` loop to count to 10:

```js
let count = 0;
while (count < 11) {
  console.log(count);
  count = count + 1;
}
```

```js
for (let count = 0; count < 11; count++) {
  console.log(count);
}
```

Explore: What is the difference between `count++` and `count = count + 1`?

---
