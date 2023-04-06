### Task : use the commands **lsblk**, **fdisk**, and **parted** commands and options
In this task, you will use disk partitioning tools.

In the terminal window, enter the command(s) (**in red**) :

list storage devices only

**lsblk | grep disk**

**Knowledge Item: all partitioning tools must be run as root (via sudo).**

command line disk partitioning tool

**sudo fdisk /dev/sda**

show disk geometry and partition table

at the **Command :** prompt, enter : **print**

at the **Command :** prompt, enter : **quit**

command line disk partitioning tool

**sudo parted /dev/sda**

show disk geometry and partition table

at the **(parted)** prompt, enter : **print**

at the **(parted)** prompt, enter : **quit**

show partition table

**sudo partx -l /dev/sda**

show partition table

**sudo kpartx -l /dev/sda**

show partition table

**sudo cfdisk /dev/sda**

hit **enter** to select: **Quit**

show disks and total sizes

**sudo sfdisk -s**

show disk geometry and partition table

**sudo sfdisk -l /dev/sda**