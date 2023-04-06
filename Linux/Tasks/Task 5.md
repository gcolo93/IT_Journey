### Task : access your home directory and special system directories
In this task, you will enter commands to obtain information and access specified directories, using commands and options.

**Knowledge Item: a directory in Linux is just a file where each line contains two entries - a file identification number and a file name. The file-id number is used to locate all of the data needed to be able to access the file (contents). You can see these two items by using the option -i on the ls command. Enter : ls -i**

In the terminal window, enter the command(s) (**in red**) :

show the current default directory (path)

**pwd**

create a subdirectory

**mkdir subdir**

show what **subdir** is

**file subdir**

show full attributes of **subdir**

**stat subdir**

show attributes of **subdir** on one line

**ls -ld subdir**

change current default directory (path

**cd subdir**

show the (new) current default directory (path)

**pwd**

**Knowledge Item: the "home" directory is the path that is tied to a user account, and is the default at login. It can be referenced by using the environment variable HOME, and is the default path for the cd command.**

change the default directory to **HOME**

**cd**

show paths of special directories

**man 7 hier**

show attributes of special directories

**ls -ld /etc /usr/bin /usr/sbin /var**

### Task : get file and directory information
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.

**Knowledge Item: the ls and dir commands do exactly the same operations, and return the same file information. The difference is that ls returns color coded output (by default), while dir does not return color coded output.**

In the terminal window, enter the command(s) (**in red**) :

change the default directory to **HOME**

**cd**

show major attributes on one line

**ls -l .bashrc**

**Hint: You will also notice that many commands in the next sequence are similar in their syntax, differing only by an option and/or and argument (value). Instead of re-entering the command again, you can hit the up-arrow key to recall the previous command, then modify it as needed.**

show files from newest to oldest (age) (**q** to exit)

**ls -lta | tail --lines=+2 | more**

show the newest file

**dir -lta | tail --lines=+2 | head -1**

show files from oldest to newest (age) (**q** to exit)

**ls -ltra | tail --lines=+2 | more**

show the oldest file

**dir -ltra | tail --lines=+2 | head -1**

show files from largest to smallest (size) (**q** to exit)

**ls -lSa | tail --lines=+2 | more**

show the largest file

**dir -lSa | tail --lines=+2 | head -1**

show files from smallest to largest (size) (**q** to exit)

**ls -lSra | tail --lines=+2 | more**

show the smallest file (**q** to exit)

**dir -lSra | tail --lines=+2 | head -1**

**Knowledge Item: the default ls color coding : blue for a directory, cyan for a symbolic link, red for an archive, for an executable.**