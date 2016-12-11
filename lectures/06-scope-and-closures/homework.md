# Homework

For each of the below exercises, try to figure out what would be alerted by the function. Attempt to reason about the code _before_ executing it to get the answer.

## Question 1

```js
var a = 12;
(function() {
  alert(a);
})();
```

## Question 2

```js
var a = 5;
(function() {
  var a = 12;
  alert(a);
})();
```

## Question 3

```js
var a = 10;
var x = (function() {
  var a = 12;
  return (function() {
    alert(a);
  });
})();
x();
```

## Question 4

```js
var a = 10;
var x = (function() {
  var y = function() {
    var a = 12;
  };
  return function() {
    alert(a);
  }
})();
x();
```

## Question 5

```js
var a = 10;
var x = (function() {
  (function() {
    a = 12; // <<< look carefully at this line.
  })();
  return (function() {
    alert(a);
  });
})();
x();
```

## Question 6

```js
var a = 10;
(function() {
  var a = 15;
  window.x = function() {
    alert(a);
  }
})();
x();
```

## Question 7

Create a module that has two methods: `print`, and `multiply`. `printModuleName` should log the module's `name` to the console, and `multiply` should multiply two numbers together. The internal implementation details of the module should be hidden (i.e. the user should not be able to see the moduleId).

Module details:

```js
obj: {
  name: 'Very Awesome Module',
  id: '12erer0ue70'
}
```

```js
console.log(myModule.printModuleName());      // Very Awesome Module
console.log(myModule.multiply(3, 2));         // 6
```
