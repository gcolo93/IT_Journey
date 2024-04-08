- **CHAPTER 19: Local Area Networking**
  - Networks are essential in modern computing, with businesses relying on small local networks and larger interconnected networks for survival.
  - This chapter covers the basics of networking technology, including TCP/IP protocol suite, network setup, organization, and troubleshooting.

- **TCP/IP Protocol Suite**
  - TCP/IP is fundamental in modern networks, facilitating communication among devices.
  - Setting up a small network involves planning, installing NICs, configuring switches, and setting up TCP/IP.

- **Organizing Modern Networks**
  - Networks are organized into LANs and WANs, with routers facilitating interconnection between LANs.
  - LANs connect to WANs through routers, with each LAN requiring a router to connect to an ISP.

- **Interconnecting Networks (1101/1102)**
  - Network protocols like TCP/IP enable communication between devices across different networks.
  - IPv4 and IPv6 address schemes are explained, along with subnet masks and CIDR notation.
  - IPv6 extends the IP address space significantly, offering 128-bit addresses compared to IPv4's 32-bit addresses.

- **IPv6 Addressing**
  - IPv6 addresses are written in hexadecimal format, with shorter notations available for ease of use.
  - Link-local addresses are automatically generated and used for local network communication, while global unicast addresses are needed for Internet access.
  - IPv6 prefix lengths determine routing decisions within the network.

- **Domain Name System (DNS)**
  - DNS translates human-readable domain names into IP addresses.
  - DNS servers maintain databases associating IP addresses with names, facilitating Internet navigation.
  - DNS records like A, AAAA, MX, and TXT play roles in addressing and managing e-mail traffic, including spam management.

- **Entering Client IP Information**
    - **IP address**: Your computer's unique address on the network
    - **Subnet mask**: Identifies your network ID
    - **Default gateway**: IP address on the LAN side of your router
    - **DNS server**: Tracks easy-to-remember DNS names for IP addresses
    - Two ways to enter IP information: statically or dynamically
        - Static: Manually input an IP address
        - Dynamic: Uses DHCP to obtain IP address automatically
            - DHCP server manages a range of IP addresses and leases them to devices
            - Lease duration varies, typically lasts about a week
            - DHCP reservation assigns a specific IP address to a device based on its MAC address

- **TCP vs. UDP**
    - TCP: Connection-oriented protocol ensuring reliable data transfer
    - UDP: Connectionless protocol for fast data transfer, suitable for applications like VoIP
    - Application developers choose which protocol to use based on communication requirements

- **TCP/IP Settings**
    - Various settings must be configured correctly for proper network functionality
    - Settings can be accessed and configured through the operating system's network settings interface

- **TCP/IP Tools**
    - Ping: Tests connectivity to another system
    - Ipconfig/Ifconfig/Ip: Displays network configuration information
    - Nslookup/Dig: Retrieves DNS information for a specified host name
    - Tracert/Traceroute: Displays the route a packet takes to reach its destination

- **Installing and Configuring a Wired Network**
    - NIC installation: Connects the computer to the network
    - Full-duplex vs. half-duplex: Modern NICs operate in full-duplex mode
    - Link lights: Indicators of NIC connectivity and activity
    - Wake-on-LAN: Allows waking up a powered-down or sleeping PC remotely
    - QoS: Quality of Service for prioritizing network traffic

- **Automatic Private IP Addressing**
    - APIPA automatically assigns an IP address when DHCP is unavailable
    - Uses the address range 169.254.0.1 to 169.254.255.254

- **Network Organization and Access Control**
    - Shared resources: Files, folders, printers, etc., can be shared over a network
    - Permissions control access to shared resources
    - NTFS permissions complement network share permissions for shared folders on NTFS drives

- **Connecting to a Switch**
    - Computers connect to switches for network communication
    - Two types of switches: unmanaged and managed
    - Managed switches offer additional features and are accessed via IP address for configuration

- **Organizing with Workgroups**
  - Workgroups or domains are used to organize Windows networks.
  - Workgroups are simpler and older, suitable for smaller networks.
  - Default workgroup name in Windows is WORKGROUP.
  - Workgroup name can be changed in system settings.
  - Workgroups lack centralized control, suitable for smaller networks.
- **Usernames and Passwords**
  - Users log in with a username and password for authentication.
  - Usernames and passwords are stored encrypted on the computer.
  - Used to access shared resources on the network.
- **Sharing Folders with the Sharing Wizard**
  - Sharing folders is easy using the Sharing Wizard in Windows.
  - Different permission levels (Read, Read/Write, Owner) can be set.
  - Advanced Sharing provides more control over access permissions.
- **Accessing Shared Folders with Workgroups**
  - Accessing shared folders requires a valid username and password.
  - Users need to know the username and password of the computer sharing the folder.
  - Options for sharing include individual logins, identical accounts on all computers, or a single account for all.
- **Organizing with Domains**
  - Windows domains centralize user accounts, passwords, and resource access.
  - Single sign-on (SSO) allows access to all machines on the domain with one account.
  - Active Directory is used to manage domain information.
  - Requires a server running Windows Server or Linux with Samba.
  - PCs on the network need to join the domain.
- **Domain Organization**
  - Active Directory stores information about the network.
  - Active Directory Users and Computers utility provides basic functions.
  - Organizational units within the domain organize resources such as users, computers, and groups.

- **Domain Administration**
  - Domain administrators manage the domain, similar to how individual systems have administrators.
  - They have powerful privileges, such as adding and removing computers and users from the domain.
  - Joining a computer to a domain involves accessing Control Panel, System and Security, and then changing settings under Computer name, domain, and workgroup settings.
  - Removing a system from a domain requires accessing the domain controller, going into Active Directory Users and Computers, and removing the computer from the domain.
  - Creation of domain accounts is done by domain administrators using Active Directory Users and Computers.
  - Active Directory Users and Computers utility is used by domain administrators to manage user accounts, including resetting passwords and enabling/disabling accounts.
  - Domain accounts offer features like logon scripts for automated tasks and roaming profiles for consistent user experience across systems.
  - Organizational Units (OUs) in Active Directory help in flexible organization of users and computers based on various criteria.

- **File Servers and Drive Mapping**
  - Dedicated file servers are preferred when many users require round-the-clock access to important files.
  - Mapping network drives in Windows involves opening File Explorer, selecting Map network drive, choosing the drive letter and folder, and configuring options.
  - In an Active Directory domain, network shares may be automatically mapped by Group Policy or login scripts.

- **Sharing Printers**
  - Sharing printers in Windows involves accessing Devices and Printers settings, selecting Printer properties, and then configuring sharing options.

- **Troubleshooting Networks**
  - Troubleshooting network issues involves diagnosing physical cabling problems, repairing physical cabling, and fixing common problems like failure to connect to resources.
  - Tools like toners are used for tracing cables, and commands like net and nbtstat are used for network diagnostics.