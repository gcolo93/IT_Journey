Lesson 14: Supporting and Troubleshooting Secure Networks

Topic 14A: Compare and Contrast Security Appliances

NETWORK SEGMENTATION ENFORCEMENT

Effective placement of security appliances depends on segmenting the network into clearly defined areas. At layers two and three, network segmentation enforcement is applied using a combination of virtual LANs and subnets. Each segment is a separate broadcast domain. Any traffic between segments must be routed. In security terms, the main unit of a logically segmented network is a zone. A zone is an area of the network where the security configuration is the same for all hosts within it. Network traffic between zones should be strictly controlled using a security device-typically a firewall.

These zones would typically be configured to protect the integrity and confidentiality of different asset groups within the organization. For example, servers storing financial records can be their own VLAN, and marketing servers could be another VLAN. If something like a remote access Trojan were introduced in one VLAN, it should not be able to spread to other VLANs without also being able to pass through the firewall protecting each zone.

One important distinction between different security zones is whether a host is Internet-facing. An Internet-facing host accepts inbound connections from the Internet. Internet-facing hosts are placed in the perimeter network zone. The basic principle of a perimeter network zone is that traffic cannot pass through it directly. A perimeter network enables external clients to access data on private systems, such as web servers, without compromising the security of the internal network.

If communication is required between hosts on either side of the perimeter network, a host within it can be configured to act as a proxy. For example, if a host on the local network requests a connection with a web server on the Internet, a proxy in the network perimeter takes the request and checks it. If the request is valid, it retransmits it to the destination. External hosts have no idea about what (if anything) is behind the perimeter.

Servers that provide public access services should be placed in a perimeter network. These would typically include web servers, mail and other communications servers, proxy servers, and remote access servers. The hosts in the perimeter are not fully trusted by the internal network because of the possibility that they could be compromised from the Internet. They are referred to as bastion hosts.

SCREENED SUBNETS

To configure a perimeter network, two different security configurations must be enabled: one on the external interface and one on the internal interface.

A screened subnet uses two firewalls placed on either side of the perimeter network zone. The edge firewall restricts traffic on the external/public interface and allows permitted traffic to the hosts in the perimeter zone subnet. The edge firewall can be referred to as the screening firewall or router. The internal firewall filters communications between hosts in the perimeter and hosts on the LAN. This firewall is often described as the choke firewall. A choke point is a purposefully narrow gateway that facilitates better access control and easier monitoring.

Screened subnet. (Images © 123RF.com.)

The screened subnet topology was formerly referred to as a demilitarized zone (DMZ). The DMZ terminology is now deprecated.

A perimeter network can also be established using one router/firewall appliance with three network interfaces, referred to as triple homed. One interface is the public one, another is the perimeter subnet, and the third connects to the LAN. Routing and filtering rules determine what forwarding is allowed between these interfaces. This can achieve the same sort of configuration as a screened subnet.

Triple-homed firewall. (Images © 123RF.com.)

FIREWALL USES AND TYPES

The basic function of a firewall is traffic filtering. The firewall processes traffic according to rules; traffic that does not conform to a rule that allows it access is blocked.

There are many types of firewalls and many ways of implementing a firewall. One distinction can be made between firewalls that protect a whole network (one that is placed inline in the network and inspects all traffic that passes through) and firewalls that protect a single host only (one that is installed on the host and inspects only that traffic addressed to that host). A further distinction can be made about what parts of a packet a particular firewall technology can inspect and operate on.

Packet Filtering Firewalls

Packet filtering describes the earliest type of firewall. All firewalls can still perform this basic function. A packet filtering firewall is configured by specifying rules in a network access control list (ACL). Each rule defines a specific type of data packet and the appropriate action to take when a packet matches the rule. An action can be either to deny (block or drop the packet, and optionally log an event) or to accept (let the packet pass through the firewall). A packet filtering firewall works at Layer 3 of the OSI model to inspect the headers of IP packets. This means that rules can be based on the information found in those headers:

●	IP filtering-Accepting or denying traffic based on its source and/or destination IP address.

●	Protocol ID/type (TCP, UDP, ICMP, routing protocols, and so on).

●	Port filtering/security-Accepting or denying a packet based on source and destination port numbers (TCP or UDP application type).

Port numbers are contained in TCP or UDP headers (layer 4), rather than the IP datagram header, but packet filtering firewalls are still almost always described as working at layer 3. They can inspect only port numbers and not any other layer 4 header information.

ACLs might be designed to control only inbound traffic or both inbound and outbound traffic. This is also often referred to as "ingress" and "egress" traffic or filtering. Controlling outbound traffic is useful because it can block applications that have not been authorized to run on the network and defeat malware, such as backdoors. Ingress and egress traffic is filtered using separate ACLs.

A packet filtering firewall is stateless. This means that it does not preserve information about the connection between two hosts. Each packet is analyzed independently with no record of previously processed packets. This type of filtering requires the least processing effort, but it can be vulnerable to attacks that are spread over a sequence of packets. A stateless firewall can also introduce problems in traffic flow, especially when some sort of load balancing is being used or when clients or servers need to make use of dynamically assigned ports.

Stateful Inspection Firewalls

A circuit-level stateful inspection firewall addresses these problems by maintaining stateful information about the session established between two hosts (including malicious attempts to start a bogus session). Information about each session is stored in a dynamically updated state table. A stateful firewall operates at Layer 5 (Session) of the OSI model. When a packet arrives, the firewall checks it to confirm whether it belongs to an existing connection. If it does not, it applies the ordinary packet filtering rules to determine whether to allow it. Once the connection has been allowed, the firewall allows traffic to pass unmonitored, in order to conserve processing effort.

State table in the OPNsense firewall appliance. (Screenshot used with permission from OPNsense.)

FIREWALL SELECTION AND PLACEMENT

You should consider how a firewall is implemented (as hardware or software, for instance) to cover a given placement or use on the network. Some types of firewalls are better suited for placement at network or segment borders; others are designed to protect individual hosts. The selection of a network firewall model will largely depend on the volume of traffic it has to process. A single firewall can represent a network bottleneck if it is not able to handle the required traffic volume.

An appliance firewall is a stand-alone hardware firewall that performs only the function of a firewall. The functions of the firewall are implemented on the appliance firmware. This is also a type of network-based firewall and monitors all traffic passing into and out of a network segment. This type of appliance could be implemented with routed interfaces or as a Layer 2/virtual wire "transparent" firewall.

Cisco ASA (Adaptive Security Appliance) ASDM (Adaptive Security Device Manager) interface. (Image © and Courtesy of Cisco Systems, Inc. Unauthorized use not permitted.)

A router firewall is similar, except that the functionality is built into the router firmware. Most SOHO Internet router/modems have this type of firewall functionality, though they are typically limited to supporting a single subnet within the home network. An enterprise-class router firewall would be able to support far more sessions than a SOHO one. Additionally, some Layer 3 switches can perform packet filtering.

PROXY SERVERS

The basic function of a network firewall is to inspect packets and determine whether to block them or allow them to pass. By contrast, a proxy server forwards requests and responses on behalf of its clients. Rather than inspecting traffic as it passes through, the proxy deconstructs each packet, performs analysis, then rebuilds the packet and forwards it on, providing it conforms to the rules. This type of device is placed in a perimeter network.

Forward Proxies

A forwarding proxy server provides for protocol-specific outbound traffic. For example, you might deploy a web proxy that enables client hosts to connect to websites and secure websites on the Internet. A proxy server must understand the application it is servicing. A web proxy must be able to parse and modify HTTP and HTTPS commands (and potentially HTML, too). Some proxy servers are application-specific; others are multipurpose. A multipurpose proxy is one configured with filters for multiple protocol types, such as HTTP, FTP, and SMTP.

The main benefit of a proxy server is that clients connect to a specified point within the perimeter network for web access. This provides for a degree of traffic management and security. In addition, most web proxy servers provide caching engines, whereby frequently requested web pages are retained on the proxy, negating the need to refetch those pages for subsequent requests.

Proxy servers can generally be classed as non-transparent or transparent. A nontransparent server means that the client must be configured with the proxy server address and port number to use it. The port on which the proxy server accepts client connections is often configured as port 8080. A transparent (or "forced" or "intercepting") proxy intercepts client traffic without the client having to be reconfigured. A transparent proxy must be implemented on a switch or router or other inline network appliance.

Configuring transparent proxy settings for the proxy server running on the OPNsense security appliance. (Screenshot used with permission from OPNsense.)

Reverse Proxies

A reverse proxy server provides for protocol-specific inbound traffic. For security purposes, it is inadvisable to place application servers, such as messaging and VoIP servers, in the perimeter network, where they are directly exposed to the Internet. Instead, you can deploy a reverse proxy and configure it to listen for client requests from a public network (the Internet) and create the appropriate request to the internal server on the corporate network.

Reverse proxies can publish applications from the corporate network to the Internet in this way. In addition, some reverse proxy servers can handle the encryption/decryption and authentication issues that arise when remote users attempt to connect to corporate servers, reducing the overhead on those servers. Typical applications for reverse proxy servers include publishing a web server, publishing messaging or conferencing applications, and enabling POP/IMAP mail retrieval.

NETWORK ADDRESS TRANSLATION

Network Address Translation (NAT) was devised as a way of freeing up scarce IP addresses for hosts needing Internet access. NAT is a service translating between a private (or local) addressing scheme used by hosts on the LAN and a public (or global) addressing scheme used by an Internet-facing device. NAT is configured on a border device, such as a router, proxy server, or firewall. NAT is not a security mechanism; security is provided by the router/firewall's ACL.

In a basic NAT static configuration, a simple 1:1 mapping is made between the private (inside local) network address and the public (inside global) address. If the destination network is using NAT, it is described as having outside global and outside local addressing schemes.

Basic NAT is useful in scenarios where an inbound connection to a host must be supported. For example, you might position a web server behind a firewall running NAT. The firewall performs 1:1 address translation on the web server's IP address. This means that external hosts do not know the true IP address of the web server, but they can communicate with it successfully.

Network Address Translation (NAT). (Images © 123RF.com.)

A single static mapping is not very useful in most scenarios. Under dynamic NAT, the NAT device exposes a pool of public IP addresses. To support inbound and outbound connections between the private network and the Internet, the NAT service builds a table of public to private address mappings. Each new session creates a new public-private address binding in the table. When the session is ended or times out, the binding is released for use by another host.

Defining NAT rules in Cisco Adaptive Security Appliance (ASA). (Screenshot used with permission from Cisco.)

PORT ADDRESS TRANSLATION

Basic NAT supports multiple simultaneous connections but is still limited by the number of available public IP addresses. Smaller companies may only be allocated a single or small block of addresses by their ISPs. In such cases, a means for multiple private IP addresses to be mapped onto a single public address would be useful. This function is provided by Port Address Translation (PAT). This can be referred to as Network Address Port Translation (NAPT) or NAT overloading or one-to-many NAT.

Port Address Translation (PAT). (Images ©123RF.com.)

PAT works by allocating each new connection an ephemeral TCP or UDP port. For example, say two hosts (10.0.0.101 and 10.0.0.102) initiate a web connection at the same time. The PAT service creates two new port mappings for these requests (10.0.0.101:61101 and 10.0.0.102:61102) in its state table. It then substitutes the private IP for the public IP and forwards the requests to the public Internet. It performs a reverse mapping on any traffic returned using those ports, inserting the original IP address and port number, and forwarding the packets to the internal hosts.

DEFENSE IN DEPTH

Firewalls, screened subnets, and proxy servers try to establish a secure barrier at the network edge. This is referred to as perimeter security. The proliferation of mobile devices with wireless or cellular data access and cloud services, plus the better recognition of insider threat and vulnerabilities to malware, has eroded confidence in a solely perimeter-based security model. Network security design must address the concept of defense in depth. This refers to placing security controls throughout the network, so that all access attempts are authenticated, authorized, and audited. Some examples of security controls that provide defense in depth additional to network segmentation and screened subnets include Network Access Control, honeypots, separation of duties, and intrusion detection.

Network Access Control

Network Access Control (NAC) is a system for authenticating endpoints at the point they connect to the network. NAC uses 802.1X port security mechanisms, EAP, and AAA model of supplicants, network access device AAA clients, and AAA servers. NAC enables devices to be authenticated when they connect to switch ports, wireless networks, or virtual private network (VPN) remote access servers.

Basic NAC solutions can authenticate a client on the basis of machine certificates and/or user passwords. More sophisticated solutions can enforce a health policy. A health policy means that the client must submit an attestation report. This secure report proves that the client is running an authorized OS and has up-to-date patches and security scanner configuration.

Honeypots

A honeypot is a computer system set up to attract attackers, with the intention of analyzing attack strategies and tools, to provide early warning of attack attempts, or possibly as a decoy to divert attention from actual computer systems. Another use is to detect internal fraud, snooping, and malpractice. A honeynet is an entire decoy network. This may be set up as an actual network or simulated using an emulator.

On a production network, a honeypot is more likely to be located in a protected but untrusted area between the Internet and the private network or on a closely monitored and filtered segment within the private network itself. This provides early warning and evidence of whether a threat actor has been able to penetrate to a given security zone.


Separation of Duties

Separation of duties is a means of establishing checks and balances against the possibility that critical systems or procedures can be compromised by insider threats. Duties and responsibilities should be divided among individuals to prevent ethical conflicts or abuse of powers.

INTRUSION DETECTION AND PREVENTION SYSTEMS

An intrusion detection system (IDS) performs real-time analysis of either network traffic or system and application logs. Where a firewall applies rules from an ACL, an IDS is configured with signature patterns. Each pattern represents a known type of malicious activity. If a pattern is matched in a traffic stream, the IDS raises an alert. Like antivirus software, the IDS must be kept up to date with the latest signature patterns. An IDS is often also configured with automated threat data, such as lists of IP addresses and domains that are associated with threat actors.

Like a packet analyzer, an IDS must be configured with a sniffer to read frames from a mirrored port or TAP. Placement of the sniffer must be carefully considered to meet security goals. Typically, an IDS is positioned behind a firewall. The aim is to detect suspicious traffic that the firewall has not blocked, providing defense in depth. This type of passive sensor does not slow down traffic and is undetectable by the attacker (it does not have an IP address on the monitored network segment).

Configuration file for the Snort IDS.

Compared to the passive logging/alerting functionality of an IDS, an intrusion prevention system (IPS) can provide an active response to any network threats that it matches. One typical preventive measure is to end the session by sending a TCP reset packet to the attacking host. Another option is for the sensor to apply a temporary filter on the firewall to block the attacker's IP address (shunning). Other advanced measures include throttling bandwidth to attacking hosts, applying complex firewall filters, and even modifying suspect packets to render them harmless. Finally, the appliance may be able to run a script or third-party program to perform some other action not supported by the IPS software itself.

IPS functionality is now very commonly built into firewall appliances and proxy servers. An IPS-enable firewall is inline with the network, meaning that all traffic passes through it (also making them a single point-of-failure if there is no fault tolerance mechanism). This obviously means that they need to be able to cope with high bandwidths and process each packet very quickly to avoid slowing down the network.

Network IDS/IPS can be combined with host-based IDS/IPS. These run as agents on end systems to monitor application processes, data files, and log files for suspicious activity. Advanced IDS/IPS suites analyze information from multiple sensors to identify suspicious traffic flows and host activity.

Topic 14B: Troubleshoot Service and Security Issues

DHCP ISSUES

The Dynamic Host Configuration Protocol (DHCP) provides IP addressing autoconfiguration to hosts without static IP parameters. If a Windows client fails to obtain a DHCP lease, it defaults to using an address in the Automatic Private IP Addressing (APIPA) range of 169.254.0.0/16. It will be limited to communication with other APIPA hosts on the same network segment (broadcast domain). Linux hosts will use the 169.254.0.0/16 range if they have Zeroconf support, leave the IP address set to 0.0.0.0, or disable IPv4 on the interface.

APIPA is Microsoft terminology. Standards documentation refers to this address range as IPv4 Link-local (IPV4LL).




DHCP Server and Scope Exhaustion Issues

Possible reasons for a client to fail to obtain a lease include:

●	The DHCP server is offline. If your DHCP servers go offline, users will continue to connect to the network for a period and thereafter start to lose contact with network services and servers as they come to try to renew a lease.

●	No more addresses available (DHCP scope exhaustion). Create a new scope with enough addresses or reduce the lease period. Remember that IP Address Management (IPAM) software suites can be used to track address usage across a complex DHCP infrastructure.

●	The router between the client and DHCP server doesn't support BOOTP forwarding. Either install RFC 1542-compliant routers or add another type of DHCP relay agent to each subnet or VLAN.

If you reconfigure your DHCP servers and their scopes, the clients will gradually get reconfigured. You will need to ensure that you plan for the fact that not all clients' IP configurations will be updated when the server scopes are edited and could be left with an expired IP, default gateway, or DNS server address. You could do this by lowering the lease duration in advance of changes, forcing all clients to renew, or running parallel settings for a period.

Rogue DHCP Server Issues

Clients have no means of preferring a DHCP server. If two DHCP servers are running on the same subnet, clients could end up with an incorrect IP configuration because they have obtained a lease from a rogue server. A rogue DHCP server may be deployed accidentally (forgetting to disable a DHCP server in an access point or router, for instance) or may be used by a malicious attacker to subvert the network. An attacker would normally use a rogue server to change the default gateway and/or DNS resolver addresses for the subnet and route communications via his or her machine (an on-path attack).

NAME RESOLUTION ISSUES

When you perform a successful connectivity test by IP address, the next step may be to try pinging by name, thus testing name resolution.

Name Resolution Methods

To troubleshoot name resolution, you should establish exactly how the process works on that specific host. A host can use a variety of methods to resolve a name or FQDN to an IP address. In very general terms, these will be as follows:

1. `	`Check local cache. One complication here is that there are different types of cache and separate caches for individual applications, such as web browsers. On Windows, you can use ipconfig /displaydns and ipconfig /flushdns to monitor and clear the system cache.
1. `	`Check HOSTS. The HOSTS file is a static list of host name to IP address mappings. The default location under Windows is %SystemRoot%\system32\drivers\etc\, while under Linux it is usually placed in the /etc directory. In most cases, HOSTS should not contain any entries (other than the loopback address). Any static entries in HOSTS could be the cause of a name resolution issue. The file can also be used for troubleshooting.
1. `	`Query DNS. A host uses the name servers defined in its IP configuration to resolve queries.

Any text preceded by the # symbol in a HOSTS file is a comment and will not be processed.

While we are focusing on name resolution via DNS here, note that a host can use multiple methods, especially on Windows workgroup networks. Link Local Multicast Name Resolution (LLMNR) and multicastDNS (mDNS) are modified forms of DNS that allow clients to perform name resolution on a local link without needing a server.

DNS Configuration Issues

Linux and Windows systems usually rely on DNS server infrastructure for name resolution and service discovery. In the absence of DNS servers, network client machines will be unable to log on or connect to services or servers.

If your hosts are experiencing DNS issues, symptoms will include the inability to connect to a server by name, despite it being accessible by IP address. To verify a name resolution problem, edit the HOSTS file and place the correct name and IP address record in the file for the test host. When you ping, if that is successful, it suggests a name resolution problem.

If a single client is unable to resolve names, the issue is likely to lie with the client configuration.

●	The client has been configured either with no DNS server address or the wrong DNS server address. Reconfigure the DNS server address.

●	The client has the incorrect DNS suffix. Verify the DNS domain in which the client is supposed to be and verify the host's configuration matches.

Bear in mind that in both of these situations, DHCP might be configuring these settings incorrectly. Therefore, check the server options or scope options configuration on the DHCP server as well.

If multiple clients are affected, the issue is likely to lie with the server service (or the way a subnet accesses the server service). Check that the server configured as a DNS resolver is online and available (that you can ping the server from the client).

If some DNS queries work from the client and others don't, then the problem is more complex. Use the nslookup or dig utilities to check what records are returned by the resolver. If trying to connect to an Internet resource, compare these records to those returned by public resolvers (such as Google's servers at 8.8.8.8). Consider whether clients have cached a record that has been changed recently. Reconfiguration of DNS records should be planned and implemented carefully to avoid caching problems.

VLAN ASSIGNMENT ISSUES

When you partition a network into separate VLANs, as each VLAN is a discrete broadcast domain, you must ensure that services, such as DHCP and DNS, are properly available to all VLANs. Otherwise, users will complain that "the Internet is down," when it transpires that there is no local DNS server available to handle their name resolution requests.

If devices are not in the same VLAN and must communicate, ensure that routing has been configured to enable VLAN-to-VLAN communications. You may also need to configure services such as DHCP relay to allow hosts to contact a DHCP server. Also, if a device is placed in a designated VLAN, its IP configuration must be appropriate in terms of IP address, subnet mask, default gateway, and DNS servers.

Another issue is that a host has been placed in an incorrect VLAN. Make sure all devices are placed into the appropriate VLAN as per the configuration baseline. VLAN assignments can be configured manually, and the administrator may have made a mistake, so check the interface configuration for the switch port. VLAN assignments can also be configured automatically, using parameters such as the host MAC address or authentication credentials, and this process may have failed, or the database used to map the dynamic data to a VLAN ID might be misconfigured.

UNRESPONSIVE SERVICE AND NETWORK PERFORMANCE ISSUES

If you can rule out connectivity problems with a local client or subnet, the issue may be with an application server, rather than the client. Such unresponsive service issues will usually manifest with multiple clients being unable to connect. There can be any number of underlying causes, but consider some of the following:

●	The application or OS hosting the service has crashed (or there is a hardware or power problem).

●	The server hosting the service is overloaded (high CPU/memory/disk I/O utilization/disk space utilization). Try throttling client connections until the server resources can be upgraded.

●	There is congestion in the network, either at the client or server end (or both). Use ping or traceroute to check the latency experienced over the link and compare to a network performance baseline. Again, throttling connections or bandwidth may help to ease the congestion until higher bandwidth links can be provisioned.

●	A broadcast storm is causing loss of network bandwidth. Switching loops cause broadcast and unknown unicast frames to circulate the network perpetually, as each switch repeatedly floods each frame. A broadcast storm may quickly consume all link bandwidth and crash network appliances (check for excessive CPU utilization on switches and hosts). The Spanning Tree Protocol (STP) is supposed to prevent such loops, but this can fail if STP communications between switches do not work correctly, either because of a fault in cabling or a port/transceiver or because of a misconfiguration.

●	Network congestion may also be a sign that the service is being subject to a Denial of Service (DoS) attack. Look for unusual access patterns (for example, use GeoIP to graph source IP addresses by country and compare to baseline access patterns).

If users on a LAN cannot connect to an external service, such as a cloud application, you can use a site such as isitdownrightnow.com to test whether the issue is local to your network or a problem with the service provider site.

Be proactive in monitoring service availability so that you can resolve problems before they affect large numbers of clients.

MISCONFIGURED FIREWALL AND ACL ISSUES

One type of firewall, ACL, or content filter misconfiguration causes blocked services, ports, or addresses that are supposed to be allowed through. This will cause an application or protocol to fail to function correctly. For example, the firewall might be blocking TCP or UDP ports that are supposed to be open, or it might be allowing the ports but denying access to an IP network or host address that is supposed to be able to connect. Also consider that advanced firewalls are capable of applying additional filtering criteria, such as evaluating process/service executable names/locations or authorizations based on user accounts or group memberships.

A deny type of error will usually be easy to identify, as users will report incidents connected with the failure of the data traffic. With such incidents, firewall configuration will always be a likely cause, so will be high on the list to investigate. Diagnosis can be confirmed by trying to establish the connection from both inside and outside the firewall. If it connects from outside the firewall but not from inside, this will confirm the firewall to be the cause of the issue.

Another potential issue is where there are both network-based and host-based firewall settings to navigate in the communication path. There could be a host firewall running on the client, on the server, or on both. To diagnose an issue with a host firewall, attempt the connection with the host firewall disabled. If the connection attempt succeeds, then the network firewall ACL is allowing the packets, but the host firewall is configured to block them. If the connection attempt fails, investigate the network firewall ACL first. You can also inspect the firewall's log files to discover what rules have been applied to block traffic at a particular time.

The other possible outcome of a badly configured firewall is that packets may be allowed through that should be blocked. This is a more serious outcome, because the result is to open the system to security vulnerabilities. It is also not necessarily so easily detected, as it does not typically cause anything to stop functioning. As no incidents usually arise from this outcome (except in the case that a vulnerability is exploited), it is not a scenario that is subject to troubleshooting. Rather, it underlines the need for regular firewall audits and thorough change control processes to deal with firewall change requests.

UNTRUSTED CERTIFICATE ISSUES

If the digital certificate presented by a subject (server or user) is not trusted by the client application (such as a browser), the client will notify the user. The most common reason for a certificate not to be trusted is that the certificate issuer is not trusted. For example, say Widget's web server receives a certificate signed by MyCA. Unless MyCA's own certificate is stored in the browser's trusted root store, the client application will not trust the Widget server. The user can usually choose to ignore this warning and add an exception, but this should be done only if the cause of the lack of a trust relationship is understood.

If you trust the issuer, you can add their certificate to the client device's root certificate store. In Windows, you can use the certmgr.msc console to manage user certificates and the certlm.msc console to manage machine certificates. You also use these consoles to manage certificates used by the computer or its user accounts.

Certificate Management console. The Trusted Root CA contains all Microsoft and enterprise trusts, plus the third-party CA trusts. (Screenshot used with permission from Microsoft.)

One complication here is that different applications may have different stores of trusted certificates. For example, there is a Windows certificate store, but the Firefox® browser does not trust it by default and maintains its own certificate stores. The various Linux distributions store trusted root certificates in several different locations.

Frequently, certificates are untrusted because they are self-signed (the certificate holder is both the issuer and the subject of the certificate). This is often the case with the certificates used to protect the web management interfaces of consumer-grade appliances and server applications. You might be able to replace the default certificate with one trusted by the enterprise.

Some other causes of untrusted certificates are:

●	The certificate's subject name does not match the URL. This is usually a configuration error on the part of the web server manager, but it could indicate malicious activity. You should confirm the certificate's common name and access the website by using that URL.

This certificate is not trusted because it is self-signed and because it does not match the subject name (because the host is being accessed via an IP address instead of an FQDN). (Screenshot courtesy of Mozilla Foundation.)

●	The certificate is not being used for its stated purpose. For example, a certificate issued to sign email is being used on a web server. In this circumstance, you should not add an exception. The service owner or subject should obtain a correctly formatted certificate.

●	The certificate is expired or revoked. Again, unless there are explainable circumstances, you should not allow an exception. If you are managing a legacy appliance (a SOHO router or NAS drive, for instance), it is likely that the certificate installed on it will have expired. If you know that the appliance has not been tampered with, you can proceed.

●	Time is not correctly synchronized between the server and client.

Browsers and email applications usually display informative error messages. In other contexts, such as EAP authentication, it might not be so obvious that the certificate is the cause of the failure or why the certificate is being rejected. Inspect the logs recording the connection for clues.

OTHER COMMON ISSUES

When it comes to application layer troubleshooting, you will usually need to use references that are specific to the environment or app to solve problems. Some other generic issues you may encounter include time synchronization, mobile devices, and licensing.

NTP Issues

Most network services, and especially authentication and authorization mechanisms, depend upon each host using a synchronized time source. Inaccurate time sources also affect the reliability and usability of log data, which can have implications for regulatory compliance.

Time synchronization is usually accomplished via the Network Time Protocol (NTP). Clients must be able to access a time source over port UDP 123. In a Windows environment, the time source for clients will usually be a domain controller. The domain controller can either use a hardware GPS-based time source or rely on Internet servers, depending on the level accuracy required. In Windows, the w32tm /query /configuration command can be used to check the current configuration.

BYOD Challenges

Bring Your Own Device (BYOD) is a smartphone/tablet provisioning model that allows users to select a personal device to use to interact with corporate network services and cloud apps. Allowing user selection of devices introduces numerous compatibility, support, and security challenges:

●	Compatibility/support-The wide range of devices, mobile OS versions, and vendor support for patches make the job of ensuring that each device can connect to corporate network apps and data resources highly complex.

●	Security-This device variety also causes security issues, especially in terms of unpatched devices. Another issue is that the device is not fully under the administrative control of the IT department. An insider threat actor could install apps that might pose a risk to corporate data or misuse the device to exfiltrate data.

Some of the impact of these issues can be mitigated through the use of enterprise mobility management (EMM) suites and corporate workspaces. EMM (or mobile device management) is a type of network access control solution that registers devices as they connect to the network. It can then enforce security policies while the device is connected. These might restrict use of device functions or personal apps. A corporate workspace is an app that is segmented from the rest of the device and allow more centralized control over corporate data. Users must also agree to acceptable use policies, which might prohibit installing non-store apps and rooting/jailbreaking a device and keeping the device up to date with patches. Users will also usually have to submit to inspection of the device to protect corporate data.

Licensed Feature Issues

Licensing for servers and network appliances can be complex and it is easy to make configuration errors. When faced with an unexpected problem, it is often worth considering whether a licensing or feature activation issue could be the cause. On a switch or router, license failures could restrict the number of ports available, the number of routes allowed in the routing table, or the availability of routing protocols. Security and management features may have been configured under a trial or evaluation period and suddenly stop working when that grace period ends.

The starting point for troubleshooting license issues will be the log. This should show whether an evaluation/trial period has just expired or when a seat/instance count has been exceeded. Verify that the appliance has the correct licenses or activation keys installed. If relevant, ensure that the appliance can connect to its licensing or activation server.