# Arrays In Depth

Arrays are very useful data structures.

* They can contain any type of data
* They're ordered
* They have many inherent methods for manipulating the data they contain.

Let's take a closer look at a few of these iteration methods!

---

# Looping Through an Array with for-of

Recently, JavaScript added `for..of`, which hides the messy details of incrementing an index counter and accessing each array item.

```js
for (let fruit of fruits) {
  console.log("I like " + fruit + "!")
}
```

|phrase|meaning|
|---|---|
| `for`                    | in a loop, |
| `of fruits`              | take each thing inside `fruits` |
| `let fruit`              | name it `fruit` |
| `{` ... `}`              | and send it to this block of code |

---

# Iteration Methods

Every JavaScript array has a few [very handy methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Iteration_methods)
that let you *apply a function* to its contents.

| method | description | returns |
|---|---|---|
| [`forEach`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)  | do something to each item | `undefined`|
| [`find`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)  | find the first item that matches | one matching item (or `undefined` if no match) |
| [`filter`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) | accept or reject each item | a new collection, possibly smaller |
| [`map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)  | change each item into a new item | a new collection of the same size |
| [`reduce`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)  | scan the entire collection and "reduce" it to... | ...a single result, e.g. a total |

* We call this group of methods "[iteration methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Iteration_methods)"
* There are about a dozen built-in iteration methods, plus lots more added by libraries like [lodash](https://lodash.com/).

---

# forEach

`forEach` works a lot like `for..of`, but using a callback function

Given this array of names...

```javascript
let names = ['Alice', 'Bob', 'Carol', 'Charlie']
```
This code...

```js
function printUpper(name) {
  console.log(name.toUpperCase())
};

names.forEach(name => printUpper)
```

prints:

```text
ALICE
BOB
CAROL
CHARLIE
DAVID
```

---

# Find

To find the first item that matches the condition...

```javascript
let names = ['Alice', 'Bob', 'Carol', 'Charlie'];

let beginsWithC = function(word) {
  return word.charAt(0).toUpperCase() === 'C';
};

let cName = names.find(beginsWithC); //=> 'Carol'
```

Note that:

* the `beginsWithC` function returns `true` or `false`
* the `.find` method returns an item (from the array)
  * that causes `beginsWithC` to return `true`

---

# Find Inline

For conciseness, people often define the filter function *inline*, like this:

```javascript
let cName = names.find(function (word) {
    return word.charAt(0).toUpperCase() === 'C'
  }
);
```

Is this more or less clear than the previous slide?

---

# Filter

the `.filter` iteration method returns *all* matching values, in a *new array*

```javascript
let names = ['Alice', 'Bob', 'Charlie', 'Carol'];

let beginsWithC = function(word) {
  return word.charAt(0).toUpperCase() === 'C';
};

let cNames = names.filter(beginsWithC); //=> [ 'Charlie', 'Carol' ]
```

---

# Map

The `.map` iteration method returns a *new array* whose elements correspond to the elements of the original array.

```javascript
let names = ['Alice', 'Bob', 'Charlie', 'Carol'];
let upper = function(word) {
  return word.toUpperCase();
}
let bigNames = names.map(upper) //=> [ 'ALICE', 'BOB', 'CHARLIE', 'CAROL']
```

It's called "map" because in a mathematical sense, it defines a *mapping* from one collection to another.

| from | to |
|---|---|
| 'Alice'| 'ALICE' | 
| 'Bob'| 'BOB' |
| 'Charlie' | 'CHARLIE' |
| 'Carol' | 'CAROL' |

---

# Method Chaining

* **method chaining** is the practice of taking the **result** of one method, and immediately calling a method on that result **without assigning it to a variable**, again and again until you get a final result.
* Method chaining can be very elegant, but it can also be very dense, making the code harder to understand, test, and debug.
* "Unspooling" a method chain into intermediate variables can make the code easier to follow, but it can also make it much more verbose and obscure the algorithm.
* For example; we could take the results of a `filter` method, and *chain* a `map` method off it to return a modified subset of an array.

---

# Reduce

The `reduce` method keeps track of a *running total* (aka *accumulator* or *memo*); whatever value the function returns is used as the accumulator for the next pass.

Here's some code that counts the total number of letters across all words in an array:

```javascript
let numbers = [17, 3, 2, 20];

const reducer = function(accumulator, nextNum) {
  return accumulator +nextNum;
};

let totalCount = numbers.reduce(reducer, 0); //=> 42
```

---

# Reduce Explained

The `reduce` algorithm can be difficult to follow at first; here's a walkthrough:

| Iteration | Accumulator In | Word | Length | Accumulator Out |
|---|---|---|---|---|
| 1 |  0 | 'Alice'   | 5 | 0 + 5 = 5 |
| 2 |  5 | 'Bob'     | 3 | 5 + 3 = 8 |
| 3 |  8 | 'Charlie' | 7 | 8 + 7 = 15 |
| 4 | 15 | 'Carol'   | 5 | 15 + 5 = 20 |
| 5 | 20 | 'David'   | 5 | 20 + 5 = 25 |

The accumulator is used to pass information from one iteration to the next.

---

# Code Along: Enemies List Refactoring

Refactoring is changing existing code so that it *works* the same, but is cleaner and easier to read.

Let's go back to the old Hello Frenemy Input lab, and use arrays to make it a little bit cleaner!
