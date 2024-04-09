Introduction
Who Should Read This Book

Introduction
Visual Studio is sexy. In the world of Integrated Development Environments (IDEs), it stands as a beautiful example of how environments should work. Yet many of the features created to improve productivity, I believe, are largely neglected. Most developers use only a small percentage of the capabilities in this wonderful product—not because they don’t want to use them, but because developers don’t know they exist.

In most books that address the various .NET languages or technologies, Visual Studio seems to be mentioned almost as an afterthought; to be fair, its focus is primarily on the language or technology that’s the subject of the book, not the IDE—which is as it should be. On the other side of the coin, books written about Visual Studio do focus on the product, but tend to be broad in scope, describing features, but without saying much about their actual use.

The goal of this book is to arm you with techniques that you can apply immediately to improve productivity. Use the content in this book anywhere, anytime, to dramatically reduce the time required to perform just about any task in Visual Studio. You won’t find an exhaustive treatment of every feature in Visual Studio in this book, but it contains sufficient coverage that we’re sure you’ll find something useful, regardless of how you use the product.

This is much more than just a tips and tricks book. Within these pages are—for the first time ever—the keyboard mapping shortcuts, commands, and menu paths for features, along with detailed descriptions of how to use them. We worked very hard to present the information in a way that makes the book easy to read cover-to-cover or as a quick reference.

System Requirements
You will need the following hardware and software to complete the practice exercises in this book.

Software Requirements
Windows XP (x86) with Service Pack 3—all editions except Starter Edition

Windows Vista (x86 & x64) with Service Pack 2—all editions except Starter Edition

Windows 7 (x86 & x64)

Windows Server 2003 (x86 & x64) with Service Pack 2

Windows Server 2003 R2 (x86 & x64)

Windows Server 2008 (x86 & x64) with Service Pack 2

Windows Server 2008 R2 (x64)

Supported Architectures:
32-Bit (x86)

64-Bit (x64)

Hardware Requirements
Computer that has a 1.6GHz or faster processor

1 GB (32-Bit) or 2 GB (64-Bit) RAM (Add 512 MB if running in a virtual machine)

3 GB of available hard disk space

5400 RPM hard disk drive

DirectX 9 capable video card running at 1024 x 768 or higher-resolution display

DVD-ROM Drive

Depending on your Windows configuration, you might require Local Administrator rights to install or configure Visual Studio.

Part I. Productivity Techniques

I. Productivity Techniques
1. Getting Started
01.01 Running Multiple Versions of Visual Studio Side-By-Side

Chapter 1. Getting Started
“A beginning is the time for taking the most delicate care […]”

— Frank Herbert “Dune”
This chapter addresses tasks that would be immediately beneficial as you work in Visual Studio. The main themes here are exporting your development settings, learning the Start Page, adjusting your performance, and other key tasks.

This chapter is arguably the most important one you will read in this book—and yet, I suspect, the one people will think they need the least. If you have been using Visual Studio for any length of time, you might easily feel that the tasks in in this chapter have little application to your situation. But whether you have been using Visual Studio for ten days or ten years, these tips will help ensure that all your other efforts go smoothly, so taking time to absorb the contents is definitely worthwhile.

01.01 Running Multiple Versions of Visual Studio Side-By-Side
VERSIONS

2005, 2008, 2010

CODE

vstipEnv0054

People often ask whether you can run multiple versions of Visual Studio side-by-side on the same machine. The answer is yes you can!

You can find documentation on MSDN, in the topic “Installing Visual Studio Versions Side-by-Side,” at http://msdn.microsoft.com/en-us/library/ms246609.aspx.

The recommendation is that you install multiple versions from oldest to newest. So you would install Visual Studio 2005, 2008, and then 2010—in that order.

01.02 Getting Table of Contents in Visual Studio 2010 Online Help
DEFAULT

Ctrl+Alt+F1 (help settings); F1 (view help)

VISUAL BASIC 6

Ctrl+Alt+F1 (help settings); F1 (view help)

VISUAL C# 2005

Ctrl+F1, M (help settings); Ctrl+F1, Ctrl+M (help settings); F1 (view help)

VISUAL C++ 2

Ctrl+Alt+F1 (help settings); F1 (view help)

VISUAL C++ 6

Ctrl+Alt+F1 (help settings); F1 (view help)

VISUAL STUDIO 6

Ctrl+Alt+F1 (help settings); F1 (view help)

WINDOWS

Alt, H, S (help settings); Alt, H, V (view help)

WINDOWS KEYBOARD

Alt, H, S (help settings); Alt, H, V (view help)

MENU

Help | Manage Help Settings; Help | View Help

COMMAND

Help.ManageHelpSettings; Help.F1Help

VERSIONS

2010

CODE

vstipTool0120

I have to admit I don’t like the new online help in Visual Studio 2010. Not that I think it’s bad per se, but I was just used to the old help system’s look and feel—particularly the table of contents list.

If you are like me and want to get that classic help look-and-feel back for online help, you need to do two things.

Online Help
First, you need to set your default help to online help (you need Internet connectivity to use this feature) by selecting Help | Manage Help Settings. Then click Choose Online Or Local Help.

Select I Want To Use Online Help, and click OK.

Using Classic View
Now that you are using online help, Go to Help | View Help to see a page similar to the following:

In the upper-right corner of the page, if you see the Preferences link, click it.

NOTE
You may not see the Preferences link but instead just three links to Lightweight, ScriptFree, and Classic. In this case, just click Classic and skip the next step.

Choose Classic and click OK.

Now your help will use the old-style contents list.

01.03 Exporting Your Environment Settings
WINDOWS

Alt,T, I

MENU

Tools | Import and Export Settings

COMMAND

Tools.ImportandExportSettings

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0021

Exporting your environment settings is a great way to back them up. You can export your settings by selecting Tools | Import And Export Settings Wizard.


The Export Selected Environment Settings option lets you save your settings to a .vssettings file.

Click Next to see the Choose Settings To Export dialog box.


You can expand the areas to choose the items you want to include or exclude.


By default, almost everything is selected except for items that could expose sensitive information. You can tell which options these are by the yellow warning symbol icon next to the item.


After you make your choices and click Next, you can pick the location (C:\users\<current user>\documents\visual studio <version>\settings, by default) and the filename (the current date, by default) where you want to save the exported information.

WARNING
If you don’t give your exported settings good names it will be hard to figure out what they are for later. For example, if you are just exporting your favorite black theme fonts and colors, a name like “Fonts and Colors (Black Theme) 2010-07-05” would make sense.


When you click Finish, Visual Studio exports your settings, and the following dialog box appears.


If you are curious, the exported file is just an XML file. You can open it in Notepad and see the contents, as shown in the following illustration.


01.04 Remove Projects from the Recent Projects List
WINDOWS

Alt,F, J, [Number]

MENU

File | Recent Projects and Solutions

VERSIONS

2010

CODE

vstipTool0017

In Visual Studio 2010, you can now remove projects from the Recent Projects list on your Start Page.

Just right-click the project, and select Remove From List, as shown in the following illustration. That’s it. The project is removed from the list but not deleted. If you want to permanently delete the project, you need to do that yourself from the filesystem.


01.05 AutoRecover
WINDOWS

Alt,T, O

MENU

Tools | Options | Environment | AutoRecover

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0019

AutoRecover can be a real life saver if the development environment crashes or if a power outage occurs. It’s simple to use: Just go to Tools | Options | Environment | AutoRecover.


To turn this feature off (not recommended), you can clear the Save AutoRecover Information Every check box. Here’s an explanation of what the other options do:

n minutes Determines how often Visual Studio saves AutoRecover information for files. The default is to save every five minutes, but you can adjust that interval up or down depending on your needs. There is an inverse relationship between this value and the frequency of your updates to code. If you make frequent code updates, you should set a smaller save interval. Conversely, if you make relatively infrequent code updates, you can increase this interval. It’s better to err by using an interval that’s too short rather than too long; in other words, it’s better to take a performance hit from file I/O than to lose a ton of work.

n days Determines how long Visual Studio keeps AutoRecover files in the Backup Files directory. The default is seven days, which is adequate for most situations. If you work with a lot of projects over a short period of time, you might want to decrease this number to keep the Backup Files directory from getting too cluttered. If you’re not sure about what you need for this value, it’s better to guess high and later reduce the number as needed.

I want to be clear about what exactly gets saved and where it gets saved. First, recovered files are stored at My Documents\Visual Studio <version>\Backup Files\<projectname>. But not every file is saved here. The backup folder is empty when you first create a solution in Visual Studio.

When I make a change to a file and save the change, I wait five minutes to see the result.


There’s still nothing there, because Visual Studio knows there is no need to recover a saved file. But if I make a change to a file without saving it and wait another five minutes, here is what you see:


At this point, the AutoRecover information appears because there are unsaved changes. If Visual Studio crashes now, you would need to make a decision about whether to recover the unsaved changes or keep the last saved version. Giving you that choice is the essential function of the AutoRecover feature.

When you do finally have to recover a file, you will see the following dialog box.


To explain the terminology in the preceding dialog box:

Recovered files

Lists the file(s) that can be recovered. Use a check box to select or clear the files you want to keep as well as to see some basic information.

<File Name> Summary

Shows detailed information about the currently selected file, including date/time information, location of the backup file, and the destination location where the recovered file will be saved.

Recover Selected Files

Performs a recovery action on the selected file(s), copying the recovered source file to the previously indicated destination.

Do Not Recover

Closes the dialog box without recovering any listed files.


01.06 Improving Performance by Changing the Visual Experience in Visual Studio 2010
WINDOWS

Alt,T, O

MENU

Tools | Options | Environment | General | Visual Experience

COMMAND

Tools.Options

VERSIONS

2010

CODE

vstipEnv0017

Visual Studio 2010 automatically adjusts the visual experience depending on the situation. For example, it might eliminate or reduce the use of gradients and animations when running in Remote Desktop or virtual machine environments. It also makes use of hardware graphics acceleration when that’s available.

In some situations, you can improve Visual Studio’s performance by changing its Visual Experience manually. To change these settings, select Tools | Options | Environment | General | Visual Experience to see the following dialog box.


Clear the Automatically Adjust Visual Experience Based On Client Performance check box.

NOTE
As you work with the preceding options, the message at the bottom of the dialog box does not change until you click OK to commit the changes you have made.

Following is a brief explanation of what each option does:

Enable Rich Client Visual Experience This option gives you gradients and animations (also known as “eye candy”) for elements such as sliding tool windows and so on. If you leave this option selected, Visual Studio uses these rich animations in all scenarios—including remote sessions. You should usually turn this option off in such situations to get a bump in performance.

Use Hardware Graphics Acceleration If Available This option lets you decide whether Windows Presentation Foundation (WPF) hardware acceleration is something you want. If this can benefit you, you’ll notice a clear change in performance when you enable or disable this option. Make sure to test both scenarios.

NOTE
If you have a system whose performance doesn’t suffer when animations and gradients are turned on, a little eye candy can be a good thing, so this tip is really for those folks who are having performance issues in their Visual Studio experience, either locally or remotely.

Now that you have played with the preceding options a bit, you might be wondering whether you can actually see how much they can improve (or hurt) performance. The Windows SDK includes a tool called WPFPerf that enables you to measure WPF performance. You can find a great article on how to use it at the Microsoft WindowsClient.NET site, at http://windowsclient.net/wpf/perf/wpf-perf-tool.aspx.

Also, when using Visual Studio 2010 over remote sessions, you should definitely read the article titled “Optimizing Visual Studio 2010 and WPF Applications for Remote Desktop,” at http://blogs.msdn.com/b/jgoldb/archive/2010/02/27/optimizing-visual-studio-2010-and-wpf-applications-for-remote-desktop.aspx. This article provides important information about how to dramatically improve performance over Remote Desktop.

01.07 Change Tool Window Animations
WINDOWS

Alt,T, O

MENU

Tools | Options | Environment | General

COMMAND

Tools.Options

VERSIONS

2005, 2008

CODE

vstipEnv0018

In the tip vstipEnv0017 (01.06 Improving Performance by Changing the Visual Experience in Visual Studio 2010, page 14), you saw a discussion of how you can improve the visual performance of Visual Studio 2010. Now let’s look at Visual Studio 2008 and 2005. You can change the animation speed of tool windows in Visual Studio 2008 and 2005, but why would you want to do this?

The answer is that you can get a performance boost by speeding up or completely turning off the animation. Select Tools | Options | Environment | General, and locate the Animate Environment Tools option.


I suggest you turn off this feature to begin with, to see whether you notice any performance improvements. Later, if you want your animations back, turn on the option and set the slider to the far-right side (the fastest speed). As you test the performance, you can adjust it back to the left to determine the best setting for you.


01.08 Importing or Changing Your Environment Settings
WINDOWS

Alt,T, I

MENU

Tools | Import and Export Settings

COMMAND

Tools.ImportandExportSettings

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0022

Assuming you have exported your settings (vstipEnv0021, 01.03 Exporting Your Environment Settings, page 6), you can import your settings by going to Tools | Import And Export Settings Wizard and selecting Import Selected Environment Settings:


This setting enables you to import a previously exported .vssettings file.

After you click Next on the Welcome page shown in the preceding illustration, you have the option to save your existing settings (recommended) before overwriting or to just overwrite them:


Click Next, and you can choose from the default settings, settings that have been saved previously, or you can browse for your own .vssettings file:


Now click Next again to choose what settings you want to import. All the previously exported settings are selected by default except for Command Window Aliases, External Tools List, and Import and Export Settings, which are considered potentially dangerous.

WARNING
You have to determine the potentially dangerous areas for yourself, but if doing a full export or import, you would most likely check all the items in this dialog. It is not recommended that you share full exports with team members as there may be information in the file you don’t want to share. Instead, just export the items you want to share with team members in a separate file.


After you have checked (or unchecked) the items you want, click Finish to import the settings and to see the final page of the wizard:


Now, just click Finish and you are done.

01.09 Change Your Visual Studio Color Scheme
WINDOWS

Alt,T, I

MENU

Tools | Import and Export Settings

COMMAND

Tools.ImportandExportSettings

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0034

Ever see a set of colors your friend or coworker has and wish you could get it too? Ever go to http://studiostyles.info and want some of those cool color schemes?


Well you can get the colors you want! Let’s walk through how it’s done.

Seeing What You Like
First, you see a seriously cool color scheme on someone’s screen or at the Studio Styles site:


Getting the Goods
On someone’s computer
Now that you see what you like, get them to export their fonts and colors. Go to Tools | Import And Export Settings:


Click Next, and export only the fonts and colors—nothing else:


Click Next, give the settings a cool name, and click Finish:


On the Studio Styles site
Click the style you want:


Choose your Visual Studio version, click Download This Scheme, and follow the instructions in the next section:


Changing Your Colors
When you have a .vssettings file you want to import, copy or move the file to your computer. While you can put the file anywhere you want on your system, I prefer to put it with the other settings files located at C:\Users\<user>\Documents\Visual Studio <version>\Settings:


Now just go to Tools | Import And Export Settings on your computer:


Make sure that Import Selected Environment Settings is selected, as shown in the preceding illustration, and click Next. If you haven’t backed up your settings in a while, feel free to do so. Check out vstipEnv0034 (01.09 Change Your Visual Studio Color Scheme, page 17) if you want more information on exporting your settings:


Choose the settings file that has the color scheme you want:

NOTE
Click Browse to find your file if you didn’t put it in your Settings folder.


Click Next. Verify that the file is importing only fonts and colors, and then click Finish:


Resetting the Colors
You should have your new colors. If things get bad (for example, you get colors you don’t like and didn’t make a backup of your old colors) and you need to get the default colors back, all you have to do is go to Tools | Options | Fonts And Colors and click Use Defaults.

WARNING
Clicking Use Defaults is an option that wipes out any custom colors used previously.


01.10 Reset All Your Development Settings
WINDOWS

Alt,T, I

MENU

Tools | Import and ExportSettings

COMMAND

Tools.ImportandExport Settings

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0023

Sometimes you need to get all your settings back to their original state. You can do this with the Reset All Settings option found under Tools | Import And Export Settings:


WARNING
Use the Reset All Settings option at your own risk. It will reset your settings, including a reset of your Toolbox, getting rid of any custom items you have put in there.

After you click Next on the Welcome page shown in the preceding illustration, you see the option to save your current settings. You should absolutely do this.


The next screen lets you choose from the list of default settings:


Choose your default settings, and click Finish. After the reset operation runs, it resets all your settings. This is definitely something you would do as a last resort, and remember, you can always bring back your old settings by importing settings you saved earlier (see vstipEnv0021, 01.03 Exporting Your Environment Settings, page 6).


01.11 Customize Your Toolbars in Visual Studio 2010: Toolbars Tab
WINDOWS

Alt,T, C

MENU

Tools | Customize

COMMAND

Tools.Customize

VERSIONS

2010

CODE

vstipEnv0030

You can customize any toolbar in Visual Studio 2010. Just click the drop-down arrow to the right of any toolbar, and then click Add Or Remove Buttons:


Then click Customize:


Alternatively, you can go to Tools | Customize on the menu bar. Whichever option you choose opens the Customize dialog box:


Custom Toolbars
As shown in the preceding illustration, the Toolbars tab lists all the available toolbars. After you click New to create a customized toolbar, you are prompted to give the new toolbar a name:


After you name it, you can delete the custom toolbar by clicking Delete, or you can change it by clicking Modify Selection to rename or relocate the toolbar:


Although you can rename custom toolbars by clicking Modify Selection, default toolbars can’t be changed in this way:


Clicking Keyboard at the bottom of the Customize dialog box takes you to the Tools | Options | Keyboard area, where you can add keyboard shortcuts for selected commands. (See vstipTool0063, 03.26 Keyboard Shortcuts: Creating New Shortcuts, page 127, for details.)


01.12 Customize Your Toolbars in Visual Studio 2010: Commands Tab
WINDOWS

Alt,T, C

MENU

Tools | Customize

COMMAND

Tools.Customize

VERSIONS

2010

CODE

vstipEnv0031

You can customize any toolbar in Visual Studio 2010. Just click the drop-down arrow to the right of any toolbar, and then click Add Or Remove Buttons:


Then click Customize:


Alternatively, you can go to Tools | Customize on the menu bar.

Either option you choose opens the Customize dialog box:


Click the Commands tab:

NOTE
For information about the Toolbars tab, see vstipEnv0030, 01.11 Customize Your Toolbars in Visual Studio 2010: Toolbars Tab, page 27.


As you can see, the Customize dialog box is fairly complex, so let’s break it down into its parts as we look at an example.

Rearrange
First is the choice of menu or toolbar to modify. In this case, choose the Editor Context Menus | Code Window option, which is what you see when you right-click while writing code:


Controls
Next is the Controls area that shows the items on the menu or toolbar you have chosen to modify. For this example, it shows the items available when you right-click in a code window:


Remember that not all the items you see are available all the time because these items show up only in the proper context. So while it seems you have a large number of buttons currently available, when you right-click in your code window, this is an example of what you will currently see:


Buttons
Finally, let’s look at the area of the dialog box that has all the buttons that actually perform actions:

Add Command

Lets you add a new item to the existing menu or toolbar.

Add New Menu

Creates a new menu in the existing menu or toolbar.

Delete

Removes the current item from the Controls area.

Move [Up or Down]

Changes the location of the item in the Controls area.


Modify Selection
Choosing Modify Selection enables you to make changes to the existing item in the Controls area, such as resetting it to the default settings, changing the name, and modifying text visibility options. Modify Selection also enables you to make a new group on the menu or toolbar:


Finally, the Reset All option resets every item in the Controls area to its default settings. This capability is particularly useful if you have made a lot of changes.

Getting back to our example: Let’s assume you want to add the comment and uncomment items to the context menu so that you can use them when you select some code. First, click Add Command to bring up the Add Command dialog box:


Now you need to figure out where the comment and uncomment items are located. How would you do this? Well, the best path is usually to see whether the item can be found on a menu somewhere and then use that as a clue:


Because the items you want are off the Edit menu, you can search there first. It turns out the items you want are called Selection Comment and Selection Uncomment:


Find each one of these items, and click OK to add them to the Controls list:


It would be nice to have these buttons in their own group, so select the item in the Controls dialog box, shown in the preceding illustration, where you would like the group line to be (Marker Commands, in this case), and then click Modify Selection and choose Begin A Group:


This creates a new group line, and your commands are in their own group:


Click Close and go to any code area. Select some code, right-click, and select Comment Selection:


It works perfectly, and you are all set to begin making your own modifications to your environment:


01.13 Visual Studio Logging
VERSIONS

2005, 2008, 2010

CODE

vstipEnv0048

There’s no doubt Visual Studio is an awesome piece of software, but occasionally you might run into a problem loading it. Did you know that it comes with a logging switch? While the documentation (http://msdn.microsoft.com/en-us/library/ms241272.aspx) is lacking, the community comment contributed by Paul Harrington on the Visual Studio team helps a great deal.

Essentially, the syntax is as follows:

devenv.exe /log [filename]
The [filename] is optional and, if not specified, the ActivityLog.xml file is called by default. The path is to the log file is:

%APPDATA%\Microsoft\VisualStudio\<version>\ActivityLog.xml
Give it a try. Go to the Visual Studio command prompt, and enter devenv.exe /log:


You can then navigate to the file location:


When you open the log file, the following illustration provides an example of what you might see:


Fortunately, an XML style sheet (XSL) comes with the data, so if you view the XML file in your browser, you can see a much cleaner view:


Now you can easily see the logging information and look for any issues.



01.14 Visual Studio Safe Mode
VERSIONS

2005, 2008, 2010

CODE

vstipEnv0050

Occasionally you have a situation where Visual Studio might not start up correctly or at all. Using Visual Studio in safe mode, you can load only the default environment, services, and shipped versions of third-party packages to see whether the problem is caused by one or more third-party add-ins. Just go to the Visual Studio command prompt, and type devenv.exe /safemode:


NOTE
Although I don’t show it here, I suggest using the Visual Studio logging feature before running safe mode to see whether it can help you determine the source of the problem. For more information, see vstipEnv0048, 01.13 Visual Studio Logging, page 37.

When Visual Studio starts up, it indicates it is running in safe mode in the title bar:


From here, you can start determining what might have caused Visual Studio to fail and remedy the issue.

01.15 The ResetSettings Switch
VERSIONS

2005, 2008, 2010

CODE

vstipEnv0047

Visual Studio supports several switches. One of these is the /ResetSettings switch. When used by itself, it resets Visual Studio to the default settings you initially chose during install. That’s nice, but an even better option is available that can be particularly useful for people in other scenarios.

Let’s take a classic example: You might have two (or more) monitors at work, but when you get home, you work with just one monitor. Your window layouts (among other things) could be very different in each place. In vstipEnv0040, 03.29 Export Your Window Layouts (page 134), I showed you how to export just your window layouts. Using the exported information, you could create and use two different window layouts: one for work and one for home. This tip shows you how to do this when using two different machines or the same machine at work and home.

Two Different Machines
The question is: What do you do once you have exported the window layouts? Well, now you put the .vssettings files where you can easily get to them on your machines and then you go to the Properties dialog box of the Visual Studio program icon:


Click the Shortcut tab:


In the Target area, type /ResetSettings [settings file], where [settings file] is the path to the settings file for one of your layouts:


Now Visual Studio loads up with the settings appropriate for your machine.

Same Machine
What if you use the same machine for home and work, like a laptop? Just make two copies of the Visual Studio program icon, put them somewhere (on your Desktop, most likely), and give them names:


Now just follow the steps for the different machines for each icon, and you can use one icon when you are at work to get the work window layouts and the other for home with the home window layout.

