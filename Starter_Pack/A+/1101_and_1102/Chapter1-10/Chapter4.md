CHAPTER 4

RAM

In this chapter, you will learn how to

-   Identify the different types of DRAM packaging

-   Explain the varieties of RAM

-   Select and install RAM

-   Perform basic RAM troubleshooting

Whenever people come up to me and start professing their computer savvy, I ask them a few questions to see how much they really know. In case you and I ever meet and you decide you want to "talk tech" with me, I'll tell you my first two questions now so you'll be ready. Both involve random-access memory (RAM), the working memory for the CPU.

1\.   "How much RAM is in your computer?"

2\.   "What is RAM and why is it so important that every PC has enough?"

Can you answer either of these questions? Don't fret if you can't---you'll know how to answer both before you finish this chapter. Let's start by reviewing what you know about RAM thus far.

When not in use, programs and data are held in a mass storage device such as a solid-state drive (SSD), USB thumb drive, optical drive, or some other device that can hold data while the computer is off. When you load a program in Windows, your PC copies the program from the mass storage device to RAM and then runs it (see Figure 4-1).

Figure 4-1  Mass storage holds programs, but programs need to run in RAM.

You saw in Chapter 3 that the CPU uses dynamic random-access memory (DRAM) as RAM for all PCs. Just like CPUs, DRAM has gone through evolutionary changes over the years, resulting in improved DRAM technologies such as SDRAM, RDRAM, and DDR RAM. This chapter starts by explaining how DRAM works, and then discusses the types of DRAM used over the past several years and how they improve on the original DRAM. The third section, "Working with RAM," goes into the details of finding and installing RAM. The chapter finishes with troubleshooting RAM problems.

Historical/Conceptual

Understanding DRAM

As discussed in Chapter 3, DRAM functions like an electronic spreadsheet, with numbered rows containing cells and each cell holding a one or a zero. Now let's look at what's physically happening. Each spreadsheet cell is a special type of semiconductor that can hold a single bit---one or zero---by using microscopic capacitors and transistors. DRAM makers put these semiconductors into chips that can hold a certain number of bits. The bits inside the chips are organized in a rectangular fashion, using rows and columns.

Each chip has a limit on the number of lines of code it can contain. Think of each line of code as one of the rows on the electronic spreadsheet; one chip might be able to store a million rows of code while another chip might be able to store over a billion lines. Each chip also has a limit on the width of the lines of code it can handle. One chip might handle 8-bit-wide data while another might handle 16-bit-wide data. Techs describe chips by bits rather than bytes, so they refer to ×8 and ×16, respectively. Just as you could describe a spreadsheet by the number of rows and columns---John's accounting spreadsheet is huge, 48 rows × 12 columns---memory makers describe RAM chips the same way. An individual DRAM chip that holds 1,048,576 rows and 8 columns, for example, would be a 1M × 8 chip, with "M" as shorthand for "mega," just like in megabytes (220 bytes). It is difficult if not impossible to tell the size of a DRAM chip just by looking at it---only the DRAM makers know the meaning of the tiny numbers on the chips (see Figure 4-2), although sometimes you can make a good guess.

Figure 4-2  What do these numbers mean?

NOTE   Serious RAM enthusiasts can enjoy chip specifics available at memory maker Web sites. Check out the charts at Micron, for example: https://www.micron.com/products/dram/ddr4-sdram/part-catalog.

Organizing DRAM

Because of its low cost, high speed, and ability to contain a lot of data in a relatively small package, DRAM has been the standard RAM used in all computers---not just PCs---since the mid-1970s. DRAM can be found in just about everything, from automobiles to automatic bread makers.

The PC has very specific requirements for DRAM. The original 8088 processor had an 8-bit frontside bus. Commands given to an 8088 processor were in discrete 8-bit chunks. You needed RAM that could store data in 8-bit (1-byte) chunks, so that each time the CPU asked for a line of code, the memory controller chip (MCC) could put an 8-bit chunk on the data bus. This optimized the flow of data into (and out from) the CPU. Although today's DRAM chips may have widths greater than 1 bit, all DRAM chips back then were 1 bit wide, meaning only sizes such as 64 K × 1 or 256 K × 1 existed---always 1 bit wide. So how was 1-bit-wide DRAM turned into 8-bit-wide memory? The solution was quite simple: just take eight 1-bit-wide chips and use the MCC to organize them electronically to be eight wide (see Figure 4-3).

Figure 4-3  The MCC accessing data on RAM soldered onto the motherboard

Practical DRAM

Okay, before you learn more about DRAM, I need to clarify a critical point. When you first saw the 8088's machine language in Chapter 3, all the examples in the "codebook" were exactly 1-byte commands. Figure 4-4 shows the codebook again---see how all the commands are 1 byte?

Figure 4-4  Codebook again

Well, the reality is slightly different. Most of the 8088 machine language commands are 1 byte, but more-complex commands need 2 bytes. For example, the following command tells the CPU to move 163 bytes "up the RAM spreadsheet" and run whatever command is there. Cool, eh?

1110100110100011

The problem here is that the command is 2 bytes wide, not 1 byte. So how did the 8088 handle this? Simple---it just took the command 1 byte at a time. It took twice as long to handle the command because the MCC had to go to RAM twice, but it worked.

So, if some of the commands are more than 1 byte wide, why didn't Intel make the 8088 with a 16-bit frontside bus? Wouldn't that have been better? Well, Intel did. Intel invented a CPU called the 8086. The 8086 predates the 8088 and was absolutely identical to the 8088 except for one small detail: it had a 16-bit frontside bus. IBM could have used the 8086 instead of the 8088 and used 2-byte-wide RAM instead of 1-byte-wide RAM. Of course, they would have needed to invent an MCC that could handle that kind of RAM (see Figure 4-5).

Figure 4-5  Pumped-up 8086 MCC at work

Why did Intel sell the 8088 to IBM instead of the 8086? There were two reasons. Nobody had invented an affordable MCC or RAM that handled 2 bytes at a time. Sure, chips had been invented, but they were expensive, and IBM didn't think anyone would want to pay $12,000 for a personal computer. So IBM bought the Intel 8088, not the Intel 8086, and all our RAM came in bytes. But as you might imagine, it didn't stay that way for long.

DRAM Sticks

As CPU data bus sizes increased, so too did the need for RAM wide enough to fill the bus. The Intel 80386 CPU, for example, had a 32-bit data bus and thus the need for 32-bit-wide DRAM. Imagine having to line up 32 one-bit-wide DRAM chips on a motherboard. Talk about a waste of space! Figure 4-6 shows motherboard RAM run amuck.

Figure 4-6  That's a lot of real estate used by RAM chips!

DRAM manufacturers responded by creating wider DRAM chips, such as ×4, ×8, and ×16, and putting multiples of them on a small circuit board called a stick or module. Figure 4-7 shows an early stick, called a single inline memory module (SIMM), with eight DRAM chips. To add RAM to a modern machine, you need to get the right stick or sticks for the particular motherboard. Your motherboard manual tells you precisely what sort of module you need and how much RAM you can install.

Figure 4-7  A 72-pin SIMM

Modern CPUs are a lot smarter than the old Intel 8088. Their machine languages have some commands that are up to 64 bits (8 bytes) wide. They also have at least a 64-bit frontside bus that can handle more than just 8 bits. They don't want RAM to give them a puny 8 bits at a time! To optimize the flow of data into and out of the CPU, the modern MCC provides at least 64 bits of data every time the CPU requests information from RAM.

Modern DRAM sticks come in 32-bit- and 64-bit-wide data form factors with a varying number of chips. Many techs describe these memory modules by their width, so we call them ×32 and ×64. Note that this number does not describe the width of the individual DRAM chips on the module. When you read or hear about by whatever memory, you need to know whether that person is talking about the DRAM width or the module width. When the CPU needs certain bytes of data, it requests those bytes via the address bus. The CPU does not know the physical location of the RAM that stores that data, nor the physical makeup of the RAM---such as how many DRAM chips work together to provide the 64-bit-wide memory rows. The MCC keeps track of this and just gives the CPU whichever bytes it requests (see Figure 4-8).

Figure 4-8  The MCC knows the real location of the DRAM.

Try This!

Dealing with Old RAM

Often in the PC world, old technology and ways of doing things are reimple-mented with some newer technology. A tech who knows these ancient ways will have extra opportunities. Many thousands of companies---including hospitals, auto repair places, and more---use very old proprietary applications that keep track of medical records, inventory, and so on. If you're called to work on one of these ancient systems, you need to know how to work with old parts, so try this.

Obtain an old computer. Ask your uncle, cousin, or Great Aunt Edna if they have a PC collecting dust in a closet that you can use. Failing that, go to a sec-ondhand store or market and buy one for a few dollars.

Open up the system and check out the RAM. Remove the RAM from the motherboard and then replace it to familiarize yourself with the internals. You never know when some critical system will go down and need repair immediately---and you're the one to do it!

Consumer RAM

If modern DRAM modules come in sizes much wider than a byte, why do people still use the word "byte" to describe how much DRAM they have? Convention. Habit. Rather than using a label that describes the electronic structure of RAM, common usage describes the total capacity of RAM on a stick in bytes. John has a single 8-GB stick of RAM on his motherboard, for example, and Sally has two 4-GB sticks. Both systems have a total of 8 GB of system RAM. That's what your clients care about. Having enough RAM makes their systems snappy and stable; not enough RAM means their systems run poorly. As a tech, you need to know more, of course, to pick the right RAM for many different types of computers.

Types of RAM

Development of newer, wider, and faster CPUs and MCCs motivates DRAM manufacturers to invent new DRAM technologies that deliver enough data at a single pop to optimize the flow of data into and out of the CPU.

SDRAM

Most modern systems use some form of synchronous DRAM (SDRAM). SDRAM is still DRAM, but it is synchronous---tied to the system clock, just like the CPU and MCC, so the MCC knows when data is ready to be grabbed from SDRAM. This results in little wasted time.

SDRAM made its debut in 1996 on a stick called a dual inline memory module (DIMM). The early SDRAM DIMMs came in a wide variety of pin sizes. The most common pin sizes found on desktops were the 168-pin variety. Laptop DIMMs came in 68-pin, 144-pin (see Figure 4-9), or 172-pin micro-DIMM packages, as well as the 72-pin, 144-pin, or 200-pin small-outline DIMM (SO-DIMM) form factors (see Figure 4-10). With the exception of the 32-bit 72-pin SO-DIMM, all these DIMM varieties delivered 64-bit-wide data to match the 64-bit data bus of every CPU since the original Pentium.

Figure 4-9  144-pin micro-DIMM (photo courtesy of Micron Technology, Inc.)

Figure 4-10  A (168-pin) DIMM above a (144-pin) SO-DIMM

EXAM TIP   Some manufacturers (and CompTIA) drop the hyphen: SODIMM. You might see the RAM package spelled as SO-DIMM, SODIMM, or even SoDIMM.

To take advantage of SDRAM, you needed a PC designed to use SDRAM. If you had a system with slots for 168-pin DIMMs, for example, your system used SDRAM. A DIMM in any one of the DIMM slots could fill the 64-bit bus, so each slot was called a bank. You could install one, two, or more sticks and the system would work. Note that on laptops that used the 72-pin SO-DIMM, you needed to install two sticks of RAM to make a full bank, because each stick only provided half the bus width.

SDRAM was tied to the system clock, so its clock speed matched the frontside bus. Five clock speeds were commonly used on the early SDRAM systems: 66, 75, 83, 100, and 133 MHz. The RAM speed had to match or exceed the system speed, or the computer would be unstable or wouldn't work at all. These speeds were prefixed with a "PC" in the front, based on a standard forwarded by Intel, so SDRAM speeds were PC66 through PC133. For a Pentium III computer with a 100-MHz frontside bus, you needed to buy SDRAM DIMMs rated to handle it, such as PC100 or PC133.

DDR SDRAM

AMD and many major system and memory makers threw their support behind a new RAM technology, double data rate SDRAM (DDR SDRAM). DDR SDRAM basically copied a proprietary memory solution developed by Rambus, doubling the throughput of SDRAM by making two processes for every clock cycle. This synchronized (pardon the pun) nicely with the Athlon and later AMD processors' double-pumped frontside bus. DDR SDRAM could not run as fast as RDRAM (DDR SDRAM's more expensive and less popular predecessor)---although relatively low frontside bus speeds made that a moot point---but cost only slightly more than regular SDRAM.

NOTE   RDRAM, short for Rambus DRAM (named for the company that developed it, Rambus, Inc.), was initially introduced as a replacement for regular SDRAM. While faster than SDRAM, RDRAM was ultimately rejected by the industry due to delays in development and high prices compared to its predecessor.

DDR SDRAM for desktops come in 184-pin DIMMs. These DIMMs match 168-pin DIMMs in physical size but not in pin compatibility (see Figure 4-11). The slots for the two types of RAM appear similar as well but have different guide notches, so you can't insert either type of RAM into the other's slot. DDR SDRAM for laptops come in either 200-pin SO-DIMMs or 172-pin micro-DIMMs (see Figure 4-12).

Figure 4-11  DDR SDRAM

Figure 4-12  172-pin DDR SDRAM micro-DIMM (photo courtesy of Kingston/Joint Harvest)

NOTE   Most techs drop some or all of the SDRAM part of DDR SDRAM when engaged in normal geekspeak. You'll hear the memory referred to as DDR, DDR RAM, and the weird hybrid, DDRAM.

Following the lead of AMD and other manufacturers, the PC industry adopted DDR SDRAM as the standard system RAM. In the summer of 2003, Intel relented and stopped producing motherboards and memory controllers that required RDRAM.

One thing is sure about PC technologies: any good idea that can be copied will be copied. One of Rambus' best concepts was the dual-channel architecture---using two sticks of RDRAM together to increase throughput. Manufacturers released motherboards with MCCs that support dual-channel architecture using DDR SDRAM. Dual-channel DDR motherboards use regular DDR sticks, although manufacturers often sell RAM in matched pairs, branding them as dual-channel RAM.

Dual-channel DDR requires two identical sticks of DDR and they must snap into two paired slots. Many motherboards offer four slots (see Figure 4-13).

Figure 4-13  A motherboard showing four RAM slots. By populating the same-colored slots with identical RAM, you can run in dual-channel mode.

SIM   I've got a great Chapter 4 Challenge! sim on calculating RAM speeds at https//www.totalsem.com/110X. Check it out right now!

NOTE   DDR SDRAM was improved in the form of DDR2. DDR2 was faster and more power efficient than the original DDR and found widespread adoption in the industry before eventually being replaced by DDR3, DDR4, and now DDR5. While no longer used in PCs, DDR2 modules can still sometimes be found in use as memory for some older devices such as printers.

1101

Current motherboards use one of three speeds of RAM, DDR3, DDR4, and DDR5. Let's start with DDR3.

DDR3

DDR3 boasts higher speeds, more efficient architecture, and around 30 percent lower power consumption than DDR2 RAM. Just like its predecessor, DDR3 uses a 240-pin DIMM, albeit one that is slotted differently to make it difficult for users to install the wrong RAM in their system without using a hammer (see Figure 4-14). DDR3 SO-DIMMs for portable computers have 204 pins. Neither fits into a DDR2 socket.

Figure 4-14  DDR2 DIMM on top of a DDR3 DIMM

EXAM TIP   The CompTIA 220-1101 exam loves to test you on pin counts with RAM! It will challenge your knowledge of the various RAM types including DDR3, DDR4, and DDR5. Make sure you know their individual characteristics and differences. DDR3 DIMMs have 240 pins, for example, and DDR3 SO-DIMMs have 204 pins.

In addition to having an impressive 8-bit buffer for bandwidth, some DDR3 (and later) modules also include a feature called XMP, or Extreme Memory Profile, that enables power users to overclock their RAM easily, boosting their already fast memory. DDR3 modules also use higher-density memory chips, up to 16-GB DDR3 modules. AMD's version of XMP is called AMP, for AMD Memory Profile.

NOTE   Do not confuse DDRx with GDDRx; the latter is a type of memory used solely in video cards (e.g., GDDR5). See Chapter 17 for the scoop on video-specific types of memory.

Some motherboards that support DDR3 also support features called triple-channel memory architecture or quad-channel memory architecture, which work a lot like dual-channel, but with three or four sticks of RAM instead of two. More recently, Intel and AMD systems have switched back to dual-channel, although there's plenty of systems out there using triple- or quad-channel architectures.

EXAM TIP   Be sure you are familiar with single-, dual-, triple-, and quad-channel memory architectures.

Table 4-1 shows common DDR3 speeds. Note that DDR3 I/O speeds are quadruple the clock speeds, whereas DDR2 I/O speeds are only double the clock. This speed increase is due to the increased buffer size, which enables DDR3 to grab twice as much data every clock cycle as DDR2 can.

Table 4-1  DDR3 Speeds

DDR4

DDR4 arrived on the scene in late 2014 with much fanfare and slow adoption, although it's the mainstream channel memory architecture now. DDR4 offers higher density and lower voltages than DDR3, and can handle faster data transfer rates. In theory, manufacturers could create DDR4 DIMMs up to 512 GB. DIMMS running DDR4 top out at 64 GB, compared to the 16 GB max of DDR3, but run at only 1.2 V. (There's a performance version that runs at 1.35 V and a low-voltage version at 1.05 V too.)

NOTE   While DDR4 DIMMs generally won't exceed 64 GB, some manufacturers have pushed the envelope, creating individual DIMMs with up to a whopping 256 GB. These high-capacity DIMMs are almost exclusively intended for enterprise-level use.

DDR4 uses a 288-pin DIMM, so DDR4 DIMMs are not backward compatible with DDR3 slots. DDR4 SO-DIMMs have 260 pins that are not compatible with DDR3 204-pin SO-DIMM slots. Some motherboard manufacturers have released boards that offer support for both DDR3 and DDR4, by providing both slot types.

With DDR4, most techs have switched from bit rate to megatransfers per second (MT/s), a way to describe the number of data transfer operations happening at any given second. For DDR4, the number is pretty huge. To determine DDR4 bandwidth, multiply the clock speed in MHz by 8. The result is not only the bandwidth in MT/s, but also the DDR4 speed rating. To determine the PC speed rating, multiply the DDR4 speed rating by 8 again. Table 4-2 shows some DDR4 speeds and labels.

Table 4-2  Standard DDR4 Varieties

DDR5

In 2017, channel memory architecture manufacturers began working on a successor to DDR4, and in 2020, they launched the first commercially available DDR5 DRAM chip. Much like previous upgrades to DDR, DDR5 boasts the potential for doubled bandwidth, decreased power consumption, and quadrupled DIMM capacity. The highest currently available bandwidth at the time of writing is 7200 MT/s. Power consumption is more efficient as well, with the voltage per DIMM decreasing to 1.1 V from 1.2 V. Power management is handled by an onboard circuit known as a power management integrated circuit, or PMIC, as opposed to DDR4 that was managed by the motherboard. The range of available DIMM sizes has gone from a maximum of 64 GB all the way up to a whopping 256 GB. As with previous improvements in DDR technology, DDR5 is not backward compatible with DDR4. DDR5 DIMMs have 288 pins, like DDR4 (see Figure 4-15), while SO-DIMMs slightly increase the pin count from 260 to 262.

Figure 4-15  DDR5 (top) vs. DDR4 (bottom) pin comparison

To determine the bandwidth of DDR5 RAM, take the channel memory architecture clock speed in MHz and multiply by 8. This number is both the bandwidth in MT/s and the DDR5 speed rating. To find the PC speed rating, multiply the DDR5 speed rating by 8 again. Table 4-3 shows the bandwidth and speed ratings for some varieties of DDR5 RAM.

Table 4-3  Standard DDR5 Varieties

While DDR5 hasn't quite achieved a high enough bandwidth to double that of the fastest DDR4 DIMMs yet, it's important to remember DDR4 also took time to reach its maximum potential after its initial release. Channel memory architecture manufacturers announce new DDR5 breakthroughs fairly regularly, and although DDR5 has yet to be widely adopted, there is no reason to think that it won't eventually find the same success as its DDR forebears.

RAM Variations

Within each class of RAM, you'll find variations in packaging, speed, quality, and the capability to handle data with more or fewer errors. Higher-end systems often need higher-end RAM, so knowing these variations is of crucial importance to techs.

Double-Sided DIMMs

Every type of RAM stick comes in one of two types: single-sided RAM and double-sided RAM. As their name implies, single-sided sticks have chips on only one side of the stick. Double-sided sticks have chips on both sides (see Figure 4-16). Double-sided sticks are basically two sticks of RAM soldered onto one board. There's nothing wrong with double-sided RAM sticks other than the fact that some motherboards either can't use them or can only use them in certain ways---for example, only if you use a single stick and it goes into a certain slot.

Figure 4-16  Double-sided DDR SDRAM

Latency

Different types of RAM respond to electrical signals at varying rates. When the memory controller starts to grab a line of memory, for example, a slight delay occurs; think of it as the RAM getting off the couch. After the RAM sends out the requested line of memory, there's another slight delay before the memory controller can ask for another line---the RAM sat back down. The delay in RAM's response time is called its latency.

If two types of RAM have the same speed rating, RAM with a lower latency (such as CL17) is slightly faster than RAM with a higher latency (such as CL19) because it responds more quickly. The CL refers to clock cycle delays. The 17 means that the memory delays 17 clock cycles before delivering the requested data; the 19 means a 19-cycle delay. Because it's measured in clock cycles, CL is relative to the clock speed of the RAM---a 19-cycle delay takes up more real-world time at a lower clock speed than it will at a higher clock speed.

Back when DDR2 and DDR3 were the latest and greatest, these latency numbers were a big deal. Gamers and other PC enthusiasts paid a handsome premium for lower-latency RAM. (See Figure 4-17.) When DDR4 debuted, its relatively high CL numbers made enthusiasts question the memory companies, afraid it would be too slow. In real-world tests, DDR4's higher clock speeds result in latencies in line with the older DDR3. It's still worth looking at latency when you go memory shopping, but it's a lot less important than it used to be.

Figure 4-17  Ancient RAM stick

NOTE   Latency numbers reflect how many clicks of the system clock it takes before the RAM responds. If you speed up the system clock---say, from 200 MHz to 266 MHz---the same stick of RAM might take an extra click before it can respond. When you take RAM out of an older system and put it into a newer one, you might get a seemingly dead PC, even though the RAM fits in the DIMM slot. Many motherboards enable you to adjust the RAM timings manually. If yours does so, try raising the latency to give the slower RAM time to respond. See Chapter 5 to learn how to make these adjustments (and how to recover if you make a mistake).

From a tech's standpoint, you need to get the proper RAM for the system you're working on. If you put a high-latency stick in a motherboard set up for a low-latency stick, you'll get an unstable or completely dead PC. Check the motherboard manual or RAM manufacturer's Web site and get the quickest RAM the motherboard can handle, and you should be fine.

Today's PCs that need to watch for RAM errors use a special type of RAM called error correction code RAM (ECC RAM). ECC is a major advance in error checking on DRAM. ECC detects and corrects any time a single bit is flipped, on-the-fly. It can detect but not correct a double-bit error. The checking and fixing come at a price, however, as ECC RAM is always slower than non-ECC RAM.

ECC DRAM comes in every DIMM package type and can lead to some odd-sounding numbers. You can find DDR3 (see Figure 4-18) or DDR4 RAM sticks, for example, that come in 240-pin, 72-bit versions. Similarly, you'll see 200-pin, 72-bit SO-DIMM format. The extra 8 bits beyond the 64-bit data stream are for the ECC. All DDR5 DIMMs have a variant of ECC built right into the chip itself, which protects against bit-flips in the chip. This differs from classic ECC, which protects against bit-flips in transit. DDR5 DIMMs are also available with or without classic ECC functionality.

Figure 4-18  Stick of ECC DDR3 with nine memory chips

You might be tempted to say, "Gee, maybe I want to try this ECC RAM." Well, don't! To take advantage of ECC RAM, you need a motherboard designed to support ECC. Only expensive motherboards for high-end systems use ECC. The special-use-only nature of ECC makes it fairly rare in desktop systems. Plenty of techs with years of experience have never even seen ECC RAM.

NOTE   Some memory manufacturers call the technology error checking and correction (ECC). Don't be thrown off if you see the phrase---it's the same thing, just a different marketing slant for error correction code.

Registered and Buffered Memory

When shopping for memory, especially for ECC memory, you are bound to come across the terms registered RAM or buffered RAM. Either term refers to a small register installed on some memory modules to act as a buffer between the DIMM and the memory controller. This little extra bit of circuitry helps compensate for electrical problems that crop up in systems with lots of memory modules, such as servers and big professional workstations.

The key thing to remember is that a motherboard will use either buffered or unbuffered RAM (that's typical consumer RAM), not both. If you insert the wrong module in a system you are upgrading, the worst that will happen is a blank screen and a lot of head scratching.

EXAM TIP   The CompTIA A+ 1101 exam covers DDR3, DDR4, and DDR5. You won't find DDR or DDR2 on the exam.

Working with RAM

Whenever people ask me what single hardware upgrade they can do to improve their system performance, I always tell them the same thing---add more RAM. Adding more RAM can improve overall system performance, processing speed, and stability---if you get it right. Botching the job can cause dramatic system instability, such as frequent, random crashes and reboots. Every tech needs to know how to install and upgrade system RAM of all types.

To get the desired results from a RAM upgrade, you must first determine if insufficient RAM is the cause of system problems. Second, you need to pick the proper RAM for the system. Finally, you must use good installation practices. Always store RAM sticks in antistatic packaging whenever they're not in use, and use strict ESD handling procedures. Like many other pieces of the PC, RAM is very sensitive to ESD and other technician abuse (see Figure 4-19).

Figure 4-19  Don't do this! Grabbing the contacts is a bad idea!

Do You Need More RAM?

Two symptoms point to the need for more RAM in a PC: general system sluggishness and excessive hard drive accessing. If programs take forever to load and running programs seem to stall and move more slowly than you would like, the problem could stem from insufficient RAM.

A friend with an older Windows system complained that her PC seemed snappy when she first got it but now takes a long time to do the things she wants to do with it, such as photograph retouching in Adobe Photoshop. Over the years, new applications and updates to her existing operating system and applications piled up until her system, with only 4 GB of RAM, was woefully insufficient for her tasks---she kept maxing out the RAM and thus the system slowed to a crawl. I replaced her single 4-GB stick with a pair of 8-GB sticks and suddenly she had the speedy workstation she desired.

Another common example of RAM-related sluggishness, and one that most of us have encountered at some point in time, is related to Web browser tabs. Over the years, Web browsers have become more complex, incorporating new features, plug-ins, and additional security measures, among other additions. As a result, they have become more resource intensive, and Web browsing habits that had no effect on your system's performance five years ago will bring that same system to its knees today. As with the previous example, adding more RAM will almost certainly fix the problem.

Excessive hard drive activity when you move between programs points to a need for more RAM. Every computer has the capability to make a portion of your hard drive look like RAM in case you run out of real RAM.

Virtual Memory

Computers use a portion of the hard drive (or solid-state drive) as an extension of system RAM called virtual memory. The operating system uses part of the available drive space to save a page file or swap file. When a computer starts running out of real RAM because you've loaded too many programs, the system swaps less-used programs from RAM to the page file, opening more space for programs currently active. All versions of Windows, macOS, and Linux use virtual memory. Let's use a typical Windows PC as an example of how paging works.

EXAM TIP   While virtual memory is generally the terminology you'll hear out in the wild, you may see it referred to as "virtual RAM" on the exam. (See Chapter 22 for an entirely different type of virtual RAM.)

Let's assume you have a PC with 8 GB of RAM. Figure 4-20 shows the system RAM as a thermometer with gradients from 0 to 8 GB. As programs load, they take up RAM, and as more and more programs are loaded (labeled A, B, and C in the figure), more RAM is used.

Figure 4-20  A RAM thermometer showing that more programs take more RAM

At a certain point, you won't have enough RAM to run any more programs (see Figure 4-21). Sure, you could close one or more programs to make room for yet another one, but you can't keep all of the programs running simultaneously. This is where virtual memory comes into play.

Figure 4-21  Not enough RAM to load program D

Windows' virtual memory starts by creating a page file that resides somewhere on your hard drive. The page file works like a temporary storage box. Windows removes running programs temporarily from RAM into the page file so other programs can load and run. If you have enough RAM to run all your programs, Windows does not need to use the page file---Windows brings the page file into play only when insufficient RAM is available to run all open programs.

NOTE   Virtual memory is a fully automated process and does not require any user intervention. This is true of virtual memory in Windows, macOS, and Linux.

To load, Program D needs a certain amount of free RAM. Clearly, this requires unloading some other program (or programs) from RAM without actually closing any programs. Windows looks at all running programs---in this case A, B, and C---and decides which program is the least used. That program is then cut out of or swapped from RAM and copied into the page file. In this case, Windows has chosen Program B (see Figure 4-22). Unloading Program B from RAM provides enough RAM to load Program D (see Figure 4-23).

Figure 4-22  Program B being unloaded from channel memory architecture

Figure 4-23  Program B stored in the page file, making room for Program D

It is important to understand that none of this activity is visible on the screen. Program B's window is still visible, along with those of all the other running programs. Nothing tells the user that Program B is no longer in RAM (see Figure 4-24).

Figure 4-24  You can't tell whether a program is swapped or not.

So what happens if you click on Program B's window to bring it to the front? The program can't actually run from the page file; it must be loaded back into RAM. First, Windows decides which program must be removed from RAM, and this time Windows chooses Program C (see Figure 4-25). Then it loads Program B into RAM (see Figure 4-26).

Figure 4-25  Program C is swapped to the page file.

Figure 4-26  Program B is swapped back into RAM.

Swapping programs to and from the page file and RAM takes time. Although no visual clues suggest that a swap is taking place, the machine slows down quite noticeably as Windows performs the swaps. Page files are a crucial aspect of Windows operation.

Windows handles page files automatically, but occasionally you'll run into problems and need to change the size of the page file or delete it and let Windows re-create it automatically. The page file is pagefile.sys. You can often find it in the root directory of the C: drive, but again, that can be changed. Wherever it is, the page file is a hidden system file, which means in practice that you'll have to play with your folder-viewing options to see it.

If Windows needs to access the page file too frequently, you will notice the hard drive access LED going crazy as Windows rushes to move programs between RAM and the page file in a process called disk thrashing. Windows uses the page file all the time, but excessive disk thrashing suggests that you need more RAM.

System RAM Recommendations

Microsoft sets very low the minimum RAM requirements listed for the various Windows operating systems to get the maximum number of users to upgrade or convert, and that's fine. Microsoft recommends a minimum system requirement of 1 GB of RAM for 32-bit versions of Windows, 2 GB of RAM for 64-bit versions, and 4 GB of RAM for Windows 11, which is only available in a 64-bit version. I think that results in dreadfully sluggish computers. Here are my recommendations:

-   32-bit Windows (8/8.1/10) 2 GB to get by; 4 GB for best results

-   64-bit Windows (8/8.1/10/11) 8 GB to get by; 16 GB for a solid machine; 32+ GB for any machine doing serious, processor-intensive work

The latest versions of macOS require a minimum of 4 GB of RAM. Like Windows, however, the 64-bit-only OS does much better with a lot more RAM. I would go with 8 GB at a minimum, 16 GB for good performance, and more for peak performance.

NOTE   Beware sealed systems! Almost all smartphones and tablets are sealed. Today many desktop and laptop systems---in the past easily upgraded by a good tech---are sealed, making upgrades impossible. If you get a sealed system, don't scrimp on the RAM at the time of purchase!

Linux RAM requirements and recommendations depend entirely on which distribution (distro) is being used. The mainstream distros, like Ubuntu, have requirements similar to Windows and macOS, but many distros get by on very minimal system requirements.

Determining Current RAM Capacity

Before you go get RAM, you obviously need to know how much RAM you currently have in your PC. Windows displays this amount in the System Control Panel applet (see Figure 4-27). You can also access the screen with the WINDOWS-PAUSE/BREAK keystroke combination on standard keyboards.

Figure 4-27  Mike's Windows 10 system only has 8 GB of RAM.

Windows also includes the handy Performance tab in the Task Manager (as shown in Figure 4-28). The Performance tab includes a lot of information about the amount of RAM being used by your PC. Access the Task Manager by pressing CTRL-SHIFT-ESC and selecting the Performance tab.

Figure 4-28  Performance tab in Windows 10 Task Manager

Getting the Right RAM

To do the perfect RAM upgrade, determine the optimum capacity of RAM to install and then get the right RAM for the motherboard. Your first two stops toward these goals are the inside of the case and your motherboard manual. Open the case to see how many sticks of RAM you have installed currently and how many free slots you have open.

Check the motherboard book or RAM manufacturer's Web site to determine the total capacity of RAM the system can handle and what specific technology works with your system.

You can't put DDR4 into a system that can only handle DDR3 SDRAM, after all, and it won't do you much good to install a pair of 8-GB DIMMs when your system tops out at 8 GB. Figure 4-29 shows the RAM limits for an ASUS-brand motherboard.

Figure 4-29  The motherboard book shows how much RAM the motherboard will handle.

NOTE   The freeware CPU-Z program tells you the total number of slots on your motherboard, the number of slots used, and the exact type of RAM in each slot---very handy. CPU-Z not only determines the latency of your RAM but also lists the latency at a variety of motherboard speeds. The media accompanying this book has a copy of CPU-Z, so check it out or download it from https://www.cpuid.com.

Mix and Match at Your Peril

All motherboards can handle different capacities of RAM. If you have three slots, you may put a 4-GB stick in one and an 8-GB stick in the other with a high chance of success. To ensure maximum stability in a system, however, shoot for as close as you can get to uniformity of RAM. Choose RAM sticks that match in technology, capacity, speed, and latency (CL).

Mixing Speeds

With so many different DRAM speeds available, you may often find yourself tempted to mix speeds of DRAM in the same system. Although you may get away with mixing speeds on a system, the safest, easiest rule to follow is to use the speed of DRAM specified in the motherboard book, and make sure that every piece of DRAM runs at that speed. In a worst-case scenario, mixing DRAM speeds can cause the system to lock up every few seconds or every few minutes. You might also get some data corruption. Mixing speeds sometimes works fine, but don't do your tax return on a machine with mixed DRAM speeds until the system has proven to be stable for a few days. The important thing to note here is that you won't break anything, other than possibly data, by experimenting.

Okay, I have mentioned enough disclaimers. Modern motherboards provide some flexibility regarding DRAM speeds and mixing. First, you can use DRAM that is faster than the motherboard specifies. For example, if the system needs PC-19200 DDR4, you may put in PC-25600 DDR4 and it should work fine. Faster DRAM is not going to make the system run any faster, however, so don't look for any system improvement.

Second, you can sometimes get away with putting one speed of DRAM in one bank and another speed in another bank, as long as all the speeds are as fast as or faster than the speed specified by the motherboard. Don't bother trying to put different-speed DRAM sticks in the same bank with a motherboard that uses dual-channel DDR.

Installing DIMMs

Installing DRAM is so easy that it's one of the very few jobs I recommend to non-techie folks. First, attach an antistatic wrist strap or touch some bare metal on the power supply to ground yourself and avoid ESD. Then swing the side tabs on the RAM slots down from the upright position. Pick up a stick of RAM---don't touch those contacts---and line up the notch or notches with the raised portion(s) of the DIMM socket (see Figure 4-30). A good hard push down is usually all you need to ensure a solid connection. Make sure that the DIMM snaps into position to show it is completely seated. Also, notice that the one or two side tabs move in to reflect a tight connection.

Figure 4-30  Inserting a DIMM

Your motherboard should detect and automatically set up any DIMM you install, assuming you have the right RAM for the system, using a technology called serial presence detect (SPD). RAM makers add a handy chip to modern sticks called the SPD chip (see Figure 4-31). The SPD chip stores all the information about your DRAM, including size, speed, ECC or non-ECC, registered or unregistered, and other more technical bits of information.

Figure 4-31  SPD chip on a stick

When a PC boots, it queries the SPD chip so that the MCC knows how much RAM is on the stick, how fast it runs, and other information. Any program can query the SPD chip. Take a look at Figure 4-32 with the results of the popular CPU-Z program showing RAM information from the SPD chip.

Figure 4-32  CPU-Z showing RAM information

All new systems count on SPD to set the RAM timings properly for your system when it boots. If you add a RAM stick with a bad SPD chip, you'll get a POST error message and the system will not boot. You can't fix a broken SPD chip; you just buy a new stick of RAM.

Installing SO-DIMMs in Laptops

It wasn't that long ago that adding RAM to a laptop was either impossible or required you to send the system back to the manufacturer. Long ago, laptop makers used expensive, proprietary, custom-made RAM packages that were hard to handle. Wide acceptance of SO-DIMMs solved these problems for a time---until ultra-thin laptops started turning up with soldered-on RAM. Most larger laptops still provide relatively convenient access to their SO-DIMMs, making it easy to add or replace RAM.

Access to RAM usually requires removing a panel or lifting up the keyboard---the procedure varies among laptop manufacturers. Figure 4-33 shows a typical laptop RAM access panel. You can slide the panel off to reveal the SO-DIMMs. Slide the pins into position and snap the SO-DIMM down into the retaining clips (see Figure 4-34).

Figure 4-33  A RAM access panel on a lap

Figure 4-34  Snapping in a SO-DIMM

Before doing any work on a laptop, turn the system off, disconnect it from the AC wall socket, and remove all batteries. If you are working on a laptop with a built-in battery, consult the service manual and look for a service mode, or similarly named, procedure. Enabling this mode will cut off power from the installed battery, making the laptop safe to work on. Finally, as always, use an antistatic wrist strap to keep ESD from damaging the system.

Troubleshooting RAM

"Memory" errors show up in a variety of ways on modern systems, including system lockups, page faults, and other error screens. These errors can indicate bad RAM but often point to something completely unrelated. This is especially true with intermittent problems. Techs need to recognize these errors and determine which part of the system caused the memory error. Then they need to follow up with various testing methods.

System lockups and page faults (they often go hand in hand) in Windows can indicate a problem with RAM. A system lockup is when the computer stops functioning. A page fault is a milder error that can be caused by memory issues but not necessarily system RAM problems. Certainly page faults look like RAM issues because Windows generates frightening error messages filled with long strings of hexadecimal digits, such as "KRNL386 caused a page fault at 03F2:25A003BC." Just because the error message contains a memory address, however, does not mean that you have a problem with your RAM. Write down the address. If it repeats in later error messages, you probably have a bad RAM stick. If Windows displays different memory locations, you need to look elsewhere for the culprit.

Every once in a while, something potentially catastrophic happens within the PC, some little electron hits the big red panic button, and the operating system has to shut down certain functions before it can save data. This panic button inside the PC is called a non-maskable interrupt (NMI), more simply defined as an interruption the CPU cannot ignore. An NMI manifests as a proprietary crash screen. In Windows 10, for example, the crash screen is what techs call the blue screen of death (BSoD)---a bright blue screen with a scary-sounding error message on it (see Figure 4-35).

Figure 4-35  Blue screen of death

Windows 10/11 display a blue screen with a sad face and the words to the effect of Windows has a problem. Restart the machine. A macOS machine might display a spinning rainbow wheel sometimes called the spinning pinwheel of death (SPoD) or, more likely, will simply restart.

Bad RAM sometimes triggers an NMI, although often the culprit lies with buggy programming or clashing code. The BSoD/SPoD varies across Windows and macOS versions and operating systems, and it would require a much lengthier tome than this one to cover all the variations. Suffice it to say that RAM could be the problem when that delightful blue screen or pinwheel appears.

Finally, intermittent memory errors can come from a variety of sources, including a dying power supply, electrical interference, buggy applications, buggy hardware, and so on. These errors show up as lockups, general protection faults, and page faults, but they never have the same address or happen with the same applications. I always check the power supply first.

Once you discover that you may have a RAM problem, you have a couple of options. First, several companies manufacture hardware RAM-testing devices. Second, you can use the method I use---replace and pray. Open the system case and replace each stick, one at a time, with a known-good replacement stick. (You have one of those lying around, don't you?) This method, although potentially time-consuming, certainly works. With PC prices as low as they are now, you could simply replace the whole system for less than the price of a dedicated RAM tester.

Third, you could run a software-based tester on the RAM. Because you have to load a software tester into the memory it's about to scan, there's always a small chance that simply starting the software RAM tester might cause an error. Still, you can find some pretty good free ones out there. Windows 7 and later include the Windows Memory Diagnostic tool, which can automatically scan your computer's RAM when you encounter a problem. If you're using another OS, my favorite tool is the open source Memtest86+ (https://www.memtest.org). The Memtest86+ software exhaustively checks your RAM and reports bad RAM when it finds it (see Figure 4-36).

Figure 4-36  Memtest86+ detecting failing RAM

NOTE   A general protection fault (GPF) is an error that can cause an application to crash. Often GPFs are caused by programs stepping on each other's toes. Chapter 16 goes into more detail on GPFs and other Windows errors.

Chapter Review

Questions

1\.   Steve adds a second 8-GB 288-pin DIMM to his PC, which should bring the total RAM in the system up to 16 GB. The PC has an Intel Core i7 4-GHz processor and four 288-pin DIMM slots on the motherboard. When he turns on the PC, however, only 8 GB of RAM shows up in Windows Settings app. Which of the following is most likely to be the problem?

A.   Steve failed to seat the RAM properly.

B.   Steve put DDR4 in a DDR3 slot.

C.   The CPU cannot handle 16 GB of RAM.

D.   The motherboard can use only one RAM slot at a time.

2\.   Scott wants to add 8 GB of PC3-12800 DDR3 to an aging but still useful desktop system. The system has a 200-MHz motherboard and currently has 4 GB of non-ECC DDR3 RAM in the system. What else does he need to know before installing?

A.   What speed of RAM he needs

B.   What type of RAM he needs

C.   How many pins the RAM has

D.   If the system can handle that much RAM

3\.   What is the primary reason that DDR4 RAM is faster than DDR3 RAM?

A.   The core speed of the DDR4 RAM chips is faster.

B.   The input/output speed of the DDR4 RAM is faster.

C.   DDR3 RAM is dual-channel and DDR4 RAM is quad-channel.

D.   DDR3 RAM uses 240-pin DIMMs and DDR4 uses 288-pin DIMMs.

4\.   What is the term for the delay in the RAM's response to a request from the MCC?

A.   Variance

B.   MCC gap

C.   Latency

D.   Fetch interval

5\.   How does an NMI manifest on a macOS system?

A.   Blue screen of death.

B.   Spinning pinwheel of death.

C.   Interrupt of death.

D.   NMIs only happen on Windows systems.

6\.   Silas has an AMD-based motherboard with two sticks of DDR3 RAM installed in two of the three RAM slots, for a total of 8 GB of system memory. When he runs CPU-Z to test the system, he notices that the software claims he's running single-channel memory. What could be the problem? (Select the best answer.)

A.   His motherboard only supports single-channel memory.

B.   His motherboard only supports dual-channel memory with DDR2 RAM, not DDR3.

C.   He needs to install a third RAM stick to enable dual-channel memory.

D.   He needs to move one of the installed sticks to a different slot to activate dual-channel memory.

7\.   Which of the following Control Panel applets will display the amount of RAM in your PC?

A.   System

B.   Devices and Printers

C.   Device Manager

D.   Action Center

8\.   What is the best way to determine the total capacity and specific type of RAM your system can handle?

A.   Check the motherboard book.

B.   Open the case and inspect the RAM.

C.   Check the Device Manager.

D.   Check the System utility in the Control Panel.

9\.   Gregor installed a third stick of known-good RAM into his Core i7 system, bringing the total amount of RAM up to 12 GB. Within a few days, though, he started having random lockups and reboots, especially when doing memory-intensive tasks such as gaming. What is most likely the problem?

A.   Gregor installed DDR2 RAM into a DDR3 system.

B.   Gregor installed DDR3 RAM into a DDR4 system.

C.   Gregor installed RAM that didn't match the speed or quality of the RAM in the system.

D.   Gregor installed RAM that exceeded the speed of the RAM in the system.

10\.   Cindy installed a second stick of DDR4 RAM into her Core i5 system, bringing the total system up to 16 GB. Within a short period of time, though, she begin experiencing blue screens of death. What could the problem be?

A.   She installed faulty RAM.

B.   The motherboard could only handle 12 GB of RAM.

C.   The motherboard needed dual-channel RAM.

D.   There is no problem. Windows always does this initially but gets better after crashing a few times.

Answers

1\.   A. Steve failed to seat the RAM properly.

2\.   D. Scott needs to know if the system can handle that much RAM.

3\.   B. The input/output speed of DDR4 RAM is faster than that of DDR3 RAM (although the latency is higher).

4\.   C. Latency is the term for the delay in the RAM's response to a request from the MCC.

5\.   B. A non-maskable interrupt on a macOS system often results in the spinning pinwheel of death.

6\.   D. Motherboards can be tricky and require you to install RAM in the proper slots to enable dual-channel memory access. In this case, Silas should move one of the installed sticks to a different slot to activate dual-channel memory architecture. (And he should check the motherboard manual for the proper slots.)

7\.   A. You can use the System applet to see how much RAM is currently in your PC.

8\.   A. The best way to determine the total capacity and specific type of RAM your system can handle is to check the motherboard book.

9\.   C. Most likely, Gregor installed RAM that didn't match the speed or quality of the RAM in the system.

10\.   A. If you have no problems with a system and then experience problems after installing something new, chances are the something new is at fault.

Copy

copy

Highlight

highlight

Add Note

note

Get Link

link

table of contents

search

Settings

queue

close x

Preparing for certification?

Take Practice Test

chevron right

Skip to Content

Topics

Start Learning

Featured

Search 50,000+ courses, events, titles, and more

Chapter 4 RAM

Chapter 5 Firmware

Chapter 6 Motherboards

42h 21m remaining
