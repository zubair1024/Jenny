---
layout: post
title:  "GIT Commands Qickie"
date:   2015-11-26 13:46:52
comments: true
categories: numeronyms, tips
---


We can all agree that git has become everyone’s favorite versioning system lately. Having experience with SVN and Git I can safely say that Git is not actually better but it is different. The key advantage is that it is decentralized. With Git, you can do practically anything offline, because everybody has their own repository. Making branches and merging between branches has never been easier. Git is complex, powerful and fast (since it works for Linux kernel of course). Every company and business setup has its own workflow and with SVN in my company we had a tough time adopting the version system with our business case. Git is very flexible and with its TIMTOWTDI approach will help is meet our goals. Well, everything has its pros and cons even though the pros will obviously outrun the cons, note that Git is much harder to learn, lacks a good GUI and revisions do not have version numbers. Below I have complied a few necessary git commands in the form of a cheat sheet:

###### Configuration:

```python

    $ git config --global user.name "[name]"

```

Sets the name you want to commit with.

```python

    $ git config --global user.email "[email address]"

```

Sets the email Address you want the author to have.

The most useful config you need to start with is

```python

    $ git config --global color.ui auto

```

Sets to colorize the command line.

***

###### Creating a New Repository:

```python

    $ git init

```

Initializes a new repository

```python

    $ git clone ssh://user@domain.com/repo.git
    $ git clone username@host:/path/to/repository
    $ git clone /path/to/repository


```

Clones an existing repository.

Adding Files to be Tracked:

```python

    $ git add

```

Adds the specified file.

```python

    $ git add .

```

Adds all files.

***

###### Tracking Changes:

```python

    $ git status

```

List all new or modified files to be committed

```python

    $ git diff


```

Shows file difference not yet staged.

```python

    $ git log

```

Shows all commits

```python

    $ git log --oneline

```

Show all commits summaried each in one line.

```python

    $ git log -p

```

Shows changes for a specific file

```python

    $ git diff --staged

```

Shows file differences between staging and the last file version

```python

    $ git blame

```

Tracking changes on a file about who changed what and when (annotated).

***

###### Committing changes:

```python

    $ git commit -m 'commit message'

```

Commit changes to head

```python

    $ git commit -a

```

Commit any file you have added with git add or modified an added file.

```python

    $ git remote add origin

```

If you haven’t connected your local repository to a remote server, add the server to be able to push to it

```python

    $ git remote -v

```

***

###### List all currently configured remote repositories:

```python

    $ git push origin master

```

Sends the changes to the master branch on the remote repository

```python

    $ git push

```

Publish local changes on a remote

***

###### Branching and Related Commands:

```python

    $ git branch

```

List all existing branches

```python

    $ git branch

```

Creates a new branch based on your current head

```python

    $ git checkout

```
Checkout a specified branch

```python

    $ git branch -d

```
Deletes a specified branch

```python

    $ git merge

```
Merge into the current head

```python

    $ git rebase

```
Rebase current head onto the branch

```python

    $ git tag

```
Mark the current commit with a tag name.

***

###### Fetching Commits:

```python

    $ git fetch

```

Download all changes from , but don’t integrate into head

```python

    $ git pull

```
Download changes from and merge into head

***

###### File System:

```python

    $ git rm

```

Deletes the specified file form the working directory and stages the deletion.

```python

    $ git rm --cached

```

Deletes the file from the version control system but preserves the file locally in the working directory.

```python

    $ git mv < original-filename>
    $ git lis-files --other --ignored --exclude-standard

```

List all ignored files in working project directory

***

###### Stashes:

```python

    $ git stash

```
Temporarily stores all modified tracked files

```python

    $ git stash pop

```
Restores the most recently stashed files

```python

    $ git stash list

```
Lists all stashed changesets

```python

    $git stash drop

```
Discards the most recently stashed changeset

***

###### Reverting and Re-doing:

```python

    $ git reset

```
Unstages the specified file, but preserve its contents

```python

    $ git reset

```

Undoes all commits after [commit] , preserving changes locally

```python

    $ git reset --hard [commit]

```

Discards all history and changes back to the specified commit

```python

    $ git revert


```

Revert a commit by producing a new commit with contrary changes

Happy committing!