## Exercise 1

```js
// Switch Statement Solution
function calculateTip(amount, rating) {
  rating = rating.toLowerCase();

  switch(rating) {
    case "terrible":
      return 0;
      break;
    case "poor":
      return Math.ceil(amount * .05);
      break;
    case "good":
      return Math.ceil(amount * .1);
      break;
    case "great":
      return Math.ceil(amount * .15);
      break;
    case "excellent":
      return Math.ceil(amount * .20);
      break;
    default:
      return "Rating not recognized";
  }
}

// If/Else Solution
function calculateTip(price, rating) {
  rating = rating.toLowerCase();
  var finalProduct = 'Rating not recognized';

  if (rating === 'terrible') {
    finalProduct = 0;
  } else if (rating === 'poor') {
    finalProduct = Math.ceil(price * .05);
  } else if (rating === 'good') {
    finalProduct = Math.ceil(price * .1);
  } else if (rating === 'great') {
    finalProduct = Math.ceil(price * .15);
  } else if (rating === 'excellent') {
    finalProduct = Math.ceil(price * .2);
  }

  return finalProduct;
}

console.log(calculateTip(20, "terrible")); //4
console.log(calculateTip(26.95, "good")); // 3
console.log(calculateTip(26.95, "kind of okay but not great")); // 3


console.log(calculateTip(20, "Excellent")); //4
console.log(calculateTip(26.95, "good")); // 3
```


## Exercise 2

```js
// Manual Solution
function repeatStr(n, s) {
  var repeatedString = s;

  for (var i = 1; i < n; i++) {
    repeatedString += s;
  }

  return repeatedString;
}

// Fancy Pants String Operation Solution
function repeatStr(n, s) {
  return s.repeat(n);
}

console.log(repeatStr(3, "foo")); // "foofoofoo"
console.log(repeatStr(1, "bar spam")); // "bar spam"
console.log(repeatStr(3, "*")); // "***"
console.log(repeatStr(2, "ha ")); // "ha ha "
```


## Exercise 3

```js
// While Loop Solution
function generateRange(min, max, step){
  var generatedArray = [];
  var current = min;

  while (current <= max) {
    generatedArray.push(current);
    current += step;
  }

  return generatedArray;
}

// For Loop Solution
function generateRange(min, max, step){
  var generatedArray = [];

  for (var i = min; i <= max; i += step) {
    generatedArray.push(i);
  }

  return generatedArray;
}

console.log(generateRange(2, 10, 2)); // [2, 4, 6, 8, 10]
console.log(generateRange(1, 10, 3)); // [1, 4, 7, 10]
console.log(generateRange(19, 49, 2)); // [19, 21, 23, 25, 27, 29, 31, 33, 35, 37, 39, 41, 43, 45, 47, 49]
console.log(generateRange(10, 82, 9)); // [10, 19, 28, 37, 46, 55, 64, 73, 82]
```


## Exercise 4

```js
// Manual Solution
var maxRedigit = function(num) {

  if (!Number.isInteger(num) || num < 100 || num > 999) {
    return null;
  }

  var numString = num.toString();
  var numArray = numString.split('').sort();
  var answerArray = [];
  var answerString;
  var maxIndex = findMaxIndex(numArray);
  var minIndex = findMinIndex(numArray);
  var midIndex;

  if (maxIndex === 0 && minIndex === 1) {
    midIndex = 2;
  } else if (maxIndex === 0 && minIndex === 2) {
    midIndex = 1;
  } else if (maxIndex === 1 && minIndex === 0) {
    midIndex = 2;
  } else if (maxIndex === 1 && minIndex === 2) {
    midIndex = 0;
  } else if (maxIndex === 2 && minIndex === 0) {
    midIndex = 1;
  } else if (maxIndex === 2 && minIndex === 1) {
    midIndex = 0;
  } else if (maxIndex === minIndex) {
    midIndex = 1;
    maxIndex = 2;
  }

  answerArray[0] = numArray[maxIndex];
  answerArray[1] = numArray[midIndex];
  answerArray[2] = numArray[minIndex];
  answerString = answerArray.join('');

  return parseInt(answerString, 10);
}

function findMaxIndex(numArray) {
  var maxIndex = 0;

  for (var i = 1; i < numArray.length; i++) {
    if (numArray[i] > numArray[maxIndex]) {
      maxIndex = i;
    }
  }

  return maxIndex;
}

function findMinIndex(numArray) {
  var minIndex = 0;

  for (var i = 1; i < numArray.length; i++) {
    if (numArray[i] < numArray[minIndex]) {
      minIndex = i;
    }
  }

  return minIndex;
}

// Fancy Pants Array Operation Solution
var maxRedigit = function(num) {
  if (num < 100 || num > 999) {
    return null;
  }

  var numString = num.toString();
  var numArray = numString.split('');
  numArray.sort().reverse();
  var answerString = numArray.join('');

  return parseInt(answerString, 10);
}

console.log(maxRedigit(123)); // 321
console.log(maxRedigit(297)); // 972
console.log(maxRedigit(368)); // 863
console.log(maxRedigit(531)); // 531
console.log(maxRedigit(636)); // 663
console.log(maxRedigit(555)); // 555
console.log(maxRedigit(32)); // null
```


## Exercise 5

```js
function removeTargetSum(nums, target) {
  var i = 0;
  var removed = false;

  while (i < nums.length - 1) {
    if (nums[i] + nums[i + 1] === target) {
      nums.splice(i + 1, 1);
      removed = true;
    }

    if (!removed) {
      i++
    }

    removed = false;
  }

  return nums;
}

console.log(removeTargetSum([1, 3, 5, 6, 7, 4, 3], 7)); // [1, 3, 5, 6, 7, 4]
console.log(removeTargetSum([4, 1, 1, 1, 4], 2)); // [4, 1, 4]
console.log(removeTargetSum([2, 2, 2, 2, 2, 2], 4)); // [2]
```
