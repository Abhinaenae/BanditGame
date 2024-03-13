# BanditGame
This repository contains my solutions to the Bandit Wargame found on [Overthewire.org](https://Overthewire.org)

An overview of this game is to progress through levels following some task on a Linux terminal, starting with Level 0.

For level 0, the task is:

- The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

To accomplish this, we need to open the Linux Terminal and type in the `ssh` command with the proper parameters, then enter the password "bandit0". Below is the proper solution:
```
ssh bandit0@bandit.labs.overthewire.org -p 2200
```
This will allow you to begin the game.

I will be adding the solutions to the levels in seperate folders in clusters of 5, i.e. levels 0 to 5, 5 to 10... and so on.
