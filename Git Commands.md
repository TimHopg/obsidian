#todo #Git #Shell 
### To Add Repo from Command Line
`curl -u "TimHopg" https://api.github.com/user/repos -d '{"name":"EDIT_NAME","private":true}'`

generate token from settings > dev tools at github. use this instead of password. set expiry date

`git init
`git add
`git commit
`git remote add origin https://github.com/username/repository-name.git` or `git@github.com:TimHopg/get_next_line_two.git`
`git remote set-url origin https://github.com/TimHopg/GNL_V9.git` to change
`git push -u origin master
`git add -u` add all modified files
`git ls-files -o -i --exclude-standard`
`git config file`
#### Git SSH
`ssh-keygen -t rsa -b 4096`
Generates pairs of SSH (secure shell) keys
`-t rsa` type rsa (Rivet-Shamir-Adleman) cryptographic algorithm
`-b 4096` 4096 bits

Use SSH github repo  7
Add public key to github
#### Git Help
`git config --help`
`git help config`
`SPACE` - goes to next page
`Q` - quit
`git config -h` - An abridged version
#### Branches
`git branch` - verifies current branch
`git branch NAME` - creates new branch
`git checkout NAME` - switches to `NAME` branch
`git checkout -b NAME` - creates and switches to `NAME` branch in one command
`git push -u origin NAME` - pushes the new branch to the remote repo

`git fetch` - if newly created branches are not appearing, `fetch` updates local references
#### Git Commands
`git rm --cached <file_name>` - Removes from git repo but leaves on disk (previously committed)
`git init` - initialise new repo
`git add file1 file2` - git add
`git commit -m "initial commit` (just `git commit` for more verbose message)
`git add file2` - removes unused file (the `git commit`)
`git status (-s)`
`git add.` -  adds all recursively
`git ls-files` - display all files in staging area
`git rm file1.txt` - removes file from working directory and staging area
`git diff (--staged)` - see all changes made in staging area
`git difftool --staged` - Using difftool
`git restore --staged file1 file2` - unstage file
`git restore --staged .` - unstage all (essentially restore - takes last known copy of file from previous commits if one exists)
`git restore file.txt` - discards local changes
`git clean -fd` - remove files from working directory (hdd), recursive, directors
`git clean -nd` - git clean dry run

`git reet --hard HEAD` - restores working directory to last commit
#### Git Logs
`git log (--oneline --reverse)` - Git history/log
`git show d60(identifier)` - shows contents of commit
`git show HEAD~1` - show commit at HEAD -1
`git show HEAD~1:bin/app.bin` - to show final version stored in commit, use full path
`git ls-tree HEAD~1` - show all files and directories in commit (files are blob, dirs are trees)
`git show ID` - shows content of blob or tree
`git restore --source=HEAD~1 file.txt` - restore file to an earlier version
#### Git Levels
System - all users
Global - all repos of current user
Local - Current repo
#### Git Config
git config --global user.name "Tim Hopgood" _(double quotes because of space)_
git config --global user.email 'timhopgood@gmail.com'
git config --global core.editor 'vim'
git config --global core.editor "code --wait" (VS Studio Code but waits for the user to close current project)
_Opens default editor to edit (-e/--edit) global settings_
git config --global -e
_Deals with carriage return and line feed. "true" on Windows and "input" on Linux_
git config --global core.autocrlf input
`git config --global diff.tool vscode` - sets vscode to difftol
`git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE` - variables are placeholders for file copies
`gi config --global -e` - checks settings
#### References