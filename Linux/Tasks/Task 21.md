### Task : get information for the : /var, /etc, /usr[/bin /sbin], /sbin, /opt system directories
In this task, you will look at the use and purpose of selected system directories.

**Knowledge Item: you will be looking at the man page for the Linux F(ile) H(ierarchy) S(ystem) information for selected directory hierarchies .**

In the terminal window, enter the command(s) (**in red**) :

for /var

**man 7 hier    then enter : 357**

**look at all entries related to /var**

`                      `**then enter: q**    

for /etc

**man 7 hier    then enter : /etc**

**look at all entries related to /etc**

`                      `**then enter: q**    

for /usr

**man 7 hier    then enter : 113**

**look at all entries related to /usr**

`                      `**then enter: q**    

for /sbin

**man 7 hier    then enter : 100**

**look at all entries related to /sbin**

`                      `**then enter: q**    

for /opt

**man 7 hier    then enter : 89**

**look at all entries related to /opt**

`                      `**then enter: q**    
### Task : use the **hostname** and **ip** commands, /etc/resolv.conf and nsswitch.conf files
In this task, you will enter commands to view networking information.

**Knowledge Item: a Linux system network identity is defined by the combination of the contents of files and results of utilities that startup mechanisms to allow both outbound and inbound activities with other systems (and even the Internet).**

In the terminal window, enter the command(s) (**in red**) :

show hostname

**hostname**

storage of hostname

**cat /etc/hostname**

show IPv4 information

**ip address show**

show IPv4 information

**nmcli con show**

show NIC information

**ip link show**

show NIC information (**q** to exit)

**nmcli dev show**

**Knowledge Item: name server and router information (to get to other networks) is controlled by the contents of files and running daemon services.**

show routing tables

**netstat -rn**

show routing tables

**route**

show routing tables

**ip route**
### Task : install, list (information), and remove Red Hat and Debian family software packages
In this task, you will enter commands to manipulate software packages.

**Knowledge Item: The Red Hat and Debian families of Linux systems use different tools to install, list, and remove software package.**

**Note: since you are doing the lab exercises on a Red Hat family Linux system, you will not be able to execute the commands labeled as "Debian" (but the concepts are the same). You would need access to a Debian family Linux system to execute these commands .**

In the terminal window, enter the command(s) (**in red**) :

see if package is installed (RHEL)

**rpm -q systemd**

see if package is installed (Debian)

**dpkg -s systemd**

list package contents (RHEL) (**q** to exit)

**rpm -ql systemd | less**

list package contents (Debian)

**dpkg -c systemd**

**Knowledge Item: installing or removing a package requires a root identity (via sudo ), and an accessible package repository.**

install package (RHEL)

**sudo yum -y install ruby**

install package (Debian

**sudo apt-get install ruby**

remove package (RHEL)

**sudo yum -y remove ruby**

remove package (Debian)

**sudo apt-get remove ruby**