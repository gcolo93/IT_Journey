**Cloud Models 4.1**

**Infrastructure as a service (IaaS)**

- Sometimes called Hardware as a Service (HaaS)
  - Outsource your equipment
- You’re still responsible for the management
  - And for the security
- Your data is out there, but more within your control
- Web server providers

**Software as a Service (SaaS)**

- On-demand software
  - No local installation
  - Why manage your own email distribution? Or payroll?
- Central management of data and applications
  - You data is out there
- A complete application offering
  - No development work required
  - Google Mail

**Platform as a Service (PaaS)**

- No servers, no software, no maintenance team no HVAC
  - Someone else handles the platform, you handle the development
- You don’t have direct control of the data, people, or infrastructure
  - Trained security professionals are watching your stuff
    - Choose carefully
- Put the building blocks together
  - Develop your app from what’s available on the platform
  - SalesForce.com

**Cloud deployment models**

- Private
  - Your own virtualized local data center
- Public
  - Available to everyone over the Internet
- Hybrid
  - A mix of public and private
- Community
  - Several organizations share the same resources

**Shared resources**

- Internal cloud
  - No resources are shared
  - Build your own cloud
  - Pay for everything up front
  - No ongoing costs
- External Cloud
  - Share resources with a public cloud
  - Underlying infrastructure owned by a third-party
  - Cost may be metered or up-front

**Metered and non-metered**

- Metered cloud services
  - You pay for what you use
  - Cost to upload
  - Cost to store
  - Cost to download
- Non-metered
  - You pay for a block of storage
  - No cost to upload
  - No cost to download

**Cloud computing characteristics**

- Rapid elasticity
  - Scale up and scale down as needed
  - Seamless to everyone
- On-demand self service
  - Adding software, networks, servers,  storage is a challenge outside the cloud
  - The cloud enables instant resource provisioning


**Cloud computing characteristics**

- Resource pooling
  - All of the computing power in one place
  - One large resource instead of many small resources
- Measured service
  - Costs and utilization are very closely tracked
  - Resource planning and granular chargebacks

**Cloud Services 4.1**

**Off-site email applications**

- Email is a staple
  - Detailed electronic communication
- A challenge to maintain
  - Expensive hardware and storage
  - Trained support team
  - Ongoing backup and maintenance
- Cloud-based email hosting
  - Flat cost per user per month
  - Personal options may have no direct cost
  - Looks and feels the same for the user
- Microsoft Office 365, Google Mail

**Cloud file storage services**

- Store your files in the cloud
  - Access, share, and edit from anywhere
- Easy to collaborate
  - One place for all files
- Synchronization app
  - Store files on a local drive
  - The app synchronizes to the cloud
  - Sync files to other devices
- Cloud storage providers
  - Dropbox, Google Drive, Box, Microsoft OneDrive

**Virtual application streaming**

- On-demand applications
  - No local installation
  - Globally distributed
- User starts the application
  - The components are downloaded as needed
  - If you don’t use a component, you don’t download
  - User data is stored securely in the cloud
- Easy to update
  - The application is in one place
  - Some data is cached, only update the changes

**Application streaming**

- Mobile phones / tablets
  - Run an app (or portion of an app) in real-time
  - Try many different apps or components
  - Can be cached locally for later use
- Applications for laptop/desktops
  - No complex deployment process
  - Apps are only streamed if they are used
  - New applications are simply added to the cloud offering
  - Quickly manage and make changes

**Cloud-hosted virtual desktops**

- A virtual desktop infrastructure (VDI) in the cloud
  - Users connect to a pre-built desktop
- Access from almost any OS
  - Windows, Mac OS, Linux, iOS, Chromebook, web browser
- Virtual NIC
  - All communication in the desktop are local to the virtual desktop
  - No sensitive information sent from the local device

**Client-side Virtualization 4.2**

**Virtualization**

- One computer, many operating systems
  - Mac OS X, Windows 7, Linux Ubuntu, all at the same time
- Separate OS, independent CPU, memory, network, etc.
  - But really one computer
- Host-based virtualization
  - Your normal desktop plus others
- Standalone server that hosts virtual machines
  - Enterprise-level
- Been around since 1967
  - IBM mainframe virtualization

**The hypervisor**

- Virtual Machine Manager
  - Manages the virtual platform and guest operating systems
- May require a CPU that supports virtualization
  - Can improve performance
- Hardware management
  - CPU
  - Networking
  - Security

**Resource requirements**

- CPU Processor Support
  - Intel: Virtualization Technology (VT)
  - AMD: AMD-V
- Memory
  - Above and beyond host OS requirements
- Disk space
  - Each guest OS has its own image
- Network
  - Configurable on each guest OS (standalone, NAT, bridged, etc.)
  - Virtual switch

**Emulation vs. Virtualization**

- Virtualization is a native operating system
  - Performing native OS processes
  - This is identical to using a non-virtual system
- Emulation is one device running processes designed for a completely different architecture
  - One device is pretending to be another
  - Original code is used
  - Code is interpreted for running on the current hardware
  - This is commonly slower than running natively
  - Emulation is not easy to do

**Hypervisor Security**

- Hypervisor is a sweet spot for the bad guys
  - No significant vulnerabilities yet
- VM escaping
  - Malware recognizes it’s on a virtual machine
  - Malware compromises the hypervisor
  - Malware jumps from one guest OS to another
- Many hosted services are virtual environments
  - Malware on one customer’s server can gather information from another.

**Guest operating system security**

- Every guest is self-contained
  - Like a real computer
- Use traditional security controls
  - Host-based firewall
  - Anti-virus, anti-spyware
- Watch out for rogue virtual machines (VMs)
  - The bad guys try to install their own system
    - You’re in big trouble
- Self-contained VMs provided by 3rd parties can be dangerous
  - You have no idea what’s running on there

**Network requirements**

- Most client-side virtual machine managers have their own virtual (internal) networks
- Shared network address
  - The virtual machine shares the same IP address as the physical host.
  - Uses a private IP address internally
  - Uses NAT to convert to the physical host IP
- Bridge network address
  - The VM is a device on the physical network
- Private address
  - The VM does not communicate outside of the virtual network
