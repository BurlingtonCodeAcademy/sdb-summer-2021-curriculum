# What is the DOM?

* DOM stands for **Document Object Model**
* The DOM can be a bit tricky to wrap your head around. It is essentially a set of objects and methods that defines how your HTML document is accessed and manipulated.
* A central metaphor of the DOM is that your HTML file is a tree, and HTML elements are branches and leaves on that tree.
* A visual representation of the DOM can be seen by using the 'Inspect' feature of your browser.

Please try this out right now, on this web page!

---

# Is the DOM Just My HTML?

* No, it isn't. :-)
* The DOM can appear similar or identical to the HTML that makes up your website. However, browsers can fix small syntax errors in your HTML automatically (such as inserting a missing close tag).
* The DOM is also kept up to date with the current state of the page, even if it is modified using JavaScript.
* JavaScript **isn't actually _editing_ your document**. It is simply modifying the DOM. You can think of the DOM as an editable copy of your read-only website, which stays pristine on your server or filesystem.

---

# Unbreaking Your Code (Using the DOM)

With both HTML and CSS, it can be easy to forget a semi-colon or a closing tag, which can lead to unwanted display issues on your website. There are a few tools that can help prevent and/or fix this going forward.

* Your Browser
* A Friend
* A Linter

---

# Debugging With Your Browser

Chrome can be one of the most useful tools for debugging HTML and CSS.

* Right clicking on an element in Chrome. You will see an option labeled 'Inspect'.
* An easy-to-read visual representation of your DOM will open, which can be modified and analyzed to track down any code that may be of issue.
* Both CSS properties and HTML elements can also be added, removed, or modified to determine their impact on specific elements of your web page.

---

# Chrome Inspector

![Image of the chrome web inspection tool](https://res.cloudinary.com/btvca/image/upload/v1574445175/curriculum/dom-debugging_a3ij2j.png)

---

# HTML Always Renders

Web pages can be frustrating to debug because your browser will always render *something* so the errors can be hard to find. When something is invalid your browser will deal with it by ignoring it.

Check your source tab to make sure all your files are being loaded in. Use the console in the browser to check your error messages.

---

# When in Doubt console.log it out!

The main source of bugs in software is when we assume we know what the data is. If your program is erroring out, or behaving unexpectedly, add `console.log`s to make sure the data is what you expect it to be! Some useful things to `console.log` are:

* `event.target`s
* dom queries
* variables that are set by user input
* `typeof` variables

---

# Grab a Second Set of Eyes

Often staring at thousands of semi-colons and angle brackets can be overwhelming and mind-numbing. A second set of trained eyes can help to find that pesky character that is breaking your code.

---

# Browser Tools

If you're running a program through your browser most modern browsers (i.e. Chrome, or FireFox) have built in debugging tools you can use! These are fairly heavy weight tools, and should only be used as a last resort.

---

# Step 1: Accessing the Dev Tools

In Chrome:

* `ctrl` + `shift` + `i` for a Windows machine
  * **or** right click and select `inspect` from the drop-down menu
* `cmd` + `option` + `i` for a Mac
  * **or** `option` + click and select `inspect` from the drop-down menu

In FireFox:

* `ctrl` + `shift` + `c` for a Windows machine
  * **or** right click and select `Inspect Element` from the drop-down menu
* `cmd` + `option` + `c` for a Mac
  * **or** `option` + click and select `Inspect Element` from the drop-down menu

---
 
# Step 2a: Add Breakpoints in Chrome

* In the dev tools, navigate to the `Sources` tab (to the immediate right of the `console` tab)
* Select the file you want to debug
* Click on the line number where you want to add your breakpoint

>Note: If you're unsure where your error is coming from you can add a break point at the top of your code and step through your whole program line by line

---

# Step 2a breakdown

![chrome debugger example](https://res.cloudinary.com/btvca/image/upload/v1574445168/curriculum/chrome-debugger_y1uc1z.png)

---

# Step 2b: Add Breakpoints in FireFox

* In the dev tools, navigate to the `Debugger` tab (to the immediate right of the `console` tab)
* Select the file you want to debug from the `Sources` section
* Click on the line number where you want to add your breakpoint

---

# Step 2b breakdown

![firefox debugger example](https://res.cloudinary.com/btvca/image/upload/v1574445177/curriculum/firefox-debugger_puni46.png)

---

# Step 3: Run your Code

Once you've added a breakpoint run your code, and step through the section by clicking the `step over`  button or pressing `f10`.

If you've stepped through your code, and are still having issues finding where the errors are coming, or you find yourself traversing through previously unknown code there are several things you may want to try:

* Disable extensions

* Run in 'incognito' mode to make sure you're not caching bad code

* Try running the code in a different browser

* Try running it in a 'pristine' browser (a fresh install with no extensions or settings changes)

>Note: If your code runs on page load, you will need to refresh the page before the debugger takes effect.

---

# What is a Linter?

A linter is a program that assesses code in order to locate any possible errors

There are endless options for both HTML and CSS linters. A quick Google search will yield a number of potential websites and plugins to help debug your code.

You can download your preferred linter through the VS Code marketplace. (ESLint comes bundled with VS Code by default)

E.g. <https://validator.w3.org/>
