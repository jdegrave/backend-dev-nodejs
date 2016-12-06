# Exercise 1

```js
var person = {
  firstName: 'John',
  lastName: 'Doe',
  getFullName: function () {
    return this.firstName + ' ' + this.lastName;
  }
}

var anotherPerson = {
  firstName: 'Jane',
  lastName: 'Smith'
}

// Most Straightforward
anotherPerson.getFullName = person.getFullName;
console.log(person.getFullName());
console.log(anotherPerson.getFullName());

// Using call on Function prototype
console.log(person.getFullName());
console.log(person.getFullName.call(anotherPerson));

// Using bind on Function prototype
var getOtherFullName = person.getFullName.bind(anotherPerson);
console.log(person.getFullName());
console.log(getOtherFullName());
```
