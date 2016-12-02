# JavaScript `this` and Regular Expressions

[this](#this) | [regex](#regex)

## This

[Default Binding](#default-binding) | [Implicit Binding](#implicit-binding) | [Explicit Binding](#explicit-binding) | [Constructor Binding](#constructor-binding) | [Practical Examples](#practical-examples)

The context of the `this` keyword is based on where the function is called, not where it is declared. The order in which functions are called is also referred to as the call-stack.

The call-stack can be viewed in modern browser dev tools by inserting a `debugger;` break point in a function. In Chrome, the function call list is descending order.

An example of the call-stack:

```js
function foo () {
	bar();	// call stack is Global >> foo() >> bar()
}

foo();		// call stack is Global >> foo()
```

There are 4 rules which determine what `this` will refer to when a function is executed.

The order in which the rules take precedence over each other when multiple apply are:

1. Constructor Binding
2. Explicit Binding
3. Implicit Binding
4. Default Binding

### Default Binding

If a function call occurs as an undecorated function reference, then `this` will refer to the global object. If the contents of the function are defined in `strict mode`, then `this` will be `undefined` and produce a TypeError.

```js
function foo () {
	this.bar = 'baz';
}

foo();
console.log(window.bar);	// 'baz'
```

### Implicit Binding

This rule specifies that if the function call-site has a context object, then this will refer to that object.

```js
function foo () {
	console.log(this.bar);
}

var baz = {
	bar: 'howdy',
	foo: foo
};

baz.foo();		// howdy
foo();			// undefined
```

It's important to note that in the snippet above, the first call to `foo()` is preceded by the `baz` reference object where `foo()` is a method. In this instance, `baz` is the containing / owning object and `this` will reference `baz`. `this.bar` could also be thought of as `baz.bar`.

### Explicit Binding

Explicit binding allows for forcing a function call to use a particular object for `this.` This can be done through the `call()` and `apply()` function methods.

For both of these methods, the first argument is an object to use for `this`. Consider:

```js
function foo () {
	console.log(this.bar);
}

var baz = {
	bar: 'howdy'
}

foo.call(baz);
```

`foo.call` specifies that the `baz` object should be used for the `this` reference.

Passing `null` or `undefined` as a `this` parameter to `call`, `apply` or `bind` causes `this` to be ignored.

It's possible for a bound `this` value to "lose" its binding, and the most common occurrence of this is related to callback functions. However, there is an explicit binding pattern to circumvent this issue:

```js
function foo () {
    console.log(this.a);
}

var obj = {
    a: 2
}

var bar = function () {
    foo.call(obj);
};

bar();  // 2
setTimeout(bar, 100);  // 2
bar.call(window);  // 2
```

`bar()` explicitly binds `this` in `foo` to `obj`, and as seen via the `bar.call(window);` and `setTimeout()` functions above cannot be overridden.

This type of binding is so common that there is a JS method called `bind` which will take an object to use as the `this` reference.

```js
// syntax
function.bind(object);

// example
function foo (arg) {
	console.log(this.a, arg);
	return this.a + arg;
}

var obj = {
	a: 2
};

var bar = foo.bind(obj);

var b = bar(9);		// 2 9
console.log(b);		// 11

// simplified version of a bind method
function bind (fn, obj) {
	return function () {
		return fn.apply(obj, arguments);
	}
}
```

### Constructor Binding

The final rule concerns constructor calls of functions. When the `new` keyword is used to call a function, `this` is bound to the newly constructed object.

```js
function foo (bar) {
	this.bar = bar;
}

var baz = new foo('howdy');
console.log(baz.bar);		// howdy
```

### Practical Examples

*Configuration of an API Service*

```js
function myService () {
  return {
    logger: null,
    data: [],
    configure: function (logger, data) {
      this.logger = logger;
      this.data = data;
    },
    log: function (val) {
      this.logger.log(val);
    }
  };
}

var service = myService();
// console.log(service);
// service.log('Hello!');
service.configure(console, [1, 2, 3, 4]);
// service.log('Hello!');
// service.log(service.data);

function logTheData () {
  console.log(this.data);
}

var otherService = {
  data: ['a', 'b', 'c', 'd']
};

logTheData.call(service);
logTheData.call(otherService);
```

*Method Chaining*

```js
function createResponse () {
  return {
    statusCode: null,
    status: function (code) {
      this.statusCode = code;
      return this;
    },
    json: function (res) {
      return this.statusCode + ' ' + res;
    }
  };
}

var response = createResponse();

console.log(response.status(200).json('it worked!'));
```

## RegEx

[Search](#search) | [Replace](#replace)

[Regular expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) (regex) are patterns used to find specific character combinations in strings. Regular expression have several [special characters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions#Using_special_characters) that are used to match to specific circumstances.

A regular expression is encased in two `/` characters. For example: `/a/` would be a regex matching the lowercase `a`. After the closing `/`, it's possible to add option flags to modify the match conditions. The two most common are `g`, which will find all characters in the string which match the regular expression (the default will only return the first match), and `i` (case `i`nsensitive) which will return matches regardless of character case.

### Search

There are a few different ways to search a string to and test for a regular expression value.

The `String` object has a method named [`search`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/search). This method takes a regular expression as an argument and returns the index of the first matching value. If the value is not found, the function returns `-1`.

```js
var myRegex = /p./g;
var fruit = 'aaaapples';

fruit.search(myRegex);	// 4
```

The `RegExp` object method [`test`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test) performs a similar function as search. However, this method will return a boolean value.

```js
var myRegex = /p./g;
var fruit = 'aaaapples';
var sleep = 'zzzzz';

myRegex.test(fruit);	// true
myRegex.test(sleep);	// false
```

If more information is required, then there are two additional options:

```js
var myRegex = /p./g;
var fruit = 'aaaapples';

myRegex.exec(fruit);
// returns ['pp'1, index: 4, input: 'aaaapples']

fruit = 'aaaapples and pppears';
fruit.match(myRegex);
// returns ['pp', 'pp', 'pe'];
```

The [`exec`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/exec) Regex method will return an array with additional information based on the successful match. If no match is found, the method returns `null`. The array returned from a positive match follows this format:

```js
['matched characters', 'substring matches', 0-based index of match, original string]
```

String's [`match`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match) method will return an array with all matched results. If no results are found, then `null` is returned.

### Replace

In order to replace a part of a string, the [`String.replace()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace) method can be used. This function takes 2 arguments:

1. A regular expression or substring to match
2. The string to replace any matched text, or a [function to be invoked](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace#Specifying_a_function_as_a_parameter)

```js
var myRegex = /p/g;
var fruit = 'aaaapples pppears';

fruit.replace(myRegex, 'z');
// aaaazzles zzzears
```
