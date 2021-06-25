# API Endpoints

API stands for "Application Program Interface"

APIs are used to send data into a front end application

They are an interface between your raw data, and the front end display

# JSON and APIs

Many APIs send data over as JSON, or have the option to send data as JSON based on query parameters.

An API Endpoint in its simplest incarnation could be a directory in your filesystem where you store JSON files

When you receive a request from your client side application your server will then query that directory for a document matching the request, and if it finds one it sends the data back over

# Querying APIs

To query an API you can send a `GET` request to a certain path (which you've defined on your server), or to the location of the endpoint in your filesystem.

You can also send requests through forms, or other inputs to bring back specific subsets of data. Often times there will be some parsing, and conversion necessary on the front end to display the data where, and how you want.

# Postman

Postman is a great tool for seeing exactly what data you will get back from a given request

If you don't already have Postman installed you can get it [here](https://www.postman.com/downloads/). Go ahead and download it now.

* Open up the Postman app, and create a new collection named 'test'
* In this collection create a new `GET` request, and name it 'basic get'
* Select `GET` as the type of request and give it the url `https://jsonplaceholder.typicode.com/posts/1`
* Hit the "Send" button, and see what you get back

There are also many prebuilt collections for commonly used API routes (such as the [GitHub API](https://developer.github.com/v3/)) which you can generally find on the site that hosts the route, or through a quick Google search.
