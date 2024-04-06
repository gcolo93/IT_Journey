Lesson 2: Deploying Ethernet Cabling

Topic 2A: Summarize Ethernet Standards

Network Data Transmission

All network signaling uses electromagnetic radiation of one type or another. Electromagnetic radiation means transmitting signals as electric current, infrared light, or radio waves. The electromagnetic radiation forms a carrier wave with a given bandwidth or range of frequencies. A signal is transmitted over the wave by modulation and encoding schemes.

\*\*The narrow definition of bandwidth is a frequency range measured in cycles per second or Hertz (Hz), but the term is very widely used in data networking to mean the amount of data that can be transferred, measured multiples of bits per second (bps). Encoding methods mean that, for instance, a signal with 100 MHz frequency bandwidth can transfer much more than 100 mbps.

Copper Cable

Copper cable is used to transmit electrical signals. The cable between two nodes creates a low voltage electrical circuit between the interfaces on the nodes. There are two main types of copper cable: twisted pair and coaxial (coax). Copper cable suffers from high attenuation, meaning that the signal quickly loses strength over long links. Twisted pair cable is rated to Cat standards.

Fiber Optic Cable

Fiber optic cable carries very high frequency radiation in the infrared light part of the electromagnetic spectrum. The light signals are also not susceptible to interference or noise from other sources and less affected by attenuation. Consequently, fiber optic cable supports higher bandwidth over longer links than copper cable. Fiber optic cabling is divided into Single Mode (SMF) and MultiMode (MMF) types, and MMF is categorized by Optical Mode designations (OM1, OM2, OM3, and OM4).






Ethernet Standards

Standards set by the Institute of Electrical and Electronics Engineers (IEEE) 802.3 Ethernet standards (ieee802.org/3).

Ethernet standards provide assurance that network cabling will meet the bandwidth requirements of applications. The standards specify the bit rate that should be achieved over different types of media up to the supported distance limitations. These Ethernet media specifications are named using a three-part convention, which is often referred to as xBASE-y. This describes:

●	The bit rate in megabits per second (Mbps) or gigabits per second (Gbps).

●	The signal mode (baseband or broadband). All mainstream types of Ethernet use baseband transmissions, so you will only see specifications of the for xBASE-y.

●	A designator for the media type.


Media Access Control and Collision Domains

Ethernet is a multiple access area network, which means that the available communications capacity is shared between the nodes that are connected to the same media. Media access control (MAC) refers to the methods a network technology uses to determine when nodes can communicate on shared media and to deal with possible problems, such as two devices attempting to communicate simultaneously.

Ethernet uses a contention-based MAC system. Each network node connected to the same media is in the same collision domain. When two nodes transmit at the same time, the signals are said to collide and neither signal can reach its destination. This means that they must be re-sent, reducing available bandwidth.

The Ethernet protocol governing contention and media access is called Carrier Sense Multiple Access with Collision Detection (CSMA/CD). A collision is the state when a signal is present on an interface’s transmit and receive lines simultaneously. On detecting a collision, the node broadcasts a jam signal. Each node that was attempting to use the media then waits for a random period (backoff) before attempting to transmit again.


The collision detection mechanism means that only half-duplex transmission is possible. This means that a node can transmit or receive, but it cannot do both at the same time.

100BASE-TX Fast Ethernet Standard

The Fast Ethernet standard uses the same CSMA/CD protocol as 10BASE-T but with higher frequency signaling and improved encoding methods raising the bit rate from 10 Mbps to 100 Mbps. 100BASE-TX refers to Fast Ethernet working over Cat 5 (or better) twisted pair copper cable with a maximum supported link length of 100 meters (328 feet).

To support compatibility with hosts still equipped with 10 Mbps Ethernet interfaces, Fast Ethernet introduced an auto negotiation protocol to allow a host to choose the highest supported connection parameters (10 or 100 Mbps and half or full duplex). 10BASE-T Ethernet specifies that a node should transmit regular electrical pulses when it is not transmitting data to confirm the viability of the link. Fast Ethernet codes a 16-bit data packet into this signal advertising its service capabilities. This is called a Fast Link Pulse. A node that does not support auto negotiation can be detected by one that does and send ordinary link integrity test signals, or Normal Link Pulses.

Gigabit Ethernet Standards

Gigabit Ethernet builds on the standards defined for Ethernet and Fast Ethernet to implement rates of 1000 Mbps (1 Gbps). Over copper wire, Gigabit Ethernet is specified as 1000BASE-T, working over Cat 5e or better. Gigabit Ethernet does not support hubs; it is implemented only using switches. The maximum distance of 100 m (328 feet) applies to cabling between the node and a switch port, or between two switch ports.

10 Gigabit Ethernet (10GbE) multiplies the nominal speed of Gigabit Ethernet by a factor of 10. Because of the higher frequencies required, 10 GbE can only run at reduced distances over unshielded twisted pairs. Longer runs require higher categories of cable with some type of shielding

Topic 2B: Summarize Copper Cabling Types

Unshielded Twisted Pair Cable Considerations

Twisted pair is a type of copper cable that has been extensively used for telephone systems and data networks. One pair of insulated wires twisted together forms a balanced pair. The pair carry the same signal but with different polarity; one wire is positive, and the other is negative. This allows the receiver to distinguish the signal from any noise more strongly. The cable is completed with an insulating outer jacket.

Twisted pair can use either solid or stranded conductor wires. Solid cabling uses a single thick wire per conductor and is used for cables that run behind walls or through ducts. Stranded cabling uses thin filament wires wrapped around one another and is used to make flexible patch cords for connecting computers to wall ports and switch ports to patch panel ports. Copper wire thickness is measured using American Wire Gauge (AWG). Increasing AWG numbers represent thinner wire. Solid cable uses thicker 22 to 24 AWG, while the stranded cable used for patch cords is often 26 AWG. The attenuation of stranded wire is higher than solid wire, so it cannot be used over extended distances.

Shielded and Screened Twisted Pair Cable Considerations

Shielded cable is less susceptible to interference and crosstalk. This type of cable is required for some Ethernet standards and may also be a requirement in environments with high levels of interference.

Shielded cable can be referred to generically as shielded twisted pair (STP), but there are actually several types of shielding:

●	Screened cable has one thin outer foil shield around all pairs. Screened cable is usually designated as screened twisted pair (STP) or foiled/unshielded twisted pair (F/UTP), or sometimes just foiled twisted pair (FTP).

●	Fully shielded cabling has a braided outer screen and foil-shielded pairs and is referred to as shielded/foiled twisted pair (S/FTP). There are also variants with a foil outer shield (F/FTP).

Cat Cable Standards

The American National Standards Institute (ANSI) and the Telecommunications Industry Association (TIA)/Electronic Industries Alliance (EIA) have created categories of cable standards for twisted pairs to simplify selection of a suitable quality cable. These categories, along with other aspects of telecommunications wiring best practices, are defined in the ANSI/TIA/EIA 568 Commercial Building Telecommunications Cabling Standards ( tiaonline.org/standard/tia-568 ). Similar standards are also maintained by the ISO (ISO/IEC 11801), which refers to categories of components and classes of permanent links (incorporating both cable and termination).

●	Cat/Class: 3

○	Cable Type: UTP

○	Network Application: 10BASE-T

○	Max Distance: 100m (328ft)

○	Frequency: 16 MHz

○	Connector: RJ-45

●	Cat/Class: 5

○	Cable Type: UTP

○	Network Application: 100BASE-TX

○	Max Distance: 100m (328ft)

○	Frequency: 100 MHz

○	Connector: RJ-45

●	Cat/Class: 5e (Class D)

○	Cable Type: UTP or F/UTP

○	Network Application: 1000BASE-T

○	Max Distance: 100m (328ft)

○	Frequency: 100 MHz

○	Connector: RJ-45

●	Cat/Class: 6 (Class E)

○	Cable Type: UTP, F/UTP, or U/FTP

○	Network Application: 1000BASE-T, 10GBASE-T

○	Max Distance: 100m (328ft), 55m (180ft)

○	Frequency: 250 MHz

○	Connector: RJ-45

●	Cat/Class: 6a (Class Ea)

○	Cable Type: UTP, F/UTP, U/FTP, or S/FTP

○	Network Application: 10GBASE-T

○	Max Distance: 100m (328ft)

○	Frequency: 500 MHz

○	Connector: RJ-45

●	Cat/Class: 7 (Class F)

○	Cable Type: S/FTP or F/FTP

○	Network Application: 10GBASE-Tv

○	Max Distance: 100m (328ft)

○	Frequency: 600 MHz

○	Connector: GG45/TERA

●	Cat/Class: 8/8.1 (Class I)

○	Cable Type: U/FTP or F/UTP

○	Network Application: 40GBASE-T

○	Max Distance: 30m (100ft)

○	Frequency: 2000 MHz

○	Connector: RJ-45

●	Cat/Class: 8.2

○	Cable Type: F/FTP or S/FTP

○	Network Application: 40GBASE-T

○	Max Distance: 30m (100ft)

○	Frequency: 2000 MHz

○	Connector: GG45/TERA

Here are some details about the categories used for network media:

●	Cat 5 cable is no longer available. Cat 5e is tested at frequencies up to 100 MHz (like Cat 5 was) but to higher overall specifications for attenuation and crosstalk, meaning that the cable is rated to handle Gigabit Ethernet throughput. Cat 5e would still be an acceptable choice for providing network links for workstations.

For 1000BASE-T, Cat 5 is also acceptable (if properly installed), but Cat 5 cable is no longer available commercially. Unlike Ethernet and Fast Ethernet, Gigabit Ethernet uses all four pairs for transmission and is thus more sensitive to crosstalk between the wire pairs.

●	Cat 6 can support 10 Gbps but over shorter distances-nominally 55 m, but often less if cables are closely bundled together.

●	Cat 6A is an improved specification cable that can support 10 Gbps over 100 m. Cat 6A cable is bulkier than Cat 5e, and the installation requirements are more stringent, so fitting it within pathways designed for older cable can be problematic. TIA/EIA standards recommend Cat 6A is recommended for use in health care facilities, with Power over Ethernet (PoE) 802.3bt installations, and for horizontal connections to wireless access points.

●	Cat 7 cable is always of a screened/shielded type and is rated for 10GbE applications up to 100 m (328 feet). Cat 7 is not recognized by TIA/EIA but appears in the cabling standards created by the ISO (ISO/IEC 11801). It must be terminated with GG45 or TERA connectors rather than standard RJ-45 connectors.

Cabling is not the only part of the wiring system that must be rated to the appropriate category. For faster network applications (Gigabit Ethernet and better), the performance of connectors becomes increasingly critical. For example, if you are installing Cat 6A wiring, you must also install Cat 6A patch panels, wall plates, and connectors.

●	Cat 8 is intended for use in data centers only for short patch cable runs that make top-of-rack connections between adjacent appliances. ISO defines two variants; 8.1 (Class I) is equivalent to TIA/EIA Cat 8 and uses RJ-45 connectors while 8.2 (Class II) must use outer shielding or screening and GG-45 or TERA connectors.

COPPER TERMINATION STANDARDS

Each conductor in a 4-pair data cable is color-coded. Each pair is assigned a color (Blue, Orange, Green, or Brown). The first conductor in each pair has a predominantly white insulator with strips of the color; the second conductor has an insulator with the solid color. The ANSI/TIA/EIA 568 standard defines two methods for terminating Ethernet connectors: T568A and T568B. The wiring for both standards is shown in the following figure.

T568A and T568B wiring diagrams. (Images © 123RF.com.)

In T568A, the green pairs are wired to pins 1 and 2 and the orange pairs are wired to pins 3 and 6. In T568B, these pairs swap places, so orange is terminated to pins 1 and 2 and green to 3 and 6. Organizations should try to avoid using a mixture of the two standards. T568A is mandated by the US government and by the residential cabling standard (TIA 570), but T568B is probably the more widely deployed of the two.


Pin	Wire Color (T568A)	Wire Color (T568B)	10/100 Mbps	1/10/40 Gbps

1. `	`Green/White	Orange/White	Tx+	BixA+
1. `	`Green	Orange	Tx-	BixA-
1. `	`Orange/White	Green/White	Rx+	BixB+
1. `	`Blue	Blue		BixB-
1. `	`Blue/White	Blue/White		BixC+
1. `	`Orange	Green	Rx-	BixC-
1. `	`Brown/White	Brown/White		BixD+
1. `	`Brown	Brown		BixD-

Cat 7 and Cat 8 are so sensitive to noise that the secondary wire in each pair is solid white with no stripe, as the coloring process reduces the effectiveness of the insulation.



Topic 2C: Summarize Fiber Optic Cabling Types

Fiber Optic Cable Considerations

Fiber optic signaling uses pulses of infrared light, which are not susceptible to interference, cannot be easily intercepted, and suffer less from attenuation. Consequently, fiber optic cabling supports higher bandwidth over longer cable runs (that can be measured in kilometers, rather than meters).

A single optical fiber is constructed from three elements:

●	Core provides the transmission path for the light signals (waveguide).

●	Cladding reflects signals back into the waveguide as efficiently as possible so that the light signal travels along the waveguide by multiple internal reflections. The core and cladding can be made from glass or plastic. The cladding is applied as a thin layer surrounding the core. While made of the same material, the cladding has a different refractive index to the core. The effect of this is to create a boundary that causes the light to bounce back into the core, facilitating the process of total internal reflection that guides the light signal through the core.

●	Buffer is a protective plastic coating. It may be of a tight or loose configuration, with the loose format using some form of lubricant between the strand and the sheath.

In basic operation modes, each fiber optic strand can only transfer light in a single direction at a time. Therefore, multiple fibers are often bundled within a cable to allow simultaneous transmission and reception of signals or to provide links for multiple applications.

Single Mode Fiber and Multimode Fiber

Fiber optic cables fall into two broad categories: single mode and multimode.

●	Single Mode Fiber (SMF): Has a small core (8 to 10 microns) and a long wavelength, near infrared (1310 nm or 1550 nm) light signal, generated by a laser. Single mode cables support data rates up to 100 Gbps and cable runs of many kilometers, depending on the quality of the cable and optics. There are two grades of SMF cable; OS1 is designed for indoor use, while OS2 is for outdoor deployment.

●	Multimode Fiber (MMF): Has a larger core (62.5 or 50 microns) and shorter wavelength light (850 nm or 1300 nm) transmitted in multiple waves of varying length. MMF uses less expensive optics and consequently is less expensive to deploy than SMF. However, it does not support such high signaling speeds or long distances as single mode and so is more suitable for LANs than WANs.

\*\*Optical transceivers for SMF are now only slightly more expensive than ones for MMF. Consequently, SMF is often used for short range applications in data centers, as well as for long distance links. SMF still comes at a slight price premium, but provides better support for 40 Gbps and 100 Gbps Ethernet standards.

MMF is graded by Optical Multimode (OM) categories, defined in the ISO/IEC 11801 standard:

●	OM1/OM2: 62.5-micron cable is OM1, while early 50-micron cable is OM2. OM1 and OM2 are mainly rated for applications up to 1 Gbps and use LED transmitters.

●	OM3/OM4: These are also 50-micron cable, but manufactured differently, designed for use with 850 nm Vertical-Cavity Surface-Emitting Lasers (VCSEL), also referred to as laser optimized MMF (LOMMF). A VCSEL is not as powerful as the solid-state lasers used for SMF, but it supports higher modulation (transmitting light pulses rapidly) than LED-based optics.

Fiber Optic Connector Types

Straight Tip: An early bayonet-style connector that uses a push-and-twist locking mechanism. ST was used mostly for multimode networks, but it is not widely used for Ethernet installations anymore.

Subscriber connector: SC is a push-pull design, allowing for simple insertion and removal. It can be used for single or multimode. It is commonly used for Gigabit Ethernet.

Local connector: LC is a small-form-factor connector with a tabbed push-pull design. LC is similar to SC, but the smaller size allows for higher port density. LC is a widely adopted form factor for Gigabit Ethernet and 10/40 GbE.

Mechanical Transfer Registered Jack: MTRJ is a small-form-factor duplex connector with a snap-in design used for multimode networks.

FIBER ETHERNET STANDARDS

Ethernet standards over fiber set out the use of different types of cable for 100 Mbps, 1 Gbps, and 10 Gbps operation. There are variants for long wavelength optics, required for long distance transmission, and short wavelength optics.

●	Specification: 100BASE-FX

○	Optics: 1300nm

○	Cable: MMF (OM1), MMF (OM2)

○	Maximum Distance: 2km (1.2 miles)

○	Connectors: ST, SC, MT-RJ

●	Specification: 100BASE-SX

○	Optics: 850nm

○	Cable: MMF (OM1), MMF (OM2)

○	Maximum Distance: 550m (1804ft)

○	Connectors: ST, SC, LC

●	Specification: 1000BASE-SX

○	Optics: 850nm

○	Cable: MMF (OM1), MMF (OM2):MMF (OM3)

○	Maximum Distance: 275m (902ft), 550m (1804ft)

○	Connectors: ST, SC, LC, MT-RJ

●	Specification: 1000BASE-LX

○	Optics: 1300nm, 1310nm

○	Cable: MMF (OM1):MMF (OM2): MMF (OM3), SMF (OS1/OS2)

○	Maximum Distance: 550m (1804ft), 5km (3.1 miles)

○	Connectors: SC, LC

●	Specification: 10GBASE-SR

○	Optics: 850nm

○	Cable: MMF (OM1), MMF (OM2), MMF (OM3), MMF (OM4)

○	Maximum Distance: 33m (108ft), 82m (269 ft), 300m (984 ft), 400m (1312ft)

○	Connectors: SC, LC

●	Specification: 10GBASE-LR

○	Optics: 1310nm

○	Cable: SMF (OS1/OS2)

○	Maximum Distance: 10km (6.2 miles)

○	Connectors: SC, LC

Fiber is often used for backbone cabling in office networks and for workstations with high bandwidth requirements, such as video editing. The principal applications of 10 GbE (and better) are:

●	Increasing bandwidth for server interconnections and network backbones, especially in datacenters and for storage area networks (SAN).

●	Replacing existing switched public data networks based on proprietary technologies with simpler Ethernet switches (Metro Ethernet).

Fiber Optic Cable Installation

Fiber optic can be installed in the same topology as copper cable using distribution frames and switches. Long distance cables are typically laid as trunks or rings with repeaters or amplifiers between cable segments to strengthen the signal.

Normally, strands are installed in pairs (duplex) at each device, with one strand for transmit (Tx) and one strand for receive (Rx).

Patch cables for fiber optic can come with the same connector on each end (LC-LC, for instance) or a mix of connectors (LC-SC, for instance.) Duplex patch cords must maintain the correct polarity, so that the Tx port on the transmitters is linked to the Rx port on the receiver and vice versa. The TIA/EIA cabling standard sets out A to B patch cord to port orientations. Each element in the link must perform a crossover, and there must be an odd number of elements, such as two patch cords and a permanent link (three elements).


Most connectors are keyed to prevent incorrect insertion, but if in doubt, an optical power meter can be used to determine whether an optical signal is being received from a particular fiber.

\*\*Transmitted optical signals are visible as bright white spots when viewed through a smartphone camera. This can be used to identify which adapter on an optical interface is transmitting and which fiber patch cord is receiving a signal from the other end of the cable.

Finishing Type

The core of a fiber optic connector is a ceramic or plastic ferrule that holds the glass strand and ensures continuous reception of the light signals. The tip of the ferrule can be finished in one of three formats:

●	Physical contact (PC): The faces of the connector and fiber tip are polished so that they curve slightly and fit together better, reducing return loss (interference caused by light reflecting back down the fiber).

●	UltraPhysical Contact (UPC): This means the cable and connector are polished to a higher standard than with PC.

●	Angled Physical Contact (APC): The faces are angled for an even tighter connection and better return loss performance. APC cannot be mixed with PC or UPC. These connectors are usually deployed when the fiber is being used to carry analog signaling, as in Cable Access TV (CATV) networks. They are also increasingly used for long distance transmissions and for Passive Optical Networks (PON), such as those used to implement Fiber to the x (FTTx) multiple subscriber networks.

Where there are multiple strands within a single cable, the strands are color-coded (TIA/EIA 598) to differentiate them. Also, by convention, cable jackets and connectors use the following color-coding:

●	OM1

○	Jacket Color: Orange

○	Connector Color: Beige

●	OM2

○	Jacket Color: Orange

○	Connector Color: Black

●	OM3/OM4

○	Jacket Color: Aqua

○	Connector Color: Aqua

●	SMF PC/UPC

○	Jacket Color: Yellow

○	Connector Color: Blue

●	SMF APC

○	Jacket Color: Yellow

○	Connector Color: Green


Topic 2D: Deploy Ethernet Cabling

Structured Cabling System

Cabled networking for client access in an office building will use a structured cabling scheme, such as that set out in the ANSI/TIA/EIA 568 Commercial Building Telecommunications Wiring Standard. ANSI/TIA/EIA 568 identifies the following subsystems within a structured cabling system:

●	Work Area: The space where user equipment is located and connected to the network, usually via a wall port.

●	Horizontal Cabling: Connects user work areas to the nearest horizontal cross-connect. A cross-connect can also be referred to as a distribution frame. Horizontal cabling is so-called because it typically consists of the cabling for a single floor and so is made up of cables run horizontally through wall ducts or ceiling spaces.


●	

●	Backbone Cabling: Connects horizontal cross-connects (HCCs) to the main cross-connect (optionally via intermediate cross-connects). These can also be described as vertical cross-connects, because backbone cabling is more likely to run up and down between floors.

●	Telecommunications Room: Houses horizontal cross-connects. Essentially this is a termination point for the horizontal cabling along with a connection to backbone cabling. An equipment room is similar to a telecommunications room but contains the main or intermediate cross-connects. Equipment rooms are also likely to house “complex” equipment, such as switches, routers, and modems.

●	Entrance Facilities/Demarc: Special types of equipment rooms marking the point at which external cabling (outside plant) is joined to internal (premises) cabling. These are required to join the access provider’s network and for inter-building communications. The demarcation point is where the access provider’s network terminates and the organization’s network begins.

Cable Management

Cable management techniques and tools ensure that cabling is reliable and easy to maintain. Copper wiring is terminated using a distribution frame or punch down block. A punch down block comprises a large number of insulation-displacement connection (IDC) terminals. The IDC contains contacts that cut the insulation from a wire and holds it in place.

●	66 Block: An older-syle distribution frame used to terminate telephone cabling and legacy data applications (pre-Cat 5). A 66 block comprises 50 roots of 4 IDC terminals. The 25-pair cable from the access provider is terminated on one side of the block. On the other side of the block, the terminals terminate the wiring from the PBX. A jumper (bridging clip) is installed over the middle two terminals to complete the connection.

●	110 Block: The 110 block (developed by AT&T) is a type of distribution frame supporting 100 MHz operation (Cat5 ) and better. A 110 wiring block is arranged horizontally rather than vertically, offering better density than a 66 block. There is also more space for labeling the connectors and each column of connectors is color-coded, making management simpler. The incoming wire pairs are fed into channels on the wiring block, then a connector block or wafer is installed to terminate the incoming wiring. Outgoing wiring pairs are then punched into the terminals on the connector blocks to complete the circuit.

●	BIX and Krone Distribution Frames: Where a 110 block uses a two-piece design where wafer blocks are installed over the main block, competing formats BIX and Krone use a single module. The IDCs are angled differently in each format, requiring a different termination blade to be used to ensure a reliable connection.

●	Patch Panel/Patch Bay: In data networks, numerous moves, adds, and changes (MACs) would require reterminating the wiring. To simplify MACs, a patch panel or patch bay is a type of distribution block with IDCs on one side and pre-terminated RJ-45 modular ports on the other. This allows incoming and outgoing connections to be reconfigured by changing the patch cable connections, which is much simpler than reterminating punch down blocks.


Fiber distribution Panels and Fusion Splicing

Permanent cables are run through conduit to wall ports at the client access end and a fiber distribution panel at the switch end. Fiber patch cables are used to complete the link from the wall port to the NIC and from the patch panel to the switch port.

Using connectors does reduce the overall performance of the cable. Each connector will “cost” a certain amount of insertion loss (typically budgeted as 0.5 dB) and reflection loss. Consequently, in some circumstances it may be preferable to splice two cables together, either to repair damage or to extend the cable run. Cables can be spliced mechanically using an adhesive junction box containing index matching fluid that ensures a continuous path between the two fiber strands. A fusion splicer achieves a more permanent join with the lower insertion loss (>=0.1 dB). Thus a fusion splicing machine performs a precise alignment between the two strands and then permanently joins them together using an arc weld. A fusion splicer is a high-precision instrument and must be kept clean and maintained following the manufacturer’s guidelines.

Splicing may also be used to attach a pigtail (a segment of cable with a factory-fitted connector at one end only) or to field terminate to a connector (splicing a factory-prepared SC or LC connector to an incoming cable). A spliced cable or pigtail must be protected with a special cover and supported by a splice tray. Connectors for field terminated splicing do not require a tray and the protective cover is built into the connector.

Transceivers

A network might involve the use of multiple types of cabling. When this occurs, switch and router equipment must be able to terminate different cable and connector types, and devices must convert from one media type to another. Enterprise switches and routers are available with modular, hot-swappable transceivers/media converters for different types of fiber optic patch cord connections.

SFP/SFP+(mini-GBIC)

Small form factor pluggable (SFP) uses LC connectors and is also designed for Gigabit Ethernet. Enhanced SFP (SFP+) is an updated specification to support 10 GbE but still uses the LC form factor. There are different modules to support the various Ethernet standards and fiber mode type (10GBASE-SR versus 10GBASE-LR, for instance). Consequently, a transceiver is designed to support a specific wavelength The transceivers must be installed as matched pairs.

\*\*You will often see the term MSA in conjunction with modular transceivers. Multi-Source Agreement (MSA) is intended to ensure that a transceiver from one vendor is compatible with the switch/router module of another vendor.

QSFP/QSFP+

Quad small form-factor pluggable (QSFP) is a transceiver form factor that supports 4 x 1 Gbps links, typically aggregated to a single 4 Gbps channel. Enhanced quad small form-factor pluggable (QSFP+) is designed to support 40 GbE by provisioning 4 x 10 Gbps links. QSFP+ is typically used with parallel fiber and multi-fiber push-on (MPO) termination. An MPO backbone ribbon cable bundles 12 or more strands with a single compact terminator (the cables are all manufactured and cannot be field terminated). When used with QSFP+, four strands transmit a full-duplex 40 Gbps link, four strands receive, and the other four strands are unused.

QSFP+ can also be used with Wavelength Division Multiplexing (WDM) Ethernet standards.

Wavelength Division Multiplexing

Ordinary (or “grey”) SFP/SFP+ are duplex interfaces with one transmit port and one receive port that require two fiber strands. Each strand is a single channel. Wavelength Division Multiplexing (WDM) is a means of using a strand to transmit and/or receive more than one channel at a time.

●	BiDirectional Wavelength Division Multiplexing: BiDi transceivers support transmit and receive signals over the same strand of fiber. This uses WDM to transmit the Tx and Rx signals over slightly shifted wavelengths, such as 1310 nm for Tx and 1490 for Rx. BiDi transceivers must be installed in opposite pairs, so the downstream transceiver would have to use 1490 nm for Tx and 1310 for Rx. Bidirectional wavelength division multiplexing (WDM) links are documented in Ethernet standards (1000BASE-BX and 10GBASE-BX).

●	Coarse and Dense Wavelength Division Multiplexing: Coarse Wavelength Division Multiplexing (CWDM) supports up to 16 wavelengths and is typically used to deploy four or eight bidirectional channels over a single fiber strand. Dense Wavelength Division Multiplexing (DWDM) provisions greater numbers of channels (20, 40, 80, or 160). This means that there is much less spacing between each channel and requires more precise and expensive lasers. CWDM and DWDM transceivers support multi-channel 1 G, 10 G, and 40 G Ethernet links. As with BiDi, the transceivers must be installed in opposite pairs for each channel.

In a point-to-point WDM topology, each transceiver is cabled to a multiplexer/demultiplexer (mux/demux). The single fiber strand is run to a mux/demux at the other site. Alternatively, devices called optical add/drop multiplexers (OADM) can insert and remove signals for a particular wavelength channel on a ring topology.
