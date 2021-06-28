# What is React

React is a front end, declarative, JavaScript framework that allows you to create modular, dynamic wep applications.

React components use babel, and JSX to allow the user to write code that looks a lot like HTML in our JavaScript files

---

# Component Oriented Design

React is built around the idea of creating modular components that can be used to construct specific sections of your web page

- Smaller components make more modular pages
- Larger components can be used to render smaller components
- Each instance of a component holds its own state
- We can create multiple instances of a single component
  - And change their state to repeat *layout* while changing *data*

---

# The Component Class

---

# React Components

- Isolated pieces of a website or app
- Can be passed data from parent components in the form of `props`
- Can be rendered manually, or programmatically
- Return JSX

---

# Using Components

- Typically the `index.js` initiates the components tree from the top level
- Usually made up of other components
- Child components are rendered by their parents
- Parents pass data as props to children

---

# Using Arrays of Components

- Many components can be rendered at once
- Wrap the components in an array
- React will iterate over and render each
- Useful when rendering many of the same component, or sets of data

---

# Immutable Components

- Once components are rendered they cannot be updated manually
- Re-rendering the component is how they are updated
- Re-renders are triggered when `state` or `props` change

---

# Granular Render Updates

![render performance](https://res.cloudinary.com/btvca/image/upload/v1574445178/curriculum/granular-dom-updates_jyda7g.gif)

---

# Component Lifecycle

## Mounting

- constructor()
- static getDerivedStateFromProps()
- render()
- componentDidMount()

## Updating

- static getDerivedStateFromProps()
- shouldComponentUpdate()
- render()
- getSnapshotBeforeUpdate()
- componentDidUpdate()

## Unmounting

- componentWillUnmount()

## Errors

- componentDidCatch()

---

# Lifecycle Methods Diagram

![react-component-lifecycle](https://res.cloudinary.com/btvca/image/upload/v1574445197/curriculum/react-component-lifecycle_vmdxp1.png)

<http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/>

---

# Responding to Events

- Event handling in React is similar to handling DOM events
- Handler functions can be passed as Props
- Event names are camelCased i.e. `onClick`, `onSubmit`, `onHover`

```html
<!-- HTML Event Handler -->
<button onclick="handleData()">Submit Data</button>
```

```javascript
/* React Event Handler */
<button onClick={handleData}>Submit Data</button>
```

---

# Preventing Default Behavior

- Works in the same way as preventing the default on a normal event
- Calling `event.preventDefault()` must be done in the handler

```javascript
function Link() {
  function handleClick(event) {
    event.preventDefault();
    doSomethingWithTarget(event.target);
  }

  return (
    <a href="#" onClick={handleClick}>
      Click Me React
    </a>
  );
}
```

---

# React Events are Synthetic Events

- Events in React are not **real** DOM events
- They are captured by React and replaced with a Synthetic Event
- Synthetic Events behave the same across all Browsers, unlike DOM Events

| Property               | Return Type    |
| ---------------------- | -------------- |
| bubbles                | boolean        |
| cancelable             | boolean        |
| currentTarget          | DOMEventTarget |
| defaultPrevented       | boolean        |
| eventPhase             | number         |
| isTrusted              | boolean        |
| nativeEvent            | DOMEvent       |
| preventDefault()       | void           |
| isDefaultPrevented()   | boolean        |
| stopPropagation()      | void           |
| isPropagationStopped() | boolean        |
| target                 | DOMEventTarget |
| timeStamp              | number         |
| type                   | string         |

---

# Events are Nullified after Handling

- After the event handler function is called the event is set to Null
- This is because SyntheticEvents are reused for other Events
- Do not handle events using Async functions, unless calling `event.persist()` first

---

# Usual Behavior

```javascript
function onClick(event) {
  console.log(event); // => nullified object.
  console.log(event.type); // => "click"
  const eventType = event.type; // => "click"

  setTimeout(function () {
    console.log(event.type); // => null
    console.log(eventType); // => "click"
  }, 0);

  // You can still access and use event properties.
  this.setState({ eventType: event.type });
}
```

[More on SyntheticEvents](https://reactjs.org/docs/events.html)

---

# Binding Event Handlers

- JavaScript classes do not by default `bind` the `this` in ES6 Classes
- Binding is a normal JavaScript behavior and is very confusing
- Either use `bind` in the constructor, or use an ES6 Arrow Function

```javascript
class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = { isToggleOn: true };

    // Binding is necessary to make `this` work in the callback
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState((prevState) => ({
      isToggleOn: !prevState.isToggleOn,
    }));
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? true : false}
      </button>
    );
  }
}

ReactDOM.render(<Toggle />, document.getElementById("root"));
```

[More about Binding Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)

---

# Binding Event Handlers - Arrow Functions

- Class constructor with `this.function = this.function.bind(this)` are verbose
- Rewrite the Class property as an arrow function as below
- Only available when transformed via Babel using `create-react-app` or other

---

```javascript
class LoggingButton extends React.Component {
  // This syntax ensures `this` is bound within handleClick.
  // Warning: this is *experimental* syntax.
  constructor(props) {
    super(props);
    this.state = { isToggleOn: true };
  }

  handleClick = () => {
    this.setState((prevState) => ({
      isToggleOn: !prevState.isToggleOn,
    }));
  };

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? "On" : "Off"}
      </button>
    );
  }
}
```

[Arrow Functions as Class Properties](https://medium.com/quick-code/react-quick-tip-use-class-properties-and-arrow-functions-to-avoid-binding-this-to-methods-29628aca2e25)
