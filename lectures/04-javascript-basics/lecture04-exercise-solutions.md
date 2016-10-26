## Exercise 1

```js
function isNumber (arg) {
  if (typeof arg === 'number') {
    return true;
  }
  return false;
}
```

## Exercise 2

```js
console.log(multiply(5,10));

function multiply(x, y) {
  return x * y;
}
```

## Exercise 3

```js
function findLongestWord (str) {
  var words = str.split(' ');
  var wordLengths = [];

  for (var i = 0; i < words.length; i++) {
    wordLengths.push(words[i].length);
  }
  var longestLength = Math.max.apply(null, wordLengths);
  return words[wordLengths.indexOf(longestLength)];
}

var sentence = 'Hello sunshine';
console.log(findLongestWord(sentence));
```

## Exercise 4

```js
function aNumber () {
  return 76;
}

function multFunc (fn) {
  return fn() * 10;
}

console.log(multFunc(aNumber));
```
