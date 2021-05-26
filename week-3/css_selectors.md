# Selectors and Properties

  * CSS is constructed of **selectors** and **properties**.
  * Selectors determine where the styles are applied.
  * Properties determine what those styles are.
  * CSS begins with a selector, followed by curly braces.
  * Declare your styles inside the curly braces.

---

# Examples of Selectors

| selector         | meaning          |
|------------------|------------------|
| `p`, `div`, etc. | element selector |
| `.class`         | class selector   |
| `#id`            | ID selector      |
| `*`              | Wildcard ("any") |

---

# Examples of Properties

| property      | meaning                                |
|---------------|----------------------------------------|
| `color`       | text color                             |
| `border`      | Defines border width, style, and color |
| `text-align`  | justifies text                         |
| `font-size`   | size of font                           |
| `font-family` | defines font                           |

---

# Basic Selectors

---

# Order of Specificity

---

# the !important Property

---

# Compound Selectors 1

Selectors can target elements nested within other elements

```css
p img {
  max-width: 320px;
  height: auto;
}
```

...means "select all `img` tags that are a decendent of 

---

# Compound Selectors 2

Selectors can target specific elements with a class

```css
h1 .title {
  display: block;
  margin: 0, auto;
  padding-top: 1em;
}
```

---

# Compound Selectors 3

Selectors can target specific elements with several layers of nesting

```css
main .introduction > p {
  background-color: lightgray;
  margin: 10px auto;
}
```

"apply these styles to all `p`s that are direct children of a `div` of class `introduction` inside the `main` section"

---

# Compound Specificity

---

# Psuedo-Class Selectors

You can target the state of an element using `psuedo-class` selectors

  * Hover
  * Visited
  * Checked
  * Active
  * Many others

[Full List on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes "Full list of CSS psuedo-classes on Mozilla Developer Network")

[MDN Psuedo-Class Tutorial](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements "MDN Psuedo-Class Tutorial")

```css
a:hover {
  background-color: red;
}

a:clicked {
  background-color: blue;
}

a:active {
  background-color: green;
}
```

---

# CSS Diner

* Complete the CSS selector game linkeed below

  * https://flukeout.github.io/
