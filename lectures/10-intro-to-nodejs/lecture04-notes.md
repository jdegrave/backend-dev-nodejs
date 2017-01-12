# JavaScript Promises

Promises are an alternative to callbacks for handling asynchronous code in JavaScript. They exist because they can be composed together (or chained) to write code that is easy to understand when multiple asynchronous calls are needed (as an alternative to callback hell).

Let's look at a few examples before we begin:

```js
// Callbacks

loadData(function (error, data) {
  if (error) {
    // handle error
  }
  loadData(function (error, data) {
    if (error) {
      // handle error
    }
    loadData(function (error, data) {
      if (error) {
        // handle error
      }
      loadData(function (error, data) {
        if (error) {
          // handle error
        }
        return data;
      });
    })
  })
})

// promises

loadData()
  .then(function (data) {
    // do all the things
  })
  .then(function (data) {
    // do all the things
  })
  .then(function (data) {
    // do all the things
  })
  .then(function (data) {
    // do all the things
  })
  .catch(function (err) {
    // handle errors
  });

// we can do even better
loadData()
  .then(doAThing)
  .then(doAnotherThing)
  .then(doYetAnotherThing)
  .then(doFinalThing)
  .catch(handlErrors);

// And lastly, we can wait until all the things are done

Promise.all([
  loadData(),
  loadData(),
  loadData(),
  loadData()
]).then(function (data) {
  // do all the things
}).catch(function (err) {
  // handle errors
});
```

Promises are the "promise" of an eventual value in the form of an object with `then` and `catch` methods. And remember - promises are just objects.

## Creation

```js
function myPromiseFunc () {
  return new Promise(function (resolve, reject) {
    try {
      // do something
      // if successful:
      resolve('value-to-be-passed-back');
    } catch (err) {
      reject('error-to-be-passed-back');
    }
  });
}

// invocation
myPromiseFunc().then(function (data) {
  // data = 'value-to-be-passed-back'
}).catch(function (err) {
  // err = 'error-to-be-passed-back'
});
```

## then

`then` is a method on all promises that is used to specify what is done when the promise has completed. This function takes 1 argument, a callback function that should specify what needs to happen. This callback function is passed the result of a successful asynchronous operation from the promise. `then` always returns another promise.

```js
// syntax
promiseFunc().then(callback(resultFromPromise));

// example
doSomethingCool().then(function (resultFromPromise) {
  console.log(resultFromPromise);
});
```

## catch

`catch` is a method on all promises that is used to specify action that should be taken in the event that the promise errors. An important callout is that promises can eat run-time errors if not properly handled with `try...catch`.

`catch` takes a single argument - a callback function that is passed the error from the failed promise.


```js
// syntax
promiseFunc().catch(callback(errorFromPromise));

// example
doSomethingCool().catch(function (errorFromPromise) {
  console.log('Something bad happened!', errorFromPromise);
});
```

## resolve

`resolve` is a function used when defining promise functionality. It is used to specify what value is passed back to the `then` function upon successful completion of the promise. `resolve` is passed as the first argument to the Promise constructor callback.

```js
function myPromise () {
  return new Promise(function (resolve, reject) {
    // promise successful!
    resolve(data);
  });
}

// example of use
myPromise().then(function (data) {
  // the data value here is what is passed into the resolve function
});
```

## reject

`reject` is the opposite of resolve in that it is used to specify what should happen when an error occurs in the promise. Typically, the error itself is passed in as the argument for the `reject` function. The value passed to the `reject` function is then passed in as the argument of the `catch` callback argument.

## How do promises work?

```js
function promiseToBeAwesome () {
  return {
    then: function (callback) {
      callback('fluffykins');
    }
  }
}

promiseToBeAwesome().then(function (name) {
  console.log(name);
});
```

This is a very simple version of a promises, but in order to create a more robust implementation, we'll need to create a Promise type using constructor notation.

```js
function Promise (func) {
  var callback = null;
  this.then = function (cb) {
    callback = cb;
  }

  function resolve (value) {
    callback(value)
  }

  func(resolve);
}

function promiseToBeAwesome () {
  return new Promise(function (resolve) {
    resolve('fluffykins');
  });
}
```

This is still pretty naive but gets the point across. I suggest diving into one of the provided [resources](resources.md) for a deeper dive.

One last point is important to know that promises have 3 "statuses" (or state):

- pending: waiting for the request to be fulfilled
- resolve: request has successfully finished
- reject: request has failed

## Chaining Promises

Multiple promises can be chained back to back. This has the advantage of reading like synchronous code, but making asynchronous data calls. Within each callback, returning another promise will enable chaining of `.then` functions. Note that only a single `catch` is required.

```js
loadData()
  .then(function (data) {
    // do all the things
    return loadData();
  })
  .then(function (data) {
    // do all the things
    return loadData();
  })
  .then(function (data) {
    // do all the things
    return loadData();
  })
  .then(function (data) {
    // do all the things
    return loadData();
  })
  .catch(function (err) {
    // handle errors
  });
```

## Promise.all

`Promise.all` is a way of ensuring that many promises have all completed before moving forward. The returned value from this function is an array of values for each of the completed promises. Similar to chaining, only a single `catch` is required.

```js
Promise.all([
  loadData(),
  loadData(),
  loadData(),
  loadData()
]).then(function (data) {
  // do all the things
  // data would look like:
  //   [resultData, resultData, resultData, resultData]
}).catch(function (err) {
  // handle errors
});
```
