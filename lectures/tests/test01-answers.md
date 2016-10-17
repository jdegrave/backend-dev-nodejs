# Test 1 - Answers

## Git Questions

1. Source control tracks the state of a project, and all the changes that have been made to it
2. Collaboration & free / open source (among many others)
3. `git config` lets you save information that is used to tag your commits
4. Version Control, Revision Control
5. Subversion, Mercurial, Perforce, Bazaar
6. `git clone`
7. sha/hash
8. Commit
9. Conflict
10. `git fetch`
11. origin
12. `git branch`
13. `git checkout`
14. fork
15. `git merge`
16. `git pull`
17. `git push`
18. HEAD
19. repository
20. stage
21. tag
22. `git init`
23. `git log`
24. `git status`
25. `git add`
26. `git commit`
27. 1 - Untracked; 2 - Unmodified; 3 - Modified; 4 - Staged

## Git & Command Line Exercises

### Warm-Up

```bash
cd ~ && mkdir test01 && cd $_
```

### Question 1

- On GitHub
  - Create new repository named `test01-question-one`
  - Initialize _without_ README

- On local machine:

```bash
mkdir ~/test01/question-one && cd $_
git init
echo -e 'Blake Johnston' > README.md
git status
git add README.md
git status
git commit -m 'Add readme'
git remote add origin git@github.com:username/test01-question-one.git
git push origin master
```

### Question 2

- On local machine:

```bash
cd ~/test01
git clone git@github.com:uagc-it-readiness/backend-dev-test-question-two.git
cd backend-dev-test-question-two
echo -e 'VEGGIES!' > bacon.txt
```

- On GitHub
  - Create new repository named `test01-question-two`
  - Initialize _without_ README

- On local machine:

```bash
git status
git add bacon.txt
git status
git commit -m 'Add bacon.txt'
git remote set-url git@github.com:username/test01-question-two.git
git push origin master
```

## Question 3

- On GitHub
  - Create new repository named `test01-question-three`
  - Initialize _without_ README

- On local machine:

```bash
cd ~/test01 && mkdir question-three && cd $_
git init
echo -e 'alias donuts=mkdir ~/cupcakes && mkdir ~/cupcakes/are-not && echo -e "SPRINKES!\n$HOME" > ~/cupcakes/are-not/better-than-donuts.txt' > my-alias.txt
git status
git add my-alias.txt
git status
git commit -m 'Add alias'
git remote add origin git@github.com:username/test01-question-three.git
git push origin master
```

## Question 4

- On GitHub
  - From the UAGC IT Readiness Question four repository:
    - Fork the repository
  - From forked repository
    - Copy clone link

- On local machine:

```bash
cd ~/test01
git clone git@github.com:username/backend-dev-test-question-four.git
cd backend-dev-test-question-four
git checkout -b blakej-spelling-fix
vim quick-brown-fox.txt
git status
git add quick-brown-fox.txt
git status
git commit -m 'Fix spelling mistake'
git push origin blakej-spelling-fix
```

- On GitHub
  - From the `blakej-spelling-fix` branch:
    - Click Open Pull Request button

## Question 5

- On local machine:

```bash
cd ~/test01 && mkdir question-five && cd $_
touch ten-files.sh && vim $_
```

- In vim (there are several ways to accomplish this):

```shell
for i in {01..05}
do
  echo "The crags are the best part!" > "crumpets${i}.txt"
done

for i in {06..10}
do
  echo "My present working directory is: ${PWD}" > "crumpets${i}.txt"
done
```

- On GitHub:
  - Create new repository named `question-five`
  - Initialize _without_ README

- Back in the terminal on your local machine:

```bash
git init
git status
git add ten-files.sh
git status
git commit -m 'Add shell script'
git remote add origin git@github.com:username/question-five.git
git push origin master
```
