# Advanced Data Types

When learning about manipulating data, we learned about the "simple" data types.

In this lesson, we'll be discussing the more complex type data type: **Objects**.

You may have noticed that all the data types we've seen so far are individual items:

```js
"a string", 10, true;
```

What do we do if we have multiple values though?

---

# Arrays

```js
let arrayExample = [
  1,
  "string",
  true,
  function () {
    console.log("yes, you can have a list of functions");
  },
  [
    "oh no",
    "we can have arrays in arrays?",
    ["in arrays in arrays in arrays?", "yes 😭"],
  ],
];
```

- Arrays are a special kind of **Object**
- We use it to store a list of values together
- **The list keeps its ordering**
- This list can be reordered however you'd like
- Duplicates are allowed (some more advanced JavaScript tools automatically take duplicates out)

---

# Array Syntax

You can make an array using `[ ]`, known as square brackets.

```js
let emptyArray = [];

let fruits = ["apple", "banana", "cherry"];
```

---

# Array Indexes

- Arrays, like Strings, are also indexed and begin at 0
- We use indexes to refer to individual values stored within the array
  - e.g. `arrayExample[0]` gets the first item of arrayExample
  - This method of accessing items is referred to as "square bracket notation"

```javascript
let fruits = ["apple", "banana", "cherry"];
fruits[1];
```

Which value does this code access?

---

# Length

Because an array is a kind of Object (more on these later), they have **properties**.

- These are values held within Objects to help you manipulate them.
- All arrays come with a property called `length`.

```js
let fruits = ["apple", "banana", "cherry"];
fruits.length; // => 3
```

How can we use this information to help us get the last value of an array without knowing its exact index?

---

# Literacy Practice: Dynamically Accessing the Last Index

We will often build programs using data we do not personally manage or create.
This means we usually will _not_ know the details of what the values are, how many there are, etc.

```js
let fruits = ["apple", "banana", "cherry"];
fruits[fruits.length - 1];
```

- How does this work? What is happening on the last line?
- What happens if we try to access index `99`?

---

# Adding Values to an Array

Before, we used _square bracket notation_ to "read" values from the array.

Now, we are using it with the assignment operator `=` to add or "write" values to the array.

`fruits[0] = 'apricot'` will set the `0`th item of the array to the string `'apricot'`

How is this similar to variables?

---

# Array Methods

Before, we covered the property length, which returns a `Number` every time.

Arrays also have properties called **methods** that are functions held within them.

These functions allow you to manipulate the array in a wide variety of ways.

For now let's look at some of the most common array methods:

- `push`/`shift`
- `pop`/`unshift`
- `reverse`
- `slice`
- `join`
- `split`

---

# Adding Values to the Right Side

- `.push` adds a value to the end of an array

```js
let fruits = ["apple", "banana", "cherry"];
fruits.push("pineapple");
fruits; //=> ["apple", "banana", "cherry", "pineapple"]
```

- `.push` can also add several values at once

```js
fruits.push("nectarine", "strawberry");
fruits; //=> ["apple", "banana", "cherry", "pineapple", "nectarine", "strawberry"]
```

> `.push` returns the new length of the array

---

# Removing Values from the Right Side

To remove a value from the end of an array you can use the `.pop` method

- `.pop` always removes the last item in the array
- `.pop` takes no arguments
- `.pop` can only ever remove one item at a time, and it's **always** the last item in the array
- `.pop` returns the item that was removed. THis means you can use it for variable assignments!

```js
let fruits = ["apple", "banana", "tangerine"];
let lastFruit = fruits.pop();
fruits; // => ["apple", "banana"]
lastFruit; // => "tangerine"
```

---

# Slicing and Dicing

You can `slice` an array to cut it into smaller arrays, a lot like how you can slice a string to get a smaller string.

```js
let fruits = ["apple", "banana", "cherry", "date", "elderberry"];

// this means "slice from item 1 to item 3"
fruits.slice(1, 3); //=> [ 'banana', 'cherry' ]

// this means "slice from item 2 to the end"
fruits.slice(2); //=> [ 'cherry', 'date', 'elderberry' ]
```

If you need an item from a middle index you can use `.slice` to access it.

[MDN: slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

---

# Array Indexing

Array indexing works in the same way as string indexing.

Think of the indexes as pointing at the _spaces between_ items, as in this diagram:

```js
0   1   2   3   4
| B | L | U | E |
['B','L','U','E']
```

---

# Arrays Vs. Strings

You might remember learning that strings are technically lists of characters.

If you have an array of strings, you can combine them all to make one big string:

```js
let fullName = ["Bob", "Saget"];
fullName.join();   // 'Bob,Saget'
fruits.join(" ");  // 'Bob Saget'
fruits.toString(); // 'Bob,Saget'
```

---

# Arrays Vs. Strings Cont.

Just like we can convert arrays to strings, the opposite is true.

You can also turn a string into an array with the string method called `.split`.

Split does not know which character in the string to do the actual _splitting_ at, so it needs an argument.

```javascript
"Bob Saget".split("");  //=> [ 'B', 'o', 'b', ' ', 'S', 'a', 'g', 'e', 't' ]
"Bob Saget".split(" "); //=> [ 'Bob', 'Saget' ]
"Bob Saget".split("o"); //=> [ 'B', 'b Saget' ]
```

> Note: Arrays and String have their own separate sets of methods. Some might have the same names.
