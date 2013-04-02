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
### Suppose you merged your branch with master or someone else and you want to go back i.e undo the merge:
```sh
git checkout YourBranch
git log 

#You Should see something like this
#Notice there is the commit hash and 2 merge hashes one for your branch and the other the merged branch
commit f0a5726f655c1679d7cebd831af97ff8b30f2e78
Merge: 966b8b1 669d292
Author: mohammad-abdulkhaliq <mohammad28march1993@gmail.com>
Date:   Tue Apr 2 19:09:05 2013 +0200

    Merge branch 'master' into C2_mohammad-abdulkhaliq_#41_create/edit_tag_reopened

#Now You need to know which merge hash is yours so git log for example the first one     
git log 966b8b1

#I see this 

Mohammads-iMac-3:Idearator mohammadabdulkhaliq$ git log 966b8b1
commit 966b8b1ac4391d894397b508dd597de222b4be43
Author: mohammad-abdulkhaliq <mohammad28march1993@gmail.com>
Date:   Tue Apr 2 15:36:38 2013 +0200

    Issue #41 basic bootstrap UI, new branch
    
    New branch merged with old working commit from C2_mohammad-abdulkhaliq_#41_create/edit_tag.

commit 93a21467193394e70a2d971df3ec8a3c46d8b4db
Author: mohammad-abdulkhaliq <mohammad28march1993@gmail.com>
Date:   Fri Mar 29 14:14:10 2013 +0200

    Issue #41 Indent fixes and Updated UML folder

#Ok definitely my branch let's revert the merge now 
#As I know the first hash is for my branch I write 1 after git revert -m then the commit hash itself
git revert -m 1 f0a5726f655c1679d7cebd831af97ff8b30f2e78

#Success should get now a revert merge commit message in your editor just save and quit 
git log
#Do another git log to make sure you have reverted the merge
```
### More Stuff
To be extended. EXTENDME!