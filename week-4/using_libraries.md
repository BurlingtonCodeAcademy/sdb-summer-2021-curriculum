# Programming Libraries

a Library is just someone elses code that modifies the way your code works. In fact we've already used some libraries in the first few weeks of this course. Remember readline? That was a core Node library, so it came installed with NodeJS. To use it all we had to do was import it into our program.

---

# Importing in the Browser

When working in the browser we don't have access to Node, and the way we import things changes. What we can do is source a script tag to a CDN where some JavaScript file lives

---

# Order of Scripts

When importing packages via a `script` tag the order you put them in your HTML does matter. Because HTML renders top to bottom the script tags will be rendered, and interpreted in order, and operate as if they are in the same file. This is useful, but can cause issues if you're reusing variable names.

- HTML is rendered procedurally from top to bottom
- A script that is imported later will have access to all global variables from files imported before it
- To make sure the elements of the page exist before the JS is interpreted internal script files are usually put at the bottom of your HTML's body
- Exterior packages are usually put in the head of the HTML document since it won't need access to the page elements

---

# Web Mapping

Web mapping is the process of creating maps on the internet. This is a deceptively tricky process, and is very hard to get right, so we'll be using a pre built library to help us create and manipulate some maps

Probably the most well known web mapping framework is Google maps. Google Maps revolutionized web mapping, and web development in general by being one of the first applications to prove that web apps could be as powerful as desktop apps.

Today we'll be looking a different web mapping library, LeafletJS. Leaflet is the second largest web mapping library in the world. It's open source, and free to use, and often has more consistent data than Google Maps.

---

# LeafletJS

- LeafletJS is a JavaScript **library** which allows for the creation of and interaction with web maps.
- It uses a simple API for building maps using **Layers**
- It allows for styling of the map layers using standard CSS and manipulation with JavaScript

---

# The `L` Object

- **L** is the **global** LeafletJS function.
- You can access all the objects and functions within LeafletJS from **L**
- There is extensive documentation:
  - <https://leafletjs.com/reference-1.6.0.html>

---

# Creating a Map

---

# Adding Markers

- Markers add a point to the map
- The text of a marker can be set using a string of HTML

```js
let marker = L.marker([51.5, -0.09]).addTo(mymap);
marker.bindPopup("<b>Hello world!</b><br>I am a popup.").openPopup();
```

---

# Removing Markers

- Markers can be removed by calling `remove()` on the marker object

```js
let marker = L.marker([51.5, -0.09]).addTo(mymap);
marker.remove();
```

---

# Adding Polygons

- Polygons are arbitrarily shaped regions of the map
- They can be created and added to the map

```js
let polygon = L.polygon(
  [
    [51.509, -0.08],
    [51.503, -0.06],
    [51.51, -0.047],
  ],
  { color: "red" }
).addTo(myMap);

// delete the polygon later
polygon.remove();
```

---

# Polyline

- a poly line is a line drawn between a collection of two or more points
- it goes point to point, in the order the points are defined
- you can set up a poly line in a very similar manner to a polygon, but it won't close itself off
- to extend a poly line you can use the `.addLatLng` method

```js
let line = L.polyline([
  [45.51, -122.68],
  [37.77, -122.43],
  [34.04, -118.2],
]).addTo(myMap);
```
