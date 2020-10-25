---
layout: post
title: Simple setup to run c/cpp and use github on W10
tags: [c, cpp, wsl, w10, visual studio, ssh keys]
excerpt_separator: <!--more-->
---

This is a simple guide to setup on your W10 PC an easy way to run c/cpp code, push it on github and use visual studio instead of Vim.
I will guide you through each step of the way for an easy and fast setup. It will take us around 30 minutes.
<!--more-->

## Simple setup cookbook

### Ingredients

For the following guide we will need the following ingredients:

1. Ubuntu on W10
2. Git
3. Visual studio

### Installing Everything!!

We will need to setup Ubuntu on W10, its a very simple prodecure that allows Ubuntu to run ontop of W10.
Ubuntu can see the filesystem of windows and vice versa (the oposite is a little bit more tricky), but here we will just do the one way road.
1. First you need to navigate to the windows store and search for ubuntu, I just use the latest version(20.04).
2. Then you need to do the following: control panel -> Programs -> Turn windows Features on or off -> Navigate to the bottom and activate Windows subsystem for linux.
3. This will take some time so in the meantime download [visual studio](https://code.visualstudio.com/) and [git](https://git-scm.com/downloads)



### Tips && Tricks
1. Instead of trying to cd every time, you can actually store the commands for future use, there are 2 ways to do that.
    1. Execute the command as follows: cd /usr/Desktop/github # cd to github repo , what does that to? Whats written after the # works as a comment but its still visible by the cmd. Meaning we can actually use the Ctrl+R(reverse search) on cmd to search for the comment. In that case you will need to do the following: Ctrl+R -> cd to github repo and the  cmd will autofill the rest, then press enter and done, you have changed directory without the need to type everything manually.
    2. You can create custom bash commands, [here](https://dev.to/mollynem/4-simple-steps-for-custom-bash-commands-4c58) is a simple guide.