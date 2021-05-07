# Lookup Tables

A lookup table is an object that is used to map strings to other values.

In the object the string you are expecting is used as the key (because all keys on an object are strings), and the value you want to match.

Lookup tables are useful in many situations, such as:

- mapping abbreviations to full words
- mapping strings to variables
- extending allowable user input

---

# Mapping strings to variables

One of the most common uses for a lookup table is to match a string (usually some form of user input) to a variable.

If we had a program that accepts a poet's name, and prints the title of a poem by that poet it might look something like this:

```js
let frost = "Stopping by Woods on a Snowy Evening"

let silverstein = "Falling Up"

let plath = "A Winter Ship"

let poetLookup = {
  "Robert Frost": frost,
  "Shel Silverstein": silverstein,
  "Sylvia Plath": plath
}

function printTitle(userInput) {
  console.log(poetLookup[userInput])
}
```

> Note that we *have* to use square bracket notation to access our object, because we're using a variable `userInput` to determine the key.

---

# State Machines
 A state machine is a system with a number of defined 'states', which can only be in one state at a time, and with defined rules to 'transition' between states.

---

# State Machine Example: Traffic Light

![traffic light](/images/traffic-light.jpg)

1. How many states? What are their names?
2. Can it be in more than one state at a time?
3. What are the rules for transitioning between states?

<small>image by [katerha](https://www.flickr.com/photos/katerha/6919352910)
</small>

---

# State Transition Diagram: Traffic Light

```
[G] -> [Y] -> [R]
 ^             |
  \___________/
```

Q: What if there was a "left turn ok" green light as well?

---
# How to implement a state machine?

> There's more than one way to do it.

Easiest way is with something like this:

```js
let states = {
  "green": {canChangeTo: ["yellow"]},
  "yellow": {canChangeTo: ["red"]},
  "red": {canChangeTo: ["green"]}
}

let currentState = "green";

function enterState(newState) {
  let validTransitions = states[currentState].canChangeTo;
  if (validTransitions.includes(newState)) {
    currentState = newState;
  } else {
    throw "Invalid state transition attempted - from " + currentState + " to " + newState;
  }
}
```

---

# Why use a state machine?

1. Clarity
2. Predicability
3. Fail-fast debugging

* Many bugs are due to the system receiving unexpected input, or input that is inappropriate *at the moment*
* an "illegal state transition" error means something unexpected *just* happened
* Without a state machine, the system may remain in an invalid state for some time
  * this makes it harder to debug once something eventually *does* break

---

# State of the State

> The term "state" has several overlapping meanings.

* in general, "state" means any data
  * especially in OO, e.g. "state and behavior" means "instance variables and instance methods"
* in particular, "state" means "there is a clear state transition diagram at work here"

> The term "state machine" has several technical variants as well.

* "Infinite State Machine" e.g. Turing Machine
* "Finite State Machine" or "Finite State Automaton" e.g. Conway's Game of Life

<https://en.wikipedia.org/wiki/Finite-state_machine>

---

# Transitioning Between Objects

---

# State Machines and Lookup Tables
