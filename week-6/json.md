# JSON

- JSON stands for "**J**ava**S**cript **O**bject **N**otation"
- one of the most common ways of sending data around the internet
- can only contain plain data -- no methods or comments

---

# Why JSON?

* used for data *without* behavior
  * saving/loading to disk or database
  * transmitting information across network
* efficient to parse and compress
* human-readable
* well-defined rules
  * always Unicode, usually UTF-8
* very flexible data format
  * allows for endlessly nestable data

---

# Example JSON object

```javascript
  {
    "Image": {
        "Width":  800,
        "Height": 600,
        "Title":  "View from 15th Floor",
        "Thumbnail": {
            "Url":    "http://www.example.com/image/481989943",
            "Height": 125,
            "Width":  100
        },
        "Animated" : false,
        "IDs": [116, 943, 234, 38793]
      }
  }
```

(from [the spec](https://tools.ietf.org/html/rfc7159#section-13))

---

# JSON Collections

- A JSON file might contain multiple JSON objects.
- It will contain an *array* of JSON objects.
- Looks and works like a normal JavaScript array
  - You can use any, and all, array methods on a JSON collection.

---

# Example JSON Collection

```javascript
[
    {
       "precision": "zip",
       "Latitude":  37.7668,
       "Longitude": -122.3959,
       "Zip":       "94107",
       "Country":   "US"
    },
    {
       "precision": "zip",
       "Latitude":  37.371991,
       "Longitude": -122.026020,
       "Zip":       "94085",
       "Country":   "US"
    }
]
```

(from [the spec](https://tools.ietf.org/html/rfc7159#section-13))

---

# Viewing JSON in the Browser

* Its mime-type is `application/json` which most browsers will display all on one line
  * No longer human-readable
* There are browser extensions that will render it better
  * Chrome: [JSON Viewer](https://github.com/tulios/json-viewer) (click on "Chrome Web Store" button to install)


![json viewer screenshot](https://raw.githubusercontent.com/tulios/json-viewer/master/screenshot.png)

---

# Viewing JSON in Node

* You can also _copy_ a JSON blob and _paste_ it into a Node REPL 

```
$ node
> { "Image": { "Width":  800, "Height": 600, "Title":  "View from 15th Floor", "Thumbnail": { "Url":    "http://www.example.com/image/481989943", "Height": 125, "Width":  100 }, "Animated" : false, "IDs": [116, 943, 234, 38793] } }
{ Image:
   { Width: 800,
     Height: 600,
     Title: 'View from 15th Floor',
     Thumbnail:
      { Url: 'http://www.example.com/image/481989943',
        Height: 125,
        Width: 100 },
     Animated: false,
     IDs: [ 116, 943, 234, 38793 ]
    }
}
```

---

# Parsing JSON in JavaScript

- `JSON.parse(someString)` => from string to object
- `JSON.stringify(someObject)` => from object to string

---

# JSON Restrictions

While JSON objects operate like normal JavaScript objects inside a JS file they do have some additional restrictions when defined in a JSON file.

* All strings, including object keys, must be double quoted
  * No single quotes, or template strings allowed!
* All values must be hard coded in, expressions can't be used, and won't be interpreted
* No methods, JSON is for data without behavior
* Any primitive data type is a valid value for a JSON property
* JSON supports nested JSON objects, and arrays

---

# Turning JavaScript into JSON

We can turn any JavaScript Object into a JSON object as long as it doesn't have any methods attached to it.

Call `JSON.stringify` passing in a JavaScript object to turn it into a string version of a JSON object. You can then pass it around, or store it in your application, and turn it into a JSON object where you need it by using `JSON.parse` on the stringified object.

```js
let customObj = {
  name: 'custom object'
}

let jsonString = JSON.stringify(customObj)
```

```js
let customJson = JSON.parse(jsonString)
```

