### Exercise 1

`tar -cvf ~/terminal-exercises/bacon.tar bacon.txt`

### Exercise 2

```
echo "Creating terminal-exercises directory"
cd ~
mkdir ~/terminal-exercises/my-directory

echo "Creating my-pets.txt and adding content"
echo -e "fluffykins\ncrumpet\nhot sauce" > ~/terminal-exercises/my-directory/my-pets.txt

echo Creating magic.txt and adding content
echo -e "shazam\!\ntada\!" > ~/terminal-exercises/my-directory/magic.txt

echo "Merging files"
cat ~/terminal-exercises/my-directory/magic.txt ~/terminal-exercises/my-directory/my-pets.txt > ~/terminal-exercises/my-directory/merged.txt

echo "Compressing file"
tar -cf ~/terminal-exercises/my-directory/merged.tar -P ~/terminal-exercises/my-directory/merged.txt

echo "Moving merged.tar"
mv ~/terminal-exercises/my-directory/merged.tar ~/terminal-exercises/my-first-shell-script.tar

echo "Cleaning up"
rm -rf ~/terminal-exercises/my-directory

echo "Done!"
```
