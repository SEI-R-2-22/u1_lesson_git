# Git

![Git](https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png)

## Overview
In this lesson, we'll learn about distributed version control using Git.

## Objectives
- Understand what Git is and why we need it
- Use Git to save our code

## What is Git?

![XKCD - Git, How do we use it?](https://imgs.xkcd.com/comics/git.png)

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. Git is easy to learn and has a tiny footprint with lightning fast performance.

Git keeps track of all your code and saves your code **locally**. *GitHub* is a service where you save your code **online**. We'll cover that later. 

Each time you save to Git, you save a version of your code. It's kind of like a video game where you can save as many times as you want. Git stores a safe version of your code that you can come back to in case something goes wrong.

## Why is Git important?

Git handles versioning our code. In simple terms, if we make a mistake, we can always revert back to the old codebase. 

Git makes it easy to share your code with other developers.

Git is a version control system (VCS), more specifically, a distributed version control system (DVCS)

## The Git Lifecycle

To understand how Git works, we need to talk about the lifecycle of a Git-tracked file.

### Staging and Commiting

There are 3 states that your file can reside in `modified`, 
`staged`, and `committed`. These states map to the different sections of a Git project.

A) `modified` means that you have changed the file in your working directory, but that's it (ie you have not committed it to
your repository yet).

B) `staged` means that you have marked a modified file in its current version
to go into your next commit snapshot. Use `git add <file name>` to `stage` files.

C) `committed` means that the data is safely stored in your local repository. Use `git commit -m 'Your message here'`.


When we add a file we are moving it from the working directory to the staging area. Commiting it means we've moved it from our staging area to our local repository.

![lifecycle](https://camo.githubusercontent.com/bd20ca544ee4372810d5de7821e23e9bed4ce7ea/68747470733a2f2f7261772e6769746875622e636f6d2f4361726c65746f6e534c414d2f6769742d776f726b73686f702f6d61737465722f2e6769746875622f72656361705f6769745f6469616772616d2e706e67)

[Image Credit](https://github.com/CarletonSLAM/git-workshop)

### First we need to initialize our Git Repository: 

1. **Initialization** — First, you need to initialize a local Git repository. This will track any changes that have been made since the creation of your *present working directory*.

You only need to initialize a directory once. You can use the following command:
```bash
git init
```

### Next there are 3 main stages of a Git-tracked file after the repository has been initialized:

1. **Add to Staging** — Once the files in your working directory are being tracked by Git, you can now add any changes to the staging area with the `git add` command.

You can use a period to add all changes in the present working directory:
```bash
git add .
```

You can also add only the changes from a specific file in your directory by writing the filename instead of a period, for example:

```bash
git add index.html
```

2. **Commit to Local Repo** - Once you're all set adding files to staging, you can commit them to your local repository with the `git commit` command. This command will commit ALL files that have been staged.

>Note: Whenever you do `git commit` you MUST add a brief message describing the commit with `-m "message text"`. So a full git commit command should look something like this:

```bash
git commit -m "Created login form frontend"
```

### Now we need to sync our local repository to our Remote/Github.

3. **Create and Add a Remote Repo** — Once you have successfully committed files to our local repository, you should push it to a remote repository (e.g. GitHub), so that you can share your code with other people and/or so that you can access your own code from other computers. 

To do this, you'll first need to set up a remote repository on GitHub. To do this, first set up an account on GitHub, then click on "create new repository." 

Once you've finished creating You can then connect your local repository to that remote repository with the `git remote add` command.

The `git remote add` command takes two arguments:
- A remote name, for example, **origin** (this is the default name. just use it)
- A remote URL, for example, https://github.com/user-name/repository-name

A real `git remote add` command might look like this:

```bash
git remote add origin https://git.generalassemb.ly/SteveVW/repo-name
```
Note the example is using **origin** which is the default. Use a different shortname when adding a remote.

4. Use `git push` to push your commits from your local branch to your remote repository.

The `git push` command takes two arguments:
- A remote name, for example, **origin**
- A branch name, for example, **main**

These are both the default names. We'll get into adding additional branches right now. In the mean time, just stick with this format. Your full command should look like this:

```bash
git push origin main
```
5. To list out the available remotes including the name and URL that Git has stored for the short name.

```bash
git remote -v
```

6. To edit an existing remote **name**, such as **origin** to a new URL.

```bash
git remote set-url origin <URL>
```

## More Git Commands

#### Git Pull

```bash
git pull origin main
```

The git pull command is used to fetch and download content from your connected remote repository and immediately update your local repository to match that content.


#### Git Clone
```bash
git clone https://github.com/user-name/repository-name.git
```
The `git clone` command allows you to copy an online repository from GitHub down to your local computer.


#### Git Status
```bash
git status
```

The `git status` command displays the state of the present working directory and the staging area. It lets you see which changes have been staged, which haven’t, and which files aren’t being tracked by Git. Status output does not show you any information regarding the committed project history. For this, you need to use `git log`.


#### Git Log
```bash
git log
```

After you have created several commits, or if you have cloned a repository with an existing commit history, you’ll probably want to look back to see what has happened. The most basic and powerful tool to do this is the `git log` command.



When you run git log in this project, you should get output that looks something like this:
```bash
$ git log
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the version number

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    removed unnecessary test

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 10:31:28 2008 -0700

    first commit
```

#### Git Help
```bash
$ git help -a -g
```
This command displays help information about Git. If the option --all or -a is given, all available commands are printed. If the option --guide or -g is given, a list of the useful Git guides is also printed.

# Writing Good Git Commit Messages

![Git Commit](https://imgs.xkcd.com/comics/git_commit.png)

5 minute reading: [Writing Good Commit Messages](https://chris.beams.io/posts/git-commit/)

# Resources

- [Atlassian Learn Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
- [Try Git](https://try.github.io/levels/1/challenges/1)
- [Git - the Simple Guide](http://rogerdudler.github.io/git-guide/)
- [The git book](https://git-scm.com/book/en/v2) Read chapters 1-3
