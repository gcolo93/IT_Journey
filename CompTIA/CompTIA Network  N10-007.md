**Introduction to IP 1.1**

**IP: Internet Protocol**

- Transfers TCP and UDP data

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
- TCP Data sent from sender, TCP ACK sent from receiver

**UDP - User Datagram Protocol**

- Connectionless
  - No formal open or close to the connection
- “Unreliable” delivery
  - No error recovery
  - No reordering of data or retransmissions
- No flow control
  - Sender determines the amount of data transmitted

**Speedy delivery**

- The IP delivery truck delivers from one (IP) address to another (IP) address
  - Every house has an address, every computer has an IP address
- Boxes arrive at the house / IP address
  - Where do the boxes go?
  - Each box has a room name
- Port is written on the outside of the box
  - Drop the box into the right room

**Port numbers**

- TCP and UDP ports can be any number between 0 and 65,535
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

**ICMP**

- Internet Control Message Protocol
  - “Text messaging” for your network devices
- Another protocol carried by IP
  - Not used for data transfer
- Devices can request and reply to administrative requests
- Devices can send messages when  things don’t go well
  - That network you’re trying to reach is not reachable from here
  - Your time-to-live expired, just letting you know

**Common Ports 1.1**

**Telnet**

- Telnet - Telecommunication Network
  - tcp/23
- Login to devices remotely
- Console access
- In-the-clear communication
- Not the best choice for production systems

**SSH - Secure Shell**

- Encrypted communication link - tcp/22
- Looks and acts the same as Telnet

**DNS - Domain Name System**

- Converts names to IP addresses - udp/53
- These are very critical resources
  - Usually multiple DNS servers are in production

**SMTP - Simple Mail Transfer Protocol**

- SMTP - Simple Mail Transfer Protocol
  - Server to server email transfer
  - tcp/25
- Also used to send mail from a device to a mail server
  - Commonly configured on mobile devices and email clients
- Other protocols are used for clients to receive email
  - IMAP, POP3

**SFTP - Secure FTP**

- Uses the SSH File Transfer Protocol
  - tcp/22
- Provides file system functionality
  - Resuming interrupted transfers, directory listings, remote file removal
- Encrypted communication
  - Using SSH

**File transfer application protocols**

- FTP - File Transfer Protocol
  - tcp/20 (active mode data), tcp/21 (control)
  - Transfers files between systems
  - Authenticates with a username and password
  - Full-featured functionality (list, add, delete, etc.)
- TFTP - Trivial File Transfer Protocol
  - udp/69
  - Very simple file transfer application
    - Read files and write files
  - No authentication
    - Not used on production systems

**DHCP - Dynamic Host Configuration Protocol**

- Automated configuration of IP address, subnet mask and other options
  - udp/67, udp/68
  - Requires a DHCP server
    - Server, appliance, integrated into a SOHO router, etc.
- Dynamic / pooled
  - IP addresses are assigned in real-time from a pool
  - Each system is given a lease and must renew at set intervals
- DHCP reservation
  - Addresses are assigned by MAC address in the DHCP server
  - Quickly manage addresses from one location

**HTTP and HTTPS**

- Hypertext Transfer Protocol
  - Communication in the browser
  - And by other applications
- In the clear or encrypted
  - HTTP - tcp/80 - Web server communication
  - HTTPS - tcp/443 - Web server communication with encryption

**SNMP - Simple Network Management Protocol**

- Gather statistics from network devices
  - udp-161
- v1 - The original
  - Structured tables
  - In-the-clear
- v2 - A good step ahead
  - Data type enhancements
  - Bulk transfers
  - Still in-the-clear
- v3 - A secure standard
  - Message integrity
  - Authentication
  - Encryption

**RDP - Remote Desktop Protocol**

- Share a desktop from a remote location over tcp/3389
- Remote Desktop Protocol
- Can connect to an entire desktop or just an application
- Clients for Windows, MacOS, Linux, Unix, iPhone, and others

**NTP - Network Time Protocol**

- Switches, routers, firewalls, servers, workstations
  - Every device has its own clock
  - udp/123
- Synchronizing the clocks becomes critical
  - Log files, authentication information, outage details
- Automatic updates
  - No flashing 12:00 lights
- Flexible - You control how clocks are updated
- Very accurate
  - Accuracy is better than 1 millisecond on a local network

**SIP - Session Initiation Protocol**

- Voice over IP (VoIP) signaling
  - tcp/5060 and tcp/5061
- Setup and manage VoIP sessions
  - Call, ring, hang up
- Extend voice communication
  - Video conferencing
  - Instant messaging
  - File transfer
  - etc.

**SMB - Server Message Block**

- Protocol used by Microsoft Windows
  - File sharing, printer sharing
  - Also called CIFS (Common Internet File System)
- Direct over tcp/445 (NetBIOS-less)
  - Direct SMB communication over TCP without the NetBIOS transport

**POP / IMAP**

- Receive emails from an email server
  - Authenticate and transfer
- POP3 - Post office Protocol Version 3
  - tcp/110
  - Basic mail transfer functionality
- IMAP4 - Internet Message Access Protocol v4
  - tcp/143
  - Includes management of email inbox from multiple clients

**LDAP / LDAPS**

- LDAP (Lightweight Directory Access Protocol)
  - tcp/389
  - Store and retrieve information in a network directory
- LDAPS (LDAP Secure)
  - A non-standard implementation of LDAP over SSL
  - tcp/636

**H.323**

- Voice over IP (VoIP) signaling
  - ITU Telecommunication H.32x protocol series
  - tcp/1720
- Setup and manage VoIP sessions
  - Call, ring, hang up
- One of the earliest VoIP standards
  - Still in use today

**Understanding the OSI Model 1.2**

**The OSI model**

- What is the OSI model?
  - Open Systems Interconnection Reference Model
- It’s a guide (thus the term “model”)
  - Don’t get wrapped up in the details
- This is not the OSI protocol suite
  - Most of the OSI protocols didn’t catch on
- There are unique protocols at every layer
- You’ll refer to this model for the rest of your career
- All people seem to need data processing

**Layer 1 - Physical Layer**

- The physics of the network
  - Signaling, cabling, connectors
  - This layer isn’t about protocols
- “You have a physical layer problem.”
  - Fix your cabling, punch-downs, etc.
  - Run loopback tests, test/replace cables, swap adapter cards

**Layer 2 - Data Link Layer**

- The basic network “language”
  - The foundation of communication at the data link layer
- Data Link Control (DLC) protocols
  - MAC (Media Access Control) address on Ethernet
- The “switching” layer

**Layer 3 - Network Layer**

- The “routing” layer
- Internet Protocol (IP)
- Fragments frames to traverse different networks

**What is IP fragmentation**

- Fragments are always in multiples of 8 because of the number of fragmentation offset bits in the IP header
- DLC Header > IP Header > TCP Header 20 bytes > TCP Data 24 bytes

**Layer 4 - Transport Layer**

- The “post office” layer
  - Parcels and letters
- TCP (Transmission Control Protocol) and UDP (User Datagram Protocol)

**Layer 5 - Session Layer**

- Communication management between devices
  - Start, stop, restart
- Control protocols, tunneling protocols

**Layer 6 - Presentation Layer**

- Character encoding
- Application encryption
- Often combined with the Application Layer

**Layer 7 - Application Layer**

- The layer we see
- HTTP, FTP, DNS, POP3

**Real-world to OSI model**

- Your eyes (Layer 7 Application)
- Application encryption (SSL/TLS)  (Layer 6 Presentation)
- Control protocols, tunneling protocols (Layer 5 Session)
- TCP segment, UDP datagram (Layer 4 Transport)
- IP Address, Router, Packet (Layer 3 Network)
- Frame, MAC address, Extended Unique Identifier (EUI-48, EUI-64), Switch (Layer 2 Data Link)
- Cables, fiber, and the signal itself (Layer 1 Physical)

**Follow the conversation**

- Application: <https://mail.google.com>
- Presentation: SSL encryption
- Session: Link the presentation to the transport
- Transport: TCP encapsulation
- Network: IP encapsulation
- Data Link: Ethernet
- Physical: Electrical signals

**Introduction to Ethernet 1.3**

**SOHO LAN**

- Internet > Router > Switch >Access point/Computer

**The Ethernet Frame**

- Preamble - 7 bytes - 56 alternating ones and zeros used for synchronization (101010…)
- SFD - 1 Byte - Start Frame Delimiter - designates the end of the preamble (10101011)
- Destination MAC Address - 6 Bytes - Ethernet MAC address of the destination device
- Source MAC address - 6 Bytes - Ethernet MAC address of the source device
- EtherType - 2 bytes - Describes the data contained the payload
- Payload - 46 - 1500 bytes - Layer 3 and higher data
- FCS - 4 bytes - Frame Check Sequence - CRC checksum of the frame

**The MAC address**

- Ethernet Media Access Control address
  - The “physical” address of a network adapter
  - Unique to a device
- 48 bits / 6 bytes long
  - Displayed in hexadecimal
- 8c:2d:aa:4b:98:a7
- 8c:2d:aa - Organizationally Unique Identifier (OUI) (the manufacturer)
- 4b:98:a7 - Network Interface Controller-Specific (the serial number)



**Duplex**

- Half-duplex
  - A device cannot send and receive simultaneously
  - All LAN hubs are half-duplex devices
  - Switch interfaces can be configured as half-duplex
    - But usually only when connecting to other half-duplex device
- Full-duplex
  - Data can be sent and received at the same time
  - A properly configured switch interface will be set to full-duplex

**Half-duplex Ethernet**

- Traffic received on one interface is repeated to all other interfaces
- If two devices communicate simultaneously, you have a collision

**CSMA/CD**

- CS - Carrier Sense
  - Is there a carrier?
  - Is there a signal available that we can use to send some data?
- MA - Multiple Access
  - More than one device on the network
- CD - Collision Detect
  - Collision - Two stations talking at once
  - Identify when data gets garbled
- Half-duplex Ethernet
  - Not used any longer
- Listen for an opening
  - Don’t transmit if the network is already busy
- Send a frame of data
  - You send data whenever you can
  - There’s no queue or prioritization
- If a collision occurs
  - Transmit a jam signal to let everyone know a collision has occurred
  - Wait a random amount of time
  - Retry the transmission

**Full-duplex Ethernet**

- Sam’s PC creates an Ethernet frame
  - Sam’s MAC address is the source
  - SGC Server MAC address is the destination
- Frame is sent to Switch A
- Switch B forwards the frame to the interfaces that matches the destination (SGC Server) MAC address
  - Destination PC receives the frame, identifies a matching destination MAC
  - Destination PC accepts the frame
- Full-duplex
  - Send and receive simultaneously

**CSMA/CA**

- CA - Collision Avoidance
  - Common on wireless networks
- Collision detection isn’t possible
  - A sending station can’t “hear” other stations
- Use RTS/CTS
  - I’m ready to send
  - You’re clear to send
- Solves the “hidden node” problem
  - Station A can hear the access point
  - Station B can hear the access point
  - Station A can’t hear station B

**Network Switching Overview 1.3**

**The switch**

- Forward or drop frames
  - Based on the destination MAC address
- Gather a constantly updating list of MAC addresses
  - Builds the list based on the source MAC address of incoming traffic
- Maintain a loop-free environment
  - Using Spanning Tree Protocol (STP)

**Learning the MACs**

- Switches examine incoming traffic
  - Makes a note of the source MAC address
- Adds unknown MAC addresses to the MAC address table
  - Sets the output interface to the received interface

**Flooding for unknown MACs**

- The switch doesn’t always have a MAC address in the table
- When in doubt, send the frame to everyone

**Address Resolution Protocol**

- Determine a MAC address based on an IP address
  - You need the hardware address to communicate
- arp -a
  - View local ARP table

**Broadcast Domains and Collision Domains 1.3**

**Collision domains**

- A historical footnote
  - It’s difficult to find a collision these days
  - The word “collision” is misleading
- The network was one big segment
  - Everyone heard everyone else’s signals
  - One big conference call
- Only one station can “talk” at a time
  - Is the line clear? Ok, I can talk.
    - Carrier Sense Multiple Access (CSMA)
- When two people spoke at the same time, there was a collision
  - Collision Detection (CD)
  - Send the jam signal

**Broadcast domains**

- Spread the word!
  - Everyone must know
    - ARP requests
    - Operating system notifications
    - Some dynamic routing protocols
- How far can a broadcast go?
  - Passed by a switch/bridge
  - Stops at the router
- This can be important
  - More devices, more broadcasts

**Unicasts, Broadcasts, and Multicasts 1.3**

**Unicast**

- One station sending information to another station
- Send information between two systems
- Web surfing, file transfers
- Does not scale optimally for real-time streaming media

**Broadcast**

- Send information to everyone at once
- One packet, received by everyone
- Limited scope
  - The broadcast domain
- Routing updates, ARP requests
- Not used in IPv6
  - Focus on multicast

**Multicast**

- Delivery of information to interested systems
  - One to many
- Multimedia delivery, stock exchanges
- Very specialized
  - Difficult to scale across large networks

**Protocol Data Units 1.3**

**PDU (Protocol Data Unit)**

- A unit of transmission
  - A different group of data at different OSI layers
- Ethernet operates on a frame of data
  - It has no idea what’s inside
- IP operates on a packet of data
  - Inside is TCP or UDP, but IP doesn’t know that
- TCP or UDP PDU
  - TCP segment
  - UDP datagram

**Maximum Transmission Unit (MTU)**

- Maximum IP packet to transmit
  - But not fragment
- Fragmentation slows things down
  - Losing a fragment loses an entire packet
  - Requires overhead along the path
- Difficult to know the MTU all the way through the path
  - Automated methods are often inaccurate
    - Especially when ICMP is filtered

**Troubleshooting MTU**

- MTU sizes are usually configured once
  - Based on the network infrastructure and don’t change often
- A significant concern for tunneled traffic
  - The tunnel may be smaller than your local Ethernet segment
- What if you send packets with the Don't Fragment (DF) set?
  - Routers will respond back and tell you to fragment
  - Hope you get the ICMP message
- Troubleshoot using ping
  - Ping with DF and force a maximum size of 1472 bytes 
  - 1500bytes - 8 byte ICMP header - 20 bytes IP address = 1472
    - Windows: ping -f -l 1472 8.8.8.8

**Network Segmentation 1.3**

**LANs**

- Local Area Networks
  - A group of devices in the same broadcast domain

**Virtual LAN’s**

- Virtual Local Area Networks
  - A group of devices in the same broadcast domain
  - Separated logically instead of physically



