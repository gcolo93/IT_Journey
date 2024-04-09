
II. Extensions for Visual Studio
8. Visual Studio Extensions
16h 24m remaining
Part II. Extensions for Visual Studio
In this part:

Chapter 8





II. Extensions for Visual Studio
8. Visual Studio Extensions
Introducing Visual Studio Extensions
16h 24m remaining
Chapter 8. Visual Studio Extensions
The new code editor is one of the most impressive improvements of the Visual Studio 2010 Integrated Development Environment (IDE). Built on top of Windows Presentation Foundation (WPF) and the Managed Extensibility Framework, the combination of user interface–rich flexibility plus plug-in extensibility takes innovation within Visual Studio to the next level.





8. Visual Studio Extensions
Introducing Visual Studio Extensions
08.01 Create Themes Using All Visual Studio Elements
16h 24m remaining
Introducing Visual Studio Extensions
Introducing Visual Studio Extensions
In addition to the editor, the Visual Studio 2010 IDE introduces a new WPF-based shell. Many core user interface features are now WPF-based, including menus, window layouts, toolbars, start page, and so forth.

Even if you’ve never developed any applications for use within Visual Studio, it is important to know that the SDK tooling has significantly improved, paving the way for a much richer Visual Studio ecosystem.

Gone are the days of requesting a package load key or a shell load key to develop Visual Studio applications. No more having to make modifications to the registry to install a Visual Studio plug-in.

The goals of this chapter are twofold: to provide a basic overview on how to find and install extensions and to catalogue the “must-have” extensions available for free for the Visual Studio 2010 IDE.

Welcome to the new world of Visual Studio extensions.

Installing an Extension
The development experience has greatly improved for Visual Studio 2010, providing additional ways for installing extensions. The preferred and most straightforward way to install an extension is through a new Visual Studio 2010 feature called the Extension Manager. Located within the IDE, the Extension Manager searches an online gallery, called the Visual Studio Gallery, for extensions. The Extension Manager also manages the installed and currently in-use extensions.

Installing from the Extension Manager
To open the Extension Manager from within Visual Studio, go to Tools | Extension Manager. To search for an extension online, select Online Gallery in the left navigation pane. Type in the name of the extension to search for within the Search Online Gallery text box. For example, you can search for “Color Theme Editor” to find the Visual Studio Color Theme Editor extension.

When the desired extension is found, click the Download button to install. When the install has completed, a message appears at the bottom of the Extension Manager dialog box, as shown in the following illustration.


A Visual Studio restart is required for all extensions, except for templates. Click Restart Now to restart Visual Studio and enable the extension.

Installing from the Visual Studio Gallery
Another addition to Visual Studio 2010 is the Visual Studio Gallery, a website that provides a catalog of free and commercial extensions for Visual Studio. Naturally, developers writing extensions have the option of hosting the extension on their own websites, but hosting in the Visual Studio Gallery greatly increases discoverability of the extension. Additionally, you can find a significant number of tools for all past Visual Studio IDE versions from 2002 onward in the Visual Studio Gallery.

The Visual Studio Gallery is located at www.visualstudiogallery.com. To browse for extensions built for Visual Studio 2010, click Browse and then select Visual Studio 2010 under Visual Studio Versions in the left navigation bar.

When the desired extension is found, click the Download image link to begin the download and installation.


You can either open the .vsix file to begin the installation or save the file to install at a later time. If you chose to save the file, you can double-click the .vsix file at any time to start the installation. Otherwise, simply click Open to begin installing the extension. The Visual Studio Extension Manager prompts you to accept a license if one was provided with the extension.

A restart is required to finish installing the extension. The Extension Manager shows a “restart required” message at the bottom of the dialog box. A Visual Studio restart is required for all extensions, except for templates. Click Restart Now to restart Visual Studio and enable the extension.

Installing Through Xcopy
Because the SDK tooling has been greatly simplified, such that registry modifications are no longer necessary, it is possible to install an extension simply by copying the extension file into a specific Visual Studio folder. This method of installation through copying files is known as Xcopy deployment.

All installed extensions can be found in an unzipped format at the following location:

%LocalAppData%\Microsoft\VisualStudio\10.0\Extensions\<Company>\<Product>\<Version>
Extensions installed through the Xcopy method are disabled by default within Visual Studio. You must manually enable the extension, as described next.

To install an extension through this method, you must do the following:

Unzip the .vsix file.

Copy the .vsix raw folder into the Extensions folder.

Start Visual Studio, and enable the extension in the Extension Manager.

Conversely, you can uninstall any extension simply by deleting its corresponding folder from the %LocalAppData%\Microsoft\VisualStudio\10.0\Extensions directory.

Inside a .vsix File
Although creating extensions is beyond the scope of this book, it’s important to be aware how content written by members of the community is installed and run on your computer, especially in the case where you need to troubleshoot a faulty extension.

All Visual Studio extensions use the .vsix file extension. A .vsix file is a .zip file (with its file extension renamed to .vsix) that uses the Open Packaging Convention to package the code and manifest for the extension. You can read more about the contents of a .vsix file on Quan To’s blog at http://blogs.msdn.com/b/quanto/archive/2009/05/26/what-is-a-vsix.aspx.

As described on Quan To’s article, the .vsix file is derived from the Visual Studio Installer found in the Visual Studio 2005 and 2008 versions. The original .vsi file launches the Content Installer from these past Visual Studio versions. The .vsi file represented many various types of content for the Visual Studio IDE (macros, add-ins, toolbox controls, code snippets, and so forth). To make the distinction clearer from this previous method of installing content, an ‘x’ was placed at the end of the extension, hence a .vsix file.

For more information about the Open Packaging Convention, please see the article titled “A New Standard For Packaging Your Data,” at http://msdn.microsoft.com/en-us/magazine/cc163372.aspx.

Disabling an Extension
If you need to disable an extension for any reason—for example, the Visual Studio performance is slower than expected, the IDE crashes repeatedly, or the extension is simply not working—you can disable an extension via Extension Manager.

Select Installed Extensions in the left navigation pane of the Extension Manager, and then click Disable on any extension in the list. Again, a restart is required to disable the extension.

NOTE
You can disable or re-enable multiple extensions at the same time within the Extension Manager, requiring only one restart of the Visual Studio IDE.

Uninstalling an Extension
The most straightforward way to uninstall an extension is through the Extension Manager. Select Installed Extension in the left navigation pane of the Extension Manager, and then click Uninstall on any extension in the list. Again, a restart is required to remove the extension.

NOTE
You can uninstall or reinstall multiple extensions at the same time within the Extension Manager, requiring only one restart of the Visual Studio IDE.

The other way to uninstall an extension is to delete the contents of the extension from the Visual Studio extension folder on your hard drive. Simply delete the extension .vsix file from the %LocalAppData%\Microsoft\VisualStudio\10.0\Extensions directory, and restart Visual Studio.

Resources for Developing Extensions
As noted, creating and developing extensions are beyond the scope of this book. However, many great resources are available, such as the following:

Visual Studio Extensibility Developer Center —http://msdn.com/vsx

Extensibility samples —http://code.msdn.microsoft.com/vsx





Introducing Visual Studio Extensions
08.01 Create Themes Using All Visual Studio Elements
08.02 Insert Images into Your Code
16h 24m remaining
08.01 Create Themes Using All Visual Studio Elements
NAME

Visual Studio Color Theme Editor

CREATED BY

Matthew Johnson (Microsoft)

LOCATION

http://visualstudiogallery.msdn.microsoft.com/en-us/20cd93a2-c435-4d00-a797-499f16402378?SRC=Home

You can use the Visual Studio Color Theme Editor to create themes consisting of colors that go beyond those listed in the Tools | Options | Fonts And Colors page.

Visual Studio Color Theme Editor
The most useful feature of the Visual Studio Color Theme Editor extension is that it provides a central location for controlling almost all possible colors in the IDE. No more having to edit individual fonts and colors options under Tools | Options. Refer to the “To Customize” section later in this section for more information about how to use this feature.


To Use
A Theme menu option is located on the Visual Studio file menu. The Theme menu lists multiple themes for you to choose from, including the Windows Classic look.

To Customize
You can create your own themes by clicking Theme | Customize Colors and choosing from hundreds of customized colors. This list of colors is significantly longer than the list found on the Tools | Options | Fonts And Colors page, because this extension lists every user interface element that implements the Visual Studio color service.


You can create new themes by clicking the Save button located in the toolbar in the upper-left corner. All themes are saved as .xml files, using the .vstheme file extension name. You can share a .vstheme file with others.

More Information
Make sure you check out the extension developer’s blog post at http://blogs.msdn.com/visualstudio/archive/2010/01/04/changing-visual-studio-s-color-palette.aspx for an in-depth overview of the extension.





Introducing Visual Studio Extensions
08.01 Create Themes Using All Visual Studio Elements
08.02 Insert Images into Your Code
16h 24m remaining
08.01 Create Themes Using All Visual Studio Elements
NAME

Visual Studio Color Theme Editor

CREATED BY

Matthew Johnson (Microsoft)

LOCATION

http://visualstudiogallery.msdn.microsoft.com/en-us/20cd93a2-c435-4d00-a797-499f16402378?SRC=Home

You can use the Visual Studio Color Theme Editor to create themes consisting of colors that go beyond those listed in the Tools | Options | Fonts And Colors page.

Visual Studio Color Theme Editor
The most useful feature of the Visual Studio Color Theme Editor extension is that it provides a central location for controlling almost all possible colors in the IDE. No more having to edit individual fonts and colors options under Tools | Options. Refer to the “To Customize” section later in this section for more information about how to use this feature.


To Use
A Theme menu option is located on the Visual Studio file menu. The Theme menu lists multiple themes for you to choose from, including the Windows Classic look.

To Customize
You can create your own themes by clicking Theme | Customize Colors and choosing from hundreds of customized colors. This list of colors is significantly longer than the list found on the Tools | Options | Fonts And Colors page, because this extension lists every user interface element that implements the Visual Studio color service.


You can create new themes by clicking the Save button located in the toolbar in the upper-left corner. All themes are saved as .xml files, using the .vstheme file extension name. You can share a .vstheme file with others.

More Information
Make sure you check out the extension developer’s blog post at http://blogs.msdn.com/visualstudio/archive/2010/01/04/changing-visual-studio-s-color-palette.aspx for an in-depth overview of the extension.





08.01 Create Themes Using All Visual Studio Elements
08.02 Insert Images into Your Code
08.03 Add Visual Guidelines to Your Code
16h 24m remaining
08.02 Insert Images into Your Code
NAME

Image Insertion

CREATED BY

Microsoft

LOCATION

http://visualstudiogallery.msdn.microsoft.com/en-us/793d16d0-235a-439a-91df-4ce7c721df12

The Image Insertion tool allows you insert images, such as a UML diagram, directly into your code. Another example is including user interface designs within your code for documentation purposes.

Image Insertion
Regardless of usage, the Image Insertion extension demonstrates that the Visual Studio 2010 editor is new and that creative extensions are possible.

Recall that the Visual Studio code editor is written using the Windows Presentation Foundation (WPF). The following illustration shows a Silverlight illustration of a hand-drawn stick figure at 100 percent zoom.


When the editor zoom is increased to 200 percent, notice how both the text and the stick figure image increase at the same ratio.


It is worth mentioning that this is not a separate designer built solely for this purpose. This is the actual Visual Studio code editor displaying the image.

To Use
Select an image from either a Windows Explorer window or Solution Explorer, and drag the image onto the editor surface. To successfully insert the image, you must see the blue placeholder line, as shown in the following illustration. Also note that Visual Studio inserts the image directly above the blue line.


To remove the inserted image, place the mouse directly over the image until a Close button appears. Click the X button in the upper-right corner to remove the inserted image. The user interface is sensitive, so it is best to move the mouse slowly towards the X button to avoid having the controls disappear.

To resize the inserted image, use the mouse to grip the arrow controls, just as you would resize any standard window.

To Save
The images are not saved as part of the code file. The images are saved in a separate .resx file. In this example, because the image is inserted in a Page.xaml.cs file, the image is saved in a Page.xaml.Images.resx file, which is viewable in Solution Explorer. Most source control management systems allow users to customize whether .resx files should be included in a source code check-in.

To Customize
Although this extension doesn’t come with any options to configure, the source code is available for tweaking at http://editorsamples.codeplex.com.





08.02 Insert Images into Your Code
08.03 Add Visual Guidelines to Your Code
08.04 Get More IntelliSense in Your XAML Editor
16h 24m remaining
08.03 Add Visual Guidelines to Your Code
NAME

Editor Guidelines, Editor Guidelines UI

CREATED BY

Paul Harrington (Microsoft)

LOCATIONS

http://visualstudiogallery.msdn.microsoft.com/0fbf2878-e678-4577-9fdb-9030389b338c

http://visualstudiogallery.msdn.microsoft.com/en-us/7f2a6727-2993-4c1d-8f58-ae24df14ea91

The Editor Guidelines displays vertical lines within your code to help you visualize regions, end of printable margins, and so forth.

Editor Guidelines
Although this feature has been in many previous versions of Visual Studio, it was necessary to modify the registry to use the feature. This extension brings the guidelines feature back to Visual Studio 2010 and includes options within the Visual Studio IDE to modify the guidelines.


To Install
The Editor Guidelines extension consists of two extensions:

Editor Guidelines (http://visualstudiogallery.msdn.microsoft.com/en-us/0fbf2878-e678-4577-9fdb-9030389b338c)—This extension brings back the guidelines feature; however, it requires modifications to the registry to use the guidelines.

Editor Guidelines UI (http://visualstudiogallery.msdn.microsoft.com/en-us/7f2a6727-2993-4c1d-8f58-ae24df14ea91)—This extension provides options within Visual Studio to use the guidelines, instead of manually editing the registry

NOTE
The Editor Guidelines UI extension is an extension of the Editor Guidelines extension. The ability to extend an extension from another extension is a feature of the Managed Extensibility Framework. To install the Editor Guidelines UI extension, the Editor Guidelines extension must be installed first; otherwise, the Extension Manager displays an error message.

To Use
If you plan to use only the first extension, you need to manually edit the registry, so use at your own risk! The registry key for the guidelines feature is the same as in previous versions of Visual Studio: [HKEY_CURRENT_USER]\Software\Microsoft\VisualStudio\10.0\Text Editor.

You need to create a new REG_SZ string called “Guides” to store the information for the guideline. For example, the string “RGB(0,255,0) 100” sets a green guideline on column 100. To add additional guidelines, add the other column numbers to the Guides value separated by commas, such as RGB(0, 255, 0) 5, 60, 100.

If you have the Editor Guidelines UI extension installed, things are a lot simpler.

Right-click wherever you wish to place the guideline, and from the context menu, select Add Guideline.

To remove the guideline, place your cursor on the column where you wish to remove the guideline, right-click, and select Remove Guideline.


To Customize
To customize the colors for the guideline, select Guideline Color from the context menu, and select colors from the color palette window.





08.03 Add Visual Guidelines to Your Code
08.04 Get More IntelliSense in Your XAML Editor
08.05 Sync the Solution Explorer to the Current File
16h 24m remaining
08.04 Get More IntelliSense in Your XAML Editor
NAME

XAML IntelliSense Presenter

CREATED BY

Karl Shifflett

LOCATION

http://visualstudiogallery.msdn.microsoft.com/1a67eee3-fdd1-4745-b290-09d649d07ee0

The XAML IntelliSense Presenter extension allows you to use the new Pascal casing and list filtering IntelliSense features in your XAML code.

XAML IntelliSense Presenter
If you’ve grown accustomed to the new Pascal casing and list filtering features in IntelliSense, you’ll be happy to know that the Visual Studio 2010 XAML Editor IntelliSense extension gives you these features and more in the XAML editor.

To Use
Start typing in any XAML editor to bring up IntelliSense. As you start typing, you can see the Pascal case narrowing the available selection. The Pascal case narrowing filter option is enabled by default, as circled in the following illustration.


You can also toggle whether code snippets, namespaces, or element tags appear in IntelliSense.

For More Information
Check out the developer’s blog post for this extension: http://karlshifflett.wordpress.com/2010/03/21/visual-studio-2010-xaml-editor-intellisense-presenter-extension.





08.04 Get More IntelliSense in Your XAML Editor
08.05 Sync the Solution Explorer to the Current File
08.06 Add PowerCommands Options to the IDE
16h 24m remaining
08.05 Sync the Solution Explorer to the Current File
NAME

Solution Explorer Tools

CREATED BY

Chris McGraph

LOCATION

http://visualstudiogallery.msdn.microsoft.com/ef4ac3e9-d056-4383-8ca2-11721bd879b4

The Solution Explorer Tools extension provides you with greater control over how and when the Solution Explorer syncs to the currently opened document.

Solution Explorer Tools
The Solution Explorer Tools extension provides additional features on the Solution Explorer toolbar for controlling the opened solution.

To Use
For this extension to work properly, you must uncheck the Track Active Item in Solution Explorer option found on the Tools | Options | Projects and Solutions | General page.

When the Tools extension is installed, several new buttons appear on the Solution Explorer toolbar, as shown in the following illustration.


The following list describes the buttons from left to right:

Sync Item —This command places the active selection in the Solution Explorer to the currently opened document.

Collapse All —This command recursively collapses everything in the Solution Explorer.

Collapse to Item —This command combines the two previous commands by placing the active selection in the Solution Explorer to the currently opened item and collapsing everything else in the Solution Explorer.

You can also assign keyboard shortcuts to each of the following commands on the Tools | Options | Environment | Keyboard page:

Project.SyncItem

Project.Collapseall

Project.CollapseToItem





08.05 Sync the Solution Explorer to the Current File
08.06 Add PowerCommands Options to the IDE
08.07 Use Emacs Commands in the Editor
16h 24m remaining
08.06 Add PowerCommands Options to the IDE
NAME

PowerCommands

CREATED BY

Microsoft

LOCATION

http://visualstudiogallery.msdn.microsoft.com/en-us/e5f41ad9-4edc-4912-bca3-91147db95b99

The PowerCommands extension provides additional tweaks for customizing the IDE.

PowerCommands for Visual Studio 2010
The PowerCommands have been a popular add-in for the past several previous versions of Visual Studio.

To Use
The PowerCommands extension provides additional options for customizing the IDE. These options are found on the Tools | Options | PowerCommands | General and Commands pages.

The following is a list of each of the PowerCommands options to help you discover all the ways you can further customize the IDE:

Format Document On Save —Saving the file automatically formats the document.

Remove And Sort Usings On Save —Saving the file automatically removes any unused using statements. This option automatically sorts all using statements in alphabetical order.

Remove and Sort Usings —This command can be found on the Solution Explorer context menu at both the Solution level and at the individual project levels. It preforms the same functionality as the previous command.

Clear All Panes —This command clears all Output Window subwindows at once. The Clear All Panes button is located just to the right of the Show Output From drop-down list on the Output Window toolbar.

Copy Path —This command copies the full file path of the currently selected item in the Solution Explorer to the clipboard. It works with the solution node, a project node, any project item node, and any folder.

Email Code Snippet —Select code in the editor, right-click to open the context menu, and select Email Code Snippet to email the code snippet. The subject of the generated email is based on the file name—for example, “Subject: CodeSnippet from Program.cs”.

Insert Guid Attribute —To add a GUID attribute to a class, right-click anywhere within the class and select Insert Guid Attribute from the context menu.

Show All Files This option places an additional Show All Files button on the Solution Explorer toolbar. The leftmost Show All Files button is for the current project, and the rightmost Show All Files button is for the entire solution.

Undo Close To reopen the most-recently closed document, go to Edit | Undo Close. The keyboard shortcut is Ctrl+Shift+Z. The cursor is placed at its last known position. To see a list of all the most-recently closed documents, go to View | Other Windows | Undo Close Window.

Collapse Projects To collapse everything under a project node, including any sub-nodes (this being the key difference from the standard Windows behavior), right-click and select Collapse Project from the Solution Explorer context menu. This command works for solutions, projects, and solution folders.

Copy Class / Paste Class To copy and paste a class, select a project item (usually a class file) on the Solution Explorer that you want to copy. Right-click and select Copy Class from the context menu. Navigate to the project node, and right-click to see the Paste Class command.

Copy As Project Reference Found on the Solution Explorer context menu, this command copies a project (from its project node) and pastes it into another project node as a project reference.

Edit Project File The Edit Project File option unloads a project and automatically opens the file in the editor for editing.

Open Containing Folder Similar to the command found on the file tabs and in the Solution Explorer for a node, this command opens the containing folder for an item in the Solution Explorer.

Open Command Prompt This option opens a Visual Studio command prompt directly from the Solution Explorer.

Unload Projects / Reload Projects Similar to the built-in command for unloading a project, the Unload Projects command (found on the Solution Explorer context menu for a project node) unloads all the projects in a solution.

Extract Constant Found under the Refactor menu, the Extract Constant creates a constant based on the selected text.

Clear Recent File List This command removes specified recent files. In past versions of Visual Studio, this clearing required manual modifications to the registry. The command is found on the File | Recent Files menu as Clear Recent File List. This command opens a window for you to specify which files to clear.

Clear Recent Project List Similar to the Clear Recent File List, this command removes projects specified by the user.

Close All Found on the file tab context menu, this command closes all open documents.

For More Information
For more information about the PowerCommands extension, you can read the following blog post: http://saraford.net/2010/09/07/power-commands-for-visual-studio-2010-extension-8.





08.06 Add PowerCommands Options to the IDE
08.07 Use Emacs Commands in the Editor
08.08 Submit to “The Daily WTF”
16h 24m remaining
08.07 Use Emacs Commands in the Editor
NAME

Emacs Emulation

CREATED BY

Microsoft

LOCATION

http://visualstudiogallery.msdn.microsoft.com/en-us/09dc58c4-6f47-413a-9176-742be7463f92

The Emacs Commands extension provides basic support for Emacs keybindings and text editing commands.

Emacs Emulation
This extension brings back the Emacs commands for the Visual Studio 2010 editor.

To Use
To finish installing the extension, you must open a project or create a new project. Opening a project prompts you for elevated permissions to finish installing the Emacs.vsk file (the Emacs keyboard shortcut file) to the Visual Studio IDE folder located under Program Files directory. Elevated permissions are required because only user accounts with administrator privileges can reach this folder by default in Windows.


Select Emacs in the Tools | Options | Environment | Keyboard page’s scheme drop-down list to enable the Emacs emulation experience.


To Uninstall
When you disable or uninstall the extension, the Emacs option remains selected in the Tools | Options | Keyboard list. You must go back to the Tools | Options | Environment | Keyboard page and select the “(Default)” key bindings or your preferred keyboard mapping scheme.

If you forget to change the keyboard mapping scheme, you’ll notice a great many commands and keyboard shortcuts not working in the editor, such as Ctrl+F for the Find window.

Because administrator rights were required to add this file, you also need administrator rights to remove it. Unlike the install scenario for opening or creating a project, there isn’t an opportunity for the extension to prompt you to remove the .vsk file. For example, the extension cannot prompt you the next time you open a project (as in the install scenario) because the extension itself is already gone.

You can manually delete the Emacs.vsk file at your own risk, but there is no impact to Visual Studio if you decide to keep the file.

More Information
You can find more information about all the Emacs keyboard shortcuts supported by the extension at the following location: http://visualstudiogallery.msdn.microsoft.com/en-us/09dc58c4-6f47-413a-9176-742be7463f92.





08.07 Use Emacs Commands in the Editor
08.08 Submit to “The Daily WTF”
08.09 Diff Files Using the Editor
16h 24m remaining
08.08 Submit to “The Daily WTF”
NAME

The Daily WTF

CREATED BY

Inedo.com

LOCATION

http://inedo.com/Downloads/SubmitToWTF.aspx

SOURCE CODE LOCATION

http://code.google.com/p/submittotdwtf

VERSIONS

2005, 2008, 2010

Have you ever inherited source code so poorly written that you’ve asked a colleague to come into your office to take a look? If so, this extension is for you.

Share Bad Code with the World
Started in May 2004, “The Daily WTF” (also known as “The Daily Worse Than Failure”) is a blog dedicated to poorly written code, poor project management decisions, and bizarre interview stories.

This extension allows you to submit a code snippet directly from your code editor to “The Daily WTF.” It is the equivalent of using the website’s contact form to submit a code suggestion.

It is a little-known fact that Sara Ford’s writing style for the “Visual Studio 2008 Tip of the Day” series was inspired by Alex Papadimoulis’ writing style for “The Daily WTF.” The idea of providing personal commentary alongside factual information was very appealing for a daily tip series. (Thank you, Alex!)

To Install
At the time of this writing, this extension is not located on the Visual Studio Gallery.

You can download the extension from http://inedo.com/Downloads/SubmitToWTF.aspx. Links for both Visual Studio 2010 and Visual Studio 2005/2008 appear on the page. After you have downloaded the extension, unzip the folder and double-click the SubmitToWTF2010.vsix file.

To Use
Select code within a code editor, and open the context menu to see the Submit To TDWTF command appear. Click the Submit To TDWTF command to open a dialog box that requests additional information about the code snippet. Additionally, there is an option to request that the code snippet is not published.

More Information
You can find more information about The Daily WTF at http://thedailywtf.com.





08.08 Submit to “The Daily WTF”
08.09 Diff Files Using the Editor
08.10 Run Windows PowerShell Within the IDE
16h 24m remaining
08.09 Diff Files Using the Editor
NAME

CodeCompare

CREATED BY

Devart Software

LOCATION

http://visualstudiogallery.msdn.microsoft.com/dace3633-0b51-4629-85d4-c59cdce5bb3b

VERSIONS

2008, 2010

You can compare code side-by-side within the Visual Studio Editor by using the CodeCompare extension.

CodeCompare
The CodeCompare tool uses the Visual Studio code editor to compare two files side-by-side, allowing you to continue using all the Visual Studio code editor functionality, like syntax coloring, IntelliSense, Ctrl+Mouse Wheel zooming, and so on.

To Install
The CodeCompare tool does not use the new Visual Studio Extensibility model, so it is not found in the Extension Manager. To install, run the executable file hosted on the Visual Studio Gallery and follow the instructions in the setup wizard.

To Use
To start the CodeCompare tool, go to Tools | CodeCompare | New Comparison. This action opens a new code comparison view alongside your code files using the Visual Studio code editor. Simply select two different files to compare to start seeing a visual representation of the differences between the files.


Features
CodeCompare is a fully functional code comparing tool, but a few features are worth mentioning, including the following:

Merge Code Move code from one comparison view to the other. Each indicated line that is different per view has a << or a >> symbol that illustrates it is possible to merge that line or block of code to the other file.

Structure Comparison Compare code by its structure, namely its classes, fields, and methods. This comparison is shown in the Difference Explorer. Oddly enough, in the free version of CodeCompare, attempting to click within the Difference Explorer clears its contents. The cursor focus must remain within the code editor for the Difference Explorer to show the structural differences between the code files.

New Folder Comparison Compare code at the file level. Select two folders, and the compare tool shows you which files are different or not included. Double-click a file to do a code comparison at the file level in a new window.

To Uninstall
Go to Windows Control Panel | Uninstall A Program window, and select the Devart CodeCompare application. Click the Uninstall command on the menu to uninstall CodeCompare.

More Information
You can find more information about CodeCompare at http://www.devart.com/codecompare.





08.09 Diff Files Using the Editor
08.10 Run Windows PowerShell Within the IDE
08.11 Visualize OData in a Graphical View
16h 24m remaining
08.10 Run Windows PowerShell Within the IDE
NAME

PowerConsole

CREATED BY

Jianchun Xu (Microsoft)

LOCATION

http://visualstudiogallery.msdn.microsoft.com/67620d8c-93dd-4e57-aa86-c9404acbd7b3

VERSIONS

2010

You can use the PowerConsole extension to run both Windows PowerShell commands and Visual Studio object model (DTE) commands within the IDE.

To Use
To open the Power Console tool window, go to View | Other Windows | Power Console.

The Power Console allows you to run more than just Windows PowerShell commands. Additionally, you can call the Visual Studio object model (DTE), access Visual Studio services, interact with Visual Studio MEF components, and host your own scripting language within the Power Console.


More Information
You can find more information about the Power Console at http://visualstudiogallery.msdn.microsoft.com/67620d8c-93dd-4e57-aa86-c9404acbd7b3.





08.10 Run Windows PowerShell Within the IDE
08.11 Visualize OData in a Graphical View
08.12 Run VIM Commands in the Editor
16h 24m remaining
08.11 Visualize OData in a Graphical View
NAME

Open Data Protocol Visualizer

CREATED BY

Microsoft

LOCATION

http://visualstudiogallery.msdn.microsoft.com/f4ac856a-796e-4d78-9a3d-0120d8137722

You can use the Open Data Protocol Visualizer extension to get a graphical view of an OData service.

Open Data Protocol Visualizer
The Open Data Protocol Visualizer provides a read-only graphical view of the types and relationships provided by a WCF Data Service.

To Use
Create a service reference through the Add Service Reference dialog box. Open the context menu for the service reference in the Solution Explorer, and select the new View In Diagram command to open the visualizer.

At the bottom of the visualizer, select the elements you want to view, or select “all” to visualize everything. You can also browse elements by using the Open Data Protocol Model Browser found under the View menu.


More Information
You can find a video explaining how to use the Open Data Protocol Visualizer extension located at http://odataprimer.com/ODataVisualizerExtensionForVS2010Screencast.ashx.

You can also find a list of OData services at http://www.odata.org/producers.





08.11 Visualize OData in a Graphical View
08.12 Run VIM Commands in the Editor
08.13 Check Spelling in Your Code
16h 24m remaining
08.12 Run VIM Commands in the Editor
NAME

VsVim

CREATED BY

Jared Parsons (Microsoft)

LOCATION

http://visualstudiogallery.msdn.microsoft.com/59ca71b3-a4a3-46ca-8fe1-0e90e3f79329

SOURCE CODE

http://github.com/jaredpar/VsVim

The VsVim extension provides a Vim editing experience within the Visual Studio editor.

To Use
When enabled, the VIM extension immediately prompts you at the top of the editor to customize how many Visual Studio keyboard shortcut defaults you want to use. You can make additional modifications by clicking the Options button at the bottom of the editor next to the VIM extension status bar, as shown in the following illustration.


More Information
You can find a frequently asked question list for the VIM extension located at https://github.com/jaredpar/VsVim/wiki/faq.





08.12 Run VIM Commands in the Editor
08.13 Check Spelling in Your Code
08.14 Zoom Across All Files
16h 24m remaining
08.13 Check Spelling in Your Code
NAME

Spell Checker

CREATED BY

Noah Richards with Roman Golovin and Michael Lehenbauer

LOCATION

http://visualstudiogallery.msdn.microsoft.com/7c8341f1-ebac-40c8-92c2-476db8d523ce

You can check for spelling errors in your code by using the Spell Checker extension.

Spell Checker
The Spell Checker extension provides a spell checker within the Visual Studio editor.

To Use
The Spell Checker extension provides spelling corrections for plain text files, comments and strings in source code, and text that isn’t included within HTML tags in .html and .aspx files.

The Spell Checker uses Smart Tags, meaning that you can simply press Ctrl+. to invoke the Smart Tag window.

If you want the change the color of the red squiggles so that spelling errors are not confused with syntax errors, you can go to the Tools | Options | Environment | Fonts And Colors page, and under Display Items, select Spelling Error and change the Item Foreground color to the appropriate color.






08.13 Check Spelling in Your Code
08.14 Zoom Across All Files
08.15 View Code Blocks Using Vertical Lines
16h 24m remaining
08.14 Zoom Across All Files
NAME

Presentation Zoom

CREATED BY

Chris Granger (Microsoft)

LOCATION

http://visualstudiogallery.msdn.microsoft.com/6a7a0b57-7059-470d-bcfa-60ceb78dc752

You can maintain a consistent zoom percentage across all open files using the Presentation Zoom extension.

Presentation Zoom
By default, the new Presentation Zoom extension in Visual Studio 2010 works only for the current file. Additional files are not affected by the zoom. This is especially noticeable when giving presentations, where the presenter has to zoom each file separately.

This extension provides a global zoom level, so all open files can share the same zoom level.

To Use
Simply use the zoom feature, either by Ctrl+Mouse wheel or updating the zoom percentage at the bottom-left corner of the editor. The next file opened or navigated to persists the same zoom percentage.

Control Zooming with a Slider Using the ZoomEditorMargin Extension
NAME

ZoomEditorMargin

CREATED BY

Benjamin Gopp

LOCATION

http://visualstudiogallery.msdn.microsoft.com/c271d574-a481-4974-b7dd-f319404de898

Similar to the Presentation Zoom extension discussed in the preceding section, the ZoomEditorMargin extension provides a slider control in the bottom-right corner of the editor for specifying the zoom percentage for the file in view. The ZoomEditorMargin extension works in conjunction with the Presentation Zoom extension.






08.14 Zoom Across All Files
08.15 View Code Blocks Using Vertical Lines
08.16 Get a Bird’s-Eye View of Your Code in an Editor Margin
16h 24m remaining
08.15 View Code Blocks Using Vertical Lines
NAME

StructureAdornment

CREATED BY

David Pugh (Microsoft)

LOCATION

http://visualstudiogallery.msdn.microsoft.com/203f22f4-3e9f-4dbb-befc-f2606835834e

The StructureAdornment extension displays vertical lines in the editor to show the block structure of the code file.

StructureAdornment
The StructureAdornment extension uses different colors to indicate different blocks.


To Use
By default, vertical lines appear in the editor. To see the beginning of a particular code block that is outside the view, mouse-over the vertical line to display the beginning of that particular code block.


To Customize
This extension does not have a page in Tools | Options; however, you can manually edit the registry settings for the extension. The following editor options are stored in the registry under HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Text Editor:

StructureAdornment/LineWidth Width of the lines used to show the various scopes.

StructureAdornment/ClassColor Color used to show the scope of class definitions as ARGB.

StructureAdornment/ConditionalColor Color used to show the scope of conditionally executed code as ARGB.

StructureAdornment/LoopColor Color used to show the scope of loop bodies as ARGB.

StructureAdornment/MethodColor Color used to show the scope of method bodies as ARGB.

StructureAdornment/UnknownColor Color used to show the scope of unknown blocks as ARGB.

StructureAdornment/MethodSeparatorColor Color used draw a horizontal separator line at the end of a method as ARGB (off by default).

StructureAdornment/Enabled Show structure adornments.

Modifications made to the extension appear the next time a code editor is opened.

To Uninstall
This extension installs five separate extensions. To completely remove this extension, you need to remove the following extensions:

BlockTagger

BlockTaggerImpl

SettingsStore

SettingsStoreImpl

StructureAdornment

You can uninstall all five extensions at the same time within the Extension Manager. If prompted about a Dependence Alert, click Uninstall Anyways to continue uninstalling all extensions.





08.15 View Code Blocks Using Vertical Lines
08.16 Get a Bird’s-Eye View of Your Code in an Editor Margin
08.17 Build Projects from the Windows 7 Taskbar
16h 24m remaining
08.16 Get a Bird’s-Eye View of Your Code in an Editor Margin
NAME

AllMargins

CREATED BY

David Pugh (Microsoft)

LOCATION

http://visualstudiogallery.msdn.microsoft.com/465a0d53-5133-4edd-a0cd-94484fe3d853

The AllMargins extension provides a complete overview of your code to improve navigation.

AllMargins
The AllMargins extension installs multiple extensions. The two most notable are the OverviewMargin extension, a bird’s-eye view of the logical layout of your code all within an editor margin, and the StructureAdornment extension, which displays vertical lines in the editor, representing structural code blocks.

See the extension 08.15 View Code Blocks Using Vertical Lines for more information about the StructureAdornment extension.

To Use
By default, both the StructureAdornment extension and the OverviewMargin extension are visible in the editor. The OverviewMargin appears on the right side of the editor.


Mouse-over the left side of the OverviewMargin to see a code snippet for that particular section of code.


Mouse-over the right side of the OverviewMargin to see the structural code block in a condensed form.


To Uninstall
This extension installs 12 separate extensions. To completely remove this extension, you need to remove the following:

AllMargins

BlockTagger

BlockTaggerImpl

CaretMargin

ErrorsToMarks

MarkersToMarks

OverviewMargin

OverviewMarginImpl

SettingsStore

SettingsStoreImpl

StructureAdornment

StructureMargin

You can uninstall all 12 extensions at the same time within the Extension Manager. If prompted about a Dependence Alert, click Uninstall Anyways to continue uninstalling all extensions.





08.16 Get a Bird’s-Eye View of Your Code in an Editor Margin
08.17 Build Projects from the Windows 7 Taskbar
08.18 Triple-Click to Select an Entire Line
16h 24m remaining
08.17 Build Projects from the Windows 7 Taskbar
NAME

Win7 Taskbar Extension

CREATED BY

Dmitry Sitnikov

LOCATION

http://visualstudiogallery.msdn.microsoft.com/0c92dd87-50ac-489e-882b-b99de7624502

You can use the Win7 Taskbar Extension to start a build or debug session directly from the Windows 7 taskbar.

Win7 Taskbar Extension
The Win7 Taskbar Extension allows you to start a build or debug session for the specified Visual Studio application directly from the Windows 7 taskbar. This extension can save you time when you need to build different projects located in multiple instances of Visual Studio.

To Install
The Win7 Taskbar Extension tool is an extension of the Windows 7 taskbar, so it is not found in the Extension Manager. To install, run the executable file hosted on the Visual Studio Gallery location and follow the instructions in the setup wizard.

To Use
Mouse-over any Visual Studio window in the Windows 7 taskbar to see the extension appear. Simply click the corresponding button for Build, Start Debugging, or Start Without Debugging.


To Uninstall
Open the Windows Control Panel | Uninstall a Program window, and select the Visual Studio Win7 Taskbar Add-in application. Click the Uninstall command listed on the menu to remove the extension.





08.17 Build Projects from the Windows 7 Taskbar
08.18 Triple-Click to Select an Entire Line
08.19 Create Regular Expressions Within Your Code
16h 24m remaining
08.18 Triple-Click to Select an Entire Line
NAME

Triple Click

CREATED BY

Noah Richards

LOCATION

http://visualstudiogallery.msdn.microsoft.com/2bbdc70c-32f7-4b69-8cff-d8190cae0cc7

SOURCE CODE

https://github.com/NoahRic/TripleClick

You can use the Triple Click extension to quickly select a line of code.

Triple Click
The Triple Click extension selects an entire line of code when the left mouse button is triple-clicked.


More Information
For more information, please see the extension author’s blog post at http://blogs.msdn.com/b/noahric/archive/2009/10/19/beta-2.aspx.





08.18 Triple-Click to Select an Entire Line
08.19 Create Regular Expressions Within Your Code
08.20 Get More Productivity Tools in the IDE
16h 24m remaining
08.19 Create Regular Expressions Within Your Code
NAME

Regex Editor

CREATED BY

Microsoft

LOCATION

http://visualstudiogallery.msdn.microsoft.com/55c24bf1-2636-4f94-831d-28db8505ce00

SOURCE CODE

http://editorsamples.codeplex.com

The Regex Editor helps you write regular expressions faster and easier.

Regex Editor
The Regex Editor extension is an aid for creating, testing, and saving regular expressions.

To Use
To invoke the Regex Editor window, you need to create a new Regex class within your code. For example, type in the following:

Regex r = new Regex(
This opens the Regex Editor window, shown in the following illustration.


More Information
For more information, please visit the project’s homepage at http://editorsamples.codeplex.com.





08.19 Create Regular Expressions Within Your Code
08.20 Get More Productivity Tools in the IDE
08.21 Create and Find Code Snippets
16h 24m remaining
08.20 Get More Productivity Tools in the IDE
NAME

Visual Studio Productivity Power Tools

CREATED BY

Microsoft

LOCATION

http://visualstudiogallery.msdn.microsoft.com/d0d33361-18e2-46c0-8ff2-4adea1e34fef

The Visual Studio Productivity Power Tools are a collection of extensions intended to maximize a developer’s productivity.

To Use
The tools include a variety of IDE productivity tweaks, such as the following:

Tools Options Support Allows for all of the included tools to be turned on or off by selecting Tools | Options | Productivity Power Tools.

Document Tab Well User Interface Customize the look and functionality of open Visual Studio tabs.

Searchable Add Reference Dialog Replace the default Add Reference Dialog with a dialog box that includes a substring search of the current pane.

Quick Access Search and execute common Visual Studio tasks.

Auto Brace Completion Improve code productivity by automatically inserting the matching closing code construct for the following characters: (), {}, [], “”, and ”.

Highlight Current Line Highlight the line in the code editor where the caret is located.

HTML Copy Copy code to the Windows Clipboard using the HTML Clipboard format, which makes it easy to retain code formatting.

Triple Click Triple-click anywhere on a line to select the entire line.

Fix Mixed Tabs Fix files that have a mix between tabs and spaces.

Ctrl+Click Go to Definition Jump quickly to a symbol definition via Ctrl+Click.

Align Assignments Increase code readability by aligning variable assignments. To use, press Ctrl+Alt+J.

Move Line Up/Down Commands Hold down the Alt key while tapping the Up/Down arrow to move the current line of code up or down.

Column Guides Everyone’s favorite Visual Studio registry modification, adding a vertical line guide to the code editor, can be set via the code editor context menu.

Colorized Parameter Help Add syntax color coding to Parameter Help.

To Customize the Document Tab Well User Interface
By default, the extension changes the Document Tab Well by coloring and grouping tabs based on their project, which is helpful when working with large solutions. You can customize these default settings by selecting Tools | Options | Productivity Power Tools | Document Tab Well.

Several preset configurations are available, including the following: Visual Studio 2008, Visual Studio 2010, Web Browser, Scrollable Tab Well, Vertical Tab Well, and Dynamic Tab Well.

The Visual Studio 2008 and 2010 configurations act exactly as their names imply, causing the default tab well to behave like those versions of the IDE.

Both the Web Browser and Dynamic Tab Wells add file type icons to what would otherwise be a typical Visual Studio 2010 tab. The difference between the two is that the Dynamic Tab Well closes the least-recently used tab when there is no more space available in the file tab channel.


The Scrollable Tab Well is the default for the extension.


The Vertical Tab Well has the same characteristics as the Scrollable Tab Well but places the tabs vertically, allowing for more viewable tabs.


It is possible to tweak all of the configurations. The ability to pin tabs is probably the most useful customization. For example, you probably often want to view the contents of many files while actually working on only one or two. The ability to pin specific tabs that you are focusing on, to keep them from falling out of focus, is a huge time-saver. When you pin many tabs, you can use the Show Pinned Tabs In A Separate Row/Column option. This keeps the pinned tabs from taking up too much space.


The biggest tab productivity boost comes in the form of added keyboard navigation. In Windows, Ctrl+Tab switches to the next child window for a given program. It’s known that many users do not prefer the Ctrl+Tab window that appears in Visual Studio. The Productivity Power Tools extension offers the option of moving backward and forward in visual order via Ctrl+Alt+Page Down/Up. Even more exciting, you can jump to a pinned tab via Ctrl+Num Pad 1 through 0. Talk about keyboard efficiency!





08.20 Get More Productivity Tools in the IDE
08.21 Create and Find Code Snippets
08.22 Document Your Code with Three Keystrokes
16h 24m remaining
08.21 Create and Find Code Snippets
NAME

Snippet Designer

CREATED BY

Matt Manela

LOCATION

http://visualstudiogallery.msdn.microsoft.com/B08B0375-139E-41D7-AF9B-FAEE50F68392

The Snippet Designer is an open source extension for Visual Studio that makes it easier to create and manage code snippets.

Snippet Designer
The Snippet Designer extension adds both an editor for .snippet files as well as a tool window to search for existing code snippets.


To Use
You can interact with the Snippet Designer within Visual Studio in several different ways, including the following:

You can create a new code snippet from scratch by launching the new file dialog box (File | New File) and then choosing Snippet Designer | Code Snippet. This launches the Snippet Editor, which lets you enter the code snippet, create variable replacements, and set metadata about the snippet.

You can create a snippet from existing code in your editor (for C#, Visual Basic, JavaScript, SQL, XML, or HTML) by highlighting the text and choosing Export As Snippet from the context menu. This launches the Snippet Editor prepopulated with the highlighted code.

You can search for existing code snippets by launching the Snippet Explorer tool window at View | Other Windows | Snippet Explorer. This tool window enables you to perform text search on all the code snippets on your computer. From this window, you can easily preview, edit, and delete any code snippet.

More Information
For more information about the Snippet Designer extension, including documentation, source code, issue tracker, and forum discussions on its CodePlex page, visit http://snippetdesigner.codeplex.com.





08.21 Create and Find Code Snippets
08.22 Document Your Code with Three Keystrokes
08.23 Customize Visual Studio Using Windows PowerShell
16h 24m remaining
08.22 Document Your Code with Three Keystrokes
NAME

GhostDoc

CREATED BY

SubMain

LOCATION

http://submain.com/download/ghostdoc

GhostDoc generates XML comments for your code by using a simple rules engine.

GhostDoc
Pairing this tool with a documentation generator such as NDoc (http://ndoc.sourceforge.net) or SandCastle (http://www.sandcastledocs.com) can automate much of the work of documenting your API.

To Use
GhostDoc adds a Document This command both to the Tools | GhostDoc menu and to the code editor context menu. By default, this command is available using the keyboard shortcut Ctrl+Shift+D.

When you invoke the command on a code element, the element’s name, parameters, and context information are passed through the GhostDoc rules engine. The rules engine performs a few linguistic tricks to produce a documentation comment that makes sense in the context of your code.

GhostDoc can produce documentation comments for classes, interfaces, structs, enums, constructors, finalizers, methods, properties, fields, events, indexers, and delegates.

The generated documentation comments are not complete, but they do provide a great starting point. The documentation comments in the code below were generated by GhostDoc and have not been edited from the original output:

/// <summary>
///
/// </summary>
public class Request : IDisposable
{
    /// <summary>
    /// Initializes a new instance of the <see cref="Request"/> class.
    /// </summary>
    public Request() {}

    /// <summary>
    /// Performs application-defined tasks associated with
    /// freeing, releasing, or resetting unmanaged resources.
    /// </summary>
    public void Dispose() {}

    /// Gets the status for user.
    /// </summary>
    /// <param name="userId">The user id.</param>
    /// <returns>
    ///   <see cref="API.RequestStatus"/> The request status
    /// </returns>
    public RequestStatus GetStatusForUser( string userId ) {/* ... */ }

    /// <summary>
    /// Gets a value indicating whether this instance is passive.
    /// </summary>
    /// <value>
    ///         <c>true</c> if this instance is passive; otherwise, <c>false</c>.
    /// </value>
    public bool IsPassive { get; private set; }

    /// <summary>
    /// Gets or sets the timeout.
    /// </summary>
    /// <value>
    /// The timeout.
    /// </value>
    public TimeSpan Timeout { get; set; }
}
Some conventions and niceties that drive GhostDoc:

Code symbols, such as parameter and member names, are split into words by case changes. For example, “userId” becomes “user id.”

Certain common members, such as the Dispose method and equality members, are recognized and documented with specific verbiage.

Method names are assumed to be describing an activity. For example, GetStatusForUser is interpreted as “Gets the status for user.” When the method name contains only a verb, such as Check, GhostDoc assumes the action applies to the class and documents the method as “Checks this instance.”

Property names that start with certain words, such as “Is,” “Has”, “Can”, and so on, are documented as state verifications. Property names containing a single word are documented as states. The documentation comment respects modifiers on property accessors, so read-only properties are documented as such.

GhostDoc is smart enough to add references to types used in member signatures.

Documentation comments applied to base types and members are inherited in deriving types.

To Customize
You can customize the way GhostDoc treats individual code element from the Tools | GhostDoc | Options page. The options for code-matching rules are extensive enough to adapt to any coding culture that relies on consistent naming conventions.

From the GhostDoc options dialog box, you can also configure linguistic operations and export or import your GhostDoc settings.

More Information
For more information about the GhostDoc extension, see http://submain.com/products/ghostdoc.aspx.





08.22 Document Your Code with Three Keystrokes
08.23 Customize Visual Studio Using Windows PowerShell
A. Visual Studio Keyboard Shortcut Posters
16h 24m remaining
08.23 Customize Visual Studio Using Windows PowerShell
NAME

StudioShell

CREATED BY

Code Owls LLC

LOCATION

http://studioshell.codeplex.com

StudioShell is a deeply integrated Windows PowerShell module that simplifies access to many of the extensibility features of Visual Studio.

StudioShell
Using StudioShell, with only a few lines of PowerShell script you can perform activities that typically require an add-in.

To Use
StudioShell ships with a hosted PowerShell console available from the main menu at View | StudioShell. By default, this console is available using the keyboard shortcut Ctrl+Shift+Enter.

You can use StudioShell features in other hosted PowerShell consoles, such as NuGet (http://nuget.codeplex.com) or PowerGUI VSX (http://powerguivsx.codeplex.com). From these consoles, enter the following command in your console to activate StudioShell:

Import-Module StudioShell
StudioShell exposes many of the extensibility features of Visual Studio as a drive named “DTE.” This drive lets you explore and access the extensibility features as if they were a file system on your local computer, using the same PowerShell commands you would use to manipulate files, the registry, and so on.

For example, you can see a list of existing Visual Studio window configurations by typing:

get-childitem dte:/windowConfigurations
You can create a new named window configuration by arranging your user interface and then entering:

new-item dte:/windowConfigurations -name MyConfig
You can apply the new window configuration at any time using:

invoke-item dte:/windowConfigurations/MyConfig
The standard PowerShell item commands apply to every area of the DTE drive. For example, you can use the same new-item command to create new project items:

new-item dte:/solution/projects/myProject -name MyClass.cs -type class
The Visual Studio features exposed on the DTE drive include the following:

User interface elements—Manipulate windows, modify menus, add custom commands implemented in PowerShell, manage items to the task and error lists, and drop data into the output pane.

Visual Studio settings—Script custom font and color settings for different environments.

Solutions and Projects—Create new projects and project items, explore and manipulate your code model, or add and remove project references.

Breakpoints and the Debugger—Create and remove breakpoints, set tracepoint conditions, write minidumps, or explore the current stack trace from the console.

StudioShell adds new features to Visual Studio as well, including the following:

Simple grid, chart, and graphing output windows usable from the console—For example, use the console to get a list of code metrics and drop them in a graph.

Profile scripts for environment customization—For example, import any other PowerShell modules you use regularly.

Solution script modules for per-solution environment customization—Modify your menus and windows on a solution-by-solution basis.

To Get Help
StudioShell documentation is available within the console. To get started, type:

get-help about_studioshell
For information about using standard PowerShell commands on the DTE drive, navigate to the area of the drive where you want to work and use the get-help command to retrieve help for the command you want to use:

cd dte:/debugger/breakpoints
get-help new-item
To Customize
StudioShell settings are available from the Tools | Options dialog in the StudioShell pane. You can indicate a specific console to use when StudioShell is invoked, including the default StudioShell hosted console, the process console, or no console (for example, if you want to use StudioShell from NuGet). In addition, you can change the profile script behavior of StudioShell and enable startup activity logging.

You can customize your console session with any PowerShell module or script. To find scripts relevant to your needs, visit the PowerShell Code Repository at http://www.poshcode.org.

More Information
For more information about the StudioShell module, see http://studioshell.codeplex.com and http://www.beefycode.com/post/Announcing-StudioShell.aspx.





08.23 Customize Visual Studio Using Windows PowerShell
