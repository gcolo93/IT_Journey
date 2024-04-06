**Copper Network Cables 3.1**

**The importance of cable**

- Fundamental to network communication
  - Incredibly important foundation
- Usually only get one good opportunity at building your cabling infrastructure
  - Make it good
- The vast majority of wireless communication uses cables
  - It has to plug in somewhere

**Twisted pair copper cabling**

- Balanced pair operation
  - Two wires with equal and opposite signals
  - Transmit+, Transmit-, / Receive+, Receive-
- The twist is the secret
  - Keeps a single wire constantly moving away from the interference
  - The opposite signals are compared on the other end
- Pairs in the same cable have different twist rates

**Network cabling standards**

- Electronic Industries Alliance (EIA)
  - Alliance of trade associations, develops standards for the industry
    - Standards start with RS-# (Recommended Standard) or EIA-#
    - <http://www.eia.org>
- Telecommunications Industry Association (TIA)
  - Standards, market analysis, trade shows, government affairs, etc.
    - ANSI/TIA/EIA-568 - Commercial Building Telecommunications Cabling Standard
  - <http://www.tiaonline.org>
- International ISO/IEC 11801 cabling standards
  - Defines classes of networking standards

**Copper cable categories**

- Category 3
  - Maximum Supported Ethernet Standard: 10BASE-T
  - Maximum Supported Distance 100 meters
- Category 5
  - Maximum Supported Ethernet Standard: 100BASE-TX, 1000BASE-T
  - Maximum Supported Distance 100 meters
- Category 5e (enhanced)
  - Maximum Supported Ethernet Standard: 100BASE-TX, 1000BASE-T
  - Maximum Supported Distance 100 meters
- Category 6
  - Maximum Supported Ethernet Standard: 10GBASE-T
  - Maximum Supported Distance 37-55 meters
- Category 6A (augmented)
  - Maximum Supported Ethernet Standard: 10GBASE-T
  - Maximum Supported Distance 100 meters

**No Plenum**

**Plenum**

- Plenum space
  - Building air circulation
  - Heating and air conditioning system
- Concerns in the case of a fire
  - Smoke and toxic fumes
- Worst-case planning
  - Important concerns for any structure

**Plenum-rated cable**

- Traditional cable jacket
  - Polyvinyl chloride (PVC)
- Fire-rated cable jacket
  - Fluorinated ethylene polymer (FEP) or low-smoke polyvinyl chloride (PVC)
- Plenum-rated cable may not be as flexible
  - May not have the same bend radius
- Worst case planning
  - Important concerns for any structure

**Unshielded and shielded cable**

- UTP (Unshielded Twisted Pair)
  - No additional shielding
  - The most common twisted pair cabling
- STP (Shielded Twisted Pair)
  - Additional shielding protects against interference
  - Shield each pair and/or the overall cable
  - Requires the cable to be grounded
- Abbreviations
  - U = Unshielded
  - S = Braided shielding
  - F = Foil shielding
- (Overall cable) / (individual pairs)TP
  - Braided shielding around the entire cable and foil around the pairs is S/FTP
  - Foil around the cable and no shielding around the pairs is F/UTP

**T568A and T568B termination**

- Pin assignments from EIA/TIA-568-B standard
  - Eight conductor 100-ohm balanced twisted-pair cabling standard
- T568A and T568B are different pin assignments for 8P8C (8 Position 8 conductor) connectors
  - Assigns the T568A pin-out to horizontal cabling
- Many organizations traditionally use 568B
  - Difficult to change in mid-stream
- You can’t terminate one side of the cable with 568A and the other with 568B
  - You’ll run into problems

**TIA/EIA 568A**

- Pin 1: White and Green
- Pin 2: Green
- Pin 3: White and Orange
- Pin 4: Blue
- Pin 5: White and Blue
- Pin 6: Orange
- Pin 7: White and Brown
- Pin 8: Brown

**TIA/EIA 568B**

- Pin 1: White and Orange
- Pin 2: Orange
- Pin 3: White and Green
- Pin 4: Blue
- Pin 5: White and Blue
- Pin 6: Green
- Pin 7: White and Brown
- Pin 8: Brown

**Coaxial cables**

- Two or more forms share a common axis
- RG-6 used in television/digital cable
  - And high-speed Internet over cable
- RG-59 used as patch cables
  - Not designed for long distances
- Plastic jacket
- Metal shielding
- Dielectric insulator
- Wire conductor

**Fiber Network Cables 3.1**

**Optical fiber communication**

- Transmission by light
  - The visible spectrum
- No RF signal
  - Very difficult to monitor or tap
- Signal slow to degrade
  - Transmission over long distances
- Immune to radio or electrical interference
  - There’s no RF

**Multimode fiber**

- Short-range communication
  - 2 kilometers for 100 Mbit/sec
  - 550 meters for 10 Gbit/sec
- Inexpensive light source
  - i.e., LED

**Single-mode fiber**

- Long-range communication
  - Over 80 km without additional processing
- Expensive light sources
  - Laser beams






**Video Cables 3.1**

**VGA (Video Graphics Array)**

- DB-15 connector
  - More accurately called DE-15
- Blue color
  - PC System Design Guide
- Analog signal
  - No digital
  - Image degrades after 5 to 10 meters

**HDMI (High-Definition Multimedia Interface)**

- Video and audio stream
  - All digital, no analog
  - 20 meter distances before losing too much signal
- 19-pin (Type A) connector
  - Proprietary connector
- miniHDMI
  - Type C connector
  - Designed for smaller devices

**DisplayPort**

- VESA standard
  - Video Electronics Standards Association
  - A royalty-free standard
- Data is sent in packetized form
  - Like Ethernet and PCI Express
- Compatible with HDMI and DVI
  - Passive adapter
- DisplayPort and Mini DisplayPort

**DVI (Digital Visual Interface)**

- Single and dual link
  - Single link; 3.7 Gbps (HDTV at 60 fps)
  - Dual link; 74 Gbps (HDTV at 85 fps)
- DVI-A
  - Analog signals
- DVI-D
  - Digital signals
- DVI-I
  - Integrated
  - Digital and analog in the same connector


**Multipurpose Cables 3.1**

**Lightning**

- Apple proprietary
  - 8-pin digital signals
  - iPhone, iPad, iPod devices
- Some advantages over Micro-USB
  - Higher power output for phones and tablets
  - Can be inserted either way
  - Simpler design, more durable

**Thunderbolt**

- High-speed serial connector
  - Data and power on the same cable
  - Based on Mini DisplayPort (MDP) standard
- Thunderbolt v1
  - Two channels
  - 10 Gbit/s per channel
  - 20 Gbit/s total throughput
  - Mini DisplayPort connector
- Thunderbolt v2
  - 20 Gbit/s aggregated channels
  - Mini DisplayPort connector
- Thunderbolt v3
  - 40 Gbit/s aggregated throughput
  - USB-C connector
- Maximum 3 meters (copper)
  - 60 meters (optical)
  - Daisy-chain up to 6 devices

**USB (Universal Serial Bus)**

- Simplify connections
  - Printers, storage devices, keyboard, mouse
- USB 1.1
  - Low speed: 1.5 megabits per second, 3 meters
  - Full speed: 12 megabits per second, 5 meters
- USB 2.0
  - 480 megabits per second, 5 meters
- USB 3.0
  - SuperSpeed
  - 5 gigabits per second, 3 meters
  - Standard does not specify a cable length
- USB 3.1
  - Released July 2013
  - SuperSpeed+
  - Type-A and USB-C connectors
  - 10 Gbit/sec - Twice the rate of USB 3.0
- USB 3.2
  - Released September 2017
  - New SuperSpeed+ modes over USB-C
  - 10 Gbit/sec and 20 Gbit/sec

**USB-C**

- USB has a lot of different connectors
  - And they have changed over time
- Can be annoying to connect USB-A
- USB-C replaces all of these
- USB-C isn’t necessarily USB 3.1
  - The cable must support the function
    - USB 3.1 speeds
    - Power delivery (>7.5 watts)
    - Alternate mode (additional data wires)

**DB-9 serial cable connector**

- D-subminiature or D-sub
  - Different sizes, A through E
- Commonly used for RS-232
  - Recommended standard 232
  - An industry standard since 1969
- Serial communications standard
  - Built for modem communication
    - Used for modems, printers, mice, networking
- Commonly used as a configuration port
  - Serial console interface

**SATA Drive Cables 3.1**

**SATA (Serial AT Attachment)**

- SATA Revision 1.0
  - SATA 1.5 Gbit/s, 1 meter
- SATA Revision 2.0
  - SATA 3.O Gbit/s, 1 meter
- SATA Revision 3.0
  - SATA 6.0 Gbit/s, 1 meter
- SATA Revision 3.2
  - SATA 16 Gbit/s, 1 meter


**PATA Drive Cables 3.1**

**The PATA Standard**

- Parallel AT Attachment, Parallel ATA, ATA
  - Remember the PC/AT?
- An evolutionary process
  - Circa 1999
- Originally called Integrated Drive Electronics (IDE)
  - A Western Digital invention
  - 2nd generation called EIDE (Enhanced IDE)
- The evolution
  - Promised faster speeds (from 16 MB/s through 133 MB/s)
  - Additional devices (CD-ROM drive, etc.)
- Now called Parallel ATA (PATA)

**SCSI Drive Cables 3.1**

**The SCSI Standard**

- Small Computer Systems Interface
  - Not really “small” any longer
- Originally designed to string many peripherals together onto a single cable/controller
  - Up to 16 devices in a SCSI “chain”
- Many different formats
  - Fast SCSI, Ultra SCSI, Ultra Wide SCSI, Ultra2 SCSI, Ultra3 SCSI, Ultra-320 SCSI, Ultra-640 SCSI, iSCSI (SCSI over IP)
- Parallel and serial options

**SCSI advantages**

- Not just for hard drives
  - Scanners, tape drives, CD-ROM drives
- Many devices on a single bus
  - 8 on narrow bus, 16 on wide bus
- Very intelligent interface functionality
  - Much of the difficult configuration work is done between the SCSI devices
- Industry longevity
  - Well supported in the enterprise
  - A standard drive for virtual systems

**SCSI ID and logical unit (LUN)**

- Every SCSI device on a single bus is assigned a separate ID number
  - SCSI ID 0 (SCSI controller), ID 2 (hard drive), ID 3 (CD-ROM)
- Logical units (LUNs) are defined within each SCSI ID
  - Separate drives in a storage array or virtual machine
- The signal at the “end” of a physical SCSI bus is terminated
  - Can be internal to the device or a separate termination device
- Serial attached SCSI (SAS) devices have no jumpers, terminators, or settings

**Serial attached SCSI**

- Move from parallel to serial
  - Increased throughput
  - Similar to the move from PATA to SATA
- Point-to-point connection
  - No more daisy chains
- No termination required
  - The bus has two devices on it
- The control and management of SCSI
  - The speed of a serial connection

**Adapters and Converters 3.1**

**Adapters and converters**

- The best laid plans…
  - Need an adapter
- Convert between different connectors
  - Electrically compatible
- Convert from one format to another
  - You need Ethernet but you only have USB
- A good temporary fix
  - Or a good permanent one

**DVI to HDMI**

- DVI-D and HDMI are electrically compatible
  - HDMI is backward-compatible with DVI-D
  - No signal conversion required
  - No loss of video quality

**DVI to VGA**

- DVI-A includes analog signals
  - Backward compatible with VGA
  - Only 640 x 480 is officially supported
- May only need an adapter
  - Analog to analog
- VGA to DVI digital converter
  - Check your interface specifications



**USB to Ethernet**

- Some laptops don’t have a wired Ethernet interface
  - Coverts USB to Ethernet

**Connectors 3.2**

**RJ11 connector**

- 6 position, 2 conductor (6P2C)
  - RJ14 uses 6P4C for dual-line use
- Telephone connection

**RJ45 connector**

- 8 position, 8 conductor (8P8C)
  - Modular connector
- Similar in shape to an RJ48C
  - 8P4C, used with T1/WAN data lines

**RS-232**

- Recommended Standard 232
  - An industry standard since 1969
- Serial communications standard
  - Built for modem communication
    - Used for modems, printers, mice, networking
- Commonly used as a configuration port
  - Serial console interface

**BNC connection**

- Bayonet Neill-Concelman
  - Paul Neill (Bell Labs) and Carl Concelman (Amphenol)
- Coaxial cable connector
  - DS3 WAN links
- Rigid and bulky
  - Can be difficult to work with

**F-connector**

- Cable television
  - Cable modem
- RG-6 or RG-59 cable
  - Threaded connector

**USB 1.1 / 2.0 connectors**

- Standard-A Plug
- Standard-B Plug
- Mini-B Plug
- Micro-B plug

**USB 3.0 connectors**

- USB 3.0 Standard-B Plug
- USB 3.0 Standard-A Plug
- USB 3.0 Micro-B Plug

**USB-C**

**Lightning**

- Apple proprietary
  - 8-pin digital signals
  - iPhone, iPad, iPod devices
- Some advantages over Micro-USB
  - Higher power output for phones and tablets
  - Can be inserted either way
  - Simpler design, more durable

**eSATA connector**

**SATA connector**

**Molex connector**

- 4-pin peripheral power connector
  - Molex Connector Company
  - AMP MATE-N-LOK
  - Provides +12 V and +5 V
- Power for many devices in the computer case
  - Storage devices
  - Optical drives
  - Fans
  - Other peripherals

**Power Supply**










**Overview of Memory**

**What is memory?**

- Random Access Memory (RAM) is the most common
  - But it’s not the only kind of memory
- RAM is not referring to hard drive or SSD storage
  - Don’t mix the two terms
  - Data is stored permanently on the drive
- Data and programs can only be used when moved to RAM

**RAM slots**

- Memory types have changed through the years
  - Driven by standardization and technology
- One of the most important components in your computer
- Every motherboard is different
  - Check your documentation

**DIMM**

- Dual inline memory module
- Electrical contacts are different on each side
- 64 bit data width

**SO-DIMM**

- Small Outline Dual In-line Memory Module
- DDR2, DDR3, and DDR4 SDRAM
- Used in laptops and mobile devices

**Dynamic Random Access Memory (DRAM)**

- The memory on the DIMM
- Dynamic 
  - Needs constant refreshing
  - Without refreshing, the data in memory disappears
- Random access
  - Any storage location can be accessed directly
  - Unlike magnetic tape

**SDRAM**

- Synchronous DRAM (SDRAM)
- SDRAM is synchronous with the common system clock
  - Queue up one process while waiting for another
  - Classic DRAM didn’t wait for a clock signal



**Single Data Rate (SDR)**

- Can pull one piece of data per clock cycle

**Double Data Rate (DDR)**

- Can pull 2 pieces of data per clock cycle

**Double Data Rate 2 (DDR2) SDRAM**

- Faster speeds
  - Twice as fast as DDR
- Not backwards compatible
  - DDR2 won’t work in DDR slots

**Double Data Rate 3 (DDR3) SDRAM**

- Twice the data rate of DDR2
  - Larger chip capacities - Maximum 16 GB per DIMM
- No backwards compatibility
  - Speed brings sacrifice

**Double Data Rate 4 (DDR4) SDRAM**

- Speed increases over DDR3
  - Faster frequencies
  - Maximum 64 GB per DIMM
- No backwards compatibility


**Memory Technologies 3.3**

**Multi-channel memory**

- Dual-channel, triple-channel, or quad-channel
- Memory combinations should match
  - Exact matches are best
- Memory module slots are often colored differently

**Memory that checks itself**

- Used on critical computer systems
  - VM servers, database servers, any server
- Parity memory
  - Adds additional parity bit
  - Won’t always detect an error
  - Can’t correct an error
- Error Correcting Code (ECC)
  - Detects errors and corrects on the fly
  - Not all systems use ECC
    - It looks the same as non-ECC memory

**Parity**

- Even parity
  - The parity bit makes an even number
- Valid or error?
  - Even parity byte

**Storage Devices 3.4**

**Optical formats**

- Small bumps read with a laser beam
  - Microscopic binary storage
- CD-ROM (Compact Disc ROM)
  - 700 megabytes (MB) capacity
- DVD-ROM (Digital Versatile Disc)
  - 4.7 gigabytes (GB) for single-layer
  - 8.5 GB for dual-layer
- Blu-ray Disc
  - 25 GB for single-layer
  - 50 GB for dual-layer

**Writing to optical media**

- “Burners” don’t create bumps
  - They darken photosensitive dye
- Compact Disc-ReWritable (CD-RW)
- DVD Read and Rewritable (DVD-R/RW)
  - And Dual Layer (DVD-R DL)
- Blu-ray Disc Recordable (BD-R)
- Blu-ray Disc Recordable Erasable (DB-RE)

**Solid-state drives (SSD)**

- Non-volatile memory
  - No moving parts
- Very fast performance
  - No spinning drive delays

**M.2 interface**

- Smaller storage device
  - As fast (or faster) than SATA
  - No SATA data or power cables
- PCI Express bus connection
  - 4 GByte/seconds throughput or faster
- Different connector types
  - Needs to be compatible with the slot key/spacer
  - B key, M key, or B and M key
  - Some M.2 drives will support both

**B-key and M-key**

- B key
  - PCIe x2
- M key 
  - PCIe x4

**Hard disk drives**

- Non-volatile magnetic storage
  - Rapidly rotating platters
- Random–access
  - Retrieve data from any part of the drive at any time
- Moving parts
  - Spinning platters, moving actuator arm
  - Mechanical components limit the access speed
  - Mechanical components can also break

**Hybrid drives**

- Solid State Hybrid Drive (SSHD)
  - Both a spinning drive and SSD in a single device
- SSD caches the slower spinning hard drive data
  - Increases speed without the cost of an SSD-only system

**USB flash drives**

- Flash memory
  - EEPROM (Electrically erasable programmable read-only memory)
  - Non-volatile memory
  - No power required to retain data
- Limited number of writes
  - Can still read the data
- Not designed for archival storage
  - Easy to lose or damage
  - Always have a backup

**RAID 3.4**

**Data redundancy**

- Hard drives store huge amounts of data
  - Important data
- Hard drives are moving components
  - They will eventually break
- What happens to the data when the drive fails
  - You can prepare for that
  - Use an array of drives

**RAID**

- Redundant Array of Independent Disks
  - They’re also inexpensive disks.
- Different RAID levels
  - Some redundant, some not
- RAID 0: Striping
- RAID 1: Mirroring
- RAID 5: Striping with Parity
- Nested RAID: RAID 1+0 (a.k.a. RAID 10)
  - A stripe of mirrors

**Software RAID vs. Hardware RAID**

- Software-based RAID
  - A feature of the operating system
  - Doesn’t require any special hardware
  - Usually lower-performance than hardware-based
- Hardware-based RAID
  - A feature of the hard drive controller
  - Configured outside of the OS
    - Usually invisible to the operating system
  - High performance, designed for speeds

**Hot swappable drives**

- Add and remove while the system is running
  - The connection is “hot”
- Drive chassis
  - Two or more drives
- Easy to repair
  - Replace a drive while the system is running
  - Combine with RAID for 100% uptime

**RAID 0 - Striping**

- Files blocks are split between two or more physical drives
- High performance
  - Data written quickly
- Disk 0			Disk 1

`	`Block 1A		Block 2A

`	`Block 3A		Block 4A

`	`Block 5A		Block 6A

`	`Block 7A		Block 8A

- No redundancy
  - A drive failure breaks the array
  - Raid 0 is zero redundancy

**RAID 1 - Mirroring**

- Files blocks are duplicated between two or more physical drives
- High disk utilization
  - Every file is duplicated
  - Required disk space is doubled
- High redundancy
  - Drive failure does not affect data availability
- Disk 0			Disk 1

`	`Block 1A		Block 1A

`	`Block 2A		Block 2A

`	`Block 3A		Block 3A

`	`Block 4A		Block 4A

**RAID 5 - Striping with parity**

- File blocks are striped
  - Along with a parity block
  - Requires at least three disks
- Efficient use of disk space
  - Files aren’t duplicated, but space is still used for parity
- High redundancy
  - Data is available after drive failure
  - Parity calculation may affect performance
- Disk 0			Disk 1			Disk 2			Disk 3

`	`Block 1A		Block 2A		Block 3A		Parity A

Block 1B		Block 2B		Parity B		Block 3B

Block 1C		Parity C		Block 2C		Block 3C

`	`Parity D		Block 1D		Block 2D		Block 3D

**RAID 10 (1+0) - A stripe of mirrors**

- The speed of striping, the redundancy of mirroring
  - The best of both worlds
- Need at least 4 drives

**Motherboard Form Factors 3.5**

- Physical size
  - Case sizing
- Basic layout
  - Room for small changes
- Power
  - Standard connectors
- Airflow
  - Increasingly important
- Wikipedia: There are 40 different motherboard types categorized.

**What you need to know**

- CompTIA exam objectives:
  - “3.5 - Given a scenario, install and configure motherboards, CPUs, and add-on cards.”
- Focus on which motherboard would be the best choice for a scenario
  - Memorizing the dimensions of the motherboard probably isn’t the most important thing
  - ATX, microATX, ITX, and mini-ITX
- Which motherboard would you choose?
  - Media center, video editing, thin client, etc.

**ATX form factor**

- Advanced Technology Extended
- Standardized by Intel in 1995
  - Seen many updates over the years
- Power
  - 20 pin connector
  - 24 pin connector, additional 4/8 pin connector
- ATX motherboards are still manufactured in 2019

**microATX (uATX)**

- Smaller than an ATX motherboard
  - Limited expansion slots
- Backward compatibility
  - Similar mounting points
  - Similar power
- Very popular form factor
  - Actively manufactured as of 2019

**ITX form factor**

- A series of lower-power motherboards
  - Developed by VIA Technologies in 2001
- Mini-ITX is screw-compatible with ATX and microATX
  - Fits almost any enclosure
- Small form factor uses
  - Single-purpose computing, i.e., streaming media





**Motherboard Expansion Slots 3.5**

**A computer bus**

- Communication path
  - A city of technology
- Internal PC growth
  - Independent pathways
- System expansion
  - Additional capabilities

**The expansion bus**

- “Width” in bits
  - Big roads, little roads
  - Width is changing to bandwidth
- Clock speed of the bus
  - The expansion bus gets its own clock
  - 1 MHz (megahertz) = 1 million cycles per second
  - 1 GHz = 1000 MHz = 1 billion cycles per second
- Clock speed does not necessarily equal transfer rate
  - DDR3 SDRAM can transfer 64 times the memory clock speed

**Conventional PCI**

- Peripheral Component Interconnect
  - Nobody ever calls it that
  - Created in 1994
- A common expansion interface
  - 32-bit and 64-bit bus width
  - Parallel communication
- Throughput varies by bus version
  - 133 MB/s (32-bit at 33 MHz)
  - 266 MB/s (32-bit at 66 MHz or 64-bit at 33 MHz)
  - 533 MB/s (64-bit at 66 MHz)

**PCI Express**

- Also known as PCIe
  - Replaced PCI, PCI-X, and AGP (Accelerated Graphics Port)
- Communicates serially
  - Unidirectional serial “lanes”
  - Slower devices don’t slow down everyone
- One, two, four, eight, sixteen, or thirty-two full-duplex lanes
  - x1, x2, x4, x8, x16, x32
  - “x” is pronounced “by” (“by 4,” “by 16”)



**PCI Express throughput**

- Different versions of PCIe
  - Improvement in speed with each iteration
- Per-lane throughput in each direction
  - v1.x: 250 MB/s
  - v2.x: 500MB/s
  - v3.0: 1 GB/s
  - v4.0: 2 GB/s
  - v5.0 (expected in 2019): 4 GB/s

**Motherboard Connectors 3.5**

**CPU sockets**

- Motherboards are matched with CPUs
  - CPUs have specific socket requirements
- CPU socket is usually the largest thing on the board
  - And usually central to everything
- Not easily upgradable
  - And often not an option

**Zero Insertion Force (ZIF) socket**

**Pin Grid Array (PGA)**

**Land Grid Array (LGA)**

- Reverse the PGA
  - Pins are on the motherboard
- No pin to damage on the CPU
  - Easier to damage the motherboard

**Land Grid Array Processor**

**Storage drive interfaces - SATA** **and PATA**

**Computer case**

- Various front-panel connections
  - Not directly connected to the motherboard
- Front panel connectors are labeled

**Internal USB connector**

- USB on the motherboard
- Integrated - part of the motherboard
  - On the back
  - Keyboard, mouse
- Internal case connection
  - Pins for case interfaces

**BIOS 3.5**

**BIOS - Basic Input/Output System**

- The software used to start your computer
  - The firmware
  - System BIOS, ROM BIOS
  - ROM or flash memory
- Initializes CPU and memory
  - Build the workspace
- POST
  - Power-On-Self-Test
- Look for a boot loader
  - Start the operating system

**Legacy BIOS**

- The original / traditional BIOS
  - It’s been around more than 25 years
- Older operating systems talked to hardware through BIOS
  - Instead of accessing hardware directly
- Limited hardware support
  - No drivers for modern network, video, and storage devices

**UEFI BIOS**

- Unified Extensible Firmware Interface
  - Based on Intel’s EFI (Extensible Firmware Interface)
- A defined standard
  - Implemented by the manufacturers
- Designed to replace the legacy BIOS
  - Need a modern BIOS for modern computers
  - Graphical and text-based

**UEFI advantages**

- Boot from large (>2.2 TB) Global Unique Identifier (GUID) partition table (GPT) disks
  - Also supports File Allocation Table (FAT) and removable media
- Includes a pre-boot environment
  - This isn’t an operating system
  - Has its own shell, drivers, and applications
  - Browse the Internet, backup a storage drive
  - Remote diagnostics, even without an OS


**Nonvolatile BIOS memory**

- Store the BIOS configuration
  - Your settings
- Complementary metal-oxide semiconductor (CMOS)
  - A type of memory
  - May be backed up with a battery
- Usually flash memory these days
  - Easily stored and accessed

**The “CMOS” battery**

- Not needed for today’s flash-based storage
  - Maintains older BIOS configurations
  - May only be used to maintain data/time
- A bad battery will require a BIOS configuration or date/time configuration on every boot
- On older systems, can reset the BIOS configuration by removing the battery
  - Newer computers use a jumper

**BIOS Options 3.5**

**The secret button(s)**

- Launching the system setup
  - Del, F1, F2 Ctrl-S, Ctrl-Alt-S
- Microsoft Virtual PC (Windows 7)
  - <https://support.microsoft.com/en-us/kb/958559>
- Hyper-V (Windows 8/10)
  - Turn Windows features on and off
- VMware Workstation Player
  - <http://www.vmware.com/products/player/>
- But not VirtualBox
  - <http://www.virtualbox.org>

**Fast startup**

- Windows 8 and Windows 10
  - Doesn’t actually shut down all the way
  - Starts up very quickly
- Starts up so quickly, you can’t open the BIOS configuration
  - This can be an issue
- Disable fast startup in Control Panel / Power Options
  - If you can
- Most motherboards have a separate process
  - Hold F2, then press the power button, for example



**Configure component information**

- RAM
  - View and configure memory settings
- Hard drive / SSD
  - Drive settings
  - Boot order
- Optical drive
  - Enable / Disable
- CPU
  - CPU types

**Built-in diagnostics**

- Part of the BIOS
  - Always available
- Run from the BIOS menu
  - No additional media or software required
- Focused on hardware checks
  - Doesn’t touch the operating system

**Important tips**

- Have a backup of your BIOS configuration
  - Make notes
  - Take a picture
- Don’t make a change unless you’re certain of the setting
  - It’s difficult to leave it alone

**BIOS Security 3.5**

**BIOS passwords**

- BIOS Password / User Password
  - System won’t start
  - Need the password to start the operating system
- Supervisor Password
  - Restrict BIOS changes
  - Must use supervisor password to change any BIOS configuration

**Full disk encryption (FDE)**

- Everything is encrypted
  - Not just individual files
- Windows BitLocker disk encryption
  - BIOS integrates with TPM
- TPM - Trusted Platform Module
  - Can be added to many motherboards
  - Built-in to some systems
  - Adds advanced cryptographics functions

**LoJack for Laptops**

- Originally called CompuTrace
  - Name licensed from the vehicle recovery service
- Built into the BIOS
  - Software installed into the OS
  - Reinstalls itself if removed or new storage drive installed
- “Phone home” function
  - Provides location information
- Theft mode
  - Remotely lock the laptop and/or delete files
  - Forces a startup password

**Secure Boot**

- Malicious software can “own” your system
  - Malicious drivers or OS software
- Secure Boot
  - Part of the UEFI specification
- Digitally sign known-good software
  - Cryptographically secure
  - Software won’t run without the proper signature
- Support in many different operating systems
  - Windows and Linux support

**Installing BIOS Upgrades 3.5**

**Firmware upgrades**

- Firmware
  - Non-volatile memory and software
  - Older-style ROMs
  - Newer-style flash memory
- Computer BIOS, video adapter firmware, game console, etc
  - Improve performance, fix bugs
- Not usually part of a normal maintenance process
  - Upgrade for a specific reason

**Identify current BIOS version**

- May appear when system starts
  - Can be difficult to catch
- Easier to look in System Information (msinfo32)
  - Version and date details
- Compare the current to the existing
  - An upgrade may not be available
- If possible, get a copy of the current version
  - Always good to have a backup plan

**Before upgrading…**

- Read the documentation
  - Some BIOS updates are bland
  - Others are full of new features
  - Check for OS prerequisites
- Locate a reliable power source
  - Laptop: Connect to AC power and have a full battery
  - Desktop: Use a UPS, if possible

**Run the upgrade program**

- Really-old BIOS upgrades may require a boot disk
  - Floppy or optical media
- Most modern upgrades run as an executable
  - Close all of your other applications before running 
  - May also run in the BIOS from a flash drive
- Most upgrade apps will check for prerequisites
  - Don’t rely on this
- Requires a reboot
  - Save your documents

**Other options**

- New options may be available
  - Modern motherboards have advantages
- Multiple BIOS versions
  - Two separate BIOS versions
  - Easily switch between them
- Upgrade from a USB flash drive
  - Computer may not even need to be powered on

**CPU Features 3.5**

**Processor Cores**

- Dual-core/ Quad-core / Octa-core / Multi-core
  - And more all the time
- Multiple cores
  - Each core has its own cache
  - The entire chip may have a shared cache

**CPU Die**


**CPU cache**

- Super fast memory
  - There’s not much of it
  - Holds data, instructions, and/or results
- Level 1 cache
  - First check
- Level 2 cache
  - Secondary data
- Level 3 cache
  - Still on the chip
  - These days

**Virtualization support**

- Run other operating systems within a single hardware platform
  - Multiple operating systems share physical hardware components
- Virtualization in software was limited
  - Performance and hardware management challenges
- Virtualization added to the processor
  - Hardware is faster and easier to manage
  - Intel Virtualization Technology (VT)
  - AMD Virtualization (AMD-V)

**Hyper-threading**

- Hyper-Threading Technology (HTT)
- One CPU, acts like two
- Doesn’t actually work as fast as two
  - 15% to 30% performance improvement
- Operating system must be written for HTT
  - Windows XP and later (any modern OS)

**Processor speed**

- Read speed: CPU clock
  - Historical qualification of speed
  - Megahertz (MHz) or gigahertz (GHz)
- Actual speed
  - Combination of different factors
    - Clock speed, CPU architecture, bus speed, bus width, L1 cache size, L2 cache size, operating system capabilities
- CPU manufacturers have moved away from marketing performance in clock cycles
- No broadly accepted measure of performance
  - Use a benchmark that works for you



**Overclocking**

- When fast isn’t fast enough
  - Increase the clock speed past the rated value
- A balancing act
  - More power required
  - More heat created
  - At some point, the system becomes unstable
- Change the base clock (BCLK)
  - Need an unlocked CPU
  - Run a stress test to confirm the stability
- This will void your warranty
  - You can break more than your CPU

**Integrated GPU**

- Graphics processing unit
  - Part of a video adapter, motherboard or CPU
- Graphics rendering requires a lot of work
  - Dedicated hardware speeds the process

**Intel and AMD**

- Two solid CPU manufacturers
  - The differences are subtle
- Cost
  - AMD tends to be a bit less expensive
- Laptops
  - Intel has a large portfolio of options
- Choosing a side
  - Historically, AMD is value and Intel is performance
  - This is a dynamic technology segment

**CPU Cooling 3.5**

**Case fans**

- Cool air is pulled through a personal computer
  - Always check for good airflow
- Motherboard layout becomes important
- Component location is key
  - Devices, wiring, power
- Many different sizes and styles
  - And volume levels




**On-board fans**

- Designed to cool an entire adapter card
- Can be bulky
  - May take additional adapter card space
- Usually seen on high-end graphics cards

**Fan specifications**

- Standard sizes
  - i.e. 80 mm, 120 mm, 200 mm
- Different speeds
  - Variable speed
- Different noise levels
  - Not all fans sound the same

**Heat sink**

- Dissipate heat through thermal conduction
  - Copper or aluminum alloy
- Fins/grid increase surface area
  - Heat is then transferred to the cooler air
- Thermal paste create a good contact between the chip and the heat sink
- They get HOT - don’t touch them

**Fanless / passive cooling**

- No fans, no noise
  - Silent operation
- Specialized functions
  - Video servers, TV set top box, satellite receiver, media server
- Functions are very controlled
  - Carefully measured thermal tests
- Low-power components
  - Heat sinks

**Liquid cooling**

- Coolant is circulated through a computer
  - Not a new concept
    - Automobiles, mainframe computers
- High-end systems
- Gaming, graphics
- Overclocking





**Expansion Cards 3.5**

**Expansion cards**

- Extend the functionality of your computer
  - You may need more than the motherboard provides
- Relatively simple process
  - Designed for end-user installation
- Install hardware
  - Add a card
- Install a driver
  - Software for the operating system

**Onboard video**

**Video Cards**

**Audio**

**Network cards**

**Multi-port Ethernet**

**USB expansion card**

**Storage cards**

**eSATA card**

**Documentation**

- Check the motherboard documentation
  - Number and type of slots
- Check the adapter card documentation
  - Minimum requirement - Hardware, software
  - Knowledge base - Any “gotchas?”
  - Support forums - What are other people saying?
- You may need to perform a driver installation before installing hardware

**Driver installation**

- Check the documentation first
- Check the web for the latest version
- Uninstall previous drivers through Windows Device Manager
- Manufacturer provided setup program
- Manual installation through Windows Device Manager
- Check the Device Manager for the status

**Peripherals 3.6**

**Printer**

- Color and B&W output
  - Paper documents
  - Photos
- All-in-one - AIO
  - Printer, scanner, copier, fax
- Connectivity
  - USB
  - Ethernet
  - 802.11 Wireless
  - Bluetooth / Infrared

**Scanner**

- Connected via USB
  - Or 802.11 wireless
- Different form factors
  - All-in-one
  - Flatbed
- May include an ADF
  - Automatic Document Feeder

**Flatbed scanner**

**Barcode/QR code reader**

- Serial or USB connector
  - Or 802.11 wireless
- Or with your phone
  - Built-in camera

**Display devices**

- The human’s display device
  - The most popular output device
- Many different connections
  - Different standards through the years
- Many different standards
  - And sizes
  - And resolutions

**VR headset**

- Virtual reality
  - Headset determines what you see
- Motion tracking
  - X, Y, and Z axis
- Interact with a virtual environment
  - Gaming 
  - Education
  - Art
  - Travel

**Optical / DVD Drive**

- Store and read data with light
  - Small bumps read with a laser beam
  - Microscopic binary storage
- Read/write media
  - Store backups and documents
- Read-only media
  - Data can’t be deleted
  - Common for video distribution
- Limited storage sizes
  - Dual-layer Blu-ray holds 50 GB

**Mouse**

- USB connection
  - Or an adapter for PS/2
- Optical mice have few moving parts
  - May need the right surface
  - Glass may cause a problem

**Keyboard**

- Connected via USB
  - Or an adapter
- Additional features may require additional drivers and/or software

**Touch Pads**

- Integrated into the keyboard
  - May be a standalone device
  - Connected via USB or Bluetooth
- Replaces a mouse
  - Uses no additional space

**Signature pad**

- We’ve gone paperless
  - But we still need somewhere to sign
- Small digitizer
  - And stylus
- USB connection
  - Driver may be required

**Gaming input**

- Gamepad and Joystick
  - USB connect
  - Used almost exclusively for games

**Webcam**

- Video capture
  - Built-in camera
  - USB connected
  - 802.11 wireless
- Usually includes both audio and video
  - Specialized drivers and software

**Microphone**

- Integrated into most new laptops and multimedia devices
  - Also external
- Connectivity
  - Analog - TRS (Tip / Ring / Sleeve)
  - Digital - USB

**Speakers**

- Analog output devices
  - Compatible with our ears
- Connectivity
  - TRS (Tip / Ring / Sleeve) jacks
  - Speaker output, audio adapter

**Headset**

- Headphones and microphone
  - One unit
- Desk and mobile use
  - USB
  - TRS plug
  - Wireless / Bluetooth
- Talk and listen
  - Desktop telephone
  - Mobile communication
  - Gaming

**Digital projectors**

- Not always LCD
  - But common to see LCD
- Metal-halide lamp
  - Very bright (very hot) light
  - Brightness measured in lumens
  - Relatively expensive ($35 to $350+ US)
- Always let bulbs cool
  - Fan will run after shutting off
  - Keep it plugged in

**External storage devices**

- Storage outside the computer and often removable
  - Very portable, easy to move large files
  - USB flash drive, SSD, hard drive
- Many different connectivity options
  - USB, Thunderbolt, eSATA etc.
- Very large storage options
  - And very mobile
  - Can be a security concern

**KVM**

- Keyboard, Video and Mouse
  - Use many computers with a single keyboard video display, and mouse

**Magnetic reader / chip reader**

- Point of sale terminal
  - Method of payment
  - Credit card
- Support for different formats
  - Integrated circuit
    - Physically inserted into reader
  - Magnetic strip
    - Backward compatibility
- Reader is USB connected
  - To a point of sale (POS) terminal

**NFC / Tap-to-pay device**

- Near-field communication
  - 10 centimeter wireless range
- Built into many phones
  - Integrates with a payment terminal
- Many different uses
  - Contactless payment systems
  - Identity token / door key
  - Gaming and entertainment

**Smart card reader**

- Smart card
  - Card with embedded circuitry
  - Used in payment cards, identification cards
- Useful form of authentication
  - Username, password, physical smart card
- Readers are built-in or external
  - USB connected

**Computer Power 3.7**

**WARNING**

- **Always disconnect from the power source when working on a device**
  - **Always.**
- Some devices store a charge in capacitors
  - Know how to discharge before touching
- Never connect your body to any part of an electrical system
  - Do not connect yourself to an electrical ground
- Respect electricity
  - It does not respect you

**Computer power supply**

- Computer uses DC voltage
  - Most power sources provide AC voltage
- Converts 115 V AC or 220 V AC
  - To 3.3 V DC, 5.5 V DC, and 12 V DC
- You’ll know when this isn’t working
  - An important component

**Amp and volt**

- Ampere (amp, A) - The rate of electron flow past a point in one second
  - The diameter of the hose
- Voltage (volt, V) Electrical “pressure” pushing the electrons
  - How open the faucet is

**Power**

- Watt (W) - Measurement of real power use
  - Volts \* amps = watts
  - 120V \* 0.5A = 60W

**Current**

- Alternating current (AC)
  - Direction of current constantly reverses
  - Distributes electricity efficiently over long distances
  - Frequency of this cycle is important
    - US/Canada - 110 to 120 volts of AC (VAC), 60 hertz (Hz)
    - Europe - 220-240 VAC, 50 Hz
- Direct current (DC)
  - Current moves in one direction with a constant voltage

**Dual-voltage input options**

- Voltage varies by country
- Manually switch between 110 V/115 V and 220 V/230 V
  - Get your meter
  - Or use an auto-switching power supply
- Don’t plug a 115 V power supply into a 230 V power source.

**24-pin motherboard power**

- Main motherboard power
  - Provides +3.3 V, +/-5 V, and +/- 12 V
- 20 pin connector was the original ATX standard
  - 24 pin was added for PCI Express power
- You can connect a 24-pin connector to a 20-pin motherboard
  - Some cables are 20-pin + 4-pin

**Power supply output**

- Different voltages
  - For different components
- Positive and negative voltage
  - Voltage is a difference in potential
  - The electrical ground is a common reference point
  - Depends on where you measure from
- At the front door of your house
  - The second floor is +10 feet
  - The basement is -10 feet
- +12 V
  - PCIe adapters, hard drive motors, cooling fans, most modern components
- +5 V
  - Some motherboard components
  - Many components are now using +3.3 V
- +3.3 V
  - M.2 slots, RAM slots, motherboard logic circuits
- -12 V
  - Integrate LAN
  - Older serial ports
  - Some PCI cards
- -5 V
  - Available for ISA adapter cards
  - Most cards didn’t use it
  - Today’s motherboards don’t have ISA slots

**Sizing a power supply**

- Power supplies are rated by watts
  - Overall and by individual voltages
- Bigger isn’t necessarily better
  - More expensive
  - Doesn’t speed up your computer
- Physical size is relatively standard
  - Older cases and systems may have proprietary sizes
- Calculate the watts required for all components
  - CPU, storage devices, video adapter
  - Many online calculators
- Video adapters are usually the largest power draw
  - Many video card specifications list a recommended power supply wattage
- 50% capacity is a good rule of thumb
  - Power supply runs efficiently and there's room to grow

**Custom Computer Systems 3.8**

**Graphics workstations**

- Computer Aided Design (CAD) / Computer Aided Manufacturing (CAM)
- SSD
  - High-speed storage
- High-end video
  - Complex graphics
- Maximum RAM
  - Significant memory use

**Audio/Video editing workstation**

- Specialized audio and video card
  - High quality audio
  - Powerful video
- Large fast hard drive
  - Constant disk writes
  - SSD
- Dual monitors
  - Edit in one monitor, view output in the other

**Virtualization workstation**

- Maximum RAM
  - Every OS needs its own memory
  - It adds up quickly
- Maximum CPU cores
  - Constant processing
  - Need an efficient CPU
  - Most virtualization apps can use multiple cores

**Gaming PC**

- SSD
  - Fast start and load times
- High-end video / specialized GPU
  - Graphically complex
- High definition sound card
  - Multiple layers, atmosphere
- High-end cooling
  - High utilization for hours at a time

**Network attached storage device**

- NAS
  - Access from anywhere
- Media streaming
  - Central location
- File sharing
  - Easy access
- Gigabit NIC
  - High speed transfers
- RAID array
  - Redundant hard drives

**Standard thick client**

- Desktop applications
  - Executable programs running in local memory and using local CPU
- Meets recommended requirements for running the operating system
  - CPU, total RAM, disk space

**Thin client**

- Basic application usage
  - Applications actually run on a remote server
  - Virtual Desktop Infrastructure (VDI)
  - Local device is a keyboard, mouse, and screen
- Minimal operating system on the silent
  - No huge memory or CPU needs
- Network connectivity
  - Big network requirement
  - Everything happens across the wire

**Common Devices 3.9**

**Thin client**

- Very little client configuration
  - All the work is done on the server
- Mouse, keyboard network, monitor
  - And power on
- Minimal OS on the client
  - Most of the OS is on the server
  - Apps are centralized on the server
- Few moving parts, if any
  - Inexpensive to buy
  - Easy to replace

**Thick client**

- A traditional computer
  - With all of the requirements
- Local resources
  - Operating system
  - Device drivers
  - Applications
- Ongoing support
  - Security patches
  - Operating system updates
  - Application updates

**Account setup and settings**

- Centralized account management
  - Microsoft Active Directory
  - User account added to the directory
- Thin client
  - No local permissions required
- Thick client
  - Device is added to the Microsoft domain
  - User authenticates to gain access to the thick client

**Laptop**

- A thick client that moves
  - Mobility brings additional administrative concerts
- Touchpad configuration
  - Finger combinations and swiping
- Synchronization and back up
  - Cloud-based or local drive
- Wireless connections
  - Mobility in the office and elsewhere
- Addition security
  - VPN connectivity, local drive encryption

**Phone / tablet**

- Centralized management
  - Mobile Device Manager (MDM)
- Touchscreen configuration
  - Lock codes and biometric access
- Application installations
  - Set by policy and requirement
- Synchronization and backup
  - Cloud-based
- Wireless enabled
  - Includes VPN Connectivity

**SOHO Multifunction Devices 3.10**

**SOHO multifunction devices**

- SOHO
  - Small-office / Home-office
- Multifunction devices
  - Printer
  - Scanner
  - Fax (yes, really)
  - Network connection
  - Phone line connection
  - Print from web
- There are a lot of things that can go wrong
  - You’re going to fix them

**Printer drivers**

- Specific to a printer model
  - Get this exactly right
- Get the right operating system drivers
  - Windows 7, Windows 8/8.1, Windows 10
- Get the right version of the operating system
  - 32-bit drivers are very different than 64-bit drivers
- You can’t mix and match drivers
  - It’s a very specific task




**Configuration settings**

- Duplex
  - Printing on both sides of the page without manually flipping over the paper
  - Not all printers can do this
- Collate
  - Print multiple copies in their proper order
  - Non-collated
    - Page 1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4
  - Collated
    - Page 1, 2, 3, 4, 1, 2, 3, 4, 1, 2, 3, 4, 1, 2, 3, 4
  - Very useful for many copies of large documents
- Orientation
  - Portrait vs. Landscape
  - The paper doesn’t rotate
    - The printer compensates
- Quality
  - Resolution
  - Color, greyscale
  - Color saving

**Wired device sharing**

- USB type B
  - The most common connector
  - USB Type B on the printer, USB type A on the computer
- Parallel
  - Legacy systems
  - Centronics interface on the printer
  - DB-25 on the computer
- Ethernet
  - RJ45 connector

**Wireless device sharing**

- Bluetooth
  - Limited range
- 802.11 a/b/g/n/ac Infrastructure mode
  - Many devices using an access point
- 802.11 Ad hoc mode
  - No access point
  - Direct link between wireless devices

**Device sharing**

- Integrated print server
  - Print directly to the printer
  - Jobs are queued on the printer
  - Jobs are managed on the printer
    - Web-based front-end
    - Client utility
- Cloud printing
  - Print to the cloud
  - Useful from mobile devices
  - The cloud send to your printer
  - Google, Brother, HP, etc.

**Sharing from an operating system**

- Network ports
  - Common on Windows devices
  - Commonly uses tcp/139, tcp/445, udp/137, and udp/138
- Bonjour
  - Discover Apple devices on the LAN
  - Part of macOS
  - Can be added to Windows (iTunes, etc.)
- AirPrint
  - Print from iOS devices to compatible printers

**Printer data privacy**

- User authentication
  - Everyone can print
  - Set rights and permissions
  - Printing vs managing the printer
- Print and scan caching
  - Click print
  - Local system creates a file of the output
  - Output file is sent to the print server spooler
  - Printing is done from the spool file
  - Spool file is deleted when done
    - But not always


**Laser Printers 3.11**

**Laser printer**

- Combine a laser, high voltage, charged ions, powdered ink, heat, and paper
- Very high quality
- Fast printing speeds
- Very complex
  - Many moving parts
  - Requires on-printer memory
  - Messy on the inside
  - Very

**Imaging drum**

- Image is drawn onto a photosensitive drum
  - “Painted” with a laser
- Picks up toner
  - Transfers toner to the paper
- Can be separate from the toner cartridge
  - Or combined

**Fuser assembly**

- Heat and pressure
  - Melt plastic toner powder
  - Permanently bond toner to paper

**Transfer belt and roller**

- Color laser printers
  - Cyan, yellow, magenta, black
- Four separate toner cartridges
- Image is transferred from all cartridges to the single belt
  - And then to a single transfer roller

**Pickup rollers**

- Pickup paper
  - Should be a single page at a time
  - Problems if no paper is picked up or multiple sheets are picked
- Should periodically cleaned or replaced

**Separation pad**

- Pull just the top sheet from the paper tray
  - Not multiple sheets
- Small and inexpensive
  - Easy to clean or replace

**Duplexing assembly**

- Printers usually print on a single side
  - Not both sides simultaneously
- Printing on both sides is a two step process
  - Print side one print side two
- You need mechanisms to “flip” the page
  - Automatically
- Can be built-in to the printer
  - Or available as an add-on

**The laser printing process**

1. Processing: Build the entire page in memory.
1. Charging: Prepare the drum with a negative electrostatic charge.
1. Exposing: Write the image with the laser.
1. Developing: Add negatively-charged toner to the imaging drum.
1. Transferring: Move the toner from the drum to the paper.
1. Fusing: Head and pressure.
1. Cleaning: Remove excess toner.

**Laser Printer Maintenance 3.11**

**Replacing the toner cartridge**

- Look for the messages
  - Low doesn’ mean empty
- The toner can also contain the OPC drum
  - Organic Photoconductor drum
  - Sensitive to light; keep it in the bag
- Power down the printer
  - Safety first
- Removing packing strips from the new drum
  - Replace it with the old

**Laser printer maintenance kit**

- Laser printers wear out
  - All those moving parts
  - Heat and pressure
- Standard maintenance kits
  - Replacement feed rollers, new fuser unit, etc.
- When to perform maintenance?
  - Check the printer’s page counter
- Power down and replace the components
  - Fuser units are HOT
- Reset the page counter when you’re done.

**Laser printer calibration**

- Different toner cartridges print with different densities
  - Some dark, some light
- Laser printer calibration can adjust the density
  - Makes it look perfect
- Can be automated or a manual process
  - Every printer is different
  - Check the printer manual


**Laser printer cleaning**

- Laser printers are dirty
  - All that toner and paper dust
- Check the manufacturer's recommendations
  - Water, isopropyl alcohol (IPA)
  - Don’t use harsh chemicals
- Outside - damp cloth
- Inside - Wipe dust away
  - Don’t use a normal vacuum cleaner or compressed air
  - Wash off skin with cold water
  - Clean rollers with IPA

**Inkjet Printers 3.11**

**Inkjet (ink-dispersion) printer**

- Relatively inexpensive technology
- Quite
- High-resolution
- Expensive ink
  - Proprietary
- Eventually fades
- Clogs easily

**Inkjet cartridge**

- Place drops of ink onto a page
  - Pulled from a set of cartridges
- CMYK
  - Cyan, Magenta, Yellow, Key (black)

**Print head**

- Some consumer printers integrate the print head into the ink cartridge
  - Change the cartridge, get a new print head
- Others separate the ink cartridge from the print head

**Feed rollers**

- Pick up and feed paper through the printer
  - Must be clean and not worn
- Duplexing
  - Print on both sides of the paper
  - Included with some printers

**Carriage and belt**

- Ink cartridges are moved over the paper
  - Carriage may include its own print head
- Belt moves the carriage back and forth
  - Another moving part

**Inkjet printer calibration**

- Align nozzles to the paper
  - Lines should be crisp
  - Colors should align
- Printer includes a calibration option
  - May need to make minor adjustments

**Inkjet Printer Maintenance 3.11**

**Cleaning print heads**

- Small droplets of ink
  - And small holes in a print head
- Clogged heads is a big issue
  - Many printers automatically clean every day
  - Output has streaks or sections of missing color
- Cleaning process can be started manually
  - Only takes a few minutes
- Some print heads/cartridges can be removed
  - Manually cleaning may help

**Replacing inkjet cartridges**

- Usually separate colors
  - Cyan, Magenta, Yellow, and Key (CMYK)
  - Some cartridges will combine these
- Takes seconds to replace
  - Takes a few minutes to calibrate and prepare the cartridge
- Recycle the empty cartridge
  - All plastic

**Inkjet printer calibration**

- Align nozzles to the paper
  - Lines should be crisp
  - Colors should not overlap
- Printer includes a calibration option
  - May need to make minor adjustments

**Clearing jams**

- Lots of turns and twists
  - A jamm is inevitable
- Remove tray paper
  - Any loose paper
- Remove paper from the path
  - Firm pressure, don’t rip
- Check for any scraps of paper
  - Remove all loose paper

**Thermal Printers 3.11**

**Thermal printer**

- White paper
  - Turns black when heated
  - No ink
- Very quiet
  - Almost silent
- Paper is sensitive to light and heat
  - And clear tape

**Feed assembly**

- Pull paper through the printer
  - Relatively small paper path

**Heating element**

- Full-length heating element
  - No moving print head

**Thermal paper**

- Paper covered with a chemical
  - Changes color when heated
- Cash registers, credit card terminals
  - And quiet areas
- Looks like normal paper
  - Feels a bit different

**Thermal Printer Maintenance 3.11**

**Thermal paper replacement**

- Relatively inexpensive
  - But impossible to substitute
- Different sizes
  - Not like laser printer paper
  - Keep a list
- Actual replacement process is easy
  - Simple paper feed
  - Small device



**Cleaning the heating element**

- Liquid cleaner 
  - Isopropyl alcohol (IPA)
  - Get a cleaning pen
  - Check manufacturer’s recommendations
- Swab gently
  - Usually small areas
- Use a cleaning card
  - Cleans the head
  - And paper pathways

**Removing debris**

- Relatively small amount
  - Paper bits and dust
  - No toner
- Blow out the printer
  - Take it outside
- Wipe it out
  - Damn cloth
- Avoid using a vacuum
  - Unless it’s designed for computers
    - Resists static buildup/discharge

**Impact printers 3.11**

**Dot-matrix (impact) printers**

- Print head with a small matrix of pins
  - Presses against a ribbon to make a mark on paper
- Good for carbon/multiple copies
- Low cost per page
- Noisy
- Poor graphics
- Niche use
  - Car rental, airports

**Dot-matrix printer head**

- Moves back and forth
  - Pins hit ribbon and paper
- One matrix
  - Must move across the page to print

**Printer ribbon**

- Fabric
  - One long ribbon
  - Never ending circle
- Easy to replace
  - One single unit
- Proprietary size
  - Specific to printer model

**Tractor feed**

- Paper pulled through with holes on the side of the paper
  - Instead of using friction
- Continuouspaper feed
  - Perforations between pages
- Holes have to line up perfectly
  - Tractor paper can be perforated to remove holes

**Impact printer maintenance 3.11**

**Printer ribbon replacement**

- Single ribbon
  - Self-contained
  - One long circle
- Replace when ink becomes too light
  - Ink is eventually consumed
- Designed to be modular
  - Replace in less than a minute

**Print head replacement**

- Takes a lot of abuse
  - Directly hits the ribbon and paper
- Gets hot
  - Watch your fingers
- Another modular part
  - Look for a release lever or bar
- Replace with the ribbon for the best effect
  - The output should look perfect

**Replacing paper**

- Not as easy as a laser printer
  - Paper must feed perfectly into holes
    - Tractor feed
- Forms must be positioned correctly
  - Text needs to fit a predefined space
- Paper must feed without constraint
  - Make sure nothing is in the way

**Virtual and 3D printers** **3.11**

**Virtual printers**

- No physical output
  - OUtput to a “digital” document
- No additional hardware required
  - No printer, no paper
- Useful for sending electronically
  - Easy to manage

**Print to file**

- You need to print to a printer at work
  - You’re at home
- Print to the work printer driver
  - But save it as a file
- File will be in an output format specific to that printer
  - You can’t open it with another program
- Must use the command line to copy the file to the printer
  - i.e, copy filename LPT1:

**Print to PDF**

- Adobe PDF
  - Portable Document Format
  - A one-way path from application to PDF
  - Cross-platform compatibility
- Proprietary Adobe format
  - Requires specialized software to create and view a PDF
  - PDF viewers built into many Internet browsers
- Many third party tools available
  - Some applications will print to PDF without any additional software

**Print to XPS**

- Microsoft XPS
  - XML Paper Specification
- Similar use case to Adobe PDF
  - But XPS is included in Windows
  - And available all the way back to Windows XP
- Print to XPS, view in any operating system
  - If there’s an XPS reader

**Print to image**

- Print to a graphics image
  - For later image editing or sharing
- Not integrated into the OS
  - A feature of the application
- Some third-party image print drivers are available
  - Application may export graphics formats natively

**3D printers**

- “Print” in three dimensions
  - Create a 3D item based on an electronic model
- Additive manufacturing
  - Melt plastic filament in layers to create the object
  - No machining process required
- Rapid prototyping
  - Design and create relatively quickly and inexpensively
- Deploy designs anywhere in the world
  - Or into space
