# Programming Fundamentals

- Overview
  - Variables
    - What are they?
      - A placeholder that represents a value.
  - Data Types
    - What are they?
      - A classification that specifies a type of data
  - Loops
    - What are they?
      - Repeating steps until an end condition is met
  - Functions
    - What are they?
      - Sequence of instructions that perform a specific task
  - Algorithms
    - What are they?
      - A set of step-by-step instructions to perform a task

- JavaScript History
  - 1995
    - Netscape Navigator
    - Brendan Eich
      - Wrote the first version of JS in 10 days
      - Looks syntactically similar to Java
    - Shipped in Netscape 2.0 as LiveScript
  - 1996
    - Netscape submitted to Ecma International
      - ECMA
        - European Computer Manufacturers Association
        - ES6 Specification: http://www.ecma-international.org/ecma-262/6.0/
  - 1997
    - First edition of ECMAScript Standard Released

  - Subsequent Versions
    - ECMA–262 1st Edition June 1997
    - ECMA–262 2nd Edition June 1998
    - ECMA–262 3rd Edition December 1999
    - ECMA–262 5th Edition December 2009
    - ECMA–262 5.1 Edition June 2011

- Why are we learning Javascript?
  - It is the most popular and ubiquitous language in the world
  - Learning JS makes you more marketable as a developer today
  - It's fun, and provides immediate feedback

- Refresher: How to run JavaScript files using Node.js

- JavaScript Basics
  - Syntax
    - Case Sensitive
      - Standard practice to use camelCase
        - Some exceptions (constructors)
          - Will cover later
      - Use kebab-case when naming files
    - Semicolon
      - Automatic Semicolon Insertion (ASI)
        - Be explicit

  ```
  a = b + c
  (d + e).foo()    // a = b + c(d + e).foo()

  a = b + c;
  (d + e).foo();
  ```

    - Commenting code

  - Operators
    - Unary
    - Arithmetic
    - Assignment
    - Comparison
    - Logical
    - Relational

  - Debugging
    - What's a stack trace?

    ```
    try {
      throw new Error('OH NOES!');
    } catch (err) {
      console.log(err.stack);9
    }
    ```

  - Data Types
    - Primitives
      - Undefined
      - Null
      - Boolean
      - Number
      - String
    - Complex
      - Objects

  - Arrays
    - Is actually a type of object
    - Zero-based schema
    - Access properties in an array with bracket notation
