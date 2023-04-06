### Task : properly structure, execute, and debug BASH shell scripts
In this task, you will enter commands to manipulate shell scripts.

In the terminal window, enter the command(s) (**in red** ) :

get a copy of a shell script file

**cp /scripting/samples/sample1.bash .**

show the signature/shebang line

**head -1 sample1.bash**

**Knowledge Item: the first line of a shell script starts with what is called the shebang #! (or signature), and is made to look like a comment. The shebang tells the Linux kernel to run the path that immediately follows in a separate child process. The rest of the (shell script) file becomes the command input to that (child or sub-) shell.**

permissions and ownership

**stat sample1.bash | grep "^Access: {"**

**Knowledge Item: a shell script must be executable in order to run it as a standalone program.**

\*show shell script contents

**cat sample1.bash**

execute shell script

**./sample1.bash**

**Knowledge Item: technically, you do not debug a shell script (execution). Instead, you can request that the shell traces the execution. The trace output : (1) will be removed of the shebang, comment and empty lines; (2) shows each actual line being executed and is preceded with an + character, and (3) all output and/or error messages will appear immediately after the line that generates them.**

[...less](https://labclient.labondemand.com/Instructions/eba3574a-df4b-4f78-9b87-4f0631e66e5a?rc=10#)

documentation for shell scripting tracing/debugging

**bash -c 'help set' | grep -- "^.\*-x   P"**

trace the execution of the shell script

**bash -x sample1.bash**









































### Task : use variables in shell scripts
In this task, you will see how variables are used in shell scripts.

**Knowledge Item: most techniques in a shell script can be tried out at the command line. This allows for testing and debugging before ever going into a text editor to create and/or modify a(n existing) script.**

In the terminal window, enter the command(s) (**in red** ) :

string data type variable

**string\_var="Linux Foundations"**

**Knowledge Item: variable scope (access) in shell script defaults to, and is usually desired to be local(to the script only). Defining variables to be exported (global access scope) is usually done in the .bashrc (or specific) shell script.**

variable scope is local (by default) - notice that there is no output

**env | grep string\_var**

change variable scope to global

**export string\_var**

**Knowledge Item: variable substitution is done by placing a $ in front of the variable name.**

request variable substitution

**echo $string\_var**

**Knowledge Item: all variable values are stored and treated as character data ( by default). The typeset -i command tells the shell to store the variable value as a binary integer. BASH only supports binary integer variables and operations.**

binary numeric variable

**typeset -i int\_var=56**

**Knowledge Item: variable substitution is done by placing a $ in front of the variable name.**

request variable substitution

**echo $int\_var**

**Knowledge Item: numeric operations are requested by ((   )) around the operation.**

binary variable operations (and forcing the substitution of the numeric operation)

**echo $((int\_var = int\_var + 1))**

shell script with variables and loops

**cp /scripting/samples/sample2.bash .**

show shell script contents

**cat sample2.bash**

execute shell script

**./sample2.bash**

find largest file - from Lab 3 section 07

**ls -l | tail -n +2 | sort -k5nr,5 | head -1**

**Knowledge Item: the commands sequence to find the largest file only works for the current default directory. It would be very useful to be able to supply one (or more) argument(s) to a shell script, and then be able to use the values in commands. To pass value(s) from the command into a shell script, there are special positional variables. The first argument to the shell script can be accessed via $1 , the second argument via $2, and so on.**

[...less](https://labclient.labondemand.com/Instructions/eba3574a-df4b-4f78-9b87-4f0631e66e5a?rc=10#)

shell script that shows the use of command line arguments

**cp /scripting/samples/sample4.bash .**

show shell script contents

**cat sample4.bash**

execute shell script (with argument)

**./sample4.bash /etc**

**./sample4.bash /var**

**./sample4.bash**

**Note: in the preceding commands, /etc was available in the shell script as $1 , /var was available in the shell script as $1 , and in the third command, $1 had a value of an empty string.**







































### Task : use **for**, **while**, **until** , **if** and **case** statements in shell scripts
In this task, you will use special shell scripting constructs.

In the terminal window, enter the command(s) (**in red** ) :

help on statements (7 screens) (**q** to exit)

**man bash   then enter : /Compound Commands**

loop over (space delimited) list

**for x in 1 2 3 4 5 ; do echo $x ; done**

**Knowledge Item: x is called a loop iterator, and it is assigned the next value in the list. When there are no more values in the list, the loop is finished.**

loop over variable value

**x=5 ; while ((x)) ; do echo $((x--)) ; done**

loop over variable value

**x=5 ; until ((x == 0 )) ; do echo $((x--)) ; done**

**Knowledge Item: while tests for a true condition (non-empty string or non-zero numeric value or a true test); until tests for a false condition (empty string or zero numeric value or a false test).**

**Knowledge Item: if has four forms: simple, complex, block, and single line.**

test variable value

**typeset -i x=5 ; if (( x == 5 )) ; then echo "x is 5" ; fi**

**typeset -i x=6 ; if (( x == 5 )) ; then echo "x is 5" ; else echo "x is not 5";fi**

**Knowledge Item: a case block takes one value and successively compares it to a list of "selector patterns". Upon the first match, the statement(s) that are tied with the selector pattern are then executed.**

**case *variable-name* in**

`   `***test-on-variable* )**

`   `***command(s)-to-execute* ;;**

`   `***test-on-variable* )**

`   `***command(s)-to-execute* ;;**

`   `**.**

`   `**as many selectors as needed**

`   `**.**

**esac**

shell script that contains loops and conditionals

**cp /scripting/samples/sample3.bash .**

show shell script contents

**cat sample3.bash**

execute shell script

**./sample3.bash**

### Task : access special status variables and error handlers
In this task, you will use special shell scripting constructs

**Knowledge Item: all commands return a completion status. A value of 0 indicates success; any other value indicates warning or failure. The completion status is available in the special variable $?.**

In the terminal window, enter the command(s) (**in red** ) :

command that "works"

**date**

show completion status

**echo $?**

try to execute non-existent command

**think**

show completion status

**echo $?**

**Knowledge Item: in a shell script, the value of $? is (usually) captured into a variable and then checked with an if statement.**

**Knowledge Item: trap defines a signal handler, which can include: errors, interrupts, and shell script exit.**

define error handler

**trap 'echo "error occurred" ' ERR**

generate error - note resultant outputs

**think**

clear error handler

**trap -- ERR**

shell script that contains error handlers and tests

**cp /scripting/samples/sample5.bash .**

show shell script contents

**cat sample5.bash**

execute shell script

**./sample5.bash**