[Operators](#operators) | [Data Types](#data-types) | [Arrays](#arrays)

## Basic Syntax

A great overview of basic JS syntax can be found on [this Wikipedia page](https://en.wikipedia.org/wiki/JavaScript_syntax).

## Operators

[Unary](#unary) | [Arithmetic](#arithmetic) | [Assignment](#assignment) | [Comparison](#comparison) | [Logical](#logical) | [Relational](#relationsal)

Lots of detailed operand information can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators).

### Unary

[Unary operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Unary_operators) require only one operand, which can come before or after the operator.

```
operator operand

// or

operand operator

// example

x++
++x
```

#### typeof

The [typeof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof) operator returns a value that indicates the type of the operand.

```
typeof operand

// or

typeof (operand)
```

```js
typeof (5 + 2)	// returns "number"
typeof "javascript"  // returns "string"
```

### Arithmetic

[Arithmetic operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Arithmetic_operators) in JS take numerical values (which can also be variables) as operands and returns a single mathematical result.

- Addition (+)
- Subtraction (-)
- Multiplication (*)
- Division (/)

There are also a few special JS arithmetic operators.

- Modulus / Remainder (%) - This will return the remainder after dividing operand 1 by operand 2. This is useful for determining if a number is odd or even.

```js
x = 4 % 2	// x = 0
y = 5 % 2	// y = 1
```

- Increment / Decrement (++ | --) - These operators are used to increment or derement an integer by 1. This operator is also considered a unary operator.

```js
x = 1
x++		// x = 2
x++		// x = 3
```

### Assignment

The [assignment operator](#https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators) assigns the value of the right operand to the left operand.

```
operand operator operand
```

```js
x = "javascript"

console.log(x) 	// returns "javascript"
```

Mathematical assignment and incrementing can happen through a number of shorthand operators. For example:

```js
// traditional version
x = x + y

// shorthand version
x += y
```

The above syntax can be used in conjunction with all mathematical operators (`-`, `*`, `/`, `%`). These can also be considered unary operators.

### Comparison

[Comparison operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators) will compare the operands and return a binary value as a result of the comparison.

#### Equal

- Equal (==) - returns true if the operands are equal. It's important to note that this operator will convert the operands if they are not of the same type. Once the operands have been converted, the double equal will apply strict comparison. In general, this comparison operator is frowned upon except in a few edge cases in order to encourage stricter type comparisons. For detailed information on the algorithm used for this comparison, see the [ECMAScript specification](http://www.ecma-international.org/ecma-262/5.1/#sec-11.9.3).

```js
9 == '9'	// returns true

x = 4
y = '4'

x == y		// returns true
```

- Not Equal (!=) - returns true if the operands are not equal. This will also attempt to convert the operands if they are not of the same type. This method of type conversion for comparison is also frowned upon in most cases.

```js
9 != '8'	// returns true
9 != '9'	// returns false

x = 4
y = (3 + 2)

x != y		// returns true
```

- Strict Equal (===) - will only return true if the operands are strictly equal with no type conversion. This is the suggested method of comparison.

```js
9 === 9		// returns true
9 === '9'	// returns false
```

- Strict Not Equal (!===) - will only return true if the operands are strictly not equal with no type conversion. Thi sis the suggested method of comparison.

```js
9 !== 9		// returns false
9 !== '9'	// returns true
```

#### Inequalities

In addition to the above arithmetic operators, JavaScript also offers inequalities in the form of greater than (>), greater than or equal to (>=), less than (<) and less than or equal to (<=).

```js
5 > 3	 	// returns true
3 < 5		// returns true
3 >= 3		// returns true
4 <= 4		// returns true
```

Similar to the equality operator (==), inequalities prescribe to certain type conversion rules when operands of different types are being compared.

- If the operands are numbers, perform a numeric comparison
- If the operands are strings, compare the character codes of each corresponding character in the string
- If the one operand is a number, convert the other oprand to a numebr and perform a numeric comparison
- If an operand is a Boolean, convert it to a number (1 or 0) and perform a comparison

It's important to note that when comparing two strings, the comparison is not done based on the alphabetical placement. In these cases, the character codes are compared. This can be a problem when the strings compare uppercase characters, as all uppercase characters have a lower character code than their lowercase counterparts.

Example:

```js
"Dog" > "cat"	// returns false
```

The character code for "D" is 68, while the character code for "c" is 99. In cases such as this, it's best practice to convert strings to the same case. This can be done with the [`.toLowerCase()` method of the String object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase).

```js
"Dog".toLowerCase() > "cat".toLowerCase() 	// returns true
```

### Logical

[Logical operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators) can be used in a few scenarios:

- to string together multiple Boolean statements
- to return a specific value if a condition is not met (only applicable to && and ||)

#### Logical NOT

[The logical NOT operator (!)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators) always returns a Boolean value and can be applied to any value. The NOT operator first converts the operand to a Boolean value and then negates it, and thus behaves:

- If the operand is an object, returns false.
- If the operand is an empty string, returns true.
- If the operand is a nonempty string, returns false.
- If the operand is the number 0, returns true.
- If the operand is any number other than 0, returns false.
- If the oeprand is null, returns true.
- If the operand is NaN, returns true.
- If the opernad is undefined, returns true.

```js
var obj = { 'greeting': 'howdy' };

console.log(!obj);			// returns false
console.log(!"");			// returns true
console.log(!"foo");		// returns false
console.log(!0);			// returns true
console.log(!7);			// returns false
console.log(!null);			// returns true
console.log(!NaN);			// returns true
console.log(!undefined);	// returns true
```

Additionally, it's also possible to convert a value into its Boolean equivalent using two NOT operators in a row. This will simulate the behavior of [Boolean()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean). The second NOT essentially negates the first Boolean value and evaluates the variable.

```js
console.log(!"foo");			// returns false
console.log(!!"foo");			// returns true
console.log(Boolean("foo"));	// returns true
```

The first example can be read as: "foo" is NOT a string, which evaluates to false because "foo" is a string. The second example states that "foo" is NOT  string, and then essentially inverts the Boolean value.

#### Logical AND

[The logical AND operator (&&)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators) is applied to two values and behaves in the following way:

| Operand 1	| Operand 2	| Result 	|
|:---------:|:---------:|:---------:|
| true		| true 		| true		|
| true	 	| false 	| false		|
| false 	| true		| false		|
| false		| false		| false 	|

As the above table illustrates, the any expression using the && operator evaluates to true only when both operands are also evaluated as true.

If one of the operands is not a primitive Boolean, then the && operator will behave in the following ways:

- If the first operand is an object, then the second operand is returned.
- If the second operand is an object, then the object is returned only if the first operand evaluates to true.
- If both operands are objects, then the second operand is returned.
- If either operand is null, then null is returned.
- If either operand is NaN, then NaN is returned.
- If either operand is undefined, then undefined is returned.

It's important to note that if the first operand of the logical && expression evaluates as false, the second operand is never evaluated. This occurs because JavaScript will assume that if the first value is false, then there is no reason to evaluate the second operand.

```js
var foo = true;

var result = (foo && bar);		// error thrown
console.log(result);
```

In the above, an error is thrown because the first part of the expression is evaluated as true, and `bar` is an undefined variable in the second part of the expression. However, if `foo` is changed to false, then the second part of the expression will not be evaluated and no error will be thrown.

```js
var foo = false;

var result = (foo && bar);		// no error
console.log(result);			// returns false
```

#### Logical OR

[The logical OR operator (||)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators) behaves as such:

| Operand 1	| Operand 2	| Result 	|
|:---------:|:---------:|:---------:|
| true		| true 		| true		|
| true	 	| false 	| true		|
| false 	| true		| true		|
| false		| false		| false 	|

Similar to the logical AND, if either of the operators is not a primitive Boolean, logical OR will do one of the following:

- If the first oeprand is an object, return first operand.
- If the first operand evaluates to false, return second operand.
- If both operands are objects, return first operand.
- If both operands are null, return null.
- If both operands are NaN, return NaN.
- If both operands are undefined, return undefined.

Also like the logical AND operator, if the first operand evaluates to true, then the second operand is not evaluated.

One of the most common uses for the logical OR operator is to prevent assigning a null or undefined value to a variable.

```js
var foo = bar || baz;
```

In the above example, if `bar` is unassigned or undefined, then `baz` is used as a backup variable / object.

### Relational

#### in

[The `in` relational operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/in) will return true if the specified property is located within the specified object.

Example:
```js
var names = ["John", "Sam", "Blake", "Mike"];

0 in names		// returns true
4 in names		// returns false


"PI" in Math	// returns true
```

#### instanceof

[The `instanceof` operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/instanceof) will return true if the specified object is of a specific type.

```js
var names = ["John", "Sam", "Blake", "Mike"];

names instanceof Array		//returns true
```

### Primitive Data Types

There are 6 primitive data types in JS:

- Undefined
- Null
- Boolean
- Number
- String

All primitive data types are immutable (cannot be changed).

#### Undefined Data Type

The Undefined data type has a single value: [`undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined). When a variable is first declared, but not assigned a value it is assigned the value of undefined by default.

```js
var foo;

typeof foo;		// returns "undefined"
```
The Undefined type was added to ECMAScript to help differentiate between an empty object (`null`) and an uninitialized variable. It's best practice to NOT set variable values as undefined or use undefined as the name of a variable. It is also advisable to always initialize variables (i.e. assign a value); doing so helps to identify variables that have not been declared vs variable sthat have simply not been initialized.

#### Null Data Type

The Null data type also has a single value: [`null`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null). The `null` value represents an empty object pointer. When finding the `typeof` a variable assigned the `null` value, it will return "object".

```js
var foo = null;

typeof null;	// returns "object"
```

It's considered best practice to define a variable that will later hold an object as null rather than `{ }`.

#### Boolean Data Type

The Boolean data Type has two literal values: `true` and `false`. It's important to note that these are not the same as the numeric values 1 and 0.

```js
1 === foo;	// returns false
```

Every data type in JavaScript can be converted into to a Boolean using the `Boolean()` casting function. The rules for the output vary by data type:

| Data Type		| Converts to True	| Converts to False	|
|:---------:	|:---------:		|:---------:		|
| Boolean		| `true` 			| `false`			|
| String	 	| Non-empty string 	| Empty String ("")	|
| Number 		| Non-zero number	| 0, NaN			|
| Object		| Any object		| null			 	|
| Undefined		| n/a				| undefined		 	|

This type of conversion allows for use of different data types within conditional statements.

```js
var foo = "bar";		// setting foo to non-empty string

if (foo) {				// foo evaluates to true
	alert("Success!");
}
```

#### Number Data Type

The number data type supports both integers (literals) and [floating-point numbers](https://en.wikipedia.org/wiki/Floating_point). In addition, there are 3 special values: +Infinity, -Infinity and NaN (not-a-number).

```js
var intNum = 10;		// integer
var floatNum = 1.49; 	// floating-point
```

Floating-point numbers use up twice as much space as integers. If a number is defined without a number after the decimal, or is equal to ##.0, JavaScript will convert that number to an integer in an effort to save space.

```js
var floatNum = 1.;		// interpreted as integer 1
var floatNum2 = 9.0;	// interpreted as integer 9
```

The presence of floating-point numbers makes addition and verification of decimals rather difficult. Consider this example:

```js
var a = 0.1;
var b = 0.2;

((a + b) === 0.3);		// false
a + b;					// 0.30000000000000004
```

It is important to note that this is a result of the way arithmatetic is handled in [IEEE-754 numbers](https://en.wikipedia.org/wiki/IEEE_floating_point), and isn't an issue or bug unique to ECMAScript. This issue exists within other languages that use the same number system.

Infinity is represented as any value greater than the value stored in the `Number.MAX_VALUE` property. Any result which returns positive or negative Infinity cannot be used in further calculations.

NaN (not-a-number) is used to represent the result of any calculathion which has failed to return a valid number. This typically occurs when trying to divide by 0.

```js
10 / 0;		// returns NaN
```

The NaN value has a few unique properties:

- Any operation containing NaN will return NaN as a result (i.e `NaN / 3` will return `NaN`).
- NaN is not equal to any value (`NaN == NaN` returns `false`).

JavaScript provides a method to determine if a value is not a number: `isNaN()`. This method accepts a single argument of any data type, and will attempt to convert it to a number if it is not already. Any value that cannot be converted to a number will return a value of `true`.

```js
isNaN(NaN);		// true
isNaN(27);		// false - 27 is a number
isNaN("27");	// false - can be converted to 27
isNaN("foo");	// true - cannot be converted
isNaN(true);	// false - can be converted to 1
```

JavaScript has 3 important functions that can be used to convert nonnumeric values into numbers:

- Number()
- parseInt()
- parseFloat()

`Number()` can be used on any data type, while `parseInt()` and `parseFloat()` are used for strings exclusively. Each of these functions converts passed values in different ways.

`Number()` converts as follows:

- If Boolean, `true` gets converted to 1 and `false` gets converted to 0
- If number, the value passed to the function is returned
- If `null`, returns 0
- If `undedfined`, returns `NaN`
- If string:
	- If string contains only numbers, value is converted to a number and returned (i.e. `"123"` would return `123`). The same is true for a floating point number (i.e. `"1.1"` returns `1.1`). Note that any leading zeroes will be removed.
	- If the string is empty (`""`), returns 0
	- If it contains a value other than any of the above, returns `NaN`
- If object:
	- `valueOf()` method is called and attempts to convert value into a number
	- If previous step is unsuccessful, `toString()` method is called and the rules for strings are applied

```js
var a = Number("foo");		// NaN
var b = Number("");			// 0
var c = Number("0017");		// 17
var d = Number(true);		// 1
```

Traditionally, the `parseInt()` method is a better option for integers. It performs the following operations:

- Leading white space is ignored
- If the first character of the string is not a number, `+` or `-` then `NaN` is retruend. This is a more accurate representation than `Number()`, which would return a 0 in the same scenario.
- The conversion continues to parse the string until a non-numeric value is found. Any remaining non-numeric vlaues are ignored. Similarly, decimal values are ignored.

```js
var a = parseInt("37red");		// 37
var b = parseInt("");			// NaN
var c = parseInt(37.9);			// 37
```

`parseFloat()` works similar to `parseInt()`, with the exception that the decimal is a valid character.

```js
var a = parseFloat("37red");	// 37
var b = parseFloat("37.9");		// 37.9
var c = parseFloat("31.3.4");	// 31.3
```

#### String Data Type

[The String data type](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures) is used to store textual data. Text can be delineated using either single (`''`) or double (`""`) quotes. Note that the beginning and end of the string must use the same type of quote. There is no difference between the two types, as it is a matter of preference.

```js
var name1 = "Blake";
var name2 = 'Blake';
```

The string data type also contains several literals that can be used to represent commonly used characters:

| Literal	| Meaning			|
|:---------:|:---------:		|
| \n		| New line 			|
| \t		| Tab			 	|
| \b 		| Backspace			|
| \r		| Carriage return	|
| \\		| Backslash			|
| \'		| Single quote		|
| \"		| Double quote		|

It's important to note that strings are an immutable data structure. Once a string is created, the value cannot change unless the original string is destroyed and the variable is filled with a new string value.

Values can be a converted to a string value using the `toString()` method, which will return the string equivalent of the value.

```js
var age = 32;
var stringAge = age.toString();		// converts to "32"
```

The `toString()` method is available for strings, Booleans, objects and numbers.

If the value being converted could potentially be either `undefined` or `null`, then it's advised to use the `String()` casting function. This method will:

- If the value has a `toString()` method, it will be used and the default value will be returned
- If the value is `null`, "null" is returned
- If the value is `undefined`, "undefined" is returned

### Complex Data Types

There is a single complex data type in JavaScript: [Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects). Objects are mutable (can be changed), and are a key component of JavaScript.

### Object Data Type

JavaScript objects are lists of non-specific data. Objects can be created via the constructor function using the keyword `new` or using the object literal notation. An object is a data structure which consists of properties and values. The value of a property can be a function (known as a method), or another data type (String, Array, Object, etc).

```js
var Person1 = new Object();		// constructor

var Person2 = {};				// object literal
```

Data within objects is stored as a series of key-value pairs. Functions within an object are referred to as methods.

```js
var person = {
	name: "Blake",
	greet: function greet () {
		console.log("My name is " + this.name + ".");
	}
}
```

*Object Properties*

Properties from within the object can be referenced using either dot notation or bracket notation.

Dot notation is considered best practice, but cannot be used in specfic instances:

- The property name contains a number
- The property name is a number
- The property name contains special characters such as a hyphen or space
- The property name contains a variable

In the above cases, it's required to use bracket notation.

```js
obj.foo 		// valid
obj.7 			// invalid
obj.foo7 		// invalid
obj.foo-bar 	// invalid

obj[7] 			// valid
obj['foo7'] 	// valid
obj['foo-bar'] 	// valid

var foo = 'bar';
obj.bar = 'howdy';

obj[foo] 		// 'howdy'
```

Note that reserved keywords _should not_ be used as object properties.

*Adding Properties*

Adding properties to an object is as easy as calling the name of th new property using dot or bracket notation.

```js
var obj = {};

obj.foo = 1;
obj['bar'] = 2;

console.log(obj.foo);		// 1
console.log(obj.bar);		// 2
```

*Updating Properties*

Updating a property name can be done using the same method as property creation.

```js
var obj = {
	foo: 'bar'
};

obj.foo 				// bar
obj.foo = 'baz';

obj.foo 				// baz
```

*Removing Properties*

Properties can be removed from an object using the [`delete`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete) operator.

```js
delete object.property
delete object['property']

var obj = {
	foo: 1,
	bar: 2,
	baz: 3
};

delete obj.bar;
obj.bar 				// undefined
```

Every instance of an Object has the following properties and methods via the Global Object:

- [`constructor`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) - the function that is invoked to create an object.
- [`hasOwnProperty(propertyName)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty) - indicates if the object has the provided property (not the prototype)
- [`isPrototypeOf(object)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isPrototypeOf) - determines if the object is a prototype of another object
- [`propertyIsEnumerable(propertyName)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/propertyIsEnumerable) - indicates if the provided property can be iterated over using a `for-in` statement
- [`toLocaleString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toLocaleString) - returns a string representation of the object that is appropriate for the locale of execution environment (i.e. the results are implementation dependent)
- [`toString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString) - returns a string representation of the object (the results are implementation indepedent)
- [`valueOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/valueOf) - returns a string, number or Boolean equivalent of the object.

## Arrays

JavaScript arrays are lists of non-specific data, just like Objects. Indeed, a JavaScript array is a type of object. A new array can be created using the keyword `new` or using the array literal notation.

```js
var fruit = ['apple', 'orange', undefined, 5];
var cars = new Array();
```

*Array Element*

Elements in an array are referenced using bracket notation (similar to objects). Each value is assigned a number when added to the array -- this is known as the `index`. Arrays used a zero-based index, meaning that the first element has an index of `0`.

```js
var fruit = ['apple', 'orange', 'banana'];

console.log(fruit[0]);    // apple
console.log(fruit[1]);    // orange
console.log(fruit[2]);    // banana
```

Every instance of an Array has the following properties and methods via the Global Object:

- `length` - returns a count of the number of elements within the array
- [`indexOf`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) - returns the index of the first matching element in the array
- [`isArray`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray) - returns true if value is an array
- [`pop`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) - removes last element from array and returns that element
- [`push`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) - adds an element to the end of an array
- [`reverse`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) - reverses the order of elements in the array
- [`shift`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) - removes the first element from the array and returns that element
- [`sort`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) - sorts elements in an array
- [`splice`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) - removes or adds elements to a specific spot in the array
- [`unshift`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) - adds elements to beginning of array and returns new length
- [`join`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) - concatenates elements in an array into a string
