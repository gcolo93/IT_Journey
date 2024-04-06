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
