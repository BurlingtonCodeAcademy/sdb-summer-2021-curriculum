# JSON?

JSON stands for "**J**ava**S**cript **O**bject **N**otation" and is one of the most common ways of sending data around the internet

JSON is a type of text document that is in the shape of a JavaScript object. However there are some restrictions to what kind of data you can put in a JSON object. In general JSON is only used for strings, numbers, and booleans, but mostly strings.

JSON objects can contain arrays of acceptable datatypes, and other JSON objects as the values for their keys, as well as the datatypes previously mentioned.

---

# Why JSON?

* used for data *sans* behavior
  * saving/loading to disk or database
  * transmitting information across network
* efficient to parse and compress
* human-readable, for the most part
* well-defined rules for whitespace and [character encoding](https://tools.ietf.org/html/rfc7159#section-8)
  * always Unicode, usually UTF-8
* very flexible data format
  * allows arbitrary nesting of arrays and objects (hashes)

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

A JSON file might contain multiple JSON objects. In this case the JSON file will contain an *array* of JSON objects

---

# Example JSON Collection

```javascript
[
    {
       "precision": "zip",
       "Latitude":  37.7668,
       "Longitude": -122.3959,
       "Address":   "",
       "City":      "SAN FRANCISCO",
       "State":     "CA",
       "Zip":       "94107",
       "Country":   "US"
    },
    {
       "precision": "zip",
       "Latitude":  37.371991,
       "Longitude": -122.026020,
       "Address":   "",
       "City":      "SUNNYVALE",
       "State":     "CA",
       "Zip":       "94085",
       "Country":   "US"
    }
]
```

(from [the spec](https://tools.ietf.org/html/rfc7159#section-13))

---

# Viewing JSON in Browser

* Its mime-type is `application/json` which most browsers will display all on one line :-(
* There are browser extensions that will render it better
  * Chrome: [JSON Viewer](https://github.com/tulios/json-viewer) (click on "Chrome Web Store" button to install)


![json viewer screenshot](https://raw.githubusercontent.com/tulios/json-viewer/master/screenshot.png)

---

# Viewing JSON in NodeJS Console

* JSON *is* JavaScript
* so if you _copy_ a JSON blob and _paste_ it into the Node REPL
* it will look like this:

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

(beware multi-line strings though: https://github.com/nodejs/node/issues/21657 )


# Parsing JSON in JavaScript

Parsing JSON in JavaScript is easy!

Since JSON objects are based off of JavaScript objects it's simple to translate them into true JavaScript objects.

There is a global `JSON` object in JavaScript that can be used to manipulate JSON data. The `JSON.parse(someJson)` method will translate `someJson` into a JavaScript Object
