---
layout: post
title: "create git remote repository and initiate it from local repository"
date: 2016-12-13
description: ""
category: git
tags: [git]
---
{% include JB/setup %}

# Table of Contents

1.  [create a remote repo](#orgb6f7e40)
2.  [initiate from local repository](#org31458e8)
3.  [my shell script](#orgc68fb5d)



<a id="orgb6f7e40"></a>

# create a remote repo

-   using the following command:
    
        curl -u '${user_name}' https://api.github.com/user/repos -d "{\"name\":\"${repo_name}\"}"
    
    -   change ${user \_name} to your github user name, and ${repo \_name} to the repository name you want to create.


<a id="org31458e8"></a>

# initiate from local repository

-   *cd* to the directory you want to initiate the remote repository with.
-   execute the following commands:
    
        touch README.md
        echo "# ${repo_name}" >> README.md
        git init
        git add .
        git commit -m "first commit"
        git remote add origin https://github.com/${user_name}/${repo_name}.git
        git push -u origin master


<a id="orgc68fb5d"></a>

# my shell script

-   this is my shell script *git-create*, I made it executable and added it's path to my PATH environment variable for convenience:
    
        user_name='lightjameslyy'
        repo_name=$1
        test -z $repo_name && echo "Repo name required." 1>&2 && exit 1
        
        curl -u ${user_name} https://api.github.com/user/repos -d "{\"name\":\"${repo_name}\"}"
        
        touch README.md
        echo "# ${repo_name}" >> README.md
        git init
        git add .
        git commit -m "first commit"
        git remote add origin https://github.com/${user_name}/${repo_name}.git
        git push -u origin master

