# State

- Any data in a component that might change is held in an object called `state` by convention.
- Examples of data that could change:
  - Newsfeed posts from an app's users
  - Logged in username
  - The number of reactions on a post
  - Someone's online or offline status
  - The loading status of a page

---

## What is State For

React takes care of updating the DOM for us, and one of the most powerful parts of React is that it updates the DOM when data changes.

Because of this, React comes with some built-in tools we can use to let it know **what** data will possibly change, **when** that data does indeed change, and **what** that data is changing to.

---

## How to Make "State"

You can name `yourState` and `functionToUpdateYourState` whatever you want. The convention is to say `someVariable` and `setSomeVariable`.

```jsx
// in any component file
import { useState } from "react";

function yourComponentHere() {
  const [yourState, functionToUpdateYourState] = useState(null); // yourState is null

  functionToUpdateYourState("new state value"); // yourState is 'new state value' now
}
```

---

## How to Make "State" Cont.

Let's demystify that syntax from before by pretending to write our own `useState` function:

```js
// "under the hood"
function useState(startingData) {
  function updateState(newData) {
    startingData = newData;
  }

  return [startingData, updateState];
}

// how you use it
const [startingData, updateState] = useState(null);
```

> Notice how the return value on line 7 and the variable declaration on line 11 match up.

---

## Props

- We use props to share data, which is sometimes the state, from component to component.
- Props is **always** an object
- Props is **read-only**. You cannot reassign it ever.
- `props` is a convention, not a keyword.
- `props` are the arguments passed into your function components.
- You do not _have_ to use `props` in every component.

---

## How to "Pass" Props

Because `props` is the data that is shared between components, there is a sender and receiver. For this reason, the phrase "passing props" is used a lot, in the same way we say we "pass an argument" to a function.

```jsx
function ParentComponent(){
  let theValue = "whatever you want"
  return <ChildComponent theKey={theValue} >
}

// The actual "passing" of props is on line 3
// We passed the props to the ChildComponent scope where it is now this object:
// { theKey: theValue }
```

---

## How to Receive Props

```jsx
function ParentComponent(){
  let theValue = "whatever you want"
  return <ChildComponent theKey={theValue} >
}

function ChildComponent(props){
  console.log(props)
  console.log(props.theKey) //=> theValue ==> "whatever you want"
}
```

---

## How to Receive Props Cont.

Why does this work?

```jsx
// The computer converts this
<ChildComponent theKey={theValue} >
```

<br/>

```js
// into this for you
React.createElement(ChildComponent, { theKey: theValue }, [
  ...anyChildComponentsYouWantToInsert,
]);

// where React.createElement eventually does this for you
ChildComponent({ theKey: theValue });
```

> See how your props become an object that is an argument for you component?

---

## Practice Making State and Props

In your replit from before,

1. Add **your name as App's state**
2. **Pass that data to your HeaderComponent as props**
3. **Console log your name** from your HeaderComponent (look the in regular dev tools to confirm)
4. Bonus: **Render your name in your HeaderComponent**

---

## Events: onChange and onSubmit

React's "virtual DOM" process uses something called a SyntheticEvent, a class that mimics DOM events. They work much the same way, but you'll want to use React docs for researching events in addition to W3Schools or MDN.

You can find a list of events that React supports [here](https://reactjs.org/docs/events.html#supported-events).

We will be covering `onChange` and `onSubmit` to prepare you for your next lab.

---

## Events: onChange and onSubmit Cont.

`onChange` and `onSubmit` are critical events for controlling [forms](https://reactjs.org/docs/forms.html)

- We do not _have_ to use events for a person to type into the form. This is built into the browser.
- We need to control the inputs so that we...
  - can change other data as the person fills out the form
  - capture the data before being sent off.

**onChange**: [occurs when the value of an element has been changed](https://www.w3schools.com/jsref/event_onchange.asp), like when someone types in an `<input />`.

```jsx
// example usage
<form onSubmit={handleSubmit}>
  <input onChange={handleChange} />
</form>
```

---

## Combining Form Events and State

```js
function FormComponent() {
  const [typing, setTyping] = useState(""); // input begins blank

  const handleChange = (e) => {
    setTyping(e.target.value); // update state with what the person typed
  };
  const handleSubmit = () => {
    console.log(typing); // I can grab this data from state instead of the form itself now
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" onChange={handleChange} value={typing} />
      {/*                                        IMPORTANT 👆*/}
      <input type="submit" />
    </form>
  );
}
```

---

## State, Props, and Forms

**Passing props is not always a good idea.**

The point of using a component is that it can be taking out of the app and used "in isolation," by itself.

If the data and functions that control a form are in a different component, you cannot use the form in isolation.

The state and functions that are vital to interacting with the form should be **in the same component as the form itself**.

---

## Follow Along: Login Form

<https://replit.com/@education-team/basic-login-form>

---
