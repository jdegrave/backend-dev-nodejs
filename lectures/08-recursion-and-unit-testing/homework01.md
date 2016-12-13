1. Trace out the following code sample by hand and determine the final output:
```js
function gcd(a, b) {
  if (b === 0) {
    return a;
  } else {
    return gcd(b, a % b);
  }
}

console.log(gcd(20, 12));
```


2. Given a multidimensional array, return the total number of integers stored anywhere in the array. Do not specifically hardcode for a number of dimensions. You may assume that no other data types will be present in the arrays.
  Examples:
    * [] results in 0
    * [[]] results in 0
    * [1, [1]] results in 2
    * [1, [], 2, [], 3, []] results in 3
    * [0, [1, [5, [4, 3], 1], 1]] results in 7
    * [[[5], 3], 0, 2, [], [4, [5, 6]]] results in 7
