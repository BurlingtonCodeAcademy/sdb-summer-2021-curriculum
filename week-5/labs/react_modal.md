# Modal Display

Let's create a simple modal popup using the power of conditional rendering!  Modal boxes are used all over the web, and are essentially a popup display. You see them quite often with image galleries where you can click a preview thumbnail, and the full size image opens as a popup, or to alert the user of some information, or prompt them to take some action.

A modal is a type of display element that sits on top of the page, and blocks interaction with other elements on the page until it is closed.

## Setting up the App

Inside your `react-apps` directory (the location where you installed `create-react-app`) create a new React application . It might take a couple of minutes for everything to install, but once it's all set up `cd` into the new directory, and open VSCode. Clear out the `return` statement of the `App` component.

In your `App` component create a button that we wil use to open our modal dialog box.

## Creating the Modal

Create a new file called `Modal.js` and inside this file set up a new React functional component called `Modal` which should:

- Cover the entire page with a semitransparent background when displayed
- Have a central opaque area with the text "Hello! I am a modal!"
- Have a button that we will use to close the modal
- Sit on top of everything else on the page

Import your `Modal` component into `App.js` and render it through the `App` component.

Currently our `Modal` component should be the only thing we can interact with on the page (though we might see other elements on the page through the semitransparent background). This isn't quite the behavior we want from our modal. We only want it to appear when we click the "open modal" button, and we want it to go away when we click the "close modal" button. So let's set up that functionality!

## Conditional Rendering

The first step is getting the modal off the page, so let's use our `useState` hook in the `App` component to create a new stateful property named `modalOpen` and the accompanying updater function `setModalOpen`. Set it with an initial value of `false`

Use one of the conditional rendering techniques we discussed earlier today to display `Modal` if `modalOpen` is true, otherwise display nothing.

Use the `setModalOpen` function to set the `modalOpen` property to `true` when it's clicked.

Now we can open our modal, but what about closing it?

## Passing Props

Since the "close modal" button is set up on our `Modal` component we will need to pass our updater function from `App` to `Modal` as a prop. When the "close modal" button is clicked use that prop to set your `modalOpen` property to `false`.

Try opening and closing the modal a few times.

You can now use the power of modals to create your own highly customizable alerts, and prompts!