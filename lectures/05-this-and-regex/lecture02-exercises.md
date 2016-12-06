# Exercise 1

Using what we've learned, how could we call getFullName, but force its this to be a different context than person? There are multiple ways to do this, try to find multiple solutions

```js
'use strict';

var person = {
  firstName: 'John',
  lastName: 'Doe',
  getFullName: function () {
    return this.firstName + ' ' + this.lastName;
  }
}

console.log(person.getFullName());
```
