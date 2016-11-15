## Exercise 1

```js
function compare(s1, s2) {
  var string1=s1.toUpperCase();
  var string2=s2.toUpperCase();

  var array1=string1.split('');
  var array2 = string2.split('');

  var sum1 = 0;
  var sum2 = 0;

  for (var i = 0; i < array1.length; i++) {
    sum1 += array1[i].charCodeAt();
  }

  for (var i = 0; i < array2.length; i++) {
    sum2 += array2[i].charCodeAt();
  }

  return ((sum1 === sum2) ? 'equal' : 'not equal');
}


console.log(compare("AD", "BC")); // equal
console.log(compare("AD", "DD")); // not equal
console.log(compare("gf", "FG")); // equal
```


## Exercise 2

```js
function howManyYears(beginningPopulation, percent, increase, targetPopulation) {
  var numberOfYears = 0;
  var totalPopulation = beginningPopulation;
  var convertedPercent = percent / 100;

  while (totalPopulation < targetPopulation) {
    totalPopulation = totalPopulation + (totalPopulation * convertedPercent) + increase;
    numberOfYears++;
  }

  return numberOfYears;
}

console.log(howManyYears(1500, 5, 100, 5000)); // 15
console.log(howManyYears(1500000, 2.5, 10000, 2000000)); // 10
console.log(howManyYears(1500000, 0.25, 1000, 2000000)); // 94
```


## Exercise 3

This problem has been assigned as homework - contact Brenna with your solution!

```js
console.log(findMissingNumber('1 2 3 5')); // 4
console.log(findMissingNumber('1 3')); // 2
console.log(findMissingNumber('1 5')); // 2
console.log(findMissingNumber('')) // 0
console.log(findMissingNumber('1 2 3 4 5')) // 0
console.log(findMissingNumber('2 3 4 5')) // 1
console.log(findMissingNumber('2 6 4 5 3')) // 1
console.log(findMissingNumber('2 1 4 3 a')) // 1
console.log(findMissingNumber('1 2 4 5')) // 3
```
