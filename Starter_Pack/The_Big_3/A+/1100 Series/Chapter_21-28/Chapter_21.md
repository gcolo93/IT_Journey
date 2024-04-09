- **CHAPTER 21: The Internet**
    - **Historical/Conceptual**
        - How the Internet Works
            - Communication process between computers
            - Organization of the Internet as a network of networks
            - Backbone routers and their role in connecting networks
            - Decentralized and redundant nature of the Internet
        - TCP/IP: The Common Language of the Internet
            - Overview of TCP/IP protocols
            - Adaptability and extensibility of TCP/IP
            - Addressing scheme provided by TCP/IP (IPv4 and IPv6)
    - **Internet Service Providers**
        - Role of Internet service providers (ISPs) in providing access to the Internet
        - Various sizes and capabilities of ISPs
        - Connection Concepts
            - Hardware and software requirements for connecting to an ISP
            - DHCP server configuration for TCP/IP information
            - Role of default gateway in connecting to an ISP
    - **Connecting to the Internet**
        - Overview of different connection types:
            - DSL
            - Cable
            - Fiber
            - Wi-Fi
            - WISP
            - Cellular
            - Satellite
        - Installation process and equipment required for each connection type
    - **Connection to the Internet**
        - Connecting a single computer or network of computers to an Internet connection
        - Basic router configuration steps:
            - UPnP (Universal Plug and Play) settings
            - Changing default credentials for router access
            - Setting static IP addresses
            - Updating firmware for router maintenance and security
    - **Using the Internet**
        - Overview of applications required for various tasks:
            - Web browsing
            - Email communication
            - Real-time communication applications
            - Streaming video services
        - Use of application protocols for communication with servers
        - Overview of application protocols commonly encountered on the Internet

- **Internet Application Protocols:**
  - Application developers often use well-known protocols for communication between applications and servers.
  - Examples include HTTP, POP3, IMAP, SMTP, Telnet, SSH, FTP/SFTP, RDP, and VoIP (SIP).
  - Each protocol has its own rules and port numbers.
  - HTTPS is commonly used for secure communication over the web, identifiable by the protocol and port 443.

- **Utility Protocols:**
  - These are hidden application protocols that perform essential tasks behind the scenes.
  - Examples include DNS, DHCP, and others.
  - They ensure the smooth functioning of visible application protocols.

- **Browsing the Web:**
  - Web browsers use protocols like HTTP and HTTPS to interact with web servers.
  - Browsers such as Mozilla Firefox, Google Chrome, Microsoft Edge, and Apple Safari are commonly used.
  - Extensions and plugins enhance browser functionality, but users should be cautious about installing them from untrusted sources.

- **Password Managers:**
  - Password managers help users store and manage passwords securely.
  - They can identify weak passwords and provide features for generating strong passwords.

- **Secure Connections and Sites:**
  - Secure connections between browsers and servers are established using encryption and certificates.
  - Browser warnings indicate potential security risks, and users should avoid ignoring them.

- **Pop-up and Ad Blockers:**
  - These tools help users avoid unwanted pop-ups and advertisements while browsing.
  - Users should be aware of allowing pop-ups for legitimate uses like online stores or browser-based games.

- **Browsing Data:**
  - Browsers accumulate various types of data, including history, cookies, settings, and cached resources.
  - Clearing browsing data can improve performance and address privacy concerns.

- **Configuring Web Browsers:**
  - Browsers offer settings menus for customization, including options for privacy, security, and content control.
  - Internet Options in Windows provides additional settings for Internet Explorer and Microsoft Edge.

- **Communicating with Others:**
  - Email and VoIP are common methods of online communication.
  - Email protocols include POP3, IMAP, and SMTP, while VoIP uses SIP.
  - Users can access email through dedicated applications, web-based clients, or integrated solutions like iCloud or Microsoft accounts.

- **Voice over IP (VoIP)**
  - Enables voice calls over computer networks
  - Utilizes high-speed Internet connections
  - Collection of protocols, including SIP
  - Offered by various vendors like Skype, Cisco, Vonage, etc.
  - Can replace traditional copper phone lines
  - Setup options: dedicated VoIP phones or adapters for analog phones

- **Remote Access**
  - Telnet and SSH for remote command-line access
  - Secure Shell (SSH) as a secure alternative to Telnet
  - Remote Desktop applications for full graphical desktop access
  - Microsoft Remote Assistance for remote troubleshooting and support

- **Video-Conferencing Software**
  - Enables sharing of windows or entire desktops during calls
  - Allows giving control of the desktop to another user for troubleshooting

- **Virtual Private Networks (VPNs)**
  - Secure connections over the Internet through encrypted tunnels
  - Requires endpoints for encryption and decryption
  - Allows remote systems to appear as if they're on the local network

- **File Transfer Software**
  - Enables sharing, synchronizing, and transferring files among users or devices
  - Examples include Dropbox, iCloud, Google Drive, OneDrive
  - Requires client applications for synchronization

- **Desktop Management Software**
  - Provides comprehensive management tools for device configuration, software updates, security policies, etc.
  - Also known as endpoint management software

- **Remote Monitoring and Management (RMM)**
  - Adds monitoring and management of network devices and servers to desktop management capabilities

- **Sharing and Transferring Files**
  - File Transfer Protocol (FTP) for transferring files between client systems and servers
  - Trivial FTP (TFTP) for simple file transfer needs
  - Secure FTP (SFTP) for encrypted file transfer over SSH connections

- **Embedded Systems**
  - Computers built into various devices such as appliances, cars, medical equipment, etc.
  - Evolving into networked smart devices with increased capabilities and challenges

- **Industrial Control Systems**
  - Factories have evolved from human-powered to fully automated systems driven by industrial control systems (ICSs).
  - Supervisory control and data acquisition (SCADA) systems manage processes spread out over wide areas and ensure safe operation.
  - Security is crucial for ICSs due to the potential risks of monitoring and controlling dangerous processes.
  
- **The Internet of Things (IoT)**
  - IoT devices actively use the internet for various operations like reporting, transactions, and updates.
  - Examples of IoT devices include thermostats, security cameras, and smart speakers.
  - Security risks exist with network-accessible embedded systems and IoT devices, especially legacy systems.
  
- **Internet Troubleshooting**
  - **No Connectivity**
    - Check local connectivity and DNS settings for issues.
    - Flush DNS cache or try using alternative DNS servers to resolve DNS failures.
  - **Limited Connectivity**
    - Investigate DHCP server issues and consider setting up a static IP address if necessary.
  - **Local Connectivity**
    - Ping the default gateway and WAN port on the router to identify network issues.
    - Troubleshoot DHCP server problems and consider router restart or ISP assistance if needed.
  - **Slow Network Speeds**
    - Distribute bandwidth effectively using Quality of Service (QoS) settings on the router.
  - **Latency and Jitter**
    - Use tools like ping, tracert, and pathping to assess latency and jitter issues.
    - High latency and jitter can affect real-time applications like VoIP and video conferencing.
  
- **Poor VoIP Call Quality**
  - Check call statistics on the VoIP provider's dashboard for signs of trouble.
  - Investigate issues such as delays, choppy audio, or low audio quality.
  - Consider factors like network congestion, bandwidth, and QoS settings to improve call quality.