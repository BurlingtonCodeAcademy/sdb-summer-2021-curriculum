# What React Is

React.js is a front-end library for building user interfaces. It is maintained by Facebook and a community of individual developers. React can be used in the development of single-page, multi-page, or mobile applications.

The primary building block of React is the **Component**. A component is a JavaScript **Function**, or **Class**, that produces HTML, using a syntax called JSX.

```jsx
const MyComponent = () => {
  return <h1>Hello, world!</h1>;
}
```

```jsx
class MyComponent extends React.Component {
  render() {
    return <h1>Hello, world!</h1>;
  }
}
```

---

## Why React

1. React helps to make your front-end code more efficient and easier to maintain.
2. It  helps to build better user interfaces by providing a declarative way of describing how the UI should look and behave.
3. If you design simple views for each state in your application,
then React will efficiently update and render just the right components when your data changes.

```jsx
const Counter = () => {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

---

## A React Timer Example

```jsx
const Timer = () => {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds(seconds + 1);
    }, 1000);
    return () => {
      clearInterval(interval);
    };
  }, [seconds]);

  return (
    <p>Timer has been running for {seconds} seconds</p>
  );
};
```

---

## Definition of a React Component

- An isolated piece of a website or application, as either a Function or Class.
- Can receive Data from parent components in the form of `props`. Known as **passing data**.
- Can be created conditionally.
- Return HTML in the form of JSX. (JavaScript + XML)

---

## React is Component Based

React is built around the idea of using modular components to construct specific parts of a web page or application.

- Components make sections reusable.
- Small components can be combined into larger components.
- Each **instance** of a component can hold its own state
- Multiple **instances** of a single component can exist on a single page.

---

## Using Components

- Typically the main file (`index.js`) initiates the component tree
- The top most component is often called `App`, and is Usually made up of other sub-components
- Child components are **rendered** by parent components.
- Parent components can pass data as **props** to child components.

```jsx
const App = () => {
  const headerTitle = 'A React Example';
  const bodyContent = 'Some text to read';
  const copyRight = 'Copyright (c) 2022';
  return (
    <main>
      <Header title={headerTitle} />
      <Content text={bodyContent} />
      <Footer legal={copyRight} />
    </main>
  );
};
```

---

## Application Components Example

Any application can be decomposed into a series of components.

![React Component Example](https://reactjs.org/static/9381f09e609723a8bb6e4ba1a7713b46/90cbd/thinking-in-react-components.png)

The image above is an excerpt from the React.js documentation page [Thinking in React](https://reactjs.org/docs/thinking-in-react.html)

---

## Class Components

A React Class Component is a JavaScript Class that includes several pre-built methods to allow access to the React lifecycle. When using a React Class, you must create a new class that *extends* the React Component class.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'React'
    };
  }
  render() {
    return (
      <h1>Hello, {this.state.name}!</h1>
    );
  }
}
```

---

## Function Components

A React function component is a JavaScript Function that returns a React element in the form of JSX.

```jsx
const MyComponent = ({ name }) => {
  return (
    <h1>Hello, {name}!</h1>
  );
};

<MyComponent name='React' />
```

---

## Class Lifecycle Methods

React Class Components have lifecycle methods that can be used to perform specific tasks.

![react-component-lifecycle](https://res.cloudinary.com/btvca/image/upload/w_1200,c_scale/v1574445197/curriculum/react-component-lifecycle_vmdxp1.png)

The above image is an excerpt from <http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/>

---

## Responding to Events

- Event handling in React is similar to handling DOM events
- Handler functions can be passed as Props
- Event names are camelCased i.e. `onClick`, `onSubmit`, `onHover`

```html
<!-- HTML Event Handler -->
<button onclick="handleData()">Submit Data</button>
```

```jsx
/* React Event Handler */
<button onClick={handleData}>Submit Data</button>
```

---

## Preventing Default Behavior

Calling `event.preventDefault()` must be done in the event handler.

```jsx
const Link = () => {
  const handleClick = (event) => {
    event.preventDefault();
    doSomethingWithTarget(event.target);
  }

  return (
    <a href="#" onClick={handleClick}>
      Click Me
    </a>
  );
}
```

---

## React Events are SyntheticEvents

- Events in React are not **real** DOM events
- They are captured by React and replaced with a Synthetic Event
- Synthetic Events behave the same across all Browsers, unlike DOM Events

### Events are Nullified after Handling

- After the event handler function is called the event is set to Null
- This is because SyntheticEvents are reused for other Events
- Do not handle events using Async functions, unless calling `event.persist()` first

---

## Event Handlers in Class Components

- JavaScript classes do not by default `bind` the `this` keyword to the class instance
- Use an Arrow Function to ensure that `this` is bound to the class instance.
- Function components do not suffer from this binding  problem.

**See the next slide for a code example.**

---

## Bind Handlers with Arrow Functions

```jsx
class LoggingButton extends React.Component {
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
