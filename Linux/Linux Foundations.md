## 1.1 Linux Evolution and Popular Operating Systems

## Topics:
* Open Source Philosophy 
* The birth of Linux 
* Distributions 
* Embedded Systems 
* Comparison with other popular Operating Systems 

### Open Source Philosophy
Source refers to the source code or the actual text code that is compiled to make a program. 
Having access to the code allows you to understand how the program works and perhaps to contribute additions to the program.
This means there are many 100s and perhaps 1000s of contributors to the code.

### The Birth of Linux
The first Linux kernel, the core of the Operating System, was released in 1991 by a student from Helsinki University, Linux Torvalds. 
In 1992 was re-released under the GNU license that opened the kernel to the wealth of GNU (Not Unix programs and utilities). 

### Linux Distributions
A distribution is the kernel packages with installers and additional software. This makes the kernel usable to humans: 
Red Hat Enterprise Linux 
SUSE Enterprise Linux 
Ubuntu 
Debian 
openSUSE 
Fedora 
Linux Mint 
The website distrowatch.com keeps track of downloads. 

### Embedded Systems
You are also going to find Linux in many devices: 
TiVo boxes 
Network Storage Servers 
Print Servers 
Android Phones 
Linux is free so it makes sense to use a free OS when building a dedicated server 



## Comparison with other OSs
### MAC OSX:
This uses a version of BSD Unix, not dissimilar to Linux. Using the command line on OSX is going to be very similar to Linux 
### Windows: 
Windows has made a huge success out of the Graphical Interface but are starting to move back towards command line with PowerShell
### UNIX: 
Linux was born out of Unix but with the requisite to be free and open source

## 1.2 Major Open Source Applications

## Topics:
Desktop Applications 
Server Applications 
Mobile Applications 
Development Languages 
Package Management Tools and Repositories 

### Desktop Applications
LibreOffice: Office suite 
Firefox: Browser 
Thunderbird: Email client 
Gimp: Photo editing and graphics 
Audacity: Manage and edit sound files 
These applications are cross platform, they can run on Windows, Mac, and Linux 

Server Applications (Services)
Apache: Web server
MySQL, MariaDB, PostgreSQL Database Servers
Squid: Web proxy
NFS: Linux and Unix File Server
SAMBA: Windows, File, Print Server and Domain Server
openLDAP: Directory Server
DNS / DHCP: Network Infrastructure services

Mobile Applications
Linux is Linux is Linux, it does not differ between server, desktop and mobile Linux
Windows CE, Windows 8 mobile are different OSs to the Windows Desktop and Server, as is Server different from Desktop
Many Linux server and desktop apps then will work on mobile Linux, Android.
Some mobile Linux apps will be written from the ground up for mobile devices

Development Languages
Simple “scripts” can be made to automate tasks using shell scripting (.sh)
PHP is often used to provide access to Databases from Apache (LAMP: Linux Apache MySQL PHP)(.php)
Perl: Perl scripting is effective and cross platform (.pl)
Python: Due to its power, simplicity, and complete object model, Python has become the scripting language of choice for many large organizations (.py)

Package Management Tools and Repositories
The Apple Store; The Microsoft Store, we might think these innovative and useful
They are not new and Linux has used Software Repositories for years
A software repository, or repo, is an online location where software can be installed from
Of course, you will not need your credit card for Linux repos

Accessing the Repo
Different distributions will use different tools
Red Hat, CentOS: Use YUM
SUSE uses ZYPPER
Ubuntu uses APT-GET
In essence, they all do the same job in locating software from defined repositories and installing the software along with any dependency packages


































1.3 Understanding Open Source Software and Licensing

Topics:
Open Source Licensing
Free Software Foundation (FSF)
Open Source Initiative (OSI)
Open Source Business Models

Open Source Licensing
The most common license that we will come across is the GPL license, GNU General Public License
Others exist, such as the BSD License, (FreeBSD license) and the Creative Commons License
In all there are about 70 licenses that can refer to Open Source

GPL 2
The current version is GPL 3, much software though still uses the established GPL 2 license and dates back to June 1991, predating the Linux Kernel

GPL 3
The current GPL which now dates to 2007, was updated to cover patenting and the abuse of the previous GPL on mobile devices where users could not modify the code

BSD
The BSD License hails from the University of California
The original owner can still copyright the source and binaries but free distribution is permitted
Redistributions of source code must retain the above copyright notice, this list of conditions, and the following disclaimer.
Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

Creative Commons
This refers to written works such as manuals and how-tos
Different CC licenses may require the work to be attributed to the original owner or may prohibit commercial reuse

Free Software Foundation
Founded by Richard Stallman in 1985
Defines free software as:
The freedom to run the program, for any purpose
The freedom to study how the program works, and change it so it does your computing as you wish
The freedom to redistribute copies so you can help your neighbor
The freedom to distribute copies of your modified versions to others
Thus, “free software” is a matter of liberty, not price. To understand the concept, you should think of “free” as in “free speech,” not as in “free beer”.
http://www.fsf.org

Open Source Initiative
The OSI are the maintainers of many of the open source software licenses
They define themselves as the stewards of the Open Source definition
Not for profit organization founded in 1998

Open Source Business Models
Companies like RedHat, SUSE, and Canonical, do very well in providing enterprise level support based on subscription
There are many ways to make money by providing software or services for free.





























1.4 ICT Skills and Working in Linux

Topics:
Desktop Skills
Accessing the Command Line
Industry uses of Linux, Cloud Computing and Virtualization

Desktop Skills
Identify different Linux Windows Managers
KDE
GNOME
Unity
Logging in and out, using the browser, configuration option
Managing passwords
Permissions
Using open source applications and your office suite

Accessing the Command Line
Terminal
Console
SSH

Industry Uses for Linux
You are going to find Linux commonly as servers but as desktops in some organizations
Virtualization hosts such as Citrix Xenserver are Linux based
Many virtual appliances for both VMWare and XenServer are Linux based.


















2.0 Python Primer

Topics:
Hello world!
Reading arguments
Testing root access
Writing to files

Hello world
#!/usr/bin/python3
print(“Hello World”)

Reading Script Arguments
#!/usr/bin/python3
import sys
print(sys.argv[1])

Testing for Root Access
#!usr/bin/python3
import sys, os
if not os.geteuid()==0:
sys.exit(“\nOnly root can write this\n”)
print(sys.argv[1])

Writing to a File
#!/usr/bin/python3
import sys, os
if not os.geteuid()==0:
sys.exit(“\nOnly root can write this\n”)
hosts=open(“/etc/hosts”,”a”)
hosts.write(sys.argv[1] + os.linesep)
host.close()












2.1 Command Line Basics

Topics:
Basic Shell
Formatting Commands
Working with options
Variables
Globbing
Quoting

Linux Command Line
The CLI, command line interface, has always been important within Linux
Especially if you are working with servers the CLI will continue to have great focus in Linux

Commands
Ctrl+Shift++: makes shell font bigger
Ctrl+Shift+-: makes shell font smaller
Ctrl+D: exits shell (can type ‘exit’ command as well)
Ctrl+L: clears screen
touch: create file
env: show variables
globbing is grouping characters together
Linux is case sensitive
history: shows used commands
Anything that includes a space must be in quotations “”
semicolon allows multiple commands to be run on the same line
double pipe || specifies to do one command of the other fails.
double ampersand && specifies to run the second command if the first succeeds















2.2 Obtaining Help from the Command Line

Topics:
Man pages
Info pages
‘- - help’
/usr/share/doc
apropos
whatis
whereis

Obtaining Help
command - - help | less will show a more organized list of features for the command
which will show all locations of an instance
for more information you man command
forward slash / allows you to search through man pages
info command will show more information as well
q to quit out
whereis command will show all locations of the man pages and executables
whatis command shows what/where the page/command is
pwd gives current working directory
/usr/share/doc houses the information for packages and files






















2.3 Using Directories and Listing Files

Topics:
Files and Directories
Hidden Files, Directories
Home and ~
File paths
cd
ls and aliases

Everything is a File
Everything in Linux is a file
Files
Directories
Links
/dev/sda1 is a file for a block device, disk partition
/dev/tty1 is a file for a character device, terminal

Hidden Files
A hidden file or directory in Linux is identified by the name starting with a dot
Use ls -a to display all files including hidden files
To display ONLY hidden files use ls -a | grep ‘^\.’

Knowing your way home
cd or cd~ to return directly to the home directory
The home directory is normally /home/<username>

Full and Relative Paths
We can access files or directories with the full path: cd /home/andrew/Documents
can use cd <folder in current directory> to go directly to a folder in the current directory.
File and Directory names are case sensitive
cd ../<Directory> moves up one directory from current location

ls and alias
The command ls lists directory contents that are color coded
when ls is run, it is actually ls - color=”auto” or something similar
Using the command: type ls we can see ls is aliased to ls with additional options
If we run the command: \ls the backslash means that it runs unaliased





2.4 Working with Files and Directories

Topics:
Files and Directories
Globbing and Quoting
mv, cp, rm, touch
mkdir, rmdir

Commands
cd !$ uses last argument
mkdir makes an empty directory
rmdir removes an empty directory
cp copies files/directories
touch creates an empty file
rm removes files
mv moves files




























3.1 Archiving Files on the Command Line

Topics:
Archiving files and compression
tar command
compression with gzip and bzip2
Extracting archives and individual files

Tar and GZIP
Use tar to create a single file that can represent many files, This is a TAR archive (Tape Archive) or tarball. The “tape” part of the acronym can be disregarded as legacy
The file is not compressed but may appear smaller than the total sum of all the files as better use is made of the block space on the disk
To compress the file we can use tools such as gzip and bzip2 from within tar.

Main Actions
tar -c to create
tar -t to test or view the archive
tar -x to expand an archive
tar -z to compress or decompress with gzip
tar -j to compress or decompress with bzip2

File Extensions
It tends to be the normal convention to add the following extensions to files:
.tar : plain tar archive
.tgz or .tar.gz : tar archives using gzip compression
.tar.bz2 : tar archives using bzip2 compression

















3.2 Searching and Extracting Data from Files

Topics:
Command line pipes
I/O redirection
Tools for searching data in text files
POSIX Regular Expressions

Command Line Pipes
Using the pipe or vertical bar character | can send to output of one command to the input of another
This is quite common in many OSs
– cat file | more

IO Redirection
> overwrite a file
>> append to a file
2> std-error
set -C or set -o noclobber
>| to overwrite a file

Tools
find
grep / egrep
less
head, tail
sort
cut
wc

Getting to Know Regular Expressions
More features than shell globbing
^ lines begin with
$ lines end with
| or
\b word boundaries
\s white space
\{1,\} repeating characters






3.3 Turning Linux Commands Into Shell Scripts

Topics:
Basic text editing
vi, nano, pico, joe
Basic shell scripting
#!/bin/sh
Variables
Arguments
Loops
echo
exit
BASH Scripting Tutorial































Task : get information on the Linux system version
In this task, you will enter commands to obtain information on your Linux lab system, using commands and the contents of system files.
In the terminal window, enter the command(s) (in red) :
show the name of the system kernel
uname -s
show the version of the kernel
uname -r
show the names of the kernel program files
ls /boot/vmlinuz-*
show the (network) nodename
uname -n
show the hardware platform architecture
uname -i
Command Hint: a useful feature of open source application commands is the ability to use the option --help which shows all of the ways to execute the command; in this case, enter : uname --help
Knowledge Item: There are also a number of text files that contain information about the actual Linux system itself.
list the names of the matching files
ls /etc/*release
Knowledge Item: note that the file /etc/system-release is shown in a blue color; this is called a symbolic link file. This type of file points to another file. The advantage of a symbolic link file is that a "known filename" can be documented for a given purpose, and used on multiple (Linux) systems.
shows the name and version of this system
cat /etc/system-release

Task : get open source licensing information
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.
In the terminal window, enter the command(s) (in red) :
opening up a manual page
man perlgpl
search for the specified string in the man page (q to exit)
then enter: /GEN
Knowledge Item: at this point you will be in the "man" page output, with the string: GNU GENERAL PUBLIC LICENSE at the top of the window. Please do a brief scan of the content on the screen, then hit the f key to continue on to the next screen. While there are thirteen (13) screens of the licensing information, you don't need to read the contents of every screen.
Knowledge Item: GNU = GNU (is) not Unix - this was meant to be a "tongue-in-cheek" way of specifying that the commands and files in Linux do the same things (and more) than their original Unix system counterparts, but are not technically the same.




















Task : get open source and version information from utilities
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.
Knowledge Item: FSF = Free Software Foundation - this organization was founded in 1989 to promote the development and sharing of open source applications and systems.
In the terminal window, enter the command(s) (in red) :
show version and licensing information
perl --version
Hint: you can add the --version option to almost any command on a Linux system to provide version and licensing information.
show version and licensing information
python3 --version
show version and licensing information
grep --version
show version and licensing information
bash --version
Linux supports every major database platform :
Oracle
mySQL
sqlite (native)
MariaDB (native)
Postgres (native)
SQL Server (starting with the 2017 version)







Task : perform user-level tasks on a Linux system
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.
Knowledge Item: the utilities shown in this lab exercise are either included in most standard Linux distributions, or can be easily installed from the Internet.
In the terminal window, enter the command(s) (in red) :
open web browser
firefox --new-window www.google.com 2>/dev/null
Note: after you see the rendering of the Google home page, please close Firefox
install email application
sudo yum -y install thunderbird
Important: sudo will prompt for your user account password, enter: Pa55.w@rd!
As an alternative, you can select the Resources tab (above), and simply left click on Pa55.w@rd!
Knowledge Item: you will cover software packaging in much more detail in Lab 4
launch email client
thunderbird
Knowledge Item: when you first launch thunderbird, a form will appear to setup the email client with : your "real" name, and your email address (so that thunderbird can find your mail server). For best security, use your Gmail account for this lab exercise. A screen shot of the setup form is below :

Knowledge Item: Linux contains a standard utility to read PDF files - evince
PDF file viewer utility
evince /usr/share/doc/valgrind/valgrind_manual.pdf
















Lab 2 : Command Line Basics - Part 1
In this lab, you will use commands on a Linux system to get familiar with syntax / rules of use, and to perform operations on files and directories.
Time to complete Part 1 this lab exercise: 60 minutes.
This lab requires that you first read from the LPI Linux Essentials Study Guide, Chapters 5 and 7.
Understand your lab environment

In this lab, you will be using a Red Hat Enterprise Linux (RHEL 8) system.
Lab Environment Instructions
Connect to your specific LOD RHEL Linux lab environment.
Enter the username and password that were provided for you - NOTE - these credentials will also be listed in the Resources area on the LOD screen; you only need to left click on the username in the larger area. A Password: prompt/box will appear. You only need to left click on the Password show in the Resources area on the LOD screen, or you may enter the password text characters manually.
Left click on the Activities icon

then left click on the Terminal Icon
     to open a command terminal window.
Knowledge Item: the terminal window that you just opened up is actually called a GNOME (GNU Network Object Module Environment) terminal window.
Hint: if you walk away from your session, there is a screen saver that will take control - you will have to enter your account password. The lab environment itself also has an idle timer. If the timer duration is reached, you will see "Save Session" screen. You can simply select "Resume".
Before you enter each command, you may want to lookup the man(ual) documentation for the command, to get an idea of what operations the command can/will do, and what types of output is/are returned. You will look at the methods of obtaining documentation officially in the first part of this lab. For now, the way to see the documentation is simple - just enter : man command (for example, man uname). You can also get an abbreviated view of the documentation by entering : command --help | less
You will also notice that many commands are similar in their syntax, differing only by an option and/or and argument (value). Instead of re-entering the command again, you can hit the up-arrow key to recall the previous command, then modify it as needed. The recall (or history) buffer default size is 1000 previous commands !

































Command Line Components Information
Knowledge Item: before you can start using commands and utilities to manipulate file and directory (contents and attributes), the syntax for entering commands must be understood.

Any text shown in bolded blue italics represents an item that has to be entered/replaced.
the elements of a command line :
shell-prompt command [option(s)] [arg1] [arg2] …. [argn]
shell-prompt defaults to value of \s-\v\$
command enter command exactly as documented
[option(s)] always preceded by a - or -- ; modifies the effect of the command
arg1 … argn filename, string, number, or some other object that the command acts on
Examples

short option
bash-4.4$ cp -i path-to-source-file path-to-destination-file

value option
bash-4.4$ tail -n 2 path-to-file

long option
bash-4.4$ tail --lines=+2 path-to-file


Knowledge Item: you can see the complete list of all three types of options for any command by entering : man command.
Example : man cp
In the terminal window, enter the command(s) (in red) :
make a copy (cp) of an existing file with prompt if target file exists
touch new_file
ls new_file
cp .bashrc new_file
cp -i .bashrc new_file
make a copy of an existing file with prompt if target file exists
clear
cp -i .bashrc new_file
show last two lines of an existing file (sort option)
tail -n 2 .bashrc



























01 Execute commands for various help systems

In this exercise, you will use (Linux) commands to : get help information on commands and files.
Technology overview – you will be using Liinux commands and looking at the contents of documentation pages.
Task : get help information using the man utility
In this task, you will enter commands to obtain manual information on your Linux lab system, using commands and options.
Knowledge Item: the man command (short for manual), does two operations - (1), looks for a file named: topic.section.gz under the /usr/share/man hierarchy; (2) decompresses the file, evaluates the markup tags in the file (bolding, paragraphs, indentation, etc), then outputs the rendered text in a paginated fashion.
In the terminal window, enter the command(s) (in red) :
help on uname command and its options
uname -s
hierarchies where man looks for the files / pages (q to exit)
man man
directories where man looks for the files / pages
manpath
ls -d /usr/share/man/man*/
documentation for cp command (q to exit)
man cp
embedded help in the cp executable file
cp --help | less
shows the hardware platform architecture
uname -i
Knowledge Item: there is separate database that contains a one line synopsis of every topic that has a manual page - this database can be created or updated via the mandb command. Note that this operation must be done in the root account (more on this later). The database can be searched by adding the -k option to the man command.
build the "whatis" database of information
sudo mandb -q
all entries that contain the string **file (q to exit)
man -k file | less
Knowledge Item: to exit from the paginated output, hit the letter: q at the : prompt
search for entries in a specific section (q to exit)
man -k file | grep "(1)" | less























Task : access your home directory and special system directories
In this task, you will enter commands to obtain information and access specified directories, using commands and options.
Knowledge Item: a directory in Linux is just a file where each line contains two entries - a file identification number and a file name. The file-id number is used to locate all of the data needed to be able to access the file (contents). You can see these two items by using the option -i on the ls command. Enter : ls -i
In the terminal window, enter the command(s) (in red) :
show the current default directory (path)
pwd
create a subdirectory
mkdir subdir
show what subdir is
file subdir
show full attributes of subdir
stat subdir
show attributes of subdir on one line
ls -ld subdir
change current default directory (path
cd subdir
show the (new) current default directory (path)
pwd
Knowledge Item: the "home" directory is the path that is tied to a user account, and is the default at login. It can be referenced by using the environment variable HOME, and is the default path for the cd command.
change the default directory to HOME
cd
show paths of special directories
man 7 hier
show attributes of special directories
ls -ld /etc /usr/bin /usr/sbin /var





































Task : get file and directory information
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.
Knowledge Item: the ls and dir commands do exactly the same operations, and return the same file information. The difference is that ls returns color coded output (by default), while dir does not return color coded output.
In the terminal window, enter the command(s) (in red) :
change the default directory to HOME
cd
show major attributes on one line
ls -l .bashrc
Hint: You will also notice that many commands in the next sequence are similar in their syntax, differing only by an option and/or and argument (value). Instead of re-entering the command again, you can hit the up-arrow key to recall the previous command, then modify it as needed.
show files from newest to oldest (age) (q to exit)
ls -lta | tail --lines=+2 | more
show the newest file
dir -lta | tail --lines=+2 | head -1
show files from oldest to newest (age) (q to exit)
ls -ltra | tail --lines=+2 | more
show the oldest file
dir -ltra | tail --lines=+2 | head -1
show files from largest to smallest (size) (q to exit)
ls -lSa | tail --lines=+2 | more
show the largest file
dir -lSa | tail --lines=+2 | head -1
show files from smallest to largest (size) (q to exit)
ls -lSra | tail --lines=+2 | more
show the smallest file (q to exit)
dir -lSra | tail --lines=+2 | head -1
Knowledge Item: the default ls color coding : blue for a directory, cyan for a symbolic link, red for an archive, for an executable.



































Task : use the cp command and options
In this task, you will enter commands to make copies of files and directory hierarchies.
Knowledge Item: the ls and dir commands do exactly the same operations, and return the same file information. The difference is that ls returns color coded output (by default), while dir does not return color coded output.
In the terminal window, enter the command(s) (in red) :
summary of options (q to exit)
cp --help | less
documentation for cp command (q to exit)
man cp
basic copy operation
cp .bashrc new-file
copy with output messages
cp -v .bashrc new-file
copy with overwrite check
cp -i .bashrc new-file
create directory hierarchy
mkdir -p subdir1/subdir2/subdir3
ls -laR subdir1
Knowledge Item: the sudo command allows you to run any command in the administrator account (root), but you must enter your user account password to validate the usage.
install tree program
sudo yum -y install tree
Knowledge Item: the user password that is entered is masked so that you do not see the actual characters.
Knowledge Item: the tree program draws a representation of a directory hierarchy.
draw directory hierarchy
tree subdir1
copy directory hierarchy
cp -r subdir1 subdir4
draw directory hierarchies
tree subdir1 subdir4
Knowledge Item: in Lab 2 section 05 you will rename and remove files and directories.






























Task : use the mv, rm, and rmdir commands and options
In this task, you will enter commands to rename and delete files and directory hierarchies.
In the terminal window, enter the command(s) (in red) :
summary of options (q to exit)
mv --help | less
Knowledge Item: to exit from the paginated output, hit the letter: q at the : prompt
rename the file new-file to newer-file
mv new-file newer-file
show files - note the error message !
ls new-file newer-file
move (not copy) the file newer-file into a subdirectory
mv newer-file subdir1
Knowledge Item: moving a file to another directory only moves the inode number and file name into the target directory - the file's data does not get relocated
show changes - note the error message !
ls newer-file ; ls subdir1
Knowledge Item: you can do multiple commands on one line by separating them with a semi-colon ( ; ) - it is called a command separator.
delete file with prompt
rm -iv subdir1/newer-file
fails : directory is not empty
rmdir subdir1
ls -la subdir1
fails : not correct method
rm subdir1
remove hierarchy recursively
rm -rf subdir1
Knowledge Item: the -f option to rm says to force the deletion(s) whether the files and directory exist (or not).

NOTE: the rm -rf is the most dangerous and destructive command on the entire Linux system. Once executed, there is no way to reverse the damage, other than to restore from backups. A good suggestion would be to add the -i option, so that you would be prompted (and verify the path is correct first)






























Task : use the chmod, chown, chgrp, setfacl commands and options
In this task, you will enter commands to change file security and ownership attributes.
In the terminal window, enter the command(s) (in red) :
make copy of existing file
cp .bashrc new-file
permissions and ownership
stat new-file | grep "^Access: ("
Knowledge Item: the grep command searches for text, sometimes using characters called "regular expressions". You will work with these two important parts of Linux in Lab 3. For now, note the base eight (octal) codes and the symbolic r(ead) and w(rite) strings.
change permissions
ls -l new-file
chmod 755 new-file
ls -l new-file
change permissions
chmod u=rwx,go=rx new-file
ls -l new-file
change file ownership
sudo chown root new-file
ls -l new-file
change group ownership
sudo chgrp root new-file
ls -l new-file
Knowledge Item: note that only the root account can change file (group) ownership.
show change in ownerships
stat new-file | grep "^Access: ("
allow write access by user60
sudo setfacl -m u:$USER:rw- new-file
show file (modified) ACL
getfacl new-file
Knowledge Item: the ACL (access control list) for a file (or directory) contains both standard and special access permissions. More on ACLs in Lab 5.































Task : use the bash executable built-in commands
In this task, you will enter commands to change file security and ownership attributes.
In the terminal window, enter the command(s) (in red) :
built-ins manual page (q to exit)
man bash   then enter : 3686
Knowledge Item: a shell built-in is part of the BASH executable; it is not a separate program.
change default directory
cd subdir4
show default directory
pwd
show file types
type cd /usr/bin/date ls
show aliases
alias ls
Knowledge Item: an alias adds additional options or arguments to a command.
note no file colorization in the output
dir
define a command alias
alias dir="dir --color"
added file colorization (only for this session)
dir
add alias definition to .bashrc file
cd
echo 'alias dir="dir --color" ' >> .bashrc
tail -1 .bashrc
Knowledge Item: the >> operator appends text to the bottom of a file - you will see redirection operators in Lab 3 section 05.
re-execute shell initialization script
source .bashrc
run a command in the background
sleep --help | head -7
sleep 500 &
Knowledge Item: the & says to run the command in parallel to the shell program, called a "child process".
background process information
jobs --help
jobs
give control to background process
fg --help
fg %1
suspend process, return to the shell
control+Z
Hint: control+Z means to hold down the CTRL key while hitting the Z key.
background process shows as Stopped
jobs
allow background process to run
bg --help
bg %1
terminate background process
kill --help
kill %1
Knowledge Item: the kill command accepts either a job number (preceded by the %) or a process identification (PID) number.
note the pagination prompt (q to exit)
more --help
ps --help a | egrep -- "-e|-f "
ps -ef | more
Knowledge Item: : the ps command with the -ef options shows all of the processes that are currently on the system - piping to more paginates the output.
change the pagination prompt
export MORE=-cd
note change in the pagination prompt (q to exit)
ps -ef | more
Knowledge Item: bash maintains a history buffer of the last 1000 entered commands, and the buffer is saved to $HOME/.bash_history at logout, then reloaded at the next login.
show the entire history buffer (q to exit)
history | less
show the last 10 commands only
history --help | head -5
history 10
Knowledge Item: you can use the up- and down- arrow keys to recall commands from the history buffer. You can use standard keys (right- and left- arrows), DEL and BS keys to modify the recalled command. The Enter key will then re-execute the command.




Task : create, list, and extract from archives using the tar utility
In this task, you will use the tar command and options
Knowledge Item: the tar command creates a (tape) archive file, although most tar archives are stored as disk files. A tar archive is made up of twenty (20) 512-byte fixed-length records - a tar block. A tar archive is a collection of one (or more) of the 10240 byte blocks. A tar archive can only be created, listed, and extracted from using the tar command.
In the terminal window, enter the command(s) (in red) :
help on the tar command and its options (q to exit)
tar --help | less
Hint: when creating a tar archive, a best practice is to specify the files and/or directories being archive as a relative path (to where ever the default directory is at that time). There are two ways to do this : (1) cd to the directory that is one level above the directory hierarchy being archived or (2) use the -C option on the tar command line.
to archive a top level directory
cd /
pwd
create tar archive
tar -cvf $HOME/userfind.tar ./userfind
**Knowledge Item: ./userfind is relative to the current default directory path of / .
back to HOME directory
cd
pwd
create (same) tar archive
tar -C / -cvf $HOME/userfind.tar ./userfind
show archive file type contents
file userfind.tar
show archive file attributes
stat userfind.tar
list contents tar archive
tar -tvf userfind.tar
extract entire tar archive to the current default directory
tar -xvf userfind.tar
show created files and directories
ls -R ./userfind
extract entire tar archive to a specific directory
tar -C /tmp -xvf userfind.tar
show created files and directories
ls -R /tmp/userfind
Hint: when extracting (or restoring) files from a tar archive, the default is to restore all files to the current default directory path. You can also specify a (list of) file(s) and/or directory paths to restore, but they key is to specify the files as they were archived, meaning the exact path captured in the archive. Any directories in the path will be created if they do not already exist.
extract specific file - fails, incorrect path
tar -xvf userfind.tar name
get specific archived file path to restore
tar -tvf userfind.tar | grep name
extract specific file - works with archived path
tar -xvf userfind.tar ./userfind/name







Task : use regular expressions with grep and sed
In this task, you will enter commands to use regular expressions.
Knowledge Item: regular expressions are supported by many standard Linux utilities besides grep and sed, such as vim. There are some similarities between regular expression characters and BASH shell wildcard characters. However, they are used in totally different situations.
In the terminal window, enter the command(s) (in red) :
get a copy of a text file
cp /userfind/name .
show file contents (note the empty lines !)
cat name
help on regular expressions (5 screens)
man grep then enter : /REG
all lines that start with specified string (greedy match)
grep "^string" name
Knowledge Item: grep matches as much as possible based on the regex and the text (a greedy match).
all lines that start with string (non-greedy)
grep --help | grep -- -w,
grep -w "^string" name
all lines that start with exactly 4 characters
grep "^….string" name
find all "empty" lines
grep "^\s*$" name
Knowledge Item: an empty line contains either no spaces (or tabs), or one (or more) spaces or tabs.
find all "non-empty" lines
grep --help | grep -- -v,
grep -v "^\s*$" name
Knowledge Item: -v tells grep to find all non-matching lines.







































Task : get file and directory names from standard utilities
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.
Knowledge Item: the ls command actually does not search the specified directories contents. It returns files by (1) simple name match, or (2) by attribute match, or (3) file names returned by the BASH shell when wildcard characters are used - the shell wildcard characters are : * (splat) ? (hook) [ ] (list)
In the terminal window, enter the command(s) (in red) :
show all non-dot files
ls *
fails - ls cannot process shell wildcard characters
ls '*'
shell returns matching files / directories
ls .b*
ls shows contents of returned directories
ls /course/*
ls shows returned directory name only
ls -d /course/*/
shell returns matching files / directories
ls /course/?????
shell returns matching directories
ls -d /course/mngmnt/????*/
shell returns matching directories
ls -d /course/mngmnt/[a-d]*/
shell returns non-matching directories
ls -d /course/mngmnt/[!a-d]*/
Knowledge Item: the find command supports shell when wildcard characters are used - the shell wildcard characters are : * (splat) ? (hook) [ ] (list)
help on find command and its options
find --help | less
default is to list out entire hierarchy
find /course
locate all file names that start with "d"
find /course -name "d*"
locate all directory names that start with "d"
find /course -name "d*" -type d
Knowledge Item: find command permissions can be specified in either absolute or symbolic format.
locate all files with specified absolute permissions
find /course -perm 755
locate all files with specified symbolic permissions
find /course -perm "u=rwx,go=rx"

















Task : use the grep and sed commands and options
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.
In the terminal window, enter the command(s) (in red ) :
get a fresh copy of the text file
cp /userfind/name .
count of all lines that contain string
grep -c "string" name
case insensitive search
grep -i "StRiNG" name
line numbers that contain string
grep -n "string" name
file names (skipping directories) that contain string
grep -l -d skip "string" *
delete all lines that start with string
sed "/^string/d" name
substitute first occurrence of string with STRING
sed "s/string/STRING/1" name
substitute all occurrences of string with STRING
sed "s/string/STRING/g" name
file was not changed
cat name
Knowledge Item: sed only changes the output by default. To actually change (a) file(s), the inline -i editing option must be added.
*substitutions are actually made in the file
sed -i "s/string/STRING/g" name
file was changed
cat name









































Task : use redirection operators
In this task, you will enter commands to manipulate standard output and standard error.
In the terminal window, enter the command(s) (in red ) :
redirections manual pages (q to exit)
man bash   then enter :   /REDIRECTION
no output in terminal window
date 1> output-file
Knowledge Item: 1> is the same as > and is referred to as standard output.
contains command output
cat output-file
no output in terminal window
who 1>> output-file
Knowledge Item: 1>> is the same as >> and appends to standard output.
contains command output
cat output-file
error - no such command
think
send error text to a file
think 2> error-file
Knowledge Item: 2> is referred to as standard error.
contains error output
cat error-file
discard error text
think 2> /dev/null
Knowledge Item: /dev/null is a valid destination for standard output or error data.










































Task : use special redirection operators and the tee command
In this task, you will enter commands to manipulate standard output and standard error.
In the terminal window, enter the command(s) (in red ) :
get a copy of a shell script
cp /userfind/output_error.sh .
contents of shell script
cat output_error.sh
execute shell script
./output_error.sh
Knowledge Item: the shell script output_error.sh sends text to both standard output and to standard error, which by default, is your terminal window. You will do much more with shell scripting (techniques) in Part 3 of this Lab (sections 10, 11, 12).
stdout and stderr sent to same file
./output_error.sh &> out_err.txt
Knowledge Item: &> is the same as 2>&1 (after the destination for standard output has been specified).
stdout and stderr sent to same file
./output_error.sh > out_err.txt 2>&1
contents of text file
cat out_err.txt
tee command documentation
info coreutils 'tee invocation'
output sent to two destinations
who | tee output.txt
Knowledge Item: tee sends output to the specified file(s) and to standard output.
contents of text file
cat output.txt






































Task : use special redirection operators and pipes
In this task, you will enter commands to manipulate standard input.
In the terminal window, enter the command(s) (in red) :
redirections manual pages (q to exit)
man bash   then enter : /REDIRECTION
get a fresh copy of the text file
cp /userfind/name .
send email with file as text body
mailx user60 0< name
Knowledge Item: 0< is the same as < and is referred to as standard input
email data is the text file contents
mailx   at & prompt enter : 1
Knowledge Item: exit mailx by entering x at the & prompt
get a copy of a shell script
cp /userfind/embed_input.sh .
contents of shell script
cat embed_input.sh
execute shell script
./embed_input.sh
Knowledge Item: << says that the input to the command immediately follows, and is specified by two matching strings. This is sometimes called a "here document"
email body is the text file contents
mailx   at & prompt enter : 2
Knowledge Item: exit mailx by entering x at the & prompt

pipelines manual page (1 screen) (q to exit)
man bash   then enter : /Pipelines
no paginated output
ps -ef
paginated output
ps -ef | less
Knowledge Item: | is a normal command line delimiter - no spaces are needed before and/or after the | (but are useful for readability).
output from pipeline into a file
ps -ef | grep sssd > output2.txt
contents of pipeline output file
cat output2.txt
find largest file
ls -l | tail -n +2 | sort -k5nr,5 | head -1
Knowledge Item: multiple pipes can be used to process output from commands. This example : (1) takes the output from ls and removes the first line (of output), then (2) does a reverse (descending) sort on the fifth field (size of the file), then (3) extracts and displays the top line (only), which will be largest file in the current default directory. We will use this example in Part 3 of Lab 3 in a shell script.
find smallest file
ls -l | tail -n +2 | sort -k5n,5 | head -1
Knowledge Item: this example : (1) takes the output from ls from and removes the first line (of output), then (2) does a default (ascending) sort on the fifth field (size of the file), then (3) extracts and displays the top line (only), which will be smallest file in the current default directory. We will use this example in Part 3 of Lab 3 in a shell script.




Task : use compression and decompression commandss
In this task, you will enter commands to manipulate file data compression.
In the terminal window, enter the command(s) (in red ) :
create tar archive
cd
tar -C / -cvf $HOME/userfind.tar ./userfind
size of .tar file (in bytes)
stat -c %s userfind.tar
compress .tar file
gzip userfind.tar
Knowledge Item: gzip creates a compressed file with the last two letters of the file name are .gz .
attributes of compressed .tar file (only)
gunzip -l userfind.tar .gz
*decompress .tar file
gunzip userfind.tar.gz
Knowledge Item: gunzip creates a decompressed file, removing the .gz suffix.
size of (decompressed) .tar file (in bytes)
stat -c %s userfind.tar
create tar archive and compress it
tar -z -C / -cvf $HOME/userfind.tar.gz ./userfind
Knowledge Item: tar (with the -z option) can create and compress a .tar file (but does not automatically add the .gz suffix).
create zip archive
(cd / ; zip -r $HOME/userfind.zip ./userfind)
Knowledge Item: zip creates and compresses data into a .zip file. The enclosing ( ) (called command grouping) force the shell to run the two commands in one separate process. After the zip command runs, the default directory path has not changed.
show attributes of zip archive
unzip -v userfind.zip




































Task : use the vim and nano text editors
In this task, you will enter editor commands to create or modify text files.
In the terminal window, enter the command(s) (in red) :
vim manual page (q to exit)
man vim
Knowledge Item: vim stands for vi improved - newer form of the very old visual editor.
get a copy of a text file
cp /userfind/line.txt .
edit existing text file
vim line.txt
Knowledge Item: on most Linux systems, vi is setup as a command alias for vim. Enter: alias vi
Primary steps to use the vi / vim editor :
1) enter the vim command and specify the file name to create or to modify
2) position the cursor (using arrow keys) at the desired start of new text entry or modification
3) hit the letter i into insert mode - all major editing keys function (DEL, BS, arrows, etc)
4) enter new text, remove/modify existing text
5) position cursor to the desired start for new text entry or modifications
6) repeat steps 4) and 5) as many times as needed
7) when all editing is complete, hit the ESC key
8) to save all changes, enter: :wq ; to quit and not save anything, enter: :q!




nano manual page (q to exit)
man nano
Knowledge Item: the name nano comes from the metric prefix. nano is primarily a control key based editor.
get a copy of a text file
cp /userfind/line.txt .
edit existing text file
nano line.txt
Primary steps to use the nano editor :
1) enter the nano command and specify the file name to create or to modify
2) position the cursor (using arrow keys) at the desired start of new text entry or modification
3) all major editing keys function (DEL, BS, arrows, etc)
4) enter new text, remove/modify existing text
5) position cursor to the desired start for new text entry or modifications
6) repeat steps 4) and 5) as many times as needed
7) when all editing is complete, hit the control+x key sequence
8) to save all changes, enter: y (and verify file name); to quit and not save anything, enter: n













Task : properly structure, execute, and debug BASH shell scripts
In this task, you will enter commands to manipulate shell scripts.
In the terminal window, enter the command(s) (in red ) :
get a copy of a shell script file
cp /scripting/samples/sample1.bash .
show the signature/shebang line
head -1 sample1.bash
Knowledge Item: the first line of a shell script starts with what is called the shebang #! (or signature), and is made to look like a comment. The shebang tells the Linux kernel to run the path that immediately follows in a separate child process. The rest of the (shell script) file becomes the command input to that (child or sub-) shell.
permissions and ownership
stat sample1.bash | grep "^Access: {"
Knowledge Item: a shell script must be executable in order to run it as a standalone program.
*show shell script contents
cat sample1.bash
execute shell script
./sample1.bash
Knowledge Item: technically, you do not debug a shell script (execution). Instead, you can request that the shell traces the execution. The trace output : (1) will be removed of the shebang, comment and empty lines; (2) shows each actual line being executed and is preceded with an + character, and (3) all output and/or error messages will appear immediately after the line that generates them.
...less
documentation for shell scripting tracing/debugging
bash -c 'help set' | grep -- "^.*-x   P"
trace the execution of the shell script
bash -x sample1.bash









































Task : use variables in shell scripts
In this task, you will see how variables are used in shell scripts.
Knowledge Item: most techniques in a shell script can be tried out at the command line. This allows for testing and debugging before ever going into a text editor to create and/or modify a(n existing) script.
In the terminal window, enter the command(s) (in red ) :
string data type variable
string_var="Linux Foundations"
Knowledge Item: variable scope (access) in shell script defaults to, and is usually desired to be local(to the script only). Defining variables to be exported (global access scope) is usually done in the .bashrc (or specific) shell script.
variable scope is local (by default) - notice that there is no output
env | grep string_var
change variable scope to global
export string_var
Knowledge Item: variable substitution is done by placing a $ in front of the variable name.
request variable substitution
echo $string_var

Knowledge Item: all variable values are stored and treated as character data ( by default). The typeset -i command tells the shell to store the variable value as a binary integer. BASH only supports binary integer variables and operations.
binary numeric variable
typeset -i int_var=56
Knowledge Item: variable substitution is done by placing a $ in front of the variable name.
request variable substitution
echo $int_var
Knowledge Item: numeric operations are requested by ((   )) around the operation.
binary variable operations (and forcing the substitution of the numeric operation)
echo $((int_var = int_var + 1))
shell script with variables and loops
cp /scripting/samples/sample2.bash .
show shell script contents
cat sample2.bash
execute shell script
./sample2.bash
find largest file - from Lab 3 section 07
ls -l | tail -n +2 | sort -k5nr,5 | head -1
Knowledge Item: the commands sequence to find the largest file only works for the current default directory. It would be very useful to be able to supply one (or more) argument(s) to a shell script, and then be able to use the values in commands. To pass value(s) from the command into a shell script, there are special positional variables. The first argument to the shell script can be accessed via $1 , the second argument via $2, and so on.
...less
shell script that shows the use of command line arguments
cp /scripting/samples/sample4.bash .
show shell script contents
cat sample4.bash
execute shell script (with argument)
./sample4.bash /etc
./sample4.bash /var
./sample4.bash
Note: in the preceding commands, /etc was available in the shell script as $1 , /var was available in the shell script as $1 , and in the third command, $1 had a value of an empty string.







































Task : use for, while, until , if and case statements in shell scripts
In this task, you will use special shell scripting constructs.
In the terminal window, enter the command(s) (in red ) :
help on statements (7 screens) (q to exit)
man bash   then enter : /Compound Commands
loop over (space delimited) list
for x in 1 2 3 4 5 ; do echo $x ; done
Knowledge Item: x is called a loop iterator, and it is assigned the next value in the list. When there are no more values in the list, the loop is finished.
loop over variable value
x=5 ; while ((x)) ; do echo $((x--)) ; done
loop over variable value
x=5 ; until ((x == 0 )) ; do echo $((x--)) ; done
Knowledge Item: while tests for a true condition (non-empty string or non-zero numeric value or a true test); until tests for a false condition (empty string or zero numeric value or a false test).
Knowledge Item: if has four forms: simple, complex, block, and single line.
test variable value
typeset -i x=5 ; if (( x == 5 )) ; then echo "x is 5" ; fi
typeset -i x=6 ; if (( x == 5 )) ; then echo "x is 5" ; else echo "x is not 5";fi
Knowledge Item: a case block takes one value and successively compares it to a list of "selector patterns". Upon the first match, the statement(s) that are tied with the selector pattern are then executed.
case variable-name in
   test-on-variable )
   command(s)-to-execute ;;


   test-on-variable )
   command(s)-to-execute ;;
   .
   as many selectors as needed
   .
esac
shell script that contains loops and conditionals
cp /scripting/samples/sample3.bash .
show shell script contents
cat sample3.bash
execute shell script
./sample3.bash























Task : access special status variables and error handlers
In this task, you will use special shell scripting constructs
Knowledge Item: all commands return a completion status. A value of 0 indicates success; any other value indicates warning or failure. The completion status is available in the special variable $?.
In the terminal window, enter the command(s) (in red ) :
command that "works"
date
show completion status
echo $?
try to execute non-existent command
think
show completion status
echo $?
Knowledge Item: in a shell script, the value of $? is (usually) captured into a variable and then checked with an if statement.
Knowledge Item: trap defines a signal handler, which can include: errors, interrupts, and shell script exit.
define error handler
trap 'echo "error occurred" ' ERR
generate error - note resultant outputs
think
clear error handler
trap -- ERR
shell script that contains error handlers and tests
cp /scripting/samples/sample5.bash .
show shell script contents
cat sample5.bash
execute shell script
./sample5.bash







































Task : get version and device information
In this task, you will enter commands and options to obtain system information.
In the terminal window, enter the command(s) (in red) :
list out release file names
ls /etc/*release
show Linux variant release file contents
cat /etc/redhat-release
documentation on the uname command (q to exit)
info coreutils 'uname invocation'
show Linux kernel version
uname -v
show Linux kernel release date
uname -r
Knowledge Item: uname actually means unix name !
naming conventions - kernel file name
ls /boot/vmlinuz*
naming conventions - storage devices
lsblk /dev/sda
naming conventions - storage devices
lsblk /dev/sr0








Task : understand the benefits of software configuration tools
In this task, you will use a specific Linux web-based configuration management tool.
Knowledge Item: many software configuration management tools have both a command line and a graphical interface. Some also have a web-based interface. Generally, these tools need to be run in a root identity. You will see many of these tools in Sections 3 - 6 of this Lab exercise.
In the terminal window, enter the command(s) (in red) :
start web-based UI service
sudo systemctl start cockpit
web-based UI service information
sudo lsof -i:9090
in the graphical desktop, left-click on :

and then left-click on :

to start up cockpit configuration tool
enter in Firefox locator box : https://localhost:9090
Knowledge Item: You will have to "Understand and accept the risks" of cockpit the first time. You will then login with the same username/password combination that you use to login to the Linux system.
in cockpit, from the left side menu (tabs), select and view information from :


System
Storage
Networking
Accounts


to exit cockpit, select

and then select : Log out



































Task : compare command line and graphical tools
In this task, you will enter commands and options to obtain system information.
Knowledge Item: you are going to compare using disk partitioning tools, parted and gparted. Note that gparted will need to be installed - it is not part of a standard RHEL installation. You will see more details on software package installation in Lab 4 Part 12.
In the terminal window, enter the command(s) (in red) :
show disk names
lsblk | grep disk
command line disk partitioning
sudo parted /dev/sda
show partition table
at the (parted) prompt, enter : print
at the (parted) prompt, enter : quit
Note: the graphical version of parted, named gparted, is not part of a standard RHEL 8 installation, but it can be installed from the EPEL repository (extra packages for enterprise Linux)..
install package repository descriptor
sudo yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
note epel/x86_64 in the listing
yum repolist
install software package
sudo yum -y install gparted
run graphical disk partitioning tool (sample output)
gparted

double left click on any partition area shown to get more information




when finished, left click on GParted tab -- select : quit

















Task : get hardware device information
In this task, you will enter commands to list hardware devices (and attributes).
In the terminal window, enter the command(s) (in red) :
hardware listing short summary
lshw -businfo
show configured CPU IDs
grep proc /proc/cpuinfo
show CPUs that are enabled
lscpu -p=cpu,online | grep -v "^#"
disable second CPU
sudo chcpu -d 1
show CPUs that are enabled
lscpu -p=cpu,online | grep -v "^#"
enable second CPU
sudo chcpu -e 1
show disks and partition information
lsblk -o name,size,type
show all mounted filesystem information
df -h -T -t xfs -t ext4 -t ext2
show USB device(s)
lsusb







Task : use the lsblk, pvs, vgs, and lvs commands and the file /proc/partitions
IIn this task, you will enter commands to view storage area descriptions.
In the terminal window, enter the command(s) (in red) :
show disk storage information
lsblk -o name,size,type,mountpoint,fstype
show all mounted filesystem information
df -h -T -t xfs -t ext4 -t ext2
show kernel view of storage areas
cat /proc/partitions
Knowledge Item: LVM (logical volume management) allows you take combine multiple storage areas of disk storage, create logical volumes from the combined space, and dynamically increase the size of a mouned file system in a logical volume
show physical volume(s)
sudo pvs
show volume group(s)
sudo vgs
show logical volume(s)
sudo lvs











Task : use the commands lsblk, fdisk, and parted commands and options
In this task, you will use disk partitioning tools.
In the terminal window, enter the command(s) (in red) :
list storage devices only
lsblk | grep disk
Knowledge Item: all partitioning tools must be run as root (via sudo).
command line disk partitioning tool
sudo fdisk /dev/sda
show disk geometry and partition table
at the Command : prompt, enter : print
at the Command : prompt, enter : quit
command line disk partitioning tool
sudo parted /dev/sda
show disk geometry and partition table
at the (parted) prompt, enter : print
at the (parted) prompt, enter : quit
show partition table
sudo partx -l /dev/sda
show partition table
sudo kpartx -l /dev/sda
show partition table
sudo cfdisk /dev/sda
hit enter to select: Quit
show disks and total sizes
sudo sfdisk -s
show disk geometry and partition table
sudo sfdisk -l /dev/sda







































Task : use commands to get attributes of executable files and for running programs/processes
In this task, you will enter commands to view executable file and process information.
In the terminal window, enter the command(s) (in red) :
show file is an executable
file /usr/bin/date
show file is an executable
readelf -h /usr/bin/date | grep Type:
show shared libs needed at run
readelf -d /usr/bin/date | grep NEEDED
show shared libs program was linked with
ldd /usr/bin/date
run program in parallel
sleep 800 &
Knowledge Item: the & character says to run the command/program in the background.
show process in the background
ps -fp $!
Knowledge Item: the $! variable contains the PID of the last program run in the background
show files opened by process
sudo lsof -p $! | less
virtual address space of process
pmap -x $! | less
stop background process
kill $!
Task : use the free, slabtop, top and sar commands
In this task, you will enter commands to view system resource areas
In the terminal window, enter the command(s) (in red) :
static view of memory related areas
free -mth
Knowledge Item: the watch command will take the output from any static command and make it dynamic. To exit watch, you hit control+c .
a simple monitor (control+c to exit)
watch -n5 'free -mth;echo;uptime;echo;ifstat'
dynamic view (q to exit)
top
show memory allocations (q to exit)
sudo slabtop
show only processes using memory(control+c to exit)
pidstat -r 10
show only processes using CPU(control+c to exit)
pidstat -u 10
show only processes with active disk I/O (control+c to exit)
pidstat -d 10
show CPU usage averages
sar -u







Task : access /var/messages, /etc/rsyslog.conf, dmesg and journalctl commands (options and arguments)
In this task, you will enter commands to look at system (event) logs.
In the terminal window, enter the command(s) (in red) :
Knowledge Item: kernel message and system event logging are written to separate locations: (1) kernel specific messages are written to /dev/kmsg, which can be read by the dmesg program and (2) /;dev/log is read by two daemons : systemd-journald and rsyslogd. Reports are generated by journalctl and reading files in the /var/log directory.
basic hardware inventory (q to exit)
dmesg | less
basic hardware inventory
dmesg | egrep "Brought|RAM covered|sda:|NIC"
basic hardware inventory
journalctl | egrep "Brought|RAM covered|sda:|NIC"
specific user events (q to exit)
journalctl _UID=$UID
specific user events verbosely (q to exit)
journalctl -o verbose_UID=$UID
Knowledge Item: the UID variable is defined at BASH login by the procedure /etc/profile.
target syslog files
grep -A29 "# RULES #" /etc/rsyslog.conf
main event logging files
ls /var/log/messages*
all daemon-related messages
sudo grep "[.*]: " /var/log/messages
Knowledge Item: logging files in /var/log are rotated based on system boot and size.
all su and sudo failures
sudo grep "authentication failure" /var/log/secure






































Task : get information for the : /var, /etc, /usr[/bin /sbin], /sbin, /opt system directories
In this task, you will look at the use and purpose of selected system directories.
Knowledge Item: you will be looking at the man page for the Linux F(ile) H(ierarchy) S(ystem) information for selected directory hierarchies .
In the terminal window, enter the command(s) (in red) :
for /var
man 7 hier    then enter : 357
look at all entries related to /var
                      then enter: q    
for /etc
man 7 hier    then enter : /etc
look at all entries related to /etc
                      then enter: q    
for /usr
man 7 hier    then enter : 113
look at all entries related to /usr
                      then enter: q    
for /sbin
man 7 hier    then enter : 100
look at all entries related to /sbin
                      then enter: q    
for /opt
man 7 hier    then enter : 89
look at all entries related to /opt
                      then enter: q    
Task : use the hostname and ip commands, /etc/resolv.conf and nsswitch.conf files
In this task, you will enter commands to view networking information.
Knowledge Item: a Linux system network identity is defined by the combination of the contents of files and results of utilities that startup mechanisms to allow both outbound and inbound activities with other systems (and even the Internet).
In the terminal window, enter the command(s) (in red) :
show hostname
hostname
storage of hostname
cat /etc/hostname
show IPv4 information
ip address show
show IPv4 information
nmcli con show
show NIC information
ip link show
show NIC information (q to exit)
nmcli dev show
Knowledge Item: name server and router information (to get to other networks) is controlled by the contents of files and running daemon services.
show routing tables
netstat -rn
show routing tables
route
show routing tables
ip route
Task : install, list (information), and remove Red Hat and Debian family software packages
In this task, you will enter commands to manipulate software packages.
Knowledge Item: The Red Hat and Debian families of Linux systems use different tools to install, list, and remove software package.
Note: since you are doing the lab exercises on a Red Hat family Linux system, you will not be able to execute the commands labeled as "Debian" (but the concepts are the same). You would need access to a Debian family Linux system to execute these commands .
In the terminal window, enter the command(s) (in red) :
see if package is installed (RHEL)
rpm -q systemd
see if package is installed (Debian)
dpkg -s systemd
list package contents (RHEL) (q to exit)
rpm -ql systemd | less
list package contents (Debian)
dpkg -c systemd
Knowledge Item: installing or removing a package requires a root identity (via sudo ), and an accessible package repository.
install package (RHEL)
sudo yum -y install ruby
install package (Debian
sudo apt-get install ruby
remove package (RHEL)
sudo yum -y remove ruby
remove package (Debian)
sudo apt-get remove ruby









































Task : Examine user information in the files: /etc/passwd, /etc/shadow, /etc/group, and /etc/gshadow, and via the commands: id and groups
In this task, you will enter commands and options to obtain information on your Linux lab system.
Knowledge Item: authorized user information is spread across a number of different files. All system type data files also have a mannual page in section 5.
In the terminal window, enter the command(s) (in red) :
man** pages for system files
man 5 passwd shadow group gshadow
locate specific record in passwd file
grep "^root" /etc/passwd
locate specific record in shadow file
sudo grep "^root" /etc/shadow
note that the /etc/shadow file can only be assessed as root (via sudo).
groups to which root belongs
sudo groups
locate specific record (for root groups)
grep "^root" /etc/group
locate specific record (for root groups)
sudo grep "^root" /etc/gshadow
note that the /etc/gshadow file can only be assessed as root (via sudo).
show UID, GID(s) and SELinux context
id
UID, GID(s), SELinux context for root
sudo id
Task : use the who, w, finger, whoami and top commands
In this task, you will enter commands to obtain information for logged in user processes
In the terminal window, enter the command(s) (in red) :
current username (only)
whoami
current username, UID, GID, and group(s)
id
list of logged in users
who
current user information from who
who am i
a more verbose who
w
install finger utility
sudo yum -y install /home/files/finger-0.17-52.el7.x86_64.rpm
parts from who and w with user information
finger
Knowledge Item: you can change the personal information field (Name) in the finger command output by using the command: chfn . You will have to enter your password to change the personal information field.
change personal information field
chfn -f "put-your-real-name-here"
Knowledge item: the personal information field is stored in the /etc/passwd file (seen in the previous lab section).
note the difference in the Name field
finger
dynamic display of specific user processes
top -u $USER
Task : use the useradd and groupadd commands (and options)
In this task, you will enter commands to obtain information for logged in user processes
In the terminal window, enter the command(s) (in red) :
useradd command options (q to exit)
useradd --help | less
create user with defaults
sudo useradd newuser
Knowledge Item: useradd gets defaults for the new user account attributes from the files /etc/default/useradd and /etc/login.defs. By default, a new group using the new user account name is also created.
show new user record
grep newuser /etc/passwd
show new group record
grep newuser /etc/group
show new user home directory attributes
ls -ld /home/newuser
no password for new user account (second field)
sudo grep newuser /etc/shadow
set password for user account (remember the password value !)
sudo passwd newuser
show hashed password for new user account
sudo grep newuser /etc/shadow
try logging into the new user account
ssh newuser@localhost
Knowledge item: to logout of the ssh session, enter the exit command.
create new group
sudo groupadd newgroup
verify group creation
grep newgroup /etc/group
put user into the new group
sudo usermod -aG newgroup newuser
show groups for the user
groups newuser
Task : use the userdel and groupdel commands (and options)
In this task, you will enter commands to remove user accounts and group identifiers.
In the terminal window, enter the command(s) (in red) :
userdel command options (q to exit)
userdel --help | less
Knowledge item: userdel only removes entries from : /etc/passwd, /etc/shadow, and /etc/group. It does not remove the email and home directories, unless the -r option is added.
remove all traces of the user account
sudo userdel -r newuser
verify user record has been removed
grep newuser /etc/passwd
verify user home directory was deleted (note the error message)
ls -ld /home/newuser
groupdel command options (q to exit)
groupdel --help | less
delete group identifier
sudo groupdel newgroup
verify group identifier has been removed
grep newgroup /etc/group
Task : use the chmod, chown, chgrp and setfacl commands (and options)
In this task, you will enter commands to change file security and ownership attributes.
In the terminal window, enter the command(s) (in red) :
make a copy of existing file
cp .bashrc new-file
show permissions and ownership
stat new-file | grep "^Access: {"
Knowledge Item: the grep command searches for text, sometimes using characters called "regular expressions". You worked with these two important parts of Linux in Lab 3. For now, note the base eight (octal) codes and the symbolic r(ead) and w(rite) strings.
change permissions
chmod 755 new-file
Knowledge Item: Linux permissions in octal: 4 = r(ead),
2 = w(rite), 1 = (e)x(ecute). If the desired permissions for a category are rwx, the octal code is 4+2+1=7. If the desired codes were r-x, the octal code is 4+1=5. All three categories (user, group, others) codes must be supplied when setting absolute codes, such as: 755.
change permissions
chmod u=rwx,go=rx new-file
change file ownership
sudo chown root new-file
change group ownership
sudo chgrp root new-file
Note: only the root account can change file (group) ownership (via sudo).
show change in file and group ownerships
stat new-file | grep "^Access: {"
allow write access by specified user
sudo setfacl -m u:${USER}:rw- new-file
show file ACL
getfacl new-file
Knowledge Item: the access control list (ACL) for a file (or directory) contains both standard and special access permissions. More on ACLs in Lab 5 section 07.
Task : use the ls, stat and getfacl commands (and options)
In this task, you will enter commands to view directory file attributes.
Knowledge Item: all directory (files) have three associated date(s) of last : (a) modification of (data) contents; (b) change of attributes; and (c) access of data contents. These dates can be seen with the commands ls and stat.
In the terminal window, enter the command(s) (in red) :
show the three major dates
ls -ld $HOME ; ls -ldc $HOME ; ls -ldu $HOME
show all attributes of the home directory
stat $HOME
Note: : there is column labeled: "Birth:" (but has no associated date). Only the ext4 file system type supports storing file creation dates, and there is no easy way to see that date.
isolate the three major dates
stat $HOME | egrep "^Access: [[:digit:]]|^Modify:|^Change:"
Knowledge Item: all files also have an ACL (access control list). The ACL contains both standard permission codes and specific user and/or group access capabilities. The getfacl command shows both security areas. The setfacl command changes the specific user and/or group accesses (next in Lab 5 section 07).
show the ACL contents
getfacl $HOME
Task : apply chmod (SUID and SGID) settings, and use setfacl to control ACE (access control entries) on files
In this task, you will enter commands to change file security and ownership attributes.
Knowledge Item: two special attributes can be put onto executable program files: (a) SUID - when the program is run, the effective UID (user identification) is that of the executable program file owner instead of the actual user that is running the program; and (b) SGID - when the program is run, the effective GID (group identification) is that of the executable program group owner instead of the actual user's primary group that is running the program.
more...
In the terminal window, enter the command(s) (in red) :
make copy of existing executable
cp /usr/bin/bash test_shell
show user (UID) and group (GID) ownerships
stat test_shell | grep "^Access: ("
create child shell process
./test_shell
show identity (no changes)
id
logout from child shell process
exit
change file and group ownerships
sudo chown root:root test_shell
change permissions (4 = SUID)
sudo chmod 4755 test_shell
show (changed) UID, GID, and permissions
stat test_shell | grep "^Access: ("
run with protected child shell process (allows changing effective UID)
./test_shell -p
show different identities
id | gawk '{print $3,$4}
logout from child shell process
exit
show identity (changes removed)
id
change permissions on root home dir
sudo chmod 755 /root
make copy of existing file (as root)
sudo cp /root/.bashrc /root/test_bashrc
change file permissions (root only access)
sudo chmod 400 /root/test_bashrc
show permission codes
sudo ls -l /root/test_bashrc
error - no access via permission codes
cat /root/test_bashrc
allow read access to user
sudo setfacl -m u:$(logname):r-- /root/test_bashrc
Knowledge Item: $(logname) substitutes in the name of the real user that executed the sudo command.
show the effective access for the user
getfacl -e /root/test_bashrc
Knowledge Item: The effective access field shows the capabilities that the specific user (and/or group) has to the file, without changing any other category-based access codes.
access is now successful
cat /root/test_bashrc
Task : use the ln and ln -s commands
In this task, you will enter commands to manipulate hard and symbolic links
Knowledge Item: : all files usually only have one (1) hard link (identifier), which points to a data structure that contains all of the files attributes. the ln command creates another directory entry in the same filesystem that points to the same data structure. This is of limited use when different software programs require that a specific file is located in a different directory, and/or with different names.
more...
In the terminal window, enter the command(s) (in red) :
create hard link to existing file
ln .bashrc hardlink
show file id and attributes (note the matching values)
ls -li .bashrc hardlink
show file and hard link attributes (note the matching values)
stat .bashrc hardlink | egrep "File:|^Device:"
access is to the real file
cat hardlink
remove hard link only
rm hardlink
Knowledge Item: : the ln -s command creates an actual file in any desired directory. It turns out that all Linux filesystems are coded to assume that every file path that is specified for all commands is a symbolic link, and automatically substitutes in the real file path (if it is a symbolic link).
create symbolic link to existing file
ln -s .bashrc symlink
show file id and all other attributes (note the different values)
ls -li .bashrc symlink
show file and symbolic link attributes (note the different values)
stat .bashrc symlink | egrep "File:|^Device:"
access is to the real file
cat symlink
remove symbolic link only
rm symlink



