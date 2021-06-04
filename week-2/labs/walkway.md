# Walkway

## Welcome!

In this lab we will be creating a program that represents a trip to the store and back. The purpose of this lab is to get more experience using state machines, and lookup tables together to handle transitions between objects.

THe first thing we'll want to do is create a new JS file to write our code in. Create a new file called `walkway.js`.

## Creating Locations

We are trying to create a program to represent a walk to the store, and back. This means we will need at least three distinct states for our program to be in. Let's create three objects to represent *home*, the *walkway*, and the *store*.

Each object should have:

* A `name` property with a the name of the location as a string for its value
* A `description` property with a brief description of the area
* Feel free to get creative, and have fun with these

## Track Your Location

To know where we can go we need to know where we currently are. Create a global variable to track which location you're in. `currentLocation` seems like a good variable name to me.

Set this variable equal to your `home` object.

## Setting up the State Machine

Now that we've got a few different states our program can be in, and a way to track our current location let's work on the logic to change our current location.

We don't want to be able to change our current location from `home` directly to `store`. Instead we should need to go from `home` to `walkway` to `store` and vice versa to get back. In order to prevent *invalid transitions* we can build a *state machine* that will handle changing the `currentLocation` for us.

Define a function, I think `moveLocation` is a good name for this function, that will:

* Take a *new location* as its argument
* Check the current location
* Determine if the current location can transfer to the new location using the following rules:
  * `home` can only change to `walkway`
  * `walkway` can change to either `home` or `store`
  * `store` can only change to `walkway`
* If the new location *is* a valid transition:
  * Print "Moving from *currentRoom* to *newRoom*" and the new room's description
  * And reassign `currentRoom` to the new room
* Otherwise just print "Invalid state transition attempted"

## Test It Out

To test out our program we can call our function, passing in `walkway` as the argument.

```js
moveLocation(walkway)
```

Then run the file with the command `node walkway.js`. If all goes well We should see something like:

```
Moving from Home to Walkway

A Small cobblestone path stretches before you. You know the store is just down the road...
```

We can test it further by calling our `moveLocation` function sequentially, passing in our next destination.

```js
moveLocation(walkway)
moveLocation(store)
```

Which should print:

```
Moving from Home to Walkway

A Small cobblestone path stretches before you. You know the store is just down the road...

Moving from Walkway to Store

You find yourself in a small corner store. The walkway leading home is outside.
```

## Fail Properly

We should also check that our `moveLocation` function *prevents invalid state changes*. To do this we can comment out the call to `moveLocation(walkway)` and run the program again.

It should now print

```
Invalid state transition attempted
```

And if you `console.log` out `currentLocation` you should see the `home` object.

## There, and Back Again

Call the function 4 times passing `walkway`, then `store`, then `walkway`, then `home` to print a nice little store about a trip to the store and back again when you run the file.

## Going Further

- Add more "rooms"
- Rather than moving through the story automatically, write a function that makes the transitions happen according to user input
- How could we make `moveLocation` a method on the location objects themselves, rather than a global function?