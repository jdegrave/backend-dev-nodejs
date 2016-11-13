## Exercise 1

```js
function describeList (arr) {
  if (arr.length === 0) {
    return 'empty';
  } else {
    return arr.length > 1 ? 'longer' : 'singleton';
  }
}
```

## Exercise 2

```js
function bonusTime(salary, bonus) {
  if (bonus) {
    return '$' + (salary * 10);
  }
  return '$' + salary;
}
```

## Exercise 3

```js
function authList (arr) {
  var isValid = [];

  for (var i = 0; i < arr.length; i++) {
    var validLength = false;
    var validLowercase = false;
    var validNumber = false;
    var validChars = true;

    if (arr[i].length >= 6 && arr[i].length <= 10) {
      validLength = true;
    }

    for (var j = 0; j < arr[i].length; j++) {
      if (arr[i][j] >= 0 && arr[i][j] <= 9) {
        validNumber = true;
      }

      if (arr[i][j].charCodeAt(0) >= 97 && arr[i][j].charCodeAt(0) <= 122) {
        validLowercase = true;
      }

      if ((arr[i][j].charCodeAt(0) < 97 || arr[i][j].charCodeAt(0) > 122) && !validNumber) {
        validChars = false;
      }
    }

    if (validLength && validLowercase && validNumber && validChars) {
      isValid.push(true);
    }
  }

  return isValid.length === arr.length;
}
```

## Exercise 4

Answer will be provided in class on Saturday. :)
