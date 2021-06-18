# Extending the Timer

## Welcome!

Let's expand on our timer lab from earlier to add some more interactive elements. In this lab we will be allowing the user to start, stop, restart, and reset our timer.

## Adding to the Page

To give our user some control over the timer let's add 3 buttons to the html with the following IDs

* "start"
* "stop"
* "reset"

Create references to these elements in your JavaScript using DOM queries.

# Starting the Timer

Add an event listener to your "start" button that will fire when it receives a `"click"` event.

We can use the logic we previously defined for our timer by wrapping it in a function, and using that function as the *callback function* for our event listener.

## Stopping the Timer

When we click the "stop" button the timer should pause. Since we need to track data across function calls we may need some global variables that are reassigned inside our timer function.

What data is needed to stop the timing function?

What data is needed to display the time?

## Restarting the Timer

To restart the timer we want to resume the execution of our timer function from the same count was stopped at when the "start" button is clicked, after the "stop" button had been clicked.

Beware of accidentally setting multiple `setIntervals`! This will cause a weird bug that makes your timer appear to speed up every time it's stopped, and restarted.

## Clearing the Timer

When the "reset" button is clicked we want to stop counting down, and reset our timer to its original value.

## Going Further

- Add a button to dynamically add more timers to the page
  - Each timer should operate independently of the others
