## What is git

Git is the origin of google docs :) GIt is like game save with bunch of functionality aded on top.

git is a distributed version control system. Git keeps track of all the files and changes to those files. 

Unlike other VCSs, git saves snapshots of history. Every time you make change to ANY file under git control, it knows about it. 

Git is not running, it doesn¨t drain resources. It only "runs" when you ask it to.

Git != github

Git is local - distributed. You can work on projeccts completely offline. It has its benefits and isadvantages, but for small teams, mostly benefits.


## When to use it?
Git works flawlessly with text based files, but cannot work (without serious tweaking) with binary files.

!!! Example
    Show an example what is the difference between text and png file

Git is designed to work as a repository for files you need to keep track of and you are developing constantly. It should NOT be used as a repository for your data files.

!!! Question
      Which of these files should be sourced and which not?
    
    - *.jpg
    - *.md
    - *.R
    - *.csv
    - *.edf

### Terminology

Git != github.

#### Repository
Or repo for short.

#### Staging and commiting
Process of adding files under version control. Staging prepares them for the commit, commiting adds them permantenly to the branch you are working on.

![Git workflow](/../assets/img/git-fundamentals/git-staging.png)

Stagin and commiting are separated becasue of practical reasons. You might need to stage multiple files before you want to commit to the commit.

#### Branch
Path of your project with the linear history - also calledd working tree.

## Git software

Git has several "clickable" GUIs. 

- Gitkraken
- SourceTree

Problems with git gui:

- unreliable from time to time
- they don't always implement all the features (gitkraken implemented LFS in September 2017 and it is still in beta)
- they don't teach you anything - in the beginnign you are missing on the underlying logic
- **MAJOR**: All internet help will be cmd based. CMD commands are universal, GUIs are not

## First repository

!!! Demo
    Before starting create a github repository for this lesson to showcase how it works and to be able to clone it back to pc. Set remotes. You will explain it later.

### Initialisation
What is in the folder. What are we looking at?

#### git init

!!! Demo
    Run `git init` and take a look at the folder. Make sure people can see hidden files.

### Writing first file
Git files exist in several states:

- untracked
- tracked and unmodified
- tracked and modified
![Git workflow](/../assets/img/git-fundamentals/git-workflow.png)

Tracked modified files can be in two states: staged or unstaged.

let's make some changes and then see how it looks.

#### git add
``` 
    touch README.md
    touch main.R
    vim README.md
    git add README.md
```

Git add has several shorthands to add all files you have changed.
```
    git add .
    git add --all
```

!!! Demo
    Create README.md and main.R file

now let's learn a seccond command
#### git status

What happens if you add and then change again file before commit?

``` 
    git status
    git status -s
```

!!! Demo
    After staging README.md, make some modifications and then run git status again. What is weird. Explain what is going on with the readme. How can it be staged and modified??


#### git diff

Git diff allows to compare what changed in what file in history

Different types of diffs
```
    git diff #diffs all the files that are tracked
    git diff path/to/file.R #diffs changes in that particular file
    git diff 243a6 #diffs changes vs particular commit in history   
    git diff path/to/file.R 24b3a6 #diffs changes of a file vs particular commit/branch
```

#### git reset
Git reset allows removing files from staged area. It doens't modify nor change the file, it only unstages it.
```
    git reset Main.

```

#### git commit
When satisfied, you can commit those files you have to the repository. Each commit needs to have an author and message.

You might be asked to set user.email and user.name. Keep them same to your github/bitbucket accounts if you want the commits to be Yours.

```
git config --global user.email "your@email.com
git config --global user.name "yourname"
```

When you are defined as a user, you can commit files.
```
git commit
```

Shorthand for commit with a message is
``` 
git commit -m "Initial commit"
```

!!! Practice
    Now make simple modifications to Main.R to load bob ross paintings from [here](https://raw.githubusercontent.com/fivethirtyeight/data/master/bob-ross/elements-by-episode.csv) into variable called `df_bob`. 
    
    Check status of your branch. Stage the file and commit it with some message.

#### git log

After you have done these two commits, we can look at how our history looks 

```
git log
git log -2
git log ---graph
git log -p -1
git log --pretty=online
```

### Changing files (and our mind)

Now we have few files, we can get into the core of git. but first, screw up our perfect bob ross loading

!!! Task
    Make a purposeful mistake in the bob ross file so that it now doesn't load anything. DO NOT COMMIT!

!!! Practice
    Use git diff to see what exactly is now different.

#### git checkout
Now we know we did something bad and we haven't commit anything yet, we can easily load past version of the file, with checkout. 

!!! WARNING
    Git checkout overwrites all changes done to the file. If you want to keep some version, you need to either `git stash` or `git branch`

```
    git checkout Main.R
```

#### git reset
Hard resetting files is not actually the best way of handeling stuff and that's why there isn't a simpler way in git to do that.

After reset you can checkout only a single file. 

#### git rm
Removes file form HDD as well as git in the next stage. 

``` 
```

!!! Demo
    Create a file called bad.R. Add and commit it. Remove it in the next commit.

If you want to keep the file on HDD but remove it from git, you can do that as well

```
    git rm --cached HIDDEN_FILE
```

!!! Demo
    Create a HIDDEN_FILE file and commit it. Then realise your mistake and remove it but keep it on HDD. WARNING: this file will still show in ONLINE history, so beware what was in it before you purged it

### Reseting strategies

#### Git

### Connecting to the internet

Main rule - what is online is LAW! That is the best version of the project. If you want to revert mistakes, you can actually rewrite online version, but you should NEVER do that in collaborative processes.

#### git remote
Multiple remotes?

#### git push

!!! Warning
    Pushing reverted

#### git fetch

#### git pull

#### .gititnore
Git tracks every file inside your directory, but sometimes you don't want that. 

E.G unity creases Library/Temp folders, that you NEVER commit. Same for Matlab asc files, R .RHistory/.RData files etc. 

it would be bothersome to always look at those files as being untracked, so we cna remove them completely.

``` 
    touch .gitnigore
    vi .gitignore
```

Github has many gitignores ready for your projects [HERE](https://github.com/github/gitignore)

!!! Important
    remember you need to ADD and commit .gitignore so that this ignoring information carries accross PCs.

!!! Demo
    Create a text file notes.txt. Put some stuff in and run `git status`. We don't want it. create .gitignore. Now we are good. Clone the repo to a different folder and create notes.txt in that clones. We need to recreate the .gititnore. Show a better way. Add and commit .gitignore.


### Git trees

#### git branch

#### git merge

mergin local branchs

merging remotes

### Cleaning up

#### git rm --cached <file>


`git clean`
`git fetch --prune`
`git branch -d -D`

