#!/bin/bash

git filter-branch --env-filter 'if [ "$GIT_AUTHOR_EMAIL" = "mw@mwmini.mw.lan" ]; then
     GIT_AUTHOR_EMAIL=booliberty+github@gmail.com;
     GIT_AUTHOR_NAME="booliberty";
     GIT_COMMITTER_EMAIL=$GIT_AUTHOR_EMAIL;
     GIT_COMMITTER_NAME="$GIT_AUTHOR_NAME"; fi' -- --all

http://stackoverflow.com/questions/4981126/how-to-amend-several-commits-in-git-to-change-author
