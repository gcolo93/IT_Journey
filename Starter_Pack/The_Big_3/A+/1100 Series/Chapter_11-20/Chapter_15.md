CHAPTER 15

Working with the Command-Line Interface

In this chapter, you will learn how to

-   Explain the operation of the command-line interface

-   Describe fundamental commands

-   Explain file manipulation

-   Describe additional useful Windows commands

-   Describe additional helpful macOS and Linux commands

-   Explain scripting languages and platforms

Whenever I teach a class of new techs and we get to the section on working with the command line, I'm invariably met with a chorus of moans and a barrage of questions and statements like "Why do we need to learn this old stuff?" and "Is this ritualistic hazing appropriate in an IT class?"

For techs who master the interface, the command line provides a powerful, quick, and flexible tool for working on a computer. Learning that interface and understanding how to make it work is not only useful, but also necessary for all techs who want to go beyond baby-tech status. You simply cannot work on modern computers without knowing the command line! I'm not the only one who thinks this way. The CompTIA A+ 220-1102 certification exam tests you on a variety of command-line commands, both in Windows and Linux, for doing everything from renaming a file to rebuilding a system file.

If you're interested in moving beyond Windows and into Unix-like operating systems such as Linux and macOS, you'll find that pretty much all of the serious work is done at the command line.

The command line is popular for many reasons. Let's consider three for this chapter. First, if you know what you're doing, you can do most jobs more quickly by typing a text command than by clicking through a graphical user interface (GUI). Second, a command-line interface (CLI) uses fewer system resources, so it's the natural choice for jobs where you don't want (or couldn't even run) a full-blown GUI. Third, you can combine multiple text commands to automate complex tasks.

This chapter gives you a tour of the Windows, Linux, and macOS command-line interfaces, explaining how they work and what's happening behind the scenes. You'll learn the concepts and master essential commands. You'll work with files and folders and learn about scripting. It's all fun! A good tactic for absorbing the material in this chapter is to try out each command as it's presented.

NOTE   If you're using a Windows system, this is a great opportunity to jump ahead to Chapter 22 and try some virtualization. Consider loading up a virtual machine and installing Linux so you can practice the Linux command line. Check out and install my favorite virtualization tool, Oracle VirtualBox at https://www.virtualbox.org, and then download an ISO file from https://ubuntu.com.

1102

Deciphering the Command-Line Interface

A command-line interface is a little like a voice assistant (such as Amazon's Alexa, Apple's Siri, and Google Assistant), but instead of talking and getting a response, you type and get a response. When you say the magic words to wake up a voice assistant, it'll do something (make a noise, light up, change its screen, etc.) to indicate that it heard you and is ready for your request. A CLI tells you it's ready to receive commands by displaying a specific set of characters called a prompt. Here's an example of a generic prompt:

You type a command and press enter to send it:

Much like a voice assistant, the computer evaluates what you entered and responds. A computer generally responds by displaying the information you requested, a list of things the command did, a request for more information, or an error message if it couldn't understand or perform your request. When it finishes, it displays a new prompt to show that it is ready for your next instruction:

Running commands from the command line is equivalent to interacting with buttons, icons, and menus in a GUI. The results are basically the same: you tell the computer to do something and it responds.

Getting the Most out of the CLI

When you're trying to find your sea legs, the big difference between CLIs and GUIs is that everything you can do in a GUI has to take up space on the screen (or be tucked away in menus that take up space). It's much easier to discover what you can do with a GUI, but it also means that GUIs for complex tasks are stuffed with deeply nested menus and panels that take time to navigate. The CLI can be faster for many tasks once you are sure-footed, but it is much less discoverable: you must learn (and then know) which commands exist and what they do.

Start a separate file (or even a notebook) for your own notes about the command line. Keep track of the different shells and commands you encounter, write a short summary of what each one does, and maintain a list of situations where you've found each helpful. Every time you have to go ask a mentor, friend, coworker, or search engine what command to use for some task, make sure to update your notes!

Shells

The command line, like a GUI, is just another way to interface with a computer. The command line interprets input and sends it to the OS in a form the OS understands, and then shows the results. The tool that interprets input is called the command-line interpreter, also known as the shell.

EXAM TIP   The CompTIA A+ 1102 objectives don't mention PowerShell or any of its key concepts. I'm including some PowerShell basics because I think you should learn how to use it---but the Windows examples in this chapter focus on Command Prompt because that's what you'll see on the exam.

While most operating systems have only one GUI, that's not the case with the shell. Every operating system has the ability to interface with different types of shells. The default in Windows is now PowerShell, but the traditional Command Prompt (we nerds call it cmd) is still there. If you use Linux or macOS, you'll be spoiled with choices. Some of the most common are the GNU Bourne-Again Shell (bash), Z shell (zsh), Fish shell (fish), and C shell (csh). Many (but not all) Linux distributions (aka distros) have long used bash as their default shell---and so did macOS until it switched to zsh in late 2019. It's a rite of nerd passage to experiment with different shells.

NOTE   There are way more shells than I'm listing here. The most common shells are everywhere because they're as old as the hills---aside from Fish (2005) and PowerShell (2006), the other shells I listed got their start between 1978 and 1993! If you want to take something more modern for a spin, my favorites are Elvish, Nushell, Oil, and Xonsh.

Accessing the Command-Line Interface in Windows

You access the command-line interface in Windows by starting the shell program Command Prompt. We touched on accessing the CLI in Chapter 2, but let's develop this procedure more here.

A common way to access the command-line interface is through the Start menu or the Start screen's Search bar. Type cmd from the Start screen. Command Prompt appears as the best match (see Figure 15-1). Press ENTER.

Figure 15-1  Starting Command Prompt in Windows 11

On Windows 11, Command Prompt opens in the brand new Windows Terminal, so it looks a little different than it does in Windows 10 (see Figure 15-2). To close the CLI, you can either click the Close box in the upper-right corner, as on any other window, or simply type exit and press ENTER.

Figure 15-2  The command-line interface in Windows 11 (top) and 10 (bottom)

Try This!

Opening Windows GUI Programs from the Command Line

Keep in mind as you go through this chapter that the command line is just another tool for communicating with the system, so try this! At a command line, type notepad and press ENTER. What happens? The graphical program Notepad opens up, just as if you'd double-clicked on its icon. Here's another: type explorer and press ENTER. Voilà! File Explorer loads.

If you try to run a command that requires elevated or administrative privileges on Windows, you receive a UAC "Windows needs your permission to continue" dialog box. (You learned about UAC in Chapter 13.) You can also manually run a command with elevated privileges by right-clicking on a command-prompt shortcut and then selecting Run as administrator. If Windows prompts for the administrator password or credentials, enter whatever is needed.

NOTE   You can create a shortcut to a Windows command prompt with elevated privileges by right-clicking on the desktop and selecting New | Shortcut. For the location of the item, type cmd and click Next. Type cmd to name the shortcut, and click Finish. The shortcut appears on the Desktop. Next, right-click the shortcut and select the Advanced button. In the Advanced Properties dialog box, check the Run as administrator box and click OK. You have now created a Windows command-prompt shortcut that will always run with administrative privileges.

Accessing the Command-Line Interface in macOS and Linux

Linux and macOS have very similar command lines. Both come with a default terminal emulator (its name comes from the fact that it emulates iconic old-school hardware terminals that were common from the 1960s to the 1990s---but you can just think of it as a GUI application that enables you to use a shell). The default in macOS is named Terminal, and different distros of Linux use different emulators, such as Konsole Terminal and GNOME Terminal. To make things easy, we'll use the command-line interface in Ubuntu Linux which is also conveniently named Terminal.

NOTE   Linux and macOS are so similar because they are both heavily influenced by the old UNIX operating system. It may not be obvious from their GUIs, but the relationship is clear at the command line. Throughout this chapter I'll use "UNIX" or "UNIX-like" or "UNIXes" when Linux and macOS are equivalent and I'll call them out by name when they differ.

To open Terminal in macOS, either launch the Terminal app from the Utilities folder (located in the Applications folder) or activate Spotlight (COMMAND-SPACEBAR), type terminal, and press ENTER to bring up the macOS Terminal (see Figure 15-3).

Figure 15-3  macOS Terminal

The way to open a terminal emulator in Linux varies depending on the Linux distro you use. Generally, every desktop-focused Linux distro has some form of finder or search function on the desktop that works similarly to the search tools in macOS and Windows. Find this tool and then type terminal and press enter to start the program. This brings up the terminal window, as shown in Figure 15-4.

Figure 15-4  Linux Terminal

TIP   Spotlight is a phenomenal search tool in macOS. It indexes your drive(s), not just for filenames, but for content. That means you can search for specific files, of course, plus all sorts of other things, like apps, e-mail messages, music, contacts, and even flight information! Try it!

UNIXes also enable you to run commands with advanced privileges, called super user or root privileges. Two commands do the trick: su and sudo. Even though this advanced privileges function is equivalent to the elevated privileges in Windows, UNIXes handle this elevation differently. First, open Terminal. Whenever you need to run a command as root, type sudo followed by the desired command and then press ENTER. The system will prompt for a password (usually; it can be configured not to) and then execute the command.

NOTE   While running commands with elevated privileges is the most common use of su and sudo, try to remember su as standing for substitute user identity instead of super user. When you need to run commands as any specific user, you can use su or sudo.

If the system doesn't have sudo, it should have its older cousin su. With su, you typically just type su and press ENTER; it will prompt you for the root password. Once you successfully enter the password, you'll end up in a new shell session for the root user. This session will have a different prompt (usually the character at the end changes from a $ to a #) and every command you enter from then on will be executed as root. When you finish working as root, type exit and press ENTER. Terminal won't close like before---it will just end the inner root shell session and return you to the outer session. You can see how the prompt changes in the following example:

TIP   The sudo command enables users to do root things without logging in as the root user or even knowing its password.

The Prompt

Regardless of what shell you use, the command line always focuses on a specific folder, the working directory, usually indicated by the prompt. If any commands use a relative file path, it will be relative to the current working directory. Here's an example: in Windows, if you see a prompt that looks like the following line, you know that the focus is on the root directory of the C: drive:

C:\>

In a UNIX-like OS the prompt is subtly different, but functionally the same. First, these systems don't use the Windows drive lettering concept: all forms of storage are simply mounted as folders. Second, prompts on these systems usually show the logged-on user and system as well as the current directory. Third, paths on these systems use a forward slash (/) instead of a backslash (\). This prompt shows user mike is on the "server" system and is in the home directory:

mike@server:/home$

In Windows, if you see a prompt that looks like Figure 15-5, you know that the focus is on the \Diploma\APLUS\ folder of the C: drive. If you're working with files from the command line, it's important to focus the prompt on the drive and folder where you want to work.

Figure 15-5  Command prompt indicating focus on the C:\Diploma\APLUS\ folder

Closing the Terminal

Closing a command prompt is easy and is done the same way in Windows, macOS, and Linux. From the CLI you want to close, just type exit and press ENTER. This technically just exits the shell itself, but many terminal emulators will automatically close the window or tab when the shell terminates. If yours doesn't, manually close the tab or window as well.

mike@server:/home$ exit

Drives and Folders

When working from the command line, you need to be able to focus the prompt at the specific drive and folder that contains the files or programs with which you want to work. This can be a little more complicated than it seems.

Before we get too deep here, let's review what you studied in Chapter 9. Windows assigns drive letters to each hard drive partition and to every recognized form of mass storage. HDD/SSD partitions usually start with the letter C:. Thumb drives, external drives, and optical drives get the next available drive letter after the last hard drive partition.

UNIXes do not use drive letters. Instead, the boot partition is defined as the root drive, shown as just a slash: /. All other storage---partitions, optical discs, thumb drives, and so on---must go through a process called mounting to enable the OS to treat them as folders. These folders are most often mounted to a single folder off the root drive called /mount or /media in Linux and /Volumes in macOS.

TIP   Windows partitions are also mounted (that's what happens when they get a drive letter), although Microsoft rarely uses that term.

Whatever the names of the drives, all operating systems use a hierarchical directory tree to organize the contents of these drives. All files are put into groups called folders, although you'll often hear techs use the interchangeable term directory. Any file not in a folder within the tree---that is, any file in the folder at the root of the directory tree---is said to be in the root directory. A folder inside another folder is called a subfolder. Any folder can have multiple subfolders. A subfolder may have subfolders. Two or more files with the same name can exist in different folders on a PC, but two files in the same folder cannot have the same name. In the same way, no two subfolders under the same folder can have the same name, but two subfolders under different folders can have the same name.

NOTE   It helps to visualize a directory tree as upside down, because in geekspeak, the trunk, or root directory, is described as "above" the folders that divide it, and those subfolders "below" root are spoken of as being "above" the other subfolders inside them. For example, "The file is in the Adobe folder under Program Files."

When describing a drive in Windows, you use its letter and a colon. For example, the hard drive would be represented by C:. To describe the root directory, put a backslash (\) after the C:, as in C:\. To describe a particular directory, add the name of the directory. For example, if a PC has a directory in the root directory called Test, it is C:\Test. Subdirectories in a directory are displayed by adding backslashes and names. If the Test directory has a subdirectory called System, it is shown like this: C:\Test\System. This naming convention provides for a complete description of the location and name of any file. If the C:\Test\System directory includes a file called test2.txt, it is C:\Test\System\test2.txt.

The location of a file is called its path. An absolute path specifies the file's exact location, while a relative path is just enough to find it from a starting point (such as the working directory). Think of this like an address. If a buddy on the other side of the world wanted to send you a gift, you'd need to give them a complete address. But if you're having pizza delivered from a few blocks over, a street and number should be enough for the delivery driver to find your house. The absolute path for the test2.txt file is C:\Test\System\test2.txt, but System\test2.txt would be enough to find it from C:\Test. Here are some examples of possible Windows paths:

UNIXes also use paths. Folder names are separated by a forward slash (/), however, instead of the backslash used by Windows. Also, Windows and macOS are not usually case sensitive, while Linux is. For example, in Linux it's perfectly acceptable to have two folders called "Mike" and "mike" inside the same folder. Windows and macOS do not allow this. Here are some examples of UNIX paths:

While it is hard to generalize about prompts on UNIXes---they differ from shell to shell and users often customize them---they usually show your folder location a bit differently than Windows. Generally, your default prompt points at the /home/<username>/ folder. By default, however, the prompt on most UNIXes just shows a tilde (~), as follows:

mike@server:~$

The ~ is really just a shorthand for your user's home directory; in this case it means my working directory is /home/mike. Yes, a little confusing, but welcome to UNIX! There's a handy utility, pwd, that tells you the full path of the current working directory if you're unsure:

Here are key points to remember about folder names and filenames:

-   Folders and files may have spaces in their names.

-   The only disallowed characters in Windows are the following eleven: * "/ \ [ ] : ; | = ,

-   In UNIX the only disallowed character is a forward slash: /

Mastering Fundamental Commands

It's time to try using the command line, but before you begin, a note of warning is in order: the command-line interface is picky and unforgiving. It will do what you say, not what you mean, so it always pays to double-check that those are one and the same before you press ENTER and commit the command. One careless keystroke can result in the loss of crucial data, with no warning and no going back. In this section, you'll explore the structure of commands and then play with basic commands to navigate and manipulate your OS's folder structure.

Structure: Syntax and Switches

All commands in every command-line interface use a similar structure and you run them the same way. You type the name of the command, followed by the target of that command and any modifications of that command that you want to apply, and then press ENTER to execute the command. You specify a modification with its switch or option (often a special character such as / or - followed by one or more letters, numbers, or words), which usually follows either the command or the target, depending on the command. The proper way to write a command is called its syntax.

NOTE   From this point on, I'll just assume you have a terminal open and ready. I'll also use the word run when I want you to type a command and then press ENTER. If I just tell you to type something, look for more instructions before you press ENTER.

The command generally won't understand if you spell anything incorrectly or use a \ when the syntax calls for a /. Since the CLI doesn't have an easy-to-discover button or menu for every command, you have to learn the correct syntax for each. (There's no shame in looking it up each time---there are plenty of commands I can't keep straight---but it will slow you down.) Consider these two common forms (the brackets are just placeholders---you wouldn't type them):

[command] [target (if any)] [switches]

or

[command] [switches] [target (if any)]

How do you know what switches are allowed? How do you know whether the switches come before or after the target? Don't just guess, look it up!

Teaching Yourself to Fish

There are thousands of commands out in the world. Some of them do something so simple they don't have any options; others are monsters with hundreds and hundreds of options. How do you know what switches are allowed and what they do? How do you know whether the switches come before or after the target? You look up the command's documentation.

If you want to find out the syntax and switches used by a particular command in Windows Command Prompt, run the command itself with the /? switch to get help:

[command name] /?

PowerShell has a dedicated command for this---just run Get-Help with the command you're interested in:

Get-Help [command name]

In UNIX, run man (manual) with the name of the command you're interested in:

man [command name]

Any of these commands searches for a matching manual entry (commonly called a manual page or man page) and---if it finds an entry---opens it in an interactive reader (which is commonly called a pager---we'll talk more about these in a minute). You should be able to scroll through the document with your mouse-wheel, trackpad, or arrow keys; press the Q key to quit the interactive reader when you're done.

EXAM TIP   In the real world, there are a bewildering number of ways to get command help (including a few I'm leaving out). The CompTIA 1102 exam objectives, however, only mention the /? switch on Windows, and the man command for Linux.

Command Types

I need to take you down a rabbit hole to learn something that trips up a lot of new CLI users, especially on UNIX: there's more than one type of command, and the command type affects how to look up information about it. The most important types are builtins (which are actually part of your shell) and standalone external commands.

On a UNIX-like OS, you can run the type builtin followed by a command to see what type it is. Here's a command we've already looked at:

Generally speaking, the manual won't have an entry for a builtin unless it is also an external command. Read that again! Yes---it's possible to have more than one version of a command. If you run type again with the -a (all) switch, it will show if there is more than one version. When you actually run this command, your shell will use the one at the top of the list):

There's no tried and true way to find the right information for builtins; it varies from shell to shell. Bash and Fish, for example, both have a built-in help command (the former displays a summary, the latter opens a Web page)---but Z shell lists them all on the "zshbuiltins" manual page. Take the time to learn how your shell handles this! Sooner or later, it'll save you a lot of confusion.

NOTE   Some external commands just don't have a manual page (or you might have to do extra work to find, enable, or install its man page). As a last resort, try running the command with the --help or -h switch.

Getting help in Windows is a little more consistent, but the method does still differ depending on which shell you use. In PowerShell, for example, the Get-Command cmdlet is roughly equivalent to the type builtin. The following command shows that, in PowerShell, pwd is an alias (an alternative name) for a cmdlet named Get-Location:

The Windows dir command and the UNIX ls command show you the contents of the working directory. If you're like most techs, you'll use dir or ls more often than any other command. When you open a command-line window in Windows, it opens focused on your user folder. You will know this because the prompt looks like C:\Users\User name>. When you run dir, you will see something like:

The default prompts in Linux don't show the full path, but on my Ubuntu Linux system, running ls shows the following in my home directory:

If you are following along, remember that different computers contain different folders, files, and programs; you will see something different from these examples. If a lot of text scrolls quickly down the screen in Windows, try running dir /p (the /p is for pause). The /p switch is a lifesaver when you need to skim a large directory. Just press SPACEBAR to display the next screen.

NOTE   Some commands give you the same result whether you include spaces or not. Running dir/p and dir /p, for example, produces the same output. Some commands, however, require spaces between the command and switches. Get into the habit of putting spaces between your command and switches and you won't run into problems.

In UNIX, you can get the same result as dir /p by running ls | more. The | symbol is an "operator" called a pipe. You are telling the shell to take the output of ls and, instead of sending it directly to the screen, "pipe" it through the more command (more is a pager---a command that enables you to browse through multipage documents). The pipe operator works in all three operating systems and is incredibly powerful. You'll see lots more of the pipe operator later in this chapter.

NOTE   If you try to follow along in PowerShell, be prepared for output and switches to differ. PowerShell has its own take on many classic Command Prompt commands! Its dir command, for example, has no equivalent to the /p switch. Instead, you can run dir | more like you would in UNIX.

dir Command

When you run a simple dir command, you will see file entries that list the creation date, creation time, file size in bytes, filename, and extension:

You'll also see directory entries that list the creation date, creation time, <DIR> to tell you it is a folder, and the folder name:

Next, run dir /w and note that it only lists filenames, arranged in columns across your screen. Finally, run dir /? to list all the command's switches, as shown in Figure 15-6.

Figure 15-6  Running dir /? in Windows lists all possible switches for the dir command.

ls Command

The ls command, which is for listing the contents of directories, has gobs of options that control things like what it lists, in how much detail, and in what order. For now let's just cover one of the more important options: -l.

NOTE   As with many fundamental UNIX commands, you can find different variants of ls (with different options) on different systems.

Running ls with the -l (or long listing) switch outputs detailed information about all the files:

We'll discuss this output in more detail as we continue through the chapter.

NOTE   You can often use more than one switch or option to modify a command (though some options conflict with each other). For example, try running ls -a -l -h in macOS or Linux. With many commands, you can run multiple switches together. With ls, for example, ls -alh works just fine, with all three switches applied.

Changing Directory Focus: The cd Command

The cd command, which changes the current working directory, works in every operating system (although there are differences). To use it, run cd followed by the directory you want to focus on.

In Windows, for example, run cd \obiwan to go to the Obiwan directory inside the root directory. If the system has an Obiwan directory there, the prompt changes focus to that directory and appears as C:\Obiwan>. If no Obiwan directory exists or if you accidentally type something like obiwam, you get the error "The system cannot find the path specified." If only I had a dollar for every time I've seen that one! I usually get them because I've typed too fast. If you get this error, check what you typed and try again.

Errors Are Good!

Consider errors in general for a moment---not just command-prompt errors such as "Invalid directory," but any error, including errors in the GUI. Many new computer users freeze in horror when they see an error message. Do not fear error messages. Error messages are good! Love them. Worship them. They will save you.

Seriously, think how confusing it would be if the computer didn't tell you when you messed up. Error messages tell you what you did wrong so you can fix it. You absolutely cannot hurt your PC in any way by typing the dir or cd command incorrectly. Take advantage of this knowledge and experiment. Intentionally make mistakes to familiarize yourself with the error messages. Have fun and learn from errors!

Ok, let's get back to the cd command. Run cd \ to focus on the root directory. You can use the cd command to point the prompt to any directory. For example, you could run cd \obiwan\my\hope from a C:\ prompt, and the prompt would change to C:\Obiwan\my\hope>---assuming, of course, that your system has a directory called C:\Obiwan\my\hope. (I can't be the only one, right?)

Once the prompt has changed, run dir again. You should see a different list of files and directories. Every directory holds different files and subdirectories, so when you point the prompt to different directories, the dir command shows you different contents.

Changing directory focus in UNIX is similar to doing so in Windows, but you use a

/ instead of a \. Using the same example just shown for Windows, from the root directory run cd /obiwan. To go to the /Obiwan/my/hope directory, run cd /Obiwan/my/hope.

NOTE   On UNIXes it is considered bad manners to create files and folders in the root (/) directory. In fact, you need "root" permissions to do such a thing. This is because of Linux's history as a multiuser system. Such restrictions keep users from inconveniencing everyone by breaking the underlying OS.

So far, the examples in this section all start with a slash (indicating the root directory). These absolute paths list the entire path from the root directory to the target directory. Absolute paths are great when you know exactly where you're going, but relative paths (those without a leading slash) come in handy when you need to browse.

When you run cd obiwan without the leading slash, it will look for a subdirectory of the current working directory. For example, you could go to the C:\Obiwan directory from the root directory simply by typing cd obiwan at the C:\> prompt. You can then move one level at a time, like this:

C:\>cd obiwan

C:\Obiwan>cd my

C:\Obiwan\my>cd hope

You can also jump multiple directory levels in one step, like this:

C:\>cd obiwan\my\hope

C:\Obiwan\my\hope>

These tricks also work for UNIX, but of course you always use a forward slash instead of a backslash as needed:

mike@server:~$ cd obiwan

mike@server:~/Obiwan$

A final trick: run cd .. to move the focus up a single directory level (cd ../.. would move it up two levels):

C:\Obiwan\my>cd ..

C:\Obiwan>

Take some time to experiment moving the prompt focus around the directories of your PC, using the cd and dir commands. Use dir to find a directory, and then use cd to move the focus to that directory. Remember, cd \ (or cd / in any UNIX) always gets you back to the root directory.

Moving Between Drives

Because Windows has drive letters and the UNIXes do not, they have very different techniques for moving between drives. Let's start with Windows and then we'll take a look at the UNIX-likes.

Moving Between Drives in Windows

The cd command is not used to move between Windows' drive letters. To focus the prompt on another drive, just type the drive letter and a colon---and then press ENTER just like it is a command. If you need to go find some files on your handy-dandy USB thumb drive (E:), just run e: and the prompt will focus on the USB drive:

C:\Users\mike>e:

E:\>

Run c: to return to the C: drive (note that it restored the same focus I had before changing drives):

E:\>c:

C:\Users\mike>

Just for fun, try typing in a drive letter that you know doesn't exist on your system. For example, I know that my system doesn't have a W: drive. If I type in a nonexistent drive on a Windows system, I get the following error:

The system cannot find the drive specified.

Try inserting an optical disc or a thumb drive and entering its drive letter to focus on its drive. Run dir to see the contents of the removable media and run cd to explore any folders it contains. Now return focus to the C: drive.

Using the dir, cd, and drive letter commands, you can access any folder on any storage device on your system. Make sure you are comfortable navigating with them.

Moving Between Drives in macOS and Linux

So if UNIXes don't use drive letters, how do you access your other drive partitions, optical media, thumb drives, and so on? Well, all media is mounted as a folder within a single hierarchy (but the location of those folders varies). In macOS, look in the /Volumes folder. In Ubuntu Linux, look in the /mnt folder for drives and the /media/<user name> folder for removable media. In other Linux distributions, well, you're going to have to explore---good thing you know how to use cd and ls, eh? The following commands show my optical drive and a thumb drive in an Ubuntu Linux system:

mike@server:/media/mike$ ls -l

drwx------ 3 mike mike 4096 Dec 31 1969 THUMBDRIVE

dr-xr-xr-x 6 mike mike 2048 May 13 10:15 Age of Empires

mike@server:/media/mike$

Making Directories: The md/mkdir Command

Now that you have learned how to navigate in a command-prompt world, it's time to make stuff---starting with a new directory to practice in. Run cd \Users\<your username> if your prompt isn't already focused on your home directory (or cd ~ on a UNIX).

To make a directory, use the md command in Windows. Alternatively, you can use the mkdir command, which works in all operating systems. Run md practice to create a practice directory:

C:\Users\mike>md practice

Windows executes the command but doesn't volunteer any information about what it did. Run dir to confirm that you have, in fact, created a new directory:

Note that that, unlike the other directory names, the name of our practice directory shows up in all lowercase. Windows displays both cases in file and folder names but rarely makes any distinction with commands---which is a nice way to say Windows doesn't support case. Try running md Practice to see what happens. This also happens in the Windows GUI---go to your desktop and try to make two folders, one called files and the other called FILES, and see what Windows tells you.

To create a files subdirectory in the practice directory, first run cd practice to focus on the practice directory:

C:Users\mike>cd practice

Then run md files to make a files directory:

C:Users\mike\practice>md files

NOTE   Ensure the prompt points to the directory you want to contain the new subdirectory before you execute the md command.

When you're finished, run dir to see the new files subdirectory. Just for fun, try the process again and add a games directory under the practice directory. Run dir to verify success.

Creating folders in a UNIX-like OS is again identical, but you must use the mkdir command. Here is the same example just given but done on my Ubuntu system:

mike@server:~$ mkdir practice

You can see the results by running the ls command:

mike@server:~$ls

practice

Don't forget that Linux is case sensitive. It will happily let you make folders for bills, BILLS, BiLLS, and so on.

Removing Directories: The rd/rmdir Command

Removing subdirectories works exactly like making them. First, get to the directory that contains the subdirectory you want to delete, and then execute either the rmdir or rd command. The rmdir command works equally well in Windows, macOS, and Linux, but the rd command only works in Windows.

NOTE   If you don't mind the extra typing, you can also use absolute paths to work with files without first navigating with cd.

Let's get rid of some folders! This time I'll use Linux as the example while we delete the files subdirectory in our ~/practice directory (remember ~ means your home directory). First, run cd ~/practice to navigate to where the files subdirectory is located. Then run rmdir files. If you received no response, you probably did it right! Run ls to confirm the files subdirectory is gone. Windows works the same, although we tend to use the shorter rd command.

Next, we'll remove the whole practice directory. Run cd .. to navigate back to your home directory and then run rmdir practice to remove it:

mike@server:~$ rmdir practice

rmdir: failed to remove 'practice': Directory not empty

There's a big, fat asterisk here---these commands won't just delete a directory that contains files or subdirectories. They'll complain like rmdir did here or ask you for confirmation (as it does in PowerShell). The message may look annoying, but the commands are being helpful! It's easy to delete more than you intended, and there is no Recycle Bin when deleting from the command line, so this speedbump gives you a chance to think twice about what you mean. Always follow the maxim "Check twice and delete once."

To remove a folder and all of its contents in Linux, we turn to the very handy rm command. (More on rm a little later in the chapter---see "Deleting Files.") Just run rm with the -r (recursive) switch as shown:

mike@server:~$ rm -r practice

Windows folks can use the rd command followed by the /s switch to delete a directory as well as all files and subdirectories:

C:\Users\mike>rd practice /s

practice, Are you sure (Y/N)?

Pressing the y key eliminates both C:\Users\mike\practice and C:\Users\mike\practice\games.

EXAM TIP   Make sure you know how to use md, mkdir, rd, rmdir, rm, and cd for the CompTIA A+ 220-1102 exam.

Running a Program in Windows

To run most programs from the Windows command line, simply type the name of the program and then press ENTER. Remember MMC from the previous chapter? To run the mmc.exe program, just run the filename, in this case mmc (see Figure 15-7). Note that you do not have to type the .exe extension, although you can. Congratulations! You have just run another application from the command line.

Figure 15-7  Running mmc in Windows

NOTE   Windows includes a lot of command-line tools for specific jobs such as starting and stopping services, viewing computers on a network, converting hard drive file systems, and more. This book discusses these task-specific tools in the chapters that reflect their task. Chapter 19 goes into detail on the versatile and powerful net command, for example.

Running a Program in macOS and Linux

As much as I like to tell folks how similar UNIX and Windows command lines are, one place they differ is what counts as a program. For starters, executable programs on UNIXes don't need a special extension such as .exe. You can give the execute permission to any file---whether it's compiled code or a text file---as shown in Figure 15-8.

Figure 15-8  Showing file properties in Ubuntu

Since any file could be an executable, UNIX shells add an extra wrinkle to protect you from running the wrong thing. Here's what happens if I download some file named "executable" to my home directory and try to run executable:

mike@server:~$ executable

executable: command not found

Even though the file is in the exact folder I am trying to run it from, the shell won't "find" it. When we run a command like this, the shell looks through a series of folders called the PATH (not to be confused with the other type of path discussed earlier) and takes the first one it finds. You can see the path by running echo $PATH:

mike@server:~/$ echo $PATH

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/

local/games

As you can see, my home directory isn't in this list. If I want the shell to run an executable that isn't in one of these directories (on my PATH, as we say), I have to be more specific. To run an executable in my working directory, I have to prefix it with "./" (the . is shorthand for the working directory):

mike@server:~$ ./executable

-bash: ./executable: Permission denied

Oops! This can be a surprise if you don't expect it. Remember: since execute is a file permission, you'll get a permission error if you try to run something that isn't marked executable. Don't get the wrong idea, though---just because you can mark anything as executable doesn't mean you can execute anything. For example, here's what happens when I mark an image file as executable and then try to run it:

mike@server:~$ ./image.png

-bash: ./image.png: cannot execute binary file: Exec format error

In reality, this means it's up to you to verify you are even trying to use a program. You cannot just start programs haphazardly in macOS or Linux. You make a point to know your executable before you run it.

Investigating Files

UNIXes also very often include an incredibly helpful command when it comes to identifying random, untrusted files: the file command. (And if they don't come with it, you can always install it.) For example, here's what the file command has to say about a PNG image file and the ls command on both macOS and Linux (in that order):

./image.png: PNG image data, 64 x 64, 8-bit/color RGBA, non-interlaced

/bin/ls: Mach-O 64-bit executable x86_64

/bin/ls: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically

linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID

[sha1]=a65f86cd6394e8f583c14d786d13b3bcbe051b87, stripped

Even though I marked this image as executable, the file command isn't fooled!

Working with Files

This section deals with basic file manipulation. You will learn how to inspect, copy, move, rename, and delete files. The examples in this section are based on a C: root directory with the following files and directories:

Because you probably don't have a PC with these files and directories, follow the examples but use what's on your drive. In other words, create your own folders and copy files to them from various folders currently on your system.

Reading Plaintext Files

Most files on your computer are in file formats that aren't very accessible to humans without special tools. If you want to view or edit a picture, you'll need a program that understands image file formats. But many programs and operating systems (especially the UNIX-like ones) have plaintext files that contain configurable options or documentation. You can open these files in Notepad or another GUI editor, but it's often faster to read them directly from the command line!

The simple way to read a file is to run a command that will write the file's contents to your terminal in one go. This doesn't help much with long files, but it's fine for short ones. On any UNIX, you can use the cat command to write out the contents of one or more files. No, it isn't named for the furry household predator! It's short for concatenate---to join things together. When you run cat with more than one filename, it writes out all the files joined into one long stream.

EXAM TIP   Forgive me for withholding something to avoid confusion. The CompTIA A+ 1102 objectives list just one command for reading files: cat. It's available in UNIX and even PowerShell---but the objectives just list it as a Linux command. I'm leaving out the Windows Command Prompt equivalent. It isn't in the objectives, and it has the same name as a UNIX command we've discussed. Focus on cat for the exam!

Now that I've shown you the simple way to read a file, I want to show you the easy way: just run more followed by the name or path of the file. The more command is a simple pager (remember, a pager is an interactive reader) that advances one line when you press ENTER and one page when you press SPACEBAR. To exit, just scroll to the end of the file or press Q. It's usually present in UNIX and Windows in both Command Prompt and PowerShell.

NOTE   There's an even better pager than more. The less command is an advanced pager that can navigate both forward and backward in the file (with your arrow keys, scroll wheel, trackpad, etc.) and recognizes gobs of keyboard shortcuts for jumping around in a file, searching its contents, and so on. As they say, less is...more!

Using Wildcards to Locate Files

Imagine having 273 files in one directory. A few of these files have the extension .docx, but most do not. You are looking only for files with the .docx extension. Instead of flipping through pages of irrelevant files, you can use wildcards to list just the ones you want.

A wildcard is one of two special characters---asterisk (*) and question mark (?)---that you can use in place of all or part of a filename, often so that a command-line command will act on more than one file at a time. Wildcards work with all command-line commands that take filenames.

NOTE   I'm glossing over a big, geeky difference between Windows and UNIX here. Windows shells don't expand wildcards (convert them into a list of matching files)---they leave it up to each command. UNIX shells generally expand the wildcards (unless quoted) and pass the list of matching files to the command. You can run echo * and echo "*" on both systems to see the difference.

Most (but not all) Windows commands that work with files will support wildcards. Relatively few UNIX commands directly support wildcards---most rely on the shell to do it for them (a well-known exception is the find command, which comes up later in the chapter). Just file this away in the back of your mind and pull it out any time you're confused as heck about how some wildcard is (or isn't) working.

A great example is the dir command. When you execute a plain dir command, it finds and displays all the files and folders in the specified directory; however, you can also narrow its search by adding a filename. For example, if you run dir ailog.txt while in your root (C:\) directory, you get the following result:

But what if you want to see all files with the extension .txt? You can use the * wildcard, which matches any number of characters (the ? wildcard, by contrast, matches any single character). Run dir *.txt to see something like this:

Wildcards also substitute for parts of filenames. This dir command will list files that start with the letter a:

Wildcards in UNIX shells work basically the same as in Windows. Head over to the /usr/sbin directory on a typical UNIX system and try using a wildcard with the ls command. Here's what comes up when I run ls z* -l on my Linux system:

mike@server:/usr/sbin$ ls z* -l

-rwxr-xr-x 1 root root  63784 Dec 16  2023 /usr/sbin/zic

-rwxr-xr-x 1 root root 117088 Jul 21  2023 /usr/sbin/zramctl

We've used wildcards only with the dir and ls commands in the previous examples, but virtually every command that deals with files and folders will take wildcards. Let's examine some more commands and see how they use wildcards.

SIM   Check out the four "Wildcard" sims in the Chapter 15 section of https://www.totalsem.com/110X. The two Type! sims plus the Show! and the Click! will prepare you for any number of performance-based questions CompTIA throws at you in the 1102 exam.

Deleting Files

To delete files, you use the del (or erase) command in Windows and the rm command in UNIXes. Deleting a file in the GUI gives you the luxury of retrieving accidentally deleted files from the Recycle Bin. The command line, however, shows no mercy to the careless. If you accidentally erase a file, don't expect to get it back without restoring it from a backup. Again, the rule here is to check twice and delete once.

To delete one file in Windows, use the del command followed by the filename. For example, to delete the file reportdraft1.docx, run

del reportdraft1.docx

In UNIX, use rm in place of del:

rm reportdraft1.docx

Nothing appears on the screen, but you can run dir or ls to confirm it's gone.

You can use wildcards with the del and rm commands to delete multiple files at once. For example, to delete all files with the extension .txt in a folder, you can run this in any UNIX:

rm *.txt

You can place the wildcard anywhere in the name. If you exported reportdraft1 in multiple formats, you could run del reportdraft1.* to delete them all.

Copying and Moving Files

Being able to copy and move files from the command line is crucial to all technicians. Because of its finicky nature and many options, the copy command is also rather painful to learn, especially if you're used to dragging icons around a GUI. The following tried-and-true, five-step process makes it easier, but the real secret is to get in front of a prompt and just copy and move files around until you're comfortable. Keep in mind that the only difference between copying and moving is whether the original is left behind (copy) or not (move). Once you've learned the copy command, you've also learned the move command! In UNIXes, the copy command is cp and the move command is mv.

Mike's Five-Step copy/move Process

There's about 10,000 different ways to copy and move files. To make learners' lives easier, I've been teaching folks how to copy and move files for years with this handy five-step process. As you grow more confident, don't be afraid to try your own methods in the operating system of your choice to learn the full power of the commands. But first, follow this process step by step:

1\.   Focus the prompt on the directory containing the file(s) you want to copy or move.

2\.   Type copy or move (Windows) or cp or mv (macOS and Linux) and a space.

3\.   Type the name(s) of the file(s) to be copied/moved (with or without wildcards) and a space.

4\.   Type the path of the new location for the file(s).

5\.   Press ENTER.

Let's try an example using Windows. The directory Jedi (in my \Users folder) contains the file notes.txt. Copy this file to a USB thumb drive (E:).

1\.   Type cd Jedi to focus the prompt on the Jedi directory.

C:\Users\mike>cd Jedi

2\.   Type copy and a space.

C:\Users\mike\Jedi>copy

3\.   Type notes.txt and a space.

C:\Users\mike\Jedi>copy notes.txt

4\.   Type e:\.

C:\Users\mike\Jedi>copy notes.txt e:

5\.   Press ENTER.

The entire command and response would look like this:

C:\Users\mike\Jedi>copy notes.txt e:

1 file(s) copied

You can focus the prompt on the E: drive and run dir to confirm the notes.txt file is there. Let's try another example, this time in macOS or Linux. Suppose 100 files are in the ~/Jedi directory, 30 of which have the .odf extension, and suppose you want to move those files to ~/Screenplays/sw2024. Follow these steps:

1\.   Type cd Jedi to focus the prompt on the correct folder.

mike@server:~$ cd Jedi

2\.   Type mv and a space.

mike@server:~/Jedi$ mv

3\.   Type *.odf and a space.

mike@server:~/Jedi$ mv *.odf

4\.   Type ~/Screenplays/sw2024/.

mike@server:~/Jedi$ mv *.odf ~/Screenplays/sw2024/

5\.   Press ENTER.

mike@server:~/Jedi$

This won't give you any feedback at all unless you use special switches. You can confirm the move with ls.

Pruning and Grafting Folder Trees

There's a number of situations where you find yourself wanting to grab a folder, complete with all of the subfolders and any files that might be anywhere in any of the folders, and copy or move the whole "pile" in one command. We call this process pruning and grafting and it's a place where the command line shines in comparison to GUI file manipulation. Done properly, command-line pruning and grafting is faster and gives you much finer control of the process.

In Windows, the standard copy and move commands can work only in one directory at a time, making them a poor choice for copying or moving files in multiple directories. To help with these multi-directory jobs, Microsoft added the xcopy command. (Note that there is no xmove, only xcopy.) We'll also look at robocopy, cp, and mv.

xcopy

The xcopy command functions similarly to copy, but xcopy has extra switches that give it the power to work with multiple directories. Here's how it does that. Let's say I have a directory called Logs in the root of my C: drive. The Logs directory has three subdirectories: Jan, Feb, and Mar. All of these directories, including the Logs directory, contain about 50 files. If I wanted to copy all of these files to my E: drive in one command, I would use xcopy in the following manner:

xcopy c:\Logs e:\Logs /s

Because xcopy works on directories, you don't have to use filenames as you would in copy, although xcopy certainly accepts filenames and wildcards. The /s switch tells xcopy to copy all subdirectories that aren't empty. The /e switch tells xcopy to copy empty subdirectories. When you have a lot of copying to do over many directories, xcopy is the tool to use.

robocopy

Microsoft introduced the robocopy command---short for Robust File Copy---many years ago as an add-on tool for Windows Server to enable techs to manage files and folders more quickly and efficiently than with xcopy or copy. The robocopy command enables you to, for example, copy the files and folders from one computer to another across a network, fully replicating the structure on the destination system and deleting anything on that system that wasn't part of the copy.

The robocopy syntax does not resemble xcopy---don't get them mixed up! Here's the basic syntax:

robocopy [source] [destination] [options]

Here's an example of the command in action. The following command would copy all files and subfolders from a local machine's D:\testserver\website folder to a shared folder on the remote server \\liveserver\website:

robocopy d:\testserver\website \\liveserver\website /mir

The /mir (mirror) switch tells robocopy to copy everything from the source and make the destination mirror it. That means robocopy will delete anything in the destination that doesn't match the source folders and files.

That's not even the tip of the robocopy iceberg! It can copy encrypted files. It enables an administrator to copy files even if the administrator account is expressly denied access to those files. It will also resume copying after an interruption at the spot it stopped. For the full syntax, run

robocopy /?

Their power and utility make the del, copy/move, xcopy, and robocopy commands indispensable for a PC technician, but that same power and utility can cause disaster. Only a trained Jedi, with The Force as his ally . . . well, wrong book, but the principle remains: Beware of the quick and easy keystroke, for it may spell your doom. Think twice and execute the command once. The data you save may be yours!

EXAM TIP   Know xcopy and robocopy for the CompTIA A+ 220-1102 exam.

cp and mv (again!)

If you really want to see some powerful commands, let's head over to Linux. Unlike Windows, you can both move and copy folders and their contents, using the same cp and mv commands we saw earlier for regular copying and moving. Let's say I have a folder called /home/mike/Backups. The Backups folder has ten subfolders and hundreds of files. I want to save a copy of these files to a folder called /mnt/storage. To do this I only need to run cp with the -R (recursive) switch (remember that the ~ in my prompt shows that the working directory is my home folder):

mike@server:~$ cp -R Backups /mnt/storage

If I want to move all of that to storage instead of copy, I use the mv command. Interestingly, the mv command doesn't even need a special switch---just run it with the folder to move and the destination:

mike@server:~$ mv Desktop/Backups /mnt/storage

Assorted Windows Commands

As a proficient IT technician in the field, you need to be familiar with a whole slew of command-line tools and other important utilities. The CompTIA A+ 220-1102 exam focuses in on several of them, and although many have been discussed in detail in previous chapters, it is extremely important that you understand and practice with chkdsk, format, hostname, gpupdate, gpresult, sfc, shutdown, and winver.

chkdsk (/f /r)

The chkdsk (checkdisk) command scans, detects, and repairs file system issues and errors. You can run the chkdsk utility from a command line with the switches /f and /r. The /f switch attempts to fix file system--related errors, while the /r switch attempts to locate and repair bad sectors. To run successfully, chkdsk needs direct access to a drive. In other words, the drive needs to be "unlocked." For example, if you run chkdsk /f /r and chkdsk does not consider your drive unlocked, you will receive a "Cannot lock current drive" message, meaning that another process has the drive locked and is preventing chkdsk from locking the drive itself. After this, chkdsk presents you with the option to run it the next time the system restarts (see Figure 15-9).

Figure 15-9  The chkdsk /f /r utility and switches on a locked drive

format

After the previous chapters, you should have an expert-level knowledge of (or, at the very least, a passing familiarity with) formatting and partitioning hard drives. Formatting, you may remember, is the process of writing a new file system to a volume (or partition, if you're old school) so it can hold an operating system or data. We have already discussed the various built-in Windows utilities available to provide the formatting of drives, and you no doubt know that many third-party formatting tools are out there. In this chapter, you just need to become familiar with the format command and its switches.

The format command, you may have guessed, enables you to format volumes from the command line. Figure 15-10 shows an example of the format command in action. Note the complex switches that let me specify which file system to use, which volume, that I want compression, and so on. The very best way to familiarize yourself with the format command and its available switches is to run format /? from the command line.

Figure 15-10  The format command in action

The CompTIA A+ 220-1102 exam focuses on both GUI and command-line operating system formatting utilities and options, so you should familiarize yourself with the format command and its switches by practicing them on a test system you are literally not afraid to wipe out. Besides, you never know what antiques CompTIA may dust off.

hostname

The hostname command is the most straightforward of all command-line commands. If you run hostname, it will display the name of your computer, also known as the hostname. When I run it, it displays "MikesPC."

winver

There's one really odd duck in the list of Windows "commands" in the 1102 objectives: winver. I personally disagree that it's even a command! When you run winver, it opens a GUI information panel that displays some version information about Windows. I guess you might do this if you're already working in the CLI, but you could also just use the Start menu to search for winver and launch it directly.

EXAM TIP   The 1102 objectives might be confusing winver with the older ver command (which is an actual Command Prompt builtin). If you're running Command Prompt, ver will write a Windows version number to your terminal. Keep winver in mind if you see a question about checking the Windows version from the command line.

gpupdate

Group policies define various security settings for Windows systems, such as password complexity, logon attempts, and permissions for users to install software. Group policies can apply to a standalone system or to systems on a domain. It takes time for a group policy change to propagate throughout a domain, but you can force a workstation to update to new policies by running gpupdate on the workstation. Here is an example of gpupdate in action:

Check out Chapter 27 to see exactly what gpudate is doing.

gpresult

If you need a quick overview of all security policies applied to a single user or computer, the gpresult tool is for you. You can run gpresult for any user or computer on your network (assuming you have a valid username and password) and you can ask for detailed or summary information. This command shows the summary results for user michaelm on the local computer:

sfc

The Windows sfc (System File Checker) command scans, detects, and restores important Windows system files, folders, and paths. Techs often turn to sfc when Windows isn't quite working correctly and use it to find and fix critical Windows system files that have become corrupt. If you run sfc and it finds issues, it attempts to replace corrupted or missing files from cached DLLs (backups of those system files) located in the Windows\System32\Dllcache\ directory. Without getting very deep into the mad science involved, just know that you can use sfc to correct corruption. To start sfc from a command line, run sfc /scannow. To familiarize yourself with sfc's switches, run sfc /? (see Figure 15-11).

Figure 15-11  Checking sfc options with sfc /? at a command line

shutdown

The shutdown command enables you to do exactly that to a local or remote computer---shut it down (or reboot it). The cool part of the tool is that you can use a number of switches to control and report the shutdown. A network administrator could use this tool to restart a computer remotely, for example, like this:

shutdown /r /m \\devserver

The /r switch tells shutdown to have the computer reboot rather than just shut down. If you want to see the full syntax for shutdown, run the following:

shutdown /?

Keyboard Shortcuts

You might find yourself repeatedly typing the same commands, or at least very similar commands, when working with a CLI. Microsoft provides several ways to access previous commands. First, run dir from the command line. Next, press F1, and the letter d appears. Press F1 again. Now the letter i appears after the d. Do you see what is happening? The F1 key rebuilds the previous command one letter at a time. Pressing F3 rebuilds the entire command at once. Now try running these three commands:

dir /w

hostname

md Skywalker

Now press the UP ARROW key. Keep pressing it till you see your original dir command---it's a history of all your old commands. Now use the RIGHT ARROW key to add /w to the end of your dir command. Windows command history is very handy.

UNIX shells come with their own shortcuts, some of which match those in Windows. (Actually, Windows copied many of the handier shortcuts, like the history feature, from the UNIX world.) UNIXes take command history one step further and can (depending on configuration) remember it even if you close the terminal or reboot the machine. For example, you can search your history with the CTRL-R combination. This can pay for itself if you have to figure out a long, complex command one day and need to use it again two weeks later!

Assorted macOS and Linux Commands

macOS and Linux generally come with a big pile of preinstalled command-line utilities---and you can install thousands and thousands more. Even if we're just talking about Linux, the list of preinstalled commands can vary widely from distro to distro. In fact, one of the most interesting challenges to learning the CLI is that for almost any task, there is more than one tool for the job (see the nano and vi commands, later). What you are going to see here are the commands listed by the CompTIA A+ objectives---you could spend the rest of your life learning CLI commands!

See Running Processes: top and ps

The 1102 objectives cover two commands you can use to see the processes running on your system, so you'll need to know what each one does, and how they differ. The (very old) ps command provides detailed and customizable information about the processes running on your system at the moment you run the command. The top command is an interactive, continuously updating monitor of what's running---and by default it focuses on resource-hungry processes. Generally, use top to monitor or investigate system performance, and use ps to look for specific processes.

top

When you just run top by itself, you get the default settings: the screen divided with the top portion showing system and resource information and the lower portion showing running processes. Figure 15-12 shows that the defaults can differ between systems.

Figure 15-12  top running on Linux (above) and macOS (below)

Once you start top, you use your keyboard to control it. Different versions of top have different options, so the first thing to try is to press ? for information about all of the interactive options. You can press Q to close this help view, and press Q from the main resource view to close top entirely.

NOTE   You need to know top for the 1102 exam, but there's room for more than one resource monitor in your life! Not only are there improved versions of top, such as htop and ytop, but you can also find top-like tools for detailed monitoring of things like storage, graphics, or network performance---and much more. Explore!

ps

The ps command is so old that it has two totally different types of switch sets! If you just run ps by itself, it won't list much. We would have to get very deep in the weeds

to understand exactly why---so instead we'll run one of the most common examples of ps: ps aux. The "aux" bit here is actually three separate switches (using the older legacy switch set): a = processes for all users, u = show process owner, and x = process not attached to a terminal.

Note that ps aux usually writes out a ton of lines. I'm going to cut most of them out for space, but before we look at any more, let's discuss what these columns actually mean:

-   USER: Who is running this process

-   PID: The process ID number assigned to the process

-   %CPU: What percentage of CPU power this process is using

-   %MEM: What percentage of memory this process is using

-   VSZ: Total paged memory in kilobytes

-   RSS: Total physical memory in kilobytes

-   TTY: The terminal that is taking the process's output

-   STAT: S = waiting, R = running, l = multithreaded, + = foreground process

-   START: When the process was started

-   TIME: Length of time process has been running

-   COMMAND: Name of the executable that created this process

Now for a few more lines of output:

EXAM TIP   For mysterious reasons, the CompTIA 1102 exam objectives ignore both the UNIX kill command (used for killing processes) and the Windows equivalent, taskkill. In my experience, the most common reason to run ps is to find the PID of a process I want to kill! Keep ps in mind if a question mentions looking up information about specific processes on Linux or macOS.

A big problem with ps aux is the enormous output I mentioned. There are a number of ways to make dealing with this output easier (including different commands), but the most common is to pipe its output into a pager (like less, or more) for reading, or pipe it into a filter such as grep, which we'll discuss next.

grep

The grep command is a filter: it enables you to search through text files or command output to find specific information and filter out the rest. For example, finding a specific process is easy if you combine grep with the ps command. Let's say LibreOffice froze while opening a document and I need to kill it. I have no idea what the PID is, but I can use grep with ps to find it. I know the command uses the word "libre," so I type

So I see there are two processes from LibreOffice: 2524 and 2543. Cool! The grep command can find any string of text and show you the line it was in. This is only a light overview of one of the most powerful tools in UNIX. If you need to look in anything to find a string of text, grep is a good place to start.

find

Another big workhorse on UNIX is the find command, which can plow through all of the files and folders in a directory (and all of its subdirectories) and output a list containing only the ones that match some criteria of your choosing. When I say criteria, the following are some good examples:

-   Its file is bigger than, smaller than, or exactly some size.

-   It was created or modified before, on, or after some date (or some number of seconds/minutes/hours/days ago).

-   It has (or doesn't have) certain permissions.

-   Its name does (or doesn't) match a pattern.

If you just run find all by itself, find will plow through all of the files in your current working directory without using any criteria at all---it'll list all of them! Give it a try (though it will output a lot if you are in a big directory). If that doesn't output much, run find /etc/ to get the same effect on a specific directory.

This isn't very useful on its own, so let's try out some criteria. Imagine you are asked to collect and archive all PDF documents in any user's home directory on a Linux laptop, wipe the device, and reinstall the OS. One of the find command's many options is perfect for this job: the -iname option adds a case-insensitive name criteria that can use a wildcard pattern. Here's how this search looks on my system (though I'm just including a few matches):

This searches each user's home directory within the /home/ directory, and prints out every file that ends with the .pdf extension (regardless of case---including .PDF, .Pdf, and so on). Fair warning: if you don't have permission to read all of the user directories on your system, find will emit a permission error for each one it can't search.

NOTE   find is one of the UNIX commands that has built-in support for wildcards. Remember: You need to quote "*.pdf" to keep your shell from expanding the wildcard before it reaches the find command. If you fail to quote it, you'll almost certainly end up with an error message or the wrong results.

Package Managers: apt-get and yum

The CompTIA A+ 1102 objectives don't have much to say about what is, to my mind, one of the most revolutionary concepts to come out of the whole spectrum of UNIX-like operating systems: package managers. The objectives do, however, mention two commands that are at least related to package management---and that's all the invitation I need!

Back in ye olde days, installing software on UNIX could be a lot like walking to school in the snow, uphill both ways! If you needed an application, you often had to dig around for the source code and try to compile it on your system. Sometimes this worked on the first try, and other times you'd just discover that it depended on yet more code that you had to find, then manually set up configuration files . . . ugh!

Over the years many improvements have been made to the availability, acquisition, and installation of UNIX software, culminating in tools called package managers that empower you to install and update software---including the other software it depends on---with a few commands.

NOTE   The commands in the 1102 objectives (apt-get and yum) are associated with the official system package managers for two major branches of the Linux family tree. They aren't the only game in town, though! In fact, package managers are so useful that the concept has even made the leap to Windows. Go ask the Internet about a few of my favorites: Chocolatey, Scoop, and winget (Windows); Homebrew (macOS and Linux); and Nix (macOS and Linux).

apt-get/APT

For Linux distros in the Debian family tree (like Ubuntu and Mint), we use APT, the advanced packaging tool. The apt-get command enables you to manage (install, uninstall, update, and so on) APT packages---assuming you know the name of the program you wish to install. Many Linux users prefer monitoring systems with something a little flashier than the original top program, such as htop. To download and install the latter program, start by running the following:

mike@server:~$ sudo apt-get update

Have APT update its package index, the list of all the available packages (software). You can technically skip this step, but you might end up installing an old version or, if the package is new enough, not finding it. Once APT's index has been updated, run this next:

mike@server:~$ sudo apt-get install htop

That's it! Got htop already installed but want the newest version? No problem! Just use apt-get again:

mike@server:~$ sudo apt-get upgrade htop

The only downside to apt-get is that you need to know the name of the package you want to install. While there are command-line tools that help (apt-cache), many people prefer to use the graphical search tool their Linux distro provides, such as the Ubuntu Software Center.

As useful as APT is for fetching and installing single applications, that's not where its real power lies. System package managers can manage all the software (minus anything you compiled yourself) on the system; they are what you use to keep the whole system up to date, just as Windows Update handles much of the software on Windows. All that it takes to upgrade all the packages on your system is to run

mike@server:~$ sudo apt-get update

mike@server:~$ sudo apt-get upgrade

If apt-get finds any out-of-date packages, it will let you know which ones and ask you to confirm the upgrade, then away it goes to download and update your system. Keeping your system up to date in this way is critical to close any security vulnerabilities that might be lurking on your system.

yum/RPM

For Red Hat--based systems (such as Fedora and CentOS), we use Red Hat Package Manager (RPM). As with APT, there's a convenient command line you can use to manage RPM packages: the yum command. There a lot of little differences between these package managers and the commands for working with them, but the essentials are virtually the same as with apt-get. Here are the commands we used to install htop, but for yum:

mike@server:~$ sudo yum update

mike@server:~$ sudo yum install htop

NOTE   There are multiple ways to use both APT and RPM. I've stuck to apt-get and yum here to avoid confusing you with alternatives before the exam. If you spend much time working with Linux, look into the alternatives later!

nano

You will sometimes need to edit raw text files in UNIX, and it's good to know you can do it from the command line (especially if you don't have access to a full GUI). The family tree of command-line editors is big, with a long history and heated arguments about which one is best.

The previous iteration of the CompTIA A+ exam objectives (220-1002) focused on a fairly ubiquitous editor, vi, which you'll find bundled in some form or another with most UNIXes. Figuring out how to edit a file (or even just exit) with vi in some ways is a rite of passage. Only after you have mastered vi's nonintuitive and perhaps even downright weird interface can you truly start to think of yourself as a UNIX Terminal Jedi master.

Luckily for you (unless you already happen to know vi, or have strong opinions about CLI text editors), the current CompTIA A+ 1102 objectives now focus on an easier-to-learn editor: GNU nano. You'll still find nano on most UNIXes, but it is a little less common than vi---tuck the name vi away in your pocket in case you need to edit a file on a system without nano! Let's get started with nano by creating a new text file called "fred" (the same command will also edit an existing file):

mike@server:~$ nano fred

You'll now be in the nano text editor, staring at a blank file, as shown in Figure 15-13. The big thing to notice here is at the bottom of the screen, where nano lists a few important keyboard shortcuts (each prefixed with ^ to indicate that you should press CTRL and the indicated key simultaneously). The most important ones are in the bottom-left corner: Get Help, and Exit. Press CTRL + G once to access the help menu, and CTRL + X once to return to the edit view.

Figure 15-13  nano open

To make basic edits in nano, all you need to do is move your cursor around with your keyboard and type or delete as needed. Enter a few lines of text, such as shown in Figure 15-14, press ENTER at the end of each line, and use the backspace key if you make an error.

Figure 15-14  nano with text

To save your new file and quit nano, press CTRL + X. If you exit with unsaved changes (a "modified buffer"), nano will prompt you to save them, discard them, or cancel and return to the editor. Just press Y to save the changes. It's important to know how to use a common editor such as nano or vi, but for day-to-day work most UNIX people usually reach for one of the hundreds of alternatives. Check out other terminal-based editors such as vim, joe, or emacs, and graphical editors such as gedit or gVim.

dd

The dd command is primarily used to create an exact, bit-by-bit image of any form of block storage, meaning mass storage devices such as hard drive volumes, thumb drives, and optical media. In its most simple form, the dd command is just

$ dd if=<source block device> of=<destination image file location>

There's no way to show you all the possible uses for dd, so I'll just show three of the typical places I use it. Let's start with something simple: copying a hard drive.

Be careful here---some people joke that dd stands for "Disk Destroyer" for a reason! This powerful tool will wreak havoc on your data if not used correctly. There are a number of issues that I'm not covering here that could greatly affect the success of running the dd command. While all of the following commands are valid, simply running them on your systems without understanding these subtleties can wipe drives. You have been warned!

Copying a Hard Drive

Let's say you have a hard drive (sda) you want to copy onto another hard drive (sdb). In this case we will say they are exactly the same size. The following command will copy the entire sda drive, partition table, file systems . . . everything to the sdb drive:

dd if=/dev/sda of=/dev/sdb

Backing Up a Thumb Drive

Let's say you have thumb drive full of important files you really want to back up. Using dd as follows, you can copy the entire USB drive and make an image file (I chose to call it thumbBackup.bak) and place that image file on your Desktop:

dd if=/dev/sdc of=/home/mike/Desktop/thumbBackup.bak

Wiping a Disk

I have a drive (sdb) that I want to totally wipe. The dd command can take input from anywhere, but in this case I'll use Linux's random number generator, /dev/urandom, to write a stream of random bits completely over the entire drive. It's not a perfect wipe, but it will stop all but the most sophisticated tools.

dd if=/dev/urandom of=/dev/sdb

df

The df (display free disk space) command makes it easy to diagnose the most common storage-space issues on UNIX systems. You can just run df by itself, but I always run df -h (the -h switch uses human-friendly units):

One quick command is all I need to know that the primary volume (mounted at the root directory /) is about 83% full.

shutdown

In Windows, you can shut down or restart the system from a terminal using the shutdown command. Run the command as follows:

shutdown <options> <time>

By far the most common time is now. To shut down the system immediately, run

shutdown now

To restart the system, run shutdown with the -r option:

shutdown -r now

Scripting

Up until now, we've entered commands into the CLI one by one. Most of the time all you need is one or two commands, but sometimes you will find yourself running the same series of commands to perform a task over and over. When you find yourself in this situation, it might be a good idea to write a script---a small program that helps automate a task by collecting a series of commands and giving them a name.

Early in the chapter---when we looked at shells---I pointed out that a shell is the command-line interpreter that interprets the commands you run. It's time to let you in on a secret. Shells can also execute a text file by interpreting each line as if it were a command you typed and ran. We call these text files shell scripts. Each command shell has its own shell scripting language---and all of the commands I've shown you so far use a little slice of it.

The rest of each shell's scripting language is for controlling when and how the shell runs the commands in a script---but you can make a super simple shell script by just copying a few shell commands to a new file and saving it. Imagine you have an application (importantapp.exe) that requires a weekly maintenance restart, where you run the following commands:

Typing these commands one after the other every week is tedious, and you may mistype or misremember them. Instead, you can put them in a text file (using Notepad, for example), give it a name like weeklyrestart.bat, and just run the script each week. (Look for more on the .bat file extension in the next section.)

The most-productive techs use scripts all the time to automate a zillion tasks. My office is relatively small, but it has a lot of computers to keep up with. My sysad (systems administrator) Michael's morning routine includes checking the status of every one of those computers, looking for errors, proper functioning, and so forth. It would take him all day to visit each machine---even over the network---to check its status. Michael created scripts that automate this task. He sits at his Mac with his morning coffee, opens Terminal, runs a few scripts, and reviews the reports they kick out. Sweet!

Script Types and Languages

Scripting is a kind of programming; a scripting language is a type of programming language for writing scripts. As with any kind of programming, there are many different scripting languages designed for a variety of purposes. The CompTIA A+ objectives expect you to be able to identify the file types for six different scripting languages.

Table 15-1 lists and describes common scripting languages and their file extensions.

Table 15-1  Common Languages and Their File Extensions

NOTE   The first three scripting languages in Table 15-1 are shell scripting languages, but the other three are more general scripting languages. In a shell scripting language, any normal command you would run is a valid part of the language. This is not true in the more general scripting languages (but they have many other useful features).

Ask Not What You Can Do for Scripting

Like I said before, scripts help automate computing tasks. They do things. Which things? Unfortunately, you can't automate one of the big tricks to scripting: figuring out exactly which tasks to automate in the first place. The closest you can get is knowing the basic capabilities of scripting, seeing how other people like to automate, and building habits that make it easier to automate when the time comes.

Use Cases for Scripting

I'm not alone, here---CompTIA also thinks it's a great idea for you to know what other people do with scripting. Before we run through the use cases for scripting that you should know for the CompTIA A+ 1102 exam, I want to make something clear: automation and scripting are huge topics and the CompTIA A+ objectives just scratch the surface. If you find this stuff interesting, dive beyond the CompTIA A+ objectives and teach yourself some code.

NOTE   There is often more than one way to automate something. When it comes to Windows systems, Group Policy (which we'll take a closer look at in Chapter 27) can help with these same use cases.

Basic Automation  It's hard to know exactly what CompTIA means by "basic automation," but in my mind basic automation is all about writing little scripts for things you do every day or week or month. Maybe that's resetting a browser profile to troubleshoot constant crashing. Maybe that's resetting default applications after users accidentally change them. Maybe that's resetting file permissions that keep getting messed up for some unknown reason.

The point is, it's usually up to you and your colleagues to spot these opportunities, figure out how to automate them, and share what you discover. I'll take a closer look at how to recognize these in the upcoming "Automatic Habits" section.

Restarting Machines  For exactly the same reason that "Have you tried turning it off and back on?" is an essential troubleshooting step, it's common for organizations to set up automation for restarting machines. Nightly or weekend reboots are common for workstations that live in a lab or office with predictable hours.

There's more variety when it comes to laptops and servers. Scripts for restarting laptops may give users advanced warning, let the user defer the restart if they are busy, or reschedule it at a specific time. Scripts for restarting servers might cautiously confirm another server with spare capacity is available, stop the flow of new requests, and wait for the server to finish everything in its queue before rebooting.

Remapping Network Drives  In many organizations, users need to work with files that are stored on file servers that they access over the network. One way to do this is by mapping the relevant network shares to a drive letter on the user's system, and it's common for organizations that work this way to have scripts for ensuring the right network shares get set up. This might mean setting up one set of shares for everyone, or setting up department-specific shares depending on which user logs in.

Installation of Applications  Much as with network shares, organizations often need to ensure that their users' computers have certain applications installed and properly configured. Scripts can both set up applications on new systems and help deploy new applications to existing systems---without having to lay hands on each device.

Automated Backups  Backups can help minimize the pain of disasters, hardware failures, and updates gone wrong. We'll take a closer look at backup procedures in Chapter 28, so for now it's enough to know that manual backups are fine in some cases---but critical systems and data should be backed up automatically. Good scripts enable you to back up exactly what you need as often as you need.

Gathering of Information/Data  A big part of good system administration is just gathering information. Sometimes we need to gather a lot of information on a single system---such as a comprehensive report on the hardware and configuration of a system that keeps crashing at odd times, or a forensic audit of a device that might have been hacked or used in a crime. Other times, we need to collect information about a whole lot of systems---maybe their network configuration, list of installed apps, or free storage space. Scripts enable you to collect everything you need in exactly the right way every time.

Initiating Updates  System and software updates are tricky to manage just right. If your organization doesn't update its devices quickly enough, it could end up being the low-hanging fruit that cyber criminals target for extortion. But if its devices take every update as soon as it's available, everyone's work could be disrupted (and data could be lost) if vendors push out a real lemon of an update.

Scripting these updates can enable your organization to avoid being the guinea pig or installing known-bad updates---but also ensure devices do get updated regularly. Scripting can also make it possible to roll out updates in stages and discover incompatibilities before they affect everyone.

Automatic Habits

Here's an all-too-common automation tragedy: I'll go to manually fix something for the umpteenth time only to realize that I've been down this same road before. I'll pop open an editor, sketch out the steps, and start filling in commands. Then, midway through, I'll run into some roadblock. Maybe it requires a complex decision, or I just can't figure out why the script is doing what I wrote instead of what I meant. I'll fight it for a while, end up frustrated that I can't automate the whole task, throw out the script, and do it manually (in a huff!).

Don't do this! When it comes to automating something complex, the best way to set yourself up for success is to develop habits that give you a head start on the automation process and then automate gradually.

The most important habits here are all about notetaking: keep detailed notes, save command-line history and logs alongside them, organize them in a way that makes sense to you, make sure to refer back to them, and update them as you learn more. Do what works for you and your organization. When it's time to automate a task, a good set of notes will answer important questions and save time!

The next key habit is to keep an eye out for signs a script could save you time. This is an art, but one good hint is when you catch yourself flipping back through your command history to find a whole sequence of commands to run them all again. Another is when you have to visit a search engine or check your notes just to remember some steps, what order they belong in, or how to run them.

Once you suspect a task deserves a script, the last habit is to automate it gradually. Start with the easy parts, and then (if you have time) take another bite each time you repeat the task. Automating gradually is all about avoiding two mistakes:

-   Putting tons of work into a script you never end up running.

-   Letting "perfect" be the enemy of "better." Yes, it is really (really!) gratifying to completely automate a complex task, but it's better to start saving time and energy today.

NOTE   One of my favorite scripting tips of the last few years comes from Dan Slimmon, who recommends kicking off your gradual automation with the opposite of a script that does things: write the task up as a script that just tells you what to do, step by step. Each time you run through it, you'll have a chance to check the instructions for accuracy, refine the process, and automate easy steps.

Here Be Dragons

Before I pat you on the head and send you off into the world armed only with a text editor and a shell, I have to share some hard truths: scripting can be just as dangerous and frustrating as it is powerful. Most of the risks that come with scripting are just the dark side of the command line's incredible power.

One big way scripts cause trouble is that they tend to be fragile---a script can be very sensitive to small differences between the system you run it on and the one the author wrote it on, unless the script's author anticipated such differences. Maybe the script assumes a directory will exist but it doesn't, or that some command will be installed and it isn't.

Once one thing goes wrong, the best scripts will try to stop, reverse any changes they've already made, and display a message about what went wrong. Many scripts aren't this good---they'll just keep right on going (with some changes failing, and others succeeding). When this happens, you'll have to manually fix whatever went wrong and clean up after the script.

When it comes to using scripts, here are three specific considerations you should keep in mind for the CompTIA A+ 1102 exam:

-   If you can install software on a system from the command line, scripts can also install software. If you (or your users) run scripts that other people wrote without carefully reading the scripts to understand what they'll do, there's a very real chance of unintentionally introducing malware.

-   If there's a way to change a setting from the command line, it's possible for a script to change it! Not only does this mean that a malicious script could intentionally change system settings to make a system easier to compromise, but it also means that there's a risk of inadvertently changing system settings when you (or your users) run a script. This risk increases greatly when a script encounters errors!

-   While it isn't exactly common for scripts to cause system or application stability problems, it is still good to be aware that they are basically little programs---it is possible for them cause browser or system crashes due to mishandling of resources.

The best way to deal with these risks is to exercise caution and diligence. Train your users not to run untrusted scripts. Read scripts before you run them. Run them on test systems before you run them on systems that work for a living. Back up systems before you try out new scripts on them. Test new scripts on a fraction of your organization's systems before deploying them everywhere.

Beyond A+

Anatomy of a Script

We use programming languages to tell computers to do something to some piece of data. You've solved math problems in school, so you are already halfway to understanding this. In a simple math problem like 3 + 4, you have two numbers, and a symbol that tells you what operation (addition, in this case) to perform.

To do this math problem, you need to know the rules. You learned the rules of arithmetic back in grade school, right? In arithmetic, each of these numbers is a value; the rules tell you to add two numbers when you see the + sign.

But what if the equation looked a little different? What would you do if it was 3 + cow? That doesn't make sense! Cow isn't a number, it's a word for a large, grass-eating bovine. You and I know this, but a C and a 3 are both just bytes to the computer. How does it know that it can't add them?

Data Types

To be able to treat numbers and words differently, programming languages need a new concept---data types. A data type is a defined category, like number or word. In many programming languages, these rules dictate important details, such as you can't add the number 3 and the word cow because the two values have different data types. The number 3 is an integer (i.e., a whole number) data type, and cow (i.e., a word) is what programmers call a string data type. Here's where it gets a little more complicated, but stick with me and it'll become clearer!

A way to think of a string is as a sequence of characters, like c -- o -- w. Most programming languages require that you identify a string with 'single' or "double" quotes, so 'cow' or "cow" in this example. While only some characters are valid integers, all characters can be valid in a string.

Every programming language dictates the actions the computer can perform on strings (like joining two strings together, breaking one string into pieces, checking how many characters are in a string, and so on). While the rules of arithmetic dictate that you can't add 3 + cow (probably because it would upset the cow), many languages combine two strings when you "add" them. Adding "brown" + "cow" produces "brown cow" (and a happier cow).

NOTE   Some languages have additional data types for more specific circumstances (like a special type for dates, or fractional numbers).

Strings also make it possible to keep the computer from interpreting something as an equation to solve. For example, if I tried to write my office phone number like 281-922-4166, a computer wouldn't have any choice but to compute the result of 281 minus 922 minus 4166 (it's -4807, an integer data type). If I write "281-922-4166" instead, a computer will leave the digits intact.

Variables

As soon as the computer thinks it's done with this value (whether it's -4807 or "281-922-4166"), it will forget it. If you need to use the value more than once, you must tell the computer to save it. Most programming languages tell the computer to remember the value by naming it; we call these named values variables. I could save my office phone number as the variable phone number:

phone_number = "281-922-4166"

Conditionals and Basic Loops

Once you move beyond the most basic shell scripts---those that are just a list of commands---you often need to control when and how different commands run. Not surprisingly, scripting languages and programming languages give you excellent tools, called control constructs, to control what they should do under different conditions.

NOTE   I've included some scripting examples in this section. Each one uses the Python language. If you try to copy them into a script file for another language, they probably won't work!

The most basic control constructs are conditionals. Conditionals enable you to specify code that should run only when some condition is (or is not) met. Most languages have keywords, such as an "if" statement. The "if" statement specifies a condition, and what code to run if the condition is met. Here's a simple example:

Here's what each line means:

1\.   The animal variable holds a string value "cow".

2\.   The if statement checks to see if the animal variable contains a value of "cat".

3\.   If it contains "cat", the computer will print the word "meow" to the terminal. If not, nothing will happen.

In this case, the script would never print "meow" because the condition is not met.

Conditionals are a critical building block for all but the most basic scripts and programs. As described earlier in this chapter, one of the main reasons to write a script in the first place is because you need to do something many times. In programming, a good way to accomplish this is with a loop. Basic loops are another kind of conditional that tell the computer to run the code over and over until the condition is (or is not) met. Depending on the language, you'll usually see loops indicated with keywords like for and while. Here's an example:

This loop will run until the number of cows is 4, so it will print "moo" four times---one for each cow. Because the value in the cows variable is an integer, we can do math with it. Each time the loop runs, it prints "moo" once and adds one to the number of cows.

NOTE   Different languages have different control structures. Most of them have at least a few. Take the time to learn the control structures of languages you deal with---it's much easier to figure out what a script does once you know them.

Comments

Scripting and programming languages usually have a way to insert special text---called a comment---that helps anyone reading the script later (including the writer, a few months on!) understand what's going on. The computer ignores this text, as it's only for the humans. Leaving comments is a really good idea even if you don't expect anyone else to ever read your script. Comments are a great way to describe the problem a script exists to solve. You should also use them to describe how, when, and where to use the script.

Each language has its own comment syntax, though most languages share two common formats. Three of the languages (PowerShell, Python, and UNIX shell) use a single format, which begins a comment with the # symbol. The comment symbol can start a line or follow statements on the same line. Let's take a look:

The comments in this example describe the goal of the script---make all the cows moo---and caution the user of the script. They note that the script starts with no cows and limits the total number of cows to four, and so on.

The other three languages are all a little different, so they'll be easy to tell apart. JavaScript:

// This is a single-line comment in JavaScript

/* This is a multiline comment

in JavaScript */

Batch file:

REM This is the older way to comment in Batch files

:: But many newer scripts use this format.

Visual Basic Script:

' Visual Basic Script's comments start with a single quote.

Comments are absolutely essential for humans who need to work on scripts and programs. Nothing's worse than trying to remember how many cows will moo a year after you write the script!

Environment Variables

Any system you access has important values stored in variables that make up what we call the environment of a running program. Some of these values are set systemwide, but these values can also be set by the user, the script/program, or even the shell it is running in. These values, which we call environment variables, tell running programs all sorts of things, like what the current directory or user is, or where to store temporary files. Figure 15-15 shows the default environment variables for programs run under the michaels user account.

Figure 15-15  Environment variables in Windows 1.

We also use environment variables to configure scripts because they make it easy for many different users to customize how the same script will behave on a given system without having to edit the script itself. Here's an example of Windows Command shell environment variables in a batch file (remember that REM here means comment):

@echo off

REM prints the name of the currently logged-in account

echo You are logged in as %username%

REM prints the currently logged-in user's main folder

echo Your home directory is %homepath%

The text surrounded by percent signs (for example, %username%) is an environment variable in batch that will change depending on the user running the script. If I run the script, it'll say "Mike" and print the location of my home directory.

UNIXes have a set of environmental variables that are similar to those in Windows, but they look a bit different. Here is the same script as the previous one but written for a UNIX system:

#!/bin/bash

# Prints the name of the currently logged-in account

echo You are logged in as $USER

# Prints the currently logged-in user's main folder

echo Your home directory is $HOME

Most scripts that are meant for use on multiple different systems will depend on at least a few environment variables. Once you can read and understand the control structures in a script, it's a good idea to learn what the most common environment variables contain and train yourself to mentally substitute them as you read. When you encounter an unfamiliar environment variable, get curious---ask a search engine about it!

Chapter Review

Questions

1\.   Which of the following is an illegal character in a Linux filename?

A.   * (asterisk)

B.   . (dot)

C.   / (forward slash)

D.   _ (underscore)

2\.   Which commands pause after displaying a screen's worth of directory contents? (Choose two.)

A.   dir p

B.   ls | more

C.   dir | less

D.   dir /p

3\.   Which of the following commands will delete all the files in a directory in macOS?

A.   del *

B.   del all

C.   rm *

D.   rm all

4\.   Which command do you use to determine what directory your prompt is focusing on in Linux?

A.   dir

B.   path

C.   pwd

D.   prompt

5\.   Which Windows command is functionally equivalent to the Linux ls command?

A.   dir

B.   command

C.   copy

D.   dd

6\.   What do you type before a macOS command to access help for that command?

A.   Get-Help

B.   ?

C.   man

D.   /?

7\.   Which of the following UNIX commands will show detailed information about the contents of a folder?

A.   ls -l

B.   ls -e

C.   ls -h

D.   ls -k

8\.   Which UNIX command enables you to see a continually updating list of active processes?

A.   ps

B.   zsh

C.   top

D.   kill

9\.   Of the following, which best describes the function of the Windows gpresult command?

A.   Lists all recently updated group policies

B.   Lists the group policies applied to a user

C.   Lists all changes to a user's group policies since the last refresh

D.   Lists any and all conflicting group policies

10\.   How do you run a command at the Windows command prompt with administrative privileges?

A.   Enter an elevated username and password at the command prompt.

B.   Right-click a command-prompt shortcut and then select Run as PowerUser.

C.   Right-click a command-prompt shortcut and then select Run as administrator.

D.   The cmd command only runs with administrator privileges.

Answers

1\.   C. Any of these characters are acceptable in a Linux filename except the forward slash (/), which is used exclusively as a path separator.

2\.   B, D. The ls | more and dir /p commands in UNIX and Windows, respectively, pause a long listing at the end of the page.

3\.   C. Type rm * and press ENTER to delete all files in a directory in macOS.

4\.   C. The pwd command enables you to determine the current folder location in Linux.

5\.   A. The Windows dir command accomplishes a similar function to the Linux ls command.

6\.   C. Access the help for a macOS command by typing man [command name].

7\.   A. Type ls -l and press ENTER to see detailed information about a folder in UNIX systems.

8\.   A. ps is the UNIX command that enables you to see a continually updating list of active processes.

9\.   B. The gpresult command in Windows lists group policies applied to a user.

10\.   C. To run a command at the Windows command prompt with administrative privileges, right-click a command-prompt shortcut and then select Run as administrator.

Copy

copy

Highlight

highlight

Add Note

note

Get Link

link

table of contents

search

Settings

queue

close x

Preparing for certification?

Take Practice Test

chevron right

Skip to Content

Topics

Start Learning

Featured

Search 50,000+ courses, events, titles, and more

Chapter 15 Working with the Command-Line Interface

Chapter 16 Troubleshooting Operating Systems

Chapter 17 Display Technologies

42h 21m remaining
