### Task : use the **useradd** and **groupadd** commands (and options)
In this task, you will enter commands to obtain information for logged in user processes

In the terminal window, enter the command(s) (**in red**) :

**useradd** command options (**q** to exit)

**useradd --help | less**

create user with defaults

**sudo useradd newuser**

**Knowledge Item: useradd gets defaults for the new user account attributes from the files /etc/default/useradd and /etc/login.defs. By default, a new group using the new user account name is also created.**

show new user record

**grep newuser /etc/passwd**

show new group record

**grep newuser /etc/group**

show new user home directory attributes

**ls -ld /home/newuser**

no password for new user account (**second field**)

**sudo grep newuser /etc/shadow**

set password for user account (**remember the password value !**)

**sudo passwd newuser**

show hashed password for new user account

**sudo grep newuser /etc/shadow**

try logging into the new user account

**ssh newuser@localhost**

**Knowledge item: to logout of the ssh session, enter the exit command.**

create new group

**sudo groupadd newgroup**

verify group creation

**grep newgroup /etc/group**

put user into the new group

**sudo usermod -aG newgroup newuser**

show groups for the user

**groups newuser**

### Task : use the **userdel** and **groupdel** commands (and options)
In this task, you will enter commands to remove user accounts and group identifiers.

In the terminal window, enter the command(s) (**in red**) :

**userdel** command options (**q** to exit)

**userdel --help | less**

**Knowledge item: userdel only removes entries from : /etc/passwd, /etc/shadow, and /etc/group. It does not remove the email and home directories, unless the -r option is added.**

remove all traces of the user account

**sudo userdel -r newuser**

verify user record has been removed

**grep newuser /etc/passwd**

verify user home directory was deleted (**note the error message**)

**ls -ld /home/newuser**

**groupdel** command options (**q** to exit)

**groupdel --help | less**

delete group identifier

**sudo groupdel newgroup**

verify group identifier has been removed

**grep newgroup /etc/group**