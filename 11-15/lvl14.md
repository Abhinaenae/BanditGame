# Level 14 to 15

## Goal:
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

## Solution
First, connect to bandit14 via `ssh bandit14@bandit.labs.overthewire.org -p 2220`.

The password, specified in the previous level, has the path of: `/etc/bandit_pass/bandit14`.

Localhost is the host of the local machine, and has the IP address ‘127.0.0.1’. You can specify either "localhost" or "127.0.0.1" 

We can use the `nc`/`netcat` command to read or write data to a specified host IP address and its port using the format: `nc <host_ip_address> <port>`. 



Below is a visual:

```
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
bandit14@bandit:~$ nc localhost 30000
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
```
This gives us the password: `jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt`, allowing us to access level 15.
