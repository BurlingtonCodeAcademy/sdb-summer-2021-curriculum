# Lab: Setting Up an API Endpoint

For this lab we will go back to the `json-server` directory.  Currently it should contain one subdirectory that contains a single JSON file. We are going to extend this so that there is a front end that asks the user some questions, accepts answers from them, and greets them differently based on if the answers match up with the values stored in your JSON.

# Setting Up an API: The Set Up

* `npm init -y`
* `npm install express`
* `npm install body-parser`
* Create a `server.js` file in the root level of your project
* Create a `public` directory inside `json-server` with a file named `index.html` inside of it, and a file named `reply.html`

# Setting Up an API: The Stories

* When the user visits the homepage there should be a form with fields for "name," "quest," and "favorite color."
* When the user visits `/check` they should see the raw JSON from the `example.json` file
* When the user fills out, and submits the form
  * And the answers match the values in `example.json`
  * The page should redirect to `/reply`
  * And the new page should say "Alrighty then, off you go. Good luck on your quest!"
* When the user fills out, and submits the form
  *And the answers **do not match** the values in `example.json`
  * The page should redirect to `/reply`
  * And the new page should say "Wrong answer! Into the chasm with you!"