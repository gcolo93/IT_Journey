## 2.1 Command Line Basics

## Topics:
* Basic Shell
* Formatting Commands
* Working with options
* Variables
* Globbing
* Quoting

### Linux Command Line
* The CLI, command line interface, has always been important within Linux
* Especially if you are working with servers the CLI will continue to have great focus in Linux

### Commands
* **Ctrl+Shift++:** makes shell font bigger
* **Ctrl+Shift+-:** makes shell font smaller
* **Ctrl+D:** exits shell (can type ‘exit’ command as well)
* **Ctrl+L:** clears screen
* **touch:** create file
* **env:** show variables
  * **globbing** is grouping characters together
  * Linux is case sensitive
* **history:** shows used commands
* Anything that includes a space must be in quotations “”
* **semicolon ;** allows multiple commands to be run on the same line
* **double pipe ||** specifies to do one command of the other fails.
* **double ampersand &&** specifies to run the second command if the first succeeds

## 2.2 Obtaining Help from the Command Line

## Topics:
* Man pages
* Info pages
* ‘- - help’
* /usr/share/doc
* apropos
* whatis
* whereis

### Obtaining Help
* **'command' - - help | less** will show a more organized list of features for the command
* **which** will show all locations of an instance
* for more information you use the **man** command
* **forward slash /** allows you to search through man pages
* **info** command will show more information as well
* **q** to quit out
* **whereis** command will show all locations of the man pages and executables
* **whatis** command shows what/where the page/command is
* **pwd** gives current working directory
* **/usr/share/doc** houses the information for packages and files

## 2.3 Using Directories and Listing Files

## Topics:
* Files and Directories
*Hidden Files, Directories
* Home and ~
* File paths
* cd
* ls and aliases

### Everything is a File
* Everything in Linux is a file
  * Files
  * Directories
  * Links
  * **/dev/sda1** is a file for a block device, disk partition
  * **/dev/tty1** is a file for a character device, terminal

### Hidden Files
* A hidden file or directory in Linux is identified by the name starting with a dot
* Use **ls -a** to display all files including hidden files
* To display ONLY hidden files use **ls -a | grep ‘^\.’**

### Knowing your way home
* **cd or cd~** to return directly to the home directory
* The home directory is normally **/home/<username>**

### Full and Relative Paths
* We can access files or directories with the full path: **cd /home/<username>/Documents**
* can use **cd <folder in current directory>** to go directly to a folder in the current directory.
* File and Directory names are case sensitive
* **cd ../<Directory>** moves up one directory from current location

### ls and alias
* The command **ls** lists directory contents that are color coded
* when ls is run, it is actually **ls - color=”auto”** or something similar
* Using the command: **type ls** we can see ls is aliased to ls with additional options
* If we run the command: **\ls** the backslash means that it runs unaliased

## 2.4 Working with Files and Directories

## Topics:
* Files and Directories
* Globbing and Quoting
* mv, cp, rm, touch
* mkdir, rmdir

### Commands
* **cd !$** uses last argument
* **mkdir** makes an empty directory
* **rmdir** removes an empty directory
* **cp** copies files/directories
* **touch** creates an empty file
* **rm** removes files
* **mv** moves files

