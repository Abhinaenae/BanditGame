# Level 15 to 16

## Goal:
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.
## Solution
First, connect to bandit15 via `ssh bandit15@bandit.labs.overthewire.org -p 2220`.

We need the password of the previous level, which is `jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt`

To use SSL encryption, we can use OpenSSL. It is is a library for secure communication over networks. It implements the Transport Layer Security (TLS) and Secure Sockets Layer (SSL) cryptographic protocols.

openssl s_client is the implementation of a simple client that connects to a server using SSL/TLS, which is perfect for this level. You can use this format to connect: `openssl s_client -connect <host_ip>:<port>`



Below is a visual:

```
bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
. . . . . . . . . . .
read R BLOCK
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1

closed
```
This gives us the password: `JQttfApK4SeyHwDlI9SXGR50qclOAil1`, allowing us to access level 16. Level 16 is located in `BanditGame/16-20/lvl6.md`
