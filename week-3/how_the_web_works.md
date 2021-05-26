# HTTP

Let's lift the hood and check out the engine that makes the World Wide Web run.

---

# Browsers - what do they do?

* A web browser is a computer application that reads files. 
* When entering a **URL** (ex. https://www.facebook.com) into the address bar in a browser, the browser requests information in the form of a file associated with that specific URL.
* Your browser renders code in the form of a website.

---

# Request - Response

* HTTP stands for **Hypertext Transfer Protocol**. 
* In a nutshell, an HTTP request is sent by the **client** (a browser), which is used to locate information in the form of a file. 
* This file contains code, which tells your browser how, and what, to render. 
* A web server responds to this request, by telling the browser where the file lives. 

![HTTP Request](/images/http_request.png "HTTP Request") (via <https://betterexplained.com/>)

---

# HTTP Methods

HTTP is a protocol that allows clients to communicate with web servers, and is a primary underlying infrastructure of the Internet. The two most common HTTP methods are:

* `GET`
* `POST`

We'll be covering HTTP methods in more detail when we dive into servers.

---

# DNS

* DNS stands for Domain Name Service
* This is a standardized way for a browser to know **where** your website lives. 
* Your browser communicates with a **nameserver**, which tells your browser the IP address of where the files for your website are located. 
* Information on your nameservers are known as **DNS Records**. 

Remember, websites live at an **IP Address**. This is a string of numbers, (ex. 70.42.251.42) that locates a specific computer (or "host") on the Internet. A domain name is simply a translation that provides humans with an easy way to remember where a website lives.

---

# HTTP: File Transfer for the Web

* HTTP: HyperText Transfer Protocol
    * Invented in ~1991 by Tim Berners-Lee as part of the World Wide Web
    * Uses TCP/IP: Internet Protocol
    * see [A Brief History of HTTP](https://hpbn.co/brief-history-of-http/)

* Essentially, HTTP is a *file transfer* protocol
  * every HTTP response contains a *body* which is often the raw, complete contents of a file
  * these files can be images, sounds, data, or code

---

# Examples of Web Code

Web code can be any language used to create web pages or applications. Common examples of these are

* HTML
* CSS
* JavaScript

The above languages run *inside* the web browser (aka "the client side").

---

# HTTP 0.9 Goals (1991)

* **very** simple protocol, geared towards ease of use and implementation
* **100%** ASCII characters in and out
* Human readability was a goal
* **stateless** meaning "one request, one response, and close"

---

# HTTP 1.0 (1993-1996)

* developed *ad hoc* as the early WWW exploded
  * many early decisions were odd, but we are now stuck with them
* same basic idea as HTTP 0.9, but with
  * a version identifier
  * request headers
  * response status line
  * response headers
* still *stateless* but some headers (notably `Cookie:`) pass state back and forth

---

# HTTP 1.0 protocol

| Step               | Client                              | Server                                                 |
|--------------------|-------------------------------------|--------------------------------------------------------|
| open connection    | `telnet example.com 80`             |                                                        |
| request a resource | `GET /index.html HTTP/1.0`  &#9166; |                                                        |
| request headers    | `User-Agent: Dogscape 1.0` &#9166;  |                                                        |
| blank line         | &#9166;                             |                                                        |
| response status    |                                     | `HTTP/1.0 200 OK`                                      |
| response headers   |                                     | `Content-Type: text/html` <br> `Content-Length: 12340` |
| blank line         |                                     | &#9166;                                                |
| response body      |                                     | `<html><body>...`                                      |

---

# HTTP 1.0 details

* *port* is a TCP/IP concept that lets a single *host* run several *services*
  * the default port for HTTP is 80
  * the default port for [HTTPS](https://en.wikipedia.org/wiki/HTTPS) is 443
* Request and (part of) Response are still ASCII
* `Content-Type` header allows different file types
  * reused **MIME**: (Multipurpose Internet Mail Extensions) spec for file type names
* `Content-Length` header so the client knows how big a file to expect
* ...and many more headers to help clients and servers work together

---

# Curl Screenshot

![curl screenshot](/images/http-curl-example.png)