Lesson 1: Comparing OSI Model Network Functions

Topic 1A

Open Systems Interconnection Model

●	7: Application

●	6: Presentation

●	5: Session

●	4: Transport

●	3: Network

●	2: Data Link

●	1: Physical

Data Encapsulation and Decapsulation

A network protocol is a set of rules for exchanging data in a structured format. A network protocol has two principal functions:

●	Addressing: Describing where data messages should go. At each layer, there are different mechanisms for identifying nodes and rules for how they can send and receive messages.

●	Encapsulation: Describing how data messages should be packaged for transmission. Encapsulation is like an envelope for a letter, with the distinction that each layer requires its own envelope. At each layer, the protocol adds fields in a header to whatever data (payload) it receives from an application or other protocol.

Same layer interaction: The protocol running at each layer communicates with its equivalent (or peer) layer on the other node.

Adjacent layer interaction: To transmit or receive a communication, on each node each layer provides services for the layer above and uses the services of the layer below.


When a message is sent from one node to another, it travels down the stack of layers on the sending node, reaches the receiving node using the transmission media, and then passes up the stack on that node. At each level (except the physical layer), the sending node adds a header to the data payload, forming a “chunk” of data called a protocol data unit (PDU). This is the process of encapsulation.

The receiving node performs the reverse process, referred to as decapsulation. It receives the stream of bits arriving at the physical layer and decodes an Ethernet frame. It extracts the IP packet from this frame and resolves the information in the IP header, then does the same for the TCP and application headers, eventually extracting the HTTP application data for processing by a software program, such as a web browser or web server.

Layer 1: Physical

The physical layer (PHY) of the OSI model (layer 1) is responsible for the transmission and receipt of the signals that represent bits of data from one node to another node.




Different types of transmission media can be classified as cabled or wireless:

●	Cabled: A physical signal conductor is provided between two nodes. Examples include cable types such as copper or fiber optic cable. Cabled media can also be described as bounded media.

●	Wireless: Uses free space between nodes, such as microwave radio. Wireless media can also be described as unbounded media.

The Physical layer specifies the following:

●	Physical topology: The layout of nodes and links as established by the transmission media. An area of a larger network is called a segment. A network is typically divided into segments to cope with the physical restrictions of the network media used, to improve performance, or to improve security. At the Physical layer, a segment is where all the nodes share access to the same media.

●	Physical interface: Mechanical specifications for the network medium, such as cable specifications, the medium connector and pin-out details (the number and functions of the various pins in a network connector), or radio transceiver specifications.

●	The process of transmitting and receiving signals over the network medium, including modulation schemes and timing/synchronization.

Devices that operate at the Physical layer include:

●	Transceiver: The part of a network interface that sends and receives signals over the network media.

●	Repeater: A device that amplifies an electronic signal to extend the maximum allowable distance for a media type.

●	Hub: A multiport repeater, deployed as the central point of connection for nodes.

●	Media converter: A device that converts one media signaling type to another.

●	Modem: A device that performs some type of signal modulation and demodulation such as sending digital data over an analog line.

Layer 2: Data Link

The data link layer (layer 2) is responsible for transferring data between nodes on the same logical segment. At the Data Link layer a segment is one where all nodes can send traffic to one another using hardware addresses, regardless of whether they share access to the same media. A layer 2 segment might include multiple physical segments. This is referred to as a logical topology.

\*\*Nodes that send and receive information are referred to as end systems or as host nodes. This type of node includes computers, laptops, servers, Voice over IP (VoiP) phones, smartphones, and printers. A node that provides only forwarding functions is referred to as an intermediate system or infrastructure node.

The data link layer organizes the stream of bits arriving from the physical layer into structured units called frames. Each frame contains a network layer packet as its payload. The data link layer adds control information to the payload in the form of header fields. These fields include source and destination hardware addresses, plus a basic error check to test if the frame was received intact.



Devices that operate at the data link layer include:

●	Network adapter or network interface card (NICs): A NIC joins an end system host to network media (cabling or wireless) and enables it to communicate over the network by assembling and disassembling frames.

●	Bridge: A bridge is a type of intermediate system that joins physical network segments while minimizing the performance reduction of having more nodes on the same network. A bridge has multiple ports, each of which functions as a network interface.

●	Switch: An advanced type of bridge with many ports. A switch creates links between large numbers of nodes more efficiently.

●	Wireless access point (AP): An AP allows nodes with wireless network cards to communicate and creates a bridge between wireless networks and wired ones.

Layer 3: Network

The network layer (layer 3) is responsible for moving data around a network of networks, known as an internetwork or the Internet. While the data link layer is capable of forwarding data by using hardware addresses within a single segment the network layer moves information around an internetwork by using logical network and host IDs. The networks are often heterogeneous; that is, they use a variety of physical layer media and data link protocols. The main appliance working at layer 3 is the router.

Router: An intermediate system working at the Network layer capable of forwarding packets around logical networks of different layer 1 and layer 2 types.



The network layer forwards information between networks by examining the destination network-layer address or logical network address. The packet is forwarded, router by router (or hop by hop), through the internetwork to the target network. Once it has reached the destination network, the hardware address can be used to deliver the packet to the target node.

\*\*The general convention is to describe PDUs packaged at the network layer as packets or datagrams, and messages packaged at the data link layer as frames. Packet is often used to describe PDUs at any layer, however.

It is usually important for traffic passing between networks to be filtered. A basic firewall operates at layer 3 to enforce an access control list (ACL). A network ACL is a list of the addresses and types of traffic that are permitted or blocked.

Layer 4: Transport

The first three layers of the OSI model are primarily concerned with moving frames and datagrams between nodes and networks. At the transport layer - also known as the end-to-end or host-to-host layer - the content of the packets becomes significant. One of the functions of the transport layer is to identify each type of network application by assigning it a port number.

At the transport layer, on the sending host, data from the upper layers is packaged as a series of layer 4 PDUs, referred to as segments. Each segment is tagged with the application’s port number. The segment is then passed to the network layer for delivery. Many different hosts could be transmitting multiple HTTP and email packets at the same time. These are multiplexed using the port numbers along with the source and destination network addresses onto the same link.



At the network and data link layers, the port number is ignored-it becomes part of the data payload and is invisible to the routers and switches that implement the addressing and forwarding functions of these layers. At the receiving host, each segment is decapsulated, identified by its port number, and passed to the relevant handler at the application layer. Put another way, the traffic stream is de-multiplexed.

The transport layer can also implement reliable data delivery mechanisms, should the application require it. Reliable delivery means that any lost or damaged packets are resent.

Devices working at the transport layer include multilayer switches-usually working as load balancers-and many types of security appliances, such as more advanced firewalls and intrusion detection systems (IDSs).

Upper Layers

The upper layers of the OSI model are less clearly associated with distinct real-world protocols. These layers collect various functions that provide useful interfaces between software applications and the transport layer.

Layer 5: Session

Most application protocols require the exchange of multiple messages between the client and server. This exchange of such a sequence of messages is called a session or dialog. The session layer (layer 5) represents functions that administer the process of establishing a dialog, managing data transfer, and then ending (or tearing down) the session.

Layer 6: Presentation

The presentation layer (layer 6) transforms data between the format required for the network and the format required for the application. The presentation layer can also be conceived as supporting data compression and encryption. However, in practical terms, these functions are often implemented by encryption devices and protocols running at lower layers of the stack or simply within a homogenous application layer.




Layer 7: Application

The application layer (layer 7) is at the top of the OSI stack. An application-layer protocol doesn’t encapsulate any other protocols or provide services to any protocol. Application-layer protocols provide an interface for software programs on network hosts that have established a communications channel through the lower-level protocols to exchange data.

More widely, upper-layer protocols provide most of the services that make a network useful, rather than just functional, including web browsing, email and communications directory lookup, remote printing, and database services.











Topic 1B Configure SOHO Networks

SOHO Routers

A network in a single location is often described as a local area network (LAN). This definition encompasses many different sizes of networks widely varying functions and capabilities. It can include both residential networks with a couple of computers, and enterprise networks with hundreds of servers and thousands of workstations.

Small office/home office (SOHO) is a category of LAN with a small number of computing hosts that typically rely on a single integrated appliance for local and Internet connectivity.

Networks such as the Internet that are located in different geographic regions but with shared links are called wide area networks (WANs). The intermediate system powering SOHO networks is usually described as a SOHO router because one of its primary functions is to forward traffic between the LAN and WAN.

Physical Layer Functions

Starting at layer 1, the SOHO router provides the following physical connections:

●	A number of RJ-45 ports (typically four) to connect to a local cabled network. These are typically labeled as the LAN ports.

●	Radio antennas to transmit and receive wireless signals.

●	A type of modem (typically cable or digital subscriber line) to connect to the Internet Service Provider’s (ISP’s) network. This is typically labeled as the WAN port. On other SOHO routers, there may be a different type of WAN modem, such as an RJ-11 port to connect to a digital subscriber line (DSL) service.


Data Link Layer Functions

At layer 2, the SOHO router implements the following functions to make use of its physical layer adapters:

●	Ethernet switch: The RJ-45 jacks are connected internally by an Ethernet switch.

●	Wireless access point: The radio antennas implement some version of the Wi-Fi standard. The access point functions as a wireless hub, allowing stations (PCs, tablets, smartphones, and printers) to form a wireless network. The access point is also wired to the Ethernet switch via an internal port. This forms a bridge between the cabled and wireless segments, creating a single logical local network.

At this layer, each host interface is identified by a media access control (MAC) address.










Network Layer Functions

At layer 3 the routing part of the SOHO router makes forwarding decisions between the local private network and public Internet. These zones are distinguished by internet protocol (IP) addresses. The local network uses a private IP address range, such as 1992.168.1.0/24. The SOHO router itself is identified by an address in this range, such as 192.168.1.1 or 192.168.1.254.


The router runs a dynamic host configuration protocol (DHCP) server to allocate a unique address to each host that connects to it over either an Ethernet port or via the wireless access point. The addresses assigned to clients use the same first three octets as the router’s address: 192.168.1. The last octet can be any value from 1 to 254, excluding whichever value is used by the router.

The SOHO router’s WAN interface is allocated a public IP address, say 203.0.113.1, by the internet service provider. When a host on the local network tries to access any valid IP address outside the 192.168.1.0/24 range, the router forwards that packet over its WAN interface and directs any replies back to the host on the LAN.

Transport and Application Layer and Security Functions

There is no separate OSI model layer for security Instead, security issues can arise and solutions are needed at every layer. Network security is essentially a matter of allowing or preventing devices, users, and services (applications) from using the network. The WAN interface is the network perimeter. The SOHO router can apply filtering rules to traffic sent between the public and private zones, implementing a firewall. The firewall can be configured to block traffic based on source or destination IP addresses and also on the type of application.

At layer 4, each application is identified by a port number. The firewall in the router can be configured with rules specifying behavior for each port.

Any host can connect to the RJ-45 ports on the router and join the network. The wireless network is usually protected by an encryption system that requires each station to be configured with a passphrase-based key to join the network.

Access to the router’s management interface and its configuration settings is protected by an administrative account passphrase. As the router is connected to the Internet, it is critical to configure a strong passphrase.

The Internet

The WAN interface of the router connects the SOHO network to the Internet.

The Public Switched Telephone Network

Most SOHO subscriber Internet access is facilitated via the public switched telephone network (PSTN). The SOHO router is described as customer premises equipment (CPE). More widely, this is any termination and routing equipment placed at the customer site. Some of this equipment may be owned or leased from the telecommunications company (or telco); some may be owned by the customer.

The CPE is connected via its modem and WAN port to the local loop. This is cabling from the customer premises to the local exchange. The point at which the telco’s cabling enters the customer premises is referred to as the demarcation point (often shortened to demarc).

Internet Service Providers

The major infrastructure of the Internet consists of high bandwidth trunks connecting Internet eXchange Points (IXPs). Within an IXP datacenter, ISPs establish links between their networks, using transit and peering arrangements to carry traffic to and from parts of the internet they do not physically own. There is a tiered hierarchy of ISPs that reflects to what extent they depend on transit arrangements with other ISPs.

Internet Standards

Internet Assigned Numbers Authority (IANA)(iana.org): Manages allocation of IP addresses and maintenance of the top-level domain space. IANA is currently run by Internet Corporation for Assigned Names and Numbers (ICANN). IANA allocates addresses to regional registries who then allocate them to local registries or ISPs. The regional registries are Asia/Pacific (APNIC), North America and Southern Africa (ARIN), Latin America (LACNIC), and Europe, Northern Africa, Central Asia, and the Middle East (RIPE NCC).

Internet Engineering Task Force (IETF)(ietf.org): Focuses on solutions to Internet problems and the adoption of new standards, published as Requests for Comments (RFCs). Some RFCs describe network services or protocols and their implementation, while others summarize policies. An older RFC is never updated. If changes are required, a new RFC is published with a new number. Not all RFCs describe standards. Some are designated informational, while others are experimental. The official repository for RFCs is at rfc-editor.org.















Lesson 2: Deploying Ethernet Cabling

Topic 2A: Summarize Ethernet Standards

Network Data Transmission

All network signaling uses electromagnetic radiation of one type or another. Electromagnetic radiation means transmitting signals as electric current, infrared light, or radio waves. The electromagnetic radiation forms a carrier wave with a given bandwidth or range of frequencies. A signal is transmitted over the wave by modulation and encoding schemes.

\*\*The narrow definition of bandwidth is a frequency range measured in cycles per second or Hertz (Hz), but the term is very widely used in data networking to mean the amount of data that can be transferred, measured multiples of bits per second (bps). Encoding methods mean that, for instance, a signal with 100 MHz frequency bandwidth can transfer much more than 100 mbps.

Copper Cable

Copper cable is used to transmit electrical signals. The cable between two nodes creates a low voltage electrical circuit between the interfaces on the nodes. There are two main types of copper cable: twisted pair and coaxial (coax). Copper cable suffers from high attenuation, meaning that the signal quickly loses strength over long links. Twisted pair cable is rated to Cat standards.

Fiber Optic Cable

Fiber optic cable carries very high frequency radiation in the infrared light part of the electromagnetic spectrum. The light signals are also not susceptible to interference or noise from other sources and less affected by attenuation. Consequently, fiber optic cable supports higher bandwidth over longer links than copper cable. Fiber optic cabling is divided into Single Mode (SMF) and MultiMode (MMF) types, and MMF is categorized by Optical Mode designations (OM1, OM2, OM3, and OM4).






Ethernet Standards

Standards set by the Institute of Electrical and Electronics Engineers (IEEE) 802.3 Ethernet standards (ieee802.org/3).

Ethernet standards provide assurance that network cabling will meet the bandwidth requirements of applications. The standards specify the bit rate that should be achieved over different types of media up to the supported distance limitations. These Ethernet media specifications are named using a three-part convention, which is often referred to as xBASE-y. This describes:

●	The bit rate in megabits per second (Mbps) or gigabits per second (Gbps).

●	The signal mode (baseband or broadband). All mainstream types of Ethernet use baseband transmissions, so you will only see specifications of the for xBASE-y.

●	A designator for the media type.


Media Access Control and Collision Domains

Ethernet is a multiple access area network, which means that the available communications capacity is shared between the nodes that are connected to the same media. Media access control (MAC) refers to the methods a network technology uses to determine when nodes can communicate on shared media and to deal with possible problems, such as two devices attempting to communicate simultaneously.

Ethernet uses a contention-based MAC system. Each network node connected to the same media is in the same collision domain. When two nodes transmit at the same time, the signals are said to collide and neither signal can reach its destination. This means that they must be re-sent, reducing available bandwidth.

The Ethernet protocol governing contention and media access is called Carrier Sense Multiple Access with Collision Detection (CSMA/CD). A collision is the state when a signal is present on an interface’s transmit and receive lines simultaneously. On detecting a collision, the node broadcasts a jam signal. Each node that was attempting to use the media then waits for a random period (backoff) before attempting to transmit again.


The collision detection mechanism means that only half-duplex transmission is possible. This means that a node can transmit or receive, but it cannot do both at the same time.

100BASE-TX Fast Ethernet Standard

The Fast Ethernet standard uses the same CSMA/CD protocol as 10BASE-T but with higher frequency signaling and improved encoding methods raising the bit rate from 10 Mbps to 100 Mbps. 100BASE-TX refers to Fast Ethernet working over Cat 5 (or better) twisted pair copper cable with a maximum supported link length of 100 meters (328 feet).

To support compatibility with hosts still equipped with 10 Mbps Ethernet interfaces, Fast Ethernet introduced an auto negotiation protocol to allow a host to choose the highest supported connection parameters (10 or 100 Mbps and half or full duplex). 10BASE-T Ethernet specifies that a node should transmit regular electrical pulses when it is not transmitting data to confirm the viability of the link. Fast Ethernet codes a 16-bit data packet into this signal advertising its service capabilities. This is called a Fast Link Pulse. A node that does not support auto negotiation can be detected by one that does and send ordinary link integrity test signals, or Normal Link Pulses.

Gigabit Ethernet Standards

Gigabit Ethernet builds on the standards defined for Ethernet and Fast Ethernet to implement rates of 1000 Mbps (1 Gbps). Over copper wire, Gigabit Ethernet is specified as 1000BASE-T, working over Cat 5e or better. Gigabit Ethernet does not support hubs; it is implemented only using switches. The maximum distance of 100 m (328 feet) applies to cabling between the node and a switch port, or between two switch ports.

10 Gigabit Ethernet (10GbE) multiplies the nominal speed of Gigabit Ethernet by a factor of 10. Because of the higher frequencies required, 10 GbE can only run at reduced distances over unshielded twisted pairs. Longer runs require higher categories of cable with some type of shielding

Topic 2B: Summarize Copper Cabling Types

Unshielded Twisted Pair Cable Considerations

Twisted pair is a type of copper cable that has been extensively used for telephone systems and data networks. One pair of insulated wires twisted together forms a balanced pair. The pair carry the same signal but with different polarity; one wire is positive, and the other is negative. This allows the receiver to distinguish the signal from any noise more strongly. The cable is completed with an insulating outer jacket.

Twisted pair can use either solid or stranded conductor wires. Solid cabling uses a single thick wire per conductor and is used for cables that run behind walls or through ducts. Stranded cabling uses thin filament wires wrapped around one another and is used to make flexible patch cords for connecting computers to wall ports and switch ports to patch panel ports. Copper wire thickness is measured using American Wire Gauge (AWG). Increasing AWG numbers represent thinner wire. Solid cable uses thicker 22 to 24 AWG, while the stranded cable used for patch cords is often 26 AWG. The attenuation of stranded wire is higher than solid wire, so it cannot be used over extended distances.

Shielded and Screened Twisted Pair Cable Considerations

Shielded cable is less susceptible to interference and crosstalk. This type of cable is required for some Ethernet standards and may also be a requirement in environments with high levels of interference.

Shielded cable can be referred to generically as shielded twisted pair (STP), but there are actually several types of shielding:

●	Screened cable has one thin outer foil shield around all pairs. Screened cable is usually designated as screened twisted pair (STP) or foiled/unshielded twisted pair (F/UTP), or sometimes just foiled twisted pair (FTP).

●	Fully shielded cabling has a braided outer screen and foil-shielded pairs and is referred to as shielded/foiled twisted pair (S/FTP). There are also variants with a foil outer shield (F/FTP).

Cat Cable Standards

The American National Standards Institute (ANSI) and the Telecommunications Industry Association (TIA)/Electronic Industries Alliance (EIA) have created categories of cable standards for twisted pairs to simplify selection of a suitable quality cable. These categories, along with other aspects of telecommunications wiring best practices, are defined in the ANSI/TIA/EIA 568 Commercial Building Telecommunications Cabling Standards ( tiaonline.org/standard/tia-568 ). Similar standards are also maintained by the ISO (ISO/IEC 11801), which refers to categories of components and classes of permanent links (incorporating both cable and termination).

●	Cat/Class: 3

○	Cable Type: UTP

○	Network Application: 10BASE-T

○	Max Distance: 100m (328ft)

○	Frequency: 16 MHz

○	Connector: RJ-45

●	Cat/Class: 5

○	Cable Type: UTP

○	Network Application: 100BASE-TX

○	Max Distance: 100m (328ft)

○	Frequency: 100 MHz

○	Connector: RJ-45

●	Cat/Class: 5e (Class D)

○	Cable Type: UTP or F/UTP

○	Network Application: 1000BASE-T

○	Max Distance: 100m (328ft)

○	Frequency: 100 MHz

○	Connector: RJ-45

●	Cat/Class: 6 (Class E)

○	Cable Type: UTP, F/UTP, or U/FTP

○	Network Application: 1000BASE-T, 10GBASE-T

○	Max Distance: 100m (328ft), 55m (180ft)

○	Frequency: 250 MHz

○	Connector: RJ-45

●	Cat/Class: 6a (Class Ea)

○	Cable Type: UTP, F/UTP, U/FTP, or S/FTP

○	Network Application: 10GBASE-T

○	Max Distance: 100m (328ft)

○	Frequency: 500 MHz

○	Connector: RJ-45

●	Cat/Class: 7 (Class F)

○	Cable Type: S/FTP or F/FTP

○	Network Application: 10GBASE-Tv

○	Max Distance: 100m (328ft)

○	Frequency: 600 MHz

○	Connector: GG45/TERA

●	Cat/Class: 8/8.1 (Class I)

○	Cable Type: U/FTP or F/UTP

○	Network Application: 40GBASE-T

○	Max Distance: 30m (100ft)

○	Frequency: 2000 MHz

○	Connector: RJ-45

●	Cat/Class: 8.2

○	Cable Type: F/FTP or S/FTP

○	Network Application: 40GBASE-T

○	Max Distance: 30m (100ft)

○	Frequency: 2000 MHz

○	Connector: GG45/TERA

Here are some details about the categories used for network media:

●	Cat 5 cable is no longer available. Cat 5e is tested at frequencies up to 100 MHz (like Cat 5 was) but to higher overall specifications for attenuation and crosstalk, meaning that the cable is rated to handle Gigabit Ethernet throughput. Cat 5e would still be an acceptable choice for providing network links for workstations.

For 1000BASE-T, Cat 5 is also acceptable (if properly installed), but Cat 5 cable is no longer available commercially. Unlike Ethernet and Fast Ethernet, Gigabit Ethernet uses all four pairs for transmission and is thus more sensitive to crosstalk between the wire pairs.

●	Cat 6 can support 10 Gbps but over shorter distances-nominally 55 m, but often less if cables are closely bundled together.

●	Cat 6A is an improved specification cable that can support 10 Gbps over 100 m. Cat 6A cable is bulkier than Cat 5e, and the installation requirements are more stringent, so fitting it within pathways designed for older cable can be problematic. TIA/EIA standards recommend Cat 6A is recommended for use in health care facilities, with Power over Ethernet (PoE) 802.3bt installations, and for horizontal connections to wireless access points.

●	Cat 7 cable is always of a screened/shielded type and is rated for 10GbE applications up to 100 m (328 feet). Cat 7 is not recognized by TIA/EIA but appears in the cabling standards created by the ISO (ISO/IEC 11801). It must be terminated with GG45 or TERA connectors rather than standard RJ-45 connectors.

Cabling is not the only part of the wiring system that must be rated to the appropriate category. For faster network applications (Gigabit Ethernet and better), the performance of connectors becomes increasingly critical. For example, if you are installing Cat 6A wiring, you must also install Cat 6A patch panels, wall plates, and connectors.

●	Cat 8 is intended for use in data centers only for short patch cable runs that make top-of-rack connections between adjacent appliances. ISO defines two variants; 8.1 (Class I) is equivalent to TIA/EIA Cat 8 and uses RJ-45 connectors while 8.2 (Class II) must use outer shielding or screening and GG-45 or TERA connectors.

COPPER TERMINATION STANDARDS

Each conductor in a 4-pair data cable is color-coded. Each pair is assigned a color (Blue, Orange, Green, or Brown). The first conductor in each pair has a predominantly white insulator with strips of the color; the second conductor has an insulator with the solid color. The ANSI/TIA/EIA 568 standard defines two methods for terminating Ethernet connectors: T568A and T568B. The wiring for both standards is shown in the following figure.

T568A and T568B wiring diagrams. (Images © 123RF.com.)

In T568A, the green pairs are wired to pins 1 and 2 and the orange pairs are wired to pins 3 and 6. In T568B, these pairs swap places, so orange is terminated to pins 1 and 2 and green to 3 and 6. Organizations should try to avoid using a mixture of the two standards. T568A is mandated by the US government and by the residential cabling standard (TIA 570), but T568B is probably the more widely deployed of the two.


Pin	Wire Color (T568A)	Wire Color (T568B)	10/100 Mbps	1/10/40 Gbps

1. `	`Green/White	Orange/White	Tx+	BixA+
1. `	`Green	Orange	Tx-	BixA-
1. `	`Orange/White	Green/White	Rx+	BixB+
1. `	`Blue	Blue		BixB-
1. `	`Blue/White	Blue/White		BixC+
1. `	`Orange	Green	Rx-	BixC-
1. `	`Brown/White	Brown/White		BixD+
1. `	`Brown	Brown		BixD-

Cat 7 and Cat 8 are so sensitive to noise that the secondary wire in each pair is solid white with no stripe, as the coloring process reduces the effectiveness of the insulation.



Topic 2C: Summarize Fiber Optic Cabling Types

Fiber Optic Cable Considerations

Fiber optic signaling uses pulses of infrared light, which are not susceptible to interference, cannot be easily intercepted, and suffer less from attenuation. Consequently, fiber optic cabling supports higher bandwidth over longer cable runs (that can be measured in kilometers, rather than meters).

A single optical fiber is constructed from three elements:

●	Core provides the transmission path for the light signals (waveguide).

●	Cladding reflects signals back into the waveguide as efficiently as possible so that the light signal travels along the waveguide by multiple internal reflections. The core and cladding can be made from glass or plastic. The cladding is applied as a thin layer surrounding the core. While made of the same material, the cladding has a different refractive index to the core. The effect of this is to create a boundary that causes the light to bounce back into the core, facilitating the process of total internal reflection that guides the light signal through the core.

●	Buffer is a protective plastic coating. It may be of a tight or loose configuration, with the loose format using some form of lubricant between the strand and the sheath.

In basic operation modes, each fiber optic strand can only transfer light in a single direction at a time. Therefore, multiple fibers are often bundled within a cable to allow simultaneous transmission and reception of signals or to provide links for multiple applications.

Single Mode Fiber and Multimode Fiber

Fiber optic cables fall into two broad categories: single mode and multimode.

●	Single Mode Fiber (SMF): Has a small core (8 to 10 microns) and a long wavelength, near infrared (1310 nm or 1550 nm) light signal, generated by a laser. Single mode cables support data rates up to 100 Gbps and cable runs of many kilometers, depending on the quality of the cable and optics. There are two grades of SMF cable; OS1 is designed for indoor use, while OS2 is for outdoor deployment.

●	Multimode Fiber (MMF): Has a larger core (62.5 or 50 microns) and shorter wavelength light (850 nm or 1300 nm) transmitted in multiple waves of varying length. MMF uses less expensive optics and consequently is less expensive to deploy than SMF. However, it does not support such high signaling speeds or long distances as single mode and so is more suitable for LANs than WANs.

\*\*Optical transceivers for SMF are now only slightly more expensive than ones for MMF. Consequently, SMF is often used for short range applications in data centers, as well as for long distance links. SMF still comes at a slight price premium, but provides better support for 40 Gbps and 100 Gbps Ethernet standards.

MMF is graded by Optical Multimode (OM) categories, defined in the ISO/IEC 11801 standard:

●	OM1/OM2: 62.5-micron cable is OM1, while early 50-micron cable is OM2. OM1 and OM2 are mainly rated for applications up to 1 Gbps and use LED transmitters.

●	OM3/OM4: These are also 50-micron cable, but manufactured differently, designed for use with 850 nm Vertical-Cavity Surface-Emitting Lasers (VCSEL), also referred to as laser optimized MMF (LOMMF). A VCSEL is not as powerful as the solid-state lasers used for SMF, but it supports higher modulation (transmitting light pulses rapidly) than LED-based optics.

Fiber Optic Connector Types

Straight Tip: An early bayonet-style connector that uses a push-and-twist locking mechanism. ST was used mostly for multimode networks, but it is not widely used for Ethernet installations anymore.

Subscriber connector: SC is a push-pull design, allowing for simple insertion and removal. It can be used for single or multimode. It is commonly used for Gigabit Ethernet.

Local connector: LC is a small-form-factor connector with a tabbed push-pull design. LC is similar to SC, but the smaller size allows for higher port density. LC is a widely adopted form factor for Gigabit Ethernet and 10/40 GbE.

Mechanical Transfer Registered Jack: MTRJ is a small-form-factor duplex connector with a snap-in design used for multimode networks.

FIBER ETHERNET STANDARDS

Ethernet standards over fiber set out the use of different types of cable for 100 Mbps, 1 Gbps, and 10 Gbps operation. There are variants for long wavelength optics, required for long distance transmission, and short wavelength optics.

●	Specification: 100BASE-FX

○	Optics: 1300nm

○	Cable: MMF (OM1), MMF (OM2)

○	Maximum Distance: 2km (1.2 miles)

○	Connectors: ST, SC, MT-RJ

●	Specification: 100BASE-SX

○	Optics: 850nm

○	Cable: MMF (OM1), MMF (OM2)

○	Maximum Distance: 550m (1804ft)

○	Connectors: ST, SC, LC

●	Specification: 1000BASE-SX

○	Optics: 850nm

○	Cable: MMF (OM1), MMF (OM2):MMF (OM3)

○	Maximum Distance: 275m (902ft), 550m (1804ft)

○	Connectors: ST, SC, LC, MT-RJ

●	Specification: 1000BASE-LX

○	Optics: 1300nm, 1310nm

○	Cable: MMF (OM1):MMF (OM2): MMF (OM3), SMF (OS1/OS2)

○	Maximum Distance: 550m (1804ft), 5km (3.1 miles)

○	Connectors: SC, LC

●	Specification: 10GBASE-SR

○	Optics: 850nm

○	Cable: MMF (OM1), MMF (OM2), MMF (OM3), MMF (OM4)

○	Maximum Distance: 33m (108ft), 82m (269 ft), 300m (984 ft), 400m (1312ft)

○	Connectors: SC, LC

●	Specification: 10GBASE-LR

○	Optics: 1310nm

○	Cable: SMF (OS1/OS2)

○	Maximum Distance: 10km (6.2 miles)

○	Connectors: SC, LC

Fiber is often used for backbone cabling in office networks and for workstations with high bandwidth requirements, such as video editing. The principal applications of 10 GbE (and better) are:

●	Increasing bandwidth for server interconnections and network backbones, especially in datacenters and for storage area networks (SAN).

●	Replacing existing switched public data networks based on proprietary technologies with simpler Ethernet switches (Metro Ethernet).

Fiber Optic Cable Installation

Fiber optic can be installed in the same topology as copper cable using distribution frames and switches. Long distance cables are typically laid as trunks or rings with repeaters or amplifiers between cable segments to strengthen the signal.

Normally, strands are installed in pairs (duplex) at each device, with one strand for transmit (Tx) and one strand for receive (Rx).

Patch cables for fiber optic can come with the same connector on each end (LC-LC, for instance) or a mix of connectors (LC-SC, for instance.) Duplex patch cords must maintain the correct polarity, so that the Tx port on the transmitters is linked to the Rx port on the receiver and vice versa. The TIA/EIA cabling standard sets out A to B patch cord to port orientations. Each element in the link must perform a crossover, and there must be an odd number of elements, such as two patch cords and a permanent link (three elements).


Most connectors are keyed to prevent incorrect insertion, but if in doubt, an optical power meter can be used to determine whether an optical signal is being received from a particular fiber.

\*\*Transmitted optical signals are visible as bright white spots when viewed through a smartphone camera. This can be used to identify which adapter on an optical interface is transmitting and which fiber patch cord is receiving a signal from the other end of the cable.

Finishing Type

The core of a fiber optic connector is a ceramic or plastic ferrule that holds the glass strand and ensures continuous reception of the light signals. The tip of the ferrule can be finished in one of three formats:

●	Physical contact (PC): The faces of the connector and fiber tip are polished so that they curve slightly and fit together better, reducing return loss (interference caused by light reflecting back down the fiber).

●	UltraPhysical Contact (UPC): This means the cable and connector are polished to a higher standard than with PC.

●	Angled Physical Contact (APC): The faces are angled for an even tighter connection and better return loss performance. APC cannot be mixed with PC or UPC. These connectors are usually deployed when the fiber is being used to carry analog signaling, as in Cable Access TV (CATV) networks. They are also increasingly used for long distance transmissions and for Passive Optical Networks (PON), such as those used to implement Fiber to the x (FTTx) multiple subscriber networks.

Where there are multiple strands within a single cable, the strands are color-coded (TIA/EIA 598) to differentiate them. Also, by convention, cable jackets and connectors use the following color-coding:

●	OM1

○	Jacket Color: Orange

○	Connector Color: Beige

●	OM2

○	Jacket Color: Orange

○	Connector Color: Black

●	OM3/OM4

○	Jacket Color: Aqua

○	Connector Color: Aqua

●	SMF PC/UPC

○	Jacket Color: Yellow

○	Connector Color: Blue

●	SMF APC

○	Jacket Color: Yellow

○	Connector Color: Green


Topic 2D: Deploy Ethernet Cabling

Structured Cabling System

Cabled networking for client access in an office building will use a structured cabling scheme, such as that set out in the ANSI/TIA/EIA 568 Commercial Building Telecommunications Wiring Standard. ANSI/TIA/EIA 568 identifies the following subsystems within a structured cabling system:

●	Work Area: The space where user equipment is located and connected to the network, usually via a wall port.

●	Horizontal Cabling: Connects user work areas to the nearest horizontal cross-connect. A cross-connect can also be referred to as a distribution frame. Horizontal cabling is so-called because it typically consists of the cabling for a single floor and so is made up of cables run horizontally through wall ducts or ceiling spaces.


●	

●	Backbone Cabling: Connects horizontal cross-connects (HCCs) to the main cross-connect (optionally via intermediate cross-connects). These can also be described as vertical cross-connects, because backbone cabling is more likely to run up and down between floors.

●	Telecommunications Room: Houses horizontal cross-connects. Essentially this is a termination point for the horizontal cabling along with a connection to backbone cabling. An equipment room is similar to a telecommunications room but contains the main or intermediate cross-connects. Equipment rooms are also likely to house “complex” equipment, such as switches, routers, and modems.

●	Entrance Facilities/Demarc: Special types of equipment rooms marking the point at which external cabling (outside plant) is joined to internal (premises) cabling. These are required to join the access provider’s network and for inter-building communications. The demarcation point is where the access provider’s network terminates and the organization’s network begins.

Cable Management

Cable management techniques and tools ensure that cabling is reliable and easy to maintain. Copper wiring is terminated using a distribution frame or punch down block. A punch down block comprises a large number of insulation-displacement connection (IDC) terminals. The IDC contains contacts that cut the insulation from a wire and holds it in place.

●	66 Block: An older-syle distribution frame used to terminate telephone cabling and legacy data applications (pre-Cat 5). A 66 block comprises 50 roots of 4 IDC terminals. The 25-pair cable from the access provider is terminated on one side of the block. On the other side of the block, the terminals terminate the wiring from the PBX. A jumper (bridging clip) is installed over the middle two terminals to complete the connection.

●	110 Block: The 110 block (developed by AT&T) is a type of distribution frame supporting 100 MHz operation (Cat5 ) and better. A 110 wiring block is arranged horizontally rather than vertically, offering better density than a 66 block. There is also more space for labeling the connectors and each column of connectors is color-coded, making management simpler. The incoming wire pairs are fed into channels on the wiring block, then a connector block or wafer is installed to terminate the incoming wiring. Outgoing wiring pairs are then punched into the terminals on the connector blocks to complete the circuit.

●	BIX and Krone Distribution Frames: Where a 110 block uses a two-piece design where wafer blocks are installed over the main block, competing formats BIX and Krone use a single module. The IDCs are angled differently in each format, requiring a different termination blade to be used to ensure a reliable connection.

●	Patch Panel/Patch Bay: In data networks, numerous moves, adds, and changes (MACs) would require reterminating the wiring. To simplify MACs, a patch panel or patch bay is a type of distribution block with IDCs on one side and pre-terminated RJ-45 modular ports on the other. This allows incoming and outgoing connections to be reconfigured by changing the patch cable connections, which is much simpler than reterminating punch down blocks.


Fiber distribution Panels and Fusion Splicing

Permanent cables are run through conduit to wall ports at the client access end and a fiber distribution panel at the switch end. Fiber patch cables are used to complete the link from the wall port to the NIC and from the patch panel to the switch port.

Using connectors does reduce the overall performance of the cable. Each connector will “cost” a certain amount of insertion loss (typically budgeted as 0.5 dB) and reflection loss. Consequently, in some circumstances it may be preferable to splice two cables together, either to repair damage or to extend the cable run. Cables can be spliced mechanically using an adhesive junction box containing index matching fluid that ensures a continuous path between the two fiber strands. A fusion splicer achieves a more permanent join with the lower insertion loss (>=0.1 dB). Thus a fusion splicing machine performs a precise alignment between the two strands and then permanently joins them together using an arc weld. A fusion splicer is a high-precision instrument and must be kept clean and maintained following the manufacturer’s guidelines.

Splicing may also be used to attach a pigtail (a segment of cable with a factory-fitted connector at one end only) or to field terminate to a connector (splicing a factory-prepared SC or LC connector to an incoming cable). A spliced cable or pigtail must be protected with a special cover and supported by a splice tray. Connectors for field terminated splicing do not require a tray and the protective cover is built into the connector.

Transceivers

A network might involve the use of multiple types of cabling. When this occurs, switch and router equipment must be able to terminate different cable and connector types, and devices must convert from one media type to another. Enterprise switches and routers are available with modular, hot-swappable transceivers/media converters for different types of fiber optic patch cord connections.

SFP/SFP+(mini-GBIC)

Small form factor pluggable (SFP) uses LC connectors and is also designed for Gigabit Ethernet. Enhanced SFP (SFP+) is an updated specification to support 10 GbE but still uses the LC form factor. There are different modules to support the various Ethernet standards and fiber mode type (10GBASE-SR versus 10GBASE-LR, for instance). Consequently, a transceiver is designed to support a specific wavelength The transceivers must be installed as matched pairs.

\*\*You will often see the term MSA in conjunction with modular transceivers. Multi-Source Agreement (MSA) is intended to ensure that a transceiver from one vendor is compatible with the switch/router module of another vendor.

QSFP/QSFP+

Quad small form-factor pluggable (QSFP) is a transceiver form factor that supports 4 x 1 Gbps links, typically aggregated to a single 4 Gbps channel. Enhanced quad small form-factor pluggable (QSFP+) is designed to support 40 GbE by provisioning 4 x 10 Gbps links. QSFP+ is typically used with parallel fiber and multi-fiber push-on (MPO) termination. An MPO backbone ribbon cable bundles 12 or more strands with a single compact terminator (the cables are all manufactured and cannot be field terminated). When used with QSFP+, four strands transmit a full-duplex 40 Gbps link, four strands receive, and the other four strands are unused.

QSFP+ can also be used with Wavelength Division Multiplexing (WDM) Ethernet standards.

Wavelength Division Multiplexing

Ordinary (or “grey”) SFP/SFP+ are duplex interfaces with one transmit port and one receive port that require two fiber strands. Each strand is a single channel. Wavelength Division Multiplexing (WDM) is a means of using a strand to transmit and/or receive more than one channel at a time.

●	BiDirectional Wavelength Division Multiplexing: BiDi transceivers support transmit and receive signals over the same strand of fiber. This uses WDM to transmit the Tx and Rx signals over slightly shifted wavelengths, such as 1310 nm for Tx and 1490 for Rx. BiDi transceivers must be installed in opposite pairs, so the downstream transceiver would have to use 1490 nm for Tx and 1310 for Rx. Bidirectional wavelength division multiplexing (WDM) links are documented in Ethernet standards (1000BASE-BX and 10GBASE-BX).

●	Coarse and Dense Wavelength Division Multiplexing: Coarse Wavelength Division Multiplexing (CWDM) supports up to 16 wavelengths and is typically used to deploy four or eight bidirectional channels over a single fiber strand. Dense Wavelength Division Multiplexing (DWDM) provisions greater numbers of channels (20, 40, 80, or 160). This means that there is much less spacing between each channel and requires more precise and expensive lasers. CWDM and DWDM transceivers support multi-channel 1 G, 10 G, and 40 G Ethernet links. As with BiDi, the transceivers must be installed in opposite pairs for each channel.

In a point-to-point WDM topology, each transceiver is cabled to a multiplexer/demultiplexer (mux/demux). The single fiber strand is run to a mux/demux at the other site. Alternatively, devices called optical add/drop multiplexers (OADM) can insert and remove signals for a particular wavelength channel on a ring topology.







Lesson 3: Deploying Ethernet Switching

Topic 3A: Deploy Networking Devices

Repeaters and Media Converters

The attenuation of signals passing over copper or fiber cable imposes a distance limitation on links. A link where the cable length exceeds the distance limitation may not achieve the required speed or may be unreliable. A repeater overcomes the distance limitation by boosting the signal at some point along the cable run. A repeater works at the physical layer of the OSI model and is transparent with regard to the rest of the network infrastructure (the link is treated as one length of cable). A repeater is always powered and represents a single point of failure for the link. Repeaters are available for both copper and fiber links, with the latter also described as an optical-electrical-optical (OEO) repeater.

Where a repeater connects two cable segments of the same type, a media converter is used to transition from one cable type to another. Media converters also work at the Physical layer of the OSI model. They may be supplied as standalone appliances or rack-mounted appliances. The following media conversions are typical:

●	Single mode fiber to twisted pair: These powered converters change light signals from SMF cabling into electrical signals carried over a copper wire Ethernet network (and vice versa).

●	Multimode fiber to twisted pair: A different media converter model is required to convert the signals carried of MMF media.

●	Single mode to multimode fiber: These passive (unpowered) devices convert between the two fiber cabling types.

Hubs

Most Ethernet networks are implemented so that each end system node is wired to a central intermediate system. In early types of Ethernet, this function was performed by a hub.

A hub acts like a multiport repeater so that every port receives transmissions sent from any other port. As a repeater, the hub works only at the Physical layer. Electrically, the network segment still looks like a single length of cable. Consequently, every hub port is part of the same shared media access area and within the same collision domain. All node interfaces are half-duplex, using the CSMA/CD protocol, and the media bandwidth (10 Mbps or 100 Mbps) is shared between all nodes.

The end system interface is referred to as medium dependent interface (MDI); the interface on the hub is referred to as MDI crossover (MDI-X). This means that the transmit (Tx) wires on the host connect to receive (Rx) wires on the hub.



There are no configuration options for a hub. You just connect the device to a power source and then connect the network cables for the hosts that are going to be part of the network segment served by the hub.

Bridges

An Ethernet bridge works at the data link layer to establish separate physical network segments while keeping all nodes in the same logical network. This reduces the number of collisions caused by having too many nodes contending for access.



Each hub is a shared access media area. The nodes connected to the hubs shared the available bandwidth-a 100 Mbps Ethernet for domain A and a 10 Mbps Ethernet for domain B- because only one node within each collision domain can communicate at any one time. The bridge isolates these segments from each other, so nodes in domain B do not slow down or contend with nodes in domain A. The bridge does allow nodes to communicate with the other collision domain, by forwarding only the appropriate traffic. This creates a single logical network, referred to as a layer 2 broadcast domain.



If no record of the hardware address exists or the frame is a broadcast or multicast, then the bridge floods the frame to all segments except for the source segment (acting like a hub).

Layer 2 Switches

An Ethernet layer 2 switch performs the same sort of function as a bridge, but in a more granular way and for many more ports than are supported by bridges. Each switch port is a separate collision domain. In effect, the switch establishes a point-to-point link between any two network nodes. This is referred to as microsegmentation.


Because each port is in a separate collision domain, collisions can occur only if the port is operating in half-duplex mode. This would only be the case if a legacy network card or a hub is attached to it. Even then, collisions affect only the microsegment between the port and the connected interface; they do not slow down the whole network. As with a bridge, though, traffic on all switch ports is in the same broadcast domain, unless the switch is configured to use virtual LANs (VLANs).

\*\*The WAN firewall that protects the network from malicious traffic is the device or appliance closest to the edge facing the wide-area network. Next is either a Layer 2 switch or an integrated or advanced services router. While a Layer 3 capable router may seem like a good idea for this role, they are not typically equipped with WAN interfaces and thus not usually deployed as edge routers. The firewall and the Layer 2 edge switch form the core layer of the three-tiered hierarchy.

The distribution layer mainly consists of (in this case, two) Ethernet-only Layer 3 switches that provide fault-tolerant interconnections between all access blocks and the core (WAN-facing) layer. These switches also maintain the logical separation of VLANs.

Finally, there are two access blocks in the access layer. An advanced services router best services the high-speed network since separate VLANs in the high-speed access block will use Ethernet and Wi-Fi. On the other hand, the legacy block will need a media converter to make the legacy twisted pair copper wiring compatible with the newer fiber optic cabling. Then a legacy Layer 2 bridge is used to physically separate network segments, each of which is to be serviced by its own legacy hub.\*\*

Topic 3B: Explain Network Interfaces

A network interface is the means by which a node is connected to the media and exchanges data with other network hosts.

Network Interface Cards

The transceiver component responsible for physically connecting the node to the transmission medium is implemented in a network interface card/controller (NIC). Most Ethernet adapters designed for use with copper cabling are capable of 10/100/1000 operation, meaning that they support Gigabit Ethernet, Fast Ethernet, and 10BASE-T. A different kind of adapter would have to be provisioned for a fiber link.

Each Ethernet network interface port has a unique hardware address known as the Media Access Control (MAC) address. This may also be referred to as the Ethernet address (EA) or, in IEEE terminology, as the extended unique identifier (EUI). A MAC address is also referred to as a local or physical address.

Ethernet Frame Format

Ethernet encapsulates the payload from higher layer protocols within a protocol data unit (PDU) called a frame. The basic format of an Ethernet frame and Ethernet headers is shown in the following figure:

Preamble: The preamble and Start Frame Delimiter (SFD) are used for clock synchronization and as part of the CSMA/CD protocol to identify collisions early. The preamble consists of 8 bytes of alternating 1s and 0s with the SFD being two consecutive 1s at the end. This is not technically considered to be part of the frame.

Error Checking: The error checking field contains a 32-bit (4-byte) checksum called a Cyclic Redundancy Check (CRC) or Frame Check Sequence (FCS). The CRC is calculated based on the contents of the frame; the receiving node performs the same calculation and, if it matches, accepts the frame. There is no mechanism for retransmission if damage is detected nor is the CRC completely accurate at detecting damage; these are functions of error checking in protocols operating at higher layers.

Media Access Control Address Format

A MAC/EUI address is a 48 bit (6 byte) identifier. The format of the numbers differs depending on the system architecture. It is often displayed as 6 groups of 2 hexadecimal digits with colon or hyphen separators or no separators at all or as 3 groups of 4 hex digits with period separators.

Burned-in Addresses

The IEEE gives each card manufacturer a range of numbers, and the manufacturer hard codes every interface produced with a unique number from their range. This is called the burned-in address or the universal address. The first six hex digits (3 bytes or octets), also known as the Organizationally Unique Identifier (OUI), identify the manufacturer of the adapter. The last six digits are a serial number.

A locally administered address is defined by changing the U/L bit from 0 to 1. The rest of the address is configured using the card driver or network management software. It becomes the network administrator’s responsibility to ensure that all interfaces are configured with a unique MAC.

Broadcast Address

The I/G bit of a MAC address determines whether the frame is addressed to an individual node (0) or a group (1). The latter is used for broadcast and multicast transmissions. A MAC address consisting entirely of 1s is the broadcast address (ff:ff:ff:ff:ff:ff) and should be processed by all nodes within the same broadcast domain.

Frame Length and Maximum Transmission Unit

The official IEEE 802.3 standard defines a 2-byte field to specify the size of the data field or payload. The payload can normally be between 46 and 1500 bytes. The upper limit of the payload is also referred to as the maximum transmission unit (MTU). However, most Ethernet products follow the original DIX specification, referred to as Type II frames, and use the field to indicate the type of network layer protocol contained in the frame-IPv4 or IPv6, for instance. These EtherTypes are values of 1536 or greater; anything less than that is interpreted as the data length.

To comply with CSMA/CD, the minimum length of an Ethernet frame is 64 bytes, so the payload must be at least 46 bytes. If this is not the case, it is automatically padded with redundant data. The Maximum size of an Ethernet frame is normally 1518 bytes, excluding the preamble. Some Gigabit and 10 GbE Ethernet products support jumbo frames with much larger MTUs. Such products are not standardized, however, making interoperability between different vendors problematic.

Packet Sniffers and Taps

One of the most important tools used for network support is a protocol analyzer. This is the tool that allows inspection of traffic received by a host or passing over a network link. A protocol analyzer depends on a packet sniffer. A sniffer captures frames moving over the network medium.

There are three main options for connecting a sniffer to the appropriate point in the network:

●	SPAN (switched port analyzer)/mirror port: This means that the sensor is attached to a specially configured port on the switch that receives copies of frames addressed to nominated access ports (or all the other ports). This method is not completely reliable. Frames with errors will not be mirrored and frames may be dropped under heavy load.

●	Passive test access point (TAP): This is a box with ports for incoming and outgoing network cabling and an inductor or optical splitter that physically copies the signal from the cabling to a monitor port. There are types for copper and fiber optic cabling. Unlike a SPAN, no logic decisions are made so the monitor port receives every frame-corrupt or malformed or not- and the copying is unaffected by load.

●	Active TAP: This is a powered device that performs signal regeneration (again, there are copper and fiber variants), which may be necessary in some circumstances. Gigabit signaling over copper wire is too complex for a passive TAP to monitor and some types of fiber links may be adversely affected by optical splitting. Because it performs an active function, the TAP becomes a point of failure for the links in the event of power loss.

A TAP will usually output two streams to monitor a full-duplex link (one channel for upstream and one for downstream). Alternatively, there are aggregation TAPs, which rebuild the streams into a single channel, but these can drop frames under very heavy load.






TCPDUMP

tcpdump is a command-line packet capture utility for Linux, providing a user interface to the libpcap library. The basic syntax of the command is:

tcpdump -i eth0

Where eth0 is the interface to listen on (you can substitute with the keyword any to listen on all interfaces of a multi-homed host). The utility will then display captured packets until halted manually (by pressing Ctrl + C). The operation of the basic command can be modified by switches. For example, the -w and -r switches write output to a file and read the contents of a capture file respectively. The -v, -vv, and -vvv can be used to increase the amount of detail shown about each frame while the -e switch shows the Ethernet header.

tcpdump is often used with some sort of filter expression:

●	Type: Filter by host, net, port, or port range.

●	Direction: filter by source (src) or destination (dst) parameters ( host, network, or port).

●	Protocol: filter by a named protocol rather than port number (for example, arp, icmp, ip, ip6, tcp, udp, and so on).

Filter expressions can be combined by using Boolean operators:

●	and: (-and-and-)

●	or: (||)

●	not: (!)

Filter syntax can be made even more detailed by using parentheses to group expressions. A complex filter expression should be enclosed by quotes.

\*\*Refer to tcpdump.org for the full help and usage examples. ngrep (github.com/jpr5/ngrep) is another useful packet capture and analysis tool. As well as the standard filter syntax, it supports use of regular expressions (regexr.com) to search and filter capture output. You can also use the netcat tool (nmap.org/ncat) to copy network traffic from one host to another for analysis.





Wireshark

Wireshark (wireshark.org) is an open source graphical packet capture and analysis utility, with installer packages for most operating systems. Having chosen the interfaces to listen on, the output is displayed on a three-pane view, with the top pane showing each frame, the middle pane showing the fields from the currently selected frame, and the bottom pane showing the raw data from the frame in hex and ASCII.

\*\*There is also a command-line version of Wireshark called Tshark: wireshark.org/docs/wsug\_html\_chunked/AppToolstshark.html\*\*

Topic 3C: Deploy Common Ethernet Switching Features

Ethernet Switch Types

The market is dominated by Cisco’s Catalyst and Nexus platforms (over 55% of sales), but other notable vendors include HP Enterprise, Huawei, Juniper, Arista, Linksys, D-Link, NETGEAR, and NEC.

Ethernet switches can be distinguished using the following general categories:

●	Unmanaged vs managed: On a SOHO network, switches are more likely to be unmanaged, standalone units that can be added to the network and run without any configuration. The switch functionality might also be built into an Internet router/modem. On a corporate network, switches are most likely to be managed. This means the switch settings can be configured. If a managed switch is left unconfigured, it functions the same as an unmanaged switch does.

●	Stackable: Switches that can be connected together and operate as a group. The switch stack can be managed as a single unit.

●	Modular vs fixed: A fixed switch comes with a set number of ports that cannot be changed or upgraded. A modular switch has slots for plug-in cards, meaning they can be configured with different numbers and types of ports.

●	Desktop vs rack-mounted: Simple unmanaged switches with five or eight ports might be supplied as small freestanding units that can be placed on a desktop. Most larger switches are designed to be fitted to the standard-size racks that are used to hold networking equipment.




Switch Interface Configuration

Configuration of a managed switch can be performed at a command line interface (CLI). Once you have established a connection to the switch’s management interface, you configure settings for each of the switch port interfaces. These settings control the network link configured for each client device attaching to the switch. Most switch operating systems work in multiple command modes or hierarchies. For example, Cisco IOS has three principal modes:

●	User EXEC mode: This is a read-only mode where commands can be used to report the configuration, show system status, or run basic troubleshooting tools.

●	Privileged EXEC mode/enable mode: This allows the user to reboot or shut down the appliance and to backup and restore the system configuration.

●	Global configuration mode: This allows the user to write configuration updates.

Most switch CLIs also support TAB and/or use of ? to list different ways to complete a partial instruction.

In user mode, a variety of show commands can be used to display the current configuration. There are usually many show commands, but two of particular importance are as follows:

●	show config displays the switch’s configuration. The startup configuration (show startup-config) could be different from the running configuration (show running-config). If there has been some undocumented change to the switch, using these commands and comparing the output may reveal the source of a problem.

●	show interface lists the state of all interfaces or the specified interface. Interfaces are identified by type, slot, and port number. An interface has a line status (up if a host is connected via a good cable) and a protocol status (up if an Ethernet link is established). Down indicates a fault while administratively down indicates that the port has been purposefully disabled. show interface will also report configuration details and traffic statistics if the link is up/up.

\*\*Stackable switches precede interface identifiers with a module ID. Note that this numbering does vary between manufacturers. Also, some start from zero and some from one.





Auto MDI/MDI-X

Under 100BASE-T, an end system uses media dependent interface (MDI) to transmit on pins 1 and 2 and receive on pins 3 and 6. This is also referred to as an uplink port. As an intermediate system, a switch port uses MDI-X and receives on pins 1 and 2 and transmits on pins 3 and 6. The cable between the host interface port and switch interface port should be straight through (either T568A on both ends or T568B on both ends).

A crossover cable has T568A termination at one end and T568B termination at the other end. Most switches are now configured to use auto-MDI/MDIX by default. This means that the switch senses the configuration of the connected device and cable wiring and ensures that an MDI uplink to an MDIX port gets configured. This will also ensure a link if a crossover cable is used to connect an end system by mistake.

MAC Address Table and Port Security

A switch learns MAC addresses by reading the source address when a frame is received on a port. The address mapping for that port is normally cached in a MAC address table. The address table is implemented as content addressable memory (CAM), a special type of memory optimized for searching, rather than random access. Consequently, the MAC address table is often also referred to as the CAM table. Entries remain in the MAC address table for a period before being flushed. This ensures problems are not encountered when network cards (MAC addresses) are changed.

If a MAC address cannot be found in the MAC address table, then the switch acts like a hub and transmits the frame out of all the ports, except for the source port. This is referred to as flooding.

You can query the MAC address table of a switch to find the MAC address or addresses associated with a particular port using a command such as:

show mac address-table

A port security configuration validates the MAC address of end systems that connect to a switch port. In most scenarios, you would not expect the MAC address of servers and workstations to change often, except for predictable upgrade cycles. Unknown or frequently changing host MAC addresses might indicate an intrusion attempt. A port security configuration has two elements:

●	Specify a static MAC address or allow the port to learn and accept a certain number of sticky addresses.

●	Specify an enforcement action when a policy violation is detected (alert only or shutdown the port, for instance).

Port Aggregation

Port aggregation means combining two or more separate cabled links into a single logical channel. From the host end, this can also be called NIC teaming. The term bonding is also widely substituted for aggregation.

Port aggregation is often implemented by the Link Aggregation Control Protocol (LACP). LACP can  be used to autonegotiate the bonded link between the switch ports and the end system, detect configuration errors, and recover from the failure of one of the physical links.

Port Mirroring

Unlike a hub, a switch forwards unicast traffic only to the specific port connected to the intended destination interface. This prevents sniffing of unicast traffic by hosts attached to the same switch. There are circumstances in which capturing and analyzing network traffic is a legitimate activity, however, and port mirroring provides the facility to do this. Port mirroring copies all packets sent to one or more source ports to a mirror (or destination) port. On a Cisco switch, this is referred to as a switched port analyzer (SPAN).

The mirror port would be used by management or monitoring software, such as a packet sniffer, network analyzer, or intrusion detection system (IDS) sensor. Either ingress or egress traffic, or both, can be captured. Optionally, in order to avoid overloading the monitoring system, packets may be filtered based on criteria such as protocol ID or TCP/UDP port number

Jumbo Frames and Flow Control

Ordinarily, an Ethernet frame can carry a data payload or maximum transmission unit (MTU) of up to 1,500 bytes. When you are transferring data around a storage network with a 10 Gbps switching fabric, a 1500-byte limit means using a lot of frames. A jumbo frame is one that supports a data payload of up to around 9,000 bytes. This reduces the number of frames that need to be transmitted, which can reduce the amount of processing that switches and routers need to do. It also reduces the bandwidth requirement somewhat, as fewer frame headers are being transmitted.

When implementing jumbo frames, it is critical that all hosts and appliances (switches and routers) along the communications path be able and configured to support them. It is also vital to ensure that each device supports the same MTU. Also, it can be complex to calculate the MTU if any additional headers are used (for IPSec, for instance).

The MTU value in the show interface output will indicate whether jumbo frames are accepted on a particular port.

IEEE 802.3x flow control allows a server to instruct the switch to pause traffic temporarily to avoid overwhelming its buffer and causing it to drop frames. A switch port can be configured to enable or disable (ignore) use of PAUSE frames. The 802.3x global PAUSE mechanism does not distinguish between traffic types, however, which can pose problems with voice/video traffic and infrastructure-critical traffic, such as routing protocol updates. Class of service (CoS) and quality of service (QoS) mechanisms ensure reliable performance for these time-sensitive applications by marking and policing traffic. The updated priority flow control (PFC) mechanism (IEEE802.1Qbb) allows PAUSE frames to apply to certain traffic classes only.

Power over Ethernet (PoE)

Power over Ethernet (PoE) is a means of supplying electrical power from a switch port over ordinary data cabling to a connected powered device (PD), such as a VoIP handset, IP camera, or wireless access point. PoE is defined in two IEEE standards (now both rolled into 802.3-2018):

●	802.3af-Powered devices can draw up to about 13 W over the link. Power is supplied as 350mA@48V and limited to 15.4 W, but the voltage drop over the maximum 100 feet of cable results in usable power of around 13 W.

●	802.3at (PoE+)-Powered devices can draw up to about 25 W, with a maximum current of 600 mA.

●	802.3bt (Ultra PoE)-Supplies up to about 51 W (Type 3) or 73 W (Type 4) usable power.

PoE switches are referred to as endspan (or endpoint) power sourcing equipment (PSE). If an existing switch does not support PoE, a device called a power injector (or midspan) can be used.

When a device is connected to a port on a PoE switch, the switch goes through a detection phase to determine whether the device is PoE-enabled. If not, it does not supply power over the port and, therefore, does not damage non-PoE devices. If so, it determines the device's power consumption and sets the supply voltage level appropriately.

Powering these devices through a switch is more efficient than using a wall-socket AC adapter for each appliance. It also allows network management software to control the devices and apply schemes, such as making unused devices go into sleep states and power capping.


























Lesson 4: Troubleshooting Ethernet Networks

Topic 4A: Explain Network Troubleshooting Methodology

Network Troubleshooting Methodology

●	Identify the problem:

○	Gather information

○	Duplicate the problem, if possible

○	Question users

○	Identify symptoms

○	Determine if anything has changed

○	Approach multiple problems individually

●	Establish a theory of probable cause:

○	Question the obvious

○	Consider multiple approaches

○	Top-to-bottom/bottom-to-top OSI model

○	Divide and conquer

●	Test the theory to determine cause:

○	Once theory is confirmed, determine next steps to resolve the problem.

○	If theory is not confirmed reestablish new theory or escalate

●	Establish a plan of action to resolve the problem

●	Implement the solution or escalate as necessary

●	Very full system functionality, and if applicable, implement preventive measures

●	Document findings, actions, and outcomes

Identify the Problem (Gather Information)

Gather Information

At the outset, define the score of the problem (the area affected). This is helpful in two ways. First, if it’s a single user, then it’s not as urgent as the other outstanding calls you have. But if it’s the whole third floor, then it’s more urgent. In addition, the fact that the problem affects a wider area means that it is unlikely to be a problem with one user’s workstation. Knowing the scope of the problem can help to identify its source and prioritize the issue in relation to other incidents.

Also:

●	Check the system documentation, such as installation or maintenance logs, for useful information.

●	Check recent job logs or consult any other technicians who might have worked on the system recently or might be working on some related issue.

●	Use vendor support sites (knowledge bases) and forums.

Identify Symptoms and Duplicate the Problem

Symptoms are facts and clues in the affected system that can be correlated with known causes and issues. To identify symptoms, complete the following tests:

●	Make a physical inspection; look for something out of the ordinary.

●	Check system logs or diagnostic software for information.

●	Duplicate the problem on the user’s system or a test system. You will need to try to follow the same steps as the user. Issues that are transitory or difficult to reproduce are often the hardest to troubleshoot.

Identify the Problem (Question Users)

Question Users

Questions are commonly divided into two types:

●	Open questions invite someone to explain in their own words. Open questions are good to start with, as they help to avoid making your own assumptions about what is wrong, and they encourage the user to give you all the information they can.

●	Closed questions invite a Yes/No answer or a fixed response. Closed questions can be used to drill down into the nature of the problem and guide a user toward giving you information that is useful.

Determine if Anything has Changed

There are two key questions to ask when trying to identify the cause of a problem:

●	Did it ever work? Did it work before x time, if so, what happened at x time. If the system never worked, then you are not looking for something that stopped working, but for something which was never working in the first place.

●	What has changed since it was last working? Check for documented changes using the system inventory, but if this does not reveal anything, look for undocumented changes in the local area of the incident.




Approach Multiple Problems Individually

If problems do not seem to be related, treat each issue as a separate case. If they seem to be related, check for outstanding support or maintenance tickets that might indicate existing problems.

Establish a Theory of Probably Cause

●	Question the obvious. Step through what should happen and identify the point at which there is a failure or error. This approach can quickly identify obvious oversights, such as a network cable not being plugged.

●	Methodically prove the functionality of each component in sequence. This approach is more time consuming but may be necessary for a difficult problem.

Top-to-bottom/Bottom-to-top OSI Model Approach

Methodical validation of network components can be approached by testing at each layer of the OSI model in sequence. There are many components which go to make up a network.



Some, or several, of these components may be at fault when a problem is reported to you. Unless a problem is trivial, break the troubleshooting process into compartments or categories, using the OSI model as a guide.

Divide and Conquer Approach

Rather than starting from the top or bottom of the OSI model, you start with the layer most likely to be causing the problem and then work either down or up depending on what your tests reveal.

Test the Theory to Determine the Cause

If you cannot prove the cause of the problem, you will either need to develop and test a new theory or decide to escalate the problem. Escalation means referring the problem to a senior technician, manager, or third party. You may need to escalate a problem for any of these reasons:

●	The problem is beyond your knowledge or ability to troubleshoot.

●	The problem falls under a system warranty and would be better dealt with by the supplier.

●	The score of the problem is very large and/or the solution requires some major reconfiguration of the network.

●	A customer becomes difficult or abusive or demands help on an unsupported item.

When you escalate a problem, you should have established the basic facts, such as the scope of the problem and its likely cause and be able to communicate these clearly to the person to whom you are referring the incident to.

If you can prove the cause of the problem, you can start to determine the next steps to resolve the problem.

Establish a Plan of Action

An action plan sets out the steps you will take to solve the problem. There are typically three solutions to any problem:

●	Repair: You need to determine whether the cost of repair/time taken to reconfigure something makes this the best option.

●	Replace: Often, this is more expensive and may be time-consuming if a part is not available There may also be an opportunity to upgrade the device or software.

●	Ignore: Not all problems are critical. If neither repair or replacement is cost-effective, it may be best to either find a workaround or just to document the issue and move on.

Another consideration is potential effects on the rest of the system.

Implement the Solution

If you are reverting to a known good configuration, you may be able to implement the solution directly. If the solution requires a change to the system or the network environment, you are likely to have to follow a change management plan.

If you do not have authorization to implement a solution, you will need to escalate the problem to more senior personnel. If applying the solution is disruptive to the wider network, you also need to consider the most appropriate time to schedule the reconfiguration work and plan how to notify other network users. When you change a system as part of implementing a solution, test after each change. If the change does not fix the problem, reverse it and then try something else. If you make a series of changes without recording what you have done, you could find yourself in a tricky position.

Verify Full System Functionality and Implement Preventive Measures

When you apply a solution, verify that it fixes the reported problem, and that the system as a whole continues to function normally. Identify the results and effects of the solution. Ensure that you were right and that the problem is resolved.

Before you can consider a problem closed, you should be satisfied in your own mind that you have resolved it and you should get the customer’s acceptance that it has been fixed. Restate what the problem was and how it was resolved, then confirm with the customer that the incident log can be closed.

To fully solve a problem, you should try to eliminate any factors that may cause the problem to recur.

Document Findings, Actions and Outcomes

When you complete a problem log remember that people other than you may come to rely on it. Also logs may be presented to customers as proof of troubleshooting activity. Write clearly and concisely checking for spelling and grammar errors.

Topic 4B: Troubleshoot Common Cable Connectivity Issues

Applying a layer-by-layer approach to network troubleshooting can greatly assist with isolating symptoms and causes.

Specification and Limitations

When troubleshooting a link, you will need to compare the expected performance with the actual current performance. To do this, you must understand how to assess and distinguish speed, throughput, and distance specifications and limitations.

Speed versus Throughput

At the physical layer, a signal transmitted over a communication channel consists of a series of events referred to as symbols. A symbol could be something like a pulse of higher voltage in an electrical current or the transition between the peak and the trough in an electromagnetic wave. The number of symbols that can be transmitted per second is called the baud rate. The baud rate is measured in hertz (or MHz or GHz).

At the data link layer, the nominal bit rate-or bandwidth- of the link is the amount of information that can be transmitted, measured in bits per second (bps), or some multiple thereof. In order to transmit information more efficiently, a signaling method might be capable of representing more than one bit per symbol. This also helps to overcome noise and detect errors. The use of these encoding methods means that the bit rate will be higher than the baud rate. In Ethernet terms, the speed is the expected performance of a link that has been properly installed to operate at 10 Mbps, 100 Mbps, 1 Gbps, or better.

The nominal bit rate will not often be achieved in practice. Throughput is an average data transfer rate achieved over a period of time excluding encoding schemes, errors, and other losses incurred at layer 1 and layer 2. Throughput can be adversely affected by link distance and by interference (noise).

\*\*Throughput is typically measured at the network or transport layer. Often the term goodput is used to measure an averaged data transfer rate at the application layer. This takes account of the effect of packet loss. Throughput is also sometimes measures as packets per second\*\*

Speed is measured as a unit of time-typically milliseconds (ms)- and is also referred to as latency, or delay. Latency can occur at many layers of the OSI Model. It is not usually a critical factor on local Ethernets, however.

\*\*The term speed is also used to describe how well or badly a link is performing in terms of throughput but do be aware of the distinction between bandwidth and latency.\*\*

Distance Limitations, Attenuation, and Noise

Each type of media can consistently support a given bit rate only over a defined distance. Some media types support higher bit rates over longer distances than others Attenuation and noise enforce distance limitations on different media types.

●	Attenuation is the loss of signal strength, expressed in decibels (dB). dB expresses the ratio between two measurements, in this case, signal strength at origin and signal strength at destination.

●	Noise is anything that gets transmitted within or close to the channel that isn’t the intended signal. This serves to make the signal itself difficult to distinguish, causing errors in data and forcing retransmissions. This is expressed as the signal to noise ratio (SNR).

Cable Issues

When troubleshooting cable connectivity you are focusing on issues at the physical layer. At layer one a typical Ethernet link for an office workstation includes the following components:

●	Network transceiver in the host (end system)

●	Patch cable between the host and a wall port

●	Structured cable between the wall port and a patch panel (the permanent link)

●	Patch cable between the patch panel port and a switch port

●	Network transceiver in the switch port (intermediate system)

The entire cable path (patch cords plus permanent link) is referred to as a channel link.

Loopback Plugs, Status Indicators and Interface Configuration

A network loopback adapter (or loopback plug) is a specially wired RJ-45 plug with a 6” stub of cable. The wiring pinout is pin 1 (Tx) to pin 3 (Rx) to pin 6 (Rx). This means that the packet sent by the NIC is received by itself. This is used to test for bad ports and network cards.

Another approach when you are troubleshooting a suspected cable problem is to check the link lights or network connection LED status indicators on the NIC at one end and the switch/router port at the other. You will need the vendor documentation to interpret the LEDs. There may be two LEDs for status and for link. On a switch port, the following LED link states are typical:

●	Solid green: The link is connected but there is no traffic.

●	Flickering green: The link is operating normally (with traffic).

●	No light: The link is not working or is disconnected at the other end.

●	Blinking amber: A fault has been detected (duplex mismatch or spanning tree blocking for instance)

●	Solid amber: The port is disabled.

Cable Testers

When troubleshooting a permanent link, you should verify that the cable type is appropriate to the application. You may also need to verify that unshielded cable has not been installed where shielded or screened cable would be more suitable.Check the identifier printed on the cable jacket to verify the type that has been used.

From a safety point of view you must also ensure that the cable jacket type is suitable for the installation location, such as using plenum rated cable in plenum spaces and riser rated cable in riser spaces.

A cable tester reports detailed information on the physical and electrical properties of the cable. Devices classed as certifiers can be used to test and certify cable installations to a performance category. They use defined transport performance specifications to ensure an installation exceeds the required performance characteristics for parameters such as attenuation and crosstalk.

A cable tester might incorporate the function of a time domain reflectometer (TDR). A TDR is used to measure the length of a cable run and can locate open and short circuits kins/sharp bends, and other imperfections in cables that could affect performance. A TDR transmits a short signal pulse of known amplitude and duration down a cable and measures the corresponding amplitude and time delay associated with resultant signal reflections. A TDR analyzes these reflections and can display any problems found and their location. The TDR measures the amount of time taken for the signal to bounce back and can therefore calculate the distance to the cable fault to within a meter, which makes isolating the problem simpler.


Wire map testers and Tone generators

A multimeter can be used to check physical connectivity if other options are unavailable. The primary purpose of a multimeter is for testing electrical circuits, but it can test for the continuity of any sort of copper wire, the existence of a short, and the integrity of a terminator. To perform useful tests, you need to know the readings that are expected from a particular test. Many multimeters designed for ICT use incorporate the function of a wire map tester. These are also available as dedicated devices. Wire map testers can identify the following problems:

●	Continuity (open): A conductor does not form a circuit because of cable damage or because the connector is not properly wired.

●	Short: Two conductors are joined at some point, usually because the insulating wire is damaged, or a connector is poorly wired.

●	Incorrect pin-out/incorrect termination/mismatched standards: The conductors are incorrectly wired into the terminals at one or both ends of the cable. The following transpositions are common:

○	Reversed pair: The conductors in a pair have been wired to different terminals.

○	Crossed pair (Tx/Rx reverse): The conductors from one pair have been connected to pins belonging to a different pair. This may be done deliberately to create a crossover cable, but such a cable would not be used to link a host to a switch.

Another potential cable wiring fault is a split pair. This is where both ends of a single wire in one pair are wired to terminals belonging to a different pair. This type of fault can only be detected by a wire map tester that also tests for excessive crosstalk. This is generally the kind of functionality associated with a cable tester or certifier.

A network tone generator and probe are used to trace a cable from one end to the other. This may be necessary when the cables are bundled and have not been labeled properly. This device is also known as a Fox and Hound or tone probe. The tone generator is used to apply a signal on the cable to be traced where it is used to follow the cable over ceilings and through ducts.

Attenuation and Interference Issues

If a cable link is too long, decibel (dB) loss or (insertion loss) may mean that the link experiences problems with high error rates and retransmissions (frame or packet loss) resulting in reduced speeds and possibly loss of connectivity. Insertion loss is measured in decibels (dB) and represents the ration of the received voltage to the original voltage.

A dB expresses the ratio between two values using a logarithmic scale. A logarithm is a mathematical tool for performing complex multiplication and division exponential operations as simpler additions and subtractions. The essential point is that a logarithmic scale is nonlinear, so a small change in value represents a large change in the performance measured. The following reference points are useful to remember:

●	+3 dB means doubling, while -3 dB means halving

●	+6 dB means quadrupling, while -6 dB relates to a quarter

●	+10 dB means ten times the ration, while -10 dB is a tenth

The maximum value allowed for insertion loss depends on the link category. When you are measuring insertion loss itself, smaller values are better (20 dB insertion loss is better than 22 dB, for instance). Consequently, higher margin values are better. Higher grade or shielded cable may alleviate the problem; otherwise, you will need to find a shorter cable run or install a repeater or additional switch.

Electromagnetic interference (EMI) is something that should be detected when the cable is installed, so you should suspect either some new source that has been installed recently or some source that was not taken into account during testing. Interference from nearby data cables is also referred to as alien crosstalk.

Crosstalk Issues

Crosstalk usually indicates a problem with bad wiring, a bad connector, or improper termination. Crosstalk is also measured in dB, but unlike insertion loss, higher values represent less noise. There are various types of crosstalk that can be measured:

●	Near End (NEXT): This measures crosstalk on the receive pairs at the transmitter end and is usually caused by excessive untwisting of pairs or faulty bonding of shielded elements.

●	Attenuation to Crosstalk Ratio, Near End (ACRN): This is the difference between insertion loss and NEXT. ACR is equivalent to a signal-to-noise ratio (SNR). A high value means that the signal is stronger than any noise present; a result closer to 0 means the link is likely to be subject to high error rates.

●	Attenuation-to-Crosstalk Ratio, Far End (ACRF): Far End Crosstalk (FEXT) is measured on the receive pairs at the recipient end. The difference between insertion loss and FEXT gives ACRF, which measures cable performance regardless of the actual link length.

●	Power sum: Gigabit and 10 GbE Ethernet use all four pairs. Power sum crosstalk calculations (PSNEXT, PSACRN, AND PSACRF) confirm that a cable is suitable for this type of application. They are measured by energizing three of the four pairs in turn

Cable Application Issues

Straight Through and Crossover Cables

There are two main formats for patch cords:

●	Straight through: The cable is terminated with either T568A at both ends or T568B at both ends. This type of cable is used for an uplink (MDI port to MDIX port).

●	Crossover: The cable is terminated with T568A at one end and T568B at the other. This type of cable is used to connect an end system (host) to another host or a hub to a hub.

Crossover cable is no longer required for this type of application as switches either have an uplink port for this purpose or can auto detect and select between a crossover and straight-through connection. This is referred to as auto-MDI/MDI-X. All Gigabit Ethernet ports support auto-MDI/MDIX.

Rollover Cable/Console Cable

A console cable is used to connect a PC or laptop to the command line terminal of a switch or router. The console port connection on the appliance is a standard RJ-45 jack (but wired in a different way to Ethernet). A legacy console cable has a serial DB-9 connector for the PC end. As almost no computers come with DB-9 ports anymore, modern cables use a USB connector and port. Console cable is traditionally colored pale blue.

\*\*Routers typically have console and AUX ports. The AUX port is used to connect to the router over a dial-up modem. The console port just uses a serial (or null modem) link.\*\*

Power over Ethernet

Cat 3 or better is required to support PoE, while PoE+ must be Cat 5e or better. Drawing power down the cable generates more heat. If this heat is not dissipated, it can affect data rates. Thermal performance is improved by using pure copper cabling with larger conductors. A thin conductor will generate more heat through resistance. Shielded cabling is capable of dispersing heat more efficiently, too.




Fiber Optic Cable Testing Tools

As with attenuation in copper cables, the signal loss is increased with increasing cable length. The EIA/TIA 568 specification for fiber allows for a signal loss of between 0.5 dB/km and 3.5 dB/km, depending on the type of fiber used and the wavelength of the light.

If a break is identified in an installed cable, the location of the break can be found using an optical time domain reflectometer (OTDR). This sends light pulses down the cable and times how long it takes for any reflections to bounce back from the break. A broken cable will need to be repaired (spliced) or replaced. An OTDR can also be used to verify that new splices are sound.

An optical spectrum analyzer (OSA) is typically used with wavelength division multiplexing (WDM) to ensure that each channel has sufficient power. At very long distances, the attenuation of different wavelengths can vary. This is referred to as spectral attenuation. An OSA can determine whether existing cable is suitable for reuse with WDM and which wavelengths will support the link distance required.






















Lesson 5: Explaining IPv4 Addressing

Topic 5A: Explain Ipv4 Addressing Schemes

IPv4 Datagram Header

The Internet Protocol (IP) header contains fields to manage the logical addressing and forwarding function.

The Version field indicates the version of Internet Protocol in use (4), while the Length fields indicate the size of the header and the total packet size (including payload). The maximum theoretical size is 6,535 bytes, but actual packets would typically be much smaller to avoid fragmentation when transported as the payload of Ethernet frames.

The Protocol field describes what is contained (encapsulated) in the payload so that the receiving host knows how to process it. For most packets, the IP protocol type value in the Protocol field will indicate a Transmission Control Protocol (TCP/6) segment or a User Datagram Protocol (UDP/17) datagram, which work at the Transport layer. The values assigned to protocols (such as 6 for TCP and 17 for UDP) are managed by IANA.

\*\*Those are the values in decimal. You are also likely to see them in their hex forms (0x06 and 0x11). Both formats ultimately represent 8-bit binary values (00000110 and 00010001).\*\*

Some protocols run directly on IP at the network layer (rather than at the Transport layer). These IP protocol types include the following:

●	Internet Control Message Protocol (ICMP/1) is used for status messaging and connectivity testing.

●	Internet Group Messaging Protocol (IGMP/2) is used with multicasting.

●	Generic Routing Encapsulation (GRE/47) is used to tunnel packets across an intermediate network. This is used (for example) in some virtual private network (VPN) implementations.

●	Encapsulating Security Payload (ESP/50) and Authentication Header (AH/51) are used with the encrypted form of IP (IPSec).

●	Enhanced Interior Gateway routing Protocol (EIGRP/88) and Open Shortest Path First (OSPF/89) are protocols used by routers to exchange information about paths to remote networks.

IPv4 Address Format

An IP address provides two pieces of information:

●	The network number (network ID): This number is common to all hosts on the same IP network.

●	The host number (host ID): This number identifies a host within an IP network

32-bit IPv4 Addressing

An IPv4 address is 32 bits long. In its raw form, it appears as follows:

●	11000110001100110110010000000001

The 32 bits are subdivided into four groups of 8 bits (1 byte) known as octets. The previous IP address could therefore be written as:

●	11000110 00110011 01100100 00000001

To make an IP address easier to use, it is formatted using dotted decimal notation. This notation requires each octet to be converted to a decimal value. The decimal numbers are separated using a period converting the previous number to this notation is:

●	198.51.100.1

Network Masks

An IP address represents both a network ID and a host ID. A 32-bit network mask (or netmask) is used to distinguish these two components within a single IP address. The mask conceals the host ID portion of the IP address and thereby reveals the network ID portion.

The mask and the IP address are the same number of bits. Wherever there is a binary 1 in the mask, the corresponding binary digit in the IP address is part of the network ID. The 1s in the mask are always contiguous. For example, this mask is valid:

●	11111111 11111111 11111111 00000000

But the following string is not a valid mask:

●	11111111 00000000 11111111 00000000

The network ID portion of an IP address is revealed by ANDing the mask to the IP address. When two 1s are ANDed together, the result is a 1. Any other combination produces a 0.

For example, to determine the network ID of the host IP address 198.51.100.1 with a mask of 255.255.255.0 , the dotted decimal notation of the IP address and mask must first be converted to binary notation. The next step is to AND the two binary numbers. The result can be converted back to dotted decimal notation to show the network ID ( 198.51.100.0 ). The only difference between the host IP address and the network ID lies in the last octet, which is not masked.

ANDing IP address and subnet mask to derive the network ID.

Instead of the dotted decimal mask, this network can be identified using prefix or slash notation. The prefix is simply the number of bits set to 1 in the mask. The network can therefore be referred to as 198.51.100.0/24.

The default masks align with octet boundaries. This means that the values in the mask will be 255 or zero. For example, the default 24-bit mask is as follows:

Network ID and host ID portions when using a 24-bit mask.

An 8-bit mask is 255.0.0.0 and a 16-bit mask is 255.255.0.0.

A longer network portion, such as 255.255.255.0, allows for more network IDs within the overall internetwork, but with fewer available host addresses per network. A short netmask (255.0.0.0) allows for millions of hosts per network, but only 126 possible network addresses.

Subnet Masks

The relative sizes of the network and host portions determine how many networks and hosts per network an addressing scheme can support. The conventional addressing technique has IP addresses with two hierarchical levels, namely the network ID and host ID. This scheme of using whole octet boundaries is inflexible, so a system of dividing networks into subnetworks or subnets was devised.

Subnet addressing has three hierarchical levels: a network ID, subnet ID, and host ID. To create logical subnets, bits from the host portion of the IP address must be allocated as a subnetwork address, rather than part of the host ID.

This means the subnet ID lies within an octet boundary. For example, a binary mask with 28 bits could use all the octets, with the network prefix boundary lying within the fourth octet:

Subnet addressing.

This leaves only 4 bits for the host ID range.

The network ID and subnet ID use different masks. The mask for the whole network is still 255.255.255.0. Hosts within the network use the subnet mask 255.255.255.240.

It is important to understand that only one mask is ever applied to the IP address on each interface. The mask containing the subnet information is only used within the IP network. External IP networks continue to address the whole network by its network ID (198.51.100.0/255.255.255.0). Hosts within the network use the longer subnet mask to differentiate the subnets. These are 198.51.100.0/255.255.255.240,198.51.100.16/255.255.255.240,198.51.100.32/255.255.255.240,198.51.100.48/255.255.255.240, and so on).

Because the 1s in a mask are always contiguous, each octet in decimal in an IPv4 mask will always be one of the following.

Octet Mask Bits	Binary Octet	Decimal Equivalent

1	10000000	128

2	11000000	192

3	11100000	224

4	11110000	240

5	11111000	248

6	11111100	252

7	11111110	254

8	11111111	255

Try to memorize these values to make converting masks between binary and decimal formats easier. For example, a shorter mask with 14 bits has the following mask:

●	11111111 11111100 00000000 00000000 255 252 0 0



Host Address Ranges

The IP network 198.51.100.0/24 allows for 254 possible host IDs. The host ID portion is 8 bits long:

Host address range for a /24 network.

1. bits can express 256 possible values (28). However, the first address (198.51.100.0) cannot be assigned to a host because it is the network address. Similarly, the last address (198.51.100.255) is reserved (for use as a broadcast address).

Using some of these 8 host bits as a subnet ID creates extra networks, but each of those subnets has fewer host addresses (14 in this example):

Host address range for a /28 network.

The purpose of subnetting is to create layer 3 broadcast domain segments with fewer hosts. The trick with subnet design is to fit the scheme to the requirements for number of subnetworks and number of hosts per subnet. Each bit added to the mask approximately halves the number of available host addresses.

Topic 5B: Explain IPv4 Forwarding

Layer 2 versus Layer 3 Addressing and Forwarding

When designing or supporting an IP network, it is important to understand how the logical addressing scheme of network, subnet, and host IDs at the network layer maps to forwarding at the data link layer. Forwarding at layer 3 is referred to as routing, while forwarding at layer 2 is described as switching.

The following figure illustrates how both switching and routing components might be used in a typical network. The whole network is connected to the wider Internet via the WAN interface on the router. The router's other interfaces are used to divide the network into three logical subnetworks. These subnets are mapped to layer 2 segments, each implemented using a switch.

Network placement of routers and switches. (Images © 123RF.com.)

Nodes within each subnet can address one another directly (they are in the same broadcast domain), but they can only communicate with nodes in other subnets via the router.

Within each subnet or broadcast domain, nodes use MAC addresses to forward frames to one another, using a mechanism to translate between layer 3 IP addresses and layer 2 MAC addresses.

The Network layer can also accommodate forwarding between different types of layer 1/2 networks. The private zone is implemented using Ethernet, but the link between the router's public interface and the ISP might use a different technology, such as digital subscriber line (DSL).

IPv4 Default Gateways

When two end system hosts attempt to communicate via IPv4, the protocol compares the source and destination address in each packet against the netmask. If the masked portions of the source and destination IP addresses match, then the destination interface is assumed to be on the same IP network or subnet.

Matching source and destination network IDs.

In the figure, the first 28 bits of the source and destination address are the same. Therefore, IP concludes the destination IPv4 address is on the same IP network and tries to deliver the packet locally.

If the masked portion does not match, as in the following figure, IP assumes the packet must be routed to another IP network:

Different source and destination network IDs.

When the destination IPv4 address is on a different IP network or subnet, the host forwards the packet to its default gateway, rather than trying to deliver it locally. The default gateway is a router configured with a path to remote networks.

The router determines what to do with the packet by performing the same comparison between the source and destination address and netmask. The router then uses its routing table to determine which interface it should use to forward the packet. If no suitable path is available, the router drops the packet and informs the host that it could not be delivered.

If the message is destined for yet another network, the process is repeated to take it to the next stage, and so on.

Paths to other IP networks can be manually configured in the routing table or learned by a dynamic routing protocol. Dynamic routing protocols allow routers to share information about known networks and possible paths to them. This information allows them to choose the best routes to any given destination and select alternate routes if one of these is unavailable.

Address Resolution Protocol (ARP)

When two hosts communicate over an Ethernet network using TCP/IP, an IP address is used at the Network layer to identify each host interface. However, transmission of data must take place at the Physical and Data Link level using the local or hardware/MAC address of the interface. The TCP/IP suite includes the Address Resolution Protocol (ARP) to perform the task of resolving an IP address to a hardware address.

When both sending and receiving hosts are within the same broadcast domain or subnet, local address resolution takes place using ARP requests and ARP replies, as shown in the figure:

ARP requests and replies. (Images © 123RF.com.)

If the destination address is on a remote network, then the local host must use its default gateway to forward the packet. Therefore, it must determine the MAC address of the default gateway using ARP.

The router also uses ARP messaging for its Ethernet interfaces. ARP messaging is only used with Ethernet, however. A router's public interface might use a different type of framing and local addressing.

Unicast and Broadcast Addressing

IPv4 uses several mechanisms with which to communicate with other hosts. When an IPv4 host wants to send a packet to a single recipient, it uses a unicast packet, addressed to the IP address of the destination host. If, however, the local host needs to communicate with multiple hosts, it can use a different scheme.

One means of addressing multiple hosts is to perform a broadcast. A broadcast can be performed by sending a packet to the network or subnet's broadcast address. The broadcast address is the last address in any IP network, or put another way, the address in any IP network where all the host bits are set to 1.

Unicast and broadcast addressing.

For example, if the subnet mask is 255.255.255.240, the last four digits of the last octet in the IP address is the host ID portion. If these digits are set to all 1s, that is the last possible address before the next subnet ID, and therefore the network broadcast address:

Broadcast addresses for four subnets.

All hosts that share the same broadcast address receive the packet. They are said to be in the same layer 3 broadcast domain. Broadcast domain boundaries are established at the Network layer by routers. Routers do not forward broadcasts, except in some specially configured circumstances.

As with unicast traffic, IP packets must be delivered to hosts using layer 2 MAC addresses. At layer 2, broadcasts are delivered using the group MAC address (ff:ff:ff:ff:ff:ff). This means that there is also a broadcast domain scope at layer 2. With legacy devices such as hubs and bridges, every port on all physically connected nodes is part of the same layer 2 broadcast domain. This is also the case with a basic or unmanaged switch. By default, a switch floods broadcasts out of every port except the source port.




Multicast and Anycast Addressing

While the majority of IPv4 traffic is unicast or broadcast, other addressing schemes are used in special circumstances.

Multicast and anycast addressing.

Multicast Addressing

IPv4 multicasting allows one host on the Internet (or private IP network) to send content to other hosts that have identified themselves as interested in receiving the originating host's content. Multicast packets are sent to a destination IP address from a special range configured for use with that multicast group.

At layer 2, multicasts are delivered using a special range of MAC addresses. The switch must be multicast capable. If the switch is not multicast-capable, it will treat multicast like a broadcast and flood the multicast transmissions out of all ports.

The intent to receive multicasts from a particular host is signaled by joining a multicast group. The Internet Group Management Protocol (IGMP) is typically used to configure group memberships and IP addresses.

Anycast Addressing

Anycast means that a group of hosts are configured with the same IP address. When a router forwards a packet to an anycast group, it uses a prioritization algorithm and metrics to select the host that is "closest" (that will receive the packet and be able to process it the most quickly). This allows the service behind the IP address to be provisioned more reliably. It allows for load balancing and failover between the server hosts sharing the IP address.

Topic 5C: Configure IP Networks and Subnets

Virtual LANs and Subnets

Modern Ethernet networks are built using switches. In its default configuration, every port on a switch will be in the same local segment or, put another way, in the same broadcast domain. Any host within a broadcast domain can contact any other host using the same logical addressing scheme (IP subnet) and by hardware/MAC addressing.

If too many hosts are attached to the same switch, broadcast traffic can become excessive and reduce performance. At layer 2, virtual LANs (VLANs) are a means of addressing this issue. Each interface on a managed switch can be assigned a VLAN ID. Using VLANs means that different groups of computers on the same cabling and attached to the same switch(es) can appear to be in separate LAN segments. Each VLAN is a separate broadcast domain.

At layer 3, subnetting is the process of logically dividing an IP network into smaller subnetworks (subnets), with each subnet having a unique address. A subnetting scheme can be applied to represent the VLAN design in the layer 3 topology.

For example, the following subnet design allocates separate subnets (10.0.1.0 and 10.0.2.0 ) for the two VLANs configured on Switch A and for the serial WAN links configured between Router A and Routers B and C ( 10.0.3.0 and 10.0.4.0 ). Routers B and C also have a subnet each for their local networks ( 10.0.5.0 and 10.0.6.0 ).

Subnet design. (Images © 123RF.com.)

Apart from breaking up broadcast domains, subnets can be used to achieve other network design goals:

●	Many organizations have more than one site with WAN links between them. The WAN link normally forms a separate subnet.

●	It is useful to divide a network into logically distinct zones for security and administrative control.

●	Networks that use different physical and data link technologies, such as Token Ring and Ethernet, should be logically separated as different subnets.

Classful Addressing

So far, we have considered IP network and subnet IDs using masks or network prefixes. This is referred to as classless addressing. A classful addressing scheme was employed in the 1980s, before the use of netmasks to identify the network ID portion of an address was developed. Classful addressing allocates a network ID based on the first octet of the IP address.

Class A, Class B, and Class C networks.

Class A network addresses support large numbers of hosts-over 16 million. However, there are only 126 Class A network addresses. There are 16,000 Class B networks, each containing up to about 65,000 hosts. Finally, Class C networks support only 254 hosts each, but there are over 2 million of them.

When considering classful addressing, you need to be able to identify the address class from the first octet of the IP address. This table shows how to identify an address class from the first octet of the IP address in decimal.

First Octet	Class

1. to 126	Class A

128 to 191	Class B

192 to 223	Class C

While routers have performed classless routing for years, the class terminology is still very widely used. Even under classless addressing, the old classes are often used as names for the netmasks that align to whole octet boundaries:

●	Class A: 255.0.0.0 (/8)

●	Class B: 255.255.0.0 (/16)

●	Class C: 255.255.255.0 (/24)

Classful addressing is also important because it establishes some IP address ranges that cannot be used for ordinary host addressing or for addressing over the Internet.

Public versus Private Addressing

A public IP address is one that can establish a connection with other public IP networks and hosts over the Internet. The allocation of public IP addresses is governed by IANA and administered by regional registries and ISPs. Hosts communicating with one another over a LAN could use a public addressing scheme but will more typically use private addressing.

Private IP Address Ranges

Private IP addresses can be drawn from one of the pools of addresses defined in RFC 1918 as non-routable over the Internet:

●	10.0.0.0 to 10.255.255.255 (Class A private address range).

●	172.16.0.0 to 172.31.255.255 (Class B private address range).

●	192.168.0.0 to 192.168.255.255 (Class C private address range).

Any organization can use private addresses on its networks without applying to a registry or ISP, and multiple organizations can use these ranges simultaneously. Internet access can be facilitated for hosts using a private addressing scheme in two ways:

●	Through a router configured with a single or block of valid public IP addresses; the router translates between the private and public addresses using a process called Network Address Translation (NAT).

●	Through a proxy server that fulfills requests for Internet resources on behalf of clients. The proxy server itself must be configured with a public IP address on the external-facing interface.



Automatic Private IP Addressing (APIPA)

A host's IP configuration can either be applied statically or it can use an autoconfiguration method. Autoconfiguration on an IPv4 network usually means using a Dynamic Host Configuration Protocol (DHCP) server.

Automatic Private IP Addressing (APIPA) was developed by Microsoft as a means for clients that could not contact a DHCP server to communicate on the local network anyway. If a Windows host does not receive a response from a DHCP server within a given time frame, it selects an address at random from the range 169.254.1.1 to 169.254.254.254.

These addresses are from one of the address ranges reserved for private addressing (169.254.0.0/16). The first and last subnets are supposed to be unused.

This type of addressing is referred to as link local in standards documentation (RFC 3927). Link local addressing mechanisms can also be implemented on other operating systems, such as Bonjour® for the macOS® platform or Avahi for Linux®.

Other Reserved Address Ranges

There are two additional classes of IP address (D and E) that use the values above 223.255.255.255:

●	Class D addresses (224.0.0.0 through 239.255.255.255) are used for multicasting.

●	Class E addresses (240.0.0.0 through 255.255.255.255) are reserved for experimental use and testing.

Loopback Addresses

While nominally part of Class A, the range 127.0.0.0 to 127.255.255.255 (or 127.0.0.0/8) is reserved. This range is used to configure a loopback address, which is a special address typically used to check that TCP/IP is correctly installed on the local host. The loopback interface does not require a physical interface to function. A packet sent to a loopback interface is not processed by a network adapter but is otherwise processed as normal by the host's TCP/IP stack. Every IP host is automatically configured with a default loopback address, typically 127.0.0.1. On some hosts, such as routers, more than one loopback address might be configured. Loopback interfaces can also be configured with an address from any suitable IP range, as long as it is unique on the network. A host will process a packet addressed to a loopback address regardless of the interface on which it is received.

Other

A few other IPv4 address ranges are reserved for special use and are not publicly routable:

●	0.0.0.0/8-Used when a specific address is unknown. This is typically used as a source address by a client seeking a DHCP lease.

●	255.255.255.255-Used to broadcast to the local network when the local network address is not known.

●	100.64.0.0/10, 192.0.0.0/24, 192.88.99.0/24, 198.18.0.0/15-Set aside for a variety of special purposes.

●	192.0.2.0/24, 198.51.100.0/24, 203.0.113.0/24-Set aside for use in documentation and examples.










IPv4 Address Scheme Design

The following factors must be weighed when planning an IPv4 network addressing scheme:

●	The number of IP networks and subnetworks required.

●	The number of hosts per subnet that must be supported.

●	The network ID must be from a valid public or a private range (not from the loopback, link local reserved range, multicast range, or reserved/experimental range, for instance).

●	The network and/or host IDs cannot be all 1s in binary-this is reserved for broadcasts.

●	The network and/or host ID cannot be all 0s in binary; 0 means "this network."

●	Each host ID must be unique on the IP network or subnet.

●	The network ID must be unique on the Internet (if you are using a public addressing scheme) or on your internal system of internetworks (if you are using a private addressing scheme).

When you are performing subnet calculations, try to think in terms of the number of mask bits. It helps to remember that each power of 2 is double the previous one:

22	23	24	25	26	27	28

4	8	16	32	64	128	256


Also memorize the decimal values for the number of bits set to 1 in an octet within a mask:

1	2	3	4	5	6	7	8

128	192	224	240	248	252	254	255

In the following example, the network design is subnetting the network address 172.30.0.0/16. The process of designing the scheme is as follows:

1. `	`Work out how many subnets are required (remembering to allow for future growth), then round this number up to the nearest power of 2.

For example, if you need 12 subnets, the next nearest power of 2 is 16. The exponent is the number of bits you will need to add to your default mask. For example, 16 is 24 (2 to the power of 4), so you will need to add 4 bits to the network prefix. In dotted decimal format, the subnet mask becomes 255.255.240.0 .

1. `	`Work out how many hosts each subnet must support and whether there is enough space left in the scheme to accommodate them.

For example, the network address is in the /16 range, and you are using 4 bits for subnetting, so you have 32-20 = 12 bits for hosts in each subnet. The number of hosts per subnet can be expressed using the formula 2 n -2, where n is the number of bits you have allocated for the host ID. 12 bits is enough for 4094 hosts in each subnet.

You subtract 2 because each subnet's network address and broadcast address cannot be assigned to hosts.

Wherever a 1 appears in the binary mask, the corresponding digit in the IP address is part of the network or subnet address. When you are planning what your mask will be, remember this rule. Allocate more bits in the mask if you need more subnets. Allocate fewer bits in the mask if you need more hosts per subnet.

Just for comparison, if you have a /24 (or Class C) network address and try to allocate 16 subnets, there will be enough space left for only 14 hosts per subnet (24-2).

1. `	`Work out the subnets. The easiest way to find the first subnet ID is to deduct the least significant octet in the mask (240 in this example) from 256. This gives the first subnet ID, which, in full, is 172.30.16.0/20.

The subsequent subnet IDs are all the lowest subnet ID higher than the one before-32, 48, 64, and so on.

1. `	`Work out the host ranges for each subnet. Take the subnet address and add a binary 1 to it for the first host. For the last host, take the next subnet ID and deduct two binary digits from it. In this case, this is 172.30.16.1 and 172.30.31.254 , respectively. Repeat for all subnets.









Lesson 6: Supporting IPv4 and IPv6 Networks

Topic 6A: User Appropriate Tools to Test IP Configuration

IP Interface Configuration in Windows

Each host adapter must be allocated an appropriate IP address and subnet mask, plus the IP address of the default gateway (router) for its network. Typically, a host is also configured with the addresses of domain name system (DNS) servers that can resolve IP address to name labels, making identification of hosts and services simpler.

These IP configuration values can be assigned statically or dynamically. Configuring large numbers of hosts with a valid static addressing parameters is a complex management task. Most hosts are configured to obtain an address automatically, using a service called the Dynamic Host Configuration Protocol (DHCP).

Under Windows, each Ethernet adapter is assigned a name. In early Windows versions the first adapter was named "Local Area Connection," but recent versions just use the label "Ethernet." Additional adapters are identified as "Ethernet2," "Ethernet3," and so on. A new name can be applied if necessary. The IP configuration for each adapter interface is often set using the GUI Properties dialog accessed via the Network Connections applet. However, you can also configure interfaces using netsh commands.

netsh interface ip set address "Ethernet" dhcp

netsh interface ip set address "Ethernet" static 10.1.0.1 255.255.255.0 10.1.0.254

In Windows, all changes to the network interface configuration are persistent, meaning that they continue to apply when the system is rebooted.

You can also use netsh to report the IP configuration ( netsh interface ip show config , for example).

netsh is implemented in the legacy command prompt interface. Script-based configuration is now more likely to use PowerShell cmdlets. The Get-NetAdapter and Get-NetIPAddress cmdlets can be used to query the existing configuration. A new configuration can be applied using New-NetIPAddress or an existing one can be modified using Set-NetIPAddress .

IPCONFIG

While netsh and PowerShell offer a lot of granular functionality, the ipconfig command is still widely used for basic configuration reporting and support tasks. ipconfig can be used as follows:

●	ipconfig without any switches will display the IP address, subnet mask, and default gateway (router) for all network interfaces to which TCP/IP is bound.

●	ipconfig /all displays complete TCP/IP configuration parameters for each interface, including whether the Dynamic Host Configuration Protocol (DHCP) is enabled for the interface and the interface's hardware (MAC) address.

●	ipconfig /renew interface forces a DHCP client to renew the lease it has for an IP address.

●	ipconfig /release interface releases the IP address obtained from a DHCP Server so that the interface(s) will no longer have an IP address.

●	ipconfig /displaydns displays the Domain Name System (DNS) resolver cache.

●	ipconfig /flushdns clears the DNS resolver cache.

●	ipconfig /registerdns registers the host with a DNS server (if it supports dynamic updates).

Identifying the current IP configuration with ipconfig. (Screenshot used with permission from Microsoft.)

There are also /release6 and /renew6 switches for use with DHCPv6 (a DHCP server supporting IPv6).

IFCONFIG and IP

In Linux, Ethernet interfaces are classically identified as eth0, eth1 , eth2 , and so on, although some network packages now use different schemes, such as en prefixes. In Linux, you need to distinguish between the running configuration and the persistent configuration. The persistent configuration is the one applied after a reboot or after a network adapter is reinitialized. The method of applying an IP configuration to an adapter interface is specific to each distribution. Historically, the persistent configuration was applied by editing the /etc/network/interfaces file and bringing interfaces up or down with the ifup and ifdown scripts. Many distributions now use the NetworkManager package, which can be operated using a GUI or the nmcli tools. Alternatively, a network configuration might be managed using the systemd-networkd configuration manager. Additionally, recent distributions of Ubuntu use netplan to abstract some of this underlying complexity to configuration files written in YAML ain't markup language (YAML). The YAML configuration files are rendered by either systemd-networkd or NetworkManager.

When it comes to managing the running configuration, you also need to distinguish between legacy and current command packages. ifconfig is part of the legacy net-tools package. Use of these commands is deprecated on most modern Linux distributions. ifconfig can still safely be used to report the network interface configuration, however.

ifconfig output.

net-tools has been replaced by the iproute2 package. These tools can interface properly with modern network configuration manager packages. As part of the iproute2 package, the ip command has options for managing routes as well as the local interface configuration. The basic reporting functionality of ifconfig (show the current address configuration) is performed by running ip addr ; to report a single interface only, use ip addr show dev eth0 . The ip link command shows the status of interfaces, while ip -s link reports interface statistics.

ip a command output.

The ip link set eth0 up|down command is used to enable or disable an interface, while ip addr add|delete can be used to modify the IP address configuration. These changes are not persistent and apply only to the running configuration, unless run as part of a startup script.

ARP Cache Utility

The Address Resolution Protocol (ARP) is used by hosts to determine which MAC address is associated with an IP address on the local network. ARP queries are sent as broadcasts. ARP broadcasts can generate considerable traffic on a network, which can reduce performance. To optimize this process, the results of an ARP broadcast are cached in an ARP table. If the entry is used within the timeout period, the entry is held in the cache for a few minutes before it is deleted.

The arp utility can be used to perform functions related to the ARP table cache. You would use this to diagnose a suspected problem with local addressing and packet delivery.

●	arp -a (or arp -g ) shows the ARP cache contents. You can use this with IPAddress to view the ARP cache for the specified interface only. The ARP cache will not necessarily contain the MAC addresses of every host on the local segment. There will be no cache entry if there has not been a recent exchange of frames.

●	arp -s IPAddress MACAddress adds an entry to the ARP cache. Under Windows, MACAddress needs to be entered with hyphens between each hex byte.

●	arp -d \* deletes all entries in the ARP cache; it can also be used with IPAddress to delete a single entry.

Output from the arp command showing network (IP) addresses mapped to physical (MAC) addresses. Host interfaces are learned (dynamic), while broadcast and multicast interfaces are configured statically. (Screenshot used with permission from Microsoft.)

In Linux, the ip neigh command shows entries in the local ARP cache (replacing the old arp command).

Internet Control Message Protocol and Ping

The Internet Control Message Protocol (ICMP) is used to report errors and send messages about the delivery of a packet. ICMP messages are generated under error conditions in most types of unicast traffic, but not for broadcast or multicast packets.

ICMP can also be used to test and troubleshoot connectivity issues on IP networks. The ping utility sends a configurable number and size of ICMP request packets to a destination host. ping is implemented on both Windows and Linux hosts. ping can be used to perform a basic connectivity test that is not dependent on the target host running any higher-level applications or services.

Basic ping Usage

A basic connectivity test is performed by running ping IPAddress , where IPAddress is an IPv4 or IPv6 address.

If the probe is successful (as in the first attempts shown in the screen capture), the output shows the message "Reply from IPAddress" and the time it takes for the server's response to arrive. The millisecond measures of Round Trip Time (RTT) can be used to diagnose latency problems on a link.

Using ping in Windows. (Screenshot used with permission from Microsoft.)

The Time to Live (TTL) IP header field is reduced by one every time a packet is forwarded by a router (referred to as a hop). The TTL output field in the ping command shows the value of the counter when the packet arrived at its destination.

To work out the number of hops it took, you need to know the initial value. Different operating systems and OS versions use different default values. For example, if you ping a remote host from a Windows 10 host and the TTL value in the output is 52, then you know the packet took 12 hops (64-52) to reach its destination.

ping Error Messaging

If ping probes are unsuccessful, one of two messages are commonly received:

●	Destination host unreachable-There is no routing information (that is, the local computer does not know how to get to that IP address). This might be caused by some sort of configuration error on the local host, such as an incorrect default gateway, by a loss of connectivity with a router, or by a routing configuration error.

●	No reply (Request timed out.)-The host is unavailable or cannot route a reply to your computer. Requests time out when the TTL is reduced to 0 because the packet is looping (because of a corrupted routing table), when congestion causes delays, or when a host does not respond.

ping Switches

ping can be used with several switches. You can use a host name or fully qualified domain name rather than an IP address to test name resolution. When pinging by name, -4 or -6 force the tool to query the IPv4 host record or IPv6 host record respectively. Also, -t continues to ping the host until interrupted (by pressing Ctrl+C).

ping has different syntax when used under Linux. By default, the command executes until manually halted, unless run with the number of packets set by the -c switch.


Topic 6B: Troubleshoot IP Networks

Hardware Failure and Network Interface Issues

When you are using the CompTIA Network+ troubleshooting model, it is wise to rule out physical hardware failure and Data Link layer issues before diagnosing a Network layer or service issue. Failures at the Network layer are more common, but if you can isolate a connectivity problem to a particular network segment, the cause may lie in a hardware failure rather than a configuration issue.

Power Issues

Like any computer system, networks require stable power to operate properly. Power anomalies, such as surges and spikes, can damage devices, brownouts (very brief power loss) can cause systems to lockup or reboot, while power failures (blackouts) will down everything, including the lights. Enterprise sites have systems to protect against these issues. Uninterruptible power supplies (UPSs) can keep servers, switches, and routers running for a few minutes. This provides time to either switch in a secondary power source (a generator) or shut down the system gracefully, hopefully avoiding data loss. Most power problems will have to be escalated to an electrician or to the power company, depending on where the fault lies.

Hardware Failure Issues

If power is not the issue, consider other components that might have experienced hardware failure, including host network adapters, switch/router/modem appliances, and the cabling between them. You can test for specific cabling faults and bad ports using cable and loopback testers and certifiers. Complete hardware failure is relatively uncommon, so if you can rule out power and cabling problems, then for a network adapter, verify that the driver is working correctly. The easiest thing to do is to replace the driver (in Windows®, use Device Manager to do this). For a network appliance, use status LEDs to confirm operation and check that things like plug-in cards and modules are seated correctly. You should also consider overheating as a potential cause of hardware issues. Make sure there is good airflow around the intake and outlet vents. Check that fans and internal components are not clogged with dust and that systems are not exposed to direct sunlight.

At the data link layer, most wired hosts connect to the network via a switch. If you suspect a device like a switch, analyze the topology of your network. You should be able to view those users who are suffering the problem, identify which part of the network is affected, and identify the problem bridging or switching device.

When you have narrowed the problem to a device, you must determine what the nature of the problem is. It is always worth resetting the switch to see if that resolves the problem. Often, restarting network devices can clear any errors.

Interface Status Issues

If you can isolate the issue to a single host and then rule out cable and transceiver issues at the physical layer, bear in mind that the data link configuration might not be working. Use the LED status indicators and switch's command line utility to check the interface status. If the line and protocol status is not up/up, check whether autonegotiation of speed and duplex settings is configured and whether it is failing. If the speed setting (10, 100, or 1000 Mbps) is mismatched between the host and the switch port, the link will fail.

Interface status commands will also report whether any collisions are being generated. Collisions might occur if the duplex setting on the switch port and host is mismatched or if a legacy hub device or host NIC is connected to a switch. If neither of these conditions apply, check for a faulty host NIC or driver.

IP Configuration Issues

If you can rule out a problem at the Physical and Data Link layers, the next thing to check is basic addressing and protocol configuration. If a host cannot perform neighbor discovery to contact any other nodes on the local network, first use ipconfig (Windows) or ip or ifconfig (Linux) to verify the host configuration.

Incorrect IP Address

Each end system host must have the same subnet mask as its neighbors and an IP address that produces a valid, unique host address within that subnet. A neighbor in this sense is another host in the same layer 2 broadcast domain. For example, if the subnet is 192.168.1.0/24, consider the following host address configurations:

●	Host A: IP: 192.168.1.10, Mask: 255.255.255.0

●	Host B: IP: 192.168.1.11, Mask: 255.255.255.0

●	Host C: IP: 192.168.0.21, Mask: 255.255.255.0

Host A and Host B have valid configurations, but Host C has an address in a different subnet (192.168.0.0 compared to 192.168.1.0 ). Hosts A and B will try to use the default gateway to forward packets to Host C. Host C is unlikely to be able to communicate on the network at all.

When you encounter non default masks, it can be slightly more difficult to identify valid host ranges. For example, if the subnet address is 198.51.100.16/28, consider the following host address configurations:

●	Host A: IP: 198.51.100.10, Mask: 255.255.255.240

●	Host B: IP: 198.51.100.11, Mask: 255.255.255.240

●	Host C: IP: 198.51.100.21, Mask: 255.255.255.240

The network prefix boundary lies within the last octet, so you cannot rely on the first three octets alone. Again, host C is in a different subnet.

Also, remember that the network address and broadcast address cannot be used as a host address.

Incorrect Subnet Mask

Another issue that might arise if a netmask is incorrect, is that the host can receive communications, but misroutes its replies, thinking that the hosts communicating with it are on a different subnet. The replies may still get through, although they may go via the default gateway (router), rather than directly.

●	Host A: IP: 192.168.1.10, Mask: 255.255.255.0

●	Host B: IP: 192.168.1.11, Mask: 255.255.255.0

●	Host C: IP: 192.168.1.21, Mask: 255.255.255.240

Because it is using a longer prefix than it should, Host C will think it needs to route to a different subnet to communicate with hosts A and B. This will cause packets to go via the router, placing unnecessary load on it.

The other scenario for an incorrect mask is where the mask is shorter than it should be:

●	Host A: IP: 192.168.1.10, Mask: 255.255.255.0

●	Host B: IP: 192.168.1.11, Mask: 255.255.255.0

●	Host C: IP: 192.168.1.21, Mask: 255.255.0.0

●	Host D: IP: 192.168.0.10, Mask: 255.255.255.0

In this case, the problem will not be obvious if hosts A, B, and C are all on the same local network, as they will be able to use ARP messaging and receive replies. However, host C will not be able to contact host D, as it thinks that host D is on the same local network, whereas in fact it needs to route messages for 192.168.0.0/24 via the default gateway.

In this scenario, the router might send ICMP redirect status messages to host C.

Duplicate IP and MAC Address Issues

Two systems could end up with the same IP address because of a configuration error; perhaps both addresses were statically assigned, or one was assigned an address that was part of a DHCP scope. If Windows detects a duplicate IP address, it will display a warning and disable IP. Linux® does not typically check for duplicate IP addresses. If there are two systems with duplicate IPs, a sort of race condition will determine which receives traffic. Obviously, this is not a good way for the network to be configured, and you should identify and fix the machines. To do this, obtain the MAC addresses of both interfaces using ping and then arp -a to examine the ARP cache table. On Linux, you can use the arping tool (arping -D) to report duplicate replies. Once identified, configure each host to use a unique address.

A duplicate MAC address will cause a problem similar to a duplicate IP address. Both hosts will contend to respond to ARP queries, and communications could be split between them or reach only one of the hosts. Duplicate MAC addresses are unlikely to arise unless the network uses locally administered addressing.

Issues with MAC addressing can be a sign that someone is attempting to perform a spoofing attack.

To diagnose MAC address issues, use the arp utility to verify the MAC addresses recorded for each host and ipconfig or ip neigh to check the MAC address assigned to the interface. Also check the MAC address and ARP tables on any switches and routers involved in the communications path. You can use a protocol analyzer to examine ARP traffic and identify which IP hosts are attempting to claim the same MAC address.








Problem Isolation

If the address configuration on the local host seems to be correct, you can complete a series of connectivity tests using ping to determine the likely location and scope of a fault.

A general ping sequence for identifying connectivity issues.

1. `	`Ping the loopback address (ping 127.0.0.1) to verify TCP/IP is installed and loaded correctly. If this fails, reinstall the network protocol stack.
1. `	`Ping the IP address of the local host to verify it was added correctly and to verify that the network adapter is functioning properly. If you cannot ping your own address, there might have been a configuration error, or the network adapter or adapter driver could be faulty.
1. `	`Ping the IP address of the default gateway to verify it is up and running and that you can communicate with another host on the local network.
1. `	`Ping the IP address of other hosts on the same subnet to test for local configuration or link problems.

If a local host cannot be pinged and the error is destination unreachable, then verify the IP configuration does not contain an incorrect IP address or netmask. If these are correct but pings still time out, suspect either a security issue (such as a switch port security issue) or a problem at the data link or physical layer.

1. `	`Ping the IP address of a remote host to verify you can communicate through the router. If a remote IP address cannot be contacted, check the default gateway parameter on the local host to rule out an incorrect gateway issue. If the gateway is configured correctly and you can ping the router, you need to start investigating the routing infrastructure.

When performing tests using ping, always be aware that ICMP could be blocked by a firewall or other security software, especially when pinging remote hosts.

Incorrect DNS Issues

If you can successfully perform all connectivity tests by IP address but cannot ping by host name, then this suggests a name resolution problem. Many services use host names and domain names to make them easier to reconfigure and easier for people to access. The Domain Name System (DNS) is used to map these names to IP addresses. When a host receives a client request to access a name and it does not have the IP mapping cached, it asks a DNS server configured as a resolver to perform the lookup and return the IP address. As name resolution is a critical service, most hosts are configured with primary and secondary DNS servers for redundancy. The server addresses are entered as IP addresses. On most workstation hosts, these addresses are likely to be auto configured via DHCP.

In Windows, you can view the DNS servers using ipconfig /all. In Linux, the DNS server addresses are recorded in /etc/resolv.conf . Typically, a package such as NetworkManager or systemd-networkd would add the entries. Entries added directly will be overwritten at reboot.

If a host cannot resolve names, check that the correct DNS server addresses have been configured and that you can ping them. If there are configuration errors, either correct them (if the interface is statically configured) or investigate the automatic addressing server. If there are connectivity errors, check the network path between the host and its DNS servers.

Multicast Flooding Issues

Multicast is a one-to-many type of transmission designed for more efficient delivery of packets. Rather than a transmitter sending separate unicast packets to each receiver, a copy of the same packet is delivered to each receiver that has joined the relevant multicast group. Multicast groups are established at layer 3 by protocols such as Internet Group Management Protocol (IGMP).

At layer 2, if a switch is not multicast-aware, it will treat multicast transmissions as broadcasts and flood them across all ports in the broadcast domain. This can consume a lot of bandwidth and slow down the network. This problem becomes particularly acute if the switch floods multicast traffic to virtual LANs (VLANs) that do not need to receive it. To combat this, IGMP snooping can be enabled as a global option on a switch and as a per-VLAN option. IGMP snooping means the switch reads IGMP messages and can determine if the host on an access port or one or more hosts in a VLAN have joined a multicast group. Multicast traffic is filtered from ports and VLANs that have no hosts participating in the multicast group.





Topic 6C: Explain IPv6 Addressing Schemes

IPv4 versus IPv6

In IPv4, the addressing scheme is based on a 32-bit binary number. 32 bits can express 232 unique addresses (in excess of four billion). However, the way in which addresses have been allocated has been inefficient, leading to waste of available addresses. Inefficiencies in the addressing scheme and unceasing demand for more addresses mean that the available IPv4 address supply is exhausted.

IP version 6 (IPv6) provides a long-term solution to this problem of address space exhaustion. Its 128-bit addressing scheme has space for 340 undecillion unique addresses. Even though only a small part of the scheme can currently be allocated to hosts, there is still enough address space within that allocation for every person on the planet to own approximately 4,000 addresses. As well as coping with the growth in ordinary company networks and Internet access subscribers, IPv6 is designed to meet the demands of billions of personal and embedded devices with Internet connectivity.

This blog explains why we have jumped from IPv4 to IPv6: colocationamerica.com/blog/ipv4-ipv6-what-happened-to-ipv5.htm.

An IPv6 packet consists of two or three elements: the main header, which is a fixed length (unlike in IPv4), one or more optional extension headers, and the payload. As with an IPv4 header, there are fields for the source and destination addresses and the version (0110 or 0x06 for IPv6). Some of the other header fields are as follows:

Field	Explanation

Traffic Class	Describes the packet's priority.

Flow Label	Used for quality of service (QoS) management, such as for real-time streams. This is set to 0 for packets not part of any delivery sequence or structure.

Payload Length	Indicates the length of the packet payload, up to a maximum of 64 KB; if the payload is bigger than that, this field is 0 and a special Jumbo Payload (4 GB) option is established.

Next Header	Used to describe what the next extension header (if any) is, or where the actual payload begins.

Hop Limit	Replaces the TTL field in IPv4 but performs the same function.

Extension headers replace the Options field in IPv4. There are several predefined extension headers to cover functions such as fragmentation and reassembly, security (IPSec), source routing, and so on.


IPV6 ADDRESS FORMAT

An IPv6 address contains eight 16-bit numbers (double-byte or double-octet), with each double-byte number expressed as 4 hex digits. For example, consider the following binary address:

0010 0000 0000 0001 : 0000 1101 1011 1000 : 0000 0000 0000 0000 : 0000 0000 0000 0000 : 0000 1010 1011 1100 : 0000 0000 0000 0000 : 1101 1110 1111 0000 : 0001 0010 0011 0100

This binary value can be represented in hex notation as:

2001:0db8:0000:0000:0abc:0000:def0:1234

Using canonical notation, the hex notation can be compressed further. Where a double byte contains leading 0s, they can be ignored. In addition, one contiguous series of 0s can be replaced by a double colon place marker. Thus, the prior address would become:

2001:db8::abc:0:def0:1234

You can only use double colon compression once in a given address. For example, 2001:db8::abc::def0:1234 is not valid as it is unclear which of the following two addresses is represented:

2001:db8:0000:0abc:0000:0000:def0:1234

2001:db8:0000:0000:0abc:0000:def0:1234

Where IPv6 addresses are used as part of a URL (web address), because both formats use colon delimiters to mean different things, the IPv6 address must be contained within brackets. For example: https://[2001:db8::abc:0:def0:1234]/index.htm.


IPV6 NETWORK PREFIXES

An IPv6 address is divided into two parts: the first 64 bits are used as a network ID, while the second 64 bits designate a specific interface. Unlike in IPv4, the interface address (or host ID portion) is always the same 64-bit length.

In IPv6, the interface identifier is always the last 64 bits. The first 64 bits are used for network addressing.

Network addresses are written using classless notation, where /nn is the length of the network prefix in bits. Within the 64-bit network ID, as with IPv4 netmasks, the length of any given network prefix is used to determine whether two addresses belong to the same IP network. For example, if the prefix is /48, then if the first 48 bits of an IPv6 address were the same as another address, the two would belong to the same IP network. This means that a given organization's network can be represented by a global routing prefix 48 bits long, and they then have 16 bits left in the network ID to subnet their network. For example,

2001:db8:3c4d::/48

would represent a network address, while:

2001:db8:3c4d:0001::/64

would represent a subnet within that network address.

Like IPv4, IPv6 can use unicast, multicast, and anycast addressing. Unlike IPv4, there is no broadcast addressing.

IPV6 UNICAST ADDRESSING

As with IPv4, an IPv6 unicast address identifies a single network interface. IPv6 unicast addressing is scoped; a scope is a region of the network. Global scopes provide the equivalent of public addressing schemes in IPv4, while link local schemes provide private addressing.

IPv6 Global Addressing

Globally scoped unicast addresses are routable over the Internet and are the equivalent of public IPv4 addresses. The parts of a global address are:

●	The first 3 bits (001) indicate that the address is within the global scope. Most of the IPv6 address space is unused. The scope for globally unique unicast addressing occupies just 1/8th of the total address space. In hex, globally scoped unicast addresses will start with a 2 (0010) or 3 (0011).

●	The next 45 bits are allocated in a hierarchical manner to regional registries and from them to ISPs and end users.

●	The next 16 bits identify site-specific subnet addresses.

●	The final 64 bits are the interface ID.

IPv6 global unicast address format.




Interface ID/EUI-64

The 64-bit interface ID can be determined by using two techniques.

One is by using the interface's MAC address. This is known as a MAC-derived address or interface identifier. As a MAC address is currently 48 bits (6 bytes), a (relatively) simple translation mechanism allows driver software to create a 64-bit interface ID (an EUI-64) from these 48 bits.

Two changes occur to derive the EUI-64 interface ID from an interface’s MAC address. First, the digits fffe are added in the middle of the MAC address. Second, the first 8 bits, or 2 hex digits, are converted to binary, and the 7th bit (or U/L bit) is flipped (from 0 to 1 or 1 to 0). For example, the MAC address 00608c123abc would become the EUI-64 address 02608cfffe123abc, which (when expressed in double bytes) becomes 0260:8cff:fe12:3abc, or (without the leading 0) 260:8cff:fe12:3abc.

In the second technique, referred to as privacy extensions, the client device uses a pseudorandom number for the interface ID. This is known as a temporary interface ID or token. There is some concern that using interface identifiers would allow a host to be identified and closely monitored when connecting to the Internet, and using a token mitigates this to some degree.

IPV6 LINK LOCAL ADDRESSING

Link local addresses span a single subnet (they are not forwarded by routers). Nodes on the same link are referred to as neighbors. The link local range is fe80::/10. Link local addresses start with a leading fe80, with the next 54 bits set to 0, and the last 64 bits are the interface ID.

IPv6 link local unicast address format.

The equivalent in IPv4 is Automatic Private IP Addressing (APIPA) and its 169.254.0.0 addresses. However, unlike IPv4, an IPv6 host is always configured with link local addresses (one for each link), even if it also has a globally unique address.

A link local address is also appended with a zone index (or scope id) of the form %1 (Windows) or %eth0 (Linux). This is used to define the source of the address and make it unique to a particular link. For example, a given host may have links to a loopback address, Ethernet, and a VPN. Each of these links may use the same link local address, so each is assigned a zone ID to make it unique. Zone indices are generated by the host system, so where two hosts communicate, they may be referring to the link using different zone IDs.

While it is relatively uncommon for an interface to have more than one IPv4 address, in IPv6 it is typical for an interface to have multiple addresses.

IPV6 INTERFACE AUTO CONFIGURATION AND TESTING

In IPv6, an interface must always be configured with a link local address. One or more routable addresses can be assigned to the interface in addition to the link local address. As with IPv4, you can either assign a routable IPv6 address statically or use an automatic addressing scheme. Static address configuration would generally be reserved to routers and possibly some types of servers.









Neighbor Discovery Protocol and Router Advertisements

The Neighbor Discovery (ND) protocol performs some of the functions on an IPv6 network that ARP and ICMP perform under IPv4. The main functions of ND are:

●	Address autoconfiguration-Enables a host to configure IPv6 addresses for its interfaces automatically and detect whether an address is already in use on the local network, by using neighbor solicitation (NS) and neighbor advertisement (NA) messages.

●	Prefix discovery-Enables a host to discover the known network prefixes that have been allocated to the local segment. This facilitates next-hop determination (whether a packet should be addressed to a local host or a router). Prefix discovery uses router solicitation (RS) and router advertisement (RA) messages. An RA contains information about the network prefix(es) served by the router, information about autoconfiguration options, plus information about link parameters, such as the MTU and hop limit. Routers send RAs periodically and in response to a router solicitation initiated by the host.

●	Local address resolution-Allows a host to discover other nodes and routers on the local network (neighbors). This process also uses neighbor solicitation (NS) and neighbor advertisement (NA) messages.

●	Redirection-Enables a router to inform a host of a better route to a particular destination.








Stateless Address Autoconfiguration

IPv4 has a system for generating link local addresses, but these are not routable outside the local network. Consequently, IPv4 depends heavily on the Dynamic Host Configuration Protocol (DHCP) for address autoconfiguration. IPv6 uses a more flexible system of address autoconfiguration called stateless address autoconfiguration (SLAAC):

●	The host generates a link local address and tests that it is unique by using the Neighbor Discovery (ND) protocol.

●	The host listens for a router advertisement (RA) or transmits a router solicitation (RS) using ND protocol messaging. The router can either provide a network prefix, direct the host to a DHCPv6 server to perform stateful autoconfiguration, or perform some combination of stateless and stateful configuration.

ICMPv6

IPv6 uses an updated version of ICMP. The key new features are:

●	Error messaging-ICMPv6 supports the same sort of destination unreachable and time exceeded messaging as ICMPv4. One change is the introduction of a Packet Too Big class of error. Under IPv6, routers are no longer responsible for packet fragmentation and reassembly, so the host must ensure that they fit in the MTUs of the various links used.

●	Informational messaging-ICMPv6 supports ICMPv4 functions, such as echo and redirect, plus a whole new class of messages designed to support Neighbor Discovery (ND) and Multicast Listener Discovery (MLD), such as router and neighbor advertisements and solicitations.

IPV6 MULTICAST ADDRESSING

A multicast address is used to send a packet from a single source to multiple network interfaces. Unlike IPv4, IPv6 routers must support multicast. The parts of a multicast address are subdivided as follows:

●	The first 8 bits indicate that the address is within the multicast scope (1111 1111 or ff).

●	The next 4 bits are used to flag types of multicast if necessary; otherwise, they are set to 0.

●	The next 4 bits determine the scope; for example, 1 is node-local (to all interfaces on the same node) and 2 is link local.

●	The final 112 bits define multicast groups within that scope.

The Multicast Listener Discovery (MLD) protocol allows nodes to join a multicast group and discover whether members of a group are present on a local subnet.

Broadcast addresses are not implemented in IPv6. Instead, hosts use an appropriate multicast address for a given situation. The well-known multicast addresses are ones reserved for these types of broadcast functionality. They allow an interface to transmit to all interfaces or routers on the same node or local link.

In IPv4, IP address resolution to a specific hardware interface is performed using ARP. ARP is chatty and requires every node to process its messages, whether they are relevant to the node or not. IPv6 replaces ARP with the Neighbor Discovery (ND) protocol.

Each unicast address for an interface is configured with a corresponding solicited-node multicast address. It has the prefix ff02::1:ff plus the last 24 bits of the unicast address. The solicited-node address is used by ND to perform address resolution. It greatly reduces the number of hosts that are likely to receive ND messages (down to one in most cases) and is therefore much more efficient than the old ARP broadcast mechanism.

IPV4 AND IPV6 TRANSITION MECHANISMS

A network is likely to have to run both IPv4 and IPv6 in some or all segments and for connectivity with internetworks. This interoperability can be implemented using dual stack hosts or by a tunneling mechanism.

Dual Stack

Dual stack hosts and routers can run both IPv4 and IPv6 simultaneously and communicate with devices configured with either type of address. Most modern desktop and server operating systems implement dual stack IP. Most modern dual stack systems will try to initiate communications using IPv6 by default.

Most services are addressed using names rather than IP addresses. This means that the preference for IPv6 over IPv4 or the availability of either addressing method depends on the Domain Name Server (DNS) records for the network.

Dual stack IP in Windows. (Screenshot used with permission from Microsoft.)

Tunneling

As an alternative to dual stack, tunneling can be used to deliver IPv6 packets across an IPv4 network. Tunneling means that IPv6 packets are inserted into IPv4 packets and routed over the IPv4 network to their destination. Routing decisions are based on the IPv4 address until the packets approach their destinations, at which point the IPv6 packets are stripped from their IPv4 carrier packets and forwarded according to IPv6 routing rules. This carries a high protocol overhead and is not nearly as efficient as operating dual stack hosts.

In 6to4 automatic tunneling, no host configuration is necessary to enable the tunnel. 6to4 addresses use the prefix 2002::/16. 6to4 has been widely replaced by an enhanced protocol called IPv6 Rapid Deployment (6RD). With 6RD, the 2002::/16 prefix is replaced by an ISP-managed prefix and there are various other performance improvements.

Microsoft provides support for tunneling by Windows hosts using its Teredo protocol. Teredo tunnels IPv6 packets as IPv4-based UDP messages over port 3544. Teredo requires compatible clients and servers. The open-source Miredo package implements the Teredo for UNIX/Linux operating systems.

Another option for tunneling is Generic Routing Encapsulation (GRE). GRE allows a wide variety of Network layer protocols to be encapsulated inside virtual point-to-point links. This protocol has the advantage that because it was originally designed for IPv4, it is considered a mature mechanism and can carry both v4 and v6 packets over an IPv4 network.

COMMON IPV6 ADDRESS PREFIXES

Use the following table to help you recognize some of the commonly used classes of IPv6 address by prefix notation or leading hex digits.

Type	Prefix	Leading Hex Characters

Global unicast	2000::/3	2

3

Link local unicast	fe80::/10	fe80

Multicast	ff00::/8	ff

Multicast (link local)	ff02::/16	ff02::1 (all nodes)

ff02::2 (all routers)

ff02::1:2 (DHCP)

Solicited-node	ff02::1:ff00:0/104	ff02::1:ff

Unspecified	::/128	0::0

Loopback	::1/128	::1

Documentation/Examples	2001:db8::/32	2001:db8

Globally unique unicast addresses are also widely referred to as /48s.

The 0000::/8 block (that is, IPv6 addresses where the first bits are 0000 0000) is reserved for special functions. Within this block, there are two special addresses defined:

●	Unspecified address (0:0:0:0:0:0:0:0)-A host that has  not obtained a valid address. This is often expressed as ::.

●	Loopback address (0:0:0:0:0:0:0:1)-Used for testing (for the host to send a packet to itself). This is often expressed as ::1.




























Lesson 7: Configuring and Troubleshooting Routers

Topic 7A: Compare and Contrast Routing Concepts

ROUTING TABLES AND PATH SELECTION

Most end system workstation and server computers are configured with a single network adapter connected to only one network. Although potentially capable of routing, they are not equipped with the necessary interfaces and knowledge of the location of other networks. A router is a multihomed intermediate system with links and network topology information to facilitate forwarding packets between subnets or around an internetwork.

Information about the location of other IP networks and hosts is stored in the routing table. Each entry in the routing table represents an available route to a destination network or host. The following main parameters define a routing entry:

●	Protocol-The source of the route.

●	Destination-Routes can be defined to specific hosts but are more generally directed to network IDs. The most specific destination prefix (the longest mask) will be selected as the forwarding path if there is more than one match.

●	Interface-The local interface to use to forward a packet along the chosen route. This might be represented as the IP address of the interface or as a layer 2 interface ID.

●	Gateway/next hop-The IP address of the next router along the path to the destination.

Routing table on a VyOS router showing connected and static route entries.

STATIC AND DEFAULT ROUTES

Routing table entries fall into four general categories:

●	Direct network routes, for subnets to which the router is directly attached.

●	Remote network routes, for subnets and IP networks that are not directly attached.

●	Host routes, for routes to a specific IP address. A host route has a /32 network prefix.

●	Default routes, which are used when an exact match for a network or host route is not found.

Directly Connected Routes

The IP network or subnet for each active router interface is automatically added to the routing table. These are known as directly connected routes.

Static Routes

A static route is manually added to the routing table and only changes if edited by the administrator. Configuring static routing entries can be useful in some circumstances, but it can be problematic if the routing topology changes often, as each route on each affected router needs to be updated manually.

Static routes can be configured either as non-persistent or persistent/permanent. A non-persistent route is removed from the routing table if the router is rebooted. A non-persistent route might be added as a troubleshooting action, for instance. If a static route is not reachable, it will be disabled.

Default Route

A default route is a special type of static route that identifies the next hop router for a destination that cannot be matched by another routing table entry. The destination address 0.0.0.0/0 (IPv4) or ::/0 (IPv6) is used to represent the default route. The default route is also described as the gateway of last resort. Most end systems are configured with a default route (pointing to the default gateway). This may also be the simplest way for an edge router to forward traffic to an ISP's routers.

ROUTING TABLE EXAMPLE

As examples of directly connected, static, and default route entries that might appear in a routing table, consider the following example of three routers connected in a series:

Routing tables for three routers connected in series. (Images © 123RF.com.)

First, consider the routing table of router A:

●	The router is directly connected to networks 10.0.1.0/24 (via interface G0) and 10.0.2.0/24 (via interface G1).

●	The router has been configured with static routes to 10.0.3.0/24 and 10.0.4.0/24, both of which are reachable via interface G1.

Router B has been configured in the same way, but here the networks 10.0.2.0/24 and 10.0.3.0/24 are directly connected and the paths to 10.0.1.0/24 and 10.0.4.0/24 are configured as static entries.

Router C has been configured differently. It is directly connected to 10.0.3.0/24 and 10.0.4.0/24, but the only static route configured is for 0.0.0.0/0. This is a default route. While the router has no specific knowledge of networks 10.0.1.0/24 and 10.0.2.0/24, it will forward packets for these destinations over its G0 interface.

PACKET FORWARDING

When a router receives a packet, it reads the destination address in the packet and looks up a matching destination network IP address and prefix in its routing table. If there is a match, the router will forward the packet out of one of its interfaces by encapsulating the packet in a new frame:

●	If the packet can be delivered to a directly connected network via an Ethernet interface, the router uses ARP (IPv4) or Neighbor Discovery (ND in IPv6) to determine the interface address of the destination host.

●	If the packet can be forwarded via a gateway over an Ethernet interface, it inserts the next hop router's MAC address into the new frame.

●	If the packet can be forwarded via a gateway over another type of interface (leased line or DSL, for instance), the router encapsulates the packet in an appropriate frame type.

●	If the destination address cannot be matched to a route entry, the packet is either forwarded via the default route or dropped (and the source host is notified that it was undeliverable).

Hop Count

If the packet is forwarded via a gateway, this process is repeated at each router to deliver the packet through the internetwork. Each router along the path counts as one hop. For example, in the network shown in the figure, host A takes 1 hop to communicate with LOCAL\_SRV via a directly connected interface on the LAN router. Note that the switches do not count as hops. Host B takes multiple hops (9) to communicate with REMOTE\_SRV, with traffic routed via two ISP networks. Also, observe the alternative routes that could be taken. Do any have a lower hop count?

Measuring hop count through an internetwork. (Images © 123RF.com.)

Time To Live

At each router, the Time to Live (TTL) IP header field is decreased by at least 1. This could be greater if the router is congested. The TTL is nominally the number of seconds a packet can stay on the network before being discarded. While TTL is defined as a unit of time (seconds), in practice, it is interpreted as a maximum hop count. When the TTL is 0, the packet is discarded. This prevents badly addressed packets from permanently circulating the network.

FRAGMENTATION

IP provides best-effort delivery of an unreliable and connectionless nature. Delivery is not guaranteed, and a packet might be lost, delivered out of sequence, duplicated, or delayed. It is possible that due to limitations in the underlying network, IP may fragment the packet into more manageable pieces to fit within the Maximum Transmission Unit (MTU) of the Data Link protocol frame.

In IPv4, the ID, Flags, and Fragment Offset IP header fields are used to record the sequence in which the packets were sent and to indicate whether the IP datagram has been split between multiple frames for transport over the underlying Data Link protocol. For example, the MTU of an Ethernet frame is usually 1500 bytes. An IP datagram larger than 1500 bytes would have to be fragmented across more than one Ethernet frame. A datagram passing over an internetwork might have to be encapsulated in different Data Link frame types, each with different MTUs.

Most systems try to avoid IP fragmentation. IPv6 does not allow routers to perform fragmentation. Instead, the host performs path MTU discovery to work out the MTU supported by each hop and crafts IP datagrams that will fit the smallest MTU.






Topic 7B: Compare and Contrast Dynamic Routing Concepts

DYNAMIC ROUTING PROTOCOLS

A dynamic routing protocol uses an algorithm and metrics to build and maintain a routing information base. This database stores information about the networks to which the router is connected and where there are multiple paths, prioritizes one over the rest. This information can be shared with the router's neighbors. A learned route is one that was communicated to a router by another router. A router can add learned routes from one or more routing protocols to its IP routing table.

Topology and Metrics

The algorithms used for path selection can be categorized according to the topology and metrics that they use to build and update a routing information base and prioritize optimal (or least-cost) paths. Most algorithms are classed as either distance vector or as link state. Some protocols use a hybrid of different methods to perform path selection more efficiently.

For each protocol that it runs, the router maintains a routing information base of routes discovered by that protocol. These databases are separate to the IP routing table used to determine the forwarding path. The routing protocol's database might contain more than one route to the same destination prefix. In this case, a metric is calculated to determine which path will be selected for use in the IP routing table. The path with the lowest cost metric is preferred.

The type of algorithm determines which factors are used to calculate the metric. For example, distance vector protocols use the number of hops to the destination as the metric. The route with the fewest hops is the least-cost path and will be selected for use.

Convergence

Convergence is the process whereby routers running dynamic routing algorithms agree on the network topology. Routers must be capable of adapting to changes such as newly added networks, router or router interface failures, link failures, and so on. Routers must be able to communicate changes to other routers quickly to avoid black holes and loops. A black hole means that a packet is discarded without notification back to the source; a loop causes a packet to be forwarded around the network until its TTL expires.

A network where all the routers share the same topology is described as steady state. The time taken to reach steady state is a measure of a routing protocol's convergence performance.

A flapping interface is one that frequently changes from online to offline and offline to online. Similarly, route flapping refers to a router changing the properties of a route it is advertising quickly and often. Flapping can cause serious convergence problems.

INTERIOR VERSUS EXTERIOR GATEWAY PROTOCOLS

As well as the algorithm used to determine the network topology, routing protocols can be classified according to the way they deal with administrative boundaries. A network under the administrative control of a single owner is referred to as an autonomous system (AS). An Interior Gateway Protocol (IGP) is one that identifies routes within an AS.

An Exterior Gateway Protocol (EGP) is one that can advertise routes between autonomous systems. An EGP includes a field to communicate the network's autonomous system ID and allows network owners to determine whether they can use paths through another organization's network.

Some of the most popular protocols are listed in the following table.

Protocol	Type	Class	Transport

Routing Information Protocol (RIP)	Distance Vector	IGP	UDP (port 520 or 521)

Enhanced Interior Gateway Routing Protocol (EIGRP)	Distance Vector/Hybrid	IGP	Native IP (88)

Open Shortest Path First (OSPF)	Link State	IGP	Native IP (89)

Border Gateway Protocol (BGP)	Path Vector	EGP	TCP (port 179)

Another factor used to compare routing protocols or protocol versions is whether they support classless addressing. While all modern protocols use classless addressing, you should understand that legacy classful protocols do not use subnet masks or network prefixes. They determine an IPv4network ID based on the value of the first three bits of the address.

Finally, some older protocol versions support IPv4 only. If IPv6 routing is required, you must select a dynamic routing protocol version that supports it. Most routers now operate dual stack routing of both IPv4 and IPv6. Each IP version has a separate routing table.

ROUTING INFORMATION PROTOCOL

The Routing Information Protocol (RIP) is a distance vector routing protocol. RIP only considers a single piece of information about the network topology-the next hop router to reach a given network or subnet (vector). It considers only one metric to select the optimal path to a given destination network-the one with the lowest hop count (distance).

RIP sends regular updates (typically every 30 seconds) of its entire routing database to neighboring routers. It can also send triggered updates whenever changes occur. When a router receives an update from a neighbor, it adds unknown routes to its own routing table, increases the hop count by 1, and identifies the originator of the update as the next hop to the specified networks.

In the following figure, RIP has been used to propagate route information between three routers connected in a chain. Router A learns about networks 10.0.3.0/24 and 10.0.4.0/24 from Router B. It adds 1 to the hop count metric of these routes. Router B learns about 10.0.1.0/24 from Router A and about 10.0.4.0/24 from Router C. Router A and Router C do not exchange any information directly. The distance vector process by which Router A learns about Router C's networks is often referred to as "routing by rumor."

Routers connected in series exchanging distance vector path updates.

The following example illustrates a mesh topology where there are multiple paths between networks. Router A has two possible paths to network 10.0.3.0/24, which it learns from Router B and Router C. It can forward a packet out of its G1 interface over network 10.0.2.0/24, which will take one hop to reach the destination. It could also forward the packet out of G2 and reach the destination via Router C and then Router B. This takes two hops and so is not used as the preferred route.

Routers connected in a mesh topology exchanging distance vector path updates.

If Router A's G1 link goes down, those entries will be removed from the routing table and the alternative routes via 10.0.4.0/24 will be selected:

Routers connected in a mesh topology exchanging distance vector path updates.

To help prevent looping, the maximum hop count allowed is 15. Consequently, this limits the maximum size of a RIP network, since networks that have a hop count of 16 or higher are unreachable.

RIP VERSIONS

There are three versions of RIP:

●	RIPv1 is a classful protocol and uses inefficient broadcasts to communicate updates over UDP port 520.

●	RIPv2 supports classless addressing and uses more efficient multicast transmissions over UDP port 520. It also supports authentication.

●	RIPng (next generation) is a version of the protocol designed for IPv6. RIPng uses UDP port 521.

The simplicity of RIP makes it suited to small networks with limited failover routes. Distance vector algorithms require that routers periodically propagate their entire routing table to their immediate neighbors. This is not scalable to environments with large numbers of networks. Distance vector algorithms provide for slower convergence than link state algorithms. For more complex networks with redundant paths, other dynamic routing protocols should be considered.

ENHANCED INTERIOR GATEWAY ROUTING PROTOCOL

The Interior Gateway Routing Protocol (IGRP) was developed by Cisco to provide a routing protocol for routing within a domain or autonomous system. Limitations in IGRP, such as lack of support for classless addressing, led to the development of Enhanced IGRP (EIGRP). There are versions for IPv4 and IPv6.

EIGRP is usually classed as an advanced distance vector or hybrid routing protocol. Like RIP, EIGRP is a distance vector protocol because it relies on neighboring routers to report paths to remote networks. Unlike RIP, which is based on a simple hop count metric, EIGRP uses a metric composed of administrator weighted elements. The two default elements are bandwidth and delay:

●	Bandwidth-Applies a cost based on the lowest bandwidth link in the path.

●	Delay-Applies a cost based on the time it takes for a packet to traverse the link. This metric is most important if the route is used to carry time-sensitive data, such as voice or video. Delay is calculated as the cumulative value for all outgoing interfaces in the path.

Where RIP sends periodic updates of its entire routing information base, EIGRP sends a full update when it first establishes contact with a neighbor and thereafter only sends updates when there is a topology change. This is more efficient and less disruptive to large networks, giving it the best convergence performance in many scenarios. EIGRP does use regular hello messaging to confirm connectivity with its neighbors. Unlike RIP, EIGRP maintains a topology table alongside its routing information base. The topology table is used to prevent loops while also supporting a greater number of maximum hops than RIP (nominally up to 255). In this respect, EIGRP has some similarities with link state routing protocols.

Unlike RIP, EIGRP is a native IP protocol, which means that it is encapsulated directly in IP datagrams, rather than using TCP or UDP. It is tagged with the protocol number 88 in the Protocol field of the IP header. Updates are transmitted using multicast addressing.

OPEN SHORTEST PATH FIRST

A distance vector algorithm relies on directly connected neighbors for information about remote networks. By contrast, a link state algorithm allows a router to store the complete network topology and assess the least-cost paths from this topology database.

Open Shortest Path First (OSPF) is the most widely adopted link state protocol. It is suited to large organizations with multiple redundant paths between networks. It has better convergence performance than RIP. It was designed from the outset to support classless addressing.

Where RIP and EIGRP are flat routing systems, OSPF is hierarchical. Networks and their connected hosts and routers within an autonomous system are grouped into OSPF areas. Routers within a given area share the same topological database of the networks they serve. Routers that can connect to multiple areas are known as area border routers. A backbone (always called Area 0) is created by the collection of border routers. This backbone is only visible to the border routers and invisible to the routers within a specific area.

In a given area, routers exchange OSPF hello messages, both as a form of a keep-alive packet and in order to acquire neighbors with which to exchange routing information. Neighbors share Link State Advertisement (LSA) updates to build a consistent link state database (LSDB) that represents the network topology of the area. The router applies an algorithm called shortest path first (SPF) to analyze the LSDB and add least-cost, loop free routes to its routing table. This use of a topology table of the whole network to select routes is the key difference between link state and distance vector algorithms.

The small, frequent updates used by OSPF lead to more rapid convergence and more efficiently support larger networks. The use of areas to subdivide the network minimizes the amount of routing traffic that must be passed around the network as a whole, further improving convergence performance. However, link state algorithms can be more expensive to implement because they require more CPU and memory resource.

Typical OSPF topology. (Images © 123RF.com.)

Messages are sent as multicasts using OSPF's own datagram format. This is tagged as protocol number 89 in the IP datagram's Protocol field. There are various packet types and mechanisms to ensure sequencing and reliable delivery and to check for errors. OSPF also supports plaintext or cryptographic authentication.

BORDER GATEWAY PROTOCOL

The Border Gateway Protocol (BGP) is designed to be used between routing domains in a mesh internetwork and as such is used as the routing protocol on the Internet, primarily between ISPs.

All the protocols discussed so far have been classed as interior gateway protocols (IGPs) used for communications between routers within a single routing domain, referred to an autonomous system (AS). Autonomous system numbers (ASN) are allocated to ISPs by IANA via the various regional registries. BGP is a type of exterior gateway protocol (in fact, it replaced a protocol named EGP) for communications between routers in separate autonomous systems. When BGP is used within an AS, it is referred to as Interior BGP (IBGP), and when implemented between autonomous systems, it is referred to as Exterior BGP (EBGP).

An AS is designed to hide the complexity of private networks from the public Internet. If all Internet locations had to be propagated to all Internet routers, the routing tables would become too large to process. Edge routers for each AS exchange only as much network-reachability information as is required to access other autonomous systems (the AS path), rather than networks and hosts within each AS. BGP prioritizes stability and can be slow to converge.

BGP works with classless network prefixes called Network Layer Reachability Information (NLRI). Path selection is based on multiple metrics, including hop count, weight, local preference, origin, and community. BGP is not a pure distance vector algorithm. In fact, BGP is more usually classed as a path vector routing protocol.

BGP works over TCP on port 179.

ADMINISTRATIVE DISTANCE

If a router has multiple entries to similar networks in its routing table, it must determine which route to prefer. The first determining factor is that longer prefixes are preferred over shorter ones. This is referred to as longest prefix match. For example, a routing table contains the following two entries:

198\.51.100.0/24 g0

198\.51.100.0/28 g1

If the router receives a packet for 198.51.100.1, the packet will be routed via g1 , as that has the longer and more specific prefix.

Each routing protocol supported by the router can add a single route for any given destination prefix to the routing table. This means that there might be more than one route with an identical length prefix in the routing table. Each routing protocol uses its metric to determine the least-cost path. However, as routing protocols use different methods to calculate the metric, it cannot be used to compare routes from different protocols in the overall IP routing table. Instead, an administrative distance (AD) value is used to express the relative trustworthiness of the protocol supplying the route. Default AD values are coded into the router but can be adjusted by the administrator if necessary.

Source	AD

Local interface/Directly connected	0

Static route	1

BGP	20

EIGRP	90

OSPF	110

RIP	120

Unknown	255

This means, for example, that given identical prefix lengths, a static route will be preferred to anything other than directly connected networks and that a route discovered by OSPF would be preferred to one reported by RIP. The value of 255 for unknown routes means that they will not be used.

Conversely, a static route with a high AD could be defined to function as a backup if a learned route update fails. In normal circumstances, the router will prefer the learned route because it has a lower AD.

CLASSLESS INTER-DOMAIN ROUTING

Classless addressing was designed to solve two major problems of the classful addressing scheme as more and more networks joined the internet through the early 1990s. The first was that network addresses, specifically, Class B addresses, were becoming very scarce and the second was near exponential growth in Internet routing tables. Classless Inter-Domain Routing (CIDR) uses bits normally assigned to the network ID to mask the complexity of the subnet and host addressing scheme within that network. CIDR is also sometimes described as supernetting.

Using CIDR/supernetting to summarize four /24 networks as one /22 network.

For example, rather than allocate a Class B (or /16) network address to a company, several contiguous Class C (or /24) addresses could be assigned. Four /24 network addresses gives 1,016 hosts. However, this would mean complicated routing with many entries in the routing tables to represent four IP networks at the same location. Using CIDR collapses these routing entries into one single entry. If the network addresses assigned to a company were 198.51.101.0 through to 198.51.103.0 and you wanted to view this as one network, you need to allocate two bits from the network address to summarize the four networks. This makes the supernet prefix /22 or the subnet mask 255.255.252.0.

The ANDing process is still used to determine whether to route. If the ANDed result reveals the same network ID as the destination address, then it is the same network. In this next example, the first IP addresses belong to the supernet, but the second is on a different company's network:


Comparing network prefixes.

Routers external to the network just use this /22 prefix, so the complexity of the LAN subnets is hidden and doesn't need to clog up their routing tables. The LAN's internal routers use the /24 prefix or even multiple prefixes to create subnets of different sizes.

CIDR public and private route advertisements. (Images © 123RF.com.)

Remember that both subnetting and supernetting require the use of a classless routing protocol (one that does not determine the network mask based on the first octet in the IP address). Dynamic routing protocols that support classless addressing include RIPv2, EIGRP, OSPF, and BGPv4.

VARIABLE LENGTH SUBNET MASKS

The IPv4 address space is close to being exhausted, making it difficult for ISPs to allocate public addresses to the companies that want them. To mitigate this, more efficient methods of allocating IP addresses must be used. Supernetting simplifies the information Internet routers need to locate IP networks. A complementary classless addressing technique, called variable length subnet masking (VLSM), allows a network designer to allocate ranges of IP addresses to subnets that match the predicted need for numbers of subnets and hosts per subnet more closely. Without VLSM, you have to allocate subnetted ranges of addresses that are the same size and use the same subnet mask throughout the network. This typically means that some subnets have many wasted IP addresses or additional routing interfaces must be installed to connect several smaller subnets together within a single building or department.

VLSM allows different length netmasks to be used within the same IP network, allowing more flexibility in the design process.

For this example, consider a company with three sites, each with differing network sizes and IP address requirements. There are also subnets representing point-to-point WAN links between the routers.

VLSM requirements for host addresses. (Images © 123RF.com.)

VLSM design usually proceeds by identifying the subnets with the most hosts and organizing the scheme in descending order. As with any subnet calculations, it helps to remember that each power of 2 is double the previous one:

22	23	24	25	26	27	28

4	8	16	32	64	128	256

1. `	`In the example, the largest requirement is for 80 hosts. 26 has a maximum of 64 values, which is not enough, so the nearest match in the table is 2 7 . This tells us that we need 7 bits for host addressing. This actually allows for 126 host addresses once the network and broadcast addresses have been accounted for (2 7 -2). Using 7 bits makes the prefix /25 (32 minus 7).
1. `	`The next requirement is technically met by a 5-bit host address space, but as this allows for exactly 30 addresses, there would be no room for growth. Using 6 bits might be safer, but for this scenario, we will choose the closest match and adopt the /27 prefix.
1. `	`The next three requirements are for 8, 12, and 12 hosts. These all require 4 bits, which gives up to 14 usable addresses.
1. `	`The routers use point-to-point links, so no more than two addresses will ever be required. This can be met by selecting a /30 prefix.

VLSM DESIGN

The final VLSM design is summarized in the following table:

Office/Subnet	Required Number of IP Addresses	Mask Bits	Actual Number of IP Addresses	Prefix

Main Office 1 (Router A)	80	7	126	/25

Main Office 2 (Router A)	30	5	30	/27

Main Office 3 (Router A)	8	4	14	/28

Branch Office (Router B)	12	4	14	/28

Branch Office (Router C)	12	4	14	/28

Router A - Router B	2	2	2	/30

Router A - Router C	2	2	2	/30

Router B - Router C	2	2	2	/30

All subnets except for Main Office 2 have room for growth.

VLSM design address space utilization.

In fact, if you analyze the final design, you will find that there are 36 unused addresses at the end of the range. Consequently, there would have been space to use a /26 prefix for the group of 30 hosts.

The actual IP address ranges generated by the VLSM design are shown in this table.

Office	Subnet	Subnet Mask	Useable Host Address Range	Broadcast Address

Main Office 1 (Router A)	198.51.100.0/25	255.255.255.128	1-126	127

Main Office 2 (Router A)	198.51.100.128/27	255.255.255.224	129-158	159

Main Office 3 (Router A)	198.51.100.160/28	255.255.255.240	161-174	175

Branch Office (Router B)	198.51.100.176/28	255.255.255.240	177-190	191

Branch Office (Router C)	198.51.100.192/28	255.255.255.240	193-206	207

Router A - Router B	198.51.100.208/30	255.255.255.252	209-210	211

Router A - Router C	198.51.100.212/30	255.255.255.252	213-214	215

Router B - Router C	198.51.100.216/30	255.255.255.252	217-218	219

The VLSM network topology can be summarized by this diagram:


Topic 7C: Install and Troubleshoot Routers

EDGE ROUTERS

Routers serve both to link physically remote networks and subdivide autonomous IP networks into multiple subnets. Router placement is primarily driven by the IP networks and subnets that have been created:

●	Hosts with addresses in the same subnet or IP network must not be separated by a router.

●	Conversely, hosts with addresses in different subnets or IP networks must be separated by a router.

Edge routers, placed at the network perimeter, are typified by distinguishing external (Internet-facing) and internal interfaces. These routers can perform framing to repackage data from the private LAN frame format to the WAN Internet access frame format. The customer's router is referred to as the customer edge (CE), while the service provider's router is referred to as the provider edge (PE).

Edge routers designed to work with DSL or cable broadband access methods are called small office/home office (SOHO) routers. Routers with similar integrated functionality are often deployed by enterprises for branch office connectivity.

An integrated services router. This type of device combines DSL Internet access with Ethernet switch, Wi-Fi, and VoIP for a "one box" solution for remote sites and branch offices. (Image © 123RF.com.)

Routers designed to service medium to large networks are complex and expensive appliances. They feature specialized processors to handle the routing and forwarding processes, and memory to buffer data. Most routers of this class will also support plug-in cards for WAN interfaces. Another important feature is support for different methods of configuring site-to-site virtual private networks (VPNs).

An advanced services router. This type of device provides network edge connectivity over Carrier Ethernet networks. (Image © 123RF.com.)

INTERNAL ROUTERS

An internal router has no public interfaces. Internal routers are positioned to implement whatever network topology is required. The figure shows a simplified example of a typical network configuration. An edge router/firewall provides access to the Internet. Traffic between the local subnets is controlled by a separate internal router.

Network placement of edge and internal routers. (Images © 123RF.com.)

A network may also use a more complex topology, such as division into OSPF areas.

Subinterfaces

Many networks are segmented using the virtual LAN (VLAN) feature of managed switches. Traffic between VLANs must be routed. In this scenario, it is possible to use a router with a single interface (a one-armed router or router on a stick) connected to a trunk port on the switch. The trunk port carries all the VLAN-to-VLAN traffic that must be routed. The router's physical interface is configured with multiple subinterfaces or virtual interfaces. Each subinterface is configured with a specific VLAN ID. The subinterface receives traffic from a given VLAN and then routes it to the subinterface serving the destination VLAN.

Router on a Stick topology with subinterfaces serving each VLAN/subnet. (Images © 123RF.com.)

Layer 3 Capable Switches

Passing traffic between a router appliance and the switch over a trunk link is relatively inefficient and does not scale well to tens of VLANs. Consequently, enterprise networks usually deploy layer 3 switches at the core of their networks. A layer 3 capable switch is one that is optimized for routing between VLANs. It can use static and dynamic routing to identify which VLAN an IP address should be forwarded to. A layer 3 switch can maintain a mapping table of IP addresses to MAC addresses so that when a path is established, it can use low-latency hardware-based forwarding. However, layer 3 switches do not typically have WAN interfaces and so are not usually used for routing at the network edge.

ROUTER CONFIGURATION

As a router appliance does not have a screen or keyboard, it is configured locally either via a serial connection known as a console port or (more usually) remotely over the network by using a protocol such as Secure Shell (SSH). SSH can be used to communicate with the router via the IP address of any configured interface. However, as any given physical interface could suffer a hardware fault or be temporarily unavailable for various reasons, it is considered best practice to create a virtual interface, known as a loopback interface, in the router's operating system and assign it an IP address for use in remotely managing the router. This is a way of giving the router an internal IP address, not connected to any physical network, that is therefore not reliant on a specific network link being available.

Configuring RIP on a VyOS-based software router. The host can be configured at a local terminal or from a remote computer over Secure Shell (SSH).

Having placed the router at an appropriate point in the network, connected its cabling, and established a management session, the principal configuration tasks are as follows:

●	Apply an IP configuration to each interface.

●	Configure one or more routing protocols and/or static routes so that the router can serve its function.

The show route, show ip route , show ipv6 route , or similar command will output the active routing table. As well as destination, gateway, AD/metric, and interface, the output will show the source of the route, identified as a letter code (C = connected, S = static, R = RIP, B = BGP, D = EIGRP, O = OSPF, and so on).

ROUTE

The route command is used to view and modify the routing table of end system Windows and Linux hosts.

Apart from loopback addresses and the local subnet, the routing table for an end system generally contains a single entry for the default route. The default route is represented as the destination 0.0.0.0/0. Any traffic that is not addressed to the local subnet is sent over this default route.

In Windows, to show the routing table, run route print.

IPv4 and IPv6 routing tables for a Windows host. For IPv4, the host uses 10.1.0.254 as its default gateway. The IPv6 configuration has no route from the local network. (Screenshot used with permission from Microsoft.)

To add a route, the syntax for the Windows version of the tool is:

route [-f -p] add DestinationIP mask Netmask GatewayIP metric MetricValue if Interface

The variables in the syntax are defined as:

●	DestinationIP is a network or host address.

●	Netmask is the subnet mask for DestinationIP.

●	GatewayIP is the router to use to contact the network or host.

●	MetricValue is the cost of the route.

●	Interface is the adapter the host should use (used if the host is multihomed).

For example:

route add 192.168.3.0 mask 255.255.255.0 192.168.5.1 metric 2

Routes added in this manner are nonpersistent by default. This means that they are stored in memory and will be discarded if the machine is restarted. A route can be permanently configured (stored in the registry) using the -p switch. The tool also allows for routes to be deleted ( route delete ) and modified ( route change ).

The Linux version of route performs the same function, but the syntax is different. The routing table is shown by entering route with no parameters. The change parameter is not supported, and the command cannot be used to add persistent routes. A nonpersistent route can be added using the following general syntax:

route add -net 192.168.3.0 netmask 255.255.255.0 metric 2 dev eth0

Output of Linux route command.

The iproute2 suite of tools is designed to replace deprecated legacy command-line tools in Linux. You can use ip route show and ip route add to achieve the same ends.

TRACERT AND TRACEROUTE

The traceroute tool allows you to test the whole path between two nodes with a view to isolating the node or link that is causing the problem.

traceroute

traceroute is supported on Linux and router OSes (such as Cisco IOS). traceroute uses UDP probe messages by default. The command issues a UDP probe for port 32767 with a TTL of 1. The first hop should reduce this to zero and respond with an ICMP Time Exceeded message. The command then increments the TTL by one and sends a second probe, which should reach the second hop router. This process is repeated until the end node is reached, which should reply with an ICMP Port Unreachable response.

The output shows the number of hops, the IP address of the ingress interface of the router or host (that is, the interface from which the router receives the probe), and the time taken to respond to each probe in milliseconds (ms). If no acknowledgment is received within the timeout period, an asterisk is shown against the probe. Note that while this could indicate that the router interface is not responding, it could also be that the router is configured to drop packets with expired TTLs silently.

traceroute can be configured to send ICMP Echo Request probes rather than UDP by using traceroute -I . The traceroute -6 or traceroute6 commands are used for IPv6 networks.

tracert

On a Windows system, the same function is performed using the tracert command. tracert uses ICMP Echo Request probes by default. The command issues an Echo Request probe with a TTL of 1. The first hop should reduce this to zero and respond with a Time Exceeded response. tracert then increments the TTL by one each time to discover the full path.

Using tracert in Windows to plot the path from a host in the UK to CompTIA's web server. (Screenshot used with permission from Microsoft.)

tracert can be used with several switches, which must precede the target IP address or host.

You can use the -d switch to suppress name resolution, -h to specify the maximum number of hops (the default is 30), and -w to specify a timeout in ms (the default is 4000). If, after increasing the value, destinations are then reachable, you probably have a bandwidth issue to resolve. When used with host names (rather than IP addresses), tracert can be forced to use IPv6 instead of IPv4 by adding the -6 switch.

tracert -6 www.microsoft.com

MISSING ROUTE ISSUES

If you can ping a host's default gateway, but you cannot ping some or all hosts on remote networks, then you should suspect a routing issue. In many cases, this will be because a router has gone offline and there is no alternative path to the network. You should also be prepared to consider configuration issues too.

If you suspect a problem with router configuration and the network topology, use traceroute to try to identify where the network path is failing and the route or show route commands to investigate the routing tables of intermediate systems at that point in the path.

When inspecting a routing table, you can use show ip route w.x.y.z to check for the presence of a route to a specific IP network. A missing route may arise because a required static routing entry has not been entered or has been entered incorrectly. Missing routes may also arise because a router fails to communicate with its neighbors and so does not receive routing protocol updates. Performing a device configuration review means checking that the running configuration matches the documented baseline.

You might start troubleshooting this by pinging the router nodes that are neighbors of the system with the issue to check basic connectivity. If there is a network path and the neighbors are up, you would investigate the protocol configuration (perhaps there is an authentication issue or incorrect parameter).

ROUTING LOOP ISSUES

A routing loop occurs when two routers use one another as the path to a network. Packets caught in a routing loop circle around until the TTL expires. One symptom of a potential routing loop is for routers to generate ICMP Time Exceeded error messages.

A routing loop created between routers B and C. (Images © 123RF.com.)

Routing protocols use various mechanisms to prevent loops. For example, distance vector protocols use the following mechanisms:

●	Maximum hop count-If the cost exceeds a certain value (16 in RIP), the network is deemed unreachable. A poison route is one advertised with a hop count of 16. This can provide an explicit failure notice to other routers.

●	Holddown timer-If a node declares a network unreachable, its neighbors start a holddown timer. Any updates about that route received from other nodes are discarded for the duration of the timer. This is designed to ensure that all nodes have converged information about an unreachable network.

●	Split horizon-Prevents a routing update from being copied back to the source. In the example above, this would prevent router C from sending an update about a route to router A via router B to router B.

Link state protocols try to ensure that each node has a consistent view of the network through continual, timely updates flooded to all nodes in the routing domain. A loop in a link state routing domain typically indicates that updates are not being propagated correctly.

You can use traceroute to diagnose a routing loop by looking for IP addresses that appear multiple times in the output.

ASYMMETRICAL ROUTING ISSUES

Asymmetrical routing refers to a topology where the return path is different to the forward path. This is common where there are load balancers and where routing takes place over multiple redundant paths across the Internet or other complex internetwork. Asymmetric routing is problematic where the return path is much higher latency than the forward path or where the difference between the paths causes stateful firewall or network address translation (NAT) devices to filter or drop communications. These types of devices should not be placed in the middle of a network where the forward and return paths could diverge. Problematic asymmetric routing could be caused by incorrectly configured static or dynamic routes. You should use traceroute from both sender and receiver to compare the per-hop latency to identify where the routing topology is misconfigured.

LOW OPTICAL LINK BUDGET ISSUES

As well as the routing configuration, you should also consider physical and data link issues when troubleshooting WAN and datacenter routing. One such issue is poor connectivity across fiber optic links.

An optical link budget, or loss budget, is the amount of loss suffered by all components along a fiber transmission path. This is calculated using the following parameters:

●	Attenuation-This is the loss over the length of the cable, based on fiber type and the wavelength used. Single mode has a loss of up to 0.4 dB/km, while multimode can be from 0.8 dB/km to 3 dB/km.

●	Connectors-Each connector in the path incurs a loss, usually assumed to be 0.75 dB.

●	Splices-Additional splices in the cable are budgeted at around 1 dB for mechanical and 0.3 dB for fusion.

Typically, an estimated loss budget is calculated when planning the link. The link is tested at deployment using an optical time domain reflectometer (OTDR) to derive an actual value. Differences between these values may reveal an installation fault or some unexpected source of signal loss.

FOA have a loss budget calculator at thefoa.org/tech/ref/Loss\_Budget/Loss\_Budget.htm.

The loss budget must be less than the power budget. The power budget is calculated from the transceiver transmit (Tx) power and receiver (Rx) sensitivity, which are both typically measured in dB per milliwatt or dBm. For example, if Tx is -8 dBm and Rx is -15 dBm, then the power budget is 7 dB.

dBm measures signal strength against a reference value, where 0 dBm is 1 milliwatt. A negative dBm is typical of Ethernet transceivers, which output less than 1 mw.

If the loss budget is 5 dB, the margin between the power budget and loss budget will be 2 dB. Margin is a safety factor to account for suboptimal installation conditions (such as bends or stress), aging, repair of accidental damage (additional splices), and performance under different thermal conditions (extreme temperatures can cause loss).

If the margin between the transmitter power and link budget is low, the link is less likely to achieve the expected bandwidth. There may be opportunities to improve performance with better or fewer splices, or it may be necessary to use an amplifier to boost the signal. Most outdoor plants would be designed with a margin of at least 5 dB. In a datacenter where conditions are less variable a lower margin might be acceptable.
































Lesson 8: Explaining Network Topologies and Types

Topic 8A: Explain Network Types and Characteristics

CLIENT-SERVER VERSUS PEER-TO-PEER NETWORKS

A network comprises nodes and links. Intermediate system nodes perform a forwarding function, while end system nodes are those that send and receive data traffic. End system nodes can be classified as either clients or servers:

●	A server makes network applications and resources available to other hosts.

●	A client consumes the services provided by servers.

A client-server network is one where some nodes, such as PCs, laptops, and smartphones, act mostly as clients. The servers are more powerful computers. Application services and resources are centrally provisioned, managed, and secured.

A peer-to-peer network is one where each end system acts as both client and server. This is a decentralized model where provision, management, and security of services and data is distributed around the network.

Business and enterprise networks are typically client-server, while residential networks are more often peer-to-peer (or workgroup). However, note that in a client-server network, often, nodes will function as both clients and servers at the same time. For example, a computer hosting a web application acts as a server to browser clients but is itself a client of database services running on other server computers. It is the centrally administered nature of the network that really defines it as client-server


NETWORK TYPES

A network type refers primarily to its size and scope. The size of a network can be measured as the number of nodes, while the scope refers to the area over which nodes sharing the same network address are distributed.

Local Area Networks

A local area network (LAN) describes a network type that is confined to a single geographical location. In a LAN, all nodes and segments are directly connected with cables or short-range wireless technologies. It does not require a leased telecommunication system to function. Most of the network infrastructure in a LAN would be directly owned and managed by a single organization. Some typical examples of LANs include:

●	Home/residential networks-with an Internet router and a few computers, plus mobile devices, gaming consoles, and printers.

●	Small office/home office (SOHO) networks-A business-oriented network possibly using a centralized server in addition to client devices and printers, but often still using a single Internet router/switch/access point to provide connectivity.

●	Small and medium-sized enterprise (SME) networks-A network supporting dozens of users. Such networks would use structured cabling and multiple switches and routers to provide connectivity.

●	Enterprise LANs-A larger network with hundreds or thousands of servers and clients. Such networks would require multiple enterprise-class switch and router appliances to maintain performance levels. The term campus area network (CAN) is sometimes used for a LAN that spans multiple nearby buildings.

●	Datacenters-A network that hosts only servers and storage, not end user client devices.

The term wireless local area network (WLAN) is used for LANs based on Wi-Fi. Open (public) WLANs are often referred to as hotspots.

Wide Area Networks

A wide area network (WAN) is a network of networks, connected by long-distance links. A typical enterprise WAN would connect a main office site with multiple branch office sites, possibly in different countries. A WAN could link two or more large LANs or could be used for remote workers connecting to an enterprise network via a public network such as the Internet. WANs are likely to use leased network devices and links, operated and managed by a service provider.

The term metropolitan area network (MAN) is sometimes used for something a bit smaller than a WAN: a city-wide network encompassing multiple buildings.

Personal Area Networks

The terms personal area network (PAN) and wireless PAN (WPAN) have gained some currency over the last few years. They refer to the fact that a person might establish close-range network links between a variety of devices, such as smartphones, tablets, headsets, and printers. As digital and network functionality continues to be embedded in more and more everyday objects, appliances (the Internet of Things), and clothing, the use of PANs will only grow.

NETWORK TOPOLOGY

Where the type defines the network scope, the topology describes the physical or logical structure of the network in terms of nodes and links.

The physical network topology describes the placement of nodes and how they are connected by the network media. For example, in one network, nodes might be directly connected via a single cable; in another network, each node might connect to a switch via separate cables. These two networks have different physical topologies.

The logical topology describes the flow of data through the network. For example, given the different physical network topologies described previously, if in each case the nodes can send messages to one another, the logical topology is the same. The different physical implementations (directly connected via a cable versus connected to the same switch) achieve the same logical layout.

In the simplest type of topology, a single link is established between two nodes. This is called a point-to-point link. Because only two devices share the connection, they are guaranteed a level of bandwidth.

Physical point-to-point topologies using different media types for half-duplex and duplex communications.

A point-to-point link can be a physical or logical topology. For example, on a WAN, two routers might be physically linked via multiple intermediate networks and physical devices but still share a logical point-to-point link, where each can address only the other router. With either a physical or logical topology, it is the 1:1 relationship that defines a point-to-point link.

STAR TOPOLOGY

In a star topology, each endpoint node is connected to a central forwarding node, such as a hub, switch, or router. The central node mediates communications between the endpoints. The star topology is the most widely used physical topology. For example, a typical SOHO network is based around a single Internet router appliance that clients can connect to with a cable or wirelessly. The star topology is easy to reconfigure and easy to troubleshoot because all data goes through a central point, which can be used to monitor and manage the network. Faults are automatically isolated to the media, node (network card), or the hub, switch, or router at the center of the star.

Star topologies using different types of concentrator.

You may also encounter the hub-and-spoke topology. This is the same layout as a star topology. The hub-and-spoke terminology is used when speaking about WANs with remote sites.


MESH TOPOLOGY

A mesh topology is commonly used in WANs, especially public networks like the Internet. In theory, a mesh network requires that each device has a point-to-point link with every other device on the network (fully connected). This approach is normally impractical, however. The number of links required by a full mesh is expressed as n ( n -1)/2, where n is the number of nodes. For example, a network of just four nodes would require six links, while a network of 40 nodes would need 780 links! Consequently, a hybrid approach is often used, with only the most important devices interconnected in the mesh, perhaps with extra links for fault tolerance and redundancy. In this case, the topology is referred to as a partial mesh.

Fully connected and partial mesh topology examples.

Mesh networks provide excellent redundancy, because other routes, via intermediary devices, are available between locations if a link failure occurs.


RING TOPOLOGY

In a physical ring topology, each node is wired to its neighbor in a closed loop. A node receives a transmission from its upstream neighbor and passes it to its downstream neighbor until the transmission reaches its intended destination. Each node can regenerate the transmission, improving the potential range of the network.

Ring topology.

The physical ring topology is no longer used on LANs, but it does remain a feature of many WANs. Two ring systems (dual counter-rotating rings) can be used to provide fault tolerance. These dual rings allow the system to continue to operate if there is a break in one ring.

BUS TOPOLOGY

A physical bus topology with more than two nodes is a shared access topology, meaning that all nodes share the bandwidth of the media. Only one node can be active at any one time, so the nodes must contend to put signals on the media. All nodes attach directly to a single cable segment via cable taps. A signal travels down the bus in both directions from the source and is received by all nodes connected to the segment. The bus is terminated at both ends of the cable to absorb the signal when it has passed all connected devices.

Physical bus topology. (Images © 123RF.com.)

This type of physical bus topology is the basis of the earliest Ethernet networks but is no longer in widespread use. Bus networks are comparatively difficult to reconfigure (adding or removing nodes can disrupt the whole network), impose limitations on the maximum number of nodes on a segment of cable, and are difficult to troubleshoot (a cable fault could be anywhere on the segment of cable). Perhaps most importantly, a fault anywhere in the cable means that all nodes are unable to communicate.

A bus network does allow cables to be connected using a device called a repeater. Two lengths of cable joined by a repeater is considered one length of cable for the purpose of the bus topology. A repeater is a passive device and is not considered a network node in the way that a switch or router would.

A logical bus topology is one in which nodes receive the data transmitted all at the same time, regardless of the physical wiring layout of the network. Because the transmission medium is shared, only one node can transmit at a time. Nodes within the same logical bus segment are in the same collision domain. When Ethernet is deployed with a legacy hub appliance, this can be described as a physical star-logical bus topology.

HYBRID TOPOLOGY

A hybrid topology is anything that uses a mixture of point-to-point, star, mesh, ring, and bus physical and/or logical topologies. As noted, an Ethernet hub establishes a logical bus topology, but the physical topology is a star. Another common legacy topology is the star-wired ring, where nodes in the ring are wired to a central multistation access unit (MAU) rather than to its neighbors. The MAU implements the logical ring and handles token passing.

On modern networks, hybrid topologies are often used to implement redundancy and fault tolerance or to connect sites in WANs:

●	Hierarchical star-corporate networks are often designed in a hierarchy, also known as a tree topology. This can be combined with a star topology to implement each node in the overall tree. The links between nodes in the tree are referred to as backbones or trunks because they aggregate and distribute traffic from multiple different areas of the network.

●	Hierarchical star-mesh-Alternatively, nodes at the top of the hierarchy can be configured in a partial or full mesh for redundancy. Switches lower in the hierarchy establish star topologies that connect end systems to the network.

●	Star of stars-A WAN might be configured as a hub-and-spoke between a central office and branch offices, with each site implementing a star topology to connect end systems. This is also referred to as a snowflake topology.

●	Star with ring-Alternatively, a ring topology might be used to connect geographically separate sites, with each site implementing a star topology to connect end systems.

Hierarchical hybrid topology example where a mesh network distributes traffic between multiple star networks.

Topic 8B: Explain Tiered Switching Architecture

THREE-TIERED NETWORK HIERARCHY

A hierarchical model breaks down a large and complex network design into smaller sections based on the functions performed. Each function can be assessed by network designers to identify the most efficient hardware and software to use to implement it.

As a practical example of this type of model, many corporate office networks follow Cisco's design principles for a three-tiered hierarchy: access, distribution, and core.

Core, distribution, and access layers in three-tiered network architecture. (Images © 123RF.com.)

Access/Edge Layer

The access or edge layer allows end-user devices, such as computers, printers, and smartphones to connect to the network. The access layer is implemented for each site using structured cabling and wall ports for wired access and access points for wireless access. Both are ultimately connected to workgroup switches. Switches deployed to serve the access layer might also be referred to as LAN switches or data switches. End systems connect to switches in the access/edge layer in a star topology. There are no direct links between the access switches.

Distribution/Aggregation Layer

The distribution or aggregation layer provides fault-tolerant interconnections between different access blocks and either the core or other distribution blocks. Each access switch has full or partial mesh links to each router or layer 3 switch in its distribution layer block. The distribution layer is often used to implement traffic policies, such as routing boundaries, filtering, or quality of service (QoS).

The layer 3 capable switches used to implement the distribution/aggregation layer have different capabilities to the layer 2 only workgroup switches used in the access tier. Rather than 1 Gbps access ports and 10 Gbps uplink ports, as would be typical of a workgroup switch, basic interfaces on an aggregation switch would be 10 Gbps and uplink/backbone ports would be 40 Gbps (or possibly 40 Gbps/100 Gbps). Layer 3 switches work on the principle of "route once, switch many," which means that once a route is discovered, it is cached with the destination MAC address and subsequent communications are switched without invoking the routing lookup. While a router uses a generic processor and firmware to process incoming packets, a layer 3 switch uses an application-specific integrated circuit (ASIC). This can have an impact on the relative performance of the two types of devices. Layer 3 switches can be far faster, but they are not always as flexible. Layer 3 switches cannot usually perform WAN routing and work with interior routing protocols only. Often layer 3 switches support Ethernet only.

An example of a core/distribution switch. (Image © 123RF.com.)

Core Layer

The core layer provides a highly available network backbone. Devices such as client and server computers should not be attached directly to the core. Its purpose should be kept simple: provide redundant traffic paths for data to continue to flow around the access and distribution layers of the network. Routers or layer 3 switches in the core layer establish a full mesh topology with switches in distribution layer blocks.

In a two tier or collapsed core model, the core must be implemented as a full mesh. This is impractical if there are large numbers of core switches.

SPANNING TREE PROTOCOL

The three-tiered network model makes use of mesh or partial mesh topologies to implement redundant links. Multiple paths are part of good network design as they increase resilience; if one link fails, then the network can remain operational by forwarding frames over a different path. However, as a layer 2 protocol, Ethernet has no concept of time to live, so layer 2 broadcast traffic could continue to loop through a network with multiple paths indefinitely.

The spanning tree protocol (STP) is a means for the bridges or switches to organize themselves into a hierarchy. The switch at the top of the hierarchy is the root. The switch with the lowest ID, comprising a priority value and the MAC address, will be selected as the root.

Each switch then determines the shortest path to the root bridge by exchanging information with other switches. This STP information is packaged as bridge protocol data unit (BPDU) multicast frames. A port that forwards "up" to the root, possibly via intermediate switches, is identified as a root port. Ports that can forward traffic "down" through the network with the least cost are identified as designated ports. A port that would create a loop is identified as a blocking or non-designated port. Subsequently, bridges exchange Topology Change Notifications if devices are added or removed, enabling them to change the status of forwarding/blocked ports appropriately.

Spanning tree configuration. (Images © 123RF.com.)

This image shows the minimum configuration necessary to prevent loops in a network with three bridges or switches. The root bridge has two designated ports (DP) connected to Bridge A and Bridge B. Bridges A and B both have root ports (RP) connected back to the interfaces on the root bridge. Bridges A and B also have a connection directly to one another. On Bridge A, this interface is active and traffic for Bridge B can be forwarded directly over it. On Bridge B, the interface is blocked (BP) to prevent a loop, and traffic for Bridge A must be forwarded via the root bridge.

SPANNING TREE PROTOCOL CONFIGURATION

If a switch supports STP (not all do), it should operate by default without configuration. An administrator can (and should) set the priority value to make the choice of one switch as root over another more likely. The root will usually be part of a high-bandwidth backbone or core switch group; performance will suffer if a switch on a low-bandwidth segment becomes root.

Viewing spanning tree configuration on a Cisco switch. (Image © and Courtesy of Cisco Systems, Inc. Unauthorized use not permitted.)

The following table shows the different states that a port can be in.

State	Forwards Frames?	Learns MACs?	Notes

Blocking	No	No	Drops all frames other than BPDUs.

Listening	No	No	Port is listening for BPDUs to detect loops.

Learning	No	Yes	The port discovers the topology of the network and builds the MAC address table.

Forwarding	Yes	Yes	The port works as normal.

Disabled	No	No	The port has been disabled by the administrator.

When all ports on all switches are in forwarding or blocking states, the network is converged. When the network is not converged, no communications can take place. Under the original 802.1D standard, this made the network unavailable for extended periods-tens of seconds-during configuration changes. STP is now more likely to be implemented as 802.1D-2004/802.1w or Rapid STP (RSTP). The rapid version creates outages of a few seconds or less. In RSTP, the blocking, listening, and disabled states are aggregated into a discarding state.

SWITCHING LOOP AND BROADCAST STORM ISSUES

A switching loop is where flooded frames circulate the network perpetually. Because switches flood broadcasts, such as ARP or DHCP requests, out all ports, these frames will go down one link to the next switch, which will send the broadcast back up the redundant link, and back to the originating switch. As this repeats, the switches start to see source MAC addresses associated with multiple ports and so clear the MAC address table mapping, which causes them to start flooding unicast traffic too.

Without intervention, this loop will continue indefinitely, causing a broadcast storm. A broadcast storm will cause network utilization to go to near maximum capacity, and the CPU utilization of the switches to jump to 80 percent or more. This makes the switched segment effectively unusable until the broadcast storm stops. A broadcast storm may quickly consume all link bandwidth and crash network appliances.

If there is a loop, spanning tree should shut down the port. This will isolate the problem to a segment of the network. Inspect physical ports that correspond to the disabled interfaces for looped connections. At the patch panel, this could mean a patch cable that connects two ports on the same switch. On the office floor, it could mean a patch cable between two wall ports. Check the switch for log events related to MAC address flapping.

If a broadcast storm occurs on a network where STP is already enabled, you should investigate the following potential causes:

●	Verify compatible versions of STP are enabled on all switches.

●	Verify the physical configuration of segments that use legacy equipment, such as Ethernet hubs.

●	Investigate networking devices in the user environment and verify that they are not connected as part of a loop. Typical sources of problems include unmanaged desktop switches and VoIP handsets.

Topic 8C: Explain Virtual LANs

VIRTUAL LAN IDS AND MEMBERSHIP

At the data link and network layers, a segment is a group of hosts in the same broadcast domain. At the network layer, this group is identified as either an IP network or as a subnet within an IP network. At the data link layer, a broadcast domain can be established by connecting the hosts to the same unmanaged switches. This hardware-based approach is inflexible, however, so managed switches allow the configuration of virtual LANs (VLANs) to isolate ports to separate broadcast domains.

If a VLAN were to contain multiple IP networks or subnets, nodes would receive broadcast traffic for all the subnets. This would be a very complex configuration, however. Normally, the network would be designed with a 1:1 mapping between VLANs and subnets.

Implementing VLANs can reduce broadcast traffic when a network has expanded beyond a certain number of hosts or users. As well as reducing the impact of broadcast traffic, from a security point of view, each VLAN can represent a separate zone. VLANs are also used to separate nodes based on traffic type and the need for Quality of Service. For example, it is commonplace to put all VoIP handsets on a voice VLAN to minimize interference coming from nodes that are sending email or downloading large files on the same network. The switches and routers can then be configured to give the VoIP VLAN priority over ordinary data VLANs.

The VLAN with ID 1 is referred to as the default VLAN. Unless configured differently, all ports on a switch default to being in VLAN 1.

The simplest means of assigning a node to a VLAN is by configuring the port interface on the switch with a VLAN ID in the range 2 to 4,094. For example, from the switch management interface, ports 1 through 10 could be configured as a VLAN with the ID 10 and ports 11 through 20 could be assigned to VLAN 20. Host A connected to port 2 would be in VLAN 10, and host B connected to port 12 would be in VLAN 20. Host A and Host B would not be able to communicate directly, even though they are connected to the same switch. Each VLAN is typically configured with its own subnet address and IP address range. Communications between VLANs must go through an IP router or layer 3 capable switch.

Cumulus VX switch output showing switch ports swp 5-8 configured in VLAN 100 and ports 9-12 in VLAN 200.

This type of port-based assignment is described as a static VLAN. Nodes or hosts can also be assigned to dynamic VLANs using some feature of the host, such as its MAC address or authentication credentials supplied by the user.

TRUNKING AND IEEE 802.1Q

On a large network, a single switch will not provide enough ports for all the hosts that need to be connected to the network. This means that multiple switches must be interconnected to build the network fabric. Multiple switches may also be deployed to provide redundant links. The interconnections between switches are referred to as trunks. One of the ports on each switch would be configured as a trunk port for this purpose.

VLAN trunk link. (Images © 123RF.com.)

When frames designated for different VLANs are transported across a trunk, the VLAN ID (VID) of each frame must be preserved for the receiving switch to forward it correctly. VIDs are normally defined by the IEEE 802.1Q standard. Under 802.1Q, per-VLAN traffic is identified by a tag inserted in the Ethernet frame between the Source Address and EtherType fields. The tag contains information about the VID (from 1 to 4,094) and priority (used for QoS functions). The EtherType value is set to identify the frame as 802.1Q.

Construction of an 802.1Q (VLAN tagged) Ethernet frame.

TAGGED AND UNTAGGED PORTS

If a switch port will only ever participate in a single VLAN, that port can be configured as untagged. This is also referred to as an access port or host port. An untagged/access port uses the following port tagging logic:

●	If a frame is addressed to a port in the same VLAN on the same switch, no tag needs to be added to the frame.

●	If the frame needs to be transported over a trunk link, the switch adds the relevant 802.1Q tag to identify the VLAN, and then forwards the frame over the trunk port.

●	If the switch receives an 802.1Q tagged frame on an access port, it strips the tag before forwarding it.

Conversely, a tagged port will normally be one that is operating as a trunk; that is, capable of transporting traffic addressed to multiple VLANs using the 802.1Q frame format. A trunk might be used to connect switches or to connect a switch to a router. In some circumstances, a host attached to a port might need to be configured to use multiple VLANs and would need to be attached to a trunk port, rather than an access port. Consider a virtualization host with multiple guest operating systems. The virtual servers might need to be configured to use different VLANs.


VOICE VLANS

Voice over IP (VoIP) transmits voice traffic as data packets, rather than over circuit-based transmission lines. The bandwidth and latency requirements of voice traffic mean that it is often necessary to prioritize it over other types of data packets. This can be accomplished using a dedicated VLAN for voice traffic. However, in many cases, VoIP has been implemented into network infrastructures that were originally designed for just desktop and laptop computers, with limited numbers of physical network access ports.

To accommodate the lack of dedicated wall ports for handsets, most VoIP endpoints incorporate an embedded switch with just two external ports. The handset is connected via its uplink port to the wall port and via the structured cabling to an access switch. The PC or laptop is connected to the handset via the other port. The handset forwards data traffic from the PC to the access switch as untagged frames. The handset sends voice traffic over the same physical link but uses 802.1Q tagged frames.

Normally, for a switch interface to process tagged frames, it would have to be configured as a trunk port. This adds a lot of configuration complexity, so most switches now support the concept of a voice or auxiliary VLAN to distinguish the PC and VoIP traffic without having to configure a trunk. In the following example, the interface configuration assigns traffic from the PC to VLAN 100 and the voice traffic to VLAN 101:

interface GigabitEthernet0/0

switchport mode access

switchport access vlan 100

switchport voice vlan 101

Sharing a single physical wall port between a PC and VoIP handset. The handset and switch interface configuration allow VoIP traffic to be assigned to a different VLAN than the PC's data traffic. (Images © 123RF.com.)

The switch will only accept tagged frames that match the configured voice VLAN ID. To avoid having to configure this manually, the voice VLAN ID and other configuration parameters can be communicated to the handset using a protocol such as Cisco Discovery Protocol (CDP).



















Lesson 9: Explaining Transport Layer Protocols

Topic 9A: Compare and Contrast Transport Protocols

TRANSPORT LAYER PORTS AND CONNECTIONS

At Layer 3, IP provides addressing and routing functionality for internetworks. Protocols at the Transport layer (Layer 4) are concerned with delivery of multiplexed application data.

A TCP/IP host may be running multiple services or communicating with multiple servers, clients, or peers in parallel. This means that incoming packets must be directed to the appropriate service or application. To facilitate this, each application is assigned a unique identification number called a port. A host can operate multiple ports simultaneously.

Port numbers 0 through 1,023 are preassigned by the Internet Assigned Numbers Authority (IANA) to "well-known" server applications. These port assignments are documented at iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml. Other server applications have been registered in the port range 1,024 through 49,151.

The remaining ports (up to 65,535) are designated for private or dynamic use. As well as the server application needing a port, each client application must assign its own port number to track its requests. Client ports are also referred to as ephemeral ports or source ports.

OS implementations of TCP/IP have not always conformed to these recommendations. For example, earlier versions of Windows and UNIX/Linux used 1,024-5,000 for client ports. Modern Linux kernels often use 32,768–60,999.

The port number is used in conjunction with the source IP address to form a socket. Each socket is bound to a software process. Only one process can operate a socket at any one time. A connection is formed when a client socket requests a service from the server socket. A connection is uniquely identified by the combination of server port and IP address and client port and IP address. A server socket can therefore support multiple connections from a number of client sockets.

Multiplexing application ports as sockets at the Transport layer. (Images © 123RF.com.)

TRANSMISSION CONTROL PROTOCOL

The Transmission Control Protocol (TCP) works at the Transport layer to provide connection-oriented, guaranteed communication using acknowledgements to ensure that delivery has occurred. If packets are missing, they can be retransmitted. TCP can be used for unicast transmission only.

TCP takes data from the Application layer as a stream of bytes and divides it up into segments, each of which is given a header. The TCP segments become the payload of the underlying IP datagrams. The use of sequencing, acknowledgments, and retransmissions means that TCP requires numerous header fields to maintain state information. The main fields in the header of a TCP segment are:

Field	Explanation

Source port	TCP port of sending host.

Destination port	TCP port of destination host.

Sequence number	The ID number of the current segment (the sequence number of the last byte in the segment). This allows the receiver to rebuild the message correctly and deal with out-of-order packets.

Ack number	The sequence number of the next segment expected from the other host (that is, the sequence number of the last segment received +1). Packets might be out-of-order because they are delayed, but they could also be lost completely or arrive in a damaged state. In the first case, the lack of acknowledgement results in the retransmission of data and, in the second case, a Negative Acknowledgement (NAK or NACK) forces retransmission.

Data length	Length of the TCP segment.

Flags	Type of content in the segment (ACK, SYN, FIN, and so on).

Window	The amount of data the host is willing to receive before sending another acknowledgement. TCP's flow control mechanism means that if it is getting overwhelmed with traffic, one side can tell the other to slow the sending rate.

Checksum	Ensures validity of the segment. The checksum is calculated on the value of not only the TCP header and payload but also part of the IP header, notably the source and destination addresses. Consequently, the mechanism for calculating the checksum is different for IPv6 (128-bit addresses) than for IPv4 (32-bit addresses).

Urgent Pointer	If urgent data is being sent, this specifies the end of that data in the segment.

Options	Allows further connection parameters to be configured. The most important of these is the Maximum Segment Size. This allows the host to specify how large the segments it receives should be, minimizing fragmentation as they are transported over data link frames.

TCP HANDSHAKE AND TEARDOWN

A TCP connection is typically established to transfer a single file, so a client session for something like a web page (HTTP) might involve multiple TCP connections being opened with the server. These connections are managed using handshake transactions, which make use of a number of TCP flags.

TCP Three-Way Handshake

A connection is established using a three-way handshake:

Observing the 3-way handshake with the Wireshark protocol analyzer. (Screenshot courtesy of Wireshark.)

1. `	`The client sends a segment with the TCP flag SYN set to the server with a randomly generated sequence number. The client enters the SYN-SENT state.
1. `	`The server, currently in the LISTEN state (assuming it is online), responds with a SYN/ACK segment, containing its own randomly generated sequence number. The server enters the SYN-RECEIVED state.
1. `	`The client responds with an ACK segment. The client assumes the connection is ESTABLISHED.
1. `	`The server opens a connection with the client and enters the ESTABLISHED state.

Servers can (usually) support thousands or even millions of TCP connections simultaneously.

The sending machine expects regular acknowledgments for segments it sends and, if a period elapses without an acknowledgment, it assumes the information did not arrive and automatically resends it. This overhead makes the system relatively slow. Connection-oriented transmission is suitable when reliability and data integrity are important.

TCP Connection Teardown

There are also functions for resetting a connection and (in some implementations) keeping a connection alive if no actual data is being transmitted (hosts are configured to timeout unused connections). To close a connection, also referred to as teardown, the following basic steps are performed:

1. `	`The client sends a FIN segment to the server and enters the FIN-WAIT1 state.
1. `	`The server responds with an ACK segment and enters the CLOSE-WAIT state.
1. `	`The client receives the ACK segment and enters the FIN-WAIT2 state. The server sends its own FIN segment to the client and goes to the LAST-ACK state.
1. `	`The client responds with an ACK and enters the TIME-WAIT state. After a defined period, the client closes its connection.
1. `	`The server closes the connection when it receives the ACK from the client.

Some implementations may use one less step by combining the FIN and ACK responses into a single segment operation.

Observing TCP connections with the netstat tool. (Screenshot used with permission from Microsoft.)

A host can also end a session abruptly using a reset (RST) segment. This would not be typical behavior and might need to be investigated. A server or security appliance might refuse connections using RST, a client or server application might be faulty, or there could be some sort of suspicious scanning activity ongoing.

USER DATAGRAM PROTOCOL

The User Datagram Protocol (UDP) also works at the Transport layer, but unlike TCP, it is a connectionless, nonguaranteed method of communication with no acknowledgments or flow control. There is no guarantee regarding the delivery of messages or mechanism for retransmitting lost or damaged packets. When an application uses UDP, it must specify reliability mechanisms in the application layer headers or software logic, if this is required.

UDP is suitable for applications that send small amounts of data in each packet and do not require acknowledgement of receipt. It is used by Application layer protocols that need to send multicast or broadcast traffic. It may also be used for applications that transfer time-sensitive data but do not require complete reliability, such as voice or video. Using small packets means that if a few are lost or arrive out of order, they only manifest as minor glitches in playback quality. The reduced overhead means that overall delivery is faster.

This table shows the structure of a UDP datagram.

Field	Explanation

Source port	UDP port of sending host.

Destination port	UDP port of destination host.

Sequence number	The ID number of the current segment (the sequence number of the last byte in the segment). This allows the receiver to rebuild the message correctly and deal with out-of-order packets.

Message length	Size of the UDP packet.

Flags	Type of content in the segment (ACK, SYN, FIN, and so on).

Checksum	Ensures validity of the packet

The header size is 8 bytes, compared to 20 bytes (or more) for TCP.

COMMON TCP AND UDP PORTS

The following table lists some of the well-known and registered port numbers.

Port Number	Transport Protocol	Service or Application	Description

20	TCP	ftp-data	File Transfer Protocol-Data

21	TCP	ftp	File Transfer Protocol-Control

22	TCP	ssh/sftp	Secure Shell/FTP over SSH

23	TCP	telnet	Telnet

25	TCP	smtp	Simple Mail Transfer Protocol

53	TCP/UDP	domain	Domain Name System

67	UDP	bootps	BOOTP/DHCP Server

68	UDP	bootpc	BOOTP/DHCP Client

69	UDP	tftp	Trivial File Transfer Protocol

80	TCP	http	HTTP

110	TCP	pop	Post Office Protocol

123	UDP	ntp/sntp	Network Time Protocol/Simple NTP

143	TCP	imap	Internet Message Access Protocol

161	UDP	snmp	Simple Network Management Protocol

162	UDP	snmp-trap	Simple Network Management Protocol Trap

389	TCP/UDP	ldap	Lightweight Directory Access Protocol

443	TCP	https	HTTP-Secure (Secure Sockets Layer (SSL)/Transport Layer Security (TLS)

445	TCP	smb	Server Message Block over TCP/IP

514	UDP	syslog	Syslog

546	UDP	dhcpv6-client	DHCPv6 Client

547	TCP	dhcpv6-server	DHCPv6 Server

587	TCP	smtps	SMTP-Secure

636	TCP	ldaps	LDAP-Secure

993	TCP	imaps	IMAP-Secure

995	TCP	pop3s	POP3-Secure

1433	TCP	sql-server	MS Structured Query Language (SQL) Server

1521	TCP	sqlnet	Oracle SQL\*Net

3306	TCP	mysql	MySQL/MariaDB

3389	TCP	rdp	Remote Desktop Protocol

5004	UDP	rtp	Real-Time Protocol

5005	UDP	rtcp	Real-Time Control Protocol

5060	TCP/UDP	sip	Session Initiation Protocol

5061	TCP/UDP	sips	SIP-Secure


Topic 9B: Use Appropriate Tools to Scan Network Ports

IP SCANNERS

One of the management tasks facing a network administrator is to verify exactly what is connected to the network and what is being communicated over it. This is usually described as network visibility. Visibility is necessary to confirm that servers and clients are in the correct VLANs or subnets and to try to identify rogue or unauthorized machines. An IP scanner is a tool that performs host discovery and can establish the overall logical topology of the network in terms of subnets and routers.

IP scanning can be performed using lightweight standalone open source or commercial tools, such as Nmap, AngryIP, or PRTG. Enterprise network management suites will also be able to perform IP scanning and combine that with asset or inventory information about each host. This functionality is often referred to as IP Address Management (IPAM). Suites that integrate with DHCP and DNS servers can be referred to as DHCP, DNS, and IPAM (DDI). Windows Server is bundled with a DDI product. Other notable vendors and solutions include ManageEngine, Infoblox, SolarWinds, Bluecat, and Men -and- Mice.

Angry IP Scanner.

Host discovery is a basic type of IP scanning that only attempts to determine whether an IP address is "up." There are many different host discovery techniques. Some are best at discovering large numbers of legitimate hosts quickly; others are optimized for identifying rogue hosts that are attempting to remain hidden. The most basic techniques use the ping, arp, and traceroute tools. Some suites use Simple Network Management Protocol (SNMP) queries, which can also report more detailed information about interface statistics, while as noted above, enterprise suites can query local DHCP and DNS servers for information. Security-oriented scanners can use specially crafted probes to locate hosts that might be configured not to respond to pings.

NMAP

The Nmap Security Scanner ( nmap.org ) is widely used for IP scanning, both as an auditing and as a penetration testing tool. The tool is open-source software with packages for most versions of Windows, Linux, and macOS®. It can be operated with a command line or via a GUI (Zenmap).

The basic syntax of an Nmap command is to give the IP subnet (or IP address) to scan. When used without switches like this, the default behavior of Nmap is to ping and send a TCP ACK packet to ports 80 and 443 to determine whether a host is present. On a local network segment, Nmap will also perform ARP and Neighbor Discovery (ND) sweeps. If a host is detected, Nmap performs a port scan against that host to determine which services it is running. This OS fingerprinting can be time consuming on a large IP scope. If you want to perform only host discovery, you can use Nmap with the -sn switch to suppress the port scan. The tool can also work out hop counts by specifying the --traceroute switch.

Nmap discovery scan. (Screenshot used with permission from Nmap.)

A variety of options are available for custom scans to try to detect stealthy hosts (nmap.org/book/host-discovery-techniques.html).

NETSTAT

As well as discovering hosts, one other visibility challenge is to establish what services a host is running. The netstat command allows you to check the state of ports on the local host. You can use netstat to check for service misconfigurations, such as a host running a web or FTP server that a user installed without authorization. You may also be able to identify suspicious remote connections to services on the local host or from the host to remote IP addresses.

On Windows®, used without switches, the command outputs active TCP connections, showing the local and foreign addresses and ports. Using the -a switch displays all open ports, including both active TCP and UDP connections and ports in the listening state.

On Linux®, running netstat without switches shows active connections of any type. If you want to show different connection types, you can use the switches for Internet connections for TCP ( -t ) and UDP ( -u ), raw connections ( -w ), and UNIX® sockets/local server ports ( -x ). Using the -a switch includes ports in the listening state in the output. -l shows only ports in the listening state, omitting established connections.

For example, the following command shows listening and established Internet connections (TCP and UDP) only: netstat -tua

Linux netstat output showing active and listening TCP and UDP connections.

On both Windows and Linux, -n displays ports and addresses in numerical format. Skipping name resolution speeds up each query. On Linux, using -4 or -6 filters sockets by IPv4 or IPv6 addresses respectively. In Windows, use the -p switch with the protocol type ( TCP , TCPv6 , UDP , or UDPv6 ).

Another common task is to identify which software process is bound to a socket. On Windows, -o shows the Process ID (PID) number that has opened the port, while -b shows the process name. In Linux, use -p to show the PID and process name.

netstat -s reports per protocol statistics, such as packets received, errors, discards, unknown requests, port requests, failed connections, and so on. The tool will report Ethernet statistics using -e (Windows) or -I (Linux). netstat -r displays the routing table.

Linux netstat interface statistics showing receive and transmit packets numbers plus errors and dropped packets.

netstat can also be set to run continuously. In Windows, run netstat nn , where nn is the refresh interval in seconds (press Ctrl+C to stop); in Linux, run netstat -c .

The Linux netstat command is part of the deprecated net-tools package. The preferred package iproute2 contains a number of different commands to replace netstat functionality. Most of the port scanning functions are performed by ss, while interface statistics are reported by nstat.

REMOTE PORT SCANNERS

Where netstat reports on the status of local ports, a remote port scanner performs the probes from another machine, or even a machine on another network.

Many of the tools used for host discovery can also perform remote port scanning. As with host discovery, there are many different techniques for performing port scans. Some techniques are designed for covert use (to try to avoid detection of the scanning activity by the target) and some are designed to probe beyond security barriers, such as firewalls.

As examples, the following represent some of the main types of scanning that Nmap can perform:

●	TCP SYN (-sS)-This is a fast technique (also referred to as half-open scanning) as the scanning host requests a connection without acknowledging it. The target's response to the scan's SYN packet identifies the port state.

●	TCP connect (-sT)-A half-open scan requires Nmap to have privileged access to the network driver so that it can craft packets. If privileged access is not available, Nmap must use the OS to attempt a full TCP connection. This type of scan is less stealthy.

●	UDP scans (-sU)-Scan UDP ports. As these do not use ACKs, Nmap needs to wait for a response or timeout to determine the port state, so UDP scanning can take a long time. A UDP scan can be combined with a TCP scan.

●	Port range (-p)-By default, Nmap scans 1,000 commonly used ports. Use the -p argument to specify a port range. You can also use --top-ports n , where n is the number of commonly used ports to scan. The frequency statistics for determining how commonly a port is used are stored in the nmap-services configuration file.

Half-open scanning with Nmap. (Screenshot used with permission from Nmap.)

When services are discovered, you can use Nmap with the -sV or -A switch to probe a host more intensively to discover the software or software version operating each port. The process of identifying an OS or software application from its responses to probes is called fingerprinting.

The responses to network probes can be used to identify the type and version of the host operating system. (Screenshot used with permission from Nmap.)

PROTOCOL ANALYZERS

A protocol analyzer works in conjunction with a packet capture or sniffer tool. You can either analyze a live capture to analyze frames as they are read by a sniffer or open a saved capture (.pcap) file. Most protocol analyzer tools bundle a sniffer component with the analyzer in the same software package.

One function of a protocol analyzer is to parse each frame in a stream of traffic to reveal its header fields and payload contents in a readable format. This is referred to as packet analysis. Analyzing protocol data at the frame or packet level will help to identify protocol or service misconfigurations. As a live stream or capture file can contain hundreds or thousands of frames, you can use display filters to show only particular frame or sequence of frames. Another useful option is to use the Follow TCP Stream context command to reconstruct the packet contents for a TCP session.

Another function of a protocol analyzer is to perform traffic analysis. Rather than reading each frame individually, you use the tool to monitor statistics related to communications flows, such as bandwidth consumed by each protocol or each host, identifying the most active network hosts, monitoring link utilization and reliability, and so on. In Wireshark, you can use the Statistics menu to access traffic analysis tools.

Using the Conversations option from Wireshark's Statistics tools. (Screenshot courtesy of Wireshark.)

Using the Protocol Hierarchy tool in Wireshark to view the most active protocols on a network link. This sort of report can be used to baseline network activity. (Screenshot courtesy of Wireshark.)











Lesson 10: Explaining Network Services

Topic 10A: Explain the Use of Network Addressing Services

DYNAMIC HOST CONFIGURATION PROTOCOL

The Dynamic Host Configuration Protocol (DHCP) provides an automatic method for allocating an IP address, subnet mask, and optional parameters, such as the default gateway and DNS server addresses, when a host joins the network. All the major operating systems provide support for DHCP clients and servers. DHCP servers are also embedded in many SOHO routers and modems.

A host is configured to use DHCP by specifying in the TCP/IP configuration that it should automatically obtain an IP address.

DHCP Discover, Offer, Request, Ack process. (Images © 123RF.com.)

When a DHCP client initializes, it broadcasts a DHCPDISCOVER packet to find a DHCP server. All communications are sent using UDP, with the server listening on port 67 and the client on port 68.

Presuming it has an IP address available, the DHCP server responds to the client with a DHCPOFFER packet, containing the address and other configuration information.

While the client doesn't have an IP address yet, the DHCPOFFER is usually delivered as unicast because the server knows the client's MAC address. Some hosts cannot receive unicast without an IP address. They should set a broadcast bit in the DHCPDISCOVER packet.

The client may choose to accept the offer using a DHCPREQUEST packet-also broadcast onto the network.

Assuming the offer is still available, the server will respond with a DHCPACK packet. The client broadcasts an ARP message to check that the address is unused. If so, it will start to use the address and options; if not, it declines the address and requests a new one.

The IP address is leased by the server for a limited period only. A client can attempt to renew or rebind the lease before it expires. If the lease cannot be renewed, the client must release the IP address and start the discovery process again.

Sometimes, the DHCP lease process is called the DORA process: Discover, Offer, Request, and Ack(nowledge).

DHCP SERVER CONFIGURATION

DHCP is normally deployed as a service of a network operating system or through an appliance such as a switch or router. A DHCP server must be allocated a static IP address and configured with a range (or pool) of IP addresses and subnet masks plus option values to allocate.

Configuring DHCP on a TP-LINK wireless access point. (Screenshot courtesy of TP-Link Technologies Co., Ltd.)

A range of addresses and options configured for a single subnet is referred to as a scope. To define a scope, you must provide a start and end IP address along with a subnet mask. The server maintains a one-to-one mapping of scopes to subnets. That is, no scope can cover more than one subnet and no subnet can contain more than one scope.

The multifunction device shown only supports a single scope. The DHCP server must be placed in the same subnet as its clients. More advanced DHCP servers might be configured to manage multiple scopes. Where a server provides IP configuration for multiple subnets/scopes, it must choose the pool to service each request based on the subnet from which the request originated.

There is no mechanism for a client to choose between multiple servers. Therefore, if multiple DHCP servers are deployed-for fault tolerance, for instance-they must be configured with nonoverlapping or split scopes. DHCP for multiple subnets is usually handled by configuring relay agents to forward requests to a central DHCP server.

DHCP OPTIONS CONFIGURATION

Along with an address scope, you also need to define other parameters, such as lease time and options.

DHCP Lease Time and Available Leases

The client can renew the lease when at least half the lease's period has elapsed (T1 timer) so that it keeps the same IP addressing information. If the original DHCP server does not respond to the request to renew the lease, the client attempts to rebind the same lease configuration with any available DHCP server. By default, this happens after 87.5% of the lease duration is up (T2 timer). If this fails, the client releases the IP address and continues to broadcast to discover a server.

A long lease time means the client does not have to renew the lease often, but the DHCP server's available pool of IP addresses is not replenished frequently. Where IP addresses are in short supply, a short lease period enables the DHCP server to allocate addresses previously assigned to hosts that are now not active on the network.

A Windows client can be forced to release a lease by issuing a command such as ipconfig. In Linux, the utility dhclient is often used for this task, though modern distributions might use NetworkManager or systemd-networkd. A Windows host that fails to obtain a lease will revert to an automatic IP address (APIPA) or link-local configuration and select an address in the 169.254.0.0/16 range. Linux might use link-local addressing, set the address to unknown (0.0.0.0), or leave the interface unconfigured.

DHCP Options

When the DHCP server offers a configuration to a client, at a minimum it must supply an IP address and subnet mask. Typically, it will also supply other IP-related settings, known as DHCP options. Each option is identified by a tag byte or decimal value between 0 and 255 (though neither 0 nor 255 can be used as option values). Some widely used options include:

●	The default gateway (IP address of the router).

●	The IP address(es) of DNS servers that can act as resolvers for name queries.

●	The DNS suffix (domain name) to be used by the client.

●	Other useful server options, such as time synchronization (NTP), file transfer (TFTP), or VoIP proxy.

A set of default (global) options can be configured on a server-wide basis. Default options can be overridden by setting scope-specific options.

DHCP RESERVATIONS AND EXCLUSIONS

One disadvantage of the standard dynamic assignment method is that it does not guarantee that any given client will retain the same IP address over time. There are some cases where it would be advantageous for certain hosts, such as network printers or wireless access points, to retain their IP addresses.

One solution is to configure static assignments, using IP addresses outside the DHCP scope. Alternatively, statically assigned addresses can be assigned from a specially configured exclusion range, if this is supported by the server. While these solutions are functional, they lose the advantages of centralized configuration management.

An alternative approach is to create a reservation. A reservation is a mapping of a MAC address or interface ID to a specific IP address within the DHCP server's address pool. When the DHCP server receives a request from the given interface, it always provides the same IP address. This is also referred to as static or fixed address assignment. An automatically allocated reservation refers to an address that is leased permanently to a client. This is distinct from static allocation as the administrator does not predetermine which specific IP address will be leased.

DHCP RELAY AND IP HELPER

Normally, routers do not forward broadcast traffic. This means that each broadcast domain must be served by its own DHCP server. On a large network with multiple subnets, this would mean provisioning and configuring many DHCP servers. To avoid this scenario, a DHCP relay agent can be configured to provide forwarding of DHCP traffic between subnets. Routers that can provide this type of forwarding are described as RFC 1542 compliant.

The DHCP relay intercepts broadcast DHCP frames, applies a unicast address for the appropriate DHCP server, and forwards them over the interface for the subnet containing the server. The DHCP server can identify the original IP subnet from the packet and offer a lease from the appropriate scope. The DHCP relay also performs the reverse process of directing responses from the server to the appropriate client subnet.

Configuring a DHCP relay agent. (Images © 123RF.com)

This IP helper functionality can be configured on routers to allow set types of broadcast traffic (including DHCP) to be forwarded to an interface. The IP helper function supports the function of the DHCP relay agent. For example, in the diagram, hosts in the 10.1.20.0/24 and 10.1.10.0/24 subnets need to use a DHCP server for autoconfiguration, but the DHCP server is located in a different subnet. The router is configured as a DHCP relay agent, using the following commands to enable forwarding of DHCP broadcasts on the interfaces serving the client subnets:

interface eth1

ip helper-address 10.1.0.200

interface eth2

ip helper-address 10.1.0.200

UDP forwarding is a more general application of the same principle. As well as DHCP, it is used for the Network Time Protocol (NTP) and other broadcast-based applications.

DHCPV6 SERVER CONFIGURATION

IPv6's Stateless Address Autoconfiguration (SLAAC) process can locate routers (default gateways) and generate a host address with a suitable network prefix automatically. In this context, the role of a DHCP server in IPv6 is different. DHCPv6 is often just used to provide additional option settings, rather than leases for host IP addresses. The format of messages is different, but the process of DHCP server discovery and address leasing (if offered) is fundamentally the same. As IPv6 does not support broadcast, clients use the multicast address ff02::1:2 to discover a DHCP server. DHCPv6 uses ports 546 (clients) and 547 (servers), rather than ports 68 and 67 as in DHCPv4.

In stateless mode, a client obtains a network prefix from a Router Advertisement and uses it with the appropriate interface ID. The router can also set a combination of flags to tell the client that a DHCP server is available. If so configured, the client solicits a DHCPv6 server using the multicast address ff02::1:2 and requests additional configuration information.

DHCPv6 stateless mode. (Images © 123RF.com.)

By contrast, stateful mode means that a host can also obtain a routable IP address from a DHCPv6 scope, plus any other options (like with DHCP for IPv4).

DHCPv6 stateful mode. (Images © 123RF.com.)

Configuring the scope requires you to define the network prefix and then any IP addresses that are to be excluded from being offered. All other addresses that are not explicitly excluded can be offered. The host must still listen for a router advertisement to obtain the network prefix and configure a default gateway. There is no mechanism in DHCPv6 for setting the default route.

Topic 10B: Explain the Use of Name Resolution Services

HOST NAMES AND FULLY QUALIFIED DOMAIN NAMES

The Internet Protocol uses a binary IP address to locate a host on an internetwork. The dotted decimal (IPv4) or hex (IPv6) representation of this IP address is used for configuration purposes, but it is not easy for people to remember. For this reason, a "friendly" name is also typically assigned to each host. There are two types of names: host names and Fully Qualified Domain Names (FQDNs).

A host name is assigned to a computer by the administrator, usually when the OS is installed. The host name needs to be unique on the local network.

To avoid the possibility of duplicate host names on the Internet, a fully qualified domain name (FQDN) is used to provide a unique identity for the host belonging to a particular network. An example of an FQDN might be nut.widget.example. An FQDN is made up of the host name and a domain suffix. In the example, the host name is nut and the domain suffix is widget.example. This domain suffix consists of the domain name widget within the top-level domain (TLD) .example . A domain suffix could also contain subdomains between the host and domain name. The trailing dot or period represents the root of the hierarchy.

When you are configuring name records, an FQDN must include the trailing period to represent the root, but this can be omitted in most other use cases.

A domain name must be registered with a registrar to ensure that it is unique within a top-level domain. Once a domain name has been registered, it cannot be used by another organization. The same domain name may be registered within different top-level domains, however-widget.example. and widget.example.uk. are distinct domains, for instance.

Numerous hosts may exist within a single domain. For example: nut, bolt , and washer might all be hosts within the widget.example. domain. Given that, FQDNs must follow certain rules:

●	The host name must be unique within the domain.

●	The total length of an FQDN cannot exceed 253 characters, with each label (part of the name defined by a period) no more than 63 characters (excluding the periods).

●	A DNS label should use letter, digit, and hyphen characters only. A label should not start with a hyphen. Punctuation characters such as the period (.) or forward slash (/) should not be used.

●	DNS labels are not case-sensitive.

Additionally, Internet registries may have their own restrictions.

DOMAIN NAME SYSTEM

The Domain Name System (DNS) is a global hierarchy of distributed name server databases that contain information on domains and hosts within those domains. At the top of the DNS hierarchy is the root, which is represented by the null label, consisting of just a period (.). There are 13 root level servers (A to M).

Immediately below the root lie the top-level domains (TLDs). There are several types of top-level domains, but the most prevalent are generic (such as .com, .org, .net, .info, .biz), sponsored (such as .gov, .edu), and country code (such as .uk, .ca, .de). DNS is operated by ICANN (icann.org), which also manages the generic TLDs. Country codes are generally managed by an organization appointed by the relevant government.

Information about a domain is found by tracing records from the root down through the hierarchy. The root DNS servers have complete information about the top-level domain servers. In turn, these servers have information relating to servers for the second level domains. No name server has complete information about all domains. Records within the DNS tell them where an authoritative name server for the missing information is found.

DNS hierarchy. (Images © 123RF.com.)

An FQDN reflects this hierarchy, from most specific on the left (the host's resource record with its name:IP address mapping) to least specific on the right (the TLD followed by the root). For example: pc.corp.515support.com.

NAME RESOLUTION USING DNS

The signal for the name resolution process to commence occurs when a user presents an FQDN (often within a web address) to an application program, such as a web browser. The client application, referred to as a stub resolver, checks its local cache for the mapping. If no mapping is found, it forwards the query to its local name server. The IP addresses of one or more name servers that can act as resolvers are usually set in the TCP/IP configuration. The resolution process then takes place as follows:

DNS name resolution process. (Images © 123RF.com.)

Most queries between name servers are performed as iterative lookups. This means that a name server responds to a query with either the requested record or the address of a name server at a lower level in the hierarchy that is authoritative for the namespace. It makes no effort to try to make additional queries to locate information that it does not have. In the figure, at steps 4 and 5, the root server and .net name server simply pass the querying server the address of an authoritative name server. They do not take on the task of resolving the original query for www.515web.net.

A recursive lookup means that if the queried server is not authoritative, it does take on the task of querying other name servers until it finds the requested record or times out. The name servers listed in a client's TCP/IP configuration accept recursive queries. This is the type of querying performed by the corp.515support.com name server.

A DNS server may be configured to only perform recursive querying (a resolver), or it may perform both recursive querying and maintain zone records, or it may only maintain zone records. Usually the roles are split, especially if the servers are open to the Internet. Most Internet-accessible DNS servers disable recursive queries. Recursive resolvers are typically only accessible by authorized clients-subscribers within an ISP's network or clients on a private LAN, for instance.

RESOURCE RECORD TYPES

A DNS zone will contain numerous resource records. These records allow a DNS name server to resolve queries for names and services hosted in the domain into IP addresses. Resource records can be created and updated manually (statically), or they can be generated dynamically from information received from client and server computers on the network.

The Start of Authority (SOA) record identifies the primary authoritative name server that maintains complete resource records for the zone. The primary name server can be used to modify resource records. The SOA also includes contact information for the zone and a serial number for version control.

Configuring a Start of Authority record in Windows DNS. (Screenshot courtesy of Microsoft.)

Name Server (NS) records identify authoritative DNS name servers for the zone. As well as the primary name server, most zones are configured with secondary name servers for redundancy and load balancing. Secondary name servers hold read-only copies of resource records but can still be authoritative for the zone.

Resource records configured on a BIND DNS server.

HOST ADDRESS AND CANONICAL NAME RECORDS

An address (A) record is used to resolve a host name to an IPv4 address. An AAAA record resolves a host name to an IPv6 address.

Both types of host records (A and AAAA) plus a CNAME record in Windows Server DNS. (Screenshot courtesy of Microsoft.)

DNS uses the UDP transport protocol over port 53 by default, and UDP has a maximum packet size of 512 bytes. Due to the much larger address sizes of IPv6, AAAA records can exceed this size. This can result in UDP packets being fragmented into several smaller packets. This can result in these packets being blocked by firewalls if they are not configured to expect them. Network administrators should check that their DNS servers can accept these transmissions and that intermediary components are not blocking them.

A Canonical Name (CNAME) (or alias) record is used to configure an alias for an existing address record (A or AAAA). For example, the IP address of a web server with the host record lamp could also be resolved by the alias www . CNAME records are also often used to make DNS administration easier. For example, an alias can be redirected to a completely different host temporarily during system maintenance.

Multiple different named resource records can refer to the same IP address (and vice versa in the case of load balancing).

There is nothing to stop an administrator configuring multiple address records to point different host names to the same IP address. Using CNAME records is usually considered better practice, however. It is also possible to configure multiple A or AAAA records with the same host name but different IP addresses. This is usually done as a basic load balancing technique, referred to as round robin DNS.

MAIL EXCHANGE, SERVICE, AND TEXT RECORDS

A Mail Exchange (MX) record is used to identify an email server for the domain. In a typical network, multiple servers are installed to provide redundancy, and each one will be represented with an MX record. Each server record is given a preference value with the lowest numbered entry preferred. The host identified in an MX record must have an associated A or AAAA record. An MX record must not point to a CNAME record.

While most DNS records are used to resolve a name into an IP address, a Service (SRV) record contains the service name and port on which a particular application is hosted. SRV records are often used to locate VoIP or media servers. SRV records are also an essential part of the infrastructure supporting Microsoft’s Active Directory; they are used by clients to locate domain controllers, for instance. As with MX, SRV records can be configured with a priority value.

SRV records in Windows Server DNS. (Screenshot courtesy of Microsoft.)

A TXT record is used to store any free-form text that may be needed to support other network services. A single domain name may have many TXT records, but most commonly they are used as part of Sender Policy Framework (SPF) and DomainKeys Identified Mail (DKIM). An SPF record is used to list the IP addresses or names of servers that are permitted to send email from a particular domain and is used to combat the sending of spam. DKIM records are used to decide whether you should allow received email from a given source, preventing spam and mail spoofing. DKIM can use encrypted signatures to prove that a message really originated from the domain it claims.

POINTER RECORDS

A DNS server may have two types of zones: forward lookup and reverse lookup. Forward lookup zones contain the resource records listed previously. For example, given a name record, a forward lookup returns an IP address; an MX record returns a host record associated with the domain's mail services. Conversely, a reverse DNS query returns the host name associated with a given IP address. This information is stored in a reverse lookup zone as a pointer (PTR) record.

Reverse lookup zone and pointer records in Windows Server DNS. (Screenshot courtesy of Microsoft.)

Reverse DNS querying uses a special domain named by the first three octets of IP addresses in the zone in reverse order and appended with in-addr.arpa. The name server is configured with a reverse lookup zone . This zone contains PTR records consisting of the final octet of each host record. For example, the reverse lookup for a host record containing the IP address 198.51.100.1 is:

1\.100.51.198.in-addr.arpa

IPv6 uses the ip6.arpa domain; each of the 32 hex characters in the IPv6 address is expressed in reverse order as a subdomain. For example, the IPv6 address:

2001:0db8:0000:0000:0bcd:abcd:ef12:1234

is represented by the following pointer record:

4\.3.2.1.2.1.f.e.d.c.b.a.d.c.b.0.0.0.0.0.0.0.0.0.8.b.d.0.1.0.0.2.ip6.arpa

Reverse lookup zones are not mandatory and are often omitted from DNS servers, as they can be used by hackers to sequentially work through a range of IP addresses to discover useful or interesting device names, which can then be targeted by other hacking mechanisms.

Topic 10C: Configure DNS Services

DNS SERVER CONFIGURATION

DNS is essential to the function of the Internet. Windows Active Directory® and most Linux networks also require a DNS service to be running and correctly configured. It is important to realize that there are different kinds of DNS servers however, fulfilling different roles in network architecture.

DNS Server Types

A DNS server is usually configured to listen for queries on UDP port 53. Some DNS servers are also configured to allow connections over TCP port 53, as this allows larger record transfers (over 512 bytes). Larger transfers might be required if IPv6 is deployed on the network or if the DNS servers are using a security protocol (DNSSEC).

DNS name servers maintain the DNS namespace in zones. A single zone namespace might host records for multiple domains. A single name server might be configured to manage multiple zones. A name server can maintain primary and/or secondary zones:

●	Primary means that the zone records held on the server are editable. A zone can be hosted by multiple primary servers for redundancy. As the zone records are editable on all primaries, changes must be carefully replicated and synchronized. It is critically important to update the serial number for each change.

●	Secondary means that the server holds a read-only copy of the zone. This is maintained through a process of replication known as a zone transfer from a primary name server. A secondary zone would typically be provided on two or more separate servers to provide fault tolerance and load balancing. Again, the serial number is a critical part of the zone transfer process.

The noninclusive terms "master" to mean primary and "slave" to mean secondary are used in some DNS server versions. This type of terminology is deprecated in the latest versions.

A name server that holds complete records for a domain can be defined as authoritative. This means that a record in the zone identifies the server as a name server for that namespace. Both primary and secondary name servers are authoritative.

Servers that don't maintain a zone (primary or secondary) are referred to as cache-only servers. A non-authoritative answer from a server is one that derives from a cached record, rather than directly from the zone records.

DNS Caching

Each resource record can be configured with a default time to live (TTL) value, measured in seconds. This value instructs resolvers how long a query result can be kept in cache. Setting a low TTL allows records to be updated more quickly but increases load on the server and latency on client connections to services. Some common TTL values include 300 (5 minutes), 3,600 (1 hour), 86,400 (1 day), and 604,800 (1 week).

DNS caching is performed by both servers and client computers. In fact, each application on a client computer might be configured to manage its own DNS cache. For example, separate web browser applications typically maintain their own caches rather than relying on a shared OS cache.

If there is a change to a resource record, server and client caching means that the updated record can be relatively slow to propagate around the Internet. These changes need to be managed carefully to avoid causing outages. Planning for a record change involves reducing the TTL in the period before the change, waiting for this change to propagate before updating the record, and then reverting to the original TTL value when the update has safely propagated.

INTERNAL VERSUS EXTERNAL DNS

As well as making sure that resource records for the managed domain(s) are accurate, administrators should ensure that DNS services are highly available and secure, to prevent DNS spoofing, where an attacker is able to supply false name resolutions to clients.

A company will use primary and secondary name servers to maintain authoritative zone records for the domains that it manages. Internal DNS zones refer to the domains used on the private network only. These name records should only be available to internal clients. For example, a company might run a Windows Active Directory network using the domain name corp.515support.com. The zone records for the subdomain corp.515support.com would be served from internal name servers. This would allow a client PC ( pc1.corp.515support.com ) to contact a local application server ( crm.corp.515support.com ). The name servers hosting these internal subdomain records must not be accessible from the Internet.

External DNS zones refer to records that Internet clients must be able to access. For example, the company might run web and email services on the domain 515support.com. In order for Internet hosts to use a web server at www.515support.com or send email to an @515support.com address, the zone records for 515support.com must be hosted on a name server that is accessible over the Internet.

Companies must also provide name resolution services to support their internal clients contacting other domains. The function of a resolver is to perform recursive queries in response to requests from client systems (stub resolvers). If a name server is not authoritative for the requested domain, it can either perform a recursive query to locate an authoritative name server or it can forward the request to another name server. A recursive resolver must be configured with a root hints file so that it can query the whole DNS hierarchy from the root servers down. DNS servers should allow recursive queries only from authorized internal clients. It is also a good idea to separate the DNS servers used to host zone records from ones used to service client requests for non authoritative domains.

It is possible for the same DNS server instance to perform in both name server and resolver roles, but more typically these functions are separated to different servers for security reasons.

As an alternative to recursion (or to supplement it), name servers can be configured to resolve queries via forwarding. A forwarder transmits a client query to another DNS server and routes the replies it gets back to the client. A conditional forwarder performs this task for certain domains only. For example, you might configure a DNS server that is authoritative for the local private network (internal DNS), but that forwards any requests for Internet domains to an external DNS resolver run by your ISP.

NSLOOKUP

Name resolution troubleshooting typically involves testing multiple clients and servers. The use of caching and the distributed nature of the system means that configuration errors can occur in several different places.

You might start investigating a name resolution issue by verifying the name configured on a host. In Windows, you can use the command ipconfig /all to display the FQDN of the local host. In Linux, you can use the command hostname --fqdn .

In a Windows environment, you can troubleshoot DNS name resolution with the nslookup command:

nslookup -Option Host DNSServer

Host can be either a host name, domain name, FQDN, or IP address. DNSServer is the IP address of a server used to resolve the query; the default DNS server is used if this argument is omitted. Option specifies an nslookup subcommand. For example, the following command queries Google's public DNS server (8.8.8.8) for information about 515support.com's mail records:

nslookup -type=mx 515support.com 8.8.8.8

If nslookup is run without any arguments (or by specifying the server only with nslookup – DNSServer ), the tool is started in interactive mode. You can perform specific query types and output the result to a text file for analysis.

The first two nslookup commands identify comptia.org's MX and primary name server records using Google's public DNS resolver (8.8.8.8). Note that the answers are nonauthoritative. The third command queries CompTIA's name server for the MX record. This answer is authoritative. (Screenshot courtesy of Microsoft.)

The Windows PowerShell environment provides a more sophisticated scripted environment that you can use to issue cmdlets to test DNS name resolution (and change DNS settings as well, if required). PowerShell® provides a cmdlet called Resolve-DnsName, which allows a more flexible method of testing name resolution than nslookup, as it allows testing of the different methods of name resolution (HOSTS file, DNS cache, and DNS server).

DIG

Domain Information Groper (dig) is a command-line tool for querying DNS servers that ships with the BIND DNS server software published by the Internet Systems Consortium (ISC) (isc.org/downloads/bind).

dig can be run pointing at a specific DNS server; otherwise, it will use the default resolver. Without any specific settings, it queries the DNS root zone. A simple query uses the syntax: dig host . This will search for the address record for the host, domain, or FQDN or PTR record for an IP address.

The following command example directs the resolve request to the specific DNS server identified after the @ symbol. This can be an FQDN or IP address.

dig @ns1.isp.example host

Other examples of dig are to display all the resource records about a domain or just specific ones such as Mail Exchange:

dig @ns1.isp.example host all

dig @ns1.isp.example host MX

dig often generates a lot of information, so it is possible to add parameters to the end of the command like +nocomments or +nostats , which will reduce the output.

Using dig to locate MX and A records.

You can install dig on Windows by downloading the BIND DNS server package and installing it using the tools-only option.











Lesson 11: Explaining Network Applications

Topic 11A: Explain the Use of Web, File/Print, and Database Services

HYPERTEXT TRANSFER PROTOCOL

Websites and web applications are perhaps the most useful and ubiquitous of network services. Web technology can be deployed for a huge range of functions and applications, in no way limited to the static pages of information that characterized the first websites. The foundation of web technology is the HyperText Transfer Protocol (HTTP). HTTP enables clients (typically web browsers) to request resources from an HTTP server. A client connects to the HTTP server using an appropriate TCP port (TCP/80, by default) and submits a request for a resource, using a uniform resource locator (URL). The server acknowledges the request and either responds with the data or with an error message.

HTTP Headers and Payload

The response and request formats are defined in the HTTP header. The HTTP payload is usually used to serve HyperText Markup Language (HTML) web pages, which are plain text files with coded tags describing how the page should be formatted. A web browser can interpret the tags and display the text and other resources associated with the page, such as binary picture or sound files linked to the HTML page.

Using Firefox's web developer tools to inspect the HTTP requests and response headers involved in serving a typical modern web page. (Screenshot courtesy of Mozilla Foundation.)

HTTP also features a forms mechanism (POST) that enables a user to submit data from the client to the server. HTTP is nominally a stateless protocol; this means that the server is not required to preserve information about the client during a session. However, the basic functionality of HTTP servers is also often extended by support for scripting and programmable features (web applications). Servers can also set text file cookies to preserve session information. These coding features, plus integration with databases, increase flexibility and interactivity, but also increase the attack surface and expose more vulnerabilities.

Many argue that HTTP is a stateful protocol. Version 2 of HTTP adds more state-preserving features (blog.zamicol.com/2017/05/is-http2-stateful-protocol-application.html).

Web Servers

Most organizations have an online presence, represented by a website. In order to run a website, it must be hosted on an HTTP server connected to the Internet. Larger organizations or SMEs with the relevant expertise may host websites themselves, but more typically, an organization will lease a server or space on a server from an ISP. The following types of hosting packages are common:

●	Dedicated server -The ISP allocates your own private server computer. This type of service is usually unmanaged (or management comes at additional cost).

●	Virtual Private Server (VPS)-The ISP allocates you a virtual machine (VM) on a physical server. This is isolated from other customer instances by the hypervisor.

●	Cloud hosting-Your website is run on a cloud over several hardware computers, allowing more scalability if demand patterns change.

●	Shared hosting-Your website is hosted within a private directory on a shared server. Performance can be severely affected by other sites hosted on the server, because all the sites are competing for the same resources.

The main web server platforms are Apache®, Microsoft Internet Information Server (IIS), and nginx.

SECURE SOCKETS LAYER/TRANSPORT LAYER SECURITY

One of the critical problems for the provision of early websites was the lack of security in HTTP. Under HTTP, all data is sent unencrypted, and there is no authentication of client or server. Secure Sockets Layer (SSL) was developed by Netscape in the 1990s to address these problems. SSL proved very popular with the industry. Transport Layer Security (TLS) was developed from SSL and ratified as a standard by the IETF.

SSL/TLS works as a layer between the Application and Transport layers of the TCP/IP stack, or, in OSI terms, at the Session layer. It's normally used to encrypt TCP connections. When it is used with the HTTP application, it is referred to as HTTP Secure (HTTPS). TLS can also be used to secure other TCP application protocols, such as FTP, POP3/IMAP, SMTP, and LDAP.

TLS can also be used with UDP, referred to as Datagram Transport Layer Security (DTLS), most often in virtual private networking (VPN) solutions.

To implement HTTPS, the web server is installed with a digital certificate issued by some trusted certificate authority (CA). The certificate uses encrypted data to prove the identity of the server, assuming that the client also trusts the CA. The certificate is a wrapper for a public/private encryption key pair. The private key is kept a secret known only to the server; the public key is given to clients via the digital certificate.

The server and client use the key pair in the digital certificate and a chosen cipher suite within the SSL/TLS protocol to set up an encrypted tunnel. Even though someone else might know the public key, they cannot decrypt the contents of the tunnel without obtaining the server's private key. This means that the communications cannot be read or changed by a third party.

Encrypted traffic between the client and server is sent over TCP port 443 (by default), rather than the open and unencrypted port 80. A web browser will open a secure session to a server providing this service by using a URL starting with https:// and it will also show a padlock icon in the address bar to indicate that the connection is secure. A website can be configured to require a secure session and reject or redirect plain HTTP requests.

HTTPS padlock icon. (Screenshot courtesy of Microsoft.)

FILE TRANSFER PROTOCOL

It is often necessary to transfer files to and from appliances or servers from a remote host. Many methods of remote file access use some form of the File Transfer Protocol (FTP). While HTTPS-based web services and web applications can now offer file downloads to end users, FTP is still often used to perform administrative upload/download of files to and from servers and appliances. For these uses, it is important to secure the FTP session.

Active versus Passive FTP

An FTP client connects to TCP port 21 on an FTP server and opens a chosen dynamic client port number (n). The TCP port 21 control port is used to transfer commands and status information, but not for data transfer. Data transfer can operate in one of two modes: active or passive. In active mode, the client sends a PORT command specifying its chosen data connection port number (typically n+1), and the server opens the data connection between the chosen client port and TCP port 20 on the server.

FTP in active mode. (Images © 123RF.com.)

In passive mode, the client opens a data port (again, typically n+1) and sends the PASV command to the server's control port. The server then opens a random high port number and sends it to the client using the PORT command. The client then initiates the connection between the two ports.

FTP in passive mode. (Images © 123RF.com.)

Active FTP poses a configuration problem for some firewalls, as the server is initiating the inbound connection, but there is no way of predicting which port number will be utilized. However, not all FTP servers and clients can operate in passive mode. If this is the case, check that firewalls installed between the client and server can support active FTP (stateful inspection firewalls).

Another problem is that the control connection can remain idle when the data connection is in use, meaning that the connection can be "timed out" by the firewall (or other routing device).

Trivial File Transfer Protocol

The Trivial File Transfer Protocol (TFTP) is a connectionless protocol running over UDP port 69. Consequently, TFTP does not provide the guaranteed delivery offered by FTP and is only suitable for transferring small files. Also, it only supports reading ( GET ) and writing ( PUT ) files, not directory browsing, file deletion, or any of the other features of FTP. A TFTP server is most commonly used by legacy network appliances (switches, routers, diskless workstations, and printers) to download configuration files. It can also be used as a backup and restore method for configuration files. However, TFTP has no security mechanisms and appliances are no longer as resource constrained as they were in the early days of networking. Consequently, secure protocols are now preferred for these functions.

SECURE FILE TRANSFER PROTOCOL

Secure FTP (SFTP) addresses the privacy and integrity issues of FTP by encrypting the authentication and data transfer between client and server. In SFTP, a secure link is created between the client and server using Secure Shell (SSH) over TCP port 22. Ordinary FTP commands and data transfer can then be sent over the secure link without risk of eavesdropping. This solution requires an SSH server that supports SFTP plus SFTP client software.

WinSCP SFTP client. (Screenshot courtesy of WinSCP.)

Another means of securing FTP is to use the connection security protocol SSL/TLS. There are two means of configuring FTP over TLS:

●	Explicit TLS (FTPES)-Use the AUTH TLS command to upgrade an unsecure connection established over port 21 to a secure one. This protects authentication credentials. The data connection for the actual file transfers can also be encrypted (using the PROT command).

●	Implicit TLS (FTPS)-Negotiate an SSL/TLS tunnel before the exchange of any FTP commands. This mode uses the secure port 990 for the control connection.

FTPS is tricky to configure when there are firewalls between the client and server. Consequently, FTPES is usually the preferred method.

FILE AND PRINT SERVICES

File and print services allow network clients to share access to disk and printer resources.

Server Message Block

On a Windows® network, the File/Print Sharing Service is provided by the Server Message Block (SMB) protocol. SMB allows a host to share its directories/files and printers to make them available for other machines to use. Support for SMB in UNIX- or Linux-based machines and network attached storage (NAS) appliances is provided by using the Samba software suite (samba.org/samba/what\_is\_samba.html), which allows a Windows client to access a Linux host as though it were a Windows file or print server.

On legacy networks, SMB ran as part of an older network services protocol called NetBIOS on TCP port 139. If no legacy client support is required, however, SMB is more typically run directly over TCP port 445. SMB should be restricted to use only on local networks. It is important that any traffic on the NetBIOS port ranges (137-139) and port 445 be blocked by a perimeter firewall.

SMB version 3 supports message encryption, which can be enabled on a file server or on a per-share basis. An encrypted share can only be accessed by an SMB 3.0 or higher client.

SMB has gone through several updates, with SMB3 as the current version. SMB1 has very serious security vulnerabilities and is now disabled by default on current Windows versions (docs.microsoft.com/en-us/windows-server/storage/file-server/troubleshoot/detect-enable-and-disable-smbv1-v2-v3).

Remote Print Protocols

A printer can be connected to the network using a cabled or wireless link and configured with an IP address and FQDN. Hosts need to be able to connect to the printer, configure options and print settings, send print jobs, and receive status messaging, such as out of paper errors. These functions are implemented using a remote print protocol to communicate between the print monitor process running on the host and the print device:

●	Port 9100-This can be referred to as the standard TCP/IP port, AppSocket, or JetDirect. This port just establishes a TCP connection to transfer raw Page Description Language (PDL) print job data and Printer Job Language (PJL) configuration and management data. The two most common PDLs are PostScript (PS) and Printer Command Language (PCL). Most printers support bidirectional status messaging to inform the host's print monitor about error conditions, such as out of paper or paper jam.

●	Internet Printing Protocol (IPP)-This is an adapted form of HTTP that uses TCP port 631 and can be implemented as a secure protocol (IPPS). It provides better support for status messaging than port 9100.

●	Web Services for Devices (WSD)/AirPrint-These technologies allow a print device to advertise service capabilities over the network and for Windows and MacOS/iOS hosts respectively to add the device using plug-and-play and manage it using bidirectional status messaging. They also allow for secure connections to the print device.

●	Printer sharing-This means that a host connects to the printer (using a local or network connection) and then shares the printer object with other hosts using SMB. Print jobs and status messaging are sent via the host that shared the printer.

DATABASE SERVICES

A database provisions information in a format that can be read and updated through some type of query language. There are two main types of databases. Relational databases store information in tables with rows (records) and columns (fields). Relationships between data fields in different tables is created using key fields that uniquely identify each record. Relational databases are operated using structured query language (SQL). SQL defines commands such as SELECT to retrieve information or UPDATE to change it.

SQL has been implemented in relational database management system (RDBMS) platforms by several different vendors. As well as providing an implementation of SQL, an RDBMS provides management tools and often a GUI to use to operate the database. A remote access protocol allows a client to connect to the database server over the network and allows replication traffic to move between database servers. Replication is a means of synchronizing the data held on each server. Each RDBMS uses a different TCP port to distinguish it as an application service:

●	Oracle's remote data access protocol SQL\*Net uses TCP/1521.

●	Microsoft SQL Server uses TCP/1433.

●	The open-source MySQL platform uses TCP/3306. The MariaDB platform forked from MySQL uses the same port.

●	The open-source PostgreSQL platform uses TCP/5432.

These are the principal ports. An RDBMS is likely to use other TCP or UDP ports for additional functions.

By default, these ports are unsecure. However, the RDBMS server can be installed with a certificate and configured to enable TLS transport encryption. The connection is still made over the same port. Either the server or the client can be configured to require encryption and drop the connection if a valid security profile is not available. Optionally, the client can also be installed with a certificate and the server configured to refuse connections from clients without a valid certificate.

The other type of database is referred to as NoSQL or "not only SQL." Rather than highly structured relational tables, NoSQL data can use a variety of formats, such as key-value pairs or wide columns (where rows do not have to have the same set of fields). NoSQL databases are typically accessed using an application programming interface (API) over HTTPS.

All the RDBMS platforms also provide support for NoSQL datastores. There are also dedicated NoSQL platforms, such as MongoDB, Amazon's DynamoDB, and CouchDB.

Topic 11B: Explain the Use of Email and Voice Services

SIMPLE MAIL TRANSFER PROTOCOL

Electronic mail enables a person to compose a message and send it to another user on their own network (intranet) or anywhere in the world via the Internet. Email uses separate mail transfer and mailbox access protocols:

Operation of delivery and mailbox email protocols. (Images © 123RF.com.)

The Simple Mail Transfer Protocol (SMTP) specifies how email is delivered from one system to another. The SMTP server of the sender discovers the IP address of the recipient SMTP server by using the domain name part of the recipient's email address. The SMTP servers for the domain are registered in DNS using Mail Exchange (MX) and host (A/AAAA) records.

SMTP does not queue messages indefinitely. If there is a communication problem, the SMTP server retries at regular intervals before timing out and returning a non-delivery report (NDR) to the sender. The NDR will contain an error code indicating the reason the item could not be delivered. SMTP provides no mechanism for persistent storage of messages.

SMTP communications can be secured using the TLS version of the protocol (SMTPS). This works much like HTTPS with a certificate on the SMTP server and a negotiation between client and server about which cipher suites to use. There are two ways for SMTP to use TLS:

●	STARTTLS-This is a command that upgrades an existing unsecure connection to use TLS. This is also referred to as explicit TLS or opportunistic TLS.

●	SMTPS-This establishes the secure connection before any SMTP commands (HELO, for instance) are exchanged. This is also referred to as implicit TLS.

The STARTTLS method is generally more widely implemented than SMTPS. Typical SMTP configurations use the following ports and secure services:

●	Port 25-Used for message relay between SMTP servers, or message transfer agents (MTAs). If security is required and supported by both servers, the STARTTLS command can be used to set up the secure connection.

●	Port 587-Used by mail clients or message submission agents (MSAs) to submit messages for delivery by an SMTP server. Servers configured to support port 587 should use STARTTLS and require authentication before message submission.

Mail clients can use port 25 to submit messages to the server for delivery, but this is not best practice. Use of port 25 is typically reserved for relay between servers.

MAILBOX ACCESS PROTOCOLS

SMTP is useful only to deliver mail to hosts that are permanently available. When a message is received by an SMTP server, it delivers the message to a mailbox server. This could be a separate machine or a separate process running on the same server. A mailbox access protocol allows the user's client email software to operate the mailbox.

Post Office Protocol

The Post Office Protocol (POP) is an early example of a mailbox access protocol. POP is often referred to as POP3 because the active version of the protocol is version 3. A POP client application, such as Microsoft Outlook® or Mozilla Thunderbird®, establishes a connection to the POP server on TCP port 110. The user is authenticated (by username and password), and the contents of his or her mailbox are downloaded for processing on the local PC. Generally speaking, the messages are deleted from the mailbox server when they are downloaded, though some clients have the option to leave messages on the server.

Configuring mailbox access protocols on a server. (Screenshot courtesy of Mozilla Foundation.)

Like other TCP application protocols, POP transfers all information as cleartext. This means anyone able to monitor the session would be able to obtain the user's credentials and snoop on messages. POP can be secured by using TLS encryption. The default TCP port for secure POP (POP3S) is port 995.

Internet Message Access Protocol

POP has some significant limitations, some of which are addressed by the Internet Message Access Protocol (IMAP). Like POP, IMAP is a mail retrieval protocol, but with mailbox management features lacking in POP. POP is primarily designed for dial-up access; the client contacts the server to download its messages, and then disconnects. IMAP supports permanent connections to a server and connecting multiple clients to the same mailbox simultaneously. It also allows a client to manage the mailbox on the server (to organize messages in folders and to control when they are deleted, for instance) and to create multiple mailboxes.

A client connects to an IMAP server over TCP port 143, but this port is unsecure. Connection security can be established using a TLS. The default port for IMAPS is TCP/993.

In a Windows environment, the proprietary Messaging Application Programming Interface (MAPI) protocol is typically used to access Microsoft Exchange mailboxes. MAPI uses HTTPS as a secure transport protocol.

VOICE AND VIDEO SERVICES

Voice over IP (VoIP), web conferencing, and video teleconferencing (VTC) solutions have become standard methods for the provision of business and social communications. Many networks are upgrading from legacy voice services to IP-based protocols and products.

Private Branch Exchange

Legacy voice services use the public switched telephone network (PSTN). A residential telephone installation would be serviced by a simple box providing a one- or two-line analog interface to the local exchange. This analog interface is also referred to as the plain old telephone service (POTS). Each line provides a single channel for an incoming or outgoing call. A typical business requires tens or hundreds of lines for voice communications, let alone capacity for data communications. Historically, this requirement would have been facilitated by a digital trunk line, also referred to as a Time Division Multiplexing (TDM) circuit. A TDM can multiplex separate voice and data channels for transmission over a single cable.

A private branch exchange (PBX) is an automated switchboard providing a single connection point for an organization's voice lines. A TDM-based PBX connects to the telecommunications carrier over a digital trunk line, which will support multiple channels (inward and outward calls). The PBX allows for the configuration of the internal phone system to direct and route calls to local extensions, and provides other telephony features such as call waiting, music on hold, and voice mail.

VoIP-Enabled PBX

TDM-based PBXes are being replaced by hybrid and fully IP/VoIP PBXes. For internal calls and conferences, a VoIP PBX establishes connections between local VoIP endpoints with data transmitted over the local Ethernet network. A VoIP PBX can also route incoming and outgoing calls from and to external networks. This might involve calls between internal and external VoIP endpoints, or with voice telephone network callers and receivers. A VoIP PBX will also support features such as music on hold and voice mail.

A TDM PBX is supplied as vendor-specific hardware. A VoIP PBX can be implemented as software running on a Windows or Linux server. Examples of software-based solutions include 3CX (3cx.com) and Asterisk ( asterisk.org ). There are also hardware solutions, where the VoIP PBX runs on a router, such as Cisco Unified Communications Manager ( cisco.com/c/en/us/products/unified-communications/unified-communications-manager-callmanager/index.html ).

A VoIP PBX would normally be placed at the network edge and be protected by a firewall. Internal clients connect to the PBX over Ethernet data cabling and switching infrastructure, using Internet Protocol (IP) at the Network layer for addressing. The VoIP PBX uses the organization's Internet link to connect to a VoIP service provider, which facilitates inward and outward dialing to voice-based telephone networks.

A VoIP PBX facilitates internal IP calls and calls to and from external VoIP networks and the landline and cellular telephone networks. (Images © 123RF.com)

VOIP PROTOCOLS

Voice and video services can be challenging to support because they require response times measured in milliseconds (ms). Delayed responses will result in poor call or video quality. This type of data can be one-way, as is the case with media streaming, or two-way, as is the case with VoIP and VTC.

The protocols designed to support real-time services cover one or more of the following functions:

●	Session control-Used to establish, manage, and disestablish communications sessions. They handle tasks such as user discovery (locating a user on the network), availability advertising (whether a user is prepared to receive calls), negotiating session parameters (such as use of audio/video), and session management and termination.

●	Data transport-Handles the delivery of the actual video or voice information.

●	Quality of Service (QoS)-Provides information about the connection to a QoS system, which in turn ensures that voice or video communications are free from problems, such as dropped packets, delay, or jitter.

Session Initiation Protocol

The Session Initiation Protocol (SIP) is one of the most widely used session control protocols. SIP endpoints are the end-user devices (also known as user agents), such as IP-enabled handsets or client and server web conference software. Each device, conference, or telephony user is assigned a unique SIP address known as a SIP Uniform Resource Indicator (URI). Examples of SIP URIs include:

sip:jaime@515support.com

sip:2622136227@515support.com

sip:jaime@2622136227

meet:sip:organizer@515support.com;ms-app=conf;ms-conf-id=subg42

There is also a tel: URI scheme allowing SIP endpoints to dial a landline or cell phone. A tel: URI can either use the global (E.164) format (such as tel:+1-866-8358020) or a local format (for internal extensions).

SIP typically runs over UDP or TCP ports 5060 (unsecured) and 5061 (SIP-TLS). SIP has its own reliability and retransmission mechanisms and can thus be seen to benefit most from the lower overhead and reduced latency and jitter of UDP. Some enterprise SIP products use TCP anyway.

Real-Time Transport Protocol and RTP Control Protocol

While SIP provides session management, the actual delivery of real-time data uses different protocols. The principal one is Real-time Transport Protocol (RTP). RTP enables the delivery of a stream of media data via UDP, while implementing some of the reliability features usually associated with TCP communications. RTP works closely with the RTP Control Protocol (RTCP). Each RTP stream uses a corresponding RTCP session to monitor the quality of the connection and to provide reports to the endpoints. These reports can then be used by the applications to modify codec parameters or by the network stacks to tune Quality of Service (QoS) parameters.

VOIP PHONES

A VoIP/SIP endpoint can be implemented as software running on a computer or smartphone or as a dedicated hardware handset. VoIP phones use VLAN tagging to ensure that the SIP control and RTP media protocols can be segregated from normal data traffic. In a typical voice VLAN configuration, the LAN port on the handset is connected to the wall port, while the PC is connected to the PC port on the handset. The two devices share the same physical link, but data traffic is distinguished from voice traffic by configuring separate VLAN IDs.

Handsets can use Power over Ethernet (PoE), if available, to avoid the need for separate power cabling or batteries. There are also wireless handsets that work over 802.11 Wi-Fi networks.

Connection security for VoIP works in a similar manner to HTTPS. To initiate the call, the secure version of SIP (SIPS) uses digital certificates to authenticate the endpoints and establish an SSL/TLS tunnel. The secure connection established by SIPS can also be used to generate a master key to use with the secure versions of the transport and control protocols.

When you are installing a new handset, you should also test that the connection works and that the link provides sufficient call quality. Most service providers have test numbers to verify basic connectivity and perform an echo test call, which replays a message you record so that you can confirm voice quality.

VOICE GATEWAYS

SIP endpoints can establish communications directly in a peer-to-peer architecture, but it is more typical to use intermediary servers, directory servers, and VoIP gateways. There can also be requirements for on-premises integration between data and voice networks and equipment. A voice gateway is a means of translating between a VoIP system and legacy voice equipment and networks, such as POTS lines and handsets. There are many types of VoIP gateways, serving different functions. For example, a company may use VoIP internally, but connect to the telephone network via a gateway. To facilitate this, you could use a hybrid or hardware-based VoIP PBX with a plug-in or integrated VoIP gateway, or you could use a separate gateway appliance. There are analog and digital types to match the type of incoming landline. An analog version of this type of gateway is also called a Foreign Exchange Office (FXO) gateway.

VoIP gateway connecting a local network using VoIP calling to the ordinary telephone network. (Images © 123RF.com)

A VoIP gateway can also be deployed to allow a legacy analog or digital internal phone system to use a VoIP service provider to place calls. In this type of setup, low rate local and national calls might be placed directly, while international calls that would attract high charges if placed directly are routed via the VoIP service provider.

VoIP gateway connecting a local network using legacy PBX and handsets to a VoIP service provider. (Images © 123RF.com)

Finally, a VoIP gateway or adapter can be used to connect POTS handsets and fax machines to a VoIP PBX. This type of device is also called a Foreign Exchange Subscriber (FXS) gateway.

VoIP gateway connecting legacy handsets to a VoIP PBX. (Images © 123RF.com)

















Lesson 12: Ensuring Network Availability

Topic 12A: Explain the Use of Network Management Services

SECURE SHELL SERVERS AND TERMINAL EMULATORS

The name "terminal" comes from the early days of computing where configuration was performed by a teletype (TTY) device. The TTY is the terminal or endpoint for communication between the computer and the user. The TTY handles text input and output between the user and the shell, or command environment. Where the terminal accepts input and displays output, the shell performs the actual processing.

A terminal emulator is any kind of software that replicates this TTY input/output function. A given terminal emulator application might support connections to multiple types of shell. A remote terminal emulator allows you to connect to the shell of a different host over the network.

Secure Shell (SSH) is the principal means of obtaining secure remote access to UNIX and Linux servers and to most types of network appliances (switches, routers, and firewalls). As well as terminal emulation, SSH can be used as the secure file transfer protocol (SFTP). There are numerous commercial and open source SSH servers and terminal emulation clients available for all the major NOS platforms (UNIX®, Linux®, Windows®, and macOS®). The most widely used is OpenSSH (openssh.com). An SSH server listens on TCP port 22 by default.

SSH Host Key

An SSH server is identified by a public/private key pair, referred to as the host key. A mapping of host names to public keys can be kept manually by each SSH client, or there are various enterprise software products designed for SSH key management.

Confirming the SSH server's host key using the SSH client. (Screenshot courtesy of Microsoft.)

The host key must be changed if any compromise of the host is suspected. If an attacker has obtained the private key of a server or appliance, they can masquerade as that server or appliance and perform a spoofing attack, usually with a view to obtaining other network credentials. You might also change the key to use a longer bit strength.

SSH Client Authentication

The server's host key is used to set up a secure channel to use for the client to submit authentication credentials. SSH allows various methods for the client to authenticate to the SSH server. Each of these methods can be enabled or disabled as required on the server:

●	Username/password -The client submits credentials that are verified by the SSH server either against a local user database or using a network authentication server.

●	Public key authentication-Each remote user's public key is added to a list of keys authorized for each local account on the SSH server.

●	Kerberos-The client submits the Kerberos credentials (a Ticket Granting Ticket) obtained when the user logged onto the workstation to the server using the Generic Security Services Application Program Interface (GSSAPI). The SSH server contacts the Ticket Granting Service (in a Windows environment, this will be a domain controller) to validate the credential.

Managing valid client public keys is a critical security task. Many recent attacks on web servers have exploited poor key management. If a user's private key is compromised, delete the public key from the appliance then regenerate the key pair on the user's (remediated) client device and copy the public key to the SSH server. Always delete public keys if the user's access permissions have been revoked.

SECURE SHELL COMMANDS

SSH features a rich command set, fully documented at the OpenSSH website (openssh.com/manual.html). Some of the most important commands are:

●	sshd-Start the SSH Daemon (server). Parameters such as the host's certificate file, port to listen on, and logging options can be set via switches or in a configuration file.

●	ssh-keygen-Create a key pair to use to access servers. The private key must be stored securely on your local computer. The public key must be copied to the server. You can use the ssh-copy-id command to do this, or you can copy the file manually.

●	ssh-agent-Configure a service to use to store the keys used to access multiple hosts. The agent stores the private key for each public key securely and reduces the number of times use of a private key has to be confirmed with a passphrase. This provides a single sign-on (SSO) mechanism for multiple SSH servers. The ssh-add command is used to add a key to the agent.

●	ssh Host -Use the SSH client to connect to the server running at Host . Host can be an FQDN or IP address. You can also create a client configuration file.

●	ssh Username@Host -Use the SSH client to connect to the server running at Host with a different Username .

●	ssh Host "Command or Script" -Use the SSH client to execute a command or script on the remote server running at Host without starting a shell.

●	scp Username@Host:RemoteFile /Local/Destination -A file transfer client with remote copy/rcp-like command interface

●	sftp-A file transfer client with FTP-like command interface.

TELNET

Telnet is both a protocol and a terminal emulation software tool that transmits shell commands and output between a client and the remote host. In order to support Telnet access, the remote computer must run a service known as the Telnet Daemon. The Telnet Daemon listens on TCP port 23 by default.

PuTTY Telnet client. (Screenshot courtesy of PuTTY.)

A Telnet interface can be password protected but the password and other communications are not encrypted and therefore could be vulnerable to packet sniffing and replay. Historically, Telnet provided a simple means to configure switch and router equipment, but only secure access methods should be used for these tasks now. Ensure that the Telnet service is uninstalled or disabled, and block access to port 23.

REMOTE DESKTOP PROTOCOL

Telnet and SSH provide terminal emulation for command-line shells. This is sufficient for most administrative tasks, but where users want to connect to a desktop, they usually prefer to work with a graphical interface. A GUI remote administration tool sends screen and audio data from the remote host to the client and transfers mouse and keyboard input from the client to the remote host. Remote Desktop Protocol (RDP) is Microsoft's protocol for operating remote GUI connections to a Windows machine. RDP uses TCP port 3389. The administrator can specify permissions to connect to the server via RDP and can configure encryption on the connection.

RDP is mainly used for the remote administration of a Windows server or client, but another function is to publish software applications on a server, rather than installing them locally on each client (application virtualization).

RDP clients are available for other operating systems, including Linux, macOS, iOS, and Android so you can connect to a Windows desktop remotely using a non-Windows device. There are also open-source RDP server products, such as xrdp (xrdp.org).

NETWORK TIME PROTOCOL

Many applications on networks are time-dependent and time-critical, such as authentication and security mechanisms, scheduling applications, and backup software. The Network Time Protocol (NTP) enables the synchronization of these time-dependent applications. NTP works over UDP on port 123.

Top-level NTP servers (stratum 1) obtain the Coordinated Universal Time (UTC) via a direct physical link to an accurate clock source, such as an atomic clock accessed over the General Positioning System (GPS). An NTP server that synchronizes its time with a stratum 1 server over a network is operating at stratum 2. Each stratum level represents a step away from the accurate clock source over a network link. These lower stratum servers act as clients of the stratum 1 servers and as servers or time sources to lower stratum NTP servers or client hosts. Most switches and routers can be configured to act as time servers to local client hosts and this function is also typically performed by network directory servers. It is best to configure each of these devices with multiple reference time sources (at least three) and to establish them as peers to allow the NTP algorithm to detect drifting or obviously incorrect time values.

Stratum 1 NTP servers are directly connected to an accurate clock source. Each stratum level below one represents a network hop away from that accurate time source. (Images © 123RF.com.)

Client hosts (application servers and workstations) usually obtain the time by using a modified form of the protocol called Simple NTP (SNTP). SNTP works over the same port as NTP. A host that supports only SNTP cannot act as a time source for other hosts. In Windows, the Time Service can be configured by using the w32tm command. In Linux, the ntp package can be configured via /etc/ntp.conf.

If a server or host is configured with the incorrect time, it may not be able to access network services. Authentication, and other security mechanisms will often fail if the time is not synchronized on both communicating devices. In this situation, errors are likely to be generic failed or invalid token type messages. Always try to rule out time synchronization as an issue early in the troubleshooting process.

If a local stratum 1 server cannot be implemented on the local network, the time source can be configured using one or more public NTP server pools, such as time.google.com, time.windows.com, time.apple.com, time.nist.gov, or pool.ntp.org.

Topic 12B: Use Event Management to Ensure Network Availability

PERFORMANCE METRICS, BOTTLENECKS, AND BASELINES

Network monitoring tools fulfill a wide range of functions. As input, they can capture and analyze traffic, monitor interface and device metrics, and consolidate log data. As output, they can alert you to events, help you define baselines, analyze traffic patterns and congestion, determine upgrade and forecast needs, and generate reports for management.

Performance Metrics

When you are monitoring a network host or intermediate system, several performance metrics can tell you whether the host is operating normally:

●	Bandwidth/throughput-This is the rated speed of all the interfaces available to the device, measured in Mbps or Gbps. For wired Ethernet links, this will not usually vary, but the bandwidth of WAN and wireless links can change over time.

●	CPU and memory-Devices such as switches and routers perform a lot of processing. If CPU and/or system memory utilization (measured as a percentage) is very high, an upgrade might be required. High CPU utilization can also indicate a problem with network traffic.

●	Storage-Some network devices require persistent storage (typically, one or more flash drives) to keep configuration information and logs. Storage is measured in MB or GB. If the device runs out of storage space, it could cause serious errors. Servers also depend on fast input/output (I/O) to run applications efficiently.

Bottlenecks

A bottleneck is a point of poor performance that reduces the productivity of the whole network. A bottleneck may occur because a device is underpowered or faulty. It may also occur because of user or application behavior. To identify the cause of a bottleneck, you need to identify where and when on the network overutilization or excessive errors occur. If the problem is continual, it is likely to be device-related; if the problem only occurs at certain times, it is more likely to be user- or application-related.

Performance Baselines

A performance baseline establishes the resource utilization metrics at a point in time, such as when the system was first installed. This provides a comparison to measure system responsiveness later. For example, if a company is expanding a remote office that is connected to the corporate office with an ISP's basic tier package, the baseline can help determine if there is enough reserve bandwidth to handle the extra user load, or if the basic package needs to be upgraded to support higher bandwidths.

Reviewing baselines is the process of evaluating whether a baseline is still fit for purpose or whether a new baseline should be established. Changes to the system usually require a new baseline to be taken.

ENVIRONMENTAL MONITORING

Distinct from performance monitors, an environmental sensor is used to detect factors that could threaten the integrity or availability of an appliance or its function.

Servers and appliances are fitted with internal sensors to monitor conditions within the device chassis. These can report problems such as excessive temperatures within the device chassis, fan speeds, component failure, and chassis intrusion to a monitoring system.

CPUID's HWMONITOR app can report temperatures from sensors installed on PC components. (Screenshot used by permission of CPUID.)

Sensors can also be installed to measure ambient environmental conditions for a network rack or enclosure or within a server room or equipment closet. The following environmental factors need monitoring:

●	Temperature-High temperature will make it difficult for device and rack cooling systems to dissipate heat effectively. This increases the risk of overheating of components within device chassis and consequent faults.

●	Humidity-More water vapor in the air risks condensation forming within a device chassis, leading to corrosion and short circuit faults. Conversely, very low humidity increases risks of static charges building up and damaging components.

●	Electrical-Computer systems need a stable power supply, free from outages (blackouts), voltage dips (brownouts), and voltage spikes and surges. Sensors built into power distribution systems and backup battery systems can report deviations from a normal power supply.

●	Flooding-There may be natural or person-made flood risks from nearby water courses and reservoirs or risks from leaking plumbing or fire suppression systems. Electrical systems need to be shut down immediately in the presence of any significant amount of water.

SIMPLE NETWORK MANAGEMENT PROTOCOL

Stand-alone devices may have a web console to use for performance and environmental monitoring. Local access is not scalable to managing tens or hundreds of devices, however.

The Simple Network Management Protocol (SNMP) is a widely used framework for remote management and monitoring of servers and network appliances. SNMP consists of agents and a monitoring system.

SNMP Agents

The agent is a process (software or firmware) running on a switch, router, server, or other SNMP-compatible network device. This agent maintains a database called a Management Information Base (MIB) that holds statistics relating to the activity of the device, such as the number of frames per second handled by a switch. Each parameter stored in a MIB is referred to by a numeric Object Identifier (OID). OIDs are stored within a tree structure. Part of the tree is generic to SNMP, while part can be defined by the device vendor.

An agent is configured with the Community Name of the computers allowed to manage the agent and the IP address or host name of the server running the management system. The community name acts as a rudimentary type of password. An agent can pass information only to management systems configured with the same community name. There are usually two community names; one for read-only access and one for read-write access (or privileged mode).

Configuring an SNMP agent on an OPNsense security appliance. (Screenshot courtesy of OPNsense.)

SNMP Monitor

An SNMP monitor is management software that provides a location from which you can oversee network activity. The monitor polls agents at regular intervals for information from their MIBs and displays the information for review. It also displays any trap operations as alerts for the network administrator to assess and act upon as necessary. The monitor can retrieve information from a device in two main ways:

●	Get-The software queries the agent for a single OID. This command is used by the monitor to perform regular polling (obtaining information from devices at defined intervals).

●	Trap-The agent informs the monitor of a notable event (port failure, for instance). The threshold for triggering traps can be set for each value.

The monitor can be used to change certain variables using the Set command. It can also walk an MIB subtree by using multiple Get and Get Next commands. This is used to discover the complete layout of an MIB. Device queries take place over UDP port 161; traps are communicated over UDP port 162.

SNMP collects information from network devices for diagnostic purposes. (Images © 123RF.com)

NETWORK DEVICE LOGS

Network device logs are one of the most valuable sources of performance, troubleshooting, and security auditing information. A single logged event consists of metadata, such as the date and time, category, and event ID, plus a description and contents of error or informational output. For example, you can use a system log to troubleshoot an IP conflict by looking for TCP/IP events or to determine when and why a system was shut down.

While the specifics of what and where events are logged can vary widely from platform to platform, it is possible to discern some general log types, including system, security, application, and performance or traffic.

System and Application Logs

A system log records startup events plus subsequent changes to the configuration at an OS level. This will certainly include kernel processes and drivers but could also include core services.

By contrast, an application log records data for a single specific service, such as DNS, HTTP, or an RDBMS. Note that a complex application could write to multiple log files, however. For example, the Apache web server logs errors to one file and access attempts to another.

Audit Logs

An audit log records use of authentication and authorization privileges. It will generally record success/fail type events. An audit log might also be described as an access log or security log. Audit logging might be performed at an OS level and at a per-application level.

Viewing audit logs on an OPNsense security appliance. (Screenshot courtesy of OPNsense.)

Audit logs typically associate an action with a particular user. This is one of the reasons that it is critical that users not share logon details. If a user account is compromised, there is no means of tying events in the log to the actual attacker.

Performance/Traffic Logs

Performance and traffic logs record statistics for compute, storage, and network resources over a defined period.

LOG COLLECTORS AND SYSLOG

A log collector aggregates event messages from numerous devices to a single storage location. As well as aggregating logs, the system can be configured to run one or more status and alerting dashboards.

Syslog is an example of a protocol and supporting software that facilitates log collection. It has become a de facto standard for logging events from distributed systems. For example, syslog messages can be generated by Cisco® routers and switches, as well as UNIX or Linux servers and workstations. A syslog collector usually listens on UDP port 514.

Configuring an OPNsense security appliance to transmit logs to a remote syslog server. (Screenshot courtesy of OPNsense.)

As well as a protocol for forwarding messages to a remote log collector, Syslog provides an open format for event data. A syslog message comprises a PRI code, a header containing a timestamp and host name, and a message part. The PRI code is calculated from the facility and a severity level. The message part contains a tag showing the source process plus content. The format of the content is application dependent. It might use space- or comma-delimited fields or name/value pairs, such as JavaScript Object Notation (JSON) data.

EVENT MANAGEMENT

Devices can generate thousands of events per hour. A system for prioritizing them between ones that require immediate or long-term response is vital. Most logging systems categorize each event. For example, in Windows, system and application events are defined as Informational, Warning, or Critical, while audit events are categorized as Success or Fail.

Syslog severity levels are as follows:

Code	Level	Interpretation

0	Emergency	The system is unusable (kernel panic)

1. `	`Alert	A fault requiring immediate remediation has occurred
1. `	`Critical	A fault that will require immediate remediation is likely to develop
1. `	`Error	A nonurgent fault has developed
1. `	`Warning	A nonurgent fault is likely to develop
1. `	`Notice	A state that could potentially lead to an error condition has developed
1. `	`Informational	A normal but reportable event has occurred
1. `	`Debug	Verbose status conditions used during development and testing

The logging level configured on each host determines the maximum level at which events are recorded or forwarded. For example, if the logging level for remote forwarding is set to 4, events that are level 5, 6, or 7 are not forwarded.

An automated event management system can be configured to generate some sort of alert when certain event types of a given severity are encountered. Alerts can also be generated by setting thresholds for performance counters. Examples include packet loss, link bandwidth drops, number of sessions established, delay/jitter in real-time applications, and so on. Most network monitors also support heartbeat tests so that you can receive an alert if a device or server stops responding to probes.

Setting alerts is a matter of balance. On the one hand, you do not want performance to deteriorate to the point that it affects user activity; on the other hand, you do not want to be overwhelmed by alerts.

You can also make a distinction between alerts and notifications. An alert means that the system has matched some sort of pattern or filter that should be recorded and highlighted. A notification means that the system sends a message to advertise the occurrence of the alert. A low priority alert may simply be displayed in the system dashboard. A high priority alert might use some sort of active notification messaging, such as emailing a system administrator, sending a text message (SMS) to a phone, or triggering a physical alarm signal.

Configuring alert and notification settings in EventSentry SIEM. (Screenshot courtesy of NETIKUS.NET Ltd.)

There should be some process for acknowledging and dismissing alerts as they are raised. A serious alert may need to be processed as an incident and assigned a job ticket for formal investigation. If an alert is a false positive, it can be dismissed. If the management system or dashboard is allowed to become cluttered with old alerts, it is much more difficult to identify new alerts and gauge the overall status of the network.


LOG REVIEWS

Monitoring involves viewing traffic, protocols, and events in real time. Network and log reviewing, or analysis involves later inspection and interpretation of captured data to determine what the data shows was happening on the network during the capture. Monitoring is aligned with incident response; analysis is aligned with investigating the cause of incidents or preventing incidents in the first place. It is important to perform performance analysis and log review continually. Referring to the logs only after a major incident is missing the opportunity to identify threats and vulnerabilities or performance problems early and to respond proactively.

Not all performance incidents will be revealed by a single event. One of the features of log analysis and reporting software should be to identify trends. A trend is difficult to spot by examining each event in a log file. Instead, you need software to chart the incidence of types of events and show how the number or frequency of those events changes over time.

Plotting data as a graph is particularly helpful as it is easier to spot trends or spikes or troughs in a visualization of events, rather than the raw data. Most performance monitors can plot metrics in a graph.

Data retrieved from a performance log file. (Screenshot courtesy of Microsoft.)

Topic 12C: Use Performance Metrics to Ensure Network Availability

NETWORK METRICS

Quality of Service (QoS) protocols and appliances are designed to support real-time services. Applications such as voice and video that carry real-time data have different network requirements to the sort of data represented by file transfer. With "ordinary" data, it might be beneficial to transfer a file as quickly as possible, but the sequence in which the packets are delivered and the variable intervals between packets arriving do not materially affect the application. This type of data transfer is described as bursty.

While streaming video applications can have a high bandwidth requirement in terms of the sheer amount of data to be transferred, bandwidth on modern networks is typically less of a problem than packet loss, latency, and jitter.

Bandwidth

Bandwidth is the amount of information that can be transmitted, measured in bits per second (bps), or some multiple thereof. When monitoring, you need to distinguish between the nominal data link/Ethernet bit rate, the throughput of a link at Layer 3, and the throughput available to an application.

Bandwidth for audio depends on the sampling frequency (Hertz) and bit depth of each sample. For example, telecommunications links are based on 64 Kbps channels. This was derived through the following calculation:

●	The voice frequency range is 4000 Hz. This must be sampled at twice the rate to ensure an accurate representation of the original analog waveform.

●	The sample size is 1 byte (or 8 bits). Therefore, 8 KHz x 8 bits = 64 Kbps.

For VoIP, bandwidth requirements for voice calling can vary, but allowing 100 Kbps per call upstream and downstream should be sufficient in most cases.

Bandwidth required for video is determined by image resolution (number of pixels), color depth, and the frame rate, measured in frames per second (fps).

Latency and Jitter

Problems with the timing and sequence of packet delivery are defined as latency and jitter. Latency is the time it takes for a transmission to reach the recipient, measured in milliseconds (ms). Jitter is defined as being a variation in the delay. Jitter manifests itself as an inconsistent rate of packet delivery. Jitter is also measured in milliseconds, using an algorithm to calculate the value from a sample of transit times.

Latency and jitter are not significant problems when data transfer is bursty, but real-time applications are much more sensitive to their effects because they manifest as echo, delay, and video slow down. If packets are delayed, arrive out of sequence, or are lost, then the receiving host must buffer received packets until the delayed packets are received. If packet loss or delay is so excessive that the buffer is exhausted, then noticeable audio or video problems (artifacts) are experienced by users.

You can test the latency of a link using tools such as ping, pathping, and mtr. You can also use mtr to calculate jitter. When assessing latency, you need to consider the Round Trip Time (RTT). VoIP is generally expected to require an RTT of less than 300 ms. Jitter should be 30 ms or less. The link should also not exhibit more than 1 percent packet loss.

BANDWIDTH MANAGEMENT

Latency and jitter on the Internet are difficult to control because of the number of different parties that are involved (both caller networks plus any ISP transit networks). On a local network, delay is typically caused by congestion. This means that the network infrastructure is not capable of meeting the demands of peak load.

You can either provision higher bandwidth links and/or faster switches and routers, or you can use some sort of bandwidth management mechanism. For example, if you are running VoIP over your network and someone decides to copy a 40 GB file down from a server, the file transfer has the potential to wreak havoc with VoIP call quality. Without QoS, switches and routers forward traffic based on best effort or first-in, first-out, meaning that frames or packets are forwarded in the order in which they arrive. A QoS system identifies the packets or traffic streams belonging to a specific application, such as VoIP, and prioritizes them over other applications, such as file transfer.

Differentiated Services

The Differentiated Services (DiffServ) framework classifies each packet passing through a device. Router policies can then be defined to use the packet classification to prioritize delivery. DiffServ is an IP (Layer 3) service tagging mechanism. It uses the Type of Service field in the IPv4 header (Traffic Class in IPv6). The field is populated with a 6-byte DiffServ Code Point (DSCP) by either the sending host or by the router. Packets with the same DSCP and destination are referred to as Behavior Aggregates and allocated the same Per Hop Behavior (PHB) at each DiffServ-compatible router.

DiffServ traffic classes are typically grouped into three types:

●	Best Effort.

●	Assured Forwarding (which is broken down into sub-levels).

●	Expedited Forwarding (which has the highest priority).

IEEE 802.1p

While DiffServ works at layer 3, IEEE 802.1p can be used at Layer 2 (independently or in conjunction with DiffServ) to classify and prioritize traffic passing over a switch or wireless access point. 802.1p defines a tagging mechanism within the 802.1Q VLAN field (it also often referred to as 802.1Q/p). The 3-bit priority field is set to a value between 0 and 7. Most vendors map DSCP values to 802.1p ones. For example, 7 and 6 can be reserved for network control (such as routing table updates), 5 and 4 map to expedited forwarding levels for 2-way communications, 3 and 2 map to assured forwarding for streaming multimedia, and 1 and 0 for "ordinary" best-effort delivery.

As well as invoking the priority tag, VLAN infrastructure is often used for traffic management on local networks. For example, voice traffic might be allocated to a different VLAN than data traffic.

TRAFFIC SHAPING

Quality of Service (QoS) is distinct from Class of Service (CoS). CoS mechanisms such as DiffServ and 802.1p just categorize protocols into groups that require different service levels and provide a tagging mechanism to identify a frame or packet's class. QoS allows fine-grained control over traffic parameters. For example, if a network link is congested, there is nothing that DiffServ and 802.1p can do about it, but a protocol such as Multiprotocol Label Switching (MPLS) with QoS functionality can reserve the required bandwidth and pre-determine statistics such as acceptable packet loss and maximum latency and jitter when setting up the link.

In terms of QoS, network functions are commonly divided into three planes:

●	Control plane-makes decisions about how traffic should be prioritized and where it should be switched.

●	Data plane-handles the actual switching of traffic.

●	Management plane-monitors traffic conditions.

Protocols, appliances, and software that can apply these three functions can be described as traffic shapers or bandwidth shapers. Traffic shapers delay certain packet types-based on their content-to ensure that other packets have a higher priority. This can help to ensure that latency is reduced for critical applications.

Simpler devices, performing traffic policing, do not offer the enhanced traffic management functions of a shaper. For example, typical traffic policing devices will simply fail to deliver packets once the configured traffic threshold has been reached (this is often referred to as tail drop). Consequently, there will be times when packets are being lost, while other times when the network is relatively idle, and the bandwidth is being under-utilized. A traffic shaper will store packets until there is free bandwidth available. Hopefully, this leads to consistent usage of the bandwidth and few lost packets.

It is essential that the selected device is capable of handling high traffic volumes. As these devices have a limited buffer, there will be situations when the buffer overflows. Devices can either drop packets and in essence provide traffic policing, or else they must implement a dropping algorithm. Random Early Detection (RED) is one of several algorithms that can be implemented to help manage traffic overflow on the shaper.

TRAFFIC ANALYSIS TOOLS

Effective bandwidth management or traffic shaping policies depend on detailed information about network traffic flows. Network analysis tools will help you to report on traffic conditions.

Throughput Testers

One fairly simple way to measure network throughput is to transfer a large file between two appropriate hosts. Appropriate in this sense means an appropriate subnet and representative of servers and workstations that you want to measure. It is also important to choose a representative time. There is not much point in measuring the throughput when the network is carrying no other traffic.

To determine your network throughput using this method, simply divide the file size by the amount of time taken to copy the file. For example, if you transfer a 1 GB file in half an hour, the throughput can be calculated as follows:

●	1 gigabyte is 1024 megabytes (1,073,741,824 bytes or 8,589,934,592 bits).

●	8,589,934,592 bits in 1,800 seconds is 4,772,186 bits per second or 4.55 Mbps.

This method derives a value that is different from the nominal data rate. Because two hosts are transferring the files between one another, it is the Application layers that handle the file transfer. The intervening layers on both hosts add complexity (headers) and introduce inaccuracy, such as corrupt frames that have to be retransmitted.

Several software utilities, such as iperf ( iperf.fr ), Ttcp (linux.die.net/man/1/ttcp), and bwping (bwping.sourceforge.io), can be used to measure network throughput. An instance of the tool is configured on two network hosts and the tools measure the throughput achieved between the sender and the listener.

iperf3 transfer report showing bitrate, jitter, and packet loss. (Screenshot courtesy of iperf.)

Top Talkers/Listeners

Top talkers are interfaces generating the most outgoing traffic (in terms of bandwidth), while top listeners are the interfaces receiving the most incoming traffic. Identifying these hosts and the routes they are using is useful in identifying and eliminating performance bottlenecks. Most network analyzer software comes with filters or built-in reporting to identify top talkers or top listeners.

The Endpoints report in Wireshark can be used to identify top talkers and top listeners. (Screenshot courtesy of Wireshark.)

Bandwidth Speed Testers

In addition to testing performance on a local network, you may also want to test Internet links using some type of bandwidth speed tester. There are many Internet tools available for checking performance. The two main classes are:

●	Broadband speed checkers-These test how fast the local broadband link to the Internet is. They are mostly designed for SOHO use. The tool will test downlink and uplink speeds, test latency using ping, and can usually compare the results with neighboring properties and other users of the same ISP.

●	Website performance checkers-These query a nominated website to work out how quickly pages load. One of the advantages of an online tool is that you can test your site's response times from the perspective of customers in different countries.

NETFLOW

A packet analyzer can be used to measure network traffic statistics but trying to record each frame imposes a heavy processing overhead on the network tap or mirror port. Collecting just the packet metadata, rather than the whole packet payload, reduces the bandwidth required by the sniffer. Technologies such as Cisco's NetFlow ( cisco.com/c/en/us/products/ios-nx-os-software/ios-netflow/index.html ) gather traffic metadata only and report it to a structured database. These technologies can also use sampling to further reduce processing demands. NetFlow has been redeveloped as the IP Flow Information Export (IPFIX) IETF standard (tools.ietf.org/html/rfc7011).

Using NetFlow involves deploying three types of components:

●	A NetFlow exporter is configured on network appliances (switches, routers, and firewalls). Each flow is defined on an exporter. A traffic flow is defined by packets that share the same characteristics, such as IP source and destination addresses and protocol type. These five bits of information are referred to as a 5-tuple. A 7-tuple flow adds the input interface and IP type of service data. Each exporter caches data for newly seen flows and sets a timer to determine flow expiration. When a flow expires or becomes inactive, the exporter transmits the data to a collector.

●	A NetFlow collector aggregates flows from multiple exporters. A large network can generate huge volumes of flow traffic and data records, so the collector needs a high bandwidth network link and substantial storage capacity. The exporter and collector must support compatible versions of NetFlow and/or IPFIX. The most widely deployed versions of NetFlow are v5 and v9.

●	A NetFlow analyzer reports and interprets information by querying the collector and can be configured to generate alerts and notifications. In practical terms, the collector and analyzer components are often implemented as a single product.

ntopng community edition being used to monitor NetFlow traffic data. (Screenshot used courtesy of ntop.)

INTERFACE MONITORING METRICS

You can collect data and configure alerts for interface statistics, whether on a network adapter or switch or router port.

●	Link state-Measures whether an interface is working (up) or not (down). You would configure an alert if an interface goes down so that it can be investigated immediately. You may also want to track the uptime or downtime percentage so that you can assess a link's reliability over time.

●	Resets-The number of times an interface has restarted over the counter period. Interfaces may be reset manually or could restart automatically if traffic volume is very high, or a large number of errors are experienced. Anything but occasional resets should be closely monitored and investigated. An interface that continually resets is described as flapping.

●	Speed-This is the rated speed of the interface, measured in Mbps or Gbps. For wired Ethernet links this will not usually vary, but the bandwidth of WAN and wireless links may change over time. For Ethernet links, the interface speed should be the same on both the host and switch ports.

●	Duplex-Most Ethernet interfaces operate in full duplex mode. If an interface is operating in half duplex mode, there is likely to be some sort of problem, unless you are supporting a legacy device.

●	Utilization-The data transferred over a period. This can either be measured as the amount of data traffic both sent and received (measured in bits or bytes per second or a multiple thereof) or calculated as a percentage of the available bandwidth.

You also need to differentiate between average utilization and peak utilization. If average utilization is around 80%, it may appear that there is sufficient bandwidth. However, if peak utilization often spikes to 100%, then that will manifest as delay and packet loss and may require that you upgrade the link. Monitoring the queue length can help to determine whether the link is a bottleneck.

●	Per-protocol utilization-Packet or byte counts for a specific protocol. It is often useful to monitor both packet counts and bandwidth consumption. High packet counts will incur processing load on the CPU and system memory resources of the appliance, even if the size of each packet is quite small.

●	Error rate-The number of packets per second that cause errors. Errors may occur as a result of interference or poor link quality causing data corruption in frames. In general terms, error rates should be under 1 percent; high error rates may indicate a driver problem, if a network media problem can be ruled out.

●	Discards/drops-An interface may discard incoming and/or outgoing frames for several reasons, including checksum errors, mismatched MTUs, packets that are too small (runts) or too large (giants), high load, or permissions- the sender is not on the interface's access control list (ACL) or there is some sort of VLAN configuration problem, for instance. Each interface is likely to class the type of discard or drop separately to assist with troubleshooting the precise cause.

Some vendors may use the term discard for frames that are rejected because of errors or security policies and drop for frames that are lost due to high load, but often the terms are used interchangeably.

●	Retransmissions-Errors and discards/drops mean that frames of data are lost during transmission between two devices. As a result, the communication will be incomplete, and the data will, therefore, have to be retransmitted to ensure application data integrity. If you observe high levels of retransmissions (as a percentage of overall traffic), you must analyze and troubleshoot the specific cause of the underlying packet loss, which could involve multiple aspects of network configuration and connectivity.

TROUBLESHOOTING INTERFACE ERRORS

As well as monitoring for traffic bottlenecks and other performance issues, interface errors might indicate a misconfiguration problem at the data link layer or interference at the physical layer.

Cyclic Redundancy Check Errors

A cyclic redundancy check (CRC) is calculated by an interface when it sends a frame. A CRC value is calculated from the frame contents to derive a 32-bit value. This is added to the header as the frame check sequence. The receiving interface uses the same calculation. If it derives a different value, the frame is rejected. The number of CRC errors can be monitored per interface.

CRC errors are usually caused by interference. This interference might be due to poor quality cable or termination, attenuation, mismatches between optical transceivers or cable types, or due to some external factor.

Encapsulation Errors

Encapsulation is the frame format expected on the interface. Encapsulation errors will prevent transmission and reception. If you check the interface status, the physical link will be listed as up, but the line protocol will be listed as down. This type of error can arise in several circumstances:

●	Ethernet frame type-Ethernet can use a variety of frame types. The most common is Ethernet II, but if a host is configured to use a different type, such as SNAP, then errors will be reported on the link.

●	Ethernet trunks-When a trunk link is established between two switches, it will very commonly use the Ethernet 802.1Q frame format. 802.1Q specifies an extra frame header to carry a VLAN ID and type of service data. If one switch interface is using 802.1Q but the other is not, this may be reported as an encapsulation error.

●	WAN framing-Router interfaces to provider networks can use a variety of frame formats. Often these are simple serial protocols, such as High-level Data Link Control (HDLC) or Point-to-Point Protocol (PPP). Alternatively, the interface may use encapsulated Ethernet over Asynchronous Transfer Mode (ATM) or Virtual Private LAN Service (VPLS) or an older protocol, such as Frame Relay. The interface on the Customer Edge (CE) router must be configured for the same framing type as the Provider Edge (PE) router.

Runt Frame Errors

A runt is a frame that is smaller than the minimum size (64 bytes for Ethernet). A runt frame is usually caused by a collision. In a switched environment, collisions should only be experienced on an interface connected to a legacy hub device and there is a duplex mismatch in the interface configuration (or possibly on a misconfigured link to a virtualization platform). If runts are generated in other conditions, suspect a driver issue on the transmitting host.

Giant Frame Errors

A giant is a frame that is larger than the maximum permissible size (1518 bytes for Ethernet II). There are two likely causes of giant frames:

●	Ethernet trunks-As above, if one switch interface is configured for 802.1Q framing, but the other is not, the frames will appear too large to the receiver, as 802.1Q adds 4 bytes to the header, making the maximum frame size 1522 bytes.

An Ethernet frame that is slightly larger (up to 1600 bytes) is often referred to as a baby giant.

●	Jumbo frames-A host might be configured to use jumbo frames, but the switch interface is not configured to receive them. This type of issue often occurs when configuring storage area networks (SANs) or links between SANs and data networks.











Lesson 13: Explaining Common Security Concepts

Topic 13A: Explain Common Security Concepts

SECURITY CONCEPTS

Establishing computer and network security means developing processes and controls that protect data assets and ensure business continuity by making network systems and hosts resilient to different kinds of attack.

The Confidentiality, Integrity, and Availability (CIA) Triad

One of the foundational principles of computer security is that the systems used to store, transmit, and process data must demonstrate three properties, often referred to as the CIA Triad:

●	Confidentiality means that certain information should only be known to certain people.

●	Integrity means that the data is stored and transferred as intended and that any modification is authorized.

●	Availability means that information is accessible to those authorized to view or modify it.

Vulnerability, Threat, and Risk

To perform assessment and monitoring, security teams must identify ways in which their systems could be attacked. These assessments involve vulnerabilities, threats, and risk:

●	Vulnerability-A weakness that could be accidentally triggered or intentionally exploited to cause a security breach.

●	Threat- The potential for someone or something to exploit a vulnerability and breach security. A threat may be intentional or unintentional. The person or thing that poses the threat is called a threat actor or threat agent. The path or tool used by a malicious threat actor can be referred to as the attack vector.

●	Risk-The likelihood and impact (or consequence) of a threat actor exercising a vulnerability.


Relationship between vulnerability, threat, and risk.

SECURITY RISK ASSESSMENTS

Many tools and techniques are available to ensure that network systems demonstrate three properties of the CIA triad. Selection and deployment of these tools is guided by security policies. Security policies ensure that an organization has evaluated the risks it faces and has put security controls in place to mitigate those risks. Making a system more secure is also referred to as hardening. Different security policies should cover every aspect of an organization's use of computer and network technologies, from procurement and change control to acceptable use.

Risk management is a process for identifying, assessing, and mitigating vulnerabilities and threats to the essential functions that a business must perform to serve its customers. Risk management is complex and treated very differently in companies and institutions of different sizes, and with different regulatory and compliance requirements. Most companies will institute enterprise risk management (ERM) policies and procedures, based on published frameworks.

Risk assessment is a subset of risk management where the company's systems and procedures are evaluated for risk factors. Separate assessments can be devised to perform an initial evaluation and ongoing monitoring of threats, vulnerabilities, and security posture.

Posture Assessment

There are many different ways of thinking about how IT services should be governed to fulfill overall business needs. Some organizations have developed IT service frameworks to provide best practice guides to implementing IT and cybersecurity. These frameworks can shape company policies and provide checklists of procedures, activities, and technologies that should ideally be in place.

Collectively, these procedures, activities, and tools can be referred to as security controls. A security control is something designed to give a system or data asset the properties of confidentiality, integrity, availability, and non-repudiation.

In theory, security controls or countermeasures could be introduced to address every risk factor. The difficulty is that security controls can be expensive, so you must balance the cost of the control with the cost associated with the risk. It is not possible to eliminate risk; rather, the aim is to mitigate risk factors to the point where the organization is exposed only to a level of risk that it can afford. The overall status of risk management is referred to as risk posture. Risk posture shows which risk response options can be identified and prioritized. Posture assessment is often performed with reference to an IT or security framework. The framework can be used to assess the organization’s maturity level in its use of security policies and controls.

Process Assessment

Mitigating risk can involve a large amount of expenditure so it is important to focus efforts. Effective risk management must focus on mission essential functions that could cause the whole business to fail if they are not performed. Part of this process involves identifying critical systems and assets that support these functions. A mission essential function (MEF) is one that cannot be deferred. This means that the organization must be able to perform the function as close to continually as possible, and if there is any service disruption, the mission essential functions must be restored first.

Business impact analysis (BIA) is the process of assessing what losses might occur for a range of threat scenarios. For instance, if a denial of service (DoS) attack suspends an e-commerce portal for five hours, the business impact analysis will be able to quantify the losses from orders not made and customers moving permanently to other suppliers based on historic data. The likelihood of a DoS attack can be assessed on an annualized basis to determine annualized impact, in terms of costs. You then have the information required to assess whether a security control, such as load balancing or managed attack mitigation, is worth the investment.

Where BIA identifies risks, business continuity planning (BCP) identifies controls and processes that enable an organization to maintain critical workflows in the face of some adverse event.

VULNERABILITY AND EXPLOIT TYPES

Vulnerabilities can exist because of misconfigurations or poor practice, but many people understand the term to mean faults in software specifically. A software vulnerability is a design flaw that can cause the application security system to be circumvented or that will cause the application to crash. The most serious vulnerabilities allow the attacker to execute arbitrary code on the system, which could allow the installation of malware or allow the threat actor to disable or weaken a secure configuration. Typically, applications such as web servers, web browsers, web browser plug-ins, email clients, and databases are targeted.

An exploit is the specific code or method of using a vulnerability to gain control of a system or damage it in some way. Typically, software vulnerabilities can be exploited only in quite specific circumstances, but because of the complexity of modern software and the speed with which new versions must be released to market, almost no software is free from vulnerabilities.

Zero-Day Vulnerabilities and Exploits

Most software vulnerabilities are discovered by software and security researchers, who notify the vendor to give them time to patch the vulnerability before releasing details to the wider public. A vulnerability that is exploited before the developer knows about it or can release a patch is called a zero-day. These can be extremely destructive, as it can take the vendor a lot of time to develop a patch, leaving systems vulnerable for days, weeks, or even years.

The term zero-day is usually applied to the vulnerability itself but can also refer to an attack or malware that exploits it.

Unpatched and Legacy Systems

While an exploit for a zero-day vulnerability can be extremely destructive, they are relatively rare events. A greater threat is the large number of unpatched or legacy systems in use. An unpatched system is one that its owner has not updated with OS and application patches; a legacy system is one where the software vendor no longer provides support or fixes for problems.

This issue does not just affect PCs. Network appliances can also be vulnerable to exploits. The risks to embedded systems have become more obvious over the last few years, and the risks posed by unpatched mobile devices and the Internet of Things is likely to grow.

Vulnerability Assessment

A vulnerability assessment is an evaluation of a system's security and ability to meet compliance requirements based on the configuration state of the system. Essentially, the vulnerability assessment determines if the current configuration matches the ideal configuration (the baseline). Vulnerability assessments might involve manual inspection of security controls but are more often accomplished through automated vulnerability scanners.

Common Vulnerabilities and Exposures

Common Vulnerabilities and Exposures (CVE) is a dictionary of vulnerabilities in published operating systems and applications software ( cve.mitre.org ). Automated vulnerability scanning software makes use of this dictionary to develop tests to discover vulnerabilities on live systems. There are several elements that make up a vulnerability's entry in the CVE:

●	An identifier in the format: CVE-YYYY-####, where YYYY is the year the vulnerability was discovered, and #### is at least four digits that indicate the order in which the vulnerability was discovered.

●	A brief description of the vulnerability.

●	A reference list of URLs that supply more information on the vulnerability.

●	The date the vulnerability entry was created.

Example of a CVE.

THREAT TYPES AND ASSESSMENT

Exploits for vulnerabilities are either developed by threat actors or exposed by unintentional weaknesses in procedures. Threat assessment is the process of identifying threat sources and profiling the types and capabilities of threat actors.

External versus Internal Threats

An external threat actor or agent is one that has no account or authorized access to the target system. A malicious external threat must infiltrate the security system using malware and/or social engineering. Note that an external actor may perpetrate an attack remotely or on-premises (by breaking into the company's headquarters, for instance). It is the threat actor that is defined as external, rather than the attack method.

Conversely, an internal (or insider) threat actor is one that has been granted permissions on the system. This typically means an employee, but insider threat can also arise from contractors and business partners.

Threat Research

Threat research is a counterintelligence gathering effort in which security companies and researchers attempt to discover the tactics, techniques, and procedures (TTPs) of threat actors.

The outputs from the primary research undertaken by security solutions providers and academics can take three main forms:

●	Behavioral threat research -narrative commentary describing examples of attacks and TTPs gathered through primary research sources.

●	Reputational threat intelligence-lists of IP addresses and domains associated with malicious behavior, plus signatures of known file-based malware.

●	Threat data-computer data that can correlate events observed on a customer's own networks and logs with known TTP and threat actor indicators.

SECURITY INFORMATION AND EVENT MANAGEMENT

Security Information and Event Management (SIEM) is a security control designed to integrate vulnerability and threat assessment efforts through automated collection, aggregation, and analysis of log data. The core function of a SIEM tool is to aggregate logs from multiple sources. In addition to logs from Windows and Linux-based hosts, this could include switches, routers, firewalls, intrusion detection sensors, vulnerability scanners, malware scanners, and databases.

The second critical function of SIEM (and the principal factor distinguishing it from basic log management) is that of correlation. This means that the SIEM software can link individual events or data points (observables) into a meaningful indicator of risk, or indicator of compromise (IOC). Correlation can then be used to drive an alerting system. Finally, SIEM can provide a long-term retention function and be used to demonstrate regulatory compliance.

OSSIM SIEM dashboard. Configurable dashboards provide the high-level status view of network security metrics. (Screenshot used with permission from AT-and-T Cybersecurity.)

PENETRATION TESTING

Where vulnerability testing uses mostly automated scanning tools and is a largely passive, or non-intrusive assessment activity, penetration testing aims to model how exposed the organization is to vulnerabilities that could be exploited by threat actors.

A penetration test-often shortened to pen test-uses authorized hacking techniques to discover exploitable weaknesses in the target's security systems. Pen testing is also referred to as ethical hacking.

The key difference from passive vulnerability scanning is that an attempt is made to actively test security controls and exploit any vulnerabilities discovered. Pen testing is an intrusive assessment technique. For example, a vulnerability scan may reveal that an SQL Server has not been patched to safeguard against a known exploit. A penetration test would attempt to use the exploit to perform code injection and compromise the server. This provides active testing of security controls. Even though the potential for the exploit exists, in practice the permissions on the server might prevent an attacker from using it. This would not be identified by a vulnerability scan but should be proven or not proven to be the case by penetration testing.

PRIVILEGED ACCESS MANAGEMENT

A privileged account is one that can make significant configuration changes to a host, such as installing software or disabling a firewall or other security system. Privileged accounts also have rights to log on network appliances and application servers.

Privileged access management (PAM) refers to policies, procedures, and technical controls to prevent the malicious abuse of privileged accounts by internal threat actors and to mitigate risks from weak configuration control over privileges. These controls identify and document privileged accounts, giving visibility into their use, and manage the credentials used to access them.

Some other general principles of PAM include least privilege, role-based access, and zero trust:

●	Least privilege means that a user is granted sufficient rights to perform his or her job and no more. This mitigates risk if the account should be compromised and fall under the control of a threat actor. Authorization creep refers to a situation where a user acquires more and more rights, either directly or by being added to security groups and roles. Least privilege should be ensured by closely analyzing business workflows to assess what privileges are required and by performing regular account audits.

●	Role-based access means that a set of organizational roles are defined, and subjects allocated to those roles. Under this system, the right to modify roles is reserved to a system owner. Therefore, the system is nondiscretionary, as each subject account has no right to modify the ACL of a resource, even though they may be able to change the resource in other ways. Users are said to gain rights implicitly (through being assigned to a role) rather than explicitly (being assigned the right directly).

●	Zero trust is based on the idea that perimeter security is unlikely to be completely robust. On a modern network, there are just too many opportunities for traffic to escape monitoring/filtering by perimeter devices. Zero trust uses systems such as continuous authentication and conditional access to mitigate privilege escalation and account compromise by threat actors. Another zero-trust technique is to apply microsegmentation. Microsegmentation is a security process that is capable of applying policies to a single node, as though it was in a zone of its own.

VENDOR ASSESSMENT

High-profile breaches have led to a greater appreciation of the importance of the supply chain in vulnerability management. A product, or even a service, may have components created and maintained by a long chain of different companies. Each company in the chain depends on its suppliers or vendors performing due diligence on their vendors. A weak link in the chain could cause impacts on service availability and performance, or in the worst cases lead to data breaches.

Vendor management is a process for selecting supplier companies and evaluating the risks inherent in relying on a third-party product or service. When it comes to data and cybersecurity, you must understand that risks cannot be wholly transferred to the vendor. If a data storage vendor suffers a data breach, you may be able to claim costs from them, but your company will still be held liable in terms of legal penalties and damage to reputation. If your webstore suffers frequent outages because of failures at a hosting provider, it is your company's reputation that will suffer and your company that will lose orders because customers look elsewhere.

A vendor may supply documentation and certification to prove that it has implemented a security policy robustly. You might be able to see evidence of security capabilities, such as a history of effective vulnerability management and product support. Larger companies will usually ask vendors to complete a detailed audit process to ensure that they meet the required standards.

Topic 13B: Explain Authentication Methods

AUTHENTICATION METHODS AND ACCESS CONTROLS

An access control system is the set of technical security controls that govern how subjects are permitted to interact with objects. Subjects in this sense are users, devices, or software processes, or anything else that can request and be granted access to a resource. Objects are the resources; these could be networks, servers, databases, files, and so on.

In computer security, the basis of access control is usually an access control list (ACL). This is a list of subjects and the rights or permissions they have been granted on the object.

An identity and access management (IAM) system to mediate use of objects by subjects is usually described in terms of four main processes:

●	Identification -Creating an account or ID that identifies the user, device, or process on the network.

●	Authentication-Proving that a subject is who or what it claims to be when it attempts to access the resource.

●	Authorization-Determining what rights subjects should have on each resource and enforcing those rights.

●	Accounting-Tracking authorized usage of a resource or use of rights by a subject and alerting when unauthorized use is detected or attempted.

MULTIFACTOR AND TWO-FACTOR AUTHENTICATION

An account defines a subject on the computer or network system. Assuming that an account has been created securely (the identity of the account holder has been verified), authentication verifies that only the account holder is able to use the account, and that the system may be used only by account holders. Authentication is performed when the account holder submits credentials to the system to request access. These are compared to the credentials stored on the system. If they match, the account is authenticated.

The type of data used to create a credential is called an authentication factor. Authentication factors fall into the following categories:

●	Knowledge factor-something you know (such as a password).

●	Ownership factor-something you have (such as a smart card).

●	Human or biometric factor-something you are (such as a fingerprint).

●	Behavioral factor-something you do (such as making a signature).

●	Location factor-somewhere you are (such as using a mobile device with location services).

An authentication technology or mechanism is considered strong if it combines the use of more than one authentication data type (multifactor). Single-factor authentication systems can quite easily be compromised: a password could be written down or shared, or compromised by a social engineering attack, a smart card could be lost or stolen, and a biometric system could be subject to high error rates.

Two-factor authentication combines something like a smart card or biometric mechanism with a knowledge factor, such as a password or personal identity number (PIN). Three-factor authentication combines three of the possible technologies. An example of this would be a smart card with an integrated fingerprint reader. This means that to authenticate, the user must possess the card, the user's fingerprint must match the template stored on the card, and the user must input a PIN.

Multifactor authentication requires a combination of different technologies. For example, requiring a PIN along with date of birth may be stronger than entering a PIN alone, but it is not multifactor.

LOCAL AUTHENTICATION AND SINGLE SIGN-ON

One of the most important features of an operating system is the authentication provider. The local authentication provider is the software architecture and code that underpins the mechanism by which the user is authenticated before starting a shell. This is usually described as a login (Linux) or a logon or sign-in (Microsoft). Knowledge-based authentication, using a password or PIN, is the default authentication provider for most operating systems.

Knowledge-based authentication relies on cryptographic hashes. A cryptographic hash is a function that converts any string to a unique, fixed-length code. The function should ensure that the code cannot be converted back into the plaintext string.

Password credentials are stored as cryptographic hashes (such as the Hash.Target value shown in the screenshot) that cannot normally be converted back to plaintext strings. The hashcat utility attempts to recover passwords by matching hashes through dictionary or brute force methods.

A password is not usually transmitted or stored in a credential database as a plaintext because of the risk of compromise. Instead, the password is stored as a cryptographic hash. When a user enters a password to log in, an authenticator converts what is typed into a hash and transmits that to an authority. The authority compares the submitted hash to the one in the database and authenticates the subject only if they match.



Windows Authentication

Windows authentication involves a complex architecture of components (docs.microsoft.com/en-us/windows-server/security/windows-authentication/credentials-processes-in-windows-authentication), but the following three scenarios are typical:

●	Windows local sign-in-the Local Security Authority (LSA) compares the submitted credential to a hash stored in the Security Accounts Manager (SAM) database, which is part of the registry. This is also referred to as interactive logon.

●	Windows network sign-in-the LSA can pass the credentials for authentication to a network service. The preferred system for network authentication is based on Kerberos, but legacy network applications might use NT LAN Manager (NTLM) authentication.

●	Remote sign-in-if the user's device is not connected to the local network, authentication can take place over some type of virtual private network (VPN) or web portal.

Linux Authentication

In Linux, local user account names are stored in /etc/passwd. When a user logs in to a local interactive shell, the password is checked against a hash stored in /etc/shadow. Interactive login over a network is typically accomplished using Secure Shell (SSH). With SSH, the user can be authenticated using cryptographic keys instead of a password.

A pluggable authentication module (PAM) is a package for enabling different authentication providers, such as smart card login (tecmint.com/configure-pam-in-centos-ubuntu-linux). The PAM framework can also be used to implement authentication to network servers.


Single Sign-On

A single sign-on (SSO) system allows the user to authenticate once to a local device and be authorized to access compatible application servers without having to enter credentials again. In Windows, SSO is provided by the Kerberos framework.

KERBEROS

Kerberos provides SSO authentication to Active Directory®, as well as compatibility with other, non-Windows operating systems. Kerberos was named after the three-headed guard dog of Hades (Cerberus) because it consists of three parts. Clients request services from a server, which both rely on an intermediary-a Key Distribution Center (KDC)-to vouch for their identity.

There are two services that make up a KDC: the Authentication Service and the Ticket Granting Service.

The Authentication Service is responsible for authenticating user logon requests. More generally, users and services can be authenticated; these are collectively referred to as principals. For example, when you sit at a Windows domain workstation and log on to the domain (Kerberos documentation refers to realms rather than domains, which is Microsoft's terminology), the first step of logon is to authenticate with a KDC server (implemented as a domain controller).

Kerberos Authentication Service. (Images © 123RF.com.)

When authenticated, the KDC server presents the user with a Ticket Granting Ticket. To access resources within the domain, the client requests a Service Ticket (a token that grants access to a target application server) by supplying the Ticket Granting Ticket to the Ticket Granting Service (TGS).

Kerberos Ticket Granting Service. (Images © 123RF.com.)

DIGITAL CERTIFICATES AND PKI

A protocol such as Kerberos can also be used with smart cards. A smart card is programmed with an encryption key pair and a digital certificate, issued by the authenticating domain. Digital certificates are also used to authenticate server machines when using Transport Layer Security (TLS). A certificate can be installed on a web server or email server to validate its identity and establish a secure transmission channel.

Digital certificates depend on the concept of public key cryptography. Public key cryptography, also referred to as asymmetric encryption, solves the problem of distributing encryption keys when you want to communicate securely with others, authenticate a message that you send to others, or authenticate yourself to an access control system. With asymmetric encryption, you generate a key pair. The private key in the pair remains a secret that only you know. The public key can be transmitted to other subjects. The private key cannot be derived from the public key. The key pair can be used in the following ways:

●	When you want others to send you confidential messages, you give them your public key to use to encrypt the message. The message can then only be decrypted by your private key, which you keep known only to yourself. Due to the way asymmetric encryption works, the public key cannot be used to decrypt a message, even though it was used to encrypt it in the first place.

As encryption using a public key is relatively slow; rather than encrypting the whole message using a public key, more typically, the public key is used to encrypt a symmetric encryption key for use in a single session and exchange it securely. The symmetric session key is then used to encrypt the actual message. A symmetric key can perform both encryption and decryption.

●	When you want to authenticate yourself to others, you create a signature and sign it by encrypting the signature with your private key. You give others your public key to use to decrypt the signature. As only you know the private key, everyone can be assured that only you could have created the signature.

The basic problem with public key cryptography lies in proving the identity of the owner of a public key. The system is vulnerable to an on-path attack where a threat actor substitutes your public key for their own. Public key infrastructure (PKI) aims to prove that the owners of public keys are who they say they are. Under PKI, anyone issuing public keys should obtain a digital certificate. The validity of the certificate is guaranteed by a certificate authority (CA). A digital certificate is essentially a wrapper for a subject's (or end entity's) public key. As well as the public key, it contains information about the subject and the certificate's issuer or guarantor. The certificate is digitally signed to prove that it was issued to the subject by a particular CA.

EXTENSIBLE AUTHENTICATION PROTOCOL AND IEEE 802.1X

Smart-card authentication is used for Kerberos authentication where the computer is attached to the local network and the user is logging on to Windows. This type of multifactor authentication may also be required in other contexts:

When the user is accessing a wireless network and needs to authenticate with the network database.

When a device is connecting to a network via a switch, network policies require the user to be authenticated before the device is allowed to communicate.

When the user is connecting to the network over a public network via a virtual private network (VPN).

In these scenarios, the Extensible Authentication Protocol (EAP) provides a framework for deploying multiple types of authentication protocols and technologies. EAP allows lots of different authentication methods, but many of them use a digital certificate on the server and/or client machines. These certificates allow the machines to establish a trust relationship and create a secure tunnel to transmit the user credential or to perform smart card authentication without a user password.

Where EAP implements a particular authentication factor and mechanism, the IEEE 802.1X Port-based Network Access Control (NAC) protocol provides the means of using an EAP method when a device connects to an Ethernet switch port, wireless access point, or VPN gateway. 802.1X uses authentication, authorization, and accounting (AAA) architecture. AAA uses the following components:

Supplicant-the device requesting access, such as a user's PC or laptop.

Network access server (NAS) or network access point (NAP)-edge network appliances, such as switches, access points, and VPN gateways. These are also referred to as AAA clients or authenticators.

AAA server-the authentication server, positioned within the local network. There are two main types of AAA server: RADIUS and TACACS+.

With AAA, the NAS devices do not have to store any authentication credentials. They forward this data between the AAA server and the supplicant.






RADIUS authentication with EAP overview. (Images © 123RF.com.)

Digital certificate details. (Screenshot used with permission from Microsoft.)

RADIUS AND TACACS+

Remote Authentication Dial-in User Service (RADIUS) is very widely used for client device access over switches, wireless networks, and VPNs. There are several RADIUS server and client products. Microsoft has the Network Policy Server (NPS) for Windows platforms, and there are open-source implementations for UNIX and Linux, such as FreeRADIUS, as well as third-party commercial products, such as Cisco's Secure Access Control Server, OSC Radiator, and Juniper Networks Steel-Belted RADIUS.

RADIUS typically uses UDP ports 1812 and 1813. Each RADIUS client must be configured with the IP address of the RADIUS server plus the same shared secret.

Configuring an OPNsense security appliance as a RADIUS client. The OPNsense appliance is working as a virtual private network (VPN) access server. It uses the RADIUS server at 10.1.16.1 to authenticate VPN users. The client must be configured with the same shared secret as the server. (Screenshot used with permission from OPNsense.)

Terminal Access Controller Access Control System (TACACS+) is a similar protocol to RADIUS but designed to be more flexible and reliable. TACACS+ was developed by Cisco but is also supported on many of the other third-party and open-source RADIUS server implementations. Where RADIUS is often used for network access control over end user devices, TACACS+ is often used in authenticating administrative access to routers and switches. It uses TCP over port 49 and the reliable delivery offered by TCP makes it easier to detect when a server is down.

Also, authentication, authorization, and accounting functions are discrete. Many device management tasks require reauthentication (similar to having to reenter a password for sudo or UAC) and per-command authorizations and privileges for users, groups, and roles. TACACS+ supports this workflow better than RADIUS.

LIGHTWEIGHT DIRECTORY ACCESS PROTOCOL

Directory services are the principal means of providing privilege management and authorization on an enterprise network.

When an authenticated user logs on to the network, the server security service generates an access key for the user. This contains the username and group memberships of the authenticated user. Whenever the user attempts to access a resource, his or her access key is provided as identification. The server's security service matches username and group memberships from the access key with entries in the access list, and from this, it calculates the user's access privileges.

All this information is stored in a directory. A directory is like a database, where an object is like a record, and things that you know about the object (attributes) are like fields. For products from different vendors to be interoperable, most directories are based on the same standard. The main directory standard is the X.500 series of standards. As X.500 is complex, most directory services are implementations of the Lightweight Directory Access Protocol (LDAP). LDAP is not a directory standard, but a protocol used to query and update an X.500-like directory. LDAP is widely supported in current directory products (Windows Active Directory®, NetIQ eDirectory, or the open source OpenLDAP). LDAP messaging uses TCP and UDP port 389 by default.

In an X.500, each object has a unique identifier called a distinguished name. A distinguished name is made up of attribute=value pairs, separated by commas. The most specific attribute is listed first, and successive attributes become progressively broader. This most specific attribute is also referred to as the relative distinguished name, as it uniquely identifies the object within the context of successive (parent) attribute values.

Browsing objects in an Active Directory LDAP schema. (Screenshot used with permission from Microsoft.)

The types of attributes, what information they contain, and the way object types are defined through attributes (some of which may be required and some optional) is described by the directory schema. For example, the distinguished name of a web server operated by Widget in London might be:

CN=WIDGETWEB, OU=Marketing, O=Widget, L=London, ST=London, C=UK, DC=widget, DC=example

LDAP SECURE

Like many TCP/IP protocols, LDAP provides no security, and all transmissions are in plaintext, making it vulnerable to sniffing and spoofing attacks. Also, a server that does not require clients to authenticate is vulnerable to overloading by denial of service attacks. Authentication, referred to as binding to the server, can be implemented in the following ways:

●	No authentication-Anonymous access is granted to the directory.

●	Simple bind-the client must supply its distinguished name (DN) and password, but these are passed as plaintext.

●	Simple Authentication and Security Layer (SASL)-the client and server negotiate the use of a supported authentication mechanism, such as Kerberos. The STARTTLS command can be used to require encryption (sealing) and message integrity (signing). This is the preferred mechanism for Microsoft's Active Directory (AD) implementation of LDAP.

●	LDAP Secure (LDAPS)-the server is installed with a digital certificate, which it uses to set up a secure tunnel for the user credential exchange. LDAPS uses port 636.

If secure access is required, anonymous and simple authentication access methods should be disabled on the server.

Generally, two levels of access will need to be granted on the directory: read-only access (query) and read/write access (update). This is implemented using an access control policy, but the precise mechanism is vendor-specific and not specified by the LDAP standards documentation.

Unless it is hosting a public service, the LDAP directory server should also only be accessible from the private network. This means that LDAP ports (389 over TCP and UDP) should be blocked by a firewall from access over the public interface.











Lesson 14: Supporting and Troubleshooting Secure Networks

Topic 14A: Compare and Contrast Security Appliances

NETWORK SEGMENTATION ENFORCEMENT

Effective placement of security appliances depends on segmenting the network into clearly defined areas. At layers two and three, network segmentation enforcement is applied using a combination of virtual LANs and subnets. Each segment is a separate broadcast domain. Any traffic between segments must be routed. In security terms, the main unit of a logically segmented network is a zone. A zone is an area of the network where the security configuration is the same for all hosts within it. Network traffic between zones should be strictly controlled using a security device-typically a firewall.

These zones would typically be configured to protect the integrity and confidentiality of different asset groups within the organization. For example, servers storing financial records can be their own VLAN, and marketing servers could be another VLAN. If something like a remote access Trojan were introduced in one VLAN, it should not be able to spread to other VLANs without also being able to pass through the firewall protecting each zone.

One important distinction between different security zones is whether a host is Internet-facing. An Internet-facing host accepts inbound connections from the Internet. Internet-facing hosts are placed in the perimeter network zone. The basic principle of a perimeter network zone is that traffic cannot pass through it directly. A perimeter network enables external clients to access data on private systems, such as web servers, without compromising the security of the internal network.

If communication is required between hosts on either side of the perimeter network, a host within it can be configured to act as a proxy. For example, if a host on the local network requests a connection with a web server on the Internet, a proxy in the network perimeter takes the request and checks it. If the request is valid, it retransmits it to the destination. External hosts have no idea about what (if anything) is behind the perimeter.

Servers that provide public access services should be placed in a perimeter network. These would typically include web servers, mail and other communications servers, proxy servers, and remote access servers. The hosts in the perimeter are not fully trusted by the internal network because of the possibility that they could be compromised from the Internet. They are referred to as bastion hosts.

SCREENED SUBNETS

To configure a perimeter network, two different security configurations must be enabled: one on the external interface and one on the internal interface.

A screened subnet uses two firewalls placed on either side of the perimeter network zone. The edge firewall restricts traffic on the external/public interface and allows permitted traffic to the hosts in the perimeter zone subnet. The edge firewall can be referred to as the screening firewall or router. The internal firewall filters communications between hosts in the perimeter and hosts on the LAN. This firewall is often described as the choke firewall. A choke point is a purposefully narrow gateway that facilitates better access control and easier monitoring.

Screened subnet. (Images © 123RF.com.)

The screened subnet topology was formerly referred to as a demilitarized zone (DMZ). The DMZ terminology is now deprecated.

A perimeter network can also be established using one router/firewall appliance with three network interfaces, referred to as triple homed. One interface is the public one, another is the perimeter subnet, and the third connects to the LAN. Routing and filtering rules determine what forwarding is allowed between these interfaces. This can achieve the same sort of configuration as a screened subnet.

Triple-homed firewall. (Images © 123RF.com.)

FIREWALL USES AND TYPES

The basic function of a firewall is traffic filtering. The firewall processes traffic according to rules; traffic that does not conform to a rule that allows it access is blocked.

There are many types of firewalls and many ways of implementing a firewall. One distinction can be made between firewalls that protect a whole network (one that is placed inline in the network and inspects all traffic that passes through) and firewalls that protect a single host only (one that is installed on the host and inspects only that traffic addressed to that host). A further distinction can be made about what parts of a packet a particular firewall technology can inspect and operate on.

Packet Filtering Firewalls

Packet filtering describes the earliest type of firewall. All firewalls can still perform this basic function. A packet filtering firewall is configured by specifying rules in a network access control list (ACL). Each rule defines a specific type of data packet and the appropriate action to take when a packet matches the rule. An action can be either to deny (block or drop the packet, and optionally log an event) or to accept (let the packet pass through the firewall). A packet filtering firewall works at Layer 3 of the OSI model to inspect the headers of IP packets. This means that rules can be based on the information found in those headers:

●	IP filtering-Accepting or denying traffic based on its source and/or destination IP address.

●	Protocol ID/type (TCP, UDP, ICMP, routing protocols, and so on).

●	Port filtering/security-Accepting or denying a packet based on source and destination port numbers (TCP or UDP application type).

Port numbers are contained in TCP or UDP headers (layer 4), rather than the IP datagram header, but packet filtering firewalls are still almost always described as working at layer 3. They can inspect only port numbers and not any other layer 4 header information.

ACLs might be designed to control only inbound traffic or both inbound and outbound traffic. This is also often referred to as "ingress" and "egress" traffic or filtering. Controlling outbound traffic is useful because it can block applications that have not been authorized to run on the network and defeat malware, such as backdoors. Ingress and egress traffic is filtered using separate ACLs.

A packet filtering firewall is stateless. This means that it does not preserve information about the connection between two hosts. Each packet is analyzed independently with no record of previously processed packets. This type of filtering requires the least processing effort, but it can be vulnerable to attacks that are spread over a sequence of packets. A stateless firewall can also introduce problems in traffic flow, especially when some sort of load balancing is being used or when clients or servers need to make use of dynamically assigned ports.

Stateful Inspection Firewalls

A circuit-level stateful inspection firewall addresses these problems by maintaining stateful information about the session established between two hosts (including malicious attempts to start a bogus session). Information about each session is stored in a dynamically updated state table. A stateful firewall operates at Layer 5 (Session) of the OSI model. When a packet arrives, the firewall checks it to confirm whether it belongs to an existing connection. If it does not, it applies the ordinary packet filtering rules to determine whether to allow it. Once the connection has been allowed, the firewall allows traffic to pass unmonitored, in order to conserve processing effort.

State table in the OPNsense firewall appliance. (Screenshot used with permission from OPNsense.)

FIREWALL SELECTION AND PLACEMENT

You should consider how a firewall is implemented (as hardware or software, for instance) to cover a given placement or use on the network. Some types of firewalls are better suited for placement at network or segment borders; others are designed to protect individual hosts. The selection of a network firewall model will largely depend on the volume of traffic it has to process. A single firewall can represent a network bottleneck if it is not able to handle the required traffic volume.

An appliance firewall is a stand-alone hardware firewall that performs only the function of a firewall. The functions of the firewall are implemented on the appliance firmware. This is also a type of network-based firewall and monitors all traffic passing into and out of a network segment. This type of appliance could be implemented with routed interfaces or as a Layer 2/virtual wire "transparent" firewall.

Cisco ASA (Adaptive Security Appliance) ASDM (Adaptive Security Device Manager) interface. (Image © and Courtesy of Cisco Systems, Inc. Unauthorized use not permitted.)

A router firewall is similar, except that the functionality is built into the router firmware. Most SOHO Internet router/modems have this type of firewall functionality, though they are typically limited to supporting a single subnet within the home network. An enterprise-class router firewall would be able to support far more sessions than a SOHO one. Additionally, some Layer 3 switches can perform packet filtering.

PROXY SERVERS

The basic function of a network firewall is to inspect packets and determine whether to block them or allow them to pass. By contrast, a proxy server forwards requests and responses on behalf of its clients. Rather than inspecting traffic as it passes through, the proxy deconstructs each packet, performs analysis, then rebuilds the packet and forwards it on, providing it conforms to the rules. This type of device is placed in a perimeter network.

Forward Proxies

A forwarding proxy server provides for protocol-specific outbound traffic. For example, you might deploy a web proxy that enables client hosts to connect to websites and secure websites on the Internet. A proxy server must understand the application it is servicing. A web proxy must be able to parse and modify HTTP and HTTPS commands (and potentially HTML, too). Some proxy servers are application-specific; others are multipurpose. A multipurpose proxy is one configured with filters for multiple protocol types, such as HTTP, FTP, and SMTP.

The main benefit of a proxy server is that clients connect to a specified point within the perimeter network for web access. This provides for a degree of traffic management and security. In addition, most web proxy servers provide caching engines, whereby frequently requested web pages are retained on the proxy, negating the need to refetch those pages for subsequent requests.

Proxy servers can generally be classed as non-transparent or transparent. A nontransparent server means that the client must be configured with the proxy server address and port number to use it. The port on which the proxy server accepts client connections is often configured as port 8080. A transparent (or "forced" or "intercepting") proxy intercepts client traffic without the client having to be reconfigured. A transparent proxy must be implemented on a switch or router or other inline network appliance.

Configuring transparent proxy settings for the proxy server running on the OPNsense security appliance. (Screenshot used with permission from OPNsense.)

Reverse Proxies

A reverse proxy server provides for protocol-specific inbound traffic. For security purposes, it is inadvisable to place application servers, such as messaging and VoIP servers, in the perimeter network, where they are directly exposed to the Internet. Instead, you can deploy a reverse proxy and configure it to listen for client requests from a public network (the Internet) and create the appropriate request to the internal server on the corporate network.

Reverse proxies can publish applications from the corporate network to the Internet in this way. In addition, some reverse proxy servers can handle the encryption/decryption and authentication issues that arise when remote users attempt to connect to corporate servers, reducing the overhead on those servers. Typical applications for reverse proxy servers include publishing a web server, publishing messaging or conferencing applications, and enabling POP/IMAP mail retrieval.

NETWORK ADDRESS TRANSLATION

Network Address Translation (NAT) was devised as a way of freeing up scarce IP addresses for hosts needing Internet access. NAT is a service translating between a private (or local) addressing scheme used by hosts on the LAN and a public (or global) addressing scheme used by an Internet-facing device. NAT is configured on a border device, such as a router, proxy server, or firewall. NAT is not a security mechanism; security is provided by the router/firewall's ACL.

In a basic NAT static configuration, a simple 1:1 mapping is made between the private (inside local) network address and the public (inside global) address. If the destination network is using NAT, it is described as having outside global and outside local addressing schemes.

Basic NAT is useful in scenarios where an inbound connection to a host must be supported. For example, you might position a web server behind a firewall running NAT. The firewall performs 1:1 address translation on the web server's IP address. This means that external hosts do not know the true IP address of the web server, but they can communicate with it successfully.

Network Address Translation (NAT). (Images © 123RF.com.)

A single static mapping is not very useful in most scenarios. Under dynamic NAT, the NAT device exposes a pool of public IP addresses. To support inbound and outbound connections between the private network and the Internet, the NAT service builds a table of public to private address mappings. Each new session creates a new public-private address binding in the table. When the session is ended or times out, the binding is released for use by another host.

Defining NAT rules in Cisco Adaptive Security Appliance (ASA). (Screenshot used with permission from Cisco.)

PORT ADDRESS TRANSLATION

Basic NAT supports multiple simultaneous connections but is still limited by the number of available public IP addresses. Smaller companies may only be allocated a single or small block of addresses by their ISPs. In such cases, a means for multiple private IP addresses to be mapped onto a single public address would be useful. This function is provided by Port Address Translation (PAT). This can be referred to as Network Address Port Translation (NAPT) or NAT overloading or one-to-many NAT.

Port Address Translation (PAT). (Images ©123RF.com.)

PAT works by allocating each new connection an ephemeral TCP or UDP port. For example, say two hosts (10.0.0.101 and 10.0.0.102) initiate a web connection at the same time. The PAT service creates two new port mappings for these requests (10.0.0.101:61101 and 10.0.0.102:61102) in its state table. It then substitutes the private IP for the public IP and forwards the requests to the public Internet. It performs a reverse mapping on any traffic returned using those ports, inserting the original IP address and port number, and forwarding the packets to the internal hosts.

DEFENSE IN DEPTH

Firewalls, screened subnets, and proxy servers try to establish a secure barrier at the network edge. This is referred to as perimeter security. The proliferation of mobile devices with wireless or cellular data access and cloud services, plus the better recognition of insider threat and vulnerabilities to malware, has eroded confidence in a solely perimeter-based security model. Network security design must address the concept of defense in depth. This refers to placing security controls throughout the network, so that all access attempts are authenticated, authorized, and audited. Some examples of security controls that provide defense in depth additional to network segmentation and screened subnets include Network Access Control, honeypots, separation of duties, and intrusion detection.

Network Access Control

Network Access Control (NAC) is a system for authenticating endpoints at the point they connect to the network. NAC uses 802.1X port security mechanisms, EAP, and AAA model of supplicants, network access device AAA clients, and AAA servers. NAC enables devices to be authenticated when they connect to switch ports, wireless networks, or virtual private network (VPN) remote access servers.

Basic NAC solutions can authenticate a client on the basis of machine certificates and/or user passwords. More sophisticated solutions can enforce a health policy. A health policy means that the client must submit an attestation report. This secure report proves that the client is running an authorized OS and has up-to-date patches and security scanner configuration.

Honeypots

A honeypot is a computer system set up to attract attackers, with the intention of analyzing attack strategies and tools, to provide early warning of attack attempts, or possibly as a decoy to divert attention from actual computer systems. Another use is to detect internal fraud, snooping, and malpractice. A honeynet is an entire decoy network. This may be set up as an actual network or simulated using an emulator.

On a production network, a honeypot is more likely to be located in a protected but untrusted area between the Internet and the private network or on a closely monitored and filtered segment within the private network itself. This provides early warning and evidence of whether a threat actor has been able to penetrate to a given security zone.


Separation of Duties

Separation of duties is a means of establishing checks and balances against the possibility that critical systems or procedures can be compromised by insider threats. Duties and responsibilities should be divided among individuals to prevent ethical conflicts or abuse of powers.

INTRUSION DETECTION AND PREVENTION SYSTEMS

An intrusion detection system (IDS) performs real-time analysis of either network traffic or system and application logs. Where a firewall applies rules from an ACL, an IDS is configured with signature patterns. Each pattern represents a known type of malicious activity. If a pattern is matched in a traffic stream, the IDS raises an alert. Like antivirus software, the IDS must be kept up to date with the latest signature patterns. An IDS is often also configured with automated threat data, such as lists of IP addresses and domains that are associated with threat actors.

Like a packet analyzer, an IDS must be configured with a sniffer to read frames from a mirrored port or TAP. Placement of the sniffer must be carefully considered to meet security goals. Typically, an IDS is positioned behind a firewall. The aim is to detect suspicious traffic that the firewall has not blocked, providing defense in depth. This type of passive sensor does not slow down traffic and is undetectable by the attacker (it does not have an IP address on the monitored network segment).

Configuration file for the Snort IDS.

Compared to the passive logging/alerting functionality of an IDS, an intrusion prevention system (IPS) can provide an active response to any network threats that it matches. One typical preventive measure is to end the session by sending a TCP reset packet to the attacking host. Another option is for the sensor to apply a temporary filter on the firewall to block the attacker's IP address (shunning). Other advanced measures include throttling bandwidth to attacking hosts, applying complex firewall filters, and even modifying suspect packets to render them harmless. Finally, the appliance may be able to run a script or third-party program to perform some other action not supported by the IPS software itself.

IPS functionality is now very commonly built into firewall appliances and proxy servers. An IPS-enable firewall is inline with the network, meaning that all traffic passes through it (also making them a single point-of-failure if there is no fault tolerance mechanism). This obviously means that they need to be able to cope with high bandwidths and process each packet very quickly to avoid slowing down the network.

Network IDS/IPS can be combined with host-based IDS/IPS. These run as agents on end systems to monitor application processes, data files, and log files for suspicious activity. Advanced IDS/IPS suites analyze information from multiple sensors to identify suspicious traffic flows and host activity.

Topic 14B: Troubleshoot Service and Security Issues

DHCP ISSUES

The Dynamic Host Configuration Protocol (DHCP) provides IP addressing autoconfiguration to hosts without static IP parameters. If a Windows client fails to obtain a DHCP lease, it defaults to using an address in the Automatic Private IP Addressing (APIPA) range of 169.254.0.0/16. It will be limited to communication with other APIPA hosts on the same network segment (broadcast domain). Linux hosts will use the 169.254.0.0/16 range if they have Zeroconf support, leave the IP address set to 0.0.0.0, or disable IPv4 on the interface.

APIPA is Microsoft terminology. Standards documentation refers to this address range as IPv4 Link-local (IPV4LL).




DHCP Server and Scope Exhaustion Issues

Possible reasons for a client to fail to obtain a lease include:

●	The DHCP server is offline. If your DHCP servers go offline, users will continue to connect to the network for a period and thereafter start to lose contact with network services and servers as they come to try to renew a lease.

●	No more addresses available (DHCP scope exhaustion). Create a new scope with enough addresses or reduce the lease period. Remember that IP Address Management (IPAM) software suites can be used to track address usage across a complex DHCP infrastructure.

●	The router between the client and DHCP server doesn't support BOOTP forwarding. Either install RFC 1542-compliant routers or add another type of DHCP relay agent to each subnet or VLAN.

If you reconfigure your DHCP servers and their scopes, the clients will gradually get reconfigured. You will need to ensure that you plan for the fact that not all clients' IP configurations will be updated when the server scopes are edited and could be left with an expired IP, default gateway, or DNS server address. You could do this by lowering the lease duration in advance of changes, forcing all clients to renew, or running parallel settings for a period.

Rogue DHCP Server Issues

Clients have no means of preferring a DHCP server. If two DHCP servers are running on the same subnet, clients could end up with an incorrect IP configuration because they have obtained a lease from a rogue server. A rogue DHCP server may be deployed accidentally (forgetting to disable a DHCP server in an access point or router, for instance) or may be used by a malicious attacker to subvert the network. An attacker would normally use a rogue server to change the default gateway and/or DNS resolver addresses for the subnet and route communications via his or her machine (an on-path attack).

NAME RESOLUTION ISSUES

When you perform a successful connectivity test by IP address, the next step may be to try pinging by name, thus testing name resolution.

Name Resolution Methods

To troubleshoot name resolution, you should establish exactly how the process works on that specific host. A host can use a variety of methods to resolve a name or FQDN to an IP address. In very general terms, these will be as follows:

1. `	`Check local cache. One complication here is that there are different types of cache and separate caches for individual applications, such as web browsers. On Windows, you can use ipconfig /displaydns and ipconfig /flushdns to monitor and clear the system cache.
1. `	`Check HOSTS. The HOSTS file is a static list of host name to IP address mappings. The default location under Windows is %SystemRoot%\system32\drivers\etc\, while under Linux it is usually placed in the /etc directory. In most cases, HOSTS should not contain any entries (other than the loopback address). Any static entries in HOSTS could be the cause of a name resolution issue. The file can also be used for troubleshooting.
1. `	`Query DNS. A host uses the name servers defined in its IP configuration to resolve queries.

Any text preceded by the # symbol in a HOSTS file is a comment and will not be processed.

While we are focusing on name resolution via DNS here, note that a host can use multiple methods, especially on Windows workgroup networks. Link Local Multicast Name Resolution (LLMNR) and multicastDNS (mDNS) are modified forms of DNS that allow clients to perform name resolution on a local link without needing a server.

DNS Configuration Issues

Linux and Windows systems usually rely on DNS server infrastructure for name resolution and service discovery. In the absence of DNS servers, network client machines will be unable to log on or connect to services or servers.

If your hosts are experiencing DNS issues, symptoms will include the inability to connect to a server by name, despite it being accessible by IP address. To verify a name resolution problem, edit the HOSTS file and place the correct name and IP address record in the file for the test host. When you ping, if that is successful, it suggests a name resolution problem.

If a single client is unable to resolve names, the issue is likely to lie with the client configuration.

●	The client has been configured either with no DNS server address or the wrong DNS server address. Reconfigure the DNS server address.

●	The client has the incorrect DNS suffix. Verify the DNS domain in which the client is supposed to be and verify the host's configuration matches.

Bear in mind that in both of these situations, DHCP might be configuring these settings incorrectly. Therefore, check the server options or scope options configuration on the DHCP server as well.

If multiple clients are affected, the issue is likely to lie with the server service (or the way a subnet accesses the server service). Check that the server configured as a DNS resolver is online and available (that you can ping the server from the client).

If some DNS queries work from the client and others don't, then the problem is more complex. Use the nslookup or dig utilities to check what records are returned by the resolver. If trying to connect to an Internet resource, compare these records to those returned by public resolvers (such as Google's servers at 8.8.8.8). Consider whether clients have cached a record that has been changed recently. Reconfiguration of DNS records should be planned and implemented carefully to avoid caching problems.

VLAN ASSIGNMENT ISSUES

When you partition a network into separate VLANs, as each VLAN is a discrete broadcast domain, you must ensure that services, such as DHCP and DNS, are properly available to all VLANs. Otherwise, users will complain that "the Internet is down," when it transpires that there is no local DNS server available to handle their name resolution requests.

If devices are not in the same VLAN and must communicate, ensure that routing has been configured to enable VLAN-to-VLAN communications. You may also need to configure services such as DHCP relay to allow hosts to contact a DHCP server. Also, if a device is placed in a designated VLAN, its IP configuration must be appropriate in terms of IP address, subnet mask, default gateway, and DNS servers.

Another issue is that a host has been placed in an incorrect VLAN. Make sure all devices are placed into the appropriate VLAN as per the configuration baseline. VLAN assignments can be configured manually, and the administrator may have made a mistake, so check the interface configuration for the switch port. VLAN assignments can also be configured automatically, using parameters such as the host MAC address or authentication credentials, and this process may have failed, or the database used to map the dynamic data to a VLAN ID might be misconfigured.

UNRESPONSIVE SERVICE AND NETWORK PERFORMANCE ISSUES

If you can rule out connectivity problems with a local client or subnet, the issue may be with an application server, rather than the client. Such unresponsive service issues will usually manifest with multiple clients being unable to connect. There can be any number of underlying causes, but consider some of the following:

●	The application or OS hosting the service has crashed (or there is a hardware or power problem).

●	The server hosting the service is overloaded (high CPU/memory/disk I/O utilization/disk space utilization). Try throttling client connections until the server resources can be upgraded.

●	There is congestion in the network, either at the client or server end (or both). Use ping or traceroute to check the latency experienced over the link and compare to a network performance baseline. Again, throttling connections or bandwidth may help to ease the congestion until higher bandwidth links can be provisioned.

●	A broadcast storm is causing loss of network bandwidth. Switching loops cause broadcast and unknown unicast frames to circulate the network perpetually, as each switch repeatedly floods each frame. A broadcast storm may quickly consume all link bandwidth and crash network appliances (check for excessive CPU utilization on switches and hosts). The Spanning Tree Protocol (STP) is supposed to prevent such loops, but this can fail if STP communications between switches do not work correctly, either because of a fault in cabling or a port/transceiver or because of a misconfiguration.

●	Network congestion may also be a sign that the service is being subject to a Denial of Service (DoS) attack. Look for unusual access patterns (for example, use GeoIP to graph source IP addresses by country and compare to baseline access patterns).

If users on a LAN cannot connect to an external service, such as a cloud application, you can use a site such as isitdownrightnow.com to test whether the issue is local to your network or a problem with the service provider site.

Be proactive in monitoring service availability so that you can resolve problems before they affect large numbers of clients.

MISCONFIGURED FIREWALL AND ACL ISSUES

One type of firewall, ACL, or content filter misconfiguration causes blocked services, ports, or addresses that are supposed to be allowed through. This will cause an application or protocol to fail to function correctly. For example, the firewall might be blocking TCP or UDP ports that are supposed to be open, or it might be allowing the ports but denying access to an IP network or host address that is supposed to be able to connect. Also consider that advanced firewalls are capable of applying additional filtering criteria, such as evaluating process/service executable names/locations or authorizations based on user accounts or group memberships.

A deny type of error will usually be easy to identify, as users will report incidents connected with the failure of the data traffic. With such incidents, firewall configuration will always be a likely cause, so will be high on the list to investigate. Diagnosis can be confirmed by trying to establish the connection from both inside and outside the firewall. If it connects from outside the firewall but not from inside, this will confirm the firewall to be the cause of the issue.

Another potential issue is where there are both network-based and host-based firewall settings to navigate in the communication path. There could be a host firewall running on the client, on the server, or on both. To diagnose an issue with a host firewall, attempt the connection with the host firewall disabled. If the connection attempt succeeds, then the network firewall ACL is allowing the packets, but the host firewall is configured to block them. If the connection attempt fails, investigate the network firewall ACL first. You can also inspect the firewall's log files to discover what rules have been applied to block traffic at a particular time.

The other possible outcome of a badly configured firewall is that packets may be allowed through that should be blocked. This is a more serious outcome, because the result is to open the system to security vulnerabilities. It is also not necessarily so easily detected, as it does not typically cause anything to stop functioning. As no incidents usually arise from this outcome (except in the case that a vulnerability is exploited), it is not a scenario that is subject to troubleshooting. Rather, it underlines the need for regular firewall audits and thorough change control processes to deal with firewall change requests.

UNTRUSTED CERTIFICATE ISSUES

If the digital certificate presented by a subject (server or user) is not trusted by the client application (such as a browser), the client will notify the user. The most common reason for a certificate not to be trusted is that the certificate issuer is not trusted. For example, say Widget's web server receives a certificate signed by MyCA. Unless MyCA's own certificate is stored in the browser's trusted root store, the client application will not trust the Widget server. The user can usually choose to ignore this warning and add an exception, but this should be done only if the cause of the lack of a trust relationship is understood.

If you trust the issuer, you can add their certificate to the client device's root certificate store. In Windows, you can use the certmgr.msc console to manage user certificates and the certlm.msc console to manage machine certificates. You also use these consoles to manage certificates used by the computer or its user accounts.

Certificate Management console. The Trusted Root CA contains all Microsoft and enterprise trusts, plus the third-party CA trusts. (Screenshot used with permission from Microsoft.)

One complication here is that different applications may have different stores of trusted certificates. For example, there is a Windows certificate store, but the Firefox® browser does not trust it by default and maintains its own certificate stores. The various Linux distributions store trusted root certificates in several different locations.

Frequently, certificates are untrusted because they are self-signed (the certificate holder is both the issuer and the subject of the certificate). This is often the case with the certificates used to protect the web management interfaces of consumer-grade appliances and server applications. You might be able to replace the default certificate with one trusted by the enterprise.

Some other causes of untrusted certificates are:

●	The certificate's subject name does not match the URL. This is usually a configuration error on the part of the web server manager, but it could indicate malicious activity. You should confirm the certificate's common name and access the website by using that URL.

This certificate is not trusted because it is self-signed and because it does not match the subject name (because the host is being accessed via an IP address instead of an FQDN). (Screenshot courtesy of Mozilla Foundation.)

●	The certificate is not being used for its stated purpose. For example, a certificate issued to sign email is being used on a web server. In this circumstance, you should not add an exception. The service owner or subject should obtain a correctly formatted certificate.

●	The certificate is expired or revoked. Again, unless there are explainable circumstances, you should not allow an exception. If you are managing a legacy appliance (a SOHO router or NAS drive, for instance), it is likely that the certificate installed on it will have expired. If you know that the appliance has not been tampered with, you can proceed.

●	Time is not correctly synchronized between the server and client.

Browsers and email applications usually display informative error messages. In other contexts, such as EAP authentication, it might not be so obvious that the certificate is the cause of the failure or why the certificate is being rejected. Inspect the logs recording the connection for clues.

OTHER COMMON ISSUES

When it comes to application layer troubleshooting, you will usually need to use references that are specific to the environment or app to solve problems. Some other generic issues you may encounter include time synchronization, mobile devices, and licensing.

NTP Issues

Most network services, and especially authentication and authorization mechanisms, depend upon each host using a synchronized time source. Inaccurate time sources also affect the reliability and usability of log data, which can have implications for regulatory compliance.

Time synchronization is usually accomplished via the Network Time Protocol (NTP). Clients must be able to access a time source over port UDP 123. In a Windows environment, the time source for clients will usually be a domain controller. The domain controller can either use a hardware GPS-based time source or rely on Internet servers, depending on the level accuracy required. In Windows, the w32tm /query /configuration command can be used to check the current configuration.

BYOD Challenges

Bring Your Own Device (BYOD) is a smartphone/tablet provisioning model that allows users to select a personal device to use to interact with corporate network services and cloud apps. Allowing user selection of devices introduces numerous compatibility, support, and security challenges:

●	Compatibility/support-The wide range of devices, mobile OS versions, and vendor support for patches make the job of ensuring that each device can connect to corporate network apps and data resources highly complex.

●	Security-This device variety also causes security issues, especially in terms of unpatched devices. Another issue is that the device is not fully under the administrative control of the IT department. An insider threat actor could install apps that might pose a risk to corporate data or misuse the device to exfiltrate data.

Some of the impact of these issues can be mitigated through the use of enterprise mobility management (EMM) suites and corporate workspaces. EMM (or mobile device management) is a type of network access control solution that registers devices as they connect to the network. It can then enforce security policies while the device is connected. These might restrict use of device functions or personal apps. A corporate workspace is an app that is segmented from the rest of the device and allow more centralized control over corporate data. Users must also agree to acceptable use policies, which might prohibit installing non-store apps and rooting/jailbreaking a device and keeping the device up to date with patches. Users will also usually have to submit to inspection of the device to protect corporate data.

Licensed Feature Issues

Licensing for servers and network appliances can be complex and it is easy to make configuration errors. When faced with an unexpected problem, it is often worth considering whether a licensing or feature activation issue could be the cause. On a switch or router, license failures could restrict the number of ports available, the number of routes allowed in the routing table, or the availability of routing protocols. Security and management features may have been configured under a trial or evaluation period and suddenly stop working when that grace period ends.

The starting point for troubleshooting license issues will be the log. This should show whether an evaluation/trial period has just expired or when a seat/instance count has been exceeded. Verify that the appliance has the correct licenses or activation keys installed. If relevant, ensure that the appliance can connect to its licensing or activation server.































Lesson 15: Deploying and Troubleshooting Wireless Networks

Topic 15A: Summarize Wireless Standards

IEEE 802.11 WIRELESS STANDARDS

Most wireless LANs (WLANs) are based on the IEEE 802.11 standards, better known by its brand name Wi-Fi. 802.11 standards define the physical layer media by which data is encoded into a radio carrier signal by using a modulation scheme. The properties of radio waves include amplitude (the height of peaks and troughs), frequency (the number of peaks per unit of time), and phase (the angle of a wave at a point in time). Modulation changes one or more of those properties to encode a signal. As well as modulation schemes, Wi-Fi standards use different carrier methods to provide sufficient resistance to interference from noise and other radio sources.

A wireless radio transmitting and receiving within a particular range of frequencies with the same modulation scheme is a half-duplex shared access medium (a physical bus). 802.11 uses Carrier Sense Multiple Access with Collision Avoidance (CSMA/CA) to cope with contention. Under CSMA/CA, when a station receives a frame, it performs error checking. If the frame is intact, the station responds with an acknowledgment (ACK). If the ACK is not received, the transmitting station resends the frame until timing out. 802.11 also defines a Virtual Carrier Sense flow control mechanism to further reduce the incidence of collisions. A station broadcasts a Request to Send (RTS) with the source and destination and the time required to transmit. The receiving station responds with a Clear To Send (CTS) and all other stations in range do not attempt to transmit within that period.

The CSMA/CA media access method. (Images © 123RF.com.)

The original 802.11 Wi-Fi standard worked only at 1 Mbps, but like the 802.3 Ethernet standard, it has been revised many times, with each iteration specifying different signaling and transmission mechanisms. Products conforming to the various standards can be certified by the Wi-Fi Alliance (wi-fi.org).

IEEE 802.11A AND 5 GHZ CHANNEL BANDWIDTH

Every wireless device operates on a specific radio frequency range within an overall frequency band. The specific frequency range is referred to as a channel . It is important to understand the difference between the two frequency bands used by the IEEE 802.11 standards:

●	2.4 GHz is better at propagating through solid surfaces, making it ideal for providing the longest signal range. However, the 2.4 GHz band does not support a high number of individual channels and is often congested, both with other Wi-Fi networks and other types of wireless technology, such as Bluetooth®. Consequently, with the 2.4 GHz band, there is increased risk of interference, and the maximum achievable data rates are typically lower than with 5 GHz.

●	5 GHz is less effective at penetrating solid surfaces and so does not support the maximum ranges achieved with 2.4 GHz standards, but the band supports more individual channels and suffers less from congestion and interference, meaning it supports higher data rates at shorter ranges.

The IEEE 802.11a standard specifies use of the 5 GHz frequency band and a multiplexed carrier scheme called Orthogonal Frequency Division Multiplexing (OFDM). 802.11a has a nominal data rate of 54 Mbps.

The 5 GHz band is subdivided into 23 non-overlapping channels, each of which is 20 MHz wide. Initially, there were 11 channels, but the subsequent 802.11h standard added another 12. 802.11h also adds the Dynamic Frequency Selection (DFS) method to prevent access points (APs) working in the 5 GHz band from interfering with radar and satellite signals. The exact use of channels can be subject to different regulations in different countries. Regulatory impacts also include a strict limit on power output, constraining the range of Wi-Fi devices.

IEEE 802.11B/G AND 2.4 GHZ CHANNEL BANDWIDTH

The 802.11b standard uses the 2.4 GHz frequency band and was released in parallel with 802.11a. It standardized the use of the carrier method Direct Sequence Spread Spectrum (DSSS), along with Complementary Code Keying (CCK) signal encoding. While in some ways DSSS was an inferior technology to OFDM-with a nominal data rate of just 11 Mbps-802.11b products were quicker to market and became better established than 802.11a.

The 2.4 GHz band is subdivided into up to 14 channels, spaced at 5 MHz intervals from 2412 MHz up to 2484 MHz. Because the spacing is only 5 MHz and Wi-Fi needs ~20 MHz channel bandwidth, 802.11b channels overlap quite considerably. This means that co-channel interference is a real possibility unless widely spaced channels are chosen (1, 6, and 11, for instance). Also, in the Americas, regulations permit the use of channels 1-11 only, while in Europe channels 1-13 are permitted, and in Japan all 14 channels are permitted.

Channel overlap in the 2.4 GHz band.

The 802.11g standard offered a relatively straightforward upgrade path from 802.11b. Like 802.11a, 802.11g uses OFDM, but in the 2.4 GHz band used by 802.11b and with the same channel layout. This made it straightforward for vendors to offer 802.11g devices that could offer backwards support for legacy 802.11b clients. 802.11g has a nominal data rate of 54 Mbps. When in 802.11b compatibility mode, it drops back to using DSSS.

IEEE 802.11N, MIMO, AND CHANNEL BONDING

The 802.11n standard increases bandwidth by multiplexing the signals from 2 to 4 separate antennas (a radio chain) using a collection of technologies generally referred to as Multiple Input Multiple Output (MIMO). The configuration of an 802.11n radio chain is identified by AxB:C notation, where A is the number of transmit antennas, B is the number of receive antennas, and C is the number of simultaneous transmit and receive streams. The maximum possible is 4x4:4, but common configurations are 2x2:2 or 3x3:2. For example, a 4x4:4 access point could allocate two streams carrying different data to a 2x2:2 client, increasing bandwidth. This is referred to as spatial multiplexing.

Having more transmit and receive antennas can also be used to improve signal reliability, rather than boosting bandwidth. If the same data stream is sent by two or three transmit antennas, the receiver can combine them to derive a stronger signal and increase range at a given data rate. Similarly, multiple receive antennas can derive a stronger signal, even if there is only one transmit stream. This is referred to as spatial diversity. For example, 2x2:2 and 2x3:2 radio chains have the same throughput, but the 2x3:2 chain could make more use of spatial diversity to increase range.

802\.11n products can also use channels in the 2.4 GHz band or the 5 GHz band. 802.11n also allows two adjacent 20 MHz channels to be combined into a single 40 MHz channel, referred to as channel bonding. Due to the restricted bandwidth of 2.4 GHz, on a network with multiple APs, channel bonding is a practical option only in the 5 GHz band. The 5 GHz band has a larger frequency range (up to 500 MHz in the USA), so it can provide up to 23 nonoverlapping channels. However, those channels are not necessarily contiguous, which slightly reduces the options for bonded channels.

Bonded channel options in the 5 GHz Unlicensed National Information Infrastructure (U-NII) sub-bands. Channels within the DFS range may be disabled if the site is near a radar transmitter.

Cheaper client adapters may support only the 2.4 GHz band. An access point (AP) or adapter that can support both is referred to as dual band. A dual band AP can support both 2.4 GHz and 5 GHz bands simultaneously. This allows legacy clients to be allocated to the 2.4 GHz band.

The data rate for 802.11n is 72 Mbps per stream. Assuming the maximum number of four spatial streams and optimum conditions, the nominal data rate could be as high as 600 Mbps for a 40 MHz bonded channel. 802.11n can work in High Throughput (HT)/greenfield mode for maximum performance or HT mixed mode for compatibility with older standards (801.11a-ht, 802.11b-ht, and 802.11g-ht). Mixed mode reduces overall WLAN performance, as it involves the transmission of legacy identification and collision avoidance frames (HT protection) but not to the extent that 802.11n devices are reduced to (say) 802.11g data rates. Operating in greenfield mode is likely to cause substantial interference if there are legacy WLANs operating nearby on the same channel(s). There is also a legacy (non-HT) mode, in which 802.11n's HT mechanisms are disabled completely. You might use this mode if you have an 802.11n-capable access point but don't have any 802.11n client devices.

In recent years, Wi-Fi standards have been renamed with simpler digit numbers. 802.11n is now officially designated as Wi-Fi 4.

WI-FI 5 AND WI-FI 6

The Wi-Fi 5 (or 802.11ac) and Wi-Fi 6 (802.11ax) standards continue the development of Wi-Fi technologies to increase bandwidth and support modern networks.

Wi-Fi 5 (802.11ac)

Wi-Fi 5 is designed to work only in the 5 GHz band. The 2.4 GHz band can be used for legacy standards (802.11g/n) in mixed mode. The aim for Wi-Fi 5 is to get throughput like that of Gigabit Ethernet or better. It supports more channel bonding (up to 80 or 160 MHz channels), up to 8 spatial streams, rather than 4, and denser modulation (at close ranges). The way Wi-Fi 5 uses the radio spectrum is designated as very high throughput (VHT).

As with 802.11n, only enterprise-class equipment is equipped with enough antennas to make use of three streams or more, and no devices were ever produced with more than 4x4:4 streams. Wi-Fi 5 access points are marketed using AC values, such as AC5300. The 5300 value represents 1000 Mbps over a 40 MHz 2.4 GHz band channel and two 2,167 Mbps streams over 80 MHz 5 GHz band channels.

Wi-Fi 6 (802.11ax)

Wi-Fi 6 uses more complex modulation and signal encoding to improve the amount of data sent per packet by about 40%. As with Wi-Fi 5, products are branded using the combined throughput. For example, AX6000 allows 1,148 Mbps on the 2.4 GHz radio and 4,804 over 5 GHz.

The way Wi-Fi 6 uses the radio spectrum is designated as high efficiency (HE) to reflect these improvements. The aim for Wi-Fi 6 is to approximate 10G connection speeds (AX11000). These data rates can only be achieved through use of a new 6 GHz frequency band.

Wi-Fi 6 reinstates operation in the 2.4 GHz band, mostly to support Internet of Things (IoT) device connectivity. In Wi-Fi 6, the OFDM with multiple access (OFDMA) modulation scheme allows sub-carriers or tones to be allocated in groups of different sizes, referred to as resource units (RUs), each of which can communicate in parallel. Where small RUs are used, this reduces throughput but provides more opportunities for a larger number of devices to transmit. The effect is to reduce latency where numerous small data packets are being transmitted. This technology provides better support for IoT devices. Stations that require more bandwidth can be assigned larger RUs. RUs can also be assigned based on class of service parameters, such as prioritizing voice over IP (VoIP) traffic. It also allows an access point to support legacy (Wi-Fi 4/5 stations) efficiently.

MULTIUSER MIMO

In basic 802.11 operation modes, bandwidth is shared between all stations because of the CSMA/CA contention protocol. An AP can communicate with only one station at a time; multiple station requests go into a queue. Wi-Fi 5 and Wi-Fi 6 products address this problem using beamforming or Multiuser MIMO (MU-MIMO).

Downlink MU-MIMO (DL MU-MIMO) allows the AP to use its multiple antennas to process a spatial stream of signals in one direction separately to other streams. This means that groups of stations on a different alignment can connect simultaneously and also obtain more bandwidth. For example, if four stations are positioned north, south, east, and west of a 4x4:4 AP, the AP should be able to allow each of them to connect at close to the maximum speed. If another station is added to the north, those two northern stations will share the available bandwidth along that beam path. Both stations and AP must support MU-MIMO. Where Wi-Fi 5 supports up to four stations communicating in parallel over 5 GHz only, Wi-Fi 6 can support up to eight in 2.4 GHz, 5 GHz, and 6 GHz bands, giving it better performance in congested areas.

With DL MU-MIMO, only the AP can initiate beamforming, so it is only available on the downlink from AP to station (not station to AP). Wi-Fi 6 supports uplink MU-MIMO (UL MU-MIMO), allowing stations to initiate beamforming with the access point.

For both Wi-Fi 5 and Wi-Fi 6, improvements are released to the market in waves. For example, UL MU-MIMO was released in wave 2 Wi-Fi 6 products, which also added support for the 6 GHz frequency band.

MU-MIMO and OFDMA are different but complementary technologies. MU-MIMO makes use of spatial streams, whereas OFDMA makes flexible use of subcarriers within a channel. Both can work together to increase parallelism (supporting communication with more devices simultaneously).

2G AND 3G CELLULAR TECHNOLOGIES

Where Wi-Fi is typically operated as private infrastructure, cellular radio is operated by telecommunications providers. A cellular radio establishes a connection using the nearest available cell or base station. Each base station has an effective range of up to 5 miles (8 km). The base station links the device to global telecommunications networks. Cellular radio works in the 850 and 1900 MHz frequency bands (mostly in the Americas) and the 900 and 1800 MHz bands (rest of the world).

Cellular digital communications standards are described as belonging to a generation. For 2G, there were two competing formats, established in different markets:

●	Global System for Mobile Communication (GSM)-based phones using Time Division Multiple Access (TDMA). With TDMA, each subscriber gets access to the radio channel by being allocated a time slot. GSM allows subscribers to use a subscriber identity module (SIM) card to use an unlocked handset with their chosen network provider. GSM is adopted internationally and by AT-and-T and T-Mobile in the United States.

●	TIA/EIA IS-95 (cdmaOne)-based handsets, using Code Division Multiple Access (CDMA). CDMA means that each subscriber uses a code to key the modulation of their signal and this "key" is used by the receiver to extract the subscriber's traffic from the radio channel. With CDMA, the handset is managed by the provider, not the SIM. CDMA adoption is largely restricted to the telecom providers Sprint and Verizon.

In both cases, the cell network was built primarily to support voice calls, so 2G data access was provided on top, using Circuit Switched Data (CSD). CSD is somewhat similar to a dial-up modem, though no analog transmissions are involved. CSD requires a data connection to be established to the base station (incurring call charges) and is only capable of around 14.4 Kbps at best.

The transition from 2G to 3G saw various packet-switched technologies deployed to mobiles:

●	General Packet Radio Services/Enhanced Data Rates for GSM Evolution (GPRS/EDGE) is a precursor to 3G (2.5G), with GPRS offering up to about 48 Kbps and EDGE about 3-4 times that. Unlike CSD, GPRS and EDGE allow "always on" data connections, with usage billed by bandwidth consumption rather than connection time.

●	Evolved High Speed Packet Access (HSPA+) is a 3G standard developed via several iterations from the Universal Mobile Telecommunications System (UMTS) used on GSM networks. HSPA+ nominally supports download speeds up to 168 Mbps and upload speeds up to 34 Mbps. HSPA+-based services are often marketed as 4G if the nominal data rate is better than about 20 Mbps.

Note that with HSPA, the TDMA channel access technology has been abandoned and a type of CDMA used.

●	CDMA2000/Evolution Data Optimized (EV-DO) are the main 3G standards deployed by CDMA network providers. EV-DO can support a 3.1 Mbps downlink and 1.8 Mbps uplink.

4G AND 5G CELLULAR TECHNOLOGIES

The replacements for 3G networks have seen convergence on a single set of worldwide standards.

4G/Long Term Evolution

Long Term Evolution (LTE) is a converged 4G standard supported by both the GSM and CDMA network providers. LTE devices must have a SIM card issued by the network provider installed. LTE has a maximum downlink of 150 Mbps in theory, but no provider networks can deliver that sort of speed at the time of writing, with around 20 Mbps far more typical of real-word performance.

LTE uses neither TDMA nor CDMA but Orthogonal Frequency Division Multiple Access (OFDMA), which is also used by Wi-Fi 6.

LTE Advanced (LTE-A) is intended to provide a 300 Mbps downlink, but again this aspiration is not matched by real-world performance. Current typical performance for LTE-A is up to 90 Mbps.

5G

According to the original specification, a 4G service was supposed to deliver 1 Gbps for stationary or slow-moving users (including pedestrians) and 100 Mbps for access from a fast-moving vehicle. Those data rates are now the minimum hoped-for standards for 5G. As with 4G, real-world speeds are nowhere near the hoped-for minimums, ranging from about 50 Mbps to 300 Mbps at time of writing.

5G uses different spectrum bands from low (sub-6 GHz) to medium/high (20-60 GHz). Low bands have greater range and penetrating power; high bands, also referred to as millimeter wave (mmWave) require close range (a few hundred feet) and cannot penetrate walls or windows. Consequently, design and rollout of 5G services is relatively complex. Rather than a single large antenna serving a large wireless cell, 5G involves installing hundreds of smaller antennas to form an array that can take advantage of multipath and beamforming to overcome the propagation limitations of the spectrum. This is also referred to as massive MIMO. As well as faster mobile speeds, 5G is expected to provide fixed-wireless broadband solutions for homes and businesses, and to support IoT networks.

Topic 15B: Install Wireless Networks

INFRASTRUCTURE TOPOLOGY AND WIRELESS ACCESS POINTS

Wireless network devices are referred to as stations (STA), similar to a node on a wired network. Most wireless networks are deployed in an infrastructure topology. In an infrastructure topology, each station is configured to connect through a base station or access point (AP), forming a logical star topology. The AP mediates communications between client devices and can also provide a bridge to a cabled network segment. In 802.11 documentation, this is referred to as an infrastructure Basic Service Set (BSS). The MAC address of the AP is used as the Basic Service Set Identifier (BSSID) . More than one BSS can be grouped together in an Extended Service Set (ESS).

Access point. (Image © 123RF.com.)

Each client station requires a wireless adapter compatible with the standard(s) supported by the AP.

WLAN configuration in infrastructure mode. (Images © 123RF.com.)

WIRELESS SITE DESIGN

Clients are configured to join a WLAN through the network name or Service Set Identifier (SSID). An SSID can be up to 32 bytes in length and for maximum compatibility should only use ASCII letters and digits plus the hyphen and underscore characters. In infrastructure mode, when multiple APs connected to the same distribution system are grouped into an ESS, this is more properly called the Extended SSID (ESSID) . This just means that all the APs are configured with the same SSID and security information. The area served by a single AP is referred to as a basic service area (BSA) or wireless cell. The area in which stations can roam between access points to stay connected to the same ESSID is referred to as an extended service area (ESA).

SSID Broadcast and Beacon Frame

A WLAN is typically configured to advertise its presence by broadcasting the SSID. This allows a user to connect to a named network. If SSID broadcast is suppressed, the user must configure the connection to the network manually. A beacon is a special management frame broadcast by the AP to advertise the WLAN. The beacon frame contains the SSID (unless broadcast is disabled), supported data rates and signaling, plus encryption/authentication requirements. The interval at which the beacon is broadcast (measured in milliseconds) can be modified. The default is usually 100 ms. Increasing the interval reduces the overhead of broadcasting the frame but delays joining the network and can hamper roaming between APs.

Even if SSID broadcast is suppressed, it is fairly easy for a network sniffer to detect it as clients still use it when connecting with the AP.

Speed and Distance Requirements

A device supporting the Wi-Fi standard should have an indoor range of at least 30 m (100 feet). 2.4 GHz radios support better ranges than 5 GHz ones and 802.11n and later standards improve range compared to earlier standards. Outdoor range can be double or triple indoor range. Each station determines an appropriate data rate based on the quality of the signal using a mechanism called Dynamic Rate Switching/Selection (DRS). If the signal is strong, the station will select the highest available data rate (determined by the 802.11 standard); if the signal is weak, the station will reduce the data rate.

Radio signals pass through solid objects, such as ordinary brick or drywall walls, but can be weakened or blocked by particularly thick walls or those of dense concrete or metal construction. Other radio-based devices can also cause interference as can devices as various as fluorescent lighting, microwave ovens, cordless phones, and (in an industrial environment), power motors and heavy machinery. Bluetooth uses the 2.4 GHz frequency range but a different modulation technique, so interference is possible but not common.

Consequently, a complex set of factors need to be taken into consideration when you are planning a wireless network. A site survey is a critical planning tool to ensure that the WLAN delivers acceptable data rates to the supported number of devices in all the physical locations expected.

SITE SURVEYS AND HEAT MAPS

A site survey is performed first by examining the blueprints or floor plan of the premises to understand the layout and to identify features that might produce radio frequency interference (RFI). This can be backed up by a visual inspection that may reveal things that are not shown on the blueprints, such as thick metal shelving surrounding a room that needs to have WLAN access. Each AP mounting point needs a network port and power jack, so it will help to obtain plans that show the locations of available ports.

A switch that supports Power over Ethernet (PoE) can be used to power a PoE-compatible AP.

The next step is to create a new plan on which you will mark the WLAN cells and associated APs and booster antennas. The idea here to is to place APs close enough together to avoid "dead zones"-areas where connectivity is difficult or data transfer rates are below an acceptable tolerance level-but far enough apart that one AP does not interfere with another or that one AP is overutilized and a nearby one underutilized.

Position an AP in the first planned location, then use a laptop with a wireless adapter and a wireless survey tool, such as Cisco Aironet, Metageek inSSIDer, or Ekahau Site Survey, to record signal strength and supported data rate at various points in the intended basic service area (BSA). Many tools can show the signal strength within a particular channel obtained in different locations graphically using a heat map. The heat map would show areas with a strong signal in greens and yellows with warning oranges and reds where signal strength drops off. This step is then repeated for each planned location. Neighboring APs should be configured with non-overlapping channels to avoid interfering with one another. It may also be necessary to adjust the transmit power of an AP to size its BSA appropriately.

Heat map generated by Ekahau Site Survey. (Image © Ekahau Inc.)

WIRELESS ROAMING AND BRIDGING

Clients can roam within an extended service area (ESA). An ESA is created by installing APs with the same SSID and security configuration connected by a wired network, or Distribution System (DS). The access points are configured with different channels so that where BSAs overlap, there is no interference. When the client detects that it is no longer receiving a good signal, it checks for another signal with the same SSID on other channels or on a different frequency band, and if there is a stronger signal, it disassociates from the current AP. The station can then reassociate with the new AP. Depending on the roaming infrastructure and security type, the station may have to reauthenticate, or if 802.11r fast roaming is supported, it may be able to use its existing authentication status to generate security properties for the new association.

Roaming is supposed to be seamless, but in practice reestablishing the connection can often cause time-out problems for applications. To improve mobility, there needs to be a balance between determining what constitutes a "good" signal and the frequency with which a client tries to associate with different APs. Many adapters support a roaming "aggressiveness" setting that can be configured to prevent a Wi-Fi adapter "flapping" between two APs or (conversely) to prevent a client remaining associated with a more distant AP when it could achieve better bandwidth through one closer to it.

You can also configure multiple access points to cover areas where it is not possible to run cabling. This is referred to as a wireless distribution system (WDS). You must set the APs to use the same channel, SSID, and security parameters. The APs are configured in WDS/repeater mode. One AP is configured as a base station, while the others are configured as remote stations. The base station can be connected to a cabled segment. The remote stations must not be connected to cabled segments. The remote stations can accept connections from wireless stations and forward all traffic to the base station.

Another use for WDS is to bridge two separate cabled segments. When WDS is configured in bridge mode, the APs will not support wireless clients; they simply forward traffic between the cabled segments.

WDSs support and implementation can vary between manufacturers. If you are implementing WDS, it is usually best to use APs from the same vendor.

WIRELESS LAN CONTROLLERS

An enterprise network might require the use of tens or hundreds of access points. If APs are individually managed, this can lead to configuration errors on specific APs and can make it difficult to gain an overall view of the wireless deployment, including which clients are connected to which APs and which clients or APs are producing the most traffic.

A wireless controller, an enterprise-level appliance capable of supporting up to 1500 APs and 20,000 clients. (Image © 123RF.com.)

Rather than configure each device individually, enterprise wireless solutions such as those manufactured by Cisco, Ruckus, or Ubiquiti allow for centralized management and monitoring of the APs on the network. This may be achieved through use of a dedicated hardware device called a wireless LAN controller. Alternatively, some implementations use a software application to centralize the management function, which can be run on a server or workstation.

An AP whose firmware contains enough processing logic to be able to function autonomously and handle clients without the use of a wireless controller is known as a fat AP, while one that requires a wireless controller in order to function is known as a thin AP . Cisco wireless controller usually communicate with the APs by using the Lightweight Access Point Protocol (LWAPP). LWAPP allows an AP configured to work in lightweight mode to download an appropriate SSID, standards mode, channel, and security configuration. Alternatives to LWAPP include the derivative Control And Provisioning of Wireless Access Points (CAPWAP) protocol or a proprietary protocol.

As well as autoconfiguring the appliances, a wireless controller can aggregate client traffic and provide a central switching and routing point between the WLAN and wired LAN. It can also assign clients to separate VLANs. Automated VLAN pooling ensures that the total number of stations per VLAN is kept within specified limits, reducing excessive broadcast traffic. Another function is to supply power to wired access points, using Power over Ethernet (PoE).

AD HOC AND MESH TOPOLOGIES

While most corporate and many SOHO networks are configured in infrastructure mode, there are also wireless topologies that allow stations to establish peer-to-peer links.

Ad Hoc Topology

In an ad hoc topology, the wireless adapter allows connections to and from other devices. In 802.11 documentation, this is referred to as an Independent Basic Service Set (IBSS). This topology does not require an access point. All the stations within an ad hoc network must be within range of one another. An ad hoc network might suit a small workgroup of devices, or connectivity to a single device, such as a shared printer, but it is not scalable to large network implementations.

IBSS is not supported by the updated WDI driver model in the latest versions of Windows (docs.microsoft.com/en-us/windows-hardware/drivers/network/wdi-features-not-carried-over-in-wdi).

Mesh Topology

The 802.11s standard defines a Wireless Mesh Network (WMN). There are also various proprietary mesh protocols and products. Unlike an ad hoc network, nodes in a WMN (called mesh stations) are capable of discovering one another and peering, forming a Mesh Basic Service Set (MBSS). The mesh stations can perform path discovery and forwarding between peers using a routing protocol, such as the Hybrid Wireless Mesh Protocol (HWMP).

These features make a mesh topology more scalable than an ad hoc topology because the stations do not need to be within direct radio range of one another-a transmission can be relayed by intermediate stations. Mesh topologies are becoming increasingly popular and are the foundation of most Internet of Things (IoT) networks.

Topic 15C: Troubleshoot Wireless Networks

WIRELESS PERFORMANCE ASSESSMENT

Wireless issues can be broadly divided into issues with signal strength or interference (like cabling issues in a wired LAN) and configuration issues. This topic focuses on issues that affect signal strength and performance, but always check that the security and authentication parameters are correctly configured before assuming you have a Physical layer connectivity problem. Configuration issues are discussed in the next topic.

As with cabled networks, you should distinguish between speed and throughput when measuring and assessing wireless performance against the specifications and limitations of a particular Wi-Fi standard:

●	Speed is the data rate established at the physical and data link layers. The nominal link speed is determined by standards support (Wi-Fi 5 or Wi-Fi 6, for instance), use of bonded channels, and optimizations, such as MU-MIMO. If the sender and receiver are far apart or subject to interference, a lower rate will be negotiated to make the link more reliable.

●	Throughput is the amount of data that can be transferred at the network layer, discarding overhead from layers 1 and 2. Often the term goodput is used to describe data transfer achieved at the application layer (accounting for overhead from header fields and packet loss/retransmissions).

As with cabling, attenuation refers to the weakening of the signal as the distance between the devices increases. This can be described more precisely as radio frequency (RF) attenuation or free space path loss. As the distance from the antenna increases, the strength of the signal decreases in accordance with the inverse-square rule. For example, doubling the distance decreases the signal strength by a factor of four. Meanwhile, interference sources collectively overlay a competing background signal, referred to as noise. These factors impose distance limitations on how far a client can be from an access point.

Attenuation and signal strength are measured in decibels. Signal strength is represented as the ratio of a measurement to 1 milliwatt (mw), where 1 mW is equal to 0 dBm. dB and dBm units can be combined to analyze losses and gains in signal strength along a communications path. For example, if you transmit a radio signal at 1 mW and use an antenna to boost the signal, the effective power is:

0 dBm + 3 dB = 2 mW = ~3 dBm

Conversely, dB loss due to attenuation or noise means loss of power/signal strength:

1. dBm – 1 dB = 2 dBm = ~1.58 mW

Because 0 dBm is 1 mW, a negative value for dBm represents a fraction of a milliwatt. For example, -30 dBm is 0.001 mW; -60 dBm is 0.000001 mW. Wi-Fi devices are all constrained by regulations governing spectrum use and output only small amounts of power.

SIGNAL STRENGTH

The Received Signal Strength Indicator (RSSI) is the strength of the signal from the transmitter at the client end. When you are measuring RSSI, dBm will be a negative value (a fraction of a milliwatt) with values closer to zero representing better performance. A value around - 65 dBm represents a good signal, while anything over -80 dBm is likely to suffer packet loss or be dropped. The RSSI must exceed the minimum receiver sensitivity.

Depending on the vendor, RSSI might be measured directly in dBm or might be an index value related to a scale of dBm measurements. RSSI indices can be measured as 0-60, 0-127, or as 0-255. On a client, this index is displayed as a number of bars of signal strength on the adapter icon.

The comparative strength of the data signal to the background noise is called the Signal-To-Noise Ratio (SNR). Noise is also measured in dBm, but here values closer to zero are less welcome as they represent higher noise levels. For example, if signal is ‑65 dBm and noise is ‑90 dBm, the SNR is the difference between the two values, expressed in dB (25 dB). If noise is -80 dBm, the SNR is 15 dB and the connection will be much, much worse.

RSSI and SNR can be measured by using a Wi-Fi analyzer. This type of software can be installed to a laptop or smartphone. It will record statistics for the AP that the client is currently associated with and detect any other access points in the vicinity.

ANTENNA TYPES

The antenna type determines the propagation pattern or shape of the radio waves transmitted. Most wireless devices have simple omnidirectional vertical rod-type antennas, which receive and send signals in all directions more-or-less equally. Access points with omnidirectional antennas should ideally be ceiling-mounted for best coverage, unless the ceiling is particularly high. The propagation pattern is shaped like a torus (donut), rather than a sphere, and radiates more powerfully in the horizontal plane than it does in the vertical plane. Locating the antenna above head height will minimize interference from obstructing furniture by allowing line-of-sight to most connecting devices but positioning it too high (above around 25 ft) will reduce signal strength, especially for stations directly below the antenna. You can obtain APs with downtilt omnidirectional antennas for use on high ceilings.

To extend the signal to a particular area, you can use an antenna focused in a single direction (unidirectional). Both the sender and receiver must use directional antennas, or one will be able to receive signals but not send responses. Unidirectional antenna types include the Yagi (a bar with fins) and parabolic (dish or grid) form factors. Unidirectional antennas are useful for point-to-point wireless bridge connections. The increase in signal strength obtained by focusing the signal is referred to as the gain and is measured in dBi (decibel isotropic). The amount of directionality, referred to as the beamwidth, is measured in degrees. A pair of 10-degree antennas are very highly directional and will require more exact alignment than a pair of 90 degree antennas.

A variety of generic antenna types: from left to right, a vertical rod antenna, a Yagi antenna, a parabolic/dish antenna, and a parabolic grid antenna.

Polarization refers to the orientation of the wave propagating from the antenna. If you imagine a rod-type antenna, when the rod is pointed up relative to the floor, the wave is horizontally polarized; if you orient the rod parallel to the floor, the wave is vertically polarized. To maximize signal strength, the transmission and reception antennas should normally use the same polarization. This is particularly important when deploying unidirectional antennas for a point-to-point link. Some antennas are dual-polarized, meaning that they can be installed in either orientation. Dual-polarized antennas are also the best way to support mobile devices, as these can be held by their user in a variety of orientations.


Surveying Wi-Fi networks using inSSIDer. The chart shows which channels are active and the signal strength of different networks in each channel. (Screenshot used with permission from MetaGeek.)

INSUFFICIENT WIRELESS COVERAGE ISSUES

Insufficient wireless coverage refers to spots within a building with no or weak Wi-Fi signal. If a sufficient signal strength cannot be obtained and sources of interference cannot be mitigated, the only solution to is to install an additional device to cover the gap. If you cannot extend the distribution system (cabled network) to support an additional access point, you will need to configure a wireless bridge or use a range extender.

Antenna Placement

Incorrect antenna placement could cause or exacerbate attenuation and interference problems. Use a site survey and heat map to determine the optimum position for APs and (if available) the direction in which to point adjustable antennas. Also, using an incorrect antenna type may adversely affect the signal strength at any given point. A unidirectional antenna is only suitable for point-to-point connections, not for general client access. The internal antennas built into APs may also be optimized to transmit and receive in some directions more than others. For example, an AP designed for ceiling mounting may produce a stronger signal in a cone directed downwards from its central axis, whereas the signal from a similar AP designed for wall installation is more likely to be angled outwards. Consult the documentation for your specific model of AP or use site survey software to produce a heat map.

Remember that some client devices might support a standard such as 802.11n, but only have a single band 2.4 GHz radio. They will not be able to join a 5 GHz network.

Antenna Cable Attenuation

Another source of attenuation is where the antenna is connected at some distance from the access point via coax cabling. Signal loss along this cable is referred to as antenna cable attenuation. LMR/HDF/CFD 200 cable has attenuation of about 0.6 dB/m (decibels per meter), while 400 cable improves that to about 0.22 dB/m. Connector loss is usually calculated as 0.15 dB.

If a device has removable antennas, check that these are screwed in firmly. A loose or disconnected antenna may reduce the range of the device or prevent connectivity altogether.

Effective Isotropic Radiated Power/Power Settings

The power at which an access point transmits is configurable. Effective Isotropic Radiated Power (EIRP) is calculated as the sum of transmit power, antenna cable/connector loss, and antenna gain. For example, if you are configuring a point-to-point link with a directional antenna, you might derive the following value for EIRP:

15 dBm (Transmit Power) – 1 dB (Cable Loss) + 6 dBi (Gain) = 20 dBm (100 mW)

The EIRP for each radio is reported through the access point or controller management software. EIRP must not exceed regulatory limits. Power limits are different for the 2.4 GHz and 5 GHz bands and for point-to-multipoint versus point-to-point operation modes.

Increasing transmit power is not usually an effective solution to improving wireless coverage. While an AP might have an EIRP of around 23 dBm, smartphone devices are more likely to be around 10 to 14 dBm. If the client detects a strong signal, it will set a high data rate. However, because the EIRP of the client radio is much lower, it fails to transmit a strong signal back to the AP. Because it is trying to use a high data rate, this results in excessive packet errors.

As a general rule of thumb, AP power should be 2/3rds of the weakest client power. For example, if the weakest client can output 14 dBm, the AP should transmit at 9 to 10 dBm.

CHANNEL UTILIZATION AND OVERLAP ISSUES

Channel overlap refers to interference issues resulting from multiple access points that are all in range of one another and are configured to use similar wavelengths. There are two main types of channel interference:

●	Co-channel interference (CCI)-This can be more accurately described as contention. When multiple access points use the same channel, opportunities to transmit are reduced. The wireless devices must use CSMA/CA to find opportunities to transmit. CCI can be measured as a percentage referred to as channel utilization. Channel utilization can be measured from the access point or using a Wi-Fi analyzer. As a design goal, a channel should exhibit no more than 50% utilization.

●	Adjacent channel interference (ACI)-This occurs when access points are configured to use different but overlapping channels, such as 1 and 3 in the 2.4 GHz band. ACI slows down the CSMA/CA process and raises noise levels.

One of the design goals for a multi-AP site is to create clean cells so that clients can select an AP with the strongest signal easily and the WLAN operates with a minimum of co-channel interference. At least 25 MHz spacing should be allowed to avoid channel overlap. In practice, therefore, no more than three nearby APs using the 2.4 GHz band can have non-overlapping channels. This could be implemented, for example, by selecting channel 1 for AP1, channel 6 for AP2, and channel 11 for AP3. When you are using the 5 GHz band for 802.11a or Wi-Fi 4/5/6, more non-overlapping channels are available.

In a complex environment, it may be necessary to adjust the power level used by an AP on a given channel. Using the maximum available power on an AP can result in it interfering with other "cells" and to situations where a client can "hear" the AP but cannot "talk" to it because it lacks sufficient power.

Checking power levels on a wireless station using Intel's PROSet Wi-Fi configuration utility. (Screenshot courtesy of Intel Corp.)

In order to enable seamless roaming for mobile clients, the cells served by each AP need to overlap to some extent in order to support roaming. This is one of the trickiest elements of site design to get right, as client behaviors and capabilities for roaming can vary widely. If there is a bring your own device (BYOD) policy in place, these support issues are even more greatly magnified.

Issues with roaming can be identified by analyzing access point association times for client devices. A WLAN controller will be able to track client mobility, showing each access point and the time that the client associated with it. If a large number of clients flap between two access points repeatedly, the site design might need to be investigated to solve the roaming issue.


OVERCAPACITY ISSUES

Overcapacity (or device saturation) occurs when too many client devices connect to the same AP. The maximum number of clients that an AP can support varies, depending on the Wi-Fi standard used and the type of network traffic generated. For example, web browsing will typically place a lighter load on the network than local client-server traffic or is likely at least to move any bottleneck further upstream to the WAN, rather than the wireless network. While individual circumstances must be considered, a maximum of 30 clients per AP is generally accepted as a rule of thumb. In designing the network, enough APs should be provided in appropriate locations to support the expected client density at this ratio. APs can usually be configured to enforce a maximum number of connections, so that additional clients will connect to the next nearest AP. Even with a relatively low number of clients, the wireless network can suffer from bandwidth saturation. Since wireless is a broadcast medium, the available bandwidth is shared between all clients. Thus, if one client is a bandwidth hog, others may find it difficult to maintain a reliable connection.

In an enterprise Wi-Fi solution, a controller will normally provide reporting tools to diagnose bandwidth issues and to report on which clients are consuming the most bandwidth. It could also report on wireless channel utilization and configure APs and clients to reassign channels dynamically to reduce overutilization. If a traffic shaper is deployed, it may work automatically to throttle bandwidth to overactive nodes.

INTERFERENCE ISSUES

If a device is within the supported range but the signal is weak or you cannot get a connection, there is likely to be interference. Apart from channel interference described earlier, there are several other sources of interference to consider:

●	Reflection/bounce (multipath interference)-Mirrors or shiny surfaces cause signals to reflect, meaning that a variable delay is introduced. This causes packets to be lost and consequently the data rate to drop.

The Wi-Fi 4/5/6 standards actually use bounce (multipath) as a means of optimizing throughput and range via MIMO.

●	Refraction -Glass or water can cause radio waves to bend and take a different path to the receiver. This can also cause the data rate to drop.

●	Absorption-This refers to the degree to which walls and windows will reduce signal strength (some of the radio wave's energy is lost as heat when passing through construction materials). An internal wall might "cost" 3 to 15 dB, depending on the material used (concrete being the most effective absorber). The 2.4 GHz frequency has better penetration than the 5 GHz one, given the same power output. To minimize absorption from office furniture (and people), use ceiling-mounted APs.

●	Electromagnetic interference (EMI)-Interference from a powerful radio or electromagnetic source working in the same frequency band, such as a Bluetooth device, cordless phone, or microwave oven.

EMI can be detected by using a spectrum analyzer. Unlike a Wi-Fi analyzer, a spectrum analyzer must use a special radio receiver-Wi-Fi adapters filter out anything that isn't a Wi-Fi signal. They are usually supplied as handheld units with a directional antenna, so that the exact location of the interference can be pinpointed. A 6 dB change in the level of a particular source represents a halving or doubling of the distance between the analyzer and the source of the RF source.

Also consider that signal problems could be a result of someone trying to attack the network by jamming the legitimate AP and making clients connect to a rogue AP.

Topic 15D: Configure and Troubleshoot Wireless Security

WI-FI ENCRYPTION STANDARDS

As well as the site design, a wireless network must be configured with security settings. Without encryption, anyone within range can intercept and read packets passing over the wireless network. The choice of which security settings to apply is determined by device support for the various Wi-Fi encryption standards, by the type of authentication infrastructure, and by the purpose of the WLAN. The encryption standard determines the cryptographic protocols that are supported, the means of generating the encryption key, and available methods for authenticating wireless stations when they try to join (or associate with) the network.

The first version of Wi-Fi Protected Access (WPA) was designed to fix critical vulnerabilities in the earlier wired equivalent privacy (WEP) standard. Like WEP, version 1 of WPA uses the RC4 stream cipher to encrypt traffic but adds a mechanism called the Temporal Key Integrity Protocol (TKIP) to try to mitigate the various attacks against WEP that had been developed.

Configuring a TP-LINK SOHO access point with wireless encryption and authentication settings. In this example, the 2.4 GHz band allows legacy connections with WPA2-Personal security, while the 5 GHz network is for 802.11ax (Wi-Fi 6) capable devices using WPA3-SAE authentication. (Screenshot used with permission from TP-Link Technologies.)

Neither WEP nor the original WPA version are considered secure enough for continued use. They can be exploited by various types of replay attack that aim to recover the encryption key. WPA2 uses the Advanced Encryption Standard (AES) cipher deployed within the Counter Mode with Cipher Block Chaining Message Authentication Code Protocol (CCMP). AES replaces RC4 and CCMP replaces TKIP. CCMP provides authenticated encryption, which is designed to make replay attacks harder.

Weaknesses have also been found in WPA2, however, which has led to its intended replacement by WPA3.

PERSONAL AUTHENTICATION

In order to secure a network, you need to be able to confirm that only valid users are connecting to it. Wi-Fi authentication comes in three types: personal, open, and enterprise. Within the personal authentication category, there are two methods: pre-shared key authentication (PSK) and simultaneous authentication of equals (SAE).

WPA2 Pre-Shared Key Authentication

In WPA2, pre-shared key (PSK) authentication uses a passphrase to generate the key that is used to encrypt communications. It is also referred to as group authentication because a group of users share the same secret. When the access point is set to WPA2-PSK mode, the administrator configures a passphrase of between 8 and 63 characters. This is converted to a type of hash value, referred to as the pairwise master key (PMK). The same secret must be configured on the access point and on each node that joins the network. The PMK is used as part of WPA2's 4-way handshake to derive various session keys.

All types of Wi-Fi PSK authentication have been shown to be vulnerable to attacks that attempt to recover the passphrase. At a minimum, the passphrase must be at least 14 characters long to try to mitigate risks from cracking.

WPA3 Personal Authentication

While WPA3 still uses a passphrase to authenticate stations in personal mode, it changes the method by which this secret is used to agree session keys. The scheme used is also referred to as Password Authenticated Key Exchange (PAKE). In WPA3, the Simultaneous Authentication of Equals (SAE) protocol replaces the 4-way handshake, which has been found to be vulnerable to various attacks.

The configuration interfaces for access points can use different labels for these methods. You might see WPA2-Personal and WPA3-SAE rather than WPA2-PSK and WPA3-Personal, for example. Additionally, an access point can be configured for WPA3 only or with support for legacy WPA2 (WPA3-Personal Transition mode).

ENTERPRISE/IEEE 802.1X AUTHENTICATION

The main problems with personal modes of authentication are that distribution of the key or passphrase cannot be secured properly, and that users may choose unsecure phrases. Personal authentication also fails to provide accounting, as all users share the same credential.

As an alternative to personal authentication, WPA’s enterprise authentication method implements IEEE 802.1X to use an Extensible Authentication Protocol (EAP) mechanism to authenticate against a network directory. 802.1X defines the use of EAP over Wireless (EAPoW) to allow an access point to forward authentication data without allowing any other type of network access. It is configured by selecting WPA2-Enterprise or WPA3-Enterprise as the security method on the access point.

With enterprise authentication, when a wireless station requests an association, the AP enables the channel for EAPoW traffic only. It passes the credentials of the supplicant to an AAA (RADIUS or TACACS+) server on the wired network for validation. When the supplicant has been authenticated, the AAA server transmits a master key (MK) to the supplicant. The supplicant and authentication server then derive the same pairwise master key (PMK) from the MK. The AAA server transmits the PMK to the access point. The wireless station and access point use the PMK to derive session keys, using either the WPA2 four-way handshake or WPA3 SAE methods.

Using Cisco's Virtual Wireless LAN Controller to set security policies for a WLAN-This policy enforces use of WPA2 and the use of 802.1X (Enterprise) authentication. (Image © and Courtesy of Cisco Systems, Inc. Unauthorized use not permitted.)

WI-FI SECURITY CONFIGURATION ISSUES

While signal loss and interference are factors that always need considering, if there is a basic connectivity problem, then you will probably want to investigate the configuration of the client and/or AP first.

Wrong SSID and Incorrect Passphrase Issues

If SSID broadcast is suppressed, a station can still connect to a WLAN by entering the network name manually. If this is the case, check that the clients are configured with the correct SSID/ESSID. Remember that this value is case sensitive. Technically, an SSID can contain spaces and special characters, but this can cause problems so is best avoided. Check that the authentication settings are the same on all devices. If a passphrase is used, make sure it is entered correctly. On the AP, ensure the authentication type is not set to open, unless the intention is to provide unrestricted public access.

It is possible that two APs are operating with the same SSID. If authentication is required, the connection with the wrong SSID will fail. If there is no authentication (open network), then the host will connect but take care, as this may be an attempt to snoop on the host's traffic using a rogue AP. Also, if a user is joining a WLAN for the first time, it may be the case that there are SSIDs from overlapping WLANs with very similar default names and the user may be confused about which name to choose.

Encryption Protocol Mismatch Issues

If the user is supplying the correct key or credentials, check that the client can support the encryption and authentication standards configured on the AP. A driver update or OS patch may be required. An encryption protocol mismatch will cause the connection to fail, even if the correct credentials are supplied.

CLIENT DISASSOCIATION ISSUES

In the normal course of operations, an access point and client use management frames to control connections. The access point normally broadcasts a beacon frame to advertise service capabilities. Clients can choose to first authenticate and then associate to an access point when they move into range of the beacon. The client or access point can use disassociation and/or deauthentication frames to notify the other party that it has ended a connection. A legitimate client might disassociate but not deauthenticate because it is roaming between wireless access points in an extended service area. A client might "flap" between two access points, causing numerous disassociations and reassociations. Investigate the access point or controller event log to identify the cause of disassociations.

If clients are disassociated unexpectedly and there is no roaming, interference, or driver issue, you should consider the possibility of a malicious attack. A disassociation attack exploits the lack of encryption in management frame traffic to send spoofed frames. One type of disassociation attack injects management frames that spoof the MAC address of a single victim station in a disassociation notification, causing it to be disconnected from the network. Another variant of the attack broadcasts spoofed frames to disconnect all stations. Frames can be spoofed to send either disassociation or deauthentication notifications.

Disassociation/deauthentication attacks may be used to perform a denial of service attack against the wireless infrastructure or to exploit disconnected stations to try to force reconnection to a rogue WAP. Disassociation/deauthentication attacks might also be used in conjunction with a replay attack aimed at recovering the network key.

OPEN AUTHENTICATION AND CAPTIVE PORTAL ISSUES

Configuring an access point for open authentication means that the client is not required to authenticate. This mode would be used on a public AP or "hotspot". In WPA/WPA2, this also means that data sent over the link is unencrypted. Open authentication may be combined with a secondary authentication mechanism managed via a browser. When the client associates with the open hotspot and launches the browser, the client is redirected to a captive portal or splash page. This will allow the client to authenticate to the hotspot provider's network (over HTTPS, so the login is secure). The portal may also be designed to enforce terms and conditions and/or take payment to access the Wi-Fi service.

Most captive portal issues arise because the redirect does not work. The captive portal should use HTTPS. Most modern browsers will block redirection to sites that do not use TLS. This means that the captive portal also needs to be installed with a digital certificate issued by a certification authority (CA) that is trusted by the client browser.

When using open wireless, users must ensure they send confidential web data only over HTTPS connections and only use email, VoIP, IM, and file transfer services with SSL/TLS enabled. Another option is for the user to join a virtual private network (VPN). The user would associate with the open hotspot then start the VPN connection. This creates an encrypted "tunnel" between the user's computer and the VPN server. This allows the user to browse the web or connect to email services without anyone eavesdropping on the open Wi-Fi network being able to intercept those communications. The VPN could be provided by the user's company or they could use a third-party VPN service provider. Of course, if using a third party, the user needs to be able to trust them implicitly. The VPN must use certificate-based tunneling to set up the "inner" authentication method.






















Lesson 16: Comparing WAN Links and Remote Access Methods

Topic 16A: Explain WAN Provider Links

WIDE AREA NETWORKS AND THE OSI MODEL

Wide area network (WAN) technologies support data communications over greater distances than LANs. The term enterprise WAN is used to describe a WAN that is used and controlled by a single organization. However, even though an enterprise may control its WAN, it rarely owns all the infrastructure that supports it. Long distance communications usually involve the use of public networks. Public networks are owned by telecommunications (telco) companies and provide WAN services to businesses and households. Organizations often choose to use public networks, as the cost is far less than implementing a private solution. Service providers often have rights of access to locations that are not available to other organizations, such as under roads.

As with a LAN, the WAN Physical layer describes the media type and interface specifications. Where the provider link is a copper cable, some type of modem is usually used, rather than a switch. A modem performs modulation of outgoing signals and demodulation of incoming data, working only at the physical layer of the OSI model. Modulation means transforming an electromagnetic wave to represent information, such as using the amplitude (height) of the wave to represent bits. Legacy modems perform digital to analog modulation for transmission over voice lines. An analog (or dial-up) modem only supports low bandwidths (up to 56 Kbps). Digital modems perform a different type of modulation to transform digital signals received as Ethernet frames for transmission over the WAN media. Digital modem types include data service units (DSUs) for leased lines, digital subscriber line (DSL) modems, cable modems, and satellite modems.

At the data link layer, WANs often use simpler protocols to Ethernet LANs as the links are more likely to be point-to-point and do not need much complexity. That said, Ethernet is increasingly being deployed for end-to-end connectivity over WANs.

At the network layer, the customer and provider site are addressed using IP. A customer edge (CE) router connects to a provider edge (PE) via the underlying link layer interface. The provider allocates public IPv4/IPv6 addresses or address ranges to the customer.

WAN PROVIDER LINKS

Establishing a WAN provider link means terminating the access provider's cabling at some point in your premises, and then attaching modem and routing equipment to that line. The service-related entry point at which the access provider's network terminates is called the demarcation point (or demarc for short) or minimum point of entry (MPOE). The demarc point represents the end of the telco's responsibility for maintaining that part of the cabling. Any cable problems arising from the other side of the demarc point are the responsibility of the customer.

Modems and routers or other access equipment that are provided or leased by the customer and installed at their site are referred to as customer premises equipment (CPE). Some providers may take on responsibility for faults that arise in CPE, depending on the contract and installation circumstances.

The demarc and CPE should be installed to a secure location within the premises, with access controls to restrict the area to authorized staff. This location is referred to as entrance facilities in TIA/EIA structured cabling standards.

T-CARRIER AND LEASED LINE PROVIDER LINKS

The T-carrier system was developed by the telecommunications provider Bell Labs to allow multiple calls to be placed on a single cable. T-carrier enabled voice traffic to be digitized for transport around the core of the telecommunications network. It also enabled other types of digital data to be transported and could be provisioned directly to subscribers as a leased line. T-carrier is based on Time Division Multiplexing (TDM). The protocol assigns each circuit (or channel) a time slot. Each 64 Kbps channel provides enough bandwidth for a digitized voice call.

A single 64 Kbps channel is known as a DS0 or narrowband link. For leased line data services, however, the foundation level of T-carrier is the DS1 or T1 digital signal circuit. This service comprises 24 channels multiplexed into a single 1.544 Mbps full duplex digital connection that can be used for voice and/or data. The T1 lines themselves can be multiplexed to provide even more bandwidth.

A T1 line from the service provider is terminated at the demarc on a smartjack or Network Interface Unit (NIU). The smart jack has an RJ-48C or RJ-48X interface on the customer side that is used to connect to the customer’s Channel Service Unit/Data Service Unit (CSU/DSU) . The cabling from the smart jack to the CSU/DSU can use an ordinary RJ-45 patch cord (up to 3 meters/10 feet in length), but a shielded two-pair 22 AWG cable with connectors wired for RJ-48 is required for any distance longer than that.

The RJ-48X jack has a shorting bar to provide loopback on the connection if the equipment on the customer side is unplugged. This allows the service provider to test the line remotely.

The DSU encodes the signal from Data Terminal Equipment (DTE)-that is, the company's private branch exchange (PBX) internal telecoms system and/or an IP router-to a serial digital signal transmitted over copper wiring. The DSU part functions as a digital modem, while the CSU is used to perform diagnostic tests on the line. The devices can be supplied separately, but more typically they are combined as a single WAN interface card that can be plugged into a compatible router or PBX.

WAN termination equipment. (Image © 123RF.com.)

At the data link layer, T1 leased lines typically use either High-level Data Link Control (HDLC) or Point-to-Point Protocol (PPP).

DIGITAL SUBSCRIBER LINE PROVIDER LINKS

Digital subscriber line (DSL) is a technology for transferring data over voice-grade telephone lines, often referred to as the local loop. DSL uses the frequencies above those used by the human voice as a full duplex communications channel.

DSL Modems

A DSL modem is installed as CPE, typically as a multifunction “wireless router,” where the RJ-11 WAN port connects to the provider’s phone jack over a short length of ribbon cable. DSL modems can also be supplied as separate appliances or plug-in cards for routers. A standalone DSL modem is connected to the phone line via an RJ-11 port and to the local network's router (or a single computer on the local network) via an RJ-45 Ethernet port.

RJ-11 DSL (left) and RJ-45 LAN (right) ports on a DSL modem. (Image © 123RF.com.)

A filter (splitter) must be installed on each phone point to prevent noise from affecting either voice calls or the DSL link. These can either be installed at the demarc point by the telco engineer or self-installed on each phone point by the customer.

The main drawback of DSL is that, as a copper-wire technology, it suffers from attenuation. The maximum range of a DSL modem is typically about 3 miles (5 km), but the longer the connection, the greater the deterioration in data rate. Domestic cabling may also be relatively poor quality and pass through "noisy" environments.

DSL Types

There are various types or flavors of DSL. These are standardized by the ITU in a series of G. recommendations.

●	Symmetrical DSL (SDSL) is so-called because it provides the same downlink and uplink bandwidth. There are various types of symmetric DSL service. SDSL services tend to be provided as business packages, rather than to residential customers.

●	Asymmetrical DSL (ADSL) (G.992) is a consumer version of DSL that provides a fast downlink but a slow uplink. There are various iterations of ADSL, with the latest (ADSL2+) offering downlink rates up to about 24 Mbps and uplink rates up to 3.3 Mbps. Service providers may impose usage restrictions to limit the amount of data downloaded per month. Actual speed may be affected by the quality of the cabling in the consumer's premises and between the premises and the exchange, and by the number of users connected to the same DSLAM (contention).

FIBER TO THE CURB

The major obstacle to providing WAN access that can approach LAN performance is bandwidth in the last mile, where the copper wiring infrastructure is generally not good. The projects to update this wiring to use fiber optic links are referred to by the umbrella term Fiber to the X (FTTx).

The most expensive solution is Fiber to the Premises (FTTP) or its residential variant Fiber to the Home (FTTH). The essential point about both these implementations is that the fiber link is terminated at the demarc. Other solutions can variously be described as Fiber to the Node (FTTN) or Fiber to the Curb (FTTC). These retain some sort of copper wiring to the demarc while extending the fiber link to a communications cabinet servicing multiple subscribers. The service providers with their roots in telephone networks use Very high-speed DSL (VDSL) to support FTTC. VDSL (G.993) achieves higher bit rates than other DSL types at the expense of range. It allows for both symmetric and asymmetric modes. Over 300 m (1000 feet), an asymmetric link supports 52 Mbps downstream and 6 Mbps upstream, while a symmetric link supports 26 Mbps in both directions. VDSL2 specifies a very short range (100 m/300 feet) rate of 100 Mbps (bi-directional).

The modem type must match the service. An ADSL-only modem cannot be used to access a VDSL service, for instance.

CABLE PROVIDER LINKS

A cable Internet connection is usually available along with Cable Access TV (CATV). These networks are sometimes described as hybrid fiber coax (HFC) because they combine a fiber optic core network with coax links to CPE, but are more simply just described as cable broadband.

A cable modem-The RJ-45 port connects to the local network, while the coax port connects to the service provider network. (Image © 123RF.com.)

Installation of a cable modem follows the same general principles as for a DSL modem. The cable modem is interfaced to a computer or router through an Ethernet or USB adapter and with the access provider's network by a short segment of coax. More coax then links all the premises in a street with a Cable Modem Termination System (CMTS), which routes data traffic via the fiber backbone to the ISP's Point of Presence (PoP) and from there to the Internet. Cable based on the Data Over Cable Service Interface Specification (DOCSIS) supports downlink speeds of up to 38 Mbps (North America) or 50 Mbps (Europe) and uplinks of up to 27 Mbps. DOCSIS version 3 allows the use of multiplexed channels to achieve higher bandwidth.

METRO-OPTICAL PROVIDER LINKS

Carrier Ethernet provisions point-to-point or point-to-multipoint Ethernet leased lines over wide area networks. Carrier Ethernet may also be also referred to as a metro-optical provider link. The term Metro Ethernet refers to Carrier Ethernet where the geographic scope is limited to a single city. Standards for Carrier Ethernet are developed by the MEF ( mef.net ). Carrier Ethernet can use different types of physical connectivity. Some examples include:

●	Ethernet over Fiber-Uses the IEEE 802.3 10GBASE-LR and 10GBASE-ER specifications.

●	Ethernet over Copper-Uses DSL variants such as single-pair high-speed DSL (SHDSL) and VDSL to overcome the usual distance limitations of copper Ethernet. This does not support anything like the same speeds as LAN Ethernet (more typically 2-10 Mbps), but multiple pairs can be aggregated for higher bandwidth.

On top of the physical connectivity method, there are multiple service categories for Carrier Ethernet. Two of these are E-line and E-LAN:

●	E-line-Establishes a point-to-point link between two sites. Multiple E-lines can be configured on a single Metro Ethernet interface, with each E-line representing a separate VLAN.

●	E-LAN-Establishes a mesh topology between multiple sites.

These services can be used by the customer to join multiple sites together or as a way of connecting their enterprise network to the Internet. From the customer’s perspective, Carrier Ethernet has many advantages. The fact that Carrier Ethernet is easily scalable affords businesses the flexibility to match the service to their changing demands. Also, the fact that the same Ethernet protocol and framing is used on the LAN and connectivity into the public network space can make the configuration of routers, Layer 3 switches, and firewalls simpler.

Full fiber connections are also being provisioned to residential and small business customers, though availability can often be limited to a few metropolitan areas. Rather than dedicated leased lines, these services are deployed as a passive optical network (PON). Packages are offered in tiers from 100 Mbps up to 1 Gbps.

In a PON, a single fiber cable is run from the nearest exchange to an optical line terminal (OLT) located in the street. This link uses dense wavelength division multiplexing (DWDM) to support a ratio of backhaul cable to subscribers of 1:64 or 1:128. From the OLT, splitters direct each subscriber’s wavelength frequency over a shorter length of fiber to an optical network unit (ONU) or optical network terminal (ONT) installed at the demarc. The ONU/ONT converts the optical signal to an electrical one. The ONU/ONT is connected to the customer’s router using a copper wire patch cord.

MICROWAVE SATELLITE

Satellite systems provide far bigger areas of coverage than can be achieved by using other technologies. The microwave dishes are aligned to orbital satellites that can either relay signals between sites directly or via another satellite. The widespread use of satellite television receivers allows for domestic Internet connectivity services over satellite connections. Satellite services for business are also expanding, especially in rural areas where DSL or cable services are unlikely to be available.

Satellite connections experience quite severe latency problems as the signal must travel over thousands of miles more than terrestrial connections, introducing a delay of four to five times what might be expected over a land link. For example, if you know that accessing a site in the US from Europe takes 200 ms over a land (undersea) link, accessing the same site over a satellite link could involve a 900 ms delay. This is an issue for real-time applications, such as videoconferencing, VoIP, and multiplayer gaming.

To create a satellite Internet connection, the ISP installs a satellite dish, referred to as a very small aperture terminal (VSAT), at the customer's premises and aligns it with the orbital satellite. The size of a VSAT ranges from 1.2 to 2.4 meters in diameter. The satellites are in geostationary orbit over the equator, so in the northern hemisphere the dish will be pointing south. The antenna is connected via coaxial cabling to a Digital Video Broadcast Satellite (DVB-S) modem.

Topic 16B: Compare and Contrast Remote Access Methods

REMOTE NETWORK ACCESS AUTHENTICATION AND AUTHORIZATION

Remote network access means that the user's device does not make a direct cabled or wireless connection to the network. The connection occurs over or through an intermediate network, usually a public WAN. Historically, remote network access might have used analog modems connecting over the telephone system. These days, most remote access is implemented as a virtual private network (VPN), running over the Internet.

Given that, administering remote access involves essentially the same tasks as administering the local network. Only authorized users who have successfully authenticated should be allowed access to local network resources and communication channels. Additional complexity comes about because it can be more difficult to ensure the security of remote workstations and servers and there is greater opportunity for remote logins to be exploited.

The creation of a remote access server (RAS) should be accompanied by documentation describing the uses of the service, security risks and countermeasures, and authorized users of the service. There should also be authorization to run the service from the network manager. The remote access policy should then implement the measures identified through compiling the documentation. Typical policy restrictions would be:

●	Restricting access to defined users or groups.

●	Restricting access to defined times of day or particular days of the week.

●	Restricting privileges on the local network (ideally, remote users would only be permitted access to a clearly defined part of the network).

●	Logging and auditing access logons and attempted logons.

In addition to this, a management plan should ensure that RASs and other hardware are kept up to date with the latest software or firmware updates. Administrative access to the devices should also be secured, using strong authentication.

TUNNELING AND ENCAPSULATION PROTOCOLS

Most modern remote network access solutions use Internet access infrastructure and set up a secure tunnel for private communications through the Internet. This is referred to as a virtual private network (VPN). Most business and residential sites have Internet connectivity, so this solution is very efficient in terms of cost. The main concerns are providing security for the transmissions that pass through the public network and preventing unauthorized users from making use of the VPN connection.

Point-to-Point Protocol

VPNs depend on tunneling protocols. Tunneling is used when the source and destination hosts are on the same logical network but connected via different physical networks. The Point-to-Point Protocol (PPP) is an encapsulation protocol that works at the Data Link layer (Layer 2). PPP is used to encapsulate IP packets for transmission over serial digital lines. PPP has no security mechanisms, so must be used with other protocols to provision a secure tunnel.

Generic Routing Encapsulation

Where PPP works at Layer 2, Generic Routing Encapsulation (GRE) works at Layer 3. A GRE packet can itself encapsulate an IP packet (or most other network layer protocol types) as its payload. The "outer" GRE packet is assigned protocol number 47 and has its own IP source and header address fields. The GRE packet is then itself encapsulated in a Layer 2 frame for transmission to the next hop router. Each intermediate router inspects only the outer GRE header to determine the forwarding destination. At the final destination, the receiving router de-encapsulates the GRE packet to extract the inner IP payload and forwards that inner packet to its destination. GRE does not have any mechanisms for authenticating users or devices and so is often used with other protocols in a VPN solution.

IP Security

Internet Protocol Security (IPSec) also operates at the network layer (Layer 3) of the OSI model to encrypt packets passing over any network. IPSec is often used with other protocols to provide connection security, but is increasingly used as a native VPN protocol.

Transport Layer Security

Transport Layer Security (TLS) over TCP or datagram TLS (DTLS) over UDP can be used to encapsulate frames or IP packets. The main drawback is that as TLS already operates at the session layer, the headers from the inner and outer packets add up to a significant overhead.

CLIENT-TO-SITE VIRTUAL PRIVATE NETWORKS

A VPN can be implemented in several topologies. In a client-to-site or remote access topology, the VPN client connects over the public network to a VPN gateway (a VPN-enabled router) positioned on the edge of the local network (typically the VPN access server will be in a screened subnet). Client-to-site is the "telecommuter" model, allowing home-workers and employees working in the field to connect to the corporate network.

Client-to-site VPNs can be configured using a number of protocols. An SSL/TLS VPN solution uses certificates to establish the secure tunnel. One example is Microsoft’s Secure Socket Tunneling Protocol (SSTP). Cisco’s Layer 2 Tunneling Protocol (L2TP) is also widely used, in conjunction with IPSec. All these solutions require client software to operate. Most VPN solutions use EAP and AAA/RADIUS architecture to authenticate client devices and users.

Microsoft’s Point-to-Point Tunneling Protocol (PPTP) was once very widely used but has too many security flaws to be deployed safely.

When a client connected to a remote access VPN tries to access other sites on the Internet, there are two ways to manage the connection:

●	Split tunnel-the client accesses the Internet directly using its "native" IP configuration and DNS servers.

Split tunnel VPN traffic flow. (Images © 123RF.com.)

●	Full tunnel-Internet access is mediated by the corporate network, which will alter the client's IP address and DNS servers and may use a proxy.

Full tunnel VPN traffic flow. (Images © 123RF.com.)

Full tunnel offers better security, but the network address translations and DNS operations required may cause problems with some websites, especially cloud services. It also means more data is channeled over the link and the connection can exhibit higher latency.

REMOTE HOST ACCESS AND REMOTE DESKTOP GATEWAYS

A remote access VPN refers to extending local network access over an intermediate public network, so that a remote computer is effectively joined to the local network. Remote access can also refer to remote host access, where a user operates a computer or configures a network appliance without having to use a local terminal. This type of remote host access can be implemented within a local network or over a public network. It can be used for a variety of purposes:

●	Remote configuration of network appliances. Most of these appliances are headless (they do not have a video monitor or input devices) and remote connections are the only practical configuration option. This type of connection is typically implemented using Secure Shell (SSH).

●	Remote desktop connections either allow an administrator to configure a server or a user to operate a computer remotely. Where remote desktop protocols provide GUI access, other protocols can be used for terminal-only access.

●	Remote desktop gateways allow user access to networked apps. A gateway can also be used to connect a user to a virtual desktop, where a client OS and applications software is provisioned as a virtual appliance. Alternatively, a remote desktop gateway is a means of implementing a clientless VPN.

Remote Desktop Protocol and Virtual Network Computing

Microsoft's Remote Desktop Protocol (RDP) can be used to access a physical machine on a one-to-one basis. Alternatively, the site can operate a remote desktop gateway that facilitates access to virtual desktops or individual apps running on the network servers (docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/welcome-to-rds). Similar services are provided by Citrix’s products (citrix.com/products).

There are several popular alternatives to Remote Desktop. Most support remote access to platforms other than Windows (macOS and iOS, Linux, Chrome OS, and Android for instance). Examples include TeamViewer (teamviewer.com/en) and Virtual Network Computing (VNC) , which is implemented by several different providers (notably realvnc.com/en).

Clientless VPNs

Traditionally, remote desktop products and client-to-site VPNs require a client app that implements the protocols and authentication methods supported by the remote desktop/VPN gateway. The canvas element introduced in HTML5 allows a browser to draw and update a desktop with relatively little lag. It can also handle audio. This allows ordinary browser software to connect to a remote desktop or VPN. This is referred to as an HTML5 VPN or clientless VPN ( guacamole.apache.org ). This solution also uses a protocol called WebSockets, which enables bidirectional messages to be sent between the server and client without requiring the overhead of separate HTTP requests.

SITE-TO-SITE VIRTUAL PRIVATE NETWORKS

A VPN can also be deployed in a site-to-site model to connect two or more private networks. Where remote access VPN connections are typically initiated by the client, a site-to-site VPN is configured to operate automatically. The gateways exchange security information using whichever protocol the VPN is based on. This establishes a trust relationship between the gateways and sets up a secure connection through which to tunnel data. Hosts at each site do not need to be configured with any information about the VPN. The routing infrastructure at each site determines whether to deliver traffic locally or send it over the VPN tunnel. This is also referred to as compulsory tunneling. Compulsory tunnels can be in place permanently (static), or they can be put in place based on the data or client type (dynamic).

Site-to-site VPN. (Images © 123rf.com.)

VPNs are not always established over the public Internet. A WAN service provider can implement VPNs via its network. The provider can use VLAN-like technology to isolate a customer's data from other traffic. This is a common model for site-to-site VPNs.

While VPNs are being covered here as part of remote access, they can be just as usefully deployed on local networks as a type of network segmentation. For example, the department for product development might need to provide secure communications with the marketing department.

HUB AND SPOKE VPNS AND VPN HEADENDS

A site-to-site VPN that involves more than two sites connects the remote sites (or spokes) to a headquarters site (hub) by using static tunnels configured between the hub and each spoke. This is referred to as a hub and spoke topology. The VPN router installed in the central office or hub needs to be a powerful machine capable of aggregating high traffic volumes. This VPN router is also referred to as a VPN headend. VPN headends would normally be installed in groups for load balancing and fault tolerance. A VPN headend must be able to scale to meet changing demand levels. The VPN routers installed at the spokes, are referred to as branch office routers.

A dynamic multipoint VPN (DMVPN) allows VPNs to be set up dynamically according to traffic requirements and demand. The original concept was developed by Cisco but has been adopted by other vendors and now runs on diverse router platforms. DMVPN allows for the use of a dynamic mesh topology between multiple remote sites, effectively setting up direct VPNs, rather than the remote sites having to route traffic via the hub. Each site can communicate with all other spokes directly no matter where they are located.

DMVPN topology. Each branch office establishes a permanent VPN with the HQ (hub) but can also create spoke-to-spoke VPNs dynamically. (Images © 123RF.com.)

To configure a DMVPN, each remote site's router is still connected to the hub router using an IPSec tunnel. As a large percentage of a remote site's traffic is likely to be with the main HQ, this ensures this normal traffic is dealt with efficiently. If two remote sites (spokes) wish to communicate with one another, the spoke instigating the link informs the hub. The hub will provide the connection details for the other spoke facilitating a dynamic IPSec tunnel to be created directly between the two spokes. This process invokes the use of the Next Hop Router Protocol (NHRP) to identify destination addresses and the GRE tunneling. GRE encapsulates the encrypted IPSec packets. The two remote sites use the physical communications links between the two locations but all traffic flows over the temporary, encrypted VPN tunnel setup between them. DMVPN will then decide how long this temporary VPN remains in place based on timers and traffic flows.

In this way, DMVPN allows remote sites to connect with each other over the public WAN or Internet, such as when using video conferencing, but doesn't require a static VPN connection between sites. This on-demand deployment of IPSec VPNs is more efficient. Routing policies can be used to select the most reliable path between the remote sites, which potentially reduces the chance of latency and jitter affecting any voice/video services running over the VPN.

INTERNET PROTOCOL SECURITY

Internet Protocol Security (IPSec) can be used to secure IPv4 and/or IPv6 communications on local networks and as a remote access protocol.

Each host that uses IPSec must be assigned a policy. An IPSec policy sets the authentication mechanism and also the protocols and mode for the connection. Hosts must be able to match at least one matching security method for a connection to be established. There are two core protocols in IPSec, which can be applied singly or together, depending on the policy.

Authentication Header

The Authentication Header (AH) protocol performs a cryptographic hash on the whole packet, including the IP header, plus a shared secret key (known only to the communicating hosts), and adds this secret in its header as an Integrity Check Value (ICV). The recipient performs the same function on the packet and key and should derive the same value to confirm that the packet has not been modified. The payload is not encrypted so this protocol does not provide confidentiality. Also, the inclusion of IP header fields in the ICV means that the check will fail across NAT gateways, where the IP address is rewritten. Consequently, AH is not often used.

IPSec datagram using AH-The integrity of the payload and IP header is ensured by the Integrity Check Value (ICV), but the payload is not encrypted.

Encapsulating Security Payload (ESP) provides confidentiality and/or authentication and integrity. It can be used to encrypt the packet rather than simply calculating a hash. ESP attaches three fields to the packet: a header, a trailer (providing padding for the cryptographic function), and an Integrity Check Value. Unlike AH, ESP excludes the IP header when calculating the ICV.

IPSec datagram using ESP-The TCP header and payload from the original packet is encapsulated within ESP and encrypted to provide confidentiality.

With ESP, algorithms for both confidentiality (symmetric cipher) and authentication/integrity (hash function) are usually applied together. It is possible to use one or the other, however.

The principles underlying IPSec are the same for IPv4 and IPv6, but the header formats are different. IPSec makes use of extension headers in IPv6 while in IPv4, ESP and AH are allocated new IP protocol numbers (50 and 51), and either modify the original IP header or encapsulate the original packet, depending on whether transport or tunnel mode is used.

IKE AND IPSEC MODES

IPSec's encryption and hashing functions depend on a shared secret. The secret must be communicated to both hosts and the hosts must confirm one another's identity (mutual authentication). The Internet Key Exchange (IKE) protocol handles authentication and key exchange, referred to as Security Associations (SA).

Configuring IKE in the OPNsense security appliance. (Screenshot used with permission from OPNsense.)

IPSec can be used in two modes:

●	Transport mode-this mode is used to secure communications between hosts on a private network (an end-to-end implementation). When ESP is applied in transport mode, the IP header for each packet is not encrypted, just the payload data. If AH is used in transport mode, it can provide integrity for the IP header.

●	Tunnel mode-this mode is used for communications between VPN gateways across an unsecure network (creating a VPN). This is also referred to as a router implementation. With ESP, the whole IP packet (header and payload) is encrypted and encapsulated as a datagram with a new IP header. AH has no real use case in tunnel mode, as confidentiality will usually be required.

Configuring an IPSec tunnel in the OPNsense security appliance. (Screenshot used with permission from OPNsense.)

OUT-OF-BAND MANAGEMENT METHODS

Some network appliances, such as unmanaged switches, do not offer any configuration options or interface. You just have to plug them in, and they operate automatically. Managed switches and appliances, such as routers, firewalls, switches, and access points, support more complex functions and can be configured and monitored over several interfaces. The functions of a managed appliance can be accessed via one of the device's management interfaces. An appliance may support the following interfaces:

●	Console Port-This requires connecting a device running terminal emulator software (a laptop, for instance) to the device via a separate physical interface using a special console (or rollover) cable. The terminal emulator can then be used to start a command line interface (CLI).

●	AUX port-This port is designed to connect to an analog modem and provide remote access over a dial-up link. Once the AUX port is enabled and configured, the modem can be connected to it by using an RS-232 serial cable, a specially wired RJ-45 rollover cable and terminal adapter (RJ-45 to DB9), or a management cable (RJ-45 to DB9). Configure the modem with appropriate serial link settings (refer to the vendor guide), connect it to an appropriate telephone line, and allocate an extension number. A remote host can connect to the appliance CLI by using a terminal emulation program such as HyperTerminal or PuTTY.

●	Management port-This means configuring a virtual network interface and IP address on the device to use for management functions and connecting to it via one of the normal Ethernet ports. The port must be enabled for this function (some appliances come with a dedicated management port). Using Telnet (unsecure) or Secure Shell (SSH) to connect to a CLI remotely over the management interface in this way is referred to as a virtual terminal.

USB and RJ-45 type console ports plus AUX and other management interfaces on a router. (Image © 123RF.com.)

Management methods can be described as either in-band or out-of-band (OOB). An in-band management link is one that shares traffic with other communications on the "production" network. The console port is a physically out-of-band management method; the link is limited to the attached device. When you are using a browser-based management interface or a virtual terminal, the link can be made out-of-band by connecting the port used for management access to physically separate network infrastructure. Obviously, this is costly to implement, but out-of-band management is more secure and means that access to the device is preserved when there are problems affecting the production network.

With an in-band connection, better security can be implemented by using a VLAN to isolate management traffic. This makes it harder for potential eavesdroppers to view or modify traffic passing over the management interface. This sort of virtual OOB does still mean that access could be compromised by a system-wide network failure, however.

Use a secure connection protocol (HTTPS rather than HTTP, or SSH rather than Telnet) for the management interface. This applies to OOB too, but it is critical for in-band management.































Lesson 17: Explaining Organizational and Physical Security Concepts

Topic 17A: Explain Organizational Documentation and Policies

OPERATING PLANS AND PROCEDURES

Running an efficient network is not just about installing cabling and network devices. The administration of the network in terms of documentation and management is a critical task.

Configuration Management

Configuration management means identifying and documenting all the infrastructure and devices installed at a site. ITIL® is a popular documentation of good and best practice activities and processes for delivering IT services. Under ITIL, configuration management is implemented using the following elements:

●	Service assets are things, processes, or people that contribute to the delivery of an IT service. Each asset must be identified by some sort of label.

●	A Configuration Item (CI) is an asset that requires specific management procedures for it to be used to deliver the service. CIs are defined by their attributes.

●	A baseline documents the approved or authorized state of a CI. This allows auditing processes to detect unexpected or unauthorized change. A baseline can be a configuration baseline (the ACL applied to a firewall, for instance) or a performance baseline (such as the throughput achieved by the firewall).

●	A Configuration Management System (CMS) is the tools and databases that collect, store, manage, update, and present information about CIs. A small network might capture this information in spreadsheets and diagrams; there are dedicated applications for enterprise CMS.

Change Management

A documented change management process minimizes the risk of unscheduled downtime by implementing changes in a planned and controlled way. The need to change is often described either as reactive, where the change is forced on the organization, or as proactive, where the need for change is initiated internally. Changes can also be categorized according to their potential impact and level of risk (major, significant, minor, or normal, for instance).

In a formal change management process, the need or reasons for change and the procedure for implementing the change is captured in a Request for Change (RFC) document and submitted for approval. The RFC will then be considered at the appropriate level and affected stakeholders will be notified. Major or significant changes might be managed as a separate project and require approval through a Change Advisory Board (CAB).

Standard Operating Procedures

Configuration changes should be made only when there is a valid job ticket authorizing the change. This means that the activity of all network personnel, whether it be installing new devices or troubleshooting, is recorded in job logs. In a fully documented environment, each task will be governed by a standard operating procedure (SOP). A SOP sets out the principal goals and considerations, such as budget, security, or customer contact standards, for performing a task and identifies lines of responsibility and authorization for performing it. A SOP may also contain detailed steps for completing a task in an approved way, or these steps may be presented as work instructions.

SYSTEM LIFE CYCLE PLANS AND PROCEDURES

It is crucial for an organization to have an inventory of its tangible and intangible assets. In terms of network management, assets are network appliances (routers, switches, threat management devices, access points), servers, workstations, and passive network infrastructure (cabling and cross-connects).

Audit Reports

An audit report focuses on identifying and recording assets. There are many software suites and associated hardware solutions available to assist with audit tracking and managing inventory. An asset management database can be configured to store as much or as little information as is deemed necessary, though typical data would be type, model, serial number, asset ID, location, user(s), value, and service information. For each asset record, there should also be a copy of or link to the appropriate vendor documentation. This includes both an invoice and warranty/support contract and support and troubleshooting guidance.

A product such as Lansweeper assists inventory management by scanning network hosts and compiling an asset information database automatically. (Screenshot used with permission from Lansweeper.)

Assessment Reports

Where an audit report focuses on identifying and documenting assets, an assessment report evaluates the configuration and deployment of those assets, such as deviation from baseline configuration or performance. The report will make recommendations where the network is not meeting goals for performance or security. Audit and assessment reports are often contracted to third parties and might be driven by regulatory or compliance demands.

System Life Cycle

One of the functions of auditing and assessment is to manage system life cycle. A system life cycle roadmap refers to the controlled acquisition, deployment, use, and decommissioning of assets. An audit and assessment report can identify assets that are no longer fully supported by the vendor or that otherwise no longer meet performance or security requirements.

PHYSICAL NETWORK DIAGRAMS

Asset and configuration item (CI) documentation makes significant use of diagrams. A diagram is the best way to capture the complex relationships between network elements. It is important not to try to include too much information as this tends to make the diagram too complex to be useful. Consequently, a large number of diagram types are used in network management. One basic distinction is between physical and logical network diagrams. Within the class of physical network diagrams, the following types are commonly used.

Floor Plan

A floor plan is a detailed diagram of wiring and port locations. For example, you might use floor plans to document wall port locations and cable runs in an office. Physically accurate floor plans are hard to design and are likely to require the help of an architect or graphics professional.

Wiring Diagram

A wiring diagram (or pin-out) shows detailed information about the termination of twisted pairs in an RJ-45 or RJ-48C jack or Insulation Displacement Connector (IDC). You might also use a wiring diagram to document how fiber-optic strands are terminated.

You should document the wiring diagrams used to terminate twisted pairs. Ethernet is wired by T568A or T568B, and the same standard should be used consistently throughout the network.

Distribution Frame

A port location diagram identifies how wall ports located in work areas are connected back to ports in a distribution frame or patch panel and then from the patch panel ports to the switch ports. Within a structured cabling system, there are two types of distribution frame:

●	Main Distribution Frame (MDF)-The location for distribution/core level internal switching. The MDF will terminate trunk links from multiple Intermediate Distribution Frames (IDFs). The MDF also serves as the location for termination of external (WAN) circuits. You should ensure that WAN links to the Internet or to remote offices from the MDF are clearly labeled and that key information such as IP addresses and bandwidth is documented. The WAN provider will assign a circuit ID, and you will need to quote this if raising any sort of support issue.

●	Intermediate Distribution Frame (IDF)-In a large network, one or more IDFs provides termination for access layer switches that serve a given area, such as a single office floor. Each IDF has a trunk link to the MDF. Make sure that these are clearly labeled and distinct from access ports.

In addition to having a diagram, it can be very useful to take a photo of the current configuration by using a digital camera or smartphone. This provides an additional visual reference for troubleshooting and identifying unauthorized changes.

In order for a physical diagram of cabling and assets to make any sense, there must be a system of labeling in place for identifying these assets. A typical type of port naming convention is for alphanumeric identifiers for the campus (for multicampus networks), building (for campus networks), telecommunications space, and port. For example, CB01-01A-D01 could refer to a cable terminating at Main Campus Building (CB01), telecommunications space A on floor 1 (01A), data port 1 (D01). Structured cable and patch cords should be labeled at both ends to fully identify the circuit.

Site Survey Report

A wireless site survey report overlays a floor plan with graphics showing signal strength and channel utilization at different points in the building.

RACK DIAGRAMS

A rack system is a specially configured steel shelving system for patch panels, switches and routers, and server devices. Racks are standard widths and can fit appliances using standard height multiples of 1.75" called units (U). For example, a basic switch might be 1U while a server might be 4U (7") in height.

A rack diagram records the position of each appliance in the rack. You can obtain stencils that represent vendor equipment from their websites or a collection such as visiocafe.com. You can record key configuration information for each item using labels. As well as service tags and port IDs and links, you should identify which power outlets on the uninterruptible power supply (UPS) connect to which appliance power supply units (PSU)s.

Designing rack layout in Microsoft Visio. (Screenshot used with permission from Microsoft.)

LOGICAL VERSUS PHYSICAL NETWORK DIAGRAMS

In contrast to diagrams such as floor plans that are drawn to an accurate scale, a schematic is a simplified or abstracted representation of a system. In terms of the physical network topology, a schematic diagram can show the general placement of equipment and telecommunications rooms, plus device and port IDs, without trying to capture the exact position or relative size of any one element. Schematics can also be used to represent the logical structure of the network in terms of zones and subnets.

When you make network schematics, resist the urge to represent too much in a single diagram. For example, create separate diagrams for the PHY, Data Link, and Logical (IP) layers. Some of the information appropriate to show at each layer includes:

●	PHY (Physical layer)-Asset IDs and cable links. You can use color-coding or line styles to represent the cable type (make sure the diagram has an accompanying legend to explain your scheme).

●	Data Link (Layer 2)-Shows interconnections between switches and routers, with asset IDs (or the management IP of the appliance), interface IDs, and link-layer protocol and bandwidth. You could use line thickness to represent bandwidth, but for clarity it is a good idea to use labels as well.

●	Logical (IP/Layer 3)-IP addresses of router interfaces (plus any other static IP assignments) and firewalls, plus links showing the IP network ID and netmask, VLAN ID (if used), and DHCP scopes.

●	Application-Server instances and TCP/UDP ports in use. You might also include configuration information and performance baselines (CPU, memory, storage, and network utilization) at this level.

Schematics can either be drawn manually using a tool such as Microsoft® Visio® or compiled automatically from network mapping software.

Schematics can use either representative icons or pictures or drawings of actual product models. As far as icons go, the ones created by Cisco are recognized as standards. These are freely available (without alteration) from Cisco's website (cisco.com/c/en/us/about/brand-center/network-topology-icons.html). Some of the more commonly used devices are shown here:

Common Cisco network icons. (Images © and Courtesy of Cisco Systems, Inc. Unauthorized use not permitted.)

SECURITY RESPONSE PLANS AND PROCEDURES

Security response plans and procedures establish what to do when certain types of events occur. These plans attempt to anticipate adverse events so that impacts can be minimized.

Incident Response Plan

An incident response plan sets out the procedures, tools, methods of communication, and guidelines for dealing with security incidents. An incident is where security is breached or there is an attempted breach. Incident response is one of the most difficult areas of security to plan for and implement because its aims can be incompatible:

1. `	`The immediate aim is usually to protect confidential data or minimize impacts from its loss and re-establish a secure working system.
1. `	`It may also be important to preserve evidence of the incident with the aim of prosecuting the perpetrators. Forensic evidence collection can interfere with re-establishing availability, however.
1. `	`Follow-up or lessons learned analysis will attempt to prevent reoccurrence of similar incidents.

The actions of first responders immediately following detection of an incident can have a critical impact on these aims, so an effective policy and well-trained incident response professionals are crucial. Incident response is also likely to require coordinated action and authorization from several different departments or managers, which adds further levels of complexity.

Disaster Recovery Plan

Where incident response is focused on individual security policy violations, a disaster recovery plan (DRP) addresses large-scale incidents. These will typically be incidents that threaten the performance or security of a whole site. A DRP should accomplish the following:

●	Identify scenarios for natural and non-natural disasters and options for protecting systems.

●	Identify tasks, resources, and responsibilities for responding to a disaster. Disaster recovery focuses on tasks such as switching services to failover systems or sites and restoring systems and data from backups.

●	Train staff in the disaster planning procedures and how to react well to adverse events.

Business Continuity Plan

Where disaster recovery focuses on plans for specific scenarios, a business continuity plan (BCP) or continuity of operations plan (COOP) is a collection of processes and resources that enable an organization to maintain normal business operations in the face of some adverse event. Continuity planning activity focuses on the functions performed by a business or other organization:

●	Business impact analysis (BIA) identifies mission essential and primary business functions and the risks that would arise if the organization cannot fulfill them.

●	IT contingency planning (ITCP) or IT service continuity planning (ITSCP) ensures that these functions are supported by resilient IT systems, working to identify and mitigate all single points of failure from a process or function.

HARDENING AND SECURITY POLICIES

Security policy establishes a duty for each employee to ensure the confidentiality, integrity, and availability of any data assets or processing systems that they use as part of their job. This overall security policy will be supplemented by numerous operational policies to govern specific areas of activity or configuration.

Human Resources (HR) is the department given the task of recruiting and managing the organization's most valuable and critical resource: people. One function of HR is to communicate security policies to employees, including any updates to the policies. Another function is to enforce disciplinary measures (perhaps in conjunction with departmental managers).

Onboarding

Onboarding is the process of welcoming a new employee to the organization. Similar principles apply to taking on new suppliers or contractors. Some of the tasks that most affect security during the onboarding process are as follows:

●	Background check-This process essentially determines that a person is who they say they are and are not concealing criminal activity, bankruptcy, or connections that would make them unsuitable or risky. Employees working in high confidentiality environments or with access to high value transactions will obviously need to be subjected to a greater degree of scrutiny.

●	Identity and access management (IAM)-Create an account for the user to access the computer system, assign the appropriate privileges, and ensure the account credentials are known only to the valid user.

●	Asset allocation-Provision computers or mobile devices for the user or agree on the use of BYOD devices.

●	Training/policies-Schedule appropriate security awareness and role-relevant training and certification.

Offboarding

Offboarding is the process of ensuring that an employee leaves a company gracefully. In terms of security, there are several processes that must be completed:

●	IAM-Disable the user account and privileges. Ensure that any information assets created or managed by the employee but owned by the company are accessible (in terms of encryption keys or password-protected files).

●	Retrieving company assets-Secure mobile devices, keys, smart cards, USB media, and so on. The employee will need to confirm (and in some cases prove) that they have not retained copies of any information assets.

●	Returning personal assets-Employee-owned devices need to be wiped of corporate data and applications. The employee may also be allowed to retain some information assets (such as personal emails or contact information), depending on the policies in force.

The departure of some types of employees should trigger additional processes to resecure network systems. Examples include employees with detailed knowledge of security systems and procedures and access to shared or generic account credentials. These credentials must be changed immediately.

USAGE POLICIES

Usage policies set out rules for how users should interact with network systems and data.

Password Policy

A password policy instructs users on best practice in choosing and maintaining a network access credential. Password protection policies mitigate against the risk of attackers being able to compromise an account and use it to launch other attacks on the network. For example, users must be instructed not to write down passwords, store them in unsecure files, or share them with other users. The credential management policy also needs to alert users to different types of social engineering and phishing attacks.

System-enforced policies can help to enforce credential management principles by stipulating requirements for user-selected passwords. The following rules enforce password complexity and make them difficult to guess or compromise:

●	Length-The longer a password, the stronger it is. A typical strong network password should be 12 to 16 characters. A longer password or passphrase might be used for mission critical systems or devices where logon is infrequent.

●	Complexity-Varying the characters in the password makes it more resistant to dictionary-based attacks.

●	Aging and history-Requiring that the password be changed periodically and preventing the reuse of previously selected passwords.

You should also note that recent guidance issued by NIST (nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63b.pdf) deprecates some of the "traditional" elements of password policy, such as complexity and aging.

Acceptable Use Policies

An acceptable use policy (AUP) sets out the permitted uses of a product or service. It might also state explicitly prohibited uses. Such a policy might be used in different contexts. For example, an AUP could be enforced by a business to govern how employees use equipment and services, such as telephone or Internet access, provided to them at work. Another example might be an ISP enforcing a fair use policy governing usage of its Internet access services.

BYOD Policies

A mobile deployment model describes the way employees are provided with smartphone or tablet devices and applications. Some companies issue employees with corporate-owned and controlled devices and insist that only these are used to process company data. Other companies might operate a bring your own device (BYOD) policy. BYOD means that the mobile is owned by the employee and can be used on the corporate network so long as it meets a minimum specification required by the company (in terms of OS version and functionality). The employee will have to agree on the installation of corporate apps and to some level of oversight and auditing. Very often, BYOD devices are registered with enterprise management software and configured with sandboxed corporate workspaces and apps.

Enterprise management software can be used to segment corporate data from personal data on BYOD devices. (Screenshot used with permission from Google.)

DATA LOSS PREVENTION

The theft or loss of confidential and/or personal information is referred to as a data breach. Data breach can expose an organization to huge reputational and financial costs. Consequently, data handling is an area of activity that should be tightly managed by both policies and technical controls.

Data loss prevention (DLP) products scan content in structured formats (such as a database with a formal access control model) or unstructured formats, such as email or word processing documents. DLP products use some sort of dictionary database or algorithm (regular expression matching) to identify confidential or personal/sensitive data. The transfer of content to removable media or by email or to social networking or cloud storage services can then be blocked if it does not conform to a predefined policy.

Creating a data loss prevention policy in Office 365. (Screenshot used with permission from Microsoft.)

REMOTE ACCESS POLICIES

Where employees are assigned the right to connect to the corporate network from a remote location using a VPN, their use of remote access privileges must be governed by technical and policy controls. Some of the issues that must be mitigated include the following:

●	Malware protection-The computer may not be accessible to network systems used to update and enforce malware protection. This may have to be left to the end-user. If a worm or Trojan is installed, network security may be compromised.

●	Security information-Authentication information may be stored on the client (saving a password, for instance), making the network vulnerable if the computer is stolen.

●	Data transfer-Files copied to the client may no longer be properly secured, raising the potential that confidential information could be stolen along with the device.

●	Local privileges-The user of a remote computer might be configured with administrative privileges but have no understanding of how such privileges can be exploited or misused. They might install unauthorized software on the machine or make it more vulnerable to malware by browsing the web using their administrative account.

●	Weak authentication-Relying on a username and password combination is simply not secure enough in a remote access scenario. Two-factor authentication using smart cards or biometric recognition in addition to a PIN or password should be enforced. If this is not an option, a strong password policy must be enforced, and users made aware of the very real risks of writing down or sharing their password.

●	Untrusted networks-The user might configure weak authentication on a home wireless network or use a public access point, raising the risk of snooping attacks.

The principal solution to remote access security problems is to educate remote users about security risks and their responsibilities. Enforcement can be provided by having remote devices audited periodically to ensure that antivirus, firewall, and OS/browser/application patches are being kept up to date and to check that unlicensed software has not been installed. It is also wise to limit what remote users can access on the local network and to severely restrict the rights of remote computer accounts. The principle of least privilege should be applied.

COMMON AGREEMENTS

Agreements are used between a company and its employees and between companies to enforce performance and security objectives.

Service Level Agreement Requirements

A service level agreement (SLA) is a contractual agreement setting out the detailed terms under which an ongoing service is provided. This can be a legally binding formal contract between supplier and customer businesses or a less formal agreement, such as an SLA agreed between internal departments. SLA requirements define aspects of the service, such as scope, performance characteristics, and responsibilities that are agreed upon between the service provider and the customer.

Depending on the nature of your organization's business, you may be responsible for maintaining SLA requirements agreed with your customers, use SLAs to guarantee service standards from your suppliers, or both.

Non-Disclosure Agreement

A non-disclosure agreement (NDA) is the legal basis for protecting information assets. It defines what uses of sensitive data are permitted, what storage and distribution restrictions must be enforced, and what penalties breaches of the agreement will incur. A contract of employment is highly likely to contain NDA clauses. NDAs are also used between companies and contractors and between two companies.

Memorandum of Understanding

A memorandum of understanding (MOU) is a preliminary or exploratory agreement to express an intent to work together. MOUs are usually intended to be relatively informal and not to act as binding contracts. MOUs almost always have clauses stating that the parties shall respect confidentiality, however.


Topic 17B: Explain Physical Security Methods

BADGES AND SITE SECURE ENTRY SYSTEMS

Prevention-type physical controls are ones that stop an intruder from gaining unauthorized access, if they work effectively. Where an area is controlled by being enclosed by walls or fencing, access is channeled through defined points of entry, such as doors and gates. These entry points can be protected by types of electronic lock.

Access Control Hardware

Various types of access control hardware or electronic locks can be deployed to enable users to authenticate quickly at access points:

●	Badge reader-A photographic ID badge showing name and access level is one of the cornerstones of building security. A smart badge comes with an integrated chip and data interface that stores the user’s key pair and digital certificate. The user presents the card and enters a PIN and then the card uses its cryptographic keys to authenticate securely via the entry point’s badge reader. A smart badge is either contact based, meaning that it must be physically inserted into a reader, or contactless, meaning that data is transferred using a tiny antenna embedded in the card. The ISO has published various ID card standards to promote interoperability, including ones for smart cards (ISO 7816 for contact and ISO 14443 for contactless types).

●	Biometric-An electronic lock may also be integrated with a biometric scanner. A biometric device is activated by human physical features, such as a fingerprint, voice, retina, or signature. Each user’s biometric is recorded as a template and stored on an authentication server. To gain access, the user’s biometric is scanned again by a fingerprint reader or iris/retina scanner and compared to the template scan.

Two types of electronic lock with biometric reader (left) and badge/card reader (right). (Images © 123RF.com.)

Access Control Vestibule

The main problem with a simple door or gate as an entry mechanism is that it cannot accurately record who has entered or left an area. More than one person may pass through the gateway at the same time; a user may hold a door open for the next person; an unauthorized user may "tailgate" behind an authorized user. This risk may be mitigated by installing a turnstile (a type of gateway that only allows one person through at a time). The other option is to add some sort of surveillance on the gateway. Where security is critical and cost is no object, an access control vestibule, or mantrap, could be employed. An access control vestibule is where one gateway leads to an enclosed space protected by another barrier.

PHYSICAL SECURITY FOR SERVER SYSTEMS

The access control hardware measures that can be deployed to prevent unauthorized entry to sites, buildings, and floors or zones within a building can also be used to manage access to IT assets.

Locking Racks

Installing equipment within secure cabinets/enclosures provides mitigation against insider attack and attacks that have broken through the perimeter security mechanisms. These can be supplied with key-operated or electronic locks. It is also possible to provision lockable brackets and drawers to protect or isolate individual elements within a rack.

Some datacenters may contain racks with equipment owned by different companies (colocation). These racks can be installed inside cages so that technicians can only physically access the racks housing their own company's servers and appliances.

Colocation cages. (Image © Chris Dag and shared with CC BY 2.0 flickr.com/photos/chrisdag/

865711871\.)

Locking Cabinets

Lockable cabinets or safes can provide secure storage for individual items, such as media with cryptographic keys or shared password lists.

Smart Lockers

A smart locker is a cabinet that supports unlocking via a smart card/badge or biometric. Lockers may also have built-in monitoring and surveillance that can alert an administrator when an item is added ore removed.

DETECTION-BASED DEVICES

Detection-based controls provide an important additional layer of defense in the event that prevention-based controls fail to work. For example, surveillance is another layer of security designed to improve the resilience of perimeter gateways. Effective surveillance mechanisms ensure that attempts to penetrate a barricade are detected. Surveillance may be focused on perimeter areas or within security zones themselves. Surveillance can be performed by security guards or via video. Camera-based surveillance is a cheaper means of monitoring than maintaining separate guards at each gateway or zone.

Cameras

A security camera is either fixed or can be operated using Pan-Tilt-Zoom (PTZ) controls. Different cameras suit different purposes. If you want to record the image of every person entering through an access control vestibule, a fixed, narrow focal length camera positioned on the doorway will be perfectly adequate. If you want to survey a large room and pick out individual faces, a camera with PTZ is required.

Pan-tilt-zoom CCTV installed to monitor a server room. (Image by Dario Lo Presti © 123RF.com.)

The cameras in a Closed-Circuit Television (CCTV) network are typically connected to a multiplexer using coaxial cabling. The multiplexer can then display images from the cameras on one or more screens, allow the operator to control camera functions, and record the images to tape or hard drive. Newer camera systems may be linked in an IP network, using regular data cabling. Small IP cameras can use Power over Ethernet (PoE), avoiding the need to provision a separate power circuit.

Asset Tags

An asset tag shows the ID of a device or component and links it to an inventory management database. Radio Frequency ID (RFID) asset tracking tags allow electronic surveillance of managed assets. The tags can be detected at entry/exit points to prevent theft. A battery-powered component might be in the tag, or the tag might be passive and read and scanned by a powered device. The tags are entered into a tracking database, which also usually has a map of the coverage area so that a particular asset can be located.

ALARMS AND TAMPER DETECTION

Alarms provide a detection-based security mechanism, though an audible alarm can also be an effective deterrent by causing the attacker to abandon the intrusion attempt. There are two main types:

●	Circuit-A circuit-based alarm sounds when the circuit is opened or closed, depending on the type of alarm. This could be caused by a door or window opening or by a fence being cut. A closed-circuit alarm is more secure because an open circuit alarm can be defeated by cutting the circuit. This type of system can be used for tamper detection.

●	Motion detection-A motion-based alarm is linked to a detector triggered by any movement within a relatively large area, such as a room. The sensors in these detectors are either microwave radio reflection (similar to radar) or passive infrared (PIR), which detect moving heat sources.

As well as protecting building areas, alarms can be installed on rack systems and appliance chassis. For example, a chassis intrusion alarm can alert an administrator if a server case is opened.

Another potential threat is that an attacker could splice a tap into network data cable. A physically secure cabled network is referred to as a Protected Distribution System (PDS). A hardened PDS is one where all cabling is routed through sealed metal conduit and subject to periodic visual inspection. Lower grade options are to use different materials for the conduit (plastic, for instance). Tamper detection alarm systems can be implemented within the cable conduit.

ASSET DISPOSAL

Physical security controls also need to take account of the disposal phase of the system life cycle. When a server or appliance is disposed of by resale, gift, or recycling, there is a risk that software licenses could be misused or that configuration information valuable to an attacker could be leaked. These risks can be mitigated by ensuring that the built-in factory reset routine is invoked to wipe any custom configuration settings or modifications when decommissioning a server, switch, router, firewall, or printer.

A factory reset may leave data remnants, however. Data remnant removal is critical because an organization's confidential data or personal/sensitive data held could be compromised.

Data remnant removal refers to ensuring that no data is recoverable from hard disk drives (HDDs), flash devices or solid state drives (SSDs), tape media, CD and DVD ROMs before they are disposed of or put to a different use. Paper documents must also be disposed of securely. Data remnants can be dealt with either by destroying the media or by sanitizing it (removing the confidential information but leaving the media intact for reuse).

Methods of destroying media include incineration, pulverization, and degaussing (for magnetic media such as hard drives).

Media sanitization refers to erasing data from HDD, SSD, and tape media before they are disposed of or put to a different use. The standard method of sanitizing an HDD is called overwriting. This can be performed using the drive's firmware tools or a utility program. The basic type of overwriting is called zero filling, which just sets each bit to zero. Single- pass zero filling can leave patterns that can be read with specialist tools. A more secure method is to overwrite the content with one pass of all zeros, then a pass of all ones, and then one or more additional passes in a pseudorandom pattern.

Secure Erase

Since 2001, the SATA and Serial Attached SCSI (SAS) specifications have included a Secure Erase (SE) command. This command can be invoked using a drive/array utility or the hdparm Linux utility. On HDDs, this performs a single pass of zero-filling.

For SSDs and hybrid drives and some USB thumb drives and flash memory cards, overwriting methods are not reliable, because the device uses wear-leveling routines in the drive controller to communicate which locations are available for use to any software process accessing the device. On SSDs, the SE command marks all blocks as empty. A block is the smallest unit on flash media that can be given an erase command. The drive firmware's automatic garbage collectors then perform the actual erase of each block over time. If this process is not completed (and there is no progress indicator), there is a risk of remnant recovery, though this requires removing the chips from the device to analyze them in specialist hardware.

Instant Secure Erase

HDDs and SSDs that are self-encrypting drives (SEDs) support another option, invoking a SANITIZE command set in SATA and SAS standards from 2012 to perform a crypto erase. Drive vendors implement this as Instant Secure Erase (ISE). With an SED, all data on the drive is encrypted using a media encryption key. When the erase command is issued, the MEK is erased, rendering the data unrecoverable.

EMPLOYEE TRAINING

Employee training is another type of prevention-based security control. Untrained users represent a serious vulnerability because they are susceptible to social engineering and malware attacks and may be careless when handling sensitive or confidential data or allowing access to premises.

Train users in secure behavior. (Image by dotshock © 123RF.com.)

Appropriate security awareness training needs to be delivered to employees at all levels, including end users, technical staff, and executives. Some of the general topics that need to be covered include the following:

●	Overview of the organization's security policies and the penalties for non-compliance.

●	Incident identification and reporting procedures.

●	Site security procedures, restrictions, and advice, including safety drills, escorting guests, use of secure areas, and use of personal devices.

●	Data handling, including document confidentiality, PII, backup, encryption, and so on.

●	Password and account management plus security features of PCs and mobile devices.

●	Awareness of social engineering and malware threats, including phishing, website exploits, and spam plus alerting methods for new threats.

●	Secure use of software such as browsers and email clients plus appropriate use of Internet access, including social networking sites.

There should also be a system for identifying staff performing security-sensitive roles and grading the level of training and education required (between beginner, intermediate, and advanced, for instance). Note that in defining such training programs you need to focus on job roles, rather than job titles, as employees may perform different roles and have different security training, education, or awareness requirements in each role.

Topic 17C: Compare and Contrast Internet of Things Devices

INTERNET OF THINGS

The term Internet of Things (IoT) is used to describe the global network of personal devices, home appliances, home control systems, vehicles, and other items that have been equipped with sensors, software, and network connectivity. These features allow these types of objects to communicate and pass data between themselves and other traditional systems like computer servers. This is often referred to as Machine to Machine (M2M) communication.

Consumer-grade Smart Devices

Smart devices are used to implement home automation systems. An IoT smart device network will generally use the following types of components:

●	Hub/control system-IoT devices usually require a communications hub to facilitate wireless networking. There must also be a control system, as most IoT devices are headless, meaning they have no user control interface. A headless hub could be implemented as a smart speaker operated by voice control or use smartphone/PC app for configuration.

●	Smart devices-IoT endpoints implement the function, such as a smart lightbulb, refrigerator, thermostat/heating control, or doorbell/video entry phone that you can operate remotely. These devices are capable of compute, storage, and network functions that are all potentially vulnerable to exploits. Most smart devices use a Linux or Android kernel. Because they're effectively running mini-computers, smart devices are vulnerable to some of the standard attacks associated with web applications and network functions. Integrated peripherals such as cameras or microphones could be compromised to facilitate surveillance.

Physical Access Control Systems and Smart Buildings

A physical access control system (PACS) is a network of monitored locks, intruder alarms, and video surveillance cameras. A building automation system (BAS) or smart building for offices and datacenters can include PACS, but also network-based configuration and monitoring of heating, ventilation, and air conditioning (HVAC), fire control, power and lighting, and elevators and escalators. These subsystems are implemented by programmable logic controllers (PLCs) and various types of sensors that measure temperature, air pressure, humidity, room occupancy, and so on.

INDUSTRIAL CONTROL SYSTEMS/SUPERVISORY CONTROL AND DATA ACQUISITION

Internet of Things and other embedded systems are used within many sectors of industry, including energy generation and distribution, mining and refining raw materials, fabrication and manufacturing, and logistics (moving and delivering components and goods).

Industrial systems have different priorities to IT systems. Often, hazardous electromechanical components are involved, so safety is the overriding priority. Industrial processes also prioritize availability and integrity over confidentiality-reversing the CIA triad as the AIC triad.

Workflow and Process Automation Systems

An industrial control system (ICS) provides mechanisms for workflow and process automation. An ICS controls machinery used in critical infrastructure, like power suppliers, water suppliers, health services, telecommunications, and national security services. An ICS that manages process automation within a single site is usually referred to as a distributed control system (DCS).

An ICS comprises plant devices and equipment with embedded PLCs. The PLCs are linked by a cabled network to actuators that operate valves, motors, circuit breakers, and other mechanical components, plus sensors that monitor some local state, such as temperature. Output and configuration of a PLC is performed by one or more human-machine interfaces (HMIs). An HMI might be a local control panel or software running on a computing host. PLCs are connected within a control loop, and the whole process automation system can be governed by a control server. Another important concept is the data historian, which is a database of all the information generated by the control loop.

Supervisory Control and Data Acquisition

A supervisory control and data acquisition (SCADA) system takes the place of a control server in large-scale, multiple-site ICSs. SCADA typically run as software on ordinary computers, gathering data from and managing plant devices and equipment with embedded PLCs, referred to as field devices. SCADA typically use WAN communications, such as cellular or satellite, to link the SCADA server to field devices.

IOT NETWORKS

Each device in an IoT network is identified with some form of unique serial number or code embedded within its own operating or control system and can interoperate within the existing Internet infrastructure, either directly or via an intermediary. As these devices tend to be small and often either unpowered or dependent on battery power, the standard Ethernet, cellular, and Wi-Fi networking products that connect computers are not always suitable for use. Other networking standards and products have been developed to facilitate IoT networks.

Operational Technology Networks

A cabled network for industrial applications is referred to as an operational technology (OT) network. These typically use either serial data protocols or industrial Ethernet. Industrial Ethernet is optimized for real-time, deterministic transfers. Such networks might use vendor-developed data link and networking protocols, as well as specialist application protocols.

Cellular Networks

A cellular network for IoT enables long-distance communication over the same system that supports mobile and smartphones. This is also called baseband radio, after the baseband processor that performs the function of a cellular modem. There are several baseband radio technologies:

●	Narrowband-IoT (NB-IoT)-this refers to a low-power version of the Long Term Evolution (LTE) or 4G cellular standard. The signal occupies less bandwidth than regular cellular. This means that data rates are limited (20-100 kbps), but most sensors need to send small packets with low latency, rather than making large data transfers. Narrowband also has greater penetrating power, making it more suitable for use in inaccessible locations, such as tunnels or deep within buildings, where ordinary cellular connectivity would be impossible.

●	LTE Machine Type Communication (LTE-M)-this is another low-power system but supports higher bandwidth (up to about 1 Mbps).

Z-Wave and Zigbee

Z-Wave is a wireless communications protocol used primarily for home automation. The Z-Wave Alliance operates a certification program for devices and software. Z-Wave creates a mesh network topology. Devices can be configured to work as repeaters to extend the network but there is a limit of four "hops" between a controller device and an endpoint. Z-Wave has been registered in most countries worldwide and uses radio frequencies in the high 800 to low 900 MHz range. It is designed to run for long periods (years) on battery power.

Zigbee has similar uses to Z-Wave and is an open-source competitor technology to it. The Zigbee Alliance operates certification programs for its various technologies and standards. Zigbee uses the 2.4 GHz frequency band. This higher frequency allows more data bandwidth at the expense of range compared to Z-Wave and the greater risk of interference from other 2.4 GHz radio communications. Zigbee supports more overall devices within a single mesh network (65,000 compared to 232 for Z-Wave), and there is no hop limit for communication between devices.

PLACEMENT AND SECURITY

Placement issues for embedded and IoT systems are best considered by dividing them into three principal groups: consumer-grade devices, smart building technology, and industrial systems.

While the network of individual devices might use Z-Wave or Zigbee, the hub for home automation plus larger appliances are usually connected directly to the local Wi-Fi network. Consumer-grade smart devices and home automation products can be poorly documented and patch management/security response processes of vendors can be inadequate. When they are designed for residential use, IoT devices can suffer from weak defaults. They may be configured to "work" with a minimum of configuration effort. There may be recommended steps to secure the device that the customer never takes.

In a corporate workspace, the main risk from smart device placement is that of shadow IT, where employees deploy a network-enabled device without going through a change and configuration management process. A vulnerability in the device would put it at risk of being exploited as an access point to the network. These devices also pose a risk for remote working, where the employee joins the corporate VPN using a home wireless network that is likely to contain numerous undocumented vulnerabilities and configuration weaknesses.

These risks can be mitigated by regular audits and through employee security awareness training.

Smart Buildings

By contrast with consumer-grade components, there should be less scope for compromise in the entry mechanisms and climate/lighting control components of a properly designed smart building system. Management and monitoring of the system should be performed over isolated network segments. Configuration management and change control processes should ensure that no weak configurations are introduced and that vendor advisories are tracked for any known vulnerabilities or exploits so that these can be patched or mitigated.

ICS/SCADA

While an ICS or SCADA is typically implemented as a dedicated OT or wireless WAN network, there may be points where these networks are linked to a corporate data network. Historically, these vulnerable links and bridging hosts have been exploited by threat actors. There are risks both to embedded systems from the data network and to corporate data assets and systems from the embedded network. Links between OT and IT networks must be monitored and subject to access controls.





Lesson 18: Explaining Disaster Recovery and High Availability Concepts

Topic 18A: Explain Disaster Recovery Concepts

HIGH AVAILABILITY

One of the key properties of a resilient system is availability. Availability is the percentage of time that the system is online, measured over a certain period, typically one year. The corollary of availability is downtime; that is, the percentage or amount of time during which the system is unavailable.

High availability is a characteristic of a system that can guarantee a certain level of availability. The Maximum Tolerable Downtime (MTD) metric states the requirement for a business function. Downtime is calculated from the sum of scheduled service intervals (Agreed Service Time) plus unplanned outages over the period. High availability might be implemented as 24x7 (24 hours per day, 7 days per week) or 24x365 (24 hours per day, 365 days per year). For a critical system, availability will be described as two-nines (99%) up to five- or six-nines (99.9999%).

Availability	Annual MTD (hh:mm:ss)

99\.9999%	00:00:32

99\.999%	00:05:15

99\.99%	00:52:34

99\.9%	08:45:36

99%	87:36:00

A system where there is almost no scheduled downtime and outages are extremely rare is also referred to as continuous availability. This sort of availability is required when there is not just a commercial imperative, but a danger of injury or loss of life associated with systems failure. Examples include networks supporting medical devices, air traffic control systems and communications satellites, as well as emerging technologies such as networked autonomous vehicles and new smart city applications, from smart law enforcement systems to smart traffic signaling systems.

The MTD metric sets the upper limit on the amount of recovery time that system and asset owners have to resume operations. Additional metrics can be used to govern recovery operations:

●	Recovery time objective (RTO) is the period following a disaster that an individual IT system may remain offline. This represents the maximum amount of time allowed to identify that there is a problem and then perform recovery (restore from backup or switch in an alternative system, for instance).

●	Work Recovery Time (WRT). Following systems recovery, there may be additional work to reintegrate different systems, restore data from backups, test overall functionality, and brief system users on any changes or different working practices so that the business function is again fully supported.

RTO+WRT must not exceed MTD!

●	Recovery Point Objective (RPO) is the amount of data loss that a system can sustain, measured in time units. That is, if a database is destroyed by a virus, an RPO of 24 hours means that the data can be recovered from a backup copy to a point not more than 24 hours before the database was infected.

Metrics governing mission essential functions. (Images © 123RF.com.)

FAULT TOLERANCE AND REDUNDANCY

A fault is usually defined as an event that causes a service to become unavailable. Each IT system will be supported by assets, such as servers, disk arrays, switches, routers, and so on. Each asset is susceptible to faults. Key Performance Indicators (KPIs) can be used to determine the reliability of each asset and assess whether goals for MTD, RTO, and RPO can be met. Some of the main KPIs relating to component reliability are as follows:

●	Mean Time Between Failures (MTBF) represents the expected lifetime of a product. The calculation for MTBF is the total operational time divided by the number of failures. For example, if you have 10 appliances that run for 50 hours and two of them fail, the MTBF is 250 hours/failure (10\*50)/2.

●	Mean Time to Failure (MTTF) expresses a similar metric for non-repairable components. For example, a hard drive may be described with an MTTF, while a server, which could be repaired by replacing the hard drive, would be described with an MTBF. The calculation for MTTF is the total operational time divided by the number of devices. For example, say two drives were installed in the server in a RAID array. One had failed after 10 years, but had never been replaced, and the second failed after 14 years, bringing down the array and the server. The MTTF of the drives is (10+14)/2 = 12 years.

MTTF/MTBF can be used to determine the amount of asset redundancy a system should have. A redundant system can failover to another asset if there is a fault and continue to operate normally. It can also be used to work out how likely failures are to occur.

●	Mean Time to Repair (MTTR) is a measure of the time taken to correct a fault so that the system is restored to full operation. This can also be described as mean time to replace or recover. MTTR is calculated as the total number of hours of unplanned maintenance divided by the number of failure incidents. This average value can be used to estimate whether a recovery time objective (RTO) is achievable.

A system that can experience failures in individual components and sub-systems and continue to provide the same (or nearly the same) level of service is said to be fault tolerant. Fault tolerance is often achieved by provisioning redundancy for critical components to eliminate single points of failure. A redundant or failover component is one that is not essential to the normal function of a system but that allows the system to recover from the failure of another component. Examples of devices and solutions that provide fault tolerance include the following:

●	Redundant spares-Components such as power supplies, network cards, drives (RAID), and cooling fans provide protection against hardware failures. A fully redundant server configuration is configured with multiple components for each function (power, networking, and storage). A faulty component will then automatically failover to the working one.

●	Network links-If there are multiple paths between switches and routers, these devices can automatically failover to a working path if a cable or network port is damaged.

●	Uninterruptible power supplies (UPSs) and standby power supplies-Provide power protection in the event of complete power failure (blackout) and other types of building power issues.

●	Backup strategies-Provide protection for data.

●	Cluster services-A means of ensuring that the total failure of a server does not disrupt services generally.

RECOVERY SITES

Within the scope of business continuity planning, disaster recovery plans (DRPs) describe the specific procedures to follow to recover a system or site to a working state. A disaster could be anything from a loss of power or failure of a minor component to manmade or natural disasters, such as fires, earthquakes, or acts of terrorism.

Providing redundant devices and spares or network links allows the spare devices to be swapped in if existing systems fail. Enterprise-level networks often also provide for spare sites. A spare site is another location that can provide the same (or similar) level of service. A disaster or systems failure at one site will cause services to failover to the alternate processing site. Disaster recovery planning must demonstrate how this will happen, what checks need to be made to ensure that failover has occurred successfully (without loss of transactional data or service availability), and how to revert to the primary site once functionality is restored there.

Site resiliency is described as hot, warm, or cold:

●	A hot site can failover almost immediately. It generally means that the site is already within the organization's ownership and is ready to deploy. For example, a hot site could consist of a building with operational computer equipment that is kept updated with a live data set.

●	A warm site could be similar, but with the requirement that the latest data set will need to be loaded.

●	A cold site takes longer to set up. A cold site may be an empty building with a lease agreement in place to install whatever equipment is required when necessary.

Clearly, providing redundancy on this scale can be very expensive. Sites are often leased from service providers. However, in the event of a nationwide emergency, demand for the services is likely to exceed supply! Another option is for businesses to enter into reciprocal arrangements to provide mutual support. This is cost effective but complex to plan and set up.

For many companies, the most cost-effective solution is to move processing and data storage to a cloud site. A cloud operator should be able to maintain hot site redundancy so that a disaster in one geographic area will not disrupt service, because the cloud will be supported by a datacenter in a different region.

FACILITIES AND INFRASTRUCTURE SUPPORT

The reliability of an individual site does not solely depend on the IT systems. A site must be provisioned with reliable power and climate conditions.

Heating, Ventilation, Air Conditioning

Environmental controls mitigate the loss of availability through mechanical issues with equipment, such as overheating. Building control systems maintain an optimum working environment for different parts of the building. The acronym HVAC (Heating, Ventilation, Air Conditioning) is often used to describe these services. An HVAC uses temperature sensors and moisture detection sensors (to measure humidity).

Fire Suppression

Health and safety legislation dictates what mechanisms an organization must put in place to detect and suppress fires. Some basic elements of fire safety include:

●	Well-marked fire exits and an emergency evacuation procedure that is tested and practiced regularly.

●	Building design that does not allow fire to spread quickly, by separating different areas with fire-resistant walls and doors.

●	Automatic smoke or fire detection systems, as well as alarms that can be operated manually.

Fire suppression systems work on the basis of the fire triangle. The fire triangle works on the principle that a fire requires heat, oxygen, and fuel to ignite and burn. Removing any one of those elements provides fire suppression (and prevention). In the United States (and most other countries), fires are divided by class under the NFPA (National Fire Protection Association) system, according to the combustible material that fuels the fire. Portable fire extinguishers come in several different types, with each type being designed for fighting a particular class of fire. Notably, Class C extinguishers use gas-based extinguishing and can be used where the risk of electric shock makes other types unsuitable.

Premises may also be fitted with an overhead sprinkler system. Wet-pipe sprinklers work automatically, are triggered by heat, and discharge water. Wet-pipe systems constantly hold water at high pressure, so there is some risk of burst pipes and accidental triggering, as well as the damage that would be caused in the event of an actual fire. There are several alternatives to wet-pipe systems that can minimize damage that may be caused by water flooding the room.

POWER MANAGEMENT

All types of network nodes require a stable power supply to operate. Electrical events, such as voltage spikes or surges, can crash computers and network appliances, while loss of power from brownouts or blackouts will cause equipment to fail. A brownout is where the voltage drops briefly, while a blackout is a complete loss of power lasting seconds or more. Power management means deploying systems to ensure that equipment is protected against these events and that network operations can either continue uninterrupted or be recovered quickly.

Power Distribution Units

The circuits supplying grid power to a rack, network closet, or server room must meet the load capacity of all the installed equipment (plus room for growth). Consequently, circuits to a server room will typically be higher capacity than domestic or office circuits (30 or 60 amps as opposed to 13 amps, for instance). These circuits may be run through a power distribution unit (PDU). A PDU has circuitry to "clean" the power signal, provides protection against spikes, surges, and brownouts, and can integrate with an uninterruptible power supply (UPS).

On a smaller scale, PDUs are also available as "strip" sockets that can take a higher load than a typical 13 amp rated strip. Such sockets are rack mounted and can be oriented horizontally or vertically to allow for different cabling and layout options. PDUs also often support remote power monitoring functions, such as reporting load and status, switching power to a socket on and off, or switching sockets on in a particular sequence.

Battery Backups and Uninterruptible Power Supplies

If there is loss of power, system operation can be sustained for a few minutes or hours (depending on load) using battery backup. Battery backup can be provisioned at the component level for disk drive and RAID array cache. The battery protects any read or write operations cached at the time of power loss.

At the system level, an uninterruptible power supply (UPS) will provide a temporary power source in the event of a blackout. UPS runtime may range from a few minutes for a desktop-rated model to hours for an enterprise system. In its simplest form, a UPS comprises a bank of batteries and their charging circuit plus an inverter to generate AC voltage from the DC voltage supplied by the batteries. Different UPS models support different power outputs and form factors-from desktop to rack mounted depending on your needs.

Generators

The runtime allowed by a UPS should be sufficient to failover to an alternative power source, such as a standby generator. If there is no secondary power source, a UPS will at least allow the administrator to shut down the server or appliance properly-users can save files, and the OS can complete the proper shut down routines.

A backup power generator can provide power to the whole building, often for several days. Most generators use diesel, propane, or natural gas as a fuel source. A UPS is always required to protect against any interruption to computer services. A backup generator cannot be brought online fast enough to respond to a power failure.

Datacenters are also investing in renewable power sources, such as solar, wind, geothermal, hydrogen fuel cells, and hydro. The ability to use renewable power is a strong factor in determining the best site for new datacenters. Large-scale battery solutions, such as Tesla's Powerpack (tesla.com/powerpack), may be able to provide an alternative to backup power generators. There are also emerging technologies to use all the battery resources of a datacenter as a microgrid for power storage (scientificamerican.com/article/how-big-batteries-at-data-centers-could-replace-power-plants).

NETWORK DEVICE BACKUP MANAGEMENT

All business continuity and disaster recovery planning procedures make use of backups. The execution and frequency of backups must be carefully planned and guided by policies. In network management, backup policies are less focused on the data stored on servers and more on swiftly restoring faulty switches, routers, firewalls, and load balancers.

Each device should have a documented baseline configuration. The deployment process should be capable of applying this configuration to a replacement device or when restoring a faulty device.

One complication here is that most network appliances have a startup or persistent configuration and a running configuration. In most cases, these should be the same. It is possible that a configuration oversight left a valid running configuration that was never saved as the startup configuration. Regular audits and other configuration management procedures should be used to detect and remediate running configs that differ from the saved config.

Most devices will also support a version history of previous configurations enabling a change to be rolled back if it causes problems.

An appliance may also support two backup modes:

●	State/bare metal-A snapshot-type image of the whole system. This can be re-deployed to any device of the same make and model as a system restore.

●	Configuration file-A copy of the configuration data in a structured format, such as extensible markup language (XML). This file can be used in a two-stage restore where the OS or firmware image is applied first (or a new appliance provisioned) and then the configuration is restored by importing the backup file.

A network appliance may also hold state information that has not been written to a log and that will not be captured by a backup of the configuration file only. State information includes data such as the MAC tables in switches or the NAT table in a firewall. Advanced firewalls may contain additional data such as malware/intrusion detection signatures. Some devices might log state data to an internal database that can be backed up periodically. In other cases, if this information needs to be preserved, the appliance should be configured to log state data to a remote server, using a protocol such as syslog.

Topic 18B: Explain High Availability Concepts

MULTIPATHING

Multipathing means that a network node has more than one physical link to another node. Multipathing is a default feature of full and partial mesh internetworks, where routers can select alternative paths through the network if a link is not available. Multipathing can be used anywhere that link redundancy is required. Two common additional scenarios are connections to storage area networks (SANs) and Internet access via an Internet Service Provider (ISP):

●	SAN multipathing-In a SAN, a server uses shared storage accessed over a network link. Multipathing means that the server has at least two SAN controllers each with a dedicated link to the storage network.

●	Multiple ISPs-If an organization depends on a single ISP for Internet access, that circuit represents a critical single point of failure. Even if there are multiple circuits to the same ISP, problems within that ISP's routing or DNS infrastructure could result in complete loss of connectivity. Contracting with multiple ISPs and using routing policies to forward traffic over multiple external circuits provides fault tolerance and load balancing. You need to ensure that the ISPs are operating separate infrastructure and not using peering arrangements.

This fault tolerance is reduced if both ISP's links use the same entrance facility. A physical disaster event such as an earthquake or construction damage is likely to affect both sets of cables. Diverse paths refers to provisioning links over separate cable conduits that are physically distant from one another. Another option is to provision cellular links as a backup, although even if 5G technologies are available, this is likely to reduce link bandwidth substantially, and even then, it could be that the 5G backhaul uses some of the same fiber infrastructure as the cabled circuit.

LINK AGGREGATION/NIC TEAMING

Link aggregation means combining two or more separate cabled links between a host and a switch into a single logical channel. From the host end, this can also be called NIC teaming; at the switch end, it can be called port aggregation and is referred to by Cisco as an EtherChannel. The term bonding is also widely substituted for aggregation. For example, a single network adapter and cable segment might support 1 Gbps; bonding this with another adapter and cable segment gives a link of 2 Gbps. Link aggregation can also be used in an uplink between two switches or between a switch and a router or between two routers.

A server node uses NIC teaming to create a 4 Gbps channel link from four 1 Gbps ports to a workgroup switch, while the workgroup switch bonds its uplink transceivers to create a 20 Gbps channel to a router.

Link aggregation can also provide redundancy; if one link is broken, the connection is still maintained by the other. It is also often cost-effective; a four-port Gigabit Ethernet card might not match the bandwidth of a 10 GbE port but will cost less.

This configuration is fully redundant only if the business function does not depend on the full speed of the bonded link. If one port fails, and the link drops to 1 Gbps, but that bandwidth is insufficient, there is not full redundancy.

Link aggregation is typically implemented using the IEEE 802.3ad/802.1ax standard. 802.3ad bonded interfaces are described as a Link Aggregation Group (LAG). 802.3ad also defines the Link Aggregation Control Protocol (LACP), which can be used to detect configuration errors and recover from the failure of one of the physical links.

LOAD BALANCERS

Where NIC teaming allows load balancing at the component level, a load balancer can be deployed as a hardware appliance or software instance to distribute client requests across server nodes in a farm or pool. You can use a load balancer in any situation where you have multiple servers providing the same function. Examples include web servers, front-end email servers, and web conferencing, A/V conferencing, or streaming media servers. The load balancer is placed in front of the server network and distributes requests from the client network or Internet to the application servers. The service address is advertised to clients as a virtual server. This is used to provision services that can scale from light to heavy loads, provision fault tolerant services, and to provide mitigation against distributed denial of service (DDoS) attacks.

Topology of basic load balancing architecture. (Images © 123RF.com.)

There are two main types of load balancers:

●	Layer 4 switch-Basic load balancers make forwarding decisions on IP address and TCP/UDP header values, working at the transport layer of the OSI model.

●	Layer 7 switch (content switch)-As web applications have become more complex, modern load balancers need to be able to make forwarding decisions based on application-level data, such as a request for a particular URL or data types like video or audio streaming. This requires more complex logic, but the processing power of modern appliances is sufficient to deal with this.

We are used to associating switches with Layer 2 (Ethernet), but appliances can perform switch-like forwarding at Layer 3, Layer 4, and Layer 7. These are collectively referred to as multilayer switches.

REDUNDANT HARDWARE/CLUSTERS

Where a load balancer distributes traffic between independent processing nodes, clustering allows multiple redundant processing nodes that share data with one another to accept connections. If one of the nodes in the cluster stops working, connections can failover to a working node. To clients, the cluster appears to be a single server.

Virtual IP

For example, you might want to provision two load balancer appliances so that if one fails, the other can still handle client connections. Unlike load balancing with a single appliance, the public IP used to access the service is shared between the two instances in the cluster. This is referred to as a virtual IP or shared or floating address. The instances are configured with a private connection, on which each is identified by its "real" IP address. This connection runs some type of redundancy protocol, such as Common Address Redundancy Protocol (CARP), that enables the active node to "own" the virtual IP and respond to connections. The redundancy protocol also implements a heartbeat mechanism to allow failover to the passive node if the active one should suffer a fault.

Topology of clustered load balancing architecture. (Images © 123RF.com.)

The same sort of topology can be used to deploy routers and firewalls for high availability and load sharing.

In the previous example, if one node is active, the other is passive. This is referred to as active-passive clustering. The major advantage of active/passive configurations is that performance is not adversely affected during failover. However, the hardware and operating system costs are higher because of the unused capacity.

An active-active cluster means that both nodes are processing connections concurrently. This allows the administrator to use the maximum capacity from the available hardware while all nodes are functional. In the event of a failover the workload of the failed node is immediately and transparently shifted onto the remaining node. At this time, the workload on the remaining nodes is higher and performance is degraded.

In a standard active-passive configuration, each active node must be matched by a passive node. There are N+1 and N+M configurations that provision fewer passive nodes than active nodes, to reduce costs.

FIRST HOP REDUNDANCY

In a full or partial mesh network topology, alternate routes can be found to bypass failed routers or faulty connections. However, end systems are typically served by a single router configured as the default gateway. While it is possible to configure hosts with multiple default gateways for fault tolerance, this does not work well in practice, as it requires a greater degree of complexity in the hosts' routing algorithms than is typically implemented on an end system host.

To address this problem, various types of first hop redundancy protocol (FHRP) have been developed.

Hot Standby Router Protocol

The proprietary Hot Standby Router Protocol (HSRP) developed by Cisco allows multiple physical routers to serve as a single default gateway for a subnet. To do this, each router must have an interface connected to the subnet, with its own unique MAC address and IP address. In addition, they also need to be configured to share a common virtual IP address and a common MAC address. The group of routers configured in this way is known as a standby group. They communicate among themselves using IP multicasts and choose an active router based on priorities configured by an administrator. The active router responds to any traffic sent to the virtual IP address. Of the remaining routers in the standby group, the router with the next highest priority is chosen as the standby router. The standby router monitors the status of the active router and takes over the role if the active router becomes unavailable, also triggering the selection of a new standby router from the remaining routers in the group.

Hot Standby Router Protocol (HSRP) topology. (Image © 123RF.com.)

Cisco also have the Gateway Load Balancing Protocol (GLBP) which allows for an active/active load balanced configuration.

Virtual Router Redundancy Protocol

The open standard protocol Virtual Router Redundancy Protocol (VRRP) is similar to HSRP, the differences mainly being in terminology and packet formats. In VRRP, the active router is known as the master, and all other routers in the group are known as backup routers. There is no specific standby router; instead, all backup routers monitor the status of the master, and in the event of a failure, a new master router is selected from the available backup routers based on priority.

One advantage of VRRP over HSRP is that it does not require each router interface to be assigned a unique IP address. It is possible to configure VRRP routers to use only the virtual IP address. This can be useful on subnets where address space utilization is high.

Lesson 19: Applying Network Hardening Techniques

Topic 19A: Compare and Contrast Types of Attacks

GENERAL ATTACK TYPES

A network can be attacked by many kinds of intruders or adversaries for many different reasons. The goals of most types of adversaries will be to steal (exfiltrate) information from the network, to misuse network services (for fraud, for instance), or to compromise the availability of the network. Insider threat-type attacks may be launched with privileged access to the network, while external threats must find some way of accessing the network, perhaps by installing malware on a host system.

Footprinting and Fingerprinting Attacks

Footprinting and fingerprinting are enumeration or information gathering attacks. Footprinting allows a threat actor to discover the topology and general configuration of the network and security systems. Footprinting can be done by social engineering attacks-persuading users to give information or locating information that has been thrown out as trash, for instance. Port scanning specifically aims to enumerate the TCP or UDP application ports on which a host will accept connections.

Fingerprinting allows a threat actor to identify device and OS types and versions. When a host running a particular operating system responds to a port scan, the syntax of the response might identify the specific operating system. This fact is also true of application servers, such as web servers, FTP servers, and mail servers. The responses these servers make often include headers or banners that can reveal a great deal of information about the server. A threat actor can use this information to probe for known vulnerabilities.

Spoofing Attacks

The term spoofing covers a wide range of different attacks. Spoofing can include any type of attack where the attacker disguises his or her identity, or in which the source of network information is forged to appear legitimate. Social engineering and techniques such as phishing and pharming, where the attacker sets up a false website in imitation of a real one, are types of spoofing attacks. It is also possible to abuse the way a protocol works or how network packets are constructed to inject false or modified data onto a network. The ARP and DNS protocols are often used as vectors for this type of attack.

Denial of Service Attacks

A denial of service (DoS) attack causes a service at a given host to fail or to become unavailable to legitimate users. Resource exhaustion DoS attacks focus on overloading a service by using up CPU, system RAM, disk space, or network bandwidth. It is also possible for DoS attacks to exploit design failures or other vulnerabilities in application software. A physical DoS attack might involve cutting telephone lines or network cabling or switching off the power to a server. DoS attacks may be motivated by the malicious desire to cause trouble. They may also be part of a wider attack, such as the precursor to a spoofing or data exfiltration attack. DoS can assist these attacks by diverting attention and resources away from the real target. For example, a blinding attack attempts to overload a logging or alerting system with events.

ON-PATH ATTACKS

An on-path attack is a specific type of spoofing attack where a threat actor compromises the connection between two hosts and transparently intercepts and relays all communications between them. The threat actor might also have the opportunity to modify the traffic before relaying it.

On-path attacks are also known by the term "Man-in-the-Middle (MitM)." Such terms are non-inclusive and/or use inappropriate or vague metaphors and are deprecated in the latest CompTIA exam objectives documents.

MAC Spoofing and IP Spoofing

A host can arbitrarily select any MAC and/or IP address and attempt to use it on the network. A threat actor might exploit this to spoof the value of a valid MAC or IP address to try to circumvent an access control list or impersonate a legitimate server. For this type of attack to succeed, the threat actor must normally disable the legitimate host or there will be duplicate addresses on the network, which will have unpredictable results.

IP spoofing is also used in most denial of service (DoS) attacks to mask the origin of the attack and make it harder for the target system to block packets from the attacking system. In this type of spoofing, the threat actor does not care about not receiving return traffic.

ARP Spoofing

ARP spoofing, or ARP cache poisoning, is a common means of perpetrating an on-path attack. It works by broadcasting unsolicited ARP reply packets, also known as gratuitous ARP replies, with a source address that spoofs a legitimate host or router interface. Because ARP has no security, all devices in the same broadcast domain as the rogue host trust this communication and update their MAC:IP address cache table with the spoofed address. Because the threat actor broadcasts endless ARP replies, it overwhelms the legitimate interface.

Observing ARP poisoning in a Wireshark packet capture. (Screenshot courtesy of Wireshark.)

The usual target will be the subnet's default gateway. If the attack is successful, all traffic destined for remote networks will be sent to the attacker. The threat actor can then perform an on-path attack to monitor the communications and continue to forward them to the router to avoid detection. The attacker could also modify the packets before forwarding them. ARP poisoning could also perform a DoS attack by not forwarding the packets.

ARP poisoning can be difficult to detect without closely monitoring network traffic. However, attempts at ARP poisoning are likely to cause sporadic communications difficulties, such as an unreachable default gateway. In such cases, performing network captures and examining ARP packets may reveal the poison packets, as will examining local ARP caches for multiple IP addresses mapping to the same MAC address.

While IPv6 does not use ARP, it is also vulnerable to layer 2 spoofing if the unencrypted Neighbor Discovery (ND) protocol is used.

Rogue DHCP

An on-path attack can also be launched by running a rogue DHCP server. DHCP communications cannot be authenticated, so a host will generally trust the first offer packet that it receives. The threat actor can exploit this to set his or her machine as the subnet's default gateway or DNS resolver.

DNS POISONING ATTACKS

DNS poisoning is an attack that compromises the name resolution process. Typically, the attacker will replace the valid IP address for a trusted website, such as mybank.example, with the attacker's IP address. The attacker can then intercept all the packets directed to mybank.example and bounce them to the real site, leaving the victim unaware of what is happening (referred to as pharming). Alternatively, DNS spoofing could be used for a DoS attack by directing all traffic for a particular FQDN to an invalid IP address (a black hole).

One way to attack DNS is to corrupt the client's name resolution process. This can be accomplished by changing the servers used for resolving queries, intercepting and modifying DNS traffic, or polluting the client's name cache (by modifying the HOSTS file, for instance). DNS server cache poisoning (or pollution) is another redirection attack, but instead of trying to subvert the name service used by the client, it aims to corrupt the records held by the DNS server itself.

Attempting to poison a DNS server cache-This attack has failed.

VLAN HOPPING ATTACKS

VLAN hopping is an attack designed to send traffic to a VLAN other than the one the host system is in. This exploits the native VLAN feature of 802.1Q. Native VLANs are designed to provide compatibility with non-VLAN capable switches. The attacker, using a device placed in the native VLAN, crafts a frame with two VLAN tag headers. The first trunk switch to inspect the frame strips the first header, and the frame gets forwarded to the target VLAN. Such an attack can only send packets one way but could be used to perform a DoS attack against a host on a different VLAN. Double tagging can be mitigated by ensuring that the native VLAN uses a different ID to any user accessible VLAN.

A VLAN hopping attack can also be launched by attaching a device that spoofs the operation of a switch to the network and negotiating the creation of a trunk port. As a trunk port, the attacker's device will receive all inter-VLAN traffic. This attack can be mitigated by ensuring that ports allowed to be used as trunks are pre-determined in the switch configuration and that access ports are not allowed to auto-configure as trunk ports.

WIRELESS NETWORK ATTACKS

Wireless networks can open several avenues for a threat actor to gain unauthorized network access.

Rogue Access Points

A rogue access point is one that has been installed on the network without authorization, whether with malicious intent or not. A malicious user can set up such an AP with something as basic as a smartphone with tethering capabilities, and a non-malicious user could enable such an AP by accident. If connected to a LAN without security, an unauthorized AP creates a backdoor through which to attack the network.

Evil Twins

A rogue AP masquerading as a legitimate one is called an evil twin. An evil twin might advertise a similar network name (SSID) to the legitimate one. For example, an evil twin might be configured with the network name "compeny" where the legitimate network name is "company." Alternatively, the evil twin might spoof the SSID and BSSID (MAC address) of an authorized access point and then the attacker might use some DoS technique to overcome the legitimate AP. After a successful DoS attack, the users will be forced to disconnect from the network and then manually attempt to reconnect. At that point, with many users busy and trying to get back to work, some or all may associate with the evil twin AP and submit the network passphrase or their credentials for authentication.

However it is configured, when a user connects to an evil twin, it might be able to harvest authentication information and, if it is able to provide wider network or Internet access, execute an on-path attack to snoop on connections established with servers or websites.

Surveying Wi-Fi networks using Xirrus Wi-Fi Inspector (xirrus.com)-Note the presence of print devices configured with open authentication (no security) and a smart TV appliance (requiring authentication). (Screenshot used with permission from Xirrus.)

One solution to the risk of rogue access points is to use EAP-TLS security so that the authentication server and clients perform mutual authentication. There are also various scanners and monitoring systems that can detect rogue APs, referred to as a wireless intrusion detection system (WIDS) or wireless intrusion prevention system (WIPS).

Deauthentication Attacks

The use of an evil twin may be coupled with a deauthentication attack. This sends a stream of spoofed management frames to cause a client to deauthenticate from an AP. This might allow the attacker to interpose the evil twin, sniff information about the authentication process, or perform a denial of service (DoS) attack against the wireless infrastructure. These attacks work against both WEP and WPA. The attacks can be mitigated if the wireless infrastructure supports Management Frame Protection (MFP/802.11w). Both the AP and clients must be configured to support MFP.

Aireplay sniffs ARP packets to harvest IVs while Airodump saves them to a capture, which Aircrack can analyze to identify the correct encryption key.

DISTRIBUTED DOS ATTACKS AND BOTNETS

A distributed DoS (DDoS)attack is launched simultaneously by multiple hosts. Some types of DDoS attack simply aim to consume network bandwidth, denying it to legitimate hosts. Others cause resource exhaustion on the hosts processing requests, consuming CPU cycles and memory. This delays processing of legitimate traffic and could potentially crash the host system completely. For example, a SYN flood attack works by withholding the client's ACK packet during TCP's three-way handshake. The client's IP address is spoofed, meaning that an invalid or random IP is entered so the server's SYN/ACK packet is misdirected. A server can maintain a queue of pending connections. When it does not receive an ACK packet from the client, it resends the SYN/ACK packet a set number of times before "timing out" and giving up on the connection. The problem is that a server may only be able to manage a limited number of pending connections, which the DoS attack quickly fills up. This means that the server is unable to respond to genuine traffic.

Dropping traffic from blacklisted IP ranges by using the Security Onion Network Security Monitoring (NSM) appliance. (Screenshot courtesy of Security Onion.)

Distributed Reflection DoS/Amplification Attacks

A more powerful TCP SYN flood attack is a type of distributed reflection DoS (DRDoS) or amplification attack. In this attack, the adversary spoofs the victim's IP address and attempts to open connections with multiple servers. Those servers direct their SYN/ACK responses to the victim server. This rapidly consumes the victim's available bandwidth.

The same sort of technique can be used to bombard a victim network with responses to bogus DNS queries. One of the advantages of this technique is that while the request is small, the response to a DNS query can be made to include a lot of information, so this is a very effective way of overwhelming the bandwidth of the victim network with much more limited resources on the attacker's network. The Network Time Protocol (NTP) can be abused in a similar way.

Botnets

A botnet is a group of compromised hosts that can be used to launch DDoS and DRDoS attacks. A threat actor will first compromise one or two machines to use as handlers or herders. The handlers are used to compromise hundreds or thousands or millions of zombie hosts with DoS tools (the bots). To compromise a host, the attacker must install malware that opens a backdoor remote connection. The attacker can then use the malware to install bots and trigger the zombies to launch the attack at the same time. The network established between the handlers and the bots is called a command and control (C-and-C or C2) network.

Any type of Internet-enabled device is vulnerable to compromise. This includes web-enabled cameras, SOHO routers, and smart TVs and other appliances. This is referred to as an Internet of Things (IoT) botnet.

MALWARE AND RANSOMWARE ATTACKS

Many of the intrusion attempts perpetrated against computer networks depend on the use of malicious software, or malware. Malware can be defined simply as software that does something bad, from the perspective of the system owner. There are many types of malware, but they are not classified in a rigorous way, so some definitions overlap or are blurred. Some malware classifications, such as Trojan, virus, and worm, focus on the vector used by the malware. The vector is the method by which the malware executes on a computer and potentially spreads to other network hosts. Another complicating factor with malware classification is the degree to which its installation is expected or tolerated by the user. The following categories describe some types of malware according to vector:

●	Viruses and worms-These represent some of the first types of malware and spread without any authorization from the user by being concealed within the executable code of another process.

●	Trojan-Malware concealed within an installer package for software that appears to be legitimate. This type of malware does not seek any type of consent for installation and is actively designed to operate secretly.

●	Potentially unwanted programs (PUPs)/Potentially unwanted applications (PUAs)-Software installed alongside a package selected by the user or perhaps bundled with a new computer system. Unlike a Trojan, the presence of a PUP is not automatically regarded as malicious. It may have been installed without active consent or consent from a purposefully confusing license agreement. This type of software is sometimes described as grayware rather than malware.

Other classifications are based on the payload delivered by the malware. The payload is an action performed by the malware other than simply replicating or persisting on a host. Examples of payload classifications include spyware, rootkit, remote access Trojan (RAT) or backdoor, and ransomware.

Ransomware is a type of malware that tries to extort money from the victim. One class of ransomware will display threatening messages, such as requiring Windows to be reactivated or suggesting that the computer has been locked by the police because it was used to view child pornography or for terrorism. This may block access to the computer by installing a different shell program or browser window that is difficult to close, but this sort of attack is usually relatively simple to fix.

The crypto-malware class of ransomware attempts to encrypt data files on any fixed, removable, and network drives. If the attack is successful, the user will be unable to access the files without obtaining the private encryption key, which is held by the attacker. If successful, this sort of attack is extremely difficult to mitigate, unless the user has up to date backups of the encrypted files. One example of this is Cryptolocker, a Trojan that searches for files to encrypt and then prompts the victim to pay a sum of money before a certain countdown time, after which the malware destroys the key that allows the decryption.

WannaCry ransomware. Wikimedia Public Domain image. (Image by Wikimedia Commons.)

PASSWORD ATTACKS

On-path and malware attacks can be difficult to perpetrate. Many network intrusions occur because a threat actor is able to obtain credentials to access the network. Also, when a threat actor gains some sort of access via an on-path or malware attack, they are likely to attempt to escalate privileges to gain access to other targets on the network by harvesting credentials for administrative accounts.

Passwords or password hashes can be captured by obtaining a password file or by sniffing the network. If the protocol uses cleartext credentials, then the threat actor can simply read the cleartext password from the captured frames.

If authentication credentials are transmitted in cleartext, such as the unencrypted version of the IMAP mailbox access protocol, it is a simple matter for the credentials to be intercepted via packet sniffing. (Screenshot courtesy of Wireshark.)

A password might be sent in an encoded form, such as Base64, which is simply an ASCII representation of binary data. This is not the same as encryption. The password value can easily be derived from the Base64 string.

In most cases, a password is stored and transmitted securely by making a cryptographic hash of the string entered by the user. A cryptographic hash algorithm, such as Secure Hash Algorithm (SHA) or Message Digest v5 (MD5), produces a fixed length string from a variable length string. This means that, in theory, no one except the user (not even the system administrator) knows the password, because the plaintext should not be recoverable from the hash.

Password cracking software uses various methods to work out the plaintext password string from a cryptographic hash:

●	Dictionary-The software matches the hash to those produced by ordinary words found in a dictionary. This could also include information such as user and company names, pet names, or any other data that people might naively use as passwords.

●	Brute force-The software tries to match the hash against one of every possible combination it could be. If the password is short (under eight characters) and non-complex (using only letters, for instance), a password might be cracked in minutes. Longer and more complex passwords increase the amount of time the attack takes to run.

A threat actor might obtain password hashes from a protocol such as SMB with no encryption configured. The risks posed by cracking software mean that it is more secure to use end-to-end encryption, such as IPSec or Transport Layer Security (TLS). This means that all payload data is encrypted, and a network sniffer cannot even recover the password hashes.

HUMAN AND ENVIRONMENTAL ATTACKS

Threat actors can use a diverse range of techniques to compromise a security system. A prerequisite of many types of attacks is to obtain information about the network and security system. Social engineering (or hacking the human) refers to a collection of techniques and tricks designed to make victims reveal confidential information. Impersonation (pretending to be someone else) is one of the basic social engineering techniques. The classic impersonation attack is for the threat actor to phone into a department pretending to be calling from IT support, claim they have to adjust something on the user's system remotely, and get the user to reveal their password. For this attack to succeed, the approach must be persuasive and establish trust. Social engineering might also use intimidation or hoaxes as a means of eliciting information.

Phishing Attacks

Phishing is a combination of social engineering and spoofing. It persuades or tricks the target into interacting with a malicious resource disguised as a trusted one, traditionally using email as the vector. A phishing message might try to convince the user to perform some action, such as installing disguised malware or allowing a remote access connection by the attacker. Other types of phishing campaign use a spoof website set up to imitate a bank or e‑commerce site or some other web resource that should be trusted by the target. The attacker then emails users of the genuine website informing them that their account must be updated or with some sort of hoax alert or alarm, supplying a disguised link that actually leads to the spoofed site. When the user authenticates with the spoofed site, their logon credentials are captured.

Example phishing email-On the right, you can see the message in its true form as the mail client has stripped out the formatting (shown on the left) designed to disguise the nature of the links.

Shoulder Surfing

A threat actor can learn a password or PIN (or other secure information) by watching the user type it. This is referred to as a shoulder surfing attack. Despite the name, the attacker may not have to be in close proximity to the target-they could use high-powered binoculars or CCTV to directly observe the target remotely.

Tailgating and Piggybacking

Tailgating is a means of entering a secure area without authorization by following closely behind the person that has been allowed to open the door or checkpoint. Piggybacking is a similar situation but means that the attacker enters a secure area with an employee's permission. For instance, an attacker might impersonate a member of the cleaning crew and request that an employee hold the door open while they bring in a cleaning cart or mop bucket. Another technique is to persuade someone to hold a door open, using an excuse, such as "I've forgotten my badge/key." Alternatively, piggybacking may be a means of an insider threat actor to allow access to someone without recording it in the building's entry log.

Topic 19B: Apply Network Hardening Techniques

DEVICE AND SERVICE HARDENING

As part of a defense in depth strategy, you need to think about making each host and network infrastructure device secure against tampering or abuse. It can be tempting to think of network devices such as switches and routers as self-contained. In fact, these devices often run quite complex firmware and host numerous services to enable remote management and configuration. Deploying systems in a secure configuration is known as device hardening. Some of the policies that will make up a secure configuration involve the following:

●	Change default passwords/credentials-Devices such as wireless access points, switches, and routers sometimes ship with a default management password such as password, admin, or the device vendor's name. These should be changed on installation.

●	Enforce password complexity/length requirements-Passwords for network infrastructure must be highly resistant to guessing and cracking attacks:

●	Length-No passwords should be less than eight characters. However, as critical infrastructure, passwords for network appliances should be 14+ characters.

●	Complexity-Requiring multiple character classes (mixing letters, case, digits, and symbols) is deprecated by NIST's latest guidance, but is still a requirement in many local password policies.

●	Avoiding common passwords-The number of successful attacks against web servers and company networks has led to huge databases of credentials being posted online. Analysis of these databases shows how many users-even administrative users-rely on trivially simple passwords, such as 123456 or password. These password database dumps give attackers a useful dictionary to work with when trying to crack credentials. Any password that could be matched to a dictionary term is completely unsecure and must not be used.

●	Configure role-based access-The default administrator, superuser, or root account has unrestricted access to the device. If the credentials for this account are shared, the risk of compromise is greatly magnified. Role-based access means that a limited set of permissions are configured for different administrative groups, such as separating permissions for configuring the system to those for configuring logging and auditing. This separation of duties reduces impacts from the compromise of any single account.

●	Disable unneeded network services-Any services or protocols that are not used should be disabled. This reduces the attack surface of a network appliance or OS. Attack surface means the range of things that an attacker could possibly exploit in order to compromise the device. It is particularly important to disable unused administration interfaces.

●	Disable unsecure protocols-Sniffing attacks can be mitigated by encrypting the channel over which communications takes place. This means that even if the eavesdropper can listen to the message, he or she cannot understand it without obtaining the encryption key. It is important to understand which protocols are unsecure in terms of using unencrypted channels. This is particularly important when using a channel to authenticate. Unsecure protocols should be deprecated, and secure protocols used instead. For example, the original versions of SNMP are unencrypted. To implement secure SNMP, either configure SNMPv3, which supports encryption, or use an encapsulation protocol such as IPSec to encrypt SNMP traffic.

ENDPOINT SECURITY AND SWITCHPORT PROTECTION

Endpoint security is a set of security procedures and technologies designed to restrict network access at a device level. Endpoint security contrasts with the focus on perimeter security established by topologies such as screened subnets and technologies such as firewalls. Endpoint security is designed not to replace perimeter security but to supplement it, creating defense in depth.

Access to the physical switch ports and switch hardware should be restricted to authorized staff, using a secure server/equipment room and/or lockable hardware cabinets. To prevent the attachment of unauthorized client devices, a switch port can be disabled using the management software or isolated to a VLAN with no route to the network (a black hole VLAN). On a Cisco switch, these configuration settings will generally be applied using some version of a switchport command or sub-command. As another option, the patch cable can be physically removed from the port. Completely disabling ports in this way can introduce a lot of administrative overhead and scope for error. Also, it doesn't provide complete protection, as an attacker could unplug a device from an enabled port and connect their own laptop. Consequently, more sophisticated methods of ensuring port security have been developed.

MAC Filtering and Dynamic ARP Inspection

Configuring MAC filtering on a switch means defining which MAC addresses are permitted to connect to a particular port. This can be done by creating a list of valid MAC addresses or by specifying a limit to the number of permitted addresses. For example, if port security is enabled with a maximum of two MAC addresses, the switch will record the first two MACs to connect to that port but then drop any traffic from machines with different network adapter IDs that try to connect

A malicious host may use a spoofed MAC address to try to perform ARP cache poisoning against other hosts on the network and perpetrate an on-path attack. A switch port security feature such as dynamic ARP inspection (DAI) prevents a host attached to an untrusted port from flooding the segment with gratuitous ARP replies. ARP inspection maintains a trusted database of IP:ARP mappings. It also ensures that ARP packets are validly constructed and use valid IP addresses.

Configuring ARP inspection and DHCP snooping on a Cisco switch. (Image © and Courtesy of Cisco Systems, Inc. Unauthorized use not permitted.)

DHCP Snooping

Configuring DHCP snooping causes the switch to inspect DHCP traffic arriving on access ports to ensure that a host is not trying to spoof its MAC address. It can also be used to prevent rogue DHCP servers from operating on the network. With DHCP snooping, only DHCP offers from ports configured as trusted are allowed.

Neighbor Discovery Inspection and Router Advertisement Guard

Neighbor Discovery (ND) Inspection and Router Advertisement (RA) Guard perform similar functions to DAI and DHCP snooping for IPv6 networks. Most hosts have IPv6 enabled by default and disabling it can often cause unexpected problems. Consequently, these switch protections should be enabled to mitigate spoofing and on-path attacks over IPv6.

Port Security/IEEE 802.1X Port-Based Network Access Control

MAC limiting and filtering and ARP inspection provide some protection against attacks, but they are not a means of ensuring only valid hosts are connecting to the network. Port security refers to the IEEE 802.1X standard’s Port-Based Network Access Control (PNAC) mechanism. PNAC means that the switch performs some sort of authentication of the attached device before activating the port.

Under 802.1X, the device requesting access is the supplicant. The switch, referred to as the authenticator, enables the Extensible Authentication Protocol over LAN (EAPoL) protocol only and waits for the device to supply authentication data. The authenticator passes this data to an authenticating server, typically a RADIUS server, which checks the credentials and grants or denies access. If access is granted, the switch will configure the port to use the appropriate VLAN and enable it for ordinary network traffic. Unauthenticated hosts may be denied any type of access or be placed in a guest VLAN with only limited access to the rest of the network.

VLAN AND PVLAN BEST PRACTICES

The virtual LAN (VLAN) feature of managed Ethernet switches is typically deployed to enforce segmentation policies. A VLAN isolates Layer 2 broadcast traffic to switch ports that are configured with the same VLAN ID. Each VLAN ID is typically mapped to a subnet and any traffic forwarding between VLANs must be performed by a router (or Layer 3 switch).

Private VLANs

A private VLAN (PVLAN) applies an additional layer of segmentation by restricting the ability of hosts within a VLAN to communicate directly with one another. This might be used by a hosting company to prevent web servers operated by different customers being able to communicate. Isolating these server instances using PVLANs is simpler than creating multiple VLANs and subnets. Similarly, ISPs use PVLANs to isolate subscriber traffic.

When configuring a PVLAN, the "host" VLAN is referred to as the primary VLAN. The following types of PVLAN ports can be configured within the primary VLAN:

●	Promiscuous port-Can communicate with all ports in all domains within the PVLAN. This is normally the port through which routed and/or DHCP traffic is sent.

●	Isolated port-Can communicate with the promiscuous port only. This creates a subdomain of a single host only. The PVLAN can contain multiple isolated ports, but each is in its own subdomain.

●	Community port-Can communicate with the promiscuous port and with other ports in the same community. This creates a subdomain that can contain multiple hosts.

Default VLAN and Native VLAN

The VLAN with ID 1 is referred to as the default VLAN. This cannot be changed. However, unless configured differently, all ports on a switch default to being in VLAN 1. When you are implementing VLANs, you should avoid sending user data traffic over the default VLAN. It should remain unused or used only for inter-switch protocol traffic, where necessary. For example, spanning tree traffic would be permitted to run over the default VLAN. Make sure that unused ports are not assigned to VLAN 1.

A native VLAN is one into which any untagged traffic is put when receiving frames over a trunk port. When a switch receives an untagged frame over a trunk, it assigns the frame to the native VLAN. Untagged traffic might derive from legacy devices such as hubs or older switches that do not support 802.1Q encapsulated frames. The native VLAN is initially set with the same VID as the default VLAN (VID 1). You can and should change this, however, to make the native VID any suitable ID. This should not be the same as any VLAN used for any other data traffic. The same native VLAN ID (VID) should be configured for the trunk port on both switches.

FIREWALL RULES AND ACL CONFIGURATION

Firewall access control lists (ACLs) are configured on the principle of least access. This is the same as the principle of least privilege; only allow the minimum amount of traffic required for the operation of valid network services and no more. The rules in a firewall's ACL are processed top-to-bottom. If traffic matches a rule that allows the packet, then it is allowed to pass. Consequently, the most specific rules are placed at the top. The final default rule is typically to block any traffic that has not matched a rule. This is called an implicit deny. If the firewall does not have a default implicit deny rule, an explicit deny all rule can be added manually to the end of the ACL.

Sample firewall ruleset configured on OPNsense. This ruleset blocks all traffic from bogon networks and private IP address ranges, but it allows ICMP traffic directed at a firewall interface, HTTP traffic from any source, and SMTP traffic from known networks, defined as the MAILHOSTS alias. (Screenshot used with permission from OPNsense.)

Each rule can specify whether to block or allow traffic based on parameters, often referred to as tuples. If you think of each rule being like a row in a database, the tuples are the columns. For example, in the screenshot, the tuples include Protocol, Source (address), (Source) Port, Destination (address), (Destination) Port, and so on.

As an example of ACL configuration, iptables is a command line utility provided by many Linux distributions that allows administrators to edit the rules enforced by the Linux kernel firewall. Iptables works with the firewall chains, which apply to the different types of traffic passing through the system. The three main chains are:

●	INPUT-Affecting incoming connections. For example, if a user attempts to SSH into the Linux server, iptables will attempt to match the source IP address and destination port to a rule in the input chain.

●	OUTPUT-For outgoing connections. For example, if you try to ping an FQDN such as comptia.org, iptables will check its output chain to see what the rules are regarding ping and comptia.org (or the IP address that comptia.org resolves to) before deciding to allow or deny the connection attempt.

●	FORWARD-Used for connections that are passing through the host, rather than being delivered locally. This chain would be used when configuring the host as a network firewall.

Rules can be assigned to these chains, or new chains can be created and then linked to the standard system chains to affect traffic flow. To view the current status of the iptables and the volume of traffic using the chains, use the command:

iptables -L -v

To change the firewall rules, commands such as those that follow would be used.

These examples allow one IP address from a specific subnet to connect and block all others from the same subnet.

iptables -A INPUT -s 10.1.0.1 -j ACCEPT

iptables -A INPUT -s 10.1.0.0/24 -j DROP

When you set least access rules (if both INPUT and OUTPUT default policy is set to deny all), you must set both INPUT and OUTPUT rules to allow most types of client/server traffic. For example, to allow a host to operate as an SSH server, configure the following rules:

iptables -A INPUT -p tcp --dport 22 -s 10.1.0.0/24 -m state --

state NEW,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -p tcp --sport 22 -d 10.1.0.0/24 -m state --

state ESTABLISHED -j ACCEPT

These commands use the stateful nature of the firewall to differentiate between new and established connections. The first rule allows hosts in the 10.1.0.0/24 net to initiate connections with the SSH server on the local host over port 22. The second rule allows the server to respond to existing connections established by hosts in the same subnet.

CONTROL PLANE POLICING

The quality of service (QoS) stack distinguishes three operational layers: control, data, and management. A network appliance uses minimal resources to process ordinary data traffic, which is often processed by dedicated hardware (one or more ASIC chips) and does not require the general purpose CPU. Conversely, control and management traffic requires software-based processing and is "punted" to the CPU's pipeline, requiring memory resource and processor time. The control plane comprises traffic that keeps the network itself operational, including routing updates, ARP traffic, STP notifications, NTP updates, QoS classification and link reservation requests, and so on. The management plane comprises traffic that allows remote administration and monitoring of network appliances, such as SSH, SNMP, NetFlow, and syslog. Management traffic is typically directed to the appliance's loopback address.

The network must always allow sufficient bandwidth and CPU/memory resource for control and management traffic. If this traffic is blocked, the ability of the network to function is disrupted. Worm malware or malicious reconnaissance tools may attempt to masquerade as high-priority traffic of multiple different types. This places unusually high demands on the routers and switches that process control plane traffic, effecting a DoS attack on the other functions they have to perform. This is also described as a route processor (RP) attack (though note that it can be performed against both routers and switches). Route processing can also be threatened by accidental misconfigurations.

A control plane policing policy is designed to mitigate the risk from route processor vulnerabilities. Such a policy can use ACLs to allow or deny control traffic from certain sources and apply rate-limiting if a source threatens to overwhelm the route processor.

WIRELESS SECURITY

The following features can be enabled to provision secure wireless network access.

●	Preshared keys (PSKs)-Group authentication allows stations to connect to the network using a shared passphrase, which is used to generate a preshared key (PSK). The passphrase should be sufficient length (14+ characters) to ensure a strong key.

●	Extensible Authentication Protocol-An access point can implement a similar port security mechanism to switches. This is configured on the access point by selecting enterprise authentication. This allows users to authenticate to the wireless network against a RADIUS server using their regular network credential. EAP also allows for device authentication using digital certificates.

●	Captive portal-A guest network might be configured to perform authentication by redirecting stations to a secure web page. The user must authenticate to the page and meet other administrator-set requirements, such as accepting a use policy, before the station is authorized to use the network.

●	MAC filtering-As with a switch, an access point can be configured with an accept or deny list of known MAC addresses.

●	Geofencing-Can be used to ensure that the station is within a valid geographic area to access the network, such as ensuring the device is within a building rather than trying to access the WLAN from a car park or other external location.

●	Antenna placement and power levels-Site designs and surveys facilitate robust wireless coverage when all expected areas receive a strong signal. Power levels and channel selection should be tuned so that access points do not interfere with one another or broadcast a signal that stations can "hear" but cannot reply to. The presence of an unusually strong transmitter (30 dBm+) might indicate the presence of an evil twin rogue access point.

●	Wireless client isolation-Clients connected to a WLAN are normally within the same broadcast domain and can communicate with one another. An access point can be configured to prevent this so that stations can only communicate via its gateway. Peer-to-peer traffic is dropped by the AP.

●	Guest network isolation-A guest network can have separate security and forwarding policies applied to it than the network that permits access to the corporate LAN. Typically, a guest network is permitted access to the Internet but not to local servers. Most SOHO routers come with a preconfigured guest network. Within an enterprise, a guest network would be implemented using a separate VLAN.

IOT ACCESS CONSIDERATIONS

Internet of Things (IoT) devices might be present in dedicated embedded systems and smart building networks and/or as individual smart devices installed in employee workplaces. Unmanaged access to these devices can pose a security risk so management and audit procedures must detect and secure them:

●	Perform regular audits to prevent "shadow IT" uncontrolled deployment of smart devices and appliances. This can be assisted through scanning software that specializes in identification of IoT devices, giving visibility into their deployment. Also, educate users about the risks from IoT devices and the necessity of complying with security and IT policies.

●	Ensure that administrative interfaces are secured, and that device configuration and management is assigned to appropriate organizational roles.

●	Include all IoT devices in patch and vulnerability management audits.

●	Isolate management and monitoring traffic for embedded systems to minimize access to and from the corporate data network.

●	Audit supplier security policies and procedures regularly, especially where there are external monitoring or management channels.

PATCH AND FIRMWARE MANAGEMENT

Each type of OS and applications software has vulnerabilities that present opportunities for would-be attackers. As soon as a vulnerability is identified in a supported product, the vendor will (or should) try to correct it. At the same time, attackers will try to exploit it. There can never be a single comprehensive list of vulnerabilities for each OS and app, so you must stay up to date with the system security advisories posted on vendor websites and in other security reference sources. Patch management refers to the procedures put in place to manage the installation of updates for hardware (firmware) and software.

The firmware on a device such as a router/firewall may be a very sophisticated piece of software. It is quite common for such software to have known vulnerabilities, so it is vital to use a secure version. Updating firmware is known as flashing the chip. This is generally done via a vendor-supplied setup program. It is important to make a backup of the system configuration (especially for a firewall) before performing a firmware update or upgrade.

A host OS, such as Windows, can apply patches individually. An appliance OS, such as Cisco IOS, must be patched to a particular version number by applying a new software image. To address a particular vulnerability, you could use a tool such as the IOS Software Checker (tools.cisco.com/security/center/softwarechecker.x) to identify the "first fix" version of IOS for that security advisory. This does mean that other changes could be introduced, so careful testing and impact assessment is required.

Once you have completed environment and compatibility checks and backed up the existing configuration, the basic upgrade process is to copy the new system image to the appliance's flash memory. This can be done over a network using Trivial File Transfer Protocol (TFTP) or remote file copy or by using a removable flash memory card. Once the image update is in place, you run a command sequence to replace the old image and load the new one at startup.

Most software and firmware version changes and updates are upward, toward newer versions. Downgrading (or rollback) refers to reverting to a previous version of the software or firmware. This might be necessary to fix a problem caused by a recently upgraded or updated device or software. In some circumstances downgrading might not be possible. A network appliance might not support downgrading to an earlier firmware version, for instance, or an OS might have to be reinstalled completely. When applying a patch or upgrade, it is common practice to make a configuration backup, in case settings must be reapplied after the update. When downgrading, a configuration backup might not work because it may involve settings not included in the earlier version.


Lesson 20: Summarizing Cloud and Datacenter Architecture

Topic 20A: Summarize Cloud Concepts

CLOUD SCALABILITY AND ELASTICITY

From the consumer point of view, cloud computing is a service that provides on-demand resources-server instances, file storage, databases, or applications-over a network, typically the Internet. The service is a cloud because the end user is not aware of or responsible for any details of the procurement, implementation, or management of the infrastructure that underpins those resources. The end user is interested in and pays for only the services provided by the cloud.

From the provider point of view, provisioning a cloud is like provisioning any other type of large-scale datacenter. Cloud computing almost always uses one or more methods of virtualization to ensure that resources are quickly and easily provisioned to the client who requires them.

Among other benefits, the cloud provides scalability and elasticity:

●	Scalability means that the costs involved in supplying the service to more users are linear. For example, if the number of users doubles in a scalable system, the costs to maintain the same level of service would also double (or less than double). If costs more than double, the system is less scalable. Scalability can be achieved by adding nodes (horizontal/scaling out) or by adding resources to each node (vertical/scaling up).

●	Elasticity refers to the system's ability to handle changes on demand in real time. A system with high elasticity will not experience loss of service or performance if demand suddenly doubles (or triples, or quadruples). Conversely, it may be important for the system to be able to reduce costs when demand is low.

In order to meet scalability and elasticity requirements, cloud providers must be able to provision and deprovision resources automatically. This is achieved through resource pooling and virtualization. Resource pooling means that the hardware making up the cloud provider's datacenter is not dedicated or reserved to a single customer account. The layers of virtualization used in the cloud architecture allow the provider to provision more CPU, memory, disk, or network resource using management software, rather than (for instance) having to go to the datacenter floor, unplug a server, add a memory module, and reboot.

CLOUD DEPLOYMENT MODELS

In most cases, the cloud-that is, the hardware and/or software hosting the service-will be offsite relative to the organization's users. The cloud users will typically require an Internet link to access the cloud services. There can be different ownership and access arrangements for clouds, however. These cloud deployment models can be broadly categorized as follows:

●	Public (or multitenant)-a service offered over the Internet by cloud service providers (CSPs) to cloud consumers, often referred to as tenants. With this model, businesses can offer subscriptions or pay-as-you-go financing, while at the same time providing lower-tier services free of charge. As a shared resource, there are risks regarding performance and security. Multicloud architectures are where the consumer organization uses services from more than one CSP.

●	Hosted Private-Hosted by a third party for the exclusive use of the organization. This is more secure and can guarantee a better level of performance, but it is correspondingly more expensive.

●	Private-Cloud infrastructure that is completely private to and owned by the organization. In this case, there is likely to be one business unit dedicated to managing the cloud while other business units make use of it. With private cloud computing, organizations can exercise greater control over the privacy and security of their services. This type of delivery method is geared more toward banking and governmental services that require strict access control in their operations.

This type of cloud could be on-premises or offsite relative to the other business units. An onsite link can obviously deliver better performance and is less likely to be subject to outages (loss of an Internet link, for instance). On the other hand, a dedicated offsite facility may provide better shared access for multiple users in different locations.

●	Community-This is where several organizations share the costs of either a hosted private or fully private cloud. This is usually done in order to pool resources for a common concern, like standardization and security policies.

●	Hybrid-A cloud computing solution that implements some sort of hybrid public/private/community/hosted/onsite/offsite solution. For example, a travel organization may run a sales website for most of the year using a private cloud but "break out" the solution to a public cloud at times when much higher utilization is forecast. As another example, a hybrid deployment may be used to provide some functions via a public cloud, but keep sensitive or regulated infrastructure, applications, and data on-premises.

Flexibility is a key advantage of cloud computing, but the implications for data risk must be well understood when you are moving data between private and public storage environments.

CLOUD SERVICE MODELS

As well as the deployment model-public, private, hybrid, or community-cloud services are often differentiated on the level of complexity and preconfiguration provided. These models are referred to as Something/Anything/Everything as a Service (XaaS). Some of the most common XaaS models are infrastructure, software, platforms, and desktops.

Infrastructure as a Service

Infrastructure as a Service (IaaS) is a means of provisioning IT resources such as servers, load balancers, and storage area network (SAN) components quickly. Rather than purchase these components and the Internet links they require, you rent them on an as-needed basis from the service provider's datacenter. Examples include Amazon Elastic Compute Cloud ( aws.amazon.com/ec2 ), Microsoft® Azure® Virtual Machines (azure.microsoft.com/services/virtual-machines), and OpenStack® (openstack.org).

Software as a Service

Software as a Service (SaaS) is a different model of provisioning software applications. Rather than purchasing software licenses for a given number of seats, a business would access software hosted on a supplier's servers on a pay-as-you-go or lease arrangement (on-demand). Virtual infrastructure allows developers to provision on-demand applications much more quickly than previously. The applications can be developed and tested in the cloud without the need to test and deploy on client computers. Examples include Microsoft Office 365® (support.office.com), Salesforce® (salesforce.com), and Google Workspace™ ( workspace.google.com ).

Platform as a Service

Platform as a Service (PaaS) provides resources somewhere between SaaS and IaaS. A typical PaaS solution would deploy servers and storage network infrastructure (as per IaaS) but also provide a multi-tier web application/database platform on top. This platform could be based on Oracle® or MS SQL or PHP and MySQL™. Examples include Oracle Database ( cloud.oracle.com/paas ), Microsoft Azure SQL Database (azure.microsoft.com/services/sql-database), and Google App Engine™ (cloud.google.com/appengine).

As distinct from SaaS though, this platform would not be configured to actually do anything. Your own developers would have to create the software (the CRM or e‑commerce application) that runs using the platform. The service provider would be responsible for the integrity and availability of the platform components, but you would be responsible for the security of the application you created on the platform.

Dashboard for Amazon Web Services Elastic Compute Cloud (EC2) IaaS/PaaS. (Screenshot courtesy of Amazon.)

Desktop as a Service

Desktop as a Service (DaaS) is a means of provisioning virtual desktop infrastructure (VDI) as a cloud service. VDI allows a client browser to operate an OS desktop plus software apps. This removes the need for an organization to deploy and maintain client PCs and software installs.

CLOUD CONNECTIVITY OPTIONS

Cloud connectivity is the mechanism by which clients connect to the cloud service. Connectivity with cloud-based services is always going to involve some tradeoffs but should consider price, bandwidth, latency (delay), and availability. In practical terms, there are a few options for connecting an organization's staff with cloud-based services.

Internet/Virtual Private Network

The simplest way of interfacing with a cloud service is to use the provider's website or application programming interface (API) over the Internet. This type of connection can also be implemented as a virtual private network (VPN), if this is supported by the cloud service provider. The VPN method has the advantages of being cost-effective and straightforward to set up wherever there is Internet connectivity, which is ideal for organizations that have a fragmented or distributed network structure. However, any connection running over the public Internet can suffer from poor performance due to latency and bandwidth throttling, so this would not normally be a solution for a mission critical or high-volume application.

Colocation within a datacenter offers a higher bandwidth solution by providing a direct or private link. The customer establishes infrastructure within a datacenter supported by the cloud provider or provisions a direct link from his or her enterprise network to the datacenter, possibly using private connections configured within a service provider's network. The datacenter installs a cross-connect cable or VLAN between the customer and the cloud provider, establishing a low latency, high bandwidth secure link. This solution is preferred for organizations which have a more centralized operation where the connection to the cloud can be from the main HQ and the company's own enterprise network is used to allow branch locations access.

INFRASTRUCTURE AS CODE

The use of cloud technologies encourages the use of scripted approaches to provisioning, rather than installing operating systems and apps and making configuration changes or installing patches manually. An approach to infrastructure management where automation and orchestration fully replace manual configuration is referred to as infrastructure as code (IaC).

One of the goals of IaC is to eliminate snowflake systems. A snowflake is a configuration or build that is different from any other. The lack of consistency-or drift-in the platform environment leads to security issues, such as patches that have not been installed, and stability issues, such as scripts that fail to run because of some small configuration difference.

Automation

Automation using scripting means that each configuration or build task is performed by a block of code. The script will take standard arguments as data, so there is less scope for uncertainty over configuration choices leading to errors. There are two principal types of automation tool:

●	Imperative tools require the precise steps to follow to achieve the desired configuration as input. This approach is most similar to automation through traditional scripting languages such as Bash and PowerShell.

●	Declarative tools take the desired configuration as input and leave detail of how that configuration should be achieved to the implementation platform.

Orchestration

Where automation focuses on making a single, discrete task easily repeatable, orchestration performs a sequence of automated tasks. For example, you might orchestrate adding a new VM to a load-balanced cluster. This end-to-end process might include provisioning the VM, configuring it with an app and network settings, adding the new VM to the load-balanced cluster, and reconfiguring the load-balancing weight distribution given the new cluster configuration. In doing this, the orchestrated steps would have to run numerous automated scripts or API service calls.

For orchestration to work properly, automated steps must occur in the right sequence, taking dependencies into account; it must provide the right security credentials at every step along the way; and it must have the rights and permissions to perform the defined tasks. Orchestration can automate processes that are complex, requiring dozens or hundreds of manual steps.

Automation and orchestration platforms connect to and provide administration, management, and orchestration for many popular cloud platforms and services. One of the advantages of using a third-party orchestration platform is protection from vendor lock in. If you wish to migrate from one cloud provider to another, or wish to move to a multicloud environment, automated workflows can often be adapted for use on new platforms. Industry leaders in this space include Chef (chef.io), Puppet ( puppet.com ), Ansible ( ansible.com ), and Kubernetes ( kubernetes.io ).

CLOUD SECURITY IMPLICATIONS

One of the risks of using a cloud-based solution is that potentially confidential or commercially secret data may be transferred over links that extend beyond the enterprise’s infrastructure and direct control. As such, it is imperative to identify precisely which risks you are transferring; to identify which responsibilities the service provider is undertaking, and which remain with you. This should be set out in a service level agreement (SLA) as a cloud responsibility matrix. This division of responsibility is referred to by Amazon as security of the cloud versus security in the cloud ( aws.amazon.com/compliance/shared-responsibility-model ).

For example, in a SaaS solution, the provider may be responsible for the confidentiality, integrity, and availability of the software. They would be responsible for configuring a fault tolerant, clustered server service; for firewalling the servers and creating proper authentication, authorization, and accounting procedures; for scanning for intrusions and monitoring network logs; applying OS and software patches; and so on. You may or may not be responsible for some or all of the software management functions, such as ensuring that administrators and users practice good password management, configuring system privileges, making backups of data, and so on. Where critical tasks are the responsibility of the service provider, you should try to ensure that there is a reporting mechanism to show that these tasks are being completed, that their disaster recovery plans are effective, and so on.

Another provision is that your company is likely to remain directly liable for serious security breaches. If customer data is stolen, for instance, or if your hosted website is hacked and used to distribute malware, the legal and regulatory "buck" still stops with you. You might be able to sue the service provider for damages, but your company would still be the point of investigation. You may also need to consider the legal implications of using a cloud provider if its servers are in a different country.

You must also consider the risk of insider threat, where the insiders are administrators working for the service provider. Without effective security mechanisms, such as separation of duties, it is possible that they would be able to gain privileged access to your data. Consequently, the service provider must be able to demonstrate to your satisfaction that they are prevented from doing so. There is also the risk that your data is in proximity to other, unknown virtual servers and that some sort of attack could be launched on your data from another virtual server.

Topic 20B: Explain Virtualization and Storage Area Network Technologies

HYPERVISOR TYPES

In a virtualization host, the hypervisor-or virtual machine monitor (VMM)-manages the virtual environment and facilitates interaction with the computer hardware and network. One basic distinction that can be made between virtual platforms is between host and bare metal methods of interacting with the host hardware. In a guest OS (or host-based) system, the hypervisor application (known as a Type II hypervisor) is itself installed onto a host operating system. Examples of host-based hypervisors include VMware Workstation™, Oracle® Virtual Box, and Parallels® Workstation. The hypervisor software must support the host OS.

Guest OS virtualization (Type II hypervisor). The hypervisor is an application running within a native OS, and guest OSes are installed within the hypervisor.

A bare metal virtual platform means that a Type I hypervisor is installed directly onto the computer and manages access to the host hardware without going through a host OS. Examples include VMware ESXi® Server, Microsoft's Hyper-V®, and Citrix's XEN Server. The hardware needs to support only the base system requirements for the hypervisor plus resources for the type and number of guest OSes that will be installed.

Type I bare metal hypervisor. The hypervisor is installed directly on the host hardware along with a management application, then VMs are installed within the hypervisor.

VIRTUAL NICS AND SWITCHES

Where multiple VMs are running on a single platform, virtualization provides a means for these VMs to communicate with each other and with other computers on the network (both physical and virtual) by using standard networking protocols. The guest OS running in each virtual machine is presented with an emulation of a standard hardware platform. Among the hardware devices emulated will be one or more network adapters. The number of adapters and their connectivity can be configured via the hypervisor.

Within the VM, the virtual NIC (vNIC) will look exactly like an ordinary network adapter and will be configurable in the same way. For example, protocols and services can be bound to it, it has a MAC address, and it can be assigned IPv4 and/or IPv6 addresses. In other words, a virtual NIC functions identically to a physical NIC for data transmission; it is just wholly software-based instead of being a combination of physical hardware, firmware, and driver software.

Typically, a hypervisor will implement network connectivity by means of one or more virtual switches (or vSwitch in VMware's terminology). These perform the same function as Layer 2 physical switches, except that they are implemented in software instead of hardware. Connectivity between the virtual network adapters in the guest VMs and the virtual switches is configured via the hypervisor. This is analogous to connecting patch cables between real computers and real switches.

In this networking model, the VMs and the virtual switch can all be contained within a single hardware platform, so no actual network traffic is generated; instead, data is moved from buffers in one VM to another. It is also possible to configure connectivity with a virtual switch that bridges the virtual and physical networks via the host computer's physical NIC. For example, in Microsoft's Hyper-V virtualization platform, three types of virtual switches can be created:

●	External-Binds to the host's NIC to allow the VM to communicate on the physical network.

●	Internal-Creates a bridge that is usable only by VMs on the host and the host itself. This type of switch does not permit access to the wider physical network.

●	Private-Creates a switch that is usable only by the VMs. They cannot use the switch to communicate with the host.

Configuring a virtual switch in Microsoft's Hyper-V hypervisor. The external switch allows the VM to use the physical network via the host's NIC. The private switches have no external access. (Screenshot used with permission from Microsoft.)

When the VMs are permitted to interact with a "real" network, the host must support a high bandwidth, high availability network link. Any failure of the physical link will affect multiple VMs.

Virtual switches can be as simple or complex as the hypervisor software makes them. For example, they can be used to implement VLANs or be configured to perform port mirroring. In a more advanced network, such as VMware's vSphere, you could also have virtual switches that can connect guests running on multiple hosts and configure advanced switching, such as QoS and traffic shaping.

NETWORK FUNCTION VIRTUALIZATION

When a VM is joined to a virtual switch, the MAC address for its virtual NIC is configured via the hypervisor. The VM must be configured with an appropriate IP address for the subnet it is in. If the VM needs a link to other networks, it must be assigned a default gateway. You might also want to configure security for the network link, such as implementing a firewall. None of the requirements of a virtual network are different than physical networks.

You can configure the VM's IP parameters statically, or you can use DHCP. You could provision a DHCP server as a VM on the virtual network, or the VM could use the physical network's DHCP server. With some types of virtual switches that bridge VMs to the physical network, the hypervisor can implement a DHCP and/or network address translation (NAT) service to VMs.

You must also provision DNS and time synchronization services for the virtual network.

Any guest Linux or Windows Server VM can be configured as a router for a VM network. Similarly, either OS (or third-party software installed under the guest VM) could be used to implement a firewall. The VMs have the same functionality as software installed on real computers.

It is also possible to provision virtual appliances. With a virtual appliance, the vendor either develops a software product that emulates the functions of an existing dedicated hardware appliance (router, firewall, load balancer, or malware/intrusion detection, for instance) or creates software that implements that kind of functionality in a new product. These virtual appliances might be developed against a standard architecture, such as ETSI's Network Function Virtualization (NFV). NFV divides the provisioning of these appliances into three domains:

●	Virtual Network Function (VNF)-Specifies and deploys instances of each virtual appliance. VNFs are designed to run as VMs on standard CPU platforms.

●	NFV infrastructure-Controls the allocation of compute (CPU and memory) plus storage and networking resources to each VNF.

●	Management and orchestration (MANO)-Positions VNFs within workflows to perform the forwarding and filtering tasks they are designed for.

STORAGE AREA NETWORKS

A storage area network (SAN) provisions access to storage devices at block level. Each read or write operation addresses the actual location of data on the media (Block I/O). A SAN is isolated from the main network. It is only accessed by servers, not by client PCs and laptops. SAN clients are servers running databases or applications that require access to shared storage.


Storage area network. (Images © 123RF.com.)

A SAN can integrate different types of storage technology-RAID arrays and tape libraries, for instance. It can contain a mixture of high-speed and low-cost devices, allowing for tiered storage to support different types of file access requirements without having to overprovision high-cost, fast drives.

SAN CONNECTION TYPES

A SAN can be implemented using a variety of technologies, but the most popular are high bandwidth Fibre Channel and Fibre Channel over Ethernet fiber optic networks.

Fibre Channel

Fibre Channel is defined in the T11 ANSI standard. The British spelling "fibre" is deliberately chosen to distinguish the standard from fiber optic cabling, which it often uses but on which it does not rely. A SAN based on a Fibre Channel (FC) Switched Fabric (FC-SW) involves three main types of components:

●	Initiator-This is a client device of the SAN, such as a file or database server installed with a fibre channel host bus adapter (HBA).

●	Target-The network port for a storage device. Typical devices include single drives, RAID drive arrays, tape drives, and tape libraries. Space on the storage devices is divided into logical volumes, each identified by a 64-bit logical unit number (LUN). The initiator will use SCSI, Serial Attached SCSI (SAS), SATA, or NVMe commands to operate the storage devices in the network, depending on which interface they support. Most devices have multiple ports for load balancing and fault tolerance.

●	The initiators and targets are identified by 64-bit WorldWide Names (WWN), similar to network adapter MAC addresses. Collectively, initiators and targets are referred to as nodes. Nodes can be allocated their own WWN, referred to as a WWNN (WorldWide Node Name). Also, each port on a node can have its own WorldWide Port Name (WWPN).

●	FC switch-This provides the interconnections between initiators and targets (a fabric). The switch topology and interconnections would be designed to provide multiple paths between initiators and targets, allowing for fault tolerance and load balancing. High performance FC switches are often referred to as directors.

Fibre Channel can use rates from 1GFC (1 Gbps) up to 128GFC. Using fiber optic cabling, an FC fabric can be up to 10 km (6 miles) in length using single mode cable or 500 m (1640 ft) using multimode cable.

Fibre Channel over Ethernet

Provisioning separate Fibre Channel adapters and cabling is expensive. As its name suggests, Fibre Channel over Ethernet (FCoE) is a means of delivering Fibre Channel packets over Ethernet cabling and switches. FCoE requires special 10/40/100G adapters that combine the function of NIC and HBA, referred to as converged network adapters (CNAs). FCoE uses a special frame type, identified by the EtherType value 0x8096. The protocol maps WWNs onto MAC addresses.

FCoE does not quite run over standard Ethernet. It requires QoS mechanisms to ensure flow control and guaranteed delivery. FCoE compliant products are referred to as lossless Ethernet, Datacenter Ethernet, or Converged Enhanced Ethernet.

ISCSI

Internet Small Computer System Interface (iSCSI) is an IP tunneling protocol that enables the transfer of SCSI data over an IP-based network. iSCSI works with ordinary Ethernet network adapters and switches.

Configuring a Linux host as an iSCSI target.

iSCSI can be used to link SANs but is also seen as an alternative to Fibre Channel itself, as it does not require FC-specific switches or adapters. iSCSI initiator and target functions are supported by both Windows Server and Linux operating systems.

Connecting to an iSCSI target using an iSCSI initiator in Windows Server. (Screenshot used with permission from Microsoft.)

Topic 20C: Explain Datacenter Network Architecture

DATACENTER NETWORK DESIGN

A datacenter is a site that is dedicated to provisioning server resources. The datacenter hosts network services (such as authentication, addressing, and name resolution), application servers, and storage area networks (SANs). Most datacenters are housed in purpose-built facilities, but some of the concepts also apply to server rooms.

A datacenter has dedicated networking, power, climate control, and physical access control features all designed to provide a highly available environment for running critical applications. Unlike a corporate network, a datacenter contains no client PCs, other than hardened secure administrative workstations (SAWs) used solely to manage servers.

Historically, datacenters were designed to use the same three-tiered architecture as an enterprise campus network, with core, distribution, and access layer switches. The changing way that applications are designed as services making use of virtualization and on-demand instances has changed the nature of network traffic flows. These changes are reflected in different topology designs in the datacenter.

Traffic Flows

Traffic that goes to and from a datacenter is referred to as north-south. This traffic represents clients outside the datacenter making requests and receiving responses. Corporate network traffic flows are also typically north-south. A client device is located on a workgroup switch connected to a router, while the server is connected to a separate switch or VLAN. Traffic from the client to the server passes "north" from the client's switch to the router and then back "south" to the server's switch.

In datacenters that support cloud and other Internet services, most traffic is actually between servers within the datacenter. This is referred to as east-west traffic. Consider a client uploading a photograph as part of a social media post. The image file might be checked by an analysis server for policy violations (indecent or copyright images, for instance), a search/indexing service would be updated with the image metadata, the image would be replicated to servers that provision content delivery networks (CDNs), the image would be copied to backup servers, and so on. A single request to the cloud tends to cascade to multiple requests and transfers within the cloud.

Overlay Networks

The preponderance of east-west traffic complicates security design. If each of these cascading transactions were to pass through a firewall or other security appliance, it would create a severe bottleneck. These requirements are driving the creation of virtualized security appliances that can monitor traffic as it passes between servers (blogs.cisco.com/security/trends-in-data-center-security-part-1-traffic-trends). At the same time, security implementations are moving towards zero trust architectures. Zero trust implies a highly segmented network where each link between two servers must be authenticated and authorized.

An overlay network is used to implement this type of point-to-point logical link between two nodes or two networks. The overlay network abstracts the complexity of the underlying physical topology. An overlay network uses encapsulation protocols and software defined networking to create a logical tunnel between two nodes or networks. When used inside the datacenter, overlay networks are typically implemented using virtual extensible LANs (VXLANs).

SOFTWARE DEFINED NETWORKING

Cloud services require the rapid provisioning and deprovisioning of server instances and networks using automation and orchestration, plus the use of overlay networks to establish point-to-point links quickly and reliably. This means that these components must be fully accessible to scripting-representing the ideal of infrastructure as code. Software defined networking (SDN) is a model for how these processes can be used to provision and deprovision networks.

SDN Architecture

In the SDN model defined by IETF (https://datatracker.ietf.org/doc/html/rfc7426), network functions are divided into three layers. The top and bottom layers are application and infrastructure:

●	Application layer-Applies the business logic to make decisions about how traffic should be prioritized and secured and where it should be switched. This layer defines policies such as segmentation, ACLs, and traffic prioritization and policing/shaping.

●	Infrastructure layer-Devices (physical or virtual) that handle the actual forwarding (switching and routing) of traffic and imposition of ACLs and other policy configurations for security.

The principal innovation of SDN is to insert a control layer between the application layer and infrastructure layer. The functions of the control plane are implemented by a virtual device referred to as the SDN controller. Each layer exposes an application programming interface (API) that can be automated by scripts that call functions in the layer above or below. The interface between SDN applications and the SDN controller is described as the service interface or as the "northbound" API, while that between the SDN controller and infrastructure devices is the "southbound" API.

Layers and components in a typical software defined networking architecture. (Images © 123RF.com.)

Management Plane

In IETF's SDN model, there are separate forwarding (data) and operational planes at the infrastructure level. The operational plane implements device state, such as CPU and memory utilization. A management plane sits at the same level as the control plane to interface with the operational plane. This is used to implement monitoring of traffic conditions and network status.

SPINE AND LEAF TOPOLOGY

The spine and leaf topology provides better support for east-west traffic and the use of SDN and overlay networks within datacenters. A spine and leaf topology has two layers:

●	The spine layer comprises a backbone of top-tier switches. Note that while this is described as a backbone, the spine switches are not linked to one another.

●	The leaf layer contains access switches. Each access switch is connected to every spine switch in a full mesh topology. The access switches never have direct connections to one another.

Spine and leaf topology diagram. (Image © 123RF.com.)

The spine and leaf topology has a number of advantages:

●	Each server is only ever a single hop from the backbone, making network latency more predictable.

●	There are multiple redundant paths between a leaf switch and the backbone, allowing for load balancing and failover.

●	As there are no direct connections between spine switches in the backbone or between leaf switches, the network is loop free and does not need to run spanning tree. Instead, each leaf switch runs a protocol called Equal Cost Multipathing (ECMP) to distribute traffic between the links to the spine switches.

●	Servers are connected to multiple leaf switches for multipath redundancy, using a first hop gateway protocol to determine the active path.

The leaf layer access switches are implemented as top-of-rack (ToR) switch models. These are switch models designed to provide high-speed connectivity to a rack of server appliances and support higher bandwidths than ordinary workgroup switches. For example, where a workgroup switch might have 1 Gbps access ports and a 10 Gbps uplink port, top-of-rack switches have 10 Gbps access ports and 40/100 Gbps uplink ports.

DATACENTER ACCESS TYPES

As well as the internal design and configuration of the datacenter, you also need to consider the changing way that datacenter services are accessed. An on-premises datacenter is one that is located at the same site as the corporate client network that it serves. This type of datacenter would be accessed over Ethernet links, but would be placed in a separate network zone with ACLs to filter access by client systems.

Branch Office Datacenter Access

Many corporate networks are traditionally based on a hub and spoke design, where services are concentrated in a main office, or hub, but access is distributed around multiple branch offices in geographically separate locations. Branch offices may be limited in terms of low bandwidth, high latency links. This can mean having to install servers to branch locations and replicate data between them and the head office or corporate network.

The Generic Routing Encapsulation (GRE) protocol encapsulates data from layer 2 (Ethernet) or layer 3 (IP) for tunneling over any suitable transport network. Multipoint GRE (mGRE) is a version of the protocol that supports point-to-multipoint links, such as the hub and spoke dynamic multipoint VPN. This protocol is widely used to connect branch offices to an on-premises datacenter located at the head office.

Colocation

An on-premises datacenter does not have any site redundancy and is also likely to suffer from poor performance when accessed by remote offices in different countries. Establishing on-premises datacenter services for multiple geographic locations is expensive. One option is to use public cloud services where your applications and data are installed to third-party servers. This is cost-effective, but also associated with a number of risks. Colocation means that a company's private servers and network appliances are installed to a datacenter that is shared by multiple tenants. The colocation provider manages the datacenter environment; the company's servers are installed to dedicated rack space on the datacenter floor. The rack or space within a rack is locked so that only authorized keyholders can gain physical access to the server equipment.

MULTIPROTOCOL LABEL SWITCHING

VPN solutions based on mGRE/DMVPN that use the public Internet as the transport network can suffer from unpredictable performance levels. Most WAN providers offer Multiprotocol Label Switching (MPLS) as a means of establishing private links with guaranteed service levels. MPLS can operate as an overlay network to configure point-to-point or point-to-multipoint links between nodes regardless of the underlying physical and data link topologies.

MPLS topology. (Images © 123RF.com.)

For example, in this diagram, the CPE router at site 1 wants to communicate with site 4. The router is attached to the service provider's MPLS cloud via a Label Edge Router (LER). This router inserts or "pushes" a label or "shim" header into each packet sent from CPE1, and then forwards it to an LSR. Each LSR examines the shim and determines the Label Switched Path (LSP) for the packet, based on the type of data, network congestion, and any other traffic engineering parameters determined by the service provider. It uses the label, rather than the Layer 3 header, to forward the packet to its neighbor. In this way, costly routing table lookups are avoided. The shim is removed (or "popped") by the egress LER and delivered to CPE4.

MPLS allows WAN providers to offer various solutions for enterprise networking requirements. A basic use of MPLS is to create site-to-site VPNs to interconnect LANs or connect a branch office to a datacenter. The traffic passing over an MPLS VPN is isolated from any other customer or public traffic. Different sites can use any access method available (DSL, cellular, leased line, or Ethernet), and the sites can use point-to-point or multipoint topologies as required. The MPLS provider can apply traffic shaping policies to communications between enterprise LANs and the datacenter to guarantee a service level and provide link redundancy, making the connection much more reliable than one over the open Internet would be.

SOFTWARE-DEFINED WAN

The hub and branch office design with on-premises datacenters has a number of performance and reliability drawbacks. Shifting services to one or more dedicated datacenters in the cloud or using colocation mitigates some of these issues. Service availability and integrity is separated from site accessibility considerations. In this model access to the datacenter from the corporate network, branch offices, and remote/teleworker locations can be facilitated through a software-defined WAN (SD-WAN). SD-WAN replaces hub and spoke type designs with more efficient, but still secure, connectivity to corporate clouds with less of the expense associated with provisioning an MPLS service to each remote location.

In a branch office topology, access to the datacenter or the cloud would be routed and authorized via the hub office. An SD-WAN is a type of overlay network that provisions a corporate WAN across multiple locations and can facilitate secure access to the cloud directly from a branch office or other remote location. It uses automation and orchestration to provision links dynamically based on application requirements and network congestion, using IPSec to ensure that traffic is tunneled through the underlying transport networks securely. An SD-WAN solution should also apply microsegmentation and zero trust security policies to ensure that all requests and responses are authenticated and authorized.

Components in an SD-WAN solution. (Image © 123RF.com.)

The SD-WAN is managed by a controller and management software located in a corporate datacenter or public cloud. Each site has a SD-WAN capable router, gateway, or VPN app. The SDN controller orchestrates connections to networks and clouds enrolled in the SD-WAN. It uses any available IP underlay network, such as broadband Internet, 4G/5G cellular, or private MPLS VPNs to provision the fastest or most reliable available transport to networks and clouds enrolled in the SD-WAN. The controller also ensures that each access request is authenticated and authorized.

