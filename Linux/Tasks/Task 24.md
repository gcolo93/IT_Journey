### Task : use the **chmod, chown, chgrp** and **setfacl** commands (and options)
In this task, you will enter commands to change file security and ownership attributes.

In the terminal window, enter the command(s) (**in red**) :

make a copy of existing file

**cp .bashrc new-file**

show permissions and ownership

**stat new-file | grep "^Access: {"**

**Knowledge Item: the grep command searches for text, sometimes using characters called "regular expressions". You worked with these two important parts of Linux in Lab 3. For now, note the base eight (octal) codes and the symbolic r(ead) and w(rite) strings.**

change permissions

**chmod 755 new-file**

**Knowledge Item: Linux permissions in octal: 4 = r(ead),**

**2 = w(rite), 1 = (e)x(ecute). If the desired permissions for a category are rwx, the octal code is 4+2+1=7. If the desired codes were r-x, the octal code is 4+1=5. All three categories (user, group, others) codes must be supplied when setting absolute codes, such as: 755.**

change permissions

**chmod u=rwx,go=rx new-file**

change file ownership

**sudo chown root new-file**

change group ownership

**sudo chgrp root new-file**

**Note: only the root account can change file (group) ownership (via sudo).**

show change in file and group ownerships

**stat new-file | grep "^Access: {"**

allow write access by specified user

**sudo setfacl -m u:${USER}:rw- new-file**

show file ACL

**getfacl new-file**

**Knowledge Item: the access control list (ACL) for a file (or directory) contains both standard and special access permissions. More on ACLs in Lab 5 section 07.**

### Task : use the **ls, stat** and **getfacl** commands (and options)
**In this task, you will enter commands to view directory file attributes.**

**Knowledge Item: all directory (files) have three associated date(s) of last : (a) modification of (data) contents; (b) change of attributes; and (c) access of data contents. These dates can be seen with the commands ls and stat.**

**In the terminal window, enter the command(s) (in red) :**

**show the three major dates**

**ls -ld $HOME ; ls -ldc $HOME ; ls -ldu $HOME**

**show all attributes of the home directory**

**stat $HOME**

**Note: : there is column labeled: "Birth:" (but has no associated date). Only the ext4 file system type supports storing file creation dates, and there is no easy way to see that date.**

**isolate the three major dates**

**stat $HOME | egrep "^Access: [[:digit:]]|^Modify:|^Change:"**

**Knowledge Item: all files also have an ACL (access control list). The ACL contains both standard permission codes and specific user and/or group access capabilities. The getfacl command shows both security areas. The setfacl command changes the specific user and/or group accesses (next in Lab 5 section 07).**

**show the ACL contents**

**getfacl $HOME**

### Task : apply **chmod** (SUID and SGID) settings, and use **setfacl** to control ACE (access control entries) on files
**In this task, you will enter commands to change file security and ownership attributes.**

**Knowledge Item: two special attributes can be put onto executable program files: (a) SUID - when the program is run, the effective UID (user identification) is that of the executable program file owner instead of the actual user that is running the program; and (b) SGID - when the program is run, the effective GID (group identification) is that of the executable program group owner instead of the actual user's primary group that is running the program.**

[**more...**](https://labclient.labondemand.com/Instructions/eba3574a-df4b-4f78-9b87-4f0631e66e5a?rc=10#)

**In the terminal window, enter the command(s) (in red) :**

**make copy of existing executable**

**cp /usr/bin/bash test\_shell**

**show user (UID) and group (GID) ownerships**

**stat test\_shell | grep "^Access: ("**

**create child shell process**

**./test\_shell**

**show identity (no changes)**

**id**

**logout from child shell process**

**exit**

**change file and group ownerships**

**sudo chown root:root test\_shell**

**change permissions (4 = SUID)**

**sudo chmod 4755 test\_shell**

**show (changed) UID, GID, and permissions**

**stat test\_shell | grep "^Access: ("**

**run with protected child shell process (allows changing effective UID)**

**./test\_shell -p**

**show different identities**

**id | gawk '{print $3,$4}**

**logout from child shell process**

**exit**

**show identity (changes removed)**

**id**

**change permissions on root home dir**

**sudo chmod 755 /root**

**make copy of existing file (as root)**

**sudo cp /root/.bashrc /root/test\_bashrc**

**change file permissions (root only access)**

**sudo chmod 400 /root/test\_bashrc**

**show permission codes**

**sudo ls -l /root/test\_bashrc**

**error - no access via permission codes**

**cat /root/test\_bashrc**

**allow read access to user**

**sudo setfacl -m u:$(logname):r-- /root/test\_bashrc**

**Knowledge Item: $(logname) substitutes in the name of the real user that executed the sudo command.**

**show the effective access for the user**

**getfacl -e /root/test\_bashrc**

**Knowledge Item: The effective access field shows the capabilities that the specific user (and/or group) has to the file, without changing any other category-based access codes.**

**access is now successful**

**cat /root/test\_bashrc**