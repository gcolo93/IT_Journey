**Introduction to IP 2.1**

**A series of moving vans**

- Efficiently move large amounts of data
  - Use a shipping truck
- The network topology is the road
  - Ethernet, DSL, cable system
- The truck is the Internet Protocol (IP)
  - We’ve designed the roads for this truck
- The boxes hold your data
  - Boxes of TCP and UDP
- Inside the boxes are more things
  - Application information

**IP - Internet Protocol**

- Client
- Ethernet Frame
  - Ethernet Header
  - Ethernet Payload
    - IP Header
    - IP Payload
      - TCP Header
      - TCP Payload
        - HTTP data
        - Application data
  - Ethernet Trailer
- Server

**TCP and UDP**

- Transported inside of IP
  - Encapsulated by the IP protocol
- Two ways to move data from place to place
  - Different features for different applications
- OSI Layer 4
  - The transport layer
- Multiplexing
  - Use many different applications at the same time
  - TCP and UDP

**TCP - Transmission Control Protocol**

- Connection-oriented
  - A formal connection setup and close
- “Reliable” delivery
  - Recovery from errors
  - Can manage out-of-order messages or retransmissions
- Flow control
  - The receiver can manage how much data is sent
    - TCP data > Receiver
    - TCP ACK (Acknowledgement) > Sender

**UDP - User Datagram Protocol**

- Connectionless
  - No formal open or close to the connection
- “Unreliable” delivery
  - No error recovery
  - No reordering of data or retransmissions
  - No flow control
    - Sender determines the amount of data transmitted
    - UDP data > Receiver
    - Receiver does not acknowledge sent data

**Speedy delivery**

- The IP delivery truck delivers from one (IP) address to another (IP) address
  - Every house has an address, every computer has an IP address
- Boxes arrive at the house/IP address
  - Where do the boxes go?
  - Each box has a room name
- Port is written on the outside of the box
  - Drop the box into the right room

**Lots of ports**

- IPv4 sockets
  - Server IP address, protocol, server application port number
  - Client IP address, protocol, client port number
- Non-ephemeral ports- permanent port numbers
  - Port numbers usually assigned to an application
  - Ports 0 through 1,023
  - Usually on a server or service
- Ephemeral ports - temporary port numbers
  - Ports 1024 through 65535
  - Determined in real-time by the client

**Port Numbers**

- TCP and UDP ports can be any number between 0 and 65535
- Most servers (services) use non-ephemeral (not-temporary) port numbers
  - This isn’t always the case
  - It’s just a number
- Port numbers are for communication, not security
- Service port numbers need to be “well known”
- TCP port numbers aren’t the same as UDP port numbers

**Ports on the network**

- Web server - tcp/80
- VoIP server - udp/5004
- Email server - tcp/143

**Common Network Ports 2.1**

**FTP - File Transfer Protocol**

- tcp/20 (active mode data)
- tcp/21 (control)
  - Transfers files between systems
- Authenticates with a username and password
  - Some systems use a generic/anonymous login
- Full-featured functionality
  - List, add, delete, etc.

**SSH - Secure Shell**

- Encrypted communication link - tcp/22
- Looks and acts the same as Telnet

**Telnet**

- Telnet - Telecommunication Network - tcp/23
- Login to devices remotely
- Console access
- In-the-clear communication
- Not the best choice for production systems

**SMTP - Simple Mail Transfer Protocol**

- SMTP - Simple Mail Transfer Protocol
  - Server to server email transfer
  - tcp/25
- Also used to send mail from a device to a mail server
  - Commonly configured on mobile devices and email
- Other protocols are used for clients to receive email
  - IMAP, POP3

**DNS - Domain Name System**

- Converts names to IP addresses - udp/53
  - [www.professormesser.com](http://www.professormesser.com) = 162.159.246.164
- These are very critical resources
  - Usually multiple DNS servers are in production

**HTTP and HTTPS**

- Hypertext Transfer Protocol (HTTP)
  - Communication in the browser
  - And by other applications
  - tcp/80
- Hypertext Transfer Protocol Secure (HTTPS)
  - Communication in the browser with encryption
  - tcp/443
- In the clear or encrypted
  - Support by nearly all web servers and clients

**POP/IMAP**

- Receive emails from an email server
  - Authenticate and transfer
- POP3 - Post office Protocol version 3
  - tcp/110
  - Basic mail transfer functionality
- IMAP4 - Internet Message Access Protocol v4
  - tcp/143
  - Includes management of email inbox from multiple clients

**RDP - Remote Desktop Protocol**

- Share a desktop from a remote location over tcp/3389
- Remote Desktop Services on many Windows versions
- Can connect to an entire desktop or just an application
- Clients for Windows, macOS, Linus, Unix, iPhone, Android, and others

**SMB - Server Message Block**

- Protocol used by Microsoft Windows
  - File sharing, printer sharing
  - Also called CIFS (Common Internet File System)
- Using NetBIOS over TCP/IP
  - udp/137 - NetBIOS name services (nbname)
  - udp/138 - NetBIOS datagram service (nbdatagram)
  - tcp/139 - NetBIOS session service (nbsession)
- Direct over tcp/445 (NetBIOS-less)
  - Direct SMB communication over TCP without the NetBIOS transport

**AFP (Apple Filing Protocol)**

- File services in macOS
  - tcp/548
- Works with SLP (Service Location Protocol)
  - tcp/427 and udp/427
  - Populates the list of available devices
- File management
  - Copy, move, delete files

**DHCP - Dynamic Host Configuration Protocol**

- Automated configuration of IP address, subnet mask, and other options
  - udp/67, udp/68
  - Requires a DHCP server
    - Server, appliance, integrated into a SOHO router, etc.
- Dynamic/pooled
  - IP addresses are assigned in real-time from a pool
  - Each system is given a lease and must renew at set intervals
- DHCP reservation
  - Addresses are assigned by MAC address in the DHCP server
  - Quickly manage addresses from one location

**LDAP**

- LDAP (Lightweight Directory Access Protocol)
  - tcp/389
- Store and retrieve information in a network directory
  - Commonly used in Microsoft Active Directory

**SNMP - Simple Network Management Protocol**

- Gather statistics from network devices
  - Queries: udp/161
  - Traps: udp/162
- v1-The original
  - Structured tables
  - In-the-clear
- v2-A good step ahead
  - Data type enhancements
  - Bulk transfers
  - Still in-the-clear
- v3-A secure standard
  - Message integrity
  - Authentication
  - Encryption

**Network Devices 2.2**

**Network Interface Card (NIC)**

- The fundamental network device
  - Every device on the network has a NIC
  - Computers, servers, printers, routers, switches, phones, tablets, cameras, etc.
- Specific to the network type
  - Ethernet, WAN, wireless, etc.
- Often built-in to the motherboard
  - Or added as an expansion card
- Many options
  - Single port, multi-port, copper, fiber

**Repeater**

- Receive signal, regenerate, resend
  - No forwarding decisions to make
- Common use
  - Boost copper or fiber connections
  - Convert one network media to another
  - Extend wireless network reach

**Hub**

- “Multi-port repeater”
  - Traffic going in one port is repeated to every other port
- Everything is half-duplex
  - Devices cannot communicate at the same time
- Becomes less efficient as network speeds increase
- 10 megabit / 100 megabit
- Difficult to find today

**Bridge**

- Imagine a switch with two to four ports
  - Fakes forwarding decisions in software
- Connects different physical networks
  - Can connect different topologies
  - Gets around physical network size limitations/collisions
- Distributes traffic based on MAC address
- An example of a modern bridge is a wireless access point
  - Bridges wired Ethernet to wireless

**Switches**

- Bridging done in hardware
  - Application-specific integrated circuit (ASIC)
  - Forwards traffic based on data link address
- Many ports and features
  - The core of an enterprise network
  - May provide Power over Ethernet (PoE)
- Multilayer switch
  - Includes routing functionality

**Unmanaged switches**

- Very few configuration options
  - Plug and play
- Fixed configuration
  - No VLANs
- Very little integration with other devices
  - No management protocols
- Low price point
  - Simple is less expensive

**Managed Switches**

- VLAN support
  - Interconnect with other switches via 802.1Q
- Traffic prioritization
  - Voice traffic gets a higher priority
- Redundancy support
  - Spanning Tree Protocol (STP)
- External management
  - Simple Network Management Protocol (SNMP)
- Port mirroring
  - Capture packets

**Routers**

- Routes traffic between IP subnets
  - Makes forwarding decisions based on IP address
  - Routers inside of switches sometimes called “layer 3 switches”
- Often connects diverse network types
  - LAN, WAN, copper, fiber

**Wireless access point (WAP)**

- Not a wireless router
  - A wireless router is a router and a WAP in a single device
- WAP is a bridge
  - Extends the wired network onto the wireless network
  - Makes forwarding decisions based on MAC address

**Wireless LAN controllers**

- Centralized management of WAPs
  - A single “pane of glass”
- Management functions
  - Deploy new access points
  - Performance and security monitoring
  - Configure and deploy changes to all sites
  - Report on access point use
- Usually a proprietary system
  - The wireless controller is paired with the access points
- Can also be cloud-based
  - Mange the console from anywhere

**Firewalls**

- Filters traffic by port number
  - OSI layer 4 (TCP/UDP)
    - Some firewalls can filter based on the application
- Can encrypt traffic into/out of the network
  - Protect your traffic between sites
- Can proxy traffic
  - A common security technique
- Most firewalls can be layer 3 devices (routers)
  - Usually sits on the ingress/egress of the network

**Cable modem**

- Broadband
  - Transmission across multiple frequencies
  - Different traffic types
- Data on the “cable” network
  - DOCSIS (Data Over Cable Service Interface Specification)
- High-speed networking
  - 4 Mbits/s through 250 Mbits/s are common
  - Gigabit speeds are possible
- Multiple services
  - Data, voice, video

**DSL modem**

- ADSL (Asymmetric Digital Subscriber Line)
  - Uses telephone lines
- Download speed is faster than the upload speed (asymmetric)
  - 10,000 foot limitation from the central office (CO)
  - 52 Mbit/s downstream / 16 Mbit/s upstream are common
  - Faster speeds may be possible if closer to the CO

**Patch panels**

- ` `Combination of punch-down blocks and RJ-45 connectors
- Runs from desks are made once
  - Permanently punched down to patch panel
- Patch panel to switch can be easily changed
  - No special tools
  - Use existing cables

**Power over Ethernet**

- Power provided on an Ethernet cable
  - One wire for both network and electricity
  - Phones, cameras, wireless access points
  - Useful in difficult-to-power areas
- Power provided at the switch
  - Built-in power - Endspans
  - In-line power injector - Midspans

**PoE switch**

- Commonly marked on the switch or interfaces

**Ethernet over Power (EOP)**

- Also called Power-line communication (PlC)
  - IEEE standard 1901
- 500 megabits per second
  - Standard includes links to the premise, intra-building networking, vehicles, smart energy devices, and more

**Installing a SOHO Network 2.3**

**The SOHO router (Small Office Home Office)**

- An all-in-one device
  - Modem, router, switch, wireless AP, firewall, etc.

**Routing and switching**

- Routing to the outside world
  - WAN/DSL port
- Switching local devices
  - One VLAN / LAN1, LAN2, LAN3, LAN4, etc.
- Not much to configure
  - Routes and switches by default

**Access point settings**

- Enable/disable frequencies
  - 2.4 GHz and/or 5 GHz
  - Available options will depend on the wireless standard used
- Configure an SSID
  - May need a separate SSID for each frequence
- Security mode
  - WPA2, preferably
  - Pre-shared key or Enterprise
- Channel / channel bandwidth
  - Automatic / other nearby networks

**IP addressing**

- WAN interface
  - Automatically assigned via DHCP from the ISP
  - May require authentication
- LAN interface
  - Internal IP address and subnet mask of the router
  - DHCP address range for other devices
  - DNS server addresses

**NIC configuration**

- Wired
  - May not have many options
  - Ports configured for auto speed and duplex
  - Speed: 10/100/1000 mbp/s
  - Duplex: Half/Full
- Wireless
  - Enable/disable
  - SSID
  - Password

**End-user device configuration**

- Automatic
  - Auto speed and duplex
  - DHCP addressing
- End-user device configures, based on router
  - IP address
  - Subnet mask
  - Default gateway
  - DNS servers

**IoT configurations**

- Internet of Things 
  - Home automation, mostly wireless
  - Security is an issue
- Devices 
  - Thermostat
  - Light switches
  - Security cameras
  - Door locks
  - Voice-enabled smart speakers / digital assistants
- Almost all devices communicate outbound
  - No special port-mapping/NAT configurations required

**Configuring a SOHO Firewall 2.3**

**Firewall and DMZ ports**

- Every SOHO router is also a firewall
  - No external device can directly access the internal network
  - This normally can’t be disabled
- DMZ (Demilitarized Zone) ports can be configured to allow unrestricted access
  - This is almost always a bad idea
  - Consider creating more specific port forwarding rules
  - Or perhaps don’t allow any access

**NAT (Network Address Translation)**

- It is estimated that there are over 20 billion devices connected to the Internet (and growing)
  - IPv4 supports around 4.29 billion addresses
- The address space for IPv4 is exhausted
  - There are no available addresses to assign
- How does it all work?
  - Network Address Translation
- This isn’t the only use of NAT
  - NAT is handy in many situations

**Configuring NAT**

- For SOHO devices, this is automatic
  - Source NAT, also called PAT (Port Address Translation)
  - All internal devices are translated to a single external address

**Port forwarding**

- 24x7 access to a service hosted internally
  - Web server, gaming server, security system, etc.
- External IP/port number maps to an internal IP/port
  - Does not have to be the same port number
- Also called Destination NAT or Static NAT
  - Destination address is translated from a public IP to a private IP
  - Does not expire or timeout


**UPnP (Universal Plug and Play)**

- Allows network devices to automatically configure and find other network devices
  - Zero configuration
- Applications on the internal network can open inbound ports using UPnP
  - No approval needed
  - Used for many peer-to-peer (P2P) applications
- Best practice would be to disable UPnP
  - Only enable if the application requires it
  - And maybe not even then

**Whitelist/blacklist**

- Content filtering, IP address ranges
  - Or a combination
- Whitelisting
  - Nothing pass through the firewall unless approved
  - Very restrictive
- Blacklisting
  - Nothing on the “bad list” is allowed
  - Specific URLs
  - Domains
  - IP addresses

**MAC Filtering**

- Media Access Control
  - The “hardware” address
- Limit access through the physical hardware address
  - Keeps the neighbors out
  - Additional administration with visitors
- Easy to find working MAC addresses through wireless LAN analysis
  - MAC addresses can be spoofed
  - Free open-source software
- Security through obscurity

**Wireless channels and encryption**

- Configure for the highest encryption possible
  - WPA2-AES
  - Choose WPA2 over WPA
  - WEP is not an appropriate option
    - Wired Equivalent Privacy
- Check your devices
  - Not all of them may allow for the highest encryption
- Use an open frequency
  - Some access points will automatically find good frequencies

**Managing QoS (Quality of Service)**

- Change the priority of your traffic
  - Voice is high, World of Warcraft is low
  - Or vice-versa
- Prioritize applications, ports, or MAC addresses
  - A feature of high-end SOHO routers

**802.11 Wireless Standards 2.4**

- Wireless Networking (802.11)
  - Managed by the IEEE LAN/MAN
  - Standards Committee (IEEE 802)
- Many updates over time
  - Check with IEEE for the latest
- The Wi-Fi trademark
  - Wi-Fi Alliance handles interoperability testing

**802.11a**

- One of the original 802.11 standards
  - October 1999
- Operates in a 5 GHz range
  - Or other frequencies with special licensing
- 54 megabits per second (Mbit/s)
- Smaller range than 802.11b
  - Higher frequency is absorbed by objects in the way
  - Many rules-of-thumb calculate 1/3rd the range of 802.11b or 802.11g
- Not commonly seen today

**802.11b**

- Also an original 802.11 standard
  - October 1999
- Operates in the 2.4 GHz range
- 11 megabits per second (Mbit/s)
- Better range than 802.11a
  - Less absorption problems
- More frequency conflict
  - Baby monitors, cordless phones, microwave ovens, Bluetooth

**802.11g**

- An “upgrade” to 802.11b
  - June 2003
- Operates in the 2.4 GHz range
- 54 megabits per second (Mbit/s)
  - Same as 802.11a (but a little less throughput)
- Backwards-compatible with 802.11b
- Same frequency conflicts as 802.11b

**802.11n**

- The update to 802.11a, 802.11b, and 802.11g
  - October 2009
- Operates at 5 GHz and/or 2.4GHz
  - 40 MHz channel widths
- 600 megabits per second (Mbit/s)
  - 40 MHz mode and 4 antennas
- 802.11n uses MIMO
  - Multiple-input Multiple-output
  - Multiple transmit and receive antennas

**802.11ac**

- Approved in January 2014
  - Significant improvements over 802.11n
- Operates in the 5 GHz band
  - Less crowded, more frequencies (up to 160 MHz channel bandwidth)
- Increased channel bonding
  - Larger bandwidth usage
- Denser signaling modulation
  - Faster data transfers
- Eight MU-MIMO streams
  - Twice as many streams as 802.11n
  - Nearly 7 gigabits per second

**Wireless Network Technologies 2.4**

**802.11 Network Technologies**

- Frequencies
  - 2.4 GHz or 5 GHz
  - Sometimes both
- Channels
  - Groups of frequencies, numbered by the IEEE
  - Non-overlapping channels would be necessary
- Bandwidth
  - Amount of frequency in use
  - 20 MHz, 40MHz, 80MHz, 160MHz

**802.11 channel bandwidths**

- 802.11a - 20MHz
- 802.11b - 22MHz
- 802.11g - 20MHz
- 802.11n
  - 20MHz or 40MHz (two contiguous 20MHz bonded channels)
  - In a 2.4GHz, a 40MHz channel uses much of the available bandwidth
- 802.11ac
  - 40MHz for 802.11n stations
  - 80MHz required for 802.11ac stations
  - 160MHz optional (contiguous channels or non-contiguous bonded)

**Bluetooth**

- High speed communication over short distances
  - PAN (Personal Area Network)
- Connects our mobile devices 
  - Smartphones
  - Tethering and file transfers
  - Headsets and headphones
  - Health monitors
  - Automobiles and phone integration
  - Smartwatches
  - External speakers

**RFID (Radio-frequency identification)**

- It’s everywhere
  - Access badges
  - Inventory/Assembly line tracking
  - Pet/Animal identification
  - Anything that needs to be tracked
- Radar technology
  - Radio energy transmitted to the tag
  - RF power the tag, ID is transmitted back
  - Bidirectional communication
  - Some tag formats can be active/powered

**Near field communication (NFC)**

- Two-way wireless communication
  - Builds on RFID, which is mostly one-way
- Payment systems
  - Major credit cards
  - Online wallets
- Bootstrap for other wireless
  - NFC helps Bluetooth pairing
- Access token, identity “card”
  - Short range with encryption support

**Zigbee**

- Internet of Things networking
  - Open standard - IEEE 802.15.4 PAN
- Alternative to WiFi and Bluetooth
  - Longer distances than Bluetooth
  - Less power consumption than WiFi
- Mesh network of all Zigbee devices in your home
  - Light switch communicates to light bulbs
  - Tell Amazon Echo to lock the door
- Uses the ISM band
  - Industrial, Scientific, and Medical
  - 900MHz and 2.4 GHz frequencies in the U.S.

**Z-wave**

- Proprietary home automation networking
  - Internet of Things (IoT)
  - Control lights, locks, garage doors, etc.
- Wireless mesh networking
  - Nodes can hop through other nodes on the way to the destination
- Uses the ISM band
  - Industrical, Scientific, and Medical
  - 900MHz frequencies in the U.S.
  - No conflicts with 802.11

**Cellular Network Technologies**

**Cellular Networks**

- Mobile devices
  - “Cell” phones
- Separate land into “cells”
  - Antenna coverages a cell with certain frequencies
- 2G networks
  - GSM - Global System for Mobile Communications
  - CDMA - Code Division Multiple Access
- Poor data support
  - Originally used circuit-switching
  - Minor upgrades for some packet switching

**3G Technology**

- 3rd Generation
  - Introduced in 1998
- Upgraded data connectivity over 2G
  - Incremental 3G updates improved speeds
  - Usually several megabits per second
- Bandwidth improvement allowed new functionality
  - GPS
  - Mobile television
  - Video on demand
  - Video conferencing

**4G and LTE**

- Long Term Evolution (LTE)
  - A “4G” Technology
  - Converged standard (GSM and CDMA providers)
  - Based on GSM and EDGE (Enhanced Data Rates for GSM Evolution)
  - Standard supports download rates of 150 Mbit/s
- LTE Advanced (LTE-A)
  - Standard supports download rates of 300 Mbit/s

**Moving to 5G**

- Update to 4G
  - Rollout in late 2018 and 2019
  - Worldwide launches in 2020
- Significant performance improvements
  - At higher frequencies
  - May not be as significant at lower frequencies
- Technology updates
  - Additional frequencies
  - Improved data transmission methods

**Network Services 2.5**

**Web Server**

- Respond to browser requests
  - Using standard web browsing protocols
  - HTML, HTML5
- Web pages are stored on the server
  - Downloaded to the browser
  - Static pages or built dynamically in real-time

**File server**

- Centralized storage documents, spreadsheets, videos, pictures, and any other files
- Standard system of file management
  - SMB (Server Message Block), Apple Filing Protocol (AFP), etc.
- The front-end hides the protocol
  - Copy, delete, rename, etc.

**Print server**

- Connect a printer to the network
  - Provide printing services for all network devices
- May be software in a computer
  - Computer is connected to the printer
- May be built-in to the printer
  - Network adapter and software
- Uses standard printing protocols
  - SMB (Server Message Block)
  - IPP (Internet Printing Protocol)
  - LPD (Line Printer Daemon)

**DHCP server**

- Dynamic Host Configuration Protocol
  - Automatic IP address configuration
- Very common service
  - Available on most home routers
- Enterprise DHCP will be redundant
  - Usually running on central servers

**DNS server**

- Domain Name System
  - Convert names to IP addresses
  - And vice versa
- Distributed naming system
  - The load is balanced across many different servers
- Usually managed by the ISP or enterprise IT department
  - A critical resource

**Proxy server**

- An intermediate server
  - Client makes the request to the proxy
  - The proxy performs the actual request
  - The proxy provides results back to the client
- Useful features
  - Access control, caching, URL filtering, content scanning

**Main server**

- Store your incoming mail
  - Send your outgoing mail
- Usually managed by the ISP or the enterprise IT department
  - A complex set of requirements
- Usually one of the most important services
- 24/7 support


**Authentication server**

- Login authentication to resources
  - Centralized management
- Almost always an enterprise service
  - Not required on a home network
- Usually a set of redundant servers
  - Always available
  - Extremely important service

**SIEM**

- Security Information and Event Management
  - Logging of security events and information
- Security alerts
  - Real-time information
- Log aggregation and long-term storage
  - Usually includes advanced reporting features
- Data correlation
  - Link diverse data types
- Forensic analysis
  - Gather details after an event

**Syslog**

- Standard for message logging
  - Diverse systems, consolidated log
- Usually a central logging receiver
  - Integrated into the SIEM
- You’re going to need a lot of disk space
  - No, more. More than that.
- WORM drive technology
  - Write Once Read Many - DVD-R
  - Protect important security logs

**IDS and IPS**

- Network-based Intrusion Detection System / Intrusion Prevention System
- Intrusion
  - Exploits against operating systems, applications, etc.
  - Buffer overflows, cross-site scripting, other vulnerabilities
- Detection vs. Prevention
  - Detection - Alarm or alert
  - Prevention - Stop it before it gets into the network




**All-in-one security appliance**

- Next-generation firewall, Unified Threat Management (UTM) / Web security gateway
- URL filter / Content inspection
- Malware inspection
- Spam filter
- CSU/DSU
- Router, Switch
- Firewall
- IDS/IPS
- Bandwidth shaper

**Endpoint management server**

- Manage all devices from one pane of glass
  - Software installations
  - Driver installations
  - Software updates
  - Security patches
  - Remote troubleshooting
- Requires an agent on the device
  - Server sends the commands
  - Agent executes the commands

**Legacy and embedded systems**

- Legacy systems
  - Another expression for “really old”
  - May also be “really important”
  - Learning old things can be just as important as learning new things
- Embedded systems
  - Purpose-built device
  - Not usual to have direct access to the operating system
  - Alarm system, door security, timecard system

**An Overview of IPv4 and IPv6 2.6**

**IP addressing**

- IPv4 is the primary protocol for everything we do
  - You probably won’t configure anything else
- IPv6 is slowly appearing

**IPv4 addresses**

- Internet Protocol version 4
  - OSI Layer 3 address
  - i.e. 192.16.1.11
  - Each section is 8 bits long
  - 11000000.10101000.00000001.10000011
  - 8 bits = 1 byte = 1 octet
- Since one byte is 8 bits, the maximum decimal value for each byte is 255

**IPv6 addresses**

- Internet Protocol v6 - 128-bit address
  - 340 undecillion addresses
- Your DNS will become very important!
- First 64 bits is generally the network prefix (/64)
- Last 64 bits is then the host network address

**Networking with IPv4**

- IP Address, e.g., 192.168.1.165
  - Every device needs a unique IP address
- Subnet mask, e.g. 255.255.255.0
  - Used by the local device to determine what subnet it’s on
    - The subnet mask isn’t (usually) transmitted across the network
    - You’ll ask for the subnet mask all the time
      - What’s the subnet mask of this network?
- Default gateway, e.g., 192.168.1.1
  - The router that allows you to communicate outside of your local subnet
  - The default gateway must be an IP address on the local subnet

**DNS servers**

- We remember names
  - Professormesser.com, google.com, youtube.com
- Internet routers don’t know names
  - Routers only know IP addresses
- Something has to translate between names and IP addresses
  - Domain Name Services
- You configure TWO DNS servers in your IP configuration
  - That’s how important it is


**Assigning IP Addresses 2.6**

**DHCP**

- IPv4 address configuration used to be manual
  - IP address, subnet mask, gateway, DNS servers, NTP servers, etc.
- October 1993 - The bootstrap protocol
  - BOOTP
- BOOTP didn’t automatically define everything
  - Some manual configurations were still required
  - BOOTP also didn’t know when an IP address might be available again
- Dynamic Host Configuration Protocol (DHCP)
  - Initially released in 1997, updated through the years
  - Provides automatic address / IP configuration for almost all devices

**Step 1: Discover**

**Step 2: Offer**

**Step 3: Request**

**Step 4: Acknowledge**

**Turning dynamic into static**

- DHCP assigns an IP address from the first available from a large pool of addresses
  - Your IP address will occasionally change
- You may not want your IP address to change
  - Server, printer, oor personal preference
- Disable DHCP on the device
  - Configure the IP address information manually
  - Requires additional administration
- Configure an IP reservation on the DHCP server
  - Associate a specific MAC address with an IP address

**Automatic Private IP Addressing (APIPA)**

- A link-local address
  - No forwarding by routers
- IETF has reserved 169.254.0.1 through 169.254.255.254
  - First and last 256 addresses are reserved
  - Functional block of 169.254.1.0 through 169.254.254.255
- Automatically assigned
  - Uses ARP too confirm the address isn’t currently in use

**IPv6 link-local addresses**

- A non-routable local network address
  - Will only work on the local subnet
- Required on every IPv6-enabled interface
  - You may see many IPv6 addresses per interface
- fe80::/10 with only one subnet allocated (all zeros)
  - Effectively becomes fe80::/64
- The last 64 bits are usually created with a modified EUI-64
  - Based on the MAC address





**Using IP Addresses 2.6**

**SSL VPN (Secure Sockets Layer VPN)**

- Uses common SSL/TLS protocol (tcp/443)
  - Avoids running into most firewall issues
- No big VPN clients
  - Usually remote access communication
- Authenticate users
  - No requirement for digital certificates or shared passwords (like IPSec)
- Can be run from a browser or from a (usually light) VPN client
  - Across many operating systems

**Client-to-Site VPNs**

- Also called “remote access VPN”
- Requires software on the user device
  - May be built-in to existing operating system

**LAN’s**

- Local Area Networks
  - A group of devices in the same broadcast domain

**Virtual LAN’s**

- Virtual Local Area Networks
  - A group of devices in the same broadcast domain
  - Separated logically instead of physically

**NAT (Network Address Translation)**

- It is estimated that there are over 20 billion devices connected to the Internet (and growing)
  - IPv4 supports around 4.29 billion addresses
- The address space for IPv4 is exhausted
  - There are no available addresses to assign
- How does it all work?
  - Network Address Translation
- This isn’t the only use of NAT
  - NAT is handy in many situations
- Translates one IP address to another
- Happens for all devices on the internal network






**Internet Connection Types 2.7**

` `**Cable modem**

- Broadband
  - Transmission across multiple frequencies
  - Different traffic types
- Data on the “cable” network
  - DOCSIS (Data Over Cable Service Interface Specification)
- High-speed networking
  - 4 MBits/s through 250 Mbits/s are common
  - Gigabit speeds are possible

**DSL modem**

- ADSL (Asymmetric Digital Subscriber Line)
  - Uses existing telephone lines
- Download speed is faster than the upload speed (asymmetric)
  - 10,000 foot limitation from the central office (CO)
  - 52 Mbit/s downstream / 16 Mbit/s upstream are common
  - Faster speeds may be possible if closer to the CO

**Dialup**

- Network with voice telephone lines
  - Analog lines with limited frequency response
- 56 kbit/s modems
  - Compression up to 320 kbit/s
- Relatively slow throughput
  - Difficult to scale
- Legacy systems, network utility
  - May be difficult to find a modem

**Fiber**

- Fiber optics to the home
  - High speed networking
- Converged services
  - Voice, Video, Data
- Enhanced features
  - Hundreds of HD channels
  - 1 Gbit/sec Internet access
  - 1 Terabyte of cloud storage
  - 2 Terabyte DVR





**Satellite networking**

- Communication to a satellite
  - Non-terrestrial communication
- High cost relative to terrestrial networking
  - 50 Mbit/s down, 3 Mbit/s up are common
  - Remote sites, difficult-to-network sites
- High latency
  - 250 ms up, 250 ms down
- High frequencies - 2 GHz
  - Line of sigh, rain fade

**ISDN**

- Integrated Services Digital Network
- BRI - Basic Rate Interface (2B+D)
  - Two 64 kbit/s bearer (B) channels
  - One 16 kbit/s signaling (D) channel
- PRI - Primary Rate Interface
  - Delivered over a T1 or E1
    - T1 - 23B + D
    - E1 - 30B + D + alarm channel
  - Commonly used as connectivity from the PSTN (Public Switched Telephone Network) to large phone systems (PBX/Private Branch Exchange)

**Cellular networks**

- Mobile devices
  - “Cell” phones
- Separate land into “cells”
  - Antenna coverages a cell with certain frequencies
- Tethering
  - Turn your phone into a wireless router
- Mobile hotspot
  - Standalone devices
  - Use your phone for other things

**Line-of-sight services**

- Line-of-sight
  - Visual path between antennas
  - High frequencies
- Common in metropolitan areas
  - Cover many homes simultaneously
- Also options for non-line-of-sight
  - Lower frequencies
- WiMAX networking
  - Worldwide Interoperability for Microwave Access
  - Wireless high-speed Internet access

**Network Types 2.7**

**LAN**

- Local Area Network
  - Local is relative
- A building or group of buildings
  - High-speed connectivity
- Ethernet and 802.11 wireless
  - Any slower and it isn’t “local”

**WAN**

- Wide Area Network
  - Spanning the globe
- Generally connects LANs across a distance
  - And generally much slower than the LAN
- Many different WAN technologies
  - Point-to-point serial, MPLS, etc.
  - Terrestrial and non-terrestrial

**PAN**

- Personal Area Network
  - Your own private network
  - Bluetooth, IR, NFC
- Automobile
  - Audio output
  - Integrate with phone
- Mobile phone
  - Wireless headset
- Health
  - Workout telemetry, daily reports

**MAN**

- Metropolitan Area Network
  - A network in your city
  - Larger than a LAN, often smaller than a WAN
- Historically MAN-specific topologies
  - Everyone’s moving to Metro Ethernet
- Common to see government ownership
  - They “own” the right-of-way


**WMN**

- Wireless mesh network
  - All devices connect together
  - A mesh “cloud”
- Self form
  - Connects to each other automatically
- Self heal
  - Reacts automatically to changes
- Many different network technologies
  - 802.11, Zigbee, Z-Wave, etc.

**Network Tools 2.8**

**Cable crimpers**

- “Pinch” the connector onto a wire
  - Coaxial, twisted pair, fiber
- Connect the modular connector to the Ethernet cable
  - The final step of the process
- Metal prongs are pushed through the insulation
  - The plug is also permanently pressed onto the cable sheath

**Modular connectors**

**Crimping best-practices**

- Get a good crimper
  - And a good pair of electrician’s scissors / cable snips
  - And a good wire stripper
- Make sure you use the correct modular connectors
  - Differences between wire types
- Practice, practice, practice
  - It won’t take long to become proficient

**Multimeters**

- AC voltage
  - Check wall outlet voltage
- DC voltage
  - PC power supply output voltages
  - CMOS battery power
- Continuity
  - Cabe connectivity
  - Fuse status
  - Wire mapping


**Tone generator**

- Where does that wire go?
  - Follow the tone
- Tone generator
  - Puts an analog sound on the wire
- Inductive probe
  - Doesn’t need to touch the copper
  - Hear through a small speaker

**Using the tone generator and probe**

- Easy wire tracing
  - Even in complex environments
- Connect the tone generator to the wire
  - Modular jack
  - Coax
  - Punch down connectors
- Use the probe to locate the sound
  - The two-tone sound is easy to find

**Cable testers**

- Relatively simple
  - Continuity test
- Can identify missing pins
  - Or crossed wires
- Not usually used for frequency testing
  - Crosstalk, signal loss, etc.

**Loopback plugs**

- Useful for testing physical ports
  - Or fooling your applications
- Serial / RS-232 (9 pin or 25 pin)
- Network connections
  - Ethernet, T1, Fiber
- These are not cross-over cables


**Punch-down tools**

- “Punch” a wire into a wiring block
  - 66 block
  - 110 block
- Can be tedious
  - Every wire must be individually punched
- Trims the wires during the punch
  - Very efficient process

**Punch-down best-practices**

- Organization is key
  - Lots of wires
  - Cable management
- Maintain your twists
  - Your Category 6A cable will thank you later
- Document everything
  - Written documentation
  - Tags
  - Graffiti

**WiFi analyzer**

- Wireless networks are incredibly easy to monitor
  - Everyone “hears” everything
- Purpose-built hardware or mobile device add-on
  - Specializes in 802.11 analysis
- Identify errors and interference
  - Validate antenna location and installation
