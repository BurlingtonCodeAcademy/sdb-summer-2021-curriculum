# What is React

**React** is a front-end JavaScript library that allows you to create complex web applications out of reusable parts called **components**.

> Everything you are about to learn is still JavaScript. It is not a completely separate technology. It only adds features to what you've learned thus far.

---

## Thinking in React

Take 10 minutes to read this article.

Come back and discuss.

<https://reactjs.org/docs/thinking-in-react.html>

---

## The Virtual DOM

- React is a tool that allows us to manipulate the DOM more efficiently.
- It does this by manipulating the DOM on our behalf.
- To do that, React has a "virtual DOM" (its own record of what should be visible).
- It checks if the real DOM matches the virtual DOM.
- If not, it will update the real DOM through a process called reconciliation.

[React | Reconciliation](https://reactjs.org/docs/reconciliation.html)

---

## Components

> Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.

- How is it useful to build apps using them?
- What parts of websites could be components?
- Should _everything_ be a component?

[React | Components and Props](https://reactjs.org/docs/components-and-props.html)

---

## Component Classes and Functions

- You can make a React component using either a function or the `Component` class.
- The entire industry is moving away from classes and towards functions.
- For this reason, we will focus on making components using functions.

---

## Components as Functions

- Each component is a function.
- We capitalize the function name to let other developers know it's a component.
- The argument passed to your component is _always_ an object.
- This object is called `props` by convention.
- Your component function will return **JSX**.

---

## Component Examples

```jsx
function Button() {
  // no props needed
  returns <button> Click </button>;
}

function Welcome(props) {
  // we use { } to use JS inside of the "HTML" (JSX)
  return <h1>Hello, {props.userName}</h1>;
}
```

> We will discuss where exactly this `props` object comes from later.

---

## JSX

This component looks like it's using HTML, but it's really using **JSX**, a syntactical extension of JavaScript:

```jsx
// This..
const element = <h1 className="greeting">Hello, world!</h1>;

// is the same as this
const element = React.createElement(
  "h1",
  { className: "greeting" },
  "Hello, world!"
);
```

[React |Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)
[React |JSX In-Depth](https://reactjs.org/docs/jsx-in-depth.html)

---

## JSX Cont.

- Because JSX is **not** the same as HTML
- Because JSX is used inside a JavaScript function or file
- There are certain words that change a little
  - class 👉 className
  - for 👉 htmlFor
  - onclick 👉 onClick
  - onsubmit 👉 onSubmit
  - etc.

---

## Component Tree

|                                                                                                                     |                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <img src="https://addons.mozilla.org/user-media/previews/full/239/239939.png" width="700" alt="component diagram"/> | <p>Components are organized like a family tree where there is **one** parent at the very top.</p><p> This top component is `<App />`, meaning your entire app is in there.</p> |
| [Firefox Extension](https://addons.mozilla.org/en-GB/firefox/addon/realizeforreact/)                                | [Chrome Extension](https://chrome.google.com/webstore/detail/realize-for-react/llondniabnmnappjekpflmgcikaiilmh?hl=en-US)                                                      |

---

## React Dev Tools

Because the React applications tend to be much more complex, we need to enhance our developer tools to account for that.

Take the time, **right now**, to search `React Dev Tools extension` followed by `Chrome` or `Firefox` and install one.

---

## Exploring the Dev Tools

|                                                                                                                                                                                                                              |                                                                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| <ol><li>Do your best to make this wireframe using **three** React components in your Replit from earlier</li><li>Do not worry about styling</li><li>Pop the preview out and use the React Dev Tools to explore your App</li> | ![3 part wireframe, one column](https://cdn.tutsplus.com/cdn-cgi/image/width=1280/webdesign/uploads/legacy/tuts/341_wf/wireframes-simple.png) |
