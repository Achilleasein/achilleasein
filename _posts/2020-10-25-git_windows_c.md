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

We will need to setup Ubuntu on W10, its a very simple procedure that allows Ubuntu to run on top of W10.
Ubuntu can see the filesystem of windows and vice versa (the oposite is a little bit more tricky), but here we will just do the one way road.
  1. First you need to navigate to the windows store and search for ubuntu, I just use the latest version(20.04).
  2. Then you need to do the following: control panel -> Programs -> Turn windows Features on or off -> Navigate to the bottom and activate Windows subsystem for linux.
  3. This will take some time so in the meantime download [visual studio](https://code.visualstudio.com/) and [git](https://git-scm.com/downloads)

When you install everything you will have to restart your PC(expected from windows at this point).

### Getting Accustomed

Let's explaining what we installed and how we are going to use them.
- Visual studio code has some excellent features, such as markdown for each different language, keep tracking of changes in repositories and connecting with compilers.
  I constantly use visual studio because it lightweight, can connect to remote servers and code remotely, its safe, has excellent default hotkeys and much more.
- Git is the toolset, it contains everything we need, but why do we also use github? Think of it that way, git are the wheel, every car manufacturer can use them, the implementation differs as well as the use case, which will get us discussing development techniques(agile, waterfall etc.). Git provides the basic commands, github provides some added functionality and the much needed free server.
- Ubuntu on W10, its a OS build on OS, its not a VM, but its not exactly a stand alone OS as well. We have shared physical space on the hard drive which grants us excellent versatility.

### Setup Github ssh

We will use public RSA key for the ssh functionality of github, that way we can pull/push our repositories safely!
If you need to understand how that works [here is a good read](https://en.wikipedia.org/wiki/RSA_(cryptosystem)#:~:text=An%20RSA%20user%20creates%20and,who%20knows%20the%20prime%20numbers.&text=Breaking%20RSA%20encryption%20is%20known%20as%20the%20RSA%20problem.) about RSA.
The steps go as follows:
   ```bash
   $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   > Enter a file in which to save the key (/c/Users/you/.ssh/id_rsa):[Press enter] (Enter for default)
   > Enter passphrase, you can also leave empty
   $ cat ~/.ssh/id_rsa.pub copy this and keep it somewhere safe temporarily
   ```
Now you have to go to github -> click on profile top right corner -> settings -> SSH and GPG keys -> New GPG key -> Paste here what you copied from above.
One more step left, you need to configure your local user. If you want to read more refer [here](https://git-scm.com/book/en/v2/Git-on-the-Server-Generating-Your-SSH-Public-Key) and [here](https://askubuntu.com/questions/1097038/how-do-i-setup-ssh-key-based-authentication-for-github-by-using-ssh-config-fi)
To do that follow the steps below:
1. Go to a directory where you want to store your repos.
2. ```bash git config user.name "FIRST_NAME LAST_NAME" ```
3. ```bash git config user.email "MY_NAME@example.com" ```
4. Now clone my example repo with the following command:  ```bash git clone git@github.com:Achilleasein/hello_world.git ```

### Executing order GCC!

Navigate to the repository folder form within the visual studio, open the .c file, do any edits you may want, save it and compile it!
To compile use the following command: ```bash gcc hello_world.c -o hello_world ```. \
Now execute it with ```bash ./hello_world ``` \
You can feel free to fork, branch or do anything you like with the repo in your own github account. It's not much use at its current state but maybe you will have some fun. \
Keep in mind that I have a .gitignore file, in that specific file we add files that want to be ignored and never be pushed in the repo, for our current use we dont want to push the executable since anyone can compile it in his PC.

### Tips && Tricks
- Instead of trying to cd every time, you can actually store the commands for future use, there are 2 ways to do that.
    1. Execute the command as follows: cd /usr/Desktop/github # cd to github repo , what does that to? Whats written after the # works as a comment but its still visible by the cmd. Meaning we can actually use the Ctrl+R(reverse search) on cmd to search for the comment. In that case you will need to do the following: Ctrl+R -> cd to github repo, just like in the image below:
    {% include aligner.html images="reverse_search.PNG" column=1 %} \ 
    The cmd will autofill the rest, then press enter and done, you have changed directory without the need to type everything manually. \ 
    
    2. You can create custom bash commands, [here](https://dev.to/mollynem/4-simple-steps-for-custom-bash-commands-4c58) is a simple guide or follow the instructions below:

     - cd ~ , this will bring you to home directory
     - In there is the .bashrc, to view it use the command ls -la
     - Edit it and find the alias, there you can add you custom command as follows: alias cdtodesk ='cd /usr/Desktop/github'
  Keep in mind that the directory is an example, its more like in the photo above. 

- Git ignore file has many uses, for example when you create a web service application on python sometimes you have some passwords as plaintext to access a DB. 
  The proper way to mitigate any security issues is to work in a Venv and setup env variables, that way you can add the venv file on .gitignore and your password will stay local. 
  It will also ensure that no other person/colleague which forks will add them as plaintext and then push by accident.