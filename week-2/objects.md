# Software Models the World

* Data Structures allow for programmers to make models of the world in code.
* People naturally think of the world as made up of things.
* Programming languages have ways to represent things.
* JavaScript's primary way of representing a thing is an "Object".
* JavaScript objects let you describe things in any way you can imagine.
  * As long as your description is valid JavaScript :)

> All models are wrong, but some are useful. -- [George Box](https://en.wikipedia.org/wiki/All_models_are_wrong)

---

# An Object Contains Properties

```javascript
let abby = {
  'species': 'dog',
  'color': 'brown',
  spayed: true,
  breed: 'mutt',
  weight: 40,
  'favorite activity': 'chasing squirrels'
}
```

* This is called **object literal** syntax since it defines the object exactly as it's **written**.
* The string on the left is called the *key*; the string on the right is called a *value*; the two together are called an *entry* or a *property*.
* JavaScript object keys are always strings, but if the key has no spaces in it, you can omit the quotations
* `let abby = {...}` is an assignment, setting the variable `abby` to point to the object we just defined

---

# An Object is a Lookup Table

An object is useful for putting many similar things together.

Let's make an object that maps a state's *abbreviation* to its *full name*

```javascript
let states = {
  'VT': 'Vermont',
  'CA': 'California',
  'MA': 'Massachusetts',
  'NY': 'New York'
}
```

---

# Getting Object Properties

You can get the properties of an object with either *dots* or *brackets*:

| With Dots   | With Brackets  | The Value         |
|-------------|----------------|-------------------|
| `states.VT` | `states['VT']` | `'Vermont'`       |
| `states.CA` | `states['CA']` | `'California'`    |
| `states.MA` | `states['MA']` | `'Massachusetts'` |
| `states.NY` | `states['NY']` | `'New York'`      |

Both syntaxes are useful in different situations.

```javascript
states['VT']  // 'Vermont'
states.VT     // also 'Vermont'
```

---

# Setting Object Properties

* You can set the properties of an object with either *dots* or *brackets* followed by a `=` (single equal sign)
* Adding properties works even after the object has been created.

```javascript
states.WY = 'Wyoming'

states['FL'] = 'Florida'
```

* Setting a property with a key that already exists *removes* the original value first
```javascript
states.VT = 'The Green Mountain State'
```

---

# Dots vs. Brackets

Dots are prettier than square brackets, but less versatile, since some keys simply cannot be represented using dot notation, and trying to use them causes syntax errors.

The bracket `[]` syntax is less common but covers more uses (e.g., if the key contains spaces, or is inside a variable).

```javascript
let capitals = {}

capitals["New York"] = 'Albany'
capitals.New York = 'Albany'
             ^^^^
SyntaxError: Unexpected identifier
```

---

# Which to Use

In general using the dot operator is much more common. It looks nicer, and takes a few less characters to set up.

But if you get the errors from the previous slide, revert to brackets, which is more flexible:

```javascript
> capitals['New York']
'Albany'
> capitals
{ 'New York': 'Albany' }
```

---

# Dots vs. Brackets vs. Variables

You can use variables instead of literals to get and set properties.

Given this code ...

```js
let items = {
    brick: 'red'
}
let item = 'brick'
```

... two of the following expressions look for *a key named `item`*, but only one looks for a key named *the value of the variable named item*:

| code            | value       | explanation                         |
|-----------------|-------------|-------------------------------------|
| `items.item   ` | `undefined` | "get me the property named 'item'"  |
| `items['item']` | `undefined` | "get me the property named 'item'"  |
| `items[item]  ` | `'red'`     | "get me the property named 'brick'" |

> This can be confusing!

---

# An Object is a Data Structure

Objects are good for a lot more than mere one-to-one maps. They allow you to design *data structures* that are as complicated and as deeply nested as you can imagine...

```javascript
let alice = {
  name: 'Alice Abrams',
  age: 36,
  married: false,
  homeAddress: {
    street: '12 Maple St.',
    city: 'Burlington',
    state: 'VT',
    zipCode: '05401',
    location: {
      latitude: 44.4759,
      longitude: -73.2121
    }
  },
  pets: ['Mittens', 'Fido']
}
```

Given the above, the value of `alice.homeAddress.zipCode` is `'05401'`

> Note: The above shows the essence of [JSON](./json):
> a syntax for representing data structures containing primitive values,
> including nested objects and arrays.

---

# `Object.keys`

`Object.keys` is a special function that:

  * takes any object as an argument
  * returns an array
  * containing that object's keys

Example:

```javascript
Object.keys(states)  //=> [ 'CA', 'MA', 'NY' ]
```

---

# Looping through an object with for...in

---

# All keys are strings, even nulls

* In a JavaScript object, keys must be strings

* **Beware** of using these as keys, since they get converted to strings in unexpected ways:

    * `null`
    * `undefined`
    * `''` (empty string)
    * `false` or `true`
    * `0` (or any number)

---

# `delete`

To remove a key-value pair from an object, use the keyword `delete`:

```js
states = {
  CA: 'California',
  MA: 'Massachusetts',
  NY: 'New York'
}

{ CA: 'California', MA: 'Massachusetts', NY: 'New York' }

> delete states.MA

true

> states

{ CA: 'California', NY: 'New York' }
```

> note that `delete` is **not** a function; it's a keyword

---

# fake delete

You can get a similar effect by setting the value to `null` or `undefined`, but beware: the key remains!

```js
> states.CA = null
null
> states.NY = undefined
undefined
> states
{ CA: null, NY: undefined }
> for (let state of states) { console.log(state) }
```

> Remember, this only removes the *value*, but not the *key*, from the property list.
> This can be dangerous!

---

# More About JS Objects

* Eloquent JavaScript: [Chapter 4](https://eloquentjavascript.net/04_data.html)

* FreeCodeCamp:
  * From [Build JavaScript Objects](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures/basic-javascript/build-javascript-objects)
  * to [Accessing Nested Objects](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures/basic-javascript/accessing-nested-objects)
