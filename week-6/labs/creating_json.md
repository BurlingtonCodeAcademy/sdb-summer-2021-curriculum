# Lab: Creating a JSON file


## Welcome!

In this lab we will be creating a JSON file which we will be using as an api endpoint in a future lab. Our JSON object will hold some data which represents the "correct" answers to a series of questions we will be asking on the client side

## Structuring the Directory

- In your Terminal, create a new directory named `json-server` with `mkdir json-server`
- Enter the directory with `cd json-server`
- Inside this directory, create a subdirectory called `api` using `mkdir api`
- Enter the directory using `cd api`
- Inside `api` create a file named `example.json`
- Create another file named `answers.json`

We will be using `example.json` to play around with some different json structures, and look at how we can view it in the browser.

`answers.json` will be used in a later lab to check against a form input, and provide a conditional response.

## Creating JSON

JSON files are easy to create since they are just JS objects that only contain strings.

 - Curly braces hold these objects, unless they are arrays
 - Arrays are held within square brackets

  The data inside each JSON object must be written in key: value pairs. **Keep in mind** that the keys need to be double quoted, as they are strings.

  - Template strings do not work!
  - Each `"key": value` pair must be separated by commas.
  - Your JSON also _cannot_ include comments.
  - Methods also will not work.

## Adding Data

Let's go ahead and create a couple JSON files now.

- In `answers.json` create a JSON object containing:
  - a name
  - a quest
  - a favorite color
