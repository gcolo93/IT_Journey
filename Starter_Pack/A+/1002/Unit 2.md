**Physical Security 2.1**

**Mantraps**

- One at a time, controlled groups
  - Managed control through an area
- All doors normally unlocked
  - Opening one door causes others to lock
- All doors normally locked
  - Unlocking one door prevents others from being unlocked
- One door open / other locked
  - when one is open, the other cannot be unlocked

**Door access controls**

- Conventional
  - Lock and key
- Deadbolt
  - Physical bolt
- Electronic
  - Keyless, PIN
- Token-based
  - RFID badge, magnetic swipe card, or key fob
- Biometric
  - Hand, fingers or retina
- Multi-factor
  - Smart card and PIN

**Tokens and cards**

- Smart card
  - Integrates with devices
  - May require a PIN
- USB token
  - Certificate is on the USB device
- Hardware or software tokens
  - Generates pseudo-random authentication codes
- Your phone
  - SMS a code to your phone

**Guards and access lists**

- Security guard
  - Physical protection
  - Validates identification of existing employees
  - Provides guest access
- ID badge
  - Picture, name, other details
  - Must be worn at all times
- Access list
  - Physical list of names
  - Enforced by security guard

**Biometrics**

- Biometric authentication
  - Fingerprint, retina, voiceprint
- Usually stores a mathematical representation of your biometric
  - Your actual fingerprint isn’t usually saved
- Difficult to change
  - You can change your password
  - You can’t change your fingerprint
- Used in very specific situations
  - Not foolproof

**Cable locks**

- Temporary security
  - Connect your hardware to something solid
- Cable works almost anywhere
  - Useful when mobile
- Most devices have a standard connector
  - Reinforced notch
- Not designed for long-term protection
  - Those cables are pretty thin

**Locking cabinets**

- Data center hardware is often managed by different groups
  - Responsibility lies with the owner
- Racks can be installed together
  - Side-to-side
- Enclosed cabinets with locks
  - Ventilation on front, back, top, and bottom

**USB locks**

- Prevent access to a USB port
  - Physical lock inside of the interface
- A secondary security option after disabling the interface in BIOS and/or OS
  - There’s always a way around security controls
- Relatively simple locks
  - Defense in depth

**Privacy filters**

- Control your input
  - Be aware of your surroundings
- Use privacy filters
- Keep your monitor out of sight
  - Away from windows and hallways






**Logical Security 2.2**

**Active Directory**

- Centralized management
  - Windows Domain Services
  - Limit and control access
- Login script
  - Map network drives
  - Update security software signatures
  - Update application software
- Group Policy/Updates
  - Define specific policies
  - Password complexity
  - Login restrictions
- Organizational Units
  - Structure Active Directory
  - can be based on the company (locations, departments)
- Home Folder
  - Assign a network share as the user’s home
  - \\server1\users\professormesser
- Folder redirection
  - Instead of a local folder, redirect to the server
  - Store the Documents folder on \\server1
  - Access files from anywhere

**Mobile Device Management (MDM)**

- Manage company-owned and user-owned mobile devices
  - BYOD - Bring Your Own Device
- Centralized management of the mobile devices
  - Specialized functionality
- Set policies on apps, data, camera, etc.
  - Control the remote device
  - The entire device or a “partition”
- Manage access control
  - Force screen locks and PINs on these single user devices

**Port security**

- Prevent unauthorized users from connecting to a switch interface
  - Alert or disable the port
- Based on the source MAC address
  - Even if forwarded from elsewhere
- Each port has its own config
  - Unique rules for every interface

**Port security example**

- Configure a maximum number of source MAC addresses on an interface
  - You decide how many is too many
  - You can also configure specific MAC addresses
- The switch monitors the number of unique MAC addresses
  - Maintains a list of every source MAC address
- Once you exceed the maximum, port security activates
  - Default is to disable the interface

**MAC filtering**

- Media Access Control
  - The “hardware” address
- Limit access through the physical hardware address
  - Keeps the neighbors out
  - Additional administration with visitors
- Easy to find working MAC addresses through wireless LAN analysis
  - MAC addresses can be spoofed
  - Free open-source software
- Security through obscurity

**Smart cards**

- Must have physical card to provide digital access
  - A digital certificate
- Multiple factors
  - Card with PIN  or fingerprint

**Certificate-based authentication**

- Smart card
  - Private key is on the card
- PIV (Personal Identity Verification) card
  - US Federal Government smart card
  - Picture and identification information
- CAC (Common Access Card)
  - US Department of Defense smart card
  - Picture and identification
- IEEE 802.1X
  - Gain access to the network using a certificate
  - On-device storage or separate physical device

**Anti-virus and anti-malware**

- Anti-malware software runs on the computer
  - Each device manages its own protection
- Updates must be completed on all devices
  - This becomes a scaling issue
- Large organizations need enterprise management
  - Track updates, push updates, confirm updates, manage engine updates
- Mobility adds to the challenge
  - Need additional management

**Host-based firewalls**

- “Personal” firewalls
  - Software-based
- Included in many operating systems
  - 3rd-part solutions also available
- Stops unauthorized network access
  - “Stateful” firewall
  - Block traffic by application
- Windows Firewall
  - Filters traffic by port number and application

**Network-based firewalls**

- Filters traffic by port number
  - HTTP is 80, SSH is 22
  - Next-generation firewalls can identify the application
- Can encrypt traffic into/out of the network
  - Protect your traffic between sites
- Can proxy traffic
  - A common security technique
- Most firewalls can be layer 3 devices (routers)
  - Usually sits on the ingress/egress of the network

**User authentication**

- Identifier
  - Something unique
  - In Windows, every account has a Security Identifier (SID)
- Credentials
  - The information used to authenticate the user
  - Password, smart card, PIN code, etc.
- Profile
  - Information stored about the user
  - Name, contact information group membership, etc.

**Strong passwords**

- Weak passwords can be difficult to protect against
  - Interactive brute force
  - Hashed passwords can be brute forced offline
- Passwords need complexity and constant refresh
  - Reduce the change of a brute force
  - Reduce the scope if a password is found
- Annual password analysis from SplashData
  - Examines leaked password files

**Multi-factor authentication**

- More than one factor
  - Something you are
  - Something you have
  - Something you know
  - Somewhere you are
  - Something you do
- Can be expensive
  - Separate hardware tokens
- Can be inexpensive
  - Free smartphone applications
  - Software-based token generator

**Software tokens**

- Pseudo-random number generator
  - Can’t guess it
  - Changes constantly
- Saves money
  - Free smartphone applications
  - No separate device to lose




**Directory permissions**

- NTFS permissions
  - Much more granular than FAT
  - Lock down access
  - Prevent accidental modification or deletion
  - Some information shouldn’t be seen
- User permissions
  - Everyone isn’t an Administrator
  - Assign proper rights and permissions
  - This may be an involved audit

**VPN concentrator**

- Virtual Private Network
  - Encrypt (private) data traversing a public network
- Concentrator
  - Encryption/decryption access device
- Many deployment options
  - Specialized cryptographic hardware
  - Software-based options available
- Used with client software
  - Sometimes built into the OS

` `**Data Loss Prevention (DLP)**

- Where’s your data?
  - Social Security numbers, credit card numbers, medical records
- Stop the data before the bad guys get it
  - Data “leakage”
- So many sources, so many destinations
  - Often requires multiple solutions in different places

**Access Control Lists (ACLs)**

- Used to allow or deny traffic
  - Also used for NAT, QoS, etc.
- Defined on the ingress or egress of an interface
  - Often on a router or switch
  - Incoming or outgoing
- ACLs evaluate on certain criteria
  - Source IP, Destination IP, TCP port numbers, UDP port numbers, ICMP
- Deny or permit
  - What happens when an ACL matches the traffic?

**Email filtering**

- Unsolicited email
  - Stop it at the gateway before it reaches the user
  - On-site or cloud-based
- Scan and block malicious software
  - Executables known vulnerabilities
  - Phishing attempts
  - Other unwanted content

**Trust/untrusted software sources**

- Consider the source
  - May not have access to the code
  - Even then, may not have the time to audit
- Trusted sources
  - Internal applications
  - Well-known publishers
  - Digitally-signed applications
- Untrusted sources
  - Applications from third-party sites
  - Links from an email
  - Pop-up/drive-by downloads

**Least privilege**

- Rights and permissions should be set to the bare minimum
  - You only get exactly what’s needed to complete your objective
- All user accounts must be limited
  - Applications should run with minimal privileges
- Don’t allow users to run with administrative privileges
  - Limits the scope of malicious behavior


**Wireless Security 2.3**

**Wireless encryption**

- All wireless computers are radio transmitters and receivers
  - Anyone can listen in
- Solution: Encrypt the data
  - Everyone gets the password
  - Or their own password
- Only people with the password can transmit and listen
  - WPA and WPA2

**WPA (Wi-Fi Protected Access)**

- 2002: WPA was the replacement for serious cryptographic weaknesses in WEP (Wired Equivalent Privacy)
  - Don’t use WEP
- Needed a short-term bridge between WEP and whatever would be the successor
  - Run on existing hardware
- WPA: RC4 with TKIP (Temporal Key Integrity Protocol)
  - Initialization Vector (IV) is larger and an encrypted hash
  - Every packet gets a unique 128-bit encryption key

**Temporal Key Integrity Protocol**

- Mixed the keys
  - Combines the secret root key with the IV
- Adds a sequence counter
  - Prevents replay attacks
- Implements a 64-bit Message Integrity Check
  - Protects against tampering
- TKIP has its own set of vulnerabilities
  - Deprecated in the 802.11-2012 standard

**WPA2 and CCMP**

- WPA2 certification began in 2004
  - AES (Advanced Encryption Standard) replaced RC4
  - CCMP (Counter Mode with Cipher Block Chaining Message Authentication Code Protocol) replaced TKIP
- CCMP block cipher mode
  - Uses AES for data confidentiality
  - 128-bit key and a 128-bit block size
  - Requires additional computing resources
- CCMP security services
  - Data confidentiality (AES), authentication, and access control

**Wireless security modes**

- Configure the authentication on your wireless access point / wireless router
- Open System
  - No authentication password is required
- WPA2-Personal /WPA2-PSK
  - WPA2 with a pre-shared key
  - Everyone uses the same 256-bit key
- WPA2-Enterprise / WPA2-802.1X
  - Authenticates users individually with an authentication server (i.e., RADIUS, TACACS+)
  - Add additional factors

**RADIUS (Remote Authentication Dial-in User Service)**

- One of the more common AAA protocols
  - Supported on a wide variety of platforms and devices
  - Not just for dial-in
- Centralized authentication for users
  - Routers, switches, firewalls
  - Server authentication
  - Remote VPN access
  - 802.1X network access
- RADIUS services available on almost any server operating system

**TACACS**

- Terminal Access Controller Access-Control System
  - Remote authentication protocol
  - Created to control access to dial-up lines to ARPANET
- TACACS+
  - The latest version of  TACACS
  - More authentication requests and response codes
  - Released as an open standard in 1993

**Types of Malware 2.4**

**Ransomware**

- The bad guys want your money
  - They’ll take your computer in the meantime
- May be a fake ransom
  - Locks your computer “by the police”
- The ransom may be avoided
  - A security professional may be able to remove these kinds of malware

**Crypto-malware**

- The latest generation of ransomware
  - Your data is unavailable until you provide cash
- Malware encrypts your data files
  - Pictures, documents, music, movies, etc.
  - Your OS remains available
  - They want you running, but not working
- You must pay the bad guys to obtain the description key
  - Untraceable payment system
  - An unfortunate use of public-key cryptography

**Trojan horse**

- Used by the Greeks to capture Troy from the Trojans
  - A digital wooden horse
- Software that pretends to be something else
  - So it can conquer your computer
  - Doesn’t really care much about replicating
- Circumvents your existing security
  - Anti-virus may catch it when it runs
    - The better trojans are built to avoid and disable AV
- Once it’s inside it has free reign
  - And it may open the gates for other programs

**Spyware**

- Malware that spies on you
  - Advertising, identity theft, affiliate fraud
- Can trick you into installing
  - Peer to peer, fake security software
- Browser monitoring
  - Capture surfing habits
- Keyloggers
  - Capture every keystroke and sends it back to the “mothership”

**Keyloggers**

- Your keystrokes contain valuable information
  - Web site login URLs, passwords email messages
- Save all of your input
  - Send it to the bad guys
- Circumvents encryption protections
  - Your keystrokes are in the clear
- Other data logging
  - Clipboard logging, screen logging, instant messaging, search engine queries

**Rootkits**

- Originally a Unix technique
  - The “root” in rootkit
- Modifies core system files
  - Part of the kernel
- Can be invisible to the operating system
  - Won’t see it in Task Manager
- Also invisible to traditional antivirus utilities
  - If you can’t see it, you can’t stop it

**Virus**

- Malware that can reproduce itself
  - With your assistance
  - It needs you to execute a program
- Reproduces through file systems or the network
  - Just running a program can spread a virus
- May or may not cause problems
  - Some viruses are invisible, some are annoying
- Anti-virus is very common
  - Thousands of new viruses every week
  - Is your signature file updated?

**Virus types**

- Program viruses
  - It’s part of the application
- Boot sector viruses
  - Who needs an OS?
- Script viruses
  - Operating system and browser-based
- Macro viruses
  - Common in Microsoft Office

**Worms**

- Malware that self-replicates
  - Doesn’t need you to do anything
  - Uses the network as a transmission medium
  - Self-propagates and spreads quickly
- Worms are pretty bad things
  - Can take over many systems very quickly
- Firewalls and IDS/IPS can mitigate many worm infestations
  - Doesn’t help much once the worm gets inside

**Wannacry worm:** Starts on an already infected system. If it finds another system that is vulnerable, it will exploit it with EternalBlue. Once EternalBlue is on the system, it downloads the malware and installs WannaCry onto that operating system. The process then repeats itself. The process will continue until you patch the operating system or block this traffic on the network.

**Botnets**

- Robot networks
  - Skynet is self-aware
- Once your machine is infected, it becomes a bot
  - You may not even know
- How does it get on your computer?
  - Trojan Horse or you run a program or click an ad you thought was legit, but…
  - OS or application vulnerability
- A day in the life of a bot
  - Sits around waiting for instructions.

**Anti-Malware Tools 2.4**

**Anti-virus and anti-malware**

- Anti-virus and anti-malware
  - You need both
- Real-time options
  - Not just an on-demand scan
- Modern anti-malware recognizes malicious activity
  - Doesn’t require a specific set of signatures

**Windows Recovery Environment**

- Very powerful
- Very dangerous
  - Last resort
- Complete control
  - Fix your problems before the system starts
  - Remove malicious software
- Requires additional information
  - Use, copy, rename, or replace operating system files and folders
  - Enable or disable service or device startup
  - Repair the file system boot sector or the hamster boot record (MBR)

**Starting the console**

- Windows 7 - System Recovery Options / Command Prompt
  - Boot from installation media
  - Or select from F8 Advanced Boot Menu
- Windows 8/8.1/10 Troubleshoot / Advanced Options / Command Prompt
  - Boot from installation media

**Backup / restore**

- Always have a backup
  - this is the best insurance policy ever
- Image backup built into Windows 
  - In Windows 8/10 it’s called Backup and Restore (Windows 7)
- This is the only way to be 100% sure that malware has been removed

**End user education**

- One on one
  - Personal training
- Posters and signs
  - High visibility
- Message board posting
- Login message
- Intranet page
  - Always available

**Software firewalls**

- Monitor the local computer
  - Alert on unknown or unauthorized network communication
- Prevent malware communication
  - Downloads after infection
  - Botnet communication
- Use Windows Firewall
  - At a minimum
- Runs by default
  - Constantly monitoring
  - Any network connection



**Secure DNS services**

- External/Hosted DNS service
  - Provides additional security services
- Real-time domain blocking
  - Sites containing malware are not resolvable
- Block harmful websites
  - Phishing sites, parked domains
- Secure platforms
  - Avoid DNS cache poisoning attacks

**Social Engineering Attacks 2.5**

**Effective social engineering**

- Constantly changing
  - You never know what they’ll use next
- May involve multiple people
  - And multiple organizations
  - There are ties connecting many organizations
- May be in person or electronic
  - Phone calls from aggressive “customers”
  - Emailed funeral notifications of a friend or associate

**Social engineering principles**

- Authority
  - The social engineer is in charge
  - I’m calling from the help desk/office of the CEO/police
- Intimidation
  - There will be bad things if you don’t help
- Consensus / Social proof
  - Convince based on what’s normally expected
- Scarcity
  - The situation will not be this way for long
  - Must make the change before time expires
- Urgency
  - Works alongside scarcity
  - Act quickly, don’t think
- Familiarity / Liking
  - Someone you know, we have common friends
- Trust
  - Someone who is safe

**Phishing**

- Social engineering with a touch of spoofing
  - Often delivered by spam, IM, etc.
  - Very remarkable when well done
- Don’t be fooled
  - Check the URL
- Usually there’s something not quite right
  - Spelling, fonts, graphics
- Vishing is done over the phone
  - Fake security checks or bank updates

**Spear phishing**

- Phishing with inside information
  - Makes the attack more believable
  - Spear phishing the SEO is “whaling”
- April 2011 - Epsilon
  - Less than 3,000 email addresses attacked
  - 100% of email operations staff
  - Downloaded antivirus disabler, keylogger, and remote admin tool
- April 2011 - Oak Ridge National Laboratory
  - Email from the “Human Resources Department”
  - 530 employees targeted, 57 people clicked, 2 were infected
  - Data downloaded, servers infected with malware

**Impersonation**

- Pretend to be someone you aren’t
  - Halloween for the fraudsters
- User some of those details you got from the dumpster
  - You can trust me, I’m with your help desk
- Attack the victim as someone higher in rank
  - Office of the Vice President for Scamming
- Throw tons of technical details around
  - Catastrophic feedback due to the depolarization of the differential magnetometer
- Be a buddy
  - How about those Cubs?




**Shoulder surfing**

- You have access to important information
  - Many people want to see
  - Curiosity, industrial espionage, competitive advantage
- This is surprisingly easy
  - Airports / flights
  - Hallway-facing monitors
  - Coffee shops
- Surf from afar
  - Binoculars / Telescopes
    - Easy in the big city
  - Webcam monitoring

**Tailgating**

- Use someone else to gain access to a building
  - Not an accident
- Johnny Long / No Tech Hacking
  - Blend in with clothing
  - 3rd-party with a legitimate reason
  - Temporarily take up smoking
  - I still prefer bringing doughnuts
- Once inside, there’s little to stop you
  - Most security stops at the border

**Dumpster diving**

- Mobile garbage bin
  - United States brand name “Dumpster”
    - Similar to a rubbish skip
- Important information thrown out with the trash
- Gather details that can be used for a different attack 
  - Impersonate names, use phone numbers
- Timing is important
  - Just after end of month, end of quarter
  - Based on pickup schedule






**Denial of Service 2.5**

**Denial of Service**

- Force a service to fail
  - Overload the service
- Take advantage of a design failure or vulnerability
  - Keep your systems patched
- Cause a system to be unavailable
  - Competitive advantage
- Create a smokescreen for some other exploit
  - Precursor to a DNS spoofing attack
- Doesn’t have to be complicated
  - Turn off the power

**A “friendly” DoS**

- Unintentional DoSing
  - It’s not always a ne’er-do-well
- Network DoS
  - Layer 2 loop with ST
- Bandwidth DoS
  - Downloading multi-gigabyte Linux distributions over a DSL line
- The water line breaks
  - Get a good shop vacuum

**Distributed Denial of Service (DDoS)**

- Launch an army of computers to bring down a service
  - Use all the bandwidth or resources - traffic spike
- This is why the bad guys have botnets
  - Thousands or millions of computers at your command
  - At its peak, Zeus botnet infected over 3.6 million PCs
  - Coordinated attack
- The attackers are zombies
  - Many people have no idea they are participating in a botnet

**Mitigating DDoS attacks**

- May be able to filter out traffic patterns
  - Stop the traffic at your firewall
- Internet service provider may have anti-DDoS systems
  - These can help “turn down” the DDoS volume
- Third-party technologies

**Zero-Day Attacks 2.5**

**Zero-day attacks**

- Many applications have vulnerabilities
  - We’ve just not found them yet
- Someone is working hard to find the next big vulnerability
  - The good guys share these with the developer
- Bad guys keep these yet-to-be-discovered holes to themselves
  - They want to use these vulnerabilities for personal gain
- Zero-day
  - The vulnerability has not been detected or published
  - Zero-day exploits are increasingly common
- Common Vulnerabilities and Exposures (CVE)
  - <http://cve.mitre.org/>

**Zero-Day vulnerabilities**

- March 2017
  - CVE-2017-0199 - Microsoft Office/WordPad Remote Code Execution Vulnerability w/Windows API
  - Open a Microsoft Office or WordPad file
  - SophosLabs documented attacks in the wild since November 2016
- May 2019
  - CVE-2019-0863 - Windows Error Reporting Service
  - Elevation of privilege vulnerability
  - Windows Error Reporting interacting with files
  - Discovered in the wild
  - Access was elevated on compromised systems
  - Regular accounts were able to run with admin access

**Man-in-the-Middle 2.5**

**Man-in-the-Middle**

- How can a bad guy watch without you knowing?
  - Man-in-the-middle
- Redirects your traffic
  - Then passes it on to the destination
  - You never know your traffic was redirected
- ARP poisoning
  - ARP has no security

**ARP poisoning (spoofing)**

**Mitigating man-in-the-middle**

- Use encrypted protocols
  - HTTPS, SSH
- Communicate over a secure channel
  - Client-based VPN
- Use encrypted wireless networks
  - Avoid insecure networks
  - Public Wifi, hotels

**Brute Force Attacks 2.5**

**The password file**

- Different across operating systems
  - Different hash methods

**Brute force**

- The password is the key
  - Secret phrase
  - Stored hash
- Brute force attacks - Online
  - Keep trying the login process
  - Very slow
  - Most accounts will lockout after a number of failed attempts
- Brute force the hash - Offline
  - Obtain the list of users and hashes
  - Calculate a password hash, compare it to a stored hash
  - Large computational resource requirement

**Dictionary attacks**

- People use common words as passwords
  - You can find them in the dictionary
- If you’re using brute force you should start with the easy ones
  - 123456, password, ninja, football
- Many common wordlists available on the ‘net
  - Some are customized by language or line of work
- This will catch the low-hanging fruit
  - You’ll need some smarter attacks for the smarter people

**Rainbow tables**

- An optimized pre-built set of hashes
  - Doesn’t need to contain every hash
  - The calculations have already been done
- Remarkable speed increase
  - Especially with longer password lengths
- Need different tables for different hashing methods
  - Windows is different than MySQL
- Rainbow tables won’t work with salted hashes
  - Additional random value added to the original hash

**Spoofing 2.5**

**Spoofing**

- Pretend to be something you aren’t
  - Fake web server, fake DNS server, etc.
- Email address spoofing
  - The sending address of an email isn’t really the sender
- Caller ID spoofing
  - The incoming call information is completely fake
- Man-in-the-middle attacks
  - The person in the middle of the conversation pretends to be both endpoints

**MAC spoofing**

- Your Ethernet device has a MAC address
  - A unique burned-in address
  - Most drivers allow you to change this
- Changing the MAC address can be legitimate
  - Internet provider expects a certain MAC address
  - Certain applications require a particular MAC address
- It might not be legitimate
  - Circumvent MAC-based ACLs
  - Fake-out a wireless address filter
- Very difficult to detect
  - How do you know it’s not the original device?

**IP address spoofing**

- Take someone else’s IP address
  - Actual device
  - Pretend to be somewhere you are not
- Can be legitimate
  - Load balancing 
  - Load testing
- May not be legitimate
  - ARP poisoning 
  - DNS amplification / DDoS
- Easier to identify than MAC address spoofing
  - Apply rules to prevent invalid traffic, enable switch security

**Non-compliant Systems 2.5**

**Non-compliant Systems**

- A constant challenge
  - There are always changes and updates
- Standard operating environments (SOE)
  - A set of tested and approved hardware/software systems
  - Often a standard operating system image
- Operating system and application updates
  - Must have patches to be in compliance
  - OS updates, anti-virus signatures
  - Can be checked and verified before access is given

**Protecting against non-compliant systems**

- Operating system control
  - Apply policies that will prevent non-compliant software
- Monitor the network for application traffic
  - Next-generation firewalls with application visibility
- Perform periodic scans
  - Login systems can scan for non-compliance
  - Require correction before the system is given access









**Windows Security Settings 2.6**

**Users and groups**

- Users
  - Administrator
    - The Windows super-user
  - Guest
    - Limited access
  - Standard Users
- Groups
  - Power Users
    - Not much more control than a regular user

**NTFS vs. Share permissions**

- NTFS permissions apply from local and network connections
- Share permissions only apply to connections over the network
  - A “network share”
- The most restrictive setting wins
  - Deny beats allow
- NTFS permissions are inherited from the parent object
  - Unless you move to a different folder on the same volume

**Shared files and folders**

- Administrative shares
  - Hidden shares (i.e., C$) created during installation 
  - Local shares are created by users
- System files and folders
  - C$ - \
  - ADMIN$ - \Windows
  - PRINT$ - Printers folder
- Computer Management / Shared Folders
  - net share

**Explicit and inherited permissions**

- Explicit permissions
  - Set default permissions for a share
- Inherited permissions
  - Propagated from the parent object to the child object
  - Set a permission once, it applies to everything underneath
- Explicit permissions take precedence over inherited permissions
  - Even inherited deny permissions

**User authentication**

- Authentication
  - Prove you are the valid account holder
  - Username / Password
  - Perhaps additional credentials
- Single sign-on (SSO)
  - Windows Domain
  - Provide credentials one time
    - No additional pop-ups or interruptions
  - Managed through Kerberos

**Run as administrator**

- Administrators have special rights and permissions
  - Editing system files, installing services
- Use rights and permissions of the administrator
  - You don’t get these by default, even if you’re in the Administrators group
- Right-click the application
  - Run as administrator
  - OR Ctrl-Shift-Enter

**BitLocker**

- Encrypt an entire volume
  - Not just a single file
  - Protects all of your data, including the OS
- Lose your laptop?
  - Doesn’t matter without the password
- Data is always protected
  - Even if the physical drive is moved to another computer
- BitLocker To Go
  - Encrypt removable USB flash drives

**EFS**

- Encrypting File System
  - Encrypt at the filesystem level
  - On NTFS
- OS support
  - 7  Professional, Enterprise and Ultimate
  - 8 and 8.1 Pro and Enterprise
  - 10 Pro, Enterprise, and Education
- Uses password and username to encrypt the key
  - Administrative resets will cause EFS files to be inaccessible

**Workstation Security Best Practices 2.7**

**Password complexity and length**

- Make your password strong
  - No single words
  - No obvious passwords
  - Mix upper and lower case
  - Use special characters
- A strong password is at least 8 characters
  - Consider a phrase or set of words
- Set password expiration, require change
  - System remembers password history, requires unique passwords

**Password expiration and recovery**

- All passwords should expire
  - Change very 30 days, 60 days, 90 days
- Critical systems might change more frequently
  - Every 15 days or every week
- The recovery process should not be trivial
  - Some organizations have a very formal process

**Desktop security**

- Require a screensaver password
  - Integrate with login credentials
  - Can be administratively enforced
  - Automatically lock after a timeout
- Disable autorun
  - autorun.inf in Vista
    - No Autorun in Windows 7, 8/8.1, or 10
  - Disabled through the registry
- Consider changing AutoPlay
  - Get the latest security patches
    - Updates to autorun.inf and AutoPlay


**Password best practices**

- Changing default usernames/passwords
  - All devices have defaults
  - There are many websites that document these
- BIOS/UEFI passwords
  - Supervisor/Administrator password: Prevent BIOS changes
  - User password: Prevent booting
- Requiring passwords
  - Always require passwords
  - No blank passwords
  - No automated logins

**Restricting user permissions**

- User permissions
  - Everyone isn’t an Administrator
  - Assign proper rights and permissions
  - The may be an involved audit
- Assign rights based on groups
  - More difficult to manage per-user rights
  - Becomes more useful as you grow
- Login time restrictions
  - Only login during working hours
  - Restrict after-hours activities

**Disabling unnecessary accounts**

- All operating systems include other accounts
  - guest, root, mail, etc.
- Not all accounts are necessary
  - Disable/remove the unnecessary
  - Disable the guest account
- Disable interactive logins
  - Not all accounts need to login
- Change the default usernames
  - User:admin Password:admin
  - Helps with brute-force attacks





**Account lockout and disablement**

- Too many bad passwords will cause a lockout
  - This should be normal for most users
  - This can cause big issues for service accounts
    - You might want this
- Disable user accounts
  - Part of the normal change process
  - You don’t want to delete accounts
    - At least not initially

**Active Directory**

- Windows networks can be centrally managed
  - Active Directory Domain Services (AD DS)
- Create and delete accounts
  - Add users to the domain
  - Remove user accounts
- Reset passwords and unlock accounts
- Disable accounts
  - Off-boarding or security processes

**Data encryption**

- Full-disk encryption
  - Encrypt the entire drive
- Filesystem encryption
  - Individual files and folders
- Removable media
  - Protect those USB flash drives
- Key backups are critical
  - You always need to have a copy
  - This may be integrated into Active Directory
  - You’ll want to keep the key handy

**Patch and update management**

- Keep OS and applications updated
  - Security and stability improvements
- Built-in to the operating system
  - Updates are deployed as available
  - Deployment may be managed internally
- Many applications include their own updater
  - Check for updates when starting
- Always stay up to date
  - Security vulnerabilities are exploited quickly

**Securing Mobile Devices 2.8**

**Screen Locks**

- Restrict access to the device
  - You’re going to leave it somewhere
- Fingerprint - Built-in fingerprint reader
- Face Unlock - Face recognition
- Swipe - Choose a pattern
- Passcode - Choose a PIN or add complexity
- Failed attempts
  - iOS: Erase everything after 10 failed attempts
  - Android: Lock the device and require a Google login

**Locator applications and remote wipe**

- Built-in GPS
  - And location “helpers”
- Find your phone
  - On a map.
- Control from afar
  - Make a sound
  - Display a message
- Wipe everything 
  - At least your data is safe

**Remote backup**

- Difficult to backup something that’s always moving
  - Backup to the cloud
- Constant backup
  - No manual process
- Backup without wires
  - Use the existing network
- Restore with one click
  - Restores everything
  - Authenticate and wait



**Anti-virus and Anti-malware**

- Apple iOS
  - Closed environment, tightly regulated
  - Malware has to find a vulnerability
- Android
  - More open, apps can be installed from anywhere
  - Easier for malware to find its way in
- Apps run in a “sandbox”
  - You control what data an app can view

**Patching/OS updates**

- All devices need updates
  - Even mobile devices
- Device patches
  - Security updates
- Operating system updates
  - New features, bug fixes
- Don’t get behind
  - Avoid security problems

**Biometric authentication**

- Multi-factor authentication
  - More than one factor
  - Passcode, password, swipe pattern
  - Fingerprint, face, iris
- A phone is always with you
  - And you’re a good source of data
- We’re just figuring this out
  - Biometrics have a long way to go
  - Use as many factors as necessary

**Authenticator apps**

- Pseudo-random token generators
  - A useful authentication factor
- Carry around physical token devices
- You’re carrying your phone around
  - And it’s pretty powerful

**Full device encryption**

- Encrypt all device data
  - Phone keeps the key
- iOS 8 and later
  - Personal data is encrypted with your passcode
- Android
  - Full device encryption can be turned on

**Trusted vs. untrusted sources**

- Once malware is on a phone, it has a huge amount of access
  - Don’t install APK files from an untrusted source
- iOS
  - All apps are curated by Apple
- Android
  - Apps can be downloaded from Google Play or sideloaded
  - This is where problems can occur

**Firewalls**

- Mobile phones don’t include a firewall
  - Most activity is outbound, not inbound
- Some mobile firewall apps are available
  - Most for Android
  - None seem to be widely used
- Enterprise environments can control mobile apps
  - Firewalls can allow or disallow access

**Policies and procedures**

- Manage company-owned and user-owned mobile devices
  - BYOD - Bring Your Own Device
- Centralized management of the mobile devices
  - Specialized functionality / Mobile Device Manager (MDM)
- Set policies on apps, data, camera, etc.
  - Control the remote device
  - The entire device or a “partition”
- Manage access control
  - Force screen locks and PINs on these single user devices






**Data Destruction and Disposal 2.9**

**Physical destruction**

- Shredder
  - Heavy machinery
  - Complete destruction
- Drill / Hammer
  - Quick and easy
  - Platters, all the way through
- Electromagnetic (degaussing)
  - Remove the magnetic field
  - Destroys the drive data and the electronics
- Incineration
  - Fire is hot.

**Certificate of destruction**

- Destruction is often done by a 3rd party
  - How many drills and degaussers do you have?
- Need confirmation that your data is destroyed
  - Service should include a certificate
- A paper trail of broken data
  - You know exactly what happened

**Disk formatting**

- Low-level formatting
  - Provided at the factory
  - Not recommended for the user
- Standard formatting / quick format
  - Sets up the file system, installs a boot sector
  - Clears the master file table but not the data
  - Can be recovered with the right software
- Standard formatting / Regular format
  - Overwrites every sector with zeros
  - Windows Vista and later
  - Can’t recover the data

**Hard drive security**

- 2019 study from Blancco and Ontrack 159 storage drives from eBay
  - 66 drives had data, 25 drives with PII
  - Personal documents, video from a hospital monitoring system, and more
- File level overwriting
  - Sdelete - Windows Sysinternals
- Whole drive wipe secure data removal
  - DBAN - Darik’s Boot and Nuke
- Physical drive destruction
  - One-off or industrial removal and destroy

**Securing a SOHO Network 2.10**

**SSID management**

- Service Set Identifier
  - Name of the wireless network
  - LINKSYS, DEFAULT, NETGEAR
- Change the SSID to something not-so obvious
- Disable SSID broadcasting?
  - SSID is easily determined through wireless network analysis
  - Security through obscurity

**Wireless encryption**

- All wireless computers are radio transmitters and receivers
  - Anyone can listen in
- Solution: Encrypt the data
  - Everyone gets the password
- Only people with the password can transmit and listen 
  - WPA2 encryption

**Antenna placement**

- Access point usually in a central location for access
- In a business environment, multiple access points with different configurations for sectors

**Power level controls**

- Usually a wireless configuration
  - Set it as low as you can
- How low is low?
  - This might require some additional study
- Consider the receiver
  - High-gain antennas can hear a lot


**Using WPS**

- Wi-Fi Protected Setup
  - Originally called Wi-Fi Simple Config
- Allows “easy” setup of a mobile device
  - A passphrase can be complicated to a novice
- Different ways to connect
  - PIN configured on access point must be entered on the mobile device
  - Push a button on the access point
  - Near-field communication - Bring the mobile device close to the access point
  - USB method, no longer used

**The WPS hack**

- December 2011 - WPS has a design flaw
  - It was built wrong from the beginning
- PIN is an eight-digit number
  - Really seven digits and a checksum
  - Seven digits, 10,000,000 possible combinations
- The WPS process validates each half of the PIN
  - First half, 4 digits. Second half, 3 digits
  - First half, 10,000 possibilities. Second half, 1,000 possibilities
- It takes about four hours to go through all of them
  - Most devices now include a lockout function

**Default usernames and passwords**

- All access points have default usernames and passwords
  - Change yours
- The right credentials provide full control
  - Administrator access
- Very easy to find the defaults for you WAP or router
  - <http://www.routerpasswords.com>

**MAC address filtering**

- Media Access Control
  - The “hardware” address
- Limit access through the physical hardware address
  - Keeps the neighbors out
  - Additional administration with visitors
- Easy to find working MAC addresses through wireless LAN analysis
  - MAC addresses can be spoofed
  - Free open-source software
- Security through obscurity

**IP addressing**

- DHCP (automatic) IP addressing vs. manual IP addressing
- IP addresses are easy to see in an unencrypted network
- If the encryption is broken, the IP addresses will be obvious
- Configuring a static IP address is not a security technique
  - Security through obscurity

**SOHO firewalls**

- Small office / home office appliances
  - Generally has reduced throughput requirements
- Usually includes multiple functions
  - Wireless access point, router, firewall, content filter
- May not provide advanced capabilities
  - Dynamic routing
  - Remote support
- Install the latest software
  - Update and upgrade the firmware
  - Firewalls, routers, switches, etc.

**Firewall Settings**

- Inbound traffic
  - Extensive filtering and firewall rules
  - Allow only required traffic
  - Configure port forwarding to map TCP/UDP ports to a device
  - Consider building a DMZ
- Outbound traffic
  - Blacklist: Allow all, stop only unwanted traffic
  - Whitelist: Block all, only allow certain traffic types

**Disabling ports**

- Enabled physical ports
  - Conference rooms
  - Break rooms
- Administratively disable unused ports
  - More to maintain, but more secure
- Network Access Control (NAC)
  - 801.`X controls
  - You can’t communicate unless you are authenticated

**Content filtering**

- Control traffic based on data within the content
  - Data in the packets
- Corporate control of outbound and inbound data
  - Sensitive materials
- Control of inappropriate content
  - Not safe for work
  - Parental controls
- Protection against evil
  - Anti-virus, anti-malware

**Physical security**

- Physical access- A relatively easy hack
  - Highly secure data centers
- Door access
  - Lock and key, electronic keyless
- Biometric
  - Eyeballs and fingers
- The process
  - Documented
  - Well-established
