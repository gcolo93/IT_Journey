The **TCP/IP and OSI models** describe a set of procedures that sends data from one host to another.

**TCP/IP** - Transmission Control Protocol and Internet Protocol - 4 Layer Model: Application > Transport > Network > Network Interface

**OSI** - Open Systems Interconnection - 7 Layer Model: Application > Presentation > Session > Transport > Network > Data Link > Physical

**TCP/IP**

- **Application Layer:** This layer is responsible for the communication protocols between nodes. The protocols in this layer include hypertext transfer protocol (HTTP and HTTPS), Secure Shell (SSH), and network time protocol (NTP), among many others.
- **Transport Layer:** This layer is responsible for the end-to-end transport of data. The protocols that live in this layer are transmission protocol (TCP) and user datagram protocol (UDP).
- **Network Layer:** This layer defines the logical transmission protocols for the whole network. The main protocols that live in this layer are internet protocol (IP), internet control message protocol (ICMP), and address resolution protocol (ARP).
- **Network Interface Layer:** This layer establishes how data should be physically sent through the network.

**OSI Model**

- **Physical Layer:** This layer is responsible for the physical connections of the devices in the network. This layer is implemented through the use of devices such as hubs, repeaters, modem devices, and physical cabling.
- **Data Link Layer:** This layer is responsible for the error-free delivery of data to the receiving device or node. This layer is implemented through the use of devices such as switches and bridge devices, as well as anything with a network interface, like wireless or wired network cards.
- **Network Layer:** This layer is responsible for the transmission of data between hosts in different networks as well as routing of data packets. This layer is implemented through the use of devices such as routers and some switches.
- **Transport Layer:** This layer provides services to the application layer and receives services from the network layer. It is responsible for the reliable delivery of data. It segments and reassembles data in the correct order for it to be sent to the receiving device. It may also handle the reliable delivery of data and any retries of data that are lost or corrupted (for example, TCP does this). This layer is often called the heart of OSI.
- **Session Layer:** This layer is responsible for connection establishment, session maintenance, and authentication.
- **Presentation Layer:** This layer is responsible for translating data from the application layer into the format required to transmit the data over the network as well as encrypting the data for security if encryption is used.
- **Application Layer:** This layer is responsible for network applications (like HTTP or FTP) and their production of data to be transferred over the network.