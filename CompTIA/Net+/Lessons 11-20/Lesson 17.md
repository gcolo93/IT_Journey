Lesson 17: Explaining Organizational and Physical Security Concepts

Topic 17A: Explain Organizational Documentation and Policies

OPERATING PLANS AND PROCEDURES

Running an efficient network is not just about installing cabling and network devices. The administration of the network in terms of documentation and management is a critical task.

Configuration Management

Configuration management means identifying and documenting all the infrastructure and devices installed at a site. ITIL® is a popular documentation of good and best practice activities and processes for delivering IT services. Under ITIL, configuration management is implemented using the following elements:

●	Service assets are things, processes, or people that contribute to the delivery of an IT service. Each asset must be identified by some sort of label.

●	A Configuration Item (CI) is an asset that requires specific management procedures for it to be used to deliver the service. CIs are defined by their attributes.

●	A baseline documents the approved or authorized state of a CI. This allows auditing processes to detect unexpected or unauthorized change. A baseline can be a configuration baseline (the ACL applied to a firewall, for instance) or a performance baseline (such as the throughput achieved by the firewall).

●	A Configuration Management System (CMS) is the tools and databases that collect, store, manage, update, and present information about CIs. A small network might capture this information in spreadsheets and diagrams; there are dedicated applications for enterprise CMS.

Change Management

A documented change management process minimizes the risk of unscheduled downtime by implementing changes in a planned and controlled way. The need to change is often described either as reactive, where the change is forced on the organization, or as proactive, where the need for change is initiated internally. Changes can also be categorized according to their potential impact and level of risk (major, significant, minor, or normal, for instance).

In a formal change management process, the need or reasons for change and the procedure for implementing the change is captured in a Request for Change (RFC) document and submitted for approval. The RFC will then be considered at the appropriate level and affected stakeholders will be notified. Major or significant changes might be managed as a separate project and require approval through a Change Advisory Board (CAB).

Standard Operating Procedures

Configuration changes should be made only when there is a valid job ticket authorizing the change. This means that the activity of all network personnel, whether it be installing new devices or troubleshooting, is recorded in job logs. In a fully documented environment, each task will be governed by a standard operating procedure (SOP). A SOP sets out the principal goals and considerations, such as budget, security, or customer contact standards, for performing a task and identifies lines of responsibility and authorization for performing it. A SOP may also contain detailed steps for completing a task in an approved way, or these steps may be presented as work instructions.

SYSTEM LIFE CYCLE PLANS AND PROCEDURES

It is crucial for an organization to have an inventory of its tangible and intangible assets. In terms of network management, assets are network appliances (routers, switches, threat management devices, access points), servers, workstations, and passive network infrastructure (cabling and cross-connects).

Audit Reports

An audit report focuses on identifying and recording assets. There are many software suites and associated hardware solutions available to assist with audit tracking and managing inventory. An asset management database can be configured to store as much or as little information as is deemed necessary, though typical data would be type, model, serial number, asset ID, location, user(s), value, and service information. For each asset record, there should also be a copy of or link to the appropriate vendor documentation. This includes both an invoice and warranty/support contract and support and troubleshooting guidance.

A product such as Lansweeper assists inventory management by scanning network hosts and compiling an asset information database automatically. (Screenshot used with permission from Lansweeper.)

Assessment Reports

Where an audit report focuses on identifying and documenting assets, an assessment report evaluates the configuration and deployment of those assets, such as deviation from baseline configuration or performance. The report will make recommendations where the network is not meeting goals for performance or security. Audit and assessment reports are often contracted to third parties and might be driven by regulatory or compliance demands.

System Life Cycle

One of the functions of auditing and assessment is to manage system life cycle. A system life cycle roadmap refers to the controlled acquisition, deployment, use, and decommissioning of assets. An audit and assessment report can identify assets that are no longer fully supported by the vendor or that otherwise no longer meet performance or security requirements.

PHYSICAL NETWORK DIAGRAMS

Asset and configuration item (CI) documentation makes significant use of diagrams. A diagram is the best way to capture the complex relationships between network elements. It is important not to try to include too much information as this tends to make the diagram too complex to be useful. Consequently, a large number of diagram types are used in network management. One basic distinction is between physical and logical network diagrams. Within the class of physical network diagrams, the following types are commonly used.

Floor Plan

A floor plan is a detailed diagram of wiring and port locations. For example, you might use floor plans to document wall port locations and cable runs in an office. Physically accurate floor plans are hard to design and are likely to require the help of an architect or graphics professional.

Wiring Diagram

A wiring diagram (or pin-out) shows detailed information about the termination of twisted pairs in an RJ-45 or RJ-48C jack or Insulation Displacement Connector (IDC). You might also use a wiring diagram to document how fiber-optic strands are terminated.

You should document the wiring diagrams used to terminate twisted pairs. Ethernet is wired by T568A or T568B, and the same standard should be used consistently throughout the network.

Distribution Frame

A port location diagram identifies how wall ports located in work areas are connected back to ports in a distribution frame or patch panel and then from the patch panel ports to the switch ports. Within a structured cabling system, there are two types of distribution frame:

●	Main Distribution Frame (MDF)-The location for distribution/core level internal switching. The MDF will terminate trunk links from multiple Intermediate Distribution Frames (IDFs). The MDF also serves as the location for termination of external (WAN) circuits. You should ensure that WAN links to the Internet or to remote offices from the MDF are clearly labeled and that key information such as IP addresses and bandwidth is documented. The WAN provider will assign a circuit ID, and you will need to quote this if raising any sort of support issue.

●	Intermediate Distribution Frame (IDF)-In a large network, one or more IDFs provides termination for access layer switches that serve a given area, such as a single office floor. Each IDF has a trunk link to the MDF. Make sure that these are clearly labeled and distinct from access ports.

In addition to having a diagram, it can be very useful to take a photo of the current configuration by using a digital camera or smartphone. This provides an additional visual reference for troubleshooting and identifying unauthorized changes.

In order for a physical diagram of cabling and assets to make any sense, there must be a system of labeling in place for identifying these assets. A typical type of port naming convention is for alphanumeric identifiers for the campus (for multicampus networks), building (for campus networks), telecommunications space, and port. For example, CB01-01A-D01 could refer to a cable terminating at Main Campus Building (CB01), telecommunications space A on floor 1 (01A), data port 1 (D01). Structured cable and patch cords should be labeled at both ends to fully identify the circuit.

Site Survey Report

A wireless site survey report overlays a floor plan with graphics showing signal strength and channel utilization at different points in the building.

RACK DIAGRAMS

A rack system is a specially configured steel shelving system for patch panels, switches and routers, and server devices. Racks are standard widths and can fit appliances using standard height multiples of 1.75" called units (U). For example, a basic switch might be 1U while a server might be 4U (7") in height.

A rack diagram records the position of each appliance in the rack. You can obtain stencils that represent vendor equipment from their websites or a collection such as visiocafe.com. You can record key configuration information for each item using labels. As well as service tags and port IDs and links, you should identify which power outlets on the uninterruptible power supply (UPS) connect to which appliance power supply units (PSU)s.

Designing rack layout in Microsoft Visio. (Screenshot used with permission from Microsoft.)

LOGICAL VERSUS PHYSICAL NETWORK DIAGRAMS

In contrast to diagrams such as floor plans that are drawn to an accurate scale, a schematic is a simplified or abstracted representation of a system. In terms of the physical network topology, a schematic diagram can show the general placement of equipment and telecommunications rooms, plus device and port IDs, without trying to capture the exact position or relative size of any one element. Schematics can also be used to represent the logical structure of the network in terms of zones and subnets.

When you make network schematics, resist the urge to represent too much in a single diagram. For example, create separate diagrams for the PHY, Data Link, and Logical (IP) layers. Some of the information appropriate to show at each layer includes:

●	PHY (Physical layer)-Asset IDs and cable links. You can use color-coding or line styles to represent the cable type (make sure the diagram has an accompanying legend to explain your scheme).

●	Data Link (Layer 2)-Shows interconnections between switches and routers, with asset IDs (or the management IP of the appliance), interface IDs, and link-layer protocol and bandwidth. You could use line thickness to represent bandwidth, but for clarity it is a good idea to use labels as well.

●	Logical (IP/Layer 3)-IP addresses of router interfaces (plus any other static IP assignments) and firewalls, plus links showing the IP network ID and netmask, VLAN ID (if used), and DHCP scopes.

●	Application-Server instances and TCP/UDP ports in use. You might also include configuration information and performance baselines (CPU, memory, storage, and network utilization) at this level.

Schematics can either be drawn manually using a tool such as Microsoft® Visio® or compiled automatically from network mapping software.

Schematics can use either representative icons or pictures or drawings of actual product models. As far as icons go, the ones created by Cisco are recognized as standards. These are freely available (without alteration) from Cisco's website (cisco.com/c/en/us/about/brand-center/network-topology-icons.html). Some of the more commonly used devices are shown here:

Common Cisco network icons. (Images © and Courtesy of Cisco Systems, Inc. Unauthorized use not permitted.)

SECURITY RESPONSE PLANS AND PROCEDURES

Security response plans and procedures establish what to do when certain types of events occur. These plans attempt to anticipate adverse events so that impacts can be minimized.

Incident Response Plan

An incident response plan sets out the procedures, tools, methods of communication, and guidelines for dealing with security incidents. An incident is where security is breached or there is an attempted breach. Incident response is one of the most difficult areas of security to plan for and implement because its aims can be incompatible:

1. `	`The immediate aim is usually to protect confidential data or minimize impacts from its loss and re-establish a secure working system.
1. `	`It may also be important to preserve evidence of the incident with the aim of prosecuting the perpetrators. Forensic evidence collection can interfere with re-establishing availability, however.
1. `	`Follow-up or lessons learned analysis will attempt to prevent reoccurrence of similar incidents.

The actions of first responders immediately following detection of an incident can have a critical impact on these aims, so an effective policy and well-trained incident response professionals are crucial. Incident response is also likely to require coordinated action and authorization from several different departments or managers, which adds further levels of complexity.

Disaster Recovery Plan

Where incident response is focused on individual security policy violations, a disaster recovery plan (DRP) addresses large-scale incidents. These will typically be incidents that threaten the performance or security of a whole site. A DRP should accomplish the following:

●	Identify scenarios for natural and non-natural disasters and options for protecting systems.

●	Identify tasks, resources, and responsibilities for responding to a disaster. Disaster recovery focuses on tasks such as switching services to failover systems or sites and restoring systems and data from backups.

●	Train staff in the disaster planning procedures and how to react well to adverse events.

Business Continuity Plan

Where disaster recovery focuses on plans for specific scenarios, a business continuity plan (BCP) or continuity of operations plan (COOP) is a collection of processes and resources that enable an organization to maintain normal business operations in the face of some adverse event. Continuity planning activity focuses on the functions performed by a business or other organization:

●	Business impact analysis (BIA) identifies mission essential and primary business functions and the risks that would arise if the organization cannot fulfill them.

●	IT contingency planning (ITCP) or IT service continuity planning (ITSCP) ensures that these functions are supported by resilient IT systems, working to identify and mitigate all single points of failure from a process or function.

HARDENING AND SECURITY POLICIES

Security policy establishes a duty for each employee to ensure the confidentiality, integrity, and availability of any data assets or processing systems that they use as part of their job. This overall security policy will be supplemented by numerous operational policies to govern specific areas of activity or configuration.

Human Resources (HR) is the department given the task of recruiting and managing the organization's most valuable and critical resource: people. One function of HR is to communicate security policies to employees, including any updates to the policies. Another function is to enforce disciplinary measures (perhaps in conjunction with departmental managers).

Onboarding

Onboarding is the process of welcoming a new employee to the organization. Similar principles apply to taking on new suppliers or contractors. Some of the tasks that most affect security during the onboarding process are as follows:

●	Background check-This process essentially determines that a person is who they say they are and are not concealing criminal activity, bankruptcy, or connections that would make them unsuitable or risky. Employees working in high confidentiality environments or with access to high value transactions will obviously need to be subjected to a greater degree of scrutiny.

●	Identity and access management (IAM)-Create an account for the user to access the computer system, assign the appropriate privileges, and ensure the account credentials are known only to the valid user.

●	Asset allocation-Provision computers or mobile devices for the user or agree on the use of BYOD devices.

●	Training/policies-Schedule appropriate security awareness and role-relevant training and certification.

Offboarding

Offboarding is the process of ensuring that an employee leaves a company gracefully. In terms of security, there are several processes that must be completed:

●	IAM-Disable the user account and privileges. Ensure that any information assets created or managed by the employee but owned by the company are accessible (in terms of encryption keys or password-protected files).

●	Retrieving company assets-Secure mobile devices, keys, smart cards, USB media, and so on. The employee will need to confirm (and in some cases prove) that they have not retained copies of any information assets.

●	Returning personal assets-Employee-owned devices need to be wiped of corporate data and applications. The employee may also be allowed to retain some information assets (such as personal emails or contact information), depending on the policies in force.

The departure of some types of employees should trigger additional processes to resecure network systems. Examples include employees with detailed knowledge of security systems and procedures and access to shared or generic account credentials. These credentials must be changed immediately.

USAGE POLICIES

Usage policies set out rules for how users should interact with network systems and data.

Password Policy

A password policy instructs users on best practice in choosing and maintaining a network access credential. Password protection policies mitigate against the risk of attackers being able to compromise an account and use it to launch other attacks on the network. For example, users must be instructed not to write down passwords, store them in unsecure files, or share them with other users. The credential management policy also needs to alert users to different types of social engineering and phishing attacks.

System-enforced policies can help to enforce credential management principles by stipulating requirements for user-selected passwords. The following rules enforce password complexity and make them difficult to guess or compromise:

●	Length-The longer a password, the stronger it is. A typical strong network password should be 12 to 16 characters. A longer password or passphrase might be used for mission critical systems or devices where logon is infrequent.

●	Complexity-Varying the characters in the password makes it more resistant to dictionary-based attacks.

●	Aging and history-Requiring that the password be changed periodically and preventing the reuse of previously selected passwords.

You should also note that recent guidance issued by NIST (nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63b.pdf) deprecates some of the "traditional" elements of password policy, such as complexity and aging.

Acceptable Use Policies

An acceptable use policy (AUP) sets out the permitted uses of a product or service. It might also state explicitly prohibited uses. Such a policy might be used in different contexts. For example, an AUP could be enforced by a business to govern how employees use equipment and services, such as telephone or Internet access, provided to them at work. Another example might be an ISP enforcing a fair use policy governing usage of its Internet access services.

BYOD Policies

A mobile deployment model describes the way employees are provided with smartphone or tablet devices and applications. Some companies issue employees with corporate-owned and controlled devices and insist that only these are used to process company data. Other companies might operate a bring your own device (BYOD) policy. BYOD means that the mobile is owned by the employee and can be used on the corporate network so long as it meets a minimum specification required by the company (in terms of OS version and functionality). The employee will have to agree on the installation of corporate apps and to some level of oversight and auditing. Very often, BYOD devices are registered with enterprise management software and configured with sandboxed corporate workspaces and apps.

Enterprise management software can be used to segment corporate data from personal data on BYOD devices. (Screenshot used with permission from Google.)

DATA LOSS PREVENTION

The theft or loss of confidential and/or personal information is referred to as a data breach. Data breach can expose an organization to huge reputational and financial costs. Consequently, data handling is an area of activity that should be tightly managed by both policies and technical controls.

Data loss prevention (DLP) products scan content in structured formats (such as a database with a formal access control model) or unstructured formats, such as email or word processing documents. DLP products use some sort of dictionary database or algorithm (regular expression matching) to identify confidential or personal/sensitive data. The transfer of content to removable media or by email or to social networking or cloud storage services can then be blocked if it does not conform to a predefined policy.

Creating a data loss prevention policy in Office 365. (Screenshot used with permission from Microsoft.)

REMOTE ACCESS POLICIES

Where employees are assigned the right to connect to the corporate network from a remote location using a VPN, their use of remote access privileges must be governed by technical and policy controls. Some of the issues that must be mitigated include the following:

●	Malware protection-The computer may not be accessible to network systems used to update and enforce malware protection. This may have to be left to the end-user. If a worm or Trojan is installed, network security may be compromised.

●	Security information-Authentication information may be stored on the client (saving a password, for instance), making the network vulnerable if the computer is stolen.

●	Data transfer-Files copied to the client may no longer be properly secured, raising the potential that confidential information could be stolen along with the device.

●	Local privileges-The user of a remote computer might be configured with administrative privileges but have no understanding of how such privileges can be exploited or misused. They might install unauthorized software on the machine or make it more vulnerable to malware by browsing the web using their administrative account.

●	Weak authentication-Relying on a username and password combination is simply not secure enough in a remote access scenario. Two-factor authentication using smart cards or biometric recognition in addition to a PIN or password should be enforced. If this is not an option, a strong password policy must be enforced, and users made aware of the very real risks of writing down or sharing their password.

●	Untrusted networks-The user might configure weak authentication on a home wireless network or use a public access point, raising the risk of snooping attacks.

The principal solution to remote access security problems is to educate remote users about security risks and their responsibilities. Enforcement can be provided by having remote devices audited periodically to ensure that antivirus, firewall, and OS/browser/application patches are being kept up to date and to check that unlicensed software has not been installed. It is also wise to limit what remote users can access on the local network and to severely restrict the rights of remote computer accounts. The principle of least privilege should be applied.

COMMON AGREEMENTS

Agreements are used between a company and its employees and between companies to enforce performance and security objectives.

Service Level Agreement Requirements

A service level agreement (SLA) is a contractual agreement setting out the detailed terms under which an ongoing service is provided. This can be a legally binding formal contract between supplier and customer businesses or a less formal agreement, such as an SLA agreed between internal departments. SLA requirements define aspects of the service, such as scope, performance characteristics, and responsibilities that are agreed upon between the service provider and the customer.

Depending on the nature of your organization's business, you may be responsible for maintaining SLA requirements agreed with your customers, use SLAs to guarantee service standards from your suppliers, or both.

Non-Disclosure Agreement

A non-disclosure agreement (NDA) is the legal basis for protecting information assets. It defines what uses of sensitive data are permitted, what storage and distribution restrictions must be enforced, and what penalties breaches of the agreement will incur. A contract of employment is highly likely to contain NDA clauses. NDAs are also used between companies and contractors and between two companies.

Memorandum of Understanding

A memorandum of understanding (MOU) is a preliminary or exploratory agreement to express an intent to work together. MOUs are usually intended to be relatively informal and not to act as binding contracts. MOUs almost always have clauses stating that the parties shall respect confidentiality, however.


Topic 17B: Explain Physical Security Methods

BADGES AND SITE SECURE ENTRY SYSTEMS

Prevention-type physical controls are ones that stop an intruder from gaining unauthorized access, if they work effectively. Where an area is controlled by being enclosed by walls or fencing, access is channeled through defined points of entry, such as doors and gates. These entry points can be protected by types of electronic lock.

Access Control Hardware

Various types of access control hardware or electronic locks can be deployed to enable users to authenticate quickly at access points:

●	Badge reader-A photographic ID badge showing name and access level is one of the cornerstones of building security. A smart badge comes with an integrated chip and data interface that stores the user’s key pair and digital certificate. The user presents the card and enters a PIN and then the card uses its cryptographic keys to authenticate securely via the entry point’s badge reader. A smart badge is either contact based, meaning that it must be physically inserted into a reader, or contactless, meaning that data is transferred using a tiny antenna embedded in the card. The ISO has published various ID card standards to promote interoperability, including ones for smart cards (ISO 7816 for contact and ISO 14443 for contactless types).

●	Biometric-An electronic lock may also be integrated with a biometric scanner. A biometric device is activated by human physical features, such as a fingerprint, voice, retina, or signature. Each user’s biometric is recorded as a template and stored on an authentication server. To gain access, the user’s biometric is scanned again by a fingerprint reader or iris/retina scanner and compared to the template scan.

Two types of electronic lock with biometric reader (left) and badge/card reader (right). (Images © 123RF.com.)

Access Control Vestibule

The main problem with a simple door or gate as an entry mechanism is that it cannot accurately record who has entered or left an area. More than one person may pass through the gateway at the same time; a user may hold a door open for the next person; an unauthorized user may "tailgate" behind an authorized user. This risk may be mitigated by installing a turnstile (a type of gateway that only allows one person through at a time). The other option is to add some sort of surveillance on the gateway. Where security is critical and cost is no object, an access control vestibule, or mantrap, could be employed. An access control vestibule is where one gateway leads to an enclosed space protected by another barrier.

PHYSICAL SECURITY FOR SERVER SYSTEMS

The access control hardware measures that can be deployed to prevent unauthorized entry to sites, buildings, and floors or zones within a building can also be used to manage access to IT assets.

Locking Racks

Installing equipment within secure cabinets/enclosures provides mitigation against insider attack and attacks that have broken through the perimeter security mechanisms. These can be supplied with key-operated or electronic locks. It is also possible to provision lockable brackets and drawers to protect or isolate individual elements within a rack.

Some datacenters may contain racks with equipment owned by different companies (colocation). These racks can be installed inside cages so that technicians can only physically access the racks housing their own company's servers and appliances.

Colocation cages. (Image © Chris Dag and shared with CC BY 2.0 flickr.com/photos/chrisdag/

865711871\.)

Locking Cabinets

Lockable cabinets or safes can provide secure storage for individual items, such as media with cryptographic keys or shared password lists.

Smart Lockers

A smart locker is a cabinet that supports unlocking via a smart card/badge or biometric. Lockers may also have built-in monitoring and surveillance that can alert an administrator when an item is added ore removed.

DETECTION-BASED DEVICES

Detection-based controls provide an important additional layer of defense in the event that prevention-based controls fail to work. For example, surveillance is another layer of security designed to improve the resilience of perimeter gateways. Effective surveillance mechanisms ensure that attempts to penetrate a barricade are detected. Surveillance may be focused on perimeter areas or within security zones themselves. Surveillance can be performed by security guards or via video. Camera-based surveillance is a cheaper means of monitoring than maintaining separate guards at each gateway or zone.

Cameras

A security camera is either fixed or can be operated using Pan-Tilt-Zoom (PTZ) controls. Different cameras suit different purposes. If you want to record the image of every person entering through an access control vestibule, a fixed, narrow focal length camera positioned on the doorway will be perfectly adequate. If you want to survey a large room and pick out individual faces, a camera with PTZ is required.

Pan-tilt-zoom CCTV installed to monitor a server room. (Image by Dario Lo Presti © 123RF.com.)

The cameras in a Closed-Circuit Television (CCTV) network are typically connected to a multiplexer using coaxial cabling. The multiplexer can then display images from the cameras on one or more screens, allow the operator to control camera functions, and record the images to tape or hard drive. Newer camera systems may be linked in an IP network, using regular data cabling. Small IP cameras can use Power over Ethernet (PoE), avoiding the need to provision a separate power circuit.

Asset Tags

An asset tag shows the ID of a device or component and links it to an inventory management database. Radio Frequency ID (RFID) asset tracking tags allow electronic surveillance of managed assets. The tags can be detected at entry/exit points to prevent theft. A battery-powered component might be in the tag, or the tag might be passive and read and scanned by a powered device. The tags are entered into a tracking database, which also usually has a map of the coverage area so that a particular asset can be located.

ALARMS AND TAMPER DETECTION

Alarms provide a detection-based security mechanism, though an audible alarm can also be an effective deterrent by causing the attacker to abandon the intrusion attempt. There are two main types:

●	Circuit-A circuit-based alarm sounds when the circuit is opened or closed, depending on the type of alarm. This could be caused by a door or window opening or by a fence being cut. A closed-circuit alarm is more secure because an open circuit alarm can be defeated by cutting the circuit. This type of system can be used for tamper detection.

●	Motion detection-A motion-based alarm is linked to a detector triggered by any movement within a relatively large area, such as a room. The sensors in these detectors are either microwave radio reflection (similar to radar) or passive infrared (PIR), which detect moving heat sources.

As well as protecting building areas, alarms can be installed on rack systems and appliance chassis. For example, a chassis intrusion alarm can alert an administrator if a server case is opened.

Another potential threat is that an attacker could splice a tap into network data cable. A physically secure cabled network is referred to as a Protected Distribution System (PDS). A hardened PDS is one where all cabling is routed through sealed metal conduit and subject to periodic visual inspection. Lower grade options are to use different materials for the conduit (plastic, for instance). Tamper detection alarm systems can be implemented within the cable conduit.

ASSET DISPOSAL

Physical security controls also need to take account of the disposal phase of the system life cycle. When a server or appliance is disposed of by resale, gift, or recycling, there is a risk that software licenses could be misused or that configuration information valuable to an attacker could be leaked. These risks can be mitigated by ensuring that the built-in factory reset routine is invoked to wipe any custom configuration settings or modifications when decommissioning a server, switch, router, firewall, or printer.

A factory reset may leave data remnants, however. Data remnant removal is critical because an organization's confidential data or personal/sensitive data held could be compromised.

Data remnant removal refers to ensuring that no data is recoverable from hard disk drives (HDDs), flash devices or solid state drives (SSDs), tape media, CD and DVD ROMs before they are disposed of or put to a different use. Paper documents must also be disposed of securely. Data remnants can be dealt with either by destroying the media or by sanitizing it (removing the confidential information but leaving the media intact for reuse).

Methods of destroying media include incineration, pulverization, and degaussing (for magnetic media such as hard drives).

Media sanitization refers to erasing data from HDD, SSD, and tape media before they are disposed of or put to a different use. The standard method of sanitizing an HDD is called overwriting. This can be performed using the drive's firmware tools or a utility program. The basic type of overwriting is called zero filling, which just sets each bit to zero. Single- pass zero filling can leave patterns that can be read with specialist tools. A more secure method is to overwrite the content with one pass of all zeros, then a pass of all ones, and then one or more additional passes in a pseudorandom pattern.

Secure Erase

Since 2001, the SATA and Serial Attached SCSI (SAS) specifications have included a Secure Erase (SE) command. This command can be invoked using a drive/array utility or the hdparm Linux utility. On HDDs, this performs a single pass of zero-filling.

For SSDs and hybrid drives and some USB thumb drives and flash memory cards, overwriting methods are not reliable, because the device uses wear-leveling routines in the drive controller to communicate which locations are available for use to any software process accessing the device. On SSDs, the SE command marks all blocks as empty. A block is the smallest unit on flash media that can be given an erase command. The drive firmware's automatic garbage collectors then perform the actual erase of each block over time. If this process is not completed (and there is no progress indicator), there is a risk of remnant recovery, though this requires removing the chips from the device to analyze them in specialist hardware.

Instant Secure Erase

HDDs and SSDs that are self-encrypting drives (SEDs) support another option, invoking a SANITIZE command set in SATA and SAS standards from 2012 to perform a crypto erase. Drive vendors implement this as Instant Secure Erase (ISE). With an SED, all data on the drive is encrypted using a media encryption key. When the erase command is issued, the MEK is erased, rendering the data unrecoverable.

EMPLOYEE TRAINING

Employee training is another type of prevention-based security control. Untrained users represent a serious vulnerability because they are susceptible to social engineering and malware attacks and may be careless when handling sensitive or confidential data or allowing access to premises.

Train users in secure behavior. (Image by dotshock © 123RF.com.)

Appropriate security awareness training needs to be delivered to employees at all levels, including end users, technical staff, and executives. Some of the general topics that need to be covered include the following:

●	Overview of the organization's security policies and the penalties for non-compliance.

●	Incident identification and reporting procedures.

●	Site security procedures, restrictions, and advice, including safety drills, escorting guests, use of secure areas, and use of personal devices.

●	Data handling, including document confidentiality, PII, backup, encryption, and so on.

●	Password and account management plus security features of PCs and mobile devices.

●	Awareness of social engineering and malware threats, including phishing, website exploits, and spam plus alerting methods for new threats.

●	Secure use of software such as browsers and email clients plus appropriate use of Internet access, including social networking sites.

There should also be a system for identifying staff performing security-sensitive roles and grading the level of training and education required (between beginner, intermediate, and advanced, for instance). Note that in defining such training programs you need to focus on job roles, rather than job titles, as employees may perform different roles and have different security training, education, or awareness requirements in each role.

Topic 17C: Compare and Contrast Internet of Things Devices

INTERNET OF THINGS

The term Internet of Things (IoT) is used to describe the global network of personal devices, home appliances, home control systems, vehicles, and other items that have been equipped with sensors, software, and network connectivity. These features allow these types of objects to communicate and pass data between themselves and other traditional systems like computer servers. This is often referred to as Machine to Machine (M2M) communication.

Consumer-grade Smart Devices

Smart devices are used to implement home automation systems. An IoT smart device network will generally use the following types of components:

●	Hub/control system-IoT devices usually require a communications hub to facilitate wireless networking. There must also be a control system, as most IoT devices are headless, meaning they have no user control interface. A headless hub could be implemented as a smart speaker operated by voice control or use smartphone/PC app for configuration.

●	Smart devices-IoT endpoints implement the function, such as a smart lightbulb, refrigerator, thermostat/heating control, or doorbell/video entry phone that you can operate remotely. These devices are capable of compute, storage, and network functions that are all potentially vulnerable to exploits. Most smart devices use a Linux or Android kernel. Because they're effectively running mini-computers, smart devices are vulnerable to some of the standard attacks associated with web applications and network functions. Integrated peripherals such as cameras or microphones could be compromised to facilitate surveillance.

Physical Access Control Systems and Smart Buildings

A physical access control system (PACS) is a network of monitored locks, intruder alarms, and video surveillance cameras. A building automation system (BAS) or smart building for offices and datacenters can include PACS, but also network-based configuration and monitoring of heating, ventilation, and air conditioning (HVAC), fire control, power and lighting, and elevators and escalators. These subsystems are implemented by programmable logic controllers (PLCs) and various types of sensors that measure temperature, air pressure, humidity, room occupancy, and so on.

INDUSTRIAL CONTROL SYSTEMS/SUPERVISORY CONTROL AND DATA ACQUISITION

Internet of Things and other embedded systems are used within many sectors of industry, including energy generation and distribution, mining and refining raw materials, fabrication and manufacturing, and logistics (moving and delivering components and goods).

Industrial systems have different priorities to IT systems. Often, hazardous electromechanical components are involved, so safety is the overriding priority. Industrial processes also prioritize availability and integrity over confidentiality-reversing the CIA triad as the AIC triad.

Workflow and Process Automation Systems

An industrial control system (ICS) provides mechanisms for workflow and process automation. An ICS controls machinery used in critical infrastructure, like power suppliers, water suppliers, health services, telecommunications, and national security services. An ICS that manages process automation within a single site is usually referred to as a distributed control system (DCS).

An ICS comprises plant devices and equipment with embedded PLCs. The PLCs are linked by a cabled network to actuators that operate valves, motors, circuit breakers, and other mechanical components, plus sensors that monitor some local state, such as temperature. Output and configuration of a PLC is performed by one or more human-machine interfaces (HMIs). An HMI might be a local control panel or software running on a computing host. PLCs are connected within a control loop, and the whole process automation system can be governed by a control server. Another important concept is the data historian, which is a database of all the information generated by the control loop.

Supervisory Control and Data Acquisition

A supervisory control and data acquisition (SCADA) system takes the place of a control server in large-scale, multiple-site ICSs. SCADA typically run as software on ordinary computers, gathering data from and managing plant devices and equipment with embedded PLCs, referred to as field devices. SCADA typically use WAN communications, such as cellular or satellite, to link the SCADA server to field devices.

IOT NETWORKS

Each device in an IoT network is identified with some form of unique serial number or code embedded within its own operating or control system and can interoperate within the existing Internet infrastructure, either directly or via an intermediary. As these devices tend to be small and often either unpowered or dependent on battery power, the standard Ethernet, cellular, and Wi-Fi networking products that connect computers are not always suitable for use. Other networking standards and products have been developed to facilitate IoT networks.

Operational Technology Networks

A cabled network for industrial applications is referred to as an operational technology (OT) network. These typically use either serial data protocols or industrial Ethernet. Industrial Ethernet is optimized for real-time, deterministic transfers. Such networks might use vendor-developed data link and networking protocols, as well as specialist application protocols.

Cellular Networks

A cellular network for IoT enables long-distance communication over the same system that supports mobile and smartphones. This is also called baseband radio, after the baseband processor that performs the function of a cellular modem. There are several baseband radio technologies:

●	Narrowband-IoT (NB-IoT)-this refers to a low-power version of the Long Term Evolution (LTE) or 4G cellular standard. The signal occupies less bandwidth than regular cellular. This means that data rates are limited (20-100 kbps), but most sensors need to send small packets with low latency, rather than making large data transfers. Narrowband also has greater penetrating power, making it more suitable for use in inaccessible locations, such as tunnels or deep within buildings, where ordinary cellular connectivity would be impossible.

●	LTE Machine Type Communication (LTE-M)-this is another low-power system but supports higher bandwidth (up to about 1 Mbps).

Z-Wave and Zigbee

Z-Wave is a wireless communications protocol used primarily for home automation. The Z-Wave Alliance operates a certification program for devices and software. Z-Wave creates a mesh network topology. Devices can be configured to work as repeaters to extend the network but there is a limit of four "hops" between a controller device and an endpoint. Z-Wave has been registered in most countries worldwide and uses radio frequencies in the high 800 to low 900 MHz range. It is designed to run for long periods (years) on battery power.

Zigbee has similar uses to Z-Wave and is an open-source competitor technology to it. The Zigbee Alliance operates certification programs for its various technologies and standards. Zigbee uses the 2.4 GHz frequency band. This higher frequency allows more data bandwidth at the expense of range compared to Z-Wave and the greater risk of interference from other 2.4 GHz radio communications. Zigbee supports more overall devices within a single mesh network (65,000 compared to 232 for Z-Wave), and there is no hop limit for communication between devices.

PLACEMENT AND SECURITY

Placement issues for embedded and IoT systems are best considered by dividing them into three principal groups: consumer-grade devices, smart building technology, and industrial systems.

While the network of individual devices might use Z-Wave or Zigbee, the hub for home automation plus larger appliances are usually connected directly to the local Wi-Fi network. Consumer-grade smart devices and home automation products can be poorly documented and patch management/security response processes of vendors can be inadequate. When they are designed for residential use, IoT devices can suffer from weak defaults. They may be configured to "work" with a minimum of configuration effort. There may be recommended steps to secure the device that the customer never takes.

In a corporate workspace, the main risk from smart device placement is that of shadow IT, where employees deploy a network-enabled device without going through a change and configuration management process. A vulnerability in the device would put it at risk of being exploited as an access point to the network. These devices also pose a risk for remote working, where the employee joins the corporate VPN using a home wireless network that is likely to contain numerous undocumented vulnerabilities and configuration weaknesses.

These risks can be mitigated by regular audits and through employee security awareness training.

Smart Buildings

By contrast with consumer-grade components, there should be less scope for compromise in the entry mechanisms and climate/lighting control components of a properly designed smart building system. Management and monitoring of the system should be performed over isolated network segments. Configuration management and change control processes should ensure that no weak configurations are introduced and that vendor advisories are tracked for any known vulnerabilities or exploits so that these can be patched or mitigated.

ICS/SCADA

While an ICS or SCADA is typically implemented as a dedicated OT or wireless WAN network, there may be points where these networks are linked to a corporate data network. Historically, these vulnerable links and bridging hosts have been exploited by threat actors. There are risks both to embedded systems from the data network and to corporate data assets and systems from the embedded network. Links between OT and IT networks must be monitored and subject to access controls.