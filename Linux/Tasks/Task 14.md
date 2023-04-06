### Task : use compression and decompression commandss
In this task, you will enter commands to manipulate file data compression.

In the terminal window, enter the command(s) (**in red** ) :

create **tar** archive

**cd**

**tar -C / -cvf $HOME/userfind.tar ./userfind**

size of **.tar** file (in bytes)

**stat -c %s userfind.tar**

compress **.tar** file

**gzip userfind.tar**

**Knowledge Item: gzip creates a compressed file with the last two letters of the file name are .gz .**

attributes of compressed **.tar** file (only)

**gunzip -l userfind.tar .gz**

\*decompress **.tar** file

**gunzip userfind.tar.gz**

**Knowledge Item: gunzip creates a decompressed file, removing the .gz suffix.**

size of (decompressed) **.tar** file (in bytes)

**stat -c %s userfind.tar**

create **tar** archive **and** compress it

**tar -z -C / -cvf $HOME/userfind.tar.gz ./userfind**

**Knowledge Item: tar (with the -z option) can create and compress a .tar file (but does not automatically add the .gz suffix).**

create **zip** archive

**(cd / ; zip -r $HOME/userfind.zip ./userfind)**

**Knowledge Item: zip creates and compresses data into a .zip file. The enclosing ( ) (called command grouping) force the shell to run the two commands in one separate process. After the zip command runs, the default directory path has not changed.**

show attributes of **zip** archive

**unzip -v userfind.zip**