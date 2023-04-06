### Task : perform user-level tasks on a Linux system
In this task, you will enter commands to obtain information on your Linux lab system, using output from commands.

**Knowledge Item: the utilities shown in this lab exercise are either included in most standard Linux distributions, or can be easily installed from the Internet.**

In the terminal window, enter the command(s) (**in red**) :

open web browser

**firefox --new-window www.google.com 2>/dev/null**

**Note: after you see the rendering of the Google home page, please close Firefox**

install email application

**sudo yum -y install thunderbird**

**Important: sudo will prompt for your user account password, enter: Pa55.w@rd!**

**As an alternative, you can select the Resources tab (above), and simply left click on Pa55.w@rd!**

**Knowledge Item: you will cover software packaging in much more detail in Lab 4**

launch email client

**thunderbird**

**Knowledge Item: when you first launch thunderbird, a form will appear to setup the email client with : your "real" name, and your email address (so that thunderbird can find your mail server). For best security, use your Gmail account for this lab exercise. A screen shot of the setup form is below :**

**Knowledge Item: Linux contains a standard utility to read PDF files - evince**

PDF file viewer utility

**evince /usr/share/doc/valgrind/valgrind\_manual.pdf**