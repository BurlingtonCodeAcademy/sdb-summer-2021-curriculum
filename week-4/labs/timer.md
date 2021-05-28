# Timer

## Welcome!

In this lab we will be practicing DOM scripting, and setting up event handlers by creating a simple timer that counts down from 2 minutes, and sends an alert when finished.

## Timing functions

Timing functions are a special type of event listener that listens for timing events. Unlike most events these are not dependant on user interaction, but will fire a preset amount of time after the function was called

In JavaScript we have two timing functions
* `setTimeout`
* `setInterval`

## setTimeout

The built-in function `setTimeout` sets up a callback.

You call it with two parameters:

  1. a callback function (let's call it F)
  2. a number of milliseconds (let's call it N)

`setTimeout` returns *immediately*, but also sets up a hidden timer

after approximately N milliseconds, F gets *called back*

Try this now:

```javascript
function later() {
  console.log("See you later...");
  setTimeout( alligator, 1000 );
}
function alligator() {
  console.log("Alligator!")
}
later();
```

[MDN: setTimeout documentation](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout)

## setInterval

`setTimeout` has a sibling named `setInterval`

It works a lot like `setTimeout` but is a little more complicated.

After calling `setInterval`, JavaScript will call your callback *again and again forever* until you *clear* the timer.

For example:

```javascript
function countDownFrom(num) {
    let intervalId = setInterval(tick, 1000);

    function tick() {
        console.log(num);
        num = num - 1;
        if (num <= 0) {
            console.log('Blastoff!');
            clearInterval(intervalId);
        }
    }
}
countDownFrom(10);
```

https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval

## setInterval or setTimeout?

When you want something to happen again and again on a fixed delay, you need to choose between `setInterval` and `setTimeout`.

`setInterval` is a bit more powerful but also a bit more complicated.

Note that anything you do with `setInterval` could instead be implemented using `setTimeout`, as long as your callback **calls `setTimeout` again** recursively, like this:

```javascript
function countDownFrom(num) {
    setTimeout(tick, 1000);

    function tick() {
        console.log(num);
        num = num - 1;
        if (num <= 0) {
          console.log('Blastoff!');
        } else {
          setTimeout(tick, 1000);
        }
    }
}
countDownFrom(10);
```

This design decision comes down to personal style and preference. Which makes more sense to you? Which will better fit your needs?

## Create the Page

To create a web page with some attached JavaScript we should first set up a new directory to hold our files. I will refer to this directory as "timer" from now on.

Inside "timer" create a new `index.html` file. Remember the name "index.html" is significant! On this page create an empty `div` with the id "timer"

## Link the JavaScript

We could create a `script` tag on our page, and write our JavaScript directly inside it, but that wouldn't be very organized. Instead we should create a dedicated JS file where we will write all our JavaScript, and link it to our page with a `script` tag using the `src` attribute to point to our JS file.

## Counting Seconds

Counting down every second is a fairly simple procedure. We can set a `timeOut` or `setInterval` function and tell it to fire after, or every (depending on which function you used) 1000 milliseconds.

We should also set a variable that we can decrement each time our timing callback fires.

* create a global variable named `count` and set it's initial value to 120
* set up your event handler function to decrement `count` by 1 every time it's called
  * until `count` is 0
  * for now just `console.log` count, we'll put it on the page in a little bit
* set up a timing function that will call your event handler every second
  * until `count` is 0

## Displaying seconds

To display our seconds on the page we will need a location we can write the data to.

* in your JavaScript use a DOM query to create a reference to the `div` with an `id` of `"timer"`
* instead of `console.log`ing count in your event handler, replace the div's *text content* with the current value of count

## Counting Minutes

Now that we have a timer that counts down 120 seconds let's format it so that it looks a bit nicer. Let's have it start at 2 minutes, and count down from there.

There are 60 seconds in a minute, so we need to have a number of minutes equal to our seconds divided by 60.

The number of seconds left in each minute would be the *remainder* of our total count divided by 60

Separate your minutes and seconds into two variables and draw both these values in the "timer" div with a colon between them, e.g. `1:37` for a count of 97.

## Left Padded Zeros

When the seconds get into the single digits things might start looking a little bit funky.

Adding left padded 0s to numbers can be surprisingly tricky. Don't be afraid to convert your numbers into strings either through *string concatenation* or by using a method such as `.toPrecision`