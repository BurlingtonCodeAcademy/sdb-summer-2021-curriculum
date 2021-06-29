# Rendering Components Conditionally

* Components can be rendered using If/Else or a Ternary
* State within the Class or Function can be used in the conditions

>Note: Conditional `if...else` statements can't by used inline to do conditional rendering, but ternaries can.

---

# React Elements as Variables - Components

```jsx
const LoginButton = (props) => {
  return (
    <button onClick={props.onClick}>
      Login
    </button>
  );
}

const LogoutButton = (props) => {
  return (
    <button onClick={props.onClick}>
      Logout
    </button>
  );
}
```

---

```jsx
function LoginControl (props) {

  const [isLoggedIn, setLogIn] = useState(false)

  function handleLoginClick () {
    setLogIn(true);
  }

  function handleLogoutClick () {
    setLogIn(false);
  }

  let button;

  if (isLoggedIn) {
    button = <LogoutButton onClick={ handleLogoutClick } />;
  } else {
    button = <LoginButton onClick={ handleLoginClick } />
  }

  return (
    <div>
      <Greeting isLoggedIn={ isLoggedIn } />
      { button }
    </div>
  );
}
```

---

# Short Hand Logic Rendering

* The Locical And `Truthy/Falsy && someExpression`
* `truth && expression` is always true and evaluates `expression`
* `false && expression` is always false and evaluates `false`

```jsx
const Mailbox = (props) => {
  const unreadMessages = props.unreadMessages;
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&
        <h2>
          You have {unreadMessages.length} unread messages.
        </h2>
      }
    </div>
  );
}
```

---

# Live Example

[Example CodePen](https://codepen.io/Dangeranger/pen/ajPxBd)

---

# Inline Conditionals Using Ternary

* One line Ternaries are fine
* Do not use nested Ternaries if possible
  * They'll work, but they are confusing
  * having an `if...else if...else` logic block that you use to reassign a variable is generally much clearer
* Keep it simple

---

# Simple

```jsx
function Greeting (props) {

  const isLoggedIn = props.isLoggedIn;

  return (
    <div>
      The user is <b>{isLoggedIn ? 'currently' : 'not'}</b> logged in.
    </div>
  );
}
```

---

# More Complex

```jsx
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  return (
    <div>
      {isLoggedIn ? (
        <LogoutButton onClick={() => {setIsLoggedIn(false)}} />
      ) : (
        <LoginButton onClick={() => {setIsLoggedIn(true)}} />
      )}
    </div>
  );
```

---

# Preventing Component Rendering

```jsx
const WarningBanner = (props) => {
  if (!props.warn) {
    return null;
  }

  return (
    <div className="warning">
      Warning!
    </div>
  );
}
```

---

```jsx
function Page (props) {

  const [showWarning, setWarning] = useState(true)

  function handleToggleClick() {
    if(showWarning) {
      setWarning(false)
    } else {
      setWarning(true)
    }
  }

  return (
    <div>
      <WarningBanner warn={showWarning} />
      <button onClick={handleToggleClick}>
        Show Warning
      </button>
    </div>
  );
}
```

---

# Example CodePen

[Example CodePen](https://codepen.io/Dangeranger/pen/BPvEqv?editors=0010)
