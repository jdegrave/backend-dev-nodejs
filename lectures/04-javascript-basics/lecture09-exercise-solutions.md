# Exercise 1

```js
function translate(str) {
  function isVowel(c) {
    return ['a', 'e', 'i', 'o', 'u'].indexOf(c.toLowerCase()) !== -1;
  }

  if (isVowel(str.charAt(0))) {
    return str + 'way';
  } else {
    for (var i = 1; i < str.length; i++) {
      if (isVowel(str[i])) {
        var letters = str.slice(0, str.indexOf(str[i]));
        var remainder = str.slice(str.indexOf(str[i]));
        return remainder + letters + 'ay';
      }
    }
  }
}
```

# Exercise 2

```js
function printerError (str) {
  var errors = 0;

  for (var i = 0; i < str.length; i++) {
    if (str[i].charCodeAt(0) > 109) {
      errors += 1;
    }
  }

  return errors + '/' + str.length;
}
```

# Exercise 3

```js
function dayPlan (hours, tasks, duration) {
  var remainingTime = (hours * 60) - (tasks * duration);
  var breakTime = Math.round(remainingTime / (tasks - 1));
  var arrayLength = tasks + (tasks - 1);
  var schedule = [];

  if (remainingTime < 0) {
    return 'You\'re not sleeping tonight!';
  }

  for (var i = 1; i <= arrayLength; i++) {
    if (i % 2 === 1) {
      schedule.push(duration);
    } else {
      schedule.push(breakTime);
    }
  }
  return schedule;
}
```

# Exercise 4

```js
function numberOfGloves (gloves) {
  var gloveList = {};
  var gloveCount = 0;

  for (var i = 0; i < gloves.length; i++) {
    if (gloveList.hasOwnProperty(gloves[i])) {
      gloveList[gloves[i]] += 1;
    } else {
      gloveList[gloves[i]] = 0;
    }
  }
  for (var gloveColor in gloveList) {
    if (gloveList[gloveColor] > 0) {
      gloveCount++;
    }
  }
  return gloveCount;
}
```

# Exercise 5

```js
function race (a, b, lead) {
  var timeToCatch = (lead / (b - a));
  var hours = Math.floor(timeToCatch);
  var minutes = Math.floor((timeToCatch * 60) - (hours * 60));
  var seconds = (timeToCatch % 1 !== 0)
    ? Math.round((timeToCatch * 3600) - (hours * 3600) - (minutes * 60))
    : 0;

  return [hours, minutes, seconds];
}
```

# Exercise 6

```js
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
