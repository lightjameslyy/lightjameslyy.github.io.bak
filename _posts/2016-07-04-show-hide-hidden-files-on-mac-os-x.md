---
layout: single
title: "show hide hidden files on mac os x"
date: 2016-07-04 19:09:58
description: ""
category: macOS
tags: [mac os x, finder, hidden files]
---

# 1. show hidden files in finder

open terminal and type in the following commands:

    > defaults write com.apple.finder AppleShowAllFiles YES
    > killall Finder

then relaunch Finder, the hidden files should be visible.

# 2. hide hidden files in finder

open terminal and type in the following commands:

    > defaults write com.apple.finder AppleShowAllFiles NO 
    > killall Finder

then relaunch Finder, the hidden files should be invisible.
