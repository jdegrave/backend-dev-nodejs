# Exercise 1

Translate the provided string to pig latin.

Pig Latin takes the first consonant (or consonant cluster) of an English word, moves it to the end of the word and suffixes an "ay".

If a word begins with a vowel you just add "way" to the end.

```js
console.log(translatePigLatin("california")); // "aliforniacay"
console.log(translatePigLatin("paragraphs")); //"aragraphspay"
console.log(translatePigLatin("glove")); // "oveglay"
console.log(translatePigLatin("algorithm")); //"algorithmway"
console.log(translatePigLatin("eight")); //"eightway"
```

# Exercise 2

In a factory a printer prints labels for boxes. For one kind of boxes the printer has to use colors which, for the sake of simplicity, are named with letters from a to m.

The colors used by the printer are recorded in a control string. For example, a "good" control string would be aaabbbbhaijjjm meaning that the printer used color a three times, color b four times, then color a again, etc.

Sometimes there are problems: lack of colors, technical malfunction and a "bad" control string is produced e.g. aaaxbbbbyyhwawiwjjjwwm.

Write a function named printerError, which given a string will output the error rate of the printer as a string with a fraction where the numerator is the number of errors and the denominator the length of the control string. Letters will always be lowercase.


```js
console.log(printerError('aaaaaaaaaaaaaaaabbbbbbbbbbbbbbbbbbmmmmmmmmmmmmmmmmmmmxyz'));   // '3/56'
console.log(printerError('aaabbbbhaijjjm'));   // '0/14'
console.log(printerError('aaaxbbbbyyhwawiwjjjwwm'));   // '8/22'
```

# Exercise 3

The best way to have a productive day is to plan out your work schedule. Given the following three inputs, please create an an array of time allotted to work, broken up with time allotted with breaks:

- Input 1: Hours - Number of hours available to you to get your work done!
- Input 2: Tasks - How many tasks you have to do throughout the day
- Input 3: Duration (minutes)- How long each of your tasks will take to complete

Criteria to bear in mind:

- Your schedule should start with work and end with work.
- It should also be in minutes, rounded to the nearest whole minute.
- If your work is going to take more time than you have, return "You're not sleeping tonight!"

```js
console.log(dayPlan(8, 5, 30));   // [30, 83, 30, 83, 30, 83, 30, 83, 30]
console.log(dayPlan(3, 5, 60));   // 'You're not sleeping tonight!'
console.log(dayPlan(2, 2, 60));   // [60, 0, 60]
```

# Exercise 4

Winter is coming! You must prepare for the bitter cold of Arkansas winter. Determine the number of pair of gloves you can constitute from the gloves you have in your very unorganized drawer.

A pair of gloves is constituted of two gloves of the same color.

You are given an array containing the color of each glove.

You must return the number of pairs you can create.

You must not change the input array.

```js
console.log(numberOfGloves(['red','red']));   // 1
console.log(numberOfGloves(['red','green','blue']));   // 0
console.log(numberOfGloves(['gray','black','purple','purple','gray','black']));   // 3
```

# Exercise 5

Two tortoises named Blurtle and Harriet must run a race. Blurtle starts with an average speed of 720 feet per hour. Young Harriet knows she runs faster than Blurtle and furthermore has not finished her cabbage.

When she starts, at last, she can see that Blurtle has a 70 feet lead, but she can travel 850 feet per hour. How long will it take Harriet to catch Blurtle?

- Input 1: speed `a` (integer > 0)
- Input 2: speed `b` (integer > 0)
- Input 3: lead of `a` over `b` (integer > 0)

The result will be an array [h, mn, s] where h, mn, s is the time needed in hours, minutes and seconds (don't worry for fractions of second).

```js
console.log(race(720, 850, 70));    // [0, 32, 18]
console.log(race(80, 91, 37));      // [3, 21, 49]
console.log(race(80, 100, 40));     // [2, 0, 0]
```

# Exercise 6

Your goal is to implement the method `filter`, which accepts an array and a predicate function, and returns an array which only contains the elements which apply to the given predicate.

For example: Given the array: [1, 2, 3], and the predicate function `function (x) { return x >=2 }`, `filter` should return [2, 3], since `x >= 2` applies to both 2 and 3.

Note: the list may be null and can hold any type of value.

```js
console.log(filter([2, 4, 8], function (x) { return x < 3; }));   // [2]
console.log(filter(['bunny', 'shark', 'bunny', 'lazer', 'bunny', 'piranhas'], function (animal) { return animal === 'bunny'; }));  // ['bunny', 'bunny', 'bunny']
```
