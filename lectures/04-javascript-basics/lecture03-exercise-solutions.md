# Lecture 3 - JavaScript Basics - Exercises

## Exercise 1

```js
var myArray = [];

for (var i = 0; i < myArray.length; i++) {
  myArray.push(i);
  console.log(myArray);
}

console.log('I can count to 10: ', myArray);
```

## Exercise 2

```js
var fruitColors = {
  apple: 'red',
  orange: 'orange',
  banana: 'yellow',
  kiwi: 'green',
  strawberry: 'red'
};

for (var fruit in fruitColors) {
  console.log(fruitColors[fruit]);
}
```

## Exercise 3

```js
var numbers = [34, 55, 63, 22, 94, 48, 91, 100, 34, 78];
var doubled = [];

for (var i = 0; i < numbers.length; i++) {
  doubled.push(numbers[i] * 2);
}

console.log(doubled);
```

## Exercise 4

```js
var autoMakes = ['Ford', 'Chevy', 'BMW', 'Audi', 'VW'];
var carList = [];

var i = 0;
do {
  var carInfo = {
    make: autoMakes[i]
  };

  switch (autoMakes[i]) {
    case 'Ford':
      carInfo.model = 'Mustang';
    case 'Chevy':
      carInfo.model = 'Silverado';
    case 'BMW':
      carInfo.model = '3';
    case 'Audi':
      carInfo.model = 'TT';
    case 'VW':
      carInfo.model = 'Beetle';
    default:
      break;
  }

  carList.push(carInfo);
  i++;
} (while i < autoMakes.length);

console.log(carList);
```

## Exercise 5

```js
var months = ['jan', 'feb', 'mar', 'apr', 'may'];
var i = 0;

while (i < months.length) {
  console.log(months[i]);
  i++;
}
```

## Exercise 6

```js
function reverseString(str) {
  return str.split('').reverse().join('');
}

console.log(reverseString('blake'));
```
