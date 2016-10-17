# Git Questions

## Instructions

- Create a local directory named `test01-questions`
- Create a file in this directory named `answers.txt`
- Answer the below questions
- Push the answers to a GitHub repo named `test01-questions`

## Questions

1. Why do developers use source control?
2. What are two benefits of using git as your source control system?
3. Why is it important to run the git config command?
4. What is another name for source control?
5. Name one other version control system.
6. What command would you use to make a local copy of a remote repository?
7. What is the main identifying factor of a commit?
8. What is a single point in history called in git?
9. What is an irreconcilable diff called?
10. What is the command to view the latest changes in a remote repository without merging them into your local working copy?
11. What is the default name for the remote repository?
12. What is the command to create a new branch on a repository?
13. What is the command to switch to a branch on a repository?
14. How do you create an identical but separate repository on GitHub?
15. What is the command to combine the contents of one branch into another?
16. What command is the combination of fetch and merge?
17. What command sends commits made locally to the remote repository?
18. What is the name of the pointer/reference that keeps track of your current git location?
19. What is the name for where code that's under source control is located?
20. What is the name of the area where changes are placed prior to forming a commit?
21. What git command is commonly used to tag release versions of code?
22. What command turns a folder into a repository tracked via source control?
23. What command lets you see the commit history of the branch you currently have checked out?
24. What command lets you see the state of various files under version control?
25. What command adds a modified file to stage?
26. What command collects all the staged changes and groups them into a single point of history?
27. Label the state names for 1, 2, 3, and 4.
![alt-text](https://raw.githubusercontent.com/uagc-it-readiness/backend-dev-nodejs/master/lectures/03-source-control/lifecycle-blank.png "git-flow-chart-blank")

# Git & Command Line Exercises

## Instructions

- All tasks should be performed from the command line and/or web browser

## Warm-Up

- Create a local directory named `test01`
- Change to this directory via the command line

## Questions

### Question 1

- Create a new repository on GitHub named `test01-question-one`
- Create a directory named `question-one` in the `test01` directory
- Initialize the directory as a git repository
- Set the `test01-question-one` directory as the remote for this repository
- Within the `question-one` directory, create a `README.md` file with your first last last name within the file
- Save the file to the git repository and ensure that it's present in the remote repository

### Question 2

- Create a working copy of the [`test01-question-two`](https://github.com/uagc-it-readiness/backend-dev-test-question-two) repository on your machine in the `test01` directory
- Add a file named `bacon.txt` to the directory
- The contents of this file should be: `VEGGIES!`
- Save this file to the git repository
- Create a repository on GitHub named `test02-question-two`
- Change the remote of the local repository to be this new repository
- Put your local changes in this remote repository

### Question 3

- Create a new GitHub Repository named `test01-question-three`
- Create a directory named `question-three` in the `test01` directory
- Make this a git repository
- Create an alias that does all of the following in a single command:
  - Creates a sub folder in the home directory named `cupcakes`
  - Creates a sub folder in the `cupcakes` directory named `are-not`
  - Creates a file in the `are-not` directory named `better-than-donuts.txt`
  - Adds the text `SPRINKLES!`
  - Put the absolute path to your home directory on the second line of this file
- Create a file in the `question-three` directory named `my-alias.txt`
- Put the alias command you've created as text in this file
- Make this file available in the remote repository

### Question 4

- Create a working copy of the [`test01-question-four`](https://github.com/uagc-it-readiness/backend-dev-test-question-four) on your GitHub repository
- Create a local copy of this remote working copy in the `test01` directory
- Create a new branch named `yourname-spelling-fix`
- There is a spelling mistake in the `quick-brown-fox.txt` file
- Fix the mistake locally
- Save the fix and make the fix present in the remote copy of the repository
- Create a pull request for the original repo with this spelling change

### Question 5

- Create a new directory `question-five` in the `test01` directory
- Within this directory, create a shell script named `ten-files.sh`
- In this file, create a shell script that does all of the following:
  - Creates 10 files named `crumpets01.txt`, `crumpets02.txt`, `crumpets03.txt`, etc.
  - In files `01 - 05`, put the text `The crags are the best part!`
  - In files `06 - 10`, put the text `My present working directory is: your-pwd-here`
- Make this directory a git repository
- Save the `ten-files.sh` to the git repository
- Make this file available on GitHub
