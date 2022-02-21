# How the Web Works

Let's lift up the hood and check out the engine that makes the World Wide Web run.

---

## Browsers - What do they do?

* A web browser is a computer application that reads files.
* When entering a **URL** <https://example.com> into the address bar in a browser, the browser requests information in the form of a file associated with that specific URL.
* Your browser renders code in the form of a website.

---

## Requests and Responses

* HTTP stands for **Hypertext Transfer Protocol**.
* In a nutshell, an HTTP request is sent by the **client** (a browser), which is used to locate information in the form of a file.
* This file contains code, which tells your browser how, and what, to render.
* A web server responds to this request, by telling the browser where the file lives.

![HTTP Request](https://603168-1953132-raikfcquaxqncofqfm.stackpathdns.com/wp-content/images/http_process_explained.jpg "HTTP Request") (via <https://study-ccna.com/>)

---

## HTTP Methods

HTTP is a protocol that allows clients to communicate with web servers, and is a primary underlying infrastructure of the Internet.

Some common HTTP methods are:

* `GET`
* `POST`
* `PATCH`
* `PUT`
* `DELETE`

We'll be covering HTTP methods in more detail when we dive into servers.

---

## DNS

DNS stands for Domain Name Service

This is a standardized way for a browser to know **where** your website lives.

Your browser communicates with a **name server**, which tells your browser the IP address of where the files for your website are located.

Information on your nameservers are known as **DNS Records**.

Remember, websites live at an **IP Address**. This is a string of numbers, (ex. 70.42.251.42) that locates a specific computer (or "host") on the Internet. A domain name is simply a translation that provides humans with an easy way to remember where a website lives.

---

## HTTP: File Transfer for the Web

HTTP: HyperText Transfer Protocol

* Invented in 1990 by Tim Berners-Lee as part of the World Wide Web project at CERN
* Uses TCP/IP: Internet Protocol
* See [A Brief History of HTTP](https://hpbn.co/brief-history-of-http/)

Essentially, HTTP is a *data transfer* protocol

* HTTP responses contain *data* which are often the raw, complete contents of a file
* The data can be images, sounds, documents, code, video, etc.

---

## Examples of Code for the Web

Web browsers natively understand three languages:

* HTML
* CSS
* JavaScript

The above languages run *inside* the web browser, also known as "on the client side"

---

## HTTP 0.9 Goals (1991)

**Very** simple protocol, geared towards ease of use and implementation

**100%** ASCII characters in and out

Human readability was a goal

**Stateless** meaning "one request, one response, and then close"

---

## HTTP 1.0 (1993-1996)

Developed **ad hoc** as the early web exploded

* Many early decisions were odd, but we are now stuck with them

The same basic ideas as HTTP 0.9, but now with

* A version identifier
* Request headers
* Response status line
* Response headers
* Still **stateless** but also included header and `Cookie` to pass state back and forth

---

## HTTP 1.0 protocol

| Step               | Client                              | Server                                                 |
|--------------------|-------------------------------------|--------------------------------------------------------|
| Open connection    | `telnet example.com 80`             |                                                        |
| Request a resource | `GET /index.html HTTP/1.0`  &#9166; |                                                        |
| Request headers    | `User-Agent: Netscape 1.0` &#9166;  |                                                        |
| Blank line         | &#9166;                             |                                                        |
| Response status    |                                     | `HTTP/1.0 200 OK`                                      |
| Response headers   |                                     | `Content-Type: text/html`                              |
|                    |                                     | `Content-Length: 12340`                                |
| Blank line         |                                     | &#9166;                                                |
| Response body      |                                     | `<html><body>...`                                      |

---

## HTTP 1.0 details

*PORT* is a TCP/IP concept that lets a single *host* run several *services*

* The default port for HTTP is 80
* The default port for [HTTPS](https://en.wikipedia.org/wiki/HTTPS) is 443

Request and Response still use ASCII characters

* `Content-Type` header allows different file types
  * Reused **MIME**: (Multipurpose Internet Mail Extensions) spec for file type names
* `Content-Length` header so the client knows how big a file to expect
* Many more headers to help clients and servers work together
