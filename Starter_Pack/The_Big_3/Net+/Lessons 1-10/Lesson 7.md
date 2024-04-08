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
