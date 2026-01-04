# GIT & GIT HUB – COMPLETE PRACTICAL NOTES

---

## Initial Setup

Download VS Code -> Download Git -> Create a folder named **VIJAY GUPTA GIT** in file Explorer -> Open VS CODE -> file -> open folder -> select **VIJAY GUPTA GIT** folder

---

## What is GIT?

* Git is a version control system.
* It's like a time machine of your code.

### With Git:

* You can track changes made to your code.
* You can go back in time to see the older versions.
* You can work in teams without messing up each other's work.

---

## What is GitHub?

GitHub is a platform to host you Git repositories online.

* Git is the tool you use on your local computer.
* GitHub is where you store and share your Git projects on the cloud.
* You can collaborate with others, review code, track issues....etc.

---

## What is REPO?

A repository (repo) is just a project folder tracked by Git.

* Contains your code, documentation, and history of changes.
* Can be stored locally (on your machine) or remotely (on GitHub).
* Ex: Root folder (VIJAY GUPTA GIT)

---

## VS Code Extension

Now open VS Code:

1 very useful extension that is useful to vizualise the changes you made to your repo, commits...etc.

**Git Graph -> Install**

---

## Converting Folder into Git Repo

As of now **VIJAY GUPTA GIT** is just a folder in your file explorer, in order to convert that into repo you need to do Git Initialize.

Open the Terminal: **ctril + shift + `**

Everytime you work you need to run ->

### 1️. Check status

```
git status
```

(it shows if our folder is folder or repo)

---

## Git Initialize & Configuration

### Configure email

```
git config -- global user.email "eswargupta@gmail.com"
```

* This is useful to know that the particular person had commited the change.
* When pushing the code to repo, this email is shown.

### Configure username

```
git config --global user.name "vijaygupta"
```

### Check status

```
git status
```

### Initialize repo

```
git init
```

### Check status again

```
git status
```

---

## .git Folder

.git folder

* search (vs code) -> >preference: open settings (ui) -> go down -> .git remove it.

.git is the backbone of git, its like the b acckbone of all the commits you do.

---

## git status tells 2 things:

1. branch name
2. commits

---

## Git Branch

```
git branch
```

* It will list out all the branches.
* git will not recognise if your branch has no commits.
* Meaning, when you write git branch command it will give you the list of branches that have commits.

So for the initial commit, people commit **readme.md** file.
This is widely common practice followed all over the industry.

---

## First Commit

### To commit the changes:

```
git add .
git commit -m "initial commit"
```

```
git branch
```

* now it will show the branch name, as the branch now is regestered as you commited the initial change.

---

## Git Flow

```
Working Directory ----------> Staging Area (Snapshot) --------> Repository
```

If you worked on 2 sql files, not commited those changes, then those changes are in working directory.

If you have commited, then those changes went to repository.

---

## Staging Area

Statging area?

* We cna select what are all the files we need to commit.

### File States:

```
Working Directory ----------> Staging Area (Snapshot) --------> Repository
Untracked                                  Staged                                          Committed
```

For Untracked + new files we see symbol -> **'U'**
For untracked + old files, you will not see **'U'** because as they were old files, that will be tracked by git repo.

---

## Create File via Terminal

This command is to create the file:

```
echo "This file relatest to copy activity" > copy_activity.txt
```

### Move file to staging area:

```
git add file_name
git commit -m "Message"
```

If you modify the existing file, you see **'M'** symbol.
Because this is being tracked by git.

---

## HEAD & Logs

HEAD -> Latest commit

### Logs

```
git log
git log --oneline
```

* It has Metadata, details, Information.
* Here we will get to know the commits you made, commit id, user id, date...etc.

---

## Git Ignore & Git Keep

If you need to commit api keys into your repo, we should not show them to every one in repo.
So we create **.gitignore** file and add those files in that file.

Git do not track empty folders.

If you need to track the empty folders, we ned to add **.gitkeep** file in that folder.

---

## Feature Branch Creation

### 1️. Switch to main branch

```
git switch dev_main
git checkout dev_main
```

### 2️. Create branch

```
git checkout -b vijay_gupta_branch
git switch -c vijay_gupta_branch
```

```
git branch
```

---

## Merge Feature Branch

### 1️. Go to main branch

```
git checkout dev_main
```

### 2️. Merge

```
git merge feature_branch -m "message"
```

---

## Merge Conflicts

Merge conflicts occur when 2 developers work on the same file.

```
git merge --abort
```

But abort will abort the other changes in that branch as well.

### Solution:

Merge the branch and eliminate the conflict

After resolving the merge conflicts:

```
git add .
git commit -m "conflicts resolved"
```

Senario in which if 2 developers woek on same file and does not give conflicts

---

## Git Rebase

While you work…

* Your teammate pushes new code to main
* They fix bugs
* They add new features
* Now main moved forward and became newer than your branch

So your branch is behind.

Manager says:

“Before you add your login work, make sure your branch has the latest code from main!”

### Choices:

* Merge → your branch will mix with main
* Rebase → your branch will restart from the latest main, then apply your work

---

## Git Rebase Graph

### Before rebase

```
feature-branch (your work)
                      *
                      *
                      *
main  *----*----*----*----*
       A    B    C    D    E
```

### Command

```
git rebase main
```

### After rebase

```
main  *----*----*----*----*
       A    B    C    D    E
                                   *
                                   *
                                   *
```

Final history becomes **straight and clean**

---

## Rebase & Fast Forward Merge

```
git checkout feature_branch
git rebase dev_main
git add .
git merge -m "merged"
```

```
git rebase --abort
```

---

## Time Travelling in Git

```
git log --oneline
git reflog
```

* git reflog is advanced version
* Shows commit id and HEAD block

### Recover deleted file

```
git reset --hard commit_id
git reset --hard HEAD~1
```

---

## git diff

```
git diff
```

* It tells the differnce between files in working directory and staging area

---

## Move from staging to working directory

```
git reset
```

---

## Cherry Pick

```
git cherry-pick 2701481
```

Use case:

* Production Hotfix

---

## Git Stashing

Git stash = temporary storage for your uncommitted changes.

### Commands

```
git stash push -m "my work paused"
git stash list
git stash apply
git stash pop
git stash drop
git stash clear
```

---

## GITHUB BASICS (CLEAN SUMMARY)

### First time push

```
git config --global user.email "your@email.com"
git config --global user.name "yourusername"
```

Create GitHub repo → Create PAT → Add remote → Push

```
git remote add origin "<repo-url>"
git remote -v
git branch -m main
git pull origin main --allow-unrelated-histories
git push origin main
```

---

## End to End Corporate Workflow

```
git clone <repo-url>
git switch -c feature-login
git add .
git commit -m "login feature added"
git push origin feature-login
```

Create PR → Review → Merge → Delete branch

---
