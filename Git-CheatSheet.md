### Commit Workflow
It is very important that you make your commits as you work. Commit every atomic piece of work separately and DO NOT just make one huge commit at the end.

```sh
# See what has changed
git status
# Add/remove files to the staging area
git add some/thing/here.js
git rm that/other/thing/there.js
# IMPORTANT see what you are about to commit
git status
# IF you wish to remove something from the staging area
# for example if you added a file and you wish to not commit it now
git reset some/thing/here.js
# Now check again what is about to be committed
git status
# Once you are happy, commit
git commit -m "Your commit message here"
```

### Pull Other Branches
If it's the first time to pull this branch you have to fetch the remote branch first:
```sh
git fetch
```
Then you can just do:
```sh
git checkout BranchNameHere
```
To update the branch after there have been new commits pushed to it, check it out as above then do:
```sh
git pull origin BranchNameHere
```
### Undoing Your Changes
If you made local changes and you wish to discard them (that is, restore the file from the repository):
```sh
git checkout path/to/file/to/restore.html
```
If you want to restore the file as it was in a specific commit:
```sh
git checkout 39ab2094 -- path/to/file/to/restore.html
```

### More Stuff
To be extended. EXTENDME!