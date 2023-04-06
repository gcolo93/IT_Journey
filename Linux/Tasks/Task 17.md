### Task : understand the benefits of software configuration tools
In this task, you will use a specific Linux web-based configuration management tool.

**Knowledge Item: many software configuration management tools have both a command line and a graphical interface. Some also have a web-based interface. Generally, these tools need to be run in a root identity. You will see many of these tools in Sections 3 - 6 of this Lab exercise.**

In the terminal window, enter the command(s) (**in red**) :

start web-based UI service

**sudo systemctl start cockpit**

web-based UI service information

**sudo lsof -i:9090**

in the graphical desktop, left-click on :

and then left-click on :

to start up **cockpit** configuration tool

enter in Firefox locator box : **https://localhost:9090**

**Knowledge Item: You will have to "Understand and accept the risks" of cockpit the first time. You will then login with the same username/password combination that you use to login to the Linux system.**

**in cockpit, from the left side menu (tabs), select and view information from :**

**System**

**Storage**

**Networking**

**Accounts**

**to exit cockpit, select**

**and then select : Log out**

### Task : compare command line and graphical tools
In this task, you will enter commands and options to obtain system information.

**Knowledge Item: you are going to compare using disk partitioning tools, parted and gparted. Note that gparted will need to be installed - it is not part of a standard RHEL installation. You will see more details on software package installation in Lab 4 Part 12.**

In the terminal window, enter the command(s) (**in red**) :

show disk names

**lsblk | grep disk**

command line disk partitioning

**sudo parted /dev/sda**

show partition table

at the **(parted)** prompt, enter : **print**

at the **(parted)** prompt, enter : **quit**

**Note: the graphical version of parted, named gparted, is not part of a standard RHEL 8 installation, but it can be installed from the EPEL repository (extra packages for enterprise Linux).**.

install package repository descriptor

**sudo yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm**

note epel/x86\_64 in the listing

**yum repolist**

install software package

**sudo yum -y install gparted**

run graphical disk partitioning tool (sample output)

**gparted**

**double left click on any partition area shown to get more information**


**when finished, left click on GParted tab -- select : quit**