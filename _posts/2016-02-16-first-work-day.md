---
layout: post
title: First Work Day After Spring Festival
categories: Tech
tags: Work
---
Today is the first work day after Spring Festival.

What I've learned today by work.

1. Usage of git merge

    I was working on an old branch which created about several weeks ago, and I need to catch up with the latest code in master.
    In this case, I need to use the git merge command to make the commits in master branch to my old branch.
    And the commands are:

    Step 1: Fetch the changes (saving the target branch as FETCH_HEAD).

        git fetch origin master
    Step 2: Checkout the source branch and merge in the changes from the target branch. Resolve conflicts.

        git checkout old_branch
        git merge FETCH_HEAD

    And in this case, the commits in mater will be merged into your old branch.

2. Intellij shortcut for imports clean

        Ctrl+Alt+O



