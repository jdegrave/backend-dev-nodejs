# Programming Fundamentals

- Nested Data
  - Arrays can contain other arrays
  ``` js
  var myOtherArray = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
  ];

  console.log('SECOND ARRAY FIRST VALUE: ', myOtherArray[1][0]); // logs 7
  ```
  - Objects can contain arrays
  ``` js
  var myObjectWithArray = {
    firstName: 'Brenna',
    lastName: 'Blackwell',
    favoriteFood: ['sushi', 'pizza', 'chocolate', 'donuts']
  };

  console.log('MY FAVORITE FOODS: ', myObjectWithArray.favoriteFood[1]); // logs pizza
  ```
  - Objects can contain other objects
  ``` js
  var myObjectWithObject = {
    firstName: 'Brenna',
    lastName: 'Blackwell',
    favoriteFood: ['sushi', 'pizza', 'chocolate', 'donuts'],
    address: {
      streetName: '123 Main St',
      city: 'Fayetteville',
      state: 'AR',
      zip: '72701'
    }
  };

  console.log('MY ADDRESS: ', myObjectWithObject.address.streetName); // logs 123 Main St
  ```
  - Arrays can contain objects
  ``` js
  var myOtherArrayOfObjects = [
    {
      first: 1,
      second: 2,
      third: 3
    },
    {
      first: 4,
      second: 5,
      third: 6
    },
    {
      first: 7,
      second: 8,
      third: 9
    }
  ];

  console.log('SECOND OBJECT: ', myOtherArrayOfObjects[1]); // logs the object with first: 4, second: 5 and third: 6
  ```

- Conditionals
  - If/Else
    - Can be used for simple or complex checks
    ``` js
    var myNumber = 5;
    if (myNumber > 10) {
      console.log('my number is big');
    } else {
      console.log('my number is small');
    }
    // logs 'my number is small'
    ```
    - You can have multiple checks
    ``` js
    var myNumber = 10;
    if (myNumber > 10) {
      console.log('my number is big');
    } else if (myNumber < 10) {
      console.log('my number is small');
    } else {
      console.log('my number is ten');
    }
    // logs my number is ten
    ```
    - You can have multiple conditions in a single check using the and ('&&') and or ('||') operators
    ``` js
    var myNumber = 5;
    var myString = 'house';
    if (myNumber > 10 && myString === 'apartment') {
      console.log('my apartment is full');
    } else {
      console.log('my house is empty');
    }
    // logs 'my house is empty'

    if (myNumber < 10 || myString === 'apartment') {
      console.log('my apartment is just right');
    } else {
      console.log('my house is empty');
    }
    // logs 'my apartment is just right'
    ```
    - Conditions can be negative
    ``` js
    var myNumber = 5;
    if (myNumber !== 10) {
      console.log('my number is not 10');
    } else {
      console.log('my number is 10');
    }
    // logs 'my number is not 10'
    ```
    - The ternary operator can take the place of a simple if/else
    ``` js
    var isBig = (myNumber > 6) ? 'greater than six' : 'less than six';
    ```
    - Can check for things not existing
    ``` js
    var myString;
    if(!myString) {
      console.log('myString is not defined');
    }
    // logs 'myString is not defined'
    ```
  - Switch
    - A switch statement can be used instead of chaining multiple else ifs, and is the cases are the equivalent of a strict equality check '==='
    ``` js
    var myNumber = 5;
    switch(myNumber) {
      case 1:
        console.log('one');
        break;
      case 2:
        console.log('two');
        break;
      case 3:
        console.log('three');
        break;
      case 4:
        console.log('four');
        break;
      case 5:
        console.log('five');
        break;
      default:
        console.log('not 1 - 5');
        break;
    }
    ```
