# Exercise 1

```js
function findOldest (arr) {
  var age = 0;
  var sameAge = [];

  for (var i = 0; i < arr.length; i++) {
    if (arr[i].age > age) {
      age = arr[i].age;
    } else if (arr[i].age === age) {
      sameAge = filter(arr, function (element) {
        return element.age === arr[i].age;
      });
      break;
    }
  }

  return sameAge.length > 0 ? sameAge : age;
}

function filter (arr, func) {
  var output = [];

  for (var i = 0; i < arr.length; i++) {
    if (func(arr[i])) {
      output.push(arr[i]);
    }
  }

  return output;
}
```
