**Documentation Best Practices 4.1**

**Internal operating procedures**

- Organizations have different business objectives
  - Processes and procedures
- Operational procedures
  - Downtime notifications
  - Facilities issues
- Software upgrades
  - Testing
  - Change control
- Documentation is the key
  - Everyone can review and understand the policies

**Network topology diagrams**

- Describes the network layout
  - May be a logical diagram
  - Can include physical rack locations


**Knowledge base and articles**

- External sources
  - Manufacturer knowledge base
  - Internet communities
- Internal documentation
  - Institutional knowledge
  - Usually part of help desk software
- Find the solution quickly
  - Searchable archive
  - Automatic searches with helpdesk ticket keywords

**Incident response: Documentation**

- Security policy
  - An ongoing challenge
- Documentation must be available
  - No questions
- Documentation always changes
  - Constant updating
  - Have a process in place
  - Use the wiki model

**Compliance**

- Compliance
  - Meeting the standards of laws, policies, and regulations
- A healthy catalog of rules
  - Across many aspects of business and life
  - Many are industry-specific or situational 
- Penalties
  - Fines
  - Loss of employment
  - Incarceration
- Scope
  - Domestic and international requirements

**Regulatory**

- Sarbanes-Oxley Act (SOX)
  - The Public Company Accounting Reform and Investor Protection Act of 2002
- The Health Insurance Portability and Accountability Act (HIPAA)
  - Extensive healthcare standards for storage, use, and transmission of healthcare information
- The Gramm-Leach-Bliley Act of 1999 (GLBA)
  - Disclosure of privacy information from financial institutions

**Acceptable use policies (AUP)**

- What is acceptable use of company assets?
  - Detailed documentation
  - May be documented in the Rules of Behavior
- Covers many topics
  - Internet use, telephones, computers, mobile devices, etc.
- Used by an organization to limit legal liability
  - If someone is dismissed, these are the well-documented reasons why

**Password policy**

- Passwords should be complex and all passwords should expire
  - Change every 30 days, 60 days, 90 days
- Critical systems might change more frequently
  - Every 15 days or every week
- The recovery process should not be trivial
  - Some organizations have a very formal process

**Account lockout and disablement**

- Too many bad passwords will cause a lockout
  - This should be normal for most users
  - This can cause big issues for service accounts
    - You might want this
- Disable accounts
  - Part of the normal change process
  - You don’t want to delete accounts
    - At least not initially

**Inventory management**

- A record of every asset
  - Routers, switches, cables, fiber modules, CSU/DSUs, etc.
- Financial records, audits, depreciation
  - Make/model, configuration, purchase date, location, etc.
- Tag the asset
  - Barcode, RFID, visible tracking number

**Change Management 4.2**

**Change management**

- Change control
  - A formal process for managing change
  - Avoid downtime, confusion, and mistakes
- Nothing changes without the process
  - Determine the scope of the change
  - Analyze the risk associated with the change
  - Create a plan
  - Get end-user approval
  - Present the proposal to the change control board
  - Have a backout plan if the change doesn’t work

**Scope the change**

- Determine the effect of the change
  - May be limited to a single server
  - Or an entire site
- A single change can be far reaching
  - Multiple applications
  - Internet connectivity
  - Remote site access
  - External customer access
- How long will this take?
  - No impact
  - Hours of downtime

**Risk analysis**

- Determine a risk value
  - i.e., high, medium, low
- The risks can be minor or far-reaching
  - The “fix” doesn’t actually fix anything
  - The fix breaks something else
  - Operating system failures
  - Data corruption
- What’s the risk with NOT making the change?
  - Security vulnerability
  - Application unavailability
  - Unexpected downtime to other services

**Plan for change**

- What’s it take to make the change?
  - Detailed information
  - Describe a technical process to other technical people
- Others can help identify unforeseen risk
  - A complete picture
- Scheduling
  - Time of day, day of week
  - Include completion timeframes

**End-user acceptance**

- Nothing happens without a sign-off
  - The end users of the application / network
- One of your jobs is to make them successful
  - They ultimately decide if a change is worth it to them
- Ideally, this is a formality
  - Of course, they have been involved through this entire process
  - There’s constant communication before and after

**Change board and approvals**

- Go or no go
  - Lots of discussion
- All important parts of the organization are represented
  - Potential changes can affect the entire company
- Some changes have priority
  - The change board makes the schedule
  - Some changes happen quickly, some take time
- This is the last step
  - The actual work comes next

**Backout plan**

- The change will work perfectly and nothing will ever go bad
  - Of course it will
- You should always have a way to revert your changes
  - Prepare for the worst, hope for the best
- This isn’t as easy as it sounds
  - Some changes are difficult to revert
- Always have backups
  - Always have backups

**Document changes**

- Something changed
  - Everyone needs to know
- Help desk documentation
  - Version numbers, network diagram, new server names
- Track changes over time
  - Cross-reference against help desk tickets
- Track before and after statistics
  - Better or worse?

**Disaster Recovery 4.3**

**Backup strategies**

- Image level
  - Bare metal backup using images
  - Operating system volume snapshots or hypervisor snapshots
  - Recover the entire system at once
  - Make an exact copy somewhere else
- File level
  - Copy individual files to a backup
  - May not necessarily store all system files
  - May need to rebuild the OS and then perform a file restore

**Critical application backups**

- Application software
  - Often distributed across multiple servers
- Application data
  - Databases, other data storage
- Location of data
  - Local and cloud-based
- All of these are needed when restoring
  - They all work together

**Backup testing**

- It’s not enough to perform the backup
  - You have to be able to restore
- Disaster recovery testing
  - Simulate a disaster situation
  - Restore from backup
- Confirm the restoration
  - Test the restored application and data
- Perform periodic audits
  - Always have a good backup

**UPS**

- Uninterruptible Power Supply
  - Short-term backup power
  - Blackouts, brownouts, surges
- UPS types
  - Offline/Standby UPS
  - Line-interactive UPS
  - On-line/Double-conversion UPS
- Features
  - Auto shutdown, battery capacity, outlets, phone line suppression

**Surge suppressor**

- Not all power is “clean”
  - Self-inflicted power spikes and noise
  - Storms, power grid changes
- Spikes are diverted to ground
- Noise filters remove line noise
  - Decibel (Db) levels at a specified frequency
    - Higher Db is better

**Cloud storage**

- Data is available anywhere, anytime, on any device
  - If you have a network, you have your data
- Advantages over local backups
  - No tape drives to manage
  - No offsite storage processing
- Disadvantages over local backups
  - Data is not under your direct control
  - Strong encryption mechanisms are critical

**Account recovery options**

- Apps won’t work if users can’t login
  - You Windows Domain will most likely be the foundation of your recovery efforts
- Consider other authentication requirements
  - Multi-factor authentication validation
  - Additional authentication databases
  - RADIUS, TACACS
- Another good reason for centralized administration
  - No local accounts

**Safety Procedures 4.4**

**WARNING**

- Power is dangerous
- Remove all power sources before working
- Don’t touch anything if you aren’t sure
- Replace entire power supply units
  - Don’t repair internal components
- High voltage
  - Power supplies, displays, laser printers

**Equipment grounding**

- Most computer products connect to ground
  - Divert any electrical faults away from people
- Also applies to equipment racks
  - Large ground wire
- Don’t remove the ground connection
  - It’s there to protect you
- Never connect yourself to an electrical ground
  - This is not a way to prevent ESD

**Handling toxic waste**

- Batteries
  - Uninterruptible Power Supplies
  - Dispose at your local hazardous waste facility
- CRTs
  - Cathode ray tubes - there’s a few of those left
  - Glass contains lead
  - Dispose at your local hazardous waste facility
- Toner
  - Recycle and reuse
  - Many printer manufacturers provide a return box
  - Some office supply companies will provide a discount for each cartridge


**Mobile device disposal**

- Wipe your data, if possible
  - This isn’t always an option
- Manufacturer or phone service provider may have a recycling program
  - Or an upgrade program
- Dispose at a local hazardous waste facility
  - Do not throw in the trash

**Personal safety**

- Remove jewelry
  - And name badge neck straps
  - Or use breakaway lanyards
- Lifting technique
  - Lift with your legs, keep your back straight
  - Don’t carry overweight items
  - You can get equipment to lift
- Electrical fire safety
  - Don’t use water or foam
  - Use carbon dioxide, FM-200, or other dry chemicals
  - Remove the power source
- Cable management
  - Avoid trip hazards
  - Use cable ties or velcro
- Safety goggles
  - Useful when working with chemicals
  - Printer repair, toner, batteries
- Air filter mask
  - Dusty computers
  - Printer toner

**Local government regulations**

- Health and safety laws
  - Vary widely depending on your location
  - Keep the workplace hazard-free
- Building codes
  - Fire prevention, electrical codes
- Environmental regulation
  - High-tech waste disposal


**Managing Electrostatic Discharge 4.4**

**What is electrostatic discharge?**

- Static electricity
  - Electricity that doesn’t move
- Static electricity isn’t harmful to computer
  - It’s the discharge that gets them
- ESD can be very damaging to computer components
  - Silicon is very sensitive to high voltages
- Feel static discharge: ~3,500 volts
  - Damage an electronic component: 100 volts or less

**Controlling ESD**

- Humidity over 60% helps control ESD
  - Won’t prevent all possible ESD
  - Keeping an air conditioned room at 60^ humidity isn’t very practical
- Use your hand to self-ground
  - Touch the exposed metal chassis before touching a component
  - You’ll want to unplug the power connection
    - Always a good idea. Really.
  - Do not connect yourself to an electrical ground
- Try not to touch the components directly
  - Card edges only

**Preventing static discharge**

- Anti-static strap
  - Connect your wrist to a metal part of the computer
- Anti-static pad
  - A workspace for the computer
- Anti-static mat
  - A mat for standing or sitting
- Anti-static bag
  - Safely move or ship components







**Environmental Impacts 4.5**

**Disposal procedures**

- Read your Material Safety Data Sheets (MSDS)
  - United States Department of Labor, Occupational Safety and Health Administration (OSHA)
    - <http://www.osha.gov>, Index page
- Provides information for all hazardous chemicals
  - Batteries, display devices / CRTs, chemical solvents and cans, toner and ink cartridges
- Sometimes abbreviated as Safety Data Sheet (SDS)
  - Different names in each country

**MSDS info**

- Product and company information
- Composition / ingredients
- Hazard information
- First aid measures
- Fire-fighting measures
- Accident release / leaking
- Handling and Storage
- Much more

**Room control**

- Temperature
  - Devices need constant cooling
  - So do humans
- Humidity level
  - High humidity promotes condensation
  - Low humidity promotes static discharges
  - 50% is a good number
- Proper ventilation
  - Computers generate heat
  - Don’t put everything in a closet

**UPS**

- Uninterruptible Power Supply
  - Backup power
  - Blackouts, brownouts, surges
- UPS types
  - Standby UPS
  - Line-interactive UPS
  - On-line UPS
- Features
  - Auto shutdown, battery capacity, outlets, phone line suppression

**Surge suppressor**

- Not all power is “clean”
  - Self-inflicted power spikes and noise
  - Storms, power grid changes
- Spikes are diverted to ground
- Noise filters remove line noise
  - Decibel (Db) levels at a specified frequency
    - Higher Db is better

**Surge suppressor specs**

- Joule ratings
  - Surge absorption
    - 200=good, 400=better
    - Look for over 600 joules of protection
- Surge amp ratings
  - Higher is better
- UL 1449 voltage let-through ratings
  - Ratings at 500, 400, and 330 colts
  - Lower is better

**Protection from airborne particles**

- Enclosures
  - Protect computers on a manufacturing floor
  - Protect from dust, oil, smoke
- Air filters and masks
  - Protect against airborne particles
  - Dust in computer cases
  - Laser printer toner

**Dust and debris**

- Cleaning
  - Neutral detergents
  - No ammonia-based cleaning liquids
  - Avoid isopropyl alcohol
- Vacuum
  - Use a “computer” vacuum
  - Maintain ventilation
- Compressed air pump
  - Try not to use compressed air in a can

**Local government regulations**

- Environmental regulations
  - May have very specific controls
- The obvious
  - Hazardous waste
  - Batteries
  - Computer components
- The not-as-obvious
  - Paper disposal

**Privacy, Licensing, and Policies 4.6**

**Incident response: First response**

- Identify the issue
  - Logs, in person, monitoring data
- Report to proper channels
  - Don’t delay
- Collect and protect information relating to an event
  - Many different data sources and protection mechanisms

**Incident response: Documentation**

- Documentation must be available
  - No questions
- Gather as much information as possible
  - Written notes, pictures
- Documentation always changes
  - Constant updating
  - Have a process in place
  - Use the wiki model

**Incident response: Chain of custody**

- Control evidence
  - Maintain integrity
- Everyone who contacts the evidence
  - Avoid tampering
    - Use hashes
- Label and catalog everything
  - Seal, store, and protect
  - Digital signatures

**Licensing / EULA**

- Closed source / Commercial
  - Source code is private
  - End user gets compiled executable
- Free and Open Source (FOSS)
  - Source code is freely available
  - End user can compile their own executable
- End User Licensing Agreement
  - Determines how the software can be used
- Digital Rights Management (DRM)
  - Used to manage the use of software

**Licenses**

- Personal license
  - Designed for the home user
  - Usually associated with a single device
    - Or small group of devices owned by the same person
  - Perpetual (one time) purchase
- Enterprise license
  - Per-seat purchase / Site license
  - The software may be installed everywhere
  - Annual renewals

**PII - Personally identifiable information**

- Any data that can identify an individual
  - Part of your privacy policy - How will you handle PII?
- Not everyone realizes the importance of this data
  - It comes a “normal” part of the day
  - It can be easy to forget its importance
- July 2015 - U.S. Office of Personnel Management (OPM)
  - Compromised personal identifiable information
  - Personnel file information; name, SSN, date of birth, job assignments, etc.
  - Approximately 21.5 million people affected

**PCI DSS**

- Payment Card Industry Data Security Standard (PCI DSS)
  - A standard for protecting credit cards
- Six control objectives
  - Build and Maintain a Secure Network and Systems
  - Protect Cardholder Data
  - Maintain a Vulnerability Management Program
  - Implement Strong Access Control Measures
  - Regularly Monitor and Test Networks
  - Maintain an Information Security Policy

**GDPR - General Data Protection Regulation**

- European Union regulation
  - Data protection and privacy for individuals in the EU
  - Name, address, photo, email address, bank details, posts on social networking websites, medical information, a computer’s IP address, etc.
- Controls export of personal data
  - Users can decide where their data goes
- Gives individuals control of their personal data
  - A right to be forgotten
- Site privacy policy
  - Details all of the privacy rights for a user

**PHI - Protected Health Information**

- Health information associated with an individual
  - Health status, health care records, payments for health care, and much more
- Data between providers
  - Must maintain similar security requirements
- HIPAA regulations
  - Health Insurance Portability and Accountability Act of 1996

**Policies and best practices**

- Policies
  - General IT guidelines
  - Determines how technology should be used
  - Provides processes for handling important technology decisions
- Security best practices
  - Some security techniques are accepted standards
  - Covers both processes and technologies
  - You need a firewall. Use WPA2. Use strong passwords. What happens if there’s a breach

**Communication 4.7**

**Communication skills**

- One of the most useful skills for the troubleshooter
- One of the most difficult skills to master
- A skilled communicator is incredibly marketable

**Avoid jargon**

- Abbreviations and TLAs
  - Three Letter Acronyms
- Avoid acronyms and slang
  - Be the translator
- Communicate in terms that everyone can understand
  - Normal conversation puts everyone at ease
  - Decisions are based on what you say
- These are the easiest problems to avoid

**Avoid interrupting**

- But I know the answer
- Why do we interrupt?
  - We want to solve problems quickly
  - We want to show how smart we are
- Actively listen, take notes
  - Build a relationship with the customer
    - They’ll need help again someday
  - Don’t miss a key piece of information
  - Especially useful on the phone
- This skill takes time to perfect
  - The better you are, the more time you’ll save later

**Clarify customer statements**

- Ask pertinent questions
  - Drill-down into the details
  - Avoid an argument
  - Avoid being judgmental
- Repeat your understand of the problem back to the customer
  - Did I understand you correctly?
- Keep an open mind
  - Ask clarifying questions, even if the issue seems obvious
    - Never make assumptions

**Setting expectations**

- Offer different options
  - Repair
  - Replace
- Document everything
  - No room for questions
- Keep everyone informed
  - Even if the status is unchanged
- Follow up afterwards
  - Verify satisfaction

**Professionalism 4.7**

**Maintain positive attitude**

- Positive tone of voice
  - Partner with your customer
  - Project confidence
- Problems can’t always be fixed
  - Do your best
  - Provide helpful options
- Your attitude has a direct impact on the overall customer experience

**Avoid being judgmental**

- Cultural sensitivity
  - Use appropriate professional titles
- You’re the teacher
  - Not the warden
  - Leave insults on the playground
- Make people smarter
  - They’ll be better technologists
- You’re going to make some big mistakes
  - Remember them

**Be on time and avoid distractions**

- Don’t allow interruptions
  - No personal calls, no texting
  - Don’t talk to co-workers
- Apologize for delays and unintended distractions
- Create an environment for conversation
  - In person
    - Open and inviting
  - On the phone
    - Quiet background, clear audio
    - Stay off the speaker phone

**Difficult situations**

- Technical problems can be stressful
- Don’t argue or be defensive
  - Don’t dismiss
  - Don’t contradict
- Diffuse a difficult situation with listening and questions
  - Relationship-building
- Communicate
  - Even if there’s no update
- Never take the situation to social media

**Don’t minimize problems**

- Technical issues can be traumatic
  - Often money and/or jobs on the line
- Even the smallest problems can seem huge
  - Especially when things aren’t working
- Part technician, part counselor
  - Computers don’t have problems
  - People have problems

**Maintain confidentiality**

- Privacy concerns
  - Sensitive information
    - Both professional and private
  - On the computer, desktop, or printer
- Professional responsibilities
  - IT professionals have access to a lot of corporate data
- Personal respect
  - Treat people as you would want to be treated


**Scripting 4.8**

**Scripting and automation**

- Automate tasks
  - You don’t have to be there
  - Solve problems in your sleep
  - Monitor and resolve problems before they happen
- The need for speed
  - The script is as fast as the computer
  - No typing or delays
- Automate mundane tasks
  - You can do something more creative

**Scripting basics**

- Variables
  - Associate a name with an area of memory
  - x=1. y=x+7. Therefore, y=8
  - pi=3.14
  - greeting=”Hello and welcome.”
- String data types
  - name=”Professor Messer”
- Integer data types
  - Whole numbers (not fractions)
  - x=42
  - Perform numerical calculations
- Floating point data types
  - Numbers with decimal points
  - pi=3.14
- Loops
  - Perform a process over and over
  - Loop a certain number of times
  - Loop until something happens
- Comments
  - Annotate the code
  - There never seems to be enough of this

**Environment variables**

- Describes the operating system environment
  - Scripts use these to make decisions
- Common environment variables
  - Location of the Windows installation
  - The search path
  - The name of the computer
  - The drive letter and path of the user’s home directory

**Batch files**

- .bat file extension
  - Scripting for Windows at the command line
  - Legacy goes back to DOS and OS/2

**Windows PowerShell**

- Command line for system administrators
  - .ps1 file extension
  - Included with Windows 8/8.1 and 10
- Extend command-line functions
  - Uses cmdlets (command-lets)
  - PowerShell scripts and functions
  - Standalone executables
- Automate and integrate
  - System administration
  - Active Domain administration

**Microsoft Visual Basic Scripting Edition**

- VBScript
  - .vbs file extension
- General purpose scripting in Windows
  - Back-end web server scripting
  - Scripting on the Windows desktop
  - Scripting inside of Microsoft Office applications

**Shell script**

- Scripting the Unix/Linux shell
  - Automate and extend the command line
- Starts with a shebang or hash-bang #!
  - Often has a .sh file extension

**Python**

- General-purpose scripting language
  - .py file extension
- Popular in many technologies
  - Broad appeal and support

**JavaScript**

- Scripting inside of your browser
  - .js file extension
- Adds interactivity to HTML and CSS
  - Used on almost every web site
- JavaScript is not Java
  - Different developers and origins
  - Very different use and implementation

**Remote Access Technologies 4.9**

**RDP (Remote Desktop Protocol)**

- Share a desktop from a remote location over tcp/3389
- Remote Desktop Services on many Windows versions
- Can connect to an entire desktop or just an application
- Clients for Windows, MacOS, Linux, Unix, iPhone, and others

**Telnet**

- Telnet - Telecommunication Network
  - tcp/23
- Login to devices remotely
  - Console access
- Unencrypted communication
  - Not the best choice for production systems

**Secure Shell (SSH)**

- Encrypted console communication - tcp/22
- Looks and acts the same as Telnet - tcp/23

**Third-party tools**

- VNC (Virtual Network Computing)
  - Remote Frame Buffer (RFB) protocol
  - Clients for many operating systems
  - Many are open source
- Commercial solutions
  - TeamViewer, LogMeIn, etc.
- Screen sharing
  - Control the desktop
- File sharing
  - Transfer files between devices

**Security considerations**

- Microsoft Remote Desktop
  - An open port of tcp/3389 is a big tell
  - Brute force attack is common
- Third-party remote desktops
  - Often secured with just a username and password
  - There’s a lot of username/password re-use
- Once you’re in , you’re in
  - The desktop is all yours
  - Easy to jump to other systems
  - Obtain personal information, bank details
  - Make purchases from the user’s browser
