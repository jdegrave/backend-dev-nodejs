# Recursion
  - Google thinks they're funny
  - Recursion
  - Factorial
    - n! = 1 * 2 * 3 * 4 * ... * n
    - Iterative factorial
      ```js
      function factorial(n) {
        var fact = 1;

        for (var i = 2; i <= n; i++) {
          fact *= i;
        }

        return fact;
      }

      console.log(factorial(8));
      ```
    - Recursive Factorial
      ```js
      function factorial(n) {
        console.log('FACTORIAL CALLED FOR: ', n);
        if (n < 0) {
          return -1;
        }

        if (n === 0) {
          return 1;
        }

        return (n * factorial(n - 1));
      }

      console.log(factorial(8));
      ```
  - Fibonacci
    - Iterative Fibonacci
      ```js
      function fibonacci(n) {
        var a = 0;
        var b = 1;
        var f = 1;

        for(var i = 2; i <= n; i++) {
          f = a + b;
          a = b;
          b = f;
        }

        return f;
      }

      console.log(fibonacci(12));
      ```
    - Recursive Fibonacci
      ```js
      function fibonacci(n) {
        if (n <= 2) {
          return 1;
        } else {
          return fibonacci(n - 2) + fibonacci(n - 1);
        }
      }

      console.log(fibonacci(12));
      ```
    - Exercise
      - Write a function that logs a series of numbers, starting at 0 up until n.
      ```js
      function count(n) {
        if (n === 0) {
          console.log(0);
        } else {
          count(n - 1);
          console.log(n);
        }
      }

      count(9);
      ```
      - Similarly, write a function that accepts a number n and counts down from there until 0.
      ```js
      function countdown(n) {
        if (n === 0) {
          console.log(0);
        } else {
          console.log(n);
          countdown(n - 1);
        }
      }

      countdown(9);
      ```
# Unit Testing
  - What is Unit Testing?
    - A method of testing individual units of source code to determine whether or not the behavior of the code is according to spec.
  - Why Unit Test?
    * Find problems early
      - The earlier in the process problems are found, the less expensive they are to fix
    * Encourages refactoring
      - Refactoring generally encourages code quality, readability and maintainability
    * Serves as documentation
      - A new developer to your project can look at the tests as a starting point for understanding the code
    * Provides confidence in code
      - Caveat: so long as the tests are written properly and thoroughly. Invalid tests only provide false confidence.
  - Test Driven Development
    - A software development process wherein requirements are turned into very specific test cases, and then the software is written and improved upon with the goal of passing the tests.
  - Test Driven Development Process
    1. Add a test
    2. Run all current tests to see if new test fails
    3. Write the code relevant to the test
    4. Run tests
    5. Refactor code

    - Repeat for new functionality
  - Add A Test
  - Run Current Tests / New Test Fails
  - Write Code
  - Run Tests
  - Refactor Code
  - Examples and Exercises
    - Create a function takes another function as an argument and multiplies the returned value of that function by 10.
      ```js
      function aNumber () {
        return 76;
      }

      function multFunc (fn) {
        return fn() * 10;
      }

      // console.log(multFunc(aNumber));

      function testMultFunction() {
        var valueToTest;

        function testNumber() {
          return 32;
        }

        valueToTest = multFunc(testNumber);

        if (valueToTest === 320) {
          console.log('multFunc test passed');
        } else {
          console.log('multFunc test failed');
        }
      }

      testMultFunction();
      ```
