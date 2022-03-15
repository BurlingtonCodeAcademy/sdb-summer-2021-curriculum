# LAB: Let's Practice Using Data in Express!

## Welcome!

We are going to add to the API from our previous lab to make requests using the 3 different types of data we can pass via a request: req.params, req.query, and req.body.

We will also learn to use an API-testing tool called [Postman](https://postman.co) (< click this), so that we do not need to have a frontend at all. Yay! 🥳

## Routes:

* GET `/` - App is listening
* GET `/pokemon` - Get all pokemon
* GET `/pokemon/:id` - Get pokemon by id
* GET `/search` - Get all matching pokemon
* POST `/pokemon` - Add a new pokemon

## Database

We will be using the `pokemon.json` to store our data. While we will practice posting data, please note that we will not actually update this file in this lab. 

## Server Setup

- Add the routes to fulfill the above list. 
- You'll want your routes to just console.log data for now
  - Consider which route will use which of your 3 options of data sources:
    - req.params
    - req.body
    - req.query
- Make a pokemon.json file in your project and put the given data in there. (Note: If you have not been given data, we forgot! Ask for it!)
- Remember to import this data so that you can use it in your file. 

# Getting A Pokemon By ID

- Our first route will match `/pokemon/1` and return the JSON associated with just ONE pokemon. 
- You will need to use your JavaScript fundamental skills to access the inner data and find what you need. 
- Use Postman to test that this route indeed works and sends the response with the corresponding JSON.

# Viewing All Pokemon 

- Now you will flesh out your `/pokemon` route
- You want this to return the *entire* list of pokemon when someone makes a GET request. 
- Be sure to use your testing tool to make the request and check the response. 

# Make a New Pokemon

- Flesh out your `/pokemon` route for the POST request.
- You don't have a database, so you'll "pretend" to save the data for now. 
  - Check to make sure the data from the client has the minimum requirements to make a new pokemon
    - If it does not
      - Send a `422` status code to let the client know their data is not proper.
    - If it does...
      - Send a `204` status code letting the client know that the Pokemon was successfully made. 


# Search Your Pokemon Data

- Now, it's time to flesh out your `/search` route
- Searches are a great time to use queryStrings, instead of params or the body data. 
- Make sure your route, sends a JSON response back to the client with all the pokemon that match their search query. 
  - Note: This might be more than one -- consider your data structure wisely. 

