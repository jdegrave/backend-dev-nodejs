# Terminology

## Inheritance
  - Objects gaining access to properties (data) and methods (functions) on another object
  - Method: class/object function

## Method
  - A function that is specifically a part of a class (classical inheritance) or as a property on an object (prototypal inheritance)

### Classical Inheritance
  - C++ examples of class and instances
  - Property/Method exercise with video code

### Prototypal Inheritance
  - Prototype
  - Prototypal Inheritance
  - Prototype Chain
  - Draw graph, then myObj code to demonstrate properties, then person code to demonstrate methods
    - Don't manually assign proto like we do in these demos - it is a very slow operation in every browser and JavaScript engine
    ```js
    var myProtoObj = {
      b: 3,
      c: 4
    }

    var myObj = Object.create(myProtoObj);
    myObj.a = 1;
    myObj.b = 2;

    // prototype chain
    // myObj -> myOtherObj -> Object.prototype -> null

    // a is an own property on myObj, this will log 1
    console.log(myObj.a);

    // b is an own property on myObj, this will log 2
    console.log(myObj.b);

    // b is an own property on myObj, this will log 2
    console.log(myObj.__proto__.b);

    // c is not an own property on myObj, JavaScript will look up the prototype chain to myOtherObj and find the c property, this will log 4
    console.log(myObj.c);

    // d is not an own property on my Obj, JavaScript will look up to the prototype chain to myOtherObj, to Object.prototype and then to null and will not find d, this will be undefined
    console.log(myObj.d);
    ```

    ```js
    // Initial setup
    var person = {
      firstname: 'Default',
      lastname: 'Default',
      getFullName: function() {
        return this.firstname + ' ' + this.lastname;
      }
    };

    var john = Object.create(person);
    john.firstname = 'John';
    john.lastname = 'Doe';

    // this gives an error - demo error



    console.log(john.getFullName());

    // Second demo
    var jane = new Object(person);
    jane.firstname = 'Jane';

    console.log(jane.getFullName());
    ```


# Everything Is An Object
  - Objects
  - Functions
  - Methods
  - Object.prototype
  - Viewing Prototype Information (need html file)
    ```js
    var person = {
      firstname: 'Default',
      lastname: 'Default',
      getFullName: function() {
        return this.firstname + ' ' + this.lastname;
      }
    };


    console.log('PERSON: ');
    console.log(person);
    console.log('PERSON PROTOTYPE: ');
    console.log(person.__proto__);
    console.log('PERSON PROTOTYPE ES6 STYLE: ');
    console.log(Object.getPrototypeOf(person));
    ```
  - hasOwnProperty()
    ```js
    var myProtoObj = {
      b: 3,
      c: 4
    }

    var myObj = Object.create(myProtoObj);
    myObj.a = 1;
    myObj.b = 2;

    console.log(myObj.a);
    console.log(myObj.hasOwnProperty('a'));
    console.log(myObj.c);
    console.log(myObj.hasOwnProperty('c'));
    console.log(myObj.valueOf());
    console.log(myObj.hasOwnProperty('valueOf'));
    ```
  - Modifying the Prototype
    - Called 'monkey patching', breaks encapsulation and should be avoided
    - The only good reason for extending a built-in prototype is to backport the features of newer JavaScript engines; for example Array.forEach, etc.
    ```js
    if (typeof String.prototype.trim === 'undefined') {
      String.prototype.trim = function() {
        return this.replace(/^\s+|\s+$/g, '');
      };
    }
    ```
    ```js
    Number.prototype.isPositive = function() {
      return (this > 0);
    };
    ```
  - Prototype Exercise
    - Modify code we've written earlier that accepts a specific data type as an argument and returns some value about that argument to be methods on the prototype.
    - Some problems like this are:
      - Lecture 4 Exercise 1
      - Lecture 4 Exercise 2
      - Lecture 6 Exercise 1
      - Lecture 6 Exercise 2
      - Lecture 7 Exercise 2
      - Lecture 7 Exercise 5
      - Lecture 8 Exercise 1
  - Prototype Information on MDN
    - Object
     - Methods with the warning sign next to them probably shouldn't be used frequently if at all. They're foundational aspects of the language.
        - For developing JavaScript, not necessarily for developing in JavaScript
    - Function
    - String
    - Array
    - Number
  - Performance Concerns
    - access via __proto__ is very expensive

# Practical Examples
  - Basic Example
    - Notice the capital letter in Rocket. Convention that communicates that this is a prototype, an abstract representation of the structure I am creating.
    - After demo, have students come up with their own simple prototype
    ```js
    function Rocket () {

    }

    Rocket.prototype.thrusters = 4;

    var myRocket = new Rocket();
    console.log(myRocket);
    console.log(myRocket.thrusters); // 4
    ```
  - Basic Example With Arguments: Person
    - Notice the use of this when using arguments, both in terms of the prototype's properties and methods.
    - After demo, have students come up with their own simple prototype
    ```js
    function Person(name) {
      this.name = name;
    }

    Person.prototype.greet = function(otherName) {
      return 'Hi ' + otherName + ', my name is ' + this.name;
    }

    var samantha = new Person('Samantha James');
    console.log(samantha.greet('Justin'));
    ```
    - instanceof
      - Tests whether an object has in its prototype chain the prototype property of a constructor.
      ```js
      function MyProto() {

      }

      function MyOtherProto() {

      }

      var myObj = new MyProto();
      var myOtherObj = new MyOtherProto();

      console.log(myObj instanceof MyProto);
      console.log(myObj instanceof MyOtherProto);
      console.log(myOtherObj instanceof MyProto);
      console.log(myOtherObj instanceof MyOtherProto);
      ```
  - Create Hierarchy
    - How To
      ```js
      function Person() {
        this.name = '';
      }

      function Child() {
        Person.call(this);
        this.gradeInSchool = '';
      }

      Child.prototype = Object.create(Person.prototype);

      var jenny = new Child();
      console.log(jenny);
      ```
    - Employee
      - Again, we're using capitalization to communicate that we're creating an abstract representation
      ```js
      function Employee(name, idNumber, department) {
        this.name = name;
        this.idNumber = idNumber;
        this.department = department;
      }

      var samantha = new Employee('Samantha Jones', '123', 'Technology');
      console.log(samantha);
      ```
        - Manager
          ```js
          function Manager(name, idNumber, department, reports) {
            Employee.call(this, name, idNumber, department);
            this.reports = reports;
          }
          Manager.prototype = new Employee;

          var samantha = new Manager('Samantha Jones', 123, 'Technology', [234, 345, 456, 567, 678]);
          console.log(samantha);
          ```
        - Worker
          ```js
          function Worker(name, idNumber, department, projects) {
            Employee.call(this, name, idNumber, department);
            this.projects = projects;
          }
          Worker.prototype = new Employee;

          var jennifer = new Worker('Jennifer Smith', 234, 'Technology', ['X467', 'T908']);
          console.log(jennifer);
          ```
          - Engineer
            ```js
            function Engineer(name, idNumber, department, projects, specialty) {
              Worker.call(this, name, idNumber, department, projects);
              this.specialty = specialty;
            }
            Engineer.prototype = new Worker;

            var jennifer = new Engineer('Jennifer Smith', 234, 'Technology', ['X467', 'T908'], 'mechanical');
            console.log(jennifer);
            ```
          - Sales
            ```js
            function Sales(name, idNumber, department, projects, quota) {
              Worker.call(this, name, idNumber, department, projects);
              this.quota = quota;
            }
            Sales.prototype = new Worker;

            var jeff = new Sales('Jeff Brown', 987, 'Sales', ['X467', 'C867'], 4);
            console.log(jeff);
            ```
            ```js
            console.log('Caroline Engineer :' + (caroline instanceof Engineer));
            console.log('Caroline Worker :' + (caroline instanceof Worker));
            console.log('Caroline Employee :' + (caroline instanceof Employee));
            console.log('Jeff Sales :' + (jeff instanceof Sales));
            console.log('Jeff Engineer :' + (jeff instanceof Engineer));
            console.log('Jeff Worker :' + (jeff instanceof Worker));
            console.log('Jeff Employee :' + (jeff instanceof Employee));
            ```
          - Add an EngineeringIntern subclass to Engineer that includes a new property, mentor, to the class
            ```js
            function EngineeringIntern(name, idNumber, department, projects, specialty, mentor) {
              Engineer.call(this, name, idNumber, department, projects, specialty);
              this.mentor = mentor;
            }
            EngineeringIntern.prototype = new Engineer;

            var carlos = new EngineeringIntern('Carlos Mendez', 345, 'Technology', ['X467', 'T908'], 'mechanical', 234);
            console.log(carlos);
            ```
          - Add a function that all objects created in this prototype chain can access
            ```js
            Employee.prototype.getIdNumber = function() {
              return this.idNumber;
            }
            ```
          - Add a function that only Engineers and Engineering Interns can access
            ```js
            Engineer.prototype.getSpecialty = function() {
              return this.specialty;
            }
            ```
  - Create Hierarchy On Your Own
    - Track side length(s), calculate area
    - Shape
      - Rectangle
      - Triangle
      - Square
      - Circle
      - Pentagon
