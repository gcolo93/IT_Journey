**PAN:** Personal Area Network is a network that is centered around a person and their devices. PANs can be used to enable communication between devices, such as a device sending music to speakers or headphones.

**LAN:** A local area network consists of computers connected within a limited area. Most often LANs use Ethernet, Wi-Fi or both to connect the network devices. Many LANs are wireless, where users are connected via Wi-Fi and can move unrestricted throughout the coverage area. This is a popular choice for home users and small businesses, as it is easy and inexpensive to install and allows guests to use the network as well.

**WLAN:** A wireless local area network, is a LAN with wireless connectivity. Unlike LANs, which are wired, WLANs use Wi-Fi to communicate with devices. Users and devices can be placed anywhere and move anywhere in the coverage area. Many WLANs act as a gateway to the internet for users.

**SAN:** A storage area network, is a network that allows access to storage devices specifically instead of more general networking that can be used for any purpose. SANs allow servers to access devices such as tape libraries and disk arrays while presenting them to the operating system like any other locally attached device.

Typically, a SAN is a network dedicated to storage devices and the servers that need access to them. The key reason for this is to reduce interference from normal LAN traffic during data transfer. SANs may also use other protocols, such as Fibre Channels that do not usually operate on traditional network equipment.

**CAN:** A campus area network provides networking of multiple LANs across a limited area, like a university campus or a group of building owned by a company Each LAN would typically be constrained to a singed building, and the CAN would link them together the same way that a WAN does but over a smaller geographic area.

**MAN:** A metropolitan area network provides networking across a larger area than a CAN, but smaller than a WAN,, such as a whole city or the equivalent of a metropolitan area, though it is not necessarily limited by city boundaries.

**WAN:** A wide area network is similar to a LAN except that it covers a large geographical area within its network. The internet is an example of a WAN.

**Client-server:** In a client-server network model, there is a distinct server and a distinct client. The server is the system that stores data and information. The client is the machine that needs access to that data.

**Peer-to-Peer:** In a peper-to-peer model, or P2P, there is no individually designated server or client. Each machine on the network can act as both server and client, sometimes requesting data from other nodes and sometimes answering requests from others. Bitcoin and Tor are examples of P2P networks.

**Bus Topology:** A bus network topology is a single line of devices connected together by one shared network cable. Typically drawn as a single straight line, the network cable is rarely as straight. Often the cable is passed around walls or cubicles so that each computer can be attached to the network.

In a bus topology, computers connect to the network by physically tapping into the network cable using special adapters. This allows the network cable to remain one continuous conduit while also allowing the computers to send and receive electrical signals on the cable.

This leads to an important requirement of bus networks: the ends of the cable must be properly terminated. At both ends of the network cable, special electrical resistors called terminators must be attached to absorb stray electrical signals on the wire. If these terminators are removed or if the network cable is accidentally cut, the electrical signals will not be properly absorbed and will bounce back along the wire, causing communication loss, a condition called signal reflection.

The network in a bus topology is also referred to as a **network segment** because the network may be extended by adding more segments of cable to either end of the network, allowing more computers to connect to the shared network. 

Computers on bus networks communicate in **half-duplex mode**, meaning that you can either send or receive at any given time but cannot send and receive simultaneously. The network cable in a bus topology is a **shared communications medium**, meaning that all computers attached to the network will receive any and all traffic sent on the network.

**Ring Topology:** The ring topology was created to combat one of the more challenging aspects of the bus network: **traffic collisions**. Ring-based protocols such as token ring or fiber distributed data interface (FDDI) allows the network cable to remain a shared medium, but it controls traffic.

The network cable may run in a similar pattern to that of a bus network topology but with some important differences: the network cable is interrupted by each computer on the ring, and the cable is connected back to itself instead of using terminators. In a ring topology, the cable enters a “ring in” port on the network card of the computer and exits a “ring out” port on its way to the next computer in the ring. 

In cases where the network must be highly available, a **dual-ring topology** can be used. In this case, there are two sets of cables, and each computer has two network cards, one for each ring. In the event of a single cable break, the second ring can take over, allowing network traffic to continue to flow. However, the dual-ring topology has its greatest benefit in the event that both rings are simultaneously cut. In this case, the two loose ends on either side of the cable break can be connected together, merging the two broken rings into one much larger, but continuous ring, where traffic can flow. This dual-ring topology is commonly found in fiber optic networks, such as the **synchronous optical network (SONET) ring.**

**Star Topology:** Also known as a **hub-and-spoke network**, is an improvement upon the bus topology. A star network is composed of a central network device such as an Ethernet switch connected to various network devices, such as servers, computers, and printers, by individual network cables.

In a star network, each device is only connected to the central switch. All device-to-device communication is sent through the switch at the center of the network and then forwarded by the switch to the proper destination.

Star networks are the most common type of network found in LAN environments.

One key advantage to this topology is versatility. Instead of running cables from computer to computer, network cables are often run in the walls to a central closet. This gives the network administrator the flexibility to move computers around the office with re-cabling the network. 

The star topology is not only used in LAN environments. It is also used in some forms of WAN, where many remote offices are connected to a central headquarters location. Each remote office then becomes a spoke off the hub of the central headquarters. When a computer in one remote office wishes to communicate with a computer in a different remote office the traffic is passed through the central headquarters network. The star topology eliminates the need for a point-to-point network connection between each remote office.

**Mesh Topology:** The term mesh originates from the interconnected threads in a fabric or a net. Mesh topologies are often drawn as a web of direct connections between computers or nodes in a network. However, those connections may be permanent or constructed dynamically, as nodes need to talk to other nodes. A mesh topology permits nodes to communicate with each other; the topology may be either a full mesh, where every node has access to all other nodes, or a partial mesh network, where each node is only able to connect to a subset of the other nodes.

The nodes may connect using Wi-Fi or radio signals or by virtual links such as VPNs. 

Mesh networks are typically used where communication within a network must be highly available and redundancy is needed. The nodes within a mesh network can communicate with each other, and these connections can be changed dynamically if one node were to fail. This behavior is often referred to as a self-healing network because the nodes in the mesh are aware of each other and can establish new connections around failed nodes as needed.

Architecturally speaking, there are two extremes in networking and computer architecture: centralization and decentralization. In between these extremes, however, are two variants: **client/server and peer-to-peer.** 

**Centralized** **networks** are networks where computing and network power is centralized ina large secure data center where users log on to dumb terminals to access mainframe data and perform tasks.

**Decentralized networks** are networks that rely on the computing power in the user’s device and enable users to operate without a network connection and be portable. Some challenges of decentralization include storage, local security, and differences in operating systems and software.

**Client/Server networks** offload some of the computing requirements from the data center’s servers allowing application designers to implement advanced user interfaces in web or terminal based applications. However, application designers are not the only ones benefiting from client/server architecture.

In a **peer-to-peer network** client computers act as both servers and workstations because they share files and printers while allowing use of the client computer for normal tasks.

Network architecture depends on both wired and wireless connections. Wireless networks are great for portability. The challenge is the signal strength and stability of that wireless signal.

Wired networks are difficult to make portable but have very stable connections, however some wireless technology is faster than wired.

**Virtualization** describes the technique of converting a hardware-based resource into software.

Virtualization relies on a special type of software, known as a hypervisor, which creates the virtual hardware for devices. There are many different varieties of hypervisors, including open source and commercial. Some hypervisors run as standalone applications on Windows, MacOS, or Linux, whereas other hypervisors are installed as the underlying operating system itself. All hypervisors use software to create the illusion of physical hardware.

Each instance of virtual hardware is called a **virtual machine, or VM**.

The operating system (OS) installed within the VM is referred to as a **guest OS** to differentiate it from the operating system of the underlying physical computer, which is called the **host OS.** 

There are two types of hypervisors: Type 1 (bare metal) and Type 2 (hosted). Both types can host VMs; however, they have very different use cases. Type 2 hypervisors look and feel like any other application that you may run on your laptop. Type 1 hypervisors typically require dedicated hardware and are installed as that machine’s operating system, making them more commonly found in data centers than in home networks.

**Type 1 hypervisors,** such as VMware ESXi or the open-source KVM hypervisor, are operating systems that natively run virtual machines and are intended to be installed on a dedicated bare metal server. 

Type 1 hypervisors present very little information to the console screen of the host computer. All administration is typically performed from another computer. You would direct a web browser to the IP address or hostname of the hypervisor to access its web-based administration portal.

A **Type 2 hypervisor**, sometimes referred to as a hosted hypervisor, is installed as an application on personal computers or laptops.