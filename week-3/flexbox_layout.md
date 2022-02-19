# Introduction to Flexbox

Flexbox is a modern tool for website layout.

Flexbox solves many issues that have existed since the beginning of CSS.

Flexbox helps to accomplish the following:

- Horizontal or vertical alignment of elements
- Arrangement of elements
- Space distribution between elements
- Space distribution around elements

---

## Notes to Remember

- Flexbox is one-dimensional. It can arrange items either in a row, or a column, but not both at the same time.
- Flexbox is useful for laying out elements such as navigation bars, headers, image galleries, etc.
- Flexbox _fixes_ CSS layout madness by placing the responsibility for layout with the _container_, and not asking _each item_ to be responsible for laying _itself_ out
- Flex containers only operate on their _direct children_

---

## The Flex Container

Flexbox works by applying CSS properties to both the container, and the children inside the container.

- First: add the CSS property `display:flex;` to the container of the items you intend to arrange.
- Remember, Flexbox is one dimensional. `display:flex` arranges your items in a row. This can be changed with `flex-direction: column`

---

## Flex Container Example

```css
.container {
  display: flex;
  flex-direction: row;
}
```

---

## Flexbox Direction Comparison

<!-- markdownlint-disable-next-line -->
<img src="https://cdn-images-1.medium.com/max/1600/1*4yKnG2-vuPF5XA-BmXADLQ.gif" width="1200" alt="Illustration of Flex Container" title="Flex Container">

---

## Justify Content

Justifying your content, both horizontally and vertically, used to be challenging.

Flexbox makes this easy. There are five different values for the CSS property `justify-content`:

1. `flex-start`
2. `flex-end`
3. `center`
4. `space-between`
5. `space-around`

![Justifying content with Flexbox](https://cdn-images-1.medium.com/max/1000/1*2-6Tw8jqWrMKOfIugKyuDA.gif "Justify Content with Flexbox")

---

## Align Items

The `align-items` property is similar to justify content, but works along the cross-axis.

If your items are arranged in a row, this would act on the vertical axis.

The five values for `align-items` are:

1. `flex-start`
2. `flex-end`
3. `center`
4. `stretch`
5. `baseline`

---

## Align Items Example

```css
#container {
  display: flex;
  align-items: flex-end;
}
```

![Flexbox Align Items Property](https://cdn-images-1.medium.com/max/1000/1*htfdNmRIIFu_veRaFOj5qA.gif "Aligning items with Flexbox")

---

## Centering Content

Flexbox makes it possible to center content vertically and horizontally by using a combination of `justify-content` and `align-items` together.

```css
#container {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

---

## Flex Direction

The default `flex-direction` is `row`, which will arrange `flex` items in the direction of text.

It is possible to reverse the `flex-direction` with `row-reverse`, or to change to a top-to-bottom direction using a value of `column` or `column` reverse.

```css
#container {
  display: flex;
  flex-direction: row-reverse;
}
```

---

## Override Alignment with Align-Self

Individual flex items can over-ride their alignment using `align-self`. Unlike other Flexbox properties, `align-self` is applied on the child item, and not the flex container.

1. `flex-start`
2. `flex-end`
3. `center`
4. `stretch`
5. `baseline`

---

## Align Self Example

```css
.card {
  display: flex;
  align-items: center;
}

.card .recipe {
  align-self: flex-end;
}
```

![Flexbox Align Self Property](https://cdn-images-1.medium.com/max/1000/1*HIADl1oL6pxXb2dMh_pXSQ.gif "Self aligning with Flexbox")

---

## Nesting Flexbox HTML

**Question**: Can you put a Flexbox inside a Flexbox?

**Answer**: Yes, this is very common.

```html
<div class="two-columns">
  <div class="column">
    <h2>Meats</h2>
    <div>Turkey</div>
    <div>Ham</div>
  </div>
  <div class="column">
    <h2>Cheeses</h2>
    <div>Cheddar</div>
    <div>Swiss</div>
    <div>American</div>
  </div>
</div>
```

---

## Nesting Flexbox CSS

```css
.two-columns {
  display: flex;
  flex-direction: row;
}

.column {
  display: flex;
  flex-direction: column;
}
```

---

## Flexbox Froggy Exercises

Flexbox Froggy is a great way to practice using flexbox to lay out elements on a page.

Click [here](https://flexboxfroggy.com/) and try to complete all 24 levels.
