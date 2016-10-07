# Command Line Homework 01 Solution

`alias crunchy='mkdir ~/crunchy; touch ~/crunchy/peanutbutter.txt && echo -e "Is the best!\n$PWD" >> $_ && chmod 666 ~/crunchy/peanutbutter.txt'`

Keep in mind that file creation and all subsequent commands should execute even if the `~/crunchy` folder already exists. If the folder exists, then executing `mkdir ~/crunchy` will fail. This requires use of either `;` after the `mkdir` command for the `-p` option for the `mkdir` command. Both of those options are acceptable. 
