
# Level 9 to 10

## Goal:
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

## Solution
First, connect to bandit9 via `ssh bandit9@bandit.labs.overthewire.org -p 2220`.

The `strings` command finds human-readable strings in files by printing sequences of printable characters. It is mainly used non-printable files.



First we want to extract the human-readable portion of data.txt and pipe the contents into `grep`, searching for lines that have more than one "=" on the same line. You could use `grep ==` for that part.

Our solution would be:

![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/d2cc42c0-8608-4477-8f4d-042519085b5a)

We get the password for level 10: `G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s`
