## Commit Workflow
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

## Pull Other Branches
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
## Undoing Your Changes
If you made local changes and you wish to discard them (that is, restore the file from the repository):
```sh
git checkout path/to/file/to/restore.html
```
If you want to restore the file as it was in a specific commit:
```sh
git checkout 39ab2094 -- path/to/file/to/restore.html
```
## Merging
Sometimes you need to merge `master` (to make a pull request mergeable, or get the latest changes) or someone else's branch (to integrate with someone's code for example)

First you need to pull the branch in question as outlined [above](git-cheatsheet#pull-other-branches)

Then you checkout your own branch and git merge like so:
```sh
git merge BranchInQuestion
```
At this point you may face conflicts. Take a deep breath. Do not panic.

## Resolving Conflicts
So you just tried to merge a branch and git told you hurtful things like:
```
CONFLICT (add/add): Merge conflict in Idearator/test/functional/home_controller_test.rb
CONFLICT (modify/delete): Idearator/db/schema.rb deleted in HEAD and modified in C1_mennaamr_#91_Facebook_login. Version C1_mennaamr_#91_Facebook_login of Idearator/db/schema.rb left in tree.
Removing Idearator/db/migrate/20130326183608_add_devise_to_users.rb
......
```
These are the dreaded **CONFLICTS**.

Conflict resolution is simple as long as you are careful. You **have to** take care of each message before git will allow you to commit.

There are two major kinds of conflicts, those that introduce conflicting modifications and those that delete files altogether (DO NOT IGNORE THESE!).

### Type 1
Examples for the first kind:
```
CONFLICT (add/add): Merge conflict in Idearator/test/functional/home_controller_test.rb
CONFLICT (content): Merge conflict in Idearator/app/views/layouts/application.html.erb
```
To resolve this kind of conflict you must open the file in question, then find the parts that are marked to be in conflict like so:
```ruby
require 'test_helper'

class HomeControllerTest < ActionController::TestCase
<<<<<<< HEAD
  # test "the truth" do
  #   assert true
  # end
=======
  test "should get index" do
    get :index
    assert_response :success
  end

>>>>>>> C1_mennaamr_#91_Facebook_login
end
```
The part between `<<<<<<< HEAD` and `=======` is the change that you introduced, while the part between `=======` and `>>>>>>> C1_mennaamr_#91_Facebook_login` is the change that the branch you are merging introduced. 

You should now see which version you want to keep (possibly a mix of the two!) and delete the merge markers (the `>>>>>>> .....` and `=======` etc)

Save the file. `git add` the file. Move to the next conflict.

### Type 2
Examples for the second kind:
```
CONFLICT (modify/delete): Idearator/db/schema.rb deleted in HEAD and modified in C1_mennaamr_#91_Facebook_login. Version C1_mennaamr_#91_Facebook_login of Idearator/db/schema.rb left in tree.
Removing Idearator/db/migrate/20130326183608_add_devise_to_users.rb
```
As the message says, the `HEAD` ref(erence) (that is, your branch) has deleted this file, while the branch you are merging has modified or kept it. You need to make a choice.

If you want to keep the file:
```
git checkout HEAD Idearator/db/schema.rb
git add Idearator/db/schema.rb
```
If you want to delete the file, like should be the case for this specific example (schema.rb), it depends on what the exact message is. If it said `Removing Idearator/db/schema.rb` then you don't need to do anything. But it actually did not remove it in our example (see the messages above! It says `left in tree` at the end), so you need to tell git to remove it:
```
git rm Idearator/db/schema.rb
```

Do NOT skip these conflicts as these WILL lead to mysterious deleted files later on.

Move to the next conflict.

### That's it!
You're golden. See? Told you it was simple. Now once you have dealt with **ALL** the conflict messages just go ahead and `git commit`; preferably without using the `-m` option so that git adds the default merge commit message. And remember, you need to [setup your git editor](https://github.com/DevYah/coolsoft-13/wiki/Configuring-Your-Environment#git) lest you get stuck in vim forever.

If you need to see what's still in conflict at any point just use our trusty `git status`

## Aborting a merge
If you tried to merge and changed your mind:
```
git merge --abort
```

## Reverting a merge
```sh
git checkout YourBranch
git log 
```

You Should see something like this
Notice there is the commit hash and 2 merge hashes one for your branch and the other the merged branch
```
commit f0a5726f655c1679d7cebd831af97ff8b30f2e78
Merge: 966b8b1 669d292
Author: mohammad-abdulkhaliq <mohammad28march1993@gmail.com>
Date:   Tue Apr 2 19:09:05 2013 +0200

    Merge branch 'master' into C2_mohammad-abdulkhaliq_#41_create/edit_tag_reopened
```

Now You need to know which merge hash is yours so git log for example the first one     
```sh
git log 966b8b1
```

I see this 
```
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
```

Ok definitely my branch let's revert the merge now 
As I know the first hash is for my branch I write 1 after git revert -m then the commit hash itself
```sh
git revert -m 1 f0a5726f655c1679d7cebd831af97ff8b30f2e78
```

Success should get now a revert merge commit message in your editor just save and quit 

Do another git log to make sure you have reverted the merge

## More Stuff
To be extended. EXTENDME!