Lesson 4: Troubleshooting Ethernet Networks

Topic 4A: Explain Network Troubleshooting Methodology

Network Troubleshooting Methodology

●	Identify the problem:

○	Gather information

○	Duplicate the problem, if possible

○	Question users

○	Identify symptoms

○	Determine if anything has changed

○	Approach multiple problems individually

●	Establish a theory of probable cause:

○	Question the obvious

○	Consider multiple approaches

○	Top-to-bottom/bottom-to-top OSI model

○	Divide and conquer

●	Test the theory to determine cause:

○	Once theory is confirmed, determine next steps to resolve the problem.

○	If theory is not confirmed reestablish new theory or escalate

●	Establish a plan of action to resolve the problem

●	Implement the solution or escalate as necessary

●	Very full system functionality, and if applicable, implement preventive measures

●	Document findings, actions, and outcomes

Identify the Problem (Gather Information)

Gather Information

At the outset, define the score of the problem (the area affected). This is helpful in two ways. First, if it’s a single user, then it’s not as urgent as the other outstanding calls you have. But if it’s the whole third floor, then it’s more urgent. In addition, the fact that the problem affects a wider area means that it is unlikely to be a problem with one user’s workstation. Knowing the scope of the problem can help to identify its source and prioritize the issue in relation to other incidents.

Also:

●	Check the system documentation, such as installation or maintenance logs, for useful information.

●	Check recent job logs or consult any other technicians who might have worked on the system recently or might be working on some related issue.

●	Use vendor support sites (knowledge bases) and forums.

Identify Symptoms and Duplicate the Problem

Symptoms are facts and clues in the affected system that can be correlated with known causes and issues. To identify symptoms, complete the following tests:

●	Make a physical inspection; look for something out of the ordinary.

●	Check system logs or diagnostic software for information.

●	Duplicate the problem on the user’s system or a test system. You will need to try to follow the same steps as the user. Issues that are transitory or difficult to reproduce are often the hardest to troubleshoot.

Identify the Problem (Question Users)

Question Users

Questions are commonly divided into two types:

●	Open questions invite someone to explain in their own words. Open questions are good to start with, as they help to avoid making your own assumptions about what is wrong, and they encourage the user to give you all the information they can.

●	Closed questions invite a Yes/No answer or a fixed response. Closed questions can be used to drill down into the nature of the problem and guide a user toward giving you information that is useful.

Determine if Anything has Changed

There are two key questions to ask when trying to identify the cause of a problem:

●	Did it ever work? Did it work before x time, if so, what happened at x time. If the system never worked, then you are not looking for something that stopped working, but for something which was never working in the first place.

●	What has changed since it was last working? Check for documented changes using the system inventory, but if this does not reveal anything, look for undocumented changes in the local area of the incident.




Approach Multiple Problems Individually

If problems do not seem to be related, treat each issue as a separate case. If they seem to be related, check for outstanding support or maintenance tickets that might indicate existing problems.

Establish a Theory of Probably Cause

●	Question the obvious. Step through what should happen and identify the point at which there is a failure or error. This approach can quickly identify obvious oversights, such as a network cable not being plugged.

●	Methodically prove the functionality of each component in sequence. This approach is more time consuming but may be necessary for a difficult problem.

Top-to-bottom/Bottom-to-top OSI Model Approach

Methodical validation of network components can be approached by testing at each layer of the OSI model in sequence. There are many components which go to make up a network.



Some, or several, of these components may be at fault when a problem is reported to you. Unless a problem is trivial, break the troubleshooting process into compartments or categories, using the OSI model as a guide.

Divide and Conquer Approach

Rather than starting from the top or bottom of the OSI model, you start with the layer most likely to be causing the problem and then work either down or up depending on what your tests reveal.

Test the Theory to Determine the Cause

If you cannot prove the cause of the problem, you will either need to develop and test a new theory or decide to escalate the problem. Escalation means referring the problem to a senior technician, manager, or third party. You may need to escalate a problem for any of these reasons:

●	The problem is beyond your knowledge or ability to troubleshoot.

●	The problem falls under a system warranty and would be better dealt with by the supplier.

●	The score of the problem is very large and/or the solution requires some major reconfiguration of the network.

●	A customer becomes difficult or abusive or demands help on an unsupported item.

When you escalate a problem, you should have established the basic facts, such as the scope of the problem and its likely cause and be able to communicate these clearly to the person to whom you are referring the incident to.

If you can prove the cause of the problem, you can start to determine the next steps to resolve the problem.

Establish a Plan of Action

An action plan sets out the steps you will take to solve the problem. There are typically three solutions to any problem:

●	Repair: You need to determine whether the cost of repair/time taken to reconfigure something makes this the best option.

●	Replace: Often, this is more expensive and may be time-consuming if a part is not available There may also be an opportunity to upgrade the device or software.

●	Ignore: Not all problems are critical. If neither repair or replacement is cost-effective, it may be best to either find a workaround or just to document the issue and move on.

Another consideration is potential effects on the rest of the system.

Implement the Solution

If you are reverting to a known good configuration, you may be able to implement the solution directly. If the solution requires a change to the system or the network environment, you are likely to have to follow a change management plan.

If you do not have authorization to implement a solution, you will need to escalate the problem to more senior personnel. If applying the solution is disruptive to the wider network, you also need to consider the most appropriate time to schedule the reconfiguration work and plan how to notify other network users. When you change a system as part of implementing a solution, test after each change. If the change does not fix the problem, reverse it and then try something else. If you make a series of changes without recording what you have done, you could find yourself in a tricky position.

Verify Full System Functionality and Implement Preventive Measures

When you apply a solution, verify that it fixes the reported problem, and that the system as a whole continues to function normally. Identify the results and effects of the solution. Ensure that you were right and that the problem is resolved.

Before you can consider a problem closed, you should be satisfied in your own mind that you have resolved it and you should get the customer’s acceptance that it has been fixed. Restate what the problem was and how it was resolved, then confirm with the customer that the incident log can be closed.

To fully solve a problem, you should try to eliminate any factors that may cause the problem to recur.

Document Findings, Actions and Outcomes

When you complete a problem log remember that people other than you may come to rely on it. Also logs may be presented to customers as proof of troubleshooting activity. Write clearly and concisely checking for spelling and grammar errors.

Topic 4B: Troubleshoot Common Cable Connectivity Issues

Applying a layer-by-layer approach to network troubleshooting can greatly assist with isolating symptoms and causes.

Specification and Limitations

When troubleshooting a link, you will need to compare the expected performance with the actual current performance. To do this, you must understand how to assess and distinguish speed, throughput, and distance specifications and limitations.

Speed versus Throughput

At the physical layer, a signal transmitted over a communication channel consists of a series of events referred to as symbols. A symbol could be something like a pulse of higher voltage in an electrical current or the transition between the peak and the trough in an electromagnetic wave. The number of symbols that can be transmitted per second is called the baud rate. The baud rate is measured in hertz (or MHz or GHz).

At the data link layer, the nominal bit rate-or bandwidth- of the link is the amount of information that can be transmitted, measured in bits per second (bps), or some multiple thereof. In order to transmit information more efficiently, a signaling method might be capable of representing more than one bit per symbol. This also helps to overcome noise and detect errors. The use of these encoding methods means that the bit rate will be higher than the baud rate. In Ethernet terms, the speed is the expected performance of a link that has been properly installed to operate at 10 Mbps, 100 Mbps, 1 Gbps, or better.

The nominal bit rate will not often be achieved in practice. Throughput is an average data transfer rate achieved over a period of time excluding encoding schemes, errors, and other losses incurred at layer 1 and layer 2. Throughput can be adversely affected by link distance and by interference (noise).

\*\*Throughput is typically measured at the network or transport layer. Often the term goodput is used to measure an averaged data transfer rate at the application layer. This takes account of the effect of packet loss. Throughput is also sometimes measures as packets per second\*\*

Speed is measured as a unit of time-typically milliseconds (ms)- and is also referred to as latency, or delay. Latency can occur at many layers of the OSI Model. It is not usually a critical factor on local Ethernets, however.

\*\*The term speed is also used to describe how well or badly a link is performing in terms of throughput but do be aware of the distinction between bandwidth and latency.\*\*

Distance Limitations, Attenuation, and Noise

Each type of media can consistently support a given bit rate only over a defined distance. Some media types support higher bit rates over longer distances than others Attenuation and noise enforce distance limitations on different media types.

●	Attenuation is the loss of signal strength, expressed in decibels (dB). dB expresses the ratio between two measurements, in this case, signal strength at origin and signal strength at destination.

●	Noise is anything that gets transmitted within or close to the channel that isn’t the intended signal. This serves to make the signal itself difficult to distinguish, causing errors in data and forcing retransmissions. This is expressed as the signal to noise ratio (SNR).

Cable Issues

When troubleshooting cable connectivity you are focusing on issues at the physical layer. At layer one a typical Ethernet link for an office workstation includes the following components:

●	Network transceiver in the host (end system)

●	Patch cable between the host and a wall port

●	Structured cable between the wall port and a patch panel (the permanent link)

●	Patch cable between the patch panel port and a switch port

●	Network transceiver in the switch port (intermediate system)

The entire cable path (patch cords plus permanent link) is referred to as a channel link.

Loopback Plugs, Status Indicators and Interface Configuration

A network loopback adapter (or loopback plug) is a specially wired RJ-45 plug with a 6” stub of cable. The wiring pinout is pin 1 (Tx) to pin 3 (Rx) to pin 6 (Rx). This means that the packet sent by the NIC is received by itself. This is used to test for bad ports and network cards.

Another approach when you are troubleshooting a suspected cable problem is to check the link lights or network connection LED status indicators on the NIC at one end and the switch/router port at the other. You will need the vendor documentation to interpret the LEDs. There may be two LEDs for status and for link. On a switch port, the following LED link states are typical:

●	Solid green: The link is connected but there is no traffic.

●	Flickering green: The link is operating normally (with traffic).

●	No light: The link is not working or is disconnected at the other end.

●	Blinking amber: A fault has been detected (duplex mismatch or spanning tree blocking for instance)

●	Solid amber: The port is disabled.

Cable Testers

When troubleshooting a permanent link, you should verify that the cable type is appropriate to the application. You may also need to verify that unshielded cable has not been installed where shielded or screened cable would be more suitable.Check the identifier printed on the cable jacket to verify the type that has been used.

From a safety point of view you must also ensure that the cable jacket type is suitable for the installation location, such as using plenum rated cable in plenum spaces and riser rated cable in riser spaces.

A cable tester reports detailed information on the physical and electrical properties of the cable. Devices classed as certifiers can be used to test and certify cable installations to a performance category. They use defined transport performance specifications to ensure an installation exceeds the required performance characteristics for parameters such as attenuation and crosstalk.

A cable tester might incorporate the function of a time domain reflectometer (TDR). A TDR is used to measure the length of a cable run and can locate open and short circuits kins/sharp bends, and other imperfections in cables that could affect performance. A TDR transmits a short signal pulse of known amplitude and duration down a cable and measures the corresponding amplitude and time delay associated with resultant signal reflections. A TDR analyzes these reflections and can display any problems found and their location. The TDR measures the amount of time taken for the signal to bounce back and can therefore calculate the distance to the cable fault to within a meter, which makes isolating the problem simpler.


Wire map testers and Tone generators

A multimeter can be used to check physical connectivity if other options are unavailable. The primary purpose of a multimeter is for testing electrical circuits, but it can test for the continuity of any sort of copper wire, the existence of a short, and the integrity of a terminator. To perform useful tests, you need to know the readings that are expected from a particular test. Many multimeters designed for ICT use incorporate the function of a wire map tester. These are also available as dedicated devices. Wire map testers can identify the following problems:

●	Continuity (open): A conductor does not form a circuit because of cable damage or because the connector is not properly wired.

●	Short: Two conductors are joined at some point, usually because the insulating wire is damaged, or a connector is poorly wired.

●	Incorrect pin-out/incorrect termination/mismatched standards: The conductors are incorrectly wired into the terminals at one or both ends of the cable. The following transpositions are common:

○	Reversed pair: The conductors in a pair have been wired to different terminals.

○	Crossed pair (Tx/Rx reverse): The conductors from one pair have been connected to pins belonging to a different pair. This may be done deliberately to create a crossover cable, but such a cable would not be used to link a host to a switch.

Another potential cable wiring fault is a split pair. This is where both ends of a single wire in one pair are wired to terminals belonging to a different pair. This type of fault can only be detected by a wire map tester that also tests for excessive crosstalk. This is generally the kind of functionality associated with a cable tester or certifier.

A network tone generator and probe are used to trace a cable from one end to the other. This may be necessary when the cables are bundled and have not been labeled properly. This device is also known as a Fox and Hound or tone probe. The tone generator is used to apply a signal on the cable to be traced where it is used to follow the cable over ceilings and through ducts.

Attenuation and Interference Issues

If a cable link is too long, decibel (dB) loss or (insertion loss) may mean that the link experiences problems with high error rates and retransmissions (frame or packet loss) resulting in reduced speeds and possibly loss of connectivity. Insertion loss is measured in decibels (dB) and represents the ration of the received voltage to the original voltage.

A dB expresses the ratio between two values using a logarithmic scale. A logarithm is a mathematical tool for performing complex multiplication and division exponential operations as simpler additions and subtractions. The essential point is that a logarithmic scale is nonlinear, so a small change in value represents a large change in the performance measured. The following reference points are useful to remember:

●	+3 dB means doubling, while -3 dB means halving

●	+6 dB means quadrupling, while -6 dB relates to a quarter

●	+10 dB means ten times the ration, while -10 dB is a tenth

The maximum value allowed for insertion loss depends on the link category. When you are measuring insertion loss itself, smaller values are better (20 dB insertion loss is better than 22 dB, for instance). Consequently, higher margin values are better. Higher grade or shielded cable may alleviate the problem; otherwise, you will need to find a shorter cable run or install a repeater or additional switch.

Electromagnetic interference (EMI) is something that should be detected when the cable is installed, so you should suspect either some new source that has been installed recently or some source that was not taken into account during testing. Interference from nearby data cables is also referred to as alien crosstalk.

Crosstalk Issues

Crosstalk usually indicates a problem with bad wiring, a bad connector, or improper termination. Crosstalk is also measured in dB, but unlike insertion loss, higher values represent less noise. There are various types of crosstalk that can be measured:

●	Near End (NEXT): This measures crosstalk on the receive pairs at the transmitter end and is usually caused by excessive untwisting of pairs or faulty bonding of shielded elements.

●	Attenuation to Crosstalk Ratio, Near End (ACRN): This is the difference between insertion loss and NEXT. ACR is equivalent to a signal-to-noise ratio (SNR). A high value means that the signal is stronger than any noise present; a result closer to 0 means the link is likely to be subject to high error rates.

●	Attenuation-to-Crosstalk Ratio, Far End (ACRF): Far End Crosstalk (FEXT) is measured on the receive pairs at the recipient end. The difference between insertion loss and FEXT gives ACRF, which measures cable performance regardless of the actual link length.

●	Power sum: Gigabit and 10 GbE Ethernet use all four pairs. Power sum crosstalk calculations (PSNEXT, PSACRN, AND PSACRF) confirm that a cable is suitable for this type of application. They are measured by energizing three of the four pairs in turn

Cable Application Issues

Straight Through and Crossover Cables

There are two main formats for patch cords:

●	Straight through: The cable is terminated with either T568A at both ends or T568B at both ends. This type of cable is used for an uplink (MDI port to MDIX port).

●	Crossover: The cable is terminated with T568A at one end and T568B at the other. This type of cable is used to connect an end system (host) to another host or a hub to a hub.

Crossover cable is no longer required for this type of application as switches either have an uplink port for this purpose or can auto detect and select between a crossover and straight-through connection. This is referred to as auto-MDI/MDI-X. All Gigabit Ethernet ports support auto-MDI/MDIX.

Rollover Cable/Console Cable

A console cable is used to connect a PC or laptop to the command line terminal of a switch or router. The console port connection on the appliance is a standard RJ-45 jack (but wired in a different way to Ethernet). A legacy console cable has a serial DB-9 connector for the PC end. As almost no computers come with DB-9 ports anymore, modern cables use a USB connector and port. Console cable is traditionally colored pale blue.

\*\*Routers typically have console and AUX ports. The AUX port is used to connect to the router over a dial-up modem. The console port just uses a serial (or null modem) link.\*\*

Power over Ethernet

Cat 3 or better is required to support PoE, while PoE+ must be Cat 5e or better. Drawing power down the cable generates more heat. If this heat is not dissipated, it can affect data rates. Thermal performance is improved by using pure copper cabling with larger conductors. A thin conductor will generate more heat through resistance. Shielded cabling is capable of dispersing heat more efficiently, too.




Fiber Optic Cable Testing Tools

As with attenuation in copper cables, the signal loss is increased with increasing cable length. The EIA/TIA 568 specification for fiber allows for a signal loss of between 0.5 dB/km and 3.5 dB/km, depending on the type of fiber used and the wavelength of the light.

If a break is identified in an installed cable, the location of the break can be found using an optical time domain reflectometer (OTDR). This sends light pulses down the cable and times how long it takes for any reflections to bounce back from the break. A broken cable will need to be repaired (spliced) or replaced. An OTDR can also be used to verify that new splices are sound.

An optical spectrum analyzer (OSA) is typically used with wavelength division multiplexing (WDM) to ensure that each channel has sufficient power. At very long distances, the attenuation of different wavelengths can vary. This is referred to as spectral attenuation. An OSA can determine whether existing cable is suitable for reuse with WDM and which wavelengths will support the link distance required.
