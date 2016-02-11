Configuring Vim
===============
  
I find that editing ~/.vimrc is the best way to accomplish this.  
  
It is possible to commit similar configuration to .viminfo, that that file is
more sensitive and dynamic.  General wisdom seems to be that .vimrc is a true
config file, and .viminfo is more of a system file.  
  
set tw=80 ts=4  # Make textwidth 80 and tabstop 4  
set sw=4 expandtab  # Make shiftwidth 4 and expand tabs to spaces  
set ai  # autoindent  
set vb  # Use visual bell instead of beeping  
set number  # Enable line numbers  
syntax on  # Use syntax coloring  
