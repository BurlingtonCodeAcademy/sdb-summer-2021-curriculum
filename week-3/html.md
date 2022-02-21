# Intro to HTML

* HTML stands for Hyper-Text Markup Language
* Every HTML file is one web page
* Invented by Sir Tim Berners-Lee
* Based on SGML
* Standard language used for creating web pages
* Composed of tags
* CSS and JavaScript are designed to work in tandem with HTML
* HTML is for structuring content

---

## What Is It?

HTML is a coding language composed of various types of _tags_, also known as _elements_. These are what are used to build web pages.

* HTML is used to **build** web pages by using **tags**.
* Web browsers "read" HTML and render it as pretty visual elements for humans.

---

## Standard Page Structure

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My House</title>
  </head>
  <body>
    <p>My house is a very very very fine
     house, with two cats in the yard.</p>
    <p>Life used to be <strong>so
     hard</strong>; now everything is
     easy 'cause of you.</p>
  </body>
</html>
```

---

## Elements

All HTML tags are surrounded by angle brackets, this is what defines the tag. Every tag also has what is known as a **closing tag**. These are the tags that have a preceding forward slash. For the most part, every HTML tag needs to have a closing tag. Between the opening and closing tags we put the content that appears on the page.

HTML tags can be broken into 2 categories: structural tags, and style tags. Structural tags determine layout and behavior on the page, while style tags change the way things (usually text) appear on the page.

---

## Examples of Structural Elements for Layout

| tag      | meaning                   |
|----------|---------------------------|
| `<head>`  | head (contains metadata)  |
| `<body>`  | page body                 |
| `<div>`   | division                  |
| `<h1>`    | Heading (level 1)         |
| `<p>`     | Paragraph containing text |
| `<span>`  | Text without a line break |
| `<img>`   | Image tag                 |

---

## Examples of Style Elements

| tag                  | example                         |
|----------------------|---------------------------------|
| `<strong>`           | `<strong>strong</strong>`       |
| `<em>`               | `<em>emphasis</em>`             |
| `<br>`               | Line break                      |
| `<hr>`               | Horizontal rule (dividing line) |
| `<blockquote>`       | "call-out" quotation            |
| `<pre>`              | pre-formatted text, code        |

---

## Self-Closing Elements

Some tags can act as both an opening and a closing tag.

These are written with a closing forward slash at the end.

They are most commonly seen for tags that insert something into the page such as an image, horizontal line, or an input.

```html
<img src="myImg.jpg" />
<hr />
<input />
```

---

## Element Attributes

Attributes further define HTML elements and their purpose. For example, an image tag may have the following attributes:

```html
<img src="/images/cat-pic.jpg" title="Cat Picture" alt="Picture of a fuzzy cat">
```

* `src` defines where the image file is located.
* `alt` is alternative text to be displayed if the image cannot be.
* Attributes are not always required. However in the example above, a source is needed for the image to be displayed.
* Others include `style` (for inline CSS), `title` (for hover-over tooltips), `href` (hyperlink reference)
* Attribute names should always be lowercase

---

## Style vs Layout vs Semantics

This war has raged inside HTML since the beginning of the web.

Some tags exclusively describe _how_ it's contents should be displayed (ex. `<b>`), where as some _describe_ it's contents (ex. `<strong>`). Web content isn't just about appearance. It matters how it is interpreted.

* Semantics are all about meaning - what is the purpose?
* Not all HTML elements convey meaning - not all HTML elements are semantic (e.g. `div`).
* Imagine a blind person using a screen reader - how might they understand the difference between a `<strong>` and a `<b>` tag?
* Not all elements **style** content, and not all elements define **structure** or layout.

---

## HTML Has Flaws

HTML Challenges

* Difficult to read, for both for humans and programs.
* Poor whitespace rules.
* Case insensitive, except when it's not.
  * For example, Ç is &amp;Ccedil; and ç is &amp;ccedil;.
* Open and close tag names should match but often aren't required to.
  * For example, &lt;b>bold &lt;i>italic&lt;/b>&lt;/i>.
* Browsers will happily render invalid HTML, which leads to the propagation of invalid HTML.
* Muddled distinctions.
  * _semantics_ what the element's content _means_ and _style_ how the elements content is _displayed_.

---

## Proper HTML5 Web Page Structure

In modern day HTML there are a number of elements that help to semantically structure and lay out the content on your website.

![Image of HTML5 page structure](https://i.pinimg.com/originals/46/e2/1c/46e21c46e7001fca6554cd45562268fa.jpg "HTML Page Structure")

---

## What To Know About Elements

* Not all elements _must_ be used.
* Each element is meant to contain a specific type of content.
* Elements help screen readers and search engines to determine the structure of your website.
* You could replace all semantic HTML5 elements with `<div>` tags and your browser will render it the same way.
* Using elements **will not automatically layout your page** as shown in the previous image.
  * They simply help to _describe_ what the content is on your website.
