# URLs

- **U**niform
- **R**esource
- **L**ocator

[What is a URL | MDN](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL)

---

## URL Subparts

<img src="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL/mdn-url-all.png" width="100%" />

---

## Scheme

- `http` - the basics
- `https` - "S" means "Secure"
- `file` - local filesystem

many others...

---

## Domain

`www.example.com`

> The domain indicates which Web server is being requested. Usually this is a domain name, but an IP address may also be used (but this is rare as it is much less convenient).

---

## Port

http://localhost:**8080**

> The technical "gate" used to access the resources on the web server. It is usually omitted if the web server uses the standard ports of the HTTP protocol (80 for HTTP and 443 for HTTPS). Otherwise, it is mandatory.

---

## Path

musical-notes.com<b>/bands/heart</b>

> The path to the resource on the server. A path like this used to represent a physical file location on the server. Nowadays, servers handle it, and it does not really have any physical reality.

---

## Queries

The _query_ is `?category=folk&date=1977` and the _query parameters_ are:

- `&` to separate parameters from each other
- `=` to separate individual parameter names from values

| name     | value  |
| -------- | ------ |
| category | `folk` |
| date     | `1977` |

---

## Queries Continued

Let's examine this Google Search query.

`google.com/search?q=search+term+here&client=safari&source=hp&ei=-q8dYtzgFteqqtsP4My7kA8&iflsig=AHkkrS4AAAAAYh2-CkSzCp-mn5nVyQmW52EWqnjRaD1P&ved=0ahUKEwjcxdjzl6T2AhVXlWoFHWDmDvIQ4dUDCAw&uact=5&oq=search+term+here`

```txt
google.com/search?
  q=search+term+here
  &client=safari
  &source=hp
  &ei=-q8dYtzgFteqqtsP4My7kA8
  &iflsig=AHkkrS4AAAAAYh2-CkSzCp-mn5nVyQmW52EWqnjRaD1P
  &ved=0ahUKEwjcxdjzl6T2AhVXlWoFHWDmDvIQ4dUDCAw
  &uact=5&oq=search+term+here
```


---

## URL Encoding

Any "special" characters in a URL are "escaped" (encoded) as hexadecimal using [percent-encoding](https://en.wikipedia.org/wiki/Percent-encoding)

- space becomes `+` or `%20`
- `-` becomes `%2B`
- `%` becomes `%25`
- Other punctuation marks
- Non-ASCII Unicode characters

e.g. `http://example.com/引き割り.html`

becomes `http://example.com/%E5%BC%95%E3%81%8D%E5%89%B2%E3%82%8A.html`

---

## URL Encoding with Query Parameters

Combining query parameter encoding and percent-encoding can lead to complex URLs.

URL: `http://musical-notes.com/bands/search?category=80%27s+Rock+Bands&page=2`

Query: `?category=80%27s+Rock+Bands&page=2`

Query Parameter: `category=80%27s+Rock+Bands`

- `%27` becomes `'`
- `+` becomes a space

| name     | value             |
| -------- | ----------------- |
| category | `80's Rock Bands` |
| page     | `2`               |

---

## Accessing Query Parameters in JavaScript

`document.location.search` returns the URL's query string.

Remember, `search` is a synonym for `query`.

This does not parse the string into an object for you.
`?x=1&y=2` ==/==> `{x: 1, y: 2}`

Instead, you can use [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) to do that for you.

```js
let params = new URLSearchParams(document.location.search);
let name = params.get("name");
```

---

## Anchors

example.com/users/alex<b>#profile</b>

- Anchors lead to another part of the resource itself. It acts as a sort of "bookmark" inside the resource.
- HTML: the browser will scroll to the point where the anchor is defined.
- Video or Audio: the browser will try to go to the time the anchor represents.
- The part after the #, also known as the fragment identifier, is never sent to the server with the request.
- You can access this data by itself using `document.location.hash`.

---
