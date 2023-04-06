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