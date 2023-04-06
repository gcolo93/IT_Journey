### **The OSI Model**
Think back to your early lessons on networking and you will likely remember the Open Systems Interconnection model (OSI model) from Unit 2, a conceptual framework that has defined the way computers communicate over networks since the early 1980s. You may recall that one of the motivations for creating the OSI model was to reduce the proprietary nature of networking and increase innovation. Prior to the publication of the OSI model, the computer system manufacturers, such as IBM and Digital, were the primary providers of all network adapters, devices, and protocols used to interconnect their computer systems.

*Diagram. The seven layers of the OSI Model*

Today, computer systems are able to intermingle products, services, and protocols from different hardware and software vendors thanks in part to the well-defined layers of the OSI model.

Each layer represents a part of the computer-to-computer communication process and includes definitions for one or more protocols, services, and devices that satisfy the requirements of that part of the communication process. For example, Layer 2 (data link) includes protocols, such as 802.3 Ethernet and 802.11 Wi-Fi, each of which defines how computers can share access to a common medium such as a wired or wireless network.

The OSI model is often used for troubleshooting network connectivity, but it is equally important to network security assessors when analyzing the network for security threats and vulnerabilities. The layers of the OSI model neatly organize the various protocols, services, and devices in use on the network, and over time the OSI model has enabled developers to create new protocols and services that operate at specific layers. These new protocols and services have, in turn, given rise to new security threats. By using the OSI model as your guide, you can discover how your devices connect together, identify the protocols and services that they use, and then scan them for vulnerabilities and threats that put your network at risk.
### **Layer 1: Physical**
The Physical layer represents the physical medium that connects the computers together. Each medium will have different strengths and weaknesses. For example, consider the security-related differences between a wired network using Category 6 cables versus a wired network using fiber optic cables. If wiretapping or electronic eavesdropping is a concern, the fiber optic cables provide greater security.

Wiretapping is a Layer 1 threat because it involves tampering with the physical cables of a victim’s network. Copper-based wiring, such as Category 6 cabling, is susceptible to electronic sniffing or listening devices because the electrons flowing through the cables create a perceptible electromagnetic field (EMF). Fiber optic cables use light waves instead of electrons and therefore do not emit an EMF signature that can be captured and interpreted.

In your security analysis, you should categorize all physical vulnerabilities and threats as Layer 1 risks. For instance, check the security of the locks on the doors to the data center, equipment racks, and wiring closets throughout your building. Though most of the threats and vulnerabilities at Layer 1 do not seem to directly relate to traditional network security, be careful not to neglect Layer 1 (physical) security. If an attacker can gain physical access to a device, your countermeasures at higher levels of the OSI model may be significantly impaired.
### **Layer 2: Data Link**
As mentioned earlier, where Layer 1 represents how a computer physically connects to the network, Layer 2 represents how computers logically connect to the network. Protocols at Layer 2 define how computers can share access to a common medium, such as a wired or wireless network. This includes protocols such as 802.3 Ethernet and 802.11 Wi-Fi.

Sometimes it can be difficult to determine at which layer of the OSI model an attack occurs. For instance, there is a very fine line between wireless attacks that occur at Layer 1 versus attacks that occur at Layer 2. Consider the following two attacks with very similar results.

An attacker executes a radio jammer attack at Layer 1. The radio jammer sends radio signals, which interfere with the victim's wireless network card and prevents the victim from communicating with a wireless access point (WAP).

Alternatively, the attacker may execute a wireless deauthentication attack at Layer 2 that sends a special wireless frame to a WAP that disconnects the victim's computer from the wireless network.

Both are denial-of-service (DoS) attacks, but the radio jammer attack will affect a large number of users simultaneously, whereas the deauthentication attack is a targeted attack. Additionally, attackers can use the deauthentication attack to capture and then later decrypt the wireless network password sent between the victim's computer and the WAP. While you may not be able to stop the DoS impacts of these attacks, you can minimize your risk of a deauthentication attack revealing your wireless password. To do so, use WPA2 or WPA3 wireless security with a very long and complex passphrase. This does not eliminate the risk, but the long and complex passphrase will resist brute force password crackers longer than a short, simple passphrase.

Wired networks are just as susceptible to attacks at Layer 2. Consider the Ethernet-based attack known as ARP poisoning, which allows an attacker to eavesdrop on all network traffic sent through an Ethernet switch. The attacker sends special Ethernet frames on the network that quickly poison or overwhelm the switch's internal traffic-handling database called the forwarding information base (FIB). Without the FIB, the switch no longer knows where to forward traffic, and so it begins flooding all its ports with every frame it receives, allowing the attacker to receive a copy of all the traffic passing through the switch. When coupled with a packet sniffer, the attacker can reconstruct and analyze the received frames to gather information that will help the attacker to conduct further attacks against the network. An intrusion prevention system (IPS) is one of the best defenses against these attacks.

Another Layer 2 attack targets Ethernet switches that separate traffic into multiple logical networks called virtual local area networks (VLAN). When configuring a switch with VLANs, the network administrator typically configures each switch port to operate in one of two modes: access mode (also called untagged mode) or trunk mode (also called tagging mode). Access mode ports are used by servers and workstations and are assigned to a single VLAN. Trunk mode ports are used for the ports which interconnect multiple switches or routers and carry the traffic of multiple VLANs.

When a computer is attached to an access port, it may only send and receive traffic on the VLAN assigned by the switch; the computer has no control over the VLAN selection. On the other hand, if a network administrator mistakenly configures a computer's switch port as trunk mode, the computer may be able to send and receive traffic on any VLAN on the switch. If an attacker gains access to a computer connected to a trunk port, the attacker can perform a VLAN hopping attack to join a network that would normally not be available to them. The good news is that this attack can be mitigated by following the switch vendor's recommendations for VLAN configuration, as well as by designating all computer switch ports as access mode instead of trunk mode.
### **Layer 3: Network**
The Network layer is so named because it allows computers on different networks to exchange data. This is where you will find the IP and ICMP protocols, which belong to the TCP/IP protocol suite. You might remember the ICMP protocol from earlier lessons because it contains a number of functions that test the connectivity of network devices. For example, the echo-request and echo-reply combination commonly referred to as ping.

Ping attacks, such as the ping flood DoS attack described in an earlier lesson, are typically intended to disrupt communication on the network. However, an attacker can also use ping for information gathering. For example, the ping sweep attack sends pings to a large number of IP addresses to detect which computers are online and may, therefore, be susceptible to other attacks. Fortunately, these attacks can be easily mitigated by using a packet-filtering firewall.

Spoofing is an attack that can occur at both Layer 2 and Layer 3. The goal of a spoofing attack is to impersonate another computer's IP or its Layer 2 media access control (MAC) address. The attacker configures a network card on their computer to impersonate the victim's computer, then sends a special frame onto the network that directs Ethernet switches to forward the victim's traffic, specifically traffic that was originally destined for the victim's IP or MAC address. Intrusion prevention systems (IPS) are best able to prevent this type of attack.
### **Layer 4: Transport**
The two most common protocols within Layer 4 are the TCP and UDP protocols, both of which belong to the TCP/IP suite. Where Layer 3 protocols such as IP use a 32-bit number (for IP version 4) or a 128-bit number (for IP version 6) to uniquely identify each host on a network, protocols at Layer 4 further refine this addressing by using a 16-bit number, called a port number, that uniquely identifies each service on a particular host.

The Transport layer ensures that data received from the upper OSI model layers are delivered according to the needs of the application, for instance, managing a connection-based or connectionless session between the hosts. The applications do not need to be aware of how the transport layer maintains its connectivity.

TCP and UDP play an important role in the way applications communicate. TCP is a connection-oriented protocol, whereas UDP is connectionless. A connection-oriented protocol, such as TCP, provides delivery confirmation for data sent between two computers. If the sender does not receive confirmation of the delivery, it will retransmit the data to ensure it is eventually received. Consider the example of sending an important letter to someone by postal mail. If you want to ensure the recipient gets the message, you can pay for delivery confirmation services. When the letter is delivered, the postmaster sends you a comment card in the mail confirming its receipt. This is similar to TCP traffic where a confirmation is sent back to the sender. UDP works more like standard mail. You place the letter in your outgoing mail without any confirmation that it will arrive, and the receiver is under no obligation to alert you if they get the message.

When a service is run on a computer, that service will open specific ports at the transport layer to allow the service to receive incoming connections from other computers. For example, the DNS service opens TCP port 53 to allow computers to perform name-to-address resolution. An attacker wishing to know which services are running on a victim's computer could run a tool called a port scanner that, as the name implies, allows the attacker to scan the victim's computer for open ports that they could later attack. A packet-filtering firewall is an appropriate defense against port scanners.

In some cases, network administrators redirect a commonly known port number such as TCP port 80, which runs HTTP, to a less expected port number such as TCP port 8080, in hopes of obscuring or hiding the fact that the computer is running a web server. This practice is known as port redirection, and while it may fool a novice attacker, simply changing the port number of a service will not fool a more advanced attacker. In this case, obscurity is not security.
### **Layer 5: Session**
The Session layer allows computers to differentiate between the connections within a service on the same host. This would be similar to you keeping track of different conversations that you are having with the same person. You might talk about one topic for a while, then switch topics back and forth as you chat. In networking, remote procedure call (RPC) is an example protocol at Layer 5 and is used by computers to execute functions and procedures on other computers, such as a central server launching a program or print job. RPC has often been the target of many attacks over the years, but with regular operating system and application patching, you can mitigate most of these attacks.
### **Layer 6: Presentation**
The Presentation layer serves as a translation and security layer between applications, allowing computers to encode and encrypt data. Encoding is the process of writing data in a particular manner, such as a standardized file format like XML or GIF. Encryption is the process of concealing data, and despite its name, is commonly performed at the Presentation layer using Transport Layer Security (TLS), the replacement for the now deprecated SSL protocol commonly used to secure web pages.

Both SSL and TLS have been subject to a number of attacks that target weaknesses in the protocol itself. The goal of many of these attacks is to create a man-in-the-middle attack where the attacker inserts themselves between the victim and an encrypted target, such as the website of a bank. The attacker then impersonates the bank's web security by exploiting a vulnerability in the encryption or by fooling the victim into accepting a false security certificate. The attacker completes the attack by encrypting the traffic between themselves and the victim and then encrypting the traffic between themselves and the target (the bank in this case). The attack is named after the fact that the attacker becomes the man-in-the-middle of the conversation, able to see everything the victim does without encryption. Many of these attacks can be mitigated using an Application-layer proxy or an IPS, though training the users about fake security certificates is equally important.
### **Layer 7: Application**
The Application layer defines how users connect with the application services through protocols such as HTTP. It is the final layer of the OSI model, and like the first layer, it is host to as many different attacks as there are applications. An example of the Application layer is an application programming interface (API) endpoint for web services and websites, both of which leverage the HTTP and HTTPS protocols. Prime targets are web servers, especially web servers that host APIs.

For example, consider that you have created a mobile application to allow your customers to update their information in the customer database located within your corporate data center. The database is not directly accessible on the internet, so you created an application server to perform the read and write requests on behalf of the mobile application. Finally, you created an API to expose a subset of the application server's functions to the mobile application over the internet via the HTTPS protocol.

When a customer uses the mobile application to update their information, the mobile application interacts with the application server via the API. The API calls a specific program or function within the application server to complete the mobile application's request. For security, you configured the mobile application to send the customer's company name along with any requested updates to the API server so that the application server only updates that customer's data when performing database read/write operations.

Analyze this a bit. Though you did use HTTPS to encrypt the data between the mobile application and the API, the application is not yet secure. You incorrectly assumed that the API would only receive requests from your mobile application, and therefore the API did not require any special login or authentication process before it forwards requests to the application server. Unfortunately, this means anyone with a web browser can connect to your API and interact with your application server and data. The HTTPS commands that invoke the API calls are human readable and well documented. It is only a matter of time before an attacker discovers the commands needed through trial and error and then gains access to your data. Now that you know the vulnerability you can probably guess the mitigation. You need to implement authentication between the mobile application and the API.

Even after securing access to the front door of an application or API, you must ensure the application is free of known vulnerabilities. Security professionals use a tool called a vulnerability scanner to detect problems and known bad code that result in vulnerabilities in your applications. The list of vulnerabilities is large and ever increasing. These scanners can help you identify weaknesses that could lead to SQL injection attacks, buffer overrun attacks, and a variety of others that may allow an attacker to take control of your server.

Another way to mitigate attacks at the Application layer is to leverage a reverse proxy system that is able to scan the incoming packet for malicious behavior instead of simply forwarding the malicious payload to the destination. An IPS device will also protect against these threats.