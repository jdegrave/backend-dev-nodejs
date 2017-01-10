# Writing a Node.js Module

A module is a reusable piece of code written by the person working on the project _or_ someone else (i.e. NPM modules).

It's possible to write our own Node.js modules and include them from other files. To do this, we'll use `module.exports`. Using this allows us to include whatever is exported in another file by using `require`, just like we did for the Node.js

There are multiple ways to do this, but a few are used commonly:

*Constructor Function*

File 1:

```js
function myModule () {
  this.dogsAreBetter = function () {
    console.log('Dogs are so much better than cats!');
  }
}

module.exports = new myModule();
```

File 2:

```js
var mod = require('./file1');

mod.dogsAreBetter();
```

*Exporting a function*

File 1:

```js
module.exports = function () {
  console.log('Dogs are so much better than cats!');
}
```

File 2:

```js
var mod = require('./file1');

mod();
```

*Extend Module.Exports*

File 1:

```js
module.exports.dogsAreBetter = function () {
  console.log('Dogs are so much better than cats!');
}
```

File 2:

```js
var mod = require('./file1').dogsAreBetter;

mod();
```

*Revealing Module Pattern*

File 1:

```js
var myModule = {
  dogsAreBetter: dogsAreBetter
};

function dogsAreBetter () {
  console.log('Dogs are so much better than cats!');
}

module.exports = myModule;
```

File 2:

```js
var mod = require('./file1');

console.log(mod.dogsAreBetter());
```

Of these methods, the "Revealing Module Pattern" is the preferred option.

# The Node.js Standard Library

We're going to spend some time working with a few more of the built-in Node.js libraries: `fs` and `path`.

## Path

The `path` module provides ways to work with directory paths. It's important to note that the functionality for some of the path functions is different depending on the file system on the OS. Windows performs a bit differently than other systems, so keep this in mind and check the documentation if working in Windows and using `path`.

### path.basename

`path.basename` will return the last portion of a path (i.e. the file name). This can be useful to retrieve file references across the file system.

```js
var path = require('path');

// from ~/dev/node-projects
path.basename('~/dev/node-projects/script.js'); // script.js
```

It's important to know that `basename` does not do any validation on the path provided, it only manipulates the string that's given to the function. This function also takes a second (optional) argument that represents the file extension type. Including this argument will only return the name of the file without the extension.

```js
var path = require('path');

// from ~/dev/node-projects
path.basename('~/dev/node-projects/script.js', 'js'); // script
```

### path.dirname

`path.dirname` will return the directory of a provided path. It's again important to note that this function is simply a string manipulation function and that it does not validate the existence of the path provided.

```js
var path = require('path');

// from ~/dev/node-projects
path.dirname('~/dev/node-projects/script.js');  // ~/dev/node-projects
```

### path.resolve

`path.resolve` will construct an absolute path from strings provided as arguments. The arguments are resolved from right to left, and if no absolute path is given as part of the arguments, then the current working directory is used. This can be great for generating paths within an application.

```js
var path = require('path');

// from ~/dev/node-projects
path.resolve('script.js');  // /Users/bjohnston/dev/node-projects/script.js
```

An example using multiple directories:

```js
var path = require('path');

// from ~/dev/node-projects
path.resolve('sub-dir', 'sub-sub-dir', 'script.js');

// /Users/bjohnston/dev/node-projects/sub-dir/sub-sub-dir/script.js
```

## FS

Interacting with the file system is done through the `fs` module. There are a few functions we'll explore now that are useful, and add a few more additional functions later.

### fs.writeFileSync

`fs.writeFileSync` creates a file synchronously. This function takes 3 arguments:

  - `filename`
  - `data` - information that should be included in the file
  - `options` (optional) - This can specify additional options such as file-encoding, mode, etc. For our purposes, we will use the default options. By default, files are encoded as the `utf-8` type.

```js
var fs = require('fs');

fs.writeFileSync('new-file.txt', 'Mmmm, pancakes!');
// creates a file named new-file.txt with 'Mmmm, pancakes!' on the first line
```

### fs.readFileSync

`fs.readFileSync` reads a file synchronously. This function takes 2 arguments:

  - `filename`
  - `options` (optional) - This option can be used to specify file-encoding. Without specifying encoding, this function will return a buffer. We want it to return a string of data, so we will have to specify the file-encoding.

```js
var fs = require('fs');

fs.writeFileSync('new-file.txt', 'Mmmm, pancakes!');
fs.readFileSync('new-file.txt', 'utf-8'); // Mmmm, pancakes!
```

### fs.appendFileSync

`fs.appendFileSync` appends data to a file synchronously. This function takes 3 arguments:

  - `filename`
  - `data` - text (or buffer) to append to the file
  - `options` (optional) - This can specify additional options such as file-encoding, mode, etc. For our purposes, we will use the default options. By default, files are encoded as the `utf-8` type.

```js
var fs = require('fs');

fs.writeFileSync('new-file.txt', 'Mmmm, pancakes!');
fs.readFileSync('new-file.txt', 'utf-8'); // Mmmm, pancakes!
fs.appendFileSync('new-file.txt', '\nBut don\'t forget about waffles!');
fs.readFileSync('new-file.txt', 'utf-8'); // Mmmm, pancakes! <n> But don't forget about waffles!
```

### fs.unlinkSync

`fs.unlinkSync` deletes a file or folder synchronously. This function takes 1 argument:

  - `path` - file path to be deleted

```js
var path = require('path');
var fs = require('fs');

fs.writeFileSync('new-file.txt', 'Mmmm, pancakes!');
fs.readFileSync('new-file.txt', 'utf-8'); // Mmmm, pancakes!
fs.appendFileSync('new-file.txt', '\nBut don\'t forget about waffles!');
fs.readFileSync('new-file.txt', 'utf-8'); // Mmmm, pancakes! <n> But don't forget about waffles!
fs.unlinkSync(path.resolve('new-file.txt'));
fs.readFileSync('new-file.txt', 'utf-8'); // Error! No file new-file.txt exists!
```

# Node.js Event Emitter

## What's an Event?

An event is something that happens somewhere in our application, and we want to react to that occurrence. This is a concept that is fundamental to Node, and prevalent on the front-end as well.

### What is an emitter?

_emitter.js_:

```js
var emitter = {
  events: {},
  on: on,
  emit: emit
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

emitter.on('call-the-hogs', function () {
  console.log('WOOOOOOOOOO');
});

emitter.on('call-the-hogs', function () {
  console.log('PIG');
});

emitter.on('call-the-hogs', function () {
  console.log('SOOOOOIE!');
});

emitter.emit('call-the-hogs');
```

## Node Events

_server.js_:

```js
var Events = require('events');

var emitter = new Events();

emitter.on('call-the-hogs', function () {
  console.log('WOOOOOOOOOO');
});

emitter.on('call-the-hogs', function () {
  console.log('PIG');
});

emitter.on('call-the-hogs', function () {
  console.log('SOOOOOIE!');
});

emitter.emit('call-the-hogs');
```
