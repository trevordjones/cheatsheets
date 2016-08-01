+++
date = "2016-07-31T15:37:55-04:00"
draft = false
title = "Git Cheatsheet"

+++

Tell git to track the folder you are currently in (be sure to `cd` into it):
```bash
$ git init
```
Only need to do this once.

Made changes to your project:
```bash
$ git add --all
$ git commit -m "your message"
```

Here are some extra commands you can play with:
```bash
$ git status
# see which files are being tracked and which are not

$ git log
# Check your log of commits

$ git diff file_name
# See the changes of the files
```
