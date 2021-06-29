# Lifting State to Parents

* React components can manage their own state
* Often components need to communicate state to others
* Siblings do not pass state to each other directly
* State should pass through a parent, then trickle down

---

# Code Along: Boiling Point Calculator

```jsx
class BoilingVerdict extends React.Component{
  let message = ''
  if (props.celsius >= 100) {
    message = <p>The water would boil.</p>;
  } else {
    message = <p>The water would not boil.</p>
  }

  render() {
    return message
  }
}
```

---

# Lifting State - Calculator Input

```jsx
class Calculator extends React.Component {

  constructor(props) {
    super(props)
    this.state = {
      temperature: ''
    }
  }

  render() {
    return (
      <fieldset>
        <legend>Enter temperature in Celsius:</legend>
        <input
          value={temperature}
          onChange={(evt) => {
            this.setState({temperature: evt.target.value})
          }} />

        <BoilingVerdict
          celsius={parseFloat(temperature)} />
      </fieldset>
    );
  }
}
```

---

# Lifting State - Another Input

* Let's make the calculator work for both celsius and fahrenheit

### Changing the Render

```jsx
render() {
  return (
    <div>
      <TemperatureInput scale="c" />
      <TemperatureInput scale="f" />
    </div>
  );
}
```

---

# Extract TemperatureInput

```jsx
class TemperatureInput extends React.Component {
  constructor(props) {
    super(props)
    this.state = {
      temperature
    }
  }

  render() {
    return (
      <fieldset>
        <legend>Enter temperature in {scaleNames[this.props.scale]}:</legend>
        <input value={temperature}
          onChange={(evt) => {
              this.setState(temperature: evt.target.value)
            }
          }
        />
      </fieldset>
      );
    }
  }
}
```

---

# Lifting State - Passing State

* The components must be kept in sync
* Each TemperatureInput holds it's own state
* Sibling components can not communicate directly
* State can be moved to `Calculator` to achieve this

---

# Remove State from TemperatureInput

```jsx
class TemperatureInput extends React.Component {
  handleChange = (evt) => {
    props.setTemperature(evt.target.value);
    props.setScale(props.scale)
  }
  render() {
    return (
      <fieldset>
        <legend>Enter temperature in {scaleNames[scale]}  :</legend>
        <input value={this.props.temperature}
               onChange={this.handleChange} />
      </fieldset>
    );
  }
}
```

---

# Lifting State - Parent State

* Children call `setTemperature` from props with new state
* Parent updates state with `setTemperature`
* Children re-render with new props

---

# Parent `Calculator` Passes State to Children

```jsx
class Calculator extends React.Component {

    constructor(props) {
      super(props)
      this.state = {
        scale: 'c',
        temperature: ''
      }
    }

    setScale = (evt) => {
      this.setState(
        {scale: evt.target.value}
      )
    }

    setTemperature = (evt) => {
      this.setState(
        {temperature: evt.target.value}
      )
    }

```

---

```jsx
  render() {
    const celsius = this.state.scale === 'f' ? tryConvert(temperature, toCelsius) : temperature;
    
    const fahrenheit = this.state.scale === 'c' ? tryConvert(temperature, toFahrenheit) : temperature;
    return (
      <div>
        <TemperatureInput
          scale="c"
          temperature={celsius}
          setScale={setScale}
          setTemperature={setTemperature}
        />

        <TemperatureInput
          scale="f"
          temperature={fahrenheit}
          setScale={setScale}
          setTemperature={setTemperature}
        />

        <BoilingVerdict
          celsius={parseFloat(celsius)} />
      </div>
    );
  }
}
```

---

# Lifting State - Live Example

<p data-height="265" data-theme-id="light" data-slug-hash="djrKLj" data-default-tab="js,result" data-user="Dangeranger" data-pen-title="djrKLj" class="codepen">See the Pen <a href="https://codepen.io/Dangeranger/pen/djrKLj/">djrKLj</a> by Joshua Burke (<a href="https://codepen.io/Dangeranger">@Dangeranger</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

---

# Lifting State - Conclusions

* A single "point of truth" holds the state
* Components communicate state by lifting it up to a Parent
* Child components use a Parent updater function to lift state up
* State flowing down makes state changes simpler to debug
* Props should be derived from State

---

### Links

- [Top Down Data Flow](https://reactjs.org/docs/state-and-lifecycle.html#the-data-flows-down)
