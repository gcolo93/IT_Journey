### 01 Execute commands for various help systems

In this exercise, you will use (Linux) commands to : get help information on commands and files.

Technology overview – you will be using Liinux commands and looking at the contents of documentation pages.
### Task : get help information using the **man** utility
In this task, you will enter commands to obtain manual information on your Linux lab system, using commands and options.

**Knowledge Item: the man command (short for manual), does two operations - (1), looks for a file named: topic.section.gz under the /usr/share/man hierarchy; (2) decompresses the file, evaluates the markup tags in the file (bolding, paragraphs, indentation, etc), then outputs the rendered text in a paginated fashion.**

In the terminal window, enter the command(s) (**in red**) :

help on **uname** command and its options

**uname -s**

hierarchies where man looks for the files / pages (**q** to exit)

**man man**

directories where **man** looks for the files / pages

**manpath**

**ls -d /usr/share/man/man\*/**

documentation for **cp** command (**q** to exit)

**man cp**

embedded help in the **cp** executable file

**cp --help | less**

shows the hardware platform architecture

**uname -i**

**Knowledge Item: there is separate database that contains a one line synopsis of every topic that has a manual page - this database can be created or updated via the mandb command. Note that this operation must be done in the root account (more on this later). The database can be searched by adding the -k option to the man command.**

build the "whatis" database of information

**sudo mandb -q**

**all entries that contain the string \*\*file** (**q** to exit)

**man -k file | less**

**Knowledge Item: to exit from the paginated output, hit the letter: q at the : prompt**

search for entries in a specific section (**q** to exit)

**man -k file | grep "(1)" | less**