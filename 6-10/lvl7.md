
# Level 7 to 8

## Goal:
The password for the next level is stored in the file "data.txt" next to the word "millionth"

## Solution
First, connect to bandit7 via `ssh bandit7@bandit.labs.overthewire.org -p 2220`.
Looking at the requirements, this level introduces us to Linux's text manipulation commands.

Let's naively use `cat data.txt`.
When we run this commmand, we are shown the long contents of the file, making it extremely difficult to find the word millionth and the password.

To clean this up, we could pipe the contents of the file to `grep millionth` and match each line of the file to the specified pattern.

Our solution would be:


![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/5a08a7d1-5e5b-4072-9f5b-19fcad00ac51)

After the word "millionth", we can see our password, `TESKZC0XvTetK0S9xNwm25STk5iWrBvP`, allowing us to go to level 8.
