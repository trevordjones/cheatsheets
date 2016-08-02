+++
date = "2016-08-02T17:25:54-04:00"
draft = false
title = "Terminal Commands"

+++

### Commands
```bash
$ ls # list directory contents

$ ls -l # list directory contents as a list (one per line)

$ ls -la # list directory contents as well as hidden files (files that begin with a '.')

$ cd 'directory_name' # change into the given directory

$ cd .. # cd out of the current directory - one level

$ cd ../.. # cd out two levels

$ cd ~ # go to home directory (should be your computer username)

$ cd / # go to root directory

$ mkdir 'directory_name' # create directory

$ rm # remove file
$ rmdir # remove directory - will only work if directory is empty
$ rm -rf 'directory_name' # remove directory and ALL it's contents. Be warned when using this - you will not be prompted to continue. It will just wipe it out.

$ touch 'file_name' # create a file with the name you give it

$ pwd # Get complete file path

$ cat 'file_name' # print contents of the file to the terminal

$ echo 'add this text' >> 'file_name.txt' # Add text to a file
```
### Hotkeys
* Tab - Autocomplete to file path. You just need to type the first letter or two and then it will complete
* Up/Down Arrow - See command history
* CTRL + r 'previous command' - Search command history
* CTRL + l - clears the screen but does not get rid of session history
* CMD + k - clears the screen and does get rid of session history
