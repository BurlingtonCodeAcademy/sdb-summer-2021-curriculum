# What is the DOM?

- DOM stands for **Document Object Model**
- The browser reads your HTML _document_ (file) and _models_ it in the form of _objects_.
- The model uses a _tree_ dta structure, much like a family tree, to organize objects, called **nodes**.
- Everything in your file becomes a _node_ -- elements, text strings, and comments.
- We can (and must) examine the DOM and its nodes in the dev tools.

---

## Exercise: Debugging HTML

- This exercise is [pulled from the docs](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML), because it illustrates the differences between the two very well.

1. <a href="https://raw.githubusercontent.com/mdn/learning-area/main/html/introduction-to-html/debugging-html/debug-example.html" alt="link to HTML file needed for exercise">Download this file by right-clicking and selecting 'Save As.'</a>
2. Open the file using your browser.
3. Examining the source code, **what 4 errors do you find**?
4. Use the dev tools to see what the DOM rendered instead.

---

## Debugging JavaScript

- Console tab in the dev tools
- Sources tab
- Breakpoints can be used to pause the execution of your file:
  - Click on the line number where you want to add your breakpoint

> Note: If you don't know where to pause, you can do so at the beginning of the file. This allows you to move line-by-line at your own pace.

---

## Debugger and Breakpoints in Chrome

![chrome debugger example](https://res.cloudinary.com/btvca/image/upload/v1574445168/curriculum/chrome-debugger_y1uc1z.png)

---

## Debugger and Breakpoints in FireFox

![firefox debugger example](https://res.cloudinary.com/btvca/image/upload/v1574445177/curriculum/firefox-debugger_puni46.png)

---

## Considerations

- Refresh the page
- Disable extensions
- Run in 'incognito' mode to make sure you're not caching bad code
- Try a different browser
- Try a freshly installed browser with no extensions or settings changes

---

## Linting and Validation

- A linter is a program that assesses code in order to locate any possible errors.
- There are endless options for both HTML and CSS linters.
- ESLint is the most popular and comes with VSCode.
- You can also use online validators like <https://validator.w3.org/>
