
7. Debugging
07.01 Setting a Breakpoint with Code
16h 24m remaining
Chapter 7. Debugging
“It has been just so in all my inventions. The first step is an intuition—and comes with a burst, then difficulties arise. This thing that gives out and then that—‘Bugs’ as such little faults and difficulties are called show themselves and months of anxious watching, study and labor are requisite before commercial success—or failure—is certainly reached.”

— Thomas Alva Edison Letter to Theodore Puskas (18 Nov 1878)
As a developer, you spend a great deal of time debugging. Visual Studio has long provided great tools for helping find errors in your code. This chapter focuses on showing how to take full advantage of common items like the Locals and Autos windows as well as exploring more advanced techniques such as setting tracepoints in the Call Stack window.

Additionally, lots of great new features in Visual Studio 2010 can help with your troubleshooting efforts. Major changes have been made to the Breakpoints window, and new DataTips are available to provide information when and where you need it. There is no shortage of great techniques to cut down the time you spend finding problems in your code.





7. Debugging
07.01 Setting a Breakpoint with Code
07.02 Using Ctrl+Alt+B to Open the Breakpoints Window
16h 24m remaining
07.01 Setting a Breakpoint with Code
VERSIONS

2005, 2008, 2010

CODE

vstipDebug0036

Sometimes you want to have clear breakpoints in your code that travel with the source. You can do this quite easily.

Compiler Directive
In C# and VB, you need to set a compiler option that hits the breakpoint only when debugging. If you don’t, your release code continues to hit the code-based breakpoint, which is generally considered a bad thing. To do this, you set the #If DEBUG compiler option, as you can see in each of the following code samples.

C#
In C#, you set a breakpoint by using the System.Diagnostics.Debugger.Break method:


VB
In VB, you set a breakpoint by using the Stop command:


Now you can use code to set breakpoints. Just as an aside, breakpoints set in this way do not show up in the Breakpoints window.

C++
In C++, it’s a very similar situation. Based on the type of C++ project you are creating, these commands can change slightly; but with native C++, you can use the __debugbreak command with the #if _DEBUG compiler option:






07.01 Setting a Breakpoint with Code
07.02 Using Ctrl+Alt+B to Open the Breakpoints Window
07.03 Adding Labels to Breakpoints
16h 24m remaining
07.02 Using Ctrl+Alt+B to Open the Breakpoints Window
DEFAULT

Ctrl+Alt+B

VISUAL BASIC 6

Ctrl+Alt+B

VISUAL C# 2005

Ctrl+Alt+B; Ctrl+D, Ctrl+B; Ctrl+D, B

VISUAL C++ 2

Ctrl+Alt+B; Ctrl+B

VISUAL C++ 6

Ctrl+Alt+B; Alt+F9

VISUAL STUDIO 6

Ctrl+B

WINDOWS

Alt, D, W, B

MENU

Debug | Windows | Breakpoints

COMMAND

Debug.Breakpoints

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0011

Use Ctrl+Alt+B to open the Breakpoints window or, if it is already open, to give it the focus.






07.02 Using Ctrl+Alt+B to Open the Breakpoints Window
07.03 Adding Labels to Breakpoints
07.04 Enable or Disable All Breakpoints
16h 24m remaining
07.03 Adding Labels to Breakpoints
DEFAULT

Alt+F9, L

VISUAL BASIC 6

Alt+F9, L

VISUAL C# 2005

Alt+F9, L

VISUAL C++ 2

Alt+F9, L

VISUAL C++ 6

[no shortcut]

VISUAL STUDIO 6

Alt+F9, L

WINDOWS

Shift+F10, A (inside Breakpoints Window)

MENU

[Context Menu] | Edit Labels

COMMAND

EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels

VERSIONS

2010

CODE

vstipDebug0001

Did you know that breakpoints in Visual Studio 2010 support labels? This tip explains how you can use them. How do labels help you? Well, first, you can now have friendly names for breakpoints to make them easier to understand. Second, you can sort by the label names. And, third, you can search the labels from the Breakpoints window. (See vstipDebug0002, 07.19 Searching Breakpoints, on page 312.)

After setting one or more breakpoints in your code, open the Breakpoint window (Ctrl+Alt+B). Notice the new Labels column:


Right-click one or more selected breakpoints to bring up the context menu, and choose Edit Labels (Alt+F9, L):


You get the following dialog box:


You can type in one (or more) labels for the breakpoint and/or select one of the labels previously used, and then click OK. You should see now your label(s):






07.03 Adding Labels to Breakpoints
07.04 Enable or Disable All Breakpoints
07.05 TODO Comments in the Task List
16h 24m remaining
07.04 Enable or Disable All Breakpoints
WINDOWS

Alt,D, N

MENU

Debug | Disable All Breakpoints; Debug | Enable All Breakpoints

COMMAND

Debug.DisableAllBreakpoints; Debug.EnableAllBreakpoints

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0018

There are times when you will want to quickly and temporarily turn off all or some of your breakpoints. This tip covers how to disable and enable your breakpoints.

You can go to Debug | Disable All Breakpoints on the menu bar, or in the Breakpoints window, you can click the Enable Or Disable All Breakpoints button:

NOTE
In Visual Studio 2010, only the breakpoints currently visible in the window are disabled when you use this option, so it is very useful for enabling or disabling a subset of your breakpoints when used with the Search feature.


The result, in either case, is the same. One or more breakpoints in the current project are disabled:


To enable them again, just go to Debug | Enable All Breakpoints on the menu bar, or click the Enable Or Disable All Breakpoints button in the Breakpoints window again:






07.04 Enable or Disable All Breakpoints
07.05 TODO Comments in the Task List
07.06 Create Custom Tokens for the Task List
16h 24m remaining
07.05 TODO Comments in the Task List
VERSIONS

2005, 2008, 2010

CODE

vstipTool0029

Have you ever written some code and want to leave a reminder to yourself to do something? Did you know about the “To Do” comment feature? It is a great feature, and because the comment goes directly in the source, everyone can have access to the information when you check in code.

So here’s how it works.

VB
In VB, you just put any comment in that begins with “todo” (case doesn’t matter):


C#
In C#, it’s the same thing (again, case doesn’t matter):


C++
The C++ version looks just like C#, but you have to explicitly turn this feature on, and the “TODO” must be all uppercase. Go to Tools | Options | Text Editor | C/C++ | Formatting | Miscellaneous, and change Enumerate Comment Tasks to True:


Whichever language you use, the result is a nice entry in your Task List dialog box:


NOTE
To see these items, you have to click the drop-down list in the Task List dialog box and choose Comments, as shown in the preceding illustration.

Like all Task List items, comments are Solution-wide in scope, so you will see all the shortcuts for the entire solution in the Task List window.





07.05 TODO Comments in the Task List
07.06 Create Custom Tokens for the Task List
07.07 Create Code Shortcuts in the Task List
16h 24m remaining
07.06 Create Custom Tokens for the Task List
WINDOWS

Alt,T, O

MENU

Tools | Options

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipTool0032

In vstipTool0029 (07.05 TODO Comments in the Task List, page 296), I showed you how to create comments that show up in the Task List:


The “TODO” part is known as a token. It’s a trigger to indicate that an item should be put in the Task List. Did you know you can create your own custom tokens? Go to Tools | Options | Environment | Task List | Tokens to see the following window:


As shown in the preceding illustration, notice the following entries in this area: HACK, TODO, UNDONE, and UnresolvedMergeConflict. By the way, UnresolvedMergeConflict is not an error; it is an actual token that you can use.

For now, let’s create a couple of our own. In the Name text box, type in the word low, set the priority to Low, and then click Add. You should see the following:


Now do the same thing again, this time using the word high and setting the priority to High:


You now have a couple of custom tokens. Add two comments to your existing code, and use the new “low” and “high” tokens:


You now see the following in the Task List:


Sharing Tokens
You can create as many tokens as you want to suit your needs, so feel free to experiment with these. Unfortunately, the tokens aren’t shared unless you export them and then someone else imports them. Go to Tools | Import And Export Settings, and export the Task List Options found under All Settings, Options, Environment:






07.06 Create Custom Tokens for the Task List
07.07 Create Code Shortcuts in the Task List
07.08 Code Definition Window
16h 24m remaining
07.07 Create Code Shortcuts in the Task List
DEFAULT

Ctrl+K, Ctrl+H

VISUAL BASIC 6

Ctrl+K, Ctrl+H

VISUAL C# 2005

Ctrl+K, Ctrl+H; Ctrl+E, Ctrl+T; Ctrl+E, T

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+K, Ctrl+H

VISUAL STUDIO 6

Ctrl+K, Ctrl+H

WINDOWS

Alt,E, K, H

MENU

Edit | Bookmarks | Add Task List Shortcut

COMMAND

Command

Edit.ToggleTaskListShortcut

VERSIONS

2005, 2008, 2010

CODE

vstipTool0030

In vstipTool0029 (07.05 TODO Comments in the Task List, page 296), I showed you how to create comments that show up in your Task List window. However, sometimes all you want is a shortcut to a line of code that you visit often. You can create shortcuts to any line of code. Just place the cursor on the line, and press Ctrl+K, Ctrl+H (toggles the shortcut on or off). This creates the shortcut glyph in the margin:


To see all your shortcuts, go to the Task List dialog (Ctrl+\, T), and choose Shortcuts from the drop-down list:


Now you should see all the shortcuts you created:


You can treat them like any other task, and you can set priority levels as well as mark them complete:


You can double-click any item to go to the line of code referenced in the shortcut, right-click, and then choose Delete to remove it from the list.

Like all Task List items, these are Solution-wide in scope, so you will see all the shortcuts for the entire solution in the Task List window.





07.07 Create Code Shortcuts in the Task List
07.08 Code Definition Window
07.09 Save Changes Before Building
16h 24m remaining
07.08 Code Definition Window
DEFAULT

Ctrl+\, Ctrl+D; Ctrl+\, D

VISUAL BASIC 6

Ctrl+\, Ctrl+D; Ctrl+\, D

VISUAL C# 2005

Ctrl+\, Ctrl+D; Ctrl+\, D; Ctrl+W, Ctrl+D; Ctrl+W, D

VISUAL C++ 2

Ctrl+\, Ctrl+D; Ctrl+\, D

VISUAL C++ 6

Ctrl+\, Ctrl+D; Ctrl+\, D; Ctrl+Shift+V

VISUAL STUDIO 6

Ctrl+\, Ctrl+D; Ctrl+\, D

WINDOWS

Alt,V, D

MENU

View | Code Definition Window

COMMAND

View.CodeDefinitionWindow

VERSIONS

2005, 2008, 2010

LANGUAGES

C++, C#

CODE

vstipTool0012

Ever want to just click on a reference and see the definition as you go without having to use Go To Definition (F12)? For quite some time, the Code Definition window has been available to use just for this purpose. Go to View | Code Definition Window, and you see the following:


Now click on any symbol you would like to get a definition for, and you should get something like this:


The Code Definition window provides you with an instant, read-only view of your definition so that you don’t have to look for it when you are looking at a symbol.





07.08 Code Definition Window
07.09 Save Changes Before Building
07.10 Navigate Errors in the Error List
16h 24m remaining
07.09 Save Changes Before Building
WINDOWS

Alt,T, O

MENU

Tools | Options | Projects and Solutions | Build and Run

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipProj0015

In Tools | Options | Projects and Solutions | Build And Run, notice the Before Building option:


The default setting is to save all changes to the solution file and to save all project files that changed since the last build, but other options are also available:


Save Changes To Open Documents Only
This option does what it says and saves changes to all open documents without any prompt.

Prompt To Save All Changes
This option prompts you with a choice about saving changes:


Don’t Save Any Changes
This runs the code but does not save any of the changes you have made. Usually this is not a good idea, but it might be useful in some situations where you are testing many different code scenarios quickly.





07.09 Save Changes Before Building
07.10 Navigate Errors in the Error List
07.11 Ordering and Multicolumn Sorting in Tool Windows
16h 24m remaining
07.10 Navigate Errors in the Error List
DEFAULT

F8 (next); Shift+F8 (previous)

VISUAL BASIC 6

[no shortcut]

VISUAL C# 2005

F8 (next); Shift+F8 (previous)

VISUAL C++ 2

F4 (next); Shift+F4 (previous)

VISUAL C++ 6

F8 (next); F4 (next)

VISUAL STUDIO 6

F8 (next); F12 (next); Shift+F8 (previous); Shift+F12 (previous)

WINDOWS

[no shortcut]

COMMAND

Edit.GoToNextLocation; Edit.GoToPrevLocation

VERSIONS

2005, 2008, 2010

CODE

vstipTool0019

When checking out errors in the Errors window, you can easily navigate to the next error by pressing F8 or to the previous error by pressing Shift+F8. These actions rotate through all the errors in the direction of choice:


Additionally, as you cycle through, the location of each error in your code is selected:






07.10 Navigate Errors in the Error List
07.11 Ordering and Multicolumn Sorting in Tool Windows
07.12 Pin a DataTip to Source Code
16h 24m remaining
07.11 Ordering and Multicolumn Sorting in Tool Windows
VERSIONS

2005, 2008, 2010

CODE

vstipTool0021

When working with the various tool windows, you often need the ability to rearrange the information in different ways. With column ordering and column sorting, you have this ability.

Column Ordering
This technique can be used in a variety of tool windows, most notably the Task List window. Let’s begin with reordering the columns. In tool windows where this is supported, you can drag the columns around to put them in the order you want:


Additionally, you can sort by clicking on a column to make it sort ascending or descending, as shown in the following illustrations:



Multicolumn Sorting
But the best part is that you can have multicolumn sorting. So you can sort first by one column:


Then just press Shift, and click on the next column you would like to sort by:


If you want, you can continue to hold Shift and sort by more columns:






07.11 Ordering and Multicolumn Sorting in Tool Windows
07.12 Pin a DataTip to Source Code
07.13 Create a Floating DataTip
16h 24m remaining
07.12 Pin a DataTip to Source Code
COMMAND

EditorContextMenus.CodeWindow.PinToSource

VERSIONS

2010

CODE

vstipDebug0005

In Visual Studio 2010, you can now pin DataTips to source code. The purpose of pinned DataTips is to have the information stay with the line of code at all times, even after you scroll away from that line. To create one, just put your mouse pointer over any variable while debugging:


Notice the little pin at the end of the DataTip shown in the preceding illustration? If you click the pin, you have a pinned DataTip. The most obvious indicator of this is the pushpin that now shows up in the far left margin:


It is now, quite literally, pinned to a certain line of code. If you click the DataTip and drag it, you can change the line that the DataTip is pinned to:


You can also drill down into objects and pin properties as well:






07.12 Pin a DataTip to Source Code
07.13 Create a Floating DataTip
07.14 Adding Comments to a DataTip
16h 24m remaining
07.13 Create a Floating DataTip
VERSIONS

2010

CODE

vstipDebug0006

Floating DataTips are great for having information available where you want it. This tip shows how you use them. First, enter Break Mode, and pause your mouse pointer over a variable in the current scope; you should see something like the following:


Click the pin to create a pinned DataTip (see vstipDebug0005, 07.12 Pin a DataTip to Source Code, on page 305). Now, to make it a floating tip, put your mouse over the pinned tip until you see the control panel shown in the following illustration.

NOTE
The control panel might not come up exactly where the pinned tip is, so you might have to look around a bit to find it.


For this tip, our focus is on the pin in the middle:


Click it, and you should get a floating DataTip. (Notice the yellow color for floating DataTips.)


OK, so why should you care? Well, unlike pinned DataTips, floating DataTips don’t follow the source code as you step through it. This is useful if you want to step through code and have one or more pieces of information. The control panel might not come up exactly where the pinned tip is, so you might have to look around a bit to find it.






07.13 Create a Floating DataTip
07.14 Adding Comments to a DataTip
07.15 Use a DataTip to Edit a Value
16h 24m remaining
07.14 Adding Comments to a DataTip
VERSIONS

2010

CODE

vstipDebug0007

You might want to make a comment to remind yourself about something in a DataTip (pinned or floating), and now you can. First, enter Debug Mode, and then pause your mouse over a pinned (see vstipDebug0005, 07.12 Pin a DataTip to Source Code, on page 305) or floating tip (see vstipDebug0006, 07.13 Create a Floating DataTip, page 306) until you see the control panel shown in the following illustration.

NOTE
The control panel might not come up exactly where the pinned tip is, so you might have to look around a bit to find it.


Click the chevron at the bottom:


You should see something like the following illustration on your DataTip:


Now you can put in comments that travel with the DataTip at all times:


At the time of this writing, no upper limit is assigned to the amount of text you can put into this area. I was able to successfully paste the entire text of “War and Peace” in here. While I don’t suggest you do the same, the point is that you can be quite verbose with your comments if you need to be.





07.14 Adding Comments to a DataTip
07.15 Use a DataTip to Edit a Value
07.16 DataTip Value from the Last Debug Session
16h 24m remaining
07.15 Use a DataTip to Edit a Value
VERSIONS

2008, 2010

CODE

vstipDebug0026

You can change a variable value on the fly in a variety of ways. One of them is through the DataTip. Just click the value for a simple variable to change it:


For more complex types, you might need to expand the variables and edit individual items:






07.15 Use a DataTip to Edit a Value
07.16 DataTip Value from the Last Debug Session
07.17 Import and Export DataTips
16h 24m remaining
07.16 DataTip Value from the Last Debug Session
VERSIONS

2010

CODE

vstipDebug0012

Ever forget the values of variables you were just debugging? This is one of the coolest features of the DataTips in Visual Studio 2010. Let’s assume that you have a pinned DataTip in your code (see vstipDebug0005, 07.12 Pin a DataTip to Source Code, on page 305):


Now you stop debugging. Even though you are not debugging, you can still view the value from the last debug session by simply resting your mouse pointer over the pin in the margin:






07.16 DataTip Value from the Last Debug Session
07.17 Import and Export DataTips
07.18 Using the Call Hierarchy
16h 24m remaining
07.17 Import and Export DataTips
WINDOWS

Alt,D, X,X, Enter; Alt,D, P, P, Enter

MENU

Debug | Export DataTips; Debug | Import DataTips

COMMAND

Debug.ExportDataTips; Debug.ImportDataTips

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0013

Just as with breakpoints (see vstipDebug0003, 07.26 Import and Export Breakpoints, on page 329), you now have the ability to share your DataTips with team members by using the Export / Import features. Just go to Debug | Import (or Export) DataTips:


When you export the DataTips, they are exported as XML. You can version these files along with your source code so that other team members can have a copy of your DataTips.





07.17 Import and Export DataTips
07.18 Using the Call Hierarchy
07.19 Searching Breakpoints
16h 24m remaining
07.18 Using the Call Hierarchy
DEFAULT

Ctrl+K, Ctrl+T; Ctrl+K, T

VISUAL C++ 2

[no shortcut]

MENU

[Context Menu] | View Call Hierarchy

COMMAND

EditorContextMenus.CodeWindow.ViewCallHierarchy

VERSIONS

2010

LANGUAGES

C++, C#

CODE

vstipTool0005

The Call Hierarchy window allows you to visualize calls to and from a selected method, property, or constructor. To see how it works, just right-click any method, property, or constructor in the editor and select View Call Hierarchy:


You should get a window similar to the following:


Notice the Calls To and Calls From areas related to your selection. You can expand them:


When you click on a node in the tree, the Call Sites pane updates so that you can visit the call if you want to:

NOTE
You can double-click on the call site to have it automatically take you to the reference.


You can continue expanding the hierarchy to see further Calls To and Calls From information:


The best part is that you can right-click a symbol and get several options:


The following table describes some options you will come across as you use this feature:

CONTEXT MENU ITEM

DESCRIPTION

Add As New Root

Adds the selected node to the tree view pane as a new root node.

Remove Root

Removes the selected root node from the tree view pane. This option is available only from a root node.

You can also use the Remove Root toolbar button to remove the selected root node.

Go To Definition

Runs the Go To Definition command on the selected node. This navigates to the original definition for a method call or variable definition.

You can also press F12 to run the Go To Definition command on the selected node.

Find All References

Runs the Find All References command on the selected node. This finds all the lines of code in your project that reference a class or member.

You can also use Shift+F12 to run the Find All References command on the selected node.

Copy

Copies the contents of the selected node (but not its subnodes).

Refresh

Collapses the selected node so that re-expanding it displays current information.





07.18 Using the Call Hierarchy
07.19 Searching Breakpoints
07.20 Breakpoint Hit Count
16h 24m remaining
07.19 Searching Breakpoints
VERSIONS

2010

CODE

vstipDebug0002

When working with larger sets of breakpoints, it is useful to be able to search and filter based on criteria you choose. In Visual Studio 2010, you finally have the ability to search breakpoints the way you want. The ability to search your breakpoints is critical to being able to take actions on groups of breakpoints because the Breakpoints window commands now act on breakpoints that match the current search criteria. First, set some sample breakpoints in your code, and then open the Breakpoints window (Ctrl+Alt+B):


For this example, set some labels for your breakpoints (see vstipDebug0001, 07.03 Adding Labels to Breakpoints, on page 293) that have values you would like to search on:


Select the column you want to search on (in this example, the Labels column):


Type the string you are looking for in the search box inside the Breakpoints window, and press Enter. In this example, I’ll search for any label with the letter b anywhere in it. This yields the following result:


Now you can take actions on the breakpoints you can currently see. Most actions in the Breakpoints window now act on the results of the current search criteria:


To clear the search so that you can see all the breakpoints, just click the Reset All Search Criteria So That All Breakpoints Are Shown button:






07.19 Searching Breakpoints
07.20 Breakpoint Hit Count
07.21 Set a Breakpoint on a Function
16h 24m remaining
07.20 Breakpoint Hit Count
MENU

[Context Menu] | Hit Count

COMMAND

EditorContextMenus.CodeWindow.Breakpoint.BreakpointHitCount

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0019

Sometimes you might not want a breakpoint to stop the first time it is encountered. This is particularly true when you are working with loops and want to stop after a number of iterations. You can set a breakpoint so that it does not break every time but only when it is hit a certain number of times. Just right-click any breakpoint, and click Hit Count:


The Breakpoint Hit Count dialog box appears:


The default is to “break always,” but you can change that to one of the following options:


Break When The Hit Count Is Equal To
Choose this option if you want to break when the hit count reaches an exact value. So, in this example, if you put in a 5, the break does not occur until the breakpoint has been hit 5 times. This is useful when you know the number of hits you want before stopping.


Break When The Hit Count Is A Multiple Of
This breaks every x number of times it is hit. So if you put in a 5, it breaks every 5th time (5, 10, 15, and so on). This helps when you aren’t sure exactly where the problem is, so you want to skip in predefined increments as you look:


At any time, you can use the Breakpoints window to tell you the current hit count while you are debugging. In this example, the hit count is currently 15:


Break When The Hit Count Is Greater Than Or Equal To
This option takes any number and stops when the hit count has reached that number or higher. Use this option when you aren’t exactly sure what the value should be but want to stop when it reaches an upper bound:






07.20 Breakpoint Hit Count
07.21 Set a Breakpoint on a Function
07.22 Set a Simple Breakpoint Condition
16h 24m remaining
07.21 Set a Breakpoint on a Function
DEFAULT

Ctrl+B

VISUAL BASIC 6

Ctrl+B

VISUAL C# 2005

Ctrl+B; Ctrl+D, Ctrl+N; Ctrl+D, N

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+B

VISUAL STUDIO 6

[no shortcut]

WINDOWS

Alt,D, B, F

MENU

Debug | New Breakpoint | Break at Function

COMMAND

Debug.BreakatFunction

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0020

By default, breakpoints are based on line and character position:



But what if you don’t want to break on a specific line but instead want to break when you hit a particular function? There are two ways to do this.

Breakpoints Window
In the Breakpoints window, click New and choose Break At Function (or press Ctrl+B) to bring up the New Breakpoint dialog box.


In the New Breakpoint dialog box, type in the name of the function you want to break at, and then click OK.

WARNING
To ensure that the correct function name is being used, always select Use IntelliSense To Verify The Function Name when you perform this action. Otherwise, the breakpoint might not work.


After you click OK in the New Breakpoint dialog box, you should see something similar to the following:


The next illustration shows what a function breakpoint looks like in the Breakpoints window:






07.21 Set a Breakpoint on a Function
07.22 Set a Simple Breakpoint Condition
07.23 Set a Complex Breakpoint Condition
16h 24m remaining
07.22 Set a Simple Breakpoint Condition
MENU

[Context Menu] | Condition

COMMAND

EditorContextMenus.CodeWindow.Breakpoint.BreakpointCondition

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0021

Conditional breakpoints are arguably the most powerful types of breakpoints you can set. Many steps are involved in using them correctly, and knowing what steps you need to take is half the battle. Start by right-clicking on any breakpoint and choosing Condition.


This gives us the Breakpoint Condition dialog box. Notice that the condition can be turned off by clearing the Condition check box. Additionally, two options are available for the condition that you set:


Is true

Used for Boolean expressions that evaluate to true or false.

Has changed

Used for detecting whether the value of an expression has changed at the breakpoint location.

Let’s take a look at a couple of examples. Suppose we have the following For loop:


Is True
We can set a simple “Is true” condition that says when the variable “i” is greater than 5, the code should stop:


When we run the code and the breakpoint is hit, sure enough, it stops when the value of “i” is greater than 5:


Has Changed
This one is more interesting. Basically we set up something to watch. In this case, let’s just have it watch the “i” variable:


When the breakpoint is hit and the value of “i” has changed in any way, the code stops:


Special Notes
Anytime you set an advanced breakpoint, you get a new glyph (red sphere with a plus sign in it):


You can always tell what kind of breakpoint you have by pausing your mouse over the glyph and looking at the tooltip or by looking in the Breakpoints window:






07.22 Set a Simple Breakpoint Condition
07.23 Set a Complex Breakpoint Condition
07.24 Setting a Breakpoint Filter
16h 24m remaining
07.23 Set a Complex Breakpoint Condition
MENU

[Context Menu] | Condition

COMMAND

EditorContextMenus.CodeWindow.Breakpoint.BreakpointCondition

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0022

We previously discussed how to set simple conditions. (See vstipDebug0021, 07.22 Set a Simple Breakpoint Condition, on page 318.) The real power of the Breakpoint Condition dialog box is the ability to execute any line of code from it:


For example, you can use it to call external methods. The following example illustrates this, but bear in mind that it’s a contrived example, designed to show how this works. The following illustration shows the code we want to execute:


Notice that a variable, x, is given a value. In this case, I hard-coded a value, but the value would presumably come as the result of some method execution. I want the breakpoint to stop only if the value of x is 20. I have a method that returns a Boolean value to test for the condition I want:


I won’t get into the obvious debate about whether this is a good idea or not, how the method should be constructed, or if the average rainfall in the Amazon Basin is a factor here. I’ll just call the method from the Breakpoint Condition dialog box.

Notice that after typing a few characters, I use Ctrl+Space to get IntelliSense here if needed (see vstipEdit0017, 06.07 Using the New IntelliSense: Pascal Case, on page 216):


Make sure the Is True option is selected:


Now I have a conditional breakpoint that uses an external method to determine whether or not the code should stop. Naturally, you can add more Boolean logic here as well and include And / Or / Not / Xor:


Now the really interesting part is that you can have your checking code be available only for Debug builds:


By surrounding your code with conditional compilation directives, you can easily have checking code that is around only while debugging. Following is what the checking method would look like in C#:


Play with this feature some, and you can see why most people (including me) think that this is one of the most powerful breakpoint features around.





07.23 Set a Complex Breakpoint Condition
07.24 Setting a Breakpoint Filter
07.25 Setting a Tracepoint in Source Code
16h 24m remaining
07.24 Setting a Breakpoint Filter
WINDOWS

Alt,T, O (options)

MENU

Tools | Options; [Context Menu] | Filter

COMMAND

Tools.Options; EditorContextMenus.CodeWindow.Breakpoint.BreakpointFilter

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0024

Breakpoint filters are used when you want to break based on thread, process, or machine information. This is particularly useful for debugging multithreaded applications. To make sure you can set them, go to Tools | Options | Debugging | General and select Enable Breakpoint Filters:


To make a breakpoint filter, just right-click any regular breakpoint and choose Filter:


You get the Breakpoint Filter dialog box:


As shown in the preceding graphic, I’ve decided to break whenever the breakpoint is hit and the thread name is “bubba.” The following illustration shows what it looks like in the Threads window when I actually run my code and the breakpoint is hit:






07.24 Setting a Breakpoint Filter
07.25 Setting a Tracepoint in Source Code
07.26 Import and Export Breakpoints
16h 24m remaining
07.25 Setting a Tracepoint in Source Code
MENU

[Context Menu] | When Hit

COMMAND

EditorContextMenus.CodeWindow.Breakpoint.BreakpointWhenHit

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0010

Tracepoints give you the opportunity to unobtrusively print out information during application execution. This tip shows you how to use the IDE to create tracepoints, but for detailed information about how to do this in code, see “Tracing and Instrumenting Applications” at http://msdn.microsoft.com/en-us/library/zs6s4h68(VS.100).aspx.

The best way to illustrate simple tracepoints is with a basic loop. I would suggest creating a new project and making a simple for loop to play with. Here is my sample code:


Setting Tracepoints
You have a couple of ways to set a tracepoint on a line of code.

One way is to right-click on the line and choose Breakpoint | Insert Tracepoint.


Alternatively, you can set a breakpoint (F9) and then right-click on the breakpoint in the indicator margin and choose When Hit:


Whichever technique you use, the When Breakpoint Is Hit dialog box appears:


The When Breakpoint Is Hit dialog box provides three options.

Print a message
Used to print out any special variables (that begin with a $), evaluated expressions (inside curly braces), or literal text.

Run a macro
Used to actually run a macro when this tracepoint is hit and can do extended processing or kick off some other task.

Continue execution
Makes the tracepoint unobtrusive and lets the application run. If you clear the Continue Execution check box, the tracepoint becomes a breakpoint.

Click OK and notice something interesting. The normal round breakpoint indicator is now a diamond:


This is how we distinguish breakpoints (stop execution) from tracepoints (don’t stop execution). For example, if I were to clear the Continue Execution check box in the When Breakpoint Is Hit dialog box, the breakpoint symbol would become round again:


Tracepoints show up along with breakpoints in the Breakpoints window:


At this point, you have done enough to see tracepoints in action, so run your application. It should execute and then end. Open the Output window (Debug | Windows | Output), and notice the entries from our tracepoint:


The default message isn’t very helpful in this case, so let’s change it to something else. In this example, let’s put The value of i is {i}. Notice that I put the expression to be evaluated (the variable i in this case) inside curly braces:


Now you should see the following in the Output window:


Change Default Message
There is a lot more to learn here, but you have a good start. One thing you might want to do is permanently change the default output message (currently “Function: $FUNCTION, Thread: $TID $TNAME”) that you get when you set a new tracepoint. This is useful if you find that you use a certain message often across projects. You can do this by going into the registry:

HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger
WARNING
Editing the registry can cause issues with Visual Studio, so perform these steps at your own risk.

Then modify the string value called DefaultTracepointMessage to the new default you would like to have.





07.25 Setting a Tracepoint in Source Code
07.26 Import and Export Breakpoints
07.27 Run to Cursor
16h 24m remaining
07.26 Import and Export Breakpoints
COMMAND

EditorContextMenus.CodeWindow.Breakpoint.BreakpointExport; DebuggerContextMenus.BreakpointsWindow.Exportselected

VERSIONS

2010

CODE

vstipDebug0003

These next features are specifically designed so that you can share breakpoints with other team members. When you do this, make sure to version your exported breakpoints with your source code for sharing.

Set one or more breakpoints in your code, and open the Breakpoints window (Ctrl+Alt+B). Notice the new Export button. It’s important to understand that it exports breakpoints matching the current search criteria. In other words, if you don’t see the breakpoint in the Breakpoints window, it will not be exported:


When you click the Export button, you get the classic Save As dialog box; notice that your breakpoints are saved as an XML file:


Put in some name for the file, and click Save. Give the file you created to your teammate or, if you are just practicing, you can delete your breakpoints.

Click on the new Import button:


Choose the XML file that was exported, and click Open to import your breakpoints.note

Get Link
link
table of contents
search
Settings





07.26 Import and Export Breakpoints
07.27 Run to Cursor
07.28 Using the Exception Assistant
16h 24m remaining
07.27 Run to Cursor
DEFAULT

Ctrl+F10

VISUAL BASIC 6

Ctrl+F10; Ctrl+F8

VISUAL C# 2005

Ctrl+F10

VISUAL C++ 2

Ctrl+F10; F7

VISUAL C++ 6

Ctrl+F10

VISUAL STUDIO 6

Ctrl+F10

WINDOWS

[no shortcut]

MENU

[Context Menu] | Run To Cursor

COMMAND

Debug.RunToCursor

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0023

This is one that has been around a while but seems to get lost among all the other features that are out there. Basically, if you have some code and want to quickly run it and set a temporary breakpoint at the same time, this tip is for you.

Just put the cursor on the line you want to break on:


Press Ctrl+F10, or right-click and choose Run To Cursor:


The application starts and a temporary Breakpoint is set on the line where you were, but you do not see any breakpoint indicator. The next time the code hits that line, it enters break mode:


Keep in mind that the application does not break until the line the temporary breakpoint is on is hit. If the line is never executed, the application will not break for debugging.





07.27 Run to Cursor
07.28 Using the Exception Assistant
07.29 Use a Specific Port for the Development Server (Web Applications)
16h 24m remaining
07.28 Using the Exception Assistant
VERSIONS

2005, 2008, 2010

CODE

vstipDebug0030

The Exception Assistant appears whenever a runtime exception occurs. It shows the type of exception, troubleshooting tips, and corrective actions as applicable:


Exception Object and Description
The layout is pretty straightforward. First you have the exception object type and description:


Troubleshooting Tips
Then you have the Troubleshooting Tips area that provides advice about how to resolve the problem in a user-friendly format. The items are typically links to more information that can be found in the online or offline Help:


Help Online
Search For More Help Online is pretty interesting when you click the link:


You get a dialog box asking permission to send information online:


Clicking OK results in sending the information to MSDN online and performing a search:


Actions
The Actions area lets you get information about the Exception Object:


The View Detail link opens a dialog box that exposes the details of the object for you to review:


The Copy Exception Detail To The Clipboard link captures textual information you can put into any editor for analysis. It’s not overly detailed but does provide a starting point for resolving the issue:


Turning Off the Exception Assistant
Although not suggested, you can actually turn this feature off. Just go to Tools | Options | Debugging | General, and clear the Enable The Exception Assistant check box:


The following illustration shows what the same error looks like with the Exception Assistant off:


Unwind The Call Stack On Unhandled Exceptions
If you want more information about the details of this option, check out the great article by Bill Horst, at http://blogs.msdn.com/b/vbteam/archive/2008/12/08/did-you-know-you-can-unwind-the-call-stack-from-exceptions-bill-horst.aspx.





07.28 Using the Exception Assistant
07.29 Use a Specific Port for the Development Server (Web Applications)
07.30 Application and Page Level Tracing
16h 24m remaining
07.29 Use a Specific Port for the Development Server (Web Applications)
VERSIONS

2005, 2008, 2010

CODE

vstipProj0029

If you are using a firewall and want to use the same port while you do web development to accommodate a firewall rule, you can configure Visual Studio to use a fixed port. To do this, go to the project properties for any web application and click Web:

On the Web tab, go to the Servers area:


In the Servers area, choose Specific Port, and then assign a port number to use:


The project now continues to use the port number assigned instead of automatically assigning one.





07.29 Use a Specific Port for the Development Server (Web Applications)
07.30 Application and Page Level Tracing
07.31 The Watch Window: Watching and Changing Values
16h 24m remaining
07.30 Application and Page Level Tracing
VERSIONS

2005, 2008, 2010

CODE

vstipProj0030

When debugging any project, it’s good to have as much information as possible to help deal with any issues. Working with web projects is always a challenge no matter what IDE you use. Fortunately, the folks on the web team have provided a useful tool just for web developers: tracing. Tracing can be enabled at two levels: application and page.

WARNING
Generally, you should not enable tracing in an production website, because this can display sensitive configuration information to anyone who views pages in the website. Tracing is intended for debugging purposes only. If the localOnly attribute is true, trace information is displayed only for localhost requests. Additionally, if <deployment retail=true> is set in the Web.config file, tracing is disabled.

Application Level Tracing
You can enable application tracing by going to Web.config and adding the <trace> element inside <system.web>:

<configuration>
  <system.web>

    <trace enabled="true" requestLimit="50" localOnly="true" />

  <system.web>

<configuration>
To access the application trace information, simply append “trace.axd” to the root of your website:


The following is a part of what you should see:


Attributes
Several attributes can be applied when using trace, all of which are optional:

enabled (Boolean) Specifies whether tracing is enabled for an application. The default is false.

localOnly (Boolean) Indicates whether the trace information is available only on the host web server. If false, the trace is visible from any computer, which can be a security issue. The default is true.

mostRecent (Boolean) Shows whether the most recent application-level tracing output is displayed. If beyond the limits that are indicated by the requestLimit attribute, older trace data is discarded. If false, trace data is displayed for requests until the requestLimit attribute is reached. The default is false.

pageOutput (Boolean) Specifies whether trace output is rendered at the end of each page. If false, trace output is accessible through the trace utility only. The default is false.

requestLimit (Int32) Indicates the number of trace requests to store on the server. If the limit is reached and the mostRecent attribute is false, trace is automatically disabled. The maximum request limit is 10,000. If a value that is greater than 10,000 is specified, it is silently rounded down to 10,000 by ASP.NET. The default is 10.

traceMode The order in which to display trace information. The traceMode attribute can be one of two possible values:

SortByCategory Trace information is displayed alphabetically by user-defined category.

SortByTime Trace information is displayed in the order that the trace information is processed. The default is SortByTime.

writeToDiagnosticsTrace (Boolean) Indicates whether ASP.NET trace messages are forwarded to the System.Diagnostics tracing infrastructure, for any listeners that are registered to display trace messages. The default is false.

You can find more information about trace element settings at http://msdn.microsoft.com/en-us/library/6915t83k.aspx.

Trace Details
Additionally, you can click on the View Details link of each item and see a great deal of information:


Page Level Tracing
You might not want to have tracing enabled for the entire application for a variety of reasons, such as performance, wanting to focus in on just one page, and so on. Turning on tracing for a page is very simple. Just turn on tracing in your @Page directive, as in the following example:

<%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.master"
AutoEventWireup="true"
  CodeBehind="Default.aspx.cs" Inherits="WebApplication61._Default" Trace="true" %>
Now when you view that page, it shows the trace information on the page:


This is equivalent to setting pageOutput to true at the application level, but it affects only those pages where you have turned tracing on.

Combined Tracing
Tracing can get confusing, but the one thing to remember is that the page always wins when tracing is explicitly set. You can use the following table to help keep the tracing results in mind if you set both application and page level tracing.

APPLICATION

PAGE

RESULT FOR A PAGE

true

false

false

false

true

true

Finally
To say there is a lot going on here would be an understatement. I leave it to you to explore more of the details, which can be found at http://msdn.microsoft.com/en-us/library/bb386420.aspx.





07.30 Application and Page Level Tracing
07.31 The Watch Window: Watching and Changing Values
07.32 Understanding QuickWatch
16h 24m remaining
07.31 The Watch Window: Watching and Changing Values
DEFAULT

Shift+F9 (QuickWatch); Ctrl+Alt+Q (QuickWatch)

VISUAL BASIC 6

Shift+F9 (QuickWatch); Ctrl+Alt+Q (QuickWatch)

VISUAL C# 2005

Shift+F9 (QuickWatch); Ctrl+Alt+Q (QuickWatch); Ctrl+D, Ctrl+Q (QuickWatch); Ctrl+D, Q (QuickWatch)

VISUAL C++ 2

Shift+F9 (QuickWatch); Ctrl+Alt+Q (QuickWatch)

VISUAL C++ 6

Shift+F9 (QuickWatch); Ctrl+Alt+Q (QuickWatch)

VISUAL STUDIO 6

Shift+F9 (QuickWatch); Ctrl+Alt+Q (QuickWatch)

WINDOWS

Alt,D, Q (QuickWatch)

MENU

Debug | QuickWatch; [Context Menu] | Add Watch

COMMAND

Debug.QuickWatch; Debug.AddWatch

VERSIONS

2005, 2008, 2010

CODE

vstipTool0104

By definition, a watch expression does exactly what it sounds like it should do: It watches something and shows you the result so that you can monitor data as you are debugging. You can use any of the following techniques to create a watch expression:

Type it in

QuickWatch

Add Watch

Let’s take a closer look.

Watch Expressions
First we need to define what you can watch. Essentially, you can watch any valid expression. Some examples of valid watch expressions are shown in the following illustration:


Watch Window
The easiest way to open the main Watch window is to press Ctrl+Alt+W,1 or go to Debug | Windows | Watch | Watch 1. You can have up to four Watch windows, so you can organize your watch expressions into groups if you want:


Creating a Watch Expression
Type it in
One of the quickest ways to put in most watch expressions is just to type in the variable or expression you want to watch in the Watch window:


QuickWatch (Shift+F9)
Despite the name, this is actually the longest way to set a watch expression. When you press Shift+F9 or go to Debug | QuickWatch, you get the following dialog box:


Type any expression in the Expression area, and then click Reevaluate to see the value appear in the Value area. If you are happy with what you see and want to add a watch expression to the QuickWatch window, just click Add Watch.

Add Watch
This is another pretty quick watch expression to set. Just right-click a variable or selected expression and instantly have it added to Watch 1:


Changing Values
With any watch expression, you can change the value to suit your needs by just selecting the value you want to change:


Then type in a new value, and press Enter:


The value turns red to indicate it has changed. This makes it easy to track your changes.





07.31 The Watch Window: Watching and Changing Values
07.32 Understanding QuickWatch
07.33 The Watch Window: Visualizers
16h 24m remaining
07.32 Understanding QuickWatch
DEFAULT

Shift+F9; Ctrl+Alt+Q

VISUAL BASIC 6

Shift+F9; Ctrl+Alt+Q

VISUAL C# 2005

Shift+F9; Ctrl+Alt+Q; Ctrl+D, Ctrl+Q; Ctrl+D, Q

VISUAL C++ 2

Shift+F9; Ctrl+Alt+Q

VISUAL C++ 6

Shift+F9; Ctrl+Alt+Q

VISUAL STUDIO 6

Shift+F9; Ctrl+Alt+Q

WINDOWS

Alt, D, Q

MENU

Debug | QuickWatch

COMMAND

Debug.QuickWatch

VERSIONS

2005, 2008, 2010

CODE

vstipTool0108

In vstipTool0104 (07.31 The Watch Window: Watching and Changing Values, page 340), I showed you how to use QuickWatch to get data into a Watch window. From that perspective, using QuickWatch is rather slow and cumbersome. However, QuickWatch doesn’t exist for only that reason, so it is worth another look.

So, why does QuickWatch exist? It was actually created to be a dialog box that is a one-stop shop for quickly working with expressions. Think of it as a dialog box dedicated to a single watch expression. It’s a modal dialog box, so you need to close it before moving on with any other debugging. Bring it up by pressing Shift+F9 or going to Debug | QuickWatch on the Menu Bar.

What Does It Do?
Like a normal watch expression, you can edit the value in it:


Also, you can change the expression and click Reevaluate to see a new value:


One big advantage to the QuickWatch window is the fact that it can be resized. It can be very useful when digging deep:


Other Options
While it is useful for specific scenarios, with the advent of DataTips (see vstipDebug0005, 07.12 Pin a DataTip to Source Code, on page 305), the usefulness of the QuickWatch dialog box has diminished somewhat, so you might choose to use DataTips instead. It all comes down to personal preference.





07.32 Understanding QuickWatch
07.33 The Watch Window: Visualizers
07.34 The Watch Window: Refreshing Data
16h 24m remaining
07.33 The Watch Window: Visualizers
DEFAULT

Ctrl+Alt+W,1; Ctrl+Alt+W,[2-4]

VISUAL BASIC 6

Ctrl+Alt+W,1; Ctrl+Alt+W,[2-4]

VISUAL C# 2005

Ctrl+Alt+W,1; Ctrl+D, Ctrl+W; Ctrl+D, W; Ctrl+Alt+W,[2-4]

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+Alt+W,1; Ctrl+Alt+W,[2-4]

VISUAL STUDIO 6

Ctrl+Alt+W,1; Ctrl+Alt+W,[2-4]

WINDOWS

Alt+D, W, W, [1-4]

MENU

Debug | Windows | Watch | Watch [1,2,3,4]

COMMAND

Debug.Watch[1,2,3,4]

VERSIONS

2005, 2008, 2010

CODE

vstipTool0106

When using the Watch windows, you might come across visualizers. A visualizer is a debugger component that enables the debugger to display (visualize) the contents of a data object in a meaningful, understandable form. Visualizers are pretty easy to spot because they have a magnifying glass icon:


Notice that when you click on the magnifying glass, it gives you options (based on the data you are looking at) for a visualizer. If you select Text Visualizer, you get the following dialog box:


You might find it useful to leverage the power of visualizers when looking at different types of data. If this output were HTML, you would use the HTML Visualizer:


And you would see the following dialog box:






07.33 The Watch Window: Visualizers
07.34 The Watch Window: Refreshing Data
07.35 The Watch Window: Adding Watches from Variable Windows
16h 24m remaining
07.34 The Watch Window: Refreshing Data
WINDOWS

Alt,T, O

MENU

Tools | Options | Debugging | General

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipTool0107

When you evaluate an expression in one of the Watch windows, one of two refresh icons might appear in the Value column. One refresh icon is a circle that contains two wavy lines that resemble threads. The other icon is two circling arrows, as shown in the following example:


Refresh Icons
Following is what the documentation (http://msdn.microsoft.com/en-us/library/z4ecfxd9.aspx) has to say about these icons.

Circling arrows
If the circling arrows appear, the expression was not evaluated for one of the following reasons:

An error occurred as the expression was being evaluated. For example, a time-out might have occurred, or a variable might have been out of scope.

Evaluating the expression would have required evaluating a property or making an implicit function code. Evaluation of properties and implicit function calls can have side effects that affect the state of your program. Because these effects can make debugging more difficult, automatic evaluation of properties and implicit function calls by the debugger is often turned off. Occasionally, a programmer might unintentionally turn off automatic evaluation.

If you want to learn more about side effects, see the topic “Side Effects and Expressions” at http://msdn.microsoft.com/en-us/library/a7a250bs.aspx.

Two threads
If the two threads appear, the expression was not evaluated because of a potential cross-thread dependency. A cross-thread dependency means that evaluating the code requires other threads in your application to run temporarily. When you are in break mode, all threads in your application are typically stopped. Allowing other threads to run temporarily can have unexpected effects on the state of your program and causes the debugger to ignore events such as breakpoints.

Refreshing the data
To refresh the data, just click the icon or press the Spacebar:


Turning It Off
Although not suggested, you can turn this feature off by going to Tools | Options | Debugging | General and clearing the Enable Property Evaluation And Other Implicit Function Calls check box:






07.34 The Watch Window: Refreshing Data
07.35 The Watch Window: Adding Watches from Variable Windows
07.36 Create Folders in Class View
16h 24m remaining
07.35 The Watch Window: Adding Watches from Variable Windows
MENU

[Context Menu] | Add Watch

COMMAND

Debug.AddWatch

VERSIONS

2005, 2008, 2010

CODE

vstipTool0109

The Locals, Autos, Watch, and QuckWatch windows are all known, collectively, as the Variable windows. Did you know that every Variable window supports the Debug.AddWatch command? This tip provides some examples.

Locals Window

Autos Window

QuickWatch

Watch [1, 2, 3, 4] Window
This is one you might not expect. The Watch windows actually have the ability to add watch expressions. Very useful if you have a complex expression and want to copy it to do a modification:


Keyboard Mapping
If you find yourself adding watch expressions frequently in break mode, you should consider mapping a keyboard shortcut. Go to Tools | Options | Environment | Keyboard, and assign a shortcut to the Debug.AddWatch command:
note

Get Link
link
table of contents
search
Settings





07.35 The Watch Window: Adding Watches from Variable Windows
07.36 Create Folders in Class View
07.37 Search in Class View
16h 24m remaining
07.36 Create Folders in Class View
MENU

[Context Menu] | New Folder

COMMAND

View.ClassViewNewFolder

VERSIONS

2005, 2008, 2010

CODE

vstipTool0072

Did you know that you can create folders to easily organize items in Class View? It’s pretty easy to do. Just open the Class View dialog box (Ctrl+Shift+C):


Create a New Folder
Click the Class View New Folder button:


Give your new folder some logical name:


NOTE
These folders are not created on the file system but are stored in your .suo file.

Putting Items into Your Folder
You can simply click and drag items into your new folder to organize them:


You can also copy and paste items into the folders as well. These operations are strictly organizational and don’t actually make an extra copy of the item in your code.

Removing Items from Folders
You can remove items from your folder at any time by deleting them (right-click or press the Delete key).

NOTE
This deletes only the item from the Class View and doesn’t actually delete your code.

Creating Subfolders
You can even nest the folder structure by creating a new folder inside an existing one:


Deleting Folders
Naturally you can delete any folder by right-clicking it and choosing Delete.





07.36 Create Folders in Class View
07.37 Search in Class View
07.38 Synchronize Your Class View
16h 24m remaining
07.37 Search in Class View
DEFAULT

Ctrl+K, Ctrl+V

VISUAL C++ 2

[no shortcut]

COMMAND

View.ClassViewGoToSearchCombo; View.ClassViewSearch

VERSIONS

2005, 2008, 2010

CODE

vstipTool0073

The Class View window has a search capability that finds items quickly. Just go to the Class View Search Combo box (Ctrl+K, Ctrl+V):


WARNING
I’ve actually had the search combo box disappear on me before. Restarting Visual Studio should bring it back if this happens to you, too.

Type in the keyword to search for, and press Enter:


It searches for the keyword in items and shows the results while highlighting the last instance where the keyword was found in an item. The search is a contains operation, so it looks for anything that has the keyword anywhere in the result.

View.ClassViewSearch Command
If you want a quick way to do this by running a command, you can use View.ClassViewSearch with any keyword(s). First, go someplace you can run a command. I prefer to use the Find Combo box with the command character (Ctrl+/) to run my commands (see vstipTool0070, 03.28 Understanding Commands: Logging Commands on page 121, for more options):


Type in View.ClassViewSearch [keyword(s)]. In this case, let’s look for the word “task”:


Just press Enter, and we get our results in the Class View:


Use a Previous Search
You can repeat any previous search in Class View by using the drop-down list from the Search Combo box:


Clear Your Search
Whichever method you use, you can always clear your search by clicking the Clear Search button:






07.37 Search in Class View
07.38 Synchronize Your Class View
07.39 The Misnamed and Misunderstood Object Browser
16h 24m remaining
07.38 Synchronize Your Class View
COMMAND

View.SynchronizeClassView

VERSIONS

2005, 2008, 2010

CODE

vstipTool0074

When you are in your code, sometimes you would like to have Class View synchronize with your code. By default, it doesn’t do this.


You can run the View.SynchronizeClassView command from the Find combo (Ctrl+/) to see how this works:


NOTE
This command works only if the editor has the focus, so you need to run it from the Find drop-down box as shown in this example or assign a shortcut key to it. It does not work if you try to run it from the Command window.

It finds your current location in Class View:






07.38 Synchronize Your Class View
07.39 The Misnamed and Misunderstood Object Browser
07.40 The Object Browser: Setting the Browsing Scope
16h 24m remaining
07.39 The Misnamed and Misunderstood Object Browser
DEFAULT

Ctrl+Alt+J

VISUAL BASIC 6

Ctrl+Alt+J; F2

VISUAL C# 2005

Ctrl+Alt+J; Ctrl+W, Ctrl+J; Ctrl+W, J

VISUAL C++ 2

Ctrl+Alt+J; Shift+Alt+F1

VISUAL C++ 6

Ctrl+Alt+J

VISUAL STUDIO 6

Ctrl+Alt+B; F2

WINDOWS

Alt,V, J

MENU

View | Object Browser

COMMAND

View.ObjectBrowser

VERSIONS

2005, 2008, 2010

CODE

vstipTool0077

Many people often ask why they should use the Object Browser. First and foremost, it is a way to browse to find the correct class, object, property, method, interface, and so on that is useful for your needs as you code. But the Object Browser does much, much more than its name implies.


As you can see from the high-level view shown in the preceding illustration, the Object Browser is composed of several parts:

Toolbar (very top) Contains various controls for manipulating the various functions available.

Objects pane (left, top and bottom) Displays an expandable list of symbols whose top-level nodes represent components or namespaces available in the current browsing scope.

Members pane (right, top) Displays the available members, if available, of any symbol selected in the Objects pane.

Description pane (right, bottom) Displays detailed information about the currently selected object or member.

First, the name would have you think that it shows only objects. This is simply untrue. In fact, it shows many different types of symbols, which is better than just showing objects:


In this example, as shown in the preceding illustration, we see a couple of projects with several namespaces in them, in addition to some interfaces and classes. The classes with envelopes represent internal classes. The icons are explained in vstipTool0076, AX.135 Creating a Class Diagram from Class View, in Appendix B (http://go.microsoft.com/FWLink/?Linkid=223758).

Second, you might think that all you can do is browse items. Again, not true. For example, you can add references to your project from the Object Browser when you find something that you want to include:


The next series of tips explore, in detail, the use of the Object Browser in your work.note

Get Link
link
table of contents
search
Settings





07.39 The Misnamed and Misunderstood Object Browser
07.40 The Object Browser: Setting the Browsing Scope
07.41 The Object Browser: Navigation and References
16h 24m remaining
07.40 The Object Browser: Setting the Browsing Scope
DEFAULT

Ctrl+Alt+J

VISUAL BASIC 6

Ctrl+Alt+J; F2

VISUAL C# 2005

Ctrl+Alt+J; Ctrl+W, Ctrl+J; Ctrl+W, J

VISUAL C++ 2

Ctrl+Alt+J; Shift+Alt+F1

VISUAL C++ 6

Ctrl+Alt+J

VISUAL STUDIO 6

Ctrl+Alt+B; F2

WINDOWS

Alt, V, J

MENU

View | Object Browser

COMMAND

View.ObjectBrowser

VERSIONS

2005, 2008, 2010

CODE

vstipTool0078

When you use the Object Browser, it’s a good idea to know what components you are browsing. So let’s start our examination at the top, with the Browse area:


Browse
The Browse drop-down box lets you specify the browsing scope (the list of items you see in the Objects pane):


All Components
The All Components drop-down quite literally lets you browse all components, including all of the .NET Framework, the current solution and its referenced components, and any other components that you have added by selecting Edit Custom Component Set. It’s a massive dose of information overload, so be prepared.

.NET Framework X / Silverlight X
Sets the browsing scope to a specific version of the Framework.

My Solution
Shows items in the current solution and referenced components.

Custom Component Set
Sets browsing scope to the list of components identified by editing the Custom Component Set. For example, if I choose NET Framework 4, I see the following:


Edit Custom Component Set
You can edit the Custom Component Set to identify the components that create the browsing scope in two ways:

Choose Edit Custom Component Set in the browse drop-down box.

Click the Edit Custom Component Set button on the toolbar:


Regardless of the method used, you get the Edit Custom Component Set dialog box:


In the Edit Custom Component Set dialog box, you can add or remove components from a variety of sources. The browsing scope of the Custom Component Set is determined by the items listed in the Selected Projects And Components section of this dialog box. As you can see, information about the type, version, and source (location) is available here.

If you pick something that can’t be browsed, you get the following message:


After you have successfully edited the Custom Component Set, it is automatically selected in the Browse drop-down box and becomes the current browsing scope:






07.40 The Object Browser: Setting the Browsing Scope
07.41 The Object Browser: Navigation and References
07.42 The Exceptions Dialog Box
16h 24m remaining
07.41 The Object Browser: Navigation and References
DEFAULT

Ctrl+Alt+J (view object browser); Alt+Right Arrow (forward); Alt+Left Arrow (back)

VISUAL BASIC 6

Ctrl+Alt+J (view object browser); F2 (view object browser); Alt+Right Arrow (forward); Alt+Left Arrow (back)

VISUAL C# 2005

Ctrl+Alt+J (view object browser); Ctrl+W, Ctrl+J (view object browser); Ctrl+W, J (view object browser); Alt+Right Arrow (forward); Alt+Left Arrow (back)

VISUAL C++ 2

Ctrl+Alt+J (view object browser); Shift+Alt+F1 (view object browser); Alt+Right Arrow (forward); Alt+Left Arrow (back)

VISUAL C++ 6

Ctrl+Alt+J (view object browser); Alt+Right Arrow (forward); Alt+Left Arrow (back)

VISUAL STUDIO 6

Ctrl+Alt+B (view object browser); F2 (view object browser); Alt+Right Arrow (forward); Alt+Left Arrow (back)

WINDOWS

Alt,V, J (view object browser)

MENU

View | Object Browser

COMMAND

View.ObjectBrowser; View.Forward; View.Backward; View.ObjectBrowserAddReference

VERSIONS

2005, 2008, 2010

CODE

vstipTool0079

Continuing our look at the Object Browser, we now turn our attention to the toolbar buttons to the right of the Browse area:


Navigation
The Forward (Alt+Right Arrow) and Back (Alt+Left Arrow) buttons can be used to easily navigate among items in the Objects pane as you browse:


I haven’t discovered any obvious upper limit to how many times you can go back. I have personally tested it to go back over 75 items, with no end in sight. The places are remembered (and more added) as long as Visual Studio remains open, regardless of which project or solution you are using.

References
You can add a reference to the currently selected item in the Objects pane to your project:



Read the tooltip carefully. Notice that it says Add To References In Selected Project In Solution Explorer. This might confuse you when you try to use it for the first time because you can select a reference that you want to add and then find the button disabled (top right in the following illustration):


This is because you most likely don’t have a project selected in Solution Explorer, as we do in the following example:


Simply click on (or in) any project, and the button becomes enabled so that you can add the reference to your project.





07.41 The Object Browser: Navigation and References
07.42 The Exceptions Dialog Box
07.43 Setting a Breakpoint in the Call Stack Window
16h 24m remaining
07.42 The Exceptions Dialog Box
DEFAULT

Ctrl+Alt+E

VISUAL BASIC 6

Ctrl+Alt+E

VISUAL C# 2005

Ctrl+Alt+E; Ctrl+D, Ctrl+E; Ctrl+D, E

VISUAL C++ 2

Ctrl+Alt+E

VISUAL C++ 6

Ctrl+Alt+E

VISUAL STUDIO 6

Ctrl+Alt+E

WINDOWS

Alt,D, X

MENU

Debug | Exceptions

COMMAND

Debug.Exceptions

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0039

By default, Visual Studio breaks only when an exception is not handled by user code. This can sometimes be problematic because the exception can bubble up through several calls far away from where the actual exception originally occurred, making it harder to find the problem.

You can use the Exceptions dialog box (Ctrl+Alt+E) to configure exceptions to break when they happen rather than checking to see whether they are unhandled:


The exceptions are divided up into five broad categories. Also, as shown in the preceding illustration, two options are provided: Thrown and User-Unhandled. When you check Thrown for any category or individual exception, it breaks when the exception occurs instead of waiting to see whether the user handles the exception.

Additionally, you can use the following buttons.

Find
Find
Helps you search for a specific exception.

Reset All
Puts exceptions back to their default settings.

Add
Allows you to add exceptions not currently in the list.

Delete
Lets you delete any added exceptions.

Special Case
You might find the User-Unhandled option missing from the Exceptions dialog box:


To get it back, go to Tools | Options | Debugging | General and select Enable Just My Code (Managed Only):






07.41 The Object Browser: Navigation and References
07.42 The Exceptions Dialog Box
07.43 Setting a Breakpoint in the Call Stack Window
16h 24m remaining
07.42 The Exceptions Dialog Box
DEFAULT

Ctrl+Alt+E

VISUAL BASIC 6

Ctrl+Alt+E

VISUAL C# 2005

Ctrl+Alt+E; Ctrl+D, Ctrl+E; Ctrl+D, E

VISUAL C++ 2

Ctrl+Alt+E

VISUAL C++ 6

Ctrl+Alt+E

VISUAL STUDIO 6

Ctrl+Alt+E

WINDOWS

Alt,D, X

MENU

Debug | Exceptions

COMMAND

Debug.Exceptions

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0039

By default, Visual Studio breaks only when an exception is not handled by user code. This can sometimes be problematic because the exception can bubble up through several calls far away from where the actual exception originally occurred, making it harder to find the problem.

You can use the Exceptions dialog box (Ctrl+Alt+E) to configure exceptions to break when they happen rather than checking to see whether they are unhandled:


The exceptions are divided up into five broad categories. Also, as shown in the preceding illustration, two options are provided: Thrown and User-Unhandled. When you check Thrown for any category or individual exception, it breaks when the exception occurs instead of waiting to see whether the user handles the exception.

Additionally, you can use the following buttons.

Find
Find
Helps you search for a specific exception.

Reset All
Puts exceptions back to their default settings.

Add
Allows you to add exceptions not currently in the list.

Delete
Lets you delete any added exceptions.

Special Case
You might find the User-Unhandled option missing from the Exceptions dialog box:


To get it back, go to Tools | Options | Debugging | General and select Enable Just My Code (Managed Only):






07.42 The Exceptions Dialog Box
07.43 Setting a Breakpoint in the Call Stack Window
07.44 Setting a Tracepoint in the Call Stack Window
16h 24m remaining
07.43 Setting a Breakpoint in the Call Stack Window
DEFAULT

Ctrl+Alt+C

VISUAL BASIC 6

Ctrl+Alt+C; Ctrl+L

VISUAL C# 2005

Ctrl+Alt+C; Ctrl+D, Ctrl+C; Ctrl+D, C

VISUAL C++ 2

Ctrl+Alt+C; Ctrl+K; Alt+6

VISUAL C++ 6

Ctrl+Alt+C; Alt+7

VISUAL STUDIO 6

Ctrl+Alt+C

WINDOWS

Alt,D, W, C

MENU

Debug | Toggle Breakpoint

COMMAND

Debug.CallStack

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0008

Did you know that breakpoints can be set inside the Call Stack window? This tip shows how to do it.

First, set a breakpoint deep in series of calls to get a nice call stack.

NOTE
If you don’t have a call stack handy, just make several methods called One, Two, Three, and so forth and have them call each other, as I have done in these examples.

Run your code, and let it stop at the breakpoint. Bring up your Call Stack window (Ctrl+Alt+C or Debug | Windows | Call Stack):


Click somewhere in the call stack you would like to stop at as it unwinds, and press F9:


It sets a breakpoint. You can verify this by looking in your Breakpoints window:


Now just press F5 to continue, and watch as the debugger stops at the place you told it to:






07.43 Setting a Breakpoint in the Call Stack Window
07.44 Setting a Tracepoint in the Call Stack Window
07.45 Using the WPF Tree Visualizer
16h 24m remaining
07.44 Setting a Tracepoint in the Call Stack Window
DEFAULT

Ctrl+Alt+C

VISUAL BASIC 6

Ctrl+Alt+C; Ctrl+L

VISUAL C# 2005

Ctrl+Alt+C; Ctrl+D, Ctrl+C; Ctrl+D, C

VISUAL C++ 2

Ctrl+Alt+C; Ctrl+K; Alt+6

VISUAL C++ 6

Ctrl+Alt+C; Alt+7

VISUAL STUDIO 6

Ctrl+Alt+C

WINDOWS

Alt,D, W, C

COMMAND

Debug.CallStack

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0009

In vstipDebug0008 (07.43 Setting a Breakpoint in the Call Stack Window, page 367), I showed you a classic technique of setting a breakpoint in the Call Stack window. The only problem is that breakpoints tend to be somewhat intrusive if all you want is information. So I thought it would be a good idea to also show how to set tracepoints. For more information about tracepoints, see vstipDebug0010 (07.25 Setting a Tracepoint in Source Code, page 325).

Set a breakpoint deep in series of calls to get a nice call stack.

NOTE
If you don’t have a call series handy, just make several methods called One, Two, Three, and so forth, and have them call each other, as I have done in these examples.

Run your code, and let it stop at the breakpoint.

Bring up your Call Stack window (Ctrl+Alt+C or Debug | Windows | Call Stack):


Right-click some place in the stack where you would like to set a tracepoint, and go to Breakpoint | Insert Tracepoint:


You get the When Breakpoint Is Hit dialog box:


You definitely want to get up to speed on the details of tracepoints if you aren’t familiar with them (see vstipDebug0010, 07.25 Setting a Tracepoint in Source Code on page 325), but for now, just click OK.

Now we get our tracepoint. (Notice the diamond glyph.)


Press F5 to continue the program and let the call stack unwind.

Now bring up your Output window (Debug | Windows | Output), and notice that the trace information is in there:






07.44 Setting a Tracepoint in the Call Stack Window
07.45 Using the WPF Tree Visualizer
07.46 Understanding Break All Processes When One Process Breaks
16h 24m remaining
07.45 Using the WPF Tree Visualizer
VERSIONS

2010

CODE

vstipDebug0004

The WPF Tree Visualizer started out as a CodePlex project and ended up in the product itself as a visualizer. This tip shows how you can use it.

NOTE
For those unfamiliar with WPF trees, you might want to review the article “Trees in WPF,” at http://msdn.microsoft.com/en-us/library/ms753391(VS.100).aspx.

Enter Debug mode in any WPF project you have. Then take a look at a DataTip, the Watch window, the Autos window, or the Locals window. For this example, let’s use the Autos window:


Choose any control in the Autos window, and then click the magnifying glass way over to the right of the control name:



On the drop-down list, choose WPF Tree Visualizer to get the following dialog box:


This dialog box has a lot of moving parts, so let’s take a look at each one. First, the Visual Tree section shows you the hierarchy of the controls:


Clicking on any particular node of the tree shows you the rendering at the bottom:


Also, the selected control has its properties displayed in the large area to the right:


In both the Visual Tree and the Properties area, you can search or filter the results by typing into the Search or Filter text boxes respectively:


WARNING
Watch out for the results because they might not be what you expect. See the extra items in the list that don’t have the word “keyboard” in them? How did they get there? Well, if I scroll to the right and look at other properties, you can see how it happened. Currently, there is no way that I am aware of to change this behavior.






07.45 Using the WPF Tree Visualizer
07.46 Understanding Break All Processes When One Process Breaks
07.47 Changing Context in the Locals Window
16h 24m remaining
07.46 Understanding Break All Processes When One Process Breaks
MENU

Tools | Options | Debugging | General

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipDebug0029

In vstipEnv0015 (02.05 Multiple Startup Projects, page 48), we examined how to run multiple projects at the same time. Now let’s explore what happens when you go into break mode on the applications. By default, when you break one application, all the other applications break too. Let’s take a look at an example.

You set a breakpoint in your first application that has a hit counter on it (see vstipDebug0019, 07.20 Breakpoint Hit Count, on page 314):


But you don’t have any breakpoints in your second application:


When you run the applications, you get the following:


Both applications stop when one of them stops. This behavior is set in Tools | Options | Debugging | General by selecting the Break All Processes When One Process Breaks check box:


If you turn this feature off and run your applications again, you see the following (predictable) result:






07.46 Understanding Break All Processes When One Process Breaks
07.47 Changing Context in the Locals Window
07.48 Understanding the Autos Window
16h 24m remaining
07.47 Changing Context in the Locals Window
DEFAULT

Ctrl+Alt+V, L (locals);

Ctrl+5 then Alt+Down Arrow (process combo);

Ctrl+6 then Alt+Down Arrow (thread combo);

Ctrl+7 then Alt+Down Arrow (stack frame combo)

VISUAL BASIC 6

Ctrl+Alt+V, L (locals);

Ctrl+5 then Alt+Down Arrow (process combo);

Ctrl+6 then Alt+Down Arrow (thread combo);

Ctrl+7 then Alt+Down Arrow (stack frame combo)

VISUAL C# 2005

Ctrl+Alt+V, L (locals); Ctrl+D, Ctrl+L (locals); Ctrl+D, L (locals);

Ctrl+5 then Alt+Down Arrow (process combo);

Ctrl+6 then Alt+Down Arrow (thread combo);

Ctrl+7 then Alt+Down Arrow (stack frame combo)

VISUAL C++ 2

Ctrl+Alt+V, L (locals); Alt+3 (locals);

Ctrl+5 then Alt+Down Arrow (process combo);

Ctrl+6 then Alt+Down Arrow (thread combo);

Ctrl+7 then Alt+Down Arrow (stack frame combo)

VISUAL C++ 6

Ctrl+Alt+V, L (locals); Alt+4 (locals);

Ctrl+5 then Alt+Down Arrow (process combo);

Ctrl+6 then Alt+Down Arrow (thread combo);

Ctrl+7 then Alt+Down Arrow (stack frame combo)

VISUAL STUDIO 6

Ctrl+Alt+V, L (locals); Ctrl+Alt+L (locals);

Ctrl+5 then Alt+Down Arrow (process combo);

Ctrl+6 then Alt+Down Arrow (thread combo);

Ctrl+7 then Alt+Down Arrow (stack frame combo)

WINDOWS

Alt,D, W, L (locals)

MENU

Debug | Windows | Locals

COMMAND

Debug.Locals; Debug.LocationToolbar.ProcessCombo;Debug.LocationToolbar.ThreadCombo; Debug.LocationToolbar.StackFrameCombo

VERSIONS

2005, 2008, 2010

CODE

vstipTool0101

Most people are familiar with the Locals window. For those who aren’t, it displays variables local to the current context or scope. Information often appears in the Locals window, but the information will not be current until the next time the program breaks.

Even those who are familiar with the Locals window might not know that you can change the context. When you are in break mode, bring up the Locals window (Ctrl+Alt+V, L):


Debug Location Toolbar
You can use the Debug Location toolbar to change the context of the Locals window. If you don’t have it up, you can right-click any toolbar and select Debug Location to make it appear:


Process
If you have multiple processes running, you can use the Process combo box (Ctrl+5) to change between them. In this example, we only have one process running:


Thread
The Thread combo (Ctrl+6) lets you change the thread context to different threads. While not of much use in this example, it is very useful in debugging multithreaded applications:


Stack Frame
The stack frame is probably the more common item you use when dealing with the Locals window. The Stack Frame combo box (Ctrl+7) allows you to switch between items in the call stack:


Currently, we’re in the one method and the Locals window shows the following:


Let’s change to another method in our code:


Now our Locals window shows the following:


Now you too can take advantage of the Debug Location toolbar to change your context and get new information in the Locals window.





07.47 Changing Context in the Locals Window
07.48 Understanding the Autos Window
II. Extensions for Visual Studio
16h 24m remaining
07.48 Understanding the Autos Window
DEFAULT

Ctrl+Alt+V, A

VISUAL BASIC 6

Ctrl+Alt+V, A

VISUAL C# 2005

Ctrl+Alt+V, A; Ctrl+D, Ctrl+A; Ctrl+D, A

Visual C++ 2:

Ctrl+Alt+V, A

VISUAL C++ 6

Ctrl+Alt+V, A

VISUAL STUDIO 6

Ctrl+Alt+V, A

WINDOWS

Alt,D, W, A

MENU

Debug | Windows | Autos

COMMAND

Debug.Autos

VERSIONS

2005, 2008, 2010

CODE

vstipTool0103

The Autos window looks a lot like the Locals window, but let’s take a closer look. According to the MSDN website (http://msdn.microsoft.com/en-us/library/aa290702(VS.71).aspx), here is what it does:

“The Autos window displays variables used in the current statement and the previous statement. (For Visual Basic, it displays variables in the current statement and three statements on either side of the current statement.)”

The current statement is the statement at the current execution location (the statement that will be executed next if execution continues). The debugger identifies these variables for you automatically, hence the window name.”

Changing Values
Just like the Locals window, you can change values in the Autos window:


Current and Previous Statement
Simple Example
OK let’s break this down. The Autos window does, in fact, show variables used in the current statement and previous statement. Following is a simple example in C# with some variables:


As you can see, it just shows the variable on the current line and the one before it—nothing else. Even though several lines have variables around them, the Autos window is not concerned with those variables. Now compare this to the Locals window that shows every variable in scope:


Another Example
I thought it would be instructive to see, step-by-step, how this works. Here I have stopped in some code:


Notice that it shows the current variable and the object variable that exists all the time. Now I go down two lines:


All I’m left with is the object variable. I go down another three lines:


Now I can see that “eLocal” is about to be used, and I go down one more line:


I can finally see that “eLocal” has changed, and “d” has shown up again because it is being used on the current line.

VB Shows Three Statements on Either Side
In versions prior to 2010, VB would, in fact, show three statements on either side of the current line. This is no longer true in Visual Studio 2010. The Autos window in Visual Basic acts just like the C++ and C# Autos windows and shows only the current line and the one prior.





07.48 Understanding the Autos Window
