# Lecture 1 - JavaScript Basics - Exercise Questions

## Exercise 1

Feed the puppies:

- Open pantry door
- Turn on light
- Open dog food container
- Scoop 2 3/4 cups of dry dog food into bowl
- Walk to office
- Pour dog food into food bowl
- Walk back to pantry
- Put bowl back in dog food container
- Close dog food container
- Turn off light
- Close pantry door

## Exercise 2

```js
console.log('Blake');
```

## Exercise 3

```
undefined:1
[object Object]
 ^

SyntaxError: Unexpected token o in JSON at position 1
    at Object.parse (native)
    at convertJSON (/Users/bjohnston/dev/node-projects/script.js:13:10)
    at /Users/bjohnston/dev/node-projects/script.js:16:3
    at Object.<anonymous> (/Users/bjohnston/dev/node-projects/script.js:17:3)
    at Module._compile (module.js:556:32)
    at Object.Module._extensions..js (module.js:565:10)
    at Module.load (module.js:473:32)
    at tryModuleLoad (module.js:432:12)
    at Function.Module._load (module.js:424:3)
    at Module.runMain (module.js:590:10)
```

- `SyntaxError`
- `Unexpected token o in JSON at position 1`
- Line 13
- `convertJSON`
- Line 16

## Exercise 4

```js
var obj = {
  car: 'porsche',
  dog: 'sprinkles',
  mow: false
};

var str = 'Blake';

var avg = ((2 + 4 + 5 + 9 + 20) / 5);

var fstr = Boolean('');

var arr = [
  undefined,
  null,
  obj,
  str,
  100
];

console.log(obj);     // { car: 'porsche', dog: 'sprinkles', mow: false }
console.log(str);     // Blake
console.log(avg);     // 8
console.log(fstr);    // false
console.log(arr);     // [undefined, null, { car: 'porsche', dog: 'sprinkles', mow: false }, 'Blake', 100]
```
