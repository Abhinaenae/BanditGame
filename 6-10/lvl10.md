
# Level 10 to 11

## Goal:
The password for the next level is stored in the file data.txt, which contains base64 encoded data

## Solution
First, connect to bandit10 via `ssh bandit10@bandit.labs.overthewire.org -p 2220`.

To understand the problem, we need to understand what base64 is. base64 is a binary-to-text encoding algorithm. It can usually be recognized by equal signs at the end of the data. Linux has a command called base64 that allows for encoding/decoding in base64.

Opening the man page for base64 command, we see the option `-d`, which decodes base64 encoded data.

Our solution would be:

![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/caf27ad9-df2b-4d78-b0cb-f9535487fc8b)

We get the password for level 10: `6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM`

For levels 11-15, navigate to the folder `11-15`.
