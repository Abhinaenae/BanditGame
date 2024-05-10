# Level 11 to 12

## Goal:
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

## Solution
First, connect to bandit11 via `ssh bandit11@bandit.labs.overthewire.org -p 2220`.

The hint given to us is "Rot13". Rot13 is a letter substitution cipher that replaces a letter with the 13th letter after it in the Latin alphabet. ROT13 is a special case of the Caesar cipher which was developed in ancient Rome. Because there are 26 letters in the alphabet, ROT13 is its inverse; that is, to undo ROT13, the same algorithm is applied, so the same action can be used for encoding and decoding.

Because there is no built-in rot13 command in Linux, we could use the `tr` command, which stands for ’translate’, allowing replacing characters with others. The base command syntax looks like: `tr <old_chars> <new_chars>`.

Our solution would be:

![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/07506bfa-3487-47a4-9017-35054a9d6990)


We get the password for level 12: `JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv`

On to level 12!
