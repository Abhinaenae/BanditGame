# Level 3 to 4

## Goal:
The password for the next level is stored in a file called spaces in this filename located in the home directory

# Solution
After connecting to bandit3, we want to change our directory to inhere using `cd inhere` and find a hidden file. We won't be able to find this file just by running `ls` because the file is hidden. 

To locate this file, we will need to add `-a` after the previous command. This extra specifier will show us all files in the directory specified, even if they're hidden. This should show us a file called ".hidden".

The complete solution is:

```
cd inhere
ls -a
cat ".hidden"

```

When running the `cat` command, you'll get the password for the next level:
`2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe`
