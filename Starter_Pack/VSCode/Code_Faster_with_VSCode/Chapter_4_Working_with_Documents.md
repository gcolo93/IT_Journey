
4. Working with Documents
04.01 Insert Documents to the Right of Existing Tabs
16h 35m remaining
Chapter 4. Working with Documents
“He turned off the word processor, realizing just a second after he’d flicked the switch that he’d forgotten to save the document. Well, that was all right. Maybe it had even been the critic in his subconscious, telling him the document wasn’t worth saving.”

— Stephen King “Secret Window, Secret Garden” in “Four Past Midnight”
Documents serve as the cornerstone of your activities in Visual Studio. Writing code, debugging code, creating interfaces, or just about anything else you do is done with documents. Yet we still seem to take our documents for granted. This chapter focuses on working with documents in the File Tab Channel as well as ways to navigate better. Several advanced topics, such as creating custom file extensions and working with previous versions are covered as well.





4. Working with Documents
04.01 Insert Documents to the Right of Existing Tabs
04.02 Recent Files
16h 35m remaining
04.01 Insert Documents to the Right of Existing Tabs
WINDOWS

Alt,T, O

MENU

Tools | Options | Environment | Documents

VERSIONS

2010

CODE

vstipEnv0001

By default, Visual Studio 2010 opens up new tabs to the left of existing ones, as shown in the following illustration.


You now have an option to put newly opened documents in the file channel to the right of existing tabs.

Just go to Tools | Options | Environment | Documents, and select the Insert Documents To The Right Of Existing Tabs option.

You should see new tabs show up to the right of existing tabs.






04.01 Insert Documents to the Right of Existing Tabs
04.02 Recent Files
04.03 Working with Documents on Multiple Monitors
16h 35m remaining
04.02 Recent Files
WINDOWS

Alt,W, [1,2,3, etc] (windows);

Alt,F, F, [1,2,3, etc] (files);

Alt,F, J, [1,2,3, etc] (projects and solutions)

MENU

Tools | Options | General | Recent files;

Window | [1,2,3, etc]; File | Recent Files | [1,2,3, etc];

File | Recent Projects and Solutions | [1,2,3, etc]

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0013

By default, the Window menu shows the 10 most recent files you had open, as shown in the illustration to the right.

Likewise, the Recent Files and Recent Projects And Solutions items on the File menu show only the last 20 entries.


You can easily modify these numbers (up or down) by going to Tools | Options | General | Recent files.


For each of these options, the minimum value is 1 and the maximum value is 24. Experiment with numbers that suit your taste.





04.02 Recent Files
04.03 Working with Documents on Multiple Monitors
04.04 Navigate Open Document Windows
16h 35m remaining
04.03 Working with Documents on Multiple Monitors
WINDOWS

Alt,W, F (float); Alt,W,T (dock)

MENU

Window | Float; Window | Dock as Tabbed Document

COMMAND

Window.Float; Window.DockasTabbedDocument

VERSIONS

2010

CODE

vstipTool0004

This is one we have all been wanting for a long time: detachable document windows. You can now detach document windows and put them on another monitor! You have a couple of ways to do this.


The first way is to simply click and drag the tab for the document window out of the IDE.


The second way is to go to Window | Float on the menu bar, as shown in the following illustration.


What if you want to put the window back? No worries; just right-click the title bar of the document and choose Dock As Tabbed Document.


If you want an alternative method, you can go the following route: Click and drag the document window by its title bar into the IDE.

The guide diamond appears in the IDE, as shown in the following illustration.


Hold down the left mouse button, and move your cursor over the middle item in the guide diamond. You should see an outline of where the window will be docked.


Release the mouse button, and it should dock where you want it to go.





04.03 Working with Documents on Multiple Monitors
04.04 Navigate Open Document Windows
04.05 Close the Current Document Window
16h 35m remaining
04.04 Navigate Open Document Windows
DEFAULT

Ctrl+F6 (next);

Ctrl+Shift+F6 (previous)

VISUAL C++ 2

Ctrl+F6; Ctrl+Tab (next)

Ctrl+Shift+F6; Ctrl+Shift+Tab (previous)

VISUAL STUDIO 6

Ctrl+F6; Ctrl+Tab (next)

Ctrl+Shift+F6; Ctrl+Shift+Tab (previous)

COMMAND

Window.NextDocumentWindow; Window.PreviousDocumentWindow

VERSIONS

2005, 2008, 2010

CODE

vstipTool0013

OK, so you have a lot of files open in the file channel:


And you don’t want to use your mouse to switch between tabs.Just press Ctrl+F6 to go forward.

Or press Ctrl+Shift+F6 to go backward.





04.04 Navigate Open Document Windows
04.05 Close the Current Document Window
04.06 Open a File Location from the File Tab
16h 35m remaining
04.05 Close the Current Document Window
DEFAULT

Ctrl+F4

VISUAL BASIC 6

Ctrl+F4

VISUAL C# 2005

Ctrl+F4

VISUAL C++ 2

Ctrl+F4

VISUAL C++ 6

Ctrl+F4

VISUAL STUDIO 6

Ctrl+F4

WINDOWS

Alt,F, C

MENU

File | Close

COMMAND

Window.CloseDocumentWindow; File.Close

VERSIONS

2005, 2008, 2010

CODE

vstipTool0014

You can close the current document window from the keyboard. Just make sure you are in the document you want to close.


Then press Ctrl+F4. The current document closes, and it prompts you to save changes if you haven’t already.





04.05 Close the Current Document Window
04.06 Open a File Location from the File Tab
04.07 Open the File Menu Drop-Down List from Your Keyboard
16h 35m remaining
04.06 Open a File Location from the File Tab
DEFAULT

Alt+- (minus sign), O (VS2010 Only)

VISUAL BASIC 6

[no shortcut]

WINDOWS

Alt+- (minus sign), O (VS2010 Only)

COMMAND

File.OpenContainingFolder; Window.ShowDockMenu

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0014

Do you often find yourself needing to go to your project location in Windows Explorer? Just right-click the file’s tab, and choose Open Containing Folder.


The file location opens in Windows Explorer, and you can manipulate the files from there.





04.06 Open a File Location from the File Tab
04.07 Open the File Menu Drop-Down List from Your Keyboard
04.08 Using the IDE Navigator
16h 35m remaining
04.07 Open the File Menu Drop-Down List from Your Keyboard
DEFAULT

Ctrl+Alt+Down Arrow

VISUAL BASIC 6

Ctrl+Alt+Down Arrow

VISUAL C# 2005

Ctrl+Alt+Down Arrow

VISUAL C++ 2

Ctrl+Alt+Down Arrow

VISUAL C++ 6

Ctrl+Alt+Down Arrow

VISUAL STUDIO 6

Ctrl+Alt+Down Arrow

WINDOWS

[no shortcut]

COMMAND

Window.ShowEzMDIFileList

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0003

When you have a lot of files open, it is sometimes easier to view them as a list instead of tabs. The File menu drop-down list does that for you. You can click the drop-down button to the far right on the file tab, or you can simply use Ctrl+Alt+Down Arrow to activate it.


An interesting thing about this list is that it has type-ahead functionality. So, in this example, if you type the letter S, it automatically selects SomethingToDo.cs. Hitting S again results in Start Page being selected. If you have a lot of files, you can type more characters to narrow down the selection. For example, typing ST jumps straight to Start Page.





04.07 Open the File Menu Drop-Down List from Your Keyboard
04.08 Using the IDE Navigator
04.09 Multiple Views of the Same Document
16h 35m remaining
04.08 Using the IDE Navigator
DEFAULT

Ctrl+Tab (forward in Active Files);

Ctrl+Shift+Tab (backward in Active Files);

Alt+F7 (forward in Active Tool Windows);

Alt+Shift+F7 (backward in Active Tool Windows)

VISUAL BASIC 6

[no shortcuts]

VISUAL C# 2005

Ctrl+Tab (forward in Active Files);

Ctrl+Shift+Tab (backward in Active Files);

Alt+F7 (forward in Active Tool Windows);

Alt+Shift+F7 (backward in Active Tool Windows)

VISUAL C++ 2

[no shortcuts]

VISUAL C++ 6

Ctrl+Tab (forward in Active Files);

Ctrl+Shift+Tab (backward in Active Files);

Alt+F7 (forward in Active Tool Windows);

Alt+Shift+F7 (backward in Active Tool Windows)

VISUAL STUDIO 6

Ctrl+Tab (forward in Active Files);

Ctrl+Shift+Tab (backward in Active Files);

Alt+F7 (forward in Active Tool Windows);

Alt+Shift+F7 (backward in Active Tool Windows)

WINDOWS

[no shortcuts]

COMMAND

Window.NextDocumentWindowNav;

Window.PreviousDocumentWindowNav;

Window.NextToolWindowNav;

Window.PreviousToolWindowNav

VERSIONS

2005, 2008, 2010

CODE

vstipTool0023

Navigating documents and tool windows in the IDE is a critical part of your development experience. You can easily move among active file and tool windows by pressing Ctrl+Tab.


NOTE
The images in this tip show the IDE Navigator with document preview (image to the right of the lists). This feature is off by default in Visual Studio 2010, but can be turned on as shown in vstipTool0113, AX.43 Thumbnail Previews in the IDE Navigator, in Appendix B (http://go.microsoft.com/FWLink/?Linkid=223758).

Some interesting things come with using this feature. For example, holding down the Ctrl key keeps the IDE Navigator showing once it is up. Also, you can select any item in this dialog box, while it is showing, by using your mouse or arrow keys.


Navigator Areas
Let’s take a look at the two major areas in the navigator: Active Files and Active Tool Windows.

Active files
To navigate active files, press Ctrl+Tab to go forward and Ctrl+Shift+Tab to go backward though the list. The currently selected file is highlighted, and its name is displayed at the top of the dialog box. Also, notice that the full file path is shown at the bottom of the IDE navigator.

Active tool windows
This part of the dialog box shows all your tool windows that are currently open. To get to this area, you can use Alt+F7 or Alt+Shift+F7. The interesting part is that this list changes depending on when you use it. The following illustration shows what mine looks like while I am writing code.


And here’s what it looks like when I’m debugging:






04.08 Using the IDE Navigator
04.09 Multiple Views of the Same Document
04.10 Closing Just the Selected Files You Want
16h 35m remaining
04.09 Multiple Views of the Same Document
WINDOWS

Alt,W, N

MENU

Window | New Window

COMMAND

Window.NewWindow

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0016

Sometimes you might want to look at a particularly large document in several different areas at the same time. For example, you might want to look at the same document on multiple monitors. This tip shows you how to make this happen.

Special Note for VB Users in Visual Studio 2010
This feature is turned off by default in VB. A lot of history and reasoning is behind this, but the long and short of it is that this was fixed for 2010 but time ran out and it wasn’t tested. So you can turn this on for VB, but you do so at your own risk. Special thanks to my friend Dustin Campbell for supplying the history and the fix.

To to fix this, go to “HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\10.0\Languages\Language Services\Basic\” and rename the Single Code Window Only registry key to something like [your initials here] Single Code Window Only. The following illustration shows what I did:



Now restart Visual Studio, and you are good to go for the rest of this tip.

Multiple Views
I came across this while I was checking my email one day and noticed a thread started by the legendary Deborah Kurata concerning the Window | New Window menu item. The following example describes how it works.

Open a document window.


Now go to Window | New Window on the menu bar to open a duplicate window of the current document.


Notice that “:1” is added to the existing document tab text and that “:2” is appended to the name on the new document tab. You can apparently do this forever (or at least up to 150, which is as high as I have tested this feature).
note

Get Link
link
table of contents
search
Settings





04.09 Multiple Views of the Same Document
04.10 Closing Just the Selected Files You Want
04.11 Understanding the File Open Location
16h 35m remaining
04.10 Closing Just the Selected Files You Want
WINDOWS

Alt,W, W

MENU

Window | Windows

COMMAND

Window.Windows

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0010

What do you do when you have a lot of files open and want to close only a few of them? Just go to Window | Windows on the menu bar, as shown in the following illustration.


Select the files you want to close (Ctrl+Left-click), and then click Close Window(s). It closes the windows you selected and leaves the rest open.





04.10 Closing Just the Selected Files You Want
04.11 Understanding the File Open Location
04.12 Show Previous Versions
16h 24m remaining
04.11 Understanding the File Open Location
MENU

Tools | Options | Environment | Documents

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0035

Have you ever noticed that when you go to open a file in Visual Studio (Ctrl+O) it automatically uses the directory of the current active document?


This is controlled by the Open File Using Directory Of Currently Active Document option. You can find this at Tools | Options | Environment | Documents.


You can turn this feature off by clearing its check box, and Visual Studio then uses the DefaultFileOpenLocation from HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version> in the registry instead.


Be aware that the DefaultFileOpenLocation changes every time you successfully open a file in the Open File dialog box. However, the update is not written to the registry until you close Visual Studio.





04.11 Understanding the File Open Location
04.12 Show Previous Versions
04.13 Using Custom File Extension Associations
16h 24m remaining
04.12 Show Previous Versions
VERSIONS

2008, 2010

CODE

vstipEnv0036

NOTE
For more information about previous versions including how to activate it if you don’t currently have it turned on, go to http://windows.microsoft.com/en-US/windows-vista/Previous-versions-of-files-frequently-asked-questions.

Ever want to go back in time when you save a change to your code that you didn’t want saved? If you use source control, you are usually OK, but if you don’t, this tip is for you.

If you run a Windows Vista or later operating system (excluding Home Editions),you have an option you might not have noticed before called Show Previous Versions. It shows up in various applications, such as Notepad, as shown in the following illustration.


You can also see this option in the Open Project dialog box as well.

When you click Show Previous Versions, you can see prior versions of the current directory you are in, as shown in the following illustration.


Now you can open previous versions of solutions, projects, files, and so forth, and do what you like.





04.12 Show Previous Versions
04.13 Using Custom File Extension Associations
5. Finding Things
16h 24m remaining
04.13 Using Custom File Extension Associations
WINDOWS

Alt,T, O

MENU

Tools | Options | Text Editor | File Extension

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0038

If you have a custom file extension that you would like to associate with an editing experience, just go to Tools | Options | Text Editor | File Extension to see the options shown in the following illustration.


Simply type in your extension and the editing experience you want to have when it is opened. In the following example, I have a .cool extension that is associated with the Script Editor:


When I click Add, as shown in the preceding illustration, the following information is added to the overall list:


Notice that you can select any item in the list, modify the extension and/or editor, and then click Apply to save the changes. Additionally, you can click Remove to take any entry out of the list.





04.13 Using Custom File Extension Associations
