**Chapter 3: Getting to Know the Environment**

*"A mobile robot has to devote a tremendous amount of processing time simply to avoid obstacles in the environment. Human beings do, too, but they’re never aware of it—until the lights go out. Then they learn painfully just how much processing is really required."*  
— Michael Crichton, "Prey"

Too often, we take our environment for granted—the familiar sights we encounter every day that we may overlook. This section aims to awaken your awareness to the potential within your Visual Studio environment.

The primary objective is to illuminate the best practices for managing your window layouts, leveraging the toolbox effectively, and mastering command usage, among other essential skills. By thoroughly exploring the Visual Studio environment, you can uncover the keys to navigating it with confidence and efficiency.

**03.01 Rearrange Windows in Visual Studio 2010 Using the Guide Diamond**

Docking and undocking windows in the IDE has always been an interesting task. In Visual Studio, we have a tool called the Guide Diamond that assists our efforts. 

**Default Shortcut:** [no shortcut]

**Visual Basic 6:** [no shortcut]

**Visual C# 2005:** [no shortcut]

**Visual C++ 2:** Alt+F6 (dock)

**Visual C++ 6:** [no shortcut]

**Visual Studio 6:** [no shortcut]

**Windows:** 
- Float: Alt,W, F 
- Dock: Alt,W, K 
- Dock as Tabbed Document: Alt,W, T 

**Menu:** 
- Float: Window | Float 
- Dock: Window | Dock 
- Dock as Tabbed Document: Window | Dock as Tabbed Document

**Command:** 
- Float: Window.Float 
- Dock: Window.Dock 
- Dock as Tabbed Document: Window.DockasTabbedDocument

**Versions:** 2010

**Code:** vstipTool0008

In Visual Studio 2010, the Guide Diamond has been revamped to provide better visual cues for docking windows. Unlike the previous version, which didn't offer clear previews, the improved Guide Diamond displays accurate previews of how your docked window will appear. 

To rearrange windows using the Guide Diamond:
1. Drag the title bar of your window over one of the previews in the Guide Diamond.
2. Once the preview matches the desired position for your window, release the mouse.
3. The window will dock at the selected location based on the preview in the Guide Diamond.

**03.02 Dock a Floating Tool Window Back to Its Previous Location**

To dock a floating tool window back to its previous location, follow these steps:

**Default Shortcut:** [no shortcut]

**Visual Basic 6:** [no shortcut]

**Visual C# 2005:** [no shortcut]

**Visual C++ 2:** Alt+F6

**Visual C++ 6:** [no shortcut]

**Visual Studio 6:** [no shortcut]

**Windows:** Alt,W, K

**Menu:** Window | Dock

**Command:** Window.Dock

**Versions:** 2005, 2008, 2010

**Code:** vstipTool0036

1. Right-click the Title Bar of the floating tool window.
2. From the context menu, select "Dock."

**Note:** 
- In Visual Studio 2008, you can alternatively double-click the title bar to dock the window back to its previous location.
- For Visual Studio 2005, you can dock the tool window back to its previous location by double-clicking the title bar. The title bar menu in Visual Studio 2005 uses the term "Dockable" instead of "Dock."

**03.03 Cycle Through Your Open Tool Windows**

To cycle through your open tool windows, follow these steps:

**Default Shortcut:** Alt+F6 (next); Alt+Shift+F6 (previous)

**Visual Basic 6:** Alt+F6 (next); Alt+Shift+F6 (previous)

**Visual C# 2005:** Alt+F6 (next); Alt+Shift+F6 (previous)

**Visual C++ 2:** F6 (next); Shift+F6 (previous)

**Visual C++ 6:** Alt+F6 (next); Alt+Shift+F6 (previous)

**Visual Studio 6:** Alt+F6 (next); Alt+Shift+F6 (previous)

**Windows:** [no shortcut]

**Command:** Window.NextPane; Window.PreviousPane

**Versions:** 2005, 2008, 2010

**Code:** vstipTool0038

1. Press Alt+F6 to cycle to the next open tool window.
2. Press Alt+Shift+F6 to cycle to the previous open tool window.

**Note:** 
- An "open" tool window refers to those whose tab appears in the IDE, even if they are hidden.

**03.04 Closing Tool Windows**

To close tool windows, follow these steps:

**Default Shortcut:** Shift+Esc

**Visual Basic 6:** Shift+Esc

**Visual C# 2005:** Shift+Esc

**Visual C++ 2:** Shift+Esc

**Visual C++ 6:** Shift+Esc

**Visual Studio 6:** Shift+Esc

**Windows:** [no shortcut]

**Command:** Window.CloseToolWindow

**Versions:** 2005, 2008, 2010

**Code:** vstipTool0039

1. Click the Close button (the "X" in the upper-right corner) of the tool window.
2. Alternatively, use the keyboard shortcut Shift+Esc to close the current tool window.

**03.05 Expand and Collapse All in the Toolbox**

To expand or collapse all items in the Toolbox, use the following shortcuts:

**Windows:** 
- * (asterisk) to expand all
- / (forward slash) to collapse all

**Versions:** 2005, 2008, 2010

**Code:** vstipTool0050

1. When the Toolbox is active, press * (asterisk) to expand all items.
2. Similarly, press / (forward slash) when the Toolbox is active to collapse all items.

**03.06 Searching in the Toolbox**

To search for controls in the Toolbox, follow these steps:

**Default Shortcut:**
- Ctrl+Alt+X to view the Toolbox

**Versions:**
- Visual Basic 6
- Visual C# 2005
- Visual C++ 2
- Visual C++ 6
- Visual Studio 6

**Visual C# 2005 Additional Shortcuts:**
- Ctrl+W, X to view the Toolbox
- Ctrl+W, Ctrl+X to view the Toolbox

**Windows Shortcut:**
- Alt+V, X to view the Toolbox
- TAB to move to the next result
- ESC to cancel

**Menu Option:**
- View | Toolbox

**Command:**
- View.Toolbox

**Code:** vstipTool0114

1. Switch focus to the Toolbox using Ctrl+Alt+X.
2. Start typing the name of the control you are looking for.
3. The letters you type will appear in the Status Bar.
4. Press Tab to navigate to the next result or Esc to cancel the search.
5. Use the Backspace key to delete characters and refine your search.

**03.07 Navigate Among Tabs in the Toolbox**

To navigate between tabs in the Toolbox, follow these steps:

**Keyboard Shortcut:**
- Ctrl+[Up, Down] Arrow

**Versions:**
- 2005, 2008, 2010

**Code:** vstipTool0051

1. Use the keyboard shortcut Ctrl+[Up, Down] Arrow to navigate between tabs in the Toolbox.
2. Pressing Ctrl+Down Arrow expands the next tab and jumps to the first item in that group.
3. Pressing Ctrl+Up Arrow jumps to the last item in the previous control group.

**03.08 Window Layouts: The Four Modes**

In Visual Studio, there are four window layout modes that dictate the arrangement of windows and toolbars:

**Versions:** 2005, 2008, 2010

**Code:** vstipEnv0051

1. **Design View:**
   - This is the default view when you start Visual Studio.
   - It's commonly referred to as the "normal" view.
   
2. **Debugging View:**
   - When you enter Debug Mode while debugging your code, Visual Studio switches to this view.
   
3. **Full Screen:**
   - Accessible via View | Full Screen (Shift+Alt+Enter).
   - It maximizes the workspace by hiding toolbars and other UI elements.
   
4. **File View:**
   - This mode is activated when opening a file via `devenv.exe [filename]`.
   - It provides a focused view of the file being edited.
   
**Note:** 
- Tool windows and command bar customizations are saved separately for each mode.
- All four states are saved when you shut down Visual Studio.

**03.09 Window Layouts: Design, Debug, and Full Screen**

In Visual Studio, there are three common window layout modes: Design, Debug, and Full Screen.

**Versions:** 2005, 2008, 2010

**Code:** vstipEnv0052

1. **Design Mode:**
   - This mode is the default view upon starting Visual Studio.
   - It's the most common mode for regular coding tasks.
   - Users can customize the layout to suit their preferences.
   - Example: A website design layout is illustrated in the provided screenshot.

2. **Debug Mode:**
   - Entered when debugging code.
   - Provides specific tools and views tailored for debugging tasks.
   - Layout can be customized independently from the Design Mode.
   - Example: Debug Window Layout for a console application is depicted.

3. **Full Screen Mode:**
   - Accessed by pressing Shift+Alt+Enter.
   - Maximizes the workspace by hiding toolbars and other UI elements.
   - Particularly useful for focused coding sessions without distractions.
   - Previously discussed in vstipEnv0024, AX.20 Full Screen Mode.
   - Illustrative example of Full Screen Mode is provided.

Each mode offers distinct layouts that users can customize based on their workflow and preferences.

**03.10 Working with Tabs in the Toolbox**

In Visual Studio, organizing items in the Toolbox using tabs can enhance productivity. Here's how to work with tabs effectively:

**Versions:** 2005, 2008, 2010

**Code:** vstipTool0054

1. **Creating Tabs:**
   - Right-click inside the Toolbox and select "Add Tab."
   - Enter a name for the new tab and press Enter.

2. **Adding Items:**
   - Copy items from existing tabs and paste them into the custom tab.
   - Alternatively, drag items onto new tabs to organize them.

3. **Custom Controls:**
   - Right-click in the custom tab and choose "Choose Items" to add custom controls.

4. **Renaming Tabs:**
   - Right-click on the tab and select "Rename" to change the tab name.

5. **Deleting Tabs:**
   - Right-click on the tab and choose "Delete."
   - Confirm deletion in the dialog box.
   - Note that deleting a tab removes it along with all its items, but doesn't permanently delete controls from the system.

Organizing Toolbox items into tabs provides a structured approach for accessing and managing controls in Visual Studio.

**03.11 Using Additional Browsers for Web Development**

In Visual Studio, you can utilize different browsers for web development tasks. Here's how to do it:

**Versions:** 2005, 2008, 2010

**Code:** vstipEnv0057

1. **Accessing the Browse With Dialog Box:**
   - Navigate to the File menu and select "Browse With" with either your web project or a webpage selected in Solution Explorer.
   - Alternatively, right-click on the file in Solution Explorer and choose "Browse With."

2. **Adding New Browsers:**
   - If your desired browser is not automatically detected, click "Add."
   - Enter the path to the browser's executable in the "Program Name" field.
   - Assign a friendly name for the browser in the "Friendly Name" field.

3. **Changing the Default Browser:**
   - Select a browser from the list and click "Set As Default" to make it the default browser.

4. **Adjusting Browser Window Size:**
   - Use the "Size Of Browser Window" drop-down list to choose the desired window size for the browser.

5. **Removing Browsers:**
   - To remove unwanted browser options, select the browser from the list and click "Remove."

Customizing browser options in Visual Studio allows for seamless integration with different web development environments and preferences.

**03.12 Auto-Hide All Tool Windows**

When dealing with a cluttered workspace in Visual Studio, you can quickly hide all tool windows using the following method:

**Versions:** 2005, 2008, 2010

**Code:** vstipTool0034

1. **Accessing the Auto Hide All Option:**
   - Go to the Window menu and select "Auto Hide All."
   - Alternatively, use the shortcut Alt + W + U.

**Note:** Once hidden, there's no direct method to "un-auto-hide" all tool windows at once. You'll need to manually bring back each tool window individually.

By using this feature, you can swiftly declutter your workspace by hiding all open tool windows simultaneously.

**03.13 Showing Hidden Tool Windows with the Auto Hide Channel**

If you've hidden tool windows in Visual Studio, you can easily reveal them using the Auto Hide Channel. Here's how:

**Versions:** 2005, 2008, 2010

**Code:** vstipTool0037

1. **Accessing the Auto Hide Channel:**
   - Navigate to any area where tool windows are hidden.
   - Right-click on the bar where the tabs are located.

2. **Viewing Hidden Tool Windows:**
   - A list of hidden tool windows will appear.
   - This method works for both the bottom and left channels.

3. **Best Practices:**
   - Click in the empty space within the channel, beyond any tabs, for optimal results.

4. **Revealing Hidden Windows:**
   - Simply select the desired tool window from the list to show it again.

By utilizing the Auto Hide Channel, you can easily manage and access hidden tool windows within Visual Studio.

**03.14 Moving Tool Windows Around with Your Keyboard**

In Visual Studio 2010, you can efficiently manage tool windows using keyboard shortcuts. Here's how:

**Versions:** 2010

**Code:** vstipTool0041

1. **Accessing the Dock Menu:**
   - When an active tool window is docked, press Alt+- (minus sign) to bring up the Dock menu.

2. **Navigating the Dock Menu:**
   - Use the arrow keys to select an item from the menu.

3. **For Floating Tool Windows:**
   - Active floating tool windows have a System menu.
   - Press Alt+Space to access the System menu for floating tool windows.

4. **Commands:**
   - Familiar commands like Float, Dock, etc., are available in the Window menu for further window manipulations.

By utilizing these keyboard shortcuts, you can efficiently move, resize, and manage tool windows in Visual Studio 2010.

**03.15 Keyboard Access to a Tool Window’s Toolbar**

In Visual Studio 2005, 2008, and 2010, you can access a tool window's toolbar using keyboard shortcuts. Here's how:

**Windows:** Shift+Alt (for some), Tab (for others)

1. **Accessing Toolbar:**
   - For some tool windows, press Shift+Alt to access the toolbar.
   - For others, simply press the Tab key.

2. **Example Usage:**
   - To access the Solution Explorer Toolbar, press Shift+Alt.
   - For the Properties Tool Window, use the Tab key.

3. **Navigation:**
   - Once the toolbar is accessible, use the arrow keys to navigate between toolbar items.
   - Press the Enter key to activate the selected button.

By utilizing these keyboard shortcuts, you can conveniently access and navigate through the toolbar of any active tool window without relying on the mouse.

**03.16 Command Prompt History**

In Windows, you can access the command prompt history using the following shortcuts:

**Accessing History:**
- **Windows:** F7 (opens history window); Up / Down Arrow (navigate through history)

**Usage:**
1. **Viewing History:**
   - After typing commands into the Command Window, clear the screen by typing "cls" and pressing Enter.
   - To view command history:
     - Press the Up Arrow key to navigate through the history directly at the prompt.
     - Alternatively, press F7 to open the history window.

2. **Navigating and Executing Commands:**
   - While in the history window, use the Up or Down Arrow keys to navigate through the list of previously typed commands.
   - Select a command from the history list and press Enter to execute it.

**Note:** Ensure that you've entered commands into the Command Window before attempting to access the command prompt history. These shortcuts provide convenient ways to retrieve and execute previously entered commands without retyping them.

**03.17 Command Prompt Tab Completion**

In Windows, you can utilize tab completion in the command prompt for efficient file and command navigation. Here's how:

**Using Tab Completion:**
- **Windows:** Tab

**Simple Search:**
1. Type the first letter of a file or command.
2. Press Tab to display all files or commands starting with that letter.
   - Example: Typing "a" and pressing Tab shows all files starting with "a".

**Wildcard Search:**
1. Utilize wildcards to match characters:
   - Use * to represent any number of characters.
   - Use ? to represent a single character.
2. Example:
   - To find files containing the letter "a" anywhere in the name, use "*a*".
   - Press Tab to display the first result.
   - Press Tab repeatedly to cycle through all files matching the criteria.

**Example Scenarios:**
1. Searching for files:
   - Enter a partial file name or pattern (e.g., "*a*").
   - Press Tab to view matching files.
   - Continue pressing Tab to cycle through results.

2. Searching for commands:
   - Type a command followed by a partial file name or pattern (e.g., "edit *a*").
   - Press Tab to view matching files.
   - Continue pressing Tab to cycle through results.

**Benefits of Tab Completion:**
- Increases efficiency in navigating files and executing commands.
- Offers a powerful and versatile feature for command prompt users.
- Enhances productivity by reducing manual typing and improving search accuracy.

Mastering tab completion is essential for maximizing productivity and efficiency when working with the command prompt.

**03.18 Undock and Dock a Single Tool Window in a Group**

Undocking and docking tool windows in Visual Studio is a common task. Here are the different techniques you can use to accomplish these actions:

**Undock:**

1. **Click and Drag:**
   - With the mouse, click and drag the tab out of the group.
   - This action separates the tool window from the group.

2. **Menu:**
   - With the tool window active, select "Window" > "Float" from the menu bar.
   - This action floats the tool window, separating it from the group.

3. **Control Box (Visual Studio 2010 only):**
   - Press Alt+minus (–) to open the tool window menu.
   - Press "F" to float the tool window.
   - This action also floats the tool window.

**Dock:**

1. **Click and Drag:**
   - Click and drag the tool window back into the desired group.
   - Drag the tool window's title bar over another tool window's title bar in the group.
   - Look for the target shading resembling a tab being added to the existing group.
   - This action docks the tool window into the specified group.

2. **Menu:**
   - Go to "Window" > "Dock" from the menu bar.
   - This action docks the tool window back into its original group.

3. **Control Box (Visual Studio 2010 only):**
   - Press Alt+minus (–) to open the tool window menu.
   - Press "K" to dock the tool window back to its original location.
   - This action also docks the tool window into its original group.

**Result:**
   - Using any of these methods places the tool window back into the group it originated from, except for the click and drag method, which allows placing the tool window anywhere.

**03.19 Understanding Commands: Simple Commands**

Understanding commands in Visual Studio is essential for efficient development. Here's a breakdown of how commands work:

1. **Definition of Commands:**
   - According to MSDN documentation, commands allow direct interaction with the IDE from the keyboard.
   - They represent actions that can be performed within Visual Studio.

2. **Example: Adding a Class:**
   - The typical way to add a class is by navigating to "Project" > "Add Class" in the menu.
   - This action opens the "Add New Item" dialog box, where you can create a new class.

3. **Accessing Commands:**
   - You can access commands through the "command well," located in "Tools" > "Options" > "Environment" > "Keyboard."
   - Typing keywords related to the action you want to perform narrows down the list of available commands.

4. **Finding the Command:**
   - In the command well, typing "Add Class" reveals the "Project.AddClass" command.
   - This command follows the menu structure and represents the action of adding a class to the project.

5. **Assigning Shortcuts:**
   - By default, some commands may not have shortcuts assigned.
   - You can assign shortcuts to commands to streamline your workflow.
   - In the example, Ctrl+M, Ctrl+7 is assigned as a shortcut for the "Project.AddClass" command.

6. **Using Assigned Shortcuts:**
   - After assigning a shortcut, you can use it to execute the associated command.
   - Pressing Ctrl+M, Ctrl+7 invokes the "Project.AddClass" command, opening the "Add New Item" dialog box.

7. **Benefits of Commands:**
   - Commands provide a quick and efficient way to perform actions in Visual Studio.
   - Once assigned a shortcut, commands can be executed directly from the keyboard, saving time and effort.

Understanding commands and assigning shortcuts can significantly enhance your productivity in Visual Studio.

**03.20 Understanding Commands: Aliases**

Understanding aliases in Visual Studio can streamline your workflow by allowing you to execute commands quickly. Here's how aliases work:

1. **Accessing the Command Window:**
   - You can access the Command Window by pressing Ctrl+Alt+A, which opens a window where you can execute commands and manage aliases.

2. **Listing Current Aliases:**
   - Typing `alias` in the Command Window displays a list of current aliases, making it easy to see which shortcuts are available.

3. **Using Existing Aliases:**
   - Aliases can be used to execute commands without typing the full syntax.
   - For example, the alias `bp` corresponds to the command `Debug.ToggleBreakpoint`, allowing you to set a breakpoint quickly by typing `bp` in the Command Window.

4. **Creating New Aliases:**
   - You can create new aliases using the syntax `alias [alias_name] [command]` in the Command Window.
   - For instance, `alias ac Project.AddClass` creates an alias `ac` for the `Project.AddClass` command.

5. **Viewing Assigned Aliases:**
   - To check which command an alias is assigned to, type `alias [alias_name]` in the Command Window.
   - For example, typing `alias ac` reveals the command assigned to the `ac` alias.

6. **Deleting Aliases:**
   - If you want to remove an alias, you can do so by typing `alias [alias_name] /d` or `alias [alias_name] /delete` in the Command Window.
   - For instance, `alias ac /d` deletes the `ac` alias.

Aliases provide a convenient way to execute commands in Visual Studio, saving time and reducing the need to remember complex command syntaxes. They can be managed easily through the Command Window, allowing for customization of your development environment to suit your preferences.

**03.21 Understanding Commands: Arguments and Switches**

Understanding commands with arguments and switches in Visual Studio allows for quick execution of actions without relying on user interface elements. Here's how to use arguments and switches with commands:

1. **Accessing the Command Window:**
   - You can access the Command Window by pressing Ctrl+Alt+A, where you can execute commands and explore their functionalities.

2. **Exploring Commands:**
   - To learn about commands that take arguments, you can refer to the "Visual Studio Commands with Arguments" MSDN documentation.

3. **Basic Use:**
   - Open the Command Window and execute a command without any arguments to observe its default behavior. For example, running the `Edit.Find` command opens the Find And Replace dialog box.

4. **Arguments and Switches:**
   - Commands like `Edit.Find` often take arguments and switches to customize their behavior.
   - The `Edit.Find` command, for instance, takes the argument `findwhat` and offers various switches such as `/doc`, `/markall`, `/wild`, etc.

5. **Listing Current Options:**
   - You can list the current options set for a command by typing `[command] /options` in the Command Window.

6. **Resetting Options:**
   - Resetting options to default values can be done using the `[command] /reset` syntax.

7. **Using Arguments and Switches:**
   - Utilize arguments and switches to perform specific tasks. For example, `Edit.Find *c* /wild /doc /markall` searches for lines containing the letter "c" in the current document, using wildcards and placing bookmarks on matching lines.

8. **Creating Aliases:**
   - To simplify frequent commands, you can create aliases. For instance, `alias findc Edit.Find *c* /wild /doc /markall` assigns an alias `findc` to the `Edit.Find` command with specific arguments and switches.
   - This alias can be recalled using `findc` in the Command Window, bypassing the need to re-enter the full command.

Understanding commands with arguments and switches enhances productivity by providing a more efficient way to execute tasks within Visual Studio. Aliases further streamline the process by allowing for quick access to frequently used commands.

**03.22 Testing a Command**

Testing commands in Visual Studio is essential for understanding their functionality. Here's how you can quickly test a command:

1. **Accessing the Command Window:**
   - Press Ctrl+Alt+A to bring up the Command Window in Visual Studio.

2. **Identifying the Command:**
   - Determine the command you want to test. For example, let's test the "View.ViewCode" command.

3. **Entering the Command:**
   - In the Command Window, start typing the command you want to test. In this case, type "View.ViewCode". Note that case doesn't matter, and IntelliSense may assist you as you type.

4. **Executing the Command:**
   - Once you've entered the command, press Enter to execute it.

5. **Observing the Result:**
   - Observe the result of the command. In this example, if a Design window is open, the "View.ViewCode" command will switch to the corresponding code view.

6. **Testing Various Commands:**
   - Feel free to test different commands to explore their functionalities. Ensure that you set up the appropriate context to ensure the command works as expected.
  
7. **Considerations:**
   - Note that some commands may not be executable directly from the Command Window and might require other methods such as assigning a shortcut key or using the Find Combo box.

By testing commands, you can gain a better understanding of their capabilities and efficiently utilize them in your Visual Studio workflow. For more information on running commands, refer to vstipTool0070 (03.23 Understanding Commands: Running Commands).

**03.23 Understanding Commands: Running Commands**

Understanding how to run commands efficiently in Visual Studio is crucial for enhancing your productivity. Here are the main ways you can run commands:

1. **Shortcuts:**
   - Utilize shortcut keys assigned to specific commands. For example, the "View.Code" command may have predefined shortcut keys.

2. **Command Window:**
   - Access the Command Window (Ctrl+Alt+A) designed explicitly for executing commands. Simply type in the command and press Enter to execute it.

3. **Immediate Window:**
   - Run commands from the Immediate Window (Ctrl+Alt+I) by typing a greater-than sign (>). Then enter the desired command and press Enter to execute it.

4. **Find Combo Box:**
   - Execute commands from the Find Combo Box, accessed by pressing Ctrl+/ or Ctrl+D. Type a greater-than sign (>) followed by the command you want to run, and then press Enter.

   - In most language settings, you can bypass typing the greater-than sign by using Ctrl+/ directly, which automatically inserts the sign for you in the Find Combo Box.

By familiarizing yourself with these methods, you can efficiently execute commands in Visual Studio, enhancing your workflow and productivity. For more information about shortcut keys, refer to vstipTool0061 (03.24 Find Keyboard Shortcuts).

**03.24 Find Keyboard Shortcuts**

In Visual Studio, discovering keyboard shortcuts for various commands can significantly enhance your productivity. Here's how you can find and utilize keyboard shortcuts effectively:

1. **Accessing Keyboard Shortcuts:**
   - Navigate to the Tools menu and select Options.
   - Within Options, go to Environment and then Keyboard settings.

   ![Tools | Options | Environment | Keyboard](image_link)

2. **Exploring Available Commands:**
   - In the Keyboard settings dialog, you can search for specific commands. For example, if you're interested in the keyboard shortcuts for "View | Code," start by typing "View." in the search bar.
   - Scroll through the list of commands to find relevant entries. Commands are typically named using dot notation, such as "View.ViewCode."

3. **Finding Shortcut Keys:**
   - Once you've located a command of interest, check the "Shortcuts For Selected Command" section to see if any shortcut keys are assigned to it.

   ![Shortcuts For Selected Command](image_link)

4. **Testing Shortcuts:**
   - Try out the discovered shortcut keys in the appropriate context to confirm their functionality.
   - For example, if F7 is listed as a shortcut for "View.ViewCode," navigate to the Designer and press F7 to see if it opens the code view.

5. **Additional Tips:**
   - Shortcuts can vary depending on the context. For instance, different shortcuts might be assigned for accessing code from the Designer and the Class Diagram.

   - Experiment with different commands and shortcuts to optimize your workflow and speed up your development tasks.

By utilizing the Keyboard settings in Visual Studio, you can easily discover and leverage keyboard shortcuts to streamline your development process and improve efficiency.

**03.25 Keyboard Shortcuts: Additional Mapping Schemes**

In Visual Studio, you can customize keyboard shortcuts to match different mapping schemes, including those from previous versions. Here's how to access and apply additional mapping schemes:

1. **Accessing Keyboard Settings:**
   - Navigate to the Tools menu and select Options.
   - Within Options, go to Environment and then Keyboard settings.

   ![Tools | Options | Environment | Keyboard](image_link)

2. **Exploring Additional Mapping Schemes:**
   - In the Keyboard settings dialog, locate the "Apply The Following Additional Keyboard Mapping Scheme" drop-down list.

3. **Understanding Mapping Scheme Options:**
   - The drop-down list contains various mapping schemes, including those from previous versions of Visual Studio.
   - For example, if you select "Visual C++ 6" as the additional mapping scheme, it will apply keyboard shortcuts common in Visual C++ 6.

4. **Viewing Shortcut Changes:**
   - After selecting an additional mapping scheme, observe how it affects the keyboard shortcuts for commands.
   - For instance, if you previously examined the shortcuts for "View.ViewCode" with the default mapping scheme, applying an additional scheme like "Visual C++ 6" may introduce new shortcuts.

   ![Shortcut Changes](image_link)

5. **Managing Mapping Schemes:**
   - If you prefer to stick with the default mapping scheme or another specific scheme, you can switch back by selecting it from the drop-down list.
   - Choose "Default" or "General" to revert to the standard mapping scheme.

By utilizing additional mapping schemes in Visual Studio, you can adapt keyboard shortcuts to match the conventions of previous versions or customize them according to your preferences. This flexibility enhances your productivity and ensures a seamless transition for users accustomed to different mapping schemes.

**03.26 Keyboard Shortcuts: Creating New Shortcuts**

In Visual Studio, you can easily create new keyboard shortcuts for commands to streamline your workflow. Here's a step-by-step guide on how to create a new shortcut:

1. **Accessing Keyboard Settings:**
   - Navigate to the Tools menu and select Options.
   - Within Options, go to Environment and then Keyboard settings.

   ![Tools | Options | Environment | Keyboard](image_link)

2. **Identifying the Command:**
   - Choose the command for which you want to create a new shortcut. In this example, let's modify the "View.ViewCode" command.

3. **Selecting Shortcut Keys:**
   - Click on the "Press Shortcut Keys" area and enter the desired shortcut combination. For instance, let's use Ctrl+Alt+4.

   ![Press Shortcut Keys](image_link)

4. **Resolving Conflicts:**
   - Check the "Shortcut Currently Used By" area to ensure that the chosen shortcut isn't already assigned to another command.
   - If a conflict arises, try a different set of shortcut keys until you find an available combination.

5. **Choosing Scope:**
   - Decide the scope of the new shortcut using the drop-down menu labeled "Use New Shortcut In."
   - The default scope is usually global, but you can specify a narrower scope if needed.

6. **Assigning the Shortcut:**
   - Once you've selected the shortcut keys and scope, click the "Assign" button to make the shortcut active.

7. **Testing the Shortcut:**
   - After assigning the shortcut, click OK to save the changes.
   - Test the new shortcut in the desired context. For example, if you modified "View.ViewCode," navigate to a design view and press the new shortcut keys (Ctrl+Alt+4).

   ![Testing Shortcut](image_link)

8. **Resetting Shortcuts (If Necessary):**
   - If you make a mistake or want to revert to the default shortcuts, you can click the "Reset" button in the Keyboard settings.
   - Exercise caution when resetting shortcuts, as it will revert all shortcuts to their default configurations.

By following these steps, you can efficiently create custom keyboard shortcuts tailored to your preferences, enhancing your productivity within Visual Studio.

**03.27 Keyboard Shortcuts: Reset All Your Shortcuts**

If you find yourself overwhelmed by the number of custom keyboard shortcuts you've created or if you simply want to return all shortcuts to their default settings, you can easily reset them. Here's how:

1. **Accessing Keyboard Settings:**
   - Navigate to the Tools menu and select Options.
   - Within Options, go to Environment and then Keyboard settings.

2. **Resetting Shortcuts:**
   - In the Keyboard settings, locate the Reset button.

   ![Reset Button](image_link)

3. **Confirmation Prompt:**
   - Clicking the Reset button prompts a warning message to confirm your action. The message highlights the consequences of resetting all keyboard mappings.

   ![Reset Confirmation](image_link)

4. **Proceeding with Reset:**
   - If you're certain you want to reset all shortcuts, click Yes in the confirmation prompt.

5. **Effect of Reset:**
   - After clicking Yes, all custom keyboard mappings are reverted to their default values.

   ![Before Reset](image_link)
   *Before Reset*

   ![After Reset](image_link)
   *After Reset*

   The illustrations above depict the state before and after resetting the keyboard shortcuts.

Before proceeding with the reset, ensure that you're fully aware of the implications, as it will remove all custom shortcuts you've created. Use this feature judiciously, especially if you've invested time in configuring personalized shortcuts.

**03.28 Understanding Commands: Logging Commands**

When working with commands in Visual Studio, it's often useful to keep a log of the commands you've executed. This is particularly handy for tracking your experimentation or troubleshooting sessions. Here's how you can log commands:

1. **Command Syntax:**
   - To initiate logging, you can use either of the following syntaxes:
     - `log [filename] [/on|/off] [/overwrite]`
     - `Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]`

2. **Arguments:**
   - **Filename:** It's advisable to specify a path and filename for the log. If not provided, the default filename is `cmdline.log`, stored at `C:\Users\<user>\AppData\Roaming\Microsoft\VisualStudio\<version>`.
   - **/on /off:** These arguments toggle logging on or off.
   - **/overwrite:** By default, logging appends to the log file. Using this switch overwrites the existing log with new commands.

3. **Example:**
   - Open the Command Window (Ctrl+Alt+A) and start logging by specifying a filename: `log C:\Users\<user>\Documents\vslog.txt /on`.
   - Execute various commands in Visual Studio. For demonstration, commands like `View.ViewCode` and `Edit.Find` are used.
   - Once done, turn off logging with the command `log /off`.
   - Navigate to the specified file location (e.g., My Documents) to view the log file.

   ![Logging Commands](image_link)

4. **Reviewing the Log:**
   - Upon opening the log file, you'll find a sequential record of the commands you entered during the logging session.
   - Each command, including the one to disable logging, is documented in the file.

By logging commands, you can maintain a record of your actions within Visual Studio, aiding in reproducibility and troubleshooting efforts.

**03.29 Export Your Window Layouts**

Once you've meticulously arranged your tool and document windows in Visual Studio to suit your workflow, it's essential to safeguard these settings for future use or in case of any mishap. Here's how you can export your window layouts:

1. **Accessing the Export Option:**
   - Navigate to **Tools | Import and Export Settings** (Alt+T, I).

2. **Initiating the Export Process:**
   - Choose **Export Selected Environment Settings** and proceed by clicking **Next**.

3. **Customizing Export Settings:**
   - Uncheck the **All Settings** option to specify individual settings to export.
   - Under **General Settings**, select **Window Layouts**, and proceed by clicking **Next**.

4. **Naming and Saving the Export File:**
   - Assign a descriptive name to the `.vssettings` file that will store your window layouts.
   - Choose a suitable location for saving the file.
   - Complete the export process by clicking **Finish**, followed by **Close**.

5. **Using Exported Layouts:**
   - Your window layouts are now safely stored in the specified location.
   - In case you need to restore these layouts in the future, refer to the instructions for importing settings (see [vstipEnv0022](http://go.microsoft.com/FWLink/?Linkid=223758), *Importing or Changing Your Environment Settings*).

By exporting your window layouts, you ensure that your preferred workspace configurations are preserved, offering peace of mind and convenience for future use.

**03.30 Stop the Toolbox from Auto-Populating from the Solution**

If you're experiencing slowdowns due to the Toolbox auto-populating from the solution, you can prevent this by following these steps:

1. **Accessing Options:**
   - Navigate to **Tools | Options | Windows Forms Designer** (Alt+T, O).

2. **Changing Auto-Population Setting:**
   - Within the Windows Forms Designer options, locate the setting named **AutoToolboxPopulate**.
   - Set its value to **False** to disable auto-population from the solution.

3. **Customizing Toolbox Items:**
   - When auto-population is disabled, you have the option to manually add custom items to the Toolbox.
   - Right-click on the Toolbox to access the context menu and select **Choose Items**.
   - From the dialog that appears, manually add the desired items to the Toolbox.

4. **Troubleshooting:**
   - If you're encountering issues where controls are not appearing automatically in the Toolbox, ensure that **AutoToolboxPopulate** is set to **True**.

Disabling auto-population can help streamline your workflow, especially in solutions with numerous projects. Should you wish to revert to auto-population in the future, simply set **AutoToolboxPopulate** back to **True**.

**03.31 Using External Tools**

External tools can be accessed and managed through the Tools menu in Visual Studio. Here's how to utilize external tools effectively:

1. **Accessing External Tools:**
   - Navigate to **Tools | External Tools** (Alt+T, E) to access the list of available external tools.

2. **Adding External Tools:**
   - To add additional external tools, click on **Add**.
   - Enter a descriptive title for the tool, such as "Visual Studio Command Prompt".

3. **Configuring Tool Properties:**
   - Click on **Properties** to configure the tool settings.
   - In the **Command** field, specify the path to the external tool or use system variables like `%comspec%` to refer to the command prompt.
   - Provide necessary arguments in the **Arguments** field. You can refer to the properties of the external tool for this information.
   - Optionally, specify the **Initial Directory** where the tool should start up.
   - Choose additional options such as:
     - **Use Output Window:** Redirects tool output to the Output window.
     - **Treat Output As Unicode:** Select if the tool returns Unicode output.
     - **Prompt For Arguments:** Enables modification of arguments before execution.
     - **Close On Exit:** Determines whether the tool window closes upon exit.

4. **Finalizing Configuration:**
   - Once configured, click **OK** to add the external tool to the list.

By adding external tools to Visual Studio, you can enhance your workflow and access commonly used utilities directly from within the IDE.

**03.32 Create Keyboard Accelerators for External Tools**

After adding external tools to the Visual Studio Tools menu, you may want to assign accelerator keys for quick keyboard access. Here's how to do it:

1. **Accessing External Tools Menu:**
   - Go to **Tools | External Tools** (Alt+T, E) to view the list of external tools.

2. **Understanding Accelerator Keys:**
   - Press **Alt+T** to access the Tools menu.
   - Notice that certain letters in the menu items are underlined. These underlined letters represent accelerator keys.
   - For example, in the "Create GUID" tool, the letter "G" is underlined. Pressing **Alt+T** followed by **G** activates this tool.

3. **Assigning Accelerator Keys:**
   - To assign an accelerator key to an external tool, insert an ampersand (&) before any character in the tool's title.
   - The character immediately following the ampersand becomes the accelerator key for that tool.
   - Ensure that each tool entry in the menu has a unique accelerator key assigned.

By assigning accelerator keys to external tools, you can streamline your workflow and access these tools quickly using keyboard shortcuts.

**03.33 Exporting Your Command Window Aliases and External Tools List**

When exporting settings in Visual Studio, it's essential to ensure that Command Window Aliases and External Tools List are included, as they are not imported by default. Here's how to export these settings separately:

1. **Accessing Import and Export Settings:**
   - Go to **Tools | Import and Export Settings** (Alt+T, I) to initiate the settings export process.

2. **Selecting Exported Settings:**
   - Choose **Export Selected Environment Settings** and click **Next**.

3. **Choosing Settings to Export:**
   - Uncheck the **All Settings** option.
   - Select the **Command Window Aliases** and **External Tools List** checkboxes.

4. **Completing the Export Process:**
   - Proceed through the wizard, following the prompts.
   - Give your exported file a logical name, such as "Command Aliases and External Tools List".

By exporting these settings separately, you ensure that you have an extra copy that can be easily imported when needed, avoiding any oversight during the import process.

**03.34 Creating and Using a Macro**

Macros in Visual Studio allow you to automate repetitive tasks. Here's how to create and use a macro:

1. **Recording a Macro:**
   - Press **Ctrl+Shift+R** to start recording the macro.
   - Perform the desired actions, such as adding a new class to the project and adding comments.
   - Stop recording by pressing **Ctrl+Shift+R** again.

2. **Saving the Macro:**
   - Go to **Tools | Macros | Save Temporary Macro**.
   - Name the macro, e.g., "MakeBubba", in the Macro Explorer.

3. **Testing the Macro:**
   - Create a new project.
   - Access the Macro Explorer using **Alt+F8**.
   - Right-click the saved macro and choose **Run**.
   - Verify that the macro performs the desired actions, such as creating a new class and adding comments.

4. **Viewing Macro Code:**
   - To view the code behind the macro, right-click the macro in the Macro Explorer and choose **Edit**.
   - Review and edit the macro code as needed. The code is typically easy to read and understand.

5. **Optional: Assigning a Shortcut Key:**
   - Visit vstipTool0066 to learn how to assign a shortcut key to the macro for quicker access.

By creating and using macros, you can automate repetitive tasks in Visual Studio, saving time and improving efficiency.

**03.35 Visual Studio Image Library**

The Visual Studio Image Library provides developers with a comprehensive collection of images that can be used in applications. Here's an overview of the library:

1. **Location:**
   - The images are stored in a .zip file located at:
     - **"C:\Program Files\Microsoft Visual Studio <version>\Common7\VS<version>ImageLibrary\1033"**
     - For example, in VS2010: **"C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\VS2010ImageLibrary\1033"**

2. **Types of Files:**
   - **Source Files:** Used with image editors to create or customize icons.
   - **Output Files:** Composite images ready for immediate use by developers.

3. **Image Library Contents:**
   - **Common Elements:** Source files consisting of various sizes of individual elements on transparent backgrounds. Useful for creating custom icons.
   - **Actions:** Output file images representing verbs. Organized by format, size, and style.
   - **Animations:** Contains common animations in .avi and .gif formats.
   - **Annotations_Buttons:** Images for notifications, actions, or object states, separated by format and style.
   - **Objects:** Output images representing nouns, commonly used in tree views or list views. Available in various sizes and colors.

4. **Using the Images:**
   - Images should be used for their original intent.
   - Ensure consistency with the description provided in the readme document found in each folder.
   - Use appropriate formats and styles based on your application's requirements.

The Visual Studio Image Library offers a wide range of images for developers to enhance the visual appeal and functionality of their applications.