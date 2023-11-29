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

Switch between different commits:

git checkout _add git hash found in git log_

NOTE: When updating from a different version we will create branches from that version!

Git only sees the commits from behind. To view all the made commits use:

git log --all
git alog --all --graph (shows a more graphical representation of the branching)

NOTE: The master branch specifies the branch name 

To restore until certain commit and avoiding branching:

git checkout _add git hash found in git log_ *name of the file/directory*

To assign aliases to git commands:

git config --global alias.s "status" 
git config --global alias.cm "commit -m"
git config --global alias.co "checkout"

NOTE: In the first e.g, everytime we now issue "git s" it will be equivalent to typing "git status"

Ignores file(s)/directory(ies) that are not meant to be added to the branch (important for keys and personal information):

touch .gitgnore
*inside the file just type the name of the files that you wish to ignore*
git add .
git commit -m "Added the .gitignore file"

To remove Git from our project:

rm -rf .git 


---------------------------------------------------------------------------------------------------------------------------

Github + Git integration

The analogy to Github is Google Drive where we can: 
1) store all of our files on the cloud to avoid losing our data. 
2) sync backups from a local folder to the cloud
3) sync backips from the Cloud to the local folder (2-Way sync)

The Git installed directory is called the "local repository" and in Github is called "remote repository"

Links our local repository to a remote repository:

git remote add origin https://github.com/carlos-tuilm/git-tutorial.git

NOTE: By convention we should call our remote repository "origin"
NOTE: The URL points at the repository that we wish to upload our local repository

Checks if our local repository is linked to a remote repository:

git remote 
git remote -v

NOTE: -v flag gives more detailed information

To remove a link to remote repository:

git remote remove origin

Terminology used for Git:
1) Push: Uploading to Github
2) Pull: Downloading from Github

Configures Git with our Github username:

git config --global credential.username "carlos-tuilm"

NOTE: This has to be done in order to Push our code to Github

Push our code to Github:

git push origin *master or git hash*

NOTE: In this case, I created a token key in Github > git-tutorial > Settings > Developer options. This is a safer 
practice when working with these projects.
NOTE: When checking the git log --all, we will see that a remote tracking branch has been created.

To sync the changes from our local repository to the remote repository:

git add .
git commit -m "Something"
git push origin *master or git hash*

NOTE: The git log -all command will tell us when the HEAD/master branch is ahead of the origin/master branch when
working on a project
NOTE: Doing this will update the remote repository with the local one

This commands creates a shorcut for "git push=git push origin master":

git push origin master --set-upstream

NOTE: Git only "pushes" commits NOT files in the "changes space"

Every time we use "git commit --amend -m "something corrected"" our HEAD/master will branch out of the origin/master.
This is due to the fact that we overwrote over our local commit in order to correct some mistakes, this makes that the
remote files do not coincide with the cronology of our work. An NON-RECOMMENDED practice to maintain the HEAD/master 
branch aligned with the origin/master branch is to:

git push origin master -f 

NOTE: The -f flag enforces the HEAD/master to OVERWRITE the origin/master branch on our remote repository. This will 
REPLACE the contents of the current remote files which CANNOT be recovered!

Updates the actual local repository to the were the remote/origin is currenlty positioned:

git fetch

NOTE: This is done because remote branches DO NOT update automatically when changes are commited to it.
NOTE: This is VERY useful when working on a team project when we want to see if some changes were commited by other users.
NOTE: We can simply emulate this by creating a directory outside our current project and use "git clone *url address of the remote repository*"

Syncs our local repository to the current remote repository:

git pull origin *master or any other branch*
git pull origin --set-up-stream (does the same shortchut is before)




