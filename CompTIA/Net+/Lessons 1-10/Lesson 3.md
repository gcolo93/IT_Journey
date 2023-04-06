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
