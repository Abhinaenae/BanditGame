# Level 12 to 13

## Goal:
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Solution
First, connect to bandit11 via `ssh bandit12@bandit.labs.overthewire.org -p 2220`.

Hexdumps are often used when we want to look at data that cannot be represented in strings and therefore is not readable, so it is easier to look at the hex values. A hexdump has three main columns. The first shows the address, the second the hex representation of the data on that address and the last shows the actual data as strings (with ‘.’ being hex values that cannot be represented as a string). Many hex editors exist just pick the one you like most.

For the command line xxd can be used. xxd <input_file> <output_file> creates hexdumps. When using the -r flag, it reverts the hexdump.

Our solution is split into 3 part: creating a directory in tmp, reverting the hexdump, and decompressing:


1. Creating a directory in /tmp

![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/5f3c85ce-8532-4ba0-b38c-c25c484c48c5)

2. Reverting the hexdump
    
The contents of the file looks like this:

![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/f7782947-318c-450a-9dd3-2b401397be71)

We want to operate on the actual data so we want to revert it and get the actual data, after reverting the hexdump with `xxd -r hexdump_data output`, we get this:
![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/1dde6952-346b-43bf-9acb-7e0114100266)

3. Decompressing the file

We can see the contents are unreadable, so we need to repeatedly decompress the data. To figure out what decompression we need to use, look at the first bytes in the hexdump to find the file signature. We can search for these first bytes in a list of file signatures. An alternative would be to use the find command.

First, we need to use gzip to decompress. Note: you need to add the `.gz` file extension to use gzip on the file.
![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/91060f18-9a68-4931-9f80-bee310b061f1)

However, the data is still not fully decompressed, so we look at the first bytes again:
![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/745af400-a64a-4ea6-872e-58d01cfbc448)
This time we have a different magic number. Quick googling tells us that BZ (= ‘425a’) is the file signature for bzip and the next two bytes h (= ‘68’) indicate the version, in this case, it is version 2. So we can rename the file with the appropriate file ending (.bz2) and decompress it with `bzip2 -d`

After running with `bzip2 -d output`, we can still see that its compressed with gzip thanks to xxd. We need to repeat the gzip process(renaming and decompressing).

![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/778a56a0-5c63-49f0-98fc-bf27119674d6)

We can see the data5.bin string, which is a filename, indicating it is an archive. We can use `tar` to extract it. After renaming our output file, run these commands:
![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/f452b571-b2e6-4601-846b-387ba214d55b)

We see data5.bin, but it seems to be another archive containing data6.bin, so run `tar -xf data5.bin`.

![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/1fdbbe0c-a85d-4446-85b2-673c7316473a)

We can see data6.bin is bzip2 compressed. So, we need decompress it.

![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/d2f2d75a-a3ea-430e-803f-68d9a0bb2a6f)

‘data6.bin.out’ shows another file name ‘data8.bin’ again. So we extract this file with `tar -xf data6.bin.out`.

![image](https://github.com/Abhinaenae/BanditGame/assets/92381984/fed285d2-05ed-4839-9fd3-955795bc5a6d)

Finally, we see data8 and the password is given.

We get the password for level 13: `wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw`

On to level 14!
