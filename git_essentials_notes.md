## check settings
git config --list

##
git config --global user.name "ArunNadda"
git config --global user.email "arunnadda@gmail.com"
git config --global color.ui "auto"

## windows
git config --global core.editor "'c:/program files/.....'"

## check settings
git config --list




## understaning Git - basics
cd <dir>
git init
-- create file
git status

git add <filename>

git log

git log --oneline

##  git diff to check differece between file last known state and current state
git diff

git diff --staged ## check diff in files which is in staged area and production area


## look around
## HEAD - current snapshot of folder we are looking at
git diff HEAD~1
git diff HEAD~2

git log


git diff <versionID> ### diff is from current status of file



### revert back to earlier version -- git checkout
git diff
git checkout HEAD~1 README.md
## DACG -- this is how git saves data
git checkout master

git reset HEAD <file Name>



## reset file to last status
git reset --hard

## remove file from staging area
git reset -HEAD



##################################################################
## ignore things in git


## create new folders in original dir
## create .gitkeep file to force git to detect it



## .gitignore file, can be used to ignore files which are not required to be added for git versioning
## this file should be under mail dir where .git dir is there
## we can use patterns in .gitignore file.
## e.g. *.aux
##      *.pdf
##        etc


## if add a file which is ignored , use -f
git add -f nobel.pdf



#############################################################################
## Remote and branches

## github, bitbucket, gitlab


## use remotes with https
## use push and pull



git remote add origin https://github.com/ArunNadda/git_learn.git
anadda (master *) git_learn $ git remote -v
origin  https://github.com/ArunNadda/git_learn.git (fetch)
origin  https://github.com/ArunNadda/git_learn.git (push)
anadda (master *) git_learn $ git push

anadda (master *) git_learn $ git remote -v
origin  https://github.com/ArunNadda/git_learn.git (fetch)
origin  https://github.com/ArunNadda/git_learn.git (push)
anadda (master *) git_learn $ git push origin master
Counting objects: 25, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (22/22), done.
Writing objects: 100% (25/25), 2.87 KiB | 0 bytes/s, done.
Total 25 (delta 6), reused 0 (delta 0)
remote: Resolving deltas: 100% (6/6), done.
To https://github.com/ArunNadda/git_learn.git
 * [new branch]      master -> master
anadda (master *) git_learn $



##########################################################################
##use remote with ssh
##create ssh pub key files
## final configuration is done with ssh.
## delete https repository and then remove from laptop using
git remote remove origin


#########################################################################
resolving conflict if file is modified locally and remote both.

## use github for project management


#########################################################################
## use branches

anadda (master *) src $ git branch my_branch
anadda (master *) src $ git branch -a
* master
  my_branch
  remotes/origin/master
anadda (master *) src $


anadda (master) src $
anadda (master) src $ git checkout my_branch
Switched to branch 'my_branch'
anadda (my_branch) src $ git status
On branch my_branch
nothing to commit, working tree clean
anadda (my_branch) src $

anadda (my_branch) src $ git branch -a
  master
* my_branch
  remotes/origin/master
anadda (my_branch) src $


anadda (my_branch) src $ git checkout -b my_branchy_checkout
Switched to a new branch 'my_branchy_checkout'
anadda (my_branchy_checkout) src $ git status
On branch my_branchy_checkout
nothing to commit, working tree clean
anadda (my_branchy_checkout) src $ git branch -a
  master
  my_branch
* my_branchy_checkout
  remotes/origin/master
anadda (my_branchy_checkout) src $


## delete branch
#########################

anadda (my_branchy_checkout) src $ git branch -a
  master
  my_branch
* my_branchy_checkout
  remotes/origin/master
anadda (my_branchy_checkout) src $ git branch -d my_branch
Deleted branch my_branch (was 8d2a6c0).
anadda (my_branchy_checkout *) src $ git branch -d my_branch_checkout
error: branch 'my_branch_checkout' not found.
anadda (my_branchy_checkout *) src $ git branch -d my_branchy_checkout
error: Cannot delete branch 'my_branchy_checkout' checked out at 'C:/Users/anadda/git_learn'
anadda (my_branchy_checkout *) src $ git checkout master
error: Your local changes to the following files would be overwritten by checkout:
        git_essentials_notes.txt
Please commit your changes or stash them before you can switch branches.
Aborting
anadda (my_branchy_checkout *) src $ git status
On branch my_branchy_checkout
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   ../git_essentials_notes.txt

no changes added to commit (use "git add" and/or "git commit -a")
anadda (my_branchy_checkout *) src $ git add ../git_essentials_notes.txt
anadda (my_branchy_checkout +) src $ git commit -m "notes added - git branch"
[my_branchy_checkout a436eb2] notes added - git branch
 1 file changed, 87 insertions(+)
anadda (my_branchy_checkout) src $ git status
On branch my_branchy_checkout
nothing to commit, working tree clean
anadda (my_branchy_checkout) src $ git commit master
error: pathspec 'master' did not match any file(s) known to git.
anadda (my_branchy_checkout) src $ git checkout master
Switched to branch 'master'
anadda (master) src $ git branch -a
* master
  my_branchy_checkout
  remotes/origin/master
anadda (master) src $ bit branch -d my_branchy_checkout
bash: bit: command not found
anadda (master) src $ git branch -d my_branchy_checkout
error: The branch 'my_branchy_checkout' is not fully merged.
If you are sure you want to delete it, run 'git branch -D my_branchy_checkout'.
anadda (master) src $ git branch -D my_branchy_checkout
Deleted branch my_branchy_checkout (was a436eb2).
anadda (master) src $









anadda (master *) src $ git branch -a
* master
  my_branch
  remotes/origin/master
anadda (master *) src $ git checkout my_branch
M       git_essentials_notes.txt
Switched to branch 'my_branch'
anadda (my_branch *) src $
anadda (my_branch *) src $ git checkout master
M       git_essentials_notes.txt
Switched to branch 'master'
anadda (master *) src $ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   ../git_essentials_notes.txt

no changes added to commit (use "git add" and/or "git commit -a")
anadda (master *) src $ git add ../git_essentials_notes.txt
anadda (master +) src $ git commit -m "more notes added to notes file"
[master 8656445] more notes added to notes file
 1 file changed, 81 insertions(+)
anadda (master) src $ git status
On branch master
nothing to commit, working tree clean
anadda (master) src $
anadda (master) src $ git checkout my_branch
Switched to branch 'my_branch'
anadda (my_branch) src $
anadda (my_branch) src $ git branch -a
  master
* my_branch
  remotes/origin/master
anadda (my_branch) src $
anadda (my_branch) src $





anadda (my_branch *) src $ git status
On branch my_branch
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   my_square.py

no changes added to commit (use "git add" and/or "git commit -a")
anadda (my_branch *) src $ python my_square.py
1936
Traceback (most recent call last):
  File "my_square.py", line 13, in <module>
    print(my-square2(44))
NameError: name 'my' is not defined
anadda (my_branch *) src $ vi my_square.py
anadda (my_branch *) src $ python my_square.py
1936
1936
anadda (my_branch *) src $

anadda (my_branch *) src $
anadda (my_branch *) src $ git status
On branch my_branch
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   my_square.py

no changes added to commit (use "git add" and/or "git commit -a")
anadda (my_branch *) src $ git branch -a
  master
* my_branch
  remotes/origin/master
anadda (my_branch *) src $ git add .
anadda (my_branch +) src $ git commit -m "added 2nd funtion to my_square.py"
[my_branch bd4f1a1] added 2nd funtion to my_square.py
 1 file changed, 5 insertions(+), 1 deletion(-)
anadda (my_branch) src $ git status
On branch my_branch
nothing to commit, working tree clean
anadda (my_branch) src $
anadda (my_branch) src $
anadda (my_branch) src $



anadda (my_branch) src $ git log --oneline --all
bd4f1a1 added 2nd funtion to my_square.py
8656445 more notes added to notes file
f463ba8 notes file updated till using remote
8d2a6c0 Merge branch 'master' of github.com:ArunNadda/git_learn
1822c41 added documentation to my_square.py about operator.
7c19b01 changed 3 to 4 in my_square.py
b9984d2 added documentation to my_square.py
dd8bdd9 python script square
4562e64 Modified Readme
f4876d0 notes - ignore files in git
1cc75b2 create data docs output and src directories
039a333 notes - add git reset
e0f032c notes - using HEAD and checkout
f9c9a87 Added git diff commands to notes file
e00b0f9 git notes added
bb00eb3 notes file added
359196a Readme file commit
anadda (my_branch) src $ git checkout master
Switched to branch 'master'
anadda (master) src $ git log --oneline --all
bd4f1a1 added 2nd funtion to my_square.py
8656445 more notes added to notes file
f463ba8 notes file updated till using remote
8d2a6c0 Merge branch 'master' of github.com:ArunNadda/git_learn
1822c41 added documentation to my_square.py about operator.
7c19b01 changed 3 to 4 in my_square.py
b9984d2 added documentation to my_square.py
dd8bdd9 python script square
4562e64 Modified Readme
f4876d0 notes - ignore files in git
1cc75b2 create data docs output and src directories
039a333 notes - add git reset
e0f032c notes - using HEAD and checkout
f9c9a87 Added git diff commands to notes file
e00b0f9 git notes added
bb00eb3 notes file added
359196a Readme file commit
anadda (master) src $ git log --oneline --all --decorate --graph
* bd4f1a1 (my_branch) added 2nd funtion to my_square.py
| * 8656445 (HEAD -> master) more notes added to notes file
|/
* f463ba8 notes file updated till using remote
*   8d2a6c0 (origin/master) Merge branch 'master' of github.com:ArunNadda/git_learn
|\
| * 1822c41 added documentation to my_square.py about operator.
* | 7c19b01 changed 3 to 4 in my_square.py
|/
* b9984d2 added documentation to my_square.py
* dd8bdd9 python script square
* 4562e64 Modified Readme
* f4876d0 notes - ignore files in git
* 1cc75b2 create data docs output and src directories
* 039a333 notes - add git reset
* e0f032c notes - using HEAD and checkout
* f9c9a87 Added git diff commands to notes file
* e00b0f9 git notes added
* bb00eb3 notes file added
* 359196a Readme file commit
anadda (master) src $



## branch merge

anadda (master) src $
anadda (master) src $ git status
On branch master
nothing to commit, working tree clean
anadda (master) src $ git branch -a
* master
  my_branch
  remotes/origin/master
anadda (master) src $ git merge my_branch
Merge made by the 'recursive' strategy.
 src/my_square.py | 6 +++++-
 1 file changed, 5 insertions(+), 1 deletion(-)
anadda (master) src $ git status
On branch master
nothing to commit, working tree clean
anadda (master) src $ cat my_square.py
def my_square(x):
        """
        takes a value and returns the squared value.

        uses ** operator
        """
        return (x ** 2)

def my_square2(z):
        return (z * z)

print(my_square(44))
print(my_square2(44))
anadda (master) src $


anadda (master) src $ git push origin master
Counting objects: 12, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (12/12), done.
Writing objects: 100% (12/12), 2.92 KiB | 0 bytes/s, done.
Total 12 (delta 6), reused 0 (delta 0)
remote: Resolving deltas: 100% (6/6), completed with 1 local objects.
To git@github.com:ArunNadda/git_learn.git
   8d2a6c0..53eb597  master -> master
anadda (master) src $

anadda (master) src $



####################################################################
git fetch --prune
git branch -a



####################################################################

git workflow:
=============

git rebase master (-- to make sure to rebase branches with master)
git push origin development




####################################################################

incorporating changes after you branch:
========================================
-- bug fix branch
git push -f origin development (force)
