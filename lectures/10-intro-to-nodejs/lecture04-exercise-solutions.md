# Exercise 1

```bash
mkdir tonight-we-ride && cd $_
touch api.js && atom $_
```

_index.js_:

```js
var api = require('./api');

function requestName () {
  return new Promise(function (resolve) {
    return api.getName(function (err, name) {
      resolve(name);
    });
  });
}

requestName().then(function (name) {
  console.log(name);
});
```

*Bonus Question*

_index.js_:

```js
var api = require('./api');

function requestName () {
  return new Promise(function (resolve, reject) {
    return api.getName(function (err, name) {
      reject('Oops!');
    });
  });
}

requestName().then(function (name) {
  console.log(name);
}).catch(function (err) {
  console.log(err);
});
```

```bash
git add .
git commit -m 'Exercise 1'
git push
```

# Exercise 2

_index.js_:

```js
var fs = require('fs');

function createFile (fileName, content) {
  return new Promise(function (resolve, reject) {
    fs.writeFile(fileName, content, function (err) {
      if (err) {
        reject(err);
      }
      resolve();
    });
  });
}

function appendFile (fileName, content) {
  return new Promise(function (resolve, reject) {
    fs.appendFile(fileName, content, function (err) {
      if (err) {
        reject(err);
      }
      resolve();
    });
  });
}

createFile('my-file.txt', 'Dinosaurs!').then(function () {
  console.log('File created!')
});

appendFile('my-file.txt', '\nAnd pancakes!').then(function () {
  console.log('File appended!');
});
```

*Bonus Question*

_index.js_:

```js
var fs = require('fs');

function createFile (fileName, content) {
  return new Promise(function (resolve, reject) {
    fs.writeFile(fileName, content, function (err) {
      if (err) {
        reject(err);
      }
      resolve();
    });
  });
}

function appendFile (fileName, content) {
  return new Promise(function (resolve, reject) {
    fs.appendFile(fileName, content, function (err) {
      if (err) {
        reject(err);
      }
      resolve();
    });
  });
}

createFile('my-file.txt', 'Dinosaurs!').then(function () {
  return appendFile('my-file.txt', '\nAnd pancakes!');
}).then(function () {
  console.log('File appended!');
});
```

```bash
git add .
git commit -m 'Exercise 2'
git push
```

# Exercise 3

_index.js_:

```js
var api = require('./api');

function getName () {
  return new Promise(function (resolve, reject) {
    return api.getName(function (err, name) {
      if (err) {
        reject(err);
      }
      resolve(name);
    });
  });
}

function getBreed (name) {
  return new Promise(function (resolve, reject) {
    return api.getBreed(name, function (err, breed) {
      if (err) {
        reject(err);
      }
      resolve(breed);
    });
  });
}

function getCoatColor (breed) {
  return new Promise(function (resolve, reject) {
    return api.getCoatColor(breed, function (err, coatColor) {
      if (err) {
        reject(err);
      }
      resolve(coatColor);
    });
  });
}

getName()
  .then(function (name) {
    return getBreed(name);
  })
  .then(function (breed) {
    return getCoatColor(breed);
  })
  .then(function (coat) {
    console.log(coat);
  })
  .catch(function (err) {
    console.log(err);
  });
```

```bash
git add .
git commit -m 'Exercise 3'
git push
```

# Exercise 4

```js
var api = require('./api');

function getRandomNumber () {
  return new Promise(function (resolve, reject) {
    return api.getRandomNumber(function (err, nbr) {
      if (err) {
        reject(err);
      }
      resolve(nbr);
    });
  });
}

Promise.all([
  getRandomNumber(),
  getRandomNumber(),
  getRandomNumber(),
  getRandomNumber(),
  getRandomNumber()
]).then(function (nbrArray) {
  console.log(nbrArray);
  var nbr = 0;

  for (var i = 0; i < nbrArray.length; i++) {
    nbr += nbrArray[i];
  }

  console.log('Final number is: ', nbr);
}).catch(function (err) {
  console.log(err);
});
```
