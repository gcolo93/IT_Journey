CHAPTER 13

Users, Groups, and Permissions

In this chapter, you will learn how to

-   Create and administer Windows users and groups

-   Define and use NTFS permissions for authorization

-   Share a Windows computer securely

-   Secure PCs with policies and User Account Control

Your computer's mass storage is filled with files that need protection. You might have personal Word documents, spreadsheets, photos, and videos that you do not want others to access. You have critical files, such as the operating system itself, that cannot be accidentally deleted. You have browser histories and download folders full of files that you want and need. So how are these protected from others, even others who may use the same computer from time to time? The answer is user accounts, groups, and permissions.

Through the combination of user accounts and groups and NTFS permissions, Windows provides incredibly powerful file and folder security. This user/group/NTFS combination scales from a single computer up to a network of computers spanning the world.

When learning about users, groups, and NTFS permissions, it's helpful to know how NTFS works on a single PC with multiple users logging on and off during the day. To that end, this chapter focuses on Windows security from the point of view of a single, or standalone, machine. Chapter 19 takes over where this chapter stops and will revisit these topics in more detail and show you how the same tools scale up to help you protect a computer in a networked environment.

This chapter begins by examining user accounts, passwords, and groups, then turns to the high level of granular security afforded by NTFS. The third section describes methods for sharing and accessing shared content. The chapter wraps with a look under the hood at security policies and User Account Control.

1102

Authentication with Users and Groups

Security begins with a standard account, a unique combination of a username and an associated password, stored in a database on your computer, that grants the user access to the system. Although we normally assign a standard account to a human user, standard accounts are also assigned to everything that runs programs on your computer. For example, every Windows system has a SYSTEM account that Windows uses when it runs programs. Two mechanisms enable standard account security: authentication and authorization.

Authentication is the process of identifying and granting access to some user, usually a person, who is trying to access a system. In Windows, authentication is most commonly handled by a password-protected user account. The process of logging into a system is where the user types in an active username and password.

NOTE   Authentication is the process of giving a user access to a system. Authorization determines what an authenticated user can do to a system.

Once a user authenticates, he or she needs authorization: the process that defines what resources an authenticated user may access and what they may do with those resources. Authorization for Windows' files and folders is controlled by the NTFS file system, which assigns permissions to users and groups. These permissions define exactly what users may do to a resource on the system. Let's continue our discussion of authentication with an overview of user accounts, passwords, and groups, then look at configuring users and groups in Windows.

NOTE   Although this section primarily describes the use of user accounts, passwords, and groups in Windows, understand that all operating systems---without exception---use user accounts, passwords, and groups.

Standard Accounts

Every standard account (previously called user account) has a username and a password. A username is a text string that identifies the user account assigned to a system. Three examples of possible usernames are "Mike1" or "john.smith" or "some.person@outlook.com." Associated with every username is a password: a unique key known only by the system and the person using that username.

Every Windows system stores the user accounts as an encrypted database of usernames and passwords. Windows calls each record in this database a local user account (see Figure 13-1).

Figure 13-1  Windows logon screen

Once upon a time, the story ended here. These days, it's increasingly common to use a global user account that you register with your OS developer. On Chrome OS, the only way to get the full experience is by logging in with an account you register with Google. The opposite is true on Linux, where local user accounts (tied to a specific computer and user) rule. For its part, macOS still uses local user accounts---but you can also link your local account with your Apple ID to enable additional features. Windows combines all three approaches, supporting traditional local user accounts, the ability to link your Microsoft account with a local account to enable synchronization, as well as the ability to directly log in to Windows with your Microsoft account.

NOTE   Global user account is my term. Each company has its own name for its global accounts, such as a Microsoft account, Apple ID, or Google Account. Still, you get the idea, right?

Global accounts function like local accounts but add the benefit of synchronizing some of your stuff with the global account settings. My custom desktop picture at home, for example, matches the desktop picture on my laptop computer. I log in to both machines with my Microsoft account.

EXAM TIP   The CompTIA A+ 1102 exam objectives want you to know the difference between using a local account and a global Microsoft account. Logging in with a Microsoft account will automatically enable a number of features on your device such as alternative authentication options (which we'll look at in a moment), full-device encryption, file and setting synchronization, the ability to lock your device if it is lost, and more. It also enables you to reset your password if you forget it. Keep in mind that these features come at the expense of a greater risk that someone halfway around the world can log in to your account and access your data.

Creating a standard account (local or global) not only adds a username to a database, it also generates several folders on a computer. In Windows, for example, each standard account gets unique personal folders, such as Documents, Desktop, Pictures, Music, and more. By default, only a person logged in as a specific user can access the personal folders for that standard account. So, the next step is to secure that local standard account.

NOTE   Your organization may also have its own equivalent of a global standard account. We'll take a closer look at single sign-on (SSO) using organizational accounts (via Active Directory) in Chapter 19.

Groups

A group is a container that holds user accounts and defines the capabilities of its members. A single account can be a member of multiple groups. Groups are an efficient way of managing multiple users, especially when you are dealing with a whole network of accounts. Standalone computers rely on groups too, though Windows obscures this a little, especially with Home edition users.

Groups make Windows administration much easier in two ways. First, you can assign a certain level of access for a file or folder to a group instead of to just a single standard account. You can make a group called Accounting, for example, and put all standard accounts for the accounting department in that group. If a person quits, you don't need to worry about assigning all the proper access levels when you create a new account for his or her replacement. After you make an account for the new person, just add that account to the appropriate access group! Second, Windows provides numerous built-in groups with various access levels already predetermined.

While all Windows editions come with many of these built-in groups, Windows Home edition handles them very differently than more advanced editions. For starters, make sure you are aware of the following groups for the exam:

-   Administrators Any account that is a member of the Administrators group has complete administrator privileges. Administrator privileges grant complete control over a machine. It is common for the primary user of a Windows system to have her account in the Administrators group.

When you create the Jane user account, in other words, and make Jane an administrator, you place the Jane account in the Administrators group. Because the Administrators group has all power over a system, Jane has all power over the system.

EXAM TIP   The default administrator account is named Administrator. You should use this default only if no other administrators can log on. Best practice is to make a complex password for Administrator; write it down and put it in a safe for emergency use. Change the default administrator's user account/password to reflect one or more of the user accounts added to the Administrators group.

-   Power Users Members of the Power Users group are almost as powerful as members of the Administrators group, but they cannot install new devices or access other users' files or folders unless the files or folders specifically provide them access.

-   Standard Account (Users) Members of a Standard Account group cannot edit the Registry or access critical system files. They can create groups but can manage only those they create. While all users are members of this group, there's a special name for members of just this group: standard account (or standard users).

If you change the Jane account from administrator to standard user, you specifically take the Jane account out of the Administrators group (the Jane account is already in the Standard Users group). Nothing happens with her personal files or folders, but what the Jane account can do on the computer changes rather dramatically.

-   Guests group The Guests group enables someone who does not have an account on the system to log on by using a guest account. You might use this feature at a party, for example, to provide casual Internet access to guests, or at a library terminal. Most often, the guest account remains disabled. Guest users (which includes the usually disabled guest account) can't change settings, install anything, or access the personal files of other user accounts.

Standard Account and Elevated Privileges

The typical scenario with Windows machines is to have a single primary standard account---a standard user---and a local administrator account for doing important tasks like installing or uninstalling apps, updating software, and so on. When you're logged in as a standard user and need to do something that requires an administrator account, you have a couple of options. You could log out and log back in as an administrator, but that's clunky. Windows gives you a way to open and run utilities with the context menu of a right-click, called Run as administrator, or generically, using elevated privileges. The mechanism that will pop when you want to do something beyond your standard account level is called User Account Control (UAC). See the "Beyond Sharing Resources" section at the end of this chapter for the gory details.

Configuring Users and Groups in Windows

Windows comes with many tools to help you create, modify, and delete users. Groups are a different story, though, so let's focus on where you can go configure both users and groups: the Local Users and Groups (lusrmgr.msc) MMC snap-in, shown in Figure 13-2. You can access Local Users and Groups several different ways, but I prefer to right-click on Start, select Computer Management, and select Local Users and Groups in the left pane.

Figure 13-2  Local Users and Groups

NOTE   For reasons that will be described shortly, Windows 10 Home edition does not have Local Users and Groups.

Local Users and Groups has two folders: Users and Groups. By default, the Users folder should already be selected. If not, click the Users folder now. Note the existing user accounts shown in Figure 13-2. Do you see Administrator? Do you see Michaelm? Do you see Guest? Note the down arrow on the Guest user (and others) to show that they are disabled.

Create a standard account (JimT) by right-clicking the whitespace below the existing standard accounts and selecting New User from the context menu. You then add the information to create the new account as shown in Figure 13-3.

Figure 13-3  Creating a new user account called JimT

By default, all new user accounts are automatically added to the Users group. Click the Groups folder to see the many default groups. Figure 13-4 shows the default groups in Windows 10. Do you see Users, Power Users, Guests, and Administrators?

Figure 13-4  Default groups

Let's add the JimT standard account to the Administrators group. Double-click the Administrators group and select Add. Enter JimT into the Select Users dialog box (see Figure 13-5), then click OK.

Figure 13-5  Adding JimT to the Administrators group

You're not limited to the default Windows groups. Here are the steps to create a group called Morning. Click the Groups folder, right-click on any whitespace on the right under the existing groups and select New Group, then fill out the name of the new group (and add an optional description) (see Figure 13-6). You can add members to this group.

Figure 13-6  Creating the Morning group

NOTE   To create and manage users, you must run Local Users and Groups as an administrator. The easiest way to do this is to open a command prompt with elevated privileges, type lusrmgr.msc, and press ENTER. See Chapter 15 for the scoop on running commands from the command-line interface.

Local Users and Groups is a perfectly fine tool for dealing with local users and groups on a single Windows system. Microsoft offers other tools as well. The newest and most important of these is the Accounts app located in Settings (see Figure 13-7).

Figure 13-7  Accounts app home

The Accounts app is more for configuring your personal account than adding users or moving an account into a group. You can work with other users, however, by moving to the Family & other users menu option and clicking Add someone else to this PC (see Figure 13-8). Good luck creating a local user account though, because Microsoft hides this ability, pressuring you to use or create a Microsoft account.

Figure 13-8  Family & other users

The User Accounts Control (UAC) utility in Windows 10 (see Figure 13-9) is handy for making more technical changes to your account. Here you can change (but not create) your group memberships and make simple changes to your account and other accounts (like changing the account name of a local non-domain account). You need to be a member of the Administrators group to make these changes. We will be discussing UAC more in-depth in the "User Accounts Control" section coming up.

Figure 13-9  User Accounts in Windows 10

EXAM TIP   You can perform most account-management tasks via the Settings app, but CompTIA wants you to also be familiar with the traditional way to do this: the User Accounts applet in Control Panel. Don't be surprised if you get a question where User Accounts is the only right answer---but in the real world most of the actions you take in the applet will just redirect you to the Settings app or some other interface!

If you're not using the Windows 10 Home edition, Local Users and Groups is still the best way to go if you're comfortable with the power of the tools (and don't try to do something dangerous such as deleting the administrator account).

Whew! All this hubbub with local user accounts and groups is designed to do one thing only: get a user logged on to a Windows system. But once a user is logged on, it's time to see what they can do to the data. That's where authorization with NTFS kicks in.

Authentication Options

When it comes to actually authenticating with (or logging in to) a computer, the standard for most computers has long been a username and password. As mobile devices (the focus of Chapters 24 and 25) have revolutionized computing, they've also affected how we authenticate. In particular, there are now several ways to log in to Windows---and a new Account | Sign-in option page in Settings for configuring them (shown in Figure 13-10).

Figure 13-10  Sign-in options in Windows 11 Settings app

The CompTIA A+ 1102 exam objectives don't expect you to know about all of these options (CompTIA refers to them as "login OS options), so I'll just focus on the ones you do need to know about. Since every account still needs to have a good password, I'll start there and discuss some password-related best practices.

Username and Passwords

Usernames and passwords help secure user accounts. For starters, never use a similar name and password. Protect your passwords. Never give out passwords over the phone. If someone learns your username and password, he or she can log on to your computer. Even if the user account has only limited permissions---perhaps it can only read files, not edit them---you still have a security breach.

Make your users choose good passwords. I once attended a security seminar, and the speaker had everyone stand up. She then began to ask questions about our passwords---if we responded yes to the question, we had to sit down. She began to ask questions like these:

"Do you use the name of your spouse as a password?"

"Do you use your pet's name?"

By the time she had asked about 15 questions, only 6 people out of some 300 were still standing. The reality is that most of us choose passwords that are amazingly easy to hack. Make sure users have a strong password: at least eight characters long, including letters (some uppercase), numbers, and non-alphanumeric symbols. Many organizations have their employees, clients, customers, etc., use these complexity requirements to ensure they've chosen a hard-to-guess password.

NOTE   The password best practices that CompTIA asks about on the A+ 1102 exam tend to lag best practices in the real world. This section focuses on what I think CompTIA expects for the exam---but I also want to make sure you're safe! Treat these requirements as the bare minimum and check out the National Institute of Technology and Standards (NIST) Special Publication 800-63B, Digital Identity Guidelines, for the latest recommendations. Password managers, which you'll learn about in Chapter 21, can help you use long, unique passwords for every account and service.

Adding additional character types such as uppercase letters, numbers, and special characters will force a hacker to consider many more possible characters (and many, many more possible passwords). Modern hardware can break an eight-character password consisting of only lowercase letters in the blink of an eye---but using each character type increases the work effort of the cracking attempt and thus serves as a deterrent. Some systems won't allow you to use special characters such as @, $, %, or \, however, so you need may need to experiment (and use a longer password if you can't use all character types).

CompTIA also recommends that you should have users change passwords at regular intervals. This can be enforced with an expiration requirements policy that forces users to select a new password periodically. Regularly changing passwords can make it harder for someone who discovers an old password to break in, but these policies are hard to maintain in the real world. For starters, users tend to forget passwords when they change too often, leading to an even bigger security problem.

If your organization forces everyone to change passwords often, some people will just adopt a numbering system to help them remember. In a simpler era, I worked at a company that required me to change my password at the beginning of each month. So, I took a root password---let's say it was "m3y3rs5"---and added a number to the end representing the current month. So, when June rolled around, for example, I would change my password to "m3y3rs56." I was pretty proud of this system at the time, but anyone who discovered one of my older passwords could have guessed my new password and broken into my system in a heartbeat!

NOTE   Every secure organization sets up various security policies and procedures to ensure that security is maintained. Windows has various mechanisms to implement such things as requiring a strong password, for example. Chapter 27 goes into detail about setting up Local Policies and Group Policy.

Windows requires you to create a password hint or password questions for your local accounts. This clue appears above the reset password option after your first logon attempt fails.

CAUTION   Blank passwords or passwords that are easily visible on a sticky note provide no security. Always insist on non-blank passwords, and do not let anyone leave a password sitting out in the open.

Fingerprints and Facial Recognition

Nothing quite makes me feel like I'm both living in the future and in line at the DMV like setting up a computer to authenticate by scanning my fingerprints or recognizing my face (refer back to Chapter 10 for fingerprint and facial recognition).

NOTE   Before you can even set up these (or many other) biometric authentication options, your computer will need special equipment---like a fingerprint scanner or a good front-facing camera.

When you decide to set up one of these options for the first time, your device will give you instructions on what it needs you to do with your fingers or face in order for it to collect sufficient information to authenticate you with later. As shown in Figure 13-11, fingerprint setup requires you to place your finger on the scanner repeatedly at slightly different angles, while facial recognition setup instructs you to center your face in the frame and look directly at the camera.

Figure 13-11  Adding fingerprint (left) and facial recognition (right) with Windows Hello

Personal Identification Number

Traditionally, a personal identification number (PIN) is usually a 4- or 6-digit numeric code that provides a little extra security---most often in a banking or financial context such as debit card transactions and accessing an ATM. This definition isn't all that much help in understanding the PIN's role in logging in to Windows, though!

The first thing to know is that the PIN is only an option when you log in to Windows with a Microsoft account. Second, it doesn't have to be a numeric PIN---you can check the Include letters and symbols checkbox (shown in Figure 13-12) to enable the "PIN" to be a strong password. Third, you'll have to set up a PIN to use biometric authentication options---Windows wants you to have a backup option in case you damage your scanner, camera, fingers, or face! Fourth, if the PIN is numbers only, it can't be a number pattern. Finally, the PIN is specific to the device you set it up on---setting up a PIN on one device won't enable you to use it on your other devices.

Figure 13-12  Creating a Windows Hello PIN

NOTE   Single sign-on (SSO) is yet another login OS option where users can authenticate through a single domain account that enables access to all machines on the domain, thus the term single sign-on. Single sign-on is further discussed in Chapter 19.

Authorization Through NTFS

User accounts and passwords provide the foundation for securing a Windows computer, enabling users to authenticate to log on to a PC. After you've created a user account, you need to determine what the user can do with the available resources (files, folders, applications, and so on). This authorization process uses the NT File System (NTFS) as the primary tool.

NTFS Permissions

Every file and folder on an NTFS partition has a list that contains two sets of data. First, the list details every user and group that has access to that file or folder. Second, the list specifies the level of access that each user or group has to that file or folder. The level of access is defined by a set of restrictions called NTFS permissions. NTFS permissions are rulesets, connected to every folder and file in your system, that define exactly what any account or group can or cannot do to the file or folder.

NTFS permissions are quite detailed and powerful. You can, for example, set up NTFS permissions to enable a user account to edit a file but not delete it. You could also configure NTFS permissions to enable any member of a user group to create a subfolder for a folder. You can even configure a folder so that one group may be able to read the files but not delete them, modify them, or even see them in File Explorer.

NTFS file and folder permissions are powerful and complicated. Entire books have been written just on NTFS permissions. Fortunately, the CompTIA A+ 220-1102 exam tests your understanding of only the following basic concepts of NTFS permissions:

-   Ownership When you create a new file or folder on an NTFS partition, you become the owner of that file or folder. This is called ownership. Owners can do anything they want to the files or folders they own, including changing the permissions to prevent anybody, even administrators, from accessing them.

-   Take Ownership permission With the Take Ownership permission, anyone with the permission can seize control of a file or folder. Administrator accounts have Take Ownership permission for everything. Note the difference here between owning a file and accessing a file. If you own a file, you can prevent anyone from accessing that file. An administrator whom you have blocked, however, can take that ownership away from you and then access that file!

-   Change permission Another important permission for all NTFS files and folders is the Change permission. An account with this permission can give or take away permissions for other accounts.

-   Folder permissions Folder permissions define what a user may do to a folder. One example might be "List folder contents," which gives the permission to see what's in the folder.

-   File permissions File permissions define what a user may do to an individual file. One example is Read & Execute, which gives a user account the permission to run an executable program.

The primary way to set NTFS permissions is through the Security tab of the Properties of a folder or file (see Figure 13-13). The Security tab contains two main areas. The top area shows the list of accounts that have permissions for that resource. The lower area shows exactly what permissions have been assigned to the selected account.

Figure 13-13  The Security tab enables you to set permissions.

You add or remove NTFS permissions by first selecting the user or group you wish to change and then clicking Edit to open a Permissions dialog box. To add an NTFS permission, select the Allow checkbox next to the NTFS permission you want to add. You remove an NTFS permission by deselecting the Allow checkbox next to the NTFS permission you want to remove. The Deny checkbox is not used very often and has a very different job---see the next section, "Inheritance."

Here are the standard NTFS permissions for a folder:

-   Full Control Enables you to do anything you want to the folder

-   Modify Enables you to read, write, and delete both files and subfolders

-   Read & Execute Enables you to see the contents of the folder and any subfolders as well as run any executable programs or associations in that folder

-   List Folder Contents Enables you to see the contents of the folder and any subfolders

-   Read Enables you to view a folder's contents and open any file in the folder

-   Write Enables you to write to files and create new files and folders

-   Full Control Enables you to do anything you want to the file

-   Modify Enables you to read, write, and delete the file

-   Read & Execute Enables you to open and run the file

-   Read Enables you to open the file

-   Write Enables you to open and write to the file

Here are a few important points about NTFS permissions:

-   To see the NTFS permissions on a folder or file, access the file's or folder's Properties dialog box and open the Security tab.

-   NTFS permissions are assigned both to user accounts and groups, although it's considered a best practice to assign permissions to groups and then add user accounts to groups instead of adding permissions directly to individual user accounts.

-   Permissions are cumulative. If you have Full Control on a folder and only Read permission on a file in the folder, you get Full Control permission on the file.

-   Whoever creates a folder or a file has complete control over that folder or file. This is ownership.

-   If an administrator wants to access a folder or file they do not have permission to access, they may go through the Take Ownership process.

Take some time to think about these permissions. Why would Microsoft create them? Think of scenarios where you might want to give a group Modify permission. Also, you can assign more than one permission. In many situations, administrators give users both the Read and Write permissions to files or folders.

Inheritance

Inheritance determines which NTFS permissions any newly introduced files or subfolders contained in a folder receive. To understand how a new folder (shown in Figure 13-14) gets its permissions, techs need to know how inheritance works.

Figure 13-14  What are the new folder's permissions?

The base rule of Windows inheritance is that any new files or folders placed into a folder automatically get all the NTFS permissions of the parent folder. So if, for example, you have Read & Execute access to a folder and someone else copies a file to that folder, you will automatically get Read & Execute permissions (see Figure 13-15).

Figure 13-15  Here are your permissions.

All versions of Windows have inheritance turned on by default, which most of the time is a good idea. If you access a folder's Properties dialog box, click the Security tab, and then click the Advanced button, you'll see a button that says either Disable inheritance or Enable inheritance. If you wanted to turn off inheritance, you could click this button. Don't do that. Inheritance is good. Inheritance is expected.

If you look closely at Figure 13-16, you'll see that there are two grayed-out NTFS Allow permissions. That's how Windows tells you that the permissions are inherited. These checkmarks can't be changed, so what do you do if you need to make a change?

Figure 13-16  Inherited permissions

You can edit the permissions by clicking the Edit button above the permissions list. This opens a new dialog (shown in Figure 13-17) where the checkmarks appear as checkboxes.

Figure 13-17  Editing permissions

Permission Propagation

Permission propagation determines what NTFS permissions are applied to files that are moved or copied into a new folder. Be careful here! You might be tempted to think, given you've just learned about inheritance, that any new files/folders copied or moved into a folder would just inherit the folder's NTFS permissions, but this is not always true. It depends on two issues: whether the data is being copied or moved, and whether the data is coming from the same volume or a different one. So, we need to consider these situations:

-   Copying data within one NTFS-based volume creates two copies of the object. The copy of the object in the new location inherits...

-   Moving data within one NTFS-based volume creates one copy of the object. That object retains its permissions, unchanged.

-   Copying data between two NTFS-based volumes creates two copies of the object. The copy of the object...

-   Moving data between two NTFS-based volumes creates one copy of the object. The object in the new location inherits...

-   Copying within a volume creates two copies of the object. The copy of the object in the new location inherits the permissions from that new location. The new copy can have different permissions than the original.

-   Moving within a volume creates one copy of the object. That object retains its permissions, unchanged.

-   Copying from one NTFS volume to another creates two copies of the object. The copy of the object in the new location inherits the permissions from that new location. The new copy can have different permissions than the original.

-   Moving from one NTFS volume to another creates one copy of the object. The object in the new location inherits the permissions from that new location. The newly moved file can have different permissions than the original.

From a tech's standpoint, you need to be aware of how permissions can change when you move or copy files. If you're in doubt about a sensitive file, check it before you sign off to a client. Table 13-1 summarizes the results of moving and copying between NTFS volumes.

Table 13-1  Permission Propagation

EXAM TIP   Current versions of Windows refer to sections of an HDD or SSD as volumes, as you'll recall from Chapter 9. Earlier versions---and many techs and exams in your near future---refer to such groupings as partitions. Be prepared for either term.

Any object that you put on a FAT partition loses any permissions because FAT doesn't support NTFS permissions. This applies in most current scenarios involving FAT32- or exFAT-partitioned mass storage devices, such as the ubiquitous thumb drives that all of us use for quick copying and moving of files from device to device.

Techs and Permissions

You must have local administrative privileges to do almost anything on a Windows machine, such as install updates, change drivers, and install applications; most administrators hate giving out administrative permissions (for obvious reasons). If an administrator does give you administrative permission for a PC and something goes wrong with that system while you're working on it, you immediately become the primary suspect!

If you're working on a Windows system administered by someone else, make sure that administrator understands what you are doing and how long you think it will take. Have the administrator create a new temporary account for you that's a member of the Administrators group. Never ask for the password to a permanent administrator account! That way, you won't be blamed if anything goes wrong on that system: "Well, I told Janet the password when she installed the new hard drive . . . maybe she did it!" When you have fixed the system, make sure the administrator deletes the account you used.

Permissions in Linux and macOS

While the CompTIA A+ 1102 exam concentrates hard on Windows users, groups, and permissions, this is a good time to consider that Linux and macOS also have their own concepts pertaining to users, groups, and permissions. Let's take a short jaunt into Linux and macOS users, groups, and permissions. We'll look at the chmod and chown commands because they are listed as objectives for the CompTIA A+ 1102 exam.

NOTE   Understanding this section requires some understanding of the Linux command line. You may need to refer to Chapter 15 to practice some of the commands shown here.

Just as in Windows, every file and folder on a Linux or macOS system has permissions. You can easily see this if you go to a Linux terminal and type this command: ls -l. This shows a detailed list of all the files and folders in a location, like the following example. Chapter 15 discusses the ls command in a lot more detail, but this is enough for our present discussion.

Let's zero in on one line of this output:

First, let's get the nonessential details out of the way: The 1 is about links (admins may need to care about these); mikemeyers is the owner and mi6 is the group. The file size is 7624; the date and time are next. The filename is honeypot.

Now note the string -rwxrwxrwx. Each of those letters represents a permission for this file. Ignore the dash at the beginning. That is used to tell us if this listing is a file, directory, or shortcut. What we have left are three groups of rwx. The three groups, in order, stand for:

-   Owner Permissions for the owner of this file or folder

-   Group Permissions for members of the group for this file or folder

-   Everyone Permissions for anyone for this file or folder

The letters r, w, and x represent the following permissions:

-   r Read the contents of a file

-   w Write or modify a file or folder

-   x Execute a file or list the folder contents

Figure 13-18 shows the relationships.

Figure 13-18  UNIX-style file permissions

Let's look at another example:

-   This file is called launch_codes. The owner of this file is me. This file is in the users group.

-   The owner, mikemeyers, has read and write privileges (rw-).

-   The group, users, has read and write privileges (rw-).

-   No one has execute permissions (x) because this is just a text file, not a script or program.

-   Everyone can read the launch_codes file (r--). We should probably fix that.

chown Command

The chown command enables you to change the owner and the group with which a file or folder is associated. The chown command uses the following syntax:

chown <new owner> filename

To change the group, use the following syntax:

chown <owner>:<group> filename

So, to change the owner of launch_codes to sally, type

chown sally launch_codes

To change the group to mi6, type

chown sally:mi6 launch_codes

If you retype the ls -l command, you would see the following output:

Be aware that the chown command needs superuser privileges (sudo or su). Refer to Chapter 15 for details.

chmod Command

The chmod command is used to change permissions. Sadly, it uses a somewhat nonintuitive addition system that works as follows:

For example, we can interpret the permissions on

as follows:

-   Owner's permissions are 6: 4 + 2 (rw-)

-   Group's permissions are 6: 4 + 2 (rw-)

-   Everyone's permissions are 4: 4 (r--)

The chmod command uses the following syntax to make permission changes:

chmod <permissions> <filename>

Using this nomenclature, we can make any permission change desired using only three numbers. The current permissions can be represented by 664. To keep the launch codes out of the wrong hands, just change the 4 to a 0: 660. To make the change, use the chmod command as follows:

chmod 660 launch_codes

To give everyone complete control, give everyone read + write + execute. 4 + 2 + 1 = 7. So, use the command as follows:

chmod 777 launch_codes

NOTE   The most common syntax for the chmod command uses three digits, from 0 to 7, but the command technically supports four digits (and even an entirely different symbolic syntax). Run the command man chmod for more details.

Sharing Resources Securely

By using NTFS, Windows makes private the folders and files in a specific user's personal folders (Documents, Music, Pictures, and so on). In other words, only the user who created those documents can access those documents. Members of the Administrators group can override this behavior, but members of the Users group (standard users) cannot. To make resources available to multiple users on a shared Windows machine requires you to take extra steps and actively share.

Sharing Folders and Files

The primary way to share resources on a single computer is to give users or groups NTFS permissions to specific folders and files. This process requires you to a right-click on a file or folder, select Properties, and click the Security tab. You'll notice the Security tab has two sections. The top section is a list of users and groups that currently have NTFS permissions to that folder, and the bottom section is a list of NTFS permissions for the currently selected users and groups (see Figure 13-19).

Figure 13-19  Folder Security tab

NOTE   The Sharing tab in Figure 13-19 accesses the Sharing Wizard, discussed shortly. It's about network shares rather than NTFS sharing.

To add a new user or group, click the Edit button. In the Permissions dialog box that opens, you not only can add new users and groups but also can remove them and edit existing NTFS permissions (see Figure 13-20).

Figure 13-20  Permissions dialog box

While the method just shown works for all versions of Windows, it's a tad old fashioned. Windows provides the Sharing Wizard, which is less powerful but easier to use. To use this method, pick anything you want to share (even a single file) in File Explorer. Then simply right-click on it and choose Give access to | Specific people, which opens the Network access dialog box, shown in Figure 13-21, where you can select specific user accounts from a drop-down list.

Figure 13-21  Network access dialog box

Once you select a user account, you can then choose what permission level to give to that user. Note that your account is listed as Owner. You have two choices for permissions to give to others: Read and Read/Write (see Figure 13-22). Read simply means the user has read-only permissions. Read/Write gives the user read and write permissions and the permission to delete any file the user contributed to the folder.

Figure 13-22  Permissions options

NOTE   If the computer in question is on a Windows domain, the Network access dialog box lets you search the network for user accounts in the domain. This makes it easy to share throughout the network. See Chapter 19 to learn about Windows domains.

Locating Shared Folders

Before you walk away from a computer, you should check for any unnecessary or unknown (to you) shared folders on the hard drives. This enables you to make the computer as secure as possible for the user. When you look in File Explorer, shared folders don't just jump out at you, especially if they're buried deep within the file system. A shared C: drive is obvious, but a shared folder all the way down in D:\temp\backup\Simon\secret_share would not be obvious, especially if none of the parent folders were shared.

Windows comes with a handy tool for locating all the shared folders on a computer, regardless of where they reside on the drives. The Computer Management console in Administrative Tools has a Shared Folders option under System Tools. Under Shared Folders are three options: Shares, Sessions, and Open Files. Select Shares to reveal all the shared folders (see Figure 13-23).

Figure 13-23  Shared Folders tool in Computer Management

You can double-click on any share to open the Properties dialog box for that folder. At that point, you can make changes to the share---such as users and permissions---just as you would from any other sharing dialog box. A close look at the screenshot in Figure 13-23 might have left some of you with raised eyebrows. What kind of share is ADMIN$ or C$?

Every version of Windows since Windows NT way back in the early 1990s comes with several default shares, notably all hard drives---not optical drives or removable devices, such as thumb drives---plus the %systemroot% folder (usually C:\Windows) and a couple of others, depending on the system. These administrative shares give local administrators administrative access to these resources, whether they log on locally or remotely. (In contrast, shares added manually are called local shares.)

Administrative shares are odd ducks. You cannot change the default permissions on them. You can delete them, but Windows will re-create them automatically every time you reboot. They're hidden, so they don't appear when you browse a machine over the network, though you can map them by name. Keep the administrator password safe, and these default shares won't affect the overall security of the computer.

Protecting Data with Encryption

The scrambling of data through encryption techniques provides the only true way to secure your data from access by any other user. Administrators can use the Take Ownership permission to seize any file or folder on a computer, even those you don't actively share. Thus, you need to implement other security measures for that data that needs to be ultra-secure. Depending on the Windows edition, you have between zero and three encryptions tools: Windows Home edition has basically no security features. Advanced editions of Windows such as Windows Pro, Windows Pro for Workstations, and Windows Enterprise add a system that can encrypt files and folders called Encrypting File System. Finally, the most advanced editions feature drive encryption through BitLocker.

Encrypting File System

The professional editions of Windows offer a feature called the Encrypting File System (EFS), an encryption scheme that any user can use to encrypt individual files or folders on a computer.

To encrypt a file or folder takes seconds. Right-click on the file or folder you want to encrypt and select Properties. On the General tab of the Properties dialog box for that object, click the Advanced button (see Figure 13-24) to open the Advanced Attributes dialog box. Check the Encrypt contents to secure data checkbox (see Figure 13-25). Click OK to close the Advanced Attributes dialog box and then click OK again to close the Properties dialog box, and you've locked that file or folder from any user account aside from your own.

Figure 13-24  Click the Advanced button on the General tab.

Figure 13-25  Selecting encryption

As long as you maintain the integrity of your password, any data you encrypt by using EFS is secure from prying. That security comes at a potential price, though, and your password is the key. The Windows security database stores the password (securely, not plain text, so no worries there), but that means access to your encrypted files is based on that specific installation of Windows. If you lose your password or an administrator resets your password, you're locked out of your encrypted files permanently. (There are some very complex ways to try to recover the files, but they're likely to fail---I wouldn't count on them working!) Also, if the computer dies and you try to retrieve your data by installing the hard drive in another system, you're likewise out of luck. Even if you have an identical username on the new system, the security ID that defines that user account will differ from what you had on the old system.

NOTE   If you use EFS, you may want to back up your file encryption certificates in case something terrible happens. You can back them up by selecting Manage your file encryption certificates in the User Accounts Control Panel applet. One of the steps in the dialog this opens will enable you to save a password-protected backup.

And one last caveat. If you copy an encrypted file to a drive formatted as anything but NTFS, you'll get a prompt saying that the copied file will not be encrypted. If you copy to a drive with NTFS, the encryption stays. The encrypted file---even if on a removable disk---will only be readable on your system with your login.

BitLocker Drive Encryption

Windows Pro and better offer full drive encryption through BitLocker Drive Encryption. BitLocker encrypts the whole drive, including every user's files, so it's not dependent on any one account. The beauty of BitLocker is that if your hard drive is stolen, such as in the case of a stolen portable computer, all the data on the hard drive is safe. The thief can't get access, even if you have a user on that system who failed to secure his or her data through EFS.

BitLocker requires a special Trusted Platform Module (TPM) chip on the motherboard to function. The TPM chip (which we looked at in Chapter 5) validates on boot that the computer has not changed---that you still have the same operating system installed, for example, and that the computer wasn't hacked by some malevolent program. The TPM also works in cases where you move the BitLocker drive from one system to another.

NOTE   BitLocker can use a USB flash drive to store its recovery key if you don't have a TPM chip. While this is better than nothing, you do sacrifice some of the security that a TPM chip provides.

If you have a legitimate BitLocker failure (rather than a theft) because of tampering or moving the drive to another system, you need to have a properly created and accessible recovery key or recovery password. The key or password is generally created at the time you enable BitLocker and should be kept somewhere secure, such as a printed copy in a safe or a file on a network server accessible only to administrators.

To enable BitLocker, double-click the BitLocker Drive Encryption icon in the Classic Control Panel, or select Security in Control Panel Home view and then click Turn on BitLocker (see Figure 13-26).

Figure 13-26  Enabling BitLocker Drive Encryption

BitLocker to Go enables you to apply BitLocker encryption to removable drives, like USB-based flash drives. Although it shares a name, BitLocker To Go applies encryption and password protection, but doesn't require a TPM chip. Still, every little bit counts when it comes to securing data.

Beyond Sharing Resources

As you've just seen, users and groups are powerful tools for authenticating users to systems as well as authorizing NTFS permissions, but that's not where their power ends. There are two more areas where we use users and groups to go beyond logging on to a system or sharing folders and files: security policies and User Account Control. Let's discuss security policies first and then cover User Account Control.

Security Policies

Security policies are rules applied to users and groups---and they can do just about everything NTFS permissions can't. Would you like to configure your system so that the Accounting group can log on only between 9 A.M. and 5 P.M.? There's a security policy for that. How about forcing anyone who logs on to your system to use a password that's at least eight characters long? There's a security policy for that as well. Windows provides thousands of preset security policies that you may use simply by turning them on in a utility called Local Security Policy (secpol.msc).

You can access this tool through Control Panel's Administrative Tools, but all of us cool kids just open a command line and run secpol.msc. However, if you choose to access this tool, it will look something like Figure 13-27.

Figure 13-27  Local Security Policy utility

EXAM TIP   The Group Policy Editor (gpedit.msc) includes the same items as Local Security Policy (in its Security folder)---plus many other policies. Local Security Policy is the most direct way to work with security policies, but CompTIA left it out of the exam objectives this time around. Look for Group Policy Editor (introduced in Chapter 11) if you see a question about editing security policies on the CompTIA A+ 1102 exam---but be flexible if Local Security Policy is the only good answer.

Local Security Policy has a number of containers that help organize the many types of policies on a typical system. Under each container are subcontainers or preset policies. As an example, let's set a local security policy that causes user passwords to expire every 30 days---better known as account password expiration or password age. To do this, open the Account Policies container and then open the Password Policy subcontainer.

Look at the Maximum password age setting. Local user accounts passwords expire after 42 days by default on Windows. On almost all versions of Windows, your local user accounts passwords expire after 42 days. You can easily change this to 30 days just by double-clicking Maximum password age and adjusting the setting in the Properties dialog box, as shown in Figure 13-28. You can also set the value to 0 and the password will never expire.

Figure 13-28  Editing Maximum password age in Local Security Policy

NOTE   Policies are useful for configuring local systems, but they really shine when you can apply them to every system in your entire network or apply different policies to systems in different departments. Keep an eye out for domains in Chapter 19 to learn more about applying policies to many systems at once.

User Account Control

The User Account Control (UAC) starting way back in Vista to stop unauthorized changes to Windows. These potential changes can come from installing applications or malicious software, among other things. You'd think consumers would applaud such a feature, right?

When picking the poster child for the "327 Reasons We Hated Vista" list, I'll bet most folks put Vista's UAC at the very top. Vista's UAC manifested as a pop-up dialog box that seemed to appear every time you tried to do anything on a Vista system (see Figure 13-29).

Figure 13-29  UAC in action. Arrgh!

It's too bad that UAC got such a bad rap. Not only is UAC an important security update for all versions of Windows, both macOS and Linux/Unix have an equivalent feature. Figure 13-30 shows the equivalent feature on a Mac.

Figure 13-30  UAC equivalent on a Mac

If every other major operating system uses something like UAC, why was Microsoft slammed so hard when it unveiled UAC in Windows Vista? The reason was simple: Windows users are spoiled rotten, and until UAC came along, the vast majority of users had no idea how risky their computing behavior was.

The problem started years ago when Microsoft created NTFS. NTFS uses robust user accounts and enables fine control over how users access files and folders---but at a cost: NTFS in its pure form is somewhat complicated.

User accounts have always been a bit of a challenge. The only account that can truly do anything on a Windows system is the administrator. Sure, you can configure a system with groups and assign NTFS permissions to those groups---and this is commonly done on large networks with a full-time IT staff---but what about small offices and home networks? These users almost never have the skill sets to deal with the complexities of users and groups, which often results in systems where the user accounts are all assigned administrator privileges by default---and that's when it gets dangerous (see Figure 13-31).

Figure 13-31  The danger of administrator privileges in the wrong hands!

User Account Control enables users to know when they are about to do something that has serious consequences. Here are some examples of common actions that require administrator privileges:

-   Installing and uninstalling applications

-   Installing a driver for a device (e.g., a video card)

-   Installing Windows Updates

-   Adjusting Windows Firewall settings

-   Changing a user's account type

-   Browsing to another user's directory

Before Vista, Microsoft invented the idea of the Power Users group to give users almost all the power of an administrator account (to handle most of the situations just described) without actually giving users the full power of the account. Assigning a user to the Power Users group still required someone who knew how to do this, however, so most folks at the small office/home level simply ignored the Power Users group (see Figure 13-32).

Figure 13-32  Power Users group---almost never used at the small office/home level

Clearly, Microsoft needed a better method to prevent people from running programs that they should not run. If users have the correct privileges, however---or the ability to "escalate" their privileges to that of an administrator---then they should be able to do what they need to do as simply as possible. Microsoft needed to make the following changes:

-   The idea of using an administrator account for daily use needed to go away.

-   Any level of account should be able to do anything as easily as possible.

-   If a regular account wants to do something that requires administrator privileges, the user of the regular account will need to enter the administrator password.

-   If a user with administrator privileges wants to run something that requires administrator privileges, the user will not have to reenter his or her password, but the user will have to respond to an "Are you sure?"--type dialog box so he or she appreciates the gravity of the action---thus, the infamous UAC dialog box.

NOTE   Both Linux and macOS have a UAC command-line function called sudo. Check it out in Chapter 15.

How UAC Works

UAC works for both standard accounts and administrator accounts. If a standard user attempts to do something that requires administrator privileges, he or she sees a UAC dialog box that prompts for the administrator password (see Figure 13-33).

Figure 13-33  Prompting for an administrator password in Windows 10

NOTE   The official name for the UAC dialog box is the "UAC consent prompt."

If a user with administrator privileges attempts to do something that requires administrator privileges, a simpler UAC dialog box appears, like the one shown in Figure 13-34.

Figure 13-34  Classic UAC prompt

UAC uses small shield icons to warn you ahead of time that it will prompt you before certain tasks, as shown in Figure 13-35. Microsoft updated this somewhat redundant feature in subsequent versions of Windows after Vista, as you'll soon see.

Figure 13-35  Shield icons in User Accounts

UAC gives users running a program an opportunity to consider their actions before they move forward. It's a good thing, but spoiled Windows users aren't accustomed to something that makes them consider their actions. As a result, one of the first things everyone learned how to do when Vista came out was to turn off UAC. While it's all but impossible to truly shut down UAC, reducing the impact of UAC is easy.

UAC in Modern Windows

Microsoft may be a huge company, but it still knows how to react when its customers speak out about features they don't like. Modern Windows versions have a refined, less "in-your-face" UAC that makes the feature much easier to use. Let's break down how it works.

A More Granular UAC

Microsoft did some research on why UAC drove users nuts, concluding that the problem wasn't UAC itself but the "I'm constantly in your face or you can turn me off and you get no help at all" aspect. To make UAC less aggressive, Microsoft introduced four UAC levels. To see these levels, start typing user account control in the Search field and select the option to Change User Account Control settings to open the Control Panel app (see Figure 13-36). You can also go to the User Accounts applet in Control Panel and select Change User Account Control settings, as shown in Figure 13-37. This takes you to the same UAC Settings dialog box shown in Figure 13-36.

Figure 13-36  Four levels of UAC

Figure 13-37  Change User Account Control settings option in Windows 10

In Figure 13-36, you can see a slider with four levels. The top level (Always notify) means you want UAC to display the aggressive consent form every time you do anything that typically requires administrator access. The bottom option (Never notify) turns off UAC. The two levels in the middle are very similar. Both do the following:

-   Don't notify me when I make changes to Windows settings.

-   Notify me only when apps/programs try to make changes to my computer.

The only difference is that the second-from-top level dims the desktop (blocking all other actions) when it displays the consent form prompted by an app's attempt to make changes, whereas the third-from-top level doesn't dim the desktop (allows all other actions) when it displays the consent form.

EXAM TIP   Make sure you know what each of the four UAC levels does.

Program Changes Versus Changes I Make

So, what's the difference between a program making a change and you making a change? Look at Figure 13-38. In this case, Windows is set to the second-from-top option. Because this is a program trying to make changes (and Windows is set to the second-from-top UAC level), the UAC consent form appears and darkens the desktop. If you lower the UAC level to the third-from-top option, you still see a consent form, but now it acts like a typical dialog box.

Figure 13-38  Darkened UAC

EXAM TIP   The default behavior for UAC in Windows is the second-from-top option, which results in a screen similar to Figure 13-38.

A program such as the Wireshark installer is very different from a feature you want to change. Notice the options with shields shown earlier in Figure 13-35. Each of these options isn't a program---each is merely a feature built into Windows. Those shields tell you that clicking the feature next to a shield will require administrator privileges. If you set UAC to any of the three lower settings, you'd go straight to that feature without any form of UAC consent prompt. Of course, this isn't true if you don't have administrator privileges. If you're a standard user, you'll still be prompted for a password.

EXAM TIP   CompTIA A+ 1102 exam objective 1.2 includes a Windows command-line utility---net user---that can pull some neat user-related tricks such as adding and deleting users, setting passwords, and enabling or disabling an existing account. It can come in handy when you want to downgrade accounts to keep users from clicking through UAC prompts. Windows won't let you downgrade the last administrator account on a system, but you can enable the super-secret hidden administrator account, give it a secure password, and then remove administrator privileges from the accounts. Just run net user administrator SuperSecurePassword/active:yes to enable the administrator account and set its password.

Overall, the improvements to UAC show that it has a place on everyone's computer. UAC might cause an occasional surprise or irritation, but that one more "Are you sure?" could mean the difference between safe and unsafe computing.

Chapter Review

Questions

1\.   The process of identifying and giving access to users is known as which of the following?

A.   Authentication

B.   Authorization

C.   Acceptance

D.   Administration

2\.   Which of the following is a unique combination of a username and an associated password stored in a database on your computer?

A.   Group

B.   Power Users

C.   User account

D.   User information

3\.   The process that defines what an authenticated user may access and what they can do with the resources is known as which of the following?

A.   Restriction

B.   Authentication

C.   Authorization

D.   Administration

4\.   Which of the following is the name of a container that holds user accounts and defines the capabilities of its users?

A.   Users

B.   Group

C.   Storage

D.   RAM

5\.   Which of the following refers to administrative privileges that provide complete control over a machine?

A.   User privileges

B.   Power Users privileges

C.   Administrator privileges

D.   Standard user privileges

6\.   Almost as powerful as members of the Administrators group, members of which group cannot install new devices or access other users' files or folders unless the files or folders specifically provide them access?

A.   User group

B.   Administrator group

C.   Power Users group

D.   Standard User group

7\.   Which types of groups cannot edit the Registry or access system files. They can create groups but may only manage those they create.

A.   Administrator group

B.   User group

C.   Power Users group

D.   Standard User group

8\.   Which of these is not a requirement for using fingerprint authentication in Windows?

A.   Setting up a PIN number

B.   Logging in with a PIN number

C.   Logging in with a Microsoft account

D.   Repeatedly placing your finger on the scanner

9\.   Which of the following defines exactly what any particular account can or cannot do to a file or folder?

A.   Admin permissions

B.   User permissions

C.   NTFS permissions

D.   Group permissions

10\.   Which of the following is an NTFS permission that enables an account to seize control of a file or folder?

A.   Take Charge

B.   Take Ownership

C.   Seize and Desist

D.   Take Away

Answers

1\.   A. Every Windows system has an authorization system account that Windows uses when it runs programs.

2\.   C. Security begins with a user account, a unique combination of a username and an associated password, stored in a database on the computer, that grants the user access to the system.

3\.   C. Authorization for Windows files and folders is controlled by the NTFS file system, which assigns permissions to users and groups. These permissions define exactly what users may do to a resource on the system.

4\.   B. A single group account can be a member of multiple groups. Groups are an efficient way of managing multiple users, especially when you are dealing with a whole network of accounts.

5\.   C. Administrator privileges grant complete control over a machine. It is common for the primary user of a Windows system to have their account linked to the Administrators group.

6\.   B. Almost as powerful as members of the Administrators group, members of the Power Users group cannot install new devices or access other users' files or folders unless the files or folders specifically provide them access.

7\.   B. User groups cannot edit the Registry or access system files. They can create groups but may only manage those they create.

8\.   B. Users will have to use a Microsoft account, set up a PIN, and repeatedly place their finger on the scanner in order to use fingerprint authentication.

9\.   C. NTFS permissions are the primary tool for authorization and provide many configuration options for user access and security.

10\.   B. Administrators have Take Ownership permission for everything and can use this to take ownership away from someone and then access their files.

Copy

copy

Highlight

highlight

Add Note

note

Get Link

link

table of contents

search

Settings

queue

close x

Preparing for certification?

Take Practice Test

chevron right

Skip to Content

Topics

Start Learning

Featured

Search 50,000+ courses, events, titles, and more

Chapter 13 Users, Groups, and Permissions

Chapter 14 Maintaining and Optimizing Operating Systems

Chapter 15 Working with the Command-Line Interface

42h 21m remaining
