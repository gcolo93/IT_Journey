### Task : use the **bash** executable built-in commands
In this task, you will enter commands to change file security and ownership attributes.

In the terminal window, enter the command(s) (**in red**) :

built-ins manual page (**q** to exit)

**man bash**   then enter : **3686**

**Knowledge Item: a shell built-in is part of the BASH executable; it is not a separate program.**

change default directory

**cd subdir4**

show default directory

**pwd**

show file types

**type cd /usr/bin/date ls**

show aliases

**alias ls**

**Knowledge Item: an alias adds additional options or arguments to a command.**

note no file colorization in the output

**dir**

define a command alias

**alias dir="dir --color"**

added file colorization (only for this session)

**dir**

add alias definition to .bashrc file

**cd**

**echo 'alias dir="dir --color" ' >> .bashrc**

**tail -1 .bashrc**

**Knowledge Item: the >> operator appends text to the bottom of a file - you will see redirection operators in Lab 3 section 05.**

re-execute shell initialization script

**source .bashrc**

run a command in the background

**sleep --help | head -7**

**sleep 500 &**

**Knowledge Item: the & says to run the command in parallel to the shell program, called a "child process".**

background process information

**jobs --help**

**jobs**

give control to background process

**fg --help**

**fg %1**

suspend process, return to the shell

**control+Z**

**Hint: control+Z means to hold down the CTRL key while hitting the Z key.**

background process shows as **Stopped**

**jobs**

allow background process to run

**bg --help**

**bg %1**

terminate background process

**kill --help**

**kill %1**

**Knowledge Item: the kill command accepts either a job number (preceded by the %) or a process identification (PID) number.**

note the pagination prompt (**q** to exit)

**more --help**

**ps --help a | egrep -- "-e|-f "**

**ps -ef | more**

**Knowledge Item: : the ps command with the -ef options shows all of the processes that are currently on the system - piping to more paginates the output.**

change the pagination prompt

**export MORE=-cd**

note change in the pagination prompt (**q** to exit)

**ps -ef | more**

**Knowledge Item: bash maintains a history buffer of the last 1000 entered commands, and the buffer is saved to $HOME/.bash\_history at logout, then reloaded at the next login.**

show the entire history buffer (**q** to exit)

**history | less**

show the last 10 commands only

**history --help | head -5**

**history 10**

**Knowledge Item: you can use the up- and down- arrow keys to recall commands from the history buffer. You can use standard keys (right- and left- arrows), DEL and BS keys to modify the recalled command. The Enter key will then re-execute the command.**