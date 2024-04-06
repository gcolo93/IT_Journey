Lesson 18: Explaining Disaster Recovery and High Availability Concepts

Topic 18A: Explain Disaster Recovery Concepts

HIGH AVAILABILITY

One of the key properties of a resilient system is availability. Availability is the percentage of time that the system is online, measured over a certain period, typically one year. The corollary of availability is downtime; that is, the percentage or amount of time during which the system is unavailable.

High availability is a characteristic of a system that can guarantee a certain level of availability. The Maximum Tolerable Downtime (MTD) metric states the requirement for a business function. Downtime is calculated from the sum of scheduled service intervals (Agreed Service Time) plus unplanned outages over the period. High availability might be implemented as 24x7 (24 hours per day, 7 days per week) or 24x365 (24 hours per day, 365 days per year). For a critical system, availability will be described as two-nines (99%) up to five- or six-nines (99.9999%).

Availability	Annual MTD (hh:mm:ss)

99\.9999%	00:00:32

99\.999%	00:05:15

99\.99%	00:52:34

99\.9%	08:45:36

99%	87:36:00

A system where there is almost no scheduled downtime and outages are extremely rare is also referred to as continuous availability. This sort of availability is required when there is not just a commercial imperative, but a danger of injury or loss of life associated with systems failure. Examples include networks supporting medical devices, air traffic control systems and communications satellites, as well as emerging technologies such as networked autonomous vehicles and new smart city applications, from smart law enforcement systems to smart traffic signaling systems.

The MTD metric sets the upper limit on the amount of recovery time that system and asset owners have to resume operations. Additional metrics can be used to govern recovery operations:

●	Recovery time objective (RTO) is the period following a disaster that an individual IT system may remain offline. This represents the maximum amount of time allowed to identify that there is a problem and then perform recovery (restore from backup or switch in an alternative system, for instance).

●	Work Recovery Time (WRT). Following systems recovery, there may be additional work to reintegrate different systems, restore data from backups, test overall functionality, and brief system users on any changes or different working practices so that the business function is again fully supported.

RTO+WRT must not exceed MTD!

●	Recovery Point Objective (RPO) is the amount of data loss that a system can sustain, measured in time units. That is, if a database is destroyed by a virus, an RPO of 24 hours means that the data can be recovered from a backup copy to a point not more than 24 hours before the database was infected.

Metrics governing mission essential functions. (Images © 123RF.com.)

FAULT TOLERANCE AND REDUNDANCY

A fault is usually defined as an event that causes a service to become unavailable. Each IT system will be supported by assets, such as servers, disk arrays, switches, routers, and so on. Each asset is susceptible to faults. Key Performance Indicators (KPIs) can be used to determine the reliability of each asset and assess whether goals for MTD, RTO, and RPO can be met. Some of the main KPIs relating to component reliability are as follows:

●	Mean Time Between Failures (MTBF) represents the expected lifetime of a product. The calculation for MTBF is the total operational time divided by the number of failures. For example, if you have 10 appliances that run for 50 hours and two of them fail, the MTBF is 250 hours/failure (10\*50)/2.

●	Mean Time to Failure (MTTF) expresses a similar metric for non-repairable components. For example, a hard drive may be described with an MTTF, while a server, which could be repaired by replacing the hard drive, would be described with an MTBF. The calculation for MTTF is the total operational time divided by the number of devices. For example, say two drives were installed in the server in a RAID array. One had failed after 10 years, but had never been replaced, and the second failed after 14 years, bringing down the array and the server. The MTTF of the drives is (10+14)/2 = 12 years.

MTTF/MTBF can be used to determine the amount of asset redundancy a system should have. A redundant system can failover to another asset if there is a fault and continue to operate normally. It can also be used to work out how likely failures are to occur.

●	Mean Time to Repair (MTTR) is a measure of the time taken to correct a fault so that the system is restored to full operation. This can also be described as mean time to replace or recover. MTTR is calculated as the total number of hours of unplanned maintenance divided by the number of failure incidents. This average value can be used to estimate whether a recovery time objective (RTO) is achievable.

A system that can experience failures in individual components and sub-systems and continue to provide the same (or nearly the same) level of service is said to be fault tolerant. Fault tolerance is often achieved by provisioning redundancy for critical components to eliminate single points of failure. A redundant or failover component is one that is not essential to the normal function of a system but that allows the system to recover from the failure of another component. Examples of devices and solutions that provide fault tolerance include the following:

●	Redundant spares-Components such as power supplies, network cards, drives (RAID), and cooling fans provide protection against hardware failures. A fully redundant server configuration is configured with multiple components for each function (power, networking, and storage). A faulty component will then automatically failover to the working one.

●	Network links-If there are multiple paths between switches and routers, these devices can automatically failover to a working path if a cable or network port is damaged.

●	Uninterruptible power supplies (UPSs) and standby power supplies-Provide power protection in the event of complete power failure (blackout) and other types of building power issues.

●	Backup strategies-Provide protection for data.

●	Cluster services-A means of ensuring that the total failure of a server does not disrupt services generally.

RECOVERY SITES

Within the scope of business continuity planning, disaster recovery plans (DRPs) describe the specific procedures to follow to recover a system or site to a working state. A disaster could be anything from a loss of power or failure of a minor component to manmade or natural disasters, such as fires, earthquakes, or acts of terrorism.

Providing redundant devices and spares or network links allows the spare devices to be swapped in if existing systems fail. Enterprise-level networks often also provide for spare sites. A spare site is another location that can provide the same (or similar) level of service. A disaster or systems failure at one site will cause services to failover to the alternate processing site. Disaster recovery planning must demonstrate how this will happen, what checks need to be made to ensure that failover has occurred successfully (without loss of transactional data or service availability), and how to revert to the primary site once functionality is restored there.

Site resiliency is described as hot, warm, or cold:

●	A hot site can failover almost immediately. It generally means that the site is already within the organization's ownership and is ready to deploy. For example, a hot site could consist of a building with operational computer equipment that is kept updated with a live data set.

●	A warm site could be similar, but with the requirement that the latest data set will need to be loaded.

●	A cold site takes longer to set up. A cold site may be an empty building with a lease agreement in place to install whatever equipment is required when necessary.

Clearly, providing redundancy on this scale can be very expensive. Sites are often leased from service providers. However, in the event of a nationwide emergency, demand for the services is likely to exceed supply! Another option is for businesses to enter into reciprocal arrangements to provide mutual support. This is cost effective but complex to plan and set up.

For many companies, the most cost-effective solution is to move processing and data storage to a cloud site. A cloud operator should be able to maintain hot site redundancy so that a disaster in one geographic area will not disrupt service, because the cloud will be supported by a datacenter in a different region.

FACILITIES AND INFRASTRUCTURE SUPPORT

The reliability of an individual site does not solely depend on the IT systems. A site must be provisioned with reliable power and climate conditions.

Heating, Ventilation, Air Conditioning

Environmental controls mitigate the loss of availability through mechanical issues with equipment, such as overheating. Building control systems maintain an optimum working environment for different parts of the building. The acronym HVAC (Heating, Ventilation, Air Conditioning) is often used to describe these services. An HVAC uses temperature sensors and moisture detection sensors (to measure humidity).

Fire Suppression

Health and safety legislation dictates what mechanisms an organization must put in place to detect and suppress fires. Some basic elements of fire safety include:

●	Well-marked fire exits and an emergency evacuation procedure that is tested and practiced regularly.

●	Building design that does not allow fire to spread quickly, by separating different areas with fire-resistant walls and doors.

●	Automatic smoke or fire detection systems, as well as alarms that can be operated manually.

Fire suppression systems work on the basis of the fire triangle. The fire triangle works on the principle that a fire requires heat, oxygen, and fuel to ignite and burn. Removing any one of those elements provides fire suppression (and prevention). In the United States (and most other countries), fires are divided by class under the NFPA (National Fire Protection Association) system, according to the combustible material that fuels the fire. Portable fire extinguishers come in several different types, with each type being designed for fighting a particular class of fire. Notably, Class C extinguishers use gas-based extinguishing and can be used where the risk of electric shock makes other types unsuitable.

Premises may also be fitted with an overhead sprinkler system. Wet-pipe sprinklers work automatically, are triggered by heat, and discharge water. Wet-pipe systems constantly hold water at high pressure, so there is some risk of burst pipes and accidental triggering, as well as the damage that would be caused in the event of an actual fire. There are several alternatives to wet-pipe systems that can minimize damage that may be caused by water flooding the room.

POWER MANAGEMENT

All types of network nodes require a stable power supply to operate. Electrical events, such as voltage spikes or surges, can crash computers and network appliances, while loss of power from brownouts or blackouts will cause equipment to fail. A brownout is where the voltage drops briefly, while a blackout is a complete loss of power lasting seconds or more. Power management means deploying systems to ensure that equipment is protected against these events and that network operations can either continue uninterrupted or be recovered quickly.

Power Distribution Units

The circuits supplying grid power to a rack, network closet, or server room must meet the load capacity of all the installed equipment (plus room for growth). Consequently, circuits to a server room will typically be higher capacity than domestic or office circuits (30 or 60 amps as opposed to 13 amps, for instance). These circuits may be run through a power distribution unit (PDU). A PDU has circuitry to "clean" the power signal, provides protection against spikes, surges, and brownouts, and can integrate with an uninterruptible power supply (UPS).

On a smaller scale, PDUs are also available as "strip" sockets that can take a higher load than a typical 13 amp rated strip. Such sockets are rack mounted and can be oriented horizontally or vertically to allow for different cabling and layout options. PDUs also often support remote power monitoring functions, such as reporting load and status, switching power to a socket on and off, or switching sockets on in a particular sequence.

Battery Backups and Uninterruptible Power Supplies

If there is loss of power, system operation can be sustained for a few minutes or hours (depending on load) using battery backup. Battery backup can be provisioned at the component level for disk drive and RAID array cache. The battery protects any read or write operations cached at the time of power loss.

At the system level, an uninterruptible power supply (UPS) will provide a temporary power source in the event of a blackout. UPS runtime may range from a few minutes for a desktop-rated model to hours for an enterprise system. In its simplest form, a UPS comprises a bank of batteries and their charging circuit plus an inverter to generate AC voltage from the DC voltage supplied by the batteries. Different UPS models support different power outputs and form factors-from desktop to rack mounted depending on your needs.

Generators

The runtime allowed by a UPS should be sufficient to failover to an alternative power source, such as a standby generator. If there is no secondary power source, a UPS will at least allow the administrator to shut down the server or appliance properly-users can save files, and the OS can complete the proper shut down routines.

A backup power generator can provide power to the whole building, often for several days. Most generators use diesel, propane, or natural gas as a fuel source. A UPS is always required to protect against any interruption to computer services. A backup generator cannot be brought online fast enough to respond to a power failure.

Datacenters are also investing in renewable power sources, such as solar, wind, geothermal, hydrogen fuel cells, and hydro. The ability to use renewable power is a strong factor in determining the best site for new datacenters. Large-scale battery solutions, such as Tesla's Powerpack (tesla.com/powerpack), may be able to provide an alternative to backup power generators. There are also emerging technologies to use all the battery resources of a datacenter as a microgrid for power storage (scientificamerican.com/article/how-big-batteries-at-data-centers-could-replace-power-plants).

NETWORK DEVICE BACKUP MANAGEMENT

All business continuity and disaster recovery planning procedures make use of backups. The execution and frequency of backups must be carefully planned and guided by policies. In network management, backup policies are less focused on the data stored on servers and more on swiftly restoring faulty switches, routers, firewalls, and load balancers.

Each device should have a documented baseline configuration. The deployment process should be capable of applying this configuration to a replacement device or when restoring a faulty device.

One complication here is that most network appliances have a startup or persistent configuration and a running configuration. In most cases, these should be the same. It is possible that a configuration oversight left a valid running configuration that was never saved as the startup configuration. Regular audits and other configuration management procedures should be used to detect and remediate running configs that differ from the saved config.

Most devices will also support a version history of previous configurations enabling a change to be rolled back if it causes problems.

An appliance may also support two backup modes:

●	State/bare metal-A snapshot-type image of the whole system. This can be re-deployed to any device of the same make and model as a system restore.

●	Configuration file-A copy of the configuration data in a structured format, such as extensible markup language (XML). This file can be used in a two-stage restore where the OS or firmware image is applied first (or a new appliance provisioned) and then the configuration is restored by importing the backup file.

A network appliance may also hold state information that has not been written to a log and that will not be captured by a backup of the configuration file only. State information includes data such as the MAC tables in switches or the NAT table in a firewall. Advanced firewalls may contain additional data such as malware/intrusion detection signatures. Some devices might log state data to an internal database that can be backed up periodically. In other cases, if this information needs to be preserved, the appliance should be configured to log state data to a remote server, using a protocol such as syslog.

Topic 18B: Explain High Availability Concepts

MULTIPATHING

Multipathing means that a network node has more than one physical link to another node. Multipathing is a default feature of full and partial mesh internetworks, where routers can select alternative paths through the network if a link is not available. Multipathing can be used anywhere that link redundancy is required. Two common additional scenarios are connections to storage area networks (SANs) and Internet access via an Internet Service Provider (ISP):

●	SAN multipathing-In a SAN, a server uses shared storage accessed over a network link. Multipathing means that the server has at least two SAN controllers each with a dedicated link to the storage network.

●	Multiple ISPs-If an organization depends on a single ISP for Internet access, that circuit represents a critical single point of failure. Even if there are multiple circuits to the same ISP, problems within that ISP's routing or DNS infrastructure could result in complete loss of connectivity. Contracting with multiple ISPs and using routing policies to forward traffic over multiple external circuits provides fault tolerance and load balancing. You need to ensure that the ISPs are operating separate infrastructure and not using peering arrangements.

This fault tolerance is reduced if both ISP's links use the same entrance facility. A physical disaster event such as an earthquake or construction damage is likely to affect both sets of cables. Diverse paths refers to provisioning links over separate cable conduits that are physically distant from one another. Another option is to provision cellular links as a backup, although even if 5G technologies are available, this is likely to reduce link bandwidth substantially, and even then, it could be that the 5G backhaul uses some of the same fiber infrastructure as the cabled circuit.

LINK AGGREGATION/NIC TEAMING

Link aggregation means combining two or more separate cabled links between a host and a switch into a single logical channel. From the host end, this can also be called NIC teaming; at the switch end, it can be called port aggregation and is referred to by Cisco as an EtherChannel. The term bonding is also widely substituted for aggregation. For example, a single network adapter and cable segment might support 1 Gbps; bonding this with another adapter and cable segment gives a link of 2 Gbps. Link aggregation can also be used in an uplink between two switches or between a switch and a router or between two routers.

A server node uses NIC teaming to create a 4 Gbps channel link from four 1 Gbps ports to a workgroup switch, while the workgroup switch bonds its uplink transceivers to create a 20 Gbps channel to a router.

Link aggregation can also provide redundancy; if one link is broken, the connection is still maintained by the other. It is also often cost-effective; a four-port Gigabit Ethernet card might not match the bandwidth of a 10 GbE port but will cost less.

This configuration is fully redundant only if the business function does not depend on the full speed of the bonded link. If one port fails, and the link drops to 1 Gbps, but that bandwidth is insufficient, there is not full redundancy.

Link aggregation is typically implemented using the IEEE 802.3ad/802.1ax standard. 802.3ad bonded interfaces are described as a Link Aggregation Group (LAG). 802.3ad also defines the Link Aggregation Control Protocol (LACP), which can be used to detect configuration errors and recover from the failure of one of the physical links.

LOAD BALANCERS

Where NIC teaming allows load balancing at the component level, a load balancer can be deployed as a hardware appliance or software instance to distribute client requests across server nodes in a farm or pool. You can use a load balancer in any situation where you have multiple servers providing the same function. Examples include web servers, front-end email servers, and web conferencing, A/V conferencing, or streaming media servers. The load balancer is placed in front of the server network and distributes requests from the client network or Internet to the application servers. The service address is advertised to clients as a virtual server. This is used to provision services that can scale from light to heavy loads, provision fault tolerant services, and to provide mitigation against distributed denial of service (DDoS) attacks.

Topology of basic load balancing architecture. (Images © 123RF.com.)

There are two main types of load balancers:

●	Layer 4 switch-Basic load balancers make forwarding decisions on IP address and TCP/UDP header values, working at the transport layer of the OSI model.

●	Layer 7 switch (content switch)-As web applications have become more complex, modern load balancers need to be able to make forwarding decisions based on application-level data, such as a request for a particular URL or data types like video or audio streaming. This requires more complex logic, but the processing power of modern appliances is sufficient to deal with this.

We are used to associating switches with Layer 2 (Ethernet), but appliances can perform switch-like forwarding at Layer 3, Layer 4, and Layer 7. These are collectively referred to as multilayer switches.

REDUNDANT HARDWARE/CLUSTERS

Where a load balancer distributes traffic between independent processing nodes, clustering allows multiple redundant processing nodes that share data with one another to accept connections. If one of the nodes in the cluster stops working, connections can failover to a working node. To clients, the cluster appears to be a single server.

Virtual IP

For example, you might want to provision two load balancer appliances so that if one fails, the other can still handle client connections. Unlike load balancing with a single appliance, the public IP used to access the service is shared between the two instances in the cluster. This is referred to as a virtual IP or shared or floating address. The instances are configured with a private connection, on which each is identified by its "real" IP address. This connection runs some type of redundancy protocol, such as Common Address Redundancy Protocol (CARP), that enables the active node to "own" the virtual IP and respond to connections. The redundancy protocol also implements a heartbeat mechanism to allow failover to the passive node if the active one should suffer a fault.

Topology of clustered load balancing architecture. (Images © 123RF.com.)

The same sort of topology can be used to deploy routers and firewalls for high availability and load sharing.

In the previous example, if one node is active, the other is passive. This is referred to as active-passive clustering. The major advantage of active/passive configurations is that performance is not adversely affected during failover. However, the hardware and operating system costs are higher because of the unused capacity.

An active-active cluster means that both nodes are processing connections concurrently. This allows the administrator to use the maximum capacity from the available hardware while all nodes are functional. In the event of a failover the workload of the failed node is immediately and transparently shifted onto the remaining node. At this time, the workload on the remaining nodes is higher and performance is degraded.

In a standard active-passive configuration, each active node must be matched by a passive node. There are N+1 and N+M configurations that provision fewer passive nodes than active nodes, to reduce costs.

FIRST HOP REDUNDANCY

In a full or partial mesh network topology, alternate routes can be found to bypass failed routers or faulty connections. However, end systems are typically served by a single router configured as the default gateway. While it is possible to configure hosts with multiple default gateways for fault tolerance, this does not work well in practice, as it requires a greater degree of complexity in the hosts' routing algorithms than is typically implemented on an end system host.

To address this problem, various types of first hop redundancy protocol (FHRP) have been developed.

Hot Standby Router Protocol

The proprietary Hot Standby Router Protocol (HSRP) developed by Cisco allows multiple physical routers to serve as a single default gateway for a subnet. To do this, each router must have an interface connected to the subnet, with its own unique MAC address and IP address. In addition, they also need to be configured to share a common virtual IP address and a common MAC address. The group of routers configured in this way is known as a standby group. They communicate among themselves using IP multicasts and choose an active router based on priorities configured by an administrator. The active router responds to any traffic sent to the virtual IP address. Of the remaining routers in the standby group, the router with the next highest priority is chosen as the standby router. The standby router monitors the status of the active router and takes over the role if the active router becomes unavailable, also triggering the selection of a new standby router from the remaining routers in the group.

Hot Standby Router Protocol (HSRP) topology. (Image © 123RF.com.)

Cisco also have the Gateway Load Balancing Protocol (GLBP) which allows for an active/active load balanced configuration.

Virtual Router Redundancy Protocol

The open standard protocol Virtual Router Redundancy Protocol (VRRP) is similar to HSRP, the differences mainly being in terminology and packet formats. In VRRP, the active router is known as the master, and all other routers in the group are known as backup routers. There is no specific standby router; instead, all backup routers monitor the status of the master, and in the event of a failure, a new master router is selected from the available backup routers based on priority.

One advantage of VRRP over HSRP is that it does not require each router interface to be assigned a unique IP address. It is possible to configure VRRP routers to use only the virtual IP address. This can be useful on subnets where address space utilization is high.