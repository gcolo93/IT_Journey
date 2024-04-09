**04.01 Insert Documents to the Right of Existing Tabs**

- **Description:**
  By default, Visual Studio 2010 opens new tabs to the left of existing ones. However, there's an option to change this behavior and insert newly opened documents to the right of existing tabs.

- **Shortcut (WINDOWS):** Alt,T, O

- **Menu:** Tools | Options | Environment | Documents

- **Versions:** 2010

- **Code:** vstipEnv0001

- **Steps:**
  1. Open Visual Studio.
  2. Navigate to Tools > Options > Environment > Documents.
  3. Select the "Insert Documents To The Right Of Existing Tabs" option.
  4. Click OK to apply the changes.

- **Result:**
  Newly opened tabs will appear to the right of existing tabs in the file channel.

**04.02 Recent Files**

- **Description:**
  Visual Studio keeps track of recently opened files and projects for quick access. You can customize the number of recent files and projects displayed in the Window and File menus.

- **Shortcut (WINDOWS):** Alt,W, [1,2,3, etc] (windows); Alt,F, F, [1,2,3, etc] (files); Alt,F, J, [1,2,3, etc] (projects and solutions)

- **Menu:** 
  - Tools | Options | General | Recent files;
  - Window | [1,2,3, etc]; 
  - File | Recent Files | [1,2,3, etc];
  - File | Recent Projects and Solutions | [1,2,3, etc]

- **Command:** Tools.Options

- **Versions:** 2005, 2008, 2010

- **Code:** vstipEnv0013

- **Steps:**
  1. Open Visual Studio.
  2. Go to Tools > Options > General > Recent files.
  3. Adjust the number of recent files and projects as per your preference.
  4. Click OK to apply the changes.

- **Result:**
  The number of recent files and projects displayed in the Window and File menus will be updated according to your settings.

**04.03 Working with Documents on Multiple Monitors**

- **Description:**
  Visual Studio now supports detachable document windows, allowing you to move them to another monitor. This feature enhances productivity, especially for users with multiple monitors.

- **Shortcut (WINDOWS):** Alt,W, F (float); Alt,W,T (dock)

- **Menu:** 
  - Window | Float;
  - Window | Dock as Tabbed Document

- **Command:** 
  - Window.Float;
  - Window.DockasTabbedDocument

- **Versions:** 2010

- **Code:** vstipTool0004

- **Steps:**
  1. To detach a document window, click and drag the tab for the document window out of the IDE.
  2. Alternatively, go to Window > Float on the menu bar.
  3. To reattach a floating window, right-click the title bar of the document and choose Dock As Tabbed Document.
  4. Another method is to click and drag the document window by its title bar into the IDE. The guide diamond appears, indicating where the window will dock.
  5. Hold down the left mouse button and move your cursor over the middle item in the guide diamond.
  6. Release the mouse button, and the window will dock at the selected location.

- **Result:**
  You can now detach document windows and move them to another monitor for improved multitasking and workflow organization.

**04.04 Navigate Open Document Windows**

- **Description:**
  Navigating between open document windows is essential for efficient coding. Visual Studio provides keyboard shortcuts for moving to the next or previous document window without using the mouse.

- **Shortcuts:**
  - **DEFAULT:**
    - Ctrl+F6: Move to the next document window
    - Ctrl+Shift+F6: Move to the previous document window
  - **VISUAL C++ 2:**
    - Ctrl+F6: Move to the next document window
    - Ctrl+Tab: Move to the next document window
    - Ctrl+Shift+F6: Move to the previous document window
    - Ctrl+Shift+Tab: Move to the previous document window
  - **VISUAL STUDIO 6:**
    - Ctrl+F6: Move to the next document window
    - Ctrl+Tab: Move to the next document window
    - Ctrl+Shift+F6: Move to the previous document window
    - Ctrl+Shift+Tab: Move to the previous document window

- **Command:** 
  - Window.NextDocumentWindow
  - Window.PreviousDocumentWindow

- **Versions:** 2005, 2008, 2010

- **Code:** vstipTool0013

- **Steps:**
  1. If you have multiple files open in the file channel, you can navigate between them using keyboard shortcuts.
  2. Press Ctrl+F6 to move forward to the next document window.
  3. Press Ctrl+Shift+F6 to move backward to the previous document window.

- **Result:**
  You can easily switch between open document windows without using the mouse, improving coding efficiency and workflow.

**04.05 Close the Current Document Window**

- **Description:**
  Closing the current document window from the keyboard is a convenient way to manage open files in Visual Studio. This action prompts to save changes if any modifications have been made.

- **Shortcuts:**
  - **DEFAULT:** Ctrl+F4
  - **VISUAL BASIC 6:** Ctrl+F4
  - **VISUAL C# 2005:** Ctrl+F4
  - **VISUAL C++ 2:** Ctrl+F4
  - **VISUAL C++ 6:** Ctrl+F4
  - **VISUAL STUDIO 6:** Ctrl+F4
  - **WINDOWS:** Alt+F, C (Note: This shortcut is specific to Windows, not Visual Studio)
  
- **Menu:**
  - File | Close

- **Command:** 
  - Window.CloseDocumentWindow
  - File.Close

- **Versions:** 2005, 2008, 2010

- **Code:** vstipTool0014

- **Steps:**
  1. Ensure the focus is on the document window you want to close.
  2. Press Ctrl+F4 on the keyboard.
  3. If there are unsaved changes, Visual Studio prompts you to save them before closing the document.

- **Result:**
  The current document window is closed, providing a quick way to manage open files in Visual Studio without using the mouse.

**04.06 Open a File Location from the File Tab**

- **Description:**
  Opening a file location from the file tab allows users to quickly navigate to the folder containing the file in Windows Explorer. This feature is helpful for managing project files and directories.

- **Shortcuts:**
  - **DEFAULT/WINDOWS:** Alt+- (minus sign), O (This shortcut is specific to Visual Studio 2010)
  - **VISUAL BASIC 6:** No shortcut available
  
- **Command:** 
  - File.OpenContainingFolder
  - Window.ShowDockMenu

- **Versions:** 2005, 2008, 2010

- **Code:** vstipEdit0014

- **Steps:**
  1. Right-click on the file's tab in Visual Studio.
  2. Choose "Open Containing Folder" from the context menu.
  3. Windows Explorer opens, displaying the folder containing the file.
  
- **Result:**
  The user is directly navigated to the folder containing the file in Windows Explorer, allowing for easy management and manipulation of files within the project directory.

**04.07 Open the File Menu Drop-Down List from Your Keyboard**

- **Description:**
  Opening the File menu drop-down list from the keyboard provides an alternative way to navigate through a large number of open files. This feature allows users to view files as a list instead of tabs, making it easier to locate specific files.

- **Shortcuts:**
  - **DEFAULT/VISUAL BASIC 6/VISUAL C# 2005/VISUAL C++ 2/VISUAL C++ 6/VISUAL STUDIO 6:** Ctrl+Alt+Down Arrow
  - **WINDOWS:** No shortcut available

- **Command:** Window.ShowEzMDIFileList

- **Versions:** 2005, 2008, 2010

- **Code:** vstipEnv0003

- **Functionality:**
  - When there are numerous files open, accessing the File menu drop-down list from the keyboard provides a convenient way to navigate through them.
  - Users can activate the drop-down list by pressing Ctrl+Alt+Down Arrow.
  - The drop-down list supports type-ahead functionality, allowing users to quickly filter and select files by typing the first few characters of their names.
  - For example, typing "S" selects "SomethingToDo.cs", and typing "ST" jumps to "Start Page".
  
- **Result:**
  Users can efficiently navigate through a large number of open files using the File menu drop-down list, enhancing productivity and ease of access.

**04.08 Using the IDE Navigator**

- **Description:**
  Navigating through documents and tool windows within the Integrated Development Environment (IDE) is crucial for efficient development. The IDE Navigator provides shortcuts and functionality to move among active files and tool windows seamlessly.

- **Shortcuts:**
  - **DEFAULT/VISUAL BASIC 6/VISUAL C# 2005/VISUAL C++ 2/VISUAL C++ 6/VISUAL STUDIO 6:**
    - Ctrl+Tab: Navigate forward in active files
    - Ctrl+Shift+Tab: Navigate backward in active files
    - Alt+F7: Navigate forward in active tool windows
    - Alt+Shift+F7: Navigate backward in active tool windows
  - **WINDOWS:** No shortcuts available

- **Command:**
  - Window.NextDocumentWindowNav
  - Window.PreviousDocumentWindowNav
  - Window.NextToolWindowNav
  - Window.PreviousToolWindowNav

- **Versions:** 2005, 2008, 2010

- **Code:** vstipTool0023

- **Functionality:**
  - The IDE Navigator facilitates the swift movement between active files and tool windows, enhancing the development experience.
  - Users can press Ctrl+Tab to navigate forward and Ctrl+Shift+Tab to navigate backward through active files.
  - Additionally, Alt+F7 allows users to navigate forward, and Alt+Shift+F7 to navigate backward through active tool windows.
  - The IDE Navigator also supports document preview, showing images to the right of the lists. This feature can be enabled in Visual Studio 2010.
  - Holding down the Ctrl key keeps the IDE Navigator visible, allowing users to interact with it using the mouse or arrow keys.
  - The navigator consists of two main areas: Active Files and Active Tool Windows.
    - Active Files: Enables navigation through currently open files, displaying file names and their full paths.
    - Active Tool Windows: Displays all currently open tool windows, with the list dynamically changing based on usage.
  
- **Result:**
  Efficient navigation through active files and tool windows in the IDE is achieved, improving productivity and workflow for developers.

**04.09 Multiple Views of the Same Document**

- **Description:**
  Sometimes, it's useful to view a large document in multiple areas simultaneously, such as on multiple monitors. This feature allows users to open multiple views of the same document, facilitating better analysis and comparison.

- **Activation:**
  - **WINDOWS:**
    - Shortcut: Alt+W, N
    - Menu: Window | New Window
  - **Command:** Window.NewWindow

- **Versions:** 2005, 2008, 2010

- **Code:** vstipEnv0016

- **Special Note for Visual Basic (VB) Users in Visual Studio 2010:**
  - This feature is disabled by default in VB due to historical reasons. However, it can be enabled manually at the user's own risk.
  - To enable this feature for VB users in Visual Studio 2010, navigate to “HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\10.0\Languages\Language Services\Basic\” in the registry.
  - Rename the "Single Code Window Only" registry key to something else (e.g., [your initials here] Single Code Window Only).
  - Restart Visual Studio to apply the changes.

- **Functionality:**
  - Users can open multiple views of the same document by selecting Window | New Window from the menu bar.
  - Each new window created displays a duplicate view of the current document, with ":1" appended to the existing document tab text and ":2" appended to the name on the new document tab.
  - This feature allows users to have as many duplicate views as needed, facilitating multitasking and analysis.
  - Note: The maximum number of duplicate views may vary, with testing indicating support for up to 150 views.

- **Result:**
  Enabling multiple views of the same document enhances productivity by allowing users to analyze and compare different sections of a document simultaneously.

**04.10 Closing Just the Selected Files You Want**

- **Description:**
  When working with multiple files open in the IDE, users may want to selectively close only certain files while keeping others open. This feature allows users to close specific files without closing all open files.

- **Activation:**
  - **WINDOWS:**
    - Shortcut: Alt+W, W
    - Menu: Window | Windows
  - **Command:** Window.Windows

- **Versions:** 2005, 2008, 2010

- **Code:** vstipEnv0010

- **Functionality:**
  - Users can access the Window | Windows menu option to manage open files.
  - Upon selecting Window | Windows, a dialog or window opens displaying a list of currently open files.
  - Users can select specific files they want to close by using Ctrl+Left-click to multi-select.
  - After selecting the desired files, users can click on the "Close Window(s)" option to close only the selected files, leaving the rest of the open files untouched.

- **Result:**
  - This feature provides users with greater control over managing open files in the IDE, allowing them to close only the files they no longer need while keeping other files open for continued work.
  - It enhances productivity by streamlining the file management process, especially when dealing with a large number of open files simultaneously.

**04.11 Understanding the File Open Location**

- **Description:**
  This tip explains how Visual Studio determines the default file open location and how users can control this behavior through the IDE settings.

- **Activation:**
  - **MENU:** Tools | Options | Environment | Documents

- **Versions:** 2005, 2008, 2010

- **Code:** vstipEnv0035

- **Explanation:**
  - Visual Studio by default opens files using the directory of the currently active document.
  - This behavior is controlled by the "Open File Using Directory Of Currently Active Document" option, accessible via Tools | Options | Environment | Documents.
  - Users can toggle this feature by clearing the checkbox associated with the option.
  - When disabled, Visual Studio uses the DefaultFileOpenLocation stored in the registry (HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>) as the default file open location.
  - The DefaultFileOpenLocation is updated each time a file is successfully opened using the Open File dialog box, but the change is not written to the registry until Visual Studio is closed.

- **Purpose:**
  - Provides insight into how Visual Studio determines the default file open location.
  - Offers users the ability to customize file open behavior according to their preferences.
  - Helps users understand and manage IDE settings related to file operations.

**04.12 Show Previous Versions**

- **Description:**
  This tip introduces the "Show Previous Versions" feature available in Windows Vista and later operating systems (excluding Home Editions). It allows users to access prior versions of files and directories, providing a way to revert changes without using source control.

- **Versions:** 2008, 2010

- **Code:** vstipEnv0036

- **Note:**
  - For more detailed information and instructions on activating this feature, users are directed to visit http://windows.microsoft.com/en-US/windows-vista/Previous-versions-of-files-frequently-asked-questions.

- **Explanation:**
  - Windows Vista and later versions (excluding Home Editions) offer the "Show Previous Versions" option.
  - This feature is accessible in various applications and dialog boxes, such as Notepad and the Open Project dialog box.
  - When activated, users can view prior versions of the current directory, including solutions, projects, and files.
  - It provides users with the ability to open and restore previous versions of files and directories.

- **Purpose:**
  - Offers a solution for users who want to revert changes to their code without using source control.
  - Demonstrates how to access and utilize the "Show Previous Versions" feature in Windows.
  - Provides users with an alternative method for managing file versions and recovering lost or unwanted changes.

**04.13 Using Custom File Extension Associations**

- **Description:**
  This tip explains how to associate custom file extensions with specific editing experiences in Visual Studio. It allows users to define the behavior of Visual Studio when opening files with custom extensions.

- **Versions:** 2005, 2008, 2010

- **Code:** vstipEnv0038

- **Instructions:**
  - To associate a custom file extension, navigate to Tools | Options | Text Editor | File Extension.
  - Input the custom extension along with the desired editing experience.
  - Users can add, modify, or remove entries from the list as needed.

- **Purpose:**
  - Provides users with a way to customize the editing experience for files with custom extensions.
  - Enables users to define specific behaviors for Visual Studio when opening files with custom extensions.
  - Offers flexibility in managing file associations, enhancing the overall development workflow.
