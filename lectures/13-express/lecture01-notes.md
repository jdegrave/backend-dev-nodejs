# Express

## What is Express?

[Express](http://expressjs.com/) is a web framework for Node.js that specializes in building small and performant APIs. It was originally released in 2010 by TJ Holowaychuk, and in 2014 IBM-owned StrongLoop took over rights to manage the project. Express is now also part of the Node.js Foundation.

There are several alternatives to Express:

- [Koa](http://koajs.com/)
- [Feathers](http://feathersjs.com/)
- [Nodal](http://www.nodaljs.com/)
- [Sails](http://sailsjs.com/)
- [Hapi](https://hapijs.com/)

Of the alternatives, Koa, Sails and Hapi are the most popular. Sails and Feathers are both built _on top_ of Express (i.e. they have the same Express functionality, but add features).

Despite many alternatives, Express continues to be the most popular web framework for Node.js, and is very flexible.

## Creating Our First Express App

Before creating our first Express app, let's review what our first Node web server looked like:

```js
var http = require('http');

var server = http.createServer(function (req, res) {
  res.write('Hello from my first server!');
  res.end();
});

server.listen(3000);
console.log('Server listening on port 3000');
```

### Step One: Install Express via NPM

`npm init -y && npm install express --save`

### Step Two: Require and Initialize

_index.js_:

```js
var express = require('express');
var app = express();
```

Wait... what? Why are we invoking the module? Express exports a function from its module, named `createApplication`. This function sets up the entire Express app and all dependencies / inheritance required.

### Step Three: Setup Root Route

```js
var express = require('express');
var app = express();

app.get('/', function (req, res) {
  res.send('Hello from my first Express app!');
});

app.listen(3000, function () {
  console.log('Server listening on port 3000');
});
```

`app.get` takes two arguments:

  - A string representing the route (i.e. `/` or `/puppies`)
  - A callback function specifying what to send as a response

Notice how concise this code is, and how easy it is to read. We didn't have to `end` the connection. Indeed, the beauty in Express is that it will take care of a lot of the Node functionality under the hood and make our APIs easier to create and reason about.

## Routing

Let's expand on routing a bit, though. It's common practice to put your routes in their own directory and to organize them in a way that meets the needs of the API.

Here's an overview of the API structure we'll be using for these examples:

```
/ - root
  /puppies
    /puppies/:id
  /kitties
```

### API documentation

It's common to document different routes and the HTTP verbs associated w/them. Let's do that for the above structure.

*GET /*

- Desc: Root
- Response: 200 text/html
- Data: "Welcome to Puppies Only!"

*GET /puppies*

- Desc: Returns all puppies
- Response: 200 application/json
- Data: [{}, {}, {}]

*POST /puppies*

- Desc: Creates and returns a new puppy
- Response: 200 application/json
- Data: {}

*GET /puppies/:id*

- Desc: Returns a single puppy represented by its `id`
- Response: 200 application/json
- Data: {}

*PUT /puppies/:id*

- Desc: Updates and returns the matching puppy
- Response: 200 application/json
- Data: {}

*GET /kitties*

- Desc: Returns all kitties (or does it?)
- Response: 200 text/html
- Data: 'lol jk - No kitties here!'

Our puppy objects will look like:

```js
{
  id: number,
  name: string,
  breed: string,
  likes: array,
  dislikes: array
}
```

### Creating the Router

Within the root file, we need to tell the Express application where to find our soon-to-be-created routes. So we'll create a `routes` Node module within our project and tell it to look there. This means that we'll need to `require` that module in the `index.js` file.

_index.js_:

```js
var express = require('express');
var app = express();

var routes = require('./routes');

app.use('/', routes);

app.listen(3000, function () {
  console.log('Listening on port 3000...');
});
```

`app.use` is an Express method for setting up Middleware in Express. We will talk more about Middleware next Wednesday and Saturday. For now, just know that it is used to setup the route.

Let's go ahead and setup the route file now:

_/routes/index.js_:

```js
var router = require('express').Router();

router.get('/', function (req, res) {
  res.status(200).send('Welcome to Puppies Only!');
});

module.exports = router;
```

Here, we've imported the Express router, and added a GET method for the root URL that will return a string and status of 200. Since we need to make the routes available to the remainder of the application, we need to make sure that we export the router object. at the end.

From here, we can split this off into different logical subfolders based on the structure of our API. From our API definition, it looks like we'll have logical paths for both `/kitties` and `/puppies`, so it makes sense to put those routes in their own folders.

Our folder structure should now look like:

```
/ root
  |-  routes
  |     |-  kitties
  |     |     |-  index.js
  |     |
  |     |-  puppies
  |     |     |-  index.js
  |     |
  |     |-  index.js
  |
  |-  index.js
```

Next create the `/kitties` route. Before we create the actual kitties route file, we need to tell the main route file in `/routes/index.js` to look for our `kitties` file when `/kitties` is called in the browser.

_routes/index.js_:

```js
var router = require('express').Router();

var kitties = require('./kitties');

router.get('/', function (req, res) {
  res.status(200).send('Welcome to Puppies Only!');
});

routes.use('/kitties', kitties);

module.exports = router;
```

_/routes/kitties/index.js_:

```js
var router = require('express').Router();

router.get('/', function (req, res) {
  res.status(200).send('lol jk - no kitties here!');
});

module.exports = router;
```

Moving onto the puppies routes, we'll have a bit more work to do. First, we should update our core router and add the puppies module.

_routes/index.js_:

```js
var router = require('express').Router();

var kitties = require('./kitties');
var puppies = require('./puppies');

router.get('/', function (req, res) {
  res.status(200).send('Welcome to Puppies Only!');
});

routes.use('/kitties', kitties);
routes.use('/puppies', puppies);

module.exports = router;
```

_/routes/puppies/index.js_:

```js
var router = require('express').Router();

var puppies = [
  {
    id: 1,
    name: 'Fluffykins',
    breed: 'Labradoodle',
    likes: ['naps', 'bones', 'cuddles'],
    dislikes: ['kitties', 'milk']
  },
  {
    id: 2,
    name: 'Sprinkles',
    breed: 'Dalmatian',
    likes: ['petting', 'snacks', 'swimming'],
    dislikes: ['all other animals', 'Dachshunds']
  },
  {
    id: 3,
    name: 'Bibblyboo',
    breed: 'Pug',
    likes: ['snoring', 'pooping'],
    dislikes: ['Dalmatians', 'trees']
  },
  {
    id: 4,
    name: 'Fred',
    breed: 'Frenchie',
    likes: ['snark', 'chasing rabbits', 'turkey'],
    dislikes: ['birds', 'squirrels', 'uneven bedding']
  }
]

router.get('/', function (req, res) {
  res.status(200).json(puppies);
});

router.get('/:id', function (req, res) {
  var puppy;
  for (var i = 0; i < puppies.length; i++) {
    if (req.params.id.toString() === puppies[i].id.toString()) {
      puppy = puppies[i];
    }
  }

  res.status(200).json(puppy);
});

module.exports = router;
```

To add the post routes, we're going to have to include something called the body-parser middleware. Again, we will talk in depth about middleware in next week's lecture, but for now know that the body-parser middleware will inspect the body property provided in the request, and turn it into a format that Express can recognize. Since we're sending our information across as JSON, we need it to interpret the JSON for us.

`npm install body-parser --save`

_index.js_:

```js
var express = require('express');
var bodyParser = require('body-parser');

var routes = require('./routes');

var app = express();

app.use(bodyParser.json());
app.use('/', routes);

app.listen(3000, function () {
  console.log('Server listening on port 3000...');
});
```

It's important to know that the `app.use` statements are processed *in the order they are listed*. This means that it's important for us to setup the body parser before we setup the routes, so that the routes can then use the body parser.

We can now setup our POST and PUT request.

_/routes/puppies/index.js_:

```js
var router = require('express').Router();

var puppies = [
  {
    id: 1,
    name: 'Fluffykins',
    breed: 'Labradoodle',
    likes: ['naps', 'bones', 'cuddles'],
    dislikes: ['kitties', 'milk']
  },
  {
    id: 2,
    name: 'Sprinkles',
    breed: 'Dalmatian',
    likes: ['petting', 'snacks', 'swimming'],
    dislikes: ['all other animals', 'Dachshunds']
  },
  {
    id: 3,
    name: 'Bibblyboo',
    breed: 'Pug',
    likes: ['snoring', 'pooping'],
    dislikes: ['Dalmatians', 'trees']
  },
  {
    id: 4,
    name: 'Fred',
    breed: 'Frenchie',
    likes: ['snark', 'chasing rabbits', 'turkey'],
    dislikes: ['birds', 'squirrels', 'uneven bedding']
  }
]

router.get('/', function (req, res) {
  res.status(200).json(puppies);
});

router.get('/:id', function (req, res) {
  var puppy = getPuppy(puppies, req.params.id);

  res.status(200).json(puppy);
});

router.post('/', function (req, res) {
  var puppyId = req.body.id;
  puppies.push(req.body);
  var puppy = getPuppy(puppies, puppyId);
  res.status(200).json(puppy);
});

router.put('/:id', function (req, res) {
  var puppy = updatePuppy(puppies, req.body, req.params.id);
  res.status(200).json(puppy);
});

function getPuppy (arr, id) {
  var puppy;
  for (var i = 0; i < arr.length; i++) {
    if (id.toString() === arr[i].id.toString()) {
      puppy = arr[i];
    }
  }
  return puppy;
}

function updatePuppy (arr, newPuppy, id) {
  var puppy;
  for (var i = 0; i < arr.length; i++) {
    if (id.toString() === arr[i].id.toString()) {
      arr[i].name = newPuppy.name;
      arr[i].breed = newPuppy.breed;
      arr[i].likes = newPuppy.likes;
      arr[i].dislikes = newPuppy.dislikes;

      puppy = arr[i];
    }
  }
  return puppy;
}

module.exports = router;
```

Finally, we want to add the ability to sort the array by name, so we'll add that as a query parameter to `GET /puppies`.

_/puppies/index.js_:

```js
var router = require('express').Router();

var puppies = [
  {
    id: 1,
    name: 'Fluffykins',
    breed: 'Labradoodle',
    likes: ['naps', 'bones', 'cuddles'],
    dislikes: ['kitties', 'milk']
  },
  {
    id: 2,
    name: 'Sprinkles',
    breed: 'Dalmatian',
    likes: ['petting', 'snacks', 'swimming'],
    dislikes: ['all other animals', 'Dachshunds']
  },
  {
    id: 3,
    name: 'Bibblyboo',
    breed: 'Pug',
    likes: ['snoring', 'pooping'],
    dislikes: ['Dalmatians', 'trees']
  },
  {
    id: 4,
    name: 'Fred',
    breed: 'Frenchie',
    likes: ['snark', 'chasing rabbits', 'turkey'],
    dislikes: ['birds', 'squirrels', 'uneven bedding']
  }
]

router.get('/', function (req, res) {
  var puppyArray = (req.query.sort === 'breed') ? sortByBreed(puppies) : puppies;
  res.status(200).json(puppyArray);
});

router.get('/:id', function (req, res) {
  var puppy = getPuppy(puppies, req.params.id);

  res.status(200).json(puppy);
});

router.post('/', function (req, res) {
  var puppyId = req.body.id;
  puppies.push(req.body);
  var puppy = getPuppy(puppies, puppyId);
  res.status(200).json(puppy);
});

router.put('/:id', function (req, res) {
  var puppy = updatePuppy(puppies, req.body, req.params.id);
  res.status(200).json(puppy);
});

function getPuppy (arr, id) {
  var puppy;
  for (var i = 0; i < arr.length; i++) {
    if (id.toString() === arr[i].id.toString()) {
      puppy = arr[i];
    }
  }
  return puppy;
}

function updatePuppy (arr, newPuppy, id) {
  var puppy;
  for (var i = 0; i < arr.length; i++) {
    if (id.toString() === arr[i].id.toString()) {
      arr[i].name = newPuppy.name;
      arr[i].breed = newPuppy.breed;
      arr[i].likes = newPuppy.likes;
      arr[i].dislikes = newPuppy.dislikes;

      puppy = arr[i];
    }
  }
  return puppy;
}

function sortByBreed (arr) {
  return arr.sort(function (a, b) {
    if (a.breed.toUpperCase() < b.breed.toUpperCase()) {
      return -1;
    }
    if (a.breed.toUpperCase() > b.breed.toUpperCase()) {
      return 1;
    }

    return 0;
  });
}

module.exports = router;
```
