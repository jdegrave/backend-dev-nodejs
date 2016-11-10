## Exercise 1

Write function `describeList` which tells if the list is empty or contains only one element or more.

```js
console.log(describeList([]));          // "empty"
console.log(describeList([1]));         // "singleton"
console.log(describeList([1,2]));       // "longer"
console.log(describeList([]));          // "empty"
console.log(describeList([1.5]));       // "singleton"
console.log(describeList([1.5,2.5]));   // "longer"
```


## Exercise 2

Build a function that takes in two arguments (salary, bonus). Salary will be an integer, and bonus a boolean.
If bonus is true, the salary should be multiplied by 10. If bonus is false, the fatcat did not make enough money and must receive only his stated salary.

Return the total figure the individual will receive as a string prefixed with '$'.

```js
console.log(bonusTime(10000, true));    // '$100000'
console.log(bonusTime(25000, true));    // '$250000'
console.log(bonusTime(10000, false));   // '$10000'
console.log(bonusTime(60000, false));   // '$60000'
console.log(bonusTime(2, true));        // '$20'
console.log(bonusTime(78, false));      // '$78'
console.log(bonusTime(67890, true));    // '$678900'
```

## Exercise 3

Given an array of strings representing a list of usernames, return true only if all usernames comply with your company's guidelines. Return false otherwise.

The guidelines say that the username is valid only if:

- it is between 6-10 characters long
- contains at least 1 lowercase letter
- contains at least 1 number
- contains only numbers and lowercase letters

```js
console.log(authList(['john123', 'alex222', 'sandra1']));    // returns true
console.log(authList(['john123', 'alex222', 'sandraW']));    // returns false because sandraW has no number
console.log(authList(['john_123', 'alex222', 'sandra1']));   // returns false because john_123 contains an invalid character
```

## Exercise 4

Write a function that takes two arrays and a function as arguments. The function should merge the two corresponding array values using the function provided as an argument.

```js
function add (a, b) {
  return a + b;
}

console.log(zip([1, 2, 3, 4, 5], ['a','b'], add));    // ['1a', '2b']

function merge (a, b) {
  return a + b.charCodeAt(0);
}

console.log(zip([1, 2, 3, 4, 5], ['a','b','c','d','e'], merge));   // [98, 100, 102, 104, 106]
```
