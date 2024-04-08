- **Roles Hosts Play in Networks**
  - Definition of a host as any computing device connected to a network
  - Different roles of hosts: client, server, print server, file server, mail server, etc.
  - Concept of accessing and sharing resources on a network

- **Networking Technologies**
  - Introduction to frames and NICs (Network Interface Controllers)
  - Explanation of MAC (Media Access Control) addresses and their representation
  - Common features of frames including MAC addresses, data, and data checks
  - Overview of Ethernet as the dominant network technology
  - Description of Ethernet frame and its stability over time
  - Ethernet speeds: 10BASE-T, 100BASE-TX, 1000BASE-T, 10GBASE-T
  - Explanation of Ethernet star bus topology
  - Difference between hubs and switches in networking
  - Limitations of Ethernet segments and the impact of splitters
  - Overview of UTP (Unshielded Twisted Pair) cabling, its categories, and markings
  - Introduction to STP (Shielded Twisted Pair) cabling and its applications
  - Description of Ethernet standards and cable requirements for different speeds
  - Explanation of RJ (Registered Jack) connectors, including RJ11 and RJ45

- **Plenum Versus PVC Cabling**
  - Workplace installations often involve cabling running through plenum space, which poses fire hazard concerns due to PVC jacketing emitting noxious fumes when burned.
  - Plenum-grade cable with fire-retardant jackets is essential for plenum spaces, despite being more expensive.
  - ANSI/TIA standards provide two acceptable RJ45 connector standards (T568A and T568B) for UTP cable connections.
  - UTP cables follow ANSI/TIA standardized color codes for wiring.

- **Ethernet with Alternative Connections**
  - Fiber optic cables offer advantages over UTP, including immunity to electrical interference and longer transmission distances.
  - Multimode fiber optic cables are common for shorter connections, while single-mode cables support longer distances and higher transfer rates.
  - Coaxial cables, primarily used for cable modems and satellite connections, come in RG-59 and RG-6 variants with 75-ohm impedance.
  - Coaxial cables use F-type connectors, while BNC connectors are largely obsolete.
  
- **Implementing Ethernet**
  - Ethernet networks typically follow a star bus topology, connecting devices through switches in a central location.
  - LANs consist of computers within close proximity, often forming broadcast domains.
  - LANs can utilize Wi-Fi or Ethernet over Power for connectivity, with the latter providing wired options in challenging environments.
  
- **Structured Cabling**
  - Structured cabling standards, defined by ANSI/TIA, ensure reliable network infrastructure and include telecommunications rooms, horizontal cabling, and work areas.
  - Horizontal cabling runs from work areas to telecommunications rooms and typically consists of solid core UTP cables.
  - Telecommunications rooms house equipment racks for network hardware, patch panels for cable organization, and often require labeling according to ANSI/TIA standards.
  - Patch panels facilitate cable organization and connection to switches through patch cables, which are typically stranded for flexibility.
  - Crimping tools are used to attach RJ45 connectors to UTP cables, with proper steps involving stripping, inserting wires, and crimping followed by testing.
  
These bullet points summarize the key information provided regarding network cabling types, Ethernet alternatives, implementation, and structured cabling standards.

- **The Work Area**
  - A work area serves as the termination point for horizontal network cables, typically featuring wall outlets with one or two female jacks.
  - Wall outlets require Cat-rated jacks to match the cabling in the network, often utilizing modular connectors such as 110 punchdowns.
  - Workstations are connected to wall outlets using patch cables, which feature stranded cabling for durability.
  - Despite its simplicity, the work area is a common source of network failures, often requiring troubleshooting for broken cables.

- **Going Wide**
  - A wide area network (WAN) connects widespread groups of computers using long-distance technologies, typically facilitated by routers.
  - LANs can be connected into a WAN using routers, creating a larger network, such as the Internet.
  - Routing protocols are essential for addressing frames between LANs within the same WAN, ensuring efficient network traffic management.
  - Routers discard broadcast frames by design, preventing network congestion, with broadcasting remaining common within single broadcast domains.
  - TCP/IP is the predominant network protocol for routing and communication between machines in WANs, with further details covered in Chapter 19.