- **Chapter 15: Working with the Command-Line Interface**
    - Introduction
    - Importance of Command Line for Techs
    - Certification Exam Relevance (CompTIA A+)
    - Popularity of Command Line
- **Deciphering the Command-Line Interface**
    - Analogy with Voice Assistants
    - Indication of Command Readiness
    - Interaction with Commands
- **Getting the Most out of the CLI**
    - Discoverability in GUI vs. CLI
    - Importance of Note-taking
- **Shells**
    - Definition and Function of Shells
    - Varieties of Shells (PowerShell, Command Prompt, bash, zsh, fish, csh)
- **Accessing the Command-Line Interface in Windows**
    - Accessing Command Prompt
    - Opening GUI Programs from Command Line
    - Running Commands with Elevated Privileges
- **Accessing the Command-Line Interface in macOS and Linux**
    - Opening Terminal in macOS
    - Opening Terminal in Linux
    - Running Commands with Elevated Privileges in UNIX-like systems
- **The Prompt**
    - Significance of the Prompt
    - Differences in Prompt Presentation (Windows vs. UNIX-like systems)
- **Drives and Folders**
    - Organization of Drives and Folders in Windows
    - Organization of Drives and Folders in UNIX-like systems
- **Mastering Fundamental Commands**
    - Syntax and Switches Structure
    - Strategies for Learning Commands
    - Types of Commands (builtins vs. standalone external commands)
- **Command Types**
    - Identification of Command Types (builtins vs. standalone external commands)
    - Obtaining Help for Commands in Windows and UNIX-like systems
- **dir Command (Windows) / ls Command (UNIX-like)**
    - Listing Contents of Directories
    - Overview of Command Options
- **Changing Directory Focus: The cd Command**
    - Functionality and Usage in Windows and UNIX-like systems

- **Errors Are Good!**
  - Error messages, including command-prompt errors and GUI errors, are beneficial.
  - Error messages provide information about mistakes, facilitating learning and troubleshooting.
  - Experimenting with intentional mistakes helps in familiarizing oneself with error messages.

- **Changing Directories with the `cd` Command**
  - Running `cd \` or `cd /` changes the directory focus to the root directory.
  - The `cd` command followed by a directory path changes the prompt to that directory.
  - Absolute paths begin with `/` in UNIX and `\` in Windows.
  - Relative paths without a leading slash specify a subdirectory of the current working directory.
  - `cd ..` moves the focus up a single directory level.

- **Moving Between Drives**
  - In Windows, typing the drive letter followed by a colon (`:`) switches focus to another drive.
  - For example, `E:` focuses on the E drive.
  - Nonexistent drive letters prompt an error message.
  - In macOS and Linux, drives are mounted as folders within a single hierarchy.
  - Access drives and removable media through folders like `/Volumes` in macOS and `/mnt` in Linux.

- **Making Directories: The `md`/`mkdir` Command**
  - Use `md` in Windows and `mkdir` in all operating systems to create directories.
  - For example, `md practice` creates a directory named "practice."
  - Ensure the prompt is focused on the desired directory before executing the `md` or `mkdir` command.

- **Removing Directories: The `rd`/`rmdir` and `rm` Command**
  - Use `rd` or `rmdir` in Windows and `rm` in UNIX to delete directories.
  - Removing directories with contents prompts a warning or confirmation message.
  - Use the `-r` (recursive) switch with `rm` to remove directories and their contents in UNIX.

- **Running a Program**
  - In Windows, type the program's name followed by `ENTER` to run it.
  - For example, `mmc` executes the `mmc.exe` program.
  - In UNIX-like systems, ensure the executable's directory is in the PATH or specify the path explicitly to run a program.

- **Investigating Files**
  - Use the `file` command in UNIX to identify file types.
  - The `cat` command displays the contents of a file in the terminal.
  - The `more` command is a simple pager for viewing file contents.

- **Using Wildcards to Locate Files**
  - Wildcards (`*` and `?`) match filenames or parts of filenames in commands.
  - Use wildcards with commands like `dir` in Windows and `ls` in UNIX to filter files.

- **Deleting Files**
  - Use `del` or `erase` in Windows and `rm` in UNIX to delete files.
  - Wildcards can be used to delete multiple files simultaneously.
  - Double-check before deleting files, as there's no built-in recovery mechanism from the command line.

- **Copying and Moving Files**
    - Crucial for all technicians
    - Copy command (cp) and move command (mv) in UNIXes
    - Five-step process:
        1. Focus the prompt on the directory containing the file(s)
        2. Type copy/move (Windows) or cp/mv (macOS and Linux) and a space
        3. Type the name(s) of the file(s) to be copied/moved (with or without wildcards) and a space
        4. Type the path of the new location for the file(s)
        5. Press ENTER
    - Example:
        - Windows: Copying a file to a USB thumb drive
        - macOS or Linux: Moving files with specific extensions to a new location

- **Pruning and Grafting Folder Trees**
    - Command-line shines for copying or moving files in multiple directories
    - **xcopy** (Windows) for copying files from multiple directories
    - **robocopy** (Windows) for efficient file and folder management, especially across networks
    - **cp** and **mv** (Linux) for copying and moving folders and contents

- **Assorted Windows Commands**
    - **chkdsk (/f /r)**: Scans, detects, and repairs file system issues and errors
    - **format**: Formats volumes from the command line
    - **hostname**: Displays the computer's name
    - **winver**: Displays version information about Windows
    - **gpupdate**: Updates group policies on a workstation
    - **gpresult**: Shows summary results for security policies applied to a user or computer
    - **sfc**: Scans, detects, and restores important Windows system files
    - **shutdown**: Shuts down or reboots a local or remote computer

- **Keyboard Shortcuts**
    - Accesses previous commands in CLI (Windows)
    - Useful for command history

- **Assorted macOS and Linux Commands**
    - **top**: Displays running processes, focusing on resource-hungry ones
    - **ps**: Provides detailed information about running processes
    - **grep**: Searches through text files or command output to find specific information

- **find Command:**
  - **Overview:**
    - UNIX workhorse for searching files and directories.
    - Outputs a list based on specified criteria.
  - **Criteria Examples:**
    - File size (bigger, smaller, exact).
    - Creation or modification date.
    - Permissions.
    - Matching name pattern.
  - **Usage:**
    - Use `find` alone to list all files in current directory.
    - Use `find /etc/` to search a specific directory.
  - **Wildcard Note:**
    - Use `"*.pdf"` to prevent wildcard expansion.
- **Package Managers (apt-get and yum):**
  - **Overview:**
    - Revolutionized software installation on UNIX-like systems.
    - Tools for installing, updating, and managing software.
  - **APT (apt-get):**
    - For Debian-based distros (e.g., Ubuntu, Mint).
    - Commands: `update`, `install`, `upgrade`.
    - Keeps system up-to-date for security.
  - **YUM (yum):**
    - For Red Hat-based distros (e.g., Fedora, CentOS).
    - Similar commands: `update`, `install`.
  - **Note:**
    - Alternative package managers exist (e.g., Chocolatey, Homebrew).
- **nano Text Editor:**
  - **Overview:**
    - Command-line text editor, simpler than vi.
    - Basic editing commands and shortcuts.
    - Useful for quick text edits without GUI.
- **dd Command:**
  - **Overview:**
    - Creates exact block-by-block images of storage.
    - Usage examples: Copying drives, backing up, wiping disks.
    - Requires caution due to potential data loss.
- **df Command:**
  - **Overview:**
    - Displays disk space usage.
    - Helpful for diagnosing storage issues.
    - Usage: `df` or `df -h` for human-readable format.
- **shutdown Command:**
  - **Overview:**
    - Shuts down or restarts system from terminal.
    - Commands: `shutdown now` for immediate shutdown.
    - Useful for scheduled system maintenance.
- **Scripting:**
  - **Overview:**
    - Automates repetitive tasks using shell scripts.
    - Gradual automation, starting with basic tasks.
    - Use cases: Basic automation, restarting machines, backups, etc.
  - **Script Types:**
    - Shell scripts and general scripting languages.
    - Common languages and file extensions listed.
  - **Automation Habits:**
    - Note-taking, recognizing automation opportunities.
    - Automate gradually, avoiding perfectionism.
  - **Risks and Considerations:**
    - Fragility of scripts, potential for errors.
    - Risks of running untrusted scripts, changing settings.
    - Exercise caution, test scripts before deployment.
- **Beyond A+:**
  - **Anatomy of a Script:**
    - Programming languages instruct computers on data operations.
    - Syntax rules dictate valid operations.
    - Awareness of data types and potential errors essential.

- **Data Types**
  - Programming languages use data types to differentiate between numbers and words.
  - Data types include integers (numbers) and strings (words).
  - Strings are sequences of characters, often enclosed in single or double quotes.
  - Different programming languages have rules for manipulating strings, such as joining or breaking them.
  - Some languages have additional data types for specific situations, like dates or fractional numbers.

- **Variables**
  - Variables are named values used to store data for later use.
  - They allow the computer to remember values and reuse them in the program.
  - Variables are essential for storing data like phone numbers, enabling reuse without re-entering values.

- **Conditionals and Basic Loops**
  - Conditionals control when and how different commands run based on specified conditions.
  - Keywords like "if" specify conditions and associated code blocks.
  - Basic loops repeat code until a condition is met or no longer met.
  - Control structures like "for" and "while" indicate loops in programming languages.

- **Comments**
  - Comments are special text inserted into scripts or programs for human readability.
  - They provide explanations and context for code segments.
  - Different languages have their own syntax for comments, but they serve a common purpose.
  - Comments are essential for understanding code, especially for future reference or collaboration.

- **Environment Variables**
  - Environment variables store important values for running programs.
  - They include systemwide settings and user-defined configurations.
  - Environment variables enable scripts to adapt to different systems without modification.
  - Understanding and utilizing environment variables is crucial for scripting across various platforms.