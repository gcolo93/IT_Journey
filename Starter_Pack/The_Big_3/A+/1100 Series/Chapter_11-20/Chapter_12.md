- **Chapter 12: Working with Operating Systems**
    - Windows is powerful, easy to use, surprisingly idiot proof, backwardly compatible, and robust.
    - A large part of Windows' power is hidden under the hood in programs and processes.
    - Technicians need to understand and work with these hidden processes.
    - This chapter covers:
        - The Registry
        - Windows 10 features and tools
        - Using Windows 10 Control Panel utilities and settings
        - Windows 11 features differing from Windows 10
        - Identifying common features and tools of macOS.

- **Registry**
    - The Registry is a critical database storing information about a PC.
    - Accessing the Registry
    - Registry Components
        - HKEY_CLASSES_ROOT
        - HKEY_CURRENT_USER
        - HKEY_LOCAL_MACHINE
        - HKEY_USERS
        - HKEY_CURRENT_CONFIG
    - Manual Registry Edits

- **Command-Line Registry Editing Tools**
    - reg
    - regsvr32

- **Your Basic Windows Toolset**
    - System Configuration
    - Windows Settings
    - Update & Security
    - Personalization
    - Apps
    - Privacy
    - System
    - Devices
    - Network & Internet
    - Gaming
    - Accounts
    - Control Panel

- **Control Panel**
    - System
    - Sound

- **Indexing Options**
  - Indexing is the process of gathering information about files to facilitate faster searching.
  - It creates a directory for easy file access.
  - Not all folders are indexed by default, but users can select files and folders to be indexed using the Indexing Options tool in the Control Panel.

- **Ease of Access**
  - Provides accessibility features for users with physical limitations.
  - Includes features like Magnifier, Narrator, On-Screen Keyboard, Sticky Keys, and Filter Keys.

- **Administrative Tools**
  - Allows access to a set of applets for system administration tasks.
  - Found in File Explorer and serves as a super applet launcher for various tools like Disk Cleanup and Defragment.

- **File Explorer Options**
  - Personalize File Explorer settings.
  - Options include showing hidden files, hiding file extensions, customizing views, and adjusting general preferences.

- **Processes, Applications, and Services Tools**
  - **Task Manager**
    - Manages applications, processes, and services.
    - Provides detailed information about running processes and system performance.

  - **Resource Monitor**
    - Offers detailed insight into system resource usage.
    - Organizes information by process ID (PID) and provides advanced monitoring features.

  - **Microsoft Management Console (MMC)**
    - Framework for launching specialized programs called snap-ins.
    - Snap-ins include Performance Monitor, Task Scheduler, and Local Users and Groups.
    - Allows users to create custom consoles by adding snap-ins.

- **Performance Monitor (perfmon.msc)**
  - Tracks system performance over time.
  - Monitors objects and counters related to CPU, memory, disk, and network usage.
  - Provides real-time data display and reporting features.
  - Offers Data Collector Sets for creating custom reports and scheduling monitoring tasks.

- **Event Viewer (eventvwr.msc)**
  - Windows' default program for monitoring and logging system events.
  - Accessed via Control Panel | Administrative Tools or by typing eventvwr.msc in the search bar.
  - Provides access to various logs including Application, Security, Setup, and System.
  - Logs events of different levels: Verbose, Information, Warning, Error, and Critical.
  - Custom Views feature allows for personalized event monitoring based on user needs.

- **Certificate Manager (certmgr.msc)**
  - Manages digital certificates used for encrypting data in Windows.
  - Accessed via Control Panel | Administrative Tools or by typing certmgr.msc in the search bar.
  - Provides access to all certificates on the system.
  - Primarily used for encryption purposes, typically not accessed unless instructed to do so.

- **macOS Preferences and Features**
  - **System Preferences**
    - Neatly organizes system settings under various preference panes.
    - Contains a search box for easy navigation.
    - Common preference panes include Displays, Network, Printers & Scanners, Privacy, Accessibility, Time Machine, Apple ID, AirDrop, Spotlight, Keychain, and FileVault.
  
  - **Displays**
    - Configures display settings such as resolution, brightness, and multiple display arrangement.
  
  - **Network**
    - Manages network connections and advanced settings.
  
  - **Printers & Scanners**
    - Configures printers, scanners, and all-in-one devices.
  
  - **Privacy**
    - Controls privacy permissions for apps and processes.
  
  - **Accessibility**
    - Configures macOS for users with vision, hearing, or motor control needs.
  
  - **Time Machine**
    - Backs up and restores files and folders on Mac.
  
  - **Apple ID**
    - Manages synchronization of data and preferences among multiple devices.
  
  - **AirDrop**
    - Shares files between Apple devices in proximity.
  
  - **Spotlight**
    - Global system search tool for files, preferences, web pages, contacts, and more.
  
  - **Keychain**
    - Manages passwords and certificates securely.
  
  - **FileVault**
    - Encrypts storage devices to protect data from unauthorized access.
    - Provides additional security layer by requiring login to unlock encrypted storage.