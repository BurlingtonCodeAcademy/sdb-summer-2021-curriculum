# Lab: Setting Up an API Endpoint

For this lab we will go back to the `json-server` directory.  Currently it should contain one subdirectory that contains a single JSON file. We are going to extend this so that there is a front end that asks the user some questions, accepts answers from them, and greets them differently based on if the answers match up with the values stored in your JSON.

# Setting Up an API: The Set Up
First, let's run some commands to bring in necessary files and packages to our application live.

This first command creates a package.json for your file. This file contains metadata, a list of packages required for the project, and key-value pairs for command line scripts.
* `npm init -y`

Then we want to install Express, our server framework for NodeJS. 
* `npm install express`

Next we'll give the Express framework something to work with by creating our server file. A server stores, sends, and receives data between our filesystem and our application. It processes requests and delivers data. *This must be in the root level!*
* Create a `server.js` file in the root level of your project

Next we want to create an API from which the server will pull the desired information.
* Create a `example.json` file in the root level of your project
* Create a JSON object in this file
* The object should include key-value pairs for "name", "quest", and "favorite color"
* Provide the value for each key based on your desired answers

Finally, let's create a directory to store two HTML files, which will hold our HTML endpoints.
* Create a `public` directory inside `json-server` with a file named `index.html` inside of it, and a file named `reply.html`

# Setting Up an API: The Stories

Our `index.html` file acts as our main page. Add html elements to this file to complete the story below:
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