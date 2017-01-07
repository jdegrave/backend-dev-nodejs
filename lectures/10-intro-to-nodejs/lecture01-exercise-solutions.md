# Exercise 1

```bash
mkdir fluffy-bunnies && cd $_
git init
npm init -y
npm install node-emoji --save-dev
git add .
git commit -m 'Initialize project'
touch emoji.js && atom .
```

_emoji.js_:

```js
var emoji = require('node-emoji');
function loopEmoji() {
  var emojis = [];

  for (var i = 0; i < 10; i++) {
    emojis.push(emoji.random().emoji);
  }

  for (var i = 0; i < emojis.length; i++) {
    console.log(emojis[i]);
  }
}
loopEmoji();
```

```bash
git add .
git commit -m 'Emoji all the things!'
git set upstream master repository-goes-here
git push origin master
```

# Exercise 2

_http-server.js_:

```js
var http = require('http');
var emoji = require('node-emoji');

var server = http.createServer(function (req, res) {
  res.write(emoji.random().emoji);
  res.end();
});

server.listen(8001);
console.log('Server listening on port 8001...');
```

```bash
curl http://localhost:8001/
git add .
git commit -m 'Server sends emoji'
git push origin master
```

# Exercise 3

_numbers-module.js_:

```js
module.exports = function (nbr, arr) {
  var result = [];
  var nbrIndex = arr.indexOf(nbr);

  if (nbr === arr[0]) {
    result.push(arr[arr.length - 1]);
    result.push(arr[nbrIndex + 1]);
  } else if (nbr === arr[arr.length - 1]) {
    result.push(arr[nbrIndex - 1]);
    result.push(arr[0]);
  } else {
    result.push(arr[nbrIndex - 1]);
    result.push(arr[nbrIndex + 1]);
  }

  return result;
};
```

_numbers-module.test.js_:

```js
var beforeAfter = require('./numbers-module.js');
var arr = [62,89,56,45,12,91,81];
var result;

console.log('Test 1 - Middle Number');

result = beforeAfter(45, arr);
if (result[0] === 56 && result[1] === 12) {
  console.log('Test passed');
} else {
  console.log('Test failed.');
}

console.log('Test 2 - First Number');

result = beforeAfter(62, arr);
if (result[0] === 81 && result[1] === 89) {
  console.log('Test passed');
} else {
  console.log('Test failed.');
}

console.log('Test 3 - Last Number');

result = beforeAfter(81, arr);
if (result[0] === 91 && result[1] === 62) {
  console.log('Test passed');
} else {
  console.log('Test failed.');
}
```

_index.js_:

```js
var beforeAfter = require('./numbers-module.js');

var arr = [62,89,56,45,12,91,81];

for (var i = 0; i < arr.length; i++) {
  console.log(beforeAfter(arr[i], arr));
}
```

```bash
git add .
git commit -m 'Lots of numbers'
git push origin master
```
