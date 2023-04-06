### Task : use the **ln** and **ln -s** commands
**In this task, you will enter commands to manipulate hard and symbolic links**

**Knowledge Item: : all files usually only have one (1) hard link (identifier), which points to a data structure that contains all of the files attributes. the ln command creates another directory entry in the same filesystem that points to the same data structure. This is of limited use when different software programs require that a specific file is located in a different directory, and/or with different names.**

[**more...**](https://labclient.labondemand.com/Instructions/eba3574a-df4b-4f78-9b87-4f0631e66e5a?rc=10#)

**In the terminal window, enter the command(s) (in red) :**

**create hard link to existing file**

**ln .bashrc hardlink**

**show file id and attributes (note the matching values)**

**ls -li .bashrc hardlink**

**show file and hard link attributes (note the matching values)**

**stat .bashrc hardlink | egrep "File:|^Device:"**

**access is to the real file**

**cat hardlink**

**remove hard link only**

**rm hardlink**

**Knowledge Item: : the ln -s command creates an actual file in any desired directory. It turns out that all Linux filesystems are coded to assume that every file path that is specified for all commands is a symbolic link, and automatically substitutes in the real file path (if it is a symbolic link).**

**create symbolic link to existing file**

**ln -s .bashrc symlink**

**show file id and all other attributes (note the different values)**

**ls -li .bashrc symlink**

**show file and symbolic link attributes (note the different values)**

**stat .bashrc symlink | egrep "File:|^Device:"**

**access is to the real file**

**cat symlink**

**remove symbolic link only**

**rm symlink**