Lesson 11: Explaining Network Applications

Topic 11A: Explain the Use of Web, File/Print, and Database Services

HYPERTEXT TRANSFER PROTOCOL

Websites and web applications are perhaps the most useful and ubiquitous of network services. Web technology can be deployed for a huge range of functions and applications, in no way limited to the static pages of information that characterized the first websites. The foundation of web technology is the HyperText Transfer Protocol (HTTP). HTTP enables clients (typically web browsers) to request resources from an HTTP server. A client connects to the HTTP server using an appropriate TCP port (TCP/80, by default) and submits a request for a resource, using a uniform resource locator (URL). The server acknowledges the request and either responds with the data or with an error message.

HTTP Headers and Payload

The response and request formats are defined in the HTTP header. The HTTP payload is usually used to serve HyperText Markup Language (HTML) web pages, which are plain text files with coded tags describing how the page should be formatted. A web browser can interpret the tags and display the text and other resources associated with the page, such as binary picture or sound files linked to the HTML page.

Using Firefox's web developer tools to inspect the HTTP requests and response headers involved in serving a typical modern web page. (Screenshot courtesy of Mozilla Foundation.)

HTTP also features a forms mechanism (POST) that enables a user to submit data from the client to the server. HTTP is nominally a stateless protocol; this means that the server is not required to preserve information about the client during a session. However, the basic functionality of HTTP servers is also often extended by support for scripting and programmable features (web applications). Servers can also set text file cookies to preserve session information. These coding features, plus integration with databases, increase flexibility and interactivity, but also increase the attack surface and expose more vulnerabilities.

Many argue that HTTP is a stateful protocol. Version 2 of HTTP adds more state-preserving features (blog.zamicol.com/2017/05/is-http2-stateful-protocol-application.html).

Web Servers

Most organizations have an online presence, represented by a website. In order to run a website, it must be hosted on an HTTP server connected to the Internet. Larger organizations or SMEs with the relevant expertise may host websites themselves, but more typically, an organization will lease a server or space on a server from an ISP. The following types of hosting packages are common:

●	Dedicated server -The ISP allocates your own private server computer. This type of service is usually unmanaged (or management comes at additional cost).

●	Virtual Private Server (VPS)-The ISP allocates you a virtual machine (VM) on a physical server. This is isolated from other customer instances by the hypervisor.

●	Cloud hosting-Your website is run on a cloud over several hardware computers, allowing more scalability if demand patterns change.

●	Shared hosting-Your website is hosted within a private directory on a shared server. Performance can be severely affected by other sites hosted on the server, because all the sites are competing for the same resources.

The main web server platforms are Apache®, Microsoft Internet Information Server (IIS), and nginx.

SECURE SOCKETS LAYER/TRANSPORT LAYER SECURITY

One of the critical problems for the provision of early websites was the lack of security in HTTP. Under HTTP, all data is sent unencrypted, and there is no authentication of client or server. Secure Sockets Layer (SSL) was developed by Netscape in the 1990s to address these problems. SSL proved very popular with the industry. Transport Layer Security (TLS) was developed from SSL and ratified as a standard by the IETF.

SSL/TLS works as a layer between the Application and Transport layers of the TCP/IP stack, or, in OSI terms, at the Session layer. It's normally used to encrypt TCP connections. When it is used with the HTTP application, it is referred to as HTTP Secure (HTTPS). TLS can also be used to secure other TCP application protocols, such as FTP, POP3/IMAP, SMTP, and LDAP.

TLS can also be used with UDP, referred to as Datagram Transport Layer Security (DTLS), most often in virtual private networking (VPN) solutions.

To implement HTTPS, the web server is installed with a digital certificate issued by some trusted certificate authority (CA). The certificate uses encrypted data to prove the identity of the server, assuming that the client also trusts the CA. The certificate is a wrapper for a public/private encryption key pair. The private key is kept a secret known only to the server; the public key is given to clients via the digital certificate.

The server and client use the key pair in the digital certificate and a chosen cipher suite within the SSL/TLS protocol to set up an encrypted tunnel. Even though someone else might know the public key, they cannot decrypt the contents of the tunnel without obtaining the server's private key. This means that the communications cannot be read or changed by a third party.

Encrypted traffic between the client and server is sent over TCP port 443 (by default), rather than the open and unencrypted port 80. A web browser will open a secure session to a server providing this service by using a URL starting with https:// and it will also show a padlock icon in the address bar to indicate that the connection is secure. A website can be configured to require a secure session and reject or redirect plain HTTP requests.

HTTPS padlock icon. (Screenshot courtesy of Microsoft.)

FILE TRANSFER PROTOCOL

It is often necessary to transfer files to and from appliances or servers from a remote host. Many methods of remote file access use some form of the File Transfer Protocol (FTP). While HTTPS-based web services and web applications can now offer file downloads to end users, FTP is still often used to perform administrative upload/download of files to and from servers and appliances. For these uses, it is important to secure the FTP session.

Active versus Passive FTP

An FTP client connects to TCP port 21 on an FTP server and opens a chosen dynamic client port number (n). The TCP port 21 control port is used to transfer commands and status information, but not for data transfer. Data transfer can operate in one of two modes: active or passive. In active mode, the client sends a PORT command specifying its chosen data connection port number (typically n+1), and the server opens the data connection between the chosen client port and TCP port 20 on the server.

FTP in active mode. (Images © 123RF.com.)

In passive mode, the client opens a data port (again, typically n+1) and sends the PASV command to the server's control port. The server then opens a random high port number and sends it to the client using the PORT command. The client then initiates the connection between the two ports.

FTP in passive mode. (Images © 123RF.com.)

Active FTP poses a configuration problem for some firewalls, as the server is initiating the inbound connection, but there is no way of predicting which port number will be utilized. However, not all FTP servers and clients can operate in passive mode. If this is the case, check that firewalls installed between the client and server can support active FTP (stateful inspection firewalls).

Another problem is that the control connection can remain idle when the data connection is in use, meaning that the connection can be "timed out" by the firewall (or other routing device).

Trivial File Transfer Protocol

The Trivial File Transfer Protocol (TFTP) is a connectionless protocol running over UDP port 69. Consequently, TFTP does not provide the guaranteed delivery offered by FTP and is only suitable for transferring small files. Also, it only supports reading ( GET ) and writing ( PUT ) files, not directory browsing, file deletion, or any of the other features of FTP. A TFTP server is most commonly used by legacy network appliances (switches, routers, diskless workstations, and printers) to download configuration files. It can also be used as a backup and restore method for configuration files. However, TFTP has no security mechanisms and appliances are no longer as resource constrained as they were in the early days of networking. Consequently, secure protocols are now preferred for these functions.

SECURE FILE TRANSFER PROTOCOL

Secure FTP (SFTP) addresses the privacy and integrity issues of FTP by encrypting the authentication and data transfer between client and server. In SFTP, a secure link is created between the client and server using Secure Shell (SSH) over TCP port 22. Ordinary FTP commands and data transfer can then be sent over the secure link without risk of eavesdropping. This solution requires an SSH server that supports SFTP plus SFTP client software.

WinSCP SFTP client. (Screenshot courtesy of WinSCP.)

Another means of securing FTP is to use the connection security protocol SSL/TLS. There are two means of configuring FTP over TLS:

●	Explicit TLS (FTPES)-Use the AUTH TLS command to upgrade an unsecure connection established over port 21 to a secure one. This protects authentication credentials. The data connection for the actual file transfers can also be encrypted (using the PROT command).

●	Implicit TLS (FTPS)-Negotiate an SSL/TLS tunnel before the exchange of any FTP commands. This mode uses the secure port 990 for the control connection.

FTPS is tricky to configure when there are firewalls between the client and server. Consequently, FTPES is usually the preferred method.

FILE AND PRINT SERVICES

File and print services allow network clients to share access to disk and printer resources.

Server Message Block

On a Windows® network, the File/Print Sharing Service is provided by the Server Message Block (SMB) protocol. SMB allows a host to share its directories/files and printers to make them available for other machines to use. Support for SMB in UNIX- or Linux-based machines and network attached storage (NAS) appliances is provided by using the Samba software suite (samba.org/samba/what\_is\_samba.html), which allows a Windows client to access a Linux host as though it were a Windows file or print server.

On legacy networks, SMB ran as part of an older network services protocol called NetBIOS on TCP port 139. If no legacy client support is required, however, SMB is more typically run directly over TCP port 445. SMB should be restricted to use only on local networks. It is important that any traffic on the NetBIOS port ranges (137-139) and port 445 be blocked by a perimeter firewall.

SMB version 3 supports message encryption, which can be enabled on a file server or on a per-share basis. An encrypted share can only be accessed by an SMB 3.0 or higher client.

SMB has gone through several updates, with SMB3 as the current version. SMB1 has very serious security vulnerabilities and is now disabled by default on current Windows versions (docs.microsoft.com/en-us/windows-server/storage/file-server/troubleshoot/detect-enable-and-disable-smbv1-v2-v3).

Remote Print Protocols

A printer can be connected to the network using a cabled or wireless link and configured with an IP address and FQDN. Hosts need to be able to connect to the printer, configure options and print settings, send print jobs, and receive status messaging, such as out of paper errors. These functions are implemented using a remote print protocol to communicate between the print monitor process running on the host and the print device:

●	Port 9100-This can be referred to as the standard TCP/IP port, AppSocket, or JetDirect. This port just establishes a TCP connection to transfer raw Page Description Language (PDL) print job data and Printer Job Language (PJL) configuration and management data. The two most common PDLs are PostScript (PS) and Printer Command Language (PCL). Most printers support bidirectional status messaging to inform the host's print monitor about error conditions, such as out of paper or paper jam.

●	Internet Printing Protocol (IPP)-This is an adapted form of HTTP that uses TCP port 631 and can be implemented as a secure protocol (IPPS). It provides better support for status messaging than port 9100.

●	Web Services for Devices (WSD)/AirPrint-These technologies allow a print device to advertise service capabilities over the network and for Windows and MacOS/iOS hosts respectively to add the device using plug-and-play and manage it using bidirectional status messaging. They also allow for secure connections to the print device.

●	Printer sharing-This means that a host connects to the printer (using a local or network connection) and then shares the printer object with other hosts using SMB. Print jobs and status messaging are sent via the host that shared the printer.

DATABASE SERVICES

A database provisions information in a format that can be read and updated through some type of query language. There are two main types of databases. Relational databases store information in tables with rows (records) and columns (fields). Relationships between data fields in different tables is created using key fields that uniquely identify each record. Relational databases are operated using structured query language (SQL). SQL defines commands such as SELECT to retrieve information or UPDATE to change it.

SQL has been implemented in relational database management system (RDBMS) platforms by several different vendors. As well as providing an implementation of SQL, an RDBMS provides management tools and often a GUI to use to operate the database. A remote access protocol allows a client to connect to the database server over the network and allows replication traffic to move between database servers. Replication is a means of synchronizing the data held on each server. Each RDBMS uses a different TCP port to distinguish it as an application service:

●	Oracle's remote data access protocol SQL\*Net uses TCP/1521.

●	Microsoft SQL Server uses TCP/1433.

●	The open-source MySQL platform uses TCP/3306. The MariaDB platform forked from MySQL uses the same port.

●	The open-source PostgreSQL platform uses TCP/5432.

These are the principal ports. An RDBMS is likely to use other TCP or UDP ports for additional functions.

By default, these ports are unsecure. However, the RDBMS server can be installed with a certificate and configured to enable TLS transport encryption. The connection is still made over the same port. Either the server or the client can be configured to require encryption and drop the connection if a valid security profile is not available. Optionally, the client can also be installed with a certificate and the server configured to refuse connections from clients without a valid certificate.

The other type of database is referred to as NoSQL or "not only SQL." Rather than highly structured relational tables, NoSQL data can use a variety of formats, such as key-value pairs or wide columns (where rows do not have to have the same set of fields). NoSQL databases are typically accessed using an application programming interface (API) over HTTPS.

All the RDBMS platforms also provide support for NoSQL datastores. There are also dedicated NoSQL platforms, such as MongoDB, Amazon's DynamoDB, and CouchDB.

Topic 11B: Explain the Use of Email and Voice Services

SIMPLE MAIL TRANSFER PROTOCOL

Electronic mail enables a person to compose a message and send it to another user on their own network (intranet) or anywhere in the world via the Internet. Email uses separate mail transfer and mailbox access protocols:

Operation of delivery and mailbox email protocols. (Images © 123RF.com.)

The Simple Mail Transfer Protocol (SMTP) specifies how email is delivered from one system to another. The SMTP server of the sender discovers the IP address of the recipient SMTP server by using the domain name part of the recipient's email address. The SMTP servers for the domain are registered in DNS using Mail Exchange (MX) and host (A/AAAA) records.

SMTP does not queue messages indefinitely. If there is a communication problem, the SMTP server retries at regular intervals before timing out and returning a non-delivery report (NDR) to the sender. The NDR will contain an error code indicating the reason the item could not be delivered. SMTP provides no mechanism for persistent storage of messages.

SMTP communications can be secured using the TLS version of the protocol (SMTPS). This works much like HTTPS with a certificate on the SMTP server and a negotiation between client and server about which cipher suites to use. There are two ways for SMTP to use TLS:

●	STARTTLS-This is a command that upgrades an existing unsecure connection to use TLS. This is also referred to as explicit TLS or opportunistic TLS.

●	SMTPS-This establishes the secure connection before any SMTP commands (HELO, for instance) are exchanged. This is also referred to as implicit TLS.

The STARTTLS method is generally more widely implemented than SMTPS. Typical SMTP configurations use the following ports and secure services:

●	Port 25-Used for message relay between SMTP servers, or message transfer agents (MTAs). If security is required and supported by both servers, the STARTTLS command can be used to set up the secure connection.

●	Port 587-Used by mail clients or message submission agents (MSAs) to submit messages for delivery by an SMTP server. Servers configured to support port 587 should use STARTTLS and require authentication before message submission.

Mail clients can use port 25 to submit messages to the server for delivery, but this is not best practice. Use of port 25 is typically reserved for relay between servers.

MAILBOX ACCESS PROTOCOLS

SMTP is useful only to deliver mail to hosts that are permanently available. When a message is received by an SMTP server, it delivers the message to a mailbox server. This could be a separate machine or a separate process running on the same server. A mailbox access protocol allows the user's client email software to operate the mailbox.

Post Office Protocol

The Post Office Protocol (POP) is an early example of a mailbox access protocol. POP is often referred to as POP3 because the active version of the protocol is version 3. A POP client application, such as Microsoft Outlook® or Mozilla Thunderbird®, establishes a connection to the POP server on TCP port 110. The user is authenticated (by username and password), and the contents of his or her mailbox are downloaded for processing on the local PC. Generally speaking, the messages are deleted from the mailbox server when they are downloaded, though some clients have the option to leave messages on the server.

Configuring mailbox access protocols on a server. (Screenshot courtesy of Mozilla Foundation.)

Like other TCP application protocols, POP transfers all information as cleartext. This means anyone able to monitor the session would be able to obtain the user's credentials and snoop on messages. POP can be secured by using TLS encryption. The default TCP port for secure POP (POP3S) is port 995.

Internet Message Access Protocol

POP has some significant limitations, some of which are addressed by the Internet Message Access Protocol (IMAP). Like POP, IMAP is a mail retrieval protocol, but with mailbox management features lacking in POP. POP is primarily designed for dial-up access; the client contacts the server to download its messages, and then disconnects. IMAP supports permanent connections to a server and connecting multiple clients to the same mailbox simultaneously. It also allows a client to manage the mailbox on the server (to organize messages in folders and to control when they are deleted, for instance) and to create multiple mailboxes.

A client connects to an IMAP server over TCP port 143, but this port is unsecure. Connection security can be established using a TLS. The default port for IMAPS is TCP/993.

In a Windows environment, the proprietary Messaging Application Programming Interface (MAPI) protocol is typically used to access Microsoft Exchange mailboxes. MAPI uses HTTPS as a secure transport protocol.

VOICE AND VIDEO SERVICES

Voice over IP (VoIP), web conferencing, and video teleconferencing (VTC) solutions have become standard methods for the provision of business and social communications. Many networks are upgrading from legacy voice services to IP-based protocols and products.

Private Branch Exchange

Legacy voice services use the public switched telephone network (PSTN). A residential telephone installation would be serviced by a simple box providing a one- or two-line analog interface to the local exchange. This analog interface is also referred to as the plain old telephone service (POTS). Each line provides a single channel for an incoming or outgoing call. A typical business requires tens or hundreds of lines for voice communications, let alone capacity for data communications. Historically, this requirement would have been facilitated by a digital trunk line, also referred to as a Time Division Multiplexing (TDM) circuit. A TDM can multiplex separate voice and data channels for transmission over a single cable.

A private branch exchange (PBX) is an automated switchboard providing a single connection point for an organization's voice lines. A TDM-based PBX connects to the telecommunications carrier over a digital trunk line, which will support multiple channels (inward and outward calls). The PBX allows for the configuration of the internal phone system to direct and route calls to local extensions, and provides other telephony features such as call waiting, music on hold, and voice mail.

VoIP-Enabled PBX

TDM-based PBXes are being replaced by hybrid and fully IP/VoIP PBXes. For internal calls and conferences, a VoIP PBX establishes connections between local VoIP endpoints with data transmitted over the local Ethernet network. A VoIP PBX can also route incoming and outgoing calls from and to external networks. This might involve calls between internal and external VoIP endpoints, or with voice telephone network callers and receivers. A VoIP PBX will also support features such as music on hold and voice mail.

A TDM PBX is supplied as vendor-specific hardware. A VoIP PBX can be implemented as software running on a Windows or Linux server. Examples of software-based solutions include 3CX (3cx.com) and Asterisk ( asterisk.org ). There are also hardware solutions, where the VoIP PBX runs on a router, such as Cisco Unified Communications Manager ( cisco.com/c/en/us/products/unified-communications/unified-communications-manager-callmanager/index.html ).

A VoIP PBX would normally be placed at the network edge and be protected by a firewall. Internal clients connect to the PBX over Ethernet data cabling and switching infrastructure, using Internet Protocol (IP) at the Network layer for addressing. The VoIP PBX uses the organization's Internet link to connect to a VoIP service provider, which facilitates inward and outward dialing to voice-based telephone networks.

A VoIP PBX facilitates internal IP calls and calls to and from external VoIP networks and the landline and cellular telephone networks. (Images © 123RF.com)

VOIP PROTOCOLS

Voice and video services can be challenging to support because they require response times measured in milliseconds (ms). Delayed responses will result in poor call or video quality. This type of data can be one-way, as is the case with media streaming, or two-way, as is the case with VoIP and VTC.

The protocols designed to support real-time services cover one or more of the following functions:

●	Session control-Used to establish, manage, and disestablish communications sessions. They handle tasks such as user discovery (locating a user on the network), availability advertising (whether a user is prepared to receive calls), negotiating session parameters (such as use of audio/video), and session management and termination.

●	Data transport-Handles the delivery of the actual video or voice information.

●	Quality of Service (QoS)-Provides information about the connection to a QoS system, which in turn ensures that voice or video communications are free from problems, such as dropped packets, delay, or jitter.

Session Initiation Protocol

The Session Initiation Protocol (SIP) is one of the most widely used session control protocols. SIP endpoints are the end-user devices (also known as user agents), such as IP-enabled handsets or client and server web conference software. Each device, conference, or telephony user is assigned a unique SIP address known as a SIP Uniform Resource Indicator (URI). Examples of SIP URIs include:

sip:jaime@515support.com

sip:2622136227@515support.com

sip:jaime@2622136227

meet:sip:organizer@515support.com;ms-app=conf;ms-conf-id=subg42

There is also a tel: URI scheme allowing SIP endpoints to dial a landline or cell phone. A tel: URI can either use the global (E.164) format (such as tel:+1-866-8358020) or a local format (for internal extensions).

SIP typically runs over UDP or TCP ports 5060 (unsecured) and 5061 (SIP-TLS). SIP has its own reliability and retransmission mechanisms and can thus be seen to benefit most from the lower overhead and reduced latency and jitter of UDP. Some enterprise SIP products use TCP anyway.

Real-Time Transport Protocol and RTP Control Protocol

While SIP provides session management, the actual delivery of real-time data uses different protocols. The principal one is Real-time Transport Protocol (RTP). RTP enables the delivery of a stream of media data via UDP, while implementing some of the reliability features usually associated with TCP communications. RTP works closely with the RTP Control Protocol (RTCP). Each RTP stream uses a corresponding RTCP session to monitor the quality of the connection and to provide reports to the endpoints. These reports can then be used by the applications to modify codec parameters or by the network stacks to tune Quality of Service (QoS) parameters.

VOIP PHONES

A VoIP/SIP endpoint can be implemented as software running on a computer or smartphone or as a dedicated hardware handset. VoIP phones use VLAN tagging to ensure that the SIP control and RTP media protocols can be segregated from normal data traffic. In a typical voice VLAN configuration, the LAN port on the handset is connected to the wall port, while the PC is connected to the PC port on the handset. The two devices share the same physical link, but data traffic is distinguished from voice traffic by configuring separate VLAN IDs.

Handsets can use Power over Ethernet (PoE), if available, to avoid the need for separate power cabling or batteries. There are also wireless handsets that work over 802.11 Wi-Fi networks.

Connection security for VoIP works in a similar manner to HTTPS. To initiate the call, the secure version of SIP (SIPS) uses digital certificates to authenticate the endpoints and establish an SSL/TLS tunnel. The secure connection established by SIPS can also be used to generate a master key to use with the secure versions of the transport and control protocols.

When you are installing a new handset, you should also test that the connection works and that the link provides sufficient call quality. Most service providers have test numbers to verify basic connectivity and perform an echo test call, which replays a message you record so that you can confirm voice quality.

VOICE GATEWAYS

SIP endpoints can establish communications directly in a peer-to-peer architecture, but it is more typical to use intermediary servers, directory servers, and VoIP gateways. There can also be requirements for on-premises integration between data and voice networks and equipment. A voice gateway is a means of translating between a VoIP system and legacy voice equipment and networks, such as POTS lines and handsets. There are many types of VoIP gateways, serving different functions. For example, a company may use VoIP internally, but connect to the telephone network via a gateway. To facilitate this, you could use a hybrid or hardware-based VoIP PBX with a plug-in or integrated VoIP gateway, or you could use a separate gateway appliance. There are analog and digital types to match the type of incoming landline. An analog version of this type of gateway is also called a Foreign Exchange Office (FXO) gateway.

VoIP gateway connecting a local network using VoIP calling to the ordinary telephone network. (Images © 123RF.com)

A VoIP gateway can also be deployed to allow a legacy analog or digital internal phone system to use a VoIP service provider to place calls. In this type of setup, low rate local and national calls might be placed directly, while international calls that would attract high charges if placed directly are routed via the VoIP service provider.

VoIP gateway connecting a local network using legacy PBX and handsets to a VoIP service provider. (Images © 123RF.com)

Finally, a VoIP gateway or adapter can be used to connect POTS handsets and fax machines to a VoIP PBX. This type of device is also called a Foreign Exchange Subscriber (FXS) gateway.

VoIP gateway connecting legacy handsets to a VoIP PBX. (Images © 123RF.com)