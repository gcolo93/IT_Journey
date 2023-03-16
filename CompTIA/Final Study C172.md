**TCP/IP and OSI Models**

The **TCP/IP and OSI models** describe a set of procedures that sends data from one host to another.

**TCP/IP** - Transmission Control Protocol and Internet Protocol - 4 Layer Model: Application > Transport > Network > Network Interface

**OSI** - Open Systems Interconnection - 7 Layer Model: Application > Presentation > Session > Transport > Network > Data Link > Physical

**TCP/IP**

- **Application Layer:** This layer is responsible for the communication protocols between nodes. The protocols in this layer include hypertext transfer protocol (HTTP and HTTPS), Secure Shell (SSH), and network time protocol (NTP), among many others.
- **Transport Layer:** This layer is responsible for the end-to-end transport of data. The protocols that live in this layer are transmission protocol (TCP) and user datagram protocol (UDP).
- **Network Layer:** This layer defines the logical transmission protocols for the whole network. The main protocols that live in this layer are internet protocol (IP), internet control message protocol (ICMP), and address resolution protocol (ARP).
- **Network Interface Layer:** This layer establishes how data should be physically sent through the network.

**OSI Model**

- **Physical Layer:** This layer is responsible for the physical connections of the devices in the network. This layer is implemented through the use of devices such as hubs, repeaters, modem devices, and physical cabling.
- **Data Link Layer:** This layer is responsible for the error-free delivery of data to the receiving device or node. This layer is implemented through the use of devices such as switches and bridge devices, as well as anything with a network interface, like wireless or wired network cards.
- **Network Layer:** This layer is responsible for the transmission of data between hosts in different networks as well as routing of data packets. This layer is implemented through the use of devices such as routers and some switches.
- **Transport Layer:** This layer provides services to the application layer and receives services from the network layer. It is responsible for the reliable delivery of data. It segments and reassembles data in the correct order for it to be sent to the receiving device. It may also handle the reliable delivery of data and any retries of data that are lost or corrupted (for example, TCP does this). This layer is often called the heart of OSI.
- **Session Layer:** This layer is responsible for connection establishment, session maintenance, and authentication.
- **Presentation Layer:** This layer is responsible for translating data from the application layer into the format required to transmit the data over the network as well as encrypting the data for security if encryption is used.
- **Application Layer:** This layer is responsible for network applications (like HTTP or FTP) and their production of data to be transferred over the network.





**Network Media and Devices**

A **switch** is a data link layer device. It is available either as a standalone or integrated with other devices, such as wireless routers or modems that can plug in physical devices. A switch keeps the traffic between the source and destination ports from interfering with other devices in the network. (Data Link and Network Layer Device)

A **router** operates at the network layer and can connect your home network to the Internet. In a business scenario, a router can connect your web server to your database server. (Network Layer Device)

**Firewalls** can operate at multiple layers of the OSI model, including data link, network, transport, session, and application - and in certain circumstances, presentation as well.

At the data link and network levels the firewall defines what traffic should go between two networks.

At the transport layer, the firewall filter settings are port-based. You can also filter traffic using a range of ports or a combination of IP addresses and ports.

The firewall that operates at the network and transport layers is called the **Layer 4 firewall**, and the one that works at the sesion, presentation, and application layers is the **Layer 7 firewall**.

The Layer 7 firewall is also smart enough to decrypt and analyze the content flowing through, thereby adding one more level of filtering to the IP address and port combination.

Firewalls can be software devices that run inside a virtual machine or physical server or can also be hardware devices like Fortinet’s Fortigate device.

A **modem** is a device necessary for sending and receiving data. Modems allow computers to transport digital information over analog lines, such as phone or cable lines. Types of modems include cable modems, DSL modems, and satellite modems. (Physical and Data Link Layer Device)

A **router** is a point of connection between two or more networks that forwards data packets between the networks. To have internet in your home, you need an internet router that connects the networks on the internet to the network of your home. You can access the internet’s network either through a wired Ethernet port, or via Wi-Fi.

A **switch** is used to connect devices in a specific network and allows them to communicate efficiently within the network. A switch is a more complex version of a hub, in that switches have the capability to add security measures and function far more intelligently, sending traffic directly from the sender to the receiver without the other devices being aware of the communication. Thus, a switch is less chatty and allows for more simultaneous conversations between devices. Most internet routers include a switch in the form of wired and wireless Ethernet connections.

A **bridge** is similar to a router in that it connects two or more networks. The difference is that a router analyzes data packets to determine where to send the packet next, whereas a bridge simply forwards the data to the next network without analysis. This makes for fast data transfer that lacks versatility. Bridges are not widely used in modern networks, as routers and switches are the favored devices. (Network Layer Device)

A **repeater** is a device used to strengthen, replicate, and regenerate signals that are weakened (for example, because of distance) during transmission. In many large homes, the Wi-Fi signal does not extend to the end of the house farthest from the router. A range extender is a form of repeater that takes the distorted Wi-Fi signal and transmits it to the formerly dead zone. (Physical Layer Device)

A **hub** connects the router to the network, takes the data packets from the router, and sends them to all the devices connected on the network. An example is a USB hub. By connecting a USB hub to your computer, data packets are able to be transferred to multiple devices connected to your computer; each device then looks at only the traffic destined for it and ignores the rest. (Physical Layer Device)








































**Basic Network Commands**

**ping:** One of the most basic tools for testing connectivity to other hosts. It sends an internet control message protocol (ICMP) echo request to a host and listens for the reply. If a reply is received, it will display the time it took and the time to live (TTL) left. Ping has many options for setting attributes of the request, like the maximum TTL, IPv4/IPv6, and the number of requests to send. Ping is useful in troubleshooting connectivity with other devices. If a reply is not received, you will receive a timeout message, which could indicate connectivity issues, firewall issues, or both issues with the other device. In addition, due to the time to get a response, the latency between two devices can be measured, enabling a network engineer to troubleshoot performance problems or a network architect to determine where to place devices to minimize response time to other systems and users.

**traceroute/tracert:** Use to trace the route an IP packet takes to a destination. It displays each hop (next router) in a numerical list with the hop’s IP address and the time it takes to receive the packet. The command traceroute is used for Linux systems and tracert is used for Windows systems. It can be useful in determining where a ping fails, troubleshooting performance issues, and other aspects regarding connectivity.

**tracepath:** Similar to traceroute or tracert in that it displays the path taken by a packet from its source to its destination. Tracepath is useful because it can be used by any user instead of needing superuser privileges. It is primarily used in Linux.

**ipconfig:** Internet protocol configuration (ipconfig) provides the user with the IP, subnet mask, and default gateway for each network adapter by default with the /all option information, such as MAC address, DHCP status, and lease information. The command ipconfig/release can be used to release all connections and renew all adapters. It is primarily used in Windows.

**ifconfig:** Used to configure the kernel network interfaces. It is implemented at the time of booting to configure the necessary interfaces. Once the interfaces are configured, it is used for debugging or tuning the system. It is primarily used in Linux.

**ARP:** Address Resolution Protocol (ARP) displays the IP to physical (MAC) address mappings for hosts that have been discovered in the ARP cache. ARP can be used to add, remove, or modify entries in the ARP cache. The hosts need to be on the local network, as these addresses are discovered by broadcasting to everyone on the network and noting the reply from the owner; broadcast traffic is not allowed through a router so that the system will maintain the MAC address of the router.

**netstat:** Network Statistics (netstat) displays information about active ports and their state and can be useful in troubleshooting and capacity management. The command netstat -r displays routing information for network adapters. It is available in Windows, MacOS, and Linux.

**nslookup:** Name server lookup (nslookup) displays information for displaying DNS information and troubleshooting DNS problems. It is useful for displaying names to IP address mappings.

**Dig (domain information groper)** is a command used to query the DNS name servers. It is helpful in troubleshooting DNS problems. It is also used for lookups and will display answers from the query. It is a replacement for nslookup.

**Whois** is a tool most often used to look up who owns a domain or block of IP addresses on the internet, including name, email address, and physical address. However, there are many privacy options that hide this information from being returned. It is primarily used in Linux.

**Route** can be used to display the current route tables on a host. Route can also be used to add or remove routes. This is used by the local host to determine where to send traffic (0.0.0.0 means the default gateway, where the router sends things if it is not otherwise defined in the routing table).

**The SCP (Secure Copy Protocol)** command is used to securely copy files between servers, leveraging SSH (secure shell) for authentication and encryption.

**FTP (file transfer protocol)** copies the file from one host to another host. The data is unencrypted. If encryption is needed, FTPS uses SSL/TLS (Secure Sockets Layer, replaced by Transport Layer Security; the same encryption used in https). Transfer uses TCP (transmission control protocol) for reliability and is often used on the internet and other wide-area networks, where errors may be more common.

**TFTP (trivial file transfer protocol)** transfers a file from either a client to a server or from a server to a client using UDP (user datagram protocol) instead of TCP, and so it is usually used on reliable (local) networks.

**Finger** displays information about a user or users on a remote system, including things such as last login time and username. It is primarily used in Linux.

**Nmap (Network Mapper)** scans networks to see what it can find in terms of hosts and open ports (including well-known ones for many applications). It is commonly used to determine what is deployed on a network for vulnerability analysis, security scans, and related activities. Nmap is not native to either Linux or Windows but can be downloaded for free and used with both.

**Tcpdump** displays TCP/IP packets and other network packets that are being transmitted over the network system. It is a form of protocol analyzer (sometimes called a sniffer) and is designed to show the contents of network packets in human-readable form for troubleshooting, security analysis, etc. Tcpdump is not native to either Linux or Windows but can be downloaded for free and used with both.

**Telnet and SSH (secure shell)** allow a user to manage accounts and devices remotely. The main difference between the two is that SSH is encrypted, and thus all data is secure from eavesdropping, while telnet is unencrypted.














**Network Topologies**

**Bus Topology:** A bus network topology is a single line of devices connected together by one shared network cable. Typically drawn as a single straight line, the network cable is rarely as straight. Often the cable is passed around walls or cubicles so that each computer can be attached to the network.

In a bus topology, computers connect to the network by physically tapping into the network cable using special adapters. This allows the network cable to remain one continuous conduit while also allowing the computers to send and receive electrical signals on the cable.

This leads to an important requirement of bus networks: the ends of the cable must be properly terminated. At both ends of the network cable, special electrical resistors called terminators must be attached to absorb stray electrical signals on the wire. If these terminators are removed or if the network cable is accidentally cut, the electrical signals will not be properly absorbed and will bounce back along the wire, causing communication loss, a condition called signal reflection.

The network in a bus topology is also referred to as a **network segment** because the network may be extended by adding more segments of cable to either end of the network, allowing more computers to connect to the shared network. 

Computers on bus networks communicate in **half-duplex mode**, meaning that you can either send or receive at any given time but cannot send and receive simultaneously. The network cable in a bus topology is a **shared communications medium**, meaning that all computers attached to the network will receive any and all traffic sent on the network.

**Ring Topology:** The ring topology was created to combat one of the more challenging aspects of the bus network: **traffic collisions**. Ring-based protocols such as token ring or fiber distributed data interface (FDDI) allows the network cable to remain a shared medium, but it controls traffic.

The network cable may run in a similar pattern to that of a bus network topology but with some important differences: the network cable is interrupted by each computer on the ring, and the cable is connected back to itself instead of using terminators. In a ring topology, the cable enters a “ring in” port on the network card of the computer and exits a “ring out” port on its way to the next computer in the ring. 

In cases where the network must be highly available, a **dual-ring topology** can be used. In this case, there are two sets of cables, and each computer has two network cards, one for each ring. In the event of a single cable break, the second ring can take over, allowing network traffic to continue to flow. However, the dual-ring topology has its greatest benefit in the event that both rings are simultaneously cut. In this case, the two loose ends on either side of the cable break can be connected together, merging the two broken rings into one much larger, but continuous ring, where traffic can flow. This dual-ring topology is commonly found in fiber optic networks, such as the **synchronous optical network (SONET) ring.**

**Star Topology:** Also known as a **hub-and-spoke network**, is an improvement upon the bus topology. A star network is composed of a central network device such as an Ethernet switch connected to various network devices, such as servers, computers, and printers, by individual network cables.

In a star network, each device is only connected to the central switch. All device-to-device communication is sent through the switch at the center of the network and then forwarded by the switch to the proper destination.

Star networks are the most common type of network found in LAN environments.

One key advantage to this topology is versatility. Instead of running cables from computer to computer, network cables are often run in the walls to a central closet. This gives the network administrator the flexibility to move computers around the office with re-cabling the network. 

The star topology is not only used in LAN environments. It is also used in some forms of WAN, where many remote offices are connected to a central headquarters location. Each remote office then becomes a spoke off the hub of the central headquarters. When a computer in one remote office wishes to communicate with a computer in a different remote office the traffic is passed through the central headquarters network. The star topology eliminates the need for a point-to-point network connection between each remote office.

**Mesh Topology:** The term mesh originates from the interconnected threads in a fabric or a net. Mesh topologies are often drawn as a web of direct connections between computers or nodes in a network. However, those connections may be permanent or constructed dynamically, as nodes need to talk to other nodes. A mesh topology permits nodes to communicate with each other; the topology may be either a full mesh, where every node has access to all other nodes, or a partial mesh network, where each node is only able to connect to a subset of the other nodes.

The nodes may connect using Wi-Fi or radio signals or by virtual links such as VPNs. 

Mesh networks are typically used where communication within a network must be highly available and redundancy is needed. The nodes within a mesh network can communicate with each other, and these connections can be changed dynamically if one node were to fail. This behavior is often referred to as a self-healing network because the nodes in the mesh are aware of each other and can establish new connections around failed nodes as needed.





















**Network Architectures**

Architecturally speaking, there are two extremes in networking and computer architecture: centralization and decentralization. In between these extremes, however, are two variants: **client/server and peer-to-peer.** 

**Centralized** **networks** are networks where computing and network power is centralized ina large secure data center where users log on to dumb terminals to access mainframe data and perform tasks.

**Decentralized networks** are networks that rely on the computing power in the user’s device and enable users to operate without a network connection and be portable. Some challenges of decentralization include storage, local security, and differences in operating systems and software.

**Client/Server networks** offload some of the computing requirements from the data center’s servers allowing application designers to implement advanced user interfaces in web or terminal based applications. However, application designers are not the only ones benefiting from client/server architecture.

In a **peer-to-peer network** client computers act as both servers and workstations because they share files and printers while allowing use of the client computer for normal tasks.

Network architecture depends on both wired and wireless connections. Wireless networks are great for portability. The challenge is the signal strength and stability of that wireless signal.

Wired networks are difficult to make portable but have very stable connections, however some wireless technology is faster than wired.























**Cloud Security**

A **network firewall** is a barrier that intercepts and inspects traffic moving from one area of the network to another. 

A **packet filter** is a firewall that operates at Layers 3 and 4 of the OSI network model: network and transport.

These firewalls inspect incoming (ingress) and outgoing (egress) traffic and compare the following attributes to a database of packet filter rules that determine if the firewall will forward (allow) or drop (deny) the traffic:

- Protocol (typically IP)
- Source IP Address
- Destination IP Address
- Source TCP or UDP port number
- Destination TCP or UDP port number

These firewalls are only concerned with the address label (header) of the pacers and perform no level of inspection on the contents of the packet (the payload). This means that potentially dangerous payloads could pass through a packet filter without being detected as long as the source and destination values were approved by the firewall rules.

A **circuit-level gateway** is a device that operates as a middleman between two or more systems to help conceal the true identity of the client and server. The gateway may change the IP address and the TCP/UDP port number of the traffic to allow two networks to communicate that otherwise could not.

Circuit-level gateways are the foundation of network address translation (NAT) and port address translation (PAT), which are commonly used in firewalls to allow private IP address ranges to communicate on the internet. These firewalls are only concerned with the address label (header) of the packets and perform no level of inspection on the contents of the packet (the payload). This means that potentially dangerous payloads could pass through a packet filter without being detected as long as the source and destination values were approved by the firewall rules.

To reduce the number of firewall rules needed to support TCP communication, firewall vendors implemented a feature known as **stateful inspection**. This feature allows a firewall to identify traffic as conversational and automatically create temporary firewall rules to permit the response traffic to flow back to the sender. In this way, instead of maintaining a multitude of rules, in a firewall with stateful inspection, you only need to create a firewall rule that allows the communication to begin.

In order for a firewall to understand whether there is a conversation going on between two endpoints, it must be able to analyze the address (Layer 3), it must be able to analyze the type of traffic - usually TCP or UDP - which requires Layer 4 inspection, and it must be able to analyze Layer 5 data in order to recognize that a session has been requested and established.

**Intrusion Prevention System**

- Intercepts and blocks threats
- Has many network ports to operate as input/output pairs
- Has cables routed physically through devices to create choke points

**Intrusion Detection System**

- Monitors the network to detect threats
- Listens passively on the network
- Alerts network admin of any detected suspicious behavior

**IPS and IDS**

- Identifies malicious traffic
- Available as virtual and host-based applications
- Can be configured to operate in tap mode








































**7 Layers of OSI for Network Security**

**Layer 1: Physical**

- The physical layer represents the physical medium that connects the computers together. Each medium will have different strengths and weaknesses.
- Wiretapping is a Layer 1 threat because it involves tampering with the physical cables of a victim’s network.
  - Copper-based wiring, such as Cat6 cabling, is susceptible to electronic sniffing or listening devices because the electrons flowing through the cables create a perceptible electromagnetic field (EMF).
  - Fiber optic cables use light waves instead of electrons and therefore do not emit an EMF signature that can be captured and interpreted.
- All physical vulnerabilities and threats are Layer 1 risks.

**Layer 2: Data Link**

- Layer 2 represents how computers logically connect to the network. Protocols at Layer 2 defined how computers can share access to a common medium, such as a wired or wireless network. This includes protocols such as 802.3 Ethernet and 802.11 Wi-Fi.

**Layer 3: Network**

- Allows computers on different networks to exchange data. This layer is where you will find the IP and ICMP protocols, which belong to the TCP/IP protocol suite.


**Layer 4: Transport**

- The two most common protocols within Layer 4 are the TCP and UDP protocols, both of which belong to the TCP/IP suite. Protocols at Layer 4 use 16-bit numbers called port numbers that uniquely identify each service on a particular host.
- The Transport layer ensures that data received from the upper OSI model layers are delivered according to the needs of the application.
  - The applications do not need to be aware of how the transport layer maintains its connectivity.
- TCP is a connection-oriented protocol.
  - Provides delivery confirmation for data sent between two computers.
  - If the sender does not receive confirmation of the delivery, it will retransmit the data to ensure it is eventually received.
- UDP is a connectionless-oriented protocol.

**Layer 5: Session**

- Allows computers to differentiate between the connections within a service on the same host.
- Remote procedure call (RPC) is an example protocol at Layer 5 and is used by computers to execute functions and procedures on other computers such as a central server launching a program or print job.
  - RPC has often been the target of many attacks over the years, but with regular operating system and application patching, you can mitigate most of these attacks.

**Layer 6: Presentation**

- Serves as a translation and security layer between applications allowing computers to encode and encrypt data.
- Encoding is the process of writing data in a particular manner, such as a standardized file format like XML or GIF.
- Encryption is the process of concealing data, and is commonly performed at the Presentation layer using Transport Layer Security (TLS), the replacement for the now deprecated SSL protocol commonly used to secure web pages.

**Layer 7: Application**

- Defines how users connect with the application services through protocols such as HTTP.

###
###
###
###
###
###
###
###
###
###
###
###
###
###
###
###
###
###
###
###
###
###
### **Network Device Hardening**
### **Why Harden Devices?**
Network devices, such as switches, routers, and firewalls have access to all data sent through them, which means they have access to a lot of your data. If these devices were compromised by a malicious user or attacker, the attacker would gain access to all of that data plus other information that could allow the attacker to change firewall rules and cause other damage to your network and the devices. These threats are even more potent when wireless networks are involved because just being in the vicinity may be enough to allow an attacker to gain access, change device settings, and eavesdrop on your network traffic.

This is why you must carefully and regularly review the security settings on your network devices, update the device software, and test the security of the device by attempting to breach its defenses. This process is known as hardening the security of a device, though the process also applies to servers and workstations.
### **How to Harden Devices**
There are some general security hardening steps that should be performed on all network devices as well as a few device-specific steps that differ by the type of device.
### **Change Default Passwords**
First and foremost, when you install a new or even previously used network device, be sure to change the device’s password. Never leave the device configured with its factory-default password. Attackers can easily search the internet and find the default password of nearly every brand and model of network device ever made. Unfortunately, due to laziness or ignorance on the part of the network administrator, attackers often succeed in logging in using the default password.
### **Remove Unnecessary Logins**
Closely related to the last point is to remove any unnecessary accounts (including the default users if possible) from the device. Unnecessary accounts, in this context, are those not used by you (at home) or the network administration team responsible for the device in question. Of course, you will first need to create replacement users and passwords for them, but this makes it that much more difficult for the attacker when they try and log in to your device as an admin, but you have deleted that account and created one with another name.

A second part of this recommendation is to periodically review the list of authorized users in each device and remove those that no longer need access (because they changed job roles, left the company, etc.). This is also a good time to make sure that no unrecognized accounts are on the device as well and to remove any that are found immediately along with changing all passwords and further hardening the device as quickly as possible to limit potential damage.
### **Enforce a Strong Password Policy**
Devices should require strong passwords for all users. If possible, enforce this policy through the device’s operating system; if not, make a company policy for everyone (including the administrators) to have a complex password (a long password of at least 10–12 characters with a combination of uppercase and lowercase letters, numbers, and special symbols, subject to what the device supports). Additionally, each user should be required to change their password frequently (typically every 30-90 days, depending on the organization, sensitivity of the data being stored and moved across the network, etc.) to further limit damage if something is compromised. If the device can provide a report on the last time a password was changed, run that report and make sure that the policy is being followed.

If the device supports multi-factor authentication (MFA), be sure to require that as well and configure it properly for every user. Text messaging and email are not considered strong forms of MFA but are better than nothing if that is all that is available. Virtual MFA applications or physical tokens are better, if possible.
### **Remove Unnecessary Services**
If there are optional features installed on the device that you are not using, disable or remove them (depending on the device and platform) to reduce the risk of attack that service opens up. This is true for all of your devices, but especially the network ones. That said, if there are features that harden the device, you may wish to enable or add them to strengthen the defenses of the device.
### **Keep Patches Up to Date**
Be sure to patch every device to get the latest security updates installed before an attacker can exploit a security flaw. This is true not only for servers and workstations, but for every network device, storage device, wireless router, etc. that can be updated. Many times, security researchers discover a vulnerability and notify the manufacturer so they can fix it before publicly disclosing it 90 days or so after discovery. The manufacturer needs time to come up with and test the patch, make it available, and then you need to get it installed before an attacker finds out about it and starts looking for victims.
### **Limit Physical Access to the Device**
One of the basic tenants of security is that physical access equals access. As has been explained elsewhere in this course, if someone has physical access to a device, they can break into it if given enough time. Many network devices also have special ports or reset buttons on them that could allow an attacker who has physical access to make changes quite easily. Lock up your network devices and be sure to observe anyone who physically interacts with the device.
### **Only Allow Changes from a Trusted Network**
For all devices, but especially firewalls and wireless devices that are often exposed to the internet and the wider public at large, there are a couple of other precautions that should be followed:

- Disallow any changes from the public side of the network device.
- Disallow changes to a wireless access point or wireless router from other wireless devices.

The purpose of these restrictions is to ensure that the user is authorized and inside the network (see the previous point about limiting physical access in this regard as well).
### **Require Encryption for Wireless Networks**
Be sure to configure and enable WPA2 (or better yet, WPA3) so that the traffic crossing the network is encrypted as discussed elsewhere in this course. You may have seen networks on your phone, tablet, or computer that do not have the lock indicator beside the network name—they are open public networks. Even if you are redirected to a log-in page, that is usually for legal reasons, not for any encryption purposes. Never send confidential information across an unencrypted network, especially a public one.
### **Audit Access**
While all of the above recommendations are proactive in nature, it is possible that something slips through. To help you look for suspicious activity and to do a forensic analysis of when a device was breached, from where, and the methods used, you will need audit logs. Be sure to collect these logs and store them off of the device (and thus, out of the attacker’s reach). In fact, the lack of audit logs being created when they have been in the past can be a red flag that something is wrong. Syslog is a common way to gather the logs and send them to a Syslog server for storage. There are many applications, both commercial and open-source, that can review these logs and alert you when anomalies are detected and should be further investigated by a person.

**Backup**

Keep backup copies of any device configuration files in case they need to be restored due to misconfiguration, attack, or device replacement, among other reasons. Devices on the network should also be backed up and stored remotely. These backups can be stored in the datacenter, but copies should be stored off-site in case of fire, flood, or other natural disasters as well as to protect against other problems that may affect the entire data center. This is your last line of defense in many cases.

15
