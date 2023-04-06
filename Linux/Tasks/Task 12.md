### Task : use the **grep** and **sed** commands and options
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.

In the terminal window, enter the command(s) (**in red** ) :

get a fresh copy of the text file

**cp /userfind/name .**

count of all lines that contain **string**

**grep -c "string" name**

case insensitive search

**grep -i "StRiNG" name**

line numbers that contain **string**

**grep -n "string" name**

file names (skipping directories) that contain string

**grep -l -d skip "string" \***

delete all lines that **start** with string

**sed "/^string/d" name**

substitute first occurrence of **string** with **STRING**

**sed "s/string/STRING/1" name**

substitute all occurrences of **string** with **STRING**

**sed "s/string/STRING/g" name**

file was not changed

**cat name**

**Knowledge Item: sed only changes the output by default. To actually change (a) file(s), the inline -i editing option must be added.**

\*substitutions are actually made in the file

**sed -i "s/string/STRING/g" name**

file was changed

**cat name**