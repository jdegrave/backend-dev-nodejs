# Reading

## this

- [You Don't Know JS - this & Object Prototypes - Ch 1 - this Or That?](https://github.com/getify/You-Dont-Know-JS/blob/master/this%20&%20object%20prototypes/README.md#you-dont-know-js-this--object-prototypes)
- [You Don't Know JS - this & Object Prototypes - Ch 2 - this All Makes Sense Now!](https://github.com/getify/You-Dont-Know-JS/blob/master/this%20&%20object%20prototypes/README.md#you-dont-know-js-this--object-prototypes)
- [this (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)
- [Understand JavaScript's "this" with Clarity](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)

## Regular Expressions

- [RegExp (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp)
- [Regular Expressions (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)
- [Regular Expressions (Eloquent JS)](http://eloquentjavascript.net/09_regexp.html)
- Go through all the exercises on the [RegexOne](https://regexone.com/) website.

# Exercises

## Exercise 1

Did you know that librarians speak a secret language of just 'o's and 'k's? Write a function to decode the messages below.

Tip:  "Hello World!" looks like - `Ok, Ook, Ooo? Okk, Ook, Ok? Okk, Okk, Oo? Okk, Okk, Oo? Okk, Okkkk? Ok, Ooooo? Ok, Ok, Okkk? Okk, Okkkk? Okkk, Ook, O? Okk, Okk, Oo? Okk, Ook, Oo? Ook, Ooook!`

Your task is to implement a function `okkOokOo`, that would take the message as input and return a decoded human-readable string.

```js
console.log(okkOokOo('Ok, Ook, Ooo!'));  // 'H!'
console.log(okkOokOo('Ok, Ook, Ooo? Okk, Ook, Ok? Okk, Okk, Oo? Okk, Okk, Oo? Okk, Okkkk? Ok, Ooooo? Ok, Ok, Okkk? Okk, Okkkk? Okkk, Ook, O? Okk, Okk, Oo? Okk, Ook, Oo? Ook, Ooook!'));  // 'Hello World!'
console.log(okkOokOo('Ok, Ok, Okkk? Okk, Ook, Ok? Okk, Okk, Oo? Okk, Okk, Oo!'));  // 'Well!'
```

## Exercise 2

The principal of a school likes to put challenges to the students related with finding words of certain features. One day she said: "Dear students, the challenge for today is to find a word that has only one vowel and seven consonants but cannot have the letters 'y' and 'm'. I'll give a special award for the first student that finds it." One of the students used his dictionary and spent all the night without sleeping, trying in vain to find the word. The next day, the word had not been found yet. This student observed that the principal has a pattern in the features for the wanted words:

- The word should have `n` vowels, may be repeated, for example: in "engineering", n = 5.
- The word should have `m` consonants, may also be repeated: in "engineering", m = 6.
- The word should not have some forbidden letters.
- Create a function that receives the three arguments in the order given above, `wantedWords(list, vowels, consonants, forbidLetters)` and output an array with the word (or words) having the words in the order given in the pre-loaded list. If no words are found, return an empty array.

```js
var wordList = ['strength', 'afterwards', 'background', 'photograph', 'successful', 'understand'];

console.log(wantedWords(wordList, 1, 7, ['m', 'y']));     // ['strength']
console.log(wantedWords(wordList, 3, 7, ['m', 'y']));     // ['afterwards', 'background', 'photograph', 'successful', 'understand']
console.log(wantedWords(wordList, 3, 7, ['a', 's' , 'm', 'y']));    // []
```

## Exercise 3

Drop the elements of an array (first argument), starting from the front, until the predicate (second argument) returns true.

The second argument, `func`, is a function you'll use to test the first elements of the array to decide if you should drop it or not.

Return the rest of the array, otherwise return an empty array.

```js
console.log(dropElements([1, 2, 3, 4], function (n) { return n >= 3; }));       // [3, 4]
console.log(dropElements([0, 1, 0, 1], function (n) { return n === 1; }));      // [1, 0, 1]
console.log(dropElements([1, 2, 3], function (n) { return n > 0; }));           // [1, 2, 3]
console.log(dropElements([1, 2, 3, 4], function (n) { return n > 5; }));        // []
console.log(dropElements([1, 2, 3, 7, 4], function (n) { return n > 3; }));     // [7, 4]
console.log(dropElements([1, 2, 3, 9, 2], function (n) { return n > 2; }));     // [3, 9, 2]
```
