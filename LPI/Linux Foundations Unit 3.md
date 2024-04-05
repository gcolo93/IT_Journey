# 3.1 Archiving Files on the Command Line #

## Topics ##

* Archiving files and compression
* tar command
* compression with gzip and bzip2
* Extracting archives and individual files

### Tar and GZIP ###

* Use **tar** to create a single file that can represent many files, This is a TAR archive (Tape Archive) or tarball. The “tape” part of the acronym can be disregarded as legacy
* The file is not compressed but may appear smaller than the total sum of all the files as better use is made of the block space on the disk
* To compress the file we can use tools such as **gzip** and **bzip2** from within tar.

### Main Actions ###

* **tar -c** to create
* **tar -t** to test or view the archive
* **tar -x** to expand an archive
* **tar -z** to compress or decompress with gzip
* **tar -j** to compress or decompress with bzip2

### File Extensions ###

* It tends to be the normal convention to add the following extensions to files:
  * **.tar**: plain tar archive
  * **.tgz** or **.tar.gz**: tar archives using gzip compression
  * **.tar.bz2**: tar archives using bzip2 compression

## 3.2 Searching and Extracting Data from Files ##

* Command line pipes
* I/O redirection
* Tools for searching data in text files
* POSIX Regular Expressions

### Command Line Pipes ###

* Using the pipe or vertical bar character | can send to output of one command to the input of another
* This is quite common in many OSs
  * – cat file | more

### IO Redirection ###

* > overwrite a file
* >> append to a file
* 2> std-error
* set -C or set -o noclobber
* >| to overwrite a file

### Tools ###

* find
* grep / egrep
* less
* head, tail
* sort
* cut
* wc

### Getting to Know Regular Expressions ###

* More features than shell globbing
* ^ lines begin with
* $ lines end with
* | or
* \b word boundaries
* \s white space
* \{1,\} repeating characters
