[Exercise 1](#exercise-1) | [Exercise 2](#exercise-2) | [Exercise 3](#exercise-3)

# Exercise 1

```bash
mkdir new-fun-exercises && cd $_
git init
touch numbers-module.js && atom $_
```

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

# Exercise 2

```bash
mkdir file-module && cd $_
touch file-io.js && atom $_
```

_file-io.js_:

```js
var fs = require('fs');
var path = require('path');

var fileIO = {
  createFile: createFile,
  readFile: readFile,
  appendToFile: appendToFile,
  deleteFile: deleteFile
};

function createFile (fileName, content) {
  fs.writeFileSync(fileName, content);
  return fs.readFileSync(fileName, 'utf-8');
}

function readFile (fileName) {
  return fs.readFileSync(fileName, 'utf-8');
}

function appendToFile (fileName, content) {
  fs.appendFileSync(fileName, content);
  return fs.readFileSync(fileName, 'utf-8');
}

function deleteFile (fileName) {
  fs.unlinkSync(path.resolve(fileName));
  return 'Successfully removed ' + fileName + '.';
}

module.exports = fileIO;
```

_server.js_:

```js
var http = require('http');

var fileIO = require('./file-io');

var server = http.createServer(function (req, res) {
  fileIO.createFile('numbers.txt', 'My Magic Number:\n');
  fileIO.appendToFile('numbers.txt', (Math.random() * 10).toString());
  res.write(fileIO.readFile('numbers.txt'));
  res.end();
});

server.listen(3000);
console.log('Server running on port 3000');
```

*Bonus - Directory Creation*

_file-io.js_:

```js
var fs = require('fs');
var path = require('path');

var fileIO = {
  createFile: createFile,
  readFile: readFile,
  appendToFile: appendToFile,
  deleteFile: deleteFile,
  createDir: createDir
};

function createFile (fileName, content) {
  fs.writeFileSync(fileName, content);
  return fs.readFileSync(fileName, 'utf-8');
}

function readFile (fileName) {
  return fs.readFileSync(fileName, 'utf-8');
}

function appendToFile (fileName, content) {
  fs.appendFileSync(fileName, content);
  return fs.readFileSync(fileName, 'utf-8');
}

function deleteFile (fileName) {
  fs.unlinkSync(path.resolve(fileName));
  return 'Successfully removed ' + fileName + '.';
}

function createDir (dirName) {
  var absPath = path.resolve() + dirName;
  if (!fs.existsSync(absPath)) {
    fs.mkdirSync(absPath);
  }
  return absPath;
}

module.exports = fileIO;
```

_server.js_:

```js
var http = require('http');

var fileIO = require('./file-io');

var server = http.createServer(function (req, res) {
  fileIO.createDir('/temp');
  fileIO.createFile('./temp/numbers.txt', 'My Magic Number:\n');
  fileIO.appendToFile('./temp/numbers.txt', (Math.random() * 10).toString());
  res.write(fileIO.readFile('./temp/numbers.txt'));
  res.end();
});

server.listen(3000);
console.log('Server running on port 3000');
```

*Bonus - Function chaining*

_file-io.js_:

```js
var fs = require('fs');
var path = require('path');

var fileIO = {
  fileName: undefined,
  createFile: createFile,
  readFile: readFile,
  appendToFile: appendToFile,
  deleteFile: deleteFile,
  createDir: createDir,
  deleteDir: deleteDir
};

function createFile (fileName, content) {
  this.fileName = fileName;
  fs.writeFileSync(this.fileName, content);
  return this;
}

function readFile () {
  return fs.readFileSync(this.fileName, 'utf-8');
}

function appendToFile (content) {
  fs.appendFileSync(this.fileName, content);
  return this;
}

function deleteFile (fileName) {
  fs.unlinkSync(path.resolve(fileName));
  return 'Successfully removed ' + fileName + '.';
}

function createDir (dirName) {
  var absPath = path.resolve() + dirName;
  if (!fs.existsSync(absPath)) {
    fs.mkdirSync(absPath);
  }
  return absPath;
}

function deleteDir (dirName) {
  var absPath = path.resolve() + dirName;
  fs.rmdirSync(absPath);
  return absPath;
}

module.exports = fileIO;
```

_server.js_:

```js
var http = require('http');

var fileIO = require('./file-io');

var server = http.createServer(function (req, res) {
  fileIO.createDir('/temp');
  res.write(
    fileIO
      .createFile('./temp/numbers.txt', 'My Magic Number:\n')
      .appendToFile((Math.random() * 10).toString())
      .readFile()
  );
  res.end();
});

server.listen(3000);
console.log('Server running on port 3000');
```

# Exercise 3

_emitter.js_:

```js
var emitter = {
  events: {},
  on: on,
  emit
};

function on (eventType, listenerFunc) {
  if (!this.events[eventType]) {
    this.events[eventType] = [listenerFunc]
  } else {
    this.events[eventType].push(listenerFunc);
  }
}

function emit (eventType) {
  if (this.events[eventType]) {
    for (var i = 0; i < this.events[eventType].length; i++) {
      this.events[eventType][i]();
    }
  }
}

module.exports = emitter;
```

_server.js_:

```js
var emitter = require('./emitter');

emitter.on('winter', function () {
  console.log('Winter is coming');
});

emitter.on('call-the-hogs', function () {
  console.log('Woooo Pig Soooie!');
});


emitter.emit('winter');
emitter.emit('call-the-hogs');
```

*Bonus - Constructor Notation*

_emitter.js_:

```js
function Emitter () {
  this.events = {};
}

Emitter.prototype.on = function (eventType, listenerFunc) {
  if (!this.events[eventType]) {
    this.events[eventType] = [];
  }
  this.events[eventType].push(listenerFunc);
};

Emitter.prototype.emit = function (eventType) {
  if (this.events[eventType]) {
    for (var i = 0; i < this.events[eventType].length; i++) {
      this.events[eventType][i]();
    }
  }
}

module.exports = Emitter;
```

_server.js_:

```js
var Events = require('./emitter');

var emitter = new Events();

emitter.on('winter', function () {
  console.log('Winter is coming');
});

emitter.on('call-the-hogs', function () {
  console.log('Woooo Pig Soooie!');
});


emitter.emit('winter');
emitter.emit('call-the-hogs');
```
