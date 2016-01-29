# Git Repository Basics

## Objectives

1. Define git and explain how it helps programmers control and manage changes
2. Initialize a new git repository with `git init`
2. Check the state of your files using `git status`
3. Stage files to commit using `git add` and `git commit`

## Introduction: What Is Version Control?

> “The past is never where you think you left it.” — [Katherine Anne Porter](http://en.wikipedia.org/wiki/Katherine_Anne_Porter)

Version Control is the process of storing multiple versions of a single project, allowing each version to be recalled at a later date. Version Control basically allows you to move back-and-forth through the timeline of changes to your code called "commits."

There are a lot of different ways to do version control - you could save a new file every time you make a change, timestamp that file, and place all of those files into a timestamped folder. You could track all of your changes in a spreadsheet with copious notes. Sounds like a lot of work... Or you could use dedicated version control software. Guess which one programmers do?

## Why Use Version Control?

Let's think about the future for a second. It's a year or two down the road and you're working at your dream job (YAY!). You just deployed a new chat feature for the app you're working on. Suddenly, your boss runs over to your desk. "Wait! We can't deploy the chat yet! Revert! Revert!"

What do you do? You need to find all of the new code you pushed to the server and delete it. Then you need to find the old code, test it and re-upload it. So much work to do. Well, since you used version control software, it's as easy as 123. Actually, it's as easy as `git reset --hard <commit id>`... but we'll get to that later. Using version control is useful because it allows you to easily rollback to a previous version of your application, saving you a ton of extra work and time.

There are a lot of advantages to version control. It's great way to keep a backup of your work, it facilitates collaboration, and gives you the freedom to experiment and try new things without messing up the code base.

## Local vs Remote Version Control

A local version control system stores all of the information on your computer, locally. This system works great while you work on a project by yourself. It becomes cumbersome when you attempt to collaborate, however. And storing source code only on your computer is a bad idea because what if you lose your computer or spill a bunch of coffee on it.

Some organizations use a centralized repository on a company server. Think of a repository as a big folder that stores all of the files of a particular project. It is simply the location where a project's data is stored. Users pull only the files they need to work on from the server. The advantage is that multiple people can collaborate and work on the same project at once. The disadvantage to this process is that a user must be connected to the network in order to work on the project.

There is a third system, the distributed version control system. In a distributed system, all users have a complete copy of the entire repository. This means that you can work on the project independent of any kind of network connection. When you get  back to a location with a connection, you can push your changes to the server and merge with the server's repository.

## Meet Git

Git is the distributed version control system that began in 2005 and has quickly grown to be one of the most widely used version control systems in the industry. Because so many companies use Git, it's important that you get used to working with it. We also use GitHub, a popular remote repository hosting service built to integrate seamlessly with Git.

So how do you use Git?

## Creating a Repository with `git init`

You want to get started on a project that's going to be the next big thing. The first step you take is you make a new directory on your computer, probably in your development directory. From your terminal and your home directory you type:

```
~ $ mkdir next-big-thing
~ $ cd next-big-thing
next-big-thing $ ls

```

You made the directory with `mkdir next-big-thing` and then moved into it by changing your directory with `cd next-big-thing`. You typed `ls` to see all the files and folders in your brand new project and as expected, it was empty. But this directory, `next-big-thing` is where you're going to be putting all your code.

The first thing you should do is transform this directory into a Git-enabled directory that can keep track of all the changes to your code and allow you to interact with other Git remotes such as GitHub. How? Use `git init`.

`git init` initializes a new git repository in your current directory. Type `git init` from within your `next-big-thing` project directory.

```
next-big-thing $ git init
Initialized empty Git repository in /Users/avi/next-big-thing/.git/
```

After typing `git init` the output in your terminal reads "Initialized empty Git repository in `/your/path/here/next-big-thing/.git/`" telling you git made a new repository in `next-big-thing` within the hidden `.git` folder. This hidden directory, `.git`, is what git uses to keep track of all the different versions of your code.

You don't need to do anything with the `.git` directory. It'll remain hidden, just remember that if a directory has a .git directory inside of it, it is controlled by git. It's also nice to know there is no magic with code, if git is keeping track of multiple versions of files that you can't see, git has to be putting them somewhere inside your computer. That somewhere is `.git`.

At this point though, git is not keeping track of any of the files or folders in your project.

## Checking the status of your repository with `git status`

Let's start our project out by creating a `README.md` that describes the project. Make your new file by typing `touch README.md`, you won't see any output after `touch` but you will see a new file has been created by typing `ls`.

```
next-big-thing $ touch README.md
next-big-thing $ ls
README.md
```

Now that we've made a change to our project, we want to keep track of that change with git. The first thing to do is to see what git thinks our current repository looks like, what changes does it see, what status does it think our project is in? Try `git status`.

```
next-big-thing $ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	README.md

nothing added to commit but untracked files present (use "git add" to track)
```

Git is telling you that this is a brand new repository and right now git isn't keeping track of any of the files in your directory.

Whenever you want to see what the status of your git repository is, which is a task you'll want to do quite often, type `git status`. We'll be discussing the various states a repository can be in and how to change states shortly.

## Keeping track of files with `git add`

You have to explicitly tell git about all the files you want it to keep track of, of all the files you want git to consider to be part of your project. We do this by adding the files to our git repository with `git add <filename or path>`. To add our new `README.md` to the repository and check the status we could type:

```
next-big-thing $ git add README.md
next-big-thing $ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   README.md
```

You can now see that git is ready to keep track of `README.md` and recognizes that the file is a brand new file for this repository. However, just because we've informed git that there is a new file, we still haven't informed git that this new file is considered a new change to our repository. We create changes in our repository by making something called a "commit".

**To capture all changes in a directory, the common pattern, type `git add .` where the `.` refers to the entire current directory.**

## Making a new version of your code with `git commit`

Git allows us to mark the changes we make in our code as versions called a commit. A commit is like a frozen copy of your code at a given point. Once you've made a commit, you can always move back to the version of your code at that exact moment.

Now that git is aware of a change to our project, the new file `README.md`, let's make the addition of this file as the first official version, the first commit, of our project, using `git commit`. Whenever we make a commit, we must supply a commit message describing the version or commit. This message log makes it easy for us to know what each commit or version is all about.

You can make a commit adding the `README.md` with: `git commit -m "Added README.md"`.

We tell the `git commit` command that our commit message, represented by the `-m` flag, is `"Added README.md"`.

```
next-big-thing $ git commit -m "Added README.md"
[master (root-commit) e55477d] Added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```

Git tells us that it created a new version of our code, represented by the esoteric SHA `e55477d` (basically how git keeps tracks of versions). The commit had 1 file changed. With that commit made and no other changes to our files, if we ask git what the status of our project is now, we'll see that it is at a "Clean State", that there is nothing to commit and no new changes.

```
next-big-thing $ git status
On branch master
nothing to commit, working directory clean
```

**To capture all changes in a commit, the common pattern, type `git commit -am "Your commit message"` where the `-a` refers to 'all the changes' and `-m` (combined, `-am`), tells git about the commit message, `"Your commit message"`.**

## Conclusion

1. To make a new git repository out of a directory, something you only ever do once per project, you use `git init`. Be careful about making an entire directory, like your home directory or your desktop, into a git repository accidentally. Make sure you only type `git init` within the directory you want to be considered a repository.
2. Whenever you make a change to a file or create a new file, you have to tell git to keep track of that change by staging it via the `git add` command. **To capture all changes in a directory, the common pattern, type `git add .` where the `.` refers to the entire current directory.**
3. Once your changes have been added and staged to be committed, you can make a commit with the `git commit` command. **To capture all changes in a commit, the common pattern, type `git commit -am "Your commit message"` where the `-a` refers to 'all the changes' and `-m` (combined, `-am`), tells git about the commit message, `"Your commit message"`.**
4. To check the status of a repository use `git status`.

If you've followed these instructions you are left with a directory, `next-big-thing` that is a git repository. You can just delete this directory, ignore it, or use it as a sandbox to experiment with git.

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/git-basics-readme' title='Git Repository Basics'>Git Repository Basics</a> on Learn.co and start learning to code for free.</p>
