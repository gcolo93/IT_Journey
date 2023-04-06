**How to Troubleshoot 5.1**

**Change management**

- Change control
  - A formal process for managing change
  - Avoid downtime, confusion, and mistakes
  - Corporate policies and procedures
- Nothing changes without the process
  - Plan for a change
  - Estimate the risk associated with the change
  - Have a recovery plan if the change doesn’t work
  - Test before making the change
  - Document all of this and get approval
  - Make the change

**Identify the problem**

- Information gathering
  - Get as many details as possible
  - Duplicate the issue, if possible
- Identify symptoms
  - May be more than a single symptom
- Question users
  - Your best source of details
- Determine if anything has changed
  - Who’s in the wiring closet?
- Approach multiple problems individually
  - Break problems into smaller pieces
- Back up everything
  - You’re going to make some changes.
  - You should always have a rollback plan.
- What else has changed?
  - The user may not be aware
  - Environmental changes
  - Infrastructure changes
- There may be some clues
  - Check OS log files
  - Applications may have log information

**Establish a Theory**

- Start with the obvious
  - Occam’s razor applies
- Consider everything
  - Even the not so obvious
- Make a list of all possible causes
  - Start with the easy theories
  - And the least difficult to test
- Research the symptoms
  - Internal knowledge base
  - Google searches

**Test the theory**

- Confirm the theory
  - Determine next steps to resolve problem
- Theory didn’t work?
  - Re-establish new theory or escalate
  - Call an expert
- The theory worked?
  - Make a plan

**Create a plan of action**

- Build the plan
  - Correct the issue with a minimum of impact
  - Some issues can’t be resolved during production hours
- Identify potential effects
  - Every plan can go bad
  - Have a plan B
  - And a plan C

**Implement the solution**

- Fix the issue
  - Implement during the change control window
- Escalate as necessary
  - You may need help from a 3rd party

**Verify full system functionality**

- It’s not fixed until it’s really fixed
  - The test should be a part of your plan
  - Have your customer confirm the fix
- Implement preventative measures
  - Let’s avoid the issue in the future

**Document Findings**

- It’s not over til you build the knowledge base
  - Don’t lose valuable knowledge
- What action did you take?
  - What outcome did it have?
- Consider a formal database
  - Help desk case notes
  - Searchable database

**Troubleshooting Common Hardware Problems 5.2**

**Unexpected shutdowns**

- No warning, black screen
  - May have some details in your event viewer
- Heat-related issue
  - High CPU or graphics, gaming
  - Check all fans and heat sinks
  - BIOS may show fan status and temperatures
- Failing hardware
  - Has anything changed?
  - Check Device Manager, run diagnostics
- Could be anything
  - Eliminate what’s working

**Lockups**

- System completely stops
  - Completely. Usually not much in the event logs.
  - Similar to unexpected shutdown
- Check for any activity
  - Hard drive, status lights, try Ctrl + Alt + Del
- Update drivers and software patches
  - Has this been done recently
- Low resources
  - RAM, storage
- Hard diagnostics may be helpful


**POST (Power On Self Test)**

- Test major system components before booting the operating system
  - Main systems (CPU, CMOS, etc.)
  - Video
  - Memory
- Failures are usually noted with beeps and/or codes
  - BIOS versions can differ, check your documentation
- Don’t bother memorizing the beep codes
  - They’re all different between manufacturers
  - Know what to do when you hear them

**POST and boot**

- Blank screen on boot
  - Listen for beeps
  - Bad video
  - BIOS configuration issue
- BIOS time and setting
  - Maintained with the motherboard battery
  - Replace the battery
- Attempts to boot to incorrect drive
  - Set boot order in BIOS configuration
  - Confirm that the startup device has a valid operating system
  - Check for media in a startup device

**Continuous reboots**

- How far does the boot go before rebooting?
  - BIOS only? OS splash screen?
- Bad driver or configuration
  - F8, “Boot from last known working configuration”
- Try F8, Safe Mode
  - If system starts, disable automatic restarts in System Properties
- Bad hardware
  - Try removing or replacing devices
  - Check connections and reseat

**No Power**

- No power
  - No power at the source
  - No power from the power supply
  - Get out your multimeter
- Fans spin - no power to other devices
  - Where is your fan power connected?
  - No POST - bad motherboard?
  - Case fans have lower voltage requirements
  - Check the power supply output

**Overheating**

- Heat generation
  - CPU’s, video adapters, memory
- Cooling systems
  - Fans and airflow
  - Heat sinks
  - Clean and clear
- Verify with monitoring software
  - Built into the BIOS
  - Try HWMonitor
    - <http://www.cpuid.com/>

**Loud Noises**

- Computers should hum
  - Not grind
- Rattling
  - Loose components
- Scraping
  - Hard drive issues
- Clicking
  - Fan problems
- Pop
  - Blown capacitor

**Intermittent device failure**

- Sometimes it works
  - Sometimes it doesn’t
- Bad install
  - Check and reseat
  - Use all screws
- Bad hardware
  - Poor connection
  - Heat and vibration

**Indicator lights**

- POST codes on motherboard
- Power
- Link light
- Speed
- Activity


**Smoke and burning smell**

- Electrical problems
  - The smoke makes everything work
- Always disconnect power
  - There should never be a burned odor
- Locate bad components
  - Even after the system has cooled down
  - Replace all damaged components

**Crash Screens**

- Windows Stop Error
- Blue Screen of Death
  - You don’t want this
- Contains important information
  - Also written to event log
- Useful when tracking down problems
  - Sometimes more useful for manufacturer support

**The spinning ball of death**

- The macOS X Spinning Wait Cursor
  - Feedback that something is happening
- The spin starts, but it never stops
  - You never get back control of your computer
- Many possible reasons
  - Application bug
  - Bad hardware
  - Slow paging to disk
- Restart the computer
  - There may be details in the console logs

**Log Entries**

- Windows
  - Event Viewer
  - Boot logs
    - System configuration
    - C:\Windows\ntbtlog.txt
- Linux
  - Individual application logs
  - /var/log
- macOS X
  - Utilities / Console.app

**Error messages**

- The details of an error message can make or break a troubleshooting session
  - Write down everything
  - Take a picture, make a video
  - Train your users
- The error might not make sense
  - Write it down anyway
  - The Internet will tell you what it means
  - Spend your time troubleshooting the right things

**Troubleshooting Hard Drives 5.3**

**Disk Failure symptoms**

- Read/write failure
  - “Cannot read from the source disk”
- Slow performance
  - Constant LED activity
  - Retry…retry…retry…
- Loud clicking noise
  - The click of death

**Troubleshooting disk failures**

- Get a back up
  - First thing - a bad drive is bad
- Check for loose or damaged cables
- Check for overheating
  - Especially if problems occur after startup
- Check power supply
  - Especially if new devices were added
- Run hard drive diagnostics
  - From the drive or computer manufacturer
  - Preferably on a known-good computer

**Boot failure symptoms**

- Drive not recognized
  - Lights (or no lights)
  - Beeps
  - Error messages
- Operating system not found
  - The drive is there
  - Windows is not


**Troubleshooting boot failures**

- Check your cables
  - Physical problem
- Check boot sequence in BIOS
  - Check for removable disks (especially USB)
  - Check for disabled storage interfaces
- For new installation, check hardware configuration
  - Data and power cables
  - Try different SATA interfaces
- Try the drive in a different computer

**RAID not found**

- Missing or faulty RAID controller

**RAID stops working / RAID recovery**

- Each RAID is different
  - Don’t start pulling drives until you check the console
- RAID 0 - Disks required: 2 or more - Failure condition: A single drive failure breaks the array with data loss
- RAID 1 - Disks required: 2 or more - Failure condition: Array will work as long as one drive is operational
- RAID 5 - Disks required: 3 or more - Failure condition: Need all drives operational but one
- RAID 10 (RAID 1+0) - Disks required: 4 or more - Failure condition: Can lose all but one from each set of mirrors

**Crash screens**

- Windows stop error, Apple spinning wait cursor
  - A very serious issue
- May indicate a storage device issue
  - Diagnostics needed for drive and motherboard

**S.M.A.R.T. errors**

- S.M.A.R.T.
  - Self-monitoring, Analysis, and Reporting Technology
  - Use third-party utilities
- Avoid hardware failure
  - Look for warning signs
- Schedule disk checks
  - Built-in to most drive arrays
- Warning signs
  - Replace a drive

**Troubleshooting Video and Display Issues 5.4**

**No video image**

- Is it connected?
  - We wouldn’t ask if it wasn’t a real solution.
  - Check both power and signal cable
- Input selection on monitor
  - HDMI, DVI, VGA, etc.
- Image is dim
  - Check brightness control
- Swap the monitor
  - Try the monitor on another computer
- No video after Windows loads
  - Use VGA mode (F8)

**Image quality problems**

- Flickering, color patterns incorrect
  - You can almost work with this
- Check the cable pins
  - Especially if missing a color
- Distorted image and geometry
  - Check the OS refresh rate and resolution settings
    - Need to match the display specifications
  - Native resolution is important on LCD displays
  - Check or replace cable
- Disable hardware acceleration
  - Troubleshoot with the software drivers

**Image quality problems**

- Oversized images and icons
  - Resolution set too low
    - Lower = larger
- Burn-in
  - A problem across all monitor types
  - Some displays will pixel shift
    - But you won’t notice it
  - LCD’s have “image sticking”
    - Remove by displaying a white screen for an extended period of time

**Other video problems**

- Pixel problems
  - Stuck pixels (constantly bright)
  - Dead pixels (always black)
- Artifacts
  - Unusual graphics - check adapter
  - Image persistence - Turn off display
  - Motion trails
    - Disable advanced video features
- BSOD and Overheating
  - Video drivers
  - Monitor the internal temperature

**Troubleshooting Laptops 5.5**

**LCD Display Troubleshooting**

- No display or dim video
  - Verify the backlight
  - Look closely, it may be barely visible
  - No backlight, replace the inverters
- Confirm video with an external display
  - Video good, but LCD bad
  - Replace the LCD display
- Flickering video
  - Connector problem
  - Bad video cable
  - Bad video hardware

**Input issues**

- Sticking keys
  - Difficult to clean
  - Key caps are very, very delicate
- Ghost cursor / pointer drift
  - Mousepad causes cursor to bounce around
  - Modify the configuration to check for palm press
  - Update your drivers
- Num lock indicator lights
  - The letters are numbers

**Wireless troubleshooting**

- Multiple antennas
  - WiFi main and aux, Bluetooth
  - Antenna wires wrap around the laptop screen
- Easy to accidentally disconnect during maintenance
  - No 802.11 wireless
  - No Bluetooth
- Check the connectors
  - Loose cables can cause intermittent wireless access

**Power Issues**

- Battery not charging
  - Batteries lose capacity over time
  - Laptop charging hardware may be faulty
- No power
  - Check the external power adapter “brick” with multimeter
- Master laptop reset
  - Hold power for 10 seconds
  - Each laptop is different

**External monitor issues**

- Toggle Fn keys
  - Secondary functions
  - Toggle between LCD / external monitor / both
- Use external monitor
  - Bypass the LCD (but not the video hardware)

**Troubleshooting Mobile Devices 5.5**

**Touchscreen unresponsive**

- Touchscreen completely black or touchscreen not responding to input
  - Button and screen presses do not register
- Apple iOS reset
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
- Stop the app and restart
  - iPhone: Double-tap home button, slide app up
  - Android: Settings/apps, select app, Force Stop
- Restart the phone
  - Hold power button, power off
- Update the app
  - Get the latest version

**Unable to decrypt email**

- Protect your email
  - Encrypted communication channels
- Built-in to corporate email systems
  - Microsoft Outlook
- Each user has a private key
  - You can’t decrypt without a key
- Install individual private keys on every mobile device
  - Use a Mobile Device Manager (MDM)

**Short battery life**

- Bad reception
  - Always searching for signal
  - Airplane mode on the ground
- Disable unnecessary features
  - 802.11 Wireless, Bluetooth, GPS
- Check application battery usage
  - iPhone: Settings/Battery
  - Android: Settings/Battery
- Replace aging battery
  - There’s only so many recharges

**Overheating**

- Phone will automatically shut down
  - Avoid overheating damage
- Charging/discharging battery, CPU usage, display light
  - All of these create heat
- Check app usage
  - Some apps can use a lot of CPU
- Avoid direct sunlight
  - Quickly overheats

**Frozen system**

- Nothing works
  - No screen or button response
- Soft reset
  - Hold power button down and turn off
- Hard reset
  - iOS: Hold power and home|volume button for 10 seconds
  - Android: Various combinations of power, home, and volume buttons
- Ongoing problems may require a factory reset
  - Install latest operating system and reload

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

**GPS not functioning**

- Check settings to enable GPS
  - iOS: Settings / Privacy / Location Services
  - Android: Settings / Location
- Configure location mode
  - iOS: Settings / Privacy / Location Services
  - Android: Settings / Location / Location mode
- Need a good view of the sky
  - You’re listening to satellites in space

**Swollen battery**

- Buildup of gas
  - Designed to self-contain
  - Do NOT open the battery packet/container
    - Significant fire risk
    - You’ll be sorry
- Faulty battery
  - Stop using immediately
  - Dispose of properly

**Device Disassembly Best Practices 5.5**

**Device disassembly**

- Different than working on a desktop computer 
  - Many different pieces
  - Intricately engineered
  - Tight quarters
- Taking apart is easy
- Easy to break something
  - Very delicate parts

**Mapping the puzzles**

- Document and label
  - It seems obvious when disassembling
  - It’s not obvious at all when reassembling
  - Check iFixit and similar sites
- Cable locations
  - There are a lot of cables
  - Antennas, drives, video, etc.
- Screw locations
  - There are a LOT of screws
  - Different sizes
  - “Hidden” locations

**Organize parts**

- Laptops disassemble in sections
  - Outer shell, keyboard, video connector, etc.
- Step-by-step
  - Take pictures
  - Use a big workspace
- Use containers to separate the sections
  - Glasses, boxes, etc.
  - Magnetic grid
  - Multi-day projects should be sealed or protected

**Get the right information**

- Refer to manufacturer resources
  - Often provide step-by-step repair guides
- The Internet provides the rest
  - Online written guides
  - Youtube videos
- Specialized sites can help
  - <http://www.ifixit.com/>

**The tools**

- Use appropriate hand tools
  - Sometimes a single screw driver
  - Get a good tweezer
  - Sometimes specialized tools
- Magnification will be needed
  - Smaller and smaller devices
- Get a big anti-static cloth
  - Something soft to protect screens
  - Easy to break tiny parts

**Troubleshooting Printers 5.6**

**Testing the printer**

- Print or scan a test page
  - Built into Windows
  - Not the application
- Use diagnostic tools
  - Web-based utilities
    - Built into printer
  - Vendor specific
    - Download from the website
  - Generic
    - Available in LiveCD form

**Bad output**

- Streaks and blurs
  - Inkjet: Clean print heads
  - Laser: Check for scratched photosensitive drum
- Faded prints, blank pages
  - Low toner or ink
- Ghost images
  - Laser printer optical drum not cleaned properly
  - Ghost or “shadow” from previous drum rotation

**Final print**

- Color prints in wrong print color
  - Low ink in one cartridge
  - Everything else works fine
- Laser printer output smudges everywhere
  - Toner not fused to the paper
    - Should be permanently melted and pressed
      - May be hot
      - Fuser problem

**Paper jam**

- Careful when removing
  - Don’t rip the paper
  - Don’t damage internal components
- Paper not feeding
  - Check the tray
  - Pickup rollers
    - Part of a laser printer maintenance kit
- Creased paper
  - Problems in the paper path
  - Check the paper weight

**Network issues**

- No connectivity
  - Powered on?
  - User intervention required
  - Wired cabling / Wireless settings
- Access denied
  - Security tab
    - Print
    - Manage this printer
    - Manage documents

**Bad output**

- Garbled characters on paper
- Bad printer driver / wrong model
- Incorrect page description language (PCL or PostScript)
- Bad application
- Check with a test page

**OS issues**

- Unable to install printer
  - Drivers are important OS updates
  - User must have proper rights
  - Check the printer driver
    - 32 bit vs. 64 bit
- Backed up print queue
  - Printer server not working
  - Print spooler crash
    - Restart the spooler
    - Change recovery options

**Error messages**

- Error codes
  - On the printer display
  - Today’s printers have large LCDs
- Low memory errors
  - Laser printers build the entire page in memory
  - Complex images and graphics consume more memory

**No output**

- Check the printer
  - Getting power? Check for display message
  - Run a test printer from the printer
- Check the connectivity
  - Print a test page from a computer
  - Check direct connection
  - Try across network
  - Tests the operating system, network, drivers, and spooler
- Check other applications
  - Print from another program

**Multiple failed jobs in logs**

- Corrupted print jobs
  - Print spooler will crash
  - Most spooler configuration will automatically restart
- Problems are logged
  - Windows Event Viewer
  - Windows-PrintService
- One job may be causing the issue
  - Monitor the queue for details

**Troubleshooting Network 5.7**

**No network connectivity**

- Do you have a link light?
  - Is it plugged in?
- Ping loopback (127.0.0.1)
  - Is the protocol stack working?
  - Availability and intermittent connectivity
- Ping local IP address
  - Checks local configuration, adapter, and link signal
- Ping default gateway
  - Connectivity on the local network
- Ping devices on router’s other side
  - 8.8.8.8

**Automatic Private IP addressing (APIPA)**

- A link-local address
  - No forwarding by routers
- IETF has allocated 162.254.1.0 through 162.254.254.255
  - 169.254.0.0/24 and 169.254.255.0/24 are reserved
- Automatically assigned
  - Uses ARP to confirm the address isn’t currently in use
- Check your IP address
  - Is it an APIPA address?

**Local resources unavailable**

- Shares
  - Server unavailable
  - Share permissions have been modified
  - Relies on DNS to find the server
- Printers
  - Device sharing printer (or printer) is unavailable
  - Printer permissions have been modified
- Email
  - Service is associated with a specific server
  - May be a cluster of servers
  - Problems may be related to the servers or the network path

**Limited or no connectivity**

- Windows alert in system tray
  - “Limited or no connectivity”
  - No Internet access
- Check local IP address
  - An APIPA address will only have local connectivity
- If DHCP address is obtained, perform the ping tests
  - Local gateway, remote IP address

**Intermittent connectivity**

- Internet access
  - Then nothing
- Check the system tray
  - A broken LAN icon is a loss of signal
  - Check for a cable problem
  - Might have bad network interfaces
- Problem with switch or wireless access point
  - Bad interfaces 
  - Router rebooting

**IP conflicts**

- DHCP helps
  - But static addresses can conflict
- Windows will identify a duplicate
  - And prevent a conflict
- Two identical IP addresses will conflict
  - Intermittent connectivity, if any
- Reboot or reset the NIC
  - Start over from the beginning

**Slow transfer speeds**

- Frustrating to the user
  - Challenging to the technician
- Router or infrastructure congestion
  - Overloaded network or devices
- Speed and duplex incompatibility
  - An easy fix
- Hardware issue with the adapter
  - Or your cabling
- Malware infection

**Low RF wireless signal**

- Interference
  - Something else is using our frequency
- Signal strength
  - Transmitting signal, transmitting antenna, receiving antenna, etc.
- Incorrect channel
  - Usually automatic; look for manual tuning
- Bounce and latency
  - Multipath interference; flat surfaces
- Incorrect access point placement
  - Locate close to the users

**Wireless interference**

- Predictable
  - Fluorescent lights
  - Microwave ovens
  - Cordless telephones
  - High-power sources
- Unpredictable
  - Multi-tenant building
- Measurements
  - Signal strength
  - Performance monitor

**SSID not found**

- Network name doesn’t appear
  - Other networks are there
- Too far away
  - Local networks are louder
- Wireless router has disabled SSID advertisements
  - It will never appear on a list
  - You can still manually connect