GIT & GIT HUB

Download VS Code -> Download Git -> Create a folder named VIJAY GUPTA GIT in file Explorer -> Open VS CODE -> file -> open folder -> select VIJAY GUPTA GIT folder

What is GIT?
- Git is a version control system.
- It's like a time machine of your code.

With Git:
- You can track changes made to your code.
- You can go back in time to see the older versions.
- You can work in teams without messing up each other's work.

What is GitHub?
GitHub is a platform to host you Git repositories online.

- Git is the tool you use on your local computer.
- GitHub is where you store and share your Git projects on the cloud.
- You can collaborate with others, review code, track issues....etc.

What is REPO?
A repository (repo) is just a project folder tracked by Git.

- Contains your code, documentation, and history of changes.
- Can be stored locally (on your machine) or remotely (on GitHub).
- Ex: Root folder (VIJAY GUPTA GIT)


Now open VS Code:
1 very useful extension that is useful to vizualise the changes you made to your repo, commits...etc.
Git Graph -> Install

As of now VIJAY GUPTA GIT is just a folder in your file explorer, in order to convert that into repo you need to do Git Initialize.

Open the Terminal: ctril + shift + `
Everytime you work you need to run -> 

1. git status (it shows if our folder is folder or repo)

Now how to convert from folder to git repo?

Git Initialize:

2. git config -- global user.email "eswargupta@gmail.com"
- This is useful to know that the particular person had commited the change.
- When pushing the code to repo, this email is shown.


3. git config --global user.name "vijaygupta"

4. git status

5. git init

6. git status

.git folder
- search (vs code) -> >preference: open settings (ui) -> go down -> .git remove it.

.git is the backbone of git, its like the b acckbone of all the commits you do.

git status tell 2 things:
1. branch name
2. commits

git branch
- It will list out all the branches.

git will not recognise if your branch has no commits. Meaning, when you write git branch command it will give you the list of branches that have commits.

So for the initial commit, people commit readme.md file. This is widely common practice followed all over the industry.

Now to commit the changes:

1. git add .
2. git commit -m "initial commit"

git branch
- now it will show the branch name, as the branch now is regestered as you commited the initial change.


FLOW:

Working Directory ----------> Staging Area (Snapshot) --------> Repository


If you worked on 2 sql files, not commited those changes, then those changes are in working directory.

If you have commited, then those changes went to repository.

Statging area?
- We cna select what are all the files we need to commit.

File States:

Working Directory ----------> Staging Area (Snapshot) --------> Repository
Untracked                                  Staged                                          Committed

For Untracked + new files we see symbol -> 'U'
For untracked + old files, you will not see 'U' because as they were old files, that will be tracked by git repo.

Create one file via UI.

This command is to create the file:
echo "This file relatest to copy activity" > copy_activity.txt

So if you want to move the changed file to staging area:

1. git add file_name

2. git commit -m "Message"


If you modify the existing file, you see 'M' symbol. Because this is being tracked by git.

HEAD -> Latest commit
------------------------------------
LOGS: (git log)
- It has Metadata, details, Information.
- Here we will get to know the commits you made, commit id, user id, date...etc.

git log --oneline (or) git log 

----------------------------------------

Git Ignore & Git Keep:

For instance, if you need to commit api keys into your repo, we should not show them to every one in repo. so we create .gitignore file and add those files in that file.

Git do not track empty folders.

If you need to track the empty folders, we ned to add .gitkeep file in that folder.

-------------------------------------------

Create the feature branch:

1. Go to main branch from where you need to create the feature branch.

git switch dev_main/ git checkout dev_main

2. Create the branch

git checkout -b vijay_gupta_branch / git switch -c vijay_gupta_branch

git branch -> shows the list of branches.


---------------------------------------------------

Merge the feature branch to dev_main:

1. Go to main branch (git checkout dev_main)

2. git merge feature_branch -m "message"

--------------------------------------------------


Merge Conflicts:

Merge conflicts occur when 2 developers work on the same file.

git merge --abort

But abort will abort the other changes in that branch as well. What's the solution in that case?

Ans: Merge the branch and eliminate the conflict

After resolving the merge conflicts
1. git add .
2. git commit -m "conflicts resolved"


Senario in which if 2 developers woek on same file and does not give conflicts

---------------------------------------------------------------------------------------

Git Rebase:

⏳ While you work…

- Your teammate pushes new code to main:
- They fix bugs
- They add new features
- Now main moved forward and became newer than your branch.

So your branch is behind.

💡 Now your manager says:

“Before you add your login work, make sure your branch has the latest code from main!”

You have 2 choices:

Merge → your branch will mix with main 
Rebase → your branch will restart from the latest main, then apply your work 


--------------------------------------------------------------------------
Here’s the Git graph explanation with a real rebase scenario:

---

✅ Before rebase


       feature-branch (your work)
                         *
                         *
                         *
main  *----*----*----*----*  (teammate pushed new updates)
          A    B      C    D    E


* You branched out at commit **C*
* Teammates added **D and E** to `main`
* Your branch is now **behind**

---

### 🧩 Command you run:

```
git rebase main
```

---

### ✅ **After rebase**

```
main  *----*----*----*----*
          A     B     C     D     E
                                        *
                                        *  ← feature-login (replayed)
                                        *
                                        *
```

Now Git does this internally:

1. Moves to latest `main` (E)
2. Takes your commits
3. **Replays them on top**
4. So it LOOKS like you started after E

Final history becomes **straight and clean**

-----------------------------------------------------------------------------------------


Rebase & Fast Forward Merge:

1. git checkout feature_branch
2. git rebase dev_main
3. git add .
4. git merge -m "merged"

git rebase --abort

----------------------------------------------------------------------------------------------


Now lets talk about Time Travelling in Git:

Go to master branch, delete the random file and commit.
git log --oneline

git reflog
- Its a advanced version of git log -oneline.
- Because you can see little more details here.

In order to time travel in git, git reflog is very useful.
- You get the commit id, HEAD block.


If you want to get back the deleted file:

1. git reflog, note the commit id and head position.
2. git reset --hard commit_id/HEAD~1

------------------------------------------------------------------


git diff
- It tells the differnce between files in working directory and staging area ,,,,etc.

---------------------------

If you want to move changes from staging area to working directory: git reset

---------------------------

Cherry Pick:

- We can actually pick the commits we want to merge to master barnch.

1. Pick the commit id that you want to merge in master. (git reflog)
2. Go to master branch.
3. git cheery-pick 2701481

To avoid any conflicts, commit id's should be in order. 

Most Common Real-World Use Case
1. Production Hotfix
- You fix a bug in the dev branch but want only THAT fix in production.
- Cherry-pick that commit → deploy.
------------------------------------------------------------------------------------


Git Stashing:

Its a temporory storage location that git provides to us.
Git stash = temporary storage for your uncommitted changes.


Why Do We Use Stash?

Scenario:
You're developing code → incomplete → manager calls → fix urgent bug.

You cannot commit (because code is incomplete).
You cannot switch branch (Git will stop you).

So you run:

git stash push -m "message"


Your progress moves into stash storage, making your working folder clean.

Working Directory → (stash push) → Stash Stack



1. Create a stash
git stash push -m "my work paused"

2. See stash list
git stash list

3. Apply stash (but keep stash)
git stash apply "stash@{0}"

Now commit the changes, and then apply git pop. Otherwise your changes will not be visisble.


If you omit the stash name:
git stash apply
→ applies latest stash.

➤ 4️⃣ Apply & Remove (POP)
git stash pop "stash@{0}"

➤ 5️⃣ Delete a specific stash
git stash drop "stash@{0}"

➤ 6️⃣ Clear all stashes
git stash clear


⭐ Real Corporate Use Case

During development:

You’re mid-way writing code

Get high-priority incident

Stash → switch → fix → come back → apply stash → continue

This is the most common daily git operation for developers.
------------------------------------------------------------------------------

GITHUB BASICS (CLEAN SUMMARY)

⭐ When pushing a local repo to GitHub for the first time

1️. Set user config (one time globally)
git config --global user.email "your@email.com"
git config --global user.name "yourusername"

2. Now we need to host our local repo to remote repo/github repo:

a. Go to github and create a new repo called someting like git & git hub.
b. Now you need to get personal access token. Go to settings -> developer settings -> personal access tokens(PAT) -> tokens (classic) -> copy the token.

c. Now to to your git repo -> code -> copy HTTPS

d. Add remote origin:
git remote add origin "<repo-url> "#http 

# origin is the destination where yo need to push your code.

https://github.com/vijaygupta944/Git-GitHub.git


d. git remote -v
- It's to check if the remote is linked or not.

5. Rename branch if needed: git branch -m main

6. git pull origin main
git pull origin main --allow-unrelated-histories

7. First push: git push origin main
---------------------------------------------------------------------------------------

End to end Cycle:

CLONE → FEATURE BRANCH → PR WORKFLOW

⭐ Most Realistic Company Workflow

First go to vs code -> open folder -> create new folder

1. Clone repo

git clone <repo-url>


2. Create feature branch

git switch -c feature-login


3. Do changes → commit

git add .
git commit -m "login feature added"


4. Push branch

git push origin feature-login


GitHub → Create Pull Request

Reviewer approves → Merge PR

Delete local/remote feature branch

This is how corporate teams work.
