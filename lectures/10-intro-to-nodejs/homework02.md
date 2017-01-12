# Homework 2

## Question 1

- Update your `api.js` file to include:

```js
module.exports = {
  getName: function (cb) {
    setTimeout(function () {
      cb(null, 'Fluffykins');
    }, 500);
  },
  getBreed: function (name, cb) {
    setTimeout(function () {
      cb(null, name + ' is a Dalmatian');
    }, 400);
  },
  getCoatColor: function (breed, cb) {
    setTimeout(function () {
      cb(null, breed + ' with spots!');
    }, 550);
  }
};
```

- Create a new file
- In this file:
  - Create a function that chains the API functions `getName`, `getBreed` and `getCoatColor` together to print a single phrase (`Fluffykins is a Dalmatian with spots!`)
- Commit & push this file and any changes to GitHub

## Question 2

- Update `api.js` one more time:

```js
module.exports = {
  getName: function (cb) {
    setTimeout(function () {
      cb(null, 'Fluffykins');
    }, 500);
  },
  getBreed: function (name, cb) {
    setTimeout(function () {
      cb(null, name + ' is a Dalmatian');
    }, 400);
  },
  getCoatColor: function (breed, cb) {
    setTimeout(function () {
      cb(null, breed + ' with spots!');
    }, 550);
  },
  getRandomNumber: function (cb) {
    setTimeout(function () {
      cb(null, Math.random() * 10);
    }, Math.random() * 500)
  }
};
```

- In this file
  - Create a function that waits until 5 calls to `getRandomNumber` have finished and then sum the result into a single number. Log this result to the console.
- Commit & push this file and any changes to GitHub

## Question 3

## Setup

- Download the file `paragraphs.txt` that's in this directory and posted in Slack (this file is pretty large).

## Instructions

- Create multiple asynchronous functions that:
  - Read the contents of the file
  - Count the number of times `the` occurs
  - Count the number of times `I` occurs
  - Count the number of times `like` occurs
  - Count the number of times `years` occurs
- The final output should look like (note that the numbers below are just examples and not necessarily the correct answer):

```js
{
  the: 500,
  i: 300,
  like: 100,
  years: 50
}
```

- Bonus: Perform this exercise using 2 different methods
