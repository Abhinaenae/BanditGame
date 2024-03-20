
# Level 8 to 9

## Goal:
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

## Solution
First, connect to bandit8 via `ssh bandit7@bandit.labs.overthewire.org -p 2220`.

Looking at the requirements, it seems `uniq` may help us greatly.

Opening the man page for `uniq`, we read that this option should help us:  -u, --unique. This outputs lines that are unique.

We also read that "'uniq' does not detect repeated lines unless they are adjacent.  You may want to sort the  input  first,  or use 'sort -u' without 'uniq'."

So, this means we have to sort the file, then pipe its contents to uniq with the option -u.
Our solution would be:

![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/10a2c31e-de12-40eb-8c6a-38c24a1a1690)

We get the password for level 9: `EN632PlfYiZbn3PhVK3XOGSlNInNE00t`
