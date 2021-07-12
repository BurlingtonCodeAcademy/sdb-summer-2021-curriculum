# Lab: Setting Up an API Endpoint

For this lab we will go back to the `json-server` directory.  Currently it should contain one subdirectory that contains a single JSON file. We are going to extend this so that there is a front end that asks the user some questions, accepts answers from them, and greets them differently based on if the answers match up with the values stored in your JSON.

# Setting Up an API: The Server Side
First, let's run some commands to bring in necessary files and packages to our application live.

This first command creates a package.json for your file. This file contains metadata, a list of packages required for the project, and key-value pairs for command line scripts.
* `npm init -y`

Then we want to install Express, our server framework for NodeJS. 
* `npm install express`

Next we'll give the Express framework something to work with by creating our server file. A server stores, sends, and receives data between our filesystem and our application. It processes requests and delivers data. *This must be in the root level!*

* Create a `server.js` file in the root level of your project
* Set up your express application to use the `/client/build` folder as it's static directory.
  * This is where our React code will be compiled to!

## Setting up the API Route

Next we want to create an API from which the server will pull the desired information.
* Create an `example.json` file in the root level of your project
* Create a JSON object in this file
* The object should include key-value pairs for "name", "quest", and "favoriteColor"
* Provide the value for each key based on your desired answers


* Set up a route on the server that servers the `example.kson` file
* When the user visits `/check` they should see the raw JSON

## Creating the Front End

Finally, let's create Our front end so we can use this data.
* Create a new `create-react-app` named `client` inside the directory your server lives in.
  * remember to remove the hidden `.git` file from the `create-react-app` by:
    * `cd`ing into `client` directory
    * running the command `rm -rf .git`
* When the user visits the homepage there should be a form with fields for "name," "quest," and "favorite color."
* Use state, and event handlers to store the form data

* When the user fills out, and submits the form
  * The data from `example.json` should be fetched from the server
  * And if the answers match the values in `example.json`
  * A new component should replace the form
  * And the new component should say "Alrighty then, off you go. Good luck on your quest!"
* When the user fills out, and submits the form
  *And the answers **do not match** the values in `example.json`
  * The page render a different component
  * And the new component should say "Wrong answer! Into the chasm with you!"