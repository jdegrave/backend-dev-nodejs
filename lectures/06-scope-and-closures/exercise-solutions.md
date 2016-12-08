# Exercise 1

```js
function addNumbers (num) {
  var x = num;
  return function (y) {
    return x + y;
  }
}

var addTen = addNumbers(10);
var addTwenty = addNumbers(20);
var addFifty = addNumbers(50);

console.log(addTen(30))       // 40
console.log(addTwenty(30))    // 50
console.log(addFifty(30))     // 80
```
