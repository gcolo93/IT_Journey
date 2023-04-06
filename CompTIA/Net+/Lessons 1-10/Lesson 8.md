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
