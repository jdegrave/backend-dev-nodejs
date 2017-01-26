# Exercise 1

```bash
mkdir expressing-myself && cd $_
git init
npm init -y
npm install express --save
```

_index.js_:

```js
var express = require('express');

var app = express();

app.get('/', function (req, res) {
  res.send('Expressing myself on the interwebs!');
});

app.listen(3000, function () {
  console.log('Listening on port 3000...');
});
```

```bash
git add .
git commit -m 'First Express app'
git set upstream master repository-goes-here
git push origin master
```
