**Operating Systems Overview 1.1**

**Why do you need an OS?**

- Control interaction between components
  - Memory, hard drives, keyboard, CPU
- A common platform for applications
  - You’re going to do some work, right?
- Humans need a way to interact with the machine
  - The “user interface”

**Standard OS features**

- File management
  - Add delete, rename
- Application support
  - Memory management, swap file management
- Input and Output support
  - Printers, keyboards, hard drives, USB drives
- Operating system configuration and management tools

**Microsoft Windows**

- Major market presence
- Many different versions
  - Windows 7, Windows 10, Windows Server
- Advantages
  - Large industry support
  - Broad selection of OS options
  - Wide variety of software support
- Disadvantages
  - Large install base provides a big target exploitation
  - Large hardware support can create challenging integration exercises

**Apple macOS**

- macOS
  - Desktop OS running on Apple hardware
- Advantages
  - Easy to use
  - Extremely compatible
  - Relatively fewer security concerns
- Disadvantages
  - Requires Apple hardware
  - Less industry support than the PC platform
  - Higher initial hardware cost



**Linux**

- Free Unix-compatible software system
  - Unix-like, but not Unix
- Many (many) different distributions
  - Ubuntu, Debian, Red Hat / Fedora
- Advantages
  - Cost: Free.
  - Works on a wide variety of hardware
  - Passionate and active user community
- Disadvantages
  - Limited driver support, especially with laptops
  - Limited support options

**Operating system technologies**

- 32-bit vs 64-bit
  - Processor specific
- 32-bit processors can store 2^32 = 4,294,967,296 values
- 64-bit processors can store 2^64 = 18,446,744,073,709,551,616 values
  - 4 GB vs. 17 billion GB
  - The OS has a maximum supported value
- Hardware drivers are specific to the OS version (32-bit / 64-bit)
  - 32-bit (x86), 64-bit (x64)
- 32-bit OS cannot run 64-bit apps
  - But 64-bit OS can run 32-bit apps
- Apps in a 64-bit Windows OS
  - 32-bit apps: \Program Files (x86)
  - 64-bit apps: \Program Files

**Windows on a mobile device**

- Microsoft Windows 10
  - Fully-featured tablets
- Many different manufacturers
  - Touchscreen computer
  - Keyboards
  - Pen stylus
- Windows Mobile
  - No longer in active development
  - No support after December 2019

**Google Android**

- Google Android
  - Open Handset Alliance
  - Open-source OS, based on Linux
  - Supported by many different manufacturer’s devices
- Android Apps
  - Apps are developed on Windows, macOS, and Linux with the Android SDK
  - Apps available from Google Play
  - Apps also available from third-party sites (i.e., Amazon Appstore)

**Apple iOS**

- Apple iOS
  - Apple iPhone and Apple iPad OS
  - Based on Unix
  - Closed-source - No access to source code
  - Exclusive to Apple products
- iOS Apps
  - Apps are developed with iOS SDK on macOS
  - Apps must be approved by Apple before release
  - Apps are available to users in the Apple App Store

**Chrome OS**

- Google’s operating system
  - Based on the Linux kernel
- Centers around Chrome web browser
  - Most apps are web-based
- Many different manufacturers
  - Relatively less expensive
- Relies on the cloud
  - Connect to the Internet

**Vendor-specific limitations**

- End-of-life
  - Different companies set their own EOL policies
- Updating
  - iOOS, Android and Windows 10 check and prompt for updates
  - Chrome OS will update automatically
- Compatibility between operating systems
  - Some movies and music can be shared
- Almost no direct application compatibility
  - Fortunately, many apps have been built to run on different OSes
  - Some data files can be moved across systems
  - Web-based apps have potential





**An Overview of Windows 7 1.2**

**Windows 7**

- Released October 22, 2009
  - Mainstream support ended January 13, 2015
  - Extended support until January 14, 2020
- Very similar to Windows Vista
  - Maintained the look and feel
  - Used the same hardware and software
  - Increased performance
- Updated features
  - Libraries
  - HomeGroup
  - Pinned taskbar

**Windows 7 editions**

- Windows 7 Starter
- Windows 7 Home Basic
- Windows 7 Home Premium
- Windows 7 Ultimate
- Windows 7 Professional
- Windows 7 Enterprise

**Windows 7 Starter**

- Built for netbooks
- No DVD playback of Windows Media Center
- No Windows Aero
- No Internet Connection Sharing (ICS)
- No IIS (Internet Information System) Web Server
- No enterprise technologies
  - No Domain connection, BitLocker, EFS (Encrypting File system), etc.
- Only a 32-bit version, maximum of 2 GB of RAM

**Windows 7 Home Premium**

- The consumer edition
  - DVD playback
  - Windows Aero
  - Internet Connection Sharing
  - IIS Web Server
- No enterprise technologies
  - No domain connection, BitLocker, EFS etc.
- X64 version supports 16 GB of RAM and 2 physical processors

**Windows 7 Ultimate**

- Complete functionality
- Domain support Remote Desktop, EFS
- All enterprise technologies
  - BitLocker
- X64 version supports 192 GB of RAM
- Same features as Windows 7 Enterprise
  - But for the home user

**Windows 7 Professional**

- Same features as Home Premium
- Can connect to a Windows Domain
- Supports Remote Desktop Host and EFS
- Missing enterprise technologies
  - No BitLocker
- X64 version supports 192 GB of RAM

**Windows 7 Enterprise**

- Sold only with volume licenses
  - Designed for very large organizations
- Multilingual User Interface packages
- BitLocker Drive Encryption

**Windows 7 hardware requirements**

- Windows 7 Minimum Requirements (x86)
  - Processor / CPU: 1 GHz processor
  - Memory: 1 GB RAM
  - Free disk space: 16 GB
  - Video: DirectX 9 graphics device with WDDM 1.0 or higher driver
- Windows 7 Minimum Requirements (x64)
  - Processor / CPU: 1 GHz processor
  - Memory: 2 GB RAM
  - Free disk space: 20 GB
  - Video: DirectX 9 graphics device with WDDM 1.0 or higher driver

**An Overview of Windows 8 and 8.1 1.2**

**Windows 8 and 81**

- Windows 8
  - Available October 26, 2012
  - New user interface
  - No traditional “Start” button
- Windows 8.1
  - Released October 17, 2013
  - A free update to Windows 8
    - Not an upgrade
- Mainstream support ended January 9, 2018
  - Extended support ends January 10, 2023

**Windows 8/8.1 editions**

- Windows 8/8.1 (Core)
- Windows 8/8.1 Pro
- Windows 8/8.1 Enterprise

**Windows 8/8.1 Core**

- A basic version for the home
  - X86 and x64 version
- Microsoft account integration
  - Login to your computer and all of your services
- Windows Defender
  - Integrated anti-virus and anti-malware
- Windows Media Player
  - Play audio CD and DVDs

**Windows 8/8.1 Pro**

- The professional version
  - Similar to Windows 7 Professional / Ultimate
- Full support for BitLocker and EFS
  - Full-disk and file-level encryption
- Join a Windows Domain
  - Support for IT management
- Group Policy support
  - Centralized management of Windows devices

**Windows 8/8.1 Enterprise**

- Available to “Software Assurance” customers
  - Large volume licenses
- Adds enterprise features
  - AppLocker
  - Windows To Go
  - DirectAccess
  - BranchCache

**Windows 8/8.1 processor requirements**

- PAE (Physical Address Extension)
  - 32-bit processors can use more than 4 GB of physical memory
- NX (NX Processor Bit)
  - Protect against malicious software
- SSE2 (Streaming SIMD Extensions 2)
  - A standard processor instruction set
  - Used by third-party applications and drivers

**Windows 8/8.1 hardware requirements**

- Windows 8/8.1 Minimum Requirements (x86)
  - Processor / CPU: 1 GHz processor with support for PAE, NX, and SSE2
  - Memory: 1 GB RAM
  - Free disk space: 16 GB
  - Video: DirectX 9 graphics device with WDDM driver
- Windows 8/8.1 Minimum Requirements (x64)
  - Processor / CPU: 1 GHz processor with support for PAE, NX, and SSE2
  - Memory: 2 GB RAM
  - Free disk space: 20 GB
  - Video: DirectX 9 graphics device with WDDM driver

**An Overview of Windows 10 1.2**

**Windows 10**

- Released on July 29, 2015
  - We skipped Windows 9
- A single platform
  - Desktops, laptops, tablets, phones all-in-one devices
- Upgrades were free for the first year
  - From Windows 7 and Windows 8.1
- Microsoft calls Windows 10 a “service”
  - Periodic updates to the OS
  - Instead of completely new versions

**Windows 10 Home**

- Home user
  - Retail sales
- Integration with Microsoft account
  - Microsoft OneDrive backup
- Windows Defender
  - Anti-virus and anti-malware
- Cortana
  - Talk to your operating system

**Windows 10 Pro**

- The business version of Windows
  - Additional management features
- Remote Desktop host
  - Remote control each computer
- BitLocker
  - Full disk encryption (FDE)
- Join a Windows domain
  - Group Policy management

**Windows 10 Education and Enterprise**

- Very similar features in both
  - Minor features differences
  - Volume licensing
- AppLocker
  - Control what applications can run
- BranchCache
  - Remote site file caching
- Granular User Experience (UX) control
  - Define the user environment
  - Useful for kiosk and workstation customization

**Windows 10 processor requirements**

- Same requirements as Windows 8/8.1
- PAE (Physical Address Extension)
  - 32-bit processors can use more than 4 GB of physical memory
- NX (NX Processor Bit)
  - Protect against malicious software
- SSE2 (Streaming SIMD Extensions 2)
  - A standard processor instruction set
  - Used by third-party applications and drivers

**Windows 10 hardware requirements**

- Windows10 Minimum Requirements (x86)
  - Processor / CPU: 1 GHz processor with support for PAE, NX, and SSE2
  - Memory: 1 GB RAM
  - Free disk space: 16 GB
  - Video: DirectX 9 graphics device with WDDM driver
- Windows 10 Minimum Requirements (x64)
  - Processor / CPU: 1 GHz processor with support for PAE, NX, and SSE2
  - Memory: 2 GB RAM
  - Free disk space: 20 GB
  - Video: DirectX 9 graphics device with WDDM driver

**Windows in the Enterprise 1.2**

**Windows at work**

- Large-scale support
  - Thousands of devices
- Security concerns
  - Mobile devices with important data
  - Local file shares
- Working on a spreadsheet
  - Watching a movie
- Geographical sprawl
  - Cache between sites

**Domain Services**

- Active Directory Domain Services
  - Large database of your network
- Distributed architecture
  - Many servers
  - Not suitable for home use
- Everything documented in one place
  - User accounts, servers volumes printers
- Many different uses
  - Authentication
  - Centralized management

**BitLocker and EFS**

- Data confidentiality
  - Encrypt important information
- Encrypting File System
  - Protect individual files and folders
  - Built-in to the NTFS files system
- BitLocker
  - Full Disk Encryption (FDE)
  - Everything on the drive is encrypted
  - Even the operating system
- Home and business use
  - Especially on mobile devices

**Media Center**

- Video, music, and television portal
  - Perfect for watching at home
  - Record shows from a TV tuner
  - Play music
  - Watch DVDs
- The center of your home entertainment center
  - Cable companies and other technologies were strong competition
- Discontinued by Microsoft
  - Not officially available in Windows 10

**Desktop styles**

- Your computer has many different uses
  - Those change depending on where you are
- Work
  - Standard desktop
  - Common user interface
  - Customization very limited
  - You can work at any computer
- Home
  - Complete flexibility
  - Background photos, colors, UI sizing

**Installing Operating Systems 1.3**

**Boot methods**

- USB storage
  - USB must be bootable
  - Computer must support booting from USB
- CD-ROM and DVD-ROM
  - A common media
- PXE (“Pixie”) - Preboot eXecution Environment
  - Perform a remote network installation
  - Computer must support booting with PXE
- NetBoot
  - Apple technology to boot macOS from the network
  - Similar concept to PXE
- Solid state drives / hard drives
  - Store many OS installation files
- External / hot swappable drive
  - Some external drives can mount an ISO image (DVD-ROM image)
  - Boot from USB
- Internal hard drive
  - Install and boot from separate drive
  - Create and boot from new partition

**Types of installations**

- Unattended installation
  - Answer Windows questions in a file (unattend.xml)
  - No installation interruptions
- In-place upgrade
  - Maintain existing applications and data
- Clean install
  - Wipe the slate clean and reinstall
  - Migration tool can help
- Image
  - Deploy a clone on every computer
- Repair installation
  - Fix problems with the Windows OS
  - Does not modify user files
- Multiboot
  - Run two or more operating systems from a single computer
- Recovery partition
  - Hidden partition with installation files
- Refresh / restore
  - Windows 8/10 feature to clean things up
  - Requires a recovery partition

**The disk partition**

- Separates the physical drive into logical pieces
  - Useful to keep data separated
  - Multiple partitions are not always necessary
- Useful for maintaining separate operating systems
  - Windows, Linux, etc.
- Formatted partitions are called volumes
  - Microsoft’s nomenclature

**MBR partition style**

- MBR (Master Boot Record)
  - The old standby, with all of the old limitations
- Primary
  - Bootable partitions
  - Maximum of four primary partitions per hard disk
  - One of the primary partitions can be marked as Active
- Extended
  - Used for extending the maximum number of partitions
  - One extended partition per hard disk (optional)
  - Contains additional logical partitions
  - Logical partitions inside an extended partition are not bootable

**GPT partition style**

- GPT (GUID Partition Table)
  - Globally Unique Identifier
  - The latest partition format standard
- Requires a UEFI BIOS
  - Can have up to 128 partitions
- No need for extended partitions or logical drives

**Disk partitioning**

- The first step when preparing disks
  - May already be partitioned
    - Existing partitions may not always be compatible with your new operating system
- An MBR-style hard disk can have up to four partitions
- GUID partition tables support up to 128 partitions
  - Requires UEFI BIOS or BIOS-compatibility mode
  - BIOS-compatibility mode disables UEFI SecureBoot
- Be careful
  - Serious potential for data loss
  - This is not an everyday occurrence

**Storage types**

- Layered on top of the partition and file system
  - A Windows thing
- Basic disk storage
  - Available in DOS and Windows versions
  - Primary/extended partitions, logical drives
  - Basic disk partitions can’t span separate physical disks
- Dynamic disk storage
  - Available in all modern Windows versions
  - Span multiple disks to create a large volume
  - Split data across physical disks (striping)
  - Duplicate data across physical disks (mirroring)
    - Not all Windows versions support all capabilities

**Files systems**

- Before data can be written to the partition, it must be formatted
  - Build the foundation
- Operating systems expect data to be written in a particular format
  - FAT32 and NTFS is popular
- Many operating systems can read (and perhaps write) multiple files system types
  - FAT, FAT32 NTFS, exFAT, etc.



**FAT**

- FAT - File Allocation Table
  - One of the first PC-based file systems (circa 1980)
- FAT32 - File Allocation Table
  - Larger (2 terabyte) volume sizes
  - Maximum file size of 4 gigabytes
- exFAT - Extended File Allocation Table
  - Microsoft flash drive file system
  - Files can be larger than 4 gigabytes

**NTFS and CDFS**

- NTFS - NT File system
  - Extensive improvements over FAT32
  - Quotas, file compression, encryption symbolic links, large file support security, recoverability
- CDFS - Compact Disk File System
  - ISO 9660 standard
  - All operating systems can read the CD

**Other file systems**

- ext3
  - Third extended file system
  - Commonly used by the Linux OS
- ext4 
  - Fourth extended file system
  - An update to ext3
  - Commonly seen in Linux and Android OS
- NFS - Network File System
  - Access files across the network as if they were local
  - NFS clients available across many operating systems
- HFS+ / HFS Plus
  - Hierarchical File System
  - Also called Mac OS Extended
  - Replaced by Apple File System (APFS) in macOS High Sierra (10.13)
- Swap partition
  - Memory management
  - Frees memory by moving unused pages onto disk
  - Copies back to RAM when needed
  - Usually a fast drive or SSD

**Quick format vs. Full format**

- Quick format
  - Creates a new file tables
    - Looks like data is erased, but it’s not
  - No additional checks
- Quick format in Windows 7, 8/8.1, and 10
  - Use diskpart for a full format
- Full format
  - Writes zeros to the whole disk
    - Your data is unrecoverable
  - Checks the disk for bad sectors - Time consuming

**Other considerations**

- Load alternate third party drivers when necessary
  - Disk controller drivers, etc.
- Workgroup vs. Domain setup
  - Home vs. business
- Time/date/region/language settings
  - Where are you?
- Driver installation, software and windows updates
  - Load video drivers, install apps, update the OS
- Factory recovery partition
  - This can help you later

**Installing and Upgrading Windows 1.3**

**Prepare the boot drive**

- Know your drive
  - Is there data on the drive?
  - Has the drive been formatted?
  - What partitions are on the drive?
- Backup any old data
  - You may need that back someday
- Most partitioning and formatting can be completed during the installation
  - Clear the drive and start fresh

**Before the installation**

- Check minimum OS requirements
  - Memory, disk space, etc.
  - And the recommended requirements
- Run a hardware compatibility check
  - Runs when you perform an upgrade
  - Run manually from the Windows setup screen
  - Windows 10 Upgrade Checker
- Plan for installation questions
  - Drive/partition configuration, license keys, etc.
- Application compatibility
  - Check with the app developer

**Why upgrade?**

- Upgrade vs. Install
  - Upgrade - Keep files in place
  - Install - Start over completely fresh
- Maintain consistency
  - Customized configurations
  - Multiple local user accounts
- Upgrades save hours of time
  - Avoid application reinstall
  - Keep user data intact
  - Get up and running quickly
- Seamless and fast
  - Run from the DVD-ROM or USB flash

**Upgrade methods**

- In-place
  - Upgrade the existing OS
  - Keeps all applications, documentations, and settings
  - Start the setup from inside the existing OS
- Clean install
  - Wipe everything and reload
  - Backup your files
  - Start the setup by booting from the installation media

**Upgrading to Windows 10**

- Upgrade from the Windows 10 installation media
  - Downloadable versions are available from Microsoft
  - Includes a media creation tool
- You cannot upgrade x86 to x64
  - Or x64 to x86
  - Applies to all Windows versions
  - You’ll have to migrate instead

**Post-installation**

- Does it work?
  - If it doesn’t boot, there are bigger problems
  - Some testing is useful for unknown hardware configurations
- Additional installations
  - Service packs
  - Security patches
  - Security applications
  - Driver updates
  - Application updates

**Microsoft Command Line Tools 1.4**

**Privileges**

- Not all users can run all commands
  - Some information and tasks are for the administrator only
- Standard privileges
  - Run applications as normal user
  - This works fine for many commands
- Administrative/elevated privileges
  - You must be a member of the Administrators group
  - Right-click Command Prompt, choose Run as Administrator
  - Cmd, Ctrl+Shift+Enter

**Command line troubleshooting**

- Use “help” if you’re not sure
  - help dir
  - help chkdsk
- Also use:
  - [command] /?
- Close the prompt with “exit”

**File management**

- dir 
  - List files and directories
- cd 
  - Change working directory
  - Use backslash \ to specify volume or folder name
- . . 
  - Two dots/periods
  - The folder above the current folder

**shutdown**

- Shutdown a computer
  - And optionally restart
- shutdown /s  /t nn
  - Wait nn seconds, then shutdown
- shutdown /r /t nn
  - Shutdown and restart after nn seconds
- shutdown /a
  - Abort the countdown!

**dism**

- Deployment Image Servicing and Management tool
  - Manage Windows Imaging Formation (WIM) files
- Make changes to your image with DISM
  - Get information about an image
  - Update applications
  - Manage drivers
  - Manage updates
  - Mount an image

**sfc**

- System File Checker
  - Scan integrity of all protected system files

**Check Disk**

- chkdsk /f
  - Fixes logical file system errors on the disk
- chkdsk /r
  - Locates bad sectors and recovers readable information
  - Implies /f
- If volume is locked, run during startup

**DiskPart**

- Manage disk configurations


**TaskList and TaskKill**

- Manage tasks from the command line
  - No Task Manager required
- tasklist
  - Displays a list of currently running processes
  - Local or remote machine
- taskkill
  - Terminate tasks by process id (PID) or image name
    - TASKKILL /IM notepad.exe
    - TASKKILL /PID 1234 /T

**Managing Group Policy**

- Group Policy
  - Manage computers in an Active Directory Domain
  - Group Policy is usually updated at login
- gpupdate
  - Force a Group Policy update
  - gpupdate /target:{computer|user} /force
  - gpupdate /target:professor /force
- gpresult
  - Verify policy settings for a computer or user
  - gpresult /r
  - gpresult /user sgc/professor /v

**format**

- Formats a disk for use with Windows
  - Be careful, you can lose data

**copy (/v, /y)**

- /v - Verifies that new files are written correctly
- /y - Suppresses prompting to confirm you want to overwrite an existing destination file

**xcopy**

- Copies files and directory trees

**Robust Copy**

- robocopy
  - A better xcopy
- Included with Windows 7, 8.1, and 10

**Network Command Line Tools 1.4**

**ipconfig**

- Most of your troubleshooting starts with your IP address
  - Ping your local router/gateway
- Determine TCP/IP and network adapter information
  - And some additional IP details
- View additional configuration details
  - DNS servers, DHCP servers, etc.

**ping**

- Test reachability
  - determine round-trip time
  - Uses Internet Control Message Protocol (ICMP)
- One of your primary troubleshooting tools
  - Can you ping the host?
- Written by Mike Muuss in 1983
  - The sound made by sonar
  - Not an acronym for Packet INternet Groper
    - A backronym

**tracert**

- Determine the route a packet takes to a destination
  - Map the entire path
- Takes advantage of ICMP Time to Live Exceeded error message
  - The time in TTL refers to hops, not seconds or minutes
  - TTL=1 is the first router, TTL=2 is the second router, etc.
- Not all devices will reply with ICMP Time Exceeded messages
  - Some firewalls filter ICMP
  - ICMP is low-priority for many devices

**Flavors of traceroute**

- Not all traceroutes are the same
  - Minor differences in the transmitted payload
- Windows commonly sends ICMP echo requests
  - Receives ICMP time exceeded messages
  - And an ICMP echo reply from the final/destination device
  - Unfortunately, outgoing ICMP is commonly filtered
- Some operating systems allow you to specify the protocol used
  - Linux, Unix, macOS, etc.
- IOS devices send UDP datagrams over port 33434
  - The port number can be changed with extended options

**netstat**

- Network statistics
  - Many different operating systems
- netstat -a
  - Show all active connections
- netstat -b
  - Show binaries (Windows)
  - Requires elevation
- netstat -n
  - Do not resolve names

**nslookup**

- Lookup information from DNS servers
  - Canonical names, IP addresses, cache timers, etc.
- Lookup names and IP addresses
  - Many different options

**net**

- Windows network commands

**Common net commands**

- View network resources
  - net view \\<servername>
  - net view /workgroup:<workgroupname>
- Map a network share to a drive letter
  - net use h: \\<servername>\<sharename>
- View user account information and reset passwords
  - net user <username>
  - net user <username> \* /domain

**Windows Administrative Tools 1.5**

**Computer Management**

- A pre-built Microsoft Management Console
  - A predefined mix of plugins
  - Control Panel / Administrative Tools
  - mmc.exe
- A handy starting point
  - Events
  - User accounts
  - Storage management
  - Services
  - and more

**Device Manager**

- The OS doesn’t know how to talk directly to most hardware
- Device drivers are hardware specific and operating system specific
  - Windows 7 device drivers may not necessarily work in Windows 10
- Technical Support FAQ
  - “Have you updated the drivers?”
- Computer Management or devmgmt.msc

**Local users and groups**

- Users
  - Administrator
    - The Windows super-user
  - Guest
    - Limited access
  - Regular Users
- Groups
  - Administrators, Users, Backup Operators, Power Users, etc.

**Local Security Policy**

- Big companies have big security policies
  - Managed through Active Directory Group Policies
- Stand-alone computers aren’t managed through AD
  - You need local policies
- Not available in Home editions
  - Available in Professional / Pro, Ultimate, Enterprise

**Performance Monitor**

- Gather long-term statistics
  - Control Panel / Administrative Tools
- OS metrics
  - Disk, memory, CPU, etc.
- Set alerts and automated actions
  - Monitor and act
- Store statistics
  - Analyze long-term trends
- Built-in reports
  - View the data

**Services**

- Background process
  - No user interaction
  - File indexing, anti-virus, network browsing, etc.
- Useful when troubleshooting the startup process
  - Many services startup automatically
- Command-line control
  - net start, net stop
- Control Panel / Administrative Tools / Services
  - services.msc

**Task Scheduler**

- Schedule an application or batch file
  - Plan your future
- Includes predefined schedules
  - Click and go
- Organize
  - Manage with folders
- Control Panel / Administrative Tools / Task Scheduler

**Component Services**

- Microsoft COM+
  - Component Object Model
- Distributed applications
  - Designed for the enterprise
- Manage COM+ apps
  - Device COM+ Management
  - Event Viewer
  - Services

**ODBC Data Sources**

- Open Database Connectivity
- Application independence
  - Database and OS doesn’t matter
- Configure in Control Panel / Administrative tools
  - Users probably won’t need this

**Print Management**

- Control Panel / Administrative Tools / Print Management
- Manage printers
  - Share printers from one central console
- Add and manage printer drivers
  - Central management of 32-bit and 64-bit drivers

**Memory diagnostics**

- Is your memory working?
  - I don’t remember
- May be notified automatically
  - Or launched manually
- Multiple passes
  - Try to find the bad chip/module
- Control Panel / Administrative Tools

**Event Viewer**

- Central event consolidation
  - What happened?
- Application, Security, Setup, System
- Information, Warning, Error, Critical, Successful Audit, Failure Audit

**Windows Firewall with Advanced Security 1.5**

**Stateful firewall**

- Understands and remembers the state of traffic that flows through it
  - If something leaves passed the firewall, it knows to allow it back in
  - If something tries to enter without there being a state or traffic flow already, the firewall blocks this data

**Windows (Defender) Firewall**

- Integrated into the operating system
- Control Panel / Windows Firewall
- Windows Firewall with Advanced Security
  - Click “Advanced Settings”

**Allowed apps**

- Fundamental firewall rules
- Based on applications
  - No detailed control
- No scope
  - All traffic applies
- No connection security rules
  - Can’t encrypt with IPsec tunnels

**Windows Firewall with Advanced Security**

- Inbound rules
- Outbound rules
- Connection security rules
- Granular
  - Program, port, predefined services, custom
- Custom
  - Program, protocol/port, scope, action, profile

**System Configuration 1.5**

**System Configuration (msconfig)**

- Manage boot processes, startup, services, etc.
  - One-stop shop
- Control Panel / Administrative Tools
  - msconfig.exe

**General tab**

- Control the startup process
  - Normal, Diagnostic, Selective
- Normal startup
  - Nothing to see here, go about your business
- Diagnostic startup
  - Similar to Safe Mode, but not quite the same
- Selective startup
  - You decide what to load

**Boot tab**

- Control the boot location
  - Multiple locations and operating systems
- Advanced options
  - Number of processors, maximum memory, etc.
- Boot options
  - Safe boot, remove the GUI, create a log file, base video, OS boot information (shows drivers as they load), set timeout for booting

**Services tab**

- Enable and disable Windows services
  - Determine what starts during boot
- Easier to manage than the Services applet
  - Click/unclick
- Useful for trial and error
  - It may take many reboots to find your problem

**Startup tab**

- Manage which programs start with a Windows login
  - Easily toggle on and off
- Multiple reboots
  - You’ll find it
- A popular feature
  - Has moved to the Task Manager in Windows 8/8.1/10

**Tools tab**

- Easy access to popular administrative tools
  - UAC settings, System Information, Computer Management, etc.
- Faster than searching through menus or typing
  - A static (but comprehensive) list

**Task Manager 1.5**

**Task Manager**

- Real-time system statistics
  - CPU, memory, disk access, etc.
- Starting the Task Manager
  - Ctrl+Alt+Del, select Task Manager
  - Right mouse click the taskbar and select Task Manager
  - Ctrl+Shift+Esc
- Enhancements since Windows 7
  - More information and features

**Applications**

- Lists user-interactive applications in use
  - Apps on the desktop
- Administratively control apps
  - End task, start new task
- Combined with the Processes tab in Windows 8/8.1/10

**Processes**

- View all running processes
  - Interactive and system tray apps
  - View processes from other accounts
- Manage the view
  - Move columns, add metrics
- Later versions combine all apps, processes, and services into a single tab
  - Easy to view and sort

**Performance**

- What’s happening?
  - CPU, memory, etc.
- Statistical views
  - Historical, real time
- Newer versions include CPU, memory, disk, Bluetooth, and network in the Performance tab

**Networking**

- Network performance
  - Separate tab in Windows 7
  - Integrated into the Performance tab in Windows 8/8.1/10
- View utilization, link speeds, and interface connection state

**Users**

- Who is connected?
  - What are they doing?
- Windows 7
  - User list, disconnect, logoff, send message
- Windows 8/8.1/10
  - Separate processes
  - Performance statistics

**Disk Management 1.5**

**Disk Management**

- Manage disk operations
  - Individual computers and file servers
- Computer management
  - Storage / Disk Management
- Warning
  - You can erase data

**Disk status**

- Healthy
  - The volume is working normally
- Healthy (At Risk)
  - The volume has experience I/O errors
  - Drive may be failing
- Initializing
  - Normal startup message
- Failed
  - Cannot be started automatically
  - The disk is damaged, or the file system is corrupted
- Failed redundancy
  - A drive has failed in a RAID 1 or RAID 5 array
- Resynching
  - Mirrored (RAID 1) volume is synching data between the drives
- Regenerating
  - RAID 5 volume is recreating the data based on the parity data

**Mounting drives**

- Extend available storage space
  - Mount a separate storage device as a folder
- Mount in an empty folder
  - Instant storage space
  - Seamless to the user

**Storage spaces**

- Storage for data centers, cloud infrastructures
  - Multiple tiers administrative control
- Storage pool
  - A group of storage drives
  - Combine different storage devices into a single pool
  - Easy to add or remove space in the pool
- Storage space
  - Allocate virtual disks from available space in the pool
  - Includes options for mirroring and parity
  - Hot spare availability

**System Utilities 1.5**

**The Run line**

- Start an application as a command
  - Instead of the graphical interface
- Use the run/search or command prompt
  - Specify options as part of the command

**The Windows command line**

- cmd
  - The “other” Windows
- Many options
  - The power under the hood

**regedit**

- The Windows Registry
  - The big huge master database
  - Hierarchical structure
- Used by almost everything
  - Kernel, Device drivers
  - Services
  - Security Account Manager (SAM)
  - User Interface, Applications
- Backup your registry
  - Built into regedit

**service.msc**

- Control Panel / Administrative Tools / Services
- Useful when troubleshooting the startup process
- Control background applications
- Services can reveal dependencies between applications

**mmc**

- Microsoft Management Console
  - Build your own management framework
  - Choose from a list of “snap-ins”
- Framework used for many built-in management tools

**mstsc**

- Microsoft Terminal Services Client
  - Remote Desktop Connection
- Access a desktop on another computer
  - Or connect to a Terminal Server
- Common for management
  - “Headless” servers

**Notepad**

- View and edit text files
  - You’ll use a lot of text files
- Included with Windows
  - Almost any version

**Explorer**

- Windows Explorer / File Explorer (Windows 10)
  - File management
- View, copy, launch files
  - Granular control
- Easy access to network resources
  - Browse and view

**msinfo32**

- Windows System Information
  - A wealth of knowledge
- Hardware Resources
  - Memory, DMA, IRQs, conflicts
- Components
  - Multimedia, display, input, network
- Software Environment
  - Drivers, print jobs, running tasks

**dxdiag**

- DirectX Diagnostic Tool
  - Manage your DirectX installation
- Multimedia API
  - 3D graphics
  - Audio
  - Input options
- Also makes a very nice generic diagnostic tool
  - Not just for testing DirectX

**defrag**

- Disk defragmentation
  - Moves file fragments so they are contiguous
  - Improves read and write time
- Not necessary for solid state drives
  - Windows won’t defrag on SSD
- Graphical version in the drive properties
- Requires elevated permissions
  - Command line:
    - defrag <volume>
    - defrag C:

**System Restore**

- Creates frequent restore points
  - go back-in-time to correct problems
- F8 - Advanced Boot Options - Repair
- Windows 7/8/8.1/10: Control Panel / Recovery
- Doesn’t guarantee recovery from viruses and spyware

**Windows Update**

- Keep your OS up to date
  - Security patches, bug fixes
- Automatic installation
  - Updates are always installed
- Download but wait for install
  - You control the time
- Check but don’t download
  - Save bandwidth
- Never check
  - Don’t do this

**The Windows Control Panel 1.6**

**Internet Options**

- General - Basic display
- Security - Different access based on site location
- Privacy - Cookies, pop-up blocker, InPrivate browsing
- Content - Certificates and auto-complete
- Connections - VPN and proxy settings
- Programs - Default browser, plugins, etc.
- Advanced - Detailed configuration options (and reset)

**Display**

- Resolution options 
  - Important for LCD monitor native resolutions
- Color depth and Refresh rate
  - Advanced Settings, Adapter modes
- Moved to Settings / System / Display

**User Accounts**

- Local user accounts
  - Domains accounts are stored elsewhere
- Account name and type
- Change password
- Change picture
- Certificate information

**Folder Options / File Explorer Options**

- Manage Windows Explorer
  - Many options
- General
  - Windows, expand folders
- View
  - View hidden files, hide extensions
- Search
  - Indexing, search options, searching non-indexed areas

**System**

- Computer information
  - Including version and edition
- Performance
  - Virtual memory

**Windows (Defender) Firewall**

- Protect from attacks
  - Scans, malicious software
- Integrated into the operating system
- Control Panel / Windows Firewall

**Power options**

- Power plans
  - Customize power usage
- Sleep (standby)
  - Open apps are stored in memory
  - Save power, startup quickly
  - Switches to hibernate if power is low
- Hibernate
  - Open docs and apps are saved to disk
  - Common on laptops

**Credential Manager**

- Centralized management of web and Windows credentials
  - Each site can have a different username and password
- Add additional Windows credentials
  - Certificates

**Programs and features**

- Installed applications
  - Uninstall, size, version
- Windows features
  - Enable and disable

**HomeGroup**

- Easily share information
  - Windows 7 / Windows 8
  - No HomeGroup options in Windows 10
  - Documents, pictures, music, video
- A network for the home
  - Must be set to “Home” in Windows
- Enable HomeGroup
  - A single password for everyone

**Device and Printers**

- Everything on the network
  - Desktops, laptops, printers, multimedia devices, storage
- Quick and easy access
  - Much less complex than Device Manager
  - Properties, device configurations

**Sound**

- Output options
  - Multiple sound devices may be available
- Set levels for output and input
  - Speakers and microphone

**Troubleshooting**

- Some problems can be easily fixed
  - Have you tried turning it off and on again?
- Automate some of the most common fixes
  - Categorized
- May require elevated account access
  - Enabling / disabling hardware and features

**Network and Sharing Center**

- All network adapters
  - Wired, wireless, etc.
- All network configs
  - HomeGroup
  - Adapter settings
  - Network addressing

**Device Manager**

- The OS doesn’t know how to talk directly to most hardware
  - You need rivers
- Manage devices
  - Add, remove, disable
- First place to go when hardware isn’t working
  - Instant feedback

**BitLocker**

- Full disk encryption
  - The operating system and all files
- A TPM is recommended
  - Trusted Platform Module
  - Use a flash drive and password if there’s no TPM
- Seamless
  - Works in the background
  - You never know it’s there

**Sync Center**

- Make files available, even when you’re not online
  - Automatically sync when back online
  - Built-in sync conflict management
- Not available in Homem editions
  - Needs offline file functionality
  - Only available in Pro and higher
- Mark files
  - “Always available offline”

**Installing Applications 1.7**

**Installing Applications**

- Extend the functionality of your operating system
  - Specialized applications
- Available everywhere
  - Find the application you need
  - Install on your operating system
- Not every computer can run every application
  - Some simple checks can help manage your desktop

**System requirements**

- Drive space
  - Initial installation space requirement
  - Application use requirement
  - Some applications use a lot of drive space after installation
- RAM
  - This would be above and beyond the OS requirements
  - Very dependent on the application
  - consider all of the other running applications
- OS compatibility
  - Operating system (Windows, macOS, Linux)
  - Version of the OS

**Installation methods**

- Local installation
  - Downloadable executable
  - CD-ROM / DVD-ROM / Optical media
  - USB
    - Very compatible with most devices
    - Supports large installation programs
- Network-based
  - The default in most organizations
  - Applications are staged and deployed from a central server
  - Can be centrally managed

**Local user permissions**

- Folder/file access
  - Installation programs will be copying a lot of files
- The user needs permission to write application files to the storage drive
  - This may not be the default in an office
- May need to run as Administrator
  - Some applications will install additional drivers or services
  - Be careful when allowing this level of access

**Security considerations**

- There’s a reason we are careful when installing applications
  - Applications have the same rights and permissions as the user
  - An unknown application can cause significant issues
- Impact to device
  - Application upgrade stops working
  - Slowdowns
  - Deleted files
- Impact to network
  - Access to internal services
  - Rights and permissions to file shares

**HomeGroups, Workgroups, and Domains 1.8**

**Organizing network devices**

- Windows HomeGroup
  - Share files, photos, video, etc. between all devices
  - Works on a single private network only
- Windows Workgroups
  - Logical groups of network devices
  - Each device is a standalone system, everyone is a peer
- Windows Domain
  - Business network
  - Centralized authentication and device access
  - Supports thousands of devices across many networks

**HomeGroup**

- Easily share information
  - Windows 7 / Windows 8/8.1
  - HomeGroup support was removed from Windows 10
  - Documents, pictures, music, video
- A network for the home
  - Must be set to “Home” in Windows
- Enable HomeGroup
  - A single password for everyone

**Workgroups**

- Workgroups
  - Small departments
  - Each computer maintains its own user information
  - Non-centralized
- Manage in Control Panel / system

**Domains**

- Central database
  - Active Directory Domain Services
  - Designed for the enterprise
- User accounts are managed centrally
  - Devices are added to the domain
- Manage all devices and users
  - Deploy software
  - Manage the operating system
- Manage in Control Panel / system

**Join a domain**

- Cannot be a Windows Home edition
  - Needs to be Pro or better

**Windows Network Technologies 1.8**

**Network locations in Windows 7**

- Automatically set security levels
  - You don’t have to remember
- Home
  - The network is trusted
- Work
  - You can see other devices, but can’t join a HomeGroup
- Public
  - Airport, coffee shop
  - You are invisible

**Network locations in Windows 8/8.1/10**

- Private
  - Sharing and connect to devices
- Public
  - No sharing or connectivity
- Network and Internet Status
  - Change connection properties

**Remote Access**

- Remote Assistance
  - Home editions
  - One-time remote access
  - Single-use password
  - Chat, diagnostics, NAT traversal
- Remote Desktop connection
  - Non-Home editions
  - Ongoing access
  - Local authentication options
  - May require port forwarding

**Proxy settings**

- Change the traffic flow
  - An Internet go-between
- Control Panel / Internet Properties

**Network shares**

- Make a folder available across the network
  - “Share” with others, view in Windows Explorer
- Assign (map) a drive letter to a share
  - Reconnect automatically
- Shares ending with a dollar sign ($) are “hidden”
  - Not a security feature
- Control Panel / Administrative Tools / Computer Management

**Mapping drives**

- Access a share
  - This PC / Map network drive
- Local drive letter and share name
  - May require additional authentication
- Or use the command line
  - net use <drive letter>\\<server name>\<name of share>

**Printer shares**

- Similar to sharing a folder
  - But it’s a printer instead
- Windows Explorer
  - Add a printer

**Establishing Windows Network Connections 1.8**

**Network Setup**

- Control Panel
  - Network and Sharing Center
  - Set up a new connection or network
- Step-by-step wizard
  - Confirmation during the process
- Many different connections
  - Direct, VPN, dial-up, etc.

**VPN concentrators:** creates an encrypted connection to a VPN concentrator that then decrypts the information to the corporate network, which sends it back to the VPN concentrator then back to your pc.

**VPN connections**

- Built-in VPN client
  - Included with Windows
- Integrate a smart card
  - Multi-factor authentication
    - Something you know
    - Something you have
    - Something you are
- Connect from the network status icon
  - Click and provide credentials


**Dialup connections**

- Modem connection
  - Standard phone lines
- Configuration
  - Authentication
  - Phone number
- Connect / disconnect from network status icon

**Wireless connections**

- Network name
  - SSID (Service Set Identification)
- Security type
  - Encryption method
- Encryption type
  - TKIP, AES
- Security key
  - WPA2-Personal
    - Pre-shared key
  - WPA2-Enterprise
    - 802.1X authentication

**Wired connections**

- Ethernet cable
  - Direct connection
- Fastest connection is the default
  - Ethernet, Wireless, WWAN

**WWAN connections**

- Wireless Wide Area Network
  - Built-in mobile technology
- Hardware adapter
  - Antenna connections
- USB connected or 802.11 wireless
  - Tether
  - Hotspot
- Requires third-party software
  - Each provider is different



**Configuring Windows Firewall 1.8**

**Enabling and disabling Windows Firewall**

- Your firewall should always be enabled
  - Sometimes you need to troubleshoot
- Temporarily disable from the main screen
  - Turn Windows Firewall on or off
  - Requires elevated permissions
- Different settings for each network type
  - Public / Private

**Windows Firewall configuration**

- Block all incoming connections
  - Ignores your exception list
  - Useful when you need security
- Modify notification
  - App blocking

**Creating a firewall exception**

- Allow an app or feature through Windows Firewall
  - The more secure exception
- Port number
  - Block or allow
- Predefined exceptions
  - List of common exceptions
- Custom rule
  - Every firewall option

**Windows IP Address Configuration 1.8**

**How Windows gets an IP address**

- DHCP (Dynamic Host Configuration Protocol)
  - Automatic IP addressing
  - This is the default
- APIPA (Automatic Private IP Addressing)
  - There’s no static address or DHCP server
  - Communicate locally (link-local address)
  - Assigns 169.254.1.0 to 169.254.254.255
  - No Internet connectivity
- Static address
  - Assign all IP address parameters manually
  - You need to know very specific details

**TCP/IP host addresses**

- IP Address: Unique identifier, Subnet mask: Identifies the subnet, Gateway: The route off the subnet to the rest of the world
- DNS: Domain Name Services
  - Converts domain names to IP addresses
- DHCP: Dynamic Host Configuration Protocol
  - Automates the IP address configuration process
  - Addresses can be dynamic or static
- Loopback address - 127.0.0.1 - It’s always there

**A backup for the DHCP server**

- Multiple DHCP servers should be configured for redundancy
  - There will always be one available
- If a DHCP server isn’t available, Windows uses the Alternate Configuration
  - The default is APIPA addressing
- You can also configure a static IP address
  - Keep working normally

**Network Adapter Properties 1.8**

**Network adapter properties**

- Link speed and duplex
  - Auto negotiation doesn’t always negotiate
  - Both sides must match
- Wake on LAN
  - Computer sleeps until needed
  - Useful for late-night software updates

**Quality of Service (QoS)**

- Prioritize network traffic
  - Applications, VoIP, and Video
- Infrastructure must support QoS
  - Differentiated Services Code Points (DSCP) field in the IP header
    - IPv4 - Type of Service (ToS) field
    - IPv6 - Traffic Class octet
- Manage through Local Computer Policy or Group Policy
  - Computer Configuration / Windows Settings / Policy-based QoS

**BIOS settings**

- Enable/disable network adapters
  - On and off
  - Not much nuance

**Best Practices for macOS 1.9**

**Scheduled backups**

- Time Machine
  - Included with macOS
- Hourly backups
  - The past 24 hours
- Daily backups
  - The past month
- Weekly backups
  - All previous months
- Starts deleting oldest information when disk is full

**Scheduled disk maintenance**

- Disk utility
  - Disk maintenance
- Rarely needed
  - No ongoing maintenance
- First Aid
  - Similar to Windows Check Disk

**System updates / App store**

- Centralized updates
  - For both OS and apps
- App Store application
  - The “Updates” option
- Automatic updates
  - Or manual install
- Patch management
  - Install and view previous updates

**Driver/firmware updates**

- Almost invisible in macOS
  - Designed to be that way
- System Information
  - Detailed hardware list
- View only
  - No changes to settings
  - By design

**Anti-virus/Anti-malware updates**

- macOS does not include anti-virus
  - Or anti-malware
- Many 3rd-party options
  - From the usual companies
- An emerging threat
  - Still doesn’t approach Windows
  - It’s all about the number of desktops
- Automate your signature updates
  - New updates every hour / day

**macOS Tools 1.9**

**Time Machine backups**

- Automatic and easy to use
  - Familiar Finder UI
- Dates along the right side
  - Files in the middle
- macOS takes snapshots if the Time Machine storage isn’t available
  - You can restore from the snapshot

**Image recovery**

- Build a disk image in Disk Utility
  - Create an Apple Disk Image (.dmg) file
- Mount on any macOS system
  - Appears as a normal file system
  - Copy files from the image
- Use the restore feature in Disk utility
  - Restore a disk image to a volume

**Disk Utility**

- Manage disks and images
  - Resolve issues
- File system utilities
  - Verify and repair file systems
  - Modify partition details
  - Erase disks
- Create, convert, and restore images
  - Manage disk images

**Terminal**

- Command line access to the operating system
  - Manage the OS without a graphical interface
- OS access
  - Run scripts, manage files
  - Configure OS and application settings

**Screen sharing**

- Integrated into the operating system
  - Can also be viewed with VNC (Virtual Network Computing)
- Available devices appear in the Finder
  - Or access by IP address or name

**Force Quit**

- Stop an application from executing
  - Some applications are badly written
- Command-Option-Escape
  - List application to quit
- Hold the option key when right-clicking the app icon in the dock
  - Choose Force-Quit

**macOS Features 1.9**

**Mission Control and Spaces**

- Quickly view everything that’s running
  - Spread out the desktop into a viewable area
  - Swipe upwards with three fingers or Control-Up arrow
- Spaces
  - Multiple desktops
  - Add Spaces inside of Mission Control

**Keychain**

- Password management
  - Password, notes, certificates, etc.
- Integrated into the OS
  - Keychain Access
- Passwords and Secure Notes are encrypted with 3DES
  - Login password is the key

**Spotlight**

- Find files, apps, images etc.
  - Similar to Windows search
- Magnifying glass in upper right
  - Or press Command-Space
- Type anything in 
  - See what you find
- Define search categories in System Preferences / Spotlight
  - Enable/disable categories

**iCloud**

- Integrates Apple technologies
  - macOS, iOS
- Share across systems
  - Calendars, photos, documents, contacts, etc.
- Backup iOS devices
  - Never lose data again
- Store files in an iCloud drive
  - Similar to Google Drive, Dropbox
  - Integrated into the operating systems

**Gestures**

- You can do more than just point and click
  - Extend the capabilities of your trackpad
- Use one, two, or three fingers
  - Swipe, pinch, click
- Customization
  - Enable/disable
  - System Preferences / Trackpad

**Finder**

- The central OS file manager
  - Compare with Windows Explorer
- File management
  - Launch, delete, rename, etc.
- Integrated access to other devices
  - File servers
  - Remote storage
  - Screen sharing

**Remote Disc**

- Use an optical drive from another computer
  - Has become more important over time
  - Designed for copying files
  - Will not work with audio Cds or video DVDs
- Set up sharing in System Preferences
  - Sharing options
  - Appears in the Finder

**Dock**

- Fast access to apps
  - Quickly launch programs
- View running applications
  - Dot underneath the icon
- Keep folders in the dock
  - Easy access to files
- Move to different sides of the screen
  - Auto-hide or always display

**Boot Camp**

- Dual-boot into Windows on Mac hardware
- Requires Apple device drivers
  - Run Windows on Apple’s Intel CPU architecture
- Everything is managed through the Boot Camp Assistant
  - Builds a Boot Camp partition
  - Installs Windows OS and drivers

**Best Practices for Linux 1.9**

**Scheduled backups**

- Many options
  - Command line and graphical
  - May be included with the distribution
- tar
  - Tape Archive
  - Easy to script into a backup schedule
- rsync
  - Sync files between storage devices
  - Instant synchronization or scheduled

**Scheduled disk maintenance**

- Very little disk maintenance required
  - Space and resources
- Check file system
  - File systems can’t be mounted
  - Done automatically every X number of reboots
  - Force after reboot by adding a file to the root
    - sudo touch /forcefsck
- Clean up log space
  - /var/log

**System Updates**

- Command line tools
  - apt-get, yum
- Graphical update managers
  - Software updater
- Patch management
  - Updates can be scheduled
- Software center
  - The Linux “App Store”

**Driver/firmware updates**

- Many drivers are in the kernel
  - Updated when the kernel updates
- Additional drivers are managed with software updates or at the command line
  - Update those yourself

**Anti-virus/Anti-malware updates**

- Relatively few viruses and malware for Linux
  - Still important to keep updated
- ClamAV
  - Open source antivirus engine
- Same best practice as any other OS
  - Always update signature database
  - Always use real-time scanning

**Linux Tools 1.9**

**Backups**

- May be built-in to the Linux distribution
  - Check with the documentation
- Graphical interface
  - Backup and restore
  - Scheduling
- Command-line options
  - rsync
- There are many different options
  - The the beauty (and challenge) of Linux

**Image recovery**

- Not as many options as Windows
  - but still some good ones
- dd is built-in to Linux
  - Convert and copy a file
  - Backup and restore a partition
  - Very powerful
- Other 3rd-party utilities can image drives
  - GNU Parted, Clonezilla

**Disk maintenance**

- Linux doesn’t require a lot of maintenance
  - You probably already know this
- Clean up log space
  - All logs are stored in /var/log
- File system check
  - Done automatically every X number of reboots
  - Force after reboot by adding a file to the root
    - sudo touch /forcefsck

**Terminal**

- Command line access to the operating system
  - Common to manage in Linux
- OS maintenance
  - Run scripts, manage files
  - Configure OS and application settings

**Screen sharing**

- Screen access to remote devices
  - Manage from your desk
- Many options
  - Like most of Linux
- May be included with your distribution
  - UltraVNC, Remmina

**Basic Linux Commands 1.9**

**Linux commands**

- The command line
  - Terminal, XTerm, or similar
- Commands are similar in both Linux and macOS
  - Mac OS derived from BSD (Berkeley Software Distribution) Unix
- Download a Live CD or install a virtual machine
  - Many pre-made Linux distributions are available
- Use the man command for help
  - An online manual
  - > man grep

**ls**

- List directory contents
  - Similar to the dir command in Windows
- Lists files, directories
  - May support color coding; Blue is a directory, red is an archive file, etc.
- For long output, pipe through more:
  - > ls -l | more (use q or Ctrl-c to exit)

**cd**

- Change current directory
  - Nearly identical to Windows command line
  - Forward slashes instead of backward
- cd <directory>
  - cd /var/log

**grep**

- Find text in a file
  - Search through many files at a time
- grep PATTERN [FILE]
  - > grep failed auth.log

**su / sudo**

- Some commands require elevated rights
  - There are some things normal users can’t do
- su
  - Become super user
  - Or change to a different user
  - You continue to be that user until you exit
- sudo
  - Execute a command as the super user
  - Or as a different user ID
  - Only that command executes as the super user

**shutdown**

- Shut the system down
  - Safely turn off the computer in software
  - Similar to the Windows shutdown command
- sudo shutdown 2	
  - Shuts down and turns off the computer in two minutes
- sudo shutdown -r 2
  - Shuts down and reboots in two minutes
  - Important when you’re not on site
- Ctrl-C or shutdown -c to cancel

**pwd vs. passwd**

- pwd
  - Print Working Directory
  - Displays the current working directory path
  - Userful when changing directories often
- passwd
  - Change a user account password
  - Yours or another
  - passwd [username]

**mv**

- Move a file
  - Rename a file
- mv SOURCE DEST
  - > mv first.txt second.txt

**cp**

- Copy a file
  - Duplicate files or directories
- cp SOURCE DEST
  - > cp first.txt second.txt

**rm**

- Remove files or directories
  - Deletes the files
- Does not remove directories by default
  - Directories must be empty to be removed or must be removed with -r

**mkdir**

- Make a directory
  - Create a folder for file storage
- mkdir DIRECTORY
  - > mkdir notes

**chmod**

- Change mode of a file system object
  - r=read, w=write, x=execute
  - Can also use octal notation
  - Set for the file owner (u), the group (g), others (o), or all (a)
- chmod mode FILE
  - > chmod 744 script.sh
    - #7: Permission - Read, Write and Execute: r w x
    - #6: Permission - Read and Write: 	r w -
    - #5: Permission - Read and Execute: r - x
    - #4: Permission - Read Only: r - -
    - #3: Permission - Write and Execute: - w x
    - #2: Permission - Write Only: - w -
    - #1: Permission - Execute Only: - - x
    - #0: Permission - None: - - -
- chmod a-w first.txt
  - All users, no writing to first.txt
- chmod u+x script.sh
  - The owner of script.sh can execute the file



**chown**

- Change file owner and group
  - Modify file settings
- sudo chown [OWNER:GROUP] file
  - >sudo chown professor script.sh

**iwconfig / ifconfig**

- iwconfig
  - View or change wireless network configuration
  - essid, frequency/channel, mode, rate, etc.
  - Requires some knowledge of the wireless network
  - iwconfig eth0 essid studio-wireless
- ifconfig
  - View or configure a network interface and IP configuration
  - if config eth0
  - Slowly being replaced by ip (ip address)

**apt-get**

- Advanced Packaging Tool
  - Handles the management of application packages
  - Applications and utilities
- Install, update, remove
  - > sudo apt-get install wireshark

**ps**

- View the current processes
  - And the process ID (PID)
  - Similar to the Windows Task Manager
- View user processes
  - -ps
- View all processes
  - -ps -e | more

**vi**

- Visual mode editor
  - Full screen editing with copy, paste, and more
- vi FILE
  - > vi script.sh
- Insert text
  - -i <text>
  - Exit insert mode with Esc
- Save (write) the file and quit vi
  - -:wq

**dd**

- Convert and copy a file
  - Backup and restore an entire partition
- > dd if=<source filename> of=<target file name> [Options]
- Creating a disk image
  - > dd if=/dev/sda of=/tmp/sda-image.img
- Restoring from an image
  - > dd if=/tmp/sda-image.img of=/dev/sda

**Closing programs**

- Use terminal
  - sudo for proper permissions
- killall
  - sudo killall firefox
- xkill
  - Graphical kill
- kill <pid>