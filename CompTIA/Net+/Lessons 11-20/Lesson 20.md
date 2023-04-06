Lesson 20: Summarizing Cloud and Datacenter Architecture

Topic 20A: Summarize Cloud Concepts

CLOUD SCALABILITY AND ELASTICITY

From the consumer point of view, cloud computing is a service that provides on-demand resources-server instances, file storage, databases, or applications-over a network, typically the Internet. The service is a cloud because the end user is not aware of or responsible for any details of the procurement, implementation, or management of the infrastructure that underpins those resources. The end user is interested in and pays for only the services provided by the cloud.

From the provider point of view, provisioning a cloud is like provisioning any other type of large-scale datacenter. Cloud computing almost always uses one or more methods of virtualization to ensure that resources are quickly and easily provisioned to the client who requires them.

Among other benefits, the cloud provides scalability and elasticity:

●	Scalability means that the costs involved in supplying the service to more users are linear. For example, if the number of users doubles in a scalable system, the costs to maintain the same level of service would also double (or less than double). If costs more than double, the system is less scalable. Scalability can be achieved by adding nodes (horizontal/scaling out) or by adding resources to each node (vertical/scaling up).

●	Elasticity refers to the system's ability to handle changes on demand in real time. A system with high elasticity will not experience loss of service or performance if demand suddenly doubles (or triples, or quadruples). Conversely, it may be important for the system to be able to reduce costs when demand is low.

In order to meet scalability and elasticity requirements, cloud providers must be able to provision and deprovision resources automatically. This is achieved through resource pooling and virtualization. Resource pooling means that the hardware making up the cloud provider's datacenter is not dedicated or reserved to a single customer account. The layers of virtualization used in the cloud architecture allow the provider to provision more CPU, memory, disk, or network resource using management software, rather than (for instance) having to go to the datacenter floor, unplug a server, add a memory module, and reboot.

CLOUD DEPLOYMENT MODELS

In most cases, the cloud-that is, the hardware and/or software hosting the service-will be offsite relative to the organization's users. The cloud users will typically require an Internet link to access the cloud services. There can be different ownership and access arrangements for clouds, however. These cloud deployment models can be broadly categorized as follows:

●	Public (or multitenant)-a service offered over the Internet by cloud service providers (CSPs) to cloud consumers, often referred to as tenants. With this model, businesses can offer subscriptions or pay-as-you-go financing, while at the same time providing lower-tier services free of charge. As a shared resource, there are risks regarding performance and security. Multicloud architectures are where the consumer organization uses services from more than one CSP.

●	Hosted Private-Hosted by a third party for the exclusive use of the organization. This is more secure and can guarantee a better level of performance, but it is correspondingly more expensive.

●	Private-Cloud infrastructure that is completely private to and owned by the organization. In this case, there is likely to be one business unit dedicated to managing the cloud while other business units make use of it. With private cloud computing, organizations can exercise greater control over the privacy and security of their services. This type of delivery method is geared more toward banking and governmental services that require strict access control in their operations.

This type of cloud could be on-premises or offsite relative to the other business units. An onsite link can obviously deliver better performance and is less likely to be subject to outages (loss of an Internet link, for instance). On the other hand, a dedicated offsite facility may provide better shared access for multiple users in different locations.

●	Community-This is where several organizations share the costs of either a hosted private or fully private cloud. This is usually done in order to pool resources for a common concern, like standardization and security policies.

●	Hybrid-A cloud computing solution that implements some sort of hybrid public/private/community/hosted/onsite/offsite solution. For example, a travel organization may run a sales website for most of the year using a private cloud but "break out" the solution to a public cloud at times when much higher utilization is forecast. As another example, a hybrid deployment may be used to provide some functions via a public cloud, but keep sensitive or regulated infrastructure, applications, and data on-premises.

Flexibility is a key advantage of cloud computing, but the implications for data risk must be well understood when you are moving data between private and public storage environments.

CLOUD SERVICE MODELS

As well as the deployment model-public, private, hybrid, or community-cloud services are often differentiated on the level of complexity and preconfiguration provided. These models are referred to as Something/Anything/Everything as a Service (XaaS). Some of the most common XaaS models are infrastructure, software, platforms, and desktops.

Infrastructure as a Service

Infrastructure as a Service (IaaS) is a means of provisioning IT resources such as servers, load balancers, and storage area network (SAN) components quickly. Rather than purchase these components and the Internet links they require, you rent them on an as-needed basis from the service provider's datacenter. Examples include Amazon Elastic Compute Cloud ( aws.amazon.com/ec2 ), Microsoft® Azure® Virtual Machines (azure.microsoft.com/services/virtual-machines), and OpenStack® (openstack.org).

Software as a Service

Software as a Service (SaaS) is a different model of provisioning software applications. Rather than purchasing software licenses for a given number of seats, a business would access software hosted on a supplier's servers on a pay-as-you-go or lease arrangement (on-demand). Virtual infrastructure allows developers to provision on-demand applications much more quickly than previously. The applications can be developed and tested in the cloud without the need to test and deploy on client computers. Examples include Microsoft Office 365® (support.office.com), Salesforce® (salesforce.com), and Google Workspace™ ( workspace.google.com ).

Platform as a Service

Platform as a Service (PaaS) provides resources somewhere between SaaS and IaaS. A typical PaaS solution would deploy servers and storage network infrastructure (as per IaaS) but also provide a multi-tier web application/database platform on top. This platform could be based on Oracle® or MS SQL or PHP and MySQL™. Examples include Oracle Database ( cloud.oracle.com/paas ), Microsoft Azure SQL Database (azure.microsoft.com/services/sql-database), and Google App Engine™ (cloud.google.com/appengine).

As distinct from SaaS though, this platform would not be configured to actually do anything. Your own developers would have to create the software (the CRM or e‑commerce application) that runs using the platform. The service provider would be responsible for the integrity and availability of the platform components, but you would be responsible for the security of the application you created on the platform.

Dashboard for Amazon Web Services Elastic Compute Cloud (EC2) IaaS/PaaS. (Screenshot courtesy of Amazon.)

Desktop as a Service

Desktop as a Service (DaaS) is a means of provisioning virtual desktop infrastructure (VDI) as a cloud service. VDI allows a client browser to operate an OS desktop plus software apps. This removes the need for an organization to deploy and maintain client PCs and software installs.

CLOUD CONNECTIVITY OPTIONS

Cloud connectivity is the mechanism by which clients connect to the cloud service. Connectivity with cloud-based services is always going to involve some tradeoffs but should consider price, bandwidth, latency (delay), and availability. In practical terms, there are a few options for connecting an organization's staff with cloud-based services.

Internet/Virtual Private Network

The simplest way of interfacing with a cloud service is to use the provider's website or application programming interface (API) over the Internet. This type of connection can also be implemented as a virtual private network (VPN), if this is supported by the cloud service provider. The VPN method has the advantages of being cost-effective and straightforward to set up wherever there is Internet connectivity, which is ideal for organizations that have a fragmented or distributed network structure. However, any connection running over the public Internet can suffer from poor performance due to latency and bandwidth throttling, so this would not normally be a solution for a mission critical or high-volume application.

Colocation within a datacenter offers a higher bandwidth solution by providing a direct or private link. The customer establishes infrastructure within a datacenter supported by the cloud provider or provisions a direct link from his or her enterprise network to the datacenter, possibly using private connections configured within a service provider's network. The datacenter installs a cross-connect cable or VLAN between the customer and the cloud provider, establishing a low latency, high bandwidth secure link. This solution is preferred for organizations which have a more centralized operation where the connection to the cloud can be from the main HQ and the company's own enterprise network is used to allow branch locations access.

INFRASTRUCTURE AS CODE

The use of cloud technologies encourages the use of scripted approaches to provisioning, rather than installing operating systems and apps and making configuration changes or installing patches manually. An approach to infrastructure management where automation and orchestration fully replace manual configuration is referred to as infrastructure as code (IaC).

One of the goals of IaC is to eliminate snowflake systems. A snowflake is a configuration or build that is different from any other. The lack of consistency-or drift-in the platform environment leads to security issues, such as patches that have not been installed, and stability issues, such as scripts that fail to run because of some small configuration difference.

Automation

Automation using scripting means that each configuration or build task is performed by a block of code. The script will take standard arguments as data, so there is less scope for uncertainty over configuration choices leading to errors. There are two principal types of automation tool:

●	Imperative tools require the precise steps to follow to achieve the desired configuration as input. This approach is most similar to automation through traditional scripting languages such as Bash and PowerShell.

●	Declarative tools take the desired configuration as input and leave detail of how that configuration should be achieved to the implementation platform.

Orchestration

Where automation focuses on making a single, discrete task easily repeatable, orchestration performs a sequence of automated tasks. For example, you might orchestrate adding a new VM to a load-balanced cluster. This end-to-end process might include provisioning the VM, configuring it with an app and network settings, adding the new VM to the load-balanced cluster, and reconfiguring the load-balancing weight distribution given the new cluster configuration. In doing this, the orchestrated steps would have to run numerous automated scripts or API service calls.

For orchestration to work properly, automated steps must occur in the right sequence, taking dependencies into account; it must provide the right security credentials at every step along the way; and it must have the rights and permissions to perform the defined tasks. Orchestration can automate processes that are complex, requiring dozens or hundreds of manual steps.

Automation and orchestration platforms connect to and provide administration, management, and orchestration for many popular cloud platforms and services. One of the advantages of using a third-party orchestration platform is protection from vendor lock in. If you wish to migrate from one cloud provider to another, or wish to move to a multicloud environment, automated workflows can often be adapted for use on new platforms. Industry leaders in this space include Chef (chef.io), Puppet ( puppet.com ), Ansible ( ansible.com ), and Kubernetes ( kubernetes.io ).

CLOUD SECURITY IMPLICATIONS

One of the risks of using a cloud-based solution is that potentially confidential or commercially secret data may be transferred over links that extend beyond the enterprise’s infrastructure and direct control. As such, it is imperative to identify precisely which risks you are transferring; to identify which responsibilities the service provider is undertaking, and which remain with you. This should be set out in a service level agreement (SLA) as a cloud responsibility matrix. This division of responsibility is referred to by Amazon as security of the cloud versus security in the cloud ( aws.amazon.com/compliance/shared-responsibility-model ).

For example, in a SaaS solution, the provider may be responsible for the confidentiality, integrity, and availability of the software. They would be responsible for configuring a fault tolerant, clustered server service; for firewalling the servers and creating proper authentication, authorization, and accounting procedures; for scanning for intrusions and monitoring network logs; applying OS and software patches; and so on. You may or may not be responsible for some or all of the software management functions, such as ensuring that administrators and users practice good password management, configuring system privileges, making backups of data, and so on. Where critical tasks are the responsibility of the service provider, you should try to ensure that there is a reporting mechanism to show that these tasks are being completed, that their disaster recovery plans are effective, and so on.

Another provision is that your company is likely to remain directly liable for serious security breaches. If customer data is stolen, for instance, or if your hosted website is hacked and used to distribute malware, the legal and regulatory "buck" still stops with you. You might be able to sue the service provider for damages, but your company would still be the point of investigation. You may also need to consider the legal implications of using a cloud provider if its servers are in a different country.

You must also consider the risk of insider threat, where the insiders are administrators working for the service provider. Without effective security mechanisms, such as separation of duties, it is possible that they would be able to gain privileged access to your data. Consequently, the service provider must be able to demonstrate to your satisfaction that they are prevented from doing so. There is also the risk that your data is in proximity to other, unknown virtual servers and that some sort of attack could be launched on your data from another virtual server.

Topic 20B: Explain Virtualization and Storage Area Network Technologies

HYPERVISOR TYPES

In a virtualization host, the hypervisor-or virtual machine monitor (VMM)-manages the virtual environment and facilitates interaction with the computer hardware and network. One basic distinction that can be made between virtual platforms is between host and bare metal methods of interacting with the host hardware. In a guest OS (or host-based) system, the hypervisor application (known as a Type II hypervisor) is itself installed onto a host operating system. Examples of host-based hypervisors include VMware Workstation™, Oracle® Virtual Box, and Parallels® Workstation. The hypervisor software must support the host OS.

Guest OS virtualization (Type II hypervisor). The hypervisor is an application running within a native OS, and guest OSes are installed within the hypervisor.

A bare metal virtual platform means that a Type I hypervisor is installed directly onto the computer and manages access to the host hardware without going through a host OS. Examples include VMware ESXi® Server, Microsoft's Hyper-V®, and Citrix's XEN Server. The hardware needs to support only the base system requirements for the hypervisor plus resources for the type and number of guest OSes that will be installed.

Type I bare metal hypervisor. The hypervisor is installed directly on the host hardware along with a management application, then VMs are installed within the hypervisor.

VIRTUAL NICS AND SWITCHES

Where multiple VMs are running on a single platform, virtualization provides a means for these VMs to communicate with each other and with other computers on the network (both physical and virtual) by using standard networking protocols. The guest OS running in each virtual machine is presented with an emulation of a standard hardware platform. Among the hardware devices emulated will be one or more network adapters. The number of adapters and their connectivity can be configured via the hypervisor.

Within the VM, the virtual NIC (vNIC) will look exactly like an ordinary network adapter and will be configurable in the same way. For example, protocols and services can be bound to it, it has a MAC address, and it can be assigned IPv4 and/or IPv6 addresses. In other words, a virtual NIC functions identically to a physical NIC for data transmission; it is just wholly software-based instead of being a combination of physical hardware, firmware, and driver software.

Typically, a hypervisor will implement network connectivity by means of one or more virtual switches (or vSwitch in VMware's terminology). These perform the same function as Layer 2 physical switches, except that they are implemented in software instead of hardware. Connectivity between the virtual network adapters in the guest VMs and the virtual switches is configured via the hypervisor. This is analogous to connecting patch cables between real computers and real switches.

In this networking model, the VMs and the virtual switch can all be contained within a single hardware platform, so no actual network traffic is generated; instead, data is moved from buffers in one VM to another. It is also possible to configure connectivity with a virtual switch that bridges the virtual and physical networks via the host computer's physical NIC. For example, in Microsoft's Hyper-V virtualization platform, three types of virtual switches can be created:

●	External-Binds to the host's NIC to allow the VM to communicate on the physical network.

●	Internal-Creates a bridge that is usable only by VMs on the host and the host itself. This type of switch does not permit access to the wider physical network.

●	Private-Creates a switch that is usable only by the VMs. They cannot use the switch to communicate with the host.

Configuring a virtual switch in Microsoft's Hyper-V hypervisor. The external switch allows the VM to use the physical network via the host's NIC. The private switches have no external access. (Screenshot used with permission from Microsoft.)

When the VMs are permitted to interact with a "real" network, the host must support a high bandwidth, high availability network link. Any failure of the physical link will affect multiple VMs.

Virtual switches can be as simple or complex as the hypervisor software makes them. For example, they can be used to implement VLANs or be configured to perform port mirroring. In a more advanced network, such as VMware's vSphere, you could also have virtual switches that can connect guests running on multiple hosts and configure advanced switching, such as QoS and traffic shaping.

NETWORK FUNCTION VIRTUALIZATION

When a VM is joined to a virtual switch, the MAC address for its virtual NIC is configured via the hypervisor. The VM must be configured with an appropriate IP address for the subnet it is in. If the VM needs a link to other networks, it must be assigned a default gateway. You might also want to configure security for the network link, such as implementing a firewall. None of the requirements of a virtual network are different than physical networks.

You can configure the VM's IP parameters statically, or you can use DHCP. You could provision a DHCP server as a VM on the virtual network, or the VM could use the physical network's DHCP server. With some types of virtual switches that bridge VMs to the physical network, the hypervisor can implement a DHCP and/or network address translation (NAT) service to VMs.

You must also provision DNS and time synchronization services for the virtual network.

Any guest Linux or Windows Server VM can be configured as a router for a VM network. Similarly, either OS (or third-party software installed under the guest VM) could be used to implement a firewall. The VMs have the same functionality as software installed on real computers.

It is also possible to provision virtual appliances. With a virtual appliance, the vendor either develops a software product that emulates the functions of an existing dedicated hardware appliance (router, firewall, load balancer, or malware/intrusion detection, for instance) or creates software that implements that kind of functionality in a new product. These virtual appliances might be developed against a standard architecture, such as ETSI's Network Function Virtualization (NFV). NFV divides the provisioning of these appliances into three domains:

●	Virtual Network Function (VNF)-Specifies and deploys instances of each virtual appliance. VNFs are designed to run as VMs on standard CPU platforms.

●	NFV infrastructure-Controls the allocation of compute (CPU and memory) plus storage and networking resources to each VNF.

●	Management and orchestration (MANO)-Positions VNFs within workflows to perform the forwarding and filtering tasks they are designed for.

STORAGE AREA NETWORKS

A storage area network (SAN) provisions access to storage devices at block level. Each read or write operation addresses the actual location of data on the media (Block I/O). A SAN is isolated from the main network. It is only accessed by servers, not by client PCs and laptops. SAN clients are servers running databases or applications that require access to shared storage.


Storage area network. (Images © 123RF.com.)

A SAN can integrate different types of storage technology-RAID arrays and tape libraries, for instance. It can contain a mixture of high-speed and low-cost devices, allowing for tiered storage to support different types of file access requirements without having to overprovision high-cost, fast drives.

SAN CONNECTION TYPES

A SAN can be implemented using a variety of technologies, but the most popular are high bandwidth Fibre Channel and Fibre Channel over Ethernet fiber optic networks.

Fibre Channel

Fibre Channel is defined in the T11 ANSI standard. The British spelling "fibre" is deliberately chosen to distinguish the standard from fiber optic cabling, which it often uses but on which it does not rely. A SAN based on a Fibre Channel (FC) Switched Fabric (FC-SW) involves three main types of components:

●	Initiator-This is a client device of the SAN, such as a file or database server installed with a fibre channel host bus adapter (HBA).

●	Target-The network port for a storage device. Typical devices include single drives, RAID drive arrays, tape drives, and tape libraries. Space on the storage devices is divided into logical volumes, each identified by a 64-bit logical unit number (LUN). The initiator will use SCSI, Serial Attached SCSI (SAS), SATA, or NVMe commands to operate the storage devices in the network, depending on which interface they support. Most devices have multiple ports for load balancing and fault tolerance.

●	The initiators and targets are identified by 64-bit WorldWide Names (WWN), similar to network adapter MAC addresses. Collectively, initiators and targets are referred to as nodes. Nodes can be allocated their own WWN, referred to as a WWNN (WorldWide Node Name). Also, each port on a node can have its own WorldWide Port Name (WWPN).

●	FC switch-This provides the interconnections between initiators and targets (a fabric). The switch topology and interconnections would be designed to provide multiple paths between initiators and targets, allowing for fault tolerance and load balancing. High performance FC switches are often referred to as directors.

Fibre Channel can use rates from 1GFC (1 Gbps) up to 128GFC. Using fiber optic cabling, an FC fabric can be up to 10 km (6 miles) in length using single mode cable or 500 m (1640 ft) using multimode cable.

Fibre Channel over Ethernet

Provisioning separate Fibre Channel adapters and cabling is expensive. As its name suggests, Fibre Channel over Ethernet (FCoE) is a means of delivering Fibre Channel packets over Ethernet cabling and switches. FCoE requires special 10/40/100G adapters that combine the function of NIC and HBA, referred to as converged network adapters (CNAs). FCoE uses a special frame type, identified by the EtherType value 0x8096. The protocol maps WWNs onto MAC addresses.

FCoE does not quite run over standard Ethernet. It requires QoS mechanisms to ensure flow control and guaranteed delivery. FCoE compliant products are referred to as lossless Ethernet, Datacenter Ethernet, or Converged Enhanced Ethernet.

ISCSI

Internet Small Computer System Interface (iSCSI) is an IP tunneling protocol that enables the transfer of SCSI data over an IP-based network. iSCSI works with ordinary Ethernet network adapters and switches.

Configuring a Linux host as an iSCSI target.

iSCSI can be used to link SANs but is also seen as an alternative to Fibre Channel itself, as it does not require FC-specific switches or adapters. iSCSI initiator and target functions are supported by both Windows Server and Linux operating systems.

Connecting to an iSCSI target using an iSCSI initiator in Windows Server. (Screenshot used with permission from Microsoft.)

Topic 20C: Explain Datacenter Network Architecture

DATACENTER NETWORK DESIGN

A datacenter is a site that is dedicated to provisioning server resources. The datacenter hosts network services (such as authentication, addressing, and name resolution), application servers, and storage area networks (SANs). Most datacenters are housed in purpose-built facilities, but some of the concepts also apply to server rooms.

A datacenter has dedicated networking, power, climate control, and physical access control features all designed to provide a highly available environment for running critical applications. Unlike a corporate network, a datacenter contains no client PCs, other than hardened secure administrative workstations (SAWs) used solely to manage servers.

Historically, datacenters were designed to use the same three-tiered architecture as an enterprise campus network, with core, distribution, and access layer switches. The changing way that applications are designed as services making use of virtualization and on-demand instances has changed the nature of network traffic flows. These changes are reflected in different topology designs in the datacenter.

Traffic Flows

Traffic that goes to and from a datacenter is referred to as north-south. This traffic represents clients outside the datacenter making requests and receiving responses. Corporate network traffic flows are also typically north-south. A client device is located on a workgroup switch connected to a router, while the server is connected to a separate switch or VLAN. Traffic from the client to the server passes "north" from the client's switch to the router and then back "south" to the server's switch.

In datacenters that support cloud and other Internet services, most traffic is actually between servers within the datacenter. This is referred to as east-west traffic. Consider a client uploading a photograph as part of a social media post. The image file might be checked by an analysis server for policy violations (indecent or copyright images, for instance), a search/indexing service would be updated with the image metadata, the image would be replicated to servers that provision content delivery networks (CDNs), the image would be copied to backup servers, and so on. A single request to the cloud tends to cascade to multiple requests and transfers within the cloud.

Overlay Networks

The preponderance of east-west traffic complicates security design. If each of these cascading transactions were to pass through a firewall or other security appliance, it would create a severe bottleneck. These requirements are driving the creation of virtualized security appliances that can monitor traffic as it passes between servers (blogs.cisco.com/security/trends-in-data-center-security-part-1-traffic-trends). At the same time, security implementations are moving towards zero trust architectures. Zero trust implies a highly segmented network where each link between two servers must be authenticated and authorized.

An overlay network is used to implement this type of point-to-point logical link between two nodes or two networks. The overlay network abstracts the complexity of the underlying physical topology. An overlay network uses encapsulation protocols and software defined networking to create a logical tunnel between two nodes or networks. When used inside the datacenter, overlay networks are typically implemented using virtual extensible LANs (VXLANs).

SOFTWARE DEFINED NETWORKING

Cloud services require the rapid provisioning and deprovisioning of server instances and networks using automation and orchestration, plus the use of overlay networks to establish point-to-point links quickly and reliably. This means that these components must be fully accessible to scripting-representing the ideal of infrastructure as code. Software defined networking (SDN) is a model for how these processes can be used to provision and deprovision networks.

SDN Architecture

In the SDN model defined by IETF (https://datatracker.ietf.org/doc/html/rfc7426), network functions are divided into three layers. The top and bottom layers are application and infrastructure:

●	Application layer-Applies the business logic to make decisions about how traffic should be prioritized and secured and where it should be switched. This layer defines policies such as segmentation, ACLs, and traffic prioritization and policing/shaping.

●	Infrastructure layer-Devices (physical or virtual) that handle the actual forwarding (switching and routing) of traffic and imposition of ACLs and other policy configurations for security.

The principal innovation of SDN is to insert a control layer between the application layer and infrastructure layer. The functions of the control plane are implemented by a virtual device referred to as the SDN controller. Each layer exposes an application programming interface (API) that can be automated by scripts that call functions in the layer above or below. The interface between SDN applications and the SDN controller is described as the service interface or as the "northbound" API, while that between the SDN controller and infrastructure devices is the "southbound" API.

Layers and components in a typical software defined networking architecture. (Images © 123RF.com.)

Management Plane

In IETF's SDN model, there are separate forwarding (data) and operational planes at the infrastructure level. The operational plane implements device state, such as CPU and memory utilization. A management plane sits at the same level as the control plane to interface with the operational plane. This is used to implement monitoring of traffic conditions and network status.

SPINE AND LEAF TOPOLOGY

The spine and leaf topology provides better support for east-west traffic and the use of SDN and overlay networks within datacenters. A spine and leaf topology has two layers:

●	The spine layer comprises a backbone of top-tier switches. Note that while this is described as a backbone, the spine switches are not linked to one another.

●	The leaf layer contains access switches. Each access switch is connected to every spine switch in a full mesh topology. The access switches never have direct connections to one another.

Spine and leaf topology diagram. (Image © 123RF.com.)

The spine and leaf topology has a number of advantages:

●	Each server is only ever a single hop from the backbone, making network latency more predictable.

●	There are multiple redundant paths between a leaf switch and the backbone, allowing for load balancing and failover.

●	As there are no direct connections between spine switches in the backbone or between leaf switches, the network is loop free and does not need to run spanning tree. Instead, each leaf switch runs a protocol called Equal Cost Multipathing (ECMP) to distribute traffic between the links to the spine switches.

●	Servers are connected to multiple leaf switches for multipath redundancy, using a first hop gateway protocol to determine the active path.

The leaf layer access switches are implemented as top-of-rack (ToR) switch models. These are switch models designed to provide high-speed connectivity to a rack of server appliances and support higher bandwidths than ordinary workgroup switches. For example, where a workgroup switch might have 1 Gbps access ports and a 10 Gbps uplink port, top-of-rack switches have 10 Gbps access ports and 40/100 Gbps uplink ports.

DATACENTER ACCESS TYPES

As well as the internal design and configuration of the datacenter, you also need to consider the changing way that datacenter services are accessed. An on-premises datacenter is one that is located at the same site as the corporate client network that it serves. This type of datacenter would be accessed over Ethernet links, but would be placed in a separate network zone with ACLs to filter access by client systems.

Branch Office Datacenter Access

Many corporate networks are traditionally based on a hub and spoke design, where services are concentrated in a main office, or hub, but access is distributed around multiple branch offices in geographically separate locations. Branch offices may be limited in terms of low bandwidth, high latency links. This can mean having to install servers to branch locations and replicate data between them and the head office or corporate network.

The Generic Routing Encapsulation (GRE) protocol encapsulates data from layer 2 (Ethernet) or layer 3 (IP) for tunneling over any suitable transport network. Multipoint GRE (mGRE) is a version of the protocol that supports point-to-multipoint links, such as the hub and spoke dynamic multipoint VPN. This protocol is widely used to connect branch offices to an on-premises datacenter located at the head office.

Colocation

An on-premises datacenter does not have any site redundancy and is also likely to suffer from poor performance when accessed by remote offices in different countries. Establishing on-premises datacenter services for multiple geographic locations is expensive. One option is to use public cloud services where your applications and data are installed to third-party servers. This is cost-effective, but also associated with a number of risks. Colocation means that a company's private servers and network appliances are installed to a datacenter that is shared by multiple tenants. The colocation provider manages the datacenter environment; the company's servers are installed to dedicated rack space on the datacenter floor. The rack or space within a rack is locked so that only authorized keyholders can gain physical access to the server equipment.

MULTIPROTOCOL LABEL SWITCHING

VPN solutions based on mGRE/DMVPN that use the public Internet as the transport network can suffer from unpredictable performance levels. Most WAN providers offer Multiprotocol Label Switching (MPLS) as a means of establishing private links with guaranteed service levels. MPLS can operate as an overlay network to configure point-to-point or point-to-multipoint links between nodes regardless of the underlying physical and data link topologies.

MPLS topology. (Images © 123RF.com.)

For example, in this diagram, the CPE router at site 1 wants to communicate with site 4. The router is attached to the service provider's MPLS cloud via a Label Edge Router (LER). This router inserts or "pushes" a label or "shim" header into each packet sent from CPE1, and then forwards it to an LSR. Each LSR examines the shim and determines the Label Switched Path (LSP) for the packet, based on the type of data, network congestion, and any other traffic engineering parameters determined by the service provider. It uses the label, rather than the Layer 3 header, to forward the packet to its neighbor. In this way, costly routing table lookups are avoided. The shim is removed (or "popped") by the egress LER and delivered to CPE4.

MPLS allows WAN providers to offer various solutions for enterprise networking requirements. A basic use of MPLS is to create site-to-site VPNs to interconnect LANs or connect a branch office to a datacenter. The traffic passing over an MPLS VPN is isolated from any other customer or public traffic. Different sites can use any access method available (DSL, cellular, leased line, or Ethernet), and the sites can use point-to-point or multipoint topologies as required. The MPLS provider can apply traffic shaping policies to communications between enterprise LANs and the datacenter to guarantee a service level and provide link redundancy, making the connection much more reliable than one over the open Internet would be.

SOFTWARE-DEFINED WAN

The hub and branch office design with on-premises datacenters has a number of performance and reliability drawbacks. Shifting services to one or more dedicated datacenters in the cloud or using colocation mitigates some of these issues. Service availability and integrity is separated from site accessibility considerations. In this model access to the datacenter from the corporate network, branch offices, and remote/teleworker locations can be facilitated through a software-defined WAN (SD-WAN). SD-WAN replaces hub and spoke type designs with more efficient, but still secure, connectivity to corporate clouds with less of the expense associated with provisioning an MPLS service to each remote location.

In a branch office topology, access to the datacenter or the cloud would be routed and authorized via the hub office. An SD-WAN is a type of overlay network that provisions a corporate WAN across multiple locations and can facilitate secure access to the cloud directly from a branch office or other remote location. It uses automation and orchestration to provision links dynamically based on application requirements and network congestion, using IPSec to ensure that traffic is tunneled through the underlying transport networks securely. An SD-WAN solution should also apply microsegmentation and zero trust security policies to ensure that all requests and responses are authenticated and authorized.

Components in an SD-WAN solution. (Image © 123RF.com.)

The SD-WAN is managed by a controller and management software located in a corporate datacenter or public cloud. Each site has a SD-WAN capable router, gateway, or VPN app. The SDN controller orchestrates connections to networks and clouds enrolled in the SD-WAN. It uses any available IP underlay network, such as broadband Internet, 4G/5G cellular, or private MPLS VPNs to provision the fastest or most reliable available transport to networks and clouds enrolled in the SD-WAN. The controller also ensures that each access request is authenticated and authorized.