# Passing Parameters

You can pass parameters from the client to the server in a variety of ways.

Some of the most common are:

* on the Path
  * (after a `/`)
* in a GET request's "query" section
  * (after the `?`)
* in a POST request in JSON format
  * (inside the request body)

---


# Path Parameters


This path
`http://github.com/UprightEducation/til/blob/master/README.md`

would match this route when using `express`:
```js
app.get('/:user/:repo/:section/:branch/:filepath',(req,res)=>{
  console.log(req.params)
})
```

---

# Path Parameters Cont.

`http://github.com/UprightEducation/til/blob/master/README.md`
`/:user/:repo/:section/:branch/:filepath`

```js
{
  user: "UprightEducation",
  repo: "til",
  section: "blob",
  branch: "master",
  filepath: "/README.md"
}
```


---



# Accessing the Params Object on the Server

```js

app.get('/',(req,res)=>{
  console.log(req.params)
})

// {
//   user: "UprightEducation",
//   repo: "til",
//   section: "blob",
//   branch: "master",
//   filepath: "README.md"
}
```

---

# Query Parameters

`github.com/file?user=UprightEducation&repo=til&section=blob&branch=master&filename=README.md`

```js
app.get('/',(req,res)=>{
  console.log(req.query)
})
// {
//   user: "UprightEducation",
//   repo: "til",
//   section: "blob",
//   branch: "master",
//   filepath: "README.md"
}
```

---

# Post Parameters

```
// frontend 
let data = { "user":"UprightEucation","repo":"til","section":"blob","branch":"master","filepath":"/README.md" }
await fetch('/file', { method: 'POST', body: JSON.stringify(data) })

// backend
app.use(express.json());
// ...
app.post('/file', (req,res)=>{
  console.log(req.body)
})
```

---

# CORS

 Cross Origin Resource Sharing requires some **middleware**

 ```js
//imports
app.use(cors())
 ```
--

