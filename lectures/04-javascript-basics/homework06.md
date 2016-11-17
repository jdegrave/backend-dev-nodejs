# Exercise 1

Write a function, `persistence`, that takes a positive integer (`num`) as input and returns its multiplicative persistence, which is the number of times you must multiply the digits in `num` until you reach a single digit.

For example:

```js
persistence(39) === 3 // because 3*9 = 27, 2*7 = 14, 1*4=4
                     // and 4 has only one digit

persistence(999) === 4 // because 9*9*9 = 729, 7*2*9 = 126,
                      // 1*2*6 = 12, and finally 1*2 = 2

persistence(4) === 0 // because 4 is already a one-digit number
```

```js
console.log(persistence(39));    // 3
console.log(persistence(4));     // 0
console.log(persistence(25));    // 2
console.log(persistence(999));   // 4
```

# Exercise 2

Dan, president of a large company, could use your help. He wants to implement a system that will switch all his devices into offline mode depending on his meeting schedule. When he's at a meeting and somebody texts him, he wants to send an automatic message informing him that he's currently unavailable and the time when he's going to be back.

Your task is to write a helper function `checkAvailability` that will take 2 arguments:

- `schedule`, which is going to be a nested array with Dan's schedule for a given day. Inside arrays will consist of 2 elements - start and finish time of a given appointment.

- `currentTime` - is a string with specific time in `hh:mm` 24-h format for which the function will check availability based on the schedule.

If no appointments are scheduled for currentTime, the function should return `true`. If there are no appointments for the day, the output should also be true. If Dan is in the middle of an appointment at `currentTime`, the function should return a string with the time he's going to be available.

```js
console.log(checkAvailability([['09:30', '10:15'], ['12:20', '15:50']], '11:00'));   // true
console.log(checkAvailability([['09:30', '10:15'], ['12:20', '15:50']], '10:00'));   // '10:15'
console.log(checkAvailability([['09:30', '10:15'], ['12:20', '15:50']], '13:24'));   // '15:50'
console.log(checkAvailability([], '8:30'));   // true
```
