# Exercise 1

- Create a new folder for tonight's exercises
- In this folder, create a file named `api.js`.
  - In this file, paste:

```js
module.exports = {
  getName: function (cb) {
    setTimeout(function () {
      cb(null, 'Fluffykins');
    }, 500);
  }
};
```

- Create another file.
  - In this file:
    - Use the API module and a promise to get a name and log it to the console
- Bonus: Can you make an error that gets caught in a `catch` block?
- Commit & push this file and any changes to GitHub

# Exercise 2

- Create a new file
- In this file:
  - Create a function that uses a promise and will create a new file
  - Create a function that uses a promise and will append a file
- Bonus: Chain these two functions together to create and then append a file
- Commit & push this file and any changes to GitHub
