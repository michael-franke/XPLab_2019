# Working with a local repository

## Creating a repository

- open a command line tool
- create a folder of your choice
  - e.g., `mkdir my_first_git`
  
## Adding a file

- go to this directory and initialize
  - e.g., `cd my_first_git && git init`
- add a file called `mynotes.md` to the directory
- open the file with a text editor
- type some markdown & save the file
  - make sure to write several lines
- inspect the status with `git status`
- add the file to version control with `git add mynotes.md`
- inspect the status with `git status` again
- now commit your changes with `git commit -m "my first commit"`
- inspect the status with `git status` again
- look at the log history of your repo with `git log`

## Add another file

- create another file called `mynotes_2.md`
- fill in some content of your choice
- add it to version control using the same procedure as before

## Seeing current changes

- make some edits to `mynotes.md`
  - add text in some lines
  - delete some text in existing lines
- inspect the status with `git status`
  - this tells you which files changed, but not how exactly
- type `git diff mynotes.md` to see changes between last commit & current version
 - commit these changes
- type `git diff mynotes.md` again

## Seeing changes between commits

- you can see what changed **in all files** from COMMIT-1 to COMMIT-2 by typing `git diff mynotes.md COMMIT-1 COMMIT-2`
  - here COMMIT-x is the commit ID (which you find in the output of `git log`)
- zoom in on changes in file `mynotes.md` with `git diff mynotes.md COMMIT-1 COMMIT-2 -- mynotes.md`
- type `git log -p mynotes.md` to get a full change history of file `mynotes.md`

## Undoing staging

- make changes to your file `mynotes.md`
- stage the changes with `git add mynotes.md`
- look at `git status` (boring!)
- to unstage these changes type `git reset mynotes.md`
- look at `git status` again
- check whether your changes got lost (using what you learned above)

## Undoing local changes

### Single files

- type `git checkout mynotes.md` to undo your recent local changes
- check the status and the diff between local file and last commit

### Whole repo

- change both of your files & inspect the status
- type `git reset --hard` to undo all local changes
- inspect status to verify

## Going back in time

- retrieve the (shortened) commit ID of your first commit by `git log --oneline`
- type `git checkout FIRST-COMMIT-ID` to roll back complete to where you were in the beginning

## Branching

- so far our history of developments was linear; it's time to change that
- create a new branch with `git branch silly_try`
- switch to that new branch with `git checkout silly_try`
- add one or more lines with text at the beginning (!) of `mynotes.md`
  - don't change anything else in the file!
- add & commit the changes with `git commit -a -m "changes to a branch"` 
- look at your history now with `git log --graph --oneline --all`
  - we now live in a branching-time universe
  - different developments of your project live next to each other
   
## Merging

- we will now bring parallel universes together
- switch back to the master branch with `git checkout master`
- merge the changes into the master branch with `git merge silly_try`
  - if we are lucky git will merge automatically
  - if not, there will be so-called merge conflicts
  - if you have merge conflicts, you will need to resolve them manually
- commit your changes with `git commit -a -m "merged in branch silly_try"` 
- have a look at your history with `git log --graph --oneline --all`


## Resolving merge conflicts

### General information

- when a conflict occurs and git cannot merge automatically, it creates a new file in which both changes are kept side by side
- the user must then decide by hand which changes to keep or how to merge
- use will find tools of your taste for doing this by searching the internet

### Creating and resolving a conflict

- make sure you are in branch `master`
- edit part of the first line of `mynotes.md`
- commit the changes
- switch to branch `silly_try`
- edit *another* part of the first line of `mynotes.md`
- commit the changes
- switch back to branch `master`
- merge the changes from `silly_branch` into `master`
  - use: `git merge silly_branch`
- you will now see a message about merge conflicts
- open `mynotes.md` and fix the conflict manually
- then commit your changes as usual


# Working with a remote repository

## Creating and linking the remote repository

- create a remote repository, e.g., on GitHub
- link your local repo to the global one with `git remote add origin YOUR-REPO-URL`
  - now `origin` is the name for your remote repo

## Pushing and pulling

- **pushing** is when you "upload" local changes
- **pulling** is when you "download" remote changes
  - merge conflicts can arise just like when merging branches
  
  
  









