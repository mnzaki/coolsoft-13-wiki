Hello coolsoft ,

I discovered a couple of GUI tools that can be used to perform complex merges safely and in short time .

the tools are :
1-Git cola : a GUI tool for Git .
2-meld : Git tool to resolve conflicts .

How to use :
1- configure cola preferences to use meld merge tool
2- when you merge using the terminal :
    * open git cola
    * check the status of the merge
in the status panel view you have three kinds of files merged ,( unmerged , staged , modified ) 
    * unmerged , click right and launch merge tool
    * staged , if you are happy with the change leave it else , click right and unstage .
    * modified(untracked) , thease files were changed (modified/deleted) by merge but unstaged . to revert unstaged 
    changes , simply click right and revert changes