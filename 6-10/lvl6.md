# Level 6 to 7

## Goal:
The password for the next level is stored somewhere on the server and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

# Solution
First, connect to bandit6.
Looking at the requirements, this level introduces us to Linux's file permissions. A file permission can be viewed with `ls -l <file-name>`.

We can use the `find` command with the properties:
- `-user bandit7` because the user is bandit7.
- `-group bandit6` because the group is bandit6.
- `-size 33c` because we want a file of 33 bytes.

However, when we run it, we get a lot of outputs of permission denied because we don't have access to every file on the server.
![image](https://github.com/Abhinaenae/SkyScan/assets/92381984/bfafa904-634b-43b4-9591-e87c6b4fde87)


To clean this up, we could add `2>/dev/null` to hide all error messages 1, and entering this in the terminal will let us find the file we need much more efficiently

![image](https://github.com/Abhinaenae/SkyScan/assets/92381984/f7e16e26-ca67-4e82-ad0c-622b8f633cb6)


So after we `cat` the file found, we get a password: `z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S`, allowing you to connect to bandit7.
