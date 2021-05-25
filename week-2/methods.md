# Object Instance Methods

A method is a *function* attached to an *object* as a *property*. One of the main benefits of using objects is to create a predictable abstraction

---

# You've Already Used some Methods!

---

# Speaking Dog

---

# Passing Arguments to Methods

---

# Using Properties

---

# Using `this`

---

# Methods Can Access Object State

`this` is a magic word that means "this object I'm in *right now*"

```js
let rectangle = {
  height: 10,
  width: 8,
  area: function() {
    return this.height * this.width;
  }
}

rectangle.height   //=> 10
rectangle.area()   //=> 80
```

---

# `this` and Binding

---

# Fat Arrow Functions

---

# Extending objects on the fly

Since JavaScript is a *dynamic* language,
you can add methods to *any object*.


```js
let rectangle = {
    height: 10,
    width: 8,
}

rectangle.area()   //=> TypeError: rectangle.area is not a function

rectangle.area = function() {
     return this.height * this.width;
}

rectangle.area()   //=> 80
```

* remember, `this` means "this object I'm in *right now*" which in this case is the rectangle
* `this.height` on the *inside* of the object means the same as `rectangle.height` on the *outside*
