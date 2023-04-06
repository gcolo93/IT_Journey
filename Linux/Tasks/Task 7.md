### Task : use the **chmod**, **chown**, **chgrp**, **setfacl** commands and options
In this task, you will enter commands to change file security and ownership attributes.

In the terminal window, enter the command(s) (**in red**) :

make copy of existing file

**cp .bashrc new-file**

permissions and ownership

**stat new-file | grep "^Access: ("**

**Knowledge Item: the grep command searches for text, sometimes using characters called "regular expressions". You will work with these two important parts of Linux in Lab 3. For now, note the base eight (octal) codes and the symbolic r(ead) and w(rite) strings.**

change permissions

**ls -l new-file**

**chmod 755 new-file**

**ls -l new-file**

change permissions

**chmod u=rwx,go=rx new-file**

**ls -l new-file**

change file ownership

**sudo chown root new-file**

**ls -l new-file**

change group ownership

**sudo chgrp root new-file**

**ls -l new-file**

**Knowledge Item: note that only the root account can change file (group) ownership.**

show change in ownerships

**stat new-file | grep "^Access: ("**

allow write access by user60

**sudo setfacl -m u:$USER:rw- new-file**

show file (modified) ACL

**getfacl new-file**

**Knowledge Item: the ACL (access control list) for a file (or directory) contains both standard and special access permissions. More on ACLs in Lab 5.**