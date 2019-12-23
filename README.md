
#### Git Tutorials
- It is a good behaviour to add README.md and LICENSE.

#### Remote
- `$git remote -v` (Show the remote repository url)
- `$git remote add origin [url]` (Add the remote repository to the local git project )
- `$git push -set-upstream origin master` (push to remote repository and start observing the master branch)

#### Creating Empty Directory
- `$touch tutorials/.keep` (create and empty folder)

#### Configuration
- `$git config --list` (shows the git configuration)
- `$git config --global --list` (show global git configuration)
- `$git config --local --list` (show local git configuration)

#### Revert
- `$git revert HEAD` (revert the staged changes)

#### git interactive adding
- `$git add -i` (interative adding)
type the first letter of the word to choose the option
```
s - status
u - commit the changes
r - revert the commit
p - patch the commit
```

for splitting the hunks press 'p' for part
there are lots of options 
```
? - help
y - stage the hunk
n - not stage the hunk
s - split the hunk 
```
- `$git mv [from_path] [to_path]`(moves the file and staged the change)
- `$git rm [path]`(deletes the file and staged the change)


#### git ignore
- `$vim .gitignore`

- `*.html` (All Files having the extension html)
- `!/*.html` (Doesnt ignore files having the extension html that are in root directory)
- `*/*.html` (All files having the extension html that arent in the root directory)

#### git global ignore
- `$git config --global core.excludesfile` (display path of the current git ignore)
- `$git config --global core.excludesfile ~/.gitignore_global` (set path to new global ignore)
[Sample Can Be Found Here](https://www.github.com/github/gitignore)

#### Viewing History
- `$git log -4`(shows latest 4 commit)
- `$git log --oneline` (shows only first line of commit message)
- `$git log --decorate` (add branch name to the log)
- `$git log --graph` (shows the ascii graph of the commits)
- `$git log --all` (includes all branch)

##### Combine parameters
- `$git log --oneline --graph --decorate --all`
- `$git log --graph --oneline`

- `$git log -p` (summary for each commit followed by the diff)

- `$git shortlog`(shows only first line of commit message grouped by author)
- `$git shortlog origin/master..HEAD` (shows all commit between origin/master and current commit)
- `$git log --author--"binish"` (filter the commit message by author)
- `$git log --grep="idea"` (shows commit message containing word idea)
- `$git log -- README.md` (shows all commit related to the particular file )
- `$git log -p -- books/` (shows all commit related to the particular directory )
- `$git log -S"Fortran" -p` (shows all commit with content changes containing the word Fortran)


#### Branching
- `$git branch myBranch`(create a new branch called myBranch)
- `$git checkout -b myBranch`(create a new branch called myBranch and switch to myBranch)
- `$cat .git/refs/heads/myBranch` (confirm the sha1 of the branch)
- `$git branch` (check the list of the branch)
- `$git branch -all`(show list of all branch including the remote branch)
- `$git branch -all -v`(show list of all branch including the remote branch -verbose)
- `$git checkout --track origin/checkbait` (checkout the remote branch and start tracking branch called checkbait of origin)
- `$git branch -d myBranch`(delete branch called myBranch)
- `$git branch -D myBranch`(force delete branch called myBranch)


#### Merging
- `$git checkout clickbait`
- `$git checkout master`
- `$git merge clickbait`
- `$git branch -d clickbait`

 #### fastForward merge
 Merge without creating a new commit but just moving the head of the master. This merge is automatically perform when there is no other commit in the master branch
-  `$git checkout -b readme_improvement`
-  `$vim README.md`
-  `$git add README.md`
-  `$git commit -m "Add readme improvement"`
-  `$git checkout master`
-  `$git merge readme_improvement`

 #### Merging without fastForward merge
-  `$git checkout readme_improvement`
-  `$vim README.md`
-  `$git add README.md`
-  `$git commit -m "Add Signature"`
-  `$git checkout master`
-  `$git merge --no-ff readme_improvement`


#### Syncing with Remote
- `$git remote -v`
- `$git branch --v` (shows local branches and remote branches they are tracking)
- `$git branch --v --all` 
- `$git push origin master`

#### Merging from another user fork branch
- `$git remote add iwantmyrealname https://github.com/iwantmyrealname/rwTODOs.git`
- `$git remote -v`
- `$git log --oneline --decorate --all --graph`
- `$git fetch iwantmyrealname`
- `$git remote show iwantmyrealname` (show remote git detail)
- `$git checkout --track origin/clickbait`
- `$git log --oneline --graph -- all`
- `$git merge iwantmyrealname/clickbait`
- `$git log --oneline --graph --all`
- `$git checkout master`
- `$git merge clickbait`
- `$git git log --oneline --graph --all`


#### Merging the master of another fork origin/master
- `$git fetch iwantmyrealname`
- `$git merge iwantmyrealname`
- `$git log --oneline --all --decorate --graph`
- `$git push`

#### Merge Conflit with terminal
- `$git checkout zIntegration`
- `$git config merge.conflictstyle diff3` (show the unchanged code from the common ancestor)
- `$git merge yUI`
(Edit the Conflict part)
- `$git status`
- `$git add .`
- `$git commit`
- `$git branch -d yUI`

#### Merge Conflict using mergeTool
- `$git config mergetool opendiff` (Configuration for the mergetool)
- `$git merge xReadMeUpdates`
- `$git mergetool`
(Command+S & Commang+Q)
- `$rm README.md.orig` (An extra file with the original conflict will be created, so delete it)
- `$git branch -d xReadMeUpdates`
#### Stash
- `$git stash` (stash current changes with default message)
- `$git stash list` (show stash list)
- `$git stash apply (apply the latest stash)
- `$git stash show -p` (show latest stash with diff)
- `$git stash show stash@{1}` (show second stash )
- `$git stash pop` (apply latest stash and delete it)
- `$git stash push -m "Stash Message"` (stash with custom message)
- `$git stash drop stash@{1}` (delete stash at particular index)

#### Alias
- `$git config alias.gl 'log --oneline --graph --decorate --all'` (Local Alias)
- `$git config --global alias.gl 'log --oneline --graph --decorate --all'` (Global Alias)
- `$cat ~/.gitconfig` (Show the content of the global alias)

#### Rebase 
- `$git checkout wValidator` (Current working branch)
- `$git rebase xValidator` (Add the codes from xValidator to current working branch)
(If merge conflits occurs)
- `$git mergetool`
(Resolve Conflict)
- `$git status`
- `$rm -rf js/magic_square/validator.js.orig`
- `$git rebase --skip`

#### Rebase rewriting history
- Reorder
- `$git checkout wValidator`
- `$git log --decorate --graph --oneline -all`
(Find the common parent, in this case 69670e7)
- `$git rebase -i 69670e7` (rebase to common parent)
(Reorder the commits by cutting and pasting the lines (use dd and p in vim))
press :wq
- `$git log --decorate --graph --oneline`

- Squash
- `$git checkout wValidator`
- `$git log --decorate --graph --oneline -all`
- `$git rebase -i 69670e7` 
(replace the all pick you want to squash to squash)
press :wq
(Delete the default message and create custom message)
press :wq

- Rename Commit
- `$git checkout wValidator`
- `$git log --decorate --graph --oneline -all`
- `$git rebase -i 69670e7` 
(replace the all pick you want to change to reword)
press :wq
(Change the commit message)
press :wq

#### Rebase Master and Fast Forward Merge
- `$git checkout wValidator`
- `$git rebase master`
- `$git log --decorate --graph --oneline -all`
- `$git checkout master`
- `$git merge wValidator` (Fast Forward Merge)

#### Add file to .gitignore that are already tracked
(Edit .gitignore and commit)
- `$git rm --cached HIDDEN` (Remove the cached)
- `$git commit -m "Message"`
