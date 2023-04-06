### Task : use regular expressions with **grep** and **sed**
In this task, you will enter commands to use regular expressions.

**Knowledge Item: regular expressions are supported by many standard Linux utilities besides grep and sed, such as vim. There are some similarities between regular expression characters and BASH shell wildcard characters. However, they are used in totally different situations.**

In the terminal window, enter the command(s) (**in red**) :

get a copy of a text file

**cp /userfind/name .**

show file contents (**note the empty lines !**)

**cat name**

help on regular expressions (5 screens)

**man grep** then enter : **/REG**

all lines that **start** with specified string (**greedy match**)

**grep "^string" name**

**Knowledge Item: grep matches as much as possible based on the regex and the text (a greedy match).**

all lines that start with string (**non-greedy**)

**grep --help | grep -- -w,**

**grep -w "^string" name**

all lines that **start** with exactly 4 characters

**grep "^….string" name**

find all "empty" lines

**grep "^\s\*$" name**

**Knowledge Item: an empty line contains either no spaces (or tabs), or one (or more) spaces or tabs.**

find all "non-empty" lines

**grep --help | grep -- -v,**

**grep -v "^\s\*$" name**

**Knowledge Item: -v tells grep to find all non-matching lines.**