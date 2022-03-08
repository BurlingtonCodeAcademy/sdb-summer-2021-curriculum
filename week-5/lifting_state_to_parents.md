# Lifting State to Parents

* Given data can *only* move down ⬇️ the component tree,
* Given the same data might be used in several different components,
* We might find ourselves in a position where the data's starting point needs to be moved

![react component diagram](https://reactjs.org/static/9381f09e609723a8bb6e4ba1a7713b46/90cbd/thinking-in-react-components.png)

---

# Follow Along: Boiling Point Calculator

We are going to make a boiling point calculator together.

<https://replit.com/team/education-team/lifting-up-state>

---

# Lifting State - Conclusions

* The state's origin point is its "single source of truth."
* Parent components can send functions to children to update their own (parent) state.
* Data "flows" down the component tree.
* We use props to spread state throughout our applications.

