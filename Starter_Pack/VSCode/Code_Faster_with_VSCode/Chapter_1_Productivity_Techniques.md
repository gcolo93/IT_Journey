**Introduction**

**Visual Studio: Unleashing Productivity**

Visual Studio, in the realm of Integrated Development Environments (IDEs), stands out as a pinnacle of functionality and design. However, despite its vast array of features aimed at enhancing productivity, many of these tools remain underutilized. Developers often only scratch the surface of what this powerful platform has to offer, not due to lack of desire, but rather due to unawareness of its full capabilities.

**The Purpose of This Book**

This book aims to bridge the gap between the potential of Visual Studio and its actual utilization. Unlike typical publications that either briefly mention Visual Studio as part of a broader discussion or provide a general overview without delving into practical application, this book offers actionable techniques to immediately enhance productivity. Whether you're a novice or an experienced user, you'll find valuable insights to streamline your workflow and reduce time spent on common tasks.

**Key Features**

This isn't merely a collection of tips and tricks. For the first time, comprehensive coverage of keyboard shortcuts, commands, and menu paths is provided, accompanied by detailed explanations of their usage. Whether you prefer reading cover-to-cover or need a quick reference guide, the information is presented in a format that caters to diverse learning styles.

**System Requirements**

Before diving into the content, ensure your system meets the following requirements:

- **Software Requirements:**
  - Compatible with Windows XP (x86) SP3 or later, Windows Vista (x86 & x64) SP2 or later, Windows 7 (x86 & x64), Windows Server 2003 (x86 & x64) SP2 or later, Windows Server 2003 R2 (x86 & x64), Windows Server 2008 (x86 & x64) SP2 or later, and Windows Server 2008 R2 (x64).
  - Supported Architectures: 32-Bit (x86) and 64-Bit (x64).
- **Hardware Requirements:**
  - Processor: 1.6GHz or faster.
  - RAM: 1 GB (32-Bit) or 2 GB (64-Bit) (Add 512 MB if running in a virtual machine).
  - Disk Space: 3 GB available.
  - Display: DirectX 9 capable video card running at 1024 x 768 or higher-resolution display.
  - Additional: DVD-ROM Drive.
  - Note: Local Administrator rights may be necessary for installation or configuration of Visual Studio, depending on your Windows configuration.

**Part I: Productivity Techniques**

**Chapter 1: Getting Started**

*"A beginning is the time for taking the most delicate care [...]"*
— Frank Herbert, "Dune"

This chapter focuses on essential tasks to enhance your productivity within Visual Studio. It covers topics such as exporting development settings, navigating the Start Page, optimizing performance, and other fundamental tasks.

**01.01 Running Multiple Versions of Visual Studio Side-By-Side**

**Versions:** 2005, 2008, 2010  
**Code:** vstipEnv0054

Many users wonder if it's possible to run multiple versions of Visual Studio concurrently on the same machine. The answer is yes, it's feasible!

Refer to the documentation on MSDN, under the topic "Installing Visual Studio Versions Side-by-Side," for detailed instructions (http://msdn.microsoft.com/en-us/library/ms246609.aspx).

It's advisable to install multiple versions in chronological order, starting with the oldest version (e.g., Visual Studio 2005, 2008, and then 2010).

**01.02 Getting Table of Contents in Visual Studio 2010 Online Help**

**Versions:** 2010  
**Code:** vstipTool0120

If you prefer the classic look of the table of contents in Visual Studio 2010 online help, you can easily switch to it by following these steps:

1. Set your default help to online help by selecting **Help | Manage Help Settings**. Then click **Choose Online Or Local Help** and select **I Want To Use Online Help**, followed by clicking **OK**.

2. Once you've switched to online help, navigate to **Help | View Help** to access a page similar to the following:

3. In the upper-right corner of the page, look for the **Preferences** link. Click it.

   - Note: If you don’t see the Preferences link, you might see links to **Lightweight**, **ScriptFree**, and **Classic** instead. In this case, simply click **Classic** and skip the next step.

4. Choose **Classic** and click **OK**.

Now your Visual Studio help will display the old-style contents list that you prefer.

**01.03 Exporting Your Environment Settings**

**Versions:** 2005, 2008, 2010  
**Code:** vstipEnv0021

Exporting your environment settings in Visual Studio is a useful way to back them up for future use. Here's how you can do it:

1. Press **Alt + T, I** or navigate to **Tools | Import and Export Settings** in the menu.

2. This will open the **Import and Export Settings Wizard**.

3. Select the **Export Selected Environment Settings** option to begin the process.

4. Click **Next** to proceed to the **Choose Settings To Export** dialog box.

5. In this dialog box, you can expand different areas to choose the items you want to include or exclude from the export.

6. By default, most settings are selected for export, except for those that could expose sensitive information, which are marked with a yellow warning symbol icon.

7. After making your selections, click **Next** to continue.

8. Now, you need to choose the location and filename for the exported settings. By default, they are saved to **C:\users\<current user>\documents\visual studio <version>\settings**, with the filename being the current date.

   - **Warning:** It's important to give your exported settings meaningful names to make it easier to identify them later. For instance, if you're exporting your favorite black theme fonts and colors, a name like “Fonts and Colors (Black Theme) 2010-07-05” would be appropriate.

9. Once you've set the location and filename, click **Finish** to complete the export process.

10. After finishing, Visual Studio will export your settings, and a dialog box will appear confirming the completion of the process.

   - If you're curious, the exported file is essentially an XML file. You can open it in Notepad to view its contents.

**01.04 Remove Projects from the Recent Projects List**

**Version:** 2010  
**Code:** vstipTool0017

In Visual Studio 2010, you have the ability to remove projects from the Recent Projects list on your Start Page. Here's how you can do it:

1. Press **Alt + F** to open the **File** menu.

2. Then press **J** to navigate to the **Recent Projects and Solutions** submenu.

3. From there, select the project you want to remove from the list.

4. Once the project is selected, press the corresponding number key displayed next to it.

5. Alternatively, you can directly right-click on the project in the Recent Projects list.

6. In the context menu that appears, select **Remove From List**.

By following these steps, you can remove a project from the Recent Projects list without deleting it from your filesystem. If you want to permanently delete the project, you'll need to do that manually.

**01.05 AutoRecover**

**Versions:** 2005, 2008, 2010  
**Code:** vstipEnv0019

AutoRecover in Visual Studio can be a lifesaver in situations where the development environment crashes or during power outages. Here's how you can access and configure AutoRecover settings:

1. Press **Alt + T** to open the **Tools** menu.

2. Then press **O** to navigate to the **Options** submenu.

3. Within the **Options** dialog, go to **Environment** and select **AutoRecover**.

In the AutoRecover settings, you can adjust the following options:

- **Save AutoRecover Information Every n minutes:** This determines how frequently Visual Studio saves AutoRecover information for files. The default interval is every five minutes. Adjust this based on the frequency of your code updates to ensure you don't lose significant work in case of a crash.

- **Keep AutoRecover Files for n days:** Specifies how long Visual Studio keeps AutoRecover files in the Backup Files directory. The default is seven days. You can decrease this number if you work with numerous projects to prevent clutter in the Backup Files directory.

AutoRecover files are stored in the directory: `My Documents\Visual Studio <version>\Backup Files\<projectname>`. However, not every file is saved here; the backup folder remains empty when you create a solution initially.

When you make changes to a file and save it, Visual Studio doesn't save AutoRecover information, assuming there's no need for recovery. However, if you make changes without saving, AutoRecover information is generated after a certain interval.

If Visual Studio crashes, AutoRecover allows you to recover unsaved changes or revert to the last saved version. You'll encounter a dialog box with options to recover files:

- **Recovered files:** Lists the files available for recovery, allowing you to select or deselect files for recovery.

- **<File Name> Summary:** Provides detailed information about the selected file, including the backup file's location and the destination for the recovered file.

- **Recover Selected Files:** Performs a recovery action on the selected file(s), copying the recovered source file to the indicated destination.

- **Do Not Recover:** Closes the dialog box without recovering any listed files.

**01.06 Improving Performance by Changing the Visual Experience in Visual Studio 2010**

**Versions:** 2010  
**Code:** vstipEnv0017

Visual Studio 2010 adjusts its visual experience dynamically based on various factors, such as running in Remote Desktop or virtual machine environments, and utilizes hardware graphics acceleration when available.

However, you can manually change Visual Studio's Visual Experience settings to potentially improve performance. Here's how:

1. Press **Alt + T** to open the **Tools** menu.

2. Then press **O** to navigate to the **Options** submenu.

3. Within the **Options** dialog, go to **Environment > General > Visual Experience** to access the relevant settings.

In the **Visual Experience** dialog box, you'll find the following options:

- **Automatically Adjust Visual Experience Based On Client Performance:** Clearing this checkbox allows you to manually control Visual Studio's visual experience.

Below are explanations for each option:

- **Enable Rich Client Visual Experience:** This option enables or disables rich animations and gradients for elements like sliding tool windows. Disabling this option can improve performance, especially in remote sessions.

- **Use Hardware Graphics Acceleration If Available:** This option allows you to enable or disable Windows Presentation Foundation (WPF) hardware acceleration. Enabling it may improve performance, particularly if your system supports it.

After adjusting these options, click **OK** to apply the changes.

Additionally, you can use the Windows SDK tool called WPFPerf to measure WPF performance and assess the impact of these changes. Further information on using this tool can be found at the Microsoft WindowsClient.NET site.

For users experiencing performance issues with Visual Studio 2010 over remote sessions, it's recommended to read the article titled "Optimizing Visual Studio 2010 and WPF Applications for Remote Desktop" for valuable insights on improving performance in such scenarios.

**01.07 Change Tool Window Animations**

**Versions:** 2005, 2008  
**Code:** vstipEnv0018

In the previous tip (vstipEnv0017 - "01.06 Improving Performance by Changing the Visual Experience in Visual Studio 2010"), we discussed enhancing the visual performance of Visual Studio 2010. Now, let's explore similar adjustments for Visual Studio 2008 and 2005. Specifically, you can modify the animation speed of tool windows in these older versions of Visual Studio.

**Instructions:**

1. Press **Alt + T** to access the **Tools** menu.

2. Then press **O** to navigate to the **Options** submenu.

3. Within the **Options** dialog, go to **Environment > General**.

In the **General** settings, locate the **Animate Environment Tools** option.

**Purpose:**

Adjusting tool window animations can provide a performance boost by either speeding up or disabling the animation entirely.

**Recommendation:**

Initially, it's suggested to disable this feature to assess any potential performance improvements. Later, if desired, you can re-enable animations by turning on the option and setting the slider to the fastest speed. As you evaluate performance, you can fine-tune the animation speed to find the optimal setting for your workflow.

**01.08 Importing or Changing Your Environment Settings**

**Versions:** 2005, 2008, 2010  
**Code:** vstipEnv0022

If you've previously exported your settings (as explained in vstipEnv0021 - "01.03 Exporting Your Environment Settings"), you can easily import them back into Visual Studio. Follow these steps to import or change your environment settings:

1. Press **Alt + T** to access the **Tools** menu.

2. Then press **I** to navigate to the **Import and Export Settings** submenu.

3. Select **Import Selected Environment Settings** from the submenu.

**Instructions:**

- Upon selecting **Import Selected Environment Settings**, you'll be prompted to choose the previously exported .vssettings file.

- After clicking **Next** on the Welcome page, you'll have the option to save your existing settings before overwriting or to proceed with overwriting them directly.

- Proceed to the next step by clicking **Next**, where you'll be given options to choose from default settings, previously saved settings, or to browse for your own .vssettings file.

- Click **Next** again to select the specific settings you want to import. By default, all previously exported settings are selected, except for Command Window Aliases, External Tools List, and Import and Export Settings, which are considered potentially risky.

**Warning:** Be cautious about sharing full exports with team members, as there may be sensitive information included in the file. Instead, export only the necessary items to share with team members in a separate file.

- Once you've chosen the settings to import, click **Finish** to initiate the import process and view the final page of the wizard.

- Simply click **Finish** again to complete the import process.

By following these steps, you can easily import your previously exported environment settings back into Visual Studio.

**01.09 Change Your Visual Studio Color Scheme**

**Seeing What You Like**
Ever see a set of colors your friend or coworker has and wish you could get it too? Ever go to http://studiostyles.info and want some of those cool color schemes? Well, you can get the colors you want! Let’s walk through how it’s done.

**Getting the Goods**
*On someone’s computer:*
1. Get them to export their fonts and colors by going to **Tools | Import And Export Settings**.
2. Click **Next**, and export only the fonts and colors—nothing else.
3. Give the settings a cool name, and click **Finish**.

*On the Studio Styles site:*
1. Click the style you want.
2. Choose your Visual Studio version, click **Download This Scheme**, and follow the instructions in the next section.

**Changing Your Colors**
1. When you have a .vssettings file you want to import, copy or move the file to your computer, preferably to the settings folder located at `C:\Users\<user>\Documents\Visual Studio <version>\Settings`.
2. Go to **Tools | Import And Export Settings** on your computer.
3. Make sure that **Import Selected Environment Settings** is selected, and click **Next**.
4. Choose the settings file that has the color scheme you want.
   - *Note:* Click **Browse** to find your file if you didn’t put it in your Settings folder.
5. Click **Next**. Verify that the file is importing only fonts and colors, and then click **Finish**.

**Resetting the Colors**
If things get bad (e.g., you get colors you don’t like and didn’t make a backup of your old colors) and you need to get the default colors back:
1. Go to **Tools | Options | Fonts And Colors**.
2. Click **Use Defaults**.
   - *Warning:* Clicking **Use Defaults** is an option that wipes out any custom colors used previously.

**01.10 Reset All Your Development Settings**

**Resetting All Settings**
Sometimes you need to get all your settings back to their original state. You can do this with the Reset All Settings option found under **Tools | Import And Export Settings**.

**Warning:** Use the Reset All Settings option at your own risk. It will reset your settings, including a reset of your Toolbox, getting rid of any custom items you have put in there.

1. Click **Next** on the Welcome page shown in the preceding illustration.
2. You see the option to save your current settings. You should absolutely do this.
3. The next screen lets you choose from the list of default settings.
   - Choose your default settings, and click **Finish**.
4. After the reset operation runs, it resets all your settings. This is definitely something you would do as a last resort, and remember, you can always bring back your old settings by importing settings you saved earlier. (see vstipEnv0021, 01.03 Exporting Your Environment Settings, page 6).

**01.11 Customize Your Toolbars in Visual Studio 2010: Toolbars Tab**

**Customizing Toolbars**

You can customize any toolbar in Visual Studio 2010. Here's how:

1. Click the drop-down arrow to the right of any toolbar.
2. Click **Add Or Remove Buttons**.
3. Then click **Customize**.

Alternatively, you can go to **Tools | Customize** on the menu bar. Whichever option you choose opens the Customize dialog box.

**Toolbars Tab**

The Toolbars tab lists all the available toolbars. You can:

- Click **New** to create a customized toolbar. You'll be prompted to give the new toolbar a name.
- Click **Delete** to delete a custom toolbar.
- Click **Modify Selection** to rename or relocate the toolbar.

Note: Default toolbars can't be changed in this way.

**Keyboard Shortcuts**

Clicking **Keyboard** at the bottom of the Customize dialog box takes you to the **Tools | Options | Keyboard** area. Here, you can add keyboard shortcuts for selected commands. See vstipTool0063, 03.26 Keyboard Shortcuts: Creating New Shortcuts, for details.

**01.12 Customize Your Toolbars in Visual Studio 2010: Commands Tab**

You can customize any toolbar in Visual Studio 2010 by following these steps:

1. Click the drop-down arrow to the right of any toolbar, then click **Add Or Remove Buttons**.

2. Click **Customize**.

Alternatively, you can go to **Tools | Customize** on the menu bar.

Upon selecting either option, the Customize dialog box will appear. Click the **Commands** tab.

**Rearrange:**

Choose the menu or toolbar to modify. For instance, select **Editor Context Menus | Code Window**, which appears when you right-click while writing code.

**Controls:**

This area displays the items on the selected menu or toolbar. It shows the items available when you right-click in a code window. Note that not all items are available all the time due to context.

**Buttons:**

Here are the actions you can perform:

- **Add Command**: Adds a new item to the existing menu or toolbar.
- **Add New Menu**: Creates a new menu in the existing menu or toolbar.
- **Delete**: Removes the current item from the Controls area.
- **Move [Up or Down]**: Changes the location of the item in the Controls area.

**Modify Selection:**

Enables changes to the existing item, such as resetting it to default settings, changing the name, modifying text visibility options, or creating a new group on the menu or toolbar.

**Reset All:**

Resets every item in the Controls area to its default settings.

Once you've customized your toolbar, click **Close** and navigate to any code area. Select some code, right-click, and select an option like **Comment Selection** to see your modifications in action.

---

**01.13 Visual Studio Logging**

If Visual Studio encounters issues loading, you can utilize its logging feature:

1. Access the Visual Studio command prompt.
2. Enter `devenv.exe /log` to activate logging.

The log file, ActivityLog.xml, is stored in the path `%APPDATA%\Microsoft\VisualStudio\<version>\`. You can navigate to this location and view the log file to troubleshoot any issues. Additionally, viewing the log file in a browser using the XML style sheet provides a cleaner view of the logging information.

---

**01.14 Visual Studio Safe Mode**

If Visual Studio fails to start correctly, you can use safe mode to isolate the issue:

1. Access the Visual Studio command prompt.
2. Type `devenv.exe /safemode`.

When Visual Studio starts in safe mode, it loads only the default environment, services, and shipped versions of third-party packages. This allows you to troubleshoot whether the problem is caused by third-party add-ins.

---

**01.15 The ResetSettings Switch**

Visual Studio supports the `/ResetSettings` switch to reset it to the default settings chosen during installation. This can be useful for different scenarios, such as using Visual Studio on multiple machines with varying configurations.

- **Two Different Machines:** After exporting window layouts, you can put the `.vssettings` files where you can easily access them on your machines. Then, modify the Visual Studio program icon's properties by adding `/ResetSettings [settings file]` to the target area.

- **Same Machine:** If you use the same machine for different locations, create two copies of the Visual Studio program icon and customize each with the appropriate settings file path.

These steps allow you to load Visual Studio with the settings appropriate for each environment.