## Conditionals / Statements

[if-else](#if-else) | [switch]($switch) | [try-catch](#try-catch) | [throw](#throw) | [label](#label) | [break and continue](#break-and-continue)

Statements in JavaScript allow for certain events to occur based on a conditional test.

Note that the [`with` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/with) is considered a statement in JavaScript, but it is widely considered poor practice (and is not permitted at all using ES5's `use strict` syntax). Thus, it has been excluded from this section.

### if-else

[The `if` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else) provides a result that should occur when certain conditions are met.

```
if (condition) statement1 else statement2
```

The condition does not have to be a Boolean, as JavaScript will automatically cast the condition as a Boolean using `Boolean()`.

If the condition is true, then statement1 is executed. If the condition evaluates to false, then statement2 is executed.

It's possible to not include a false statement, and to chain `if` statements if needed.

```js
var x = 2;

if (x < 4) {
	console.log('true');
} else {
	console.log('false');
}

// above statement would evaluate to true

var y = 5;

if (y < 4) {
	console.log('true');
} else {
	console.log('false');
}

// above statement would evaluate to false

var z = 10;

if (z < 10) {
	console.log('less than 10');
} else if (z > 10) {
	console.log('greater than 10')
} else {
	console.log('equal to 10')
}

// above would evaluate to 'equal to 10'
```

Note that it's possible to put the entire statement on a single line, and even forego the brackets. This is generally frowned upon.

```js
// valid, but not recommended:
if (true) { console.log('true'); }

// valid, but not recommended:
if (true)
	console.log('true');
else
	console.log('false');
```

### switch

[The `switch` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch) is a close relative of the `if` statement. This statement allows specification of several types of input and each corresponding result.

```js
switch (expression) {
	case case_value: statement;
		break;
	case case_value: statement;
		break;
	case case_value: statement;
		break;
	default: statement;
		break;
}
```

If the evaluated expression is equal to one of the case_values, then the corresponding statement will be executed. The `break` keyword causes the code to exit the switch statement without further evaluation. This is required following each statement.

The `default` case value specifies what should happen when none of the previous case_values are provided as input.

```js
// example if statement
if (x === 25) {
	console.log('25');
} else if (x === 17) {
	console.log('17');
} else if (x === 9) {
	console.log('9');
} else {
	console.log('other value');
}

// equivalent switch statement
switch (x) {
	case 25:
		console.log('25');
		break;
	case 17:
		console.log('17');
		break;
	case 9:
		console.log('9');
		break;
	default:
		console.log('other value');
}
```

Note that it's not required for the case value to be a constant. Strings such as (`"first name" + " last name"` can be used in addition to constants). Additionally, it's important to realize that the comparison of the values uses the strict equal (`===`), so no type coercion occurs.

### try-catch

[The `try-catch` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) in JavaScript is used for error handling and testing. It specifies a piece of code to try and a subsequent block that is executed if an exception is thrown.

```js
try {
	// potential error code
} catch (error) {
	// do this if error occurs
}
```

If an error occurs during the `try` block, execution immediately halts and the object containing the error is passed to the catch portion of the code. This error object varies by browser, but at a minimum contains a `name` specifying the type of error and a `message` that contains the actual error message.

```js
try {
	foo();
} catch (error) {
	alert(error.message);
}
```

It's also possible to include a `finally` clause at the end of a `try-catch` statement. The `finally` clause will always be executed, both if an error is thrown and if it is not thrown. This can be used in conjuction with a `catch` block, or without it.

```js
try {
	// potential error code
} catch (error) {
	// do this if error occurs
} finally {
	// do this no matter what
}
```

It's important to note that if a `finally` clause is included, any `return` statements as part of the `try` or `catch` blocks will be ignored.

### throw

[The `throw` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw) throws a user-defined exception. Any statements which occur after the `throw` statement is executed will not be executed. This is most typically used with error-handling.

If a catch block exists within the call stack, control will be passed to that block. If no catch block is present, the program will terminate.

```js
// syntax
throw exception

// example
if (err) {
	throw new Error('Error message here');
}
```
