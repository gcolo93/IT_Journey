Lesson 16: Comparing WAN Links and Remote Access Methods

Topic 16A: Explain WAN Provider Links

WIDE AREA NETWORKS AND THE OSI MODEL

Wide area network (WAN) technologies support data communications over greater distances than LANs. The term enterprise WAN is used to describe a WAN that is used and controlled by a single organization. However, even though an enterprise may control its WAN, it rarely owns all the infrastructure that supports it. Long distance communications usually involve the use of public networks. Public networks are owned by telecommunications (telco) companies and provide WAN services to businesses and households. Organizations often choose to use public networks, as the cost is far less than implementing a private solution. Service providers often have rights of access to locations that are not available to other organizations, such as under roads.

As with a LAN, the WAN Physical layer describes the media type and interface specifications. Where the provider link is a copper cable, some type of modem is usually used, rather than a switch. A modem performs modulation of outgoing signals and demodulation of incoming data, working only at the physical layer of the OSI model. Modulation means transforming an electromagnetic wave to represent information, such as using the amplitude (height) of the wave to represent bits. Legacy modems perform digital to analog modulation for transmission over voice lines. An analog (or dial-up) modem only supports low bandwidths (up to 56 Kbps). Digital modems perform a different type of modulation to transform digital signals received as Ethernet frames for transmission over the WAN media. Digital modem types include data service units (DSUs) for leased lines, digital subscriber line (DSL) modems, cable modems, and satellite modems.

At the data link layer, WANs often use simpler protocols to Ethernet LANs as the links are more likely to be point-to-point and do not need much complexity. That said, Ethernet is increasingly being deployed for end-to-end connectivity over WANs.

At the network layer, the customer and provider site are addressed using IP. A customer edge (CE) router connects to a provider edge (PE) via the underlying link layer interface. The provider allocates public IPv4/IPv6 addresses or address ranges to the customer.

WAN PROVIDER LINKS

Establishing a WAN provider link means terminating the access provider's cabling at some point in your premises, and then attaching modem and routing equipment to that line. The service-related entry point at which the access provider's network terminates is called the demarcation point (or demarc for short) or minimum point of entry (MPOE). The demarc point represents the end of the telco's responsibility for maintaining that part of the cabling. Any cable problems arising from the other side of the demarc point are the responsibility of the customer.

Modems and routers or other access equipment that are provided or leased by the customer and installed at their site are referred to as customer premises equipment (CPE). Some providers may take on responsibility for faults that arise in CPE, depending on the contract and installation circumstances.

The demarc and CPE should be installed to a secure location within the premises, with access controls to restrict the area to authorized staff. This location is referred to as entrance facilities in TIA/EIA structured cabling standards.

T-CARRIER AND LEASED LINE PROVIDER LINKS

The T-carrier system was developed by the telecommunications provider Bell Labs to allow multiple calls to be placed on a single cable. T-carrier enabled voice traffic to be digitized for transport around the core of the telecommunications network. It also enabled other types of digital data to be transported and could be provisioned directly to subscribers as a leased line. T-carrier is based on Time Division Multiplexing (TDM). The protocol assigns each circuit (or channel) a time slot. Each 64 Kbps channel provides enough bandwidth for a digitized voice call.

A single 64 Kbps channel is known as a DS0 or narrowband link. For leased line data services, however, the foundation level of T-carrier is the DS1 or T1 digital signal circuit. This service comprises 24 channels multiplexed into a single 1.544 Mbps full duplex digital connection that can be used for voice and/or data. The T1 lines themselves can be multiplexed to provide even more bandwidth.

A T1 line from the service provider is terminated at the demarc on a smartjack or Network Interface Unit (NIU). The smart jack has an RJ-48C or RJ-48X interface on the customer side that is used to connect to the customer’s Channel Service Unit/Data Service Unit (CSU/DSU) . The cabling from the smart jack to the CSU/DSU can use an ordinary RJ-45 patch cord (up to 3 meters/10 feet in length), but a shielded two-pair 22 AWG cable with connectors wired for RJ-48 is required for any distance longer than that.

The RJ-48X jack has a shorting bar to provide loopback on the connection if the equipment on the customer side is unplugged. This allows the service provider to test the line remotely.

The DSU encodes the signal from Data Terminal Equipment (DTE)-that is, the company's private branch exchange (PBX) internal telecoms system and/or an IP router-to a serial digital signal transmitted over copper wiring. The DSU part functions as a digital modem, while the CSU is used to perform diagnostic tests on the line. The devices can be supplied separately, but more typically they are combined as a single WAN interface card that can be plugged into a compatible router or PBX.

WAN termination equipment. (Image © 123RF.com.)

At the data link layer, T1 leased lines typically use either High-level Data Link Control (HDLC) or Point-to-Point Protocol (PPP).

DIGITAL SUBSCRIBER LINE PROVIDER LINKS

Digital subscriber line (DSL) is a technology for transferring data over voice-grade telephone lines, often referred to as the local loop. DSL uses the frequencies above those used by the human voice as a full duplex communications channel.

DSL Modems

A DSL modem is installed as CPE, typically as a multifunction “wireless router,” where the RJ-11 WAN port connects to the provider’s phone jack over a short length of ribbon cable. DSL modems can also be supplied as separate appliances or plug-in cards for routers. A standalone DSL modem is connected to the phone line via an RJ-11 port and to the local network's router (or a single computer on the local network) via an RJ-45 Ethernet port.

RJ-11 DSL (left) and RJ-45 LAN (right) ports on a DSL modem. (Image © 123RF.com.)

A filter (splitter) must be installed on each phone point to prevent noise from affecting either voice calls or the DSL link. These can either be installed at the demarc point by the telco engineer or self-installed on each phone point by the customer.

The main drawback of DSL is that, as a copper-wire technology, it suffers from attenuation. The maximum range of a DSL modem is typically about 3 miles (5 km), but the longer the connection, the greater the deterioration in data rate. Domestic cabling may also be relatively poor quality and pass through "noisy" environments.

DSL Types

There are various types or flavors of DSL. These are standardized by the ITU in a series of G. recommendations.

●	Symmetrical DSL (SDSL) is so-called because it provides the same downlink and uplink bandwidth. There are various types of symmetric DSL service. SDSL services tend to be provided as business packages, rather than to residential customers.

●	Asymmetrical DSL (ADSL) (G.992) is a consumer version of DSL that provides a fast downlink but a slow uplink. There are various iterations of ADSL, with the latest (ADSL2+) offering downlink rates up to about 24 Mbps and uplink rates up to 3.3 Mbps. Service providers may impose usage restrictions to limit the amount of data downloaded per month. Actual speed may be affected by the quality of the cabling in the consumer's premises and between the premises and the exchange, and by the number of users connected to the same DSLAM (contention).

FIBER TO THE CURB

The major obstacle to providing WAN access that can approach LAN performance is bandwidth in the last mile, where the copper wiring infrastructure is generally not good. The projects to update this wiring to use fiber optic links are referred to by the umbrella term Fiber to the X (FTTx).

The most expensive solution is Fiber to the Premises (FTTP) or its residential variant Fiber to the Home (FTTH). The essential point about both these implementations is that the fiber link is terminated at the demarc. Other solutions can variously be described as Fiber to the Node (FTTN) or Fiber to the Curb (FTTC). These retain some sort of copper wiring to the demarc while extending the fiber link to a communications cabinet servicing multiple subscribers. The service providers with their roots in telephone networks use Very high-speed DSL (VDSL) to support FTTC. VDSL (G.993) achieves higher bit rates than other DSL types at the expense of range. It allows for both symmetric and asymmetric modes. Over 300 m (1000 feet), an asymmetric link supports 52 Mbps downstream and 6 Mbps upstream, while a symmetric link supports 26 Mbps in both directions. VDSL2 specifies a very short range (100 m/300 feet) rate of 100 Mbps (bi-directional).

The modem type must match the service. An ADSL-only modem cannot be used to access a VDSL service, for instance.

CABLE PROVIDER LINKS

A cable Internet connection is usually available along with Cable Access TV (CATV). These networks are sometimes described as hybrid fiber coax (HFC) because they combine a fiber optic core network with coax links to CPE, but are more simply just described as cable broadband.

A cable modem-The RJ-45 port connects to the local network, while the coax port connects to the service provider network. (Image © 123RF.com.)

Installation of a cable modem follows the same general principles as for a DSL modem. The cable modem is interfaced to a computer or router through an Ethernet or USB adapter and with the access provider's network by a short segment of coax. More coax then links all the premises in a street with a Cable Modem Termination System (CMTS), which routes data traffic via the fiber backbone to the ISP's Point of Presence (PoP) and from there to the Internet. Cable based on the Data Over Cable Service Interface Specification (DOCSIS) supports downlink speeds of up to 38 Mbps (North America) or 50 Mbps (Europe) and uplinks of up to 27 Mbps. DOCSIS version 3 allows the use of multiplexed channels to achieve higher bandwidth.

METRO-OPTICAL PROVIDER LINKS

Carrier Ethernet provisions point-to-point or point-to-multipoint Ethernet leased lines over wide area networks. Carrier Ethernet may also be also referred to as a metro-optical provider link. The term Metro Ethernet refers to Carrier Ethernet where the geographic scope is limited to a single city. Standards for Carrier Ethernet are developed by the MEF ( mef.net ). Carrier Ethernet can use different types of physical connectivity. Some examples include:

●	Ethernet over Fiber-Uses the IEEE 802.3 10GBASE-LR and 10GBASE-ER specifications.

●	Ethernet over Copper-Uses DSL variants such as single-pair high-speed DSL (SHDSL) and VDSL to overcome the usual distance limitations of copper Ethernet. This does not support anything like the same speeds as LAN Ethernet (more typically 2-10 Mbps), but multiple pairs can be aggregated for higher bandwidth.

On top of the physical connectivity method, there are multiple service categories for Carrier Ethernet. Two of these are E-line and E-LAN:

●	E-line-Establishes a point-to-point link between two sites. Multiple E-lines can be configured on a single Metro Ethernet interface, with each E-line representing a separate VLAN.

●	E-LAN-Establishes a mesh topology between multiple sites.

These services can be used by the customer to join multiple sites together or as a way of connecting their enterprise network to the Internet. From the customer’s perspective, Carrier Ethernet has many advantages. The fact that Carrier Ethernet is easily scalable affords businesses the flexibility to match the service to their changing demands. Also, the fact that the same Ethernet protocol and framing is used on the LAN and connectivity into the public network space can make the configuration of routers, Layer 3 switches, and firewalls simpler.

Full fiber connections are also being provisioned to residential and small business customers, though availability can often be limited to a few metropolitan areas. Rather than dedicated leased lines, these services are deployed as a passive optical network (PON). Packages are offered in tiers from 100 Mbps up to 1 Gbps.

In a PON, a single fiber cable is run from the nearest exchange to an optical line terminal (OLT) located in the street. This link uses dense wavelength division multiplexing (DWDM) to support a ratio of backhaul cable to subscribers of 1:64 or 1:128. From the OLT, splitters direct each subscriber’s wavelength frequency over a shorter length of fiber to an optical network unit (ONU) or optical network terminal (ONT) installed at the demarc. The ONU/ONT converts the optical signal to an electrical one. The ONU/ONT is connected to the customer’s router using a copper wire patch cord.

MICROWAVE SATELLITE

Satellite systems provide far bigger areas of coverage than can be achieved by using other technologies. The microwave dishes are aligned to orbital satellites that can either relay signals between sites directly or via another satellite. The widespread use of satellite television receivers allows for domestic Internet connectivity services over satellite connections. Satellite services for business are also expanding, especially in rural areas where DSL or cable services are unlikely to be available.

Satellite connections experience quite severe latency problems as the signal must travel over thousands of miles more than terrestrial connections, introducing a delay of four to five times what might be expected over a land link. For example, if you know that accessing a site in the US from Europe takes 200 ms over a land (undersea) link, accessing the same site over a satellite link could involve a 900 ms delay. This is an issue for real-time applications, such as videoconferencing, VoIP, and multiplayer gaming.

To create a satellite Internet connection, the ISP installs a satellite dish, referred to as a very small aperture terminal (VSAT), at the customer's premises and aligns it with the orbital satellite. The size of a VSAT ranges from 1.2 to 2.4 meters in diameter. The satellites are in geostationary orbit over the equator, so in the northern hemisphere the dish will be pointing south. The antenna is connected via coaxial cabling to a Digital Video Broadcast Satellite (DVB-S) modem.

Topic 16B: Compare and Contrast Remote Access Methods

REMOTE NETWORK ACCESS AUTHENTICATION AND AUTHORIZATION

Remote network access means that the user's device does not make a direct cabled or wireless connection to the network. The connection occurs over or through an intermediate network, usually a public WAN. Historically, remote network access might have used analog modems connecting over the telephone system. These days, most remote access is implemented as a virtual private network (VPN), running over the Internet.

Given that, administering remote access involves essentially the same tasks as administering the local network. Only authorized users who have successfully authenticated should be allowed access to local network resources and communication channels. Additional complexity comes about because it can be more difficult to ensure the security of remote workstations and servers and there is greater opportunity for remote logins to be exploited.

The creation of a remote access server (RAS) should be accompanied by documentation describing the uses of the service, security risks and countermeasures, and authorized users of the service. There should also be authorization to run the service from the network manager. The remote access policy should then implement the measures identified through compiling the documentation. Typical policy restrictions would be:

●	Restricting access to defined users or groups.

●	Restricting access to defined times of day or particular days of the week.

●	Restricting privileges on the local network (ideally, remote users would only be permitted access to a clearly defined part of the network).

●	Logging and auditing access logons and attempted logons.

In addition to this, a management plan should ensure that RASs and other hardware are kept up to date with the latest software or firmware updates. Administrative access to the devices should also be secured, using strong authentication.

TUNNELING AND ENCAPSULATION PROTOCOLS

Most modern remote network access solutions use Internet access infrastructure and set up a secure tunnel for private communications through the Internet. This is referred to as a virtual private network (VPN). Most business and residential sites have Internet connectivity, so this solution is very efficient in terms of cost. The main concerns are providing security for the transmissions that pass through the public network and preventing unauthorized users from making use of the VPN connection.

Point-to-Point Protocol

VPNs depend on tunneling protocols. Tunneling is used when the source and destination hosts are on the same logical network but connected via different physical networks. The Point-to-Point Protocol (PPP) is an encapsulation protocol that works at the Data Link layer (Layer 2). PPP is used to encapsulate IP packets for transmission over serial digital lines. PPP has no security mechanisms, so must be used with other protocols to provision a secure tunnel.

Generic Routing Encapsulation

Where PPP works at Layer 2, Generic Routing Encapsulation (GRE) works at Layer 3. A GRE packet can itself encapsulate an IP packet (or most other network layer protocol types) as its payload. The "outer" GRE packet is assigned protocol number 47 and has its own IP source and header address fields. The GRE packet is then itself encapsulated in a Layer 2 frame for transmission to the next hop router. Each intermediate router inspects only the outer GRE header to determine the forwarding destination. At the final destination, the receiving router de-encapsulates the GRE packet to extract the inner IP payload and forwards that inner packet to its destination. GRE does not have any mechanisms for authenticating users or devices and so is often used with other protocols in a VPN solution.

IP Security

Internet Protocol Security (IPSec) also operates at the network layer (Layer 3) of the OSI model to encrypt packets passing over any network. IPSec is often used with other protocols to provide connection security, but is increasingly used as a native VPN protocol.

Transport Layer Security

Transport Layer Security (TLS) over TCP or datagram TLS (DTLS) over UDP can be used to encapsulate frames or IP packets. The main drawback is that as TLS already operates at the session layer, the headers from the inner and outer packets add up to a significant overhead.

CLIENT-TO-SITE VIRTUAL PRIVATE NETWORKS

A VPN can be implemented in several topologies. In a client-to-site or remote access topology, the VPN client connects over the public network to a VPN gateway (a VPN-enabled router) positioned on the edge of the local network (typically the VPN access server will be in a screened subnet). Client-to-site is the "telecommuter" model, allowing home-workers and employees working in the field to connect to the corporate network.

Client-to-site VPNs can be configured using a number of protocols. An SSL/TLS VPN solution uses certificates to establish the secure tunnel. One example is Microsoft’s Secure Socket Tunneling Protocol (SSTP). Cisco’s Layer 2 Tunneling Protocol (L2TP) is also widely used, in conjunction with IPSec. All these solutions require client software to operate. Most VPN solutions use EAP and AAA/RADIUS architecture to authenticate client devices and users.

Microsoft’s Point-to-Point Tunneling Protocol (PPTP) was once very widely used but has too many security flaws to be deployed safely.

When a client connected to a remote access VPN tries to access other sites on the Internet, there are two ways to manage the connection:

●	Split tunnel-the client accesses the Internet directly using its "native" IP configuration and DNS servers.

Split tunnel VPN traffic flow. (Images © 123RF.com.)

●	Full tunnel-Internet access is mediated by the corporate network, which will alter the client's IP address and DNS servers and may use a proxy.

Full tunnel VPN traffic flow. (Images © 123RF.com.)

Full tunnel offers better security, but the network address translations and DNS operations required may cause problems with some websites, especially cloud services. It also means more data is channeled over the link and the connection can exhibit higher latency.

REMOTE HOST ACCESS AND REMOTE DESKTOP GATEWAYS

A remote access VPN refers to extending local network access over an intermediate public network, so that a remote computer is effectively joined to the local network. Remote access can also refer to remote host access, where a user operates a computer or configures a network appliance without having to use a local terminal. This type of remote host access can be implemented within a local network or over a public network. It can be used for a variety of purposes:

●	Remote configuration of network appliances. Most of these appliances are headless (they do not have a video monitor or input devices) and remote connections are the only practical configuration option. This type of connection is typically implemented using Secure Shell (SSH).

●	Remote desktop connections either allow an administrator to configure a server or a user to operate a computer remotely. Where remote desktop protocols provide GUI access, other protocols can be used for terminal-only access.

●	Remote desktop gateways allow user access to networked apps. A gateway can also be used to connect a user to a virtual desktop, where a client OS and applications software is provisioned as a virtual appliance. Alternatively, a remote desktop gateway is a means of implementing a clientless VPN.

Remote Desktop Protocol and Virtual Network Computing

Microsoft's Remote Desktop Protocol (RDP) can be used to access a physical machine on a one-to-one basis. Alternatively, the site can operate a remote desktop gateway that facilitates access to virtual desktops or individual apps running on the network servers (docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/welcome-to-rds). Similar services are provided by Citrix’s products (citrix.com/products).

There are several popular alternatives to Remote Desktop. Most support remote access to platforms other than Windows (macOS and iOS, Linux, Chrome OS, and Android for instance). Examples include TeamViewer (teamviewer.com/en) and Virtual Network Computing (VNC) , which is implemented by several different providers (notably realvnc.com/en).

Clientless VPNs

Traditionally, remote desktop products and client-to-site VPNs require a client app that implements the protocols and authentication methods supported by the remote desktop/VPN gateway. The canvas element introduced in HTML5 allows a browser to draw and update a desktop with relatively little lag. It can also handle audio. This allows ordinary browser software to connect to a remote desktop or VPN. This is referred to as an HTML5 VPN or clientless VPN ( guacamole.apache.org ). This solution also uses a protocol called WebSockets, which enables bidirectional messages to be sent between the server and client without requiring the overhead of separate HTTP requests.

SITE-TO-SITE VIRTUAL PRIVATE NETWORKS

A VPN can also be deployed in a site-to-site model to connect two or more private networks. Where remote access VPN connections are typically initiated by the client, a site-to-site VPN is configured to operate automatically. The gateways exchange security information using whichever protocol the VPN is based on. This establishes a trust relationship between the gateways and sets up a secure connection through which to tunnel data. Hosts at each site do not need to be configured with any information about the VPN. The routing infrastructure at each site determines whether to deliver traffic locally or send it over the VPN tunnel. This is also referred to as compulsory tunneling. Compulsory tunnels can be in place permanently (static), or they can be put in place based on the data or client type (dynamic).

Site-to-site VPN. (Images © 123rf.com.)

VPNs are not always established over the public Internet. A WAN service provider can implement VPNs via its network. The provider can use VLAN-like technology to isolate a customer's data from other traffic. This is a common model for site-to-site VPNs.

While VPNs are being covered here as part of remote access, they can be just as usefully deployed on local networks as a type of network segmentation. For example, the department for product development might need to provide secure communications with the marketing department.

HUB AND SPOKE VPNS AND VPN HEADENDS

A site-to-site VPN that involves more than two sites connects the remote sites (or spokes) to a headquarters site (hub) by using static tunnels configured between the hub and each spoke. This is referred to as a hub and spoke topology. The VPN router installed in the central office or hub needs to be a powerful machine capable of aggregating high traffic volumes. This VPN router is also referred to as a VPN headend. VPN headends would normally be installed in groups for load balancing and fault tolerance. A VPN headend must be able to scale to meet changing demand levels. The VPN routers installed at the spokes, are referred to as branch office routers.

A dynamic multipoint VPN (DMVPN) allows VPNs to be set up dynamically according to traffic requirements and demand. The original concept was developed by Cisco but has been adopted by other vendors and now runs on diverse router platforms. DMVPN allows for the use of a dynamic mesh topology between multiple remote sites, effectively setting up direct VPNs, rather than the remote sites having to route traffic via the hub. Each site can communicate with all other spokes directly no matter where they are located.

DMVPN topology. Each branch office establishes a permanent VPN with the HQ (hub) but can also create spoke-to-spoke VPNs dynamically. (Images © 123RF.com.)

To configure a DMVPN, each remote site's router is still connected to the hub router using an IPSec tunnel. As a large percentage of a remote site's traffic is likely to be with the main HQ, this ensures this normal traffic is dealt with efficiently. If two remote sites (spokes) wish to communicate with one another, the spoke instigating the link informs the hub. The hub will provide the connection details for the other spoke facilitating a dynamic IPSec tunnel to be created directly between the two spokes. This process invokes the use of the Next Hop Router Protocol (NHRP) to identify destination addresses and the GRE tunneling. GRE encapsulates the encrypted IPSec packets. The two remote sites use the physical communications links between the two locations but all traffic flows over the temporary, encrypted VPN tunnel setup between them. DMVPN will then decide how long this temporary VPN remains in place based on timers and traffic flows.

In this way, DMVPN allows remote sites to connect with each other over the public WAN or Internet, such as when using video conferencing, but doesn't require a static VPN connection between sites. This on-demand deployment of IPSec VPNs is more efficient. Routing policies can be used to select the most reliable path between the remote sites, which potentially reduces the chance of latency and jitter affecting any voice/video services running over the VPN.

INTERNET PROTOCOL SECURITY

Internet Protocol Security (IPSec) can be used to secure IPv4 and/or IPv6 communications on local networks and as a remote access protocol.

Each host that uses IPSec must be assigned a policy. An IPSec policy sets the authentication mechanism and also the protocols and mode for the connection. Hosts must be able to match at least one matching security method for a connection to be established. There are two core protocols in IPSec, which can be applied singly or together, depending on the policy.

Authentication Header

The Authentication Header (AH) protocol performs a cryptographic hash on the whole packet, including the IP header, plus a shared secret key (known only to the communicating hosts), and adds this secret in its header as an Integrity Check Value (ICV). The recipient performs the same function on the packet and key and should derive the same value to confirm that the packet has not been modified. The payload is not encrypted so this protocol does not provide confidentiality. Also, the inclusion of IP header fields in the ICV means that the check will fail across NAT gateways, where the IP address is rewritten. Consequently, AH is not often used.

IPSec datagram using AH-The integrity of the payload and IP header is ensured by the Integrity Check Value (ICV), but the payload is not encrypted.

Encapsulating Security Payload (ESP) provides confidentiality and/or authentication and integrity. It can be used to encrypt the packet rather than simply calculating a hash. ESP attaches three fields to the packet: a header, a trailer (providing padding for the cryptographic function), and an Integrity Check Value. Unlike AH, ESP excludes the IP header when calculating the ICV.

IPSec datagram using ESP-The TCP header and payload from the original packet is encapsulated within ESP and encrypted to provide confidentiality.

With ESP, algorithms for both confidentiality (symmetric cipher) and authentication/integrity (hash function) are usually applied together. It is possible to use one or the other, however.

The principles underlying IPSec are the same for IPv4 and IPv6, but the header formats are different. IPSec makes use of extension headers in IPv6 while in IPv4, ESP and AH are allocated new IP protocol numbers (50 and 51), and either modify the original IP header or encapsulate the original packet, depending on whether transport or tunnel mode is used.

IKE AND IPSEC MODES

IPSec's encryption and hashing functions depend on a shared secret. The secret must be communicated to both hosts and the hosts must confirm one another's identity (mutual authentication). The Internet Key Exchange (IKE) protocol handles authentication and key exchange, referred to as Security Associations (SA).

Configuring IKE in the OPNsense security appliance. (Screenshot used with permission from OPNsense.)

IPSec can be used in two modes:

●	Transport mode-this mode is used to secure communications between hosts on a private network (an end-to-end implementation). When ESP is applied in transport mode, the IP header for each packet is not encrypted, just the payload data. If AH is used in transport mode, it can provide integrity for the IP header.

●	Tunnel mode-this mode is used for communications between VPN gateways across an unsecure network (creating a VPN). This is also referred to as a router implementation. With ESP, the whole IP packet (header and payload) is encrypted and encapsulated as a datagram with a new IP header. AH has no real use case in tunnel mode, as confidentiality will usually be required.

Configuring an IPSec tunnel in the OPNsense security appliance. (Screenshot used with permission from OPNsense.)

OUT-OF-BAND MANAGEMENT METHODS

Some network appliances, such as unmanaged switches, do not offer any configuration options or interface. You just have to plug them in, and they operate automatically. Managed switches and appliances, such as routers, firewalls, switches, and access points, support more complex functions and can be configured and monitored over several interfaces. The functions of a managed appliance can be accessed via one of the device's management interfaces. An appliance may support the following interfaces:

●	Console Port-This requires connecting a device running terminal emulator software (a laptop, for instance) to the device via a separate physical interface using a special console (or rollover) cable. The terminal emulator can then be used to start a command line interface (CLI).

●	AUX port-This port is designed to connect to an analog modem and provide remote access over a dial-up link. Once the AUX port is enabled and configured, the modem can be connected to it by using an RS-232 serial cable, a specially wired RJ-45 rollover cable and terminal adapter (RJ-45 to DB9), or a management cable (RJ-45 to DB9). Configure the modem with appropriate serial link settings (refer to the vendor guide), connect it to an appropriate telephone line, and allocate an extension number. A remote host can connect to the appliance CLI by using a terminal emulation program such as HyperTerminal or PuTTY.

●	Management port-This means configuring a virtual network interface and IP address on the device to use for management functions and connecting to it via one of the normal Ethernet ports. The port must be enabled for this function (some appliances come with a dedicated management port). Using Telnet (unsecure) or Secure Shell (SSH) to connect to a CLI remotely over the management interface in this way is referred to as a virtual terminal.

USB and RJ-45 type console ports plus AUX and other management interfaces on a router. (Image © 123RF.com.)

Management methods can be described as either in-band or out-of-band (OOB). An in-band management link is one that shares traffic with other communications on the "production" network. The console port is a physically out-of-band management method; the link is limited to the attached device. When you are using a browser-based management interface or a virtual terminal, the link can be made out-of-band by connecting the port used for management access to physically separate network infrastructure. Obviously, this is costly to implement, but out-of-band management is more secure and means that access to the device is preserved when there are problems affecting the production network.

With an in-band connection, better security can be implemented by using a VLAN to isolate management traffic. This makes it harder for potential eavesdroppers to view or modify traffic passing over the management interface. This sort of virtual OOB does still mean that access could be compromised by a system-wide network failure, however.

Use a secure connection protocol (HTTPS rather than HTTP, or SSH rather than Telnet) for the management interface. This applies to OOB too, but it is critical for in-band management.