Lesson 19: Applying Network Hardening Techniques

Topic 19A: Compare and Contrast Types of Attacks

GENERAL ATTACK TYPES

A network can be attacked by many kinds of intruders or adversaries for many different reasons. The goals of most types of adversaries will be to steal (exfiltrate) information from the network, to misuse network services (for fraud, for instance), or to compromise the availability of the network. Insider threat-type attacks may be launched with privileged access to the network, while external threats must find some way of accessing the network, perhaps by installing malware on a host system.

Footprinting and Fingerprinting Attacks

Footprinting and fingerprinting are enumeration or information gathering attacks. Footprinting allows a threat actor to discover the topology and general configuration of the network and security systems. Footprinting can be done by social engineering attacks-persuading users to give information or locating information that has been thrown out as trash, for instance. Port scanning specifically aims to enumerate the TCP or UDP application ports on which a host will accept connections.

Fingerprinting allows a threat actor to identify device and OS types and versions. When a host running a particular operating system responds to a port scan, the syntax of the response might identify the specific operating system. This fact is also true of application servers, such as web servers, FTP servers, and mail servers. The responses these servers make often include headers or banners that can reveal a great deal of information about the server. A threat actor can use this information to probe for known vulnerabilities.

Spoofing Attacks

The term spoofing covers a wide range of different attacks. Spoofing can include any type of attack where the attacker disguises his or her identity, or in which the source of network information is forged to appear legitimate. Social engineering and techniques such as phishing and pharming, where the attacker sets up a false website in imitation of a real one, are types of spoofing attacks. It is also possible to abuse the way a protocol works or how network packets are constructed to inject false or modified data onto a network. The ARP and DNS protocols are often used as vectors for this type of attack.

Denial of Service Attacks

A denial of service (DoS) attack causes a service at a given host to fail or to become unavailable to legitimate users. Resource exhaustion DoS attacks focus on overloading a service by using up CPU, system RAM, disk space, or network bandwidth. It is also possible for DoS attacks to exploit design failures or other vulnerabilities in application software. A physical DoS attack might involve cutting telephone lines or network cabling or switching off the power to a server. DoS attacks may be motivated by the malicious desire to cause trouble. They may also be part of a wider attack, such as the precursor to a spoofing or data exfiltration attack. DoS can assist these attacks by diverting attention and resources away from the real target. For example, a blinding attack attempts to overload a logging or alerting system with events.

ON-PATH ATTACKS

An on-path attack is a specific type of spoofing attack where a threat actor compromises the connection between two hosts and transparently intercepts and relays all communications between them. The threat actor might also have the opportunity to modify the traffic before relaying it.

On-path attacks are also known by the term "Man-in-the-Middle (MitM)." Such terms are non-inclusive and/or use inappropriate or vague metaphors and are deprecated in the latest CompTIA exam objectives documents.

MAC Spoofing and IP Spoofing

A host can arbitrarily select any MAC and/or IP address and attempt to use it on the network. A threat actor might exploit this to spoof the value of a valid MAC or IP address to try to circumvent an access control list or impersonate a legitimate server. For this type of attack to succeed, the threat actor must normally disable the legitimate host or there will be duplicate addresses on the network, which will have unpredictable results.

IP spoofing is also used in most denial of service (DoS) attacks to mask the origin of the attack and make it harder for the target system to block packets from the attacking system. In this type of spoofing, the threat actor does not care about not receiving return traffic.

ARP Spoofing

ARP spoofing, or ARP cache poisoning, is a common means of perpetrating an on-path attack. It works by broadcasting unsolicited ARP reply packets, also known as gratuitous ARP replies, with a source address that spoofs a legitimate host or router interface. Because ARP has no security, all devices in the same broadcast domain as the rogue host trust this communication and update their MAC:IP address cache table with the spoofed address. Because the threat actor broadcasts endless ARP replies, it overwhelms the legitimate interface.

Observing ARP poisoning in a Wireshark packet capture. (Screenshot courtesy of Wireshark.)

The usual target will be the subnet's default gateway. If the attack is successful, all traffic destined for remote networks will be sent to the attacker. The threat actor can then perform an on-path attack to monitor the communications and continue to forward them to the router to avoid detection. The attacker could also modify the packets before forwarding them. ARP poisoning could also perform a DoS attack by not forwarding the packets.

ARP poisoning can be difficult to detect without closely monitoring network traffic. However, attempts at ARP poisoning are likely to cause sporadic communications difficulties, such as an unreachable default gateway. In such cases, performing network captures and examining ARP packets may reveal the poison packets, as will examining local ARP caches for multiple IP addresses mapping to the same MAC address.

While IPv6 does not use ARP, it is also vulnerable to layer 2 spoofing if the unencrypted Neighbor Discovery (ND) protocol is used.

Rogue DHCP

An on-path attack can also be launched by running a rogue DHCP server. DHCP communications cannot be authenticated, so a host will generally trust the first offer packet that it receives. The threat actor can exploit this to set his or her machine as the subnet's default gateway or DNS resolver.

DNS POISONING ATTACKS

DNS poisoning is an attack that compromises the name resolution process. Typically, the attacker will replace the valid IP address for a trusted website, such as mybank.example, with the attacker's IP address. The attacker can then intercept all the packets directed to mybank.example and bounce them to the real site, leaving the victim unaware of what is happening (referred to as pharming). Alternatively, DNS spoofing could be used for a DoS attack by directing all traffic for a particular FQDN to an invalid IP address (a black hole).

One way to attack DNS is to corrupt the client's name resolution process. This can be accomplished by changing the servers used for resolving queries, intercepting and modifying DNS traffic, or polluting the client's name cache (by modifying the HOSTS file, for instance). DNS server cache poisoning (or pollution) is another redirection attack, but instead of trying to subvert the name service used by the client, it aims to corrupt the records held by the DNS server itself.

Attempting to poison a DNS server cache-This attack has failed.

VLAN HOPPING ATTACKS

VLAN hopping is an attack designed to send traffic to a VLAN other than the one the host system is in. This exploits the native VLAN feature of 802.1Q. Native VLANs are designed to provide compatibility with non-VLAN capable switches. The attacker, using a device placed in the native VLAN, crafts a frame with two VLAN tag headers. The first trunk switch to inspect the frame strips the first header, and the frame gets forwarded to the target VLAN. Such an attack can only send packets one way but could be used to perform a DoS attack against a host on a different VLAN. Double tagging can be mitigated by ensuring that the native VLAN uses a different ID to any user accessible VLAN.

A VLAN hopping attack can also be launched by attaching a device that spoofs the operation of a switch to the network and negotiating the creation of a trunk port. As a trunk port, the attacker's device will receive all inter-VLAN traffic. This attack can be mitigated by ensuring that ports allowed to be used as trunks are pre-determined in the switch configuration and that access ports are not allowed to auto-configure as trunk ports.

WIRELESS NETWORK ATTACKS

Wireless networks can open several avenues for a threat actor to gain unauthorized network access.

Rogue Access Points

A rogue access point is one that has been installed on the network without authorization, whether with malicious intent or not. A malicious user can set up such an AP with something as basic as a smartphone with tethering capabilities, and a non-malicious user could enable such an AP by accident. If connected to a LAN without security, an unauthorized AP creates a backdoor through which to attack the network.

Evil Twins

A rogue AP masquerading as a legitimate one is called an evil twin. An evil twin might advertise a similar network name (SSID) to the legitimate one. For example, an evil twin might be configured with the network name "compeny" where the legitimate network name is "company." Alternatively, the evil twin might spoof the SSID and BSSID (MAC address) of an authorized access point and then the attacker might use some DoS technique to overcome the legitimate AP. After a successful DoS attack, the users will be forced to disconnect from the network and then manually attempt to reconnect. At that point, with many users busy and trying to get back to work, some or all may associate with the evil twin AP and submit the network passphrase or their credentials for authentication.

However it is configured, when a user connects to an evil twin, it might be able to harvest authentication information and, if it is able to provide wider network or Internet access, execute an on-path attack to snoop on connections established with servers or websites.

Surveying Wi-Fi networks using Xirrus Wi-Fi Inspector (xirrus.com)-Note the presence of print devices configured with open authentication (no security) and a smart TV appliance (requiring authentication). (Screenshot used with permission from Xirrus.)

One solution to the risk of rogue access points is to use EAP-TLS security so that the authentication server and clients perform mutual authentication. There are also various scanners and monitoring systems that can detect rogue APs, referred to as a wireless intrusion detection system (WIDS) or wireless intrusion prevention system (WIPS).

Deauthentication Attacks

The use of an evil twin may be coupled with a deauthentication attack. This sends a stream of spoofed management frames to cause a client to deauthenticate from an AP. This might allow the attacker to interpose the evil twin, sniff information about the authentication process, or perform a denial of service (DoS) attack against the wireless infrastructure. These attacks work against both WEP and WPA. The attacks can be mitigated if the wireless infrastructure supports Management Frame Protection (MFP/802.11w). Both the AP and clients must be configured to support MFP.

Aireplay sniffs ARP packets to harvest IVs while Airodump saves them to a capture, which Aircrack can analyze to identify the correct encryption key.

DISTRIBUTED DOS ATTACKS AND BOTNETS

A distributed DoS (DDoS)attack is launched simultaneously by multiple hosts. Some types of DDoS attack simply aim to consume network bandwidth, denying it to legitimate hosts. Others cause resource exhaustion on the hosts processing requests, consuming CPU cycles and memory. This delays processing of legitimate traffic and could potentially crash the host system completely. For example, a SYN flood attack works by withholding the client's ACK packet during TCP's three-way handshake. The client's IP address is spoofed, meaning that an invalid or random IP is entered so the server's SYN/ACK packet is misdirected. A server can maintain a queue of pending connections. When it does not receive an ACK packet from the client, it resends the SYN/ACK packet a set number of times before "timing out" and giving up on the connection. The problem is that a server may only be able to manage a limited number of pending connections, which the DoS attack quickly fills up. This means that the server is unable to respond to genuine traffic.

Dropping traffic from blacklisted IP ranges by using the Security Onion Network Security Monitoring (NSM) appliance. (Screenshot courtesy of Security Onion.)

Distributed Reflection DoS/Amplification Attacks

A more powerful TCP SYN flood attack is a type of distributed reflection DoS (DRDoS) or amplification attack. In this attack, the adversary spoofs the victim's IP address and attempts to open connections with multiple servers. Those servers direct their SYN/ACK responses to the victim server. This rapidly consumes the victim's available bandwidth.

The same sort of technique can be used to bombard a victim network with responses to bogus DNS queries. One of the advantages of this technique is that while the request is small, the response to a DNS query can be made to include a lot of information, so this is a very effective way of overwhelming the bandwidth of the victim network with much more limited resources on the attacker's network. The Network Time Protocol (NTP) can be abused in a similar way.

Botnets

A botnet is a group of compromised hosts that can be used to launch DDoS and DRDoS attacks. A threat actor will first compromise one or two machines to use as handlers or herders. The handlers are used to compromise hundreds or thousands or millions of zombie hosts with DoS tools (the bots). To compromise a host, the attacker must install malware that opens a backdoor remote connection. The attacker can then use the malware to install bots and trigger the zombies to launch the attack at the same time. The network established between the handlers and the bots is called a command and control (C-and-C or C2) network.

Any type of Internet-enabled device is vulnerable to compromise. This includes web-enabled cameras, SOHO routers, and smart TVs and other appliances. This is referred to as an Internet of Things (IoT) botnet.

MALWARE AND RANSOMWARE ATTACKS

Many of the intrusion attempts perpetrated against computer networks depend on the use of malicious software, or malware. Malware can be defined simply as software that does something bad, from the perspective of the system owner. There are many types of malware, but they are not classified in a rigorous way, so some definitions overlap or are blurred. Some malware classifications, such as Trojan, virus, and worm, focus on the vector used by the malware. The vector is the method by which the malware executes on a computer and potentially spreads to other network hosts. Another complicating factor with malware classification is the degree to which its installation is expected or tolerated by the user. The following categories describe some types of malware according to vector:

●	Viruses and worms-These represent some of the first types of malware and spread without any authorization from the user by being concealed within the executable code of another process.

●	Trojan-Malware concealed within an installer package for software that appears to be legitimate. This type of malware does not seek any type of consent for installation and is actively designed to operate secretly.

●	Potentially unwanted programs (PUPs)/Potentially unwanted applications (PUAs)-Software installed alongside a package selected by the user or perhaps bundled with a new computer system. Unlike a Trojan, the presence of a PUP is not automatically regarded as malicious. It may have been installed without active consent or consent from a purposefully confusing license agreement. This type of software is sometimes described as grayware rather than malware.

Other classifications are based on the payload delivered by the malware. The payload is an action performed by the malware other than simply replicating or persisting on a host. Examples of payload classifications include spyware, rootkit, remote access Trojan (RAT) or backdoor, and ransomware.

Ransomware is a type of malware that tries to extort money from the victim. One class of ransomware will display threatening messages, such as requiring Windows to be reactivated or suggesting that the computer has been locked by the police because it was used to view child pornography or for terrorism. This may block access to the computer by installing a different shell program or browser window that is difficult to close, but this sort of attack is usually relatively simple to fix.

The crypto-malware class of ransomware attempts to encrypt data files on any fixed, removable, and network drives. If the attack is successful, the user will be unable to access the files without obtaining the private encryption key, which is held by the attacker. If successful, this sort of attack is extremely difficult to mitigate, unless the user has up to date backups of the encrypted files. One example of this is Cryptolocker, a Trojan that searches for files to encrypt and then prompts the victim to pay a sum of money before a certain countdown time, after which the malware destroys the key that allows the decryption.

WannaCry ransomware. Wikimedia Public Domain image. (Image by Wikimedia Commons.)

PASSWORD ATTACKS

On-path and malware attacks can be difficult to perpetrate. Many network intrusions occur because a threat actor is able to obtain credentials to access the network. Also, when a threat actor gains some sort of access via an on-path or malware attack, they are likely to attempt to escalate privileges to gain access to other targets on the network by harvesting credentials for administrative accounts.

Passwords or password hashes can be captured by obtaining a password file or by sniffing the network. If the protocol uses cleartext credentials, then the threat actor can simply read the cleartext password from the captured frames.

If authentication credentials are transmitted in cleartext, such as the unencrypted version of the IMAP mailbox access protocol, it is a simple matter for the credentials to be intercepted via packet sniffing. (Screenshot courtesy of Wireshark.)

A password might be sent in an encoded form, such as Base64, which is simply an ASCII representation of binary data. This is not the same as encryption. The password value can easily be derived from the Base64 string.

In most cases, a password is stored and transmitted securely by making a cryptographic hash of the string entered by the user. A cryptographic hash algorithm, such as Secure Hash Algorithm (SHA) or Message Digest v5 (MD5), produces a fixed length string from a variable length string. This means that, in theory, no one except the user (not even the system administrator) knows the password, because the plaintext should not be recoverable from the hash.

Password cracking software uses various methods to work out the plaintext password string from a cryptographic hash:

●	Dictionary-The software matches the hash to those produced by ordinary words found in a dictionary. This could also include information such as user and company names, pet names, or any other data that people might naively use as passwords.

●	Brute force-The software tries to match the hash against one of every possible combination it could be. If the password is short (under eight characters) and non-complex (using only letters, for instance), a password might be cracked in minutes. Longer and more complex passwords increase the amount of time the attack takes to run.

A threat actor might obtain password hashes from a protocol such as SMB with no encryption configured. The risks posed by cracking software mean that it is more secure to use end-to-end encryption, such as IPSec or Transport Layer Security (TLS). This means that all payload data is encrypted, and a network sniffer cannot even recover the password hashes.

HUMAN AND ENVIRONMENTAL ATTACKS

Threat actors can use a diverse range of techniques to compromise a security system. A prerequisite of many types of attacks is to obtain information about the network and security system. Social engineering (or hacking the human) refers to a collection of techniques and tricks designed to make victims reveal confidential information. Impersonation (pretending to be someone else) is one of the basic social engineering techniques. The classic impersonation attack is for the threat actor to phone into a department pretending to be calling from IT support, claim they have to adjust something on the user's system remotely, and get the user to reveal their password. For this attack to succeed, the approach must be persuasive and establish trust. Social engineering might also use intimidation or hoaxes as a means of eliciting information.

Phishing Attacks

Phishing is a combination of social engineering and spoofing. It persuades or tricks the target into interacting with a malicious resource disguised as a trusted one, traditionally using email as the vector. A phishing message might try to convince the user to perform some action, such as installing disguised malware or allowing a remote access connection by the attacker. Other types of phishing campaign use a spoof website set up to imitate a bank or e‑commerce site or some other web resource that should be trusted by the target. The attacker then emails users of the genuine website informing them that their account must be updated or with some sort of hoax alert or alarm, supplying a disguised link that actually leads to the spoofed site. When the user authenticates with the spoofed site, their logon credentials are captured.

Example phishing email-On the right, you can see the message in its true form as the mail client has stripped out the formatting (shown on the left) designed to disguise the nature of the links.

Shoulder Surfing

A threat actor can learn a password or PIN (or other secure information) by watching the user type it. This is referred to as a shoulder surfing attack. Despite the name, the attacker may not have to be in close proximity to the target-they could use high-powered binoculars or CCTV to directly observe the target remotely.

Tailgating and Piggybacking

Tailgating is a means of entering a secure area without authorization by following closely behind the person that has been allowed to open the door or checkpoint. Piggybacking is a similar situation but means that the attacker enters a secure area with an employee's permission. For instance, an attacker might impersonate a member of the cleaning crew and request that an employee hold the door open while they bring in a cleaning cart or mop bucket. Another technique is to persuade someone to hold a door open, using an excuse, such as "I've forgotten my badge/key." Alternatively, piggybacking may be a means of an insider threat actor to allow access to someone without recording it in the building's entry log.

Topic 19B: Apply Network Hardening Techniques

DEVICE AND SERVICE HARDENING

As part of a defense in depth strategy, you need to think about making each host and network infrastructure device secure against tampering or abuse. It can be tempting to think of network devices such as switches and routers as self-contained. In fact, these devices often run quite complex firmware and host numerous services to enable remote management and configuration. Deploying systems in a secure configuration is known as device hardening. Some of the policies that will make up a secure configuration involve the following:

●	Change default passwords/credentials-Devices such as wireless access points, switches, and routers sometimes ship with a default management password such as password, admin, or the device vendor's name. These should be changed on installation.

●	Enforce password complexity/length requirements-Passwords for network infrastructure must be highly resistant to guessing and cracking attacks:

●	Length-No passwords should be less than eight characters. However, as critical infrastructure, passwords for network appliances should be 14+ characters.

●	Complexity-Requiring multiple character classes (mixing letters, case, digits, and symbols) is deprecated by NIST's latest guidance, but is still a requirement in many local password policies.

●	Avoiding common passwords-The number of successful attacks against web servers and company networks has led to huge databases of credentials being posted online. Analysis of these databases shows how many users-even administrative users-rely on trivially simple passwords, such as 123456 or password. These password database dumps give attackers a useful dictionary to work with when trying to crack credentials. Any password that could be matched to a dictionary term is completely unsecure and must not be used.

●	Configure role-based access-The default administrator, superuser, or root account has unrestricted access to the device. If the credentials for this account are shared, the risk of compromise is greatly magnified. Role-based access means that a limited set of permissions are configured for different administrative groups, such as separating permissions for configuring the system to those for configuring logging and auditing. This separation of duties reduces impacts from the compromise of any single account.

●	Disable unneeded network services-Any services or protocols that are not used should be disabled. This reduces the attack surface of a network appliance or OS. Attack surface means the range of things that an attacker could possibly exploit in order to compromise the device. It is particularly important to disable unused administration interfaces.

●	Disable unsecure protocols-Sniffing attacks can be mitigated by encrypting the channel over which communications takes place. This means that even if the eavesdropper can listen to the message, he or she cannot understand it without obtaining the encryption key. It is important to understand which protocols are unsecure in terms of using unencrypted channels. This is particularly important when using a channel to authenticate. Unsecure protocols should be deprecated, and secure protocols used instead. For example, the original versions of SNMP are unencrypted. To implement secure SNMP, either configure SNMPv3, which supports encryption, or use an encapsulation protocol such as IPSec to encrypt SNMP traffic.

ENDPOINT SECURITY AND SWITCHPORT PROTECTION

Endpoint security is a set of security procedures and technologies designed to restrict network access at a device level. Endpoint security contrasts with the focus on perimeter security established by topologies such as screened subnets and technologies such as firewalls. Endpoint security is designed not to replace perimeter security but to supplement it, creating defense in depth.

Access to the physical switch ports and switch hardware should be restricted to authorized staff, using a secure server/equipment room and/or lockable hardware cabinets. To prevent the attachment of unauthorized client devices, a switch port can be disabled using the management software or isolated to a VLAN with no route to the network (a black hole VLAN). On a Cisco switch, these configuration settings will generally be applied using some version of a switchport command or sub-command. As another option, the patch cable can be physically removed from the port. Completely disabling ports in this way can introduce a lot of administrative overhead and scope for error. Also, it doesn't provide complete protection, as an attacker could unplug a device from an enabled port and connect their own laptop. Consequently, more sophisticated methods of ensuring port security have been developed.

MAC Filtering and Dynamic ARP Inspection

Configuring MAC filtering on a switch means defining which MAC addresses are permitted to connect to a particular port. This can be done by creating a list of valid MAC addresses or by specifying a limit to the number of permitted addresses. For example, if port security is enabled with a maximum of two MAC addresses, the switch will record the first two MACs to connect to that port but then drop any traffic from machines with different network adapter IDs that try to connect

A malicious host may use a spoofed MAC address to try to perform ARP cache poisoning against other hosts on the network and perpetrate an on-path attack. A switch port security feature such as dynamic ARP inspection (DAI) prevents a host attached to an untrusted port from flooding the segment with gratuitous ARP replies. ARP inspection maintains a trusted database of IP:ARP mappings. It also ensures that ARP packets are validly constructed and use valid IP addresses.

Configuring ARP inspection and DHCP snooping on a Cisco switch. (Image © and Courtesy of Cisco Systems, Inc. Unauthorized use not permitted.)

DHCP Snooping

Configuring DHCP snooping causes the switch to inspect DHCP traffic arriving on access ports to ensure that a host is not trying to spoof its MAC address. It can also be used to prevent rogue DHCP servers from operating on the network. With DHCP snooping, only DHCP offers from ports configured as trusted are allowed.

Neighbor Discovery Inspection and Router Advertisement Guard

Neighbor Discovery (ND) Inspection and Router Advertisement (RA) Guard perform similar functions to DAI and DHCP snooping for IPv6 networks. Most hosts have IPv6 enabled by default and disabling it can often cause unexpected problems. Consequently, these switch protections should be enabled to mitigate spoofing and on-path attacks over IPv6.

Port Security/IEEE 802.1X Port-Based Network Access Control

MAC limiting and filtering and ARP inspection provide some protection against attacks, but they are not a means of ensuring only valid hosts are connecting to the network. Port security refers to the IEEE 802.1X standard’s Port-Based Network Access Control (PNAC) mechanism. PNAC means that the switch performs some sort of authentication of the attached device before activating the port.

Under 802.1X, the device requesting access is the supplicant. The switch, referred to as the authenticator, enables the Extensible Authentication Protocol over LAN (EAPoL) protocol only and waits for the device to supply authentication data. The authenticator passes this data to an authenticating server, typically a RADIUS server, which checks the credentials and grants or denies access. If access is granted, the switch will configure the port to use the appropriate VLAN and enable it for ordinary network traffic. Unauthenticated hosts may be denied any type of access or be placed in a guest VLAN with only limited access to the rest of the network.

VLAN AND PVLAN BEST PRACTICES

The virtual LAN (VLAN) feature of managed Ethernet switches is typically deployed to enforce segmentation policies. A VLAN isolates Layer 2 broadcast traffic to switch ports that are configured with the same VLAN ID. Each VLAN ID is typically mapped to a subnet and any traffic forwarding between VLANs must be performed by a router (or Layer 3 switch).

Private VLANs

A private VLAN (PVLAN) applies an additional layer of segmentation by restricting the ability of hosts within a VLAN to communicate directly with one another. This might be used by a hosting company to prevent web servers operated by different customers being able to communicate. Isolating these server instances using PVLANs is simpler than creating multiple VLANs and subnets. Similarly, ISPs use PVLANs to isolate subscriber traffic.

When configuring a PVLAN, the "host" VLAN is referred to as the primary VLAN. The following types of PVLAN ports can be configured within the primary VLAN:

●	Promiscuous port-Can communicate with all ports in all domains within the PVLAN. This is normally the port through which routed and/or DHCP traffic is sent.

●	Isolated port-Can communicate with the promiscuous port only. This creates a subdomain of a single host only. The PVLAN can contain multiple isolated ports, but each is in its own subdomain.

●	Community port-Can communicate with the promiscuous port and with other ports in the same community. This creates a subdomain that can contain multiple hosts.

Default VLAN and Native VLAN

The VLAN with ID 1 is referred to as the default VLAN. This cannot be changed. However, unless configured differently, all ports on a switch default to being in VLAN 1. When you are implementing VLANs, you should avoid sending user data traffic over the default VLAN. It should remain unused or used only for inter-switch protocol traffic, where necessary. For example, spanning tree traffic would be permitted to run over the default VLAN. Make sure that unused ports are not assigned to VLAN 1.

A native VLAN is one into which any untagged traffic is put when receiving frames over a trunk port. When a switch receives an untagged frame over a trunk, it assigns the frame to the native VLAN. Untagged traffic might derive from legacy devices such as hubs or older switches that do not support 802.1Q encapsulated frames. The native VLAN is initially set with the same VID as the default VLAN (VID 1). You can and should change this, however, to make the native VID any suitable ID. This should not be the same as any VLAN used for any other data traffic. The same native VLAN ID (VID) should be configured for the trunk port on both switches.

FIREWALL RULES AND ACL CONFIGURATION

Firewall access control lists (ACLs) are configured on the principle of least access. This is the same as the principle of least privilege; only allow the minimum amount of traffic required for the operation of valid network services and no more. The rules in a firewall's ACL are processed top-to-bottom. If traffic matches a rule that allows the packet, then it is allowed to pass. Consequently, the most specific rules are placed at the top. The final default rule is typically to block any traffic that has not matched a rule. This is called an implicit deny. If the firewall does not have a default implicit deny rule, an explicit deny all rule can be added manually to the end of the ACL.

Sample firewall ruleset configured on OPNsense. This ruleset blocks all traffic from bogon networks and private IP address ranges, but it allows ICMP traffic directed at a firewall interface, HTTP traffic from any source, and SMTP traffic from known networks, defined as the MAILHOSTS alias. (Screenshot used with permission from OPNsense.)

Each rule can specify whether to block or allow traffic based on parameters, often referred to as tuples. If you think of each rule being like a row in a database, the tuples are the columns. For example, in the screenshot, the tuples include Protocol, Source (address), (Source) Port, Destination (address), (Destination) Port, and so on.

As an example of ACL configuration, iptables is a command line utility provided by many Linux distributions that allows administrators to edit the rules enforced by the Linux kernel firewall. Iptables works with the firewall chains, which apply to the different types of traffic passing through the system. The three main chains are:

●	INPUT-Affecting incoming connections. For example, if a user attempts to SSH into the Linux server, iptables will attempt to match the source IP address and destination port to a rule in the input chain.

●	OUTPUT-For outgoing connections. For example, if you try to ping an FQDN such as comptia.org, iptables will check its output chain to see what the rules are regarding ping and comptia.org (or the IP address that comptia.org resolves to) before deciding to allow or deny the connection attempt.

●	FORWARD-Used for connections that are passing through the host, rather than being delivered locally. This chain would be used when configuring the host as a network firewall.

Rules can be assigned to these chains, or new chains can be created and then linked to the standard system chains to affect traffic flow. To view the current status of the iptables and the volume of traffic using the chains, use the command:

iptables -L -v

To change the firewall rules, commands such as those that follow would be used.

These examples allow one IP address from a specific subnet to connect and block all others from the same subnet.

iptables -A INPUT -s 10.1.0.1 -j ACCEPT

iptables -A INPUT -s 10.1.0.0/24 -j DROP

When you set least access rules (if both INPUT and OUTPUT default policy is set to deny all), you must set both INPUT and OUTPUT rules to allow most types of client/server traffic. For example, to allow a host to operate as an SSH server, configure the following rules:

iptables -A INPUT -p tcp --dport 22 -s 10.1.0.0/24 -m state --

state NEW,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -p tcp --sport 22 -d 10.1.0.0/24 -m state --

state ESTABLISHED -j ACCEPT

These commands use the stateful nature of the firewall to differentiate between new and established connections. The first rule allows hosts in the 10.1.0.0/24 net to initiate connections with the SSH server on the local host over port 22. The second rule allows the server to respond to existing connections established by hosts in the same subnet.

CONTROL PLANE POLICING

The quality of service (QoS) stack distinguishes three operational layers: control, data, and management. A network appliance uses minimal resources to process ordinary data traffic, which is often processed by dedicated hardware (one or more ASIC chips) and does not require the general purpose CPU. Conversely, control and management traffic requires software-based processing and is "punted" to the CPU's pipeline, requiring memory resource and processor time. The control plane comprises traffic that keeps the network itself operational, including routing updates, ARP traffic, STP notifications, NTP updates, QoS classification and link reservation requests, and so on. The management plane comprises traffic that allows remote administration and monitoring of network appliances, such as SSH, SNMP, NetFlow, and syslog. Management traffic is typically directed to the appliance's loopback address.

The network must always allow sufficient bandwidth and CPU/memory resource for control and management traffic. If this traffic is blocked, the ability of the network to function is disrupted. Worm malware or malicious reconnaissance tools may attempt to masquerade as high-priority traffic of multiple different types. This places unusually high demands on the routers and switches that process control plane traffic, effecting a DoS attack on the other functions they have to perform. This is also described as a route processor (RP) attack (though note that it can be performed against both routers and switches). Route processing can also be threatened by accidental misconfigurations.

A control plane policing policy is designed to mitigate the risk from route processor vulnerabilities. Such a policy can use ACLs to allow or deny control traffic from certain sources and apply rate-limiting if a source threatens to overwhelm the route processor.

WIRELESS SECURITY

The following features can be enabled to provision secure wireless network access.

●	Preshared keys (PSKs)-Group authentication allows stations to connect to the network using a shared passphrase, which is used to generate a preshared key (PSK). The passphrase should be sufficient length (14+ characters) to ensure a strong key.

●	Extensible Authentication Protocol-An access point can implement a similar port security mechanism to switches. This is configured on the access point by selecting enterprise authentication. This allows users to authenticate to the wireless network against a RADIUS server using their regular network credential. EAP also allows for device authentication using digital certificates.

●	Captive portal-A guest network might be configured to perform authentication by redirecting stations to a secure web page. The user must authenticate to the page and meet other administrator-set requirements, such as accepting a use policy, before the station is authorized to use the network.

●	MAC filtering-As with a switch, an access point can be configured with an accept or deny list of known MAC addresses.

●	Geofencing-Can be used to ensure that the station is within a valid geographic area to access the network, such as ensuring the device is within a building rather than trying to access the WLAN from a car park or other external location.

●	Antenna placement and power levels-Site designs and surveys facilitate robust wireless coverage when all expected areas receive a strong signal. Power levels and channel selection should be tuned so that access points do not interfere with one another or broadcast a signal that stations can "hear" but cannot reply to. The presence of an unusually strong transmitter (30 dBm+) might indicate the presence of an evil twin rogue access point.

●	Wireless client isolation-Clients connected to a WLAN are normally within the same broadcast domain and can communicate with one another. An access point can be configured to prevent this so that stations can only communicate via its gateway. Peer-to-peer traffic is dropped by the AP.

●	Guest network isolation-A guest network can have separate security and forwarding policies applied to it than the network that permits access to the corporate LAN. Typically, a guest network is permitted access to the Internet but not to local servers. Most SOHO routers come with a preconfigured guest network. Within an enterprise, a guest network would be implemented using a separate VLAN.

IOT ACCESS CONSIDERATIONS

Internet of Things (IoT) devices might be present in dedicated embedded systems and smart building networks and/or as individual smart devices installed in employee workplaces. Unmanaged access to these devices can pose a security risk so management and audit procedures must detect and secure them:

●	Perform regular audits to prevent "shadow IT" uncontrolled deployment of smart devices and appliances. This can be assisted through scanning software that specializes in identification of IoT devices, giving visibility into their deployment. Also, educate users about the risks from IoT devices and the necessity of complying with security and IT policies.

●	Ensure that administrative interfaces are secured, and that device configuration and management is assigned to appropriate organizational roles.

●	Include all IoT devices in patch and vulnerability management audits.

●	Isolate management and monitoring traffic for embedded systems to minimize access to and from the corporate data network.

●	Audit supplier security policies and procedures regularly, especially where there are external monitoring or management channels.

PATCH AND FIRMWARE MANAGEMENT

Each type of OS and applications software has vulnerabilities that present opportunities for would-be attackers. As soon as a vulnerability is identified in a supported product, the vendor will (or should) try to correct it. At the same time, attackers will try to exploit it. There can never be a single comprehensive list of vulnerabilities for each OS and app, so you must stay up to date with the system security advisories posted on vendor websites and in other security reference sources. Patch management refers to the procedures put in place to manage the installation of updates for hardware (firmware) and software.

The firmware on a device such as a router/firewall may be a very sophisticated piece of software. It is quite common for such software to have known vulnerabilities, so it is vital to use a secure version. Updating firmware is known as flashing the chip. This is generally done via a vendor-supplied setup program. It is important to make a backup of the system configuration (especially for a firewall) before performing a firmware update or upgrade.

A host OS, such as Windows, can apply patches individually. An appliance OS, such as Cisco IOS, must be patched to a particular version number by applying a new software image. To address a particular vulnerability, you could use a tool such as the IOS Software Checker (tools.cisco.com/security/center/softwarechecker.x) to identify the "first fix" version of IOS for that security advisory. This does mean that other changes could be introduced, so careful testing and impact assessment is required.

Once you have completed environment and compatibility checks and backed up the existing configuration, the basic upgrade process is to copy the new system image to the appliance's flash memory. This can be done over a network using Trivial File Transfer Protocol (TFTP) or remote file copy or by using a removable flash memory card. Once the image update is in place, you run a command sequence to replace the old image and load the new one at startup.

Most software and firmware version changes and updates are upward, toward newer versions. Downgrading (or rollback) refers to reverting to a previous version of the software or firmware. This might be necessary to fix a problem caused by a recently upgraded or updated device or software. In some circumstances downgrading might not be possible. A network appliance might not support downgrading to an earlier firmware version, for instance, or an OS might have to be reinstalled completely. When applying a patch or upgrade, it is common practice to make a configuration backup, in case settings must be reapplied after the update. When downgrading, a configuration backup might not work because it may involve settings not included in the earlier version.