# Level 2 to 3

## Goal:
The password for the next level is stored in a file called spaces in this filename located in the home directory

# Solution
After connecting to bandit2, we want to find a file "spaces in this file name" in the home directory.
We will end up getting some errors saying that the files "spaces", "in, "this", and "filename" don't exist when running `cat ./spaces in this filename` because the shell assumes these are seperate files.

This can be solved by putting the filename in quotes:

```
cat ./"spaces in this filename"
```

When running this command, you'll get the password for the next level:
`aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG`
