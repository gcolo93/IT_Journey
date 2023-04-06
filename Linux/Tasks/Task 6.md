### Task : use the **cp** command and options
In this task, you will enter commands to make copies of files and directory hierarchies.

**Knowledge Item: the ls and dir commands do exactly the same operations, and return the same file information. The difference is that ls returns color coded output (by default), while dir does not return color coded output.**

In the terminal window, enter the command(s) (**in red**) :

summary of options (**q** to exit)

**cp --help | less**

documentation for **cp** command (**q** to exit)

**man cp**

basic copy operation

**cp .bashrc new-file**

copy with output messages

**cp -v .bashrc new-file**

copy with overwrite check

**cp -i .bashrc new-file**

create directory hierarchy

**mkdir -p subdir1/subdir2/subdir3**

**ls -laR subdir1**

**Knowledge Item: the sudo command allows you to run any command in the administrator account (root), but you must enter your user account password to validate the usage.**

install tree program

**sudo yum -y install tree**

**Knowledge Item: the user password that is entered is masked so that you do not see the actual characters.**

**Knowledge Item: the tree program draws a representation of a directory hierarchy.**

draw directory hierarchy

**tree subdir1**

copy directory hierarchy

**cp -r subdir1 subdir4**

draw directory hierarchies

**tree subdir1 subdir4**

**Knowledge Item: in Lab 2 section 05 you will rename and remove files and directories.**

### Task : use the **mv**, **rm**, and **rmdir** commands and options
In this task, you will enter commands to rename and delete files and directory hierarchies.

In the terminal window, enter the command(s) (**in red**) :

summary of options (**q** to exit)

**mv --help | less**

**Knowledge Item: to exit from the paginated output, hit the letter: q at the : prompt**

rename the file new-file to newer-file

**mv new-file newer-file**

show files - **note the error message !**

**ls new-file newer-file**

move (not copy) the file newer-file into a subdirectory

**mv newer-file subdir1**

**Knowledge Item: moving a file to another directory only moves the inode number and file name into the target directory - the file's data does not get relocated**

show changes - **note the error message !**

**ls newer-file ; ls subdir1**

**Knowledge Item: you can do multiple commands on one line by separating them with a semi-colon ( ; ) - it is called a command separator.**

delete file with prompt

**rm -iv subdir1/newer-file**

fails : directory is not empty

**rmdir subdir1**

**ls -la subdir1**

fails : not correct method

**rm subdir1**

remove hierarchy recursively

**rm -rf subdir1**

**Knowledge Item: the -f option to rm says to force the deletion(s) whether the files and directory exist (or not).**

**NOTE: the rm -rf is the most dangerous and destructive command on the entire Linux system. Once executed, there is no way to reverse the damage, other than to restore from backups. A good suggestion would be to add the -i option, so that you would be prompted (and verify the path is correct first)**