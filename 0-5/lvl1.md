# Level 1 to 2

## Goal:
The password for the next level is stored in a file called - located in the home directory

# Solution
After connecting to bandit1, we want to find a file "-" in the home directory.
While this may seem the same to the previous problem, we don't get what we are looking for when running `cat -`.


This is because the command "cat -" in Unix-like operating systems is used to read data from the standard input (stdin) and display it on the standard output (stdout). 
The hyphen "-" is used as a placeholder to represent stdin.

This can be solved by putting the filename in quotes and adding the path, like this:

```
cat ./"-"
```

When running this command, you'll get the password for the next level:
`rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi`
