### Task : get information on the Linux system version
In this task, you will enter commands to obtain information on your Linux lab system, using commands and the contents of system files.

In the terminal window, enter the command(s) (**in red**) :

show the name of the system kernel **uname -s** 

show the version of the kernel **uname -r**

show the names of the kernel program files **ls /boot/vmlinuz-\***

show the (network) nodename **uname -n**

show the hardware platform architecture **uname -i**

**Command Hint: a useful feature of open source application commands is the ability to use the option --help which shows all of the ways to execute the command; in this case, enter : uname --help**

**Knowledge Item: There are also a number of text files that contain information about the actual Linux system itself.**

list the names of the matching files

**ls /etc/\*release**

**Knowledge Item: note that the file /etc/system-release is shown in a blue color; this is called a symbolic link file. This type of file points to another file. The advantage of a symbolic link file is that a "known filename" can be documented for a given purpose, and used on multiple (Linux) systems.**

shows the name and version of this system

**cat /etc/system-release**

### Task : get open source licensing information
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.

In the terminal window, enter the command(s) (**in red**) :

opening up a manual page

**man perlgpl**

search for the specified string in the **man** page (**q** to exit)

**then enter: /GEN**

**Knowledge Item: at this point you will be in the "man" page output, with the string: GNU GENERAL PUBLIC LICENSE at the top of the window. Please do a brief scan of the content on the screen, then hit the f key to continue on to the next screen. While there are thirteen (13) screens of the licensing information, you don't need to read the contents of every screen.**

**Knowledge Item: GNU = GNU (is) not Unix - this was meant to be a "tongue-in-cheek" way of specifying that the commands and files in Linux do the same things (and more) than their original Unix system counterparts, but are not technically the same.**




















### Task : get open source and version information from utilities
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.

**Knowledge Item: FSF = Free Software Foundation - this organization was founded in 1989 to promote the development and sharing of open source applications and systems.**

In the terminal window, enter the command(s) (**in red**) :

show version and licensing information

**perl --version**

**Hint: you can add the --version option to almost any command on a Linux system to provide version and licensing information.**

show version and licensing information

**python3 --version**

show version and licensing information

**grep --version**

show version and licensing information

**bash --version**

**Linux supports every major database platform :**

- Oracle
- mySQL
- sqlite (native)
- MariaDB (native)
- Postgres (native)
- SQL Server (starting with the 2017 version)

### Task : get version and device information
In this task, you will enter commands and options to obtain system information.

In the terminal window, enter the command(s) (**in red**) :

list out release file names

**ls /etc/\*release**

show Linux variant release file contents

**cat /etc/redhat-release**

documentation on the **uname** command (**q** to exit)

**info coreutils 'uname invocation'**

show Linux kernel version

**uname -v**

show Linux kernel release date

**uname -r**

**Knowledge Item: uname actually means unix name !**

naming conventions - kernel file name

**ls /boot/vmlinuz\***

naming conventions - storage devices

**lsblk /dev/sda**

naming conventions - storage devices

**lsblk /dev/sr0**

### Task : get hardware device information
In this task, you will enter commands to list hardware devices (and attributes).

In the terminal window, enter the command(s) (**in red**) :

hardware listing short summary

**lshw -businfo**

show configured CPU IDs

**grep proc /proc/cpuinfo**

show CPUs that are enabled

**lscpu -p=cpu,online | grep -v "^#"**

disable second CPU

**sudo chcpu -d 1**

show CPUs that are enabled

**lscpu -p=cpu,online | grep -v "^#"**

enable second CPU

**sudo chcpu -e 1**

show disks and partition information

**lsblk -o name,size,type**

show all mounted filesystem information

**df -h -T -t xfs -t ext4 -t ext2**

show USB device(s)

**lsusb**

### Task : use the **lsblk**, **pvs**, **vgs**, and **lvs** commands and the file /proc/partitions
In this task, you will enter commands to view storage area descriptions.

In the terminal window, enter the command(s) (**in red**) :

show disk storage information

**lsblk -o name,size,type,mountpoint,fstype**

show all mounted filesystem information

**df -h -T -t xfs -t ext4 -t ext2**

show kernel view of storage areas

**cat /proc/partitions**

**Knowledge Item: LVM (logical volume management) allows you take combine multiple storage areas of disk storage, create logical volumes from the combined space, and dynamically increase the size of a mouned file system in a logical volume**

show physical volume(s)

**sudo pvs**

show volume group(s)

**sudo vgs**

show logical volume(s)

**sudo lvs**