# Titleize

## Objective

In this lab we will be creating a function that accepts a multi-word String as a parameter, capitalizes the first letter of each word, and makes the rest of the word lowercase. To do this we will be utilizing Arrays and Array methods.

### Learning

We will practice using String methods, Array methods, and Array iteration methods to write a function. We will also reference our old code from our `capitalize` lab.  

Topics

- String method `.split()`
- Array method `.join()`
- Iteration method `.map()`
- Arrays
- Strings

### Achieving

In this lab, we will achieve a piece of software that takes a multi-word string and capitalizes the first letter of each word, while making sure the rest of the word is lowercase. Your work will result in:

- `titleize.js`
- `titleize` function that takes a string as it's argument.
- Within `titleize`, a variable containing the result of calling `.split()` on the passed in string.
- Within `titleize` a `.map()` method on our array with our `capitalize` function as the callback function.
- Within `titleize` a `.join()` method which joins our array we created with our `.map()` method.
- A `console.log` to print our results to the console.

## Procedure

### Create the `titleize.js` file

- [ ] Create a file named `titleize.js` and open it in your editor.

### Bring in the `capitalize` function

- [ ] Reference your `capitalize` function from last week's [Capitalize Lab](https://online.uprighted.com/lessons/lab/capitalize)
- [ ] Put this function at the top of your file.

- If you don't have a working version of this function you can use the following. Please make sure to fully understand this before you use it. Ask your fellow classmates or your instructors if you need any clarification.

``` js
function capitalize(string) {
  //Isolate first letter of word
  let firstLetter = string[0];
  //capitalize the first letter
  firstLetter = firstLetter.toUpperCase();
  //get the rest of the word
  let restOfWord = string.slice(1).toLowerCase();

  //rejoin the parts of the word
  let fullWord = firstLetter + restOfWord;
  return fullWord;
}
```

### Create the `titleize` function

- [ ] Declare a function named `titleize` that will take a string as its argument.
- [ ] Within the `titleize` code block, assign the returned value from calling `.split()` on our string to a variable. You should split the string on spaces.
- [ ] Within the `titleize` code block, call the `.map()` method on our new array we created from `.split()` and use the `capitalize` function as our callback function. Assign the result to a variable.
- [ ] Within the `titleize` code block, call the `.join()` method on our new array we created from `.map()`. You should join the array on spaces.

### Call the `titleize` function

- [ ] Call the function several times passing in different multi-word strings with different styles of capitalization. Print the results of those functions, and run the program.

## Review

In this lab, we practiced using string methods, array methods, and iteration methods to write a function. We also looked back at our old code and made use of it here. The software you made should:

- Take a multi-word string and capitalize the first letter of each word, while making sure the rest of the word is lowercase.
- Print the result to the console.

### Going Further

- Try to chain methods to make your code more concise but still readable.
- What if you only wanted to capitalize the first word?
- How could you write this function to allow a user to enter their own phrase they want to "titleize"?
