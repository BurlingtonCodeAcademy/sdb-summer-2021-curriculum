# React Modal

## Objective

To understand how to conditionally render the contents of a modal and how to pass a function as props to a child component. Modals are pop-ups that are typically dynamically rendered.

## Learning

In this lab, we will practice with using React to conditionally render elements on the page. We will need to pass props (both a state and a function) to do so.

Topics:

- React conditional rendering
- React props

## Achieving

Your work will result in:

- A webpage with a 'Open Modal' button.
- When the button is clicked, a semi-transparent modal pops up that covers the original content. It should inform the user it is a modal, and contain a 'Close Modal' button.
- When 'Close Modal' is clicked, the modal disappears and only the original content remains.

## Procedure

### Setting up the components

- [ ] Create a new file, `Modal.jsx`. Set up `Modal.jsx` as you would any other new component. 

_In `App.jsx`_

- [ ] Ensure you have the Modal component imported.
- [ ] Create the `modalState` state variable and have it set initially to `false`.
- [ ] Create a function named `handleClick`.
- [ ] Within `handleClick`, set up the following conditional logic: if `modalState` is true, `setModalState` to false. Else, `setModalState` to true.
- Now, in the return statement, set up the following:
- Within `<main>`, a button that has an onClick event set to the `handleClick` function and has the text "Open modal".
- Below the button, a paragraph of placeholder text.
- Below the paragraph, render `<Modal />`. Pass it two props: `modalState` and `handleClick`.

_In `Modal.jsx`_

-  [ ] Ensure the Modal function accepts the parameter of `props` AND that `Modal.css` is imported.
-  [ ] Inside of your Modal function, the first line will be a conditional if statement that checks if `props.modalState` is true.
-  [ ] **Inside of the if statement's code block**, set up a `return()` statement that contains the following:
-  [ ] A `<main>` element with an id of `modal-background`.
-  [ ] A `<section>` element with an id of `modal-content`; it should contain "I am a modal!"
-  [ ] A `<button>` within `<section>`with the `onClick` event of `props.handleClick` and the text "Close modal."
-  [ ] **Outside of the if statement's code block**, set up a `return()` statement that contains the following:
-  [ ] A `<div>` with an inline `style` of `display:"none"`.


## Review

In this lab, we will have created a page that contains buttons to open and close a modal. 

The software should:

- Have placeholder text and an "Open Modal" button.
- When the "Open Modal" button is clicked, new elements appear on the page that inform the user that this is a modal; it also contains a "Close Modal" button.
- When the "Close Modal" button is clicked, the new elements disappear and the page returns to its original state.

## Going Further

- Many modals you come across on the Internet do not utilize a "Close" button but close when you click on the background. How could you implement an `onClick` event to do this?
- Many modals you come across on the Internet pop up upon page load. How would you change the conditional logic and buttons to acheive this?
- This modal is not styled. Try incorporating this [frontendmentor challenge](https://www.frontendmentor.io/challenges/order-summary-component-QlPmajDUj) so your modal is now an order summary. You will need to import the image assets and the fonts into replit.
