# Setting Up an API Endpoint

For this lab we will go back to the `json-server` directory.  Currently it should contain one subdirectory that contains two JSON files, but we only care about the `answers.js` file in this lab. We are going to extend this so that there is a front end that asks the user some questions, accepts answers from them, and greets them differently based on if the answers match up with the values stored in your JSON.

## Structuring your Directory

* Run the Command `npm install create-react-app`
* Create a new `create-react-app` named `client` inside the directory your server lives in.
  * remember to remove the hidden `.git` file from the `create-react-app` by:
    * `cd`ing into the `client` directory
    * running the command `rm -rf .git`
* Set up your express server to use the `/client/build` folder as it's static directory.
  * This is where our React code will be compiled to!

## Setting up the API Route

Next we want to create an API from which the server will pull the desired information. If you haven't already:

* Create an `answers.json` file in the `api` directory of your project
* Create a JSON object in this file
* The object should include key-value pairs for "name", "quest", and "favoriteColor"
* Provide the value for each key based on your desired answers

## Making the API Route

* Set up a route on the server listening for a `GET` request on the path `"/check"` that servers the `answers.json` file
* When the user visits `/check` they should see the raw JSON

We will be fetching from this route on the client side to check our answers

## Creating the Front End

Finally, let's create Our front end so we can use this data.

* When the user visits the homepage there should be a form with fields for "name," "quest," and "favorite color."
* This should be a *controlled input* form since we're working with react
  * That means the data should not go from the client to the server!
  * Use event handlers to store the form data in state when the form is submitted

## Using the API

If you're using a functional React component bring in the `useEffect` hook and set it up so that:

* When the user fills out, and submits the form
  * The data from `answers.json` should be fetched from the api route you set up on the server
  * Check the data in the JSON object you just fetched against the data stored in state
  * And if the all the answers match the values in `answers.json`
    * A new component should replace the form
    * And the new component should say "Alrighty then, off you go. Good luck on your quest!"

* When the user fills out, and submits the form
  * And the answers **do not match** the values in `answers.json`
  * The page renders a different component
    * And the new component should say "Wrong answer! Into the chasm with you!"