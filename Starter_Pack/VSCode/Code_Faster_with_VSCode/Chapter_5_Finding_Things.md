**Chapter 5: Finding Things**

- **Introduction:**
  - Describes the frustration of not being able to find something in code.
  - Emphasizes the importance of efficient search features in Visual Studio for effective code navigation and development.

- **Quote:**
  - "I am in hopes, then, that we may find the object of our search thus. I imagine that our state, being rightly organized, is a perfectly good state." - Plato, "The Republic"

- **Key Points:**
  - Efficient code navigation is crucial for software development.
  - Mastery of search features saves time and enhances productivity.

- **Topics Covered:**
  - Different types of searches in Visual Studio.
  - Techniques for finding specific code elements.
  - Strategies for replacing code.

- **Purpose:**
  - Provides guidance on using Visual Studio's search features effectively.
  - Aims to improve developers' ability to navigate and manage code efficiently.
  - Enhances productivity and reduces frustration by enabling quick and accurate code location and modification.

**05.01 Repeat Your Last Search**

- **Default Shortcuts:**
  - F3 (next)
  - Shift+F3 (previous)

- **Versions Supported:**
  - 2005, 2008, 2010

- **Command:**
  - Edit.FindNext
  - Edit.FindPrevious

- **Purpose:**
  - Quickly repeat the last find operation.
  - Enables efficient navigation through search results.

- **Steps:**
  1. Verify that the last Find operation appears in the Find combo box on the Standard toolbar.
  2. Press F3 to move to the next occurrence of the search term, or Shift+F3 to move to the previous occurrence.
  3. Continue pressing the respective shortcut keys as needed to navigate through the search results and locate the desired content.

**05.02 Using Quick Find**

- **Default Shortcut:**
  - Ctrl+F

- **Versions Supported:**
  - 2005, 2008, 2010

- **Command:**
  - Edit.Find

- **Purpose:**
  - Provides a quick and versatile way to find specific content within code.
  - Offers various search options and customization for efficient navigation.

- **Steps:**
  1. Press Ctrl+F to open Quick Find, a tool window that can be moved and docked like other tool windows.
  2. Choose the type of find operation from the Quick Find drop-down menu:
     - **Find What:** Enter the search term manually or select from previous searches.
     - **Look In:** Determine the scope of the search, such as the current document, project, or solution.
     - **Find Options:** Customize the search with options like matching case, whole word, searching up, and using regular expressions or wildcards.
  3. Optionally, utilize the Expression Builder button for advanced search options when using regular expressions or wildcards.
  4. Use the **Find Next** button to navigate to the next instance of the search term.
  5. Consider using the **Bookmark All** button to place bookmarks at all locations where the search term is found, with caution due to potential bookmark overload.

**05.03 Using a Simple Quick Replace**

- **Default Shortcut:**
  - Ctrl+H

- **Versions Supported:**
  - 2005, 2008, 2010

- **Command:**
  - Edit.Replace

- **Purpose:**
  - Facilitates quick and simple find and replace operations within code.

- **Steps:**
  1. Press Ctrl+H to open Quick Replace, a tool window similar to Quick Find.
  2. Choose the type of replace operation from the Quick Replace drop-down menu.
     - **Find What:** Enter the search term to find.
     - **Replace With:** Enter the replacement text.
     - **Look In:** Determine the scope of the search.
     - **Find Options:** Customize the search criteria.
  3. Use the **Find Next** button to navigate to the next instance of the search term.
  4. Use the **Replace** button to replace the currently selected instance.
  5. Use the **Replace All** button to replace all instances of the search term throughout the document or scope.
  6. Pay attention to the confirmation dialog after using Replace All to ensure the expected number of replacements was made.

**05.04 Hide the Quick Find and Quick Replace Tool Window After the First Match**

- **Shortcut to Access Options:**
  - Alt, T, O

- **Menu Path:**
  - Tools | Options | Environment | Find and Replace

- **Versions Supported:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0010

- **Purpose:**
  - Enables the option to automatically hide the Quick Find or Quick Replace tool window after the first match is found.

- **Steps:**
  1. Navigate to Tools | Options | Environment | Find and Replace.
  2. Check the box labeled "Hide Find And Replace Window After A Match Is Located For Quick Find Or Quick Replace".

- **Note:**
  - This feature can be useful for improving workflow efficiency, especially when you want to continue using shortcut keys after the first match is found.

**05.05 Undo Quick Replace and Replace in Files**

- **Default Shortcut:**
  - Ctrl+Z; Alt+Backspace

- **Menu Path:**
  - Edit | Undo

- **Command:**
  - Edit.Undo

- **Versions Supported:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0020

- **Purpose:**
  - To undo changes made through Quick Replace or Replace in Files operations.

- **Steps to Undo Quick Replace:**
  1. Press Ctrl+Z or Alt+Backspace to undo changes made through Quick Replace.
  2. The changes made by the Quick Replace operation will be reversed.

- **Conditions for Undo:**
  - For Quick Replace:
    - After performing a Replace All operation, documents are marked with an asterisk in the file name tab.
    - Undoing (Ctrl+Z) reverses all the changes made by the Replace All operation.

- **Steps to Undo Replace in Files:**
  1. After performing a Replace in Files operation, ensure that "Keep Modified Files Open After Replace All" option is unchecked.
  2. Clicking Replace All without selecting this option will open a dialog box.
  3. Check the option "Replace All Will Open All Files With Changes For Editing" to enable undoing of all changes.
  4. Press Ctrl+Z or Alt+Backspace to undo changes made by Replace in Files.
  5. The changes made through Replace in Files operation will be reversed.

- **Note:**
  - Undoing Quick Replace and Replace in Files operations is straightforward and allows for reverting changes efficiently.

**05.06 Using the Find Combo Box Keyboard Shortcuts**

- **Versions Supported:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0019

- **Purpose:**
  - Utilize keyboard shortcuts associated with the Find Combo Box in Visual Studio for various tasks such as finding strings, running commands, navigating to specific lines or files, and setting breakpoints.

- **Default Keyboard Shortcuts:**
  - **Find (Ctrl+D):**
    - Used to find strings.
  - **Run Command (Ctrl+/):**
    - Executes commands entered into the Find Combo box.
  - **Go To Line (Ctrl+G):**
    - Navigates to a specific line number.
  - **Go To File (Ctrl+Shift+G):**
    - Jumps to a specific file within the solution or INCLUDE path.
  - **Set a Breakpoint (F9):**
    - Sets breakpoints at the selected function name.

- **Visual Basic 6 Specifics:**
  - No unique shortcuts; follows the default shortcuts.

- **Visual C# 2005 Specifics:**
  - Utilizes Ctrl+/ for running commands.

- **Visual C++ 2 Specifics:**
  - Introduces Alt+A for finding in addition to Ctrl+F.

- **Visual C++ 6 Specifics:**
  - No unique shortcuts; follows the default shortcuts.

- **Visual Studio 6 Specifics:**
  - Utilizes Ctrl+Shift+F for finding.

- **Usage:**
  - Access the Find Combo Box with the designated shortcut.
  - Enter search terms, commands, line numbers, or file names.
  - Utilize the respective keyboard shortcuts to execute the desired action:
    - Find (Ctrl+D)
    - Run Command (Ctrl+/)
    - Go To Line (Ctrl+G)
    - Go To File (Ctrl+Shift+G)
    - Set a Breakpoint (F9)

- **Additional Notes:**
  - F9 sets breakpoints only in open documents.
  - Repeat actions as needed based on search results or commands entered.

**05.07 Using Incremental Search**

- **Versions Supported:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0001

- **Purpose:**
  - Utilize incremental search to quickly locate text within the current document without the need for dialog boxes or mouse interaction.

- **Default Keyboard Shortcuts:**
  - **Incremental Search (Ctrl+I):**
    - Initiates incremental search mode.
  - **Visual Basic 6 Specifics:**
    - Uses Alt+I for incremental search.
  - **Visual C# 2005 Specifics:**
    - Follows the default Ctrl+I shortcut for incremental search.
  - **Visual C++ 2 Specifics:**
    - Follows the default Ctrl+I shortcut for incremental search.
  - **Visual C++ 6 Specifics:**
    - Follows the default Ctrl+I shortcut for incremental search.
  - **Visual Studio 6 Specifics:**
    - No unique shortcut; incremental search functionality is accessed through the default Ctrl+I.
  - **Windows Shortcut:**
    - Alt+E, V, S

- **Usage:**
  - Press Ctrl+I to initiate incremental search mode.
  - Begin typing the text to search for; the cursor jumps to the first match.
  - Observe the binoculars icon in the editor, indicating the direction of the search (up or down).
  - View search details in the status bar.
  - Press Ctrl+I again to jump to the next occurrence of the search string.
  - Utilize additional options within incremental search mode:
    - **Move to the next match in the file:** Ctrl+I
    - **Reverse the direction of the search:** Ctrl+Shift+I
    - **Remove a character from the search string:** Backspace
    - **Stop the incremental search:** Esc

- **Additional Notes:**
  - Incremental search allows hands-on keyboard operation without reliance on mouse interaction.
  - Provides efficient navigation through the document to find specific text occurrences.

**05.08 Search the Currently Selected String Without the Find Window**

- **Default Shortcut:**
  - **Find Next (Ctrl+F3):**
    - Initiates a search for the next occurrence of the currently selected string.
  - **Find Previous (Ctrl+Shift+F3):**
    - Initiates a search for the previous occurrence of the currently selected string.

- **Visual Basic 6:**
  - Follows the default shortcuts for finding next and previous occurrences.

- **Visual C# 2005:**
  - Utilizes the default shortcuts for finding next and previous occurrences.

- **Visual C++ 2:**
  - Utilizes the default shortcuts for finding next and previous occurrences.

- **Visual C++ 6:**
  - Utilizes the default shortcuts for finding next and previous occurrences.

- **Visual Studio 6:**
  - Utilizes the default shortcuts for finding next and previous occurrences.

- **Windows:**
  - No specific shortcut assigned.

- **Command:**
  - **FindNextSelected:**
    - Command to find the next occurrence of the currently selected string.
  - **FindPreviousSelected:**
    - Command to find the previous occurrence of the currently selected string.

- **Supported Versions:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0003

- **Purpose:**
  - Provides a quick way to find the next or previous occurrence of a selected string without opening the Find dialog box.

- **Usage:**
  - Place the cursor within the word you wish to search.
  - Press Ctrl+F3 to search for the next occurrence.
  - Press Ctrl+Shift+F3 to search for the previous occurrence.
  - The status bar displays search parameters for reference.

- **Additional Notes:**
  - Settings for the search can be modified in the Find dialog box (Ctrl+F).
  - After initiating the search, use F3 (next) or Shift+F3 (previous) to continue searching as needed.

**05.09 Find In Files: Find Options**

- **Default Shortcut:**
  - **Find In Files (Ctrl+Shift+F):**
    - Initiates the Find In Files dialog box to search for text across multiple files.

- **Visual Basic 6:**
  - Follows the default shortcut for initiating Find In Files.

- **Visual C# 2005:**
  - Utilizes the default shortcut for initiating Find In Files.

- **Visual C++ 2:**
  - Utilizes the default shortcut for initiating Find In Files.

- **Visual C++ 6:**
  - Utilizes the default shortcut for initiating Find In Files.

- **Visual Studio 6:**
  - No specific shortcut assigned.

- **Windows:**
  - Alt, E, F, I

- **Menu:**
  - Edit | Find and Replace | Find in Files

- **Command:**
  - Edit.FindinFiles

- **Supported Versions:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0013

- **Purpose:**
  - Facilitates searching for specific information across multiple files within a Visual Studio project.

- **Usage:**
  - Press Ctrl+Shift+F to open the Find In Files dialog box.
  - Set various options to customize the search parameters according to your requirements.
  - Search for text by typing in the Find What box or selecting from previous searches.
  - Utilize additional options such as Match case, Match whole word, and Use for advanced search operations.
  - Specify the scope of the search using the Look in drop-down list, which includes options like Current Project, Entire Solution, Choose Search Folders, and Look At These File Types.
  - Enable Include sub-folders to search within the current directory and all its subdirectories.

- **Additional Notes:**
  - Options such as Regular Expressions and Wildcards provide advanced search capabilities.
  - Refer to vstipFind0005 for customizing search folders and file types in Find In Files.

**05.10 Find In Files: Result Options**

- **Default Shortcut:**
  - **Find In Files (Ctrl+Shift+F):**
    - Opens the Find In Files dialog box for searching text across multiple files within a Visual Studio project.

- **Visual Basic 6:**
  - Follows the default shortcut for initiating Find In Files.

- **Visual C# 2005:**
  - Utilizes the default shortcut for initiating Find In Files.

- **Visual C++ 2:**
  - Utilizes the default shortcut for initiating Find In Files.

- **Visual C++ 6:**
  - Utilizes the default shortcut for initiating Find In Files.

- **Visual Studio 6:**
  - No specific shortcut assigned.

- **Windows:**
  - Alt, E, F, I

- **Menu:**
  - Edit | Find and Replace | Find in Files

- **Command:**
  - Edit.FindinFiles

- **Supported Versions:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0014

- **Purpose:**
  - Describes the options available for managing and navigating search results obtained through the Find In Files operation.

- **Usage:**
  - After performing a Find In Files operation, navigate through search results using F8 (next) and Shift+F8 (previous) shortcuts.
  - Utilize the Find Results windows to view and manage search results, with each search operation replacing the contents of the previous find.
  - Clear the results in a Find Results window manually by clicking the Clear All button.
  - Display file names only in search results by enabling the appropriate option.
  - Additional customization of displayed results is possible, as detailed in vstipFind0002.

- **Additional Notes:**
  - The Find Results windows toolbar provides buttons for navigating to the next and previous items in the results list.
  - The Keep Modified Files Open After Replace All option does not apply to Find In Files and is always disabled during find operations.
  

**05.11 Replace In Files: Basic Options**

- **Default Shortcut:**
  - **Replace In Files (Ctrl+Shift+H):**
    - Opens the Replace In Files dialog box for replacing text across multiple files within a Visual Studio project.

- **Visual Basic 6:**
  - Follows the default shortcut for initiating Replace In Files.

- **Visual C# 2005:**
  - Utilizes the default shortcut for initiating Replace In Files.

- **Visual C++ 2:**
  - Utilizes the default shortcut for initiating Replace In Files.

- **Visual C++ 6:**
  - Utilizes the default shortcut for initiating Replace In Files.

- **Visual Studio 6:**
  - Utilizes the default shortcut for initiating Replace In Files.

- **Windows:**
  - Alt, E, F, S

- **Menu:**
  - Edit | Find and Replace | Replace in Files

- **Command:**
  - Edit.ReplaceinFiles

- **Supported Versions:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0015

- **Purpose:**
  - Describes the options available for replacing text in files using the Replace In Files feature.

- **Find Options:**
  - Utilizes the same options as Find In Files, allowing users to set parameters for the search operation.

- **Replace With:**
  - Allows users to specify the text to replace the found text with, supporting both simple literal replacements and more complex expressions.

- **Result Options:**
  - Mirrors the options available in Find In Files, with the addition of the "Keep Modified Files Open After Replace All" option.
    - This option keeps modified files open after changes are made, enabling users to review changes or make additional manual modifications.

- **Execution Buttons:**
  - Find Next: Locates the next instance of the search string.
  - Replace: Replaces the current instance of the search string and moves to the next instance.
  - Replace All: Replaces all instances of the search string in all files within the specified scope.
    - Caution: Users should pay attention to the scope of the operation to avoid unintended changes to files.
  - Skip File: Skips the current file when multiple files are included in the search scope, continuing the search in the next file.

**05.12 Go To Definition for Cascading Style Sheets**

- **Default Shortcut:**
  - **Go To Definition (F12):**
    - Navigates to the definition of the selected item, including CSS class names within a Visual Studio project.

- **Visual Basic 6:**
  - Utilizes F12 for Go To Definition.
  - Also supports Shift+F2 as an alternative shortcut.

- **Visual C# 2005:**
  - Utilizes F12 for Go To Definition.

- **Visual C++ 2:**
  - Supports F11 and Alt+F1 for Go To Definition.

- **Visual C++ 6:**
  - Utilizes F12 for Go To Definition.

- **Visual Studio 6:**
  - Does not have a specific shortcut for Go To Definition.

- **Windows:**
  - Does not have a specific shortcut for Go To Definition.

- **Command:**
  - Edit.GoToDefinition

- **Supported Versions:**
  - 2008, 2010

- **Code Reference:**
  - vstipFind0021

- **Purpose:**
  - Explains how to use the Go To Definition feature to navigate to the definition of CSS class names within a Visual Studio project.

- **Procedure:**
  1. Place the cursor inside the CSS class name.
  2. Press F12 or right-click and choose "Go To Definition."
  3. Visual Studio navigates to the CSS definition and highlights it.

- **Usage:**
  - Allows users to quickly review the definition of CSS classes and make changes as needed.

**05.13 How to Use Navigate To**

- **Default Shortcut:**
  - **Navigate To (Ctrl+,):**
    - Opens the Navigate To dialog box, allowing users to search for symbols within the project.

- **Visual Basic 6:**
  - Utilizes Ctrl+, for Navigate To.

- **Visual C# 2005:**
  - Utilizes Ctrl+, for Navigate To.

- **Visual C++ 2:**
  - Utilizes Ctrl+, for Navigate To.

- **Visual C++ 6:**
  - Utilizes Ctrl+, for Navigate To.

- **Visual Studio 6:**
  - Utilizes Ctrl+, for Navigate To.

- **Windows:**
  - Alt+E, . (period) can be used to access Navigate To.

- **Menu Path:**
  - Edit | Navigate To

- **Command:**
  - Edit.NavigateTo

- **Supported Versions:**
  - 2010

- **Code Reference:**
  - vstipTool0006

- **Purpose:**
  - Introduces the Navigate To dialog box, which enables users to search for symbols within the project.

- **Procedure:**
  1. Press Ctrl+, to open the Navigate To dialog box.
  2. Enter the symbol you are looking for.
  3. Review the search results, which include symbols containing the entered letters.
  4. Optionally, select the Hide External Items option to limit the search to the local project only.

- **Usage:**
  - Facilitates quick navigation to symbols within the project.
  - Searches are case-insensitive and support Pascal Case for better matching.
  - Does not support special logic or characters such as wildcards, Boolean operators, or regular expressions.

**05.14 Understanding Find Symbol**

- **Default Shortcut:**
  - **Find Symbol (Alt+F12):**
    - Opens the Find Symbol dialog box, facilitating the search for symbols such as objects, definitions, and references.

- **Visual Basic 6:**
  - Utilizes Alt+F12 for Find Symbol.

- **Visual C# 2005:**
  - Utilizes Alt+F12 for Find Symbol.

- **Visual C++ 2:**
  - Utilizes Alt+F12 for Find Symbol.
  - Additionally, Ctrl+F11 and Ctrl+Alt+F11 can be used.

- **Visual C++ 6:**
  - Utilizes Alt+F12 for Find Symbol.
  - Also supports Ctrl+Shift+Y for Find Symbol.

- **Visual Studio 6:**
  - Utilizes Alt+F12 for Find Symbol.

- **Windows:**
  - Alt+E, F, Y can be used to access Find Symbol.

- **Menu Path:**
  - Edit | Find and Replace | Find Symbol

- **Command:**
  - Edit.FindSymbol

- **Supported Versions:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0011

- **Purpose:**
  - Introduces the Find Symbol dialog box, enabling users to search for symbols like objects, definitions, and references.

- **Procedure:**
  1. Press Alt+F12 to open the Find Symbol dialog box.
  2. Enter the search string for the symbol you are looking for.
  3. Set the search criteria and options such as Match, Whole Word, Prefix, Substring, and Match Case.
  4. Choose the scope of the search under Look In, including All Components, Framework X / Silverlight X, My Solution, and Custom Component Sets.
  5. Initiate the search by clicking Find All.
  6. Review the search results, which include icons indicating the type of symbol found.
  7. Navigate through the results using F8 for forward and Shift+F8 for backward navigation.

- **Usage:**
  - Facilitates quick search for symbols like objects, definitions, and references within the project.
  - Offers various search options and criteria for refining the search results.
  - Provides navigational shortcuts for ease of browsing through the search results.

**05.15 Find Symbol Results Shortcuts**

- **Default:**
  - **Go to Definition (F12):**
    - Takes you to the definition of the symbol in your code.
  - **Go to Declaration (Ctrl+F12):**
    - *Note: Applicable to C++ only.* Takes you to the declaration of the symbol in your code.
  - **Go to Reference (Shift+F12):**
    - Finds all references to the symbol.
  - **Copy (Ctrl+C):**
    - Copies the fully qualified name for the selected symbol to the clipboard.
  - **Copy (Ctrl+Insert):**
    - Copies the fully qualified name for the selected symbol to the clipboard.
- **Visual Basic 6:**
  - Utilizes F12 for Go to Definition.
  - Utilizes Shift+F2 for Go to Definition.
  - Utilizes Ctrl+F12 for Go to Declaration.
  - Utilizes Alt+F2 for Find All References.
- **Visual C# 2005:**
  - Utilizes F12 for Go to Definition.
  - Utilizes Ctrl+F12 for Go to Declaration.
  - Utilizes Shift+F12 for Find All References.
  - Utilizes Ctrl+K, Ctrl+R for Find All References.
  - Utilizes Ctrl+K, R for Find All References.
- **Visual C++ 2:**
  - Utilizes F11 for Go to Definition.
  - Utilizes Alt+F1 for Go to Definition.
- **Visual C++ 6:**
  - Utilizes F12 for Go to Definition.
  - Utilizes Ctrl+F12 for Go to Declaration.
  - Utilizes Ctrl+Alt+F12 for Go to Declaration.
- **Visual Studio 6:**
  - Does not have a shortcut for Go to Definition.
  - Utilizes Ctrl+F12 for Go to Declaration.
- **Windows:**
  - Utilizes Alt+E, C for Copy.
- **Menu Path:**
  - Edit | Copy
- **Command:**
  - Edit.GoToDefinition; Edit.GoToDeclaration; Edit.FindAllReferences; View.BrowseDefinition; Edit.Copy; Edit.ClearAll
- **Supported Versions:**
  - 2005, 2008, 2010
- **Code Reference:**
  - vstipFind0012
- **Purpose:**
  - Provides a list of keyboard shortcuts and commands for navigating and managing symbol search results.
- **Procedure:**
  1. Use the respective shortcut keys to perform various actions on the symbol search results:
     - F12: Go to Definition
     - Ctrl+F12: Go to Declaration (C++ only)
     - Shift+F12: Find All References
     - Ctrl+C or Ctrl+Insert: Copy fully qualified name to clipboard
  2. Additionally, the Browse Definition option allows you to explore symbols in the Object Browser.
  3. Clear All option clears the Find Symbol Results window.

**05.15 Find Symbol Results Shortcuts**

- **Default:**
  - **Go to Definition (F12):**
    - Takes you to the definition of the symbol in your code.
  - **Go to Declaration (Ctrl+F12):**
    - *Note: Applicable to C++ only.* Takes you to the declaration of the symbol in your code.
  - **Go to Reference (Shift+F12):**
    - Finds all references to the symbol.
  - **Copy (Ctrl+C):**
    - Copies the fully qualified name for the selected symbol to the clipboard.
  - **Copy (Ctrl+Insert):**
    - Copies the fully qualified name for the selected symbol to the clipboard.
- **Visual Basic 6:**
  - Utilizes F12 for Go to Definition.
  - Utilizes Shift+F2 for Go to Definition.
  - Utilizes Ctrl+F12 for Go to Declaration.
  - Utilizes Alt+F2 for Find All References.
- **Visual C# 2005:**
  - Utilizes F12 for Go to Definition.
  - Utilizes Ctrl+F12 for Go to Declaration.
  - Utilizes Shift+F12 for Find All References.
  - Utilizes Ctrl+K, Ctrl+R for Find All References.
  - Utilizes Ctrl+K, R for Find All References.
- **Visual C++ 2:**
  - Utilizes F11 for Go to Definition.
  - Utilizes Alt+F1 for Go to Definition.
- **Visual C++ 6:**
  - Utilizes F12 for Go to Definition.
  - Utilizes Ctrl+F12 for Go to Declaration.
  - Utilizes Ctrl+Alt+F12 for Go to Declaration.
- **Visual Studio 6:**
  - Does not have a shortcut for Go to Definition.
  - Utilizes Ctrl+F12 for Go to Declaration.
- **Windows:**
  - Utilizes Alt+E, C for Copy.
- **Menu Path:**
  - Edit | Copy
- **Command:**
  - Edit.GoToDefinition; Edit.GoToDeclaration; Edit.FindAllReferences; View.BrowseDefinition; Edit.Copy; Edit.ClearAll
- **Supported Versions:**
  - 2005, 2008, 2010
- **Code Reference:**
  - vstipFind0012
- **Purpose:**
  - Provides a list of keyboard shortcuts and commands for navigating and managing symbol search results.
- **Procedure:**
  1. Use the respective shortcut keys to perform various actions on the symbol search results:
     - F12: Go to Definition
     - Ctrl+F12: Go to Declaration (C++ only)
     - Shift+F12: Find All References
     - Ctrl+C or Ctrl+Insert: Copy fully qualified name to clipboard
  2. Additionally, the Browse Definition option allows you to explore symbols in the Object Browser.
  3. Clear All option clears the Find Symbol Results window.

**05.16 Replace in Files: Tagged Expressions**

- **Default Shortcut:**
  - Ctrl+Shift+H

- **Visual Basic 6:**
  - Utilizes Ctrl+Shift+H.

- **Visual C# 2005:**
  - Utilizes Ctrl+Shift+H.

- **Visual C++ 2:**
  - Utilizes Ctrl+Shift+H.

- **Visual C++ 6:**
  - Utilizes Ctrl+Shift+H.

- **Visual Studio 6:**
  - Utilizes Ctrl+Shift+H.

- **Windows Shortcut:**
  - Alt+E, F, S

- **Menu Path:**
  - Edit | Find and Replace | Replace in Files

- **Command:**
  - Edit.ReplaceinFiles

- **Supported Versions:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0016

- **Purpose:**
  - Demonstrates the usage of tagged expressions in the Replace in Files feature.

- **Procedure:**
  1. Access the Replace in Files dialog.
  2. In the Replace With field, enter the replacement text.
  3. Use curly brackets to denote tagged expressions (e.g., `{expression}`).
  4. Tagged expressions are numbered sequentially starting from 1.
  5. Use the notation `\n` to refer to the nth tagged expression.
  6. Example:
     - Original text: `bubbajones`
     - Replace With: `{bubba}{jones}`
     - Result: `jones`

- **Additional Information:**
  - Tagged expressions can be used for complex replacements, especially when combined with regular expressions.

**05.17 Customize Results in Find In Files Searches**

- **Default Shortcut:**
  - Ctrl+Shift+F

- **Visual Basic 6:**
  - Utilizes Ctrl+Shift+F.

- **Visual C# 2005:**
  - Utilizes Ctrl+Shift+F.

- **Visual C++ 2:**
  - Utilizes Ctrl+Shift+F.

- **Visual C++ 6:**
  - Utilizes Ctrl+Shift+F.

- **Visual Studio 6:**
  - Does not have a specific shortcut.

- **Windows Shortcut:**
  - Alt+E, F, I

- **Menu Path:**
  - Edit | Find and Replace | Find in Files

- **Command:**
  - Edit.FindinFiles

- **Supported Versions:**
  - 2005, 2008, 2010

- **Code Reference:**
  - vstipFind0002

- **Purpose:**
  - Provides instructions for customizing Find In Files results format.

- **Procedure:**
  1. Open RegEdit.exe.
  2. Navigate to HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Find.
  3. Add a new string named Find Result Format with the desired format value.
  4. Run a Find In Files search in Visual Studio to see the changes.
  
- **Variables:**
  - Files:
    - $p: path
    - $f: filename
    - $v: drive/UNC share
    - $d: directory
    - $n: name
    - $e: extension
  - Location:
    - $l: line
    - $c: column
    - $x: end column if on first line, else end of first line
    - $L: span end line
    - $C: span end column
  - Text:
    - $0: matched text
    - $t: text of first line
    - $s: summary of hit
    - $T: text of spanned lines
  - Char:
    - \n: newline
    - \s: space
    - \t: tab
    - \\: backslash
    - \$: dollar sign