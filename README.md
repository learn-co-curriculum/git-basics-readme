##Git Repository Basics

###Objectives
1. Define git and explain how it helps programmers control and manage changes
2. Understand how to initialize a new git repository with `git init`
2. Understand how to check the state of your files using `git status`
3. Understand how to stage files to commit using `git add` and git `commit`


###Overview
This lesson is an intro to git and basic commands to get started.

###`git init`
The `git init` command initializes a new git repository in your current directory. What does this mean? Let's say you have a directory called `app`. If you change into that directory in your terminal and type `git init`, you will create a new subdirectory called `.git`. The output in your terminal will read "Initialized empty Git repository in `/your/path/here/app/.git/`" This subdirectory will contain everything needed to start tracking your file changes. Tracking is how `.git` knows about what files are being created or changed. However, at this point, nothing in your project is actually being tracked. So if you create a new file inside your `app` directory called `index.html`, `.git` will not know about it. In order to start tracking files we need another command, which we will talk about shortly.

###`git status`
Befor we move on to actually tracking our files, let's take a look at `git status`. This command, as the name implies, gives the status of your files. Using our example before, when we initialize our new `.git` subdirectory inside our `app` directory and create our `index.html` file, if we type `git status` in our terminal it will read.

```bash
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	index.html

nothing added to commit but untracked files present (use "git add" to track)
```
Here `git` is telling us, "I see you've created a new file called `index.html`, but it's not yet being tracked. In order to track it, use `git add`.

###`git add`
The `git add` command is how you stage files. Staging is a way of saying your files are ready to be committed. However, this command has to be told what to add. If you just type `git add` by itself in your terminal you will see:

```bash
Nothing specified, nothing added.
Maybe you wanted to say 'git add .'?
```
There are two common ways to tell `git add` what to track.
The first way, as the message before specificed is through `.`. When you pass `.` to `git add` you are saying "track all of the files in the current directory". The second most common way is by passing the actual file name, such as `git add index.html`. In this case we are specifically telling it to track `index.html` and ignore everything else.

###`git commit`
