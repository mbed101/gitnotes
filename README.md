# gitnotes
important commands using git. Minimalism is emphasized

Clone a repo
------------
git clone \<url\> <br>
cd \<dir\>  <br>
git pull

New Branch
-------------
git branch spielwiese/mand (new branch) <br>
git pull <br>
git branch --set-upstream origin spielwiese/mand <br>
git checkout spielwiese/mand  (to change to already existing branch) <br>

Commit:
---------
git commit -am "msg" <br>
git push <br>

Delete local branch
---------------------
link: https://www.git-tower.com/learn/git/faq/delete-local-branch/

git branch -d feature/showImageVersion
- but switch to another branch before deleting this 
- if remote is already pushed, then delete remote using 
	git push origin --delete <remote-branch-name>

force delete local -> git branch -D feature/showImageVersion

Merge:
----------
to merge hotfix to master
1. checkout to master <br>
2. run merge with the branch name that the changes from this branch to be merged to master <br>

git checkout master <br>
git merge hotfix <br>
git pull <br>
git push <br>

Example: Merge develop from remote to local branch features/msvcCompiler
git pull <br> 
git merge origin/develop <br>
git push <br>

:warning: Dont forget **git push** after Merge!!

After merge delete the hotfix branch
git branch -d hotfix

Merge RESET:
git merge --abort

Reset last commit 
----------------------
git reset --soft HEAD~1

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
