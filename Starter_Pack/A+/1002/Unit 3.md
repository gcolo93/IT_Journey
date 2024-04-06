**Troubleshooting Windows 3.1**

**Slow system performance**

- Task Manager
  - Check for high CPU utilization and I/O
- Windows Update
  - Latest patches and drivers
- Disk space
  - Check for available space and defrag
- Laptops may be using power-saving mode
  - Throttles the CPU
- Anti-virus and anti-malware
  - Scan for bad guys



**Limited connectivity**

- Limited or no connectivity: The connection has limited or no connectivity. You might be unable to access the Internet or some network resources. The connection is limited
- Local issues
  - Wireless signal, disconnected cable
  - Check IP address configuration
  - Reboot
- External issues
  - Wireless router rebooted/turned off
  - Ping your default gateway and external IP

**Boot errors**

- Can’t find operating system
  - OS missing
- Boot loader replaced or changed
  - Multiple operating systems installed
- Check boot drives
  - Remove any media
- Startup Repair
- Modify the Windows Boot Configuration Database (BCD)
  - Formerly boot.ini
  - Recovery Console: bootrec /rebuildbcd

**Startup Repair**

- Missing NTLDR
  - The main Windows boot loader is missing
  - Run Startup Repair or replace manually and reboot
  - Disconnect removable media
- Missing operating system
  - Boot Configuration Data may be incorrect
  - Run Startup Repair or manually configure BCD store
- Boots to Safe Mode
  - Windows is not starting normally
  - Run Startup Repair

**Application crashes**

- Application stops working
  - May provide an error message
  - May just disappear
- Check the Event Log
  - Often includes useful reconnaissance
- Check the Reliability Monitor
  - A history of application problems
  - Checks for resolutions
- Reinstall the application
  - Contact application support

**Bluescreens and spontaneous shutdowns**

- Startup and shutdown BSOD
  - Bad hardware, bad drivers, bad application
- Use Last Known Good, System Restore, or Rollback Driver
  - ` `Try Safe mode
- Reseat or remove the hardware
  - If possible
- Run hardware diagnostics
  - Provided by the manufacturer
  - BIOS may have hardware diagnostics

**Black screen**

- No login dialog, no desktop
  - Driver corruption, OS file corruption
- Start in VGA mode
  - F8 for startup options
- Run SFC
  - System File Checker
  - Run from recovery console
- Update drivers in Safe Mode
  - Download from known good source
- Repair/Refresh or recover from backup

**Testing the printer**

- Print or scan a test page
  - Built into Windows
  - Not the application
- Use diagnostic tools
  - Web-based utilities
    - Built into the printer
  - Vendor specific
    - Download from the web site
  - Generic
    - Available in LiveCD form

**Starting the system**

- Device not starting
  - Check Device Manager and Event Viewer
  - Often a bad driver
  - Remove or replace driver
- “One or more services failed to start”
  - Bad/incorrect driver, bad hardware
  - Try starting manually
  - Check account permissions
  - Confirm service dependencies
  - Windows service; check system files
  - Application service; reinstall application

**Slow boot**

- Boot process hangs or takes longer than normal
  - No activity, no drive lights
- Manage the startup apps
  - Control what loads during the boot process
- Task Manager
  - Startup tab
  - Startup impact, Right-click / Disable
- Disable everything
  - Load them back one at a time

**Slow profile load**

- Roaming user profile
  - Your desktop follows you to any computer
  - Changes are synchronized
- Network latency to the domain controller
  - Slows login script transfers
  - Slow to apply computer and user policies
  - May require many hundreds (or thousands) of LDAP queries
- Client workstation picks a remote domain controller instead of local DC
  - Problems with local infrastructure



**Troubleshooting Solutions 3.1**

**Defragmentation**

- Move file fragments so they are contiguous
  - Sharing a common border
  - Improves read and write time
  - Only applicable to spinning hard drives
- Graphical version in the drive properties
  - Command line: defrag
- Weekly schedule
  - Use Control Panel / Administrative Tools / Task Scheduler

**Reboot**

- Have you tried turning it off and on again?
  - There’s a reason it works
- Bug in your router software
  - Reboot the router
- Application is using too many resources
  - Stops the app
- Memory leak slowly consumes all available RAM
  - Clears the RAM and starts again

**Kill tasks**

- Instead of rebooting, find the problem
  - And kill it
- Task Manager 
  - Processes tab
- Sort by resource
  - CPU, memory, disk, network
- Right-click to end task
  - Trial and error

**Restart services**

- Services
  - Applications that run in the background
  - No user interaction
- Similar issues as a normal process
  - Resource utilization
  - Memory leaks
  - Crashes
- View status in Task Manager
  - Services tab
  - Right-click to start, stop, or restart

**Troubleshooting Security Issues 3.2**

**Pop-ups**

- Pop-ups in your browser
  - May look like a legitimate application
  - May be a malware infection
- Update your browser
  - Use the latest version
  - Check pop-up block feature
- Scan for malware
  - Consider a cleaning
  - Rebuild from scratch or known good backup to guarantee removal

**Browser redirection**

- Instead of  your Google result, your browser goes somewhere else
  - this shouldn’t ever happen
- Malware is the most common cause
  - Makes money for the bad guys
- Use an anti-malware/anti-virus cleaner
  - This is not the best option

**Browser security alerts**

- Security alerts and invalid certificates
  - Something isn’t quite right
  - should raise your interest
- Look at the certificate details
  - Click the lock icon
  - May be expired or the wrong domain name
  - The certificate may not be properly signed (untrusted certificate authority)

**Malware network symptoms**

- Slow performance, lock-up
  - Malware isn’t the best written code
- Internet connectivity issues
  - Malware likes to control everything 
  - You go where it wants you to go
  - You can’t protect yourself if you can’t download
- OS updates failures
  - Malware keeps you vulnerable
  - Some malware uses multiple communication paths
- Reload or clean
  - Malware cleaner or recover from known good backup

**Malware OS symptoms**

- Renamed system files
  - Won’t need that anymore
- Files disappearing
  - Or encrypted
- File permission changes
  - Protections are modified
- Access denied
  - Malware locks itself away
  - It doesn’t leave easily
- Use a malware cleaner or restore from known good backup
  - Some malware is exceptionally difficult to remove

**System lock up**

- Completely stops
  - Check Caps Lock and Num Lock status lights
- May still be able to terminate bad apps
  - Windows and Linux Task Manager
  - Mac OS X Force Quit (Command-Option-Esc)
- Check logs when restarting
  - May have some clues about what’s happening
- May be a security issue
  - Perform a virus/malware scan
- Perform a hardware diagnostic
  - System issues can be a factor

**Application crashes**

- Application stops working
  - May provide an error message
  - May just disappear
- Check the Event Log
  - Often includes useful reconnaissance
- Check the Reliability Monitor
  - A history of application problems
  - Checks for resolutions
- Reinstall the application
  - Contact application support

**Virus alerts and hoaxes**

- Rogue antivirus
  - May include recognizable logos and language
- May require money to “unlock” your PC
  - Or to “subscribe” to their service
- Often requires a specific anti-malware removal utility or technique
  - The bad guys are very, very good

**Email security**

- Spam
  - Unsolicited email messages
  - Advertisements
  - Phishing attacks
  - Spread viruses
  - Spam filters can be helpful
- Hijacked email
  - Infected computers can become email spammers
  - You receive odd replies from other users
  - You receive bounce messages from unknown email addresses
  - Scan for malware

**System / application log errors**

- Many errors go undetected
  - The details are in the log
- It may take some work to find them
  - Filter and research
- Find security issues
  - Improper logins
  - Unexpected application use
  - Failed login attempts





**Removing Malware 3.3**

**Identify malware symptoms**

- Odd error messages 
  - Application failures, security alerts
- System performance issues
  - Slow boot, slow applications
- Research the malware
  - Know what you’re dealing with

**Quarantine infected systems**

- Disconnect from the network
  - Keep it contained
- Isolate all removable media
  - Everything should be contained
- Prevent the spread
  - Don’t transfer files, don’t try to backup

**Disable System Restore**

- Restore points make it easy to rewind
  - Malware infects restore points
- Disable System Protection
  - No reason to save an infected config
- Delete all restore points
  - Remove all infection locations

**Remediate: Update anti-virus**

- Signature and engine updates
  - The engine
- Signature updates
- Automatic vs. manual
  - Manual updates are almost pointless
- Your malware may prevent the update process
  - Copy from another computer

**Remediate: Scan and remove**

- Microsoft, Symantec, McAfee
  - The big anti-virus apps
- Malwarebytes Anti-Malware
  - Malware-specific
- Stand-alone removal apps
  - Check with your anti-virus company
- Safe mode
  - Load the bare minimum operating system
  - Just enough to get the OS running 
  - Can also prevent the bad stuff from running
- Pre-installation environment (WinPE)
  - Recovery Console, bootable CD/DVDs/USBs
  - Build your own from the Windows Assessment and Deployment Kit (ADK)
- May require the repair of boot records and sectors

**Schedule scans and run updates**

- Built into the antivirus software
  - Automated signature updates and scans
- Task scheduler
  - Run any task
- Operating system updates
  - Make sure its enabled and working

**Enable System Protection**

- Now you’re clean
  - Put things as the were
- Create a restore point
  - Start populating again

**Educate the end user**

- One on one
  - Personal training
- Posters and signs
  - High visibility
- Message board posting
  - The real kind
- Login message
  - These become invisible
- Intranet page
  - Always available





**Troubleshooting Mobile Apps 3.4**

**Dim display**

- Difficult to see the details
  - Even in low light
- Brightness setting
  - iOS: Settings / Display and brightness
  - Android: Settings / Display / Brightness level
- Replace the bad display
  - Backlight issue

**Wireless connectivity**

- Intermittent connectivity
  - Move closer to access point
  - Try a different access point
- No wireless connectivity
  - Check/Enable WiFi
  - Check security key configuration
  - Hard reset can restart wireless subsystem
- No Bluetooth connectivity
  - Check/Enable Bluetooth
  - Check/Pair Bluetooth component
  - Hard reset to restart Bluetooth subsystem

**Cannot broadcast to monitor**

- Broadcast to a TV
  - Apple TV, Xbox, Playstation, Chromecast, Roku, Smart TVs
- Check app requirements
  - Every broadcast device is different
- All devices must be on the same wireless network
  - Can’t mix your private and guest network
- Signal strength is important
  - Between phone and television
  - Between television and the internet

**Non-responsive touchscreen**

- Touchscreen completely black or touchscreen not responding to input
  - Buttons and screen presses do not register
- Apple iOS restart
  - Press power button, slide to power off, press power button
  - Hold down power button and Home|Volume for 10 seconds
- Android device restart
  - Remove battery, put back in, power on
  - Hold down power and volume down until restart
    - Some phones have different key combinations
    - Some phones do not have a key-based reset

**App issues**

- Problematic apps
  - Apps not loading
  - Slow app performance
- Restart the phone
  - Hold power button, power off
- Stop the app and restart
  - iPhone: Double-tap home|slide up, slide app up
  - Android: Settings/Apps, select app, Force stop
- Update the app
  - Get the latest version

**Unable to decrypt email**

- Protect your email
  - Encrypted communication channels
- Built-in to corporate email systems
  - Microsoft Outlook
- Each user has a private key
  - You can’t decrypt without the key
- Install individual private keys on every mobile device
  - Use a Mobile Device Manager (MDM)

**Short battery life**

- Bad reception
  - Always searching for signal
  - Airplane mode on the ground
- Disable unnecessary features
  - 802.11 wireless, Bluetooth, GPS
- Check application battery usage
  - iOS: Settings/Battery
  - Android: Settings/Battery
- Aging battery
  - There’s only so many recharges

**Overheating**

- Phone will automatically shut down
  - Avoid overheating damage
- Charging/discharging the battery, CPU usage, display light
  - All of these create heat
- Check app usage
  - Some apps can use a lot of CPU
- Avoid direct sunlight
  - Quickly overheats

**Frozen system**

- Nothing works
  - No screen or button response
- Soft reset
  - Hold power down and turn off
- Hard reset
  - iOS: Hold power and home|volume for 10 seconds
  - Android: Various combinations of power, home, and volume buttons
- Ongoing problems may require a factory reset
  - Install the latest operating system and reload

**No sound from speakers**

- No sound from a particular app
  - Check volume settings
    - Both app and phone settings
  - Bad software / delete and reload
  - Try headphones
- Sound starts but then stops
  - Dueling apps / keep app in foreground
- No speaker sound from any app (no alarm, no music, no audio)
  - Load latest software
  - Factory reset

**Inaccurate touch screen response**

- Screen responds incorrectly
  - Or is unresponsive
- Close some apps
  - Low memory can cause resource contention
- Restart the device
  - Soft reset, unless a hard reset is required
- May require a hardware fix
  - Replace the digitizer or reseat the cables

**System lockout**

- Too many incorrect unlock attempts
- iOS: Erases the phone after 10 failed attempts
  - Can disable, but delays increase with failed attempts
- Android: Locks or wipes the phone after failed attempts
  - Use Google login to unlock the phone

**App log errors**

- Most log information is hidden
  - You’ll need developer tools to view it
- A wealth of information
  - If you can decipher it
  - This might take a bit of research
- Viewing logs
  - iOS - Xcode
  - Android - Logcat

**Troubleshooting Mobile Device Security 3.5**

**Signal drop / weak signal**

- Drops and weak signals prevent traffic flows
  - Location is everything
- Make sure you’re connecting to a trusted WiFi network
  - Use a VPN if you’re not
  - Never trust a public WiFi Hotspot
  - Tether with your own device
- Run a speed test
  - Cell tower analyzer and test

**Power drain**

- Power drains faster than normal
  - Heavy application use
  - Increased network activity
  - High resource utilization
  - It’s a Denial of Service (DoS)
- Check application before install
  - Use an App scanner
  - Force stop running apps
- Run anti-malware
  - Check for malicious activity
- Perform a clean install
  - Factory reset, reinstall apps

**Slow data speeds**

- Unusual network activity
  - Unintended WiFi connections
  - Data transmission over limit
- Check your network connection
  - Run a WiFi analyzer
  - Are you on a trusted WiFi network?
- Check overall network speed
  - Run speed check / cell tower analyzer
- Examine running apps for unusual activity
  - Large file transfers, constant activity

**Unintended Bluetooth pairing**

- Connect with a device that isn’t yours
  - This isn’t a good idea
- Remove the Bluetooth device
  - You would have to re-pair to access again
- Disable Bluetooth radio
  - No Bluetooth communication at all
- Run an anti-malware scan
  - Make sure there are no malicious apps

**Leaked information**

- Unauthorized account access
  - Unauthorized root access
  - Leaked personal files and data
- Determine cause of data breach
  - Perform an app scan, run anti-malware scan
- Factory reset and clean install
  - This is obviously a huge issue
- Check online data sources
  - Apple iTunes/iCloud/Apple Configurator, Google Sync, Microsoft OneDrive
  - Change passwords

**Unauthorized location tracking**

- Real-time tracking information and historical tracking details
  - This should be as protected as your other data
- Run an anti-malware scan
  - Malicious apps can capture many data points
- Check apps with an offline app scanner
  - Get some insight into what’s running
- Perform a factory reset
  - Restore from a know-good backup

**Unauthorized camera / microphone use**

- Third-party app captures intimate information
  - Ethical and legal issues
- Run an anti-malware scan
  - Try to identify the source of the breach
- Confirm that loaded apps are legitimate
  - Check with a third-party app scanner
- Factory refresh
  - Completely reset and start from the beginning
