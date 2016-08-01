+++
date = "2016-08-01T13:48:13-04:00"
draft = false
title = "Github Cheatsheet"

+++

Repositories are often called Repos.

You have a local repo (on your computer) and a remote repo (on Github).

You should first have a local repo.

Then create a remote repo by going to Github. You will either see a button to create one, or click the "+" sign at the top of the page and create one there. This page will have instructions for you. You'll need to copy the correct command.

## Push to Remote Repo

Return to your local repo and paste the command. It will look something like this:

```bash
$ git remote add origin "your-remote-repo-url" # will look like git@github.com:username/repo-name.git
$ git add --all
$ git commit -m "commit message"
# Then you can push to your remote repo
$ git push origin master
```

## Clone
If you go to a Github repo you can clone it - you can click "Clone or Download", copy the url (be sure you select clone with SSH). `cd` into the directory you want this repo to live.

```bash
$ git clone "the-copied-git-url" # it will look like git@github.com:username/repo-name.git
```
## Fork
The top right of any Github repo will have an option to "Fork" it in the top right corner. You will then be presented with an option to fork to your personal account or any organizations you have permissions to.

Once it's in your or your organizations account, you can follow the Clone directions above.
