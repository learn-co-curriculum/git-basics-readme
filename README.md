# Git Repository Basics

## Objectives

1. Define Git and explain how it helps programmers control and manage changes
2. Initialize a new Git repository with `git init`
3. Check the state of your files using `git status`
4. Stage files to commit using `git add` and `git commit`

So, how do you use Git?

## Creating a Repository with `git init`

You want to get started on a project that's going to be the next big thing. The first step is to make a new directory on your computer, probably in your development directory. To do so in the terminal, type:

```
~ $ mkdir next-big-thing
~ $ cd next-big-thing
next-big-thing $ ls

```

You created a new directory with `mkdir next-big-thing` and then moved into it by changing your directory with `cd next-big-thing`. You typed `ls` to see all the files and folders in your brand new project, and, as expected, it was empty. But this directory, `next-big-thing`, is where you're going to put all your code.

The first step is to transform this directory into a Git-enabled directory, which will allow it to keep track of all the changes to your code and interact with other Git remotes such as GitHub. How do we accomplish this? It's as simple as `git init`.

`git init` initializes a new Git repository in your current directory. Type `git init` from within your `next-big-thing` project directory.

```
next-big-thing $ git init
Initialized empty Git repository in /Users/avi/next-big-thing/.git/
```

After entering `git init`, the output in your terminal reads `Initialized empty Git repository in /your/path/here/next-big-thing/.git/`. Git is letting you know that it created a new repository within the hidden `.git` folder in `next-big-thing`. This hidden directory, `.git`, is what Git uses to keep track of all the different versions of your code.

You don't need to do anything with the `.git` directory –– it'll remain hidden. Just remember that if a directory has a `.git` directory inside of it, it is controlled by Git. It's also nice to know there's no magic behind the process: if Git is keeping track of multiple versions of files that you can't see, Git has to be putting them somewhere inside your computer. That somewhere is `.git`.

At this point, though, there's nothing for Git to keep track of. We'll have to create some files and folders in our project first.

## Checking the status of your repository with `git status`

Let's start our project out by creating a `README.md` that describes the project. Make your new file by typing `touch README.md` from within the `next-big-thing` directory. You won't see any output after `touch`, but you will see a new file has been created if you type `ls`.

```
next-big-thing $ touch README.md
next-big-thing $ ls
README.md
```

Now that we've created our first project file, let's have Git start tracking changes. The first thing to do is to see what Git thinks our current repository looks like; that is, what changes it sees or what it thinks the current status of our project is. Try `git status`.

```
next-big-thing $ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	README.md

nothing added to commit but untracked files present (use "git add" to track)
```

Git is telling you that this is a brand new repository and right now Git isn't keeping track of any of the files in your directory.

Whenever you want to check the status of your Git repository –– which you'll probably do quite often –– type `git status`. We'll discuss the various states a repository can be in and how to change states shortly.

## Keeping track of files with `git add`

You have to explicitly tell Git about all the files you want it to keep track of– the files you want Git to consider as part of your project. We do this by adding the files to our Git repository with `git add <filename or path>`. To add our new `README.md` to the repository and check the status, we would type:

```
next-big-thing $ git add README.md
next-big-thing $ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   README.md
```

You can now see that Git is ready to keep track of `README.md` and recognizes that the file is new to this repository. However, while we've informed Git that there is a new file, we still haven't informed Git that this new file is considered a change to our repository. We create changes in our repository by making "commits."

**To capture all changes in a directory –– the standard way to do it –– type `git add .`, where the `.` refers to the entire current directory.**

## Cataloging a new version of your code with `git commit`

Git allows us to mark changes to our code as different versions, or, in Git speak, "commits." A commit is like a frozen copy of your code at a given point. Once you've made a commit, you can always easily revert to that version of your code as it existed at that exact moment.

Now that Git is aware of a change to our project –– the addition of `README.md` –– let's submit the first official version of our project using `git commit`. Whenever we make a commit, we must supply a commit message describing the version or commit. This message log makes it easy for us to figure out what each commit or version is all about.

To make your first commit, type: `git commit -m "Added README.md"`. This tells Git that our commit message, represented by the `-m` flag, is `"Added README.md"`.

```
next-big-thing $ git commit -m "Added README.md"
[master (root-commit) e55477d] Added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```

Git tells us that it created a new version of our code, represented by the esoteric SHA `e55477d` (basically how Git keeps tracks of versions). The commit changed 1 file. With that commit made and no other changes to our files, if we ask Git what the status of our project is now, we'll see that it is at a "Clean State", that there is nothing to commit and no new changes.

```
next-big-thing $ git status
On branch master
nothing to commit, working directory clean
```

**The best way to capture all outstanding changes in a commit is with `git commit -am "Your commit message"`, where `-a` refers to 'all changes' and `-m` (combined as `-am`) assigns a commit message of `"Your commit message"`.**

## Conclusion

1. To make a new Git repository out of a directory –– which you'll only have to do once per project –– use `git init`. Be careful about making an entire directory, like your home directory or your desktop, into a Git repository accidentally. Make sure you only type `git init` within the directory you want Git to track.
2. Whenever you make a change to a file or create a new file, you have to tell Git to keep track of that change by staging it via the `git add` command. **To capture all changes in a directory, type `git add .`, where the `.` refers to the entire current directory.**
3. Once your changes have been added and staged, you can make a commit with the `git commit` command. **To capture all outstanding changes in a commit, type `git commit -am "Your commit message"`, where `-a` refers to 'all changes' and `-m` (combined as `-am`) assigns a commit message of `"Your commit message"`.**
4. To check the status of a repository, use `git status`.

If you've followed these instructions, your `next-big-thing` directory is now a Git repository. You can retain the directory as a sandbox for Git experimentation, or simply delete or ignore it.

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/git-basics-readme' title='Git Repository Basics'>Git Repository Basics</a> on Learn.co and start learning to code for free.</p>
