# Error Boundaries

* JavaScript errors within Components can corrupt an entire App
* Boundaries place a container around errors to prevent propagation
* Child components errors are caught and contained
* ERrors become easier to track
* Fallback UI can be rendered on error

---

# Limitations

* Error boundaries only catch errors below themselves in the Render tree
* They cannot catch errors in:
  * Event handlers
  * Asynchronous code such as setTimeout or requestAnimationFrame
  * React pages generated on the Server
  * Errors from the ErrorBoundary itself

---

# Error Boundaries - Creation

* Any component can be a boundary if it defines a `componentDidCatch` lifecycle method
* `componentDidCatch` behaves like JavaScript `catch {}`
* Only React Class components can be Boundaries

---

```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }
  componentDidCatch(error, info) {
    this.setState({ hasError: true });
    logErrorToMyService(error, info);
  }
  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}
```

```jsx
<ErrorBoundary>
  <MyWidget />
</ErrorBoundary>
```

---

# Error Boundaries - componentDidCatch

* `error` is a JavaScript error object
* `info` is a JavaScript object with `componentStack`
  * Holds information about the component stack at the time of error
* Can be used as a top level wrapper, or many small error wrappers

```jsx
componentDidCatch(error, info) {

  /* Example stack information:
     in ComponentThatThrows (created by App)
     in ErrorBoundary (created by App)
     in div (created by App)
     in App
  */
  logComponentStackToMyService(info.componentStack);
}
```

---

# Example CodePen

[CodePen](https://codepen.io/Dangeranger/pen/oMRpQg?editors=0010)

---

# Error Boundaries - Within Event Handlers

* Event handlers are just normal JavaScript functions
* Use regular `try/catch` syntax to catch errors within the callback

---

```jsx
function MyComponent (props) {

  const [error, setError] = useState(null)

  const handleClick = () => {
    try {
      // Do something that could fail
    } catch (error) {
      setError(error);
    }
  }

  if (error) {
    return <h1>Caught an error.</h1>
  }
  return <div onClick={this.handleClick}>Click Me</div>
}
```

---

# Error Boundaries - Live Example

<p data-height="500" data-theme-id="light" data-slug-hash="oMRpQg" data-default-tab="js,result" data-user="Dangeranger" data-pen-title="oMRpQg" class="codepen">See the Pen <a href="https://codepen.io/Dangeranger/pen/oMRpQg/">oMRpQg</a> by Joshua Burke (<a href="https://codepen.io/Dangeranger">@Dangeranger</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
