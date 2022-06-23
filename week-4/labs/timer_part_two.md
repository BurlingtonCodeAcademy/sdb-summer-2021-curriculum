## Learning

In this lab, we will extend the previous [Timers](https://online.uprighted.com/lessons/written/timer) lab to include a nested timer. All of the topics will be the same, we will just be diving into more complexity. If you did not complete the previous lab, you can find a basic version at this link: [Mission Countdown Timer Lab](https://replit.com/@limzkil/mission-countdown-timer#index.html).

Topics:

- DOM Scripting.
- The Web API `setInterval` timer with `clearInterval`.
- Booleans.
- HTML.

## Achieving

In this lab, you will have a nested `setInterval` timer that fires after the initial interval is complete.

Your work will result in:

- When the initial `setInterval` hits "GO!" as described in the previous lab, another `setInterval` will fire.
- This new `setInterval` will change the content of three `<h2>`s to print "GO!" one after the other.

## Procedure

### Adding three new `<h2>`s
- [ ] Within `index.html`, create three new `<h2>`s beneath "interval-display" that all have the class "repeat-go".

### Gaining reference to the new `<h2>`s in JavaScript
- [ ] Utilize a query selector that gets all elements by class and assign this to the variable `repeatGo`.

### Setting up our new `setInterval` timer
- [ ] Below the first `clearInterval` and **within the same scope**, do the following:
- [ ] Set up an `if` whose condition checks if `isCountedDown` is true.
- [ ] Within this `if`: `repeatGo` is currently a HTML Collection, not an Array. Turn it into an Array and assign the result to `repeatGoArray`.
- [ ] Set up the variable `index` with the initial value of 0.
- [ ] Create a variable to hold the new `setInterval` timer.
- [ ] The callback function to this second `setInterval` should target `repeatGoArray` at `index` and change its `textContent` to "GO!". It should also increment index. 
- [ ] Beneath the incrementation of index, we will need another `if` statement that checks if `repeatGoArray` at `index` is undefined.
- [ ] Within this `if`: call `clearInterval()` and pass in the variable holding the timer as its argument.
- [ ] The new `setInterval` should fire every second.

## Review

The software should:

- Now print "GO!" three times on a one second delay after the intial `setInterval` completes.

## Going Further

- Refer to the Going Further on the previous lab and complete those suggestions.
- Refactor the logic handling the nested timer using a [for loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration#for_statement) for more concision.
- Remove the 'repeat-go' elements in `index.html`. Instead, use JavaScript to programmatically generate these elements in the nested timer.
