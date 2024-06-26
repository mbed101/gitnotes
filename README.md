# gitnotes
important commands using git. Minimalism is emphasized

# Initialize a github empty new repo
-----------------------------------
## create a new repository on the command line
```bash
echo "# pyNotes" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:mbed101/pyNotes.git
git push -u origin main
```

## …or push an existing repository from the command line
```bash
git remote add origin git@github.com:mbed101/pyNotes.git
git branch -M main
git push -u origin main
```

# Clone a repo
------------
```bash
git clone \<url\> <br>
cd \<dir\>  <br>
git pull
```

# New Branch
-------------
```
git branch spielwiese/mand (new branch) <br>
git pull <br>
git branch --set-upstream origin spielwiese/mand <br>
git checkout spielwiese/mand  (to change to already existing branch) <br>
```

# Commit:
---------
```
git commit -am "msg" <br>
git push <br>
```

# Delete local branch
---------------------
link: https://www.git-tower.com/learn/git/faq/delete-local-branch/

git branch -d feature/showImageVersion
- but switch to another branch before deleting this 
- if remote is already pushed, then delete remote using 
	git push origin --delete <remote-branch-name>

force delete local -> git branch -D feature/showImageVersion

#Merge:
----------
to merge hotfix to master
1. checkout to master <br>
2. run merge with the branch name that the changes from this branch to be merged to master <br>

```
git checkout master <br>
git merge hotfix <br>
git pull <br>
git push <br>
```

Example: Merge develop from remote to local branch features/msvcCompiler
```
git pull <br> 
git merge origin/develop <br>
git push <br>
```
:warning: Dont forget **git push** after Merge!!

After merge delete the hotfix branch
git branch -d hotfix

Merge RESET:
git merge --abort

Reset last commit 
----------------------
git reset --soft HEAD~1

Reset last merge
----------------------
git reset --merge HEAD~1

Undo last Reset
---------
git reset 'HEAD@{1}'

Reset only one file from another commit
------------------------------------------
git checkout 5670de57 -- Project_BIN/Release/AppSystem.ini

where,  commit to take be applied (wished) = 5670de57 

## Show Last commit message

git log -1 

### Show last 2 commt messages 

git log -2

Deleted a file locally and didnt yet commit
-------------------------------------------
So you deleted a file, and immediately realized it was a mistake? This one is easy, just do: <br>
$ git checkout HEAD \<filename\>

Reset all files in the folder to the remote GIT Repo
----------------------------------------------------
git restore --source=HEAD --staged --worktree -- aDirectory
#### (shorter as follows) 
git restore -s@ -SW -- aDirectory    <br/>

where 'aDirectory' is the directory name u want to restore

Update submodules of an already cloned repo
------------------------------------------------
git submodule update --init --recursive

Rebase and squash within a branch (eg. bugfix branch)
------------------------------------------------
git rebase -i HEAD~3  <br>
.. where 3 is the number of commits to be squashed <br>
.. then in the i ( interactive) mode, leave the first command in vim to 'pick' but change other picks to 'squash' and then edit the commit for this commit(squash)  <br>
... this will squash all the 3 commits in the HEAD into one to clean up the branch <br>

more tutorial: [https://docs.gitlab.com/ee/topics/git/git_rebase.html](https://docs.gitlab.com/ee/topics/git/git_rebase.html#rebase-interactively-by-using-git)

Force change the author of the last commit 
----------------------------------------------
git commit --amend --author="New Author Name <new.email@example.com>" --no-edit

This will directly apply the change without opening the editor.

After amending the commit with the new author's name, you may need to force push the changes to the remote repository if the commit is already pushed:

git push origin HEAD --force

