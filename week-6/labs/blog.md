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

You will need to make a `pokemon.json` to store our data. While we will practice posting data, please note that we will not actually update this file from the API.

```json
[
  {
    "name": "bulbasaur",
    "hitPoints": 45,
    "attack": 49,
    "defense": 49,
    "description": "For some time after its birth, it grows by gaining nourishment from the seed on its back.",
    "abilities": [
      "chlorophyll",
      "overgrow"
    ],
    "evolution": {
      "name": "ivysaur",
      "level": 16
    },
    "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1.png",
    "id": 1
  },
  {
    "name": "ivysaur",
    "hitPoints": 60,
    "attack": 62,
    "defense": 63,
    "description": "When the bud on its back starts swelling, a sweet aroma wafts to indicate the flowers coming bloom.",
    "abilities": [
      "chlorophyll",
      "overgrow"
    ],
    "evolution": {
      "name": "venusaur",
      "level": 32
    },
    "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/2.png",
    "id": 2
  },
  {
    "name": "venusaur",
    "hitPoints": 80,
    "attack": 82,
    "defense": 83,
    "description": "After a rainy day, the flower on its back smells stronger. The scent attracts other Pokémon.",
    "abilities": [
      "chlorophyll",
      "overgrow"
    ],
    "evolution": {},
    "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/3.png",
    "id": 3
  },
  {
    "name": "charmander",
    "hitPoints": 39,
    "attack": 52,
    "defense": 43,
    "description": "The fire on the tip of its tail is a measure of its life. If healthy, its tail burns intensely.",
    "abilities": [
      "blaze",
      "solar-power"
    ],
    "evolution": {
      "name": "charmeleon",
      "level": 16
    },
    "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/4.png",
    "id": 4
  },
  {
    "name": "charmeleon",
    "hitPoints": 58,
    "attack": 64,
    "defense": 58,
    "description": "In the rocky mountains where Charmeleon live, their fiery tails shine at night like stars.",
    "abilities": [
      "blaze",
      "solar-power"
    ],
    "evolution": {
      "name": "charizard",
      "level": 36
    },
    "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/5.png",
    "id": 5
  },
  {
    "name": "charizard",
    "hitPoints": 58,
    "attack": 64,
    "defense": 78,
    "description": "It is said that Charizards fire burns hotter if it has experienced harsh battles.",
    "abilities": [
      "blaze",
      "solar-power"
    ],
    "evolution": {},
    "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/6.png",
    "id": 6
  },
  {
    "name": "squirtle",
    "hitPoints": 44,
    "attack": 48,
    "defense": 65,
    "description": "It shelters itself in its shell then strikes back with spouts of water at every opportunity.",
    "abilities": [
      "rain-dish",
      "torrent"
    ],
    "evolution": {
      "name": "wartortle",
      "level": 16
    },
    "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/7.png",
    "id": 7
  },
  {
    "name": "wartortle",
    "hitPoints": 59,
    "attack": 63,
    "defense": 80,
    "description": "It is said to live 10,000 years. Its furry tail is popular as a symbol of longevity.",
    "abilities": [
      "rain-dish",
      "torrent"
    ],
    "evolution": {
      "name": "blastoise",
      "level": 36
    },
    "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/8.png",
    "id": 8
  },
  {
    "name": "blastoise",
    "hitPoints": 79,
    "attack": 83,
    "defense": 100,
    "description": "The jets of water it spouts from the rocket cannons on its shell can punch through thick steel.",
    "abilities": [
      "rain-dish",
      "torrent"
    ],
    "evolution": {},
    "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/9.png",
    "id": 9
  }
]
```

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

