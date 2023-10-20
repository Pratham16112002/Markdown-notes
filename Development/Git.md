# Git & GitHub

Git is a version control system , tracks the history of all the changes made my all the people and team on the project together. 

As a team you can run tests and review the code and generate some issues in the project . 

Open source contributors can make pull requests. 

**Git Branch** : It is defined as the series of code changes. 

Team or people can make multiple branch as much they need, such as testing branch or production branch, etc. 

`git init`

initializes a branch new git repository and begins tracking the existing directory, It adds a sub-folder that has all the config files required to manage the version control system. 

`git clone` 

It is going to create a local repository that already exist remotely . This clone includes all the version control data , along with the data and code. 

`git status` 

This command tells us all the changes that are done on particular repository. 

`git diff <file name>`

This command tells us that what are the exact changes that are done to any particular file. 

> Note we cannot commit any change in the repository unless it is staged .
> 

To stage any change we need : 

`git add .` 

This command will stage all the changes made in the local repository. 

`git log` 

This command shows all the different commits  made to that repository. 

`git show <commit-id>` 

If you want to get any particular commit done by some one then . 

`git branch` 

This command tell us the current branch we are on. 

`git checkout -b <new-branch>`

This command is to create another branch in the repository , `-b` is the argument to specify the new branch name. 

`git checkout branch-name`

To move into a particular branch we use this command. 

`git branch -d branch-name`

To delete a particular branch from the repository.

`git merge <branch-name>` 

To merge the branch into the currently used branch. 

`git reset -—hard HEAD^`

To revert back the most recent commit done in the branch. 

The local changes made in the repository are also lost.

Code change is also reverted and commit for that is also removed from the logs. 

`git reset —soft HEAD^`

To revert back the most recent commit done in the branch. 

It will remove the last commit but it will keep the local changes done to the repository unchanged.

> Note HEAD is referred to the currently pointed branch.
> 

`git restore <file-name> or git restore .` 

It is about restoring files in the working tree , used to restore files from another commit. 

if the above commands are executed with `—staged`

then the file is converted from staged to upstaged state . 

 `git pull` 

To get all the latest changes from the remote branch. 

`git push` 

To push al the changes done locally to the remote branch. 

git commit `—amend`

Used to modify the most recent commit, it lets you combine stages changes with the previous commit instead of creating a new commit.