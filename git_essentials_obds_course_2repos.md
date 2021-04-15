# **Git essentials**

### For the OBDS course you have 2 repositories (repos)

- i'm really sorry they are so confusingly named

    A) `OBDS_Training_Jan21` ->
    the repo containing all the shared code we are writing in the course

    B) `obds_training` ->
    your personal repo where you can put copies of code that are just for you

### We have copies of these 2 repositories in 3 locations

#### 1) Github (online)
- The `OBDS_Training_Jan21`  repo  belongs to the `OBDS_Training organisation`

        https://github.com/OBDS-Training   
        you can all see, use and commit changes to this.


- Your personal `obds_training` repo is on `your personal github` account
        e.g. https://github.com/Charlie-George
        only you can edit and make changes to this


#### 2) On the cgat cluster

- in your directory on the cgat cluster  (e.g. `/ifs/obds-traning/jan21/charlie/devel`) you have a copy of both

    -  the shared `OBDS_Training_Jan21` repo   (i.e. your copy of the shared repo)
            e.g. `/ifs/obds-training/jan21/charlie/devel/OBDS_Training_Jan21`

    - your personal `obds_training` repo      (i.e your copy of your personal repo)
            e.g. /ifs/obds-training/jan21/charlie/devel/obds_training

#### 3) On your laptop/local machine (wherever you put them in week1)

- the shared OBDS_Training_Jan21 repo   (i.e. your copy of the shared repo)

        e.g. /ifs/obds-training/jan21/charlie/devel/OBDS_Training_Jan21

-  your personal obds_training repo      (i.e your copy of your personal repo)
            e.g. /ifs/obds-training/jan21/charlie/devel/obds_training


--------------------------

### The three copies of the repos are linked by pushing to github and pulling from github
```
   cgat cluster copy of                   github copy of                     laptop copy of shared
shared OBDS_Training_Jan21  <------->  shared OBDS_Training_Jan21 <------> OBDS_Training_Jan21 repo
```
```
  cgat cluster copy of your             github copy of your                          laptop copy of
personal obds_training repo <-------> personal obds_training repo  <-----------> personal obds_training repo

```

## **Using git**
================

## Before you do anything in git **always** do these three things!


1) `git status` # check your status - do you need to add file

2) `git branch` # check what branch you are on

3) `git pull` # make sure your branch is upto date with github

*When you try the above your might get error messages from git* - read these carefully!!!


- e.g. `your branch is ahead` -> you have changes on your files that github (or the branch your switching to) doesn't
            git add file.txt
            git commit -m 'updated file'
            # you can now carry on with what you were trying to do

- `your branch is behind` -> there are changes on github that you don't have
            git pull   # gets changes from github

- `merge conflict` - your file and the one from github is different
    - you've tried git pull and git's tried to merge these files together but knows its got something wrong
    - it wants you to check the file its made (look for the file name in the error message)
    - open the file in `nano` or `atom` and look for lines that say
            <=========== HEAD   
                or
             ==========>
    - `delete these lines` and anything else that looks weird
    - it will state both the github version and your version of lines its not sure about
    - you need to delete the one you want to get rid of then `save file`
    ```
        git add file
        git commit -m 'fixed merge'
        git push
    ```


### If you have made changes (or created a file) you need to add and commit them
```
git add file.txt
git commit -m 'made file'
```
### Send your files to github
```
git push
```

### Get updated files from github
```
git pull
```

## Git Branching

### Check what branch your on
```
git branch
```

### Making a branch

```
# make sure your on master and do git pull first to to most up to date copy of code from github

git checkout master

# if it doesn't let you you might need to `git add` and `git commit -m message` your files first

git pull

# make branch in your code folder and switch to it (this branch doesn't exist on github until you push it)
git checkout -b new_branch_name

# this creates and pushes your branch up to github
git push --set-upstream origin new_branch_name
```

### Getting a branch someone else has created from github
```
git fetch  # let git see all new branch names
git checkout --track origin/new_branch_name   # this gets branch from github and moves you to that branch
```
### Make edits on a branch and push code to github
```
git pull  # get latest changes from github
git add file.txt
git commit -m 'editted file'
git push
```
### Switch between branches
```
git checkout branchname
```

### Delete a branch
```
git checkout master      # you might need to commit and add you files before it lets you move
git branch -d branch_name
```
#### Sometimes if you switch branch and the folder you were in doesn't exist on the other branch you might get:
```
'fatal - this is not a git repository'
```
Just do `cd /full/path/back/to/where/you/want/to/go`  replace the path with where you want to go
