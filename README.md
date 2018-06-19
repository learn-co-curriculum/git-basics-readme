# Git Repository Basics


## Objectives

1. Define `git` and explain how it helps programmers track changes
2. Use `git` to enhance your workflow
3. State how to initialize a Git repository with `git init`
4. Use `git status` to check the status of your repository 
5. Recognize how to keep track of files with `git add`
6. Create a commit with `git commit` and apply a commit message

## Problem Statement

Have you ever found yourself moving between different workstations, or having to 
work together in a team setting on the same sets of files? Your filenames get very
verbose at times: 

```
important_presentation-v1.docx
important_presentation-v2.docx
important_presentation-v3.docx
important_presentation-final.docx
important_presentation-final-final.docx
important_presentation-final-final-FINAL.docx
important_presentation-final-final-FINAL-SERIOUSLY.docx
```
Luckily, there's a better way to keep track of versions of files and share them 
amongst multiple parties without causing complete chaos or confusion without 
having to keep naming or renaming files in this manner!

## Define `git` and Explain How it Helps Programmers Track Changes

Git is a widely used, collaborative, version control system that is optimized for
building software projects, whether commercial or open source. It logs changes in
files on your computer and allows work to be coordinated among multiple people.
It is primarily used for source code management in software development, but it can
be used to keep track of changes in any set of files. It's fast, secure, and supports
functionality that allows for non-linear workflows.

## Use `git` to Enhance Your Workflow

While building a project on your local machine, you may want to be able to keep
a running log of your changes as illustrated in the problem statement, as well
as store these changes somewhere accessible for other developers to review or
collaborate with you --or just put it somewhere you can come back to it later,
regardless of  what may happen to the physical files on your computer. This is
where `git` can save  the day! `Git` will allow you to keep track of all changes
to your files, and keep detailed tabs and backups of each on your project.

Now that we've established what `git` does and its potential usefulness, how can
we start using it? If you haven't already generated some files on your local machine
at this point--You can do so by using these commands to create a project:

```
~ $ mkdir my-git-project //Creates new directory
~ $ cd my-git-project //Moves into the newly created directory
```

Now that the files are available, how do we get them in the cloud so we can collaborate
with other developers or backup your progress thus far? 

## State How to Initialize a Git Repository with `git init`

Move into your new directory where you want to initialize a new instance of `git`.
You can use a few commands to get things up and running quickly. In your terminal type:

```
my-git-project $ git init
Initialized empty Git repository in /Users/avi/my-git-project/.git/
```

After entering `git init`, the output in your terminal reads `Initialized empty Git repository in /your/path/here/my-git-project/.git/`. Git is letting you know that it created
a new repository within the hidden `.git` folder in `my-git-project`. This hidden
directory, `.git`, is what Git uses to keep track of all the different versions
of your code.

You won't need to do anything with the `.git` directory –– it'll remain hidden.
Just remember that if a directory has a `.git` directory inside of it, it is
controlled by Git. It's also nice to know there's no magic behind the process:
if Git is keeping track of multiple versions of files that you can't see, Git
has to be putting them somewhere inside your computer. That somewhere is `.git`.

## Use `git status` to Check the Status of Your Repository 

Let's create a `README.md` that describes the project. Make your new file by
typing `touch README.md` from within the `my-git-project` directory. You won't
see any output after `touch`, but you will see a new file has been created if
you type `ls`, which gives a list of all the files in the directory.

```
my-git-project $ touch README.md
my-git-project $ ls
README.md
```

With at least 1 new project file we can enable Git to start tracking changes.
Type `git status`. Git will show you what your current repository looks like
and what changes it sees.

```
my-git-project $ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	README.md

nothing added to commit but untracked files present (use "git add" to track)
```

Git is telling you that this is a brand new repository and right now Git
isn't keeping track of any of the files in your directory.

Whenever you want to check the status of your Git repository –– which
you'll probably do quite often –– type `git status`. 

## Recognize How to Keep Track of Files with `git add`

Currently the files in your repository are not being tracked by Git just yet.
You have to explicitly tell Git about all the files you want it to keep track
of and consider as part of your project. You can do this by adding the files
to our Git repository with `git add <filename or path>`. To add our new
`README.md` to the repository and check the status, we would type:

```
my-git-project $ git add README.md
my-git-project $ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   README.md
```

You can now see that Git is ready to keep track of `README.md` and recognizes
that the file is new to this repository. However, while we've informed Git that
there is a new file, we still haven't informed Git that this new file is
considered a change to our repository. We create changes in our repository 
by making "commits."

**To capture all changes in a directory –– the standard way to do it –– type `git add .`, where the `.` refers to the entire current directory.**

## Create a Commit With `git commit` and Apply a Commit Message

Git allows us to mark changes to our code as different versions, or, in Git
speak, "commits." A commit is like a frozen copy of your code at a given point.
Once you've made a commit, you can always easily revert to that version of your
code as it existed at that exact moment.

Now that Git is aware of a change to our project –– the addition of `README.md`
–– let's submit the first official version of our project using `git commit`.
Whenever we make a commit, we must supply a commit message describing the version
or commit. This message log makes it easy for us to figure out what each commit
or version is all about.

To make your first commit, type: `git commit -m "Added README.md"`. This tells
Git that our commit message, represented by the `-m` flag, is `"Added README.md"`.

```
my-git-project $ git commit -m "Added README.md"
[master (root-commit) e55477d] Added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```

Git tells us that it created a new version of our code, represented by the
esoteric SHA `e55477d` (the identification system that Git uses to keep track
of versions). The commit changed 1 file. Now, if you type `git status` ask to
see the status of our project, with no other changes to any files, you'll see
that it is at a "Clean State", and there is nothing to commit and no new changes.   

```
my-git-project $ git status
On branch master
nothing to commit, working directory clean
```

**The best way to capture all outstanding changes in a commit is with
`git commit -am "Your commit message"`, where `-a` refers to 'all changes'
and `-m` (combined as `-am`) assigns a commit message of `"Your commit message"`.**

## Conclusion

To make a new Git repository out of a directory –– which you'll only have to
do once per project –– use `git init`. Be careful about making an entire directory,
like your home directory or your desktop, into a Git repository accidentally. Make
sure you only type `git init` within the directory you want Git to track. Whenever
you make a change to a file or create a new file, you have to tell Git to keep
track of that change by staging it via the `git add` command. **To capture all
changes in a directory, type `git add .`, where the `.` refers to the entire current
directory.** Once your changes have been added and staged, you can make a commit with
the `git commit` command. **To capture all outstanding changes in a commit, type
`git commit -am "Your commit message"`, where `-a` refers to 'all changes' and `-m`
(combined as `-am`) assigns a commit message of `"Your commit message"`.** To check
the status of a repository, use `git status`.

If you've followed these instructions, your `my-git-project` directory is now a Git
repository. You can retain the directory as a sandbox for Git experimentation, or simply
delete or ignore it.

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/git-basics-readme' title='Git Repository Basics'>Git Repository Basics</a> on Learn.co and start learning to code for free.</p>

<p class='util--hide'>View <a href='https://learn.co/lessons/git-basics-readme'>Git Repository Basics</a> on Learn.co and start learning to code for free.</p>
