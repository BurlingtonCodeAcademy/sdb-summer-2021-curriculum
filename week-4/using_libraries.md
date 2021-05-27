# Programming Libraries

a Library is just someone elses code that modifies the way your code works. In fact we've already used some libraries in the first few weeks of this course. Remember readline? That was a core Node library, so it came installed with NodeJS. To use it all we had to do was import it into our program.

---

# Importing in the Browser

When working in the browser we don't have access to Node, and the way we import things changes. What we can do is source a script tag

---

# Order of Scripts

---

# Web Mapping

---

# LeafletJS

* LeafletJS is a JavaScript **library** which allows for the creation of and interaction with web maps.
* It uses a simple API for building maps using **Layers**
* It allows for styling of the map layers using standard CSS and manipulation with JavaScript

---

# The `L` Object

* **L** is the **global** LeafletJS function.
* You can access all the objects and functions within LeafletJS from **L**
* There is extensive documentation:
  * <https://leafletjs.com/reference-1.6.0.html>

---

# Adding Markers

* Markers add a point to the map
* The text of a marker can be set using a string of HTML

```js
let marker = L.marker([51.5, -0.09]).addTo(mymap);
marker.bindPopup("<b>Hello world!</b><br>I am a popup.").openPopup();
```

---

# Removing Markers

* Markers can be removed by calling `remove()` on the marker object

```js
let marker = L.marker([51.5, -0.09]).addTo(mymap);
marker.remove();
```

---

# Adding Polygons

* Polygons are arbitrarily shaped regions of the map
* They can be created and added to the map

```js
let polygon = L.polygon([
  [51.509, -0.08],
  [51.503, -0.06],
  [51.51, -0.047],
], { color: 'red'}).addTo(mymap);

// delete the polygon later
polygon.remove()
```

---

# PolyLine