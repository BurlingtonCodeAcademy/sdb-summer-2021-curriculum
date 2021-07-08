# Lab: Creating a JSON file

JSON files are easy to create since they are just JS objects that only contain strings.

 - Curly braces hold these objects, unless they are arrays
 - Arrays are held within square brackets

  The data inside each JSON object must be written in key: value pairs. **Keep in mind** that the keys need to be double quoted, as they are strings.

  - Template strings do not work!
  - Each key: value pair must be separated by commas.
  - Your JSON also _cannot_ include comments.
  - Methods also will not work.

Let's go ahead and create a JSON file now.

- In your Terminal, create a new directory named `json-server` with `mkdir json-server`
- Enter the directory with `cd json-server`
- Inside this directory, create a subdirectory called `api` using `mkdir api`
- Enter the directory using `cd api`

* inside `api` create a file named `example.json`
* In `example.json` create a JSON object containing:
  - a name
  - a quest
  - a favorite color
