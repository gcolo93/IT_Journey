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
