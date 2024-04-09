
2. Projects and Items
02.01 Search for Project Templates in the New Project Dialog Box

Chapter 2. Projects and Items
“He recalled his exertions and solicitations, and the history of his project […], which had been accepted for consideration […]”

— Leo Tolstoy “War and Peace”
After you get past your initial customization of Visual Studio, you will start creating projects and items to get your work done. This section contains a group of resources that you will find useful early on. Some will definitely be more useful to beginners (for example, searching templates), and others will apply to more advanced users (such as creating custom templates).

On the subject of custom templates, make sure you read though (and practice) how to create them. Of all the topics in this chapter, I feel that creating custom project and item templates will save you the greatest amount of time. That’s a pretty bold statement—but I have seen properly set up templates save untold hours for developers.





2. Projects and Items
02.01 Search for Project Templates in the New Project Dialog Box
02.02 Recent Project Templates in the New Project Dialog Box
16h 55m remaining
02.01 Search for Project Templates in the New Project Dialog Box
DEFAULT

Ctrl+Shift+N (new project dialog box); Ctrl+E (puts cursor in search box)

VISUAL BASIC 6

Ctrl+Shift+N (new project dialog box); Ctrl+N (new project); Ctrl+E (puts cursor in search box)

VISUAL C# 2005

Ctrl+Shift+N (new project dialog box); Ctrl+E (puts cursor in search box)

VISUAL C++ 2

Ctrl+Shift+N (new project dialog box); Ctrl+E (puts cursor in search box)

VISUAL C++ 6

Ctrl+Shift+N (new project dialog box); Ctrl+E (puts cursor in search box)

VISUAL STUDIO 6

Ctrl+N (new project dialog box); Ctrl+E (puts cursor in search box)

WINDOWS

Alt,F, N, P (new project dialog box); Alt,F, D, N (add new project)

MENU

File | New Project; File | Add New Project

COMMAND

File.NewProject; File.AddNewProject

VERSIONS

2010

CODE

vstipProj0001

Did you know that you can search for templates in the New Project dialog box? Look in the upper-right corner, and notice the new search area.


Click there or press Ctrl+E, and type the word web into the search box. The following illustration shows what you should expect to see.


Good News
The search populates the middle pane with results from the recent, installed, or online lists, depending on which category you select.

Bad News
The search doesn’t automatically filter the results according to your preferred language, and it doesn’t support any advanced search options, such as Boolean searches, regular expressions, and so on.

More Good News
In most cases, you can easily filter on your language by simply typing in an abbreviation of your language (C#, VB, F#, or C++).






02.01 Search for Project Templates in the New Project Dialog Box
02.02 Recent Project Templates in the New Project Dialog Box
02.03 Using Older Frameworks with Multi-Targeting
16h 55m remaining
02.02 Recent Project Templates in the New Project Dialog Box
DEFAULT

Ctrl+Shift+N (new project dialog box)

VISUAL BASIC 6

Ctrl+Shift+N (new project dialog box); Ctrl+N (new project)

VISUAL C# 2005

Ctrl+Shift+N (new project dialog box)

VISUAL C++ 2

Ctrl+Shift+N (new project dialog box)

VISUAL C++ 6

Ctrl+Shift+N (new project dialog box)

VISUAL STUDIO 6

Ctrl+N (new project dialog box)

WINDOWS

Alt,F, N, P (new project); Alt,F, D, N (add new project)

MENU

File | New Project; File | Add New Project

COMMAND

File.NewProject; File.AddNewProject

VERSIONS

2010

CODE

vstipProj0002

In the Visual Studio 2010 New Project dialog box, you can get a list of your five most recently used templates. Just click Recent Templates to see a list of the templates you have used.






02.02 Recent Project Templates in the New Project Dialog Box
02.03 Using Older Frameworks with Multi-Targeting
02.04 Create Web Application or Virtual Directory in IIS
16h 55m remaining
02.03 Using Older Frameworks with Multi-Targeting
DEFAULT

Ctrl+Shift+N (new project dialog box)

VISUAL BASIC 6

Ctrl+Shift+N (new project dialog box); Ctrl+N (new project)

VISUAL C# 2005

Ctrl+Shift+N (new project dialog box)

VISUAL C++ 2

Ctrl+Shift+N (new project dialog box)

VISUAL C++ 6

Ctrl+Shift+N (new project dialog box)

VISUAL STUDIO 6

Ctrl+N (new project dialog box)

WINDOWS

Alt,F, N, P (new project); Alt,F, D, N (add new project)

MENU

File | New Project; File | Add New Project

COMMAND

File.NewProject; File.AddNewProject

VERSIONS

2008, 2010

CODE

vstipProj0005

Even if you use an older version of the Microsoft .NET Framework, you can still use all the great features in Visual Studio 2008 and Visual Studio 2010 through multi-targeting.

When you create a new project, locate the drop-down list of supported .NET Framework versions and simply choose the one you prefer. You get to use most of the great features in the new IDE but still keep your older version of the .NET Framework. The following graphic shows the New Project dialog box in Visual Studio 2010.






02.03 Using Older Frameworks with Multi-Targeting
02.04 Create Web Application or Virtual Directory in IIS
02.05 Multiple Startup Projects
16h 55m remaining
02.04 Create Web Application or Virtual Directory in IIS
DEFAULT

Shift+Alt+N

VISUAL BASIC 6

Shift+Alt+N

VISUAL C# 2005

Shift+Alt+N

VISUAL C++ 2

Shift+Alt+N

VISUAL C++ 6

Shift+Alt+N

VISUAL STUDIO 6

Shift+Alt+N

WINDOWS

Alt,F, N, W

MENU

File | New Web Site

COMMAND

File.NewWebSite

VERSIONS

2008, 2010

CODE

vstipEnv0058

How can you create Web Applications and Virtual Directories in Internet Information Server from inside Visual Studio? Just select File | New Web Site, and click Browse in the lower-right corner.

In the Choose Location dialog box, select Local IIS, and pick the website in which you want to create the new item.


In the upper-right corner of the dialog box, notice the three buttons, as shown in the following illustration.


The button to the far left creates a new Web Application.


The middle button creates a new Virtual Directory.


You can pick whichever one you want to create, without ever leaving Visual Studio.





02.04 Create Web Application or Virtual Directory in IIS
02.05 Multiple Startup Projects
02.06 Change the Default New Project Location
16h 55m remaining
02.05 Multiple Startup Projects
DEFAULT

Alt+Enter (in Solution Explorer)

VISUAL BASIC 6

Alt+Enter (in Solution Explorer)

VISUAL C# 2005

Alt+Enter (in Solution Explorer)

VISUAL C++ 2

Alt+Enter (in Solution Explorer)

VISUAL C++ 6

Alt+Enter (in Solution Explorer)

VISUAL STUDIO 6

Alt+Enter (in Solution Explorer)

WINDOWS

Alt, P, P

MENU

Project | Properties [with Solution Selected in Solution Explorer]; [Right-Click the solution in Solution Explorer] | Properties

COMMAND

Project.Properties

VERSIONS

2005, 2008, 2010

LANGUAGES

C#, VB

CODE

vstipEnv0015

It’s common for developers to work with multiple projects. For example, consider a classic Client/Server scenario: One project includes all the elements shown here:


In this case, setting a single Startup Project isn’t sufficient; you want both these projects to start up when you press F5. Just click the solution in Solution Explorer, and then click the Properties button (Alt+Enter) at the top.


Make sure you are in the Common Properties | Startup Project area, and you should see a dialog box similar to the following.


Notice that, currently, Single Startup Project is selected, but that isn’t what you need. Instead, select Multiple Startup Projects.


Now you need to indicate which action each project should take when you press F5. Click the drop-down in the Action field.


As shown in the preceding illustration, you see the following choices:

None

Don’t start this project.

Start

Start with debugging.

Start without debugging

Start without attaching the debugger.

For this example, you would choose Start for both projects.


Now both projects start when you press F5. But there’s just one little problem: The Client project launches first, and you need the Server project to launch first. To set the launch order, use the buttons to the far right of the project list, as shown in the following illustration.


These buttons move the selected project up or down in the list so that you can arrange them to start in the order you would like. In this case, as shown in the following illustration, I’ve selected the Server project and then clicked the Move button to move it up in the startup order.


With the Server first in the list, you’re all set. When you press F5, you can see the server start and then the client.

One interesting side effect of setting multiple startup projects is that the bold project name you normally see in Solution Explorer isn’t there—because there is more than one startup project.





02.05 Multiple Startup Projects
02.06 Change the Default New Project Location
02.07 Track Active Item in Solution Explorer
16h 55m remaining
02.06 Change the Default New Project Location
WINDOWS

Alt,T, O

MENU

Tools | Options | Projects And Solutions | General

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipProj0006

You probably know that you can change the location for a new project in the New Project dialog box by entering a different location in the Location field.


But if you do this often, did you know that you can change the default location so that you don’t have to keep typing in custom paths? To change the default, select Tools | Options | Projects And Solutions | General from the menu bar. You’ll see an Options dialog box, shown below, where you can change several default paths to suit your needs.






02.06 Change the Default New Project Location
02.07 Track Active Item in Solution Explorer
02.08 Type-Ahead Selection Support in Solution Explorer
16h 55m remaining
02.07 Track Active Item in Solution Explorer
WINDOWS

Alt,T, O

MENU

Tools | Options | Projects and Solutions | General

COMMAND

View.TrackActivityinSolutionExplorer

VERSIONS

2005, 2008, 2010

CODE

vstipProj0011

By default, Visual Studio tracks the file you are currently editing in Solution Explorer. The Solution Explorer tool window highlights the current file.


As you switch between files in the editor, notice that Solution Explorer automatically highlights the file you’re currently editing. This is a great way to keep track of where you are in the solution when you are working with a lot of files.

If you don’t like the feature, you can turn it off. Just select Tools | Options | Projects And Solutions | General, and clear the Track Active Item In Solution Explorer check box shown in the following illustration.






02.07 Track Active Item in Solution Explorer
02.08 Type-Ahead Selection Support in Solution Explorer
02.09 Using Solution Folders
16h 55m remaining
02.08 Type-Ahead Selection Support in Solution Explorer
DEFAULT

Ctrl+Alt+L

VISUAL BASIC 6

Ctrl+R; Ctrl+Alt+L

VISUAL C# 2005

Ctrl+W, S; Ctrl+W, Ctrl+S; Ctrl+Alt+L

VISUAL C++ 2

Alt+0; Ctrl+Alt+L

VISUAL C++ 6

Ctrl+Alt+L

VISUAL STUDIO 6

Ctrl+Alt+J

WINDOWS

Alt,V, P

MENU

View | Solution Explorer

COMMAND

View.SolutionExplorer

VERSIONS

2005, 2008, 2010

CODE

vstipTool0010

Have you ever had a big list of files in Solution Explorer and wanted to jump to a specific file very quickly? Just click anywhere in Solution Explorer, and start typing the name of the file you want. For example, suppose you have a solution with multiple projects:


Assume you need to find a file called SeriousCoolness. To find it, click in Solution Explorer and then just start typing the name. Solution Explorer finds the file for you as you type.


What if you don’t know the whole name—just that it starts with an “S”? No worries! Just type S several times, and the selection cycles though all the files that begin with that letter.

NOTE
The type-ahead feature works only with items that have been expanded, so if you have collapsed folders or projects in Solution Explorer, the tool cannot search within those areas.





02.08 Type-Ahead Selection Support in Solution Explorer
02.09 Using Solution Folders
02.10 Navigating Property Tabs in the Project Properties
16h 55m remaining
02.09 Using Solution Folders
WINDOWS

(with Solution selected) Alt,P, D

MENU

(with Solution selected) Project | Add New Solution Folder; [Right-Click Solution] | Add | New Solution Folder

COMMAND

(with Solution selected) Project.AddNewSolutionFolder

VERSIONS

2005, 2008, 2010

CODE

vstipProj0009

Did you know that Visual Studio provides special folders that can help you organize large solutions? They are called, appropriately enough, “Solution Folders.”

NOTE
Solution Folders are an organizational tool in Solution Explorer; creating one doesn’t create a corresponding Windows file system folder. Microsoft recommends that you organize your projects on disk in the same way that you organize them in the Solution Folder. But of course, you’re free to organize them as you like.

Adding Solution Folders
To create a Solution Folder, right-click your solution (or, with the solution selected, go to Project | Add New Solution Folder). Solution Explorer adds a new folder, which you can type a name for.


After you enter a name for the new folder, press Enter, and you’re done. So what can you actually do with these things? It turns out, quite a lot:

Move or add projects to them. Solution Folders can be nested to create greater organizational structure.

Add, delete, or rename Solution Folders at any time, if the organizational requirements of your solution change.

Unload all projects in a Solution Folder to make them temporarily unavailable for building.

Collapse or hide entire Solution Folders so that you can work more easily in Solution Explorer. Hidden projects are built when you build the solution.

Build or rebuild all the projects. The projects are built in the order specified by the project dependencies.

Removing Solution Folders
If you want to get rid of a folder, just right-click it and choose Remove to delete it, or alternatively, select it and press the Delete key.






02.09 Using Solution Folders
02.10 Navigating Property Tabs in the Project Properties
02.11 Pin a Project to the Recent Projects List
16h 55m remaining
02.10 Navigating Property Tabs in the Project Properties
DEFAULT

Ctrl+PgUp; Ctrl+PgDn

VISUAL BASIC 6

Ctrl+PgUp; Ctrl+PgDn

VISUAL C# 2005

Ctrl+PgUp; Ctrl+PgDn

VISUAL C++ 2

Ctrl+PgUp; Ctrl+PgDn

VISUAL C++ 6

Ctrl+PgUp; Ctrl+PgDn

VISUAL STUDIO 6

Ctrl+PgUp; Ctrl+PgDn

WINDOWS

[no shortcut]

COMMAND

Window.PreviousTab; Window.NextTab

VERSIONS

2005, 2008, 2010

CODE

vstipProj0023

When you are looking at your project’s properties, you might have wondered whether you can navigate among the property tabs by using the keyboard.

It turns out that you can. Just use Ctrl+PgUp or Ctrl+PgDn to move between the property tabs. This also works for properties in C++ projects if you want to quickly navigate among the categories.






02.10 Navigating Property Tabs in the Project Properties
02.11 Pin a Project to the Recent Projects List
02.12 Creating Temporary Projects
16h 55m remaining
02.11 Pin a Project to the Recent Projects List
VERSIONS

2010

CODE

vstipTool0003

Tired of your projects getting pushed out of the Recent Projects list on the Start Page? You can pin projects to the Recent Projects list in Visual Studio 2010 so that they stay around until you unpin them.


Pinned projects do not stay at the top of the list; instead, they’re sorted according to when you use them. In other words, the most recent project is on top—pinned or not. Pinning guarantees only that the project will not be pushed out of the list.





02.11 Pin a Project to the Recent Projects List
02.12 Creating Temporary Projects
02.13 Create Your Own Item Template
16h 35m remaining
02.12 Creating Temporary Projects
WINDOWS

Alt,T, O

MENU

Tools | Options | Projects and Solutions | General

COMMAND

Tools.Options

VERSIONS

2005, 2008, 2010

CODE

vstipProj0010

Temporary projects are particularly useful for showing a colleague some trick or technique quickly, or for performing ad hoc demos. To create temporary projects, select Tools | Options | Projects And Solutions | General and clear the Save New Projects When Created check box, as shown in the following illustration.


While convenient, the option has some side effects. For example, when you subsequently create a new project, the New Project dialog box does not show the usual “save” fields at the bottom of the dialog box.

Before:


After:


The good news is that now you can create projects all day long but can choose to either save or discard the changes when the solution is closed.


NOTE
You can still save changes to a project—even a temporary project—anytime you like if you decide you want to keep the code around. When you decide to save, your AutoRecover settings take over. For more information, see vstipEnv0019 (01.05 AutoRecover, page 10).





02.12 Creating Temporary Projects
02.13 Create Your Own Item Template
02.14 Roll Your Own Project Template with the Export Template Wizard
16h 35m remaining
02.13 Create Your Own Item Template
WINDOWS

Alt,F, E

MENU

File | Export Template

COMMAND

File.ExportTemplate

VERSIONS

2005, 2008, 2010

LANGUAGES

C#, VB

CODE

vstipProj0013

Have you ever used or created a template in Microsoft Word, Excel, or PowerPoint? Unless you live in a cave, the answer is most likely “yes.” Just as with the Microsoft Office products, you can create and use your own templates in Visual Studio. This tip shows you how to make your own item template. Sometimes you just want to customize an individual item that you use frequently in projects. Class files are a perfect example of this type of scenario. Here’s an example.

Create a new project, and then add a class to it (Ctrl+Shift+A).

NOTE
The process is the same regardless of which language you’re using.


Now modify the class code so that it looks the way you would like your item template to look, and save your changes to the file.


At this point, you can export the item template so that you can use it in future projects. Select File | Export Template to start the Export Template Wizard.

NOTE
You are prompted to save changes to your project if you haven’t already done so.


Select Item Template, and select the project that currently contains the item you want to export (if you have more than one project in your solution).


Click Next and then select the item to export as a template.

NOTE
The wizard automatically selects any dependent files as needed based on your selection. Also, even though it looks like you can select more than one item here, you can only select a single item in this list.


Click Next again. Now you can select any references that you want included with the item. If you have any Using or Imports statements, you need to pick the references here or the template will not work correctly.

NOTE
The wizard generates this list of assemblies from the assembly references in the current project. If the assembly you want to reference does not appear in the list, exit the wizard and add the reference to your project, and then run the wizard again.


Click Next. As you can see from the following illustration, you can add quite a bit of information.


Here’s a description of the information you can add:

Template Name The friendly name for the template that Visual Studio displays in the list of templates. I suggest keeping this to around 50–60 characters. Don’t get too verbose here.

Template Description A short description that provides a little more detail about the template’s purpose. In this text box, I want you to get very descriptive. This is your one and only chance to make it perfectly clear what this template should be used for, so don’t skimp on detail.

Icon Image A small image that represents the icon for the item. I suggest you just leave this blank.

Preview Image A larger image that provides a preview of what the template looks like. As with the Icon Image field, I suggest you leave this blank.

Output Location The location where the wizard stores exported items. This is the initial storage location of your templates. To be clear, they are not usable in Visual Studio when they are just created. To make them useable in Visual Studio, you need to check Automatically Import The Template Into Visual Studio. Leave this as-is unless you are storing your templates on a network share somewhere. If you do change this value, make sure you use the new location consistently when you create templates or you will wind up forgetting where you put them.

Automatically Import The Template Into Visual Studio Lets you decide whether you want to import the template right away or want to do it manually later. This “import” is just a copy of the .zip file created in the appropriate location in My Documents\Visual Studio <version>\Templates\ItemTemplates. By doing this, the template immediately becomes usable in Visual Studio.

Display An Explorer Window On The Output Files Folder Opens up the location where the template files are stored after they are created. This is useful when you want to see the .zip file that is created. It’s interesting the first few times you do it, but then it’s pretty much a waste of time. You will wind up turning off this option most of the time.

The following illustration shows the settings I used for this example.


To complete the wizard, click Finish. The wizard closes and opens up the output file location, showing the .zip file that contains the exported templates.


Although you aren’t interested in the details right now, if you explore inside the .zip file, you can see the files that make up an item template.


Finally, test your new template. Create a new item (Ctrl+Shift+A), and you should see the new template. Notice the Icon Image next to the name of the item and the Preview Image (the Visual Studio 2010 logo in the lower-right) that is below the description. I feel that the names and descriptions are critical but really don’t see a lot of value in the icons.


You can also see the template in the My Documents\Visual Studio <version>\Templates\ItemTemplates\ folder.


If you aren’t happy with your new template, just delete the .zip file from this directory; it no longer shows up in the Add New Item dialog box.





02.13 Create Your Own Item Template
02.14 Roll Your Own Project Template with the Export Template Wizard
02.15 Organizing Your Custom Item Templates
16h 35m remaining
02.14 Roll Your Own Project Template with the Export Template Wizard
WINDOWS

Alt,F, E

MENU

File | Export Template

COMMAND

File.ExportTemplate

VERSIONS

2005, 2008, 2010

CODE

vstipProj0004

Are you always adding the same extra files to projects when you create them? Ever wish you could have it all just “be there”? Well, you can when you become familiar with the Export Template Wizard.

First, set up an existing project template the way you want it. All changes (new files, code, interfaces, and so on) will be used in the template you create. In this simple example, I always want to include larry, curly, and moe C# class files with my console applications.


Now select File | Export Template from the menu bar.

NOTE
Choosing Export Template prompts you to save any pending changes if you haven’t already.

You’ll see the Export Template Wizard. From this first screen, you can choose to make either a Project template or an Item template.


For this example, I selected Project Template and then clicked Next to continue to the Select Template Options screen, shown in the following illustration.


The following list provides a brief description of each option:

Template Name The friendly name for the template that Visual Studio displays in the list of templates. I suggest keeping this to around 50–60 characters. Don’t get too verbose here.

Template Description A more complete explanation of how this template is intended to be used. This is your one and only opportunity for you to be very clear on the proper usage for this template.

Icon Image and Preview Image The images used with the template name (icon image) and just below the description (preview image). I suggest you don’t bother setting these because they don’t have much use, in my opinion.

Output Location The location where the wizard saves the .zip file that it creates. The default value is usually what you will stick with unless you have, say, a network share where you want your templates to stored.

Automatically Import The Template Into Visual Studio Controls whether the wizard puts a copy of the new template to your templates directory: My Documents\Visual Studio <version>\Templates\ProjectTemplates. If you want the template to be available the next time you create a new project, select this option. Most of the time you should leave this option selected.

Display An Explorer Window On The Output Files Folder Controls what happens when you complete the wizard. When selected, it displays the folder containing the .zip file that the wizard saves. After the first few times you create templates, this option can get tiresome, so I usually turn it off. I suggest you leave it on the first few times you create templates to see the template that is created.

After filling out the wizard and clicking Finish, the wizard closes and opens up my Exported Templates (output) folder, where I can see the new .zip file containing the template files.


Now, when I create a new application, the new template appears, visible in the New Project dialog box.


Obviously, this is a simple example; you can do a lot more with templates, and I suggest you visit the “Export Template Wizard” documentation, at http://msdn.microsoft.com/en-us/library/ms185318.aspx, for more detailed information about how to make good use of this feature.





02.14 Roll Your Own Project Template with the Export Template Wizard
02.15 Organizing Your Custom Item Templates
02.16 Organizing Your Custom Project Templates
16h 35m remaining
02.15 Organizing Your Custom Item Templates
VERSIONS

2005, 2008, 2010

CODE

vstipProj0020

In vstipProj0013 (02.14 Roll Your Own Project Template with the Export Template Wizard, page 57), I showed you how to create custom item templates but didn’t show you how to organize them.

Fortunately, organizing them is pretty easy. After you have created your template(s), navigate to the folder My Documents\Visual Studio <version>\Templates\ItemTemplates. For example, on my machine, the path is My Documents\Visual Studio 2010\Templates\ItemTemplates.


As you can see in the preceding illustration, I have a custom item—a class called “Really Cool Regex Class.” Unfortunately, when I want to use it and I bring up the Add New Item (Ctrl+Shift+A) dialog box, that class shows up in the root list.


I want it to show up in the Code area, but it doesn’t.


To get the custom template to show up in the Code area, you need to go back to the ItemTemplates directory and create a new folder named Code.


Then move the custom template into the Code folder.


Now whenever I press Ctrl+Shift+A to add a new item, my custom template appears in the Code section.


In addition to working with existing folder names, you can create custom names as well. If, for example, you wanted an XYZ Company folder for your templates you would just create one and put your templates in there:


Now, when you go to add a new item, you will see your new folder in the dialog box:






02.15 Organizing Your Custom Item Templates
02.16 Organizing Your Custom Project Templates
02.17 Reorganize the Default Item Templates
16h 35m remaining
02.16 Organizing Your Custom Project Templates
VERSIONS

2005, 2008, 2010

CODE

vstipProj0019

In vstipProj0004 (02.14 Roll Your Own Project Template with the Export Template Wizard, page 64), we discussed how to create custom project templates, but it doesn’t show you how to organize them. Fortunately, that’s pretty easy. After you have created one or more custom project templates, browse to My Documents\Visual Studio <version>\Templates\ProjectTemplates. For example, on my machine, the full path is My Documents\Visual Studio 2010\Templates\ProjectTemplates.


As the preceding illustration shows, I created a custom Console application project type for this example with the name ConsoleApplication1. By default, custom project templates don’t show up in the project subfolders.


To get the custom templates to appear, the trick is to create a new folder in that directory with a name that matches where you want the template(s) to show up. You place custom templates in this new folder—and then they show up in the appropriate areas.

To do this, return to the My Documents\Visual Studio <version>\Templates\ProjectTemplates directory and create a new folder called Windows—to match the Windows area in the New Project dialog box, which is where we want the new Console template to appear.


Move your template into the new folder. For this example, I moved ConsoleApplication1.zip into the Windows folder.


The next time you open up the New Project dialog box (Ctrl+Shift+N), it shows the project template in the proper area.


In addition to matching the existing folder names, you can create new ones. If you want a custom area for your company templates, for example, you would just create a folder with your company name and put at least one template in the folder:


The next time you bring up the New Project dialog box, it will show your new subfolder in the list:






02.16 Organizing Your Custom Project Templates
02.17 Reorganize the Default Item Templates
02.18 Reorganize the Default Project Templates
16h 35m remaining
02.17 Reorganize the Default Item Templates
VERSIONS

2005, 2008, 2010

CODE

vstipProj0021

WARNING
The procedures in this tip could cause your templates to disappear if you don’t follow the instructions carefully. So do this at your own risk. You might want to back up your ItemTemplates folder just to be safe.

You’ve probably noticed that General section of the New Item dialog box contains a large number of items. If you want to organize those a bit more, this tip shows you how to create custom areas in which you can store the default item templates that ship with Visual Studio. This example creates a Diagram area for the diagram items that—by default—appear in the General section.


To get started, find where Visual Studio stores item templates on your machine. Typically, this is in C:\Program Files\Microsoft Visual Studio <version>\Common7\IDE\ItemTemplates\<language>. You might have to drill down into the file structure, depending on what items you’re looking for, and the path might be slightly different on your machine, based on your Visual Studio version. In this case, the actual full path on my machine is C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\ItemTemplates\CSharp.


When you’ve found the template location for your language, create a new folder. For this example, I created a folder called Diagrams.


Now go into the General\1033 folder, and locate the diagram .zip files you want, as shown in the following illustration.


Now carefully move them to the new Diagrams folder.


Close all instances of Visual Studio, and then run the following command from the Visual Studio command prompt (must be run with administrative privileges):

devenv.com /installvstemplates


WARNING
Let this process complete without interfering. It is extremely important that you let the process finish. The devenv.com command runs without any user interface. You know it is done when another cursor shows up:


When the process completes, open up Visual Studio, and then open any project. Bring up the Add New Item dialog box (Ctrl+Shift+A). Notice your brand new Diagrams area, with the templates you moved there inside it.






02.17 Reorganize the Default Item Templates
02.18 Reorganize the Default Project Templates
02.19 Change the Templates that Appear in the New Project or Item Dialog Boxes
16h 35m remaining
02.18 Reorganize the Default Project Templates
VERSIONS

2005, 2008, 2010

CODE

vstipProj0018

WARNING
The procedures in this tip could cause some of your templates to disappear unless you follow the instructions carefully. So do this at your own risk. You might want to back up your ProjectTemplates folder just to be safe.

Maybe it’s just me, but I get really annoyed that, for example, my WCF project templates are in a WCF section when I go to create a new project—but my WPF projects are under “Windows.” That just doesn’t seem intuitive. So this example shows you how you can create custom areas for the default project templates that ship with Visual Studio. In this example, you create a WPF area for your WPF project templates.

You need to find the location where your version of Visual Studio stores project templates. Typically, that’s in C:\Program Files\Microsoft Visual Studio <version>\Common7\IDE\ProjectTemplates\<language>. You might need to explore the file system to find the templates, and your path might be slightly different, based on which Visual Studio version you’re running. For example, the actual full path on my machine for C# templates is C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\ProjectTemplates\CSharp.


Now create a new folder, and name it “WPF.”


These next steps are potentially dangerous, so be careful. Navigate to the Windows folder (actually Windows\1033\), and locate the WPF templates.


Move these .zip files into the new folder you just created.


Close all instances of Visual Studio, and then run the following command from the Visual Studio command prompt, which you can find on your Start menu:

devenv.com /installvstemplates

WARNING
It is very important that you let this process finish without interruption. The devenv.com command runs without any user interface. You know it is done when the command prompt shows up again:


When the process completes, open up Visual Studio, and open the New Project dialog box (Ctrl+Shift+N) to see your brand-new WPF area containing the WPF templates, as shown in the following illustration.


NOTE
While researching how to do this, I experimented with copying the templates instead of moving them. However, Visual Studio apparently detects duplicate template names and doesn’t allow you to have multiple copies in different locations. So I wound up with an empty WPF section; the templates stayed in their original Windows section. I suspect this is dependent on load order—and my tests indicate Visual Studio loads the known default directories first, so having a folder called “Abacus” to beat the sort order doesn’t work.





02.18 Reorganize the Default Project Templates
02.19 Change the Templates that Appear in the New Project or Item Dialog Boxes
3. Getting to Know the Environment
16h 35m remaining
02.19 Change the Templates that Appear in the New Project or Item Dialog Boxes
VERSIONS

2008, 2010

CODE

vstipProj0017

WARNING
Manipulating templates as discussed here can cause serious problems if you don’t know what you are doing. Use this information at your own risk. You should consider backing up your ProjectTemplates or ItemTemplates folders.

With all the great changes to the New Project and New Item dialog boxes, you might be perfectly happy with the list of things that Visual Studio presents by default. But for argument’s sake, suppose you want to get rid of some of the entries. This example removes the C# Windows Forms Control Library from the New Project dialog box (Ctrl+Shift+N), but you can follow the same steps to remove or change items in the New Item dialog box.


Navigate to the location where your version of Visual Studio stores templates for your selected language. Typically, that’s C:\Program Files\Microsoft Visual Studio <version>\Common7\IDE\<Project or Item>Templates\<language>\<project category>. You might have to explore a little; your path might be slightly different, based on which Visual Studio version you’re running. On my machine, the path to the Windows Forms Control Library .zip file is C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\ProjectTemplates\CSharp\Windows.


You don’t want to simply delete the file—you might need it in the future. Instead, just move the .zip file to another directory. That way, you can always retrieve it from that location if you need it again.

Close all instances of Visual Studio, and then run the following command from the Visual Studio command prompt, which you can find on your Start menu:

devenv.com /installvstemplates

WARNING
It is very important that you let this process finish without interruption. The devenv.com command runs without any user interface. You know it is done when the cursor shows up again:


After the process completes, start Visual Studio again, and then create a new project (Ctrl+Shift+N). You should see that the moved template is no longer in the list.






02.19 Change the Templates that Appear in the New Project or Item Dialog Boxes
