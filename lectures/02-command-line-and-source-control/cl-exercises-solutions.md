# Command Line Exercise Solutions

## Exercise 1

`mkdir terminal-exercises`

`touch ./terminal-exercises/hello.txt`

`mkdir ./terminal-exercises/the-underdark`

`touch ./terminal-exercises/the-underdark/world.txt`

## Exercise 2

`mv ~/Downloads/bacon.txt ~/terminal-exercises/veggies.txt`

`grep -oni nomnomnom ~/terminal-exercises/veggies.txt`

The result of the `grep` should be:

```
5:nomnomnom
15:nomnomnom
25:nomnomnom
31:nomnomnom
39:NOMNOMNOM
```

`sed -i '' 's/nomnomnom/veggies/g' bacon.txt`

`sed -i '' 's/NOMNOMNOM/veggies/g' bacon.txt`

`grep -oni veggies ~/terminal-exercises/veggies.txt`

Final result:

```
5:veggies
15:veggies
25:veggies
31:veggies
39:veggies
```

## Exercise 3

`cd ~/terminal-exercises`

`mkdir permissions`

`touch ./permissions/my-file.txt`

`vim ./permissions/my-file.txt`

Add a few lines of text -- whatever you want.
  - Don't forget to enter `insert mode` in vim by pressing the `i` key
  - `Shift + ZZ` to close and save the file with your changes

`chmod 700 ./permissions/my-file.txt`

To check the result of the `chmod` change: `ls -alt ./permissions`

This should be the result:

`-rwx------   1 username  group    3 Oct  2 16:39 my-file.txt`

## Exercise 4

This is an example of an alias that will accomplish all of the exercise objectives:

`alias kapow='mkdir shazam && cd $_ && touch magic-wand.txt && echo -e "1\n2\n3\n4\n5" >> $_`
