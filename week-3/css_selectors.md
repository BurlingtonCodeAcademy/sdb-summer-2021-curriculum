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

# Order of Specificity

All CSS selectors have a level of specificity which is used to determine which styles to apply to which elements.

* 5. Element Selectors
* 4. Class Selectors
* 3. ID Selectors
* 2. Inline CSS
* 1. !important

---

# the !important Property

The `!important` property can be added to any style to apply that style on the specified type of element no matter what. Styles tagged with `!important` will always overwrite any other styles, even inline styles.

Because of this `!important` should be used sparingly.  Using `!important` is almost never the correct way for you to apply a style. It should only be used as a method of last resort.

---

# Compound Selectors 1

Selectors can target elements nested within other elements

```css
p img {
  max-width: 320px;
  height: auto;
}
```

...means "select all `img` tags that are a descendent of a `p` tag

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

# Compound Operators

We can apply compound operators to our compound selectors to further refine which elements are targeted.

* `>` Direct children only
* `,` Either matching selector
* `+` Immediately adjacent sibling elements
* `~` Subsequent sibling elements.

---

# Compound Specificity

In general compound selectors are at the same level of specificity as their most specific identifier, but they are more specific than non-compound selectors.

Longer compound selectors will be more specific than shorter compound selectors *of the same basic level of specificity*

* a compound selector looking through 3 tags e.g. `main div p` would be more specific than `main div`
* a compound selector containing a *class* is more specific than one just containing *tags*
  * even if the one with just tags is longer
* a non-compound *id* selector would be more specific than a compound selector that only contains *tags* and *classes*

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

---

# Pseudo-Class Selector Example

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

* Complete the CSS selector game linked below

  * https://flukeout.github.io/
