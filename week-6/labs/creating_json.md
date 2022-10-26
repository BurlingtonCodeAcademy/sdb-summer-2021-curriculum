# Lab: Creating a JSON file

We will be creating a JSON file to use in our next lab.

## Learning

- Express Server
- JSON files

## Achieving

- A server that serves a JSON file that you created.

## Procedure

## Setting up your files

Create a new folder called **creating-json** in your **labs** folder. Initialize your project there with `npm init -y`.

## Creating the Express server

You will need to set up an Express server with the basic boilerplate code.

This boilerplate includes:

- Importing express and assigning the invocation to a variable.
- Setting up your port.
- Setting up the listen method.

## Creating the JSON

- Create a new subfolder at the top level, called `api`.
- Within `api`, create `answers.json`
- This JSON should contain the following key-value pairs: name, quest, favorite color.
- _Think back to a previous project where you were provided a JSON and use that as a reference for syntax_


## Serving the JSON

In your server, use a GET method to serve your 'answers.json' file. If you have done this correctly, when you navigate to the server in the browser at the route of the GET, you will see your JSON.

## Outcome 

- A server that serves a JSON file that you created.

## Going Further

- Add multiple values to each key, either as an array or an object. This would allow for multiple names, quests, and favorite colors. 
