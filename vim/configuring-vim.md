Configuring Vim
===============
  
I find that editing ~/.vimrc is the best way to accomplish this.  
  
It's possible to commit similar configuration to .viminfo, that that file is
more sensitive and dynamic.  General wisdom seems to be that .vimrc is a true
config file, and .viminfo is more of a system file.  
  
# Make textwidth 80 and tabstop 4
set tw=80 ts=4
# Make shiftwidth 4 and expand tabs to spaces
set sw=4 expandtab
# autoindent
set ai
# Use visual bell instead of beeping
set vb
# Enable line numbers
set number
# Use syntax coloring
syntax on
