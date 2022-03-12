# Overview

Welcome to the backend!

The **backend** refers to code that does not run on the user's computer but instead on the **server**. 

We will be learning about servers and databases, the two main parts of a backend. 

---

## What is a server?

- Computer program and/or device 
- Provides a service to another computer program and its user
  - The one receiving the service is the client

---

## Server Hardware

- Ordinary computer
  - *Usually* in a different location
  - Can be the same computer as the client technically
- Stores programs that can do a variety of things
- Store files and data needed to serve websites
  - JavaScript files
  - HTML
  - CSS stylesheets
  - Images

---

## Server Software

- Understands URLs 
- Listens for HTTP requests
- Sends responses to those requests
- Often used to conduct behaviors that are not safe to perform on the client-side. 

---

## Requests

- Different requests are sent 
  - _from the client_ 
  - _to the server_
  - along different **routes**
    - "Route" on the backend refers to a URL, just like on the frontend.
  - carrying information from the client if needed
- Requests follow HTTP:
  - POST - **C**reate  
  - GET - **R**ead 
  - PUT - **U**pdate 
  - DELETE - **D**elete

---

# Responses

Servers **respond** to clients

- while following specific rules, determined by the engineer.
- to send information back to the *client*
- after carrying out actions warranted by the request 
  - e.g. updating a database
- with a status code
  - 200 is `OK`
  - 404 is `Not Found`
  - [and more...](https://http.cat/)

---


# Node vs JavaScript Review

* Global Objects
  * `global` v. `browser` or `window`
* Import/export methods
  * `require` v. `import`
* Different access to APIs
  * e.g. fetch - browser only
  * e.g. fs - node only

---

