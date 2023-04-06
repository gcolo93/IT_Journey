### Task : get file and directory names from standard utilities
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.

**Knowledge Item: the ls command actually does not search the specified directories contents. It returns files by (1) simple name match, or (2) by attribute match, or (3) file names returned by the BASH shell when wildcard characters are used - the shell wildcard characters are : \* (splat) ? (hook) [ ] (list)**

In the terminal window, enter the command(s) (**in red**) :

show all non-dot files

**ls \***

fails - **ls** cannot process shell wildcard characters

**ls '\*'**

shell returns matching files / directories

**ls .b\***

**ls** shows contents of returned directories

**ls /course/\***

**ls** shows returned directory name only

**ls -d /course/\*/**

shell returns matching files / directories

**ls /course/?????**

shell returns matching directories

**ls -d /course/mngmnt/????\*/**

shell returns matching directories

**ls -d /course/mngmnt/[a-d]\*/**

shell returns non-matching directories

**ls -d /course/mngmnt/[!a-d]\*/**

**Knowledge Item: the find command supports shell when wildcard characters are used - the shell wildcard characters are : \* (splat) ? (hook) [ ] (list)**

help on find command and its options

**find --help | less**

default is to list out entire hierarchy

**find /course**

locate all file names that start with "d"

**find /course -name "d\*"**

locate all directory names that start with "d"

**find /course -name "d\*" -type d**

**Knowledge Item: find command permissions can be specified in either absolute or symbolic format.**

locate all files with specified absolute permissions

**find /course -perm 755**

locate all files with specified symbolic permissions

**find /course -perm "u=rwx,go=rx"**