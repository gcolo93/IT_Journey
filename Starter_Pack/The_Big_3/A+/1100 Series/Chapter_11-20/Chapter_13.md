- **CHAPTER 13: Users, Groups, and Permissions**
  - Introduction to protecting files and folders on your computer
  - Overview of user accounts, groups, and NTFS permissions
  - Focus on Windows security for standalone machines

- **Authentication with Users and Groups**
  - Standard accounts: usernames, passwords, and encrypted database storage
  - Mechanisms for authentication and authorization
  - Overview of user authentication process in Windows

- **Standard Accounts**
  - Creation and management of local and global user accounts
  - Personal folders and security settings for standard accounts
  - Differences in account management across various operating systems

- **Groups**
  - Definition and purpose of groups in managing user capabilities
  - Benefits of using groups for access control and administration
  - Overview of built-in groups in Windows and their access levels

- **Standard Account and Elevated Privileges**
  - Utilization of standard and administrator accounts for system tasks
  - Introduction to User Account Control (UAC) and elevated privileges
  - Strategies for managing user accounts and access levels effectively

- **Configuring Users and Groups in Windows**
  - Tools and methods for creating, modifying, and deleting users and groups
  - Demonstration of Local Users and Groups MMC snap-in
  - Alternative tools for user and group configuration in Windows

- **Authentication Options**
  - Overview of authentication methods beyond username and password
  - Introduction to biometric authentication and PINs in Windows
  - Considerations for configuring authentication options in Windows

- **Authorization Through NTFS**
  - Understanding NTFS permissions and their role in access control
  - Overview of ownership, take ownership permission, and change permission
  - Detailed explanation of folder and file permissions in NTFS

- **NTFS Permissions**
  - Standard NTFS permissions for folders and files
  - Cumulative nature of permissions and ownership principles
  - Importance of assigning permissions to groups rather than individual accounts

- **Inheritance**
  - Explanation of inheritance in NTFS permissions
  - Automatic propagation of permissions to new files and folders
  - Managing inheritance settings and editing permissions in Windows

- **Permission Propagation**
  - Determines NTFS permissions applied to files moved or copied into a new folder
  - Dependent on whether data is copied or moved and whether it's within the same volume
  - Situational considerations:
    - Copying data within one NTFS volume creates two copies inheriting permissions from the new location
    - Moving data within one NTFS volume retains permissions unchanged
    - Copying data between two NTFS volumes creates two copies inheriting permissions from the new location
    - Moving data between two NTFS volumes creates one copy inheriting permissions from the new location
    - Copying within a volume creates two copies inheriting permissions from the new location, allowing for different permissions
    - Moving within a volume retains permissions unchanged
    - Copying from one NTFS volume to another creates two copies inheriting permissions from the new location, allowing for different permissions
    - Moving from one NTFS volume to another creates one copy inheriting permissions from the new location, allowing for different permissions
  - Important for techs to understand how permissions change during file movement or copying
  
- **Techs and Permissions**
  - Require local administrative privileges for most tasks on a Windows machine
  - Administering Windows systems necessitates careful management of permissions to avoid security issues
  - It's crucial for techs to communicate with system administrators and use temporary accounts when necessary to avoid blame for system issues
  
- **Permissions in Linux and macOS**
  - Similar to Windows, Linux and macOS have user, group, and permissions concepts
  - File and folder permissions can be managed using commands like `chmod` and `chown`
  - File permissions in Linux/macOS are represented by letters indicating read, write, and execute permissions
  
- **Sharing Resources Securely**
  - NTFS permissions control access to folders and files on Windows machines
  - Sharing resources involves granting NTFS permissions to specific users or groups
  - Windows provides a Sharing Wizard for easier sharing but with less granularity in permissions
  
- **Protecting Data with Encryption**
  - Encryption is essential for securing data from unauthorized access
  - Windows offers Encrypting File System (EFS) for encrypting individual files or folders
  - EFS encryption relies on user passwords, and losing access to the password can permanently lock encrypted files
  - Backing up file encryption certificates is recommended for EFS users to prevent data loss
  - Encrypted files copied to non-NTFS drives lose encryption, while NTFS retains encryption even on removable disks

- **BitLocker Drive Encryption:**
    - Windows Pro and better offer full drive encryption through BitLocker Drive Encryption.
    - BitLocker encrypts the whole drive, including every user's files, making it independent of any one account.
    - BitLocker requires a special Trusted Platform Module (TPM) chip on the motherboard to function.
    - BitLocker can use a USB flash drive to store its recovery key if a TPM chip is unavailable.
    - Properly created and accessible recovery keys or recovery passwords are essential in case of legitimate BitLocker failures.
    - To enable BitLocker, access the BitLocker Drive Encryption icon in the Classic Control Panel or select Security in Control Panel Home view and then click Turn on BitLocker.

- **Beyond Sharing Resources:**
    - Users and groups serve additional purposes beyond logging on to systems and sharing folders and files.
    - Security policies are rules applied to users and groups that can do what NTFS permissions can't.
    - Local Security Policy (secpol.msc) provides access to various preset security policies that can be applied.
    - User Account Control (UAC) helps prevent unauthorized changes to Windows and prompts users when administrator privileges are required.
    - UAC works for both standard accounts and administrator accounts and involves consent prompts for actions requiring elevated privileges.
    - Modern Windows versions have refined UAC levels to make the feature less intrusive while still ensuring security.
    - The four UAC levels range from Always notify to Never notify, with options to notify only when apps/programs try to make changes or when changes are made to Windows settings.

- **Program Changes Versus Changes I Make:**
    - UAC distinguishes between changes made by programs and changes initiated by users.
    - Programs attempting changes prompt UAC consent forms, while changes initiated by users typically do not if UAC settings allow.

- **Overall:**
    - BitLocker and UAC are integral security features in modern Windows systems, providing robust encryption and protection against unauthorized system changes.
    - While UAC may occasionally be perceived as intrusive, its role in prompting users for consent helps maintain system security and prevents accidental or malicious changes.