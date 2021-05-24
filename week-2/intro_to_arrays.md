# Arrays

* An array is a *collection*
  * an object that contains any type of value
* It's a list of items
* An array is a *data structure*

---

# What Makes an Array an Array

* You can put any values inside it
* In any order
* They stay in order (unless you move them later)
* Duplicates are fine

---

# Creating an Array

```js
let fruits = ["apple", "banana", "cherry"]
```

* square brackets on their own mean "please go *create* an array now"
* and put these 3 other values inside it

---

# Array Indexes

* Every slot in the array has an index
* You can retrieve any item in an array by its INDEX
* Square brackets after an array mean "the whatever-th item in this array"
  * This method of accessing items is referred to as "square bracket notation"
* The following code retrieves one fruit

```javascript
let fruits = ["apple", "banana", "cherry"];
fruits[1]
```

...but which fruit?

---

# Start At Zero

* When counting,
* humans start at one,
* but **computers start at zero**.
* So the first item in an array is the number `0`, 
  * not the number `1`.

---

# Length

Every array has a *property* named `length`

```js
let fruits = ["apple", "banana", "cherry"]
fruits.length //=> 3
```

Q: How can you get the last item in an array... even if you don't know its index beforehand?

---

# The End

You usually won't know how long an array is when you're writing functions, or programs that deal with user input. In these cases we'll have to figure out the length of the array programmatically and count backwards from there

```js
let fruits = ["apple", "banana", "cherry"]
fruits[fruits.length - 1]
```

* `fruits.length` evaluates to the number `3`
* then we subtract 1 to get the last index of the array (`2`) because arrays are 0 indexed
* Using an expression as value is not particular to arrays
  * Because JavaScript evaluates expressions *first* it's a common pattern

---

# After The End

Try this:

```js
fruits[99]
```

Did you get the result you expected?

Why or why not?

---

# Undefined Means 🤷

By returning *undefined*, the computer is answering the question

> "What is the 99th item?"

with the answer

> "I don't know what the 99th item is."

---

# Setting Items in an Array

The `[]` operator works for assignment as well.

`fruits[0] = 'apricot'` will set the `0`th item of the array to the string `'apricot'`

---

# Array Methods

There are many useful methods on arrays. We'll cover many of them in more depth later today.

For now let's look at some of the most common array methods:

* `push`/`shift`
* `pop`/`unshift`
* `reverse`
* `slice`
* `join`
* `split`

---

# Adding Items

* `.push` adds a value to the end of an array

```javascript
let fruits = ["apple", "banana", "cherry"]
fruits.push("pineapple")
fruits //=> ["apple", "banana", "cherry", "pineapple"]
```

* `.push` can also add several values at once

```javascript
fruits.push("nectarine", "strawberry")
fruits //=> ["apple", "banana", "cherry", "pineapple", "nectarine", "strawberry"]
```

> `.push` returns the new length of the array

---

# Removing Values from an Array

To remove a value from the end of an array you can use the `.pop` method

- `.pop` always removes the last item in the array
- `.pop` takes no arguments
- `.pop` can only ever remove one item at a time, and it's **always** the last item in the array
- `.pop` returns the item that was removed. THis means you can use it for variable assignments!

```js
let fruits = ["apple", "banana", "cherry"]
let lastFruit = fruits.pop()
fruits // => ["apple", "banana"]
lastFruit // => "cherry"
```

---

# Yarra Lasrever

```js
let fruits = ["apple", "banana", "cherry"]
fruits.reverse()
```

Try this now in a console. Do you see what you expect?

---

# Slicing and Dicing

you can `slice` an array to cut it into smaller arrays, a lot like how you can slice a string to get a smaller string.

```js
let fruits = ['apple', 'banana', 'cherry', 'date', 'elderberry']

// this means "slice from item 1 to item 3"
fruits.slice(1, 3) //=> [ 'banana', 'cherry' ]

// this means "slice from item 2 to the end"
fruits.slice(2) //=> [ 'cherry', 'date', 'elderberry' ]
```

These start and end numbers are called *indexes* (or *indices* if you're feeling fancy).

If you need an item from a middle index you can use `.slice` to access it.

[MDN: slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

---

# Array Indexing Explained

Array indexing works in the same way as string indexing.

Think of the indexes as pointing at the *spaces between* items, as in this diagram:

```js
0   1   2   3   4
| B | L | U | E |
['B','L','U','E']
```

So with this picture in your mind, imagine that `.slice`...

   * includes the item to the *right* of the start index
   * includes the item to the *left* of the end index...
   * ...but *excludes* the item to the *right* of the end index

---

# Array to String

There are a few easy ways to turn an array into a string.

So we could take the following array:

```js
let fruits = []
```

and 

```js
fruits.join()           // 'apple,banana,cherry'
fruits.join(" and ")    // 'apple and banana and cherry'
fruits.toString()       // 'apple,banana,cherry'
```

---

# String to Array

You can also easily turn a string into an array with the `.split` method.

This method will give you an array of strings split on whatever character you passed to `.split`.

So if we use the string we got from `.join` on the previous slide we could turn it *back* into an array

```javascript
'dog'.split('') //=> ['d', 'o', 'g']
'my dog has fleas'.split(' ') //=> [ 'my', 'dog', 'has', 'fleas' ]
```

This will work with any string.

> Note also that the character you're splitting on gets removed.
