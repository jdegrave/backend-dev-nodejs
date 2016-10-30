## Exercise 1

```js
function alternateCase(inputString) {
  console.log('STRING RECEIVED: ', inputString);
  var inputStringArray = inputString.split('');
  console.log('STRING ARRAY: ', inputStringArray);
  var alteredStringArray = [];

  for (var i = 0; i < inputStringArray.length; i++) {
    if (isUppercase(inputStringArray[i])) {
      alteredStringArray.push(inputStringArray[i].toLowerCase());
    } else if (isLowercase(inputStringArray[i])) {
      alteredStringArray.push(inputStringArray[i].toUpperCase());
    } else {
      alteredStringArray.push(inputStringArray[i]);
    }
  }

  console.log('ALTERED STRING ARRAY: ', alteredStringArray);
  var alteredString = alteredStringArray.join('');
  console.log('JOINED STRING: ', alteredString)
  return alteredString;
}

function isUppercase(letter) {
  var charCode = letter.charCodeAt();
  if (charCode >= 65 && charCode <= 90) {
    return true;
  } else {
    return false;
  }
}

function isLowercase(letter) {
  var charCode = letter.charCodeAt();
  if (charCode >= 97 && charCode <= 122) {
    return true;
  } else {
    return false;
  }
}
```

## Exercise 2
```js
function reverseString(inputString) {
  console.log('STRING RECEIVED: ', inputString);
  var stringArray = inputString.split('');
  console.log('STRING ARRAY: ', inputStringArray);
  var reversedStringArray = [];

  for (var i = stringArray.length - 1; i >= 0; i--) {
    reversedStringArray.push(stringArray[i]);
  }

  console.log('REVERSED STRING ARRAY: ', reversedStringArray);
  var reversedString = reversedStringArray.join('');
  console.log('JOINED STRING: ', reversedString)
  return reversedString;
}
```
