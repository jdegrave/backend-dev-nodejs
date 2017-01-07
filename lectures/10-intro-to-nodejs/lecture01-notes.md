# Node.js

## History

Node is an open-source JavaScript run-time environment for creating JavaScript applications outside of the browser. It uses Google's V8 JavaScript engine to interpret JavaScript.

Node was originally created in 2009 by Ryan Dahl, and its current development is steered by a foundation which consists of companies like Joyent, PayPal, IBM, Intel, Google and Microsoft.

It is written in C, C++ and JavaScript. In general, Node adds functionality needed to perform work on a server (and is not included in standard JavaScript):

- Organize code into reusable pieces (modules)
- Interact with databases
- Interact with the file system
- Communicate over the internet using proper protocols
- Handle processes that take a long period of time

## What's the V8 engine?

V8 is a JavaScript engine used in Google Chrome. This engine compiles JavaScript into machine code before executing it.

# NPM

NPM stands for Node Package Manager, and is the application used in the Node ecosystem to manage external code dependencies (packages). A package is a stand-alone piece of code often written by another author. NPM stores these packages on their own servers and make them available to Node / NPM users world-wide.

NPM is installed automatically when Node is installed. Packages are also known as modules (i.e. NPM modules). These will become very important to our development process.

## Usage

### Initialization

The first step in using NPM is to create a `package.json` file in the root of the project.

```
npm init
```

`npm init` will begin the initialization process and ask a series of questions. At the end it will create a `package.json` folder in the same directory. This file will contain different information depending on how the questions were answered. It's possible to use `-y` to short-circuit this process and instruct NPM to create a `package.json` with the default options.

An example `package.json`:

```json
{
  "name": "project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

- `name`: The name of the current directory / project
- `version`: The version of the module
- `description`: A short description of the module
- `main`: The file that runs the application. In projects that contain multiple files, this is the "bootstrap" or first file that is executed and starts the application
- `scripts`: Scripts that can be run via NPM (more on this at a later time)
- `author`: The author(s) of the project
- `license`: The type of usage license for the project. MIT is a common open source license

### Installing Modules

`npm install module` will create a folder in the project root called `node_modules`. This directory will contain all the code of the module. Note that this requires an internet connection. This works, however it does show that this module was used in the project. If someone else joined your team and wanted to work on this project, you'd have to remember and list all the dependencies and their versions.

Instead, this can be done via NPM's `package.json` file. `npm install module --save` will add the name of the package and its version to a `dependencies` object within the `package.json`. By default, NPM will install the latest version of the module. It's possible to specify a version number to install by using `npm install module@0.0.0 --save`.

### Removing Modules

Modules can be removed using `npm uninstall module --save`. This will remove the package from both the node_modules folder and the `dependencies` object in the `package.json`.

### Dev Dependencies vs Dependencies

When using `--save` with `npm install package`, the module is added to the `dependencies` property in the `package.json`, as mentioned above. However, it's also possible to use `--save-dev`, which will add the module and its version to a `devDependencies` property in the `package.json`.

*Dependencies should:*

- Be required for the package to function
- Be installed when using `npm install package`

*Dev Dependencies should:*

- Not be required for the package to function, but are required to work / develop the module
- Not be installed when using `npm install package`

# .gitignore

`.gitignore` is a file that can be included in the root directory of a project and specifies directories or files that git should ignore.

Examples include:
  - External dependencies
  - Build directories
  - Environmental Variables

An example of a `.gitignore` file:

```
node_modules
.env
```

In the above example, git would ignore the `node_modules` directory and the `.env` file. All files should be a relative path from the project root.

# Creating Our First HTTP Server

## Using Modules and Packages

Node.js uses the [CommonJS module pattern](http://www.commonjs.org/), which specifies how the module system should be implemented. For us, this means that we'll be using `require` and `export`. Modules are exported from their source, and required where needed in the application. Node.js has many "built-in" modules (also known as the standard library -- more on that later). One of these is `http`, which provides functionality pertaining to writing HTTP servers.

```js
var http = require('http');
```

Now we can access any of the HTTP methods that Node has to offer. Let's create our first server! To do this, we'll need to use 2 new methods: `createServer` and `listen`.

```js
var server = http.createServer(listenerFunction);

var server = http.createServer(function (req, res) {});

var server = http.createServer(function (req, res) {
  res.write('Hello from my first server!');
  res.end();
});
```

`createServer` accepts a listener function which will be passed a request (`req`) and response (`res`) object. Both of these objects have several built-in functions that we'll use over the course of this course, but for now we're going to focus on two: `write` and `end`. `write` tells the server what to send back to whatever client made the request. In this case, it will send back a string of text ('Hello from my first server!'). After we're done, it's important to close the connection, which is what `end` does.

Next, we need to start the server and tell it what port to listen on:

```js
var http = require('http');

var server = http.createServer(function (req, res) {
  res.write('Hello from my first server!');
  res.end();
});

server.listen(3000);
console.log('Server listening on port 3000');
```

### Node.js Standard Library

Node includes several useful modules. Here are a few of the most useful:

- `http`: HTTP functionality
- `https`: HTTPS functionality
- `fs`: File System functionality
- `crypto`: Cryptography functionality
- `path`: File path functionality

The Node.js documentation is very good. Use it!
