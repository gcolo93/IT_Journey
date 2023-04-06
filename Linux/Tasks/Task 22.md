### Task : Examine user information in the files: /etc/passwd, /etc/shadow, /etc/group, and /etc/gshadow, and via the commands: **id** and **groups**
In this task, you will enter commands and options to obtain information on your Linux lab system.

**Knowledge Item: authorized user information is spread across a number of different files. All system type data files also have a mannual page in section 5.**

In the terminal window, enter the command(s) (**in red**) :

man\*\* pages for system files

**man 5 passwd shadow group gshadow**

locate specific record in passwd file

**grep "^root" /etc/passwd**

locate specific record in shadow file

**sudo grep "^root" /etc/shadow**

**note that the /etc/shadow file can only be assessed as root (via sudo).**

groups to which root belongs

**sudo groups**

locate specific record (for root groups)

**grep "^root" /etc/group**

locate specific record (for root groups)

**sudo grep "^root" /etc/gshadow**

**note that the /etc/gshadow file can only be assessed as root (via sudo).**

show UID, GID(s) and SELinux context

**id**

UID, GID(s), SELinux context for root

**sudo id**

### Task : use the **who, w, finger, whoami** and **top** commands
In this task, you will enter commands to obtain information for logged in user processes

In the terminal window, enter the command(s) (**in red**) :

current username (only)

**whoami**

current username, UID, GID, and group(s)

**id**

list of logged in users

**who**

current user information from **who**

**who am i**

a more verbose **who**

**w**

install **finger** utility

**sudo yum -y install /home/files/finger-0.17-52.el7.x86\_64.rpm**

parts from **who** and **w** with user information

**finger**

**Knowledge Item: you can change the personal information field (Name) in the finger command output by using the command: chfn . You will have to enter your password to change the personal information field.**

change personal information field

**chfn -f "*put-your-real-name-here*"**

**Knowledge item: the personal information field is stored in the /etc/passwd file (seen in the previous lab section).**

note the difference in the **Name** field

**finger**

dynamic display of specific user processes

**top -u $USER**