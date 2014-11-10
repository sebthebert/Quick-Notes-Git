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
  2. Files are staged
  3. Files in staged area are commited

## Settings

To setup git configuration for every user on the system (configuration will be stored in `/etc/gitconfig`):
```shell
git config --system
```

To setup git configuration for your user (configuration will be stored in `~/.gitconfig` or `~/.config/git/config`):
```shell
git config --global
```

To setup git configuration for one repository only (configuration will be stored in `.git/config` of the repository):
```shell
git config
```

To setup user name & email:
```shell
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```


## Sources

**Pro Git** book
