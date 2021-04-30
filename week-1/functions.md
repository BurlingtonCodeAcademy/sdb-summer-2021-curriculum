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

# Lab: Age Calculator

Write a function that calculates the number of seconds old you are when given your age

```javascript
let age = 27

function ageCalc (num) {
  //Your code goes here
}

ageCalc(age) // should print "You are 852055200 seconds old." to the console
```

How could we use ARGV to make this more modular?

# Flip it around!

Can you write the inverse function; one that takes a number of seconds and tells you the exact age?

You can get the current date by calling `Date.now()` which will give you a time in milliseconds, and the date you were born by creating a new `Date` object. You can then figure out the time that's elapsed in milliseconds by subtracting the date you were born from the current date

```javascript
  let date = new Date(1992, 05, 12, 3, 14) //new Date(year, month, day, hour, minute)
  let ageInMilliSec = Date.now() - date
```

# Solution

Here's one solution for the age calculator:

<details>
<summary>Answer</summary>
<div>

```js
let age = 27

function ageCalc(num) {
  let secondsInMin = 60
  let minInHour = 60
  let hrInDay = 24
  let dayInYr = 365.25

  let secInYr = secondsInMin * minInHour * hrInDay * dayInYr

  let ageInSec = num * secInYr

  return ageInSec
}

console.log(ageCalc(age))

```

To flip it you could simply divide the `num` variable by `secInYr` rather than multiplying to get years in a number of seconds.

</div>
</details>

# Lab: Supply Calculator

Write a function that:

* accepts three arguments, a starting age, an amount per day, and an item name
* calculates the amount of items used over the course of the rest of your life
  * based on a 100 year constant max age
* Outputs "You will need **Number** **Item**s to last the rest of your life." e.g.

```js
supplyCal(20, 3, "cookie") // => "You will need 87600 cookies to last the rest of your life"
supplyCal(99, 3, "cookie") // => "You will need 1095 cookies to last the rest of your life"
supplyCal(0, 3, "cookie") // => "You will need 109500 cookies to last the rest of your life"
```

> Supply Calculator inspired by the Lifetime Supply Calculator lab designed for the Girl Develope It! curriculum. The original can be found [here](https://www.teaching-materials.org/javascript/exercises/functions)

# Supply Calculator Solution

<details>
<summary>Hint 1</summary>
<div>

```js
let amountPerYear = amountPerDay * 365
```

</div>
</details>

<details>
<summary>Hint 2</summary>
<div>

```js
let numberOfYears = 100 - age
```

</div>
</details>

<details>
<summary>Solution</summary>
<div>

```js
function supplyCalc(age, amountPerDay, item) {
  let amountPerYear = amountPerDay * 365
  let numberOfYears = 100 - age
  let totalNeeded = amountPerYear * numberOfYears

  let message = "You will need" + totalNeeded + " " + item + "s to last the rest of your life"
}
```

</div>
</details>

# Lab: Titleize

Write a function that:

* accepts a string as an argument
* splits apart the words in the string
* capitalizes each word
* returns a string with the first letter of each word capitalized e.g.

```js
titilize("all dogs are good dogs") // => "All Dogs Are Good Dogs"
titilize("eveRY green bus drives fAst") // => "Every Green Bus Drives Fast"
titilize("FRIDAY IS THE LONGEST DAY") // => "Friday Is The Longest Day"
```

# Titilize solution

<details>
<summary>Hint 1</summary>
<div>

```js
function capitalize(word) {
  return word[0].toUpperCase() + word.slice(1).toLowerCase()
}
```

</div>
</details>

<details>
<summary>Hint 2</summary>
<div>

```js
let wordArray = string.split(" ")
```

</div>
</details>

<details>
<summary>Solution</summary>
<div>

```js
function titilize(string){
  let wordArray = string.split(" ")
  let newArray = wordArray.map(function(word){
    return word[0].toUpperCase() + word.slice(1).toLowerCase()
  })

  return newArray.join(" ")
}
```

</div>
</details>

# More About Functions

* [FreeCodeCamp](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures)
    - start with the challenge [Write Reusable JavaScript with Functions](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures/basic-javascript/write-reusable-javascript-with-functions)
    - continue through the challenge [Assignment with a Returned Value](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures/basic-javascript/assignment-with-a-returned-value)

* Read [Eloquent JavaScript chapter 3](http://eloquentjavascript.net/03_functions.html)