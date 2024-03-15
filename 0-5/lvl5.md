# Level 5 to 6

## Goal:
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

# Solution
After connecting to bandit5, we need to change our directory to inhere using `cd inhere` and find the file with those properties.
We can look at all the files in all the subdirectories of inhere using `ls -Ral`, but that brute force method would be even more inefficient.

Instead, we can use the `find` command and specify the properties we want to filter through the files.
Then, finding this file, we can use `cat` on the file to find the password.

I recommend you do further research on the find command if you don't understand the solution.
The complete solution is:

```
cd inhere
find ./ -readable -size 1033c ! -executable
cat ./inhere/maybehere07/.file2
```

After running the `cat` command, you'll get the password for the next level:
`P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU`
