Before beginning, create a directory named `all-together` and enter that directory from the command line. All exercises below should be done within this working directory.

# Exercise 1

We live in a future where we have the ability to build our own cars using JavaScript (hey - it could happen). Your task is to create a blueprint for a car, and then produce two cars from that blueprint. Your task:

  - Create a folder named `js-cars` from the command line
  - Initialize the `js-cars` folder as a git repository
  - Create a file named `blueprint.js` from the command line
    - In this file, create a car blueprint. Your car should have:
      - Between 0 - 6 wheels
      - A top speed
      - A color
      - A function to report how long this car would take to travel 1/4 mile at top speed
    - Within this same file, create two different versions of cars based on this blueprint
    - Within the same file, write a function that tests that each of your built cars works as intended
      This function should return `true` if everything is as expected, and `false` if not
  - Commit and push all changes to a new GitHub repository from the command line

# Exercise 2

Secrets are bad. Unless they're good. JavaScript secrets are always good.

- Create new folder in `all-together` named `secret-module`
- Initialize the `secret-module` folder as a git repository
- Create a file named `module.js` from the command line
- In this file, create a module named `superSecret`
  - This module should contain:
    - This module should store a secret phrase
      - This phrase can be anything you want it to be
      - This phrase should not be accessible from outside the function
    - This module should also have a function named `shareSecret` that takes the secret phrase and applies the Roman Cipher to it, then reverses it and logs it to the console
  - Within this same file, create a function that tests that the secret phrase cannot be accessed outside the function
    - It should return `true` if it cannot access the function and `false` otherwise
  - Create another function within this file that tests that the output when running the module's `shareSecret` method
- Commit and push all changes to a new GitHub repository from the command line

# Exercise 3

The New York Times has hired you to gather metrics about their website. $$ BIG PAYDAY, YES! $$

- Create new folder in `all-together` named `scraping-html`
- Initialize the `scraping-html` folder as a git repository
- Create new file named `html-scrape.js` from the command line
- In this file, create a function that will take in a string of HTML and output the number of `<div>` elements in the file
- In this file, create a function that will take in a string of HTML and output the total number of html elements in the file
  - Note that an HTML element is anything between `<` and `>` symbol. For example `<div></div>` is one element which has an opening and closing HTML tag.
- In this file, create a function that will take in a string of HTML and output the number of times `New York` is referenced in the file (hyperlinks do not count)
- Within this same file, create a function that tests each of the above output scenarios and outputs `true` where the function is successful and false otherwise
- HTML content can be found in this directory, as `content.js`. This text can be imported into your file using `var htmlContent = require('./content.js')();`
- Commit and push all changes to a new GitHub repository from the command line

# Exercise 4

_All_ of the below should be done from the command line. :) We're going to hack like it's 1999. Oh wait, it's 2016. :( My jokes are terrible, I'm sorry.

- Create new folder in `all-together` named `shell-scripting`
- Initialize the `shell-scripting` folder as a git repository
- Create new file named `hacking-your-js.sh` from the command line
- In this file, create a shell script that does all of the following:
  - Creates a new folder from a user's home directory named `happy-fun-time`
  - In the `happy-fun-time` folder, create a new file named `do-not-open.js`
  - In the `do-not-open.js` file, create a javascript function that logs 'ALL YOUR TERMINAL ARE BELONG TO US'.
  - Execute the `do-not-open.js` file
- Commit and push all changes to a new GitHub repository from the command line

# Exercise 5

- Create new folder in `all-together` named `tick-tock`
- Initialize the `tick-tock` folder as a git repository
- Create new file named `making-a-clock.js` from the command line
- Within this file, create a function that will log the current time to the console and continue logging the time every minute until the application has manually been terminated with Ctrl+C
  - The time should be reported in the format: `MM/DD/YYYY HH:MM`
  - This will require some Googling and research to accomplish
- Commit and push all changes to a new GitHub repository from the command line
