# Lookup Tables AKA Dictionaries AKA Hash Maps

A lookup table is an object that is used to map strings to other values.

The search is used as a key in the object, and the result for that search term is the corresponding value.

Lookup tables are useful in many situations, such as:

* searching abbreviations to find full words
* keeping track of your program's work by mapping an item from a list to the output
  * you can use this to avoid repeat work
* efficiently processing user input

---

# Lookup Table Example and Practice

```js

function getPoemTitle (authorUserSelected) {
  
  let poemTitlesByAuthor = {
    "Robert Frost": "Stopping by Woods on a Snowy Evening",
    "Shel Silverstein": "Falling Up",
    "Sylvia Plath": "The Bell Jar"
  };

  return poemTitlesByAuthor[authorUserSelected];
};

console.log(getPoemTitle('Sylvia Plath'))
```

> Try making a function that gets a song from a list of musicians and song titles and send it via DM in Discord.

---

# State Machines

A **state machine** is a system with a number of defined 'states'. The system can only be in one **state** at a time and has rules that determine how it 'transitions' between states.

An object is one kind of state machine. The keys reference the current state, and the values of those keys are the allowable transitions.

They also use a function to determine if they can change to a certain state while preventing invalid state changes.

---

# State Machine Example: Traffic Light


1. How many states? What are their names?
2. Can it be in more than one state at a time?
3. What are the rules for transitioning between states?

<figure>
  <img src="https://res.cloudinary.com/btvca/image/upload/v1574445209/curriculum/traffic-light_saqe87.jpg" />
  <figcaption>image by <a href="https://www.flickr.com/photos/katerha/6919352910">katerha</a></figcaption>
</figure>

---

# State Machine Example: Traffic Light Cont.

```
[🟢] → [🟡] → [🔴] ↤↦ [⚠️]
  ↖⎽⎽⎽⎽⎽⎽⎽⎽⎽⎽⎽⎽」 

```

* Green can transition to yellow
* Yellow can transition to red
* Red can transition to *either* a warning to yield or back to green
* The warning to yield can transition back to Red.

---

# Setting up the Allowable Transitions

The first step when creating a state machine is to set up an object that will hold your allowable transitions. You will need a key to represent each possible state, and a value that's an array of possible transitions.

```js
let states = {
  green: ["yellow"],
  yellow: ["red"],
  red: ["green", "yield"],
  yield: ["red"]
}
```

---

# Moving Between States

To enforce our state machine we will create a function that knows what the current state is, and accepts the next state as an argument.

If the change from the current state to the next state is valid we change our current state, otherwise we throw an error and the state doesn't change.

```js
let currentState = "green";

function enterState(newState) {
  let validTransitions = states[currentState];
  if (validTransitions.includes(newState)) {
    currentState = newState;
    console.log(currentState)
  } else {
    throw("Invalid state transition attempted - from " + currentState + " to " + newState;)
  }
}
```

---

# Using our State Machine

Now we can run through some state transitions using our state machine.

```js
enterState("yellow")
enterState("red")
enterState("yellow")
```

Note that the last call to `enterState` *should* throw an error, because `"yellow"` is not a valid transition from `"red"`

---

# Why Use a State Machine?

1. Clarity
2. Predictability
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

Often times you will want to do more than just change from one string to another. You'll need to transition between more complex data structures like objects.

We can combine state machines, and lookup tables to allow for more complex interactions.

You can still keep track of the current state as a string, and use our state machine just as we previously set it up. The difference comes in how we use that current state. If you need to map it to an object you can create a lookup table which you access *at the current state*
