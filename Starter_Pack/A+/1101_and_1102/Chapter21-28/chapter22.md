CHAPTER 22

Virtualization

In this chapter, you will learn how to

-   Explain why virtualization is so highly adopted

-   Describe the service layers and architectures, and characteristics of cloud computing

The subject of this chapter, virtualization, can be a little slippery and hard to understand. A big reason is that virtualization isn't one concrete thing you can grab with your hands. There are many kinds of virtualization, and the thread tying them together isn't very obvious---it's just an idea.

The important idea at the heart of every kind of virtualization is to take an existing component (anything in or attached to the system) and make it more flexible by replacing it with a layer of software that (as far as anything interacting with the component can tell) behaves the same. This idea is so fundamental to modern computing that, way back in Chapter 4, we looked at a well-known application of it: virtual memory.

Once upon a time, computer programs had direct access to the system's RAM. Programs in modern systems actually access virtual memory---a layer of software that, as far as the program can tell, is RAM. Operating systems use the extra flexibility this layer of software provides to store the memory contents of active programs in RAM but swap the memory contents of idle programs out to a storage drive.

To virtualize something is to replace it with this more flexible layer of software. Why do we virtualize things? The answer is almost always because the extra flexibility enables us to do something new, makes things easier to manage, or both.

This chapter delves into virtualization in detail, starting with the reasons why virtualization is important today, and then looking at a collection of technologies that use virtualization extensively: cloud computing. Let's get started.

1101

Hardware Virtualization

One of the most important kinds of virtualization, hardware virtualization, takes the entire computer that an OS expects to interact with and virtualizes it. The physical host computer uses software known as a hypervisor to create environments (each saved in a separate file) that have virtual versions of all the "hardware" devices you need to install and run an OS. The hypervisor allocates fractions of the host's real hardware resources to power these virtual devices.

EXAM TIP   For clarity, I will specify what kind of virtualization I mean and only use the term "virtualization" by itself to refer to the broader idea. If you see "virtualization" by itself on the exam, however, it will almost certainly mean hardware virtualization!

These environments are called virtual machines (VMs) or guests. Figure 22-1 shows one such example: a Windows host system using a hypervisor called Hyper-V to run two guest virtual machines, one running Ubuntu Linux and another running Windows 10.

Figure 22-1  Hyper-V running Linux and Windows 10

The CompTIA A+ 1101 objectives expect you to be able to summarize the purpose of virtual machines. We'll build up to the list of purposes CompTIA has in mind by the end of this section, but first I want to get philosophical so that we don't lose sight of something.

Just as a hammer is a tool for the purpose of hitting things, a computer is a tool for the purpose of computing things. Virtualizing a computer doesn't change this---the purpose of a virtual machine is still to run computations! The benefits of hardware virtualization are to make virtual machines more convenient than physical computers in some situations, but they are just another tool we can use to meet a need or solve a problem.

Let's take a closer look how we can use hardware virtualization on our own local systems, and then address the elephant in the room---what are the benefits of virtual computers and what on Earth can you do with them? Then, I'll walk you through the process of setting up a VM of your own to experiment with, and finish the section with a look at how hardware virtualization tends to manifest on a server.

Client-side Virtualization

A normal operating system installed directly on the hardware uses programming called a supervisor (better known as the kernel) to handle very low-level interaction among hardware and software, such as task scheduling, allotment of time and resources, and so on. Figure 22-2 shows how the supervisor works between the OS and the hardware.

Figure 22-2  Supervisor on a generic single system

Hardware virtualization enables one machine---the host---to run multiple guest operating systems simultaneously. The CompTIA A+ 1101 objectives focus mostly on what CompTIA calls client-side virtualization---when the VM host also serves as someone's day-to-day workstation.

EXAM TIP   If you see the words "client-side" and "virtualization" in the same question on the exam, keep an open mind! As a term, "client-side virtualization" is vague. It refers to where the work is done---usually in contrast to server-side virtualization---and omits what kind of virtualization it is. I think CompTIA means client-side hardware virtualization, but CompTIA might mean client-side desktop virtualization. We'll discuss desktop virtualization later in the chapter.

In hardware virtualization, the hypervisor takes on the role of the supervisor---plus the added chore of dividing up the hardware resources among active virtual machines. Figure 22-3 shows a single hypervisor hosting three different guest virtual machines.

Figure 22-3  Hypervisor on a generic single system hosting three virtual machines

There are a fair number of hypervisors to choose from. Microsoft's Hyper-V (shown earlier in Figure 22-1) is included in Windows Server and Windows Pro. Another very popular hypervisor is Oracle VM VirtualBox (see Figure 22-4), which runs on Windows, macOS, and Linux.

Figure 22-4  Oracle VM VirtualBox

This is in no way a complete list. Many Linux users swear by KVM, for example, and VMware has long made a number of popular commercial hypervisors.

Benefits of Virtualization

One of the tricks to getting your mind around any given kind of virtualization is understanding why anyone bothers---what benefits are they getting from the extra flexibility? Hardware virtualization unlocks a lot of little benefits, so I'll focus on two big categories: saving resources and making systems easier to manage.

Saving Resources

A dirty little secret of modern life is that most people have things they almost never use---and big organizations are no different! When it comes to resource use, most computers and cars have a lot in common: they spend most of the time just sitting there, a little time partly occupied, and are only rarely used to their full capacity.

Before hardware virtualization, each OS needed a physical system. With a hypervisor, though, you can place multiple virtual servers or clients on a single physical system. Rather than one machine running a Windows file server, another Windows system acting as a DNS server, and a third machine running Linux for a DHCP server, why not use one physical computer to handle all three servers simultaneously as virtual machines?

The flexibility of virtual machines makes it possible to consolidate multiple systems down into a single box. Every physical computer requires a minimum amount of hardware, and a lot of that hardware---like its fans, power supply, and motherboard---require a minimum amount of electricity just to turn on. When organizations reduce the number of physical systems they need to do the same amount of work, they benefit from ongoing energy savings (see Figure 22-5).

Figure 22-5  Hardware virtualization saves power.

Lowering your energy bill is great, but it's just where the benefits start. Hardware consolidation reduces the time and money an organization spends maintaining hardware and enables it to entirely avoid purchasing expensive hardware that rarely if ever runs at full capacity during its useful lifetime.

These benefits are biggest for servers, but they also apply to desktop computers. A Windows user who needs regular access to Linux doesn't need two computers or a complex multi-boot setup---they just need a Windows hypervisor and a Linux VM. Likewise, support techs who need occasional access to every OS version they support can have a single system with a VM for each.

Complex desktop PCs can also be replaced with simple but durable thin clients that offload most of their work on servers. Each thin client still needs a keyboard, mouse, and monitor---but they may not need hard drives or fans. They can usually get away with simpler motherboards and less-powerful CPUs, GPUs (which can be built into the CPUs), and RAM.

Simplifying System Management and Security

The most popular reason for virtualizing is probably the benefits we reap from easy-to-manage systems. We can take advantage of the fact that VMs are simply files: like any other files, they are easy to copy around. It's easy to set up new employees with a department-specific virtual machine that has all of the software they need already installed.

These management advantages turn out to be a nice security advantage, too. Let's say you have set up a new employee with a traditional physical system. If that system goes down---due to hacking, malware, or so on---you need to restore the system from a backup (which may or may not be easily at hand) or break out the OS installation media. With hardware virtualization, the host machine, hypervisor, and any other VMs it runs are generally unaffected and uninfected; you merely need to shut down the virtual machine and reload an alternate (clean) copy of it. And because VMs are just files, these are easy to keep around.

TIP   VMs on a network face the same risks---and pose the same risks to other networked devices---as any other networked computer. Networked VMs have security requirements similar to a physical system and should usually get whatever security treatment you'd give physical systems. VMs need regular OS and software updates, firewalls, anti-malware software, accounts with strong passwords, backups, and good general security hygiene.

Most virtual machines also let us make a snapshot or checkpoint, which saves the virtual machine's state at that moment, allowing us to quickly return to this state later. Snapshots are great for doing risky (or even not-so-risky) maintenance with a safety net. They also give you the freedom to install updates without worrying they'll render the OS unusable, making it easier to keep systems secure. These aren't, however, a long-term backup strategy---each snapshot may reduce performance and should be removed as soon as the danger has passed. Figure 22-6 shows VMware ESXi saving a snapshot.

Figure 22-6  Saving a snapshot

TIP   Virtualized operating systems use the same security features as real operating systems. For each virtual machine user account, you'll need to keep track of user names, passwords, permissions, and so on, just like on a normal PC.

Purpose of Virtual Machines

As I said earlier: like physical computers, virtual machines are just another tool for computing things. This means you can find people using virtual machines to do almost anything they can do with physical computers. It also means you'll find people using physical computers for things virtual machines do well.

Above all else, it means that---just like with physical computers---people are constantly finding new ways to use virtual machines. Let's review the list of purposes you should know for the CompTIA A+ 1101 exam---but keep in mind that the best problem you ever solve with a VM may not be on this list!

Sandboxing

We'll take a closer look at security topics in Chapter 27, so for now I just want to touch lightly on a fundamental idea. If you need to run software that you don't trust, the safest way to do it is to run it on a separate computer where it can't interact with real data and programs.

Isolating untrusted software this well is rarely practical, so the next-best thing is to run the software inside a tightly restricted execution environment---a sandbox---which limits how the software can interact with the host system and any files and other programs on it. CompTIA wants you to know that virtual machines can serve as a sandbox---but I need to split a few hairs.

First, there are many kinds of sandbox. One of the most common types is for keeping applications from interfering with each other in day-to-day use. These generally come with the operating system and are especially important on smartphones. Another type enables you to occasionally run untrusted software in an environment that is isolated from the core system---a good example is Windows Sandbox, included in Windows 10 Pro and newer. There are also sandboxes designed from the ground up for analyzing the behavior and safety of software you run inside them.

Second, a general virtual machine is not a true sandbox. It is not designed to isolate software! As a tool, virtual machines just happen to be useful for this task; they are better than running sketchy software on the host, but not perfectly safe.

NOTE   If you need to isolate the software for boring reasons---imagine you need to run multiple versions of a program but can't install more than one on a system---a VM is just fine (though it will consume a lot of resources).

Development Testing

When it comes to programming, there's always a chance that differences between systems will cause the software that developers are working on to run differently---or not at all! For this reason, developers often test the software they are writing in a development environment that matches the intended environment (i.e., where the software should run) as closely as possible. Virtual machines are a popular choice for these environments.

EXAM TIP   The CompTIA A+ 1101 objectives call this purpose test development. I think CompTIA means "test" as a verb---to test development work. But there's a chance CompTIA means "development" as the verb---to develop tests. Know that VMs are a popular way to test development work and look for "VM" in the answers if you see a question about creating or developing tests.

It isn't enough to just use any VM, though. Surprisingly small differences between systems can cause trouble. Not only are two systems set up by hand likely to differ, but differences accumulate on every system as users install different software in them, run updates at different times, create different files, and so on. Developers may regularly run special software to prepare a fresh VM---to provision it with the exact operating system, files, and software specified in configuration files shared among everyone working on the project.

Application Virtualization

The final purpose of VMs that CompTIA focuses on is application virtualization. Application virtualization entails virtualizing the OS capabilities that an application would normally use to install and do its work. The flexibility this creates enables some neat tricks, such as being able to run an application without installing it, run applications that only work in a different version of your OS, run applications that would normally interfere with each other, and even run applications that were written for another OS entirely.

EXAM TIP   The CompTIA A+ 1101 objectives call out two of these tricks: running applications for a different OS version (identified as legacy software/OS), and running applications written for another OS (identified as cross-platform virtualization). Look for "application virtualization" or "virtual machines" as an answer to questions about running applications for a different or older OS.

I need to be clear about two things here. First, there are different approaches to application virtualization out there and they don't all use virtual machines. Second, you can manually use virtual machines to accomplish these same tricks, but application virtualization means more than just running an application in a VM. The point is to have your cake and eat it, too.

Here's an example of application virtualization. Having to run a full Windows 7 VM to access a legacy app on macOS is clunky. Users must jump through hoops to move files around between the host system and the VM, and they'll almost certainly catch themselves trying to use macOS keyboard shortcuts inside the Windows VM or Windows keyboard shortcuts outside of it.

In contrast, some forms of application virtualization are so seamless that users will launch it just like any other native desktop app and not even know they are interacting with old software written for Windows 7.

Creating a Virtual Machine

Before we go any further, let's take the basic pieces you've learned about hardware virtualization and put them together in one of its simplest forms: a virtual machine on your local system.

The basic process for creating virtual machines is as follows:

1\.   Set up your system's hardware to support virtual machines and verify it can meet the resource requirements for running them.

2\.   Install a hypervisor on your system.

3\.   Create a new virtual machine that has the proper virtualized hardware requirements for the guest OS.

4\.   Start the new virtual machine and install the new guest OS exactly as you'd install it on a new physical machine.

Hardware Support and Resource Requirements

While any computer running Linux, Windows, or macOS will support a hypervisor, there are a few hardware requirements we need to address.

Every Intel-based CPU since the late 1980s is designed to support a supervisor for multitasking, but it's hard work for that same CPU to support multiple supervisors on multiple VMs. Both AMD and Intel added extra features to their CPUs just to support hypervisors: Intel's VT-x and AMD's AMD-V. This is hardware virtualization support, and VMs will run better with it enabled.

If your CPU and BIOS support hardware virtualization, you can turn it on or off inside the system setup utility (it may or may not be enabled by default). Figure 22-7 shows the virtualization setting in a typical system setup utility. Note that AMD's AMD-V virtualization is often referred to as SVM mode, as shown in Figure 22-7.

Figure 22-7  BIOS setting for CPU hardware virtualization support on an AMD-based system

RAM  The most important concern is RAM. Each virtual machine needs just as much RAM as a physical one, so it's common practice to stuff your host machine with large amounts of RAM. The more virtual machines you run, the more RAM you need. Generally, you need to leave enough RAM (4 GB recommended) for the hypervisor and every VM you intend to run simultaneously.

NOTE   As we discussed way back in Chapter 4, different motherboards can support different quantities of RAM. If you plan to build a PC to run virtual machines, it pays to do your research. You don't want to get stuck with a board that maxes out at 16 GB of RAM.

VM Storage  VM files can be huge because they include everything installed on the VM. Depending on the OS and how the VM is used, the VM file could range from megabytes to hundreds of gigabytes. On top of that, every snapshot or checkpoint you make requires space. Figure 22-8 shows a newly minted Windows 10 VM taking about 10 GB of storage space.

Figure 22-8  Single VM file taking about 10 GB

The particulars of VM storage depend on your circumstances, but here are a few basic recommendations:

-   Make sure you have plenty of storage space for all of the VMs you plan to have, and room to grow.

-   Your VM files are precious. Plan ahead to protect them with good RAID arrays and regular backups to make sure they are available when you need them.

-   If performance is critical for your VMs, plan to store them on an SSD.

Virtual Networks

Probably one of the coolest features of VMs is that you can "virtually" network them in many different ways. Don't just limit yourself to thinking, "Oh, can I get a VM to connect to the Internet?" Well, sure you can, but hypervisors do so much more. Every hypervisor has the capability to connect each of its virtual machines to a network in a number of different ways. All of these options depend on virtual switches, but the way this looks will vary a lot from hypervisor to hypervisor.

Some common ways to network VMs include the following:

-   Create an internal network (see Figure 22-9) for multiple VMs within the same hypervisor, enabling them to communicate with each other (and optionally the outside world).

Figure 22-9  Configuring a VM for an internal network in VirtualBox

-   Place a VM on a virtual network that only enables it to communicate with the host system.

-   "Bridge" a VM's NIC to the host's NIC, enabling the VM to join the same network that the host computer is connected to.

-   Provide a VM with no network, isolating it from other VMs, the host, and the broader network.

Installing a Virtual Machine

The actual process of installing a hypervisor is usually no more complicated than installing any other type of software. Let's use Hyper-V as an example. If you have a Windows 10 or 11 Professional system, you can enable Microsoft's Hyper-V by going to the Programs and Features Control Panel applet and selecting Turn Windows features on or off, which opens the Windows Features dialog box, as shown in Figure 22-10.

Figure 22-10  Installing Hyper-V in Windows

NOTE   If you are using Windows 10/11 Home, Hyper-V is not available from this menu. Use a third-party virtualization tool.

Once you've installed the hypervisor of choice, you'll have a virtual machine manager (VMM) that acts as the primary place to create, start, stop, save, and delete guest virtual machines. Figure 22-11 shows the manager for VirtualBox.

Figure 22-11  Oracle VM VirtualBox Manager (three VMs installed)

How to Build a Virtual Machine

Now that you've got a hypervisor, you can set up a virtual machine. On pretty much any virtual machine manager, this is simply a matter of selecting New | Virtual Machine, which starts a wizard to ensure you're creating the right virtual machine for your guest OS. Most hypervisors have presets for crucial settings (such as virtual RAM, storage space, and so on) to ensure your guest OS has the virtual hardware it needs to run. Figure 22-12 shows the VirtualBox wizard asking what OS you intend to install in the Machine Folder field. You also need to give the virtual machine a name. For this overview I'm going with Fedora Workstation.

Figure 22-12  Creating a new VM in Oracle VirtualBox

NOTE   Use descriptive names for virtual machines. This will spare you a lot of confusion when you have multiple VMs on a single host.

Click Next, and you get to pick how much memory you want for your VM (see Figure 22-13). VirtualBox recommends at least 1 GB for Fedora, but I'm going with 2 GB.

Figure 22-13  Selecting the amount of memory for the VM

After clicking Next, you get to create the virtual hard drive. Clicking Create opens the Create Virtual Hard Disk wizard, which asks several technical questions about hard disk file type and how it should allocate the space. I'm just going with the defaults, but it can be useful to change them in certain situations. Finally, on the last screen, you get to set how big the virtual disk will be, the default being 8 GB. That's a bit small for me, so I've gone with 25 GB, as shown in Figure 22-14. With that, you've created a new virtual machine.

Figure 22-14  Setting the virtual drive size

Installing the Operating System

Once you've created the new guest VM, it's time to install a guest operating system. Would you like to use Microsoft Windows in your virtual machine? No problem, but every Windows virtual machine requires a separate, legal copy of Windows; this also goes for any licensed software installed in the VM.

All good virtual machine managers enable you to load installation media from removable media on the host, but the easy way is to tell the new virtual machine to treat an ISO file as its own optical drive. In Figure 22-15, I'm installing Fedora Workstation on a VirtualBox virtual machine. I downloaded an ISO image from the Fedora Web site (https://getfedora.org) and selected it as the installation media. From here I click Start and install Fedora like any other installation.

Figure 22-15  Selecting the installation media

After you've gone through all the configuration and OS installation screens, you can start using your virtual machine. Figure 22-16 shows VirtualBox running the newly installed Fedora Workstation.

Figure 22-16  Fedora Workstation running in VirtualBox

Like with a real system, you can add or remove hardware---but adding hardware won't take a trip to the electronics store or a box from Newegg. With a good hypervisor, you can easily add and remove virtual hard drives, virtual network cards, virtual RAM, and so on, helping you adapt your VM to meet changing needs. Figure 22-17 shows the Settings System screen from VirtualBox.

Figure 22-17  Configuring virtual hardware in VirtualBox

SIM   Check out the excellent Chapter 22 Show! and Click! sims on "Virtual Hardware" over at https://www.totalsem.com/110X. These help reinforce terminology and typical steps for setting up a virtual machine.

Server-side Virtualization

When it comes to servers, hardware virtualization has pretty much taken over everywhere. Many of the servers we access, such as those that power Web sites and video streaming services, are virtualized. These severs usually aren't running in a desktop hypervisor such as VirtualBox because that type of hypervisor requires the host to have a full operating system.

This full host OS not only ties up at least enough resources to run a full VM---it also adds a little overhead to every operation. For this reason (and others), most server VMs run on a powerful hypervisor/OS combination called a bare-metal hypervisor. We call it bare metal because there's no other software between it and the hardware---just bare metal. The industry also refers to this class of hypervisors as Type-1, and applications such as VirtualBox as Type-2 (see Figure 22-18).

Figure 22-18  Type-1 versus Type-2 hypervisors

I hope by this point that you have a sense of what hardware virtualization is---but don't worry if you're still a bit confused about why it's a big deal. One hurdle to understanding how and why virtualization is continually revolutionizing IT is that the flexibility it creates is often most helpful at very large scales (like data centers with tens of thousands of servers) that aren't familiar to most people. In the next section, we'll see how this flexibility plays out on a massive scale.

To the Cloud

Before we look at what "the cloud" is, I want to take a step back and talk about something that will sound unrelated: money. One of the really great things money does is give us common, easily divisible units we can exchange for the goods and services we need. When we don't have money, we have to trade goods and services to get it, and before money was invented, humans had to trade goods and services for other goods and services.

Let's say I'm starving and all I have is a hammer, and you just so happen to have a chicken. I offer to build you something with my hammer, but all you really want is a hammer of your own. This might sound like a match made in heaven, but what if my hammer is actually worth at least five chickens, and you just have one? I can't give you a fifth of a hammer, and once I trade the hammer for your chicken, I can't use it to build anything else. I have to choose between going without food and wasting most of my hammer's value. If only my hammer was money!

In the same vein, a top-of-the-line physical server can be a bit like a really expensive hammer. It has the resources to do a lot of work, but it is often underused because you would have to find tasks in which to take advantage of its various resources. Installing a hypervisor on this server sets us on the path to using it in a new, more productive way.

In this new model, servers become (a little) less like hammers and (a little) more like money. I still can't trade a fifth of my hammer for a chicken, but a powerful physical server has the flexibility to host one huge VM, two large VMs, or one large VM and a dozen tiny ones---and this configuration can change constantly!

As the number of VM hosts and guest VMs increases, so do the options for distributing VMs across hosts to minimize unused resources (see Figure 22-19). At larger scales, the hosts become more and more like a pool of common, easily divisible units we can use to solve problems---more and more like money.

Figure 22-19  No vacancy on these hosts

Many organizations use this flexibility to make their own data centers more efficient, but its most impressive use is in the services offered by massive cloud computing providers. These companies cobble together massive pools of computing resources from data centers all around the world.

When we talk about the cloud, we're talking not just about friendly file-storage services like Dropbox or Google Drive, but about all of the services that enable us to dip into the vast pools of computing resources sold by Amazon (see Figure 22-20), Microsoft, and many other companies over the open Internet. The technology at the heart of these innovative services is virtualization (and they apply it to far more than just virtual servers).

Figure 22-20  Amazon Web Services Management Console

The Service-Layer Cake

Service is the key to understanding the cloud. At the hardware level, we'd have trouble telling the difference between the cloud and the servers and networks that comprise the Internet as a whole. We use the servers and networks of the cloud through layers of software that add great value to the underlying hardware by making it simple to perform complex tasks or manage powerful hardware. As end users we generally interact with just the sweet software icing of the service-layer cake---Web applications like Dropbox, Gmail, and Facebook, which have been built atop it. The rest of the cake exists largely to support Web applications like these and their developers. Let's slice it open (see Figure 22-21) and start at the bottom.

Figure 22-21  A tasty three-layer cake

Infrastructure as a Service

Large-scale global Infrastructure as a Service (IaaS) providers use hardware virtualization to minimize idle hardware, protect against data loss and downtime, and respond to spikes in demand. We can use big IaaS providers like Amazon Web Services (AWS) to launch new virtual servers using an operating system of choice on demand (see Figure 22-22) for pennies an hour. The beauty of IaaS is that you no longer need to purchase expensive, heavy hardware. You are using Amazon's powerful infrastructure as a service.

Figure 22-22  Creating an instance on AWS

A huge number of Web sites are really more easily understood if you use the term Web applications. If you want to access Mike Meyers' videos, you go to https://hub.totalsem.com. This Web site is really an application that you use to watch videos, practice simulation questions, and so forth. This Web application is a great tool, but as more people access the application, we often need to add more capacity so you won't yell at us for a slow server. Luckily, our application is designed to run distributed across multiple servers. If we need more servers, we just add as many more virtual servers as we need. But even this is just scratching the surface. AWS provides many of the services needed to drive popular, complex Web applications---unlimited data storage (see Figure 22-23), database servers, caching, media hosting, and more---all billed by usage.

Figure 22-23  Amazon Simple Storage Service (S3)

The hitch is that, while we're no longer responsible for the hardware, we are still responsible for configuring and maintaining the operating system and software of any virtual machines we create. This can mean we have a lot of flexibility to tune it for our needs, but it also requires knowledge of the underlying OS and time to manage it. If you want someone to handle the infrastructure, the operating system, and everything else (except your application), you need to move up to Platform as a Service (PaaS).

Platform as a Service

Web applications are built by programmers. Programmers do one thing really well: they program. The problem for programmers is that a Web application needs a lot more than just a programmer. Developing a Web application requires people to manage the infrastructure: system administrators, database administrators, general network support, and so on. A Web application also needs more than just hardware and an operating system. It needs development tools, monitoring tools, database tools, and potentially hundreds of other tools and services. Getting a Web application up and running is a big job.

A Platform as a Service (PaaS) provider gives programmers all the tools they need to deploy, administer, and maintain a Web application. The PaaS provider starts with some form of infrastructure, which could be provided by an IaaS, and on top of that infrastructure the provider builds a platform: a complete deployment and management system to handle every aspect of a Web application.

The important point of PaaS is that the infrastructure underneath the PaaS is largely invisible to the developer. The PaaS provider is aware of their infrastructure, but the developer cannot control it directly, and doesn't need to think about its complexity. As far as the programmer is concerned, the PaaS is just a place to deploy and run his or her application.

Heroku, one of the earliest PaaS providers, creates a simple interface on top of the IaaS offerings of AWS, further reducing the complexity of developing and scaling Web applications. Heroku's management console (see Figure 22-24) enables developers to increase or decrease the capacity of an application with a single slider, or easily set up add-ons that add a database, monitor logs, track performance, and more. It could take days for a tech or developer unfamiliar with the software and services to install, configure, and integrate a set of these services with a running application; PaaS providers help cut this down to minutes or hours.

Figure 22-24  Heroku's management console

Software as a Service

Software as a Service (SaaS) sits at the top layer of the cake. SaaS shows up in a number of ways, but the best examples are the Web applications we just discussed. Some Web applications, such as Total Seminars Training Hub, charge for access. Other Web applications, like Google Maps, are offered for free. Users of these Web applications don't own this software; you don't get an installation DVD, nor is it something you can download once and keep using. If you want to use a Web application, you must get on the Internet and access the site. While this may seem like a disadvantage at first, the SaaS model provides access to necessary applications wherever you have an Internet connection, often without having to carry data with you or regularly update software. At the enterprise level, the subscription model of many SaaS providers makes it easier to budget and keep hundreds or thousands of computers up to date (see Figure 22-25).

Figure 22-25  SaaS versus updating every desktop

The challenge to defining SaaS perfectly is an argument that almost anything you access on the Internet could be called SaaS. A decade ago we would've called the Google search engine a Web site, but it provides a service (search) that you do not own and that you must access on the Internet. If you're on the Internet, you're arguably always using SaaS.

It isn't all icing, though. In exchange for the flexibility of using public, third-party SaaS, you often have to trade strict control of your data. Security might not be crucial when someone uses Google Drive to draft a blog post, but many companies are concerned about sensitive intellectual property or business secrets traveling through untrusted networks and being stored on servers they don't control.

EXAM TIP   Know the differences between basic cloud concepts such as SaaS, IaaS, and PaaS.

Ownership and Access

Security concerns like those just discussed don't mean organizations have to forfeit all of the advantages of cloud computing, but they do make their management think hard about the trade-offs between cost, control, customization, and privacy. Some organizations also have unique capacity, performance, or other needs no existing cloud provider can meet. Each organization makes its own decisions about these trade-offs, but the result is usually a cloud network that can be described as public, private, community, or hybrid.

Public Cloud

Most folks usually just interact with a public cloud, a term used to describe software, platforms, and infrastructure delivered through networks that the general public can use. When we talk about the cloud, this is what we mean. Out on the open, public Internet, cloud services and applications can collaborate in ways that make it easier to think of them collectively as the cloud than as many public clouds. The public doesn't own this cloud---the hardware is often owned by companies like Amazon, Google, and Microsoft---but there's nothing to stop a company like Netflix from building its Web application atop the IaaS offerings of all three of these companies at once.

Private Cloud

If a business wants some of the flexibility of the cloud, needs complete ownership of its data, and can afford both, it can build an internal cloud the business actually owns---a private cloud. A security-minded company with enough resources could build an internal IaaS network in an onsite data center. Departments within the company could create and destroy virtual machines as needed and develop SaaS to meet collaboration, planning, or task and time management needs all without sending the data over the open Internet. A company with these needs but without the space or knowledge to build and maintain a private cloud can also contract a third party to maintain or host it.

Community Cloud

While a community center is usually a public gathering place for those in the community it serves, a community cloud is more like a private cloud paid for and used by more than one organization. Community clouds aren't run by a city or state for citizens' use; the community in this case is a group of organizations with similar goals or needs. If you're a military contractor working on classified projects, wouldn't it be nice to share the burden of defending your cloud against sophisticated attackers sponsored by foreign states with other military and intelligence contractors?

Hybrid Cloud

Sometimes we can have our cake and eat it too. Not all data is crucial, and not every document is a secret. Needs that an organization can only meet in-house might be less important than keeping an application running when demand exceeds what it can handle onsite. We can build a hybrid cloud by connecting some combination of public, private, and community clouds, allowing communication between them. Using a hybrid cloud model can mean not having to maintain a private cloud powerful enough to meet peak demand---an application can grow into a public cloud instead of grind to a halt, a technique called cloud bursting.

But a hybrid cloud isn't just about letting one Web application span two types of cloud---it's also about integrating services across them. Let's take a look at how Jimmy could use a hybrid cloud to expand his business.

EXAM TIP   Know the differences between public, private, community, and hybrid cloud models.

Jimmy runs a national chain of sandwich shops and is looking into drone-delivered lunch. He'll need a new application in his private cloud to calculate routes and track drones, and that application will have to integrate with the existing order-tracking application in his private cloud. But then he'll also need to integrate it with a third-party weather application in the public cloud to avoid sending drones out in a blizzard, and a flight-plan application running in a community cloud to avoid other drones, helicopters, and aircraft (and vice versa). The sum of these integrated services and applications is the hybrid cloud that will power Jimmy's drone-delivered lunch.

Cloud Characteristics

When it comes to whether and how to make use of cloud computing, every organization has to weigh the positives and negatives of the cloud against a more traditional approach. Different organizations will care about different things, but let's take a moment to discuss five cloud characteristics that CompTIA wants you to know for the exam.

Shared Resources

Cloud computing focuses less on individual physical systems and more on the underlying resources. Instead of renting out each physical unit separately, cloud providers aggregate them into a pool of shared resources that they make available on-demand. The provider's customers draw from this pool as they need additional resources and release them back into the pool when they are done.

This flexibility is one of the cloud's big strengths. For example, this makes it practical to spin up tons of resources to render special-effects animations for an upcoming movie and release the resources once the job's done. Unfortunately, this also means jobs for other users are likely running on the same hardware---and that's not always acceptable.

Most cloud neighbors are fine, but you never know! There's always a chance that a cloud neighbor could be intentionally exploiting a weakness in the host system to spy on their neighbors, could get hacked or infected with malware, or could overuse shared resources in a way that hinders performance for everyone else.

Rapid Elasticity

Let's say you start a new Web application. If you use an IaaS provider such as Amazon, you can start with a single server and get your new Web application out there. But what happens if your application gets really, really popular? No problem! Using AWS features, you can easily expand the number of servers, even spread them out geographically, with just a click of the switch. This capability is known as rapid elasticity.

Metered Utilization

Ah, the biggest downside to using someone else's cloud: you have to write a check to whoever is doing the work for you---and boy can these cloud providers get creative about how to charge you! In many cases they charge a precise metered utilization rate based on factors such as the traffic that goes in and out of your Web application and how much data you store. In other cases you pay for the exact amount of time that every single one of your virtualized servers is running.

Regardless of how costs are measured, this differs from more traditional hosting with a fixed monthly or yearly fee. You pay for what resources you use, rather than a more general fee for all the hardware of a system.

High Availability

For every small organization with a single physical server doing some critical job 24 hours a day, there's a tech who doesn't sleep well at night. All kinds of problems can knock a single system out of commission for hours or days, and many organizations can't justify the cost of hiring someone to keep an eye on the server closet all night just in case.

Large cloud providers, however, have an army of automated systems and technicians perpetually watching over their global network of data centers. This already reduces the odds of an extended outage, enabling many cloud providers to promise that most of their services will be available 99.9 percent of the time or more.

Cloud computing enables organizations to get as close to 100 percent uptime as they can afford. Sometimes this is as simple as paying the cloud provider extra for a service to guarantee greater uptime. Organizations can also design their cloud deployments for high availability---for example, they can set up redundant servers all around the world and automatically reroute traffic whenever a server is down.

NOTE   High availability isn't limited to the cloud---it is a huge topic in its own right! If you continue on to take the CompTIA Network+ exam, you'll learn more about how important high availability is in networking and data centers.

File Synchronization

Cloud file storage services, like Dropbox and Box, were early smash successes in getting people to move to the cloud for some of their storage needs. Most of these services provide file synchronization apps that propagate file changes to the storage provider on to any other connected devices. Synchronization apps make it easy to access the same set of files across multiple devices.

These days, file synchronization is often bundled with productivity suites (i.e., collections of apps that enable you to edit documents, spreadsheets, presentations, and so on) such as Microsoft 365 and Google Workspaces. Regardless of how your organization approaches it, file synchronization makes it easier for users to collaborate or work on the same files from multiple devices without having to shuffle files around.

Unfortunately, cloud-based file synchronization also means giving up a lot of control over the organization's files to the provider. It also makes it easier for disgruntled users to pass documents on to people who shouldn't have access to them.

Desktop Virtualization

Desktop virtualization tries to apply the flexibility associated with both hardware virtualization and cloud computing to user workstations. The most common forms of desktop virtualization entail using a client program on one device to connect to a virtual desktop, providing access to a user's files and applications.

If each human user still needs a system to access their virtual desktop, why would an organization be eager to also set aside server resources for them? Some of the big reasons are control, security, and management. Every user walking around with a laptop stuffed to the gills with sensitive organization data and applications is a huge risk! Desktop virtualization enables users to access the apps and files they need without storing them on local devices that could get lost or stolen at any time.

Some folks do desktop virtualization with just a remote desktop client and a user account on a multiuser OS such as Windows Server. The CompTIA A+ 1101 objectives focus on a form called virtual desktop infrastructure (VDI), in which each user's client program connects to an automatically managed virtual machine running on a central server. In many organizations these VDI servers will be on premises, but it's also possible to set up VDI servers in the cloud.

NOTE   CompTIA didn't include cloud-based Desktop as a Service (DaaS) in the 1101 objectives, but any organization considering cloud-based VDI will likely consider using DaaS as well. They both accomplish roughly the same goal, but differ when it comes to cost, licensing, control, flexibility, and management.

Chapter Review

Questions

1\.   Upgrading which component of a host machine would most likely enable you to run more virtual machines simultaneously?

A.   CPU

B.   Hard drive

C.   RAM

D.   Windows

2\.   Which of the following could an organization use to enable its users to access their files and applications from multiple devices?

A.   Virtual desktop

B.   Client-side virtual machine

C.   File-synchronization service

D.   Virtual memory

3\.   What feature lets you save a VM's state so you can quickly restore to that point? (Choose two.)

A.   Checkpoint

B.   Save

C.   Snapshot

D.   Zip

4\.   What do you need to install a legal copy of Windows 10 into a virtual machine using VirtualBox?

A.   A valid Windows 10 license

B.   Valid Windows 10 installation media

C.   A valid ESXi key

D.   A second NIC

5\.   Which of the following is an advantage of a virtual machine over a physical machine?

A.   Increased performance

B.   Hardware consolidation

C.   No backups needed

D.   Operating systems included

6\.   Janelle wants to start a new photo-sharing service for real pictures of Bigfoot, but doesn't own any servers. How can she quickly create a new server to run her service?

A.   Public cloud

B.   Private cloud

C.   Community cloud

D.   Hybrid cloud

7\.   After the unforeseen failure of her Bigfoot-picture-sharing service, bgFootr---which got hacked when she failed to stay on top of her security updates---Janelle has a great new idea for a new service to report Loch Ness Monster sightings. What service would help keep her from having to play system administrator?

A.   Software as a Service

B.   Infrastructure as a Service

C.   Platform as a Service

D.   Network as a Service

8\.   Which kind of hypervisor is installed and run from within a full operating system?

A.   Bare-metal

B.   Virtual-metal

C.   Type-1

D.   Type-2

9\.   When a virtual machine is not running, how is it stored?

A.   Firmware

B.   RAM drive

C.   Optical disc

D.   Files

10\.   BigTracks is a successful Bigfoot-tracking company using an internal service to manage all of its automated Bigfoot monitoring stations. A Bigfoot migration has caused a massive increase in the amount of audio and video sent back from their stations. In order to add short-term capacity, they can create new servers in the public cloud. What model of cloud computing does this describe?

A.   Public cloud

B.   Private cloud

C.   Community cloud

D.   Hybrid cloud

Answers

1\.   C. Adding more RAM will enable you to run more simultaneous VMs. Upgrading a hard drive could help, but it's not the best answer here.

2\.   A. Users can access a virtual desktop, which may include their files and applications, from different devices.

3\.   A, C. The saved state of a VM is called a snapshot or checkpoint. Not to be confused with a true backup.

4\.   A. You need a valid Windows 10 license to run Windows legally.

5\.   B. A big benefit of hardware virtualization is hardware consolidation.

6\.   A. Using the public cloud will enable Janelle to quickly create the servers she needs.

7\.   C. By switching to a PaaS, Janelle can concentrate on creating her service and leave the lower-level administration up to the PaaS provider.

8\.   D. A Type-2 hypervisor runs inside a full operating system.

9\.   D. VMs are just files, usually stored on a hard drive.

10\.   D. BigTracks is creating a hybrid cloud by connecting its internal private cloud to a public cloud to quickly expand capacity.

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

Chapter 22 Virtualization

Chapter 23 Portable Computing

Chapter 24 Mobile Devices

42h 21m remaining
