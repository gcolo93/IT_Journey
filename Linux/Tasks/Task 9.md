### Task : create, list, and extract from archives using the **tar** utility
In this task, you will use the **tar** command and options

**Knowledge Item: the tar command creates a (tape) archive file, although most tar archives are stored as disk files. A tar archive is made up of twenty (20) 512-byte fixed-length records - a tar block. A tar archive is a collection of one (or more) of the 10240 byte blocks. A tar archive can only be created, listed, and extracted from using the tar command.**

In the terminal window, enter the command(s) (**in red**) :

help on the **tar** command and its options (**q** to exit)

**tar --help | less**

**Hint: when creating a tar archive, a best practice is to specify the files and/or directories being archive as a relative path (to where ever the default directory is at that time). There are two ways to do this : (1) cd to the directory that is one level above the directory hierarchy being archived or (2) use the -C option on the tar command line.**

to archive a top level directory

**cd /**

**pwd**

create **tar** archive

**tar -cvf $HOME/userfind.tar ./userfind**

\*\*Knowledge Item: ./userfind is relative to the current default directory path of / .

back to **HOME** directory

**cd**

**pwd**

create (same) **tar** archive

**tar -C / -cvf $HOME/userfind.tar ./userfind**

show archive file type contents

**file userfind.tar**

show archive file attributes

**stat userfind.tar**

list contents tar archive

**tar -tvf userfind.tar**

extract entire **tar** archive to the current default directory

**tar -xvf userfind.tar**

show created files and directories

**ls -R ./userfind**

extract entire tar archive to a specific directory

**tar -C /tmp -xvf userfind.tar**

show created files and directories

**ls -R /tmp/userfind**

**Hint: when extracting (or restoring) files from a tar archive, the default is to restore all files to the current default directory path. You can also specify a (list of) file(s) and/or directory paths to restore, but they key is to specify the files as they were archived, meaning the exact path captured in the archive. Any directories in the path will be created if they do not already exist.**

extract specific file - **fails, incorrect path**

**tar -xvf userfind.tar name**

get specific archived file path to restore

**tar -tvf userfind.tar | grep name**

extract specific file - **works with archived path**

**tar -xvf userfind.tar ./userfind/name**