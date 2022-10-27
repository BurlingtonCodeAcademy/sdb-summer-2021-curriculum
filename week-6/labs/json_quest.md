# LAB: Extending JSON File to JSON Quest

We will be extending the previous [Creating a JSON](https://online.uprighted.com/lessons/written/creating-json) lab.

## Learning

- Forms.
- Fetching from a local API.
- Using fetched data to conditionally render information to the user.

## Achieving 

- A server that creates a local API route by serving `answers.json`
- A webpage with a form that asks the user for their name, quest, and color.
- The webpage should change its display depending on whether or not the user's answers match the answers in the JSON.

## Procedures

## Creating the Front End

Your front end should contain a form that asks the user for the following information: name, quest, and color.

Every input will need an `change` event that saves the value of the user input.

The form will need an `submit` that is detailed later on in the lab.

## Using the API

You will need to use `fetch` to get the data from your local end point. 

This fetch will be set up identically to how you learned in Week 4.

You will need to set name, quest, and color to states.

## Setting up the submit handler

When the user submits the form, we want to check their answers against the answers in the JSON. The JSON answers and the user answers should all be held in states.

IF all of their answers match the answers in the json, the text content of a div should change to inform the user they can continue on their way.

ELSE the text content of a div should change to inform the user they are denied passage.

## Outcome

- A server that creates a local API route by serving `answers.json`
- A webpage with a form that asks the user for their name, quest, and color.
- The webpage should change its display depending on whether or not the user's answers match the answers in the JSON.

## Going Further

- What if one answer is correct and the others are wrong? How could you change your conditional logic to inform the user of what the error is?
- Instead of changing the text content of a div, how could you render different components to users based on their answers?
- Complete the Going Further on [Creating a JSON](https://online.uprighted.com/lessons/written/creating-json). How would you change your states and logic to account for multiple potential answers?
