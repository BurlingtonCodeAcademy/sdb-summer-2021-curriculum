# Extended Timer Lab

## Objective

Begin to practice with nested code and nested timers.

## Learning

In this lab, we will extend the previous [Timers](https://online.uprighted.com/lessons/written/timer) lab to include a nested timer. All of the topics will be the same, we will just be diving into more complexity. If you did not complete the previous lab, you can find a basic version at this link: [Mission Countdown Timer Lab](https://replit.com/@limzkil/mission-countdown-timer#index.html).

Topics:

- DOM Scripting.
- The Web API `setInterval` timer with `clearInterval`.
- Booleans.
- HTML.

## Achieving

In this lab, you will have another `setInterval` timer that fires dependent upon the Boolean assigned to a variable. This concept is commonly known as a "flag" and is useful for conditional statements.

Your work will result in:

- When the initial `setInterval` hits "GO!" as described in the previous lab, another `setInterval` will fire.
- This new `setInterval` will change the content of three `<h2>`s to print "GO!" one after the other.

## Procedure

### Adding three new `<h2>`s
- [ ] Within `index.html`, create three new `<h2>`s beneath "interval-display" that all have the class "repeated-go".

### Gaining reference to the new `<h2>`s in JavaScript
- [ ] Utilize a query selector that gets all elements by class and assign this to the variable `repeatedGo`.

### Creating our Boolean flag variable

- [ ] Within the scope of the event listener on our start interval button, add a new variable `isCountedDown` that is initially set to false.

###  Flipping our `isCountedDown` flag

- [ ] Above the first `clearInterval`, reassign `isCountedDown` to be true.

### Setting up our new `setInterval` timer
- [ ] Below the first `clearInterval` and **within the same scope**, do the following:
- [ ] Set up an `if` whose condition checks if `isCountedDown` is true.
- [ ] Within this `if`: `repeatedGo` is currently a HTML Collection, not an Array. Turn it into an Array and assign the result to `repeatedGoArray`.
- [ ] Set up the variable `index` with the initial value of 0.
- [ ] Create a variable to hold the new `setInterval` timer.
- [ ] The callback function to this second `setInterval` should change the `textContent` of `repeatedGoArray` at `index` to "GO!". It should also increment index. 
- [ ] Beneath the incrementation of index, we will need another `if` statement that checks if `repeatedGoArray` at `index` is undefined.
- [ ] Within this `if`: call `clearInterval()` and pass in the variable holding the timer as its argument.
- [ ] The new `setInterval` should fire every second.

## Review

In this first paragraph, touch again upon what was described in the Objective section. Remind students of what the goal of the lab was and what the software achieved should be.

The software should:

- Now print "GO!" three times on a one second delay after the intial `setInterval` completes.

## Going Further

- Refer to the Going Further on the previous lab and complete those suggestions.
- Examine your code for opportunities to refactor: is there code that could be written more concisely? Is there code that could be broken apart for clarity?
