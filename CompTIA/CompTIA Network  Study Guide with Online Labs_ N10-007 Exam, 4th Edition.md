**Chapter 1: Introduction to Networks**

**Networks**

Two or more connected computers that can share resources such as data and applications, office machines, an Internet connection, or a combination of these, is known as a **network.**

A **local area network (LAN)** is usually restricted to spanning a particular geographic location. It is best to split a big LAN into smaller logical zones known as **workgroups** to make administration easier.

Workgroups are physically on the same network segment.

You must be physically connected to a workgroup’s LAN to get the resources from it.

You can’t get from one LAN to another LAN and use its server data and printing resources remotely.

Hubs and switches are devices that connect other devices together into a network and routers connect networks together.

**Workstations** are often seriously powerful computers that run more than one central processing unit (CPU) and whose resources are available to other users on the network to access when needed. 

A client machine is any device on the network that can ask for access to resources like a printer or other hosts from a server or powerful workstation.

A **host** is anything that takes an IP address.

**Servers** 

Run specialized software known as the network operating system to maintain and control the network.

**File Server:** Stores and dispenses files.

**Mail Server:** The network’s post office; handles email functions.

**Print Server:** Manages printers on the network.

**Web Server:** Manages web-based activities by running Hypertext Transfer Protocol (HTTP) for storing web content and accessing web pages.

**Fax Server:** The “memo maker” that sends and receives paperless faxes over the network.

**Application Server:** Manages network applications.

**Telephony Server:** Handles the call center and call routing and can be thought of as a sophisticated network answering machine.

**Proxy Server:** Handles tasks in the place of other machines on the network, particularly an internet connection.

Servers can provide resources to a larger number of individual users at the same time but workstations cannot.

**WAN (Wide Area Network)** networks are what we use to span large geographic areas. WANs usually employ both routers and public links.

Differences between WANs and LANs:

- WANs usually need a router port or ports.
- WANs span larger geographic areas and/or can link disparate locations.
- WANs are usually slower.
- We can choose when and how long we can connect to a WAN. A LAN is all or nothing - our workstation is connected to it either permanently or not at all, although most of us have dedicated WAN links now.
- WANs can utilize either private or public data transport media such as phone lines.

**Multiprotocol Label Switching (MPLS)** 

This has become one of the most innovative and flexible networking technologies on the market, and it has some key advantages over other WAN technologies:

- Physical layout flexibility
- Prioritizing of data
- Redundancy in case of link failure
- One-to-many connection.

MPLS is a switching mechanism that imposes labels (numbers) to data and then uses those labels to forward data when it arrives at the MPLS network.

The labels are assigned on the edge of the MPLS network, and forwarding inside the MPLS network (cloud) is done solely based on labels through virtual links instead of physical links.

Computers connected together in a **peer-to-peer network** do not have any central, or special, authority - they’re all peers, meaning that when it comes to authority, they’re all equals. The authority to perform a security check for proper access rights lies with the computer that has the desired resource being requested from it.

If your network is running Windows, Mac, or Unix in a local LAN workgroup, you have a peer-to-peer network.

**Client-server networks** use a network operating system for managing the whole network. A client machine’s request for a resource goes to the main server, which responds by handling security and directing the client to the desired resource. This happens instead of the request going directly to the machine with the desired resource, and it has some advantages. It is easier to find resources because everything is stored in one spot. Security also gets tighter because all usernames and passwords are on a specific server that is never used as a workstation 

The **physical topology** of a network is a type of map. It defines the specific characteristics of a network, such as where all the workstations and other devices are located and the precise arrangement of all the physical media such as cables. **Logical network topologies** delineate exactly how data moves through a network. A network can have both physical and logical topologies. A physical topology gives the lay of the land, and logical topologies show how a digital signal or data navigates through that layout.

**Bus Topology**

The bus topology consists of two distinct and terminated ends, with each of its computers connecting to one unbroken cable running its entire length. Even though all computers on this kind of network see the data flowing through the cable, only the one computer, which the data is specifically addressed to, actually gets the data.

Some of the benefits of using a bus topology are that it’s easy to install and it’s not very expensive, partly because it doesn’t require as much cable as the other types of physical topologies. Some of the drawbacks are that it’s hard to troubleshoot, change, or move, and it doesn’t offer much in the way of fault tolerance because everything is connected to a single cable.

**Fault tolerance** is the capability of a computer or a network system to respond to a condition automatically , often resolving it, which reduces the impact on the system. If fault-tolerance measures have been implemented correctly on a network, it’s highly unlikely that any of that network’s users will know that a problem ever existed at all.

**Star Topology**

A star topology’s computers are connected to a central point with their own individual cables or wireless connections. The central spot is often inhabited by a device like a hub, a switch, or an access point.

One of its best features is that because each computer or network segment is connected to the central device individually, if the cable fails, it only brings down the machine or network segment related to the point of failure. This makes the network much more fault tolerant as well as a lot easier to troubleshoot. Star topologies are a lot more scalable - all you have to do if you want to add to it is run a new cable and connect to the machine at the core of the star.

Benefits of a star topology:

- New stations can be added or moved easily and quickly
- A single cable failure won’t bring down the entire network.
- It’s relatively easy to troubleshoot.

Disadvantages of a star topology:

- The total installation cost can be higher because of the larger number of cables, even though prices are becoming more competitive.
- It has a single point of failure - the hub or other central device.

There are two more sophisticated implementations of a star topology. The first is called a **point-to-point link**, where you have not only the device in the center of the spoke acting as a hub but also the device on the other end, which extends the network. This is still a star-wired topology, but gives much more scalability.

Another refined version is the wireless version, but to understand this variety well, you’ve got to have a solid grasp of all the capabilities and features of any devices populating the wireless star topology. Access points are pretty much just wireless hubs or switches that behave like their wired counterparts.

**Ring Topology**

Each computer is directly connected to other computers within the same network. The ring topology has a lot in common with the bus topology because if you want to add to the network, you have no choice but to break the cable ring, which is likely to bring down the entire network.

It is pricey because you need several cables to connect each computer, it’s really hard to reconfigure, and it’s not fault tolerant. 

You may find a physical ring topology still in use for a technology called SONET or some other WAN technology.

**Mesh Topology**

There’s a path from every machine to every other one in the network. You won’t find this used in LAN’s very often but instead find a modified version of it known as a **hybrid mesh**, which is used in a restrained manner on WAN’s including the internet.

Often, hybrid mesh topology networks will have quite a few connections between certain places to create redundancy (backup). And other types of topologies can sometimes be found in the mix, which is another reason it’s dubbed hybrid. It isn’t a full on mesh topology if there isn’t a connection between all devices in the network.

Everything becomes more and more complex as the wiring and connections multiply. For each n locations or hosts, you end up with n(n-1)/2 connections. Small networks typically used this topology the best. There is a good level of fault tolerance, but mesh isn’t used in corporate LANs anymore because they were so complicated to manage.

A full mesh physical topology is least likely to have a collision, which happens when the data from two hosts trying to communicate simultaneously “collides” and gets lost.

**Point-to-point Topology**

In a point-to-point topology you have a direct connection between two routers or switches, giving you one communication path. The routers in a point-to-point topology can be linked by a serial cable, making it a physical network, or if they’re located far apart and connected only via a circuit within a Frame Relay or MPLS network, it’s a logical network instead.

**Point-to-Multipoint Topology**

A point-to-multipoint topology consists of a succession of connections between an interface on one router and multiple destination routers - one point of connection to multiple points of connection. Each of the routers and every one of their interfaces involved in the point-to-multipoint connection are part of the same network.

**Hybrid Topology**

Hybrid topology means a combination of two or more types of physical or logical network topologies working together within the same network.

**Topology Selection, Backbones, and Segments**

Choosing the right topology for the right network:

- Cost
- Ease of installation
- Ease of maintenance
- Fault-tolerance requirement
- Security requirement

**The Network Backbone**

The backbone of a network is what all of the network segments and servers connect to and what gives the network its structure. The backbone must use some kind of fast, robust technology - often Gigabit Ether. And to optimize network performance, - its speed and efficiency - it follows that you would want to connect all of the network’s servers and segments directly to the network’s backbone.

**Network Segments**

A segment is any small section of the network that may be connected to, but isn't actually a piece of, the backbone. The networks workstations and servers organized into segments connect to the network backbone, which is the common connecting point for all segments.

**CAN**

A campus area network (CAN) refers to a network that encompasses several buildings. It comprises the part of the network where data, services and connectivity to the outside world is provided to those who work in the corporate office or headquarters.

**SAN**

Classic Storage area networks (SANs) are comprised of high-capacity storage devices that are connected by a high-speed private network (separate from the LAN) using a storage-specific switch. This storage information architecture addresses the collection of data, management of data, and use of data. These networks are typically fiber networks.

**Chapter 2: The Open Systems Interconnection Specifications**

**Internetworking Models**

The OSI model is the primary architectural model for networks. It describes how data and network information are communicated from an application on one computer through the network media to an application on another computer. The OSI reference model breaks this approach into layers.


**The Layered Approach**

A reference model is a conceptual blueprint of how communications should take place. It addresses all the processes required for effective communication and divides these processes into logical groupings called layers. When a communication system is designed in this manner, it’s known as layered architecture.

**Advantages of Reference Models**

The OSI model is hierarchical, and the same beneficial characteristics can apply to any layered model. 

- The OSI model divides network communication processes into smaller and simpler components, thus aiding component development, design, and troubleshooting.
- It allows multiple-vendor development through the standardization of network components.
- It encourages industry standardization by defining the specific functions that occur at each layer of the model.
- It allows various types of network hardware and software to communicate.
- It prevents changes in one layer from affecting other layers, facilitating development and making application programming much easier.

**The OSI Reference Model**

The seven layers:

- Application (Layer 7)
- Presentation (Layer 6)
- Session (Layer 5)
- Transport (Layer 4)
- Network (Layer 3)
- Data Link (Layer 2)
- Physical (Layer 1)

The top three layers define the rules of how the applications working within host machines communicate with each other as well as with end users. The bottom four layers define how the actual data is transmitted from end to end.

**The Application Layer**

The application layer of the OSI model marks the spot where users actually communicate or interact with the computer. Technically, users communicate with the network stack through application processes, interfaces, or APIs that connect the application in use to the operating system of the computer. The application layer chooses and determines the availability of communicating partners along with the resources necessary to make their required connections. It coordinates partnering applications and forms a consensus on procedures for controlling data integrity and error recovery. The application layer comes into play only when it’s apparent that access to the network will be needed soon. The application layer acts as an interface between the application program - which isn’t part of the layered structure - and the next layer down by providing ways for the application to send information down through the protocol stack. 

This layer is also responsible for identifying and establishing the availability of the intended communication partner and determining whether sufficient resources for the requested communication exist.

**The Presentation Layer**

The presentation layer presents data to the Application layer and is responsible for data translation and code formatting. A successful data-transfer technique is to adapt the data into a standard format before transmission. By providing translation services, the Presentation layer ensures that the data transferred from one system’s Application layer can be read and understood by the Application layer on another system.

Tasks like data compression, decompression, encryption, and decryption are all associated with this layer.

**The Session Layer**

This layer is responsible for setting up, managing, and then tearing down sessions between presentation layer entities. This layer also provides dialog control between devices, or nodes. It coordinates communication between systems and serves to organize their communication by offering three different modes: **simplex, half duplex, and full duplex.** The Session layer basically keeps applications’ data separate from other applications’ data.

**The Transport Layer**

This layer segments and reassembles data into a data stream. Services located in the Transport layer handle data from upper-layer applications and unite it onto the same data stream. They provide end-to -end data transport services and can establish a logical connection between the sending host and destination host on an internetwork.

The transport layer is responsible for providing the mechanisms for multiplexing upper-layer applications, establishing virtual connections, and tearing down virtual circuits. It also hides the many and sundry details of any network-dependent information from the higher layers, facilitating transfer.

The term **reliable networking** relates to the Transport layer and means that acknowledgements, sequencing, and flow control will be used.

**Connection-Oriented Communication**

Before a transmitting host starts to send segments down the model, the sender’s TCP process contacts the destination’s TCP process to establish a connection. The resulting creation is known as a **virtual circuit.** This type of communication is called **connection-oriented.** During this initial handshake, the two TCP processes also agree on the amount of information that will be sent in either direction before the respective recipient’s TCP sends back an acknowledgement.

Both of the host’s application programs begin by notifying their individual operating systems that a connection is about to be initiated. The two operating systems communicate by sending messages over the network confirming that the transfer is approved and that both sides are ready for it to take place. After all of this required synchronization occurs, a connection is fully established and the data transfer begins. This virtual circuit setup is called **overhead.**

**Three-way Handshake**

- The first “connection agreement” segment is a request for synchronization.
- The next segments acknowledge the request and establish connection parameters - the rules - between hosts. These segments request that the receiver’s sequencing is synchronized here as well so that a bidirectional connection is formed.
- The final segment is also an acknowledgment. It notifies the destination host that the connection agreement has been accepted and that the connection has been established. Data transfer can now begin.

The process is also described as: SYN, SYN/ACK, ACK or synchronize, synchronize-acknowledgement, acknowledgement.

**Flow Control**

Data integrity is ensured at the Transport layer by maintaining **flow control** and by allowing users to request reliable data transport between systems. Flow control provides a means for the receiver to govern the amount of data sent by the sender. It prevents a sending host on one side of the connection from overflowing the buffers int he receiving host - an event that can result in lost data. Reliable data transport employs a connection-oriented communications between systems, and the protocols involved ensure that the following will be achieved:

- The segments delivered are acknowledged back to the sender upon their reception.
- Any segments not acknowledged are retransmitted.
- Segments are sequenced back into their proper order upon arrival at their destination.
- A manageable data flow is maintained in order to avoid congestion, overloading, and data loss.

A **buffer** is a memory section that stores datagrams that flood a machine too quickly for it to process. Buffering can only solve the problem if the datagrams are part of a small burst. If not, and the datagram deluge continues, a device’s memory will eventually be exhausted, its flood capacity will be exceeded, and it will react by discarding any additional datagrams that arrive.

The transport can issue a “not ready” indicator to the sender, or source, of the flood, instead of dumping resources and allowing data to be lost. Once the receiving machine processes segments it will send a “ready” transport indicator, allowing transmissions to resume.

A service is considered connection-oriented if it has the following characteristics:

- A virtual circuit is set up (such as a three-way handshake).
- It uses sequencing.
- It uses acknowledgements.
- It uses flow control

**Windowing**

The quantity of data segments (measured in bytes) that the transmitting machine is allowed to send without receiving an acknowledgment is represented by something called a **window.** Windows are used to control the amount of outstanding, unacknowledged data segments.

The size of the window controls how much information is transferred from one end to the other. Some protocols quantify information by observing the number of packets, TCP/IP measures it by counting the number of bytes.

If a receiving host fails to receive all the segments that it should acknowledge, the host can improve the communication session by decreasing the window size.

**Acknowledgements**

Reliable data delivery ensures the integrity of a data stream being sent from one machine to the other through a fully functional data link. It guarantees that the data won’t be duplicated or lost. This is achieved through **positive acknowledgment with retransmission** - a technique that requires a receiving machine to communicate with the transmitting source by sending an acknowledgment message back to the sender when it receives data. The sender documents each segment it sends and waits for the acknowledgment before sending the next segment. When it sends a segment, the transmitting machine starts a timer and retransmits if it expires before an acknowledgment is returned from the receiving end.

**Devices Used in an Internetwork**

These following network devices operate at all seven layers of the OSI model:

- Network Management Stations (NMSs)
- Web and application servers
- Gateways (not default gateways)
- Network hosts

Several devices operate primarily at the Physical layer of th eOSI model. These devices manipulate mainly the physical aspects of a network data stream - things like voltages, signal direction, and signal strength. These devices are the most popular:

- Network Interface Cards (NICs)
- Transceivers
- Repeaters
- Hubs

**The Network Layer**

This layer manages logical device addressing, tracks the location of devices on the network, and determines the best way to move data. The traffic is between devices that aren’t locally attached. Routers are Layer 3 devices that are specified at the Network layer and provide the routing services within an internetwork.

There are two types of packets used at the network layer:

- **Data packets:** These are used to transport user data through the internetwork. Protocols used to support data traffic are called **routed protocols.** Examples are IP and IPv6.
- **Route update packets:** Used to update neighboring routers about the networks connected to all routers within the internetwork. Protocols that send route-update packets are called routing protocols, and some coming ones are Routing Information Protocol (RIP), RIPv2, Enhanced Interior Gateway Routing Protocol (EIGRP), and Open Shortest Path First (OSPF).

**Network Addresses:** A router must maintain a routing table for individual routing protocols because each routing protocol keeps track of a network that includes different addressing schemes, like IP and IPv6. 

**Interface:** The exact interface a packet will take when destined for a specific network.

**Metric:** This value equals the distance to the remote network. Different routing protocols use different ways of computing this distance. Some routing protocols, namely RIP, use something called a **hop count** - the number of routers a packet passes through en route to a remote network. Other routing protocols alternatively use bandwidth, delay of the line, and something known as tick count, which equals 1/18 of a second, to make routing decisions.

Routers break up broadcast domains, which means by default, broadcast’s aren’t forwarded through a router. This is a good thing because it reduces traffic on the network. Routers also break up collision domains, but this can be accomplished using Layer 2 switches as well.

Routers breakup broadcast domains, switches break up collision domains.

Because each interface in a router represents a separate network, it must be assigned unique network identification numbers, and each host on the network connected to that router must use the same network number.

Key points about routers:

- Routers, by default, won’t forward any broadcast or multicast packets.
- Routers use the logical address in a Network layer header to determine the next-hop router to forward the packet to.
- Routers can use access lists, created by an administrator, to control security on the types of packets that are allowed to enter or exit an interface.
- Routers can provide Layer 2 bridging functions if needed and can simultaneously route through the same interface.
- Layer 3 devices (routers, in this case) provide connections between virtual LANs (VLANs)
- A router can also be referred to as a Layer 3 switch. These terms are interchangeable.

**The Data Link Layer**

This layer provides the physical transmission of the data and handles error notification, network topology, and flow control. This means the Data Link layer ensures that messages are delivered to the proper device on a LAN using hardware (MAC) addresses and translates messages from the Network layer into bits for the Physical layer to transmit.

The data link layer formats the message into pieces, each called a **data frame**, and adds a customized header containing the destination and source hardware addresses. This added information forms a sort of capsule that surrounds the original message.

Routers which work at the network layer, don’t care where a particular host is located. They’re only concerned about where networks are located and the best way to reach them - including remote ones. The data link layer is responsible for the unique identification of each device that resides on a local network.

For a host to send packets to individual hosts on a local network as well as transmit packets between routers, the data link layer uses hardware addressing. Each time a packet is sent between routers, it’s framed with control information at the data link layer. However, that information is stripped off at the receiving router, and only the original packet is left completely intact. This framing of the packet continues for each hop until the packet is finally delivered to the correct receiving host. It’s important to understand that the packet itself is never altered along the route; it’s only encapsulated with the type of control information required for it to be properly passed on to the different media types.

The IEEE Ethernet Data Link layer has two sublayers:

- **Media Access Control (MAC):** Defines how packets are placed on the media. contention media access is “first come, first served” access, where everyone shares the same bandwidth. Physical addressing is defined here, as are logical topologies. A logical topology is the signal path through a physical topology. Line discipline, error notification (not correction), ordered delivery of frames, and optional flow control can also be used at this sublayer.
- **Logical Link Control (LLC):** Responsible for identifying Network layer protocols and then encapsulating them, an LLC header tells the Data LInk layer what to do with a packet once a frame is received. A host receives a frame and looks in the LLC header to find out where the packet is destined - say, the IP protocol at the Network Layer. The LLC can also provide flow control and sequencing of control bits.

**Project 802**

One of the major components of the Data Link layer is the result of the IEEE’s 802 subcommittees and their work on standards for local area and metropolitan area networks (LANs/MANs). The committee met in February 1980, so they used the 80 from 1980 and then the 2 from the second month to create the name Project 802. The designation for an 802 standard always includes a dot (.) followed by either a single or double digit. These numeric digits specify particular categories within the 802 standard.

- 801.1: LAN/MAN Management (and Media Access Control Bridges)
- 802.2: Logical Link Control
- 802.3: CSMA/CD (Ethernet)
- 802.4: Token Passing Bus
- 802.5: Token Passing Ring
- 802.6: Distributed Queue Dual Bus (DQDB) Metropolitan Area Network (MAN)
- 802.7: Broadband Local Area Networks
- 802.8: Fiber Optic LANs and MANs
- 802.9: Isochronous LANs
- 802.10: LAN/MAN Security
- 802.11: Wireless LAN
- 802.12: Demand Priority Access Method
- 802.15: Wireless Personal Area Network
- 802.16: Wireless Metropolitan Area Network (also called WiMAX)
- 802.17: Resilient Packet Ring

**The Physical Layer**

This layer sends bits and receives bits. Bits come only in values of 1 or 0 - a Morse code with numerical values. The physical layer communicates directly with the various types of actual communication media. Different kinds of media represent these bit values in different ways. Specific protocols are needed for each type of media to describe the proper bit patterns to be used, how data is encoded into media signals, and the various qualities of the physical media’s attachment interface.

The physical layer specifies the electrical, mechanical, procedural, and functional requirements for activating, maintaining, and deactivating a physical link between end systems. This layer is also where you identify the interface between the **data terminal equipment(DTE)** and the **data communication equipment (DCE).** The DCE is usually located at the customer, whereas the DTE is the attached device. The services available to the DTE are most often accessed via the DCE device, which is a modem or **channel service unit/data service unit(CSU/DSU).**

This layer specifies the layout of the transmission media, otherwise known as its topology. 

**Introduction to Encapsulation**

When a host transmits data across a network to another device, the data goes through **encapsulation:** It’s wrapped with protocol information at each layer of the OSI model. Each layer communicates only with its peer layer on the receiving device.

To communicate and exchange information, each layer uses **Protocol Data Units (PDUs).** These hold the control information attached to the data at each layer of the model. They’re usually attached to the header in front of the data field but can also be in the trailer, or end of it.

At a transmitting device, the data-encapsulation method works as such:

- User information is converted to data for transmission on the network.
- Data is converted to segments, and a reliable connection is setup between the transmitting and receiving hosts.
- Segments are converted to packets or datagrams, and a logical address is placed in the header so each packet can be routed through an internetwork. A packet carries a segment of data.
- Packets or datagrams are converted to frames for transmission on the local network. Hardware (Ethernet) addresses are used to uniquely identify hosts on a local network segment. Frames carry packets.
- Frames are converted to bits, and a digital encoding and clocking scheme is used.

**Modulation Techniques**

Modulation is the process of varying one or more properties of a waveform, called the **carrier signal**, with a signal that typically contains information to be transmitted.

Modulation of a waveform transforms a baseband (Ethernet or wireless) message signal into a passband signal (a passband [a band-pass filtered signal] is the range of frequencies or wavelengths that can pass through a filter without being attenuated). 

A modulator is a device that performs modulation of a signal and a demodulator is a device that performs demodulation, the inverse of modulation. We typically just call these modems, which can perform both operations.

The purpose of digital modulation is to transfer a digital bit stream over an analog bandpass channel. The purpose of an analog modulation is to transfer an analog baseband (or lowpass) signal over an analog bandpass channel at a different frequency.

Analog and digital modulation use something called frequency-division multiplexing (FDM), where several low-pass information signals are transferred simultaneously over the same shared physical network, using separate passband channels (several different frequencies).

Baseband means that the signal being modulated uses the complete available bandwidth.

Time-division multiplexing (TDM) is a method of transmitting and receiving many independent signals over a common signal path by means of synchronized network devices at each end of the transmission line so that each signal appears on the line only a fraction of time in an alternating pattern. The receiving end demultiplexes the signal back to its original form.

**Chapter 3: Networking Topologies, Connectors, and Wiring Standards**

**Physical Media**

- Coaxial
- Twisted-pair
- Fiber optic

**Coaxial Cable**

Also referred to as coax, it contains a center conductor made of copper that’s surrounded by a plastic jacket with a braided shield over it. A plastic such as polyvinyl chloride (PVC) or fluoroethylene propylene (FEP, commonly known as teflon) covers this metal shield. The Teflon-type covering is frequently referred to as a **plenum-rated coating.** This is expensive but often mandated by local or municipal fire code when cable is hidden in walls and ceilings.

The National Fire Protection Association (NFPA) demands that cables run within the plenum space have been tested and guaranteed as safe. They must be fire retardant and create little or no smoke and poisonous gas when burned. 

**Thin Ethernet**, also referred to as Thinnet or 10Base2, is a thin coaxial cable. The cable is Radio Grade 58, or just RG-58. This connector resembles the coaxial connector used for cable TV, which is called an **F-type connector.**

To attach a Thinnet cable to the network, you must use a BNC connector. 

Thicknet is known as RG-8 and was about ½” in diameter, also requiring 50 ohm terminating resistors on each end of the cable. Nowadays, we use 75 ohm coax for cable TV; using coax in the Ethernet LAN world is pretty much a thing of the past, but we do use them for high-bandwidth runs in our data centers. RG-6, or CATV coax, is used in our broadband world.

**Coaxial Cable Specifications**

- RG-58 U
  - Popular Name: N/A
  - Ethernet Implementation: None
  - Type of Cable: Solid Copper
- RG-58 A/U
  - Popular Name: Thinnet
  - Ethernet Implementation: 10Base2
  - Type of Cable: Stranded Copper
- RG-8
  - Popular Name: Thicknet 
  - Ethernet Implementation: 10Base5
  - Type of Cable: Solid Copper
- RG-59
  - Popular Name: Cable television Low cost, short distance
  - Ethernet Implementation: N/A
  - Type of Cable: Solid Copper
- RG-6
  - Popular Name: Cable television, cable modems, Longer distances than RG-59; some power implementations 
  - Ethernet Implementation: N/A
  - Type of Cable: Solid Copper
- RG-62
  - Popular Name: ARCnet (obsolete)
  - Ethernet Implementation: N/A
  - Type of Cable: Solid/stranded

**F-Type**

A form of coaxial connector that is used for cable TV. It has an end that screws to tighten the connector to the interface. It resembles RG-58. An advantage of using coax cable is the braided shielding that provides resistance to electronic pollution like **electromagnetic interference (EMI), radio frequency interference (RFI),** and other types of stray electrical signals that can make their way onto a network cable and cause communication problems.

**Twisted-Pair Cable**

Consists of multiple individually insulated wires that are twisted together in pairs. Sometimes a metallic shield is placed around them, hence the name **shielded twisted-pair (STP).** Cable without outer shielding is called **unshielded twisted-pair (UTP),** and it’s used in twisted-pair Ethernet (10BaseT, 100BaseTX, 1000BaseTX) networks.

**Ethernet Cable Descriptions**

These cables are described using a code that follows this format: N <Signaling> X. The N refers to the signaling rate in megabits per second. <Signaling> stands for the signaling type - either baseband or broadband j- and the X is a unique identifier for a specific Ethernet cabling scheme.







