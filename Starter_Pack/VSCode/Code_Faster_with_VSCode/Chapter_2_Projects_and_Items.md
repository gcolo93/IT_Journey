**02.01 Search for Project Templates in the New Project Dialog Box**

In Visual Studio, you can search for project templates directly within the New Project dialog box. Here are the shortcuts and steps for various versions:

- **Default**
  - Shortcut: Ctrl+Shift+N (to open new project dialog); Ctrl+E (to activate search box)

- **Visual Basic 6**
  - Shortcut: Ctrl+Shift+N (to open new project dialog); Ctrl+N (to create a new project); Ctrl+E (to activate search box)

- **Visual C# 2005**
  - Shortcut: Ctrl+Shift+N (to open new project dialog); Ctrl+E (to activate search box)

- **Visual C++ 2**
  - Shortcut: Ctrl+Shift+N (to open new project dialog); Ctrl+E (to activate search box)

- **Visual C++ 6**
  - Shortcut: Ctrl+Shift+N (to open new project dialog); Ctrl+E (to activate search box)

- **Visual Studio 6**
  - Shortcut: Ctrl+N (to open new project dialog); Ctrl+E (to activate search box)

- **Windows**
  - Shortcut: Alt+F, N, P (to open new project dialog); Alt+F, D, N (to add new project)

- **Menu**
  - Commands: File | New Project; File | Add New Project

This functionality allows you to quickly find templates by typing keywords into the search box. While it doesn't support advanced search options like Boolean searches or regular expressions, you can filter results by typing in language abbreviations (e.g., C#, VB, F#, or C++).

**02.02 Recent Project Templates in the New Project Dialog Box**

In Visual Studio 2010, accessing recent project templates is made simple. Here's how to do it:

- **Default**
  - Shortcut: Ctrl+Shift+N (opens new project dialog box)

- **Visual Basic 6**
  - Shortcut: Ctrl+Shift+N (opens new project dialog box); Ctrl+N (creates a new project)

- **Visual C# 2005**
  - Shortcut: Ctrl+Shift+N (opens new project dialog box)

- **Visual C++ 2**
  - Shortcut: Ctrl+Shift+N (opens new project dialog box)

- **Visual C++ 6**
  - Shortcut: Ctrl+Shift+N (opens new project dialog box)

- **Visual Studio 6**
  - Shortcut: Ctrl+N (opens new project dialog box)

- **Windows**
  - Shortcut: Alt+F, N, P (opens new project); Alt+F, D, N (adds new project)

- **Menu**
  - Commands: File | New Project; File | Add New Project

When you open the New Project dialog box in Visual Studio 2010, you'll notice a section labeled "Recent Templates." This section displays a list of the five most recently used project templates. Simply click on "Recent Templates" to view and access these templates quickly.

**02.03 Using Older Frameworks with Multi-Targeting**

In Visual Studio 2008 and 2010, you can utilize older versions of the .NET Framework while still leveraging the latest IDE features through multi-targeting. Here's how:

- **Default**
  - Shortcut: Ctrl+Shift+N (opens new project dialog box)

- **Visual Basic 6**
  - Shortcut: Ctrl+Shift+N (opens new project dialog box); Ctrl+N (creates a new project)

- **Visual C# 2005**
  - Shortcut: Ctrl+Shift+N (opens new project dialog box)

- **Visual C++ 2**
  - Shortcut: Ctrl+Shift+N (opens new project dialog box)

- **Visual C++ 6**
  - Shortcut: Ctrl+Shift+N (opens new project dialog box)

- **Visual Studio 6**
  - Shortcut: Ctrl+N (opens new project dialog box)

- **Windows**
  - Shortcut: Alt+F, N, P (opens new project); Alt+F, D, N (adds new project)

- **Menu**
  - Commands: File | New Project; File | Add New Project

By accessing the drop-down list of supported .NET Framework versions when creating a new project, you can select the desired framework version. This allows you to enjoy the enhanced features of the new IDE while continuing to work with older versions of the .NET Framework. See the New Project dialog box in Visual Studio 2010 for reference.

**02.04 Create Web Application or Virtual Directory in IIS**

To create Web Applications and Virtual Directories in Internet Information Server (IIS) directly from Visual Studio, follow these steps:

- **Default**
  - Shortcut: Shift+Alt+N

- **Visual Basic 6**
  - Shortcut: Shift+Alt+N

- **Visual C# 2005**
  - Shortcut: Shift+Alt+N

- **Visual C++ 2**
  - Shortcut: Shift+Alt+N

- **Visual C++ 6**
  - Shortcut: Shift+Alt+N

- **Visual Studio 6**
  - Shortcut: Shift+Alt+N

- **Windows**
  - Shortcut: Alt+F, N, W (opens the File menu, then selects New Web Site)

- **Menu**
  - Commands: File | New Web Site

By selecting File | New Web Site from the menu, and clicking Browse in the lower-right corner, you can access the Choose Location dialog box.

In the Choose Location dialog box:
- Select Local IIS.
- Choose the website in which you want to create the new item.

In the upper-right corner of the dialog box, you'll notice three buttons:
- The button to the far left creates a new Web Application.
- The middle button creates a new Virtual Directory.
- The button to the far right cancels the operation.

You can pick whichever option you want to create without ever leaving Visual Studio.

**02.05 Multiple Startup Projects**

When working on projects involving multiple components, such as a client-server scenario, it's common to need both projects to start up simultaneously. Here's how to set up multiple startup projects in Visual Studio:

- **Default**
  - Shortcut: Alt+Enter (in Solution Explorer)

- **Visual Basic 6**
  - Shortcut: Alt+Enter (in Solution Explorer)

- **Visual C# 2005**
  - Shortcut: Alt+Enter (in Solution Explorer)

- **Visual C++ 2**
  - Shortcut: Alt+Enter (in Solution Explorer)

- **Visual C++ 6**
  - Shortcut: Alt+Enter (in Solution Explorer)

- **Visual Studio 6**
  - Shortcut: Alt+Enter (in Solution Explorer)

- **Windows**
  - Shortcut: Alt, P, P (opens Project Properties with the solution selected in Solution Explorer)

- **Menu**
  - Commands: Project | Properties [with Solution Selected in Solution Explorer]; [Right-Click the solution in Solution Explorer] | Properties

To set up multiple startup projects:
1. Click on the solution in Solution Explorer.
2. Press Alt+Enter or navigate to Project Properties using the menu.
3. Ensure you are in the Common Properties | Startup Project area.
4. Select Multiple Startup Projects instead of Single Startup Project.
5. Choose the desired action for each project when pressing F5 (Start, Start with debugging, or Start without debugging).
6. Adjust the startup order by using the Move buttons to arrange the projects.
   - Click the project to select it, then click the Move button to move it up or down in the startup order list.
7. Confirm the changes.

Now, when you press F5, both projects will start up according to the specified actions and order. Keep in mind that when using multiple startup projects, the bold project name normally seen in Solution Explorer won't be present since there are more than one startup project.

**02.06 Change the Default New Project Location**

When working in Visual Studio, you can streamline your workflow by customizing the default location for new projects. Here's how:

- **Windows**
  - Shortcut: Alt,T, O (opens Tools | Options)

- **Menu**
  - Tools | Options | Projects And Solutions | General

- **Command**
  - Tools.Options

- **Versions**
  - 2005, 2008, 2010

- **Code**
  - vstipProj0006

To change the default location for new projects:
1. Access the Options dialog by either clicking Tools > Options or using the shortcut Alt,T,O.
2. In the Options dialog, navigate to Projects And Solutions > General.
3. Locate the setting for Default location for new projects.
4. Enter the desired path or use the Browse button to select a folder.
5. Click OK to save your changes and close the Options dialog.

By setting a default location, you eliminate the need to repeatedly enter custom paths every time you create a new project. This simple customization can significantly improve your efficiency when working with Visual Studio.

**02.07 Track Active Item in Solution Explorer**

In Visual Studio, the Solution Explorer tool window can automatically highlight the file you are currently editing. This feature, known as "Track Active Item in Solution Explorer," helps you stay organized and easily navigate your project. Here's how to manage this feature:

- **Windows**
  - Shortcut: Alt,T, O (opens Tools | Options)

- **Menu**
  - Tools | Options | Projects and Solutions | General

- **Command**
  - View.TrackActivityinSolutionExplorer

- **Versions**
  - 2005, 2008, 2010

- **Code**
  - vstipProj0011

By default, Visual Studio enables this feature. As you switch between files in the editor, Solution Explorer automatically highlights the corresponding file, providing visual feedback on your current location within the solution.

If you prefer to disable this feature:
1. Access the Options dialog by either clicking Tools > Options or using the shortcut Alt,T,O.
2. In the Options dialog, navigate to Projects And Solutions > General.
3. Find the option labeled "Track Active Item In Solution Explorer."
4. Uncheck the corresponding checkbox to disable the feature.
5. Click OK to save your changes and close the Options dialog.

Disabling this feature can be useful if you find the automatic highlighting distracting or unnecessary for your workflow. Adjusting these settings allows you to personalize your Visual Studio experience to suit your preferences.

**02.08 Type-Ahead Selection Support in Solution Explorer**

Navigating through a large list of files in Solution Explorer can be time-consuming, but Visual Studio offers a convenient feature called "Type-Ahead Selection" to help you find files quickly. Here's how to use it effectively:

- **Default Shortcut**: Ctrl+Alt+L

- **Versions**: 2005, 2008, 2010

- **Menu**: View | Solution Explorer (Alt,V, P)

- **Command**: View.SolutionExplorer

- **Code**: vstipTool0010

**Usage:**
1. **Click anywhere in Solution Explorer**: This activates the type-ahead feature.

2. **Start typing the name of the file**: For example, if you're looking for a file named "SeriousCoolness," just begin typing "SeriousCoolness" in Solution Explorer.

3. **Dynamic Filtering**: As you type, Solution Explorer dynamically filters the files, narrowing down the list to match what you've typed so far.

4. **Partial Matching**: If you're unsure of the full name but know a part of it (e.g., the file starts with "S"), you can type the partial name. Solution Explorer cycles through all files that match the entered characters.

**Note:**
- This feature only works with expanded items in Solution Explorer. If folders or projects are collapsed, the tool won't search within them.
- Each Visual Studio language (Visual Basic, Visual C#, Visual C++ 2, Visual C++ 6, Visual Studio 6) may have its own specific keyboard shortcuts for activating the type-ahead feature. Check the list above for language-specific shortcuts.
- Utilizing this feature can significantly improve your productivity when working with large solutions containing numerous files.

**02.09 Using Solution Folders**

Solution Folders are a powerful organizational tool in Visual Studio's Solution Explorer. They help manage large solutions efficiently. Here's how to utilize them effectively:

- **Shortcut**: (with Solution selected) Alt,P, D
- **Menu**: (with Solution selected) Project | Add New Solution Folder; [Right-Click Solution] | Add | New Solution Folder
- **Command**: (with Solution selected) Project.AddNewSolutionFolder
- **Versions**: 2005, 2008, 2010
- **Code**: vstipProj0009

**Adding Solution Folders:**
1. **Creation**: Right-click your solution in Solution Explorer or select the solution and go to Project | Add New Solution Folder. This action adds a new folder, allowing you to name it.
2. **Naming**: Enter a descriptive name for the new folder and press Enter to confirm.

**Functionality:**
- **Organization**: Solution Folders help organize projects within the solution. They don't correspond to physical folders in the file system.
- **Manipulation**: You can move or add projects to Solution Folders. They can also be nested for better organizational structure.
- **Flexibility**: Solution Folders can be added, deleted, or renamed at any time to adapt to changing organizational requirements.
- **Management**: You can unload all projects within a Solution Folder temporarily, making them unavailable for building.
- **Visibility**: Collapse or hide Solution Folders to streamline the view in Solution Explorer. Hidden projects are still built when the solution is built.
- **Build Control**: Build or rebuild all projects within Solution Folders. Projects are built according to their specified dependencies.

**Removing Solution Folders:**
- **Deletion**: Right-click the Solution Folder and choose Remove to delete it. Alternatively, select it and press the Delete key.

Utilizing Solution Folders effectively can enhance the organization and management of large solutions, improving overall productivity in Visual Studio.

**02.10 Navigating Property Tabs in the Project Properties**

Navigating property tabs in Visual Studio's project properties can be done efficiently using keyboard shortcuts. Here's how:

- **Default Shortcut**: Ctrl+PgUp; Ctrl+PgDn
- **Visual Basic 6**: Ctrl+PgUp; Ctrl+PgDn
- **Visual C# 2005**: Ctrl+PgUp; Ctrl+PgDn
- **Visual C++ 2**: Ctrl+PgUp; Ctrl+PgDn
- **Visual C++ 6**: Ctrl+PgUp; Ctrl+PgDn
- **Visual Studio 6**: Ctrl+PgUp; Ctrl+PgDn
- **Windows**: [No shortcut]
- **Command**: Window.PreviousTab; Window.NextTab
- **Versions**: 2005, 2008, 2010
- **Code**: vstipProj0023

When viewing your project's properties, you can easily navigate among the property tabs using these keyboard shortcuts. Press Ctrl+PgUp to move to the previous tab and Ctrl+PgDn to move to the next tab. This functionality simplifies navigation and is particularly useful for quickly switching between property categories, even in C++ projects.

**02.11 Pin a Project to the Recent Projects List**

In Visual Studio 2010, you can ensure that specific projects remain in the Recent Projects list on the Start Page by pinning them. Here's how:

- **Versions**: 2010
- **Code**: vstipTool0003

Tired of your projects disappearing from the Recent Projects list on the Start Page? Pinning projects allows them to remain in the list until you choose to unpin them.

- Pinned projects are not fixed at the top of the list; instead, they are sorted based on usage. The most recently accessed project, whether pinned or not, appears at the top. Pinning only ensures that the project remains in the list, preventing it from being pushed out.

**02.12 Creating Temporary Projects**

Temporary projects serve as quick demonstrations or ad hoc demos, allowing you to showcase techniques or tricks swiftly. Here's how to create them:

- **Windows Shortcut**: Alt,T, O
- **Menu Path**: Tools | Options | Projects and Solutions | General
- **Command**: Tools.Options
- **Versions**: 2005, 2008, 2010
- **Code**: vstipProj0010

To create temporary projects, follow these steps:

1. Go to Tools | Options | Projects And Solutions | General.
2. Clear the "Save New Projects When Created" checkbox.

Once enabled, this option has some implications. For instance, the New Project dialog box will no longer display the typical "save" fields at the bottom.

Before enabling:

After enabling:

However, this setting grants you the flexibility to create projects without immediately committing to saving them. You can decide whether to save or discard changes when closing the solution.

**Note**: Even for temporary projects, you can save changes anytime you prefer, with AutoRecover settings coming into play. Refer to vstipEnv0019 (01.05 AutoRecover) for more details.

**02.13 Create Your Own Item Template**

Ever used or created templates in Microsoft Word, Excel, or PowerPoint? Just like in those applications, you can create and utilize your own templates in Visual Studio. This tip guides you through making your own item template, which is handy for customizing frequently used items like class files.

**Instructions**:

1. Create a new project and add a class to it (Ctrl+Shift+A).
   - *Note*: The process remains the same irrespective of the programming language you're using.

2. Modify the class code to your desired template format and save your changes.

3. Export the item template for future use:
   - Select File | Export Template to launch the Export Template Wizard.
   - Choose "Item Template" and select the project containing the item to export.
   - Select the item to export as a template.

4. Choose any necessary references to include with the item.

5. Add information about the template:
   - Template Name: A concise name for the template.
   - Template Description: A detailed description of the template's purpose.
   - Icon Image: Leave this blank.
   - Preview Image: Also leave this blank.
   - Output Location: The initial storage location of your templates.
   - Automatically Import The Template Into Visual Studio: Decide whether to import the template right away or manually later.
   - Display An Explorer Window On The Output Files Folder: Option to open the location where the template files are stored after creation.

6. Complete the wizard by clicking Finish. The output file location will open, showing the .zip file containing the exported templates.

7. Test your new template by creating a new item (Ctrl+Shift+A). You should see the new template with its associated icon image, description, and preview image.

8. Your template will also appear in the My Documents\Visual Studio <version>\Templates\ItemTemplates\ folder.

9. If you're unhappy with the template, simply delete the .zip file from the directory; it will no longer show up in the Add New Item dialog box.

**02.14 Roll Your Own Project Template with the Export Template Wizard**

Are you tired of adding the same extra files to projects every time you create them? With the Export Template Wizard, you can have everything ready to go with just a few clicks.

**Instructions**:

1. Set up an existing project template the way you want it, including any desired changes (new files, code, interfaces, etc.).

2. Select File | Export Template from the menu bar. This action prompts you to save any pending changes if you haven't already.

3. In the Export Template Wizard, choose whether to create a Project template or an Item template.

4. Provide details for your template:
   - Template Name: A concise name for the template.
   - Template Description: A clear explanation of how the template should be used.
   - Icon Image and Preview Image: Optional images for the template name and description.
   - Output Location: The location where the wizard saves the .zip file containing the template.
   - Automatically Import The Template Into Visual Studio: Decide whether to import the template into Visual Studio immediately.
   - Display An Explorer Window On The Output Files Folder: Choose whether to display the folder containing the .zip file after completion.

5. After filling out the wizard and clicking Finish, the wizard closes, and you'll see the new .zip file containing the template files.

6. The new template will be available in the New Project dialog box when creating a new application.

This example is straightforward, but templates offer much more functionality. For further details and advanced usage, refer to the Export Template Wizard documentation on the Microsoft Developer Network (MSDN) website.

**02.15 Organizing Your Custom Item Templates**

After creating custom item templates using the method described in vstipProj0013, organizing them is straightforward. Here's how to do it:

1. **Locate the ItemTemplates Folder**: Navigate to the folder named My Documents\Visual Studio <version>\Templates\ItemTemplates. For example, the path could be My Documents\Visual Studio 2010\Templates\ItemTemplates.

2. **Move Templates to Desired Category**: By default, custom templates may appear in the root list when adding a new item. To categorize them, create a new folder within the ItemTemplates directory, such as "Code."

3. **Organize Templates into Categories**: Move the custom item templates into the newly created folder (e.g., "Code"). This categorization ensures that the templates will appear under the specified category when adding a new item.

4. **Custom Folder Names**: If desired, you can create custom folder names for your templates. For instance, creating an "XYZ Company" folder and placing templates inside it will result in the folder being displayed as a category when adding a new item.

By organizing your custom item templates into specific folders within the ItemTemplates directory, you can easily access and categorize them according to your preferences when adding new items to your projects.

**02.16 Organizing Your Custom Project Templates**

After creating custom project templates using the Export Template Wizard as described in vstipProj0004, organizing them is simple. Here's how to do it:

1. **Locate the ProjectTemplates Folder**: Browse to the folder named My Documents\Visual Studio <version>\Templates\ProjectTemplates. For instance, the full path could be My Documents\Visual Studio 2010\Templates\ProjectTemplates.

2. **Move Templates to Desired Category**: By default, custom project templates may not appear in specific subfolders in the New Project dialog box. To organize them, create a new folder within the ProjectTemplates directory with a name corresponding to the desired category (e.g., "Windows" for Windows projects).

3. **Organize Templates into Categories**: Move the custom project templates into the newly created folder (e.g., "Windows"). This categorization ensures that the templates will appear under the specified category in the New Project dialog box, making it easier to locate and select them.

4. **Custom Folder Names**: You can also create custom folder names for organizing templates. For example, creating a folder with your company name and placing templates inside it will result in the folder being displayed as a category in the New Project dialog box.

By organizing your custom project templates into specific folders within the ProjectTemplates directory, you can easily access and categorize them according to your preferences when creating new projects.

**02.17 Reorganize the Default Item Templates**

This tip explains how to reorganize the default item templates in Visual Studio to create custom areas for better organization. Here's a step-by-step guide:

1. **Locate Item Templates**: Find where Visual Studio stores item templates on your machine. Typically, this is in a directory like C:\Program Files\Microsoft Visual Studio <version>\Common7\IDE\ItemTemplates\<language>. Depending on your Visual Studio version and the items you're looking for, the path might vary. For example, the full path on the author's machine is C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\ItemTemplates\CSharp.

2. **Create Custom Folder**: Create a new folder within the item templates directory. For example, the tip suggests creating a folder named "Diagrams" for storing diagram-related item templates.

3. **Move Templates**: Navigate to the General\1033 folder within the item templates directory and locate the .zip files of the diagram templates you want to organize. Carefully move these .zip files to the newly created "Diagrams" folder.

4. **Close Visual Studio**: Close all instances of Visual Studio to ensure the changes take effect.

5. **Run Command**: Open the Visual Studio command prompt with administrative privileges and run the following command:
   
   ```
   devenv.com /installvstemplates
   ```

   Let the process complete without interference. It's crucial to wait until the process finishes. You'll know it's done when another cursor appears.

6. **Verify Changes**: Open Visual Studio and any project. Bring up the Add New Item dialog box (Ctrl+Shift+A) and observe the new "Diagrams" area with the templates you moved inside it.

By following these steps, you can reorganize the default item templates in Visual Studio to create custom areas for better organization, enhancing your workflow efficiency.

**02.18 Reorganize the Default Project Templates**

This tip guides you through reorganizing the default project templates in Visual Studio to create custom areas for better organization. Here's a step-by-step process:

1. **Locate Project Templates**: Find where Visual Studio stores project templates on your machine. Typically, this is in a directory like C:\Program Files\Microsoft Visual Studio <version>\Common7\IDE\ProjectTemplates\<language>. Depending on your Visual Studio version and the templates you're looking for, the path might vary. For example, on the author's machine, the full path for C# templates is C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\ProjectTemplates\CSharp.

2. **Create Custom Folder**: Within the project templates directory, create a new folder and name it appropriately. For example, the tip suggests creating a folder named "WPF" for organizing WPF project templates.

3. **Move Templates**: Navigate to the Windows folder (usually Windows\1033\) within the project templates directory and locate the WPF templates. Move these .zip files into the newly created "WPF" folder.

4. **Close Visual Studio**: Close all instances of Visual Studio to ensure the changes take effect.

5. **Run Command**: Open the Visual Studio command prompt and run the following command with administrative privileges:
   
   ```
   devenv.com /installvstemplates
   ```

   Allow the process to complete without interruption. You'll know it's done when the command prompt shows up again.

6. **Verify Changes**: Open Visual Studio and access the New Project dialog box (Ctrl+Shift+N) to see the newly created "WPF" area containing the WPF templates.

By following these steps, you can reorganize the default project templates in Visual Studio, creating custom areas for better organization and improving your workflow efficiency.

**02.19 Change the Templates that Appear in the New Project or Item Dialog Boxes**

This tip explains how to manipulate the templates that appear in the New Project or New Item dialog boxes in Visual Studio. Here's a step-by-step guide:

1. **Locate Template Files**: Navigate to the directory where Visual Studio stores templates for your selected language and category. Typically, this is in a path like C:\Program Files\Microsoft Visual Studio <version>\Common7\IDE\<Project or Item>Templates\<language>\<project category>. Depending on your Visual Studio version and the templates you want to modify, the path might vary. For example, on the author's machine, the path to the Windows Forms Control Library .zip file is C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\ProjectTemplates\CSharp\Windows.

2. **Move Template**: Instead of deleting the template file, which might be needed in the future, move the .zip file to another directory. This ensures that you can retrieve it later if necessary.

3. **Close Visual Studio**: Close all instances of Visual Studio to ensure the changes take effect.

4. **Run Command**: Open the Visual Studio command prompt from the Start menu and run the following command with administrative privileges:
   
   ```
   devenv.com /installvstemplates
   ```

   Allow the process to complete without interruption. You'll know it's done when the cursor shows up again.

5. **Verify Changes**: After the process completes, restart Visual Studio and create a new project (Ctrl+Shift+N). You should observe that the moved template is no longer present in the list.

By following these steps, you can customize the templates that appear in the New Project or New Item dialog boxes in Visual Studio, tailoring the options to better suit your needs.