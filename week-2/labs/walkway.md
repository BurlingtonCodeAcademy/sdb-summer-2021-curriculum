# Walkway

## Objective

In this lab we will create a program that represents a trip to the store and back.

## Learning

In this lab, we will be utilizing [state machines](https://en.wikipedia.org/wiki/Finite-state_machine) with lookup tables to handle transitions between Objects.

We will create these Objects utilizing a [Class constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes).

Topics:

- Class construction
- Objects
- State machines
- Lookup tables

### Links

- [Finite State Machines on Wikipedia](https://en.wikipedia.org/wiki/Finite-state_machine)
- [MDN Creating Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
- [MDN Class Tutorial](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Classes_in_JavaScript)

## Achieving

In this lab, we will create a piece of software that represents a trip to the corner store and back. This software will transfer the user between different states ("locations") and only allow state transitions between certain states.

Your work will result in:

- The `walkway.js`file.
- `Location` class constructor.
- Three Objects of the `Location` class.
- Variable that represents our initial state.
- Lookup table that maps representative strings to their Objects.
- State machine that maps states to the states they will accept in string format.
- Console log describing the narrative setup.
- `moveLocation` function that contains `if...else` logic to check if state transitions are valid within the state machine.
- Multiple invocations of `moveLocation` to verify our states are transitioning correctly.

## Procedure

### Create the `walkway.js` file

- [ ] Create a new file named `walkway.js` and open it in your editor.

### Construct the `Location` class

- [ ] Define a class named `Location`
- [ ] Within `Location`'s code block, create a constructor that takes `name` and `description` as its arguments.
- [ ] Within the constructor's code block, map `this.name` to `name` and `this.description` to `description`.

### Define the `Location` Class Objects

- [ ] Create a new `home` Object of the Location class. Pass in the name of the location and the description of the location to the constructor.
- [ ] Repeat this process for two more Objects: `sidewalk` and `store`.

### Define the `locationCurrent` variable and the `locationLookUp` lookup table

- [ ] Create the `locationCurrent` variable and assign it the value "home". This represents our initial state.
- [ ] Create the `locationLookUp` table. This will be an Object consisting of `key: value` pairs wherein the key is a String that matches the _exact_ names of our Objects.

### Define the `locationStates` state machine

- [ ] Create the `locationStates` state machine. This will be an Object consisting of `key: value` pairs wherein the key is a state and the value is an array that contains its possible transitions as Strings.

### Inform the user of the opening scene

- [ ] Create a console log that informs the user of the opening scene. "You are at your house." This will not be inside of a function.

### Create the `moveLocation` function

- [ ] Create the function `moveLocation` that accepts the parameter of `newLocation`.
- [ ] Inside of `moveLocation`, set up an `if` statement whose conditional logic checks if `locationStates[locationCurrent]` includes `newLocation`.
- [ ] Inside of this `if` statement, set `locationCurrent` to now be `newLocation`.
- [ ] Inside of this `if` statement, console log the `name` and `description` of `locationCurrent` by checking it in `locationLookUp` using bracket notation.
- [ ] Outside of this `if`, `else` console log a message informing the user they cannot go from `locationCurrent` to `newLocation`.

### Invoke the `moveLocation()` function

- [ ] Invoke `moveLocation` multiple times. Include states that should transition successfully and states that will fail to test your code.

## Review

In this lab, we have practiced utilizing state machines combined with lookup tables to manipulate Objects. The software should:

- Transition between successful states and inform users of the new state and its description.
- If a transition fails, inform users that those states do not transition to each other.
- Utilize narrative as a metaphor for what process is occurring.

## Going Further

- Build out your narrative with more locations.
- Add more properties to the constructor for Location class Objects to possess.
