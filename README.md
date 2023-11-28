Git Tutorial

To set up git and track all the files inside the current directory:

git init 

Shows all the changes that have been done since our previous version:

git status

(NOTE: Untracked files are those which are not been tracked in our "version history".)

Selects the files and/or directories that we want to track:

git add . (Tracks current folder in this case)

(NOTE: this command does NOT create a new version, instead it allows to choose which changes we want in the next version.)

Creates a new "version" (commit in Git terminology) in our "version history":

git commit -m "Version 1"

(NOTE: -m is the message flag that allows us to state a custom message.)
(NOTE: The output of this commands tells us the number of files that were modified and the number of new lines that were inserted.)

Adds the user's name and email in order to keep track on who made the changes to the file:

git config --global user.name "Carlos Perez"
git config --global user.email "carlos-daniel.perez-tablante@tu-ilmenau.de"

Outputs the version history of the branch:

git log

Corrects an erronous commit (e.g mispelling):

git commit -m "Version 1" --ammend

(NOTE: The custom message can also be changed when issuing the --ammend flag.)

(NOTE: The staging area (git add .) holds all the tracked or soon to be tracked files/directories that have some made changes. Here the changes WILL go to the next version.)

(NOTE: The changes area are all the modified files/directories that were previously tracked but NOT added to the staging area.)

(NOTE: The file can be both in the staged area and the working area due to that git only takes into account ONLY changes NOT the actual files theirself.)

Removes the file/directory out of the staging area:

git reset . (it can be an specific file also)

Resets all the changes made in the working area (careful but useful):

git checkout -- . (it can be an specific file also)

Creates a new commit (version):

git add .
git commit -m "Version 2"

From this point we can change between 3 commits or versions

To switch between between different commits:

git checkout *insert the commit hash* 

