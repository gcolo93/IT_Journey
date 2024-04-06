Lesson 13: Explaining Common Security Concepts

Topic 13A: Explain Common Security Concepts

SECURITY CONCEPTS

Establishing computer and network security means developing processes and controls that protect data assets and ensure business continuity by making network systems and hosts resilient to different kinds of attack.

The Confidentiality, Integrity, and Availability (CIA) Triad

One of the foundational principles of computer security is that the systems used to store, transmit, and process data must demonstrate three properties, often referred to as the CIA Triad:

●	Confidentiality means that certain information should only be known to certain people.

●	Integrity means that the data is stored and transferred as intended and that any modification is authorized.

●	Availability means that information is accessible to those authorized to view or modify it.

Vulnerability, Threat, and Risk

To perform assessment and monitoring, security teams must identify ways in which their systems could be attacked. These assessments involve vulnerabilities, threats, and risk:

●	Vulnerability-A weakness that could be accidentally triggered or intentionally exploited to cause a security breach.

●	Threat- The potential for someone or something to exploit a vulnerability and breach security. A threat may be intentional or unintentional. The person or thing that poses the threat is called a threat actor or threat agent. The path or tool used by a malicious threat actor can be referred to as the attack vector.

●	Risk-The likelihood and impact (or consequence) of a threat actor exercising a vulnerability.


Relationship between vulnerability, threat, and risk.

SECURITY RISK ASSESSMENTS

Many tools and techniques are available to ensure that network systems demonstrate three properties of the CIA triad. Selection and deployment of these tools is guided by security policies. Security policies ensure that an organization has evaluated the risks it faces and has put security controls in place to mitigate those risks. Making a system more secure is also referred to as hardening. Different security policies should cover every aspect of an organization's use of computer and network technologies, from procurement and change control to acceptable use.

Risk management is a process for identifying, assessing, and mitigating vulnerabilities and threats to the essential functions that a business must perform to serve its customers. Risk management is complex and treated very differently in companies and institutions of different sizes, and with different regulatory and compliance requirements. Most companies will institute enterprise risk management (ERM) policies and procedures, based on published frameworks.

Risk assessment is a subset of risk management where the company's systems and procedures are evaluated for risk factors. Separate assessments can be devised to perform an initial evaluation and ongoing monitoring of threats, vulnerabilities, and security posture.

Posture Assessment

There are many different ways of thinking about how IT services should be governed to fulfill overall business needs. Some organizations have developed IT service frameworks to provide best practice guides to implementing IT and cybersecurity. These frameworks can shape company policies and provide checklists of procedures, activities, and technologies that should ideally be in place.

Collectively, these procedures, activities, and tools can be referred to as security controls. A security control is something designed to give a system or data asset the properties of confidentiality, integrity, availability, and non-repudiation.

In theory, security controls or countermeasures could be introduced to address every risk factor. The difficulty is that security controls can be expensive, so you must balance the cost of the control with the cost associated with the risk. It is not possible to eliminate risk; rather, the aim is to mitigate risk factors to the point where the organization is exposed only to a level of risk that it can afford. The overall status of risk management is referred to as risk posture. Risk posture shows which risk response options can be identified and prioritized. Posture assessment is often performed with reference to an IT or security framework. The framework can be used to assess the organization’s maturity level in its use of security policies and controls.

Process Assessment

Mitigating risk can involve a large amount of expenditure so it is important to focus efforts. Effective risk management must focus on mission essential functions that could cause the whole business to fail if they are not performed. Part of this process involves identifying critical systems and assets that support these functions. A mission essential function (MEF) is one that cannot be deferred. This means that the organization must be able to perform the function as close to continually as possible, and if there is any service disruption, the mission essential functions must be restored first.

Business impact analysis (BIA) is the process of assessing what losses might occur for a range of threat scenarios. For instance, if a denial of service (DoS) attack suspends an e-commerce portal for five hours, the business impact analysis will be able to quantify the losses from orders not made and customers moving permanently to other suppliers based on historic data. The likelihood of a DoS attack can be assessed on an annualized basis to determine annualized impact, in terms of costs. You then have the information required to assess whether a security control, such as load balancing or managed attack mitigation, is worth the investment.

Where BIA identifies risks, business continuity planning (BCP) identifies controls and processes that enable an organization to maintain critical workflows in the face of some adverse event.

VULNERABILITY AND EXPLOIT TYPES

Vulnerabilities can exist because of misconfigurations or poor practice, but many people understand the term to mean faults in software specifically. A software vulnerability is a design flaw that can cause the application security system to be circumvented or that will cause the application to crash. The most serious vulnerabilities allow the attacker to execute arbitrary code on the system, which could allow the installation of malware or allow the threat actor to disable or weaken a secure configuration. Typically, applications such as web servers, web browsers, web browser plug-ins, email clients, and databases are targeted.

An exploit is the specific code or method of using a vulnerability to gain control of a system or damage it in some way. Typically, software vulnerabilities can be exploited only in quite specific circumstances, but because of the complexity of modern software and the speed with which new versions must be released to market, almost no software is free from vulnerabilities.

Zero-Day Vulnerabilities and Exploits

Most software vulnerabilities are discovered by software and security researchers, who notify the vendor to give them time to patch the vulnerability before releasing details to the wider public. A vulnerability that is exploited before the developer knows about it or can release a patch is called a zero-day. These can be extremely destructive, as it can take the vendor a lot of time to develop a patch, leaving systems vulnerable for days, weeks, or even years.

The term zero-day is usually applied to the vulnerability itself but can also refer to an attack or malware that exploits it.

Unpatched and Legacy Systems

While an exploit for a zero-day vulnerability can be extremely destructive, they are relatively rare events. A greater threat is the large number of unpatched or legacy systems in use. An unpatched system is one that its owner has not updated with OS and application patches; a legacy system is one where the software vendor no longer provides support or fixes for problems.

This issue does not just affect PCs. Network appliances can also be vulnerable to exploits. The risks to embedded systems have become more obvious over the last few years, and the risks posed by unpatched mobile devices and the Internet of Things is likely to grow.

Vulnerability Assessment

A vulnerability assessment is an evaluation of a system's security and ability to meet compliance requirements based on the configuration state of the system. Essentially, the vulnerability assessment determines if the current configuration matches the ideal configuration (the baseline). Vulnerability assessments might involve manual inspection of security controls but are more often accomplished through automated vulnerability scanners.

Common Vulnerabilities and Exposures

Common Vulnerabilities and Exposures (CVE) is a dictionary of vulnerabilities in published operating systems and applications software ( cve.mitre.org ). Automated vulnerability scanning software makes use of this dictionary to develop tests to discover vulnerabilities on live systems. There are several elements that make up a vulnerability's entry in the CVE:

●	An identifier in the format: CVE-YYYY-####, where YYYY is the year the vulnerability was discovered, and #### is at least four digits that indicate the order in which the vulnerability was discovered.

●	A brief description of the vulnerability.

●	A reference list of URLs that supply more information on the vulnerability.

●	The date the vulnerability entry was created.

Example of a CVE.

THREAT TYPES AND ASSESSMENT

Exploits for vulnerabilities are either developed by threat actors or exposed by unintentional weaknesses in procedures. Threat assessment is the process of identifying threat sources and profiling the types and capabilities of threat actors.

External versus Internal Threats

An external threat actor or agent is one that has no account or authorized access to the target system. A malicious external threat must infiltrate the security system using malware and/or social engineering. Note that an external actor may perpetrate an attack remotely or on-premises (by breaking into the company's headquarters, for instance). It is the threat actor that is defined as external, rather than the attack method.

Conversely, an internal (or insider) threat actor is one that has been granted permissions on the system. This typically means an employee, but insider threat can also arise from contractors and business partners.

Threat Research

Threat research is a counterintelligence gathering effort in which security companies and researchers attempt to discover the tactics, techniques, and procedures (TTPs) of threat actors.

The outputs from the primary research undertaken by security solutions providers and academics can take three main forms:

●	Behavioral threat research -narrative commentary describing examples of attacks and TTPs gathered through primary research sources.

●	Reputational threat intelligence-lists of IP addresses and domains associated with malicious behavior, plus signatures of known file-based malware.

●	Threat data-computer data that can correlate events observed on a customer's own networks and logs with known TTP and threat actor indicators.

SECURITY INFORMATION AND EVENT MANAGEMENT

Security Information and Event Management (SIEM) is a security control designed to integrate vulnerability and threat assessment efforts through automated collection, aggregation, and analysis of log data. The core function of a SIEM tool is to aggregate logs from multiple sources. In addition to logs from Windows and Linux-based hosts, this could include switches, routers, firewalls, intrusion detection sensors, vulnerability scanners, malware scanners, and databases.

The second critical function of SIEM (and the principal factor distinguishing it from basic log management) is that of correlation. This means that the SIEM software can link individual events or data points (observables) into a meaningful indicator of risk, or indicator of compromise (IOC). Correlation can then be used to drive an alerting system. Finally, SIEM can provide a long-term retention function and be used to demonstrate regulatory compliance.

OSSIM SIEM dashboard. Configurable dashboards provide the high-level status view of network security metrics. (Screenshot used with permission from AT-and-T Cybersecurity.)

PENETRATION TESTING

Where vulnerability testing uses mostly automated scanning tools and is a largely passive, or non-intrusive assessment activity, penetration testing aims to model how exposed the organization is to vulnerabilities that could be exploited by threat actors.

A penetration test-often shortened to pen test-uses authorized hacking techniques to discover exploitable weaknesses in the target's security systems. Pen testing is also referred to as ethical hacking.

The key difference from passive vulnerability scanning is that an attempt is made to actively test security controls and exploit any vulnerabilities discovered. Pen testing is an intrusive assessment technique. For example, a vulnerability scan may reveal that an SQL Server has not been patched to safeguard against a known exploit. A penetration test would attempt to use the exploit to perform code injection and compromise the server. This provides active testing of security controls. Even though the potential for the exploit exists, in practice the permissions on the server might prevent an attacker from using it. This would not be identified by a vulnerability scan but should be proven or not proven to be the case by penetration testing.

PRIVILEGED ACCESS MANAGEMENT

A privileged account is one that can make significant configuration changes to a host, such as installing software or disabling a firewall or other security system. Privileged accounts also have rights to log on network appliances and application servers.

Privileged access management (PAM) refers to policies, procedures, and technical controls to prevent the malicious abuse of privileged accounts by internal threat actors and to mitigate risks from weak configuration control over privileges. These controls identify and document privileged accounts, giving visibility into their use, and manage the credentials used to access them.

Some other general principles of PAM include least privilege, role-based access, and zero trust:

●	Least privilege means that a user is granted sufficient rights to perform his or her job and no more. This mitigates risk if the account should be compromised and fall under the control of a threat actor. Authorization creep refers to a situation where a user acquires more and more rights, either directly or by being added to security groups and roles. Least privilege should be ensured by closely analyzing business workflows to assess what privileges are required and by performing regular account audits.

●	Role-based access means that a set of organizational roles are defined, and subjects allocated to those roles. Under this system, the right to modify roles is reserved to a system owner. Therefore, the system is nondiscretionary, as each subject account has no right to modify the ACL of a resource, even though they may be able to change the resource in other ways. Users are said to gain rights implicitly (through being assigned to a role) rather than explicitly (being assigned the right directly).

●	Zero trust is based on the idea that perimeter security is unlikely to be completely robust. On a modern network, there are just too many opportunities for traffic to escape monitoring/filtering by perimeter devices. Zero trust uses systems such as continuous authentication and conditional access to mitigate privilege escalation and account compromise by threat actors. Another zero-trust technique is to apply microsegmentation. Microsegmentation is a security process that is capable of applying policies to a single node, as though it was in a zone of its own.

VENDOR ASSESSMENT

High-profile breaches have led to a greater appreciation of the importance of the supply chain in vulnerability management. A product, or even a service, may have components created and maintained by a long chain of different companies. Each company in the chain depends on its suppliers or vendors performing due diligence on their vendors. A weak link in the chain could cause impacts on service availability and performance, or in the worst cases lead to data breaches.

Vendor management is a process for selecting supplier companies and evaluating the risks inherent in relying on a third-party product or service. When it comes to data and cybersecurity, you must understand that risks cannot be wholly transferred to the vendor. If a data storage vendor suffers a data breach, you may be able to claim costs from them, but your company will still be held liable in terms of legal penalties and damage to reputation. If your webstore suffers frequent outages because of failures at a hosting provider, it is your company's reputation that will suffer and your company that will lose orders because customers look elsewhere.

A vendor may supply documentation and certification to prove that it has implemented a security policy robustly. You might be able to see evidence of security capabilities, such as a history of effective vulnerability management and product support. Larger companies will usually ask vendors to complete a detailed audit process to ensure that they meet the required standards.

Topic 13B: Explain Authentication Methods

AUTHENTICATION METHODS AND ACCESS CONTROLS

An access control system is the set of technical security controls that govern how subjects are permitted to interact with objects. Subjects in this sense are users, devices, or software processes, or anything else that can request and be granted access to a resource. Objects are the resources; these could be networks, servers, databases, files, and so on.

In computer security, the basis of access control is usually an access control list (ACL). This is a list of subjects and the rights or permissions they have been granted on the object.

An identity and access management (IAM) system to mediate use of objects by subjects is usually described in terms of four main processes:

●	Identification -Creating an account or ID that identifies the user, device, or process on the network.

●	Authentication-Proving that a subject is who or what it claims to be when it attempts to access the resource.

●	Authorization-Determining what rights subjects should have on each resource and enforcing those rights.

●	Accounting-Tracking authorized usage of a resource or use of rights by a subject and alerting when unauthorized use is detected or attempted.

MULTIFACTOR AND TWO-FACTOR AUTHENTICATION

An account defines a subject on the computer or network system. Assuming that an account has been created securely (the identity of the account holder has been verified), authentication verifies that only the account holder is able to use the account, and that the system may be used only by account holders. Authentication is performed when the account holder submits credentials to the system to request access. These are compared to the credentials stored on the system. If they match, the account is authenticated.

The type of data used to create a credential is called an authentication factor. Authentication factors fall into the following categories:

●	Knowledge factor-something you know (such as a password).

●	Ownership factor-something you have (such as a smart card).

●	Human or biometric factor-something you are (such as a fingerprint).

●	Behavioral factor-something you do (such as making a signature).

●	Location factor-somewhere you are (such as using a mobile device with location services).

An authentication technology or mechanism is considered strong if it combines the use of more than one authentication data type (multifactor). Single-factor authentication systems can quite easily be compromised: a password could be written down or shared, or compromised by a social engineering attack, a smart card could be lost or stolen, and a biometric system could be subject to high error rates.

Two-factor authentication combines something like a smart card or biometric mechanism with a knowledge factor, such as a password or personal identity number (PIN). Three-factor authentication combines three of the possible technologies. An example of this would be a smart card with an integrated fingerprint reader. This means that to authenticate, the user must possess the card, the user's fingerprint must match the template stored on the card, and the user must input a PIN.

Multifactor authentication requires a combination of different technologies. For example, requiring a PIN along with date of birth may be stronger than entering a PIN alone, but it is not multifactor.

LOCAL AUTHENTICATION AND SINGLE SIGN-ON

One of the most important features of an operating system is the authentication provider. The local authentication provider is the software architecture and code that underpins the mechanism by which the user is authenticated before starting a shell. This is usually described as a login (Linux) or a logon or sign-in (Microsoft). Knowledge-based authentication, using a password or PIN, is the default authentication provider for most operating systems.

Knowledge-based authentication relies on cryptographic hashes. A cryptographic hash is a function that converts any string to a unique, fixed-length code. The function should ensure that the code cannot be converted back into the plaintext string.

Password credentials are stored as cryptographic hashes (such as the Hash.Target value shown in the screenshot) that cannot normally be converted back to plaintext strings. The hashcat utility attempts to recover passwords by matching hashes through dictionary or brute force methods.

A password is not usually transmitted or stored in a credential database as a plaintext because of the risk of compromise. Instead, the password is stored as a cryptographic hash. When a user enters a password to log in, an authenticator converts what is typed into a hash and transmits that to an authority. The authority compares the submitted hash to the one in the database and authenticates the subject only if they match.



Windows Authentication

Windows authentication involves a complex architecture of components (docs.microsoft.com/en-us/windows-server/security/windows-authentication/credentials-processes-in-windows-authentication), but the following three scenarios are typical:

●	Windows local sign-in-the Local Security Authority (LSA) compares the submitted credential to a hash stored in the Security Accounts Manager (SAM) database, which is part of the registry. This is also referred to as interactive logon.

●	Windows network sign-in-the LSA can pass the credentials for authentication to a network service. The preferred system for network authentication is based on Kerberos, but legacy network applications might use NT LAN Manager (NTLM) authentication.

●	Remote sign-in-if the user's device is not connected to the local network, authentication can take place over some type of virtual private network (VPN) or web portal.

Linux Authentication

In Linux, local user account names are stored in /etc/passwd. When a user logs in to a local interactive shell, the password is checked against a hash stored in /etc/shadow. Interactive login over a network is typically accomplished using Secure Shell (SSH). With SSH, the user can be authenticated using cryptographic keys instead of a password.

A pluggable authentication module (PAM) is a package for enabling different authentication providers, such as smart card login (tecmint.com/configure-pam-in-centos-ubuntu-linux). The PAM framework can also be used to implement authentication to network servers.


Single Sign-On

A single sign-on (SSO) system allows the user to authenticate once to a local device and be authorized to access compatible application servers without having to enter credentials again. In Windows, SSO is provided by the Kerberos framework.

KERBEROS

Kerberos provides SSO authentication to Active Directory®, as well as compatibility with other, non-Windows operating systems. Kerberos was named after the three-headed guard dog of Hades (Cerberus) because it consists of three parts. Clients request services from a server, which both rely on an intermediary-a Key Distribution Center (KDC)-to vouch for their identity.

There are two services that make up a KDC: the Authentication Service and the Ticket Granting Service.

The Authentication Service is responsible for authenticating user logon requests. More generally, users and services can be authenticated; these are collectively referred to as principals. For example, when you sit at a Windows domain workstation and log on to the domain (Kerberos documentation refers to realms rather than domains, which is Microsoft's terminology), the first step of logon is to authenticate with a KDC server (implemented as a domain controller).

Kerberos Authentication Service. (Images © 123RF.com.)

When authenticated, the KDC server presents the user with a Ticket Granting Ticket. To access resources within the domain, the client requests a Service Ticket (a token that grants access to a target application server) by supplying the Ticket Granting Ticket to the Ticket Granting Service (TGS).

Kerberos Ticket Granting Service. (Images © 123RF.com.)

DIGITAL CERTIFICATES AND PKI

A protocol such as Kerberos can also be used with smart cards. A smart card is programmed with an encryption key pair and a digital certificate, issued by the authenticating domain. Digital certificates are also used to authenticate server machines when using Transport Layer Security (TLS). A certificate can be installed on a web server or email server to validate its identity and establish a secure transmission channel.

Digital certificates depend on the concept of public key cryptography. Public key cryptography, also referred to as asymmetric encryption, solves the problem of distributing encryption keys when you want to communicate securely with others, authenticate a message that you send to others, or authenticate yourself to an access control system. With asymmetric encryption, you generate a key pair. The private key in the pair remains a secret that only you know. The public key can be transmitted to other subjects. The private key cannot be derived from the public key. The key pair can be used in the following ways:

●	When you want others to send you confidential messages, you give them your public key to use to encrypt the message. The message can then only be decrypted by your private key, which you keep known only to yourself. Due to the way asymmetric encryption works, the public key cannot be used to decrypt a message, even though it was used to encrypt it in the first place.

As encryption using a public key is relatively slow; rather than encrypting the whole message using a public key, more typically, the public key is used to encrypt a symmetric encryption key for use in a single session and exchange it securely. The symmetric session key is then used to encrypt the actual message. A symmetric key can perform both encryption and decryption.

●	When you want to authenticate yourself to others, you create a signature and sign it by encrypting the signature with your private key. You give others your public key to use to decrypt the signature. As only you know the private key, everyone can be assured that only you could have created the signature.

The basic problem with public key cryptography lies in proving the identity of the owner of a public key. The system is vulnerable to an on-path attack where a threat actor substitutes your public key for their own. Public key infrastructure (PKI) aims to prove that the owners of public keys are who they say they are. Under PKI, anyone issuing public keys should obtain a digital certificate. The validity of the certificate is guaranteed by a certificate authority (CA). A digital certificate is essentially a wrapper for a subject's (or end entity's) public key. As well as the public key, it contains information about the subject and the certificate's issuer or guarantor. The certificate is digitally signed to prove that it was issued to the subject by a particular CA.

EXTENSIBLE AUTHENTICATION PROTOCOL AND IEEE 802.1X

Smart-card authentication is used for Kerberos authentication where the computer is attached to the local network and the user is logging on to Windows. This type of multifactor authentication may also be required in other contexts:

When the user is accessing a wireless network and needs to authenticate with the network database.

When a device is connecting to a network via a switch, network policies require the user to be authenticated before the device is allowed to communicate.

When the user is connecting to the network over a public network via a virtual private network (VPN).

In these scenarios, the Extensible Authentication Protocol (EAP) provides a framework for deploying multiple types of authentication protocols and technologies. EAP allows lots of different authentication methods, but many of them use a digital certificate on the server and/or client machines. These certificates allow the machines to establish a trust relationship and create a secure tunnel to transmit the user credential or to perform smart card authentication without a user password.

Where EAP implements a particular authentication factor and mechanism, the IEEE 802.1X Port-based Network Access Control (NAC) protocol provides the means of using an EAP method when a device connects to an Ethernet switch port, wireless access point, or VPN gateway. 802.1X uses authentication, authorization, and accounting (AAA) architecture. AAA uses the following components:

Supplicant-the device requesting access, such as a user's PC or laptop.

Network access server (NAS) or network access point (NAP)-edge network appliances, such as switches, access points, and VPN gateways. These are also referred to as AAA clients or authenticators.

AAA server-the authentication server, positioned within the local network. There are two main types of AAA server: RADIUS and TACACS+.

With AAA, the NAS devices do not have to store any authentication credentials. They forward this data between the AAA server and the supplicant.






RADIUS authentication with EAP overview. (Images © 123RF.com.)

Digital certificate details. (Screenshot used with permission from Microsoft.)

RADIUS AND TACACS+

Remote Authentication Dial-in User Service (RADIUS) is very widely used for client device access over switches, wireless networks, and VPNs. There are several RADIUS server and client products. Microsoft has the Network Policy Server (NPS) for Windows platforms, and there are open-source implementations for UNIX and Linux, such as FreeRADIUS, as well as third-party commercial products, such as Cisco's Secure Access Control Server, OSC Radiator, and Juniper Networks Steel-Belted RADIUS.

RADIUS typically uses UDP ports 1812 and 1813. Each RADIUS client must be configured with the IP address of the RADIUS server plus the same shared secret.

Configuring an OPNsense security appliance as a RADIUS client. The OPNsense appliance is working as a virtual private network (VPN) access server. It uses the RADIUS server at 10.1.16.1 to authenticate VPN users. The client must be configured with the same shared secret as the server. (Screenshot used with permission from OPNsense.)

Terminal Access Controller Access Control System (TACACS+) is a similar protocol to RADIUS but designed to be more flexible and reliable. TACACS+ was developed by Cisco but is also supported on many of the other third-party and open-source RADIUS server implementations. Where RADIUS is often used for network access control over end user devices, TACACS+ is often used in authenticating administrative access to routers and switches. It uses TCP over port 49 and the reliable delivery offered by TCP makes it easier to detect when a server is down.

Also, authentication, authorization, and accounting functions are discrete. Many device management tasks require reauthentication (similar to having to reenter a password for sudo or UAC) and per-command authorizations and privileges for users, groups, and roles. TACACS+ supports this workflow better than RADIUS.

LIGHTWEIGHT DIRECTORY ACCESS PROTOCOL

Directory services are the principal means of providing privilege management and authorization on an enterprise network.

When an authenticated user logs on to the network, the server security service generates an access key for the user. This contains the username and group memberships of the authenticated user. Whenever the user attempts to access a resource, his or her access key is provided as identification. The server's security service matches username and group memberships from the access key with entries in the access list, and from this, it calculates the user's access privileges.

All this information is stored in a directory. A directory is like a database, where an object is like a record, and things that you know about the object (attributes) are like fields. For products from different vendors to be interoperable, most directories are based on the same standard. The main directory standard is the X.500 series of standards. As X.500 is complex, most directory services are implementations of the Lightweight Directory Access Protocol (LDAP). LDAP is not a directory standard, but a protocol used to query and update an X.500-like directory. LDAP is widely supported in current directory products (Windows Active Directory®, NetIQ eDirectory, or the open source OpenLDAP). LDAP messaging uses TCP and UDP port 389 by default.

In an X.500, each object has a unique identifier called a distinguished name. A distinguished name is made up of attribute=value pairs, separated by commas. The most specific attribute is listed first, and successive attributes become progressively broader. This most specific attribute is also referred to as the relative distinguished name, as it uniquely identifies the object within the context of successive (parent) attribute values.

Browsing objects in an Active Directory LDAP schema. (Screenshot used with permission from Microsoft.)

The types of attributes, what information they contain, and the way object types are defined through attributes (some of which may be required and some optional) is described by the directory schema. For example, the distinguished name of a web server operated by Widget in London might be:

CN=WIDGETWEB, OU=Marketing, O=Widget, L=London, ST=London, C=UK, DC=widget, DC=example

LDAP SECURE

Like many TCP/IP protocols, LDAP provides no security, and all transmissions are in plaintext, making it vulnerable to sniffing and spoofing attacks. Also, a server that does not require clients to authenticate is vulnerable to overloading by denial of service attacks. Authentication, referred to as binding to the server, can be implemented in the following ways:

●	No authentication-Anonymous access is granted to the directory.

●	Simple bind-the client must supply its distinguished name (DN) and password, but these are passed as plaintext.

●	Simple Authentication and Security Layer (SASL)-the client and server negotiate the use of a supported authentication mechanism, such as Kerberos. The STARTTLS command can be used to require encryption (sealing) and message integrity (signing). This is the preferred mechanism for Microsoft's Active Directory (AD) implementation of LDAP.

●	LDAP Secure (LDAPS)-the server is installed with a digital certificate, which it uses to set up a secure tunnel for the user credential exchange. LDAPS uses port 636.

If secure access is required, anonymous and simple authentication access methods should be disabled on the server.

Generally, two levels of access will need to be granted on the directory: read-only access (query) and read/write access (update). This is implemented using an access control policy, but the precise mechanism is vendor-specific and not specified by the LDAP standards documentation.

Unless it is hosting a public service, the LDAP directory server should also only be accessible from the private network. This means that LDAP ports (389 over TCP and UDP) should be blocked by a firewall from access over the public interface.