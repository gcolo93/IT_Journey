Lesson 15: Deploying and Troubleshooting Wireless Networks

Topic 15A: Summarize Wireless Standards

IEEE 802.11 WIRELESS STANDARDS

Most wireless LANs (WLANs) are based on the IEEE 802.11 standards, better known by its brand name Wi-Fi. 802.11 standards define the physical layer media by which data is encoded into a radio carrier signal by using a modulation scheme. The properties of radio waves include amplitude (the height of peaks and troughs), frequency (the number of peaks per unit of time), and phase (the angle of a wave at a point in time). Modulation changes one or more of those properties to encode a signal. As well as modulation schemes, Wi-Fi standards use different carrier methods to provide sufficient resistance to interference from noise and other radio sources.

A wireless radio transmitting and receiving within a particular range of frequencies with the same modulation scheme is a half-duplex shared access medium (a physical bus). 802.11 uses Carrier Sense Multiple Access with Collision Avoidance (CSMA/CA) to cope with contention. Under CSMA/CA, when a station receives a frame, it performs error checking. If the frame is intact, the station responds with an acknowledgment (ACK). If the ACK is not received, the transmitting station resends the frame until timing out. 802.11 also defines a Virtual Carrier Sense flow control mechanism to further reduce the incidence of collisions. A station broadcasts a Request to Send (RTS) with the source and destination and the time required to transmit. The receiving station responds with a Clear To Send (CTS) and all other stations in range do not attempt to transmit within that period.

The CSMA/CA media access method. (Images © 123RF.com.)

The original 802.11 Wi-Fi standard worked only at 1 Mbps, but like the 802.3 Ethernet standard, it has been revised many times, with each iteration specifying different signaling and transmission mechanisms. Products conforming to the various standards can be certified by the Wi-Fi Alliance (wi-fi.org).

IEEE 802.11A AND 5 GHZ CHANNEL BANDWIDTH

Every wireless device operates on a specific radio frequency range within an overall frequency band. The specific frequency range is referred to as a channel . It is important to understand the difference between the two frequency bands used by the IEEE 802.11 standards:

●	2.4 GHz is better at propagating through solid surfaces, making it ideal for providing the longest signal range. However, the 2.4 GHz band does not support a high number of individual channels and is often congested, both with other Wi-Fi networks and other types of wireless technology, such as Bluetooth®. Consequently, with the 2.4 GHz band, there is increased risk of interference, and the maximum achievable data rates are typically lower than with 5 GHz.

●	5 GHz is less effective at penetrating solid surfaces and so does not support the maximum ranges achieved with 2.4 GHz standards, but the band supports more individual channels and suffers less from congestion and interference, meaning it supports higher data rates at shorter ranges.

The IEEE 802.11a standard specifies use of the 5 GHz frequency band and a multiplexed carrier scheme called Orthogonal Frequency Division Multiplexing (OFDM). 802.11a has a nominal data rate of 54 Mbps.

The 5 GHz band is subdivided into 23 non-overlapping channels, each of which is 20 MHz wide. Initially, there were 11 channels, but the subsequent 802.11h standard added another 12. 802.11h also adds the Dynamic Frequency Selection (DFS) method to prevent access points (APs) working in the 5 GHz band from interfering with radar and satellite signals. The exact use of channels can be subject to different regulations in different countries. Regulatory impacts also include a strict limit on power output, constraining the range of Wi-Fi devices.

IEEE 802.11B/G AND 2.4 GHZ CHANNEL BANDWIDTH

The 802.11b standard uses the 2.4 GHz frequency band and was released in parallel with 802.11a. It standardized the use of the carrier method Direct Sequence Spread Spectrum (DSSS), along with Complementary Code Keying (CCK) signal encoding. While in some ways DSSS was an inferior technology to OFDM-with a nominal data rate of just 11 Mbps-802.11b products were quicker to market and became better established than 802.11a.

The 2.4 GHz band is subdivided into up to 14 channels, spaced at 5 MHz intervals from 2412 MHz up to 2484 MHz. Because the spacing is only 5 MHz and Wi-Fi needs ~20 MHz channel bandwidth, 802.11b channels overlap quite considerably. This means that co-channel interference is a real possibility unless widely spaced channels are chosen (1, 6, and 11, for instance). Also, in the Americas, regulations permit the use of channels 1-11 only, while in Europe channels 1-13 are permitted, and in Japan all 14 channels are permitted.

Channel overlap in the 2.4 GHz band.

The 802.11g standard offered a relatively straightforward upgrade path from 802.11b. Like 802.11a, 802.11g uses OFDM, but in the 2.4 GHz band used by 802.11b and with the same channel layout. This made it straightforward for vendors to offer 802.11g devices that could offer backwards support for legacy 802.11b clients. 802.11g has a nominal data rate of 54 Mbps. When in 802.11b compatibility mode, it drops back to using DSSS.

IEEE 802.11N, MIMO, AND CHANNEL BONDING

The 802.11n standard increases bandwidth by multiplexing the signals from 2 to 4 separate antennas (a radio chain) using a collection of technologies generally referred to as Multiple Input Multiple Output (MIMO). The configuration of an 802.11n radio chain is identified by AxB:C notation, where A is the number of transmit antennas, B is the number of receive antennas, and C is the number of simultaneous transmit and receive streams. The maximum possible is 4x4:4, but common configurations are 2x2:2 or 3x3:2. For example, a 4x4:4 access point could allocate two streams carrying different data to a 2x2:2 client, increasing bandwidth. This is referred to as spatial multiplexing.

Having more transmit and receive antennas can also be used to improve signal reliability, rather than boosting bandwidth. If the same data stream is sent by two or three transmit antennas, the receiver can combine them to derive a stronger signal and increase range at a given data rate. Similarly, multiple receive antennas can derive a stronger signal, even if there is only one transmit stream. This is referred to as spatial diversity. For example, 2x2:2 and 2x3:2 radio chains have the same throughput, but the 2x3:2 chain could make more use of spatial diversity to increase range.

802\.11n products can also use channels in the 2.4 GHz band or the 5 GHz band. 802.11n also allows two adjacent 20 MHz channels to be combined into a single 40 MHz channel, referred to as channel bonding. Due to the restricted bandwidth of 2.4 GHz, on a network with multiple APs, channel bonding is a practical option only in the 5 GHz band. The 5 GHz band has a larger frequency range (up to 500 MHz in the USA), so it can provide up to 23 nonoverlapping channels. However, those channels are not necessarily contiguous, which slightly reduces the options for bonded channels.

Bonded channel options in the 5 GHz Unlicensed National Information Infrastructure (U-NII) sub-bands. Channels within the DFS range may be disabled if the site is near a radar transmitter.

Cheaper client adapters may support only the 2.4 GHz band. An access point (AP) or adapter that can support both is referred to as dual band. A dual band AP can support both 2.4 GHz and 5 GHz bands simultaneously. This allows legacy clients to be allocated to the 2.4 GHz band.

The data rate for 802.11n is 72 Mbps per stream. Assuming the maximum number of four spatial streams and optimum conditions, the nominal data rate could be as high as 600 Mbps for a 40 MHz bonded channel. 802.11n can work in High Throughput (HT)/greenfield mode for maximum performance or HT mixed mode for compatibility with older standards (801.11a-ht, 802.11b-ht, and 802.11g-ht). Mixed mode reduces overall WLAN performance, as it involves the transmission of legacy identification and collision avoidance frames (HT protection) but not to the extent that 802.11n devices are reduced to (say) 802.11g data rates. Operating in greenfield mode is likely to cause substantial interference if there are legacy WLANs operating nearby on the same channel(s). There is also a legacy (non-HT) mode, in which 802.11n's HT mechanisms are disabled completely. You might use this mode if you have an 802.11n-capable access point but don't have any 802.11n client devices.

In recent years, Wi-Fi standards have been renamed with simpler digit numbers. 802.11n is now officially designated as Wi-Fi 4.

WI-FI 5 AND WI-FI 6

The Wi-Fi 5 (or 802.11ac) and Wi-Fi 6 (802.11ax) standards continue the development of Wi-Fi technologies to increase bandwidth and support modern networks.

Wi-Fi 5 (802.11ac)

Wi-Fi 5 is designed to work only in the 5 GHz band. The 2.4 GHz band can be used for legacy standards (802.11g/n) in mixed mode. The aim for Wi-Fi 5 is to get throughput like that of Gigabit Ethernet or better. It supports more channel bonding (up to 80 or 160 MHz channels), up to 8 spatial streams, rather than 4, and denser modulation (at close ranges). The way Wi-Fi 5 uses the radio spectrum is designated as very high throughput (VHT).

As with 802.11n, only enterprise-class equipment is equipped with enough antennas to make use of three streams or more, and no devices were ever produced with more than 4x4:4 streams. Wi-Fi 5 access points are marketed using AC values, such as AC5300. The 5300 value represents 1000 Mbps over a 40 MHz 2.4 GHz band channel and two 2,167 Mbps streams over 80 MHz 5 GHz band channels.

Wi-Fi 6 (802.11ax)

Wi-Fi 6 uses more complex modulation and signal encoding to improve the amount of data sent per packet by about 40%. As with Wi-Fi 5, products are branded using the combined throughput. For example, AX6000 allows 1,148 Mbps on the 2.4 GHz radio and 4,804 over 5 GHz.

The way Wi-Fi 6 uses the radio spectrum is designated as high efficiency (HE) to reflect these improvements. The aim for Wi-Fi 6 is to approximate 10G connection speeds (AX11000). These data rates can only be achieved through use of a new 6 GHz frequency band.

Wi-Fi 6 reinstates operation in the 2.4 GHz band, mostly to support Internet of Things (IoT) device connectivity. In Wi-Fi 6, the OFDM with multiple access (OFDMA) modulation scheme allows sub-carriers or tones to be allocated in groups of different sizes, referred to as resource units (RUs), each of which can communicate in parallel. Where small RUs are used, this reduces throughput but provides more opportunities for a larger number of devices to transmit. The effect is to reduce latency where numerous small data packets are being transmitted. This technology provides better support for IoT devices. Stations that require more bandwidth can be assigned larger RUs. RUs can also be assigned based on class of service parameters, such as prioritizing voice over IP (VoIP) traffic. It also allows an access point to support legacy (Wi-Fi 4/5 stations) efficiently.

MULTIUSER MIMO

In basic 802.11 operation modes, bandwidth is shared between all stations because of the CSMA/CA contention protocol. An AP can communicate with only one station at a time; multiple station requests go into a queue. Wi-Fi 5 and Wi-Fi 6 products address this problem using beamforming or Multiuser MIMO (MU-MIMO).

Downlink MU-MIMO (DL MU-MIMO) allows the AP to use its multiple antennas to process a spatial stream of signals in one direction separately to other streams. This means that groups of stations on a different alignment can connect simultaneously and also obtain more bandwidth. For example, if four stations are positioned north, south, east, and west of a 4x4:4 AP, the AP should be able to allow each of them to connect at close to the maximum speed. If another station is added to the north, those two northern stations will share the available bandwidth along that beam path. Both stations and AP must support MU-MIMO. Where Wi-Fi 5 supports up to four stations communicating in parallel over 5 GHz only, Wi-Fi 6 can support up to eight in 2.4 GHz, 5 GHz, and 6 GHz bands, giving it better performance in congested areas.

With DL MU-MIMO, only the AP can initiate beamforming, so it is only available on the downlink from AP to station (not station to AP). Wi-Fi 6 supports uplink MU-MIMO (UL MU-MIMO), allowing stations to initiate beamforming with the access point.

For both Wi-Fi 5 and Wi-Fi 6, improvements are released to the market in waves. For example, UL MU-MIMO was released in wave 2 Wi-Fi 6 products, which also added support for the 6 GHz frequency band.

MU-MIMO and OFDMA are different but complementary technologies. MU-MIMO makes use of spatial streams, whereas OFDMA makes flexible use of subcarriers within a channel. Both can work together to increase parallelism (supporting communication with more devices simultaneously).

2G AND 3G CELLULAR TECHNOLOGIES

Where Wi-Fi is typically operated as private infrastructure, cellular radio is operated by telecommunications providers. A cellular radio establishes a connection using the nearest available cell or base station. Each base station has an effective range of up to 5 miles (8 km). The base station links the device to global telecommunications networks. Cellular radio works in the 850 and 1900 MHz frequency bands (mostly in the Americas) and the 900 and 1800 MHz bands (rest of the world).

Cellular digital communications standards are described as belonging to a generation. For 2G, there were two competing formats, established in different markets:

●	Global System for Mobile Communication (GSM)-based phones using Time Division Multiple Access (TDMA). With TDMA, each subscriber gets access to the radio channel by being allocated a time slot. GSM allows subscribers to use a subscriber identity module (SIM) card to use an unlocked handset with their chosen network provider. GSM is adopted internationally and by AT-and-T and T-Mobile in the United States.

●	TIA/EIA IS-95 (cdmaOne)-based handsets, using Code Division Multiple Access (CDMA). CDMA means that each subscriber uses a code to key the modulation of their signal and this "key" is used by the receiver to extract the subscriber's traffic from the radio channel. With CDMA, the handset is managed by the provider, not the SIM. CDMA adoption is largely restricted to the telecom providers Sprint and Verizon.

In both cases, the cell network was built primarily to support voice calls, so 2G data access was provided on top, using Circuit Switched Data (CSD). CSD is somewhat similar to a dial-up modem, though no analog transmissions are involved. CSD requires a data connection to be established to the base station (incurring call charges) and is only capable of around 14.4 Kbps at best.

The transition from 2G to 3G saw various packet-switched technologies deployed to mobiles:

●	General Packet Radio Services/Enhanced Data Rates for GSM Evolution (GPRS/EDGE) is a precursor to 3G (2.5G), with GPRS offering up to about 48 Kbps and EDGE about 3-4 times that. Unlike CSD, GPRS and EDGE allow "always on" data connections, with usage billed by bandwidth consumption rather than connection time.

●	Evolved High Speed Packet Access (HSPA+) is a 3G standard developed via several iterations from the Universal Mobile Telecommunications System (UMTS) used on GSM networks. HSPA+ nominally supports download speeds up to 168 Mbps and upload speeds up to 34 Mbps. HSPA+-based services are often marketed as 4G if the nominal data rate is better than about 20 Mbps.

Note that with HSPA, the TDMA channel access technology has been abandoned and a type of CDMA used.

●	CDMA2000/Evolution Data Optimized (EV-DO) are the main 3G standards deployed by CDMA network providers. EV-DO can support a 3.1 Mbps downlink and 1.8 Mbps uplink.

4G AND 5G CELLULAR TECHNOLOGIES

The replacements for 3G networks have seen convergence on a single set of worldwide standards.

4G/Long Term Evolution

Long Term Evolution (LTE) is a converged 4G standard supported by both the GSM and CDMA network providers. LTE devices must have a SIM card issued by the network provider installed. LTE has a maximum downlink of 150 Mbps in theory, but no provider networks can deliver that sort of speed at the time of writing, with around 20 Mbps far more typical of real-word performance.

LTE uses neither TDMA nor CDMA but Orthogonal Frequency Division Multiple Access (OFDMA), which is also used by Wi-Fi 6.

LTE Advanced (LTE-A) is intended to provide a 300 Mbps downlink, but again this aspiration is not matched by real-world performance. Current typical performance for LTE-A is up to 90 Mbps.

5G

According to the original specification, a 4G service was supposed to deliver 1 Gbps for stationary or slow-moving users (including pedestrians) and 100 Mbps for access from a fast-moving vehicle. Those data rates are now the minimum hoped-for standards for 5G. As with 4G, real-world speeds are nowhere near the hoped-for minimums, ranging from about 50 Mbps to 300 Mbps at time of writing.

5G uses different spectrum bands from low (sub-6 GHz) to medium/high (20-60 GHz). Low bands have greater range and penetrating power; high bands, also referred to as millimeter wave (mmWave) require close range (a few hundred feet) and cannot penetrate walls or windows. Consequently, design and rollout of 5G services is relatively complex. Rather than a single large antenna serving a large wireless cell, 5G involves installing hundreds of smaller antennas to form an array that can take advantage of multipath and beamforming to overcome the propagation limitations of the spectrum. This is also referred to as massive MIMO. As well as faster mobile speeds, 5G is expected to provide fixed-wireless broadband solutions for homes and businesses, and to support IoT networks.

Topic 15B: Install Wireless Networks

INFRASTRUCTURE TOPOLOGY AND WIRELESS ACCESS POINTS

Wireless network devices are referred to as stations (STA), similar to a node on a wired network. Most wireless networks are deployed in an infrastructure topology. In an infrastructure topology, each station is configured to connect through a base station or access point (AP), forming a logical star topology. The AP mediates communications between client devices and can also provide a bridge to a cabled network segment. In 802.11 documentation, this is referred to as an infrastructure Basic Service Set (BSS). The MAC address of the AP is used as the Basic Service Set Identifier (BSSID) . More than one BSS can be grouped together in an Extended Service Set (ESS).

Access point. (Image © 123RF.com.)

Each client station requires a wireless adapter compatible with the standard(s) supported by the AP.

WLAN configuration in infrastructure mode. (Images © 123RF.com.)

WIRELESS SITE DESIGN

Clients are configured to join a WLAN through the network name or Service Set Identifier (SSID). An SSID can be up to 32 bytes in length and for maximum compatibility should only use ASCII letters and digits plus the hyphen and underscore characters. In infrastructure mode, when multiple APs connected to the same distribution system are grouped into an ESS, this is more properly called the Extended SSID (ESSID) . This just means that all the APs are configured with the same SSID and security information. The area served by a single AP is referred to as a basic service area (BSA) or wireless cell. The area in which stations can roam between access points to stay connected to the same ESSID is referred to as an extended service area (ESA).

SSID Broadcast and Beacon Frame

A WLAN is typically configured to advertise its presence by broadcasting the SSID. This allows a user to connect to a named network. If SSID broadcast is suppressed, the user must configure the connection to the network manually. A beacon is a special management frame broadcast by the AP to advertise the WLAN. The beacon frame contains the SSID (unless broadcast is disabled), supported data rates and signaling, plus encryption/authentication requirements. The interval at which the beacon is broadcast (measured in milliseconds) can be modified. The default is usually 100 ms. Increasing the interval reduces the overhead of broadcasting the frame but delays joining the network and can hamper roaming between APs.

Even if SSID broadcast is suppressed, it is fairly easy for a network sniffer to detect it as clients still use it when connecting with the AP.

Speed and Distance Requirements

A device supporting the Wi-Fi standard should have an indoor range of at least 30 m (100 feet). 2.4 GHz radios support better ranges than 5 GHz ones and 802.11n and later standards improve range compared to earlier standards. Outdoor range can be double or triple indoor range. Each station determines an appropriate data rate based on the quality of the signal using a mechanism called Dynamic Rate Switching/Selection (DRS). If the signal is strong, the station will select the highest available data rate (determined by the 802.11 standard); if the signal is weak, the station will reduce the data rate.

Radio signals pass through solid objects, such as ordinary brick or drywall walls, but can be weakened or blocked by particularly thick walls or those of dense concrete or metal construction. Other radio-based devices can also cause interference as can devices as various as fluorescent lighting, microwave ovens, cordless phones, and (in an industrial environment), power motors and heavy machinery. Bluetooth uses the 2.4 GHz frequency range but a different modulation technique, so interference is possible but not common.

Consequently, a complex set of factors need to be taken into consideration when you are planning a wireless network. A site survey is a critical planning tool to ensure that the WLAN delivers acceptable data rates to the supported number of devices in all the physical locations expected.

SITE SURVEYS AND HEAT MAPS

A site survey is performed first by examining the blueprints or floor plan of the premises to understand the layout and to identify features that might produce radio frequency interference (RFI). This can be backed up by a visual inspection that may reveal things that are not shown on the blueprints, such as thick metal shelving surrounding a room that needs to have WLAN access. Each AP mounting point needs a network port and power jack, so it will help to obtain plans that show the locations of available ports.

A switch that supports Power over Ethernet (PoE) can be used to power a PoE-compatible AP.

The next step is to create a new plan on which you will mark the WLAN cells and associated APs and booster antennas. The idea here to is to place APs close enough together to avoid "dead zones"-areas where connectivity is difficult or data transfer rates are below an acceptable tolerance level-but far enough apart that one AP does not interfere with another or that one AP is overutilized and a nearby one underutilized.

Position an AP in the first planned location, then use a laptop with a wireless adapter and a wireless survey tool, such as Cisco Aironet, Metageek inSSIDer, or Ekahau Site Survey, to record signal strength and supported data rate at various points in the intended basic service area (BSA). Many tools can show the signal strength within a particular channel obtained in different locations graphically using a heat map. The heat map would show areas with a strong signal in greens and yellows with warning oranges and reds where signal strength drops off. This step is then repeated for each planned location. Neighboring APs should be configured with non-overlapping channels to avoid interfering with one another. It may also be necessary to adjust the transmit power of an AP to size its BSA appropriately.

Heat map generated by Ekahau Site Survey. (Image © Ekahau Inc.)

WIRELESS ROAMING AND BRIDGING

Clients can roam within an extended service area (ESA). An ESA is created by installing APs with the same SSID and security configuration connected by a wired network, or Distribution System (DS). The access points are configured with different channels so that where BSAs overlap, there is no interference. When the client detects that it is no longer receiving a good signal, it checks for another signal with the same SSID on other channels or on a different frequency band, and if there is a stronger signal, it disassociates from the current AP. The station can then reassociate with the new AP. Depending on the roaming infrastructure and security type, the station may have to reauthenticate, or if 802.11r fast roaming is supported, it may be able to use its existing authentication status to generate security properties for the new association.

Roaming is supposed to be seamless, but in practice reestablishing the connection can often cause time-out problems for applications. To improve mobility, there needs to be a balance between determining what constitutes a "good" signal and the frequency with which a client tries to associate with different APs. Many adapters support a roaming "aggressiveness" setting that can be configured to prevent a Wi-Fi adapter "flapping" between two APs or (conversely) to prevent a client remaining associated with a more distant AP when it could achieve better bandwidth through one closer to it.

You can also configure multiple access points to cover areas where it is not possible to run cabling. This is referred to as a wireless distribution system (WDS). You must set the APs to use the same channel, SSID, and security parameters. The APs are configured in WDS/repeater mode. One AP is configured as a base station, while the others are configured as remote stations. The base station can be connected to a cabled segment. The remote stations must not be connected to cabled segments. The remote stations can accept connections from wireless stations and forward all traffic to the base station.

Another use for WDS is to bridge two separate cabled segments. When WDS is configured in bridge mode, the APs will not support wireless clients; they simply forward traffic between the cabled segments.

WDSs support and implementation can vary between manufacturers. If you are implementing WDS, it is usually best to use APs from the same vendor.

WIRELESS LAN CONTROLLERS

An enterprise network might require the use of tens or hundreds of access points. If APs are individually managed, this can lead to configuration errors on specific APs and can make it difficult to gain an overall view of the wireless deployment, including which clients are connected to which APs and which clients or APs are producing the most traffic.

A wireless controller, an enterprise-level appliance capable of supporting up to 1500 APs and 20,000 clients. (Image © 123RF.com.)

Rather than configure each device individually, enterprise wireless solutions such as those manufactured by Cisco, Ruckus, or Ubiquiti allow for centralized management and monitoring of the APs on the network. This may be achieved through use of a dedicated hardware device called a wireless LAN controller. Alternatively, some implementations use a software application to centralize the management function, which can be run on a server or workstation.

An AP whose firmware contains enough processing logic to be able to function autonomously and handle clients without the use of a wireless controller is known as a fat AP, while one that requires a wireless controller in order to function is known as a thin AP . Cisco wireless controller usually communicate with the APs by using the Lightweight Access Point Protocol (LWAPP). LWAPP allows an AP configured to work in lightweight mode to download an appropriate SSID, standards mode, channel, and security configuration. Alternatives to LWAPP include the derivative Control And Provisioning of Wireless Access Points (CAPWAP) protocol or a proprietary protocol.

As well as autoconfiguring the appliances, a wireless controller can aggregate client traffic and provide a central switching and routing point between the WLAN and wired LAN. It can also assign clients to separate VLANs. Automated VLAN pooling ensures that the total number of stations per VLAN is kept within specified limits, reducing excessive broadcast traffic. Another function is to supply power to wired access points, using Power over Ethernet (PoE).

AD HOC AND MESH TOPOLOGIES

While most corporate and many SOHO networks are configured in infrastructure mode, there are also wireless topologies that allow stations to establish peer-to-peer links.

Ad Hoc Topology

In an ad hoc topology, the wireless adapter allows connections to and from other devices. In 802.11 documentation, this is referred to as an Independent Basic Service Set (IBSS). This topology does not require an access point. All the stations within an ad hoc network must be within range of one another. An ad hoc network might suit a small workgroup of devices, or connectivity to a single device, such as a shared printer, but it is not scalable to large network implementations.

IBSS is not supported by the updated WDI driver model in the latest versions of Windows (docs.microsoft.com/en-us/windows-hardware/drivers/network/wdi-features-not-carried-over-in-wdi).

Mesh Topology

The 802.11s standard defines a Wireless Mesh Network (WMN). There are also various proprietary mesh protocols and products. Unlike an ad hoc network, nodes in a WMN (called mesh stations) are capable of discovering one another and peering, forming a Mesh Basic Service Set (MBSS). The mesh stations can perform path discovery and forwarding between peers using a routing protocol, such as the Hybrid Wireless Mesh Protocol (HWMP).

These features make a mesh topology more scalable than an ad hoc topology because the stations do not need to be within direct radio range of one another-a transmission can be relayed by intermediate stations. Mesh topologies are becoming increasingly popular and are the foundation of most Internet of Things (IoT) networks.

Topic 15C: Troubleshoot Wireless Networks

WIRELESS PERFORMANCE ASSESSMENT

Wireless issues can be broadly divided into issues with signal strength or interference (like cabling issues in a wired LAN) and configuration issues. This topic focuses on issues that affect signal strength and performance, but always check that the security and authentication parameters are correctly configured before assuming you have a Physical layer connectivity problem. Configuration issues are discussed in the next topic.

As with cabled networks, you should distinguish between speed and throughput when measuring and assessing wireless performance against the specifications and limitations of a particular Wi-Fi standard:

●	Speed is the data rate established at the physical and data link layers. The nominal link speed is determined by standards support (Wi-Fi 5 or Wi-Fi 6, for instance), use of bonded channels, and optimizations, such as MU-MIMO. If the sender and receiver are far apart or subject to interference, a lower rate will be negotiated to make the link more reliable.

●	Throughput is the amount of data that can be transferred at the network layer, discarding overhead from layers 1 and 2. Often the term goodput is used to describe data transfer achieved at the application layer (accounting for overhead from header fields and packet loss/retransmissions).

As with cabling, attenuation refers to the weakening of the signal as the distance between the devices increases. This can be described more precisely as radio frequency (RF) attenuation or free space path loss. As the distance from the antenna increases, the strength of the signal decreases in accordance with the inverse-square rule. For example, doubling the distance decreases the signal strength by a factor of four. Meanwhile, interference sources collectively overlay a competing background signal, referred to as noise. These factors impose distance limitations on how far a client can be from an access point.

Attenuation and signal strength are measured in decibels. Signal strength is represented as the ratio of a measurement to 1 milliwatt (mw), where 1 mW is equal to 0 dBm. dB and dBm units can be combined to analyze losses and gains in signal strength along a communications path. For example, if you transmit a radio signal at 1 mW and use an antenna to boost the signal, the effective power is:

0 dBm + 3 dB = 2 mW = ~3 dBm

Conversely, dB loss due to attenuation or noise means loss of power/signal strength:

1. dBm – 1 dB = 2 dBm = ~1.58 mW

Because 0 dBm is 1 mW, a negative value for dBm represents a fraction of a milliwatt. For example, -30 dBm is 0.001 mW; -60 dBm is 0.000001 mW. Wi-Fi devices are all constrained by regulations governing spectrum use and output only small amounts of power.

SIGNAL STRENGTH

The Received Signal Strength Indicator (RSSI) is the strength of the signal from the transmitter at the client end. When you are measuring RSSI, dBm will be a negative value (a fraction of a milliwatt) with values closer to zero representing better performance. A value around - 65 dBm represents a good signal, while anything over -80 dBm is likely to suffer packet loss or be dropped. The RSSI must exceed the minimum receiver sensitivity.

Depending on the vendor, RSSI might be measured directly in dBm or might be an index value related to a scale of dBm measurements. RSSI indices can be measured as 0-60, 0-127, or as 0-255. On a client, this index is displayed as a number of bars of signal strength on the adapter icon.

The comparative strength of the data signal to the background noise is called the Signal-To-Noise Ratio (SNR). Noise is also measured in dBm, but here values closer to zero are less welcome as they represent higher noise levels. For example, if signal is ‑65 dBm and noise is ‑90 dBm, the SNR is the difference between the two values, expressed in dB (25 dB). If noise is -80 dBm, the SNR is 15 dB and the connection will be much, much worse.

RSSI and SNR can be measured by using a Wi-Fi analyzer. This type of software can be installed to a laptop or smartphone. It will record statistics for the AP that the client is currently associated with and detect any other access points in the vicinity.

ANTENNA TYPES

The antenna type determines the propagation pattern or shape of the radio waves transmitted. Most wireless devices have simple omnidirectional vertical rod-type antennas, which receive and send signals in all directions more-or-less equally. Access points with omnidirectional antennas should ideally be ceiling-mounted for best coverage, unless the ceiling is particularly high. The propagation pattern is shaped like a torus (donut), rather than a sphere, and radiates more powerfully in the horizontal plane than it does in the vertical plane. Locating the antenna above head height will minimize interference from obstructing furniture by allowing line-of-sight to most connecting devices but positioning it too high (above around 25 ft) will reduce signal strength, especially for stations directly below the antenna. You can obtain APs with downtilt omnidirectional antennas for use on high ceilings.

To extend the signal to a particular area, you can use an antenna focused in a single direction (unidirectional). Both the sender and receiver must use directional antennas, or one will be able to receive signals but not send responses. Unidirectional antenna types include the Yagi (a bar with fins) and parabolic (dish or grid) form factors. Unidirectional antennas are useful for point-to-point wireless bridge connections. The increase in signal strength obtained by focusing the signal is referred to as the gain and is measured in dBi (decibel isotropic). The amount of directionality, referred to as the beamwidth, is measured in degrees. A pair of 10-degree antennas are very highly directional and will require more exact alignment than a pair of 90 degree antennas.

A variety of generic antenna types: from left to right, a vertical rod antenna, a Yagi antenna, a parabolic/dish antenna, and a parabolic grid antenna.

Polarization refers to the orientation of the wave propagating from the antenna. If you imagine a rod-type antenna, when the rod is pointed up relative to the floor, the wave is horizontally polarized; if you orient the rod parallel to the floor, the wave is vertically polarized. To maximize signal strength, the transmission and reception antennas should normally use the same polarization. This is particularly important when deploying unidirectional antennas for a point-to-point link. Some antennas are dual-polarized, meaning that they can be installed in either orientation. Dual-polarized antennas are also the best way to support mobile devices, as these can be held by their user in a variety of orientations.


Surveying Wi-Fi networks using inSSIDer. The chart shows which channels are active and the signal strength of different networks in each channel. (Screenshot used with permission from MetaGeek.)

INSUFFICIENT WIRELESS COVERAGE ISSUES

Insufficient wireless coverage refers to spots within a building with no or weak Wi-Fi signal. If a sufficient signal strength cannot be obtained and sources of interference cannot be mitigated, the only solution to is to install an additional device to cover the gap. If you cannot extend the distribution system (cabled network) to support an additional access point, you will need to configure a wireless bridge or use a range extender.

Antenna Placement

Incorrect antenna placement could cause or exacerbate attenuation and interference problems. Use a site survey and heat map to determine the optimum position for APs and (if available) the direction in which to point adjustable antennas. Also, using an incorrect antenna type may adversely affect the signal strength at any given point. A unidirectional antenna is only suitable for point-to-point connections, not for general client access. The internal antennas built into APs may also be optimized to transmit and receive in some directions more than others. For example, an AP designed for ceiling mounting may produce a stronger signal in a cone directed downwards from its central axis, whereas the signal from a similar AP designed for wall installation is more likely to be angled outwards. Consult the documentation for your specific model of AP or use site survey software to produce a heat map.

Remember that some client devices might support a standard such as 802.11n, but only have a single band 2.4 GHz radio. They will not be able to join a 5 GHz network.

Antenna Cable Attenuation

Another source of attenuation is where the antenna is connected at some distance from the access point via coax cabling. Signal loss along this cable is referred to as antenna cable attenuation. LMR/HDF/CFD 200 cable has attenuation of about 0.6 dB/m (decibels per meter), while 400 cable improves that to about 0.22 dB/m. Connector loss is usually calculated as 0.15 dB.

If a device has removable antennas, check that these are screwed in firmly. A loose or disconnected antenna may reduce the range of the device or prevent connectivity altogether.

Effective Isotropic Radiated Power/Power Settings

The power at which an access point transmits is configurable. Effective Isotropic Radiated Power (EIRP) is calculated as the sum of transmit power, antenna cable/connector loss, and antenna gain. For example, if you are configuring a point-to-point link with a directional antenna, you might derive the following value for EIRP:

15 dBm (Transmit Power) – 1 dB (Cable Loss) + 6 dBi (Gain) = 20 dBm (100 mW)

The EIRP for each radio is reported through the access point or controller management software. EIRP must not exceed regulatory limits. Power limits are different for the 2.4 GHz and 5 GHz bands and for point-to-multipoint versus point-to-point operation modes.

Increasing transmit power is not usually an effective solution to improving wireless coverage. While an AP might have an EIRP of around 23 dBm, smartphone devices are more likely to be around 10 to 14 dBm. If the client detects a strong signal, it will set a high data rate. However, because the EIRP of the client radio is much lower, it fails to transmit a strong signal back to the AP. Because it is trying to use a high data rate, this results in excessive packet errors.

As a general rule of thumb, AP power should be 2/3rds of the weakest client power. For example, if the weakest client can output 14 dBm, the AP should transmit at 9 to 10 dBm.

CHANNEL UTILIZATION AND OVERLAP ISSUES

Channel overlap refers to interference issues resulting from multiple access points that are all in range of one another and are configured to use similar wavelengths. There are two main types of channel interference:

●	Co-channel interference (CCI)-This can be more accurately described as contention. When multiple access points use the same channel, opportunities to transmit are reduced. The wireless devices must use CSMA/CA to find opportunities to transmit. CCI can be measured as a percentage referred to as channel utilization. Channel utilization can be measured from the access point or using a Wi-Fi analyzer. As a design goal, a channel should exhibit no more than 50% utilization.

●	Adjacent channel interference (ACI)-This occurs when access points are configured to use different but overlapping channels, such as 1 and 3 in the 2.4 GHz band. ACI slows down the CSMA/CA process and raises noise levels.

One of the design goals for a multi-AP site is to create clean cells so that clients can select an AP with the strongest signal easily and the WLAN operates with a minimum of co-channel interference. At least 25 MHz spacing should be allowed to avoid channel overlap. In practice, therefore, no more than three nearby APs using the 2.4 GHz band can have non-overlapping channels. This could be implemented, for example, by selecting channel 1 for AP1, channel 6 for AP2, and channel 11 for AP3. When you are using the 5 GHz band for 802.11a or Wi-Fi 4/5/6, more non-overlapping channels are available.

In a complex environment, it may be necessary to adjust the power level used by an AP on a given channel. Using the maximum available power on an AP can result in it interfering with other "cells" and to situations where a client can "hear" the AP but cannot "talk" to it because it lacks sufficient power.

Checking power levels on a wireless station using Intel's PROSet Wi-Fi configuration utility. (Screenshot courtesy of Intel Corp.)

In order to enable seamless roaming for mobile clients, the cells served by each AP need to overlap to some extent in order to support roaming. This is one of the trickiest elements of site design to get right, as client behaviors and capabilities for roaming can vary widely. If there is a bring your own device (BYOD) policy in place, these support issues are even more greatly magnified.

Issues with roaming can be identified by analyzing access point association times for client devices. A WLAN controller will be able to track client mobility, showing each access point and the time that the client associated with it. If a large number of clients flap between two access points repeatedly, the site design might need to be investigated to solve the roaming issue.


OVERCAPACITY ISSUES

Overcapacity (or device saturation) occurs when too many client devices connect to the same AP. The maximum number of clients that an AP can support varies, depending on the Wi-Fi standard used and the type of network traffic generated. For example, web browsing will typically place a lighter load on the network than local client-server traffic or is likely at least to move any bottleneck further upstream to the WAN, rather than the wireless network. While individual circumstances must be considered, a maximum of 30 clients per AP is generally accepted as a rule of thumb. In designing the network, enough APs should be provided in appropriate locations to support the expected client density at this ratio. APs can usually be configured to enforce a maximum number of connections, so that additional clients will connect to the next nearest AP. Even with a relatively low number of clients, the wireless network can suffer from bandwidth saturation. Since wireless is a broadcast medium, the available bandwidth is shared between all clients. Thus, if one client is a bandwidth hog, others may find it difficult to maintain a reliable connection.

In an enterprise Wi-Fi solution, a controller will normally provide reporting tools to diagnose bandwidth issues and to report on which clients are consuming the most bandwidth. It could also report on wireless channel utilization and configure APs and clients to reassign channels dynamically to reduce overutilization. If a traffic shaper is deployed, it may work automatically to throttle bandwidth to overactive nodes.

INTERFERENCE ISSUES

If a device is within the supported range but the signal is weak or you cannot get a connection, there is likely to be interference. Apart from channel interference described earlier, there are several other sources of interference to consider:

●	Reflection/bounce (multipath interference)-Mirrors or shiny surfaces cause signals to reflect, meaning that a variable delay is introduced. This causes packets to be lost and consequently the data rate to drop.

The Wi-Fi 4/5/6 standards actually use bounce (multipath) as a means of optimizing throughput and range via MIMO.

●	Refraction -Glass or water can cause radio waves to bend and take a different path to the receiver. This can also cause the data rate to drop.

●	Absorption-This refers to the degree to which walls and windows will reduce signal strength (some of the radio wave's energy is lost as heat when passing through construction materials). An internal wall might "cost" 3 to 15 dB, depending on the material used (concrete being the most effective absorber). The 2.4 GHz frequency has better penetration than the 5 GHz one, given the same power output. To minimize absorption from office furniture (and people), use ceiling-mounted APs.

●	Electromagnetic interference (EMI)-Interference from a powerful radio or electromagnetic source working in the same frequency band, such as a Bluetooth device, cordless phone, or microwave oven.

EMI can be detected by using a spectrum analyzer. Unlike a Wi-Fi analyzer, a spectrum analyzer must use a special radio receiver-Wi-Fi adapters filter out anything that isn't a Wi-Fi signal. They are usually supplied as handheld units with a directional antenna, so that the exact location of the interference can be pinpointed. A 6 dB change in the level of a particular source represents a halving or doubling of the distance between the analyzer and the source of the RF source.

Also consider that signal problems could be a result of someone trying to attack the network by jamming the legitimate AP and making clients connect to a rogue AP.

Topic 15D: Configure and Troubleshoot Wireless Security

WI-FI ENCRYPTION STANDARDS

As well as the site design, a wireless network must be configured with security settings. Without encryption, anyone within range can intercept and read packets passing over the wireless network. The choice of which security settings to apply is determined by device support for the various Wi-Fi encryption standards, by the type of authentication infrastructure, and by the purpose of the WLAN. The encryption standard determines the cryptographic protocols that are supported, the means of generating the encryption key, and available methods for authenticating wireless stations when they try to join (or associate with) the network.

The first version of Wi-Fi Protected Access (WPA) was designed to fix critical vulnerabilities in the earlier wired equivalent privacy (WEP) standard. Like WEP, version 1 of WPA uses the RC4 stream cipher to encrypt traffic but adds a mechanism called the Temporal Key Integrity Protocol (TKIP) to try to mitigate the various attacks against WEP that had been developed.

Configuring a TP-LINK SOHO access point with wireless encryption and authentication settings. In this example, the 2.4 GHz band allows legacy connections with WPA2-Personal security, while the 5 GHz network is for 802.11ax (Wi-Fi 6) capable devices using WPA3-SAE authentication. (Screenshot used with permission from TP-Link Technologies.)

Neither WEP nor the original WPA version are considered secure enough for continued use. They can be exploited by various types of replay attack that aim to recover the encryption key. WPA2 uses the Advanced Encryption Standard (AES) cipher deployed within the Counter Mode with Cipher Block Chaining Message Authentication Code Protocol (CCMP). AES replaces RC4 and CCMP replaces TKIP. CCMP provides authenticated encryption, which is designed to make replay attacks harder.

Weaknesses have also been found in WPA2, however, which has led to its intended replacement by WPA3.

PERSONAL AUTHENTICATION

In order to secure a network, you need to be able to confirm that only valid users are connecting to it. Wi-Fi authentication comes in three types: personal, open, and enterprise. Within the personal authentication category, there are two methods: pre-shared key authentication (PSK) and simultaneous authentication of equals (SAE).

WPA2 Pre-Shared Key Authentication

In WPA2, pre-shared key (PSK) authentication uses a passphrase to generate the key that is used to encrypt communications. It is also referred to as group authentication because a group of users share the same secret. When the access point is set to WPA2-PSK mode, the administrator configures a passphrase of between 8 and 63 characters. This is converted to a type of hash value, referred to as the pairwise master key (PMK). The same secret must be configured on the access point and on each node that joins the network. The PMK is used as part of WPA2's 4-way handshake to derive various session keys.

All types of Wi-Fi PSK authentication have been shown to be vulnerable to attacks that attempt to recover the passphrase. At a minimum, the passphrase must be at least 14 characters long to try to mitigate risks from cracking.

WPA3 Personal Authentication

While WPA3 still uses a passphrase to authenticate stations in personal mode, it changes the method by which this secret is used to agree session keys. The scheme used is also referred to as Password Authenticated Key Exchange (PAKE). In WPA3, the Simultaneous Authentication of Equals (SAE) protocol replaces the 4-way handshake, which has been found to be vulnerable to various attacks.

The configuration interfaces for access points can use different labels for these methods. You might see WPA2-Personal and WPA3-SAE rather than WPA2-PSK and WPA3-Personal, for example. Additionally, an access point can be configured for WPA3 only or with support for legacy WPA2 (WPA3-Personal Transition mode).

ENTERPRISE/IEEE 802.1X AUTHENTICATION

The main problems with personal modes of authentication are that distribution of the key or passphrase cannot be secured properly, and that users may choose unsecure phrases. Personal authentication also fails to provide accounting, as all users share the same credential.

As an alternative to personal authentication, WPA’s enterprise authentication method implements IEEE 802.1X to use an Extensible Authentication Protocol (EAP) mechanism to authenticate against a network directory. 802.1X defines the use of EAP over Wireless (EAPoW) to allow an access point to forward authentication data without allowing any other type of network access. It is configured by selecting WPA2-Enterprise or WPA3-Enterprise as the security method on the access point.

With enterprise authentication, when a wireless station requests an association, the AP enables the channel for EAPoW traffic only. It passes the credentials of the supplicant to an AAA (RADIUS or TACACS+) server on the wired network for validation. When the supplicant has been authenticated, the AAA server transmits a master key (MK) to the supplicant. The supplicant and authentication server then derive the same pairwise master key (PMK) from the MK. The AAA server transmits the PMK to the access point. The wireless station and access point use the PMK to derive session keys, using either the WPA2 four-way handshake or WPA3 SAE methods.

Using Cisco's Virtual Wireless LAN Controller to set security policies for a WLAN-This policy enforces use of WPA2 and the use of 802.1X (Enterprise) authentication. (Image © and Courtesy of Cisco Systems, Inc. Unauthorized use not permitted.)

WI-FI SECURITY CONFIGURATION ISSUES

While signal loss and interference are factors that always need considering, if there is a basic connectivity problem, then you will probably want to investigate the configuration of the client and/or AP first.

Wrong SSID and Incorrect Passphrase Issues

If SSID broadcast is suppressed, a station can still connect to a WLAN by entering the network name manually. If this is the case, check that the clients are configured with the correct SSID/ESSID. Remember that this value is case sensitive. Technically, an SSID can contain spaces and special characters, but this can cause problems so is best avoided. Check that the authentication settings are the same on all devices. If a passphrase is used, make sure it is entered correctly. On the AP, ensure the authentication type is not set to open, unless the intention is to provide unrestricted public access.

It is possible that two APs are operating with the same SSID. If authentication is required, the connection with the wrong SSID will fail. If there is no authentication (open network), then the host will connect but take care, as this may be an attempt to snoop on the host's traffic using a rogue AP. Also, if a user is joining a WLAN for the first time, it may be the case that there are SSIDs from overlapping WLANs with very similar default names and the user may be confused about which name to choose.

Encryption Protocol Mismatch Issues

If the user is supplying the correct key or credentials, check that the client can support the encryption and authentication standards configured on the AP. A driver update or OS patch may be required. An encryption protocol mismatch will cause the connection to fail, even if the correct credentials are supplied.

CLIENT DISASSOCIATION ISSUES

In the normal course of operations, an access point and client use management frames to control connections. The access point normally broadcasts a beacon frame to advertise service capabilities. Clients can choose to first authenticate and then associate to an access point when they move into range of the beacon. The client or access point can use disassociation and/or deauthentication frames to notify the other party that it has ended a connection. A legitimate client might disassociate but not deauthenticate because it is roaming between wireless access points in an extended service area. A client might "flap" between two access points, causing numerous disassociations and reassociations. Investigate the access point or controller event log to identify the cause of disassociations.

If clients are disassociated unexpectedly and there is no roaming, interference, or driver issue, you should consider the possibility of a malicious attack. A disassociation attack exploits the lack of encryption in management frame traffic to send spoofed frames. One type of disassociation attack injects management frames that spoof the MAC address of a single victim station in a disassociation notification, causing it to be disconnected from the network. Another variant of the attack broadcasts spoofed frames to disconnect all stations. Frames can be spoofed to send either disassociation or deauthentication notifications.

Disassociation/deauthentication attacks may be used to perform a denial of service attack against the wireless infrastructure or to exploit disconnected stations to try to force reconnection to a rogue WAP. Disassociation/deauthentication attacks might also be used in conjunction with a replay attack aimed at recovering the network key.

OPEN AUTHENTICATION AND CAPTIVE PORTAL ISSUES

Configuring an access point for open authentication means that the client is not required to authenticate. This mode would be used on a public AP or "hotspot". In WPA/WPA2, this also means that data sent over the link is unencrypted. Open authentication may be combined with a secondary authentication mechanism managed via a browser. When the client associates with the open hotspot and launches the browser, the client is redirected to a captive portal or splash page. This will allow the client to authenticate to the hotspot provider's network (over HTTPS, so the login is secure). The portal may also be designed to enforce terms and conditions and/or take payment to access the Wi-Fi service.

Most captive portal issues arise because the redirect does not work. The captive portal should use HTTPS. Most modern browsers will block redirection to sites that do not use TLS. This means that the captive portal also needs to be installed with a digital certificate issued by a certification authority (CA) that is trusted by the client browser.

When using open wireless, users must ensure they send confidential web data only over HTTPS connections and only use email, VoIP, IM, and file transfer services with SSL/TLS enabled. Another option is for the user to join a virtual private network (VPN). The user would associate with the open hotspot then start the VPN connection. This creates an encrypted "tunnel" between the user's computer and the VPN server. This allows the user to browse the web or connect to email services without anyone eavesdropping on the open Wi-Fi network being able to intercept those communications. The VPN could be provided by the user's company or they could use a third-party VPN service provider. Of course, if using a third party, the user needs to be able to trust them implicitly. The VPN must use certificate-based tunneling to set up the "inner" authentication method.