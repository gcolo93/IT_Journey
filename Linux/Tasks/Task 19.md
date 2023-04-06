### Task : use commands to get attributes of executable files and for running programs/processes
In this task, you will enter commands to view executable file and process information.

In the terminal window, enter the command(s) (**in red**) :

show file is an executable

**file /usr/bin/date**

show file is an executable

**readelf -h /usr/bin/date | grep Type:**

show shared libs needed at run

**readelf -d /usr/bin/date | grep NEEDED**

show shared libs program was linked with

**ldd /usr/bin/date**

run program in parallel

**sleep 800 &**

**Knowledge Item: the & character says to run the command/program in the background.**

show process in the background

**ps -fp $!**

**Knowledge Item: the $! variable contains the PID of the last program run in the background**

show files opened by process

**sudo lsof -p $! | less**

virtual address space of process

**pmap -x $! | less**

stop background process

**kill $!**
### Task : use the **free**, **slabtop**, **top** and **sar** commands
In this task, you will enter commands to view system resource areas

In the terminal window, enter the command(s) (**in red**) :

static view of memory related areas

**free -mth**

**Knowledge Item: the watch command will take the output from any static command and make it dynamic. To exit watch, you hit control+c .**

a simple monitor (**control+c** to exit)

**watch -n5 'free -mth;echo;uptime;echo;ifstat'**

dynamic view (**q** to exit)

**top**

show memory allocations (**q** to exit)

**sudo slabtop**

show only processes using memory(**control+c** to exit)

**pidstat -r 10**

show only processes using CPU(**control+c** to exit)

**pidstat -u 10**

show only processes with active disk I/O (**control+c** to exit)

**pidstat -d 10**

show CPU usage averages

**sar -u**