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
