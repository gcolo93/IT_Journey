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

The least expensive and most common type of cable is the **unshielded twisted pair (utp).**

**Shielded twisted pair (stp)** has an extra shielding to prevent the leakage of electrical noise from one wire to another.

**UTP cables** come in six different standard types as defined by TIA/EIA 568. You can identify the type of cable you have by looking at the writing on the cable itself.

- **Cat3** supports up to 10 Mbps for up to 100 meters and is commonly used for phone lines today.
- **Cat4** supports 16 Mbps for up to 100 meters and is not commonly used today.
- **Cat5** is used in Ethernet LANs containing two twisted pairs allowing for up to 100 Mbps up to 100 meters between the device and the switch, hub, or router. This has been practically replaced by the Cat5e specification.
- **Cat5e** doubles the number of twisted pairs to four for up to 1 Gbps over up to 100 meters.
- **Cat6** is also used in Ethernet LANs and data centers. Cat6 is made up of four tightly woven twisted pairs (more twists per linear foot) and supports 1 Gbps for up to 100 meters or 10 Gbps for up to 55 meters.
- **Cat6a** is an improvement of the Cat6 standard, supporting the same standards and lengths (with the ability to run 10 Gbps over 100 meters maximum), but using a higher quality cable that is more resistant to interference. This is most commonly used in wired networks today.

**RJ11:** A connector that supports two pairs of wires (four total); typically used in telephones.

**RJ45:** This is an end connector typically used with Ethernet cables and supports four pairs (eight wires).

**Coaxial cables:** Analog cables made of copper but specifically engineered with a metal shield intended to block signal interference. The protection on the coaxial cable allows them to be laid next to metal gutters or other objects without receiving interference. Today, coaxial cables are mostly used by cable TV companies to connect their customers to the company’s facilities.

**ST:** Stands for straight tip connector. This was the most commonly used connector with multimode fiber until the mid-2000s.

**LC:** Stands for lucent connector. This is a smaller version of the standard connector (SC). This supports more ports to be used in the same space.

Networking Standards

**The Institute of Electrical and Electronics Engineers (IEEE)** is an association of professional electron and electrical engineers responsible for many of the standards created in networking today.

IEEE Standards for Wired Ethernet Networks

- 802.3i
  - 1990
  - 10BASE-T: 10 Mbps over UTP
- 802.3j
  - 1993
  - Added fiber-optic cable options
- 802.3u
  - 1995
  - Added 100 Mbps speed, also known as Fast Ethernet
  - Added auto-negotiation of speed (10 Mbps or 100 Mbps)
- 802.3x
  - 1997	
  - Full-duplex (bi-directional communication at the same time - a node could both send and receive traffic instead of one or the other, similar to the difference between a phone and a walkie-talkie)
- 802.3z
  - 1998
  - 1000BASE-X: 1 Gbps over fiber-optic cables
- 802.3ab
  - 1999
  - 1000BASE-T: 1 Gbps over UTP
- 802.3ae
  - 2002
  - 10GBASE-X: 10 Gbps over fiber-optic cables
- 802.3af
  - 2003
  - Power over Ethernet (PoE), the ability to power a low-power device, 15 watts or less, without plugging it into an electrical outlet, reducing cabling.
- 802.3ak
  - 2004
  - Added support for twinaxial cables, a type of coax with two wires in the cable instead of one; used in short connections (typically just a few meters, such as within a rack) as an inexpensive alternative to fiber-optic cabling.
- 802.3an
  - 2006
  - 10GBASE-T: 10 Gbps over UTP
- 802.3bm
  - 2015
  - 40 and 100 Gbps over fiber-optic cables
- 802.3by
  - 2016
  - 25 Gbps over fiber-optic and twinaxial cables
- 802.3bs
  - 2017
  - 200 Gbps and 400 Gbps over fiber-optic cables
- 802.3bt
  - 2018
  - Update to power over Ethernet (PoE) to support up to 100W devices.

IEEE Standards for Wireless Networks

- 802.11
  - 1997
  - Provides 1 or 2 Mbps transmission in the 2.4 GHz band
  - Uses frequency-hopping spread spectrum (FHSS)(the signal hops between random frequencies to reach the destination)
  - Can also use direct-sequence spread spectrum (DSSS)(data is divided into smaller pieces before being sent with a higher bitrate)
- 802.11a
  - 1999
  - Provides up to 54 Mbps in the 5 GHz band
- 802.11b
  - 2000
  - Provides 11 Mbps in the 2.4 GHz band
  - Uses only direct-sequence spread spectrum (DSSS)
- 802.11g
  - 2003
  - Used for transmissions over short distances
  - Speeds up to 54 Mbps in the 2.4 GHz bands
- 802.11n
  - 2007
  - Adds multiple-input multiple-output (MIMO)(uses multiple signals on different frequencies to increase the range and bandwidth of wireless networks and forms directed beams toward each client, reducing the interference from other wireless devices nearby).
  - 4-5 times faster than 802.11g
- 802.11ac
  - 2013
  - Delivers data rates of 433 Mbps per signal or 1.3 Gbps in a three-signal design
- 802.11ah
  - 2017
  - The first Wi-Fi specification to operate in frequency bands below 1 GHz (900 MHz)
  - Nearly twice the range of other Wi-Fi technologies
  - Can penetrate walls and other barriers better than previous Wi-Fi standards
  - Much lower bandwidth (< 9 Mbps)
  - Designed for Internet of Things (IoT) devices and similar use cases with limited bandwidth needs over larger distances
- 802.11ax
  - 2019
  - Update to 802.11ac
  - Rebranded to Wi-Fi 6
  - Adds support for 6 GHz frequency range
  - Support for approximately 1 - 10 Gbps
















Basic Network Commands

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

**PAN:** Personal Area Network is a network that is centered around a person and their devices. PANs can be used to enable communication between devices, such as a device sending music to speakers or headphones.

**LAN:** A local area network consists of computers connected within a limited area. Most often LANs use Ethernet, Wi-Fi or both to connect the network devices. Many LANs are wireless, where users are connected via Wi-Fi and can move unrestricted throughout the coverage area. This is a popular choice for home users and small businesses, as it is easy and inexpensive to install and allows guests to use the network as well.

**WLAN:** A wireless local area network, is a LAN with wireless connectivity. Unlike LANs, which are wired, WLANs use Wi-Fi to communicate with devices. Users and devices can be placed anywhere and move anywhere in the coverage area. Many WLANs act as a gateway to the internet for users.

**SAN:** A storage area network, is a network that allows access to storage devices specifically instead of more general networking that can be used for any purpose. SANs allow servers to access devices such as tape libraries and disk arrays while presenting them to the operating system like any other locally attached device.

Typically, a SAN is a network dedicated to storage devices and the servers that need access to them. The key reason for this is to reduce interference from normal LAN traffic during data transfer. SANs may also use other protocols, such as Fibre Channels that do not usually operate on traditional network equipment.

**CAN:** A campus area network provides networking of multiple LANs across a limited area, like a university campus or a group of building owned by a company Each LAN would typically be constrained to a singed building, and the CAN would link them together the same way that a WAN does but over a smaller geographic area.

**MAN:** A metropolitan area network provides networking across a larger area than a CAN, but smaller than a WAN,, such as a whole city or the equivalent of a metropolitan area, though it is not necessarily limited by city boundaries.

**WAN:** A wide area network is similar to a LAN except that it covers a large geographical area within its network. The internet is an example of a WAN.

**Client-server:** In a client-server network model, there is a distinct server and a distinct client. The server is the system that stores data and information. The client is the machine that needs access to that data.

**Peer-to-Peer:** In a peper-to-peer model, or P2P, there is no individually designated server or client. Each machine on the network can act as both server and client, sometimes requesting data from other nodes and sometimes answering requests from others. Bitcoin and Tor are examples of P2P networks.

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

Architecturally speaking, there are two extremes in networking and computer architecture: centralization and decentralization. In between these extremes, however, are two variants: **client/server and peer-to-peer.** 

**Centralized** **networks** are networks where computing and network power is centralized ina large secure data center where users log on to dumb terminals to access mainframe data and perform tasks.

**Decentralized networks** are networks that rely on the computing power in the user’s device and enable users to operate without a network connection and be portable. Some challenges of decentralization include storage, local security, and differences in operating systems and software.

**Client/Server networks** offload some of the computing requirements from the data center’s servers allowing application designers to implement advanced user interfaces in web or terminal based applications. However, application designers are not the only ones benefiting from client/server architecture.

In a **peer-to-peer network** client computers act as both servers and workstations because they share files and printers while allowing use of the client computer for normal tasks.

Network architecture depends on both wired and wireless connections. Wireless networks are great for portability. The challenge is the signal strength and stability of that wireless signal.

Wired networks are difficult to make portable but have very stable connections, however some wireless technology is faster than wired.

**Virtualization** describes the technique of converting a hardware-based resource into software.

Virtualization relies on a special type of software, known as a hypervisor, which creates the virtual hardware for devices. There are many different varieties of hypervisors, including open source and commercial. Some hypervisors run as standalone applications on Windows, MacOS, or Linux, whereas other hypervisors are installed as the underlying operating system itself. All hypervisors use software to create the illusion of physical hardware.

Each instance of virtual hardware is called a **virtual machine, or VM**.

The operating system (OS) installed within the VM is referred to as a **guest OS** to differentiate it from the operating system of the underlying physical computer, which is called the **host OS.** 

There are two types of hypervisors: Type 1 (bare metal) and Type 2 (hosted). Both types can host VMs; however, they have very different use cases. Type 2 hypervisors look and feel like any other application that you may run on your laptop. Type 1 hypervisors typically require dedicated hardware and are installed as that machine’s operating system, making them more commonly found in data centers than in home networks.

**Type 1 hypervisors,** such as VMware ESXi or the open-source KVM hypervisor, are operating systems that natively run virtual machines and are intended to be installed on a dedicated bare metal server. 

Type 1 hypervisors present very little information to the console screen of the host computer. All administration is typically performed from another computer. You would direct a web browser to the IP address or hostname of the hypervisor to access its web-based administration portal.

A **Type 2 hypervisor**, sometimes referred to as a hosted hypervisor, is installed as an application on personal computers or laptops.


Network Security Terminology

**Asset:** A person, device, location, or information the SecOps aims to protect from attack.

**Attack:** An action taken by a threat that exploits a vulnerability that attempts to either block authorized access to an asset, or to gain unauthorized access to an asset.

**Risk:** The potential of a threat to exploit a vulnerability via an attack.

**SecOps:** The abbreviation for IT security operations; a discipline within IT responsible for protecting assets by reducing the risk of attacks.

**Threat:** Something or someone that can exploit a vulnerability to attack an asset.

**Vulnerability:** A weakness in software, hardware, facilities, or humans that can be exploited by a threat.

Vulnerability testers are responsible for scanning servers and network devices for known vulnerabilities. There are a variety of vulnerability scanning tools on the market. Some are open source, such as Nessus, whereas most are commercial products.

**Blue, Red, White, and Purple Teams:** The red team attempts to compromise the security, while the blue team defends. There may also be a neutral white team that observes the festivities and may even serve as referee.

Some companies use this attack and defend approach but take it to the next level by involving continuous improvement in the process. This is referred to as the purple team. In the purple team approach, the red and blue team engage, and then when certain success criteria are met, the teams debrief, cross-train each other, and repeat. This is also known as an iterate and improve model.

**Hackers: White Hat, Black Hat, and Gray Hat**

White hat hackers are IT professionals who specialize in penetrating or compromising network security but only to help an organization improve its own security posture. Most importantly, they only perform the attacks when authorized to do so; to the fullest extent possible, they remain in compliance with any and all laws governing such behavior.

Black hat hackers may or may not be IT professionals but possess the knowledge and will to breach systems for profit. That profit may be monetary, street credibility, or just a source of entertainment. Black hat hackers do not ask permission and are not interested in helping their targets improve their network security.

Grey hat hackers are a group of people who may or may not be IT professionals and may or may not choose to break laws in pursuit of their hacking goals. Unlike black hat hackers, gray hats have no malicious intent in their actions; unlike white hats, they may not have obtained permission to perform the attack.

A **honeypot** is a server or device that is configured to look very authentic, potentially containing data that appears to be legitimate user data, or configuration files that seem authentic. It is also known as a **“tar pit”** because it is intended to attract or distract would-be attackers from the actual targets on the network. The goal of the honeypot is to provide a false positive for hackers, whereby the attacker breaches the honeypot and believes the data it contains is the target’s actual data.

An alternate use of the honeypot or tar pit servers is to collect data on the attacker. A tar pit server is similar to a honeypot in that it contains data that is fictitious; however the tar pit server is also designed to slow down the attacker so that tracing information can be obtained by the intrusion detection system (IDS).

### The CIA Triad
The **confidentiality, integrity, and availability (CIA) triad** is a reference model to help protect information from unauthorized disclosure and modification while ensuring it is accessible and intelligible to its authorized users. The CIA triad is composed of three principles: confidentiality, which limits access; integrity, which enables you to trust the information; and availability, which ensures that you have access to the information.
### **Confidentiality**
The confidentiality principle helps limit access to information, which, by definition, can contradict some of the recommendations found in the availability principle. The goal of confidentiality is to prevent an unauthorized user from accessing, copying, or transmitting the information.

Confidentiality is often equated to privacy because the two terms share many of the same characteristics, such as ensuring that only the intended recipient of the information can access it, following a need-to-know policy, and reducing exposure by destroying all copies of the information that are no longer needed.

There are many ways to breach or compromise the confidentiality of data if the proper precautions are not taken in advance and then routinely checked for accuracy and consistency.

- Unencrypted information is easy to steal and change.
- Deleted files are rarely purged from a disk immediately and often can be recovered with ease.
- The physical theft of a device gives an attacker an unlimited time window to break the encryption of your data.
- Social engineering is a method used by attackers to gain an unsuspecting victim’s trust to provide information, such as passwords or server names, or even just to gain physical building access.
- Accidents and malfunctions also play into the equation. For example, confidentiality of information can easily be breached by storing files in the wrong location, emailing data to the wrong person, or printing confidential information to a public printer.

Some methods that may help prevent compromises include:

- Where possible, encrypt the information at-rest (where it is stored) and in-transit (while it is moving across the network).
- Be sure to encrypt and physically secure your laptops, servers, portable hard drives, and even backup tapes/disks.
- Consider using a tool to securely delete files or overwrite them after deletion.
- Train your employees about social engineering attacks.
- Create and enforce a policy that ensures all users must use complex passwords (a combination of uppercase and lowercase letters, numbers, and symbols with a minimum length) and use multifactor authentication (MFA), such as biometrics or a digital key fob.
- Following the principle of least privilege (which means you only assign users the minimum permissions needed to perform their jobs), institute restrictive access controls on all data and provide access to information on a need-to-know basis only.
### **Integrity**
The integrity principle helps identify the trustworthiness of the information. It is possible to identify where the information came from and if the data has changed since it was originally sent. Integrity is a function that is often incorporated into encryption and, therefore, works well with the confidentiality principle.

Some of the compromises of data integrity include:

- Man-in-the-middle attacks, where an attacker changes the contents of the message after it was sent, but before it was received
- The intentional or unintentional deletion or modification of data
- Malfunctions in equipment that cause data corruption
- Natural phenomena such as electromagnetic pulse (EMP) attacks, which can destroy or severely corrupt data

Some methods that can be employed to help prevent the compromise of data integrity include:

- Require all data transmissions to use encryption or digital signatures to confirm the identity of the sender and to identify if the message has been changed.
- In cases where digital signatures will not work, use one-way hash calculations, such as SHA-3 (Secure Hash Algorithm 3), to create a value that can be used to verify the data has not changed.
- Use version control within your data storage to help you quickly revert accidental changes or deletions.
### **Availability**
The goal of the availability principle is to ensure that the data is always accessible by its authorized users. This includes aspects such as adding high availability to your server solutions and minimizing downtime by carefully managing your application updates and patches.

Some of the common actions that can compromise the availability of data include:

- denial-of-service (DoS) and distributed denial-of-service (DDoS) attacks, which prevent legitimate users from accessing the resource by sending an overwhelming amount of data to the target server;
- unplanned downtime due to server crashes or failed upgrades; and
- accidental changes to access control lists, which removes access for authorized users.

Some methods that can be employed to help prevent availability issues include:

- creating and maintaining a full disaster recovery plan that includes a full site failover as well as the method to restore data for individual servers;
- implementing server high availability where possible, employing clustering technology where appropriate; and
- setting up regular backups of your data and considering storing a backup copy at another physical location to protect against site-level disasters.

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

In cryptography terms, **unencrypted data** is referred to as being sent or stored in the clean meaning that the data can be read by anyone who intercepts the communication or accesses the unencrypted file.

**Encrypted data** is referred to as ciphertext because the proper term for an encryption algorithm is a cipher. These ciphers come in many forms and rely on different types of keys to encrypt and decrypt the data.

If the cipher uses the same key to encrypt the data as it does to decrypt the data, the cipher is said to use a symmetric key. Conversely, if the keys are different, the cipher is said to use an asymmetric key pair: one key to encrypt the data and another to decrypt it.

**3DES:** Triple DES is a symmetric encryption algorithm that uses the now antiquated DES (data encryption standard) algorithm three times in a row to encrypt data. The DES algorithm uses only 56-bit encryption and can be compromised by brute force software running on modern hardware in less than a day. By utilizing multiple independent keys, 3DES increases the overall complexity of the encryption, but the encryption can still be compromised.

**AES:** The Advanced Encryption Standard (AES) is considered a very secure form of encryption today, although, with advances in computing power and quantum computing, it may not be considered secure forever. AES can be used with a 128-bit, 192-bit, or 256-bit key. Longer key lengths are exponentially harder to crack, but they also increase the amount of computing power required to encrypt the data. The AES standard is a symmetric key algorithm.

**WEP:** Wired equivalent privacy was part of the first wireless standards proposed by the IEEE in 1997. A WEP key is either 10 or 26 hexadecimal digits. Each hexadecimal digit is 4 bits. Therefore, the bit length of the encryption key is either 40-bit or 104-bit, both of which can be compromised in under a day using brute force methods on standard workstation hardware.

**WPA:** Wi-Fi protected access, and the subsequent standards WPA2 and WPA3, were defined by th eWi-Fi Alliance and the IEEE to overcome the weaknesses of WEP. WPA uses a variable-length alphanumeric passphrase, which can range from 8 to 63 characters in length. TKIP (temporal key integrity protocol) gives WPA a significant security boost by generating a new 128-bit encryption key for every packet sent on the network.

**WPA2:** The major difference between WPA2 and WPA is the mandatory support for Counter Mode Cipher Block Chaining Message Authentication Code Protocol (CCMP for short), which is part of the AES encryption standard. It is designed to provide data confidentiality, authentication, and access control to the network.

**WPA3:** Increases the minimum key strength to 192-bits for enterprise mode connections, which are often used in organizations instead of the alternate personal mode available in WPA standards. All devices now use the simultaneous authentication of equals (SAE) method to exchange the network key as defined in the IEEE 902.11-2016 standard. The SAE method ensures the initial key exchange in personal mode is more secure by eliminating the need to tell others the key before they connect to the network.

WPA3 also implements another method known as forward secrecy or perfect forward secrecy (PFS) which ensures that even if one session key is compromised, that compromised key will only affect data exchanged in that encryption session not in any past or future sessions.

In **ad-hoc mode** all wireless communication is performed in a peer-to-peer fashion and does not require or involve WAP. Ad-hoc wireless networks are rarely used in homes or offices but they can be helpful in setting up a new device such as a printer by connecting them directly. Ad-hoc networks are also occasionally used to transfer files between devices.

**802.1x security standard** provides network access control at the port level, whether physical or wireless, and it provides an authentication standard based on the Extensible Authentication Protocol (EAP). Authentication is typically done via a username and password, but you can also configure it to use public key infrastructure (PKI) certificates.

802\.1x trusted network access process:

- Client requests access to the network via a WAP or a wired Ethernet switch and then provides credentials for the network access.
- The WAPP or switch forwards the network access request to a special authentication server running remote authentication dial-in user service (RADIUS) or EAP, which then validates the credentials and determines the user’s authorization based on policies defined by a network administrator.
- If the credentials are validated and the user is authorized, the WAP or switch grants network access to the user.
- If the user is not authenticated properly or does not have the authorization to access that network, the WAP or switch will block network access to the user.

**Deauth Attack:** Deauthentication is a denial-of-service attack where the attacker can force any client off of the network. The attacker does not need to be on the network they are attacking. 

The simplest defense is to use WPA3 security on WAPs because the management packets are encrypted.

**Fake Access:** An attacker sets up an illegitimate wireless network using their own WAP and may even share their own cellular data to create a hotspot. The attacker usually opens this network without any security or authentication so as to entice people in a hurry to connect to the attacker’s rogue WAP.


**Authentication authorization, and accounting (AAA)** describes the process of granting or denying access to data and network resources as well as verifying that the security controls are working properly.

Authentication is the process of confirming a person’s identity. A system can confirm your identity via usernames and passwords or with certificates as is the case with PKI.

Authorization determines what the user may access.

Accounting verifies that the restrictions put in place are working as expected and there is not attempted or actual unauthorized access. Accounting also includes verifying the correct access control settings on data files, providing a forensic trail after a security breach to determine how the attacker got in and what they accessed.
