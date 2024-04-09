
5. Finding Things
05.01 Repeat Your Last Search
16h 24m remaining
Chapter 5. Finding Things
“I am in hopes, then, that we may find the object of our search thus. I imagine that our state, being rightly organized, is a perfectly good state.”

— Plato “The Republic”
It’s very frustrating when you are looking for something in your code and can’t find it. This can range from a simple method definition to a complex set of classes in the .NET Framework, and everything in between. This chapter explores how to use the various search features in Visual Studio.

The ability to find information and then act on that information in some way is one of the central keys to creating good code. When we search for or replace code with complex criteria, our mastery of the various Find dialog boxes becomes the difference between a few minutes or several hours of work.





5. Finding Things
05.01 Repeat Your Last Search
05.02 Using Quick Find
16h 24m remaining
05.01 Repeat Your Last Search
DEFAULT

F3 (next); Shift+F3 (previous)

VISUAL BASIC 6

F3 (next); Shift+F3 (previous)

VISUAL C# 2005

F3 (next); Shift+F3 (previous)

VISUAL C++ 2

F3 (next); Shift+F3 (previous)

VISUAL C++ 6

F3 (next); Shift+F3 (previous)

VISUAL STUDIO 6

F3 (next); Shift+F3 (previous)

WINDOWS

[no shortcut]

COMMAND

Edit.FindNext; Edit.FindPrevious

VERSIONS

2005, 2008, 2010

CODE

vstipFind0004

After you perform a Find operation, you can quickly repeat that find. The following steps show you how.

Verify that your last Find shows up in the Find combo box on the Standard toolbar (usually located toward the upper right of your screen).


Press F3 (next) or Shift+F3 (previous) to move through the results.

Continue pressing F3 (next) or Shift+F3 (previous) as needed to find what you are looking for.





05.01 Repeat Your Last Search
05.02 Using Quick Find
05.03 Using a Simple Quick Replace
16h 24m remaining
05.02 Using Quick Find
DEFAULT

Ctrl+F

VISUAL BASIC 6

Ctrl+F

VISUAL C# 2005

Ctrl+F

VISUAL C++ 2

Alt+F3

VISUAL C++ 6

Ctrl+F

VISUAL STUDIO 6

Ctrl+F

WINDOWS

Alt, E, F, F

MENU

Edit | Find and Replace | Quick Find

COMMAND

Edit.Find

VERSIONS

2005, 2008, 2010

CODE

vstipFind0007

There’s more to Quick Find than meets the eye. The first thing to understand is that this is a tool window, so it can be moved and docked like any other tool window. Press Ctrl+F to bring up Quick Find.


The Quick Find drop-down menu lets you choose what type of find you want to do:


Find What
For this discussion, we want to focus only on Quick Find, but each of these items comes with its own set of options. The Find What area is used to determine what you want to find:


You can type what to look for in the drop-down combo box, or you can choose from the list of previous searches:


Don’t worry about the arrow button to the right of the drop-down combo box (not shown here)—we will get to that later.

Look In
Next is the Look In area. It’s used to determine the scope of your search:


Most of the options are pretty self-explanatory, but we have a couple of key things to know, as follows:

The Current Project and Entire Solution actions search files whether they are open or closed.

Current Block is a little misleading because it doesn’t search the current block but the entire method you are currently in.

Find Options
The Find Options area is where the fun really happens:


Following is a run-down of these options:

Match case
This option makes your search case-specific. Searching for elocal would show “elocal” but not “eLocal” or any other variant.

Match whole word
By default, your search is a “contains” operation and therefore finds a result anywhere the word exists. For example, searching for “elocal” finds “elocal” and “elocalstuff”, and so on. This option restricts the search to only the word by itself. So, in this example, it finds “elocal” but not “elocalstuff.”

Search up
Ordinarily, the search starts from the current cursor location and searches down in the current document. You can use this option to search up from the current cursor location instead.

Use
This option is a lot more interesting and requires a bit of explanation. When you select this, you get to choose between Regular Expressions and Wildcards:


When you use this option, it automatically enables the Expression Builder button to the right of the Find What combo box:


Regular expressions
Whether or not you are familiar with regular expressions, Visual Studio has its own syntax, so be aware of the differences. The following illustration shows what options the Expression Builder button provides you when Regular Expressions is selected.


NOTE
To see the details of the regular expression syntax available in Visual Studio, see the topic “Regular Expressions (Visual Studio)” at http://msdn.microsoft.com/en-us/library/2k3te2cs.aspx.

Wildcards
These aren’t as advanced as regular expressions but are more familiar to people. They allow you to use special characters to represent one or more letters. More information about wildcard searches can be found at http://msdn.microsoft.com/en-us/library/afy96z92.aspx. The following illustration shows what options the Expression Builder button provides when Wildcards is selected.


Buttons
Finally, we have the two buttons at the bottom of the Quick Find tool window:


Find Next
Keeps going to the next instance of the search term you are looking for until it reaches your original starting point.

Bookmark All
Automatically places a bookmark at every location where the search term is found. Use this with caution because it can definitely cause a large number of bookmarks to be created.





05.02 Using Quick Find
05.03 Using a Simple Quick Replace
05.04 Hide the Quick Find and Quick Replace Tool Window After the First Match
16h 24m remaining
05.03 Using a Simple Quick Replace
DEFAULT

Ctrl+H

VISUAL BASIC 6

Ctrl+H

VISUAL C# 2005

Ctrl+H

VISUAL C++ 2

Ctrl+H

VISUAL C++ 6

Ctrl+H

VISUAL STUDIO 6

Ctrl+H

WINDOWS

Alt, E, F, R

MENU

Edit | Find and Replace | Quick Replace

COMMAND

Edit.Replace

VERSIONS

2005, 2008, 2010

CODE

vstipFind0008

Previously, we looked at Quick Find, and now we will look at Quick Replace. They are almost exactly the same except for the replace operation itself. For that reason, I will not repeat all the options here but refer you back to vstipFind0007 (05.02 Using Quick Find, page 172), for most of the details.

Press Ctrl+H to bring up Quick Replace:


This is a tool window, so it can be docked like any other tool window, pretty much anywhere you want. Notice that the Quick Replace drop-down menu lets you choose what type of replace you want to do:


For this discussion, let’s focus only on Quick Replace. The Find What area is used to determine what you want to find:


The Replace With area functions exactly the same way, but it takes the text that you want to be used to replace the Find What text with:


The Look In and Find Options function the same way as using Quick Find and are explained in vstipFind0007 (05.02 Using Quick Find, page 172).

Finally, we have the three buttons at the bottom of the Quick Replace tool window:


Find Next—Selects the next instance of the search term you are looking for until it reaches your original starting point.

Replace—Replaces the currently selected item from Find What by using the text in Replace With.

Replace All—Replaces all instances of Find What by using the text in Replace With. This produces a dialog box that shows how many replacements were made:


Make sure to pay attention to this value because it might be higher (or lower) than expected and might require further investigation. If you make a mistake, you can always undo a Replace All:






05.03 Using a Simple Quick Replace
05.04 Hide the Quick Find and Quick Replace Tool Window After the First Match
05.05 Undo Quick Replace and Replace in Files
16h 24m remaining
05.04 Hide the Quick Find and Quick Replace Tool Window After the First Match
WINDOWS

Alt, T, O

MENU

Tools | Options | Environment | Find and Replace

VERSIONS

2005, 2008, 2010

CODE

vstipFind0010

When using the Quick Find or the Quick Replace tool window, you have an option to make the window disappear after the first match. This can be useful when you want to use your shortcut keys after the first match is found.

Just go to Tools | Options | Environment | Find And Replace, and then select the Hide Find And Replace Window After A Match Is Located For Quick Find Or Quick Replace check box.note

Get Link
link
table of contents
search
Settings





05.04 Hide the Quick Find and Quick Replace Tool Window After the First Match
05.05 Undo Quick Replace and Replace in Files
05.06 Using the Find Combo Box Keyboard Shortcuts
16h 24m remaining
05.05 Undo Quick Replace and Replace in Files
DEFAULT

Ctrl+Z; Alt+Backspace

VISUAL BASIC 6

Ctrl+Z; Alt+Backspace

VISUAL C# 2005

Ctrl+Z; Alt+Backspace

VISUAL C++ 2

Ctrl+Z; Alt+Backspace

VISUAL C++ 6

Ctrl+Z; Alt+Backspace

VISUAL STUDIO 6

Ctrl+Z; Alt+Backspace

WINDOWS

Alt,E, U

MENU

Edit | Undo

COMMAND

Edit.Undo

VERSIONS

2005, 2008, 2010

CODE

vstipFind0020

When using Find And Replace, people often wonder under what conditions you can undo the changes. Because performing a Find Next and Replace operation is very straightforward and easy to undo, let’s focus on how to undo the Replace All operations. Following is a summary of the conditions that allow undo to happen.

Quick Replace (Ctrl+H)
Let’s assume we’re choosing the Quick Replace option with the Look In option set to Current Project or Entire Solution:


A Replace All operation, by default, opens documents and marks them by putting an asterisk in the file name tab so that you can undo the changes:


When we undo (Ctrl+Z), it reverses all the changes made. In this case, it undoes all eleven changes:


From the toolbar, the following entry appears in the undo stack:


Replace in Files (Ctrl+Shift+H)
If we perform a Replace in Files operation with Look In set to Current Project, Entire Solution, or Visual C++ Include Directories, we see the following dialog box:


As shown in the preceding illustration, notice the option called Keep Modified Files Open After Replace All. If we do not select this option and click Replace All, we get the following message:


Checking the Replace All Will Open All Files With Changes For Editing makes it possible to undo all the changes made:


The entry in the undo stack on the toolbar looks like this:


So, as you can see, it is quite easy to undo the changes made by Quick Replace and Replace in Files.





05.05 Undo Quick Replace and Replace in Files
05.06 Using the Find Combo Box Keyboard Shortcuts
05.07 Using Incremental Search
16h 24m remaining
05.06 Using the Find Combo Box Keyboard Shortcuts
DEFAULT

Ctrl+D (find); Ctrl+/ (run command); Ctrl+G (go to line); Ctrl+Shift+G (go to file); F9 (set breakpoint)

VISUAL BASIC 6

[no shortcut] (find); [no shortcut] (run command); [no shortcut] (go to line); Ctrl+Shift+G (go to file); F9 (set breakpoint)

VISUAL C# 2005

Ctrl+/ (find); [no shortcut] (run command); Ctrl+G (go to line); Ctrl+Shift+G (go to file); F9 (set breakpoint)

VISUAL C++ 2

Ctrl+F (find); ALT+A (find); Ctrl+D (find); Ctrl+/ (run command); Ctrl+G (go to line); Ctrl+Shift+G (go to file); F9 (set breakpoint); Ctrl+Shift+F9 (set breakpoint)

VISUAL C++ 6

Ctrl+D (find); Ctrl+/ (run command); Ctrl+G (go to line); Ctrl+Shift+G (go to file); F9 (set breakpoint)

VISUAL STUDIO 6

Ctrl+Shift+F (find); Ctrl+/ (run command); Ctrl+G (go to line); Ctrl+Shift+G (go to file); F9 (set breakpoint)

COMMAND

Edit.GoToFindCombo; Tools.GoToCommandLine; Edit.GoTo; Edit.OpenFile; Debug.ToggleBreakpoint

VERSIONS

2005, 2008, 2010

CODE

vstipFind0019

We have looked at the Find Combo box in a variety of places. Recall that this toolbar item is located on the standard toolbar by default:


I thought it would be a good idea to consolidate the keyboard shortcuts of this wonderful tool into one place.

Find (Ctrl+D)
First and foremost, the Find / Command box is used to find strings. Just press Ctrl+D to go to the box and type in your search term:


When you press Enter, it searches for your string by using the settings from Quick Find (Ctrl+F) as it searches. Pressing Enter again finds the next instance, and so on.

Run Command (Ctrl+/)
The Find / Command box is also used to run commands. For more information about commands, see vstipTool0067 (03.19 Understanding Commands: Simple Commands, page 110). Just press Ctrl+/ to go to the box, and type in your command:


When you press Enter, it runs the command you typed.

Go To Line (Ctrl+G)
When in the Find / Command box, you can type any line number:


Then press Ctrl+G, and you are taken to the line number that you entered.

Go To File (Ctrl+Shift+G)
Type in any file name that is in your solution or in the INCLUDE path:


Use Ctrl+Shift+G to go to the file. If the file isn’t already open, this command opens the file first.

Set a Breakpoint (F9)
Enter any function name:


Then press F9, and Visual Studio sets a breakpoint on the function:


A couple of things to note:

Pressing F9 again does not turn off the breakpoint—that is, it’s not a toggle.

This feature works only with open documents.





05.06 Using the Find Combo Box Keyboard Shortcuts
05.07 Using Incremental Search
05.08 Search the Currently Selected String Without the Find Window
16h 24m remaining
05.07 Using Incremental Search
DEFAULT

Ctrl+I

VISUAL BASIC 6

Alt+I

VISUAL C# 2005

Ctrl+I

VISUAL C++ 2

Ctrl+I

VISUAL C++ 6

Ctrl+I

VISUAL STUDIO 6

[no shortcut]

WINDOWS

Alt,E, V, S

MENU

Edit | Advanced | Incremental Search

COMMAND

Edit.IncrementalSearch

VERSIONS

2005, 2008, 2010

CODE

vstipFind0001

Incremental search is a powerful feature to use when you want to keep your cursor in the editor while searching in the current document. It allows you to keep your hands on the keyboard without having to use the mouse for any dialog boxes.

To conduct an incremental search, press Ctrl+I and start typing the text you are searching for. You’ll see the cursor in the editor jump to the first match, highlighting the current search string, and your mouse cursor turns into a pair of binoculars with an arrow pointing in the direction (up or down) you are searching:


If you look at the status bar, you can see the details of your incremental search:


Press Ctrl+I again to jump to the next occurrence of the search string:


The following table lists all the options you can leverage while in this mode:

ACTION

SHORTCUT

Move to the next match in the file

Ctrl+I

Reverse the direction of the search

Ctrl+Shift+I

Remove a character from the search string

Backspace

Stop the incremental search

Esc





05.07 Using Incremental Search
05.08 Search the Currently Selected String Without the Find Window
05.09 Find In Files: Find Options
16h 24m remaining
05.08 Search the Currently Selected String Without the Find Window
DEFAULT

Ctrl+F3 (next); Ctrl+Shift+F3 (previous)

VISUAL BASIC 6

Ctrl+F3 (next); Ctrl+Shift+F3 (previous)

VISUAL C# 2005

Ctrl+F3 (next); Ctrl+Shift+F3 (previous)

VISUAL C++ 2

Ctrl+F3 (next); Ctrl+Shift+F3 (previous)

VISUAL C++ 6

Ctrl+F3 (next); Ctrl+Shift+F3 (previous)

VISUAL STUDIO 6

Ctrl+F3 (next); Ctrl+Shift+F3 (previous)

WINDOWS

[no shortcut]

COMMAND

Edit.FindNextSelected; Edit.FindPreviousSelected

VERSIONS

2005, 2008, 2010

CODE

vstipFind0003

Ever just want to find the next (or previous) instance of a word quickly without using the Quick Find dialog box? Well, it’s easy.

Put the cursor in any word you want to look for:


Press Ctrl+F3 (next) or Ctrl+Shift+F3 (previous) to start a find:


You can also see a message in the status bar showing you the parameters of the search:


NOTE
As you can see, the find has certain settings already in place. These settings can be changed in the Find dialog box (Ctrl+F).

After the Find has started, just press F3 (next) or Shift+F3 (previous) to continue searching as you normally would with a Quick Find.





05.08 Search the Currently Selected String Without the Find Window
05.09 Find In Files: Find Options
05.10 Find In Files: Result Options
16h 24m remaining
05.09 Find In Files: Find Options
DEFAULT

Ctrl+Shift+F

VISUAL BASIC 6

Ctrl+Shift+F

VISUAL C# 2005

Ctrl+Shift+F

VISUAL C++ 2

Ctrl+Shift+F

VISUAL C++ 6

Ctrl+Shift+F

VISUAL STUDIO 6

[no shortcut]

WINDOWS

Alt,E, F, I

MENU

Edit | Find and Replace | Find in Files

COMMAND

Edit.FindinFiles

VERSIONS

2005, 2008, 2010

CODE

vstipFind0013

When working in Visual Studio, you often need to search for information in files. Find In Files allows you to quickly locate information you need. Let’s begin by looking at the options you can set to find information in files (Ctrl+Shift+F).

NOTE
If you have already read vstipFind0007 (05.02 Using Quick Find, page 172), you might want to just skim this one because much of the information is repeated here for those who might not have read the prior tip.


Find What
The Find What combo box lets you type in text to find or choose from previous text that has been searched:


This area is very closely bound to all but one of the options under Find Options:


Following is an overview of these options:

Match case
This option makes your search case-specific. Searching for elocal would show “elocal” but not “eLocal” or any other variant.

Match whole word
By default, the search is a “contains” operation and finds the word anywhere it exists. For example, searching for “elocal” finds “elocal” and “elocalstuff”, and so on.

Use
This is a lot more interesting and requires a bit of explanation. When you select this, you get to choose between Regular Expressions and Wildcards:


When you use this option, it automatically enables the Expression Builder button to the right of the Find What combo box:


Regular expressions
Whether or not you are familiar with regular expressions, Visual Studio has its own syntax, so be aware of the differences. The following illustration shows the options provided by the Expression Builder button when you have selected Regular Expressions:


NOTE
To see the details of the regular expression syntax available in Visual Studio, see the topic “Regular Expressions (Visual Studio)” at http://msdn.microsoft.com/en-us/library/2k3te2cs.aspx.

Wildcards
This option isn’t as advanced as regular expressions but is more familiar to most people. It allows you to use special characters to represent one or more letters. For more information about wildcard searches, see “Wildcards (Visual Studio) at http://msdn.microsoft.com/en-us/library/afy96z92.aspx. The following illustration shows the options provided by the Expression Builder button when Wildcards is selected:


Look in
The Look in drop-down list lets you specify what areas you want to look in:


Most of the options are pretty self-explanatory. The Current Project and Entire Solution commands search files whether they are open or closed.

The Choose Search Folders and Look At These File Types options are discussed in vstipFind0005 (AX.47 Customize the Files to Search with Find In Files, in Appendix B [http://go.microsoft.com/FWLink/?Linkid=223758]):



Include sub-folders
This option searches the current directory and all subdirectories and shows up only if you use the Visual C++ Include Directories or Choose Search Folders options:






05.09 Find In Files: Find Options
05.10 Find In Files: Result Options
05.11 Replace In Files: Basic Options
16h 24m remaining
05.10 Find In Files: Result Options
DEFAULT

Ctrl+Shift+F (find); F8 (next); Shift+F8 (previous);

VISUAL BASIC 6

Ctrl+Shift+F (find);[no shortcut] (next); [no shortcut] (previous);

VISUAL C# 2005

Ctrl+Shift+F (find); F8 (next); Shift+F8 (previous);

VISUAL C++ 2

Ctrl+Shift+F (find); F4 (next); Shift+F4 (previous);

VISUAL C++ 6

Ctrl+Shift+F (find); F8 (next); F4 (next); Shift+F8 (previous); Shift+F4 (previous);

VISUAL STUDIO 6

[no shortcut] (find); F8 (next); F12 (next); Shift+F8 (previous); Shift+F12 (previous);

WINDOWS

Alt,E, F, I (find)

MENU

Edit | Find and Replace | Find in Files

COMMAND

Edit.FindinFiles; Edit.GoToNextLocation; Edit.GoToPrevLocation; Edit.ClearFindResults1; Edit.ClearFindResults2

VERSIONS

2005, 2008, 2010

CODE

vstipFind0014

When working with Find In Files (Ctrl+Shift+F), you can choose several result options:


Find Results [1,2] Window
The Find Results windows allow you to view and navigate the results of a find operation. Each time you use Find, the results replace the contents of the previous find. This is why two windows are available—so that you avoid overwriting a find result you might want to keep.

Navigation
You can use F8 and Shift+F8 to go to the next and previous items in the results list. This operation also shows the line of code where the item was found, which includes opening closed files if needed:

The Find Results windows have toolbar buttons that allow you to go to the next and previous items as well:


Clear All
You can manually clear the results in a Find Results window by clicking Clear All:


Display File Names Only
The operation shows only the files names in your results and not the full path and additional information. This means the result set is much smaller.

Before:


After:


You can do much more with the displayed results than this. See vstipFind0002 (05.17 Customize Results in Find In Files Searches, page 206) for more information.

Keep Modified Files Open After Replace All
This option doesn’t apply to Find In Files and is always disabled when doing a find operation. You can see this option when using the Replace In Files option.





05.10 Find In Files: Result Options
05.11 Replace In Files: Basic Options
05.12 Go To Definition for Cascading Style Sheets
16h 24m remaining
05.11 Replace In Files: Basic Options
DEFAULT

Ctrl+Shift+H

VISUAL BASIC 6

Ctrl+Shift+H

VISUAL C# 2005

Ctrl+Shift+H

VISUAL C++ 2

Ctrl+Shift+H

VISUAL C++ 6

Ctrl+Shift+H

VISUAL STUDIO 6

Ctrl+Shift+H

WINDOWS

Alt,E, F, S

MENU

Edit | Find and Replace | Replace in Files

COMMAND

Edit.ReplaceinFiles

VERSIONS

2005, 2008, 2010

CODE

vstipFind0015

Did you know that you can replace text in files, whether or not they are open, by choosing Replace In Files (Ctrl+Shift+H)? Let’s take a look at what can be done.

Find Options

Fortunately, the majority of find options are the same for Replace In Files as they are for Find In Files (see vstipFind0013, 05.09 Find In Files: Find Options, on page 186), so you can leverage those skills again here.

Replace With

This area is the most interesting piece of the Replace In Files dialog box. It can be as simple as a literal string (replacing “static” with “Franc”, for example) or very, very complex. In simple situations, you just want to use the literal text as a replacement to the Find What text.

Result Options
Again, these options are exactly like the Find In Files options (vstipTool0014, “Find In Files: Result Options,” page 158) with the exception of the Keep Modified Files Open After Replace All option:


This option makes it possible to keep modified files open after they are changed so that you can review the change or make additional manual changes. This is particularly useful when you are modifying closed files and want to look inside files that were modified.

Execution
After all the options have been set, we can execute find and replace operations by using the following four buttons:


Find Next
Used to find the next instance of the Find What search string.

Replace
Used to replace the current instance of the Find What string with the Replace With string and then find the next instance.

Replace All
Used to replace all instances of the Find What string with the Replace With string, in all files within the Look In scope.

WARNING
The Replace All option can get you into big trouble if you don’t pay attention to the scope of Look In.

Skip File
Available when the Look In list includes multiple files. Choose this button if you do not want to search or modify the current file. The search continues in the next file on the Look In list.





05.11 Replace In Files: Basic Options
05.12 Go To Definition for Cascading Style Sheets
05.13 How to Use Navigate To
16h 24m remaining
05.12 Go To Definition for Cascading Style Sheets
DEFAULT

F12

VISUAL BASIC 6

F12; Shift+F2

VISUAL C# 2005

F12

VISUAL C++ 2

F11; Alt+F1

VISUAL C++ 6

F12

VISUAL STUDIO 6

[no shortcut]

WINDOWS

[no shortcut]

COMMAND

Edit.GoToDefinition

VERSIONS

2008, 2010

CODE

vstipFind0021

For those who are familiar with using Go To Definition in your code, you might not be aware that you can use the same technique to go to your Cascading Style Sheet (CSS) definition class for attributes. Just put your cursor inside the class name:


Then press F12 (or right-click and choose Go To Definition). It instantly takes you to the CSS definition and highlights it:


Now you can review the definition and make changes as you see fit.





05.12 Go To Definition for Cascading Style Sheets
05.13 How to Use Navigate To
05.14 Understanding Find Symbol
16h 24m remaining
05.13 How to Use Navigate To
DEFAULT

Ctrl+, [comma]

VISUAL BASIC 6

Ctrl+, [comma]

VISUAL C# 2005

Ctrl+, [comma]

VISUAL C++ 2

Ctrl+, [comma]

VISUAL C++ 6

Ctrl+, [comma]

VISUAL STUDIO 6

Ctrl+, [comma]

WINDOWS

Alt,E, .[period]

MENU

Edit | Navigate To

COMMAND

Edit.NavigateTo

VERSIONS

2010

CODE

vstipTool0006

The Navigate To dialog box is very useful for finding symbols. The search is an “includes” operation, so it shows you symbols that contain the letters you type. Just put in what you are looking for:


Notice that the search is not case-specific. However, you might notice a surprise in this dialog box. Watch what happens when you put in ACM:


It pays attention to Pascal Case. There is also summary information at the bottom of this dialog box:


You’re probably wondering about the Hide External Items option as well. When selected, only the local project is examined for symbols, instead of your project plus every library you reference.

Also, notice that the Navigate To syntax does not support special logic or special characters such as the following:

Wildcard matching

Boolean logic operators

Regular expressions





05.13 How to Use Navigate To
05.14 Understanding Find Symbol
05.15 Find Symbol Results Shortcuts
16h 24m remaining
05.14 Understanding Find Symbol
DEFAULT

Alt+F12

VISUAL BASIC 6

Alt+F12

VISUAL C# 2005

Alt+F12

VISUAL C++ 2

Alt+F12; Ctrl+F11; Ctrl+Alt+F11

VISUAL C++ 6

Alt+F12; Ctrl+Shift+Y

VISUAL STUDIO 6

Alt+F12

WINDOWS

Alt,E, F, Y

MENU

Edit | Find and Replace | Find Symbol

COMMAND

Edit.FindSymbol

VERSIONS

2005, 2008, 2010

CODE

vstipFind0011

You can quickly search for symbols (objects, definitions, and references) by using the Find Symbol dialog box (Alt+F12):


Find What
This is pretty straightforward; you just type in the search string you are looking for.

NOTE
You can also get to Find Symbol by using any shortcut to get to the Find and Replace dialog box and selecting Find Symbol from the drop-down list in the upper-right corner.

Look In
This indicates where you want to look:


As you can see, the Look In dialog box has a number of search options.

All Components
Includes the current solution and its referenced components, all of the .NET Framework, and any components that you have added.

Framework X / Silverlight X
Searches specific versions of the Framework for a symbol.

My Solution
Searches the current open solution.

Custom Component Set (Object Browser)
Searches the predefined custom component set in the Object Browser. See vstipTool0078 (07.40 The Object Browser: Setting the Browsing Scope, page 358) for more information.

Custom Component Set (Find Symbol)
Searches the custom component set defined in this dialog box. You edit the list of components by clicking the ellipsis in the dialog box:


The Edit Custom Component Set dialog box allows you to pick components from a variety of areas to have a specialized search experience when looking for symbols. It allows for a very refined search capability:


Look In References
Displays references in the projects within the current browsing scope.

Find Options
Match
Sets criteria for the search string when finding matches.

Whole Word
Finds the complete word only, not partial matches.

Prefix
Finds results where the search string is at the beginning of the result.

Substring
Finds results where the search string is anywhere in the result.

Match Case
Finds only results that exactly match the case of the search string.

Find All
Initiates the search based on the criteria that has been set.

Search Results
When you run a search, the results look something like this:


The icons to the left of each entry indicate what type of symbol you are looking at in the results. For a complete list of icons and their meanings, see vstipTool0076 (AX.120 Class View and Object Browser Icons, in Appendix B [http://go.microsoft.com/FWLink/?Linkid=223758]) for more information.

Additionally, you can use F8 or Shift+F8 to navigate forward or backward through the results while automatically showing the location of the result as you proceed.





05.14 Understanding Find Symbol
05.15 Find Symbol Results Shortcuts
05.16 Replace in Files: Tagged Expressions
16h 24m remaining
05.15 Find Symbol Results Shortcuts
DEFAULT

F12 (go to definition); Ctrl+F12 (go to declaration); Shift+F12 (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

VISUAL BASIC 6

F12 (go to definition); Shift+F2 (go to definition); Ctrl+F12 (go to declaration); Alt+F2 (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

VISUAL C# 2005

F12 (go to definition); Ctrl+F12 (go to declaration); Shift+F12 (find all references); Ctrl+K, Ctrl+R (find all references); Ctrl+K, R (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

VISUAL C++ 2

F11 (go to definition); Alt+F1 (go to definition); [no shortcut] (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

VISUAL C++ 6

F12 (go to definition); Ctrl+F12 (go to declaration); Ctrl+Alt+F12 (go to declaration); [no shortcut] (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

VISUAL STUDIO 6

[no shortcut] (go to definition); Ctrl+F12 (go to declaration); [no shortcut] (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

WINDOWS

Alt,E, C (copy)

MENU

Edit | Copy

COMMAND

Edit.GoToDefinition; Edit.GoToDeclaration; Edit.FindAllReferences;View.BrowseDefinition;Edit.Copy;Edit.ClearAll

VERSIONS

2005, 2008, 2010

CODE

vstipFind0012

To locate any symbol, you can quickly leverage a series of commands to help you. The nice thing about these commands is that many of them work both in the Find Symbol Results window and in the code editor.

Go To Definition (F12)
This command takes you to the definition of the symbol in your code, if one is available.



Go To Declaration (Ctrl+F12)
NOTE
The information in this section applies to C++ only.

This command takes you to the declaration of the symbol in your code, if one is available.

Go To Reference (Shift+F12)
This command works for any symbol:


This command finds all references to that symbol:


If you are using the Find Symbol Results window, you can make this much easier by simply expanding a node in the window. It automatically shows all references:


If no references are found, it tells you that also:


Browse Definition
For any symbol in your results, simply right-click and choose Browse Definition:


Clicking Browse Definition takes you to the primary node (typically top level) for the symbol in the Object Browser, which can be particularly useful for deeper examination:


Copy (Ctrl+C)
Allows you to copy the fully qualified name for the selected symbol to the clipboard. You can then paste the code as text into the code editor.

Clear All
Clears the Find Symbol Results window.





05.14 Understanding Find Symbol
05.15 Find Symbol Results Shortcuts
05.16 Replace in Files: Tagged Expressions
16h 24m remaining
05.15 Find Symbol Results Shortcuts
DEFAULT

F12 (go to definition); Ctrl+F12 (go to declaration); Shift+F12 (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

VISUAL BASIC 6

F12 (go to definition); Shift+F2 (go to definition); Ctrl+F12 (go to declaration); Alt+F2 (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

VISUAL C# 2005

F12 (go to definition); Ctrl+F12 (go to declaration); Shift+F12 (find all references); Ctrl+K, Ctrl+R (find all references); Ctrl+K, R (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

VISUAL C++ 2

F11 (go to definition); Alt+F1 (go to definition); [no shortcut] (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

VISUAL C++ 6

F12 (go to definition); Ctrl+F12 (go to declaration); Ctrl+Alt+F12 (go to declaration); [no shortcut] (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

VISUAL STUDIO 6

[no shortcut] (go to definition); Ctrl+F12 (go to declaration); [no shortcut] (find all references); Ctrl+C (copy); Ctrl+Insert (copy);

WINDOWS

Alt,E, C (copy)

MENU

Edit | Copy

COMMAND

Edit.GoToDefinition; Edit.GoToDeclaration; Edit.FindAllReferences;View.BrowseDefinition;Edit.Copy;Edit.ClearAll

VERSIONS

2005, 2008, 2010

CODE

vstipFind0012

To locate any symbol, you can quickly leverage a series of commands to help you. The nice thing about these commands is that many of them work both in the Find Symbol Results window and in the code editor.

Go To Definition (F12)
This command takes you to the definition of the symbol in your code, if one is available.



Go To Declaration (Ctrl+F12)
NOTE
The information in this section applies to C++ only.

This command takes you to the declaration of the symbol in your code, if one is available.

Go To Reference (Shift+F12)
This command works for any symbol:


This command finds all references to that symbol:


If you are using the Find Symbol Results window, you can make this much easier by simply expanding a node in the window. It automatically shows all references:


If no references are found, it tells you that also:


Browse Definition
For any symbol in your results, simply right-click and choose Browse Definition:


Clicking Browse Definition takes you to the primary node (typically top level) for the symbol in the Object Browser, which can be particularly useful for deeper examination:


Copy (Ctrl+C)
Allows you to copy the fully qualified name for the selected symbol to the clipboard. You can then paste the code as text into the code editor.

Clear All
Clears the Find Symbol Results window.





05.15 Find Symbol Results Shortcuts
05.16 Replace in Files: Tagged Expressions
05.17 Customize Results in Find In Files Searches
16h 24m remaining
05.16 Replace in Files: Tagged Expressions
DEFAULT

Ctrl+Shift+H

VISUAL BASIC 6

Ctrl+Shift+H

VISUAL C# 2005

Ctrl+Shift+H

VISUAL C++ 2

Ctrl+Shift+H

VISUAL C++ 6

Ctrl+Shift+H

VISUAL STUDIO 6

Ctrl+Shift+H

WINDOWS

Alt,E, F, S

MENU

Edit | Find and Replace | Replace in Files

COMMAND

Edit.ReplaceinFiles

VERSIONS

2005, 2008, 2010

CODE

vstipFind0016

As mentioned in vstipFind0015 (05.11 Replace In Files: Basic Options, page 192), the Replace With area is the most interesting piece of the Replace In Files dialog box. It can be as simple as a literal string replacement:


Under normal situations, this is just the literal text you want to use as a replacement for the Find What text. However, suppose you choose to use regular expressions:


This enables the Expression Builder:


These options are not like the builder options you get in the Find What area:


In addition to being able to use any of the regular expression characters, you can refer to the original text and any tagged expressions.

Example
The best way to show how tagged expressions work is with an example. Let’s assume you have the following text:


And you use the following options:


Notice the curly brackets around “jones”? That denotes a tagged expression. Every time you use the brackets, it creates a tagged expression that is numbered (beginning with 1). So, in this example, we are looking for “bubba{jones}” and replacing it with tagged expression 1 (which is just “jones”). Also, notice the notation used to refer to the tagged expression: \n, where n is the tagged expression we want.

When I do my replacements, this is the result:


We can take this further. Now we want to turn “bubbajones” into “jonesbubba,” so we can use the following settings:


So now we are looking for “{bubba}{jones},” which creates tagged expression 1 (“bubba”) and tagged expression 2 (“jones”). At this point, it’s simply a matter of replacing with the expressions switched around (“\2\1”), and we get the following:


Of course, this can get much more complex when using regular expressions, so you definitely need to spend some time learning how to fully leverage these features.note

Get Link
link
table of contents
search
Settings





05.16 Replace in Files: Tagged Expressions
05.17 Customize Results in Find In Files Searches
6. Writing Code
16h 24m remaining
05.17 Customize Results in Find In Files Searches
DEFAULT

Ctrl+Shift+F

VISUAL BASIC 6

Ctrl+Shift+F

VISUAL C# 2005

Ctrl+Shift+F

VISUAL C++ 2

Ctrl+Shift+F

VISUAL C++ 6

Ctrl+Shift+F

VISUAL STUDIO 6

[no shortcut]

WINDOWS

Alt,E, F, I

MENU

Edit | Find and Replace | Find in Files

COMMAND

Edit.FindinFiles

VERSIONS

2005, 2008, 2010

CODE

vstipFind0002

You can customize your Find In Files results to just about any format you can imagine. For example, let’s say you don’t want to view the entire file path shown in the Find Results tool window:


Instead, you want this:


You can easily make this change. Just follow these instructions:

WARNING
This involves modifying the registry, so use this tip at your own risk.

Open RegEdit.exe.

Go to HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Find.

Add a new string called Find Result Format, with a value of $f$e($l,$c):$t\r\n.


In Visual Studio, run a Find In Files search.

NOTE
You do not need to restart Visual Studio to see the changes made in the registry, which is great for testing different string combinations.

Variables
For your reference, the following are valid values you can use when creating your own custom values.

Files
$p path

$f filename

$v drive/unc share

$d directory

$n name

$e .extension

Location
$l line

$c col

$x end col if on first line, else end of first line

$L span end line

$C span end col

Text
$0 matched text

$t text of first line

$s summary of hit

$T text of spanned lines

Char
\n newline

\s space

\t tab

\\ backslash

\$ $





05.17 Customize Results in Find In Files Searches
