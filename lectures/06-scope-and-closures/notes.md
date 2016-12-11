# JavaScript Scope & Closures

[Hoisting](#hoisting) | [Block Scope](#block-scope) | [Closures](#closures)

Scope is the set of rules defined around variable creation, storage and usage. This set of rules determines where the variables are stored, how long they are stored for and when said variables are available for use.

JavaScript employs lexical scoping -- variables and function scope are dependent upon where they are declared. Any function or variable that is defined outside of a function is added to the `global` (i.e. `window` in browsers) scope.

Variables and functions defined within functions are bound to the scope of the outer function. These variables and functions have access to outer variables and functions through the scope chain. Similar to the prototype chain, the compiler will continue to examine scope outside of the local variable scope until it finds a match. If no match is found, a `ReferenceError` is thrown.

```js
var a = 7;

function foo () {
	console.log(a);
}

foo();		// 7
```

In the above snippet, the `console.log` statement has access to the globally defined `a`. Consider:

```js
var a = 7;

function foo () {
	var b = 8;

	function bar () {
		console.log(a + b);
	}

	bar();
}

foo();				// 15
console.log(b);		// ReferenceError
```

In this snippet, `bar()` has access to both `a` and `b`. However, outside of `foo()`, `b` does not exist and cannot be used.

### Hoisting

A nuance of variable declaration occurs through what's known as 'hoisting'. Variables and function declarations are captured first by the compiler. This gives the illustion that they are 'pushed to the top', or 'hoisted'. Assignment by the compiler occurs after declaration.

For example, `var a = 7;` is read by the JS engine as `var a;` followed by `a = 7;`. Additionally, function declarations (`function foo () { ... }`) are hoisted, but function expressions (`var foo = function () { ... }`) are not hoisted. If there is a conflict between a hoisted function and a variable, the function takes precedence.

Note that function declarations should not be done within blocks. The behavior is unreliable and frowned upon.

### Block Scope

There is no block scope in JS similar to other programming languages (there are a few exceptions).

The only block scope exception worth mentioning is that the `catch` part of a `try...catch` block employs block-scoping.

```js
try {
	undefined();	// force error
} catch (err) {
	console.log(err);
}

console.log(err);	// ReferenceError
```

### Closures

A closure is when a function remembers the scope in which it was defined, even if the function is being executed outside its original scope.

```js
function foo () {
	var a = 7;

	function bar () {
		console.log(a);
	}

	return bar;
}

var baz = foo();

baz();		// 7
```

In the above code, because `bar` is returned within the `foo()` function, and `foo()` is instantiated and captured within the `baz` variable, the compiler will remember the scope in which `bar` was created.

Another example:

```js
var myFunction;

function foo () {
	var a = 7;

	function bar () {
		console.log(a);
	}

	myFunction = bar;
}

function baz () {
	myFunction();
}

foo();

baz();		// 7
```

The context of `bar()` is passed to the global `myFunction` variables. The `bar` function has a closure around the scope of the `foo()` function, and thus the value of `7` is logged to the console when `baz()` is called.
