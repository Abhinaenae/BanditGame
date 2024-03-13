# Level 0 to 1

## Goal:
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

## Solution:
First, we need to ssh to bandit1 and go the home directory using `cd ~` then use the find command for the "readme" to ensure it exists, and print out the contents of "readme" using cat. Below is a method doing so.

```
cd ~
find readme
cat readme
```
The password will be `NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL`

Time to exit the ssh and move on to the next level!
