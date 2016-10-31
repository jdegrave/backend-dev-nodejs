## Exercise 1

Write a function that returns the average of the given array rounded down to its nearest integer.

Hint: [Math.floor()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)

```js
console.log(getAverage([2,2,2,2])); //2
console.log(getAverage([1,2,3,4,5,])); //3
console.log(getAverage([1,1,1,1,1,1,1,2])); //1
```

## Exercise 2

Write a function that accepts an array of integers and returns the smallest integer in the array.

```js
console.log(smallestInteger([34, 15, 88, 2])); // 2
console.log(smallestInteger([34, -345, -1, 100])); // -345
```

## Exercise 3

Write a function that takes an array of ones and zeros and converts the equivalent binary value to a decimal integer.

Hint: [Convert binary to decimal](http://www.wikihow.com/Convert-from-Binary-to-Decimal)

```js
console.log(binaryArrayToNumber([0, 0, 0, 1]), 1); // 1
console.log(binaryArrayToNumber([0, 0, 1, 0]), 2); // 2
console.log(binaryArrayToNumber([1, 1, 1, 1]), 15); // 15
console.log(binaryArrayToNumber([0, 1, 1, 0]), 6); // 6
```

## Exercise 4

Write a function that accepts a string and returns a string every letter replaced with its position in the alphabet. If anything in the text isn't a letter, ignore it and don't put anything in that place.

```js
console.log(alphabetPosition("The sunset sets at twelve o' clock.")); // "20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11"
console.log(alphabetPosition("The narwhal bacons at midnight.")); // "20 8 5 14 1 18 23 8 1 12 2 1 3 15 14 19 1 20 13 9 4 14 9 7 8 20"
```

## Exercise 5

Write a function that accepts a string as an argument and returns the number of vowels in the string

Hint: [Array.includes()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)

```js
console.log(vowelCount('Hello, World!')); //3
console.log(vowelCount('abracadabra')); //5
console.log(vowelCount('Javascript is great!')); //6
console.log(vowelCount('wRjuUJvJxbnyTB3?sCLAp2mbGL3xe8')); //4
console.log(vowelCount('A')); //1
```

## Exercise 6

Write a function that accepts a string and returns a string with all the vowels replaced with exclamation marks.

```js
console.log(replace('Hi!')) //'H!!'
console.log(replace('!Hi! Hi!')) // '!H!! H!!'
console.log(replace('aeiou')) // '!!!!!'
console.log(replace('ABCDE')) //'!BCD!'
```
