# the `state` Object

React components keep track of private data in the `state` object.

- Each instance of a React Component has it's _own state_
- Stateful data can only be accessed by the component it belongs to
  - It can only be updated by that instance as well
- State is used to determine what the component shows
  - Or how the component is displayed
  - Or if the component is displayed
  - Or any other information you want that component to keep track of

---

# Updating State

To update the state in React you will want to use the state updating function `setState` passing in an object that has the stateful property you want to update, and the new value.

- Only the properties defined in the update object are changed. All other stateful data is preserved
- You can access previous state, by passing a callback instead of an object as the argument to `setState`
  - The argument to that callback function is the previous state
- In a functional component you can access the `state` object through the `useState` hook. More on that later!
- You should never directly update the state through reassignment. Ever.

---

# `setState` Example

```js
class Home extends React.Component {
  constructor(props) {
    super(props);
  }
}
```

---

# Never Touch the DOM

React expects to be responsible for all content on the page. It uses the differences between the DOM and the VDOM to determine what needs to be updated in each render cycle. If you go in and directly manipulate the DOM React gets very confused, and strange things start happening.

- Modify state to effect changes on the page. **Never directly manipulate the DOM**
- Use state to display variable data (e.g. a user name). **Never write directly to the DOM**
- Use state to track user input. **Don't even look at the DOM**
- Pretty much any time you find yourself using the `document` object in React you should rethink how you're doing things
  - There are some exceptions, but they are few and far between

---

# Controlled Inputs

We want our React components to be responsible for all their own data. We don't want to be storing data on the page directly without React getting notified. `<input>` elements like to store their data on themselves, as a value property which can lead to some unexpected behavior in React.

To get around this we can use _controlled inputs_. We store a value in state, and use that stateful property to determine what the value of our `input` element is. When the input is changed we update the value in state to reflect those changes.

```js
class ExampleForm extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      userInput: "",
    };
  }

  handleChange(event) {
    let newValue = event.target.value;

    this.setState({ userInput: newValue });
  }

  render() {
    return(
      <div>
        <h1>{this.props.title}</h1>
        <form>
          <input type="text" onChange={handleChange}    value={this.state.userInput} />

          <input type="submit" />
        </form>;
      </div>
    )
  }
}
```

---

# Props, and State

In React there are two sources of data for your components: `props`, and `state`.

**State:**

- Private data held by the component
- Can only be read, and modified by the component it belongs to
- Defined as an object in the constructor
- Must be modified with the updater method

**Props:**

- Data passed in from outside the component
- Read only property, cannot be modified from inside the component
  - Can only be modified where they are passed _from_
- Like `state` props are unique to the instance of their component
- Is the argument to your constructor

---

# Passing Props

To pass props to a component we need to *render* the component, and assign the `props` *as if the were html properties on an element*. This is why they're called "`props`."

If we were to use our `ExampleForm` component from before, passing the `title` prop would look like this

```js
render() {
  return (
    <ExampleForm title="Working With Controlled Inputs" />
  )
}
```

Our `prop` is title, and we're giving it the value `"Working With Controlled Inputs"`

---

# Using Props

To access `props` in a class based component you can reference `this.props` and then the name of the property you want to access. In the example from before `this.props.title` is how we can access the value `"Working With Controlled Inputs"`

* Prop names are just variable names
  * They should follow standard JS naming conventions. i.e. camelCase
* All props passed to a component become keys on the `props` object
* `props` can be used to share data between components
* `props` are *defined* when a component is rendered, but *used* in the component's definition

---

# Updating the Component

Whenever `props` or `state` change the `componentDidUpdate` lifecycle method gets triggered, and causes the component to be redrawn.

In generally you should only update a component by changing props or state. You don't want to manually trigger a rerender if you can avoid it.

If you are setting state from inside `componentDidUpdate` the state updater should be wrapped in a guard clause because a `setState` will automatically trigger `componentDidUpdate`. If your `setState` is unguarded it gets called during `componentDidUpdate` which calls another `setState`, which triggers `componentDidUpdate`, and now you're trapped in an infinite recursive loop which will break your application.
