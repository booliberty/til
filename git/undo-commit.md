Undoing The Last Commit
=======================

There are man different approaches and opinions here.  I'll start with the
simplest.  
  
        git reset --soft HEAD^     # use --soft if you want to keep your changes  
        git reset --hard HEAD^     # use --hard if you don't care about keeping the changes you made  

This resets to the commit before HEAD (current position).  __NOTE:__ The
__hard__ argument can destroy local data.  This is especially important if the
commit has already been pushed to a remote, and you use "git push --force" to
undo the commit on the remote, as the force argument can destroy remote data.

Safer, and more complex, is interactive rebase.  
  
        git rebase -i @~9   # Show the last 9 commits in a text editor

Find the commit you want, change pick to e (edit), and save and close the file.
Git will rewind to that commit, allowing you to either:  
        git commit --amend    # make changes  
        git reset @~          # discard last commit, but not changes to files  
  
Then, run "git rebase --continue", and Git will replay the subsequent changes on
top of your modified commit. You may be asked to fix some merge conflicts.  

https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things
https://git-scm.herokuapp.com/book/en/v2/Git-Tools-Rewriting-History
http://stackoverflow.com/questions/1186535/how-to-modify-a-specified-commit-in-git
