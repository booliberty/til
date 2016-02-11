Bash Startup Configuration
==========================
  
Add some context here describing intent and differences related to .bashrc and
.bash_profile  
  
### .bash_profile  
        [[ -s ~/.bashrc ]] && source ~/.bashrc  
 
### .bashrc  
        export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\]\$"
        export CLICOLOR=1
        export LSCOLORS=ExFxBxDxCxegedabagacad
        alias ls='ls -GFh'

http://dghubble.com/blog/posts/.bashprofile-.profile-and-.bashrc-conventions/
