# Level 4 to 5

## Goal:
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.


# Solution
After connecting to bandit4, we want to change our directory to inhere using `cd inhere` and find the only human-readable file.
We can `cat` on all the files, but that would be wildly inefficient.

Instead, we can use the `file` to find the file types of a file, and specify to search for all files using an asterisk `*`. 
Then, finding this file, we can use `cat` on the file with type ASCII text to find the password.
The complete solution is:

```
cd inhere
file ./*
cat ./-file07
```

After running the `cat` command, you'll get the password for the next level:
`lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR`
