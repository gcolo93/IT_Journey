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