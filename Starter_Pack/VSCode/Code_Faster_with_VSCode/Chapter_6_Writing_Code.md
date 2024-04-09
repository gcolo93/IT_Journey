Chapter 6. Writing Code
“We will never be rid of code, because code represents the details of the requirements. At some level those details cannot be ignored or abstracted; they have to be specified. And specifying requirements in such detail that a machine can execute them is programming. Such a specification is code.”

— Robert C. Martin “Clean Code: A Handbook of Agile Software Craftsmanship”
Writing code and debugging code are the two activities we tend to do more than any other as developers. It’s no accident that this chapter is one of the two largest in the book. Within these pages, you’ll find tips from older versions all the way through to the great new features in Visual Studio 2010. Really take your time to absorb the material here, and find those pieces that are most relevant to your situation.

As you are reading, make sure to pay particular attention to the new IntelliSense and box selection improvements. In my travels, thousands of people have found these particularly useful for daily work. Also, take some time to review the tips on code snippets and discover how they can accelerate your code writing.

06.01 Zoom In or Out of Text in the Editor Using the Mouse Wheel
WINDOWS

Ctrl,Mouse Wheel

COMMAND

View.ZoomIn; View.ZoomOut

VERSIONS

2010

CODE

vstipEdit0002

The editor has a new feature that allows you to instantly change the zoom factor of text. It’s particularly useful for pair programming and doing code demos for your team. Just hold down your Ctrl key and use the wheel on your mouse to zoom in or out.



If you don’t like this feature, you can disable it by installing an extension called “Disable Mouse Wheel Zoom,” which you can find at http://visualstudiogallery.msdn.microsoft.com/en-us/d088791c-150a-4834-8f28-462696a82bb8?SRC=VSIDE.





6. Writing Code
06.01 Zoom In or Out of Text in the Editor Using the Mouse Wheel
06.02 Zoom In or Out of Text in the Editor
16h 24m remaining
06.01 Zoom In or Out of Text in the Editor Using the Mouse Wheel
WINDOWS

Ctrl,Mouse Wheel

COMMAND

View.ZoomIn; View.ZoomOut

VERSIONS

2010

CODE

vstipEdit0002

The editor has a new feature that allows you to instantly change the zoom factor of text. It’s particularly useful for pair programming and doing code demos for your team. Just hold down your Ctrl key and use the wheel on your mouse to zoom in or out.



If you don’t like this feature, you can disable it by installing an extension called “Disable Mouse Wheel Zoom,” which you can find at http://visualstudiogallery.msdn.microsoft.com/en-us/d088791c-150a-4834-8f28-462696a82bb8?SRC=VSIDE.





06.01 Zoom In or Out of Text in the Editor Using the Mouse Wheel
06.02 Zoom In or Out of Text in the Editor
06.03 How to Keep from Accidentally Copying a Blank Line
16h 24m remaining
06.02 Zoom In or Out of Text in the Editor
DEFAULT

Ctrl+Shift+> (zoom in); Ctrl+Shift+< (zoom out)

VISUAL BASIC 6

Ctrl+Shift+> (zoom in); Ctrl+Shift+< (zoom out)

VISUAL C# 2005

Ctrl+Shift+> (zoom in); Ctrl+Shift+< (zoom out)

VISUAL C++ 2

Ctrl+Shift+> (zoom in); Ctrl+Shift+< (zoom out)

VISUAL C++ 6

Ctrl+Shift+> (zoom in); Ctrl+Shift+< (zoom out)

VISUAL STUDIO 6

Ctrl+Shift+> (zoom in); Ctrl+Shift+< (zoom out)

WINDOWS

[no shortcut]

COMMAND

View.ZoomIn; View.ZoomOut

VERSIONS

2010

CODE

vstipEdit0003

In vstipEdit0002, 06.01 Zoom In or Out of Text in the Editor Using the Mouse Wheel, on page 209, I showed you how to use the mouse to zoom in and out of your text. Now I’ll show you two additional ways to accomplish this goal.

Combo Box
First, you can change the zoom factor for text by using the Zoom combo box in the lower-left corner of the editor. Simply choose a pre-determined size, or type in a value of your own. To my knowledge there is no keyboard shortcut for getting to this area.


Keyboard
Second, you can use the keyboard shortcuts Ctrl+Shift+Greater Than (>), to zoom in, and Ctrl+Shift+Less Than (<), to zoom out.


Universal Zoom
The zoom factor is per tab and doesn’t apply across each file, so you need to manually set it on each tab. Alternatively, you can use an extension called “Presentation Zoom,” located at http://visualstudiogallery.msdn.microsoft.com/en-us/6a7a0b57-7059-470d-bcfa-60ceb78dc752?SRC=VSIDE.





06.02 Zoom In or Out of Text in the Editor
06.03 How to Keep from Accidentally Copying a Blank Line
06.04 Make IntelliSense Transparent
16h 24m remaining
06.03 How to Keep from Accidentally Copying a Blank Line
WINDOWS

Alt,T, O

MENU

Tools | Options | Text Editor | All Languages | General

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0004

Ever cut something and accidentally cut a blank line? I can’t really think of a good reason to cut or copy just a blank line, and yet you are still allowed to do it.

The good news is that you can keep this from ever happening again by simply going to Tools | Options | Text Editor | All Languages | General and clearing the Apply Cut Or Copy Commands To Blank Lines When There Is No Selection check box.






06.03 How to Keep from Accidentally Copying a Blank Line
06.04 Make IntelliSense Transparent
06.05 Cut or Delete the Current Line
16h 24m remaining
06.04 Make IntelliSense Transparent
WINDOWS

Ctrl

VERSIONS

2008, 2010

CODE

vstipEdit0077

Sometimes when you are writing code, you find yourself in a situation where IntelliSense is covering up something you want to see, as shown in the following illustration.


You can make it temporarily transparent simply by pressing and holding the Ctrl key.


Using this tip, you don’t have to get rid of IntelliSense, look at the code, and then bring IntelliSense back. Just press the Ctrl key, get the information you need, and move on.





06.04 Make IntelliSense Transparent
06.05 Cut or Delete the Current Line
06.06 Using the New IntelliSense: Keywords
16h 24m remaining
06.05 Cut or Delete the Current Line
DEFAULT

Ctrl+L (cut line);

Ctrl+Shift+L (delete line);

Shift+Del (cut line);

Ctrl+X (cut line)

VISUAL BASIC 6

Ctrl+Y (cut line);

[no shortcut] (delete line);

Shift+Del (cut line);

Ctrl+X (cut line)

VISUAL C# 2005

Ctrl+Y (cut line);

Ctrl+Shift+L (delete line);

Shift+Del (cut line);

Ctrl+X (cut line)

VISUAL C++ 2

Ctrl+Y (cut line);

Ctrl+L (cut line);

Ctrl+Shift+L (delete line);

Shift+Del (cut line);

Ctrl+X (cut line);

Ctrl+Alt+W (cut line)

VISUAL C++ 6

Ctrl+L (cut line);

Shift+Alt+L (cut line);

Ctrl+Shift+L (delete line);

Shift+Del (cut line);

Ctrl+X (cut line)

VISUAL STUDIO 6

Ctrl+M (cut line);

Ctrl+L (cut line);

Ctrl+Shift+L (delete line);

Ctrl+Shift+M (delete line);

Shift+Del (cut line);

Ctrl+X (cut line)

WINDOWS

Alt,E, T

MENU

Edit | Cut

COMMAND

Edit.LineCut;

Edit.LineDelete;

Edit.Cut

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0038

You will often find times when you want to cut a line to be pasted somewhere else or just delete a line entirely. Let’s take a look at how you can quickly cut or delete any line.

Regardless of what you are trying to do, begin by placing your cursor inside the line anywhere:


Cut
If you want to cut the line for use somewhere else, perform one of the following actions:

Press Ctrl+L to cut the line; this uses the Edit.LineCut command.

Press Shift+Del or Ctrl+X to cut the line using the Edit.Cut command.

There is no difference in the result just two different commands for accomplishing the same task.

Delete
If you want to delete the line instead, you can use Ctrl+Shift+L to have it permanently removed from your code.





06.05 Cut or Delete the Current Line
06.06 Using the New IntelliSense: Keywords
06.07 Using the New IntelliSense: Pascal Case
16h 24m remaining
06.06 Using the New IntelliSense: Keywords
DEFAULT

Ctrl+J

VISUAL BASIC 6

Ctrl+J

VISUAL C# 2005

Ctrl+J

Ctrl+K, L

Ctrl+K, Ctrl+L

VISUAL C++ 2

Ctrl+J

Ctrl+Alt+T

VISUAL C++ 6

Ctrl+J

Ctrl+Alt+T

VISUAL STUDIO 6

Ctrl+J

WINDOWS

Alt,E, I, L

MENU

Edit | IntelliSense | List Members

COMMAND

Edit.ListMembers

VERSIONS

2010

LANGUAGES

VB, C#

CODE

vstipEdit0016

The one feature we use more than just about anything else in Visual Studio is IntelliSense. It has been our friend for many years. Well, it just got friendlier. To show you the new features, let’s take a closer look at Visual Studio 2008 IntelliSense. Notice what happens when you type Console.Key:


It does what you would expect it to do and highlights the first (in this case, only) item that begins with the word “Key” in a huge alphabetical list of item names. That’s great, but what if you don’t know what you are looking for but you do know that it has the word “Key” somewhere in it? Well, you can go search in the Object Browser, of course, or better yet, you can use the new IntelliSense in Visual Studio 2010. Look what happens when you do the same thing in Visual Studio 2010:


It now shows only those items that have the word “Key” in them and doesn’t care where the word is in the name of the member. This results in a significantly smaller list of items in IntelliSense and an easier way to find names even if you don’t know what they begin with.





06.06 Using the New IntelliSense: Keywords
06.07 Using the New IntelliSense: Pascal Case
06.08 Comment and Uncomment in Web Pages
16h 24m remaining
06.07 Using the New IntelliSense: Pascal Case
DEFAULT

Ctrl+J

VISUAL BASIC 6

Ctrl+J

VISUAL C# 2005

Ctrl+J

Ctrl+K, L

Ctrl+K, Ctrl+L

VISUAL C++ 2

Ctrl+J

Ctrl+Alt+T

VISUAL C++ 6

Ctrl+J

Ctrl+Alt+T

VISUAL STUDIO 6

Ctrl+J

WINDOWS

Alt,E, I, L

MENU

Edit | IntelliSense | List Members

COMMAND

Edit.ListMembers

VERSIONS

2010

LANGUAGES

VB, C#

CODE

vstipEdit0017

Have you ever been in a situation where you wanted to use IntelliSense to get a method but you’re faced with a ton of methods that start with same word, meaning that you have to type almost the entire method name?


Well, those days are over. Let’s say you want the SetWindowSize method, but you really, really don’t want to type it out or even scroll down to get the method. IntelliSense now supports Pascal case. All you have to do is type SWS, and you are all set:


What if you don’t remember all the uppercase letters in a name? No problem. Just type what you know (they don’t even have to be in the correct order), and IntelliSense narrows the list down for you:






06.07 Using the New IntelliSense: Pascal Case
06.08 Comment and Uncomment in Web Pages
06.09 Insert a Blank Line Above or Below the Current Line
16h 24m remaining
06.08 Comment and Uncomment in Web Pages
DEFAULT

Ctrl+K, Ctrl+C (comment);

Ctrl+K, Ctrl+U (uncomment)

VISUAL BASIC 6

Ctrl+K, Ctrl+C (comment);

Ctrl+K, Ctrl+U (uncomment)

VISUAL C# 2005

Ctrl+K, Ctrl+C (comment);

Ctrl+E, Ctrl+C (comment);

Ctrl +E, C (comment);

Ctrl+K, Ctrl+U (uncomment)

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+K, Ctrl+C (comment);

Ctrl+K, Ctrl+U (uncomment)

VISUAL STUDIO 6

Ctrl+K, Ctrl+C (comment);

Ctrl+K, Ctrl+U (uncomment)

WINDOWS

Alt,E, V, M (comment)

Alt,E, V, E (uncomment)

MENU

Edit | Advanced | Comment Selection;

Edit | Advanced | Uncomment Selection

COMMAND

Edit.CommentSelection;

Edit.UncommentSelection

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0083

By now, you probably know that you can comment and uncomment your code, but did you know that you can do the same thing with your source during web development? Just put your cursor inside any element you want commented, as shown in the following illustration.


Comment
Now just press Ctrl+K, Ctrl+C to comment out the selection.


Of course, you can also select multiple elements:


And you can comment them out too:


Uncomment
Naturally, you can put your cursor inside any commented area:


And you can uncomment that area by pressing Ctrl+K, Ctrl+U:






06.08 Comment and Uncomment in Web Pages
06.09 Insert a Blank Line Above or Below the Current Line
06.10 Transpose Lines, Words, and Characters
16h 24m remaining
06.09 Insert a Blank Line Above or Below the Current Line
DEFAULT

Ctrl+Enter (line above); Ctrl+Shift+Enter (line below)

VISUAL BASIC 6

Ctrl+Enter (line above); Ctrl+Shift+Enter (line below)

VISUAL C# 2005

Ctrl+Enter (line above); Ctrl+Shift+Enter (line below)

VISUAL C++ 2

Ctrl+Enter (line above); Ctrl+Shift+Enter (line below)

VISUAL C++ 6

Ctrl+Enter (line above); Ctrl+Shift+Enter (line below)

VISUAL STUDIO 6

Ctrl+Enter (line above); Ctrl+Shift+Enter (line below)

WINDOWS

[no shortcut]

COMMAND

Edit.LineOpenAbove; Edit.LineOpenBelow

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0005

This is a great feature for adding extra white space when you need it. Go to any line in the editor, and press Ctrl+Enter to insert a blank line above or press Ctrl+Shift+Enter to insert a blank line below the current line, as shown in the following illustration.






06.09 Insert a Blank Line Above or Below the Current Line
06.10 Transpose Lines, Words, and Characters
06.11 How to Cycle Through the Clipboard Ring
16h 24m remaining
06.10 Transpose Lines, Words, and Characters
DEFAULT

Alt+Shift+T (line); Ctrl+Shift+T (word); Ctrl+T (character)

VISUAL BASIC 6

Alt+Shift+T (line); Ctrl+Shift+T (word); [no shortcut] (character)

VISUAL C# 2005

Alt+Shift+T (line); Ctrl+Shift+T (word); Ctrl+T (character)

VISUAL C++ 2

Alt+Shift+T (line); Ctrl+Shift+T (word); Ctrl+T (character)

VISUAL C++ 6

Alt+Shift+T (line); Ctrl+Shift+T (word); Ctrl+T (character)

VISUAL STUDIO 6

Alt+Shift+T (line); Ctrl+Shift+T (word); Ctrl+T (character)

WINDOWS

[no shortcut]

COMMAND

Edit.LineTranspose; Edit.WordTranspose; Edit.CharTranspose

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0042

Ever have a line you want to move down or switch with another line? Just find a couple of lines you want to switch, and put your cursor in the top line:


Then press Alt+Shift+T to transpose the two lines:


You can also do something similar with words. Place the cursor in the word you want to transpose:


Press Ctrl+Shift+T:


Just want to transpose a character? Just place the cursor to the right of the character you want to transpose:


And then press Ctrl+T to transpose that character with the character at its immediate right:






06.10 Transpose Lines, Words, and Characters
06.11 How to Cycle Through the Clipboard Ring
06.12 Using the Undo and Redo Stack
16h 24m remaining
06.11 How to Cycle Through the Clipboard Ring
DEFAULT

Ctrl+Shift+V; Ctrl+Shift+Insert

VISUAL BASIC 6

Ctrl+Shift+V; Ctrl+Shift+Insert

VISUAL C# 2005

Ctrl+Shift+V; Ctrl+Shift+Insert

VISUAL C++ 2

Ctrl+Shift+V; Ctrl+Shift+Insert

VISUAL C++ 6

Ctrl+Shift+Insert

VISUAL STUDIO 6

Ctrl+Shift+V; Ctrl+Shift+Insert

WINDOWS

Alt,E, Y

MENU

Edit | Cycle Clipboard Ring

COMMAND

Edit.CycleClipboardRing

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0001

The Clipboard Ring keeps track of the past 20 items you’ve either cut or copied so that you can reuse them over and over again. After you hit item 20, it goes back to the first item. This is why the feature is called the Clipboard Ring.

This is particularly useful when you move between several code windows and need to copy and paste different items. You can copy all of the code from the original window and then go to one of the other windows and, using the Clipboard Ring, paste all of your items.


Try it out. Copy a few pieces of text into your clipboard, and then keep pressing Ctrl+Shift+V to repeat-paste them into the editor. This is one seriously cool time-saving feature. Unfortunately, there is no way to see the contents of the Clipboard Ring in Visual Studio without cycling through the list.





06.11 How to Cycle Through the Clipboard Ring
06.12 Using the Undo and Redo Stack
06.13 Undo and Redo Global Actions
16h 24m remaining
06.12 Using the Undo and Redo Stack
DEFAULT

Ctrl+Z (undo); Alt+Backspace (undo); Ctrl+Shift+Z (redo); Alt+Shift+Backspace (redo); Ctrl+Y (redo)

VISUAL BASIC 6

Ctrl+Shift+Z (redo); Alt+Shift+Backspace (redo)

VISUAL C# 2005

Ctrl+Z (undo); Alt+Backspace (undo); Ctrl+Shift+Z (redo); Alt+Shift+Backspace (redo); Ctrl+Y (redo)

VISUAL C++ 2

Ctrl+Shift+Z (redo); Alt+Shift+Backspace (redo); Ctrl+Y (redo); Ctrl+A

VISUAL C++ 6

Ctrl+Z (undo); Alt+Backspace (undo); Ctrl+Shift+Z (redo); Alt+Shift+Backspace (redo); Ctrl+Y (redo)

VISUAL STUDIO 6

Ctrl+Z (undo); Alt+Backspace (undo); Ctrl+Shift+Z (redo); Alt+Shift+Backspace (redo); Ctrl+Y (redo)

WINDOWS

Alt,E, U (undo); Alt,E, R (redo)

MENU

Edit | Undo; Edit | Redo

COMMAND

Edit.Undo; Edit.Redo

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0045

We have all used Ctrl+Z (undo) at one time or another to fix a mistake. Did you know you don’t have to press Ctrl+Z a billion times to go back to a particular action? The Undo and Redo stacks are readily available for you to use for quick, multiple undo or redo operations.

It’s easy to use. Just locate the Undo and Redo section of the toolbar shown in the following illustration.


Next, click the drop-down arrow for the action you want to perform. In this case, let’s look at the Undo stack:


By default, it undoes only the last action. However, notice what happens when I put my mouse over the list:


It automatically selects multiple actions to undo or redo. Also notice that it shows you at the bottom how many actions you are about to undo. When you have all the actions selected that you want to undo or redo, just click the left mouse button.





06.12 Using the Undo and Redo Stack
06.13 Undo and Redo Global Actions
06.14 How to Use Reference Highlighting
16h 24m remaining
06.13 Undo and Redo Global Actions
WINDOWS

Alt,E, N (undo); Alt,E, U (redo)

MENU

Edit | Undo Last Global Action; Edit | Redo Last Global Action

COMMAND

Edit.UndoLastGlobalAction; Edit.RedoLastGlobalAction

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0020

Everyone knows about undo and redo, but did you know that the Edit menu offers global versions of these actions?


By definition, global actions impact multiple files. Global actions include renaming a class or namespace, performing a find-and-replace operation across a solution, refactoring a database, or any other action that changes multiple files.

You can apply the global undo and redo commands to actions in the current Visual Studio session, even after you close the solution that an action applies to.





06.13 Undo and Redo Global Actions
06.14 How to Use Reference Highlighting
06.15 Moving or Selecting Between Matching Braces (C++, C# Only)
16h 24m remaining
06.14 How to Use Reference Highlighting
DEFAULT

Ctrl+Shift+Down Arrow (next); Ctrl+Shift+Up Arrow (previous)

VISUAL BASIC 6

Ctrl+Shift+Down Arrow (next); Ctrl+Shift+Up Arrow (previous)

VISUAL C# 2005

Ctrl+Shift+Down Arrow (next); Ctrl+Shift+Up Arrow (previous)

VISUAL C++ 2

Ctrl+Shift+Down Arrow (next); Ctrl+Shift+Up Arrow (previous)

VISUAL C++ 6

Ctrl+Shift+Down Arrow (next); Ctrl+Shift+Up Arrow (previous)

VISUAL STUDIO 6

Ctrl+Shift+Down Arrow (next); Ctrl+Shift+Up Arrow (previous)

WINDOWS

[no shortcut]

COMMAND

Edit.NextHighlightedReference; Edit.PreviousHighlightedReference

VERSIONS

2010

LANGUAGES

C#, VB

CODE

vstipEdit0010

This is absolutely one of my favorite tips because you don’t have to do anything to make it work. The MSDN documentation (at http://msdn.microsoft.com/en-us/library/ee349251.aspx) describes reference highlighting this way:

“When you click a symbol in the Code Editor, all instances of the symbol are highlighted in the document. […] Highlighted symbols may include declarations and references, and generally anything else that Find All References would return. This includes the names of classes, objects, variables, methods, and properties.”


Navigation
All you have to do is click in any symbol, and it automatically highlights any references in the current document. You can navigate through the highlights by using Ctrl+Shift+Down Arrow (next) or Ctrl+Shift+Up Arrow (previous).

Turning it Off
What if you don’t like this feature? You can always turn it off by using following instructions, depending on whether you’re working in VB or C#.

VB: Go to Tools | Options | Text Editor | Basic | VB Specific, and clear the Enable Highlighting Of References And Keywords check box.


C#: Go to Tools | Options | Text Editor | C#| Advanced, and clear the Highlight References To Symbol Under Cursor check box.






06.14 How to Use Reference Highlighting
06.15 Moving or Selecting Between Matching Braces (C++, C# Only)
06.16 Invoke Statement Completion
16h 24m remaining
06.15 Moving or Selecting Between Matching Braces (C++, C# Only)
DEFAULT

Ctrl+] (move); Ctrl+Shift+] (select)

VISUAL BASIC 6

Ctrl+] (move); Ctrl+Shift+] (select)

VISUAL C# 2005

Ctrl+] (move); Ctrl+Shift+] (select)

VISUAL C++ 2

Ctrl+] (move); Ctrl+M (move);

Ctrl+Shift+] (select); Ctrl+Shift+M (select)

VISUAL C++ 6

Ctrl+] (move); Ctrl+Shift+] (select)

VISUAL STUDIO 6

Ctrl+] (move); Ctrl+Shift+] (select)

WINDOWS

[no shortcut]

COMMAND

Edit.GotoBrace; Edit.GotoBraceExtend

VERSIONS

2005, 2008, 2010

LANGUAGES

C++, C#

CODE

vstipEdit0075

When you are working with the C* languages, you sometimes want to move to the bottom or top of a method or code block. You can quickly travel or select between matching braces by performing the following steps.

Moving
Click next to an opening or closing brace:



Now press Ctrl+] to go from one brace to the other one. You should find yourself easily navigating between them. This technique is very useful when you have braces far apart from each other. Also notice that the term “brace” is very loose here and applies to curly braces, square brackets, and parentheses.

Selecting
In addition to moving, you can also select everything between matching braces by pressing Ctrl+Shift+], as shown in the following illustration.






06.15 Moving or Selecting Between Matching Braces (C++, C# Only)
06.16 Invoke Statement Completion
06.17 Move Between the Common Tab and All Tab in Statement Completion (VB)
16h 24m remaining
06.16 Invoke Statement Completion
DEFAULT

Ctrl+J

VISUAL BASIC 6

Ctrl+J

VISUAL C# 2005

Ctrl+J; Ctrl+K, Ctrl+L; Ctrl+K, L

VISUAL C++ 2

Ctrl+J; Ctrl+Alt+T

VISUAL C++ 6

Ctrl+J; Ctrl+Alt+T

VISUAL STUDIO 6

Ctrl+J

WINDOWS

Alt,E, I, L

MENU

Edit | IntelliSense | List Members

COMMAND

Edit.ListMembers

VERSIONS

2005, 2008, 2010

LANGUAGES

C++ (not available in VS2010), C#, VB

CODE

vstipEdit0061

This little trick is particularly useful if you lose IntelliSense and want to get it back. You can invoke statement completion from the command line by using Ctrl+J.






06.16 Invoke Statement Completion
06.17 Move Between the Common Tab and All Tab in Statement Completion (VB)
06.18 Using Parameter Information
16h 24m remaining
06.17 Move Between the Common Tab and All Tab in Statement Completion (VB)
DEFAULT

Alt+. (All Tab); Alt+, (Common Tab)

COMMAND

Edit.IncreaseFilterLevel; Edit.DecreaseFilterLevel

VERSIONS

2005, 2008, 2010

LANGUAGES

VB

CODE

vstipEdit0064

You don’t have to take your hands off the keyboard when switching between Common and All in statement completion for Visual Basic. Just press Alt+Period (.) to go to the All tab, and press Alt+Comma (,) to go to the Common tab.






06.17 Move Between the Common Tab and All Tab in Statement Completion (VB)
06.18 Using Parameter Information
06.19 Using Quick Info
16h 24m remaining
06.18 Using Parameter Information
DEFAULT

Ctrl+Shift+Space (show Parameter Info); Up or Down Arrow (move to next or previous overload)

VISUAL BASIC 6

Ctrl+Shift+Space (show Parameter Info); Ctrl+Shift+I (show Parameter Info); Up or Down Arrow (move to next or previous overload)

VISUAL C# 2005

Ctrl+Shift+Space (show Parameter Info); Ctrl+K, Ctrl+P (show Parameter Info); Ctrl+K, P (show Parameter Info); Up or Down Arrow (move to next or previous overload)

VISUAL C++ 2

Ctrl+Shift+Space (show Parameter Info); Up or Down Arrow (move to next or previous overload)

VISUAL C++ 6

Ctrl+Shift+Space (show Parameter Info); Up or Down Arrow (move to next or previous overload)

VISUAL STUDIO 6

Ctrl+Shift+Space (show Parameter Info); Ctrl+Shift+I (show Parameter Info); Up or Down Arrow (move to next or previous overload)

WINDOWS

Alt,E, I, P

MENU

Edit | IntelliSense | Parameter Info

COMMAND

Edit.ParameterInfo

VERSIONS

2005, 2008, 2010

LANGUAGES

C++ (not available in VS2010); C#, VB

CODE

vstipEdit0062

When working with a function, you automatically get parameter information, as shown in the following illustration.


If it goes away and you want it back, you can always press Ctrl+Shift+Space.

Also notice that the function in this example has 19 overloads. You can iterate through them by pressing your Up or Down Arrow keys. If you are using your mouse, you can go forward by clicking anywhere in the parameter information area. You do not have to click the tiny up and down arrows inside the box unless you want to go backward in the list.





06.18 Using Parameter Information
06.19 Using Quick Info
06.20 Word Completion
16h 24m remaining
06.19 Using Quick Info
DEFAULT

Ctrl+K, Ctrl+I

VISUAL BASIC 6

Ctrl+K, Ctrl+I; Ctrl+I

VISUAL C# 2005

Ctrl+K, Ctrl+I; Ctrl+K, I

VISUAL C++ 2

Ctrl+T

VISUAL C++ 6

Ctrl+K, Ctrl+I

VISUAL STUDIO 6

Ctrl+K, Ctrl+I; Ctrl+I

WINDOWS

ALT,E, I, Q

MENU

Edit | IntelliSense | Quick Info

COMMAND

Edit.QuickInfo

VERSIONS

2005, 2008, 2010

LANGUAGES

C++ (not available in VS2010), C#, VB

CODE

vstipEdit0063

The Quick Info option helps you identify the details of a particular function. It comes up automatically as you type, but if it goes away, you can quickly bring it back by placing the cursor in a method and pressing Ctrl+K, Ctrl+I.






06.19 Using Quick Info
06.20 Word Completion
06.21 Drag and Drop Code into the Toolbox
16h 24m remaining
06.20 Word Completion
DEFAULT

Ctrl+Space; Alt+Right Arrow

VISUAL BASIC 6

Ctrl+Space; Alt+Right Arrow

VISUAL C# 2005

Ctrl+Space; Alt+Right Arrow

Ctrl+K, Ctrl+W; Ctrl+K, W

VISUAL C++ 2

Ctrl+Space; Alt+Right Arrow

VISUAL C++ 6

Ctrl+Space; Alt+Right Arrow

VISUAL STUDIO 6

Ctrl+Space; Alt+Right Arrow

WINDOWS

Alt,E, I, W

MENU

Edit | IntelliSense | Complete Word

COMMAND

Edit.CompleteWord

VERSIONS

2005, 2008, 2010

LANGUAGES

C++ (not available in VS2010), C#, VB

CODE

vstipEdit0065

This one is very popular and one of the core skills to use in Visual Studio. Let’s say you are typing and you have the situation shown in the following illustration.


You can press Ctrl+Space or Alt+Right Arrow to complete the word:


This works only if there are no other possible matches. Suppose, for example, that you have something similar to the following:


If you now press Ctrl+Space or Alt+Right Arrow to complete the word, you would just get statement completion instead.





06.20 Word Completion
06.21 Drag and Drop Code into the Toolbox
06.22 Using Smart Tags from the Keyboard
16h 24m remaining
06.21 Drag and Drop Code into the Toolbox
VERSIONS

2005, 2008, 2010

CODE

vstipTool0007

Got code you use all the time? Start using the Toolbox for more than just controls. When you are in the Editor, the Toolbox appears as shown in the following illustration.


This is a vast expanse of opportunity! Just select some text from the editor, and drag it into the Toolbox and see the magic happen.

Now you have code ready to go anytime. Just place the cursor where you want the code to go, and double-click the item in your Toolbox.


You can also click and drag where you want the code to go, as shown in the following illustration.


You also have a couple of extra things you can do. For example, you can rename (among other tasks) the item in the Toolbox to whatever you would like by right-clicking on it:


You can also create additional tabs, delete existing tabs, and rename tabs to organize the Toolbox better.






06.21 Drag and Drop Code into the Toolbox
06.22 Using Smart Tags from the Keyboard
06.23 Organize Using Statements (C# Only)
16h 24m remaining
06.22 Using Smart Tags from the Keyboard
DEFAULT

Ctrl+. (period);

Shift+Alt+F10

VISUAL BASIC 6

Ctrl+. (period);

Shift+Alt+F10

VISUAL C# 2005

Ctrl+. (period);

Shift+Alt+F10

VISUAL C++ 2

Ctrl+. (period);

Shift+Alt+F10

VISUAL C++ 6

Ctrl+. (period);

Shift+Alt+F10

VISUAL STUDIO 6

Ctrl+. (period);

Shift+Alt+F10

WINDOWS

[no shortcut]

COMMAND

View.ShowSmartTag

VERSIONS

2008, 2010

LANGUAGES

C#, VB

CODE

vstipEdit0076

You have probably seen the smart tag indicator before. It’s a blue or red bar that shows up in your code when you use certain items.


Most people just put their mouse over the line and choose the option(s) listed in the tag.


However, did you know that you can use a keyboard shortcut to bring up the options? Just press Ctrl+Period (.), and it brings up the option(s) without using the mouse.





06.22 Using Smart Tags from the Keyboard
06.23 Organize Using Statements (C# Only)
06.24 Switch Between Design and Source in Web Projects
16h 24m remaining
06.23 Organize Using Statements (C# Only)
WINDOWS

Alt,E, I, [R (remove), U (sort), A (remove and sort)]

MENU

Edit | IntelliSense | Organize Usings | [Remove Unused Usings, Sort Usings, Remove and Sort]; Right Click | Organize Usings | [Remove Unused Usings, Sort Usings, Remove and Sort]

COMMAND

EditorContextMenus.CodeWindow.OrganizeUsings.[RemoveUnusedUsings, SortUsings, RemoveAndSort]

VERSIONS

2008, 2010

LANGUAGES

C#

CODE

vstipEdit0070

You can easily organize your using statements. Simply right-click anywhere in the editor to get the context menu, choose Organize Usings, and then Remove, Sort, or Remove And Sort.


Remove Unused Usings
Before removing unused using directives, using aliases, and extern aliases, you should consider a couple things about this feature.

First, it should be used only on code that builds, because it could remove required using statements if activated on code that does not build. As shown in the following illustration, you have an option in Visual Studio 2008 (not Visual Studio 2010), found at Tools | Options | Text Editor | C# | Advanced | Organize Usings, that prevents you from removing using statements if your code doesn’t build.


Second, it works only on the active set of code. For example, suppose you have a set of using statements such as the following:


If you remove the unused using statements, you see the following result:


However, suppose those using statements are organized into code that has active and inactive blocks:


When you perform the action to remove them, only the extra using statements in the active block are removed:


Generally accepted reasons for removing unused using statements include the following:

Results in cleaner code

Significantly reduces the size of the IntelliSense list because there are fewer namespaces

Enables potentially faster compilation because the compiler has fewer namespaces to resolve

Avoids potential naming collisions when new types are added to the unused namespaces that might have the same name as types you are currently using

Sort Usings
When you perform a sort action on your using statements, they sort in the following order: extern aliases, using directives, using aliases. Also, by default, using statements that reference the System namespace are sorted before the other using directives. So, suppose you have some using statements such as the following:


When you sort them, you get the result shown in the following illustration.


Notice that the Microsoft namespace is below all the System namespaces. If you don’t like this behavior, you can change it by going to Tools | Options | Text Editor | C# | Advanced | Organize Usings and clearing the Place ‘System’ Directives First When Sorting Usings check box.

Now, when you sort, you see the following result:


Remove and Sort
When you click the Remove And Sort command, it first performs a remove operation and then it performs a sort operation.





06.23 Organize Using Statements (C# Only)
06.24 Switch Between Design and Source in Web Projects
06.25 Toggle Designer
16h 24m remaining
06.24 Switch Between Design and Source in Web Projects
DEFAULT

Shift+F7 (view designer and view markup toggle)

VISUAL BASIC 6

Shift+F7 (view designer and view markup toggle)

VISUAL C# 2005

Shift+F7 (view designer and view markup toggle)

VISUAL C++ 2

Shift+F7 (view designer and view markup toggle)

VISUAL C++ 6

Shift+F7 (view designer and view markup toggle)

VISUAL STUDIO 6

Shift+F7 (view designer and view markup toggle)

WINDOWS

Alt,V, D (view designer); Alt, V, K (view markup)

MENU

View | Designer; View | Markup

COMMAND

View.ViewDesigner; View.ViewMarkup

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0045

When working with web projects, you can switch between Design and Source (Markup) views quite easily.


In any view, simply press Shift+F7 to switch to the other view. In other words, you can press Shift+F7 as a toggle between views.

Split View
This keyboard shortcut does not work the way you might think in Split view.

Pressing Shift+F7 takes you to either the Design or Source view (depending on which one you were in last) and does not return to Split view when you press Shift+F7 again.





06.24 Switch Between Design and Source in Web Projects
06.25 Toggle Designer
06.26 Change the Default View in the HTML Editor
16h 24m remaining
06.25 Toggle Designer
DEFAULT

F7 (view designer); F7 (view code)

VISUAL BASIC 6

[no shortcut] (view designer); F7 (view code)

VISUAL C# 2005

[no shortcut] (view designer); F7 (view code)

VISUAL C++ 2

[no shortcut] (view designer); F7 (view code)

VISUAL C++ 6

[no shortcut] (view designer); F7 (view code)

VISUAL STUDIO 6

[no shortcut] (view designer); F7 (view code)

WINDOWS

Alt,V, D (view designer); Alt,V, C (view code)

MENU

View | Designer; View | Code

COMMAND

View.ToggleDesigner; View.ViewCode

VERSIONS

2005, 2008, 2010

CODE

vstipEnv0044

You often find that there is a need to switch from Design view (web, windows, or WPF) to code. You can use F7 to go from the current Source or Design view to the Code view.

To go back, just press F7 again. It’s a toggle, so it jumps back and forth between the views.

In WPF applications, you can use F7 to view code but not to go back to Design view, so it isn’t a full toggle operation in that scenario.





06.25 Toggle Designer
06.26 Change the Default View in the HTML Editor
06.27 Jump Back to the Editor from Just About Anywhere
16h 24m remaining
06.26 Change the Default View in the HTML Editor
WINDOWS

Alt,T, O

MENU

Tools | Options | HTML Designer | General

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0088

The default view when you use the HTML Designer is Source view.


If you don’t like this or just want another view to be the default, you can go to Tools | Options | HTML Designer | General and choose a new view in the Start Pages In area.


NOTE
In Visual Studio 2005, you don’t have the Split View option.





06.26 Change the Default View in the HTML Editor
06.27 Jump Back to the Editor from Just About Anywhere
06.28 Replacing Text with a Box Selection
16h 24m remaining
06.27 Jump Back to the Editor from Just About Anywhere
DEFAULT

Esc

VISUAL BASIC 6

Esc

VISUAL C# 2005

Esc

VISUAL C++ 2

Esc

VISUAL C++ 6

Esc; Alt+0

VISUAL STUDIO 6

Esc

WINDOWS

[no shortcut]

COMMAND

Window.ActivateDocumentWindow

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0066

Did you know that you can usually get to the active document window by just pressing Esc? For example, if you are in any tool window (like the Output window) and you press Esc, you go back to the active document window.

You might have to press Esc multiple times, depending on the situation, but it should almost always wind up at the active document window.





06.27 Jump Back to the Editor from Just About Anywhere
06.28 Replacing Text with a Box Selection
06.29 Pasting the Contents of One Box Selection into Another
16h 24m remaining
06.28 Replacing Text with a Box Selection
DEFAULT

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL BASIC 6

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C# 2005

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C++ 2

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C++ 6

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL STUDIO 6

Shift+Alt+[Up, Down, Left, Right] Arrow

WINDOWS

[no shortcut]

COMMAND

Edit.Line[Up, Down]ExtendColumn; Edit.Char[Left, Right]ExtendColumn

VERSIONS

2010

CODE

vstipEdit0006

You have been able to select a block of text for some time in Visual Studio by holding down the Alt+Shift+Arrow keys (or Alt+Left Mouse Button) and making a selection. In Visual Studio 2010, you can now do multiline replacements of a box selection.

Simply select a block of text:


Now type your replacement text:


The Editor turns your box selection into a zero-length box selection (a multiline cursor) that you can use to type in what you like.





06.28 Replacing Text with a Box Selection
06.29 Pasting the Contents of One Box Selection into Another
06.30 Pasting a Single Selection into a Box Selection
16h 24m remaining
06.29 Pasting the Contents of One Box Selection into Another
DEFAULT

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL BASIC 6

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C# 2005

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C++ 2

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C++ 6

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL STUDIO 6

Shift+Alt+[Up, Down, Left, Right] Arrow

WINDOWS

[no shortcut]

COMMAND

Edit.Line[Up, Down]ExtendColumn; Edit.Char[Left, Right]ExtendColumn

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0007

Box selection is a powerful tool that is often overlooked. One of the things you can do, for example, is paste one box selection into another of the same size. Let’s assume you have the following code:


However, you want the first set of variables to be the same data types as the second set (and in the same order). Simply box select (Alt+Left Mouse Button) the second set of data types, and then copy the selection (Ctrl+C).


Next, select the first set of data types (Alt+Left Mouse Button):


And paste (Ctrl+V):






06.29 Pasting the Contents of One Box Selection into Another
06.30 Pasting a Single Selection into a Box Selection
06.31 Using Zero-Length Box Selection
16h 24m remaining
06.30 Pasting a Single Selection into a Box Selection
DEFAULT

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL BASIC 6

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C# 2005

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C++ 2

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C++ 6

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL STUDIO 6

Shift+Alt+[Up, Down, Left, Right] Arrow

WINDOWS

[no shortcut]

COMMAND

Edit.Line[Up, Down]ExtendColumn; Edit.Char[Left, Right]ExtendColumn

VERSIONS

2010

CODE

vstipEdit0008

In this tip, we see how to take a single selection and put it into a box selection. Let’s assume you have the following code:


But you realize that you need change all the ints to doubles.

Select the double keyword and copy it (Ctrl+C):


Then box select the destination (Alt+left mouse button):


Finally, do a paste (Ctrl+V) to see the following result:






06.30 Pasting a Single Selection into a Box Selection
06.31 Using Zero-Length Box Selection
06.32 View White Space
16h 24m remaining
06.31 Using Zero-Length Box Selection
DEFAULT

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL BASIC 6

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C# 2005

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C++ 2

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL C++ 6

Shift+Alt+[Up, Down, Left, Right] Arrow

VISUAL STUDIO 6

Shift+Alt+[Up, Down, Left, Right] Arrow

WINDOWS

[no shortcut]

COMMAND

Edit.Line[Up, Down]ExtendColumn; Edit.Char[Left, Right]ExtendColumn

VERSIONS

2010

CODE

vstipEdit0009

The power of box selection is even more powerful with the new zero-length box selection. Let’s assume that you have a situation with some variables, like the ones shown in the following illustration, and you want to make them all public.


The answer is a zero-length box selection. Hold down your Alt key, and use your Down Arrow key to extend straight down. A line is created, as shown in the following illustration.


Release the keys, and now just start typing.


This feature acts just like any cursor, so you can go forward and backward at will, plus you can put one of these anywhere you want to create or edit multiple lines of text.





06.31 Using Zero-Length Box Selection
06.32 View White Space
06.33 Collapsing Your Code with Outlining
16h 24m remaining
06.32 View White Space
DEFAULT

Ctrl+R, Ctrl+W

VISUAL BASIC 6

[no shortcut]

VISUAL C# 2005

Ctrl+R, Ctrl+W; Ctrl+E, Ctrl+S; Ctrl+E, S

VISUAL C++ 2

Ctrl+R, Ctrl+W; Ctrl+Alt+T

VISUAL C++ 6

Ctrl+R, Ctrl+W; Ctrl+Shift+8

VISUAL STUDIO 6

Ctrl+R, Ctrl+W

WINDOWS

Alt,E, V, W

MENU

Edit | Advanced | View White Space

COMMAND

Edit.ViewWhiteSpace

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0043

Ever want to see the white space you are working with? Maybe you want to know whether you have tabs or extra spaces on lines? It’s easy to find out. Just go to Edit | Advanced | View White Space (Ctrl+R, Ctrl+W).



Spaces are represented as dots, and tabs are the arrows you see in the preceding illustration.





06.32 View White Space
06.33 Collapsing Your Code with Outlining
06.34 Using Hide Selection
16h 24m remaining
06.33 Collapsing Your Code with Outlining
DEFAULT

Ctrl+M, Ctrl+M

VISUAL BASIC 6

Ctrl+M, Ctrl+M

VISUAL C# 2005

Ctrl+M, Ctrl+M;

Ctrl+M, M

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

[no shortcut]

VISUAL STUDIO 6

[no shortcut]

WINDOWS

Alt, E, O, T

MENU

Edit | Outlining | Toggle Outlining Expansion

COMMAND

Edit.ToggleOutliningExpansion

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0029

By default, outlining is enabled in Visual Studio. It’s the line you see with the boxes to indicate the status of the area (collapsed or expanded):


You can collapse code to get it out of your way so that you can focus on other areas. You have four ways to do it.

Minus Sign
Click the minus sign to collapse an area of code.


NOTE
Visual Studio 2010, if Visual Experience is turned on in Tools | Options | Environment | General, now highlights the area that will be collapsed. If you don’t like the highlighting color, you can go to Tools | Options | Environment | Fonts and Colors and change the color for the Collapsible Region setting.

Vertical Line
In Visual Studio 2010 only, click anywhere on the vertical line in the highlighted region.


Click Anywhere in Area (Keyboard Shortcut)
Click anywhere in the area to be collapsed, and press Ctrl+M, Ctrl+M.

Click Anywhere in Area (Menu Item)
Click anywhere in the area to be collapsed, and go to Edit | Outlining | Toggle Outlining Expansion on the menu bar.

After collapsing, the code area looks like this:






06.33 Collapsing Your Code with Outlining
06.34 Using Hide Selection
06.35 Collapse to Definitions with Outlining
16h 24m remaining
06.34 Using Hide Selection
DEFAULT

Ctrl+M, Ctrl+H

VISUAL BASIC 6

Ctrl+M, Ctrl+H

VISUAL C# 2005

Ctrl+M, Ctrl+H

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+M, Ctrl+H

VISUAL STUDIO 6

[no shortcut]

WINDOWS

Alt, E, O, H

MENU

Edit | Outlining | Hide Selection

COMMAND

Edit.HideSelection

VERSIONS

2005 (C++ Only), 2008 (C++ Only), 2010

CODE

vstipEdit0036

Let’s say you have a chunk of code such as the following:


Outlining allows you to collapse only the entire method by default (minus sign in the upper-left corner of the preceding illustration). What if you want to collapse only the if statements at the top? First, select the chunk of code you want to hide.

NOTE
You don’t have to select entire lines for this feature to work. Just select as much or as little as you want to hide.


Now either press Ctrl+M, Ctrl+H or go to Edit | Outlining | Hide Selection on your menu bar.


You have successfully collapsed a selected region of code. Now you can expand and collapse the area as long as you like. Also, if you ever want to get rid of the new region, just press Ctrl+M, Ctrl+U or go to Edit | Outlining | Stop Hiding Current to remove the region.





06.34 Using Hide Selection
06.35 Collapse to Definitions with Outlining
06.36 Cut, Copy, and Paste Collapsed Code with Outlining
16h 24m remaining
06.35 Collapse to Definitions with Outlining
DEFAULT

Ctrl+M, Ctrl+O

VISUAL BASIC 6

Ctrl+M, Ctrl+O

VISUAL C# 2005

Ctrl+M, Ctrl+O; Ctrl+M, O

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+M, Ctrl+O

VISUAL STUDIO 6

[no shortcut]

WINDOWS

Alt, E, O, O

MENU

Edit | Outlining | Collapse to Definitions

COMMAND

Edit.CollapsetoDefinitions

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0032

One of the features of outlining is the Collapse To Definitions option. This feature collapses the areas for all members. Let’s suppose you have the following code:


You can press Ctrl+M, Ctrl+O, or you can go to Edit | Outlining | Collapse To Definitions on your menu bar to see the following result:






06.35 Collapse to Definitions with Outlining
06.36 Cut, Copy, and Paste Collapsed Code with Outlining
06.37 Understanding Word Wrap
16h 24m remaining
06.36 Cut, Copy, and Paste Collapsed Code with Outlining
VERSIONS

2005, 2008, 2010

CODE

vstipEdit0035

When working with outlining, you can perform many timesaving operations. One of these is the ability to take a piece of code and work with it in a collapsed state.

When you collapse code using outlining (click the minus sign to the left of the signature), you get the result shown in the following illustration.


Now we can select all of that code in one compact unit:


Then simply cut or copy the code, and paste it where you want.





06.36 Cut, Copy, and Paste Collapsed Code with Outlining
06.37 Understanding Word Wrap
06.38 Properties Window Keyboard Shortcuts
16h 24m remaining
06.37 Understanding Word Wrap
DEFAULT

Ctrl+E, Ctrl+W

VISUAL BASIC 6

[no shortcut]

VISUAL C# 2005

Ctrl+E, Ctrl+W; Ctrl+E, W

VISUAL C++ 2

Ctrl+E, Ctrl+W

VISUAL C++ 6

Ctrl+E, Ctrl+W

VISUAL STUDIO 6

Ctrl+E, Ctrl+W

WINDOWS

Alt, E, V, R

MENU

Edit | Advanced | Word Wrap;

Tools | Options | Text Editor | All Languages | General

COMMAND

Edit.ToggleWordWrap

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0022

You can turn on or off the word wrap feature by going to Tools | Options | Text Editor | All Languages | General and selecting or clearing the Word Wrap check box.

Word wrap automatically makes sure that your text is always in the visible space. So if you already have a lot of visible space, it probably doesn’t need to wrap.

But if you have less space and wrap is turned on, it wraps automatically, as shown in the following illustration.


And, naturally, if you have almost no space, it still makes sure all the text is in the visible space.


The arrows on the far right of each line (see the preceding illustration) show that the lines are being wrapped. This can be turned on or off by going to Tools | Options | Text Editor | All Languages | General and checking the Show Visual Glyphs For Word Wrap check box.






06.37 Understanding Word Wrap
06.38 Properties Window Keyboard Shortcuts
06.39 Document Outline: Web Projects
16h 24m remaining
06.38 Properties Window Keyboard Shortcuts
DEFAULT

F4 (properties window); Shift+F4 (property pages)

VISUAL BASIC 6

F4 (properties window); Shift+F4 (property pages)

VISUAL C# 2005

F4 (properties window); Ctrl+W, Ctrl+P (properties window); Ctrl+W, P (properties window)

VISUAL C++ 2

Alt+Enter (properties window); Ctrl+W (properties window); [no shortcut] (property pages)

VISUAL C++ 6

Alt+Enter (properties window); [no shortcut] (property pages)

VISUAL STUDIO 6

F4 (properties window); Shift+F4 (property pages)

WINDOWS

Alt,V, W (properties window); Alt,V, Y (property pages)

MENU

View | Properties; View | Property Pages

COMMAND

View.PropertiesWindow; View.PropertyPages

VERSIONS

2005, 2008, 2010

CODE

vstipTool0111

The Properties window allows you to view and change the design-time properties and events of selected objects that are located in editors and designers. You can also use the Properties window to edit and view file, project, and solution properties. The Properties window is available from the View menu.

For more information, see “Properties Window” on MSDN at http://msdn.microsoft.com/en-us/library/ms171352.aspx.

Working with the Tool Window
The following table lists the keyboard shortcuts that you can use with the Properties window:

ACTION

SHORTCUT

Open / Show

F4 or Alt+Enter

Close

Shift+Esc

Working with Categories

The following table lists the keyboard shortcuts that you can use when working with the categories in the Properties window:

NOTE
The category needs to be selected as shown in the preceding illustration, using the Misc category. You can use your Arrow keys to select the node.

ACTION

SHORTCUT

Collapse

Left Arrow or - (minus)

Expand

Right Arrow or + (plus)

Show next set of properties

Page Up

Show previous set of properties

Page Down

Move to next item in list

Down or Left Arrow

Move to previous item in list

Up or Right Arrow

Move to first property

Home

Move to last property

End

Property Items

The following table lists the keyboard shortcuts that you can use when you are working with individual items in the Properties window:

ACTION

SHORTCUT

Cancel current changes

Esc

Show drop-down list

Alt+Down Arrow

Previous/next option in list

Up / Down Arrow

Cut selection

Ctrl+X

Copy selection

Ctrl+C

Paste

Ctrl+V

Undo

Ctrl+Z





06.38 Properties Window Keyboard Shortcuts
06.39 Document Outline: Web Projects
06.40 Inserting Code Snippets
16h 24m remaining
06.39 Document Outline: Web Projects
DEFAULT

Ctrl+Alt+T

VISUAL BASIC 6

Ctrl+Alt+T

VISUAL C# 2005

Ctrl+Alt+T; Ctrl+W, Ctrl+U; Ctrl+W, U

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+Alt+D

VISUAL STUDIO 6

Ctrl+Alt+T

WINDOWS

Alt,V, E, D

MENU

View | Other Windows | Document Outline

COMMAND

View.DocumentOutline

VERSIONS

2005, 2008, 2010

LANGUAGES

C#, VB

CODE

vstipTool0116

If you are working with web projects, you need to know about the Document Outline feature (Ctrl+Alt+T). It can be used to do the following:

View the logical structure of your document.

Determine which elements are HTML elements and which ones are web server controls.

Navigate to specific elements, in Design view and in Source view.

If you are working in Source view, it shows you the body element and the child elements of the head element, the page directive, and any script elements and code elements.

I created a default web application in Visual Studio 2010, added a couple of server controls, and switched to Source view. The following illustration shows what the Document Outline looks like.


Notice that you can clearly distinguish between the HTML and server content (server content has the little gears in them). It can also be used to select items in the Source.


In Design view, it essentially does the same thing and allows you to get a bird’s-eye view of the layout and can be used to select controls.


If you have a scenario with many controls, this makes getting to specific items very easy.


Additionally, many people like to use this feature with Split view so that it can show both Design and Source.





06.39 Document Outline: Web Projects
06.40 Inserting Code Snippets
06.41 Surround with a Code Snippet
16h 24m remaining
06.40 Inserting Code Snippets
DEFAULT

Ctrl+K, Ctrl+X

VISUAL BASIC 6

Ctrl+K, Ctrl+X

VISUAL C# 2005

Ctrl+K, Ctrl+X; Ctrl+K, X

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+K, Ctrl+X

VISUAL STUDIO 6

Ctrl+K, Ctrl+X

WINDOWS

Alt,E, I, I

MENU

Edit | IntelliSense | Insert Snippet

COMMAND

Edit.InsertSnippet

VERSIONS

2005, 2008, 2010

LANGUAGES

C#, VB

CODE

vstipEdit0051

Even though these have been around for a while, a lot of people still don’t fully understand snippets. Let’s assume you are in the editor and you want to create an if statement. You can type it out, but that would be the hard way. Why not just use a snippet? You have several ways to do this.

Tab
Just type if, and press the Tab key twice.

C#
The paper-like icon, shown in the following illustration, indicates that this is a snippet in C#.


VB
In VB, you don’t have the paper icon, but you do have a note in the tooltip that indicates this is a snippet.

WARNING
Don’t be fooled by the #if directive. You want the if statement for this example.


Keyboard Shortcut and Context Menu
Press Ctrl+K, Ctrl+X or right-click and choose Insert Snippet, or go to Edit | IntelliSense | Insert Snippet on the menu bar.

C#
First you see a prompt to insert the snippet, as shown in the following illustration.


Choose Visual C# from the list, and then press Enter.


Then type if, and press Enter.


VB
Similar to C#, you see a prompt to insert the snippet, but the path is different. From the list, choose Code Patterns – If, For Each, Try Catch, Property, Etc, and then press Enter:


Then choose Conditionals And Loops, and press Enter:


Finally, pick the if statement you want from the list:


Result
No matter which option you choose, the result is essentially the same. You can now type in your condition and the rest of your logic.





06.40 Inserting Code Snippets
06.41 Surround with a Code Snippet
06.42 Using Code Snippets
16h 24m remaining
06.41 Surround with a Code Snippet
DEFAULT

Ctrl+K, Ctrl+S

VISUAL BASIC 6

Ctrl+K, Ctrl+S

VISUAL C# 2005

Ctrl+K, Ctrl+S; Ctrl+K, S

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+K, Ctrl+S

VISUAL STUDIO 6

Ctrl+K, Ctrl+S

WINDOWS

Alt,E, I, S

MENU

Edit | IntelliSense | Surround With

COMMAND

Edit.SurroundWith

VERSIONS

2005, 2008, 2010

LANGUAGES

C#

CODE

vstipEdit0052

This is one that even people who know about snippets tend to forget. You can actually put a snippet around existing code, assuming you have some code selected.

Just press Ctrl+K, Ctrl+S:


Then type the statement you want to surround the code with. In this case, let’s use an if statement:


Press your Tab key once, and you see the result shown in the following illustration.


Now you can put in your condition and any additional logic you want.





06.41 Surround with a Code Snippet
06.42 Using Code Snippets
06.43 HTML Code Snippets
16h 24m remaining
06.42 Using Code Snippets
DEFAULT

Ctrl+K, Ctrl+X

VISUAL BASIC 6

Ctrl+K, Ctrl+X

VISUAL C# 2005

Ctrl+K, Ctrl+X; Ctrl+K, X

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+K, Ctrl+X

VISUAL STUDIO 6

Ctrl+K, Ctrl+X

WINDOWS

Alt,E, I, I

MENU

Edit | IntelliSense | Insert Snippet

COMMAND

Edit.InsertSnippet

VERSIONS

2005, 2008, 2010

LANGUAGES

C#, VB

CODE

vstipEdit0053

I thought it would be a good idea to review how to use snippets. This example uses tags in ASP.NET, but the concepts apply across the board to all snippets.

Let’s say you are in an ASP.NET application and you start to type an anchor tag, as shown in the following illustration.


You press Tab twice to insert a snippet and see the following result:


Snippets have special areas that you can change the values in by pressing Tab to cycle through them. For example, the following snippet has two special areas. Let’s put in a URL:


Now press Tab to go to the next area, and type in some text as shown in the following illustration.


You can keep pressing Tab to toggle between these two locations as much as you want. When you are done, you can press Enter to put the cursor at the end of the element and continue typing more code.

So, in a nutshell, that’s how to work with snippets. They take a little getting used to, but they are great timesavers.





06.42 Using Code Snippets
06.43 HTML Code Snippets
06.44 JavaScript Code Snippets
16h 24m remaining
06.43 HTML Code Snippets
DEFAULT

Ctrl+K, Ctrl+X

VISUAL BASIC 6

Ctrl+K, Ctrl+X

VISUAL C# 2005

Ctrl+K, Ctrl+X; Ctrl+K, X

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+K, Ctrl+X

VISUAL STUDIO 6

Ctrl+K, Ctrl+X

WINDOWS

Alt,E, I, I

MENU

Edit | IntelliSense | Insert Snippet

COMMAND

Edit.InsertSnippet

VERSIONS

2010

CODE

vstipEdit0018

You might have used code snippets for a while now, but did you know that Visual Studio 2010 has added support for HTML snippets?

From any webpage, go to Edit | IntelliSense | Insert Snippet on the menu bar (Ctrl+K, Ctrl+X). You should see the Insert Snippet prompt:


Next, choose your category and the specific snippet you want:


Type in the details, pressing Tab if there are multiple areas where you need to put in details.


Press Enter when you are done, and continue putting in your code.

NOTE
This is the long way to insert a snippet the quicker way, in most cases, is to just start typing an element and hit tab twice to insert the snippet for that element.





06.43 HTML Code Snippets
06.44 JavaScript Code Snippets
06.45 Using the Code Snippets Manager
16h 24m remaining
06.44 JavaScript Code Snippets
DEFAULT

Ctrl+K, Ctrl+B

VISUAL BASIC 6

Ctrl+K, Ctrl+B

VISUAL C# 2005

Ctrl+K, Ctrl+B

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+K, Ctrl+B

VISUAL STUDIO 6

Ctrl+K, Ctrl+B

WINDOWS

Alt,E, I, I

MENU

Edit | IntelliSense | Insert Snippet

COMMAND

Edit.InsertSnippet

VERSIONS

2010

CODE

vstipEdit19

Want to get that JavaScript code created more quickly? Use JavaScript snippets.

When you are inside any script block, go to Edit | IntelliSense | Insert Snippet on the menu bar (Ctrl+K, Ctrl+X), choose the JScript category, as shown in the following illustration, and then press Tab.


Now pick what you want to do, and then press Tab again.


Now fill in any details, pressing Tab to cycle between details if needed.


Then press Enter when you are done, and keep typing your code.





06.44 JavaScript Code Snippets
06.45 Using the Code Snippets Manager
06.46 Insert Quotes When Typing Attribute Values
16h 24m remaining
06.45 Using the Code Snippets Manager
DEFAULT

Ctrl+K, Ctrl+B

VISUAL C++ 2

[no shortcut]

WINDOWS

Alt,T, T

MENU

Tools | Code Snippets Manager

COMMAND

Tools.CodeSnippetsManager

VERSIONS

2005, 2008, 2010

CODE

vstipTool0015

Ever wonder where you can get a list of code snippets just to browse? The Code Snippets Manager is your friend. Start by pressing Ctrl+K, Ctrl+B to see the following dialog box.


The first thing you need to do is pick the language you want to browse through. Go ahead and choose Visual Basic for this example. This action gives you several folders (categories) to choose from. Let’s choose the Application – Compiling, Resources, And Settings folder, as shown in the following illustration.


From here, you can browse individual snippets and put your mouse over each of them to get the full description:


Click the Change The Foreground And Background Colors In A Console Window snippet. Notice that summary information about the snippet is provided:


To use this snippet, you have to copy the shortcut name, “appChanCol” in this case. Now click OK or Cancel to close the dialog box, and paste your shortcut name into the editor.


Finally, press Tab twice to get the results shown in the following illustration.

NOTE
Technically, you have to press Tab only once in this case, but pressing it twice preserves muscle memory for the snippets and has no downside.


But what about the buttons in the Code Snippet Manager we didn’t talk about?


Following are quick descriptions of what they do.

Add—Lets you pick a folder to add to the current list of folders for snippets. The folder can be any accessible location, including network drives. This is useful for shared snippets among team members where everyone uses snippets on a shared drive.

Remove—Takes a folder out of the list but does not physically delete the folder.

Import—Used for including individual .snippet files in the folder you are currently viewing.





06.45 Using the Code Snippets Manager
06.46 Insert Quotes When Typing Attribute Values
06.47 Format the Current Document or Selection (Web)
16h 24m remaining
06.46 Insert Quotes When Typing Attribute Values
WINDOWS

Alt,T, O

MENU

Tools | Options

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0082

One of the more annoying things about web development in Visual Studio is that when you type in attributes it doesn’t include the quotes automatically.


You can have quotes included automatically when you type in attributes if you go to Tools | Options | Text Editor | HTML | Formatting and select Insert Attribute Value Quotes When Typing:


From now on, you will see the quotes when you type in the attributes:






06.46 Insert Quotes When Typing Attribute Values
06.47 Format the Current Document or Selection (Web)
06.48 Using the Navigation Bar
16h 24m remaining
06.47 Format the Current Document or Selection (Web)
DEFAULT

Ctrl+K, Ctrl+D (document); Ctrl+K, Ctrl+F (selection)

VISUAL BASIC 6

Ctrl+K, Ctrl+D (document); Ctrl+K, Ctrl+F (selection)

VISUAL C# 2005

Ctrl+K, Ctrl+D (document); Ctrl+K, Ctrl+E (document); Ctrl+K, E (document); Ctrl+K, Ctrl+F (selection); Ctrl+E, Ctrl+F (selection); Ctrl+E, F (selection)

VISUAL C++ 2

[no shortcut] (document); Ctrl+Shift+F (selection); Ctrl+Alt+I (selection)

VISUAL C++ 6

Ctrl+K, Ctrl+D (document); Ctrl+K, Ctrl+F (selection); Alt+F8 (selection)

VISUAL STUDIO 6

Ctrl+K, Ctrl+D (document); Ctrl+K, Ctrl+F (selection); Alt+F8 (selection)

WINDOWS

Alt,E, V, A (document); Alt,E, V, F (selection)

MENU

Edit | Advanced | Format Document; Edit | Advanced | Format Selection

COMMAND

Edit.FormatDocument; Edit.FormatSelection

VERSIONS

2008, 2010

CODE

vstipEdit0089

In vstipEdit0057 (AX.63 Format the Current Document or Selection, in Appendix B [http://go.microsoft.com/FWLink/?Linkid=223758]), I showed you how to format code. I thought it would be a good idea to look at the same task from a web project perspective. Let’s say you have the following HTML:


WARNING
You need to have spaces around the <DIV> tags, as I have shown here, or the formatting will not work correctly.

But you want to clean it up a bit. Just select everything you want formatted, right-click, and choose Format Selection (Ctrl+K, Ctrl+F), as shown in the following illustration.


You see the following result:


The formatting rules that govern this operation can be found at Tools | Options | Text Editor | HTML | Formatting. You can also format the entire document by going to Edit | Advanced | Format Document or using the shortcut Ctrl+K, Ctrl+D.





06.47 Format the Current Document or Selection (Web)
06.48 Using the Navigation Bar
06.49 HTML Editor Tag Navigation
16h 24m remaining
06.48 Using the Navigation Bar
DEFAULT

Ctrl+F2 (navigation bar);

Tab (move between Objects and Members drop-down lists)

VISUAL BASIC 6

Ctrl+F2 (navigation bar);

Tab (move between Objects and Members drop-down lists)

VISUAL C# 2005

Ctrl+F2 (navigation bar);

Tab (move between Objects and Members drop-down lists)

VISUAL C++ 2

Ctrl+F2 (navigation bar);

Tab (move between Objects and Members drop-down lists)

VISUAL C++ 6

Ctrl+F8 (navigation bar);Tab (move between Objects and Members drop-down lists)

VISUAL STUDIO 6

Ctrl+F2 (navigation bar);

Tab (move between Objects and Members drop-down lists)

WINDOWS

[no shortcut]

COMMAND

Window.MovetoNavigationBar

VERSIONS

2005, 2008, 2010

CODE

vstipTool0026

Ever notice the two drop-down lists just below the file tab channel? The one on the left is the Objects list (classes and objects), and the one on the right is the Members list.


You probably don’t have much use for the Objects list unless you have a lot of classes in one file. The Members list is extremely useful when you want to jump around in your code. If you have a class with several functions, you can click the Members list to see them all:


Now you can just click a member to instantly go to that section in your code.





06.48 Using the Navigation Bar
06.49 HTML Editor Tag Navigation
06.50 Format HTML on Paste
16h 24m remaining
06.49 HTML Editor Tag Navigation
VERSIONS

2005, 2008, 2010

CODE

vstipEdit0091

According to the documentation, “the tag navigator is a representation of the element that is currently selected in the document, along with the hierarchy of parent tags to which it belongs.”

For more detailed information, see the topic “HTML Editor Tag Navigation in Visual Web Developer” at http://msdn.microsoft.com/en-us/library/b53y76zk.aspx.

The tag navigator is particularly useful for working with deeply nested structures such as tables within tables. You can use the tag navigator to determine which element in the document has the focus.


In addition, you can use the tag navigator to move from the current element to an element that is located higher in the current hierarchy:


NOTE
The tag navigator does not display all of the elements in the current document. Instead, it shows the path from the current element to the outermost parent. For information about how to see all of the elements in the document, see vstipTool0116 (06.39 Document Outline: Web Projects, page 251).





06.49 HTML Editor Tag Navigation
06.50 Format HTML on Paste
06.51 Display HTML/CSS Warnings as Errors
16h 24m remaining
06.50 Format HTML on Paste
WINDOWS

Alt,T, O

MENU

Tools | Options Text Editor | HTML | Miscellaneous

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0092

If you find yourself copying and pasting unformatted HTML a lot, this tip is for you. Just go to Tools | Options | Text Editor | HTML | Miscellaneous, and select Format HTML On Paste.


From now on, when you paste it, your HTML is formatted according to the rules set up in Tools | Options | Text Editor | HTML | Formatting.





06.50 Format HTML on Paste
06.51 Display HTML/CSS Warnings as Errors
06.52 Updating JScript IntelliSense
16h 24m remaining
06.51 Display HTML/CSS Warnings as Errors
WINDOWS

Alt,T, O

MENU

Tools | Options Text Editor | HTML | Validation

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0084

Normally, HTML and CSS syntax problems show up as warnings (green squiggles):


These syntax problems also show up as warnings in the Error List window:


This means that you can build and run the application if you choose to ignore the warnings. Or you can have them show up as errors instead, by going to Tools | Options | Text Editor | HTML | Validation and clearing the As Warnings check box.


Now the green squiggles will be red:


The previous warnings now show up as errors in the Error List window and you are notified when you try to build that a problem exists.





06.51 Display HTML/CSS Warnings as Errors
06.52 Updating JScript IntelliSense
06.53 Using JScript Libraries in Other JScript Files
16h 24m remaining
06.52 Updating JScript IntelliSense
DEFAULT

Ctrl+Shift+J

WINDOWS

Alt,E, I, J

MENU

Edit | IntelliSense | Update JScript IntelliSense

COMMAND

Edit.UpdateJScriptIntellisense

VERSIONS

2008, 2010

CODE

vstipEdit0086

If you find that your IntelliSense isn’t showing for JScript items you recently put in, you can update the JScript IntelliSense by going to Edit | IntelliSense | Update JScript IntelliSense or pressing Ctrl+Shift+J.


It goes by quickly, but you might see the 06.52 Updating JScript IntelliSense message in the Status Bar at the lower-left corner of your screen.

When it is done, you should be able to see the newly added items.





06.52 Updating JScript IntelliSense
06.53 Using JScript Libraries in Other JScript Files
06.54 Create New Code Snippets from Existing Ones
16h 24m remaining
06.53 Using JScript Libraries in Other JScript Files
VERSIONS

2008, 2010

CODE

vstipProj0025

When you want to use your own custom JScript library, it’s a very straightforward process. You just click and drag the file from Solution Explorer into your web page.


Then start using the library:


But what if you want to use the library in another JScript file? No problem. To have one file used by another, just click and drag the file name from the resource file into the consuming file.

When you do, it makes a reference automatically:


And you can start using it right away with IntelliSense now aware of the resource contents:






06.53 Using JScript Libraries in Other JScript Files
06.54 Create New Code Snippets from Existing Ones
06.55 Understanding the Navigation Stack
16h 24m remaining
06.54 Create New Code Snippets from Existing Ones
DEFAULT

Ctrl+K, Ctrl+B

VISUAL BASIC 6

Ctrl+K, Ctrl+B

VISUAL C# 2005

Ctrl+K, Ctrl+B

VISUAL C++ 2

[no shortcut]

VISUAL C++ 6

Ctrl+K, Ctrl+B

VISUAL STUDIO 6

Ctrl+K, Ctrl+B

WINDOWS

Alt,T, T

MENU

Tools | Code Snippets Manager

COMMAND

Tools.CodeSnippetsManager

VERSIONS

2005, 2008, 2010

CODE

vstipTool0016

When you use snippets, you often need to change the default values. Naturally, you can modify the values after the snippet is used. But what if you want to permanently change the value and make a new snippet out of it?

First, figure out which snippet you want to modify by finding it in the Code Snippets Manager (see vstipTool0015, 06.45 Using the Code Snippets Manager, in Appendix B [http://go.microsoft.com/FWLink/?Linkid=223758]). In this case, let’s modify the If..End If snippet for Visual Basic.


What you are after is the location of the snippet. See the path under Location in the following illustration. Select the path in the dialog box and Copy it (Ctrl+C).


Now, go to File | Open | File, paste in the file path, and click Open.


This next part is really just to make sure we don’t modify the original snippet. As you gain more experience doing modifications, you might choose to change the original, but for now, you want to make sure you can keep your existing set of snippets intact. Go to File | Save IfEndifStatement.snippet As:


Now just save the file with the original file name and your initials appended to the end.


You are ready to modify the snippet. Start with the header information:


For now, just change the Title and Shortcut to include your initials:



NOTE
The key here is the shortcut name. It is the name you will use most often to invoke this snippet so make it something that makes sense.

Because you are here to change the default value as well, locate the Default tag:


Change “True” to “False,” and then save the file and close it.

You are ready to use your new snippet. Go into your code, type in your new snippet shortcut, and press Tab (once or twice, both work the same).


And you get the following result:


You now have a new snippet you can use. You can verify this by going back into the Code Snippets Manager (Ctrl+K, Ctrl+B) and finding your snippet in the list.





06.54 Create New Code Snippets from Existing Ones
06.55 Understanding the Navigation Stack
06.56 Navigate Backward and Navigate Forward Using Go Back Markers
16h 24m remaining
06.55 Understanding the Navigation Stack
DEFAULT

Ctrl+Shift+8 (back); Ctrl+Shift+7 (forward)

VISUAL BASIC 6

[no shortcut] (back); Ctrl+Shift+7 (forward)

VISUAL C# 2005

Ctrl+Shift+8 (back); Ctrl+Shift+7 (forward)

VISUAL C++ 2

Ctrl+Shift+8 (back); Ctrl+Num * (back); Ctrl+Shift+7 (forward)

VISUAL C++ 6

Ctrl+Num * (back); Ctrl+Shift+7 (forward)

VISUAL STUDIO 6

Ctrl+Shift+8 (back); Ctrl+Shift+7 (forward)

WINDOWS

[no shortcut]

COMMAND

View.PopBrowseContext; View.ForwardBrowseContext

VERSIONS

2005, 2008, 2010

LANGUAGES

C++, C#

CODE

vstipEdit0078

Did you know that a dedicated stack is available to you, just for going to definitions? Let’s look at a couple of examples.

Suppose you are looking at a method call, as shown in the following illustration.


You can press F12 to go to its definition:


How do you go back? Just press Ctrl+Shift+8, and it takes you back:


Pressing Ctrl+Shift+7 moves you to the definition again.


So what’s going on? Well, every time you go to a definition it keeps track of where you come from. This works every time you go to definition so that you can always find your way back. The following illustrations show another example.


Press F12 (go to definition):


From here, you could press Ctrl+Shift+8 to go back. But what if you want to keep digging into definitions? In this example, let’s say you’ve clicked in the GetNumber method:


Now press F12:


Now, if you want to go back, press Ctrl+Shift+8:


Then press Ctrl+Shift+8 again:






06.55 Understanding the Navigation Stack
06.56 Navigate Backward and Navigate Forward Using Go Back Markers
06.57 Select from the Current Cursor Location to the Last Go Back Marker
16h 24m remaining
06.56 Navigate Backward and Navigate Forward Using Go Back Markers
DEFAULT

Ctrl+- (back); Ctrl+Shift+- (forward)

VISUAL BASIC 6

Ctrl+- (back); Ctrl+Shift+F2 (back); Ctrl+Shift+- (forward)

VISUAL C# 2005

Ctrl+- (back); Ctrl+Shift+- (forward)

VISUAL C++ 2

Ctrl+- (back); Ctrl+Shift+- (forward)

VISUAL C++ 6

Ctrl+- (back); Ctrl+Shift+- (forward)

VISUAL STUDIO 6

Ctrl+- (back); Ctrl+Shift+- (forward)

WINDOWS

Alt,V, B (back); Alt,V, F (forward)

MENU

View | Navigate Backward; View | Navigate Forward

COMMAND

View.NavigateBackward; View.NavigateForward

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0024

If you move in a single command more than several lines away from where you are currently working or if you edit in a particular location that is not adjacent to the last place you edited, the editor remembers locations. It does this by creating Go Back markers based on specific conditions. The goal is to remember interesting locations so that you can recall where you have been working without remembering so many locations that the feature is not useful (such as every character typed, or every line entering several new lines of code one right after the other).

A Go Back marker is dropped under the following conditions:

An incremental search (including reverse) leaves a Go Back marker at the beginning of the search and another one at the end.

A Go To Line action, like Ctrl+G, or a mouse-click that moves the cursor 11 lines or more from the current position drops a Go Back marker at the new location.

A destructive action (like pressing backspace) after having moved the cursor to a new location drops a Go Back marker.

Doing a search, like Ctrl+F, drops a Go Back marker at the found location.

Opening a file drops a Go Back marker wherever the cursor was on the old file and drops another on the opened file.

That now brings us to the navigation buttons on the Standard Toolbar (and keyboard shortcuts, too). These gems make travelling around your code much, much easier:


You can use the buttons to quickly navigate among the Go Back markers that have been dropped throughout Visual Studio. To quickly look at the list of places you can go, just click the drop-down arrow for the back button.

NOTE
The navigation buttons in the Standard Toolbar are on the upper-left of the image below.






06.56 Navigate Backward and Navigate Forward Using Go Back Markers
06.57 Select from the Current Cursor Location to the Last Go Back Marker
06.58 Track Changes in the Editor
16h 24m remaining
06.57 Select from the Current Cursor Location to the Last Go Back Marker
DEFAULT

Ctrl+=

VISUAL BASIC 6

Ctrl+=

VISUAL C# 2005

Ctrl+=

VISUAL C++ 2

Ctrl+=

VISUAL C++ 6

Ctrl+=

VISUAL STUDIO 6

Ctrl+=

WINDOWS

[no shortcut]

COMMAND

Edit.SelectToLastGoBack

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0069

In vstipEdit0024 (06.56 Navigate Backward and Navigate Forward Using Go Back Markers, on page 277), we defined Go Back markers. In this tip, we look at how they can be useful for selecting text. Let’s say you are writing some code and want to quickly select a chunk of text. In the following illustration, the cursor is at your starting location (line 15).


You click on a new location (line 27), which results in a Go Back marker (which you can’t see) being placed at the starting location (line 15).


Now we have the Go Back marker at the beginning of line 15 and the current cursor location at the end of line 27. In this case, you had to jump at least 11 lines to get your Go Back marker. To select from the current cursor location to the last Go Back marker, just press Ctrl+= and watch the magic happen.






06.57 Select from the Current Cursor Location to the Last Go Back Marker
06.58 Track Changes in the Editor
06.59 Edit Read-Only Files
16h 24m remaining
06.58 Track Changes in the Editor
WINDOWS

Alt,T, O

MENU

Tools | Options | Text Editor | General

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0048

To use this feature, you need to go to Tools | Options | Text Editor | General and have Track Changes and Selection Margin checked.

Ever wonder how the colored lines to the left of your code (by the line numbers) actually work?

Let’s begin with a clean slate.


Let’s add a couple of lines of code, and now we see two vertical yellow (you’ll have to trust me on the colors) lines to the left of lines 14 and 15:


All new code will have a yellow line to show you what part of the document is unsaved. If we save the code, the yellow lines turn green to indicate code that has been saved.

The saved indicator remains as long as you have the file open. When you close and reopen the file, the line goes away:


In Visual Studio 2010, an orange indicator shows a change that is different from the saved version. This was added for the scenario where a user does an undo after saving the changes.

You can use the following grid to help keep the colors straight.

MARKER

DIFFERENT FROM FILE SAVED ON DISK?

DIFFERENT FROM FILE THAT WAS OPENED?

Nothing

No

No

Yellow

Yes

Yes

Green

No

Yes

Orange

Yes

No





06.58 Track Changes in the Editor
06.59 Edit Read-Only Files
06.60 Choosing CSS Versions
16h 24m remaining
06.59 Edit Read-Only Files
WINDOWS

Alt,T, O

MENU

Tools | Options | Environment | Documents

COMMAND

Tools.Options

VERSIONS

2008, 2010

CODE

vstipEdit0074

When you open a read-only document, you get an indicator that looks like a tiny lock on the file tab:


If you make changes and try to save them, you are (by default) met with the Save Of Read-Only File dialog box.


At this point, you can save your changes as another copy of the file, overwrite the existing file, or cancel. If you don’t like these options, you can turn this feature off by going to Tools | Options | Environment | Documents and clear the Allow Editing Of Read-Only Files; Warn When Attempt To Save check box.


Now if you attempt to make any changes to a read-only file, you see the Edit of Read-Only File dialog box.


Edit In-Memory
Allows you to make edits and then display the Save Of Read-Only File dialog box when you save changes.

Make Writable
If possible, turns off the read-only attribute of the file so that it can be edited.





06.59 Edit Read-Only Files
06.60 Choosing CSS Versions
06.61 Understanding Tag Specific Options
16h 24m remaining
06.60 Choosing CSS Versions
WINDOWS

Alt,T, O

MENU

Tools | Options Text Editor | HTML | Validation (HTML Schema)

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010, 2010 SP1

CODE

vstipEdit0093

When working with Cascading Style Sheets (CSS), you often find yourself working with specific versions. In this tip, we look at how to set your CSS version for dedicated and embedded styles.

NOTE
Visual Studio 2010 Service Pack 1 added limited support for HTML5 and CSS3. For more information, see http://blogs.msdn.com/b/zainnab/archive/2011/04/12/vs2010-sp1-new-features-html-5-and-css-3-support.aspx.

Dedicated Style Sheets
When you create a CSS file in Visual Studio, you can choose the version you want by selecting it from the Cascading Style Sheet Version For Validation drop-down list on the Style Sheet Toolbar:


NOTE
CSS3 doesn’t show up in this list even after you install Visual Studio 2010 Service Pack 1.

Embedded Styles
It is recommended that you use dedicated style sheets; however, you might find that you want to embed styles in your HTML source.

When you do this, it might not be clear how you select the CSS version. Most people think it is the same as the version chosen for dedicated CSS files. This is not the case. It’s bound to the choice you make in the Target Schema For Validation drop-down list located on the HTML Source Editing Toolbar or at Tools | Options | Text Editor | HTML | Validation (HTML Schema).


The following table shows how the CSS version relates to the choices.

HTML SCHEMA

CSS SCHEMA

Internet Explorer 6.0

Internet Explorer 6.0

HTML 4.01

CSS 1.0

XHTML 1.0 Transitional

CSS 2.0

XHTML 1.0 Frameset

CSS 2.0

XHTML 1.1

CSS 2.1

HTML5 (limited)

CSS 3.0 (limited)

XHTML5 (limited)

CSS 3.0 (limited)

Finally
You have many good reasons to use dedicated style sheets, but if you do find yourself doing embedded CSS, make sure you understand which schema you are using based on your HTML schema choices.





06.60 Choosing CSS Versions
06.61 Understanding Tag Specific Options
7. Debugging
16h 24m remaining
06.61 Understanding Tag Specific Options
WINDOWS

Alt,T, O

MENU

Tools | Options | Text Editor | HTML | Formatting

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipEdit0090

In vstipEdit0089 (06.47 Format the Current Document or Selection (Web), on page 265), I showed you how to use selection formatting on a sample.

Let’s say you don’t like the way <DIV> tags are formatted. You can go to Tools | Options | Text Editor | HTML | Formatting and click the Tag Specific Options button.

Exploring the Tag Specific Options Dialog Box
This dialog box is somewhat complicated, so let’s go though it one area at a time. For reference, the following illustration provides a bird’s eye view to help us stay oriented as we go along.


Tree view

Allows you to select either the individual tag to format or a class of tags. By default, the tree contains the following nodes:

Default Settings
Expand this node to set default formatting options for a complete class of tags, such as all server tags that support contents.

Client HTML Tags
Expand this node to set custom formatting options for HTML elements.

ASP.NET Controls
Expand this node to set custom formatting options for ASP.NET server controls.

New Tag
Use to define new tags that aren’t already listed.

New Folder
Create a new node on the tree for organizing custom tags.

Delete
Delete a tag or folder.

NOTE
In the following examples, our working reference is the <DIV> tag from the Client HTML Tags section of the Tag Specific Actions dialog box.

Per tag formatting

Per tag formatting works on a model with default settings for each tag. These settings provide the base rules by which the tag is formatted. The four categories of tags are as follows:

Client tags that do not support contents, such as <BR />

Client tags that support contents, such as <TABLE> or <H1>

Server tags that do not support contents, such as asp:CheckBox

Server tags that support contents, such as asp:Repeater

For each tag, the values from the appropriate category in the preceding list are used, unless an override is specified for that tag. By default, some overrides are supplied based on the common usage of the tags.

Closing tag
Indicates how the closing tag should look when automatically created.


Line breaks
Directs the formatting to place line breaks as specific points in the entire element.


Indent contents
Indents the contents for the element, if appropriate.

Preview

The absolute best way to see how the per-tag formatting is going to look is to use the Preview area (bottom of the dialog box). It updates based on your choices so that you can make informed decisions on the formatting. Unfortunately it does not show color choices (described later).

Outlining in code editor

Enable outlining for tag
When outlining is enabled, the editor monitors the number of lines in the element and then applies outlining to the tag when the element exceeds the specified line threshold. (The editor does not automatically collapse the tag.) This feature is useful for collapsing long elements, such as large tables.

NOTE
If outlining doesn’t show up as expected try closing and re-opening the file to make it appear.

Minimum lines
Number of lines before outlining is enabled for the element.

Example: The <DIV> has outlining enabled and minimum lines set to three. For three lines or more in an element, outlining, the minus sign to the left of the opening tag, is enabled for that element:


Notice the outlining (the minus sign to the left of the opening <DIV> tag, shown in the preceding illustration) that has kicked in because we have the minimum number of lines. In this example, if the minimum lines are changed to five, outlining is not enabled and no minus sign appears:


Per tag colorization

Tag foreground
The color of the text for the tags.

Tag background
The color of the text background.

Bold
Makes the tags bold.

Finally
You can see that there is much to learn about tag-specific options. Take your time as you explore the possibilities in the Tag Specific Options dialog box.





06.61 Understanding Tag Specific Options
