Quick-Notes-Git
===============

Quick Notes about git

## Introduction

Git is a **Distributed Version Control System (DVCS)**.

Git clients **fully mirror** the repository.

Git thinks about its data more like a **stream of snapshots**.

Git has 3 main states:
  * **modified** (file has changed but is not yet commited)
  * **staged** (modified file is marked to go into your next commit)
  * **commited** (file is safely stored in your local git database)

Git workflow:
  1. Files are modified in working directory
  2. Files are staged (with `git add`)
  3. Files in staged area are commited (with `git commit`)

## Settings

Setup git configuration for every user on the system (configuration will be stored in `/etc/gitconfig`):
```shell
git config --system
```

Setup git configuration for your user (configuration will be stored in `~/.gitconfig` or `~/.config/git/config`):
```shell
git config --global
```

Setup git configuration for one repository only (configuration will be stored in `.git/config` of the repository):
```shell
git config
```

Setup user name & email:
```shell
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

List all settings configured:
```shell
git config --list 
```

Get the value of a configuration key:
```shell
git config <key> 
```

### Bash Completion

Download from Github:
```shell
cd ~
curl -OL https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash
mv ~/git-completion.bash ~/.git-completion.bash
```

Edit `.bash_profile`:
```shell
if [ -f ~/.git-completion.bash ]; 
then
    source ~/.git-completion.bash
fi
```


## Basics

Create a Git repository (a `.git/` directory is created):
```shell
git init 
```

Clone an existing repository:
```shell
git clone https://github.com/sebthebert/Quick-Notes-Git
git clone https://github.com/sebthebert/Quick-Notes-Git another_directory
```

Check status of your files:
```shell
git status 
```

For a shorter status:
```shell
git status -s
git status --short
```

To stage a file:
```shell
git add <filename> 
```

### git checkout

"Undo" changes on working area file or directory (by checkout-ing the repository one) 
```shell
git checkout -- <filename>

git checkout -- <directory>
```

Get an older version (with sha1-hash) of one file in stage area, diff it to check it and the re-commit
```shell
git checkout <sha1-hash> -- <filename>
git diff --stagged
git commit ...
```
See also [git revert](#git-revert)

### git commit

Modify the last commit (don't create another one in commit history) (but hash and date change)
```shell
git commit --amend -m "<message>"
```

### git diff

Diff between working directory and stage area
```shell
git diff
```

Diff between stage area and repository
```shell
git diff --staged
```

Diff at 'word level'
```shell
git diff --word-diff=plain dist.ini
```

https://stackoverflow.com/a/3686507/24820

### git log

```shell
git log -n 10

git log --since=2018-02-01

git log --until=2018-01-31

git log --author="author name"

git log --grep="something to search"
```

### git reset

**USE WITH CAUTION !**
Move HEAD pointer...

(doesn't change staging area and working diretory)
```shell
git reset --soft <sha1-hash>
```

(changes staging area but not the working directory)
```shell
git reset --mixed <sha1-hash>
```

(changes staging area and the working directory)
```shell
git reset --hard <sha1-hash>
```

### git revert

Undo a complete commit:
```shell
git revert <sha1-hash>
```

To ignore files that you don't want to track with git, list them in a `.gitignore` file

## Sources

**Pro Git** book
