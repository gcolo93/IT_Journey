### **Network Security Terminology**
Many of these terms are defined using the other terms. Where applicable, the corresponding terms are emphasized in the definitions below.

*Asset*: A person, device, location, or information that SecOps aims to protect from attack.

*Attack*: An action taken by a threat that exploits a vulnerability that attempts to either block authorized access to an asset, or to gain unauthorized access to an asset.

*Risk*: The potential of a threat to exploit a vulnerability via an attack.

*SecOps*: The abbreviation for IT security operations; a discipline within IT responsible for protecting assets by reducing the risk of attacks.

*Threat*: Something or someone that can exploit a vulnerability to attack an asset.

*Vulnerability*: A weakness in software, hardware, facilities, or humans that can be exploited by a threat.

Vulnerabilities come in many forms, from hardware and software to buildings and people. You could have an application that runs outdated code that could be exploited by a threat, such as a hacker or a virus. Or your data center may be vulnerable to physical break-ins because it has windows or doors that are left unlocked. Humans can also become vulnerabilities by falling prey to trust games designed by attackers to gain unauthorized access to a building, computer, or network. The goal of SecOps is to eliminate the vulnerabilities where possible, but that is not always possible. You may, however, be able to mitigate the impact of the vulnerability by reducing the amount of damage a potential attack could have on your organization.

A vulnerability scanner is an indispensable tool for detecting vulnerabilities within servers, computers, and network devices. Vulnerability scanners can be cloud-based or may be installed as a software application on your laptop or a dedicated security server. It is important to regularly run these scanners within your network for early identification and mitigation of new vulnerabilities.

### **The CIA Triad**
The confidentiality, integrity, and availability (CIA) triad is a reference model to help protect information from unauthorized disclosure and modification while ensuring it is accessible and intelligible to its authorized users. The CIA triad is composed of three principles: confidentiality, which limits access; integrity, which enables you to trust the information; and availability, which ensures that you have access to the information.

The CIA triad is a model that guides information security policies in organizations. We represent it as a triangle with points C for confidentiality, I for integrity, and A for availability.

Confidentiality refers to data privacy and sensitivity. You could classify internal records, like salaries, financial data, or product development documents as confidential and restrict access to this data.

Integrity is verification that the stored data you retrieve is untampered, unmodified, or unadjusted. For instance, a hacker wouldn't want to delete a log and raise a red flag. But what if the hacker edited the record to remove evidence of any alteration? In this situation, how do you prove data integrity?

Availability is about how accessible you want the information to be. Information on a public website is for wide distribution. Hence, it is entirely available and less private.

To determine where the security needs for a given data set fit in the CIA triad, picture a two-dimensional graph. The Y-axis is between confidentiality and integrity, and the X-axis is between confidentiality and availability. Your data will be somewhere in this triangle— from complete confidentiality to complete availability on the X-axis and between that balance of confidentiality and availability versus integrity on the Y-axis. You usually want to ensure that your data is not corrupted or maliciously modified. Of course, you do update documents and spreadsheets, but those don’t count as malicious modifications. Because you want a fair amount of integrity, your data might be at the top of the Y-axis near the “I.” Next, you need to decide where your data should be on the X-axis between confidentiality and availability. Something on a public website might be closer to A, while private information might be closer to C. You decide where your data fits within the C, I, and A points in the triad. You might mark information as sensitive, extremely sensitive, or top secret and accordingly decide where to store it, how to make it available, and who can access it. You might use checksums to verify data integrity. For this, you could use a file that lists all the files, each with a checksum, to make sure a hacker didn't maliciously delete data. You can control the availability of data with permissions. For this, you again decide how accessible you want to make it, where you store it, and who gets access to modify it.

To summarize, think about where your data fits within the CIA triad. Typically, your data would be more towards the upper end of the Y-axis and just about anywhere on the X-axis.
### **CIA Triad**
*Diagram: The CIA Triad*

Consistency is critical in security management; therefore, some organizations create specific classifications for their data that define different sensitivity levels, each with specific policies that explain how the information should be handled. These classification levels are then applied to every file, email, database, and even printed papers. When evaluating the sensitivity of a piece of information, all three of the CIA principles should be taken into consideration; however, depending on the type of information, you may focus more on one principle than another.
### **Confidentiality**
The confidentiality principle helps limit access to information, which, by definition, can contradict some of the recommendations found in the availability principle. The goal of confidentiality is to prevent an unauthorized user from accessing, copying, or transmitting the information.

Confidentiality is often equated to privacy because the two terms share many of the same characteristics, such as ensuring that only the intended recipient of the information can access it, following a need-to-know policy, and reducing exposure by destroying all copies of the information that are no longer needed.

There are many ways to breach or compromise the confidentiality of data if the proper precautions are not taken in advance and then routinely checked for accuracy and consistency.

- Unencrypted information is easy to steal and change.
- Deleted files are rarely purged from a disk immediately and often can be recovered with ease.
- The physical theft of a device gives an attacker an unlimited time window to break the encryption of your data.
- Social engineering is a method used by attackers to gain an unsuspecting victim’s trust to provide information, such as passwords or server names, or even just to gain physical building access.
- Accidents and malfunctions also play into the equation. For example, confidentiality of information can easily be breached by storing files in the wrong location, emailing data to the wrong person, or printing confidential information to a public printer.

Some methods that may help prevent compromises include:

- Where possible, encrypt the information at-rest (where it is stored) and in-transit (while it is moving across the network).
- Be sure to encrypt and physically secure your laptops, servers, portable hard drives, and even backup tapes/disks.
- Consider using a tool to securely delete files or overwrite them after deletion.
- Train your employees about social engineering attacks.
- Create and enforce a policy that ensures all users must use complex passwords (a combination of uppercase and lowercase letters, numbers, and symbols with a minimum length) and use multifactor authentication (MFA), such as biometrics or a digital key fob.
- Following the principle of least privilege (which means you only assign users the minimum permissions needed to perform their jobs), institute restrictive access controls on all data and provide access to information on a need-to-know basis only.
### **Integrity**
The integrity principle helps identify the trustworthiness of the information. It is possible to identify where the information came from and if the data has changed since it was originally sent. Integrity is a function that is often incorporated into encryption and, therefore, works well with the confidentiality principle.

Some of the compromises of data integrity include:

- Man-in-the-middle attacks, where an attacker changes the contents of the message after it was sent, but before it was received
- The intentional or unintentional deletion or modification of data
- Malfunctions in equipment that cause data corruption
- Natural phenomena such as electromagnetic pulse (EMP) attacks, which can destroy or severely corrupt data

Some methods that can be employed to help prevent the compromise of data integrity include:

- Require all data transmissions to use encryption or digital signatures to confirm the identity of the sender and to identify if the message has been changed.
- In cases where digital signatures will not work, use one-way hash calculations, such as SHA-3 (Secure Hash Algorithm 3), to create a value that can be used to verify the data has not changed.
- Use version control within your data storage to help you quickly revert accidental changes or deletions.
### **Availability**
The goal of the availability principle is to ensure that the data is always accessible by its authorized users. This includes aspects such as adding high availability to your server solutions and minimizing downtime by carefully managing your application updates and patches.

Some of the common actions that can compromise the availability of data include:

- denial-of-service (DoS) and distributed denial-of-service (DDoS) attacks, which prevent legitimate users from accessing the resource by sending an overwhelming amount of data to the target server;
- unplanned downtime due to server crashes or failed upgrades; and
- accidental changes to access control lists, which removes access for authorized users.

Some methods that can be employed to help prevent availability issues include:

- creating and maintaining a full disaster recovery plan that includes a full site failover as well as the method to restore data for individual servers;
- implementing server high availability where possible, employing clustering technology where appropriate; and
- setting up regular backups of your data and considering storing a backup copy at another physical location to protect against site-level disasters.

### **Firewalls**
A network firewall is a barrier that intercepts and inspects traffic moving from one area of the network to another. Nearly all networks today benefit from the protection of some type of firewall. In all likelihood, you passed through several firewalls when you opened this material. You probably have a firewall at home that allows you to access the internet while simultaneously preventing intruders from accessing your home network. The servers hosting this material are also protected by a firewall that limits the type of internet traffic that can reach them.

Firewalls come in a variety of forms and provide a range of functionality. Some may be physical appliances mounted in data centers, while others may be virtual appliances operating as VMs (virtual machines). Still, there are others known as host-based firewalls that operate as applications running on workstations and servers. They all have something in common though; they have a set of rules that define whether the firewall will permit or deny the traffic to pass on to its intended destination. In the following sections you will explore firewall types, functionality, and terminology.

*Diagram. Packet filtering in the OSI model.*
### **Packet Filters**
A packet filter is a firewall that operates at Layers 3 and 4 of the OSI network model: network and transport.

In most networks today, that equates to the IP address (Layer 3) and the TCP or UDP port number (Layer 4) of the traffic passing through the firewall. These firewalls inspect incoming (ingress) and outgoing (egress) traffic and compare the following attributes to a database of packet filter rules that determine if the firewall will forward (allow) or drop (deny) the traffic:

- Protocol (typically IP)
- Source IP Address
- Destination IP Address
- Source TCP or UDP port number
- Destination TCP or UDP port number

These firewalls are only concerned with the address label (header) of the packets and perform no level of inspection on the contents of the packet (the payload). This means that potentially dangerous payloads could pass through a packet filter without being detected as long as the source and destination values were approved by the firewall rules.
### **Circuit-Level Gateways**
A circuit-level gateway is a device that operates as a middleman between two or more systems to help conceal the true identity of the client and server. The gateway may change the IP address and the TCP/UDP port number of the traffic to allow two networks to communicate that otherwise could not (for example, your home network and the internet).

Circuit-level gateways are the foundation of network address translation (NAT) and port address translation (PAT), which are commonly used in firewalls to allow private IP address ranges to communicate on the internet. These firewalls are only concerned with the address label (header) of the packets and perform no level of inspection on the contents of the packet (the payload). This means that potentially dangerous payloads could pass through a packet filter without being detected as long as the source and destination values were approved by the firewall rules.

*Diagram. A stateful firewall in the OSI model.*
### **Stateful Inspection**
To help you understand the significance of stateful inspection in firewalls, you must first understand the meaning of the term state. In this context, the word state refers to the connection state of a conversation between two computers. Some protocols, such as TCP, require that the recipient of a message respond back to the sender with an acknowledgment that it received the data. In a packet filter firewall, this would require at least two firewall rules: one that allows the sender to transmit data to the recipient, and another that allows the recipient to respond (acknowledge) back to the sender. Now consider the implications of a sender communicating with many recipients. There is still one rule for the sender, but now there are many rules for the acknowledgments because each recipient requires a rule to respond to the sender.

To reduce the number of firewall rules needed to support TCP communication, firewall vendors implemented a feature known as stateful inspection. This feature allows a firewall to identify traffic as conversational and automatically create temporary firewall rules to permit the response traffic to flow back to the sender. In this way, instead of maintaining a multitude of rules, in a firewall with stateful inspection, you only need to create a firewall rule that allows the communication to begin.
### **Application Level**
Remember, packet filter firewalls lack the ability to inspect the contents of the packets. Because of this, malicious traffic could pass into the network unchecked. To combat this potential weakness in security, network administrators began using proxy servers that could act as a middleman, reading and parsing the traffic payload, and then forwarding it on to the intended destination if the payload was safe. This behavior was later incorporated into firewalls to provide a deeper level of inspection. Firewalls with this ability are commonly called application-aware firewalls, or Layer-7 firewalls because application is the seventh layer of the OSI model.
### **Intrusion Detection and Prevention**
Intrusion detection systems (IDS) and intrusion prevention systems (IPS) are advanced security solutions that can identify malicious traffic based on a database of known behaviors and payload signatures. IDSs monitor the network to detect threats, whereas IPSs intercept and block threats.

Both types of systems can be configured to operate in tap mode, which is where they attach to the network as listening devices only. The name tap comes from the term wiretapping because these devices are essentially eavesdropping on the traffic flowing through the network. The tap mode works well for IDS devices because they are passive listeners on the network and are designed to alert a network administrator if they detect any suspicious behavior.

On the other hand, tap mode does not work as well for IPS devices, which are designed to intercept and block suspicious traffic. For an IPS device to stop traffic, it must be positioned in the middle of the traffic stream, a configuration known as in-line mode. Typically, IPS devices have many network ports that are designed to operate as input/output pairs. The network administrator will physically route cables through the IPS device to create choke points in the network. For example, you have a set of public web servers connected to a dedicated network switch that is connected to your firewall by one network cable. You acquire an IPS device so that you can scan the traffic entering and leaving that network. To do so, you will disconnect the existing cable that connects the switch to the firewall and then place the IPS device in-line by connecting the firewall to one of the ports in an input/output pair and the switch to the other port in the pair. The IPS device bridges the traffic and appears invisible on the network, yet it is actually inspecting every packet and copying it from one cable to the other.

If the IPS device detects an anomaly, such as an unknown packet type or pattern of traffic, it can alert the administrator or block the traffic immediately. If it detects malicious traffic, it typically blocks the traffic automatically. There are also cases where the IPS device may block traffic, particularly files that are known to carry viruses and malware. This is a method known as reputation-based protection, because the file is blocked based on how often that type of file is found to carry viruses or malware. A good example of this is when IPS devices and firewalls block executable (EXE) attachments or downloads.

Like firewalls, IPS and IDS devices are not always physical appliances. They are also available as virtual appliances and as host-based IPS/IDS applications, which can be installed on your servers or workstations.

*Diagram. Intrusion detection system (IDS).*