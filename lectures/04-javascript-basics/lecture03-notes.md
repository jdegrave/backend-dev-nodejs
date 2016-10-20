e[Loops](#loops) | [Functions](#functions)

## Loops

[for](#for) | [for-in](#for-in) | [#do-while](#do-while) | [while](#while)

[Loops offer a way to easily iterate over data](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration), or perform the same task repeatedly.

### for

The most common type of loop in JavaScript is the [`for` loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration#for_statement). The for loop will continue to run until a specified condition evaluates to false.

```
for (initialization; condition; post-loop-expression) statement
```

When the for loop is executed:

- The initialization expression is executed. This is typically initialization of a counter variable like `i` or `count` or `counter`.
- Next, the condition expression is evaluated. If the condition is true, the loop statement will continue. If the condition is false, then the `for` loop terminates. Note that if a condition expression is not provided, then it is interpreted as true.
- The statement executes.
- If the conditional statement was true prior to the execution of the statement, then the post-loop-expression will be executed after the statement. This is typically used o increment the counter variable in some way (i.e. `i++` or `count--`).

```js
for (var i = 1; i < 4; i++) {
	console.log(i);
}
```

The above code will log 1, 2, 3 to the console. It's important to note that everything that can be done with a `for` loop can also be done with a `while` loop.

```js
var fruits = ['apple', 'orange', 'banana'];

for (var i = 0; i < fruits.length; i++) {
	console.log(fruits[i]);
}

// apple
// orange
// banana
```

Above is an example using a `for` loop to iterate over an array and return the values within.

### for-in

[The `for-in` loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration#for...in_statement) is used to iterate over the enumerable properties in an object.

```js
for (property in object) {
	// do this
}
```

Note that the standard `for` loop should be used to iterate over arrays. It's possible to use `for-in`, but it will return both the user-defined properties and the numeric indices.

```js
var apple = {
	'color': 'red',
	'type': 'Pink Lady',
	'size': 'Medium'
};

for (properties in apple) {
	console.log(properties);
}

// color
// type
// size
```

It's important to realize that the order in which the properties are returned may vary depending on the browser.

### do-while

[The `do-while` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration#do...while_statement) allows a statement to repeat until a specified condition evaluates to false. The code within the `do` block of the code will _always_ execute once prior to checking if the condition is met.

```js
var i = 1;

do {
	console.log('do statement executes')
	i++;
} while (i < 1);


// the for statement will not log anything to the console
for (var count = 1; count < 1; count++) {
	console.log('for statement executes');
}

// do statement executes
```

In the example above, the `do-while` statement logs to the console once even though the condition specified is already met. Alternatively, the `for` loop does not log anything to the console.

### while

[The `while` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration#while_statement) will execute its statements as long as the specified condition evaluates to true. Similar to the `for` loop, the escape condition is tested before the loop is executed.

```
while (expression) statement
```

```js
var i = 1;
while (i < 4) {
	console.log(i);
	i++;
}
```

Similar to the `for` loop example, this will log 1, 2, 3 to the console before exiting.

### label

In JavaScript, it's possible to provide a [`label` for a statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration#label_statement), so that it can be referred to later in the application.

```
label: statement
```

Labeled statements are typically used within nested loops to make them more semantic.

```js
myLoop:
for (var i = 1; i < 4; i++) {
	console.log(i);
}
```

`myLoop` will now refer to the subsequent for loop anywhere in the code.

### break and continue

In conjunction with labeled statements, the `break` and `continue` statements can be used for greater control over the execution of a loop.

The `break` statement will exit the loop immediately.

```js
var num = 0;
for (var i = 1; i < 11; i++) {
	if (i % 2 === 0) {
		break;
	}
	num++;
}

console.log(num);	// 1
```

Normally, the above `num` variable would be incremented to 10 before being logged to the console. However, when the `for` loop reaches the first number divisible by 2 (2 in this case), the `for` loop is exited and the console statement is evaluated.

The `continue` statement will exit the loop immediately, but execution will continue from the beginning of the loop.

```js
var num = 0;
for (var i = 1; i < 11; i++) {
	if (i % 2 === 0) {
		continue;
	}
	num++;
}

console.log(num);	// 5
```

In the above example, each time a number is divisble by 2 (2, 4, 6, 8, 10), the code exits the currently loop before `num` is incremented and starts again.

```js
var num = 0;

myLoop:
for (var i = 1; i < 6; i++) {
	for (var j = 1; j < 6; j++) {
		if (i % 2 === 0 && j % 2 === 0) {
			break myLoop;
		}
		num++
	}
}

console.log(num);	// 6
```

The above example will iterate a total of 25 times without the conditional if statement. However, when inserting the `break`, the inside loop will exit as soon as both conditions are met, and `num` is only incremented 6 times.

Similarly, when `continue` is used in place of `break`, `num` is only incremented 17 times.

```js
var num = 0;

myLoop:
for (var i = 1; i < 6; i++) {
	for (var j = 1; j < 6; j++) {
		if (i % 2 === 0 && j % 2 === 0) {
			continue myLoop;
		}
		num++
	}
}

console.log(num);	// 6
```

## Functions

[Arguments Object](#arguments-object) | [Functions as Values](#functions-as-values)

A function in JavaScript is actually an object -- an instance of the Function type. Functions can be defined using this syntax:

```js
// Function declaration
function foo (arg1, arg2) {
	// code here...
}
```

In the above `foo` is the name of the function, `arg1` and `arg2` are arguments. Alternative syntax for creating a function:

```js
// Function expression
var foo = function (arg1, arg2) {
	// code here...
}
```

The primary difference between a function declarations and expressions is the order in which the JavaScript engine loads the execution context. For example, this code will work perfectly fine:

```js
foo();

function foo () {
	// code here...
}
```

This is because function declarations are ["hoisted"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions#Calling_functions) to the top of the execution context. This means that function declarations can be declared after the code that executes them. Conversely, a function expression is evaluated at the point in which it is defined within the code. Therefore:

```js
foo();

var function foo () {
	// code here...
}
```

The above will throw an error because `foo` is not defined.

### Arguments Object

Function arguments can be accessed within the function using the `arguments` object. The `arguments` object is what's known as an 'array-like' object. This name comes from the fact that the `arguments` have property names similar to an array (0-based index).

```js
function args (a, b) {
	console.log(arguments);
}

args('hi', 'howdy');
// ['hi', 'howdy']
// This is actually
// [
//	0: 'hi',
//	1: 'howdy'
// ]

```

However, unlike arrays the `arguments` object does not have array methods like `push()` and `pop()`. The only array method that the `arguments` object has is `length`.

```js
function args (a, b) {
  arguments.push('yo');
}

args('hi', 'howdy');		// TypeError: arguments.push is not a function

function argLen (a, b) {
	console.log(arguments.length);
}

args('hi', 'howdy');		// 2
```

Because arguments has a zero-based index property, it's possible to access arguments using bracket notation just like array elements.

```js
function args (a, b) {
	console.log(arguments[0]);
	console.log(arguments[1]);
}

args('hi', 'hello');
// 'hi'
// 'hello'
```

It's important to note that the arguments array is mutable and values can be overwritten.

```js
function args (a, b) {
	arguments[0] = 'hola';
	console.log(arguments[0]);
}

args('hi', 'hello');
// hola
```

### Functions as Values

Functions in JavaScript can be passed into other functions as arguments, but also returned from inside another function.

```js
function foo (anotherFunction, myArgument) {
	return anotherFunction(myArgument);
}
```

In the example above, the function `foo` accepts two arguments:

- a function (`anotherFunction`)
- an argument (`myArgument`) that should be passed to `anotherFunction`

A simple of this would be:

```js
function foo (anotherFunction, myArgument) {
	return anotherFunction(myArgument);
}

function tenTimes (num) {
	return num * 10;
}

var myNumber = foo(tenTimes, 10);
console.log(myNumber);		// 100
```
