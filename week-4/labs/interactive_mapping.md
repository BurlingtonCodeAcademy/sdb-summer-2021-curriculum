# Interactive Mapping

## Welcome!

In this lab we will be building web application with a map that will allow us to enter an address through a form, and then use that address to drop a pin on the map, and zoom to it. Create a new directory, and inside it create an `index.html` page with a container for a map, and a form that will allow a user to enter an address.

# Leaflet

Leaflet is an open source web mapping library It's also the second largest provider of web based maps in the world (right after Google Maps).

Leaflet is a great resource, and has very good [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) and [tutorials](https://leafletjs.com/examples.html). If you are struggling with any aspects of this lab, check the documentation.

# Installation

Include the CSS and JavaScript in the Head of the HTML page

**Add the CSS First**
**Then the JavaScript**

Now you have access to Leaflet's `L` object, and can use it to set up your map in your JavaSCript file. Don't forget to link your JS file to your HTML!

# Using a Basemap

There are many open source tile sets you can use for Leaflet which change the way your map looks

Look through the basemap providers for LeafletJS here:
<https://leaflet-extras.github.io/leaflet-providers/preview/>

And choose one that you like to use as your `tileLayer`.

# Geocoding

Geocoding is the process of converting an address into a set of lat/long coordinates.

Leaflet can only add markers (and polygons, and lines, and...) by using lat/long values. So if we want to add markers at certain addresses we will need to use geocoding to get their lat/long locations.

# Geocoding Services

Geocoding like many mapping problems can be rather tricky. Luckily there are free resources we can use to do the geocoding for us! The one we will be using in this lab is called '[nominatim](https://nominatim.openstreetmap.org/)'

# Nominatim

To get a set of geographic coordinates from nominatim you can go to [nominatim.openstreetmap.org](https://nominatim.openstreetmap.org/) and enter an address in the search bar.

This will redirect you to a zoomed in view of the address, and you will see a blue box with the address on the left side of the screen, underneath the 'search' bar.

Click on the button labeled 'details' to see all sort sof geographic information about the address including the latitude and longitude.

# Success!

You can now use the data from the `Center Point` value, which is in lat, long format, to add a marker to your Leaflet map.

Be we want our users to be able to look up the address on our site, we don't want to be sending them to Nominatim!

# Make it Procedural

Let's write a function that when given an address fetches the lat/long value from Nominatim, and brings it back to us.

First we'll need to send a fetch to nominatim, passing in whatever address our user enters. We can use a query parameter in the address we're fetching from to fetch data for a specific address in a specific format. Since we're writing a JavaScript program JSON will be extremely easy for us to deal with.

```js
function getLatLong(address) {
  fetch(`https://nominatim.openstreetmap.org/search/?q=${address}&format=json`)
    .then((res) => res.json())
    .then((geoJson) => {
      //This is where you can interact with your GeoJSON data
    });
}
```

# Sanitize Your Inputs!

A normal string isn't necessarily url safe. Luckily we can use the function `encodeURIComponent()` to turn any string into a url safe string.

```js
function getLatLong(address) {
  let urlAddress = encodeURIComponent(address);
  fetch(
    `https://nominatim.openstreetmap.org/search/?q=${urlAddress}&format=json`
  )
    .then((res) => res.json())
    .then((geoJson) => {
      //This is where you can interact with your GeoJSON data
    });
}
```

# Translate the Data

Now that we've fetched the data we need from Nominatim we need to translate it into something we can use. We can do this by chaining promises with `.then()`, making our `getLatLong` function asynchronous and awaiting our fetch

> Remember: `.then()` only returns a promise so to get the values out of the function we'll need to have a variable we can manipulate

```js
async function getLatLong(address) {
  let urlAddress = encodeURIComponent(address);
  let latLngObj = {
    lat: null,
    long: null,
  };

  await fetch(
    `https://nominatim.openstreetmap.org/search/?q=${urlAddress}&format=json`
  )
    .then((res) => res.json())
    .then((jsonObj) => {
      latLngObj.lat = jsonObj[0].lat;
      latLngObj.long = jsonObj[0].lon;
    });

  return latLngObj;
}
```

# Congratulations!

You now have a function that can take any address and get a lat/long object back for that address! Now we can use this function as part of an event listener on our form.

When an address is entered, and the form is submitted we want to:

* Get the Lat/Long coordinates for that address
* Use those coordinates to zoom our map to a new center
* Drop a pin at the new center point of the map.

Don't forget to add lots of `console.log`s throughout your code to make sure the data is what you expect it to be!
