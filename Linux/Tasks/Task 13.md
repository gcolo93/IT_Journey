### Task : use redirection operators
In this task, you will enter commands to manipulate standard output and standard error.

In the terminal window, enter the command(s) (**in red** ) :

redirections manual pages (**q** to exit)

**man bash   then enter :   /REDIRECTION**

no output in terminal window

**date 1> output-file**

**Knowledge Item: 1> is the same as > and is referred to as standard output.**

contains command output

**cat output-file**

no output in terminal window

**who 1>> output-file**

**Knowledge Item: 1>> is the same as >> and appends to standard output.**

contains command output

**cat output-file**

error - no such command

**think**

send error text to a file

**think 2> error-file**

**Knowledge Item: 2> is referred to as standard error.**

contains error output

**cat error-file**

discard error text

**think 2> /dev/null**

**Knowledge Item: /dev/null is a valid destination for standard output or error data.**










































### Task : use special redirection operators and the **tee** command
In this task, you will enter commands to manipulate standard output and standard error.

In the terminal window, enter the command(s) (**in red** ) :

get a copy of a shell script

**cp /userfind/output\_error.sh .**

contents of shell script

**cat output\_error.sh**

execute shell script

**./output\_error.sh**

**Knowledge Item: the shell script output\_error.sh sends text to both standard output and to standard error, which by default, is your terminal window. You will do much more with shell scripting (techniques) in Part 3 of this Lab (sections 10, 11, 12).**

stdout and stderr sent to same file

**./output\_error.sh &> out\_err.txt**

**Knowledge Item: &> is the same as 2>&1 (after the destination for standard output has been specified).**

stdout and stderr sent to same file

**./output\_error.sh > out\_err.txt 2>&1**

contents of text file

**cat out\_err.txt**

**tee** command documentation

**info coreutils 'tee invocation'**

output sent to two destinations

**who | tee output.txt**

**Knowledge Item: tee sends output to the specified file(s) and to standard output.**

contents of text file

**cat output.txt**






































### Task : use special redirection operators and pipes
In this task, you will enter commands to manipulate standard input.

In the terminal window, enter the command(s) (**in red**) :

redirections manual pages (**q** to exit)

**man bash   then enter : /REDIRECTION**

get a fresh copy of the text file

**cp /userfind/name .**

send email with file as text body

**mailx user60 0< name**

**Knowledge Item: 0< is the same as < and is referred to as standard input**

email data is the text file contents

**mailx   at & prompt enter : 1**

**Knowledge Item: exit mailx by entering x at the & prompt**

get a copy of a shell script

**cp /userfind/embed\_input.sh .**

contents of shell script

**cat embed\_input.sh**

execute shell script

**./embed\_input.sh**

**Knowledge Item: << says that the input to the command immediately follows, and is specified by two matching strings. This is sometimes called a "here document"**

email body is the text file contents

**mailx   at & prompt enter : 2**

**Knowledge Item: exit mailx by entering x at the & prompt**

pipelines manual page (1 screen) (**q** to exit)

**man bash   then enter : /Pipelines**

no paginated output

**ps -ef**

paginated output

**ps -ef | less**

**Knowledge Item: | is a normal command line delimiter - no spaces are needed before and/or after the | (but are useful for readability).**

output from pipeline into a file

**ps -ef | grep sssd > output2.txt**

contents of pipeline output file

**cat output2.txt**

find largest file

**ls -l | tail -n +2 | sort -k5nr,5 | head -1**

**Knowledge Item: multiple pipes can be used to process output from commands. This example : (1) takes the output from ls and removes the first line (of output), then (2) does a reverse (descending) sort on the fifth field (size of the file), then (3) extracts and displays the top line (only), which will be largest file in the current default directory. We will use this example in Part 3 of Lab 3 in a shell script.**

find smallest file

**ls -l | tail -n +2 | sort -k5n,5 | head -1**

**Knowledge Item: this example : (1) takes the output from ls from and removes the first line (of output), then (2) does a default (ascending) sort on the fifth field (size of the file), then (3) extracts and displays the top line (only), which will be smallest file in the current default directory. We will use this example in Part 3 of Lab 3 in a shell script.**