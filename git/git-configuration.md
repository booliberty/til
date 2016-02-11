Basic Initial Git Configuration
===============================

This is widely documented, so I'll be brief and minimize context.
  
To assign the global user's name:  
        git config --global user.name "YOUR NAME"  
  
To assign the global user's email address (must match github account email
address for commits to show proper ownership):  
        git config --global user.email "YOUR EMAIL ADDRESS"  
  
To enable the osxkeychain credential helper for https cloning (you may be
prompted for login keychain password to store github credentials):
        git config --global credential.helper osxkeychain  
  
To edit the global git config in a text editor:
        git config --global --edit  
  
https://help.github.com/articles/set-up-git/
https://help.github.com/articles/caching-your-github-password-in-git/
