# Timer Lab

A mission Countdown Timer

## Objective

Understand how to use the browser's `window` object to create a timer to execute a callback function after a period of time, or on an interval of time.

## Learning

In this lab, we will be practicing with basic DOM scripting. We will utilize the `setTimeout` and `setInterval` Web API timers. We will also need to utilize HTML.

Topics:

- DOM Scripting.
- The Web API  `setTimeout` timer.
- The Web API `setInterval` timer with `clearInterval`.
- HTML.

## Achieving

In this lab, we will want to create a MISSION COUNTDOWN.

Your work will result in:

- A website that displays a MISSION COUNTDOWN title.
- A button with the text GET READY? that starts the timeout timer.
- A header that displays GET READY... that changes to READY! when the time out is complete.
- A button with the text START COUNTDOWN that starts the interval timer.
- When START COUNTDOWN is clicked, an interval timer appears on the page that countdowns from 5 to 1.
- After 1 in the interval timer, the display changes to GO!

## Procedure

### Setting up the HTML

- [ ] This page will need a few of elements:
- [ ] A `<h1>` with the text MISSION COUNTDOWN.
- [ ] A `<button>` with the text GET READY? and the id "start-timeout".
- [ ] A `<h2>` with the id of "timeout-display" that is initially empty.
- [ ] A `<button>` with the text START COUNTDOWN and the id "start-interval".
- [ ] A `<h2>` with the id of "interval-display" that is initially empty.
- [ ] You will need to import `script.js` into `index.html`.

### Getting our DOM elements with `getElementById`

- [ ] In `script.js`, utilize the DOM selector `getElementById` to grab our four element nodes and assign them to individual variables.

### Assigning our event listeners

- [ ] Utilizing the variable you assigned the DOM selector to, append `.addEventListener()` to the "start-timeout" button. We will need to complete this step again for the "start-interval" button.
- [ ] `addEventListener()` takes two arguments: the event and the function that represents the event that will occur.
- [ ] The event should be 'click' and the callback functions will be described below.

### Creating our callback function to the 'start-timeout' `addEventListener`

- [ ] The first thing that needs to happen is the `textContent` of our "timeout-display" changes to "Getting ready..."
- [ ] Then, create a variable to hold our `setTimeout` timer.
- [ ] Refer to the syntax of `setTimeout` here: [MDN setTimeout](https://developer.mozilla.org/en-US/docs/Web/API/setTimeout)
- [ ] The first argument passed to `setTimeout` is a callback function that represents what happens once the timer expires.
- [ ] When the timer expires, we want the `textContent` of "timeout-display" to change to "READY"
- [ ] We want the timer to expire in 5 seconds which is the second argument passed to `setTimeout`. It should be passed in as milliseconds.

### Creating our callback function to the 'start-interval' `addEventListener`

- [ ] The first thing that needs to happen is the creation of a `count` variable that starts at `5`.
- [ ] Then, create a variable to hold our `setInterval` timer.
- [ ] Refer to the syntax of `setInterval` here: [MDN setInterval](https://developer.mozilla.org/en-US/docs/Web/API/setInterval)
- [ ] The first argument passed to `setInterval` is a callback function that represents what happens every time the delay or interval occurs.
- [ ] Inside of this callback function, we want the `textContent` of "interval-display" to decrement.
- [ ] Set up an `if` statement to catch when count is less than 0.
- [ ] Inside of this `if` statement, change the `textContent` to be "GO!"
- [ ] Inside of this `if` statement, utilize `clearInterval` and pass in the variable that holds the `setInterval` timer.
- [ ] The second argument passed to `setInterval` is the time in milliseconds we want the delay or interval to be. We want it to be 1 second.

## Review

In this lab, we utilized the `setTimeout` and `setInterval` timers to achieve two different kinds of display to the user.

The software should:

- Be a website that displays a MISSION COUNTDOWN title.
- Have a button with the text GET READY? that starts the timeout timer.
- Have a header that displays "Getting ready..." when GET READY? is clicked, that changes to READY! when the time out is complete.
- Have a button with the text START COUNTDOWN that starts the interval timer.
- When START COUNTDOWN is clicked, an interval timer appears on the page that countdowns from 5 to 1.
- After 1 in the interval timer, the display changes to GO!

## Going Further

- Right now, you can click the buttons multiple times which will create multiple timers and cause a bug in your page. How can you disable the buttons so users can only click them at the appropriate times?
- Can you change the text colors so that it is red when the user is waiting and green when the user is ready to go?
- Feel free to practice your CSS and style this page further.
