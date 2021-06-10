# Recursion

*recursion* is when a function *calls itself*

![ouroboros](/images/ouroboros.jpg)

(like Ouroboros, a mythical serpent who eats its own tail)

<small>(image source: [wikipedia, public domain](https://en.wikipedia.org/wiki/Ouroboros#/media/File:Serpiente_alquimica.jpg))</small>

---

# Infinite Recursion

Here's a not very useful recursive function:

```js
function go() {
  console.log("Go!");
  go();                // do it all again
}
```

Call this function with `go()`, then either wait a few seconds, or stop it by pressing <kbd>CTRL</kbd>-<kbd>C</kbd>.

`RangeError: Maximum call stack size exceeded` means that `go` has called itself too many times.

---

# Recursion Requires Termination

For recursion to be useful, it needs to (eventually) stop.

The standard way to stop is called a *guard clause*.

Also called a *base case* or a *terminator*.

```js
function countdown(seconds) {
  if (seconds === 0) {
    console.log("Blastoff!");
  }
```

This means, "When seconds reaches 0, **stop recursing**."

---

# Countdown

The simplest form of recursion uses a counter; in this example we are counting down the seconds until a rocket launches.

```js
function countdown(seconds) {
  if (seconds == 0) {
    console.log("Blastoff!");
  } else {
    console.log("" + seconds + "...");
    let nextCount = seconds - 1;
    countdown(nextCount);
  }
}

countdown(10);
```

Put the above in a source file called `countdown.js` and try it now. 

Note that you *must change* the value; otherwise you will recurse forever.

---

# Exercise: Draw It Out

Please dive into the above `countdown` function in excruiciating detail.

Fill out the cells of the following table for the call `countdown(5)`:

| Iteration | seconds | nextCount |
|---|---|---|
| 0 |   |   |
| 1 |   |   |
| 2 |   |   |
| 3 |   |   |
| 4 |   |   |

---

# Recursion is Reduction

In addition to the base case, a recursive function needs to define at least one other case; this case *wraps around* the base case like a Russian doll.

![matryoshka](/images/matryoshka.jpg)

You can think of a recursive function as starting with a large problem, and gradually reducing the problem until it reaches the base case.

Since the base case has a known solution, every other step can then be built back up on top of it -- which is why it's called the *base*.

In this way, recursion is an example of the *divide and conquer* approach to problem-solving.

<small>(image source: [wikipedia, public domain](https://en.wikipedia.org/wiki/Matryoshka_doll#/media/File:First_matryoshka_museum_doll_open.jpg))</small>
