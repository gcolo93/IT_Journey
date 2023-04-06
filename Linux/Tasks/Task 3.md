## Lab 2 : Command Line Basics - Part 1
In this lab, you will use commands on a Linux system to get familiar with syntax / rules of use, and to perform operations on files and directories.

**Time to complete Part 1 this lab exercise: 60 minutes.**

**This lab requires that you first read from the LPI Linux Essentials Study Guide, Chapters 5 and 7.**
### Understand your lab environment

In this lab, you will be using a Red Hat Enterprise Linux (**RHEL 8**) system.
### Lab Environment Instructions
1. Connect to your specific LOD RHEL Linux lab environment.
1. Enter the username and password that were provided for you - **NOTE** - these credentials will also be listed in the Resources area on the LOD screen; you only need to **left click** on the username in the larger area. A Password: prompt/box will appear. You only need to **left click** on the Password show in the **Resources** area on the LOD screen, or you may enter the password text characters manually.
1. Left click on the Activities icon

   then left click on the Terminal Icon

`     `to open a command terminal window.

**Knowledge Item: the terminal window that you just opened up is actually called a GNOME (GNU Network Object Module Environment) terminal window.**

**Hint: if you walk away from your session, there is a screen saver that will take control - you will have to enter your account password. The lab environment itself also has an idle timer. If the timer duration is reached, you will see "Save Session" screen. You can simply select "Resume".**

4. Before you enter each command, you may want to lookup the **man**(ual) documentation for the command, to get an idea of what operations the command can/will do, and what types of output is/are returned. You will look at the methods of obtaining documentation officially in the first part of this lab. For now, the way to see the documentation is simple - just enter : **man** *command* (for example, **man uname**). You can also get an abbreviated view of the documentation by entering : *command* **--help | less**
4. You will also notice that many commands are similar in their syntax, differing only by an option and/or and argument (value). Instead of re-entering the command again, you can hit the **up-arrow key** to recall the previous command, then modify it as needed. The recall (or history) buffer default size is 1000 previous commands !

































### Command Line Components Information
**Knowledge Item: before you can start using commands and utilities to manipulate file and directory (contents and attributes), the syntax for entering commands must be understood.**

**Any text shown in *bolded blue italics* represents an item that has to be entered/replaced.**

- the elements of a command line :
  ***shell-prompt command [option(s)] [arg1] [arg2] …. [argn]***

***shell-prompt*** defaults to value of **\s-\v\$**

***command*** enter command exactly as documented

***[option(s)]*** always preceded by a **-** or **--** ; modifies the effect of the command

***arg1 … argn*** filename, string, number, or some other object that the command acts on

**Examples**

short option

bash-4.4$ **cp -i *path-to-source-file path-to-destination-file***

value option

bash-4.4$ **tail -n 2 *path-to-file***

long option

bash-4.4$ **tail --lines=+2 *path-to-file***

**Knowledge Item: you can see the complete list of all three types of options for any command by entering : man *command*.**

**Example : man cp**

In the terminal window, enter the command(s) (**in red**) :

make a copy (**cp**) of an existing file with prompt if target file exists

**touch new\_file**

**ls new\_file**

**cp .bashrc new\_file**

**cp -i .bashrc new\_file**

make a copy of an existing file with prompt if target file exists

**clear**

**cp -i .bashrc new\_file**

show last two lines of an existing file (sort option)

**tail -n 2 .bashrc**