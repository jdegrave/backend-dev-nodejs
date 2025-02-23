# JavaScript Scope & Closures

- What is scope?
  - Scope is the set of rules used to determine which variables a particular part of your program has access to.
  - Global scope
    - Anything created in the global namespace (i.e. `var a`)
  - Function Scope
    - Functions create their own isolated scope
    - This scope has access to the outer levels of scope, however outer levels do not have access to the inner function scope
  - Diagram
  - Examples
- IIFE
  - What is it?
    - Immediately Invoked Function Expression
    - Why?
      - Creates modules where variable names don't pollute the global namespace (i.e. we don't have variable name conflicts)
    - Syntax
- Hoisting Review
  - What is it?
    - Function declaration definitions are assigned at the beginning of the JS compilation, therefore it's possible to call (invoke) a function before it's actually defined
  - Why is it important?
    - Code organization
  - Examples
- Block Scope
  - What is it?
    - Other languages will create unique variables for "blocks" or pieces / statements of code. This isn't possible in ES5
  - Why is it important?
    - Nice to know as a comparison. Some ES6 features can create blocks similar to other languages
- Closures
  - What are they?
    - A closure is when a function remembers the scope in which it was defined, even if the function is being executed outside its original scope.
  - Why is it important?
    - Privacy / hide implementation details
    - Ability to create a module where variables do not intrude on global scope or namespace
  - Examples
  - Exercise 1
  - Exercise 2
