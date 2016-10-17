# Lecture 1 - JavaScript Basics - Exercises

## Exercise 1

Write an algorithm to complete a task in the real world (i.e. baking a cake).

## Exercise 2

Log your name to the Node console.

# Exercise 3

Copy the code snippet below into a file, run it via Node and answer the following questions:

- What type of error is thrown?
- What's the error message?
- On what line does the error occur?
- In what function does the error occur?
- On what line is that function executed?

```js
(function () {
  const o = {
    animal: 'dog',
    integer: 7,
    fruits: [
      'apple',
      'orange',
      'banana'
    ]
  };

  function convertJSON (object) {
    JSON.parse(object);
  }

  convertJSON(o);
})();
```

# Exercise 4

Create the following and log them to the console:

- An object with 3 properties
- A string
- The result of averaging 5 numbers
- A string that translates to `false`
- An array containing 5 different types of data
