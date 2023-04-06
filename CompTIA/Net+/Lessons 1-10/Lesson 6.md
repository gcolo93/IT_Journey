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
