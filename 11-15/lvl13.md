# Level 13 to 14

## Goal:
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.

## Solution
First, connect to bandit13 via `ssh bandit13@bandit.labs.overthewire.org -p 2220`.

So far, we have logged onto a remote machine using `ssh` with a password. But, an alternative to using a password is public-key cryptography. The public key is on the remote host that allows access to the user who owns the private key. The `-i` flag allows you to log in with the private key.

`scp` is a command that uses SSH to transfer data over the network. The syntax to get a file from a remote host: scp -P <port> <user>@<IP>:<remotefilepath> <localfilepath>. 

I logged into the server as bandit13 and found 'sshkey.private' in home directory. We can transfer the file to local since we know the location.

```
bandit13@bandit:~$ ls
sshkey.private
bandit13@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```

then, I used `scp` to connect to the remote machine and get the ssh key, and confirmed it is in my local machine.

```
root@Abhinay:~# scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit13@bandit.labs.overthewire.org's password:
sshkey.private
root@Abhinay:~# ls -l | grep sshkey.private
-rw-r----- 1 root root       1679 May 12 16:04 sshkey.private
```
When connecting to bandit14 via `ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220`, this error appears:
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0640 for 'sshkey.private' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "sshkey.private": bad permissions
bandit14@bandit.labs.overthewire.org's password:
```
So, we need to reduce the permissions so that only the owner(me) has permissions for the file.
This is done by the `chmod` command.

```
root@Abhinay:~# chmod 700 sshkey.private
root@Abhinay:~# ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

And now we are in level 14!


