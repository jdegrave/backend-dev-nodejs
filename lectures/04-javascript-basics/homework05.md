# Exercise 1

Calculate the circumference of a circle, given the radius as a function argument. The calculation for circumference is `2πr`.

## Test Cases

```js
console.log(circumference(1));
console.log(circumference(π));
console.log(circumference(0));
console.log(circumference(-1));
console.log(circumference(2720));
```

# Exercise 2

Write a function that takes two arguments: first an array of letters; second a number. The function should split the array into a two-dimensional array with elements the size of the second arguments.

## Test Cases

```js
console.log(splitArray(['a', 'b', 'c', 'd'], 2));   // [['a', 'b'], ['c', 'd']]
console.log(splitArray(['a', 'b', 'c', 'd', 'e'], 3));    // [['a', 'b', 'c'], 'd', 'e']
console.log(splitArray(['a', 'b', 'c', 'd', 'e'], 4));
```

# Exercise 3

Write a function that generates a random percentage between 75 & 99.99.

## Test Cases

```js
console.log(randPercent());
```

# Exercise 4

Truncate a string (first argument) if it is longer than the given maximum string length (second argument). Return the truncated string with a ... ending.

Note that inserting the three dots to the end will add to the string length.

However, if the given maximum string length num is less than or equal to 3, then the addition of the three dots does not add to the string length in determining the truncated string.

## Test Cases

```js
console.log(truncateString('A-tisket a-tasket A green and yellow basket', 11));
console.log(truncateString('Peter Piper picked a peck of pickled peppers', 14));
console.log(truncateString('A-tisket a-tasket A green and yellow basket', 'A-tisket a-tasket A green and yellow basket'.length));
```

# Exercise 5

Write a function that given the number (n), will populate an array with all numbers up to and including that number, but excluding zero.

For example, if n = 10:

return [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

## Test Cases

```js
console.log(counting(1));
console.log(counting(0));
console.log(counting(-4));
console.log(counting(10));
console.log(counting(6));
```
