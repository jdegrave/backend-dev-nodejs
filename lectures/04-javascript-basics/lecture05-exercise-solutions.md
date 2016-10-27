## Exercise 1

```js
function phoneNumber (nbr) {
  var splitNbr = nbr.split('');
  var goodNbr = [];
  for (var i = 0; i < splitNbr.length; i++) {
    if (parseInt(splitNbr[i], 10) || splitNbr[i] === '0') {
      goodNbr.push(splitNbr[i]);
    }
  }

  if (goodNbr.length > 10 && goodNbr[0] === '1') {
    goodNbr.shift();
    return goodNbr.join('');
  } else if ((goodNbr.length > 10 && goodNbr[0] !== '1') || goodNbr.length < 10) {
    return '0000000000';
  } else {
    return goodNbr.join('');
  }
}

console.log(phoneNumber('(123) 456-7890'));
console.log(phoneNumber('123.456.7890'));
console.log(phoneNumber('11234567890'));
console.log(phoneNumber('21234567890'));
console.log(phoneNumber('123456789'));
```

## Exercise 2

```js
function cipher (str) {
  var upperString = str.toUpperCase();
  var newStr = [];

  for (var i = 0; i < upperString.length; i++) {
    var charCode = upperString.charCodeAt(i);
    var newCharCode = 0;
    if (charCode < 78) {
      newCharCode = 90 - (13 - (charCode - 64));
    }

    if (upperString[i] === ' ') {
      newStr.push(' ');
    } else if (newCharCode > 0) {
      newStr.push(String.fromCharCode(newCharCode));
    } else {
      newStr.push(String.fromCharCode(charCode - 13));
    }
  }
  return newStr.join('');
}

console.log(cipher('SERR CVMMN'));
console.log(cipher('LBH QVQ VG'));
```
