# Database Amendment/Modification Protocol
## Steps to add push migrations to master:

1) Make a branch from latest version of master with the same name as the branch you are working on, but adding "migrations" to it.       
         For example:    

    Branch name: C4_Gezeery_#52_view_user_profile
    Migrations branch name: C4_Gezeery_#52_view_user_profile_migrations 

2) Add your migration files and anything that you did to make this part of the task work, meaning if you used a gem with these migrations be sure to add them to the gem file.

3) In each migration file, make sure you add comments that explain what this migration actually does. This can be needed for future reference.

4) Make a pull request with a small descriptive title and mention @hishamelgezeery in the description. Make sure to describe what these migrations do and why they should be merged into master. 

5) Make sure this branch is merge-able with master. This should always be the case but if you encounter conflicts in the gem file for example, make sure you resolve them so I can approve the merge.  

***

## Creating Migrations: a quick guide
FIXME