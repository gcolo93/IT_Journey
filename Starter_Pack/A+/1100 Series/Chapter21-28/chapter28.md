
CHAPTER 28

Operational Procedures

In this chapter, you will learn how to

-   Implement best practices associated with documentation and support systems information management

-   Explain basic change-management best practices

-   Summarize environmental impacts and local environmental controls

-   Explain the importance of prohibited content/activity and privacy, licensing, and policy concepts

The term operational procedures encompasses a lot for any organization, from best practices for safety (Chapter 1) to dealing with security risks (Chapter 27); from organizational polices for limiting access to sensitive data (also Chapter 27) to proper communication techniques and professionalism all techs should employ (again, Chapter 1). The CompTIA A+ 1102 exam even throws in basics of scripting (Chapter 15) and remote access technologies (Chapter 21) as operational procedures (though labeling them as such feels like a reach to me).

This chapter explores another aspect of operational procedures---namely, business practices that enable continuity, a fancy way of saying that an organization should keep working more or less the same in the face of both mundane day-to-day change and sudden disasters. We'll focus here on four categories of business continuity and operational procedures: documentation and support systems management, basic change management, environmental impacts and controls, and prohibited content/activity, privacy, licensing, and policies.

1102

Implementing Best Practices Associated with Documentation and Support Systems Information Management

Organizations need documentation to provide continuity and structure. Documentation can take many forms, but the four categories of concern to a new tech are asset management, custom installation of software packages, ticketing systems, and knowledge base/articles.

Asset Management

Techs help organizations institute asset management practices to protect organizational assets. These include inventory lists, database systems, and barcodes, among other things.

EXAM TIP   Although the term "barcode" is not likely to appear on the CompTIA A+ 1102 exam, organizations still use this technology to track assets.

Inventory Lists

Have you ever worked for a company that issued you a piece of equipment that had a company-specific tag on it? This could be anything from a number engraved onto the handle of a shovel to an RFID tag attached to a computer. Regardless of the form, every organization has to track the physical and virtual assets that it has in its inventory at any given time. For a tech company, the inventory might include, for example, 32 Dell laptops, 32 USB-C power adapters, 32 copies of Microsoft Office, and so forth. Regardless of the form, inventory lists are found in every organization and document the assets that the organization has deployed and holds in reserve. Keeping track of these assets is an essential function. Inventory lists document the who, what, and where of each asset so that an organization can track all its assets.

Database System

For now, let's keep this really simple. In the context of asset management, database systems are used to track things like who has the asset (e.g., Melissa Layne), what type of asset this person has (e.g., a laptop), and where this asset is located (e.g., the research and innovation department). Sometimes database systems document why the person is using the asset (e.g., to analyze quantitative and qualitative data for her department). Asset management database systems can also be used for things like

-   Recording an asset's description: make, model, serial numbers, asset barcode, asset category, etc.

-   Recording an asset's acquisition and disposal information

-   Linking purchase receipts, manuals, and other digital documents to asset records

-   Tracking an asset's status and location

-   Obtaining a report listing assets assigned to a department or employee

-   Recording asset maintenance and repair histories (date, details, costs, etc.)

Some of the listed items will be discussed further in the "New User Set-Up Checklist" and "End-User Termination Checklist" sections later in the chapter. As you progress through more advanced topics and courses, there will be much more to learn about database systems.

NOTE   The difference between an inventory list and a database system is that an inventory list keeps track of the assets that the organization has given out to people and that it has as "extras." A database system tracks more detailed information about the assets.

Barcodes

Many inventory items have simple stickers or printed labels with barcodes---unique symbols/numbers that track specific items. Figure 28-1 shows a typical barcode. A barcode acts as a fingerprint for an item, binary code that can be readily scanned. One drawback to barcodes is that they're read-only. You can't add data or information to them at all.

Figure 28-1  Barcode on an SSD encoding its serial number

Asset Tags and IDs

Asset tags can use the radio frequency identification (RFID) wireless networking protocol to also keep track of inventory (see Figure 28-2). The asset tag includes an RFID tag (consisting of a microchip and antenna), which an RFID scanner or reader can electronically read and identify even without line of sight to the item. Most RFID tags are passive, meaning that the tag receives all the power it needs from the scanner's signal! An active RFID tag, on the other hand, uses a battery or external power source to send out and receive signals. Both types of RFID tags enable asset management. Unlike barcodes, the information stored in an RFID tag can be updated with new details.

Figure 28-2  RFID tag

Procurement Life Cycle

This is one of those topics that is a pain to talk about because every organization has its own process. For small companies, the procurement life cycle can be as simple as picking up the phone, making a few calls, and getting what they need. For highly bureaucratic organizations, the procurement life cycle can be a years-long process involving thousands of pages of rules. At its core, the procurement life cycle is the process involved in buying assets that your project needs. However, we are going to try to keep this simple and break down the procurement life cycle into six simple phases.

Identify Needs  Develop an understanding of what you need and why you need it. This can involve simple statements of work or complex documents detailing very specific objectives. This phase will vary from organization to organization and across use cases.

Evaluate Suppliers  Once you know what you need and why you need it, you need to scope out who provides the product or service you require. Sometimes this can be completed with a simple Web search. Other times it may require you to conduct a lengthy series of interviews. Typically, the cost of an implementation is directly proportional to the amount of time you spend evaluating the best supplier.

Negotiate Terms and Finalize the Purchase Order  When you have decided on the best supplier, you need to contact that supplier and enter into a negotiation of terms. Think of this as buying a car, but at a much larger scale. Everyone is willing to make concessions. In the world of business, it is how many concessions you can get, while maintaining quality, that matters in the end.

So, now you have bargained your way down to the very best terms that you can extract from the supplier. This is known as their best and final offer. You agree that this works for your organization, which then sends to the supplier a purchase order (PO) with relevant payment information. The supplier in turn sends an invoice to your organization to initiate the billing process.

Receive Invoice and Process Payment  Your organization receives an invoice, aligned with the purchase order, and sends the supplier the funds to facilitate payment. Are you finished? Not just yet.

Delivery and Audit  After the supplier has been paid, they deliver the service or product as promised. Upon implementation, you begin to monitor how effective the new service or product is compared to your previous state. This is called the audit.

Maintain Records for Future Audits  Everything is up and running. You are happy. The supplier is happy. Now you must continue to track effectiveness versus the return on investment (ROI), to assess periodically whether this solution is still effective or, if you need a new approach.

Warranty and Licensing

In the role of an asset manager, you will also need to keep track of warranty and licensing documentation. Although this may seem like an overwhelming task, as long as you have established solid security measures and adhere to licensing compliance requirements, you will be able to easily manage and update this important documentation. This in no way means that this job is easy. It's not. In terms of licensing compliance, the stakes are high. If, for example, a company has 50 unlicensed copies of a software application running on 400 of its computers, the company could face fines as high as $500,000!

Unlicensed assets are also linked to potential data loss. Data loss leads to privacy violations, and the snowball continues to get bigger and bigger. There are, however, software applications that can make the tracking job easier, such as various Software as a Service (SaaS) products that make maintaining compliance a little easier.

Assigned Users

Your organization may receive a set number of licenses for a particular product, such as software. This represents how many people in your organization can use the product. Sometimes suppliers are flexible, and they will say, "As long as you don't have more than ten people accessing our product, then everything is fine." Other times, suppliers want to know specifically who is using their product, and if this changes they will want to know who the replacement is. In this case the users are known as assigned users.

Individual organizations may also have their own rules about assigning user roles to individuals, even if the supplier does not require the organization to provide identities for individual users. When this is the case, it is often related to audits that determine if the right people are receiving access to the right products or services to ensure optimal performance of the organization as a whole.

Documentation for Policies, Procedures, Industry Standards, and Compliance

Organizations of every size should have a library of documents that cover the organization's policies and procedures and any industry standards and compliance regulations that apply to the organization. New employees should be given a package of these documents the first week on the job and instructed to review them. The onus, however, is on the employer to have these documents ready for new employees and to instill the need to apply the core principles contained within them to the organizational culture. Doing so will prevent issues, avoid inefficiencies, and create a sense of ownership.

Standard Operating Procedures

From a technician's point of view, the most common operating issue revolves around software, such as what sort of software users are allowed to install on their computers or, conversely, why you have to tell a user that he can't install the latest application that may help him do his job more effectively because that software isn't on the approved list. This can lead to some uncomfortable confrontations, but it's part of a tech's job.

EXAM TIP   The CompTIA A+ 1102 exam objectives call out procedures for custom installations of software packages. If your organization has rules about what software you can and can't install, it probably also has processes that lay out what to do when users request job-related software that isn't on the approved list. For example, folks who work out at NASA's Johnson Space Center here in Houston have to open a support ticket with the IT department if they need a program that isn't on the approved list. From there, the process governs how to decide if the software's license is acceptable, whether it will cause security or compatibility problems, and so on.

The concepts behind standard operating procedures (SOPs) are not meant to make a tech's life difficult and mundane. They are meant, for example, to stop users with insufficient technical skill or knowledge from installing malicious programs or applications that will destabilize their systems, thus keeping technical support calls down, which in turn enables techs to focus on more serious problems.

Organizations largely develop standard operating procedures for employees for two reasons: to enhance the success of the organization, and to meet government-related compliance requirements. Organizational policies include regulatory compliance policies, acceptable use polices, and password policies, among others. Because security is growing to include SOPs associated with regulatory compliance, risk management, end-user training, and so forth, those who have service desk responsibilities will likely have to eventually incorporate these SOPs to keep the organization secure.

Acceptable Use (AUP)

An acceptable use policy (AUP) describes what employees can and cannot do with the organization's property. An example of a common AUP provision is that a company laptop can be used only for company business. Another common AUP provision bars employees from accessing illegal Web sites from the organization's computers. AUPs are often very detailed and specific documents that employees must read, agree to, and sign as a step in the employment process.

Network Topology Diagrams

Network documentation provides a road map for current and future techs who need to make changes or repairs over time. For the most part, CompTIA Network+ techs and system administrators handle the oversight of the network, but CompTIA A+ techs do a lot of the implementation of fixes. A network topology diagram provides a map for how everything connects in an organization's network. These diagrams include switches, routers, WAPs, servers, and workstations (see Figure 28-3). More complex diagrams identify connection types and speeds, and the technologies in use (listing a WAP as an 802.11ax or Wi-Fi 6, for example). Many organizations rely on the Cisco icon set as a universal visual aid for creating these diagrams (see Figure 28-4).

Figure 28-3  Typical network topology diagram

Figure 28-4  A sampling of Cisco network diagram icons

Regulatory Compliance Requirements

Part of a government's job is to ensure safe work environments and minimize exploitation of workers. To this end, governments develop rules and regulations that specify how organizations are supposed to manage their workplaces, workers, and materials. Properly run organizations enforce regulatory compliance requirements---following the laws and regulations---to maintain a healthy workforce. Compliance means, in a nutshell, that members of an organization must abide by or comply with all of the rules that apply to the organization. Statutes with funny names such as Sarbanes-Oxley impose certain behaviors or prohibitions on what people can and cannot do in the workplace.

It has become commonplace for Web sites and applications to collect useful and informative data about their visitors and users. In this age of information overload, it's equally important that visitors and users understand that their usage data is being collected. To ensure there is understanding and agreement from both parties, many organizations have integrated a splash screen prior to using the application or Web site requiring users to agree to things such as data privacy, terms and conditions, or other compliance measures.

New-User Setup Checklist

To make the first day of work easier for new employees, most employers have developed documentation to make sure that they are not overwhelmed and, more importantly, that they have everything they need to start working.

One of these documents is a new-user setup checklist, which is a best practice associated with the documentation and support systems information management that techs use to ensure that a new user is set up with the proper equipment, network credentials, company policies and procedures, and so forth. New-user setup checklists are flexible, meaning that predefined items can be listed in a set order (1, 2, 3, etc.). Although the items may vary based on the employee's position and role in the company, here are some common items you might need to provide to a new employee:

-   Technology: PC, laptop, mouse/mouse pad, keyboard, phone, webcam, external storage

-   Software: product/project development, analytical, statistical, etc.

-   E-mail/messaging setup (e.g., Microsoft Outlook, Teams, Zoom, Teams, etc.)

-   Password security

-   Documentation for hardware or software for further reference on functionality provided

-   Documentation on data privacy policies for new employee to read and sign

-   Contact information provided if new employees have questions, issues, concerns, etc.

Good onboarding gets users to the point where they have everything they need to perform their job functions, they understand how to use it, and they understand and agree to any related security policies that could have a significant negative impact on them and the organization should they not practice them.

End-User Termination Checklist

For any number of reasons, voluntary or involuntary, an employee may leave an organization. Regardless of the reason, the IT department should complete an end-user termination checklist to ensure that the departing employee returns all equipment issued by the organization, that their network access has been removed, and, where applicable, that knowledge transfer is facilitated, such as requesting documents the user has created that could help their successor. If you are given this responsibility in your organization, you need to follow your organization's checklist carefully to make sure that the former employee cannot engage in malicious behavior.

Ticketing Systems

Ticketing systems help handle requests for technical assistance. Many companies use ticketing software internally to provide employees with technical support. Some companies also offer consumer ticketing services. For example, if a user encounters a problem with software, the system might allow them to submit a ticket to the software vendor to resolve the problem.

A ticketing system for internal use usually involves requests to an IT department. It streamlines the process for submitting problems and getting them resolved. Ticketing software for consumers might be assigned to a support person who is familiar with typical technical issues. According to CompTIA, some of the information needed to resolve an issue using a ticketing system might include:

-   User information (name, location, job position, etc.)

-   Date

-   Device information (type of device, model, serial, etc.)

-   Categories

-   Severity

-   Escalation levels

-   Problem description (clarity here is very important)

-   Progress notes

-   Problem resolution (never forget this, always document your findings)

Clear, concise writing is critical when it comes to the problem description, notes, and resolution. You probably won't be the only tech responding to every ticket, so it's important that your coworkers can understand what the problem is and how it is being addressed. Figure 28-5 shows how this information might be presented on a trouble ticket.

Figure 28-5  A typical interface for a ticketing system

Here is an example of how a ticketing system process might play out. Jamie's company computer is not starting. She contacts the IT department by submitting a helpdesk "ticket" in which she provides necessary information (name, date, device information, description of problem, etc.) that helps the responding tech, Jamal, get an initial idea of what the issue is and how to help resolve the issue.

Next, depending on the type of ticketing system, Jamal the tech contacts user Jamie and asks her to explain in further detail what is wrong with the computer. Jamal starts troubleshooting by asking questions such as "Is the computer plugged in?" and "Is the power source completely plugged into the PC?" He also takes notes, documenting his questions and her responses, and any information about their interaction regarding the issue. Jamie responds to Jamal's questions until they have pinpointed the issue with the computer. Depending on the severity of the issue, the issue either will be resolved and the ticket will be closed or, if the issue cannot be resolved, the ticket will be escalated to another tech who might have more in-depth experience and guidance to help solve Jamie's PC issue.

Knowledge Base/Articles

Organizations use documentation to enable cooperation among employees and coordination among departments. From a tech's perspective, documentation helps in troubleshooting various issues. Creating and maintaining a company knowledge base---a set of documents that tell the tale of equipment used, problems encountered, and solutions to those problems---provides an essential tool for current and future techs. The articles could be, for example, articles from third-party tech sources that apply to the organization's equipment, such as Cisco articles about the routers the organization uses.

Change-Management Best Practices

CompTIA A+ techs are well positioned to offer valuable change management insights. You see what works, what doesn't, and what needs to change. The old laser printers in the accounting department, for example, can't keep up with user needs and you're spending way too much time each week keeping them running. And you're tired of users complaining to you. Change is needed.

Change isn't only grass-roots driven, but often comes from the top. Every organization has formal and informal change-management processes and a designated individual to oversee these processes. You can't just buy a new laser printer, for example, without considering the cost and impact. You can't upgrade the operating systems for 100 users without thorough testing and analysis of the OS. Let's take a closer look at change-management best practices, which include documented business processes and the change-management process.

Documented Business Processes

Every step of a change needs documented business processes. Documented business processes include a plan to return an infrastructure to its pre-change environment, the steps to create an operational environment for development and/or testing, as well as appointing an individual who is responsible for these types of processes. Let's take a look at these three documented business processes, which the CompTIA A+ 1102 objectives identify, respectively, as rollback plan, sandbox testing, and responsible staff member.

Rollback Plan

What if an executed change is a failure? This happens more than you think. Therefore, before a change occurs, a rollback plan must be in place that defines the steps needed to return the infrastructure to its pre-change environment. OS rollbacks, uninstallation, or return to old equipment are all possible parts of a good rollback plan.

For example, Jamie at Bayland Widgets Corp. (BWC) wants to upgrade 16 systems in the design lab from Windows 7 to Windows 11. She obtains approval from management and subsequently implements the upgrade. After a few days, several users have complained that an important CAD application BWC uses is having issues, such as software freezes.

Jamie looks at the rollback plan documentation that lays out the steps for undoing the upgrades. She follows through with the undo process, making notes about the steps, then awaits further instructions for how to get the design lab computers upgraded without failures.

Sandbox Testing

Simply put, a sandbox is a place where you can experiment without messing up the primary system. A sandbox usually is a virtualized environment (refer to Chapter 22) that isolates the test machine from the host machine to avoid causing additional problems. The ability to restore a VM or container from a snapshot makes each of them an ideal choice for sandbox testing, which entails checking out new and updated applications without putting the systems and data you depend on at risk.

Responsible Staff Member

Activities like rollback plans and sandbox testing (and change management, discussed in the next section) are typically led by a responsible staff member (RSM). This individual leads projects like these by following policies, processes, and procedures that have been developed (and likely refined over time) toward facilitating, coordinating, and implementing projects.

For example, Janice, the director of the accounting department, needs 20 of her employees' computers upgraded to Windows 11. Who does she contact to initiate this change? The responsible staff member, of course! This person is appointed by IT department leadership and will assist Janice from the beginning of the upgrade all the way to the end. Depending on the size of your organization, the RSM may be the person who addresses the problem themselves or a manager who coordinates with others to get it fixed.

Change-Management Process

A change-management process enables organizations to implement changes to IT infrastructure in a safe and cost-effective manner. Any organization with a change-management process should have documents that lay out the steps, who performs them, and how they go about it.

One of your first jobs as a tech is to consult these documents so that---when change comes your way (either from you or from on high)---you'll already understand the process. When it's time for a change, start by reviewing this process to avoid being embarrassed about (and possibly disciplined for) missing some important step.

There's no single guide to change management, though most organizations follow common-sense guidelines. This section provides an outline of the change-management best practices CompTIA recommends. A package created by a CompTIA A+ tech should include all the documentation just discussed, plus receipts, overtime records, an inventory of changed systems, lists of new users created, signed end-user acceptance forms, and so on.

Request Forms

A request form kicks off the change-management process. At some point, someone (maybe you or maybe the CIO of the company you work for) identifies a problem that needs to be fixed and submits a basic request form to IT. Depending on your organization, this form may range from a simple one-pager to an extremely complex set of documents. However, regardless of the level of complexity, all request forms have three things in common. They state the problem, what needs to be fixed, and what the desired outcome is.

Beyond these essentials, other information may be needed, such as why this change is important, who it will benefit, how soon it needs to be implemented, and a host of other factors. Again, these requirements all vary depending on the organization you work for and the procedures and requirements it has put in place. The key thing to remember here is that if you submit a change request form, you should be ready to explain why the change is needed. If you can do that, the rest is all a matter of following processes, which you will pick up quickly.

Determine the Purpose of the Change

No organization is ever going to give you new equipment or allow you to make upgrades without knowing why they are needed. To propose a change, you'll almost certainly need to document the purpose of the change. Returning to the scenario from the earlier "Rollback Plan" section in which Jamie at BWC wanted to upgrade 16 systems in the design lab from Windows 7 to Windows 11, users have demanded the latest OS from Microsoft to better serve customers who have (all) jumped to Windows 11. The purpose of the change, therefore, is improved performance and support for clients.

Determine the Scope of the Change

Usually included as part of the purpose of the change, the scope of the change defines who and what this change will affect. This includes an inventory of all systems involved, the number of people involved in making the change, how long the change will take, and often the estimated cost of the change.

In our design lab scenario, Jamie estimates that in order to upgrade 16 computing devices to Windows 11, she will need approximately three people to help with the upgrade, and it should be completed in three days. With this information, in addition to a determination of which edition of Windows 11 will be installed, Jamie now has a pretty good idea of what her overall budget will be.

Document the Date and Time of the Change

Knowing when changes will be deployed is essential. Depending on the application and your organization, anywhere from a few people to literally thousands of people may be impacted. Thus, a clearcut date and time needs to be established for when any system changes will occur. You don't want to be "that guy" who pushes the big red button and sends their company into complete chaos. Imagine that your alarm clock has been set to play heavy metal music at maximum volume and you have no idea what time it will go off. If the music starts to blare before you want to get up, you would very likely wake up extremely grumpy and the day that followed would be far from optimal. This is exactly what your colleagues will be like if you don't adequately document the date and time associated with system changes.

Determine Impact

This phase of change management can be a little tricky, depending on the existing level of documentation related to your systems. Your goal here is to identify which systems the change will impact (both the system the change is made to and its interconnected systems) and to what extent they will be impacted (e.g., unavailable to users for two hours). In a perfect world, every organization should have a complete architectural mapping of all systems and the interrelationships that exist between components. When this is the case, you can reference the documentation and trace where connections exist and deduce where the change will likely impact other systems. This enables you to give everyone a heads-up as to what to expect, when it will happen, and what steps they might need to take. However, you aren't always going to be in a situation where you have access to a complete overview of how systems are connected.

There is an old joke in the IT world that goes like this, "There is only one guy who knows how this all works and he died three years ago." Yea, it's rather gallows humor, but unfortunately it is frequently applicable in a general sense. As organizations grow, they have the tendency to stack systems upon systems, with little or no documentation explaining what happened, when it happened, or why it happened. If this describes your organization, you are in the unenviable spot of basically flying with one eye covered. However, by acquainting yourself with the systems that you will be working with, you will quickly learn how things are connected, and when asked to perform this type of assessment, you can make assumptions as to where interrelationships exist. The key here is to remember the old adage "Better safe than sorry." So, if anything, be overly cautious and prepare others for the worst-case scenario.

Analyze the Level of Risk

All changes to infrastructure come with risk. A proper change-management request will certainly require a risk analysis, a detailed assessment of possible problems that could result from the change to determine the risk level of the change. Determining the risk level will include the development of a non-exhaustive list of questions covering as many possible things that could go wrong during the change. What if the upgrade fails? Has the new application been tested on a sample system? Will the new computers have adequate firewalls? Don't panic (well, not too much), as any risk analysis will almost certainly be passed off to a security person in your organization---but that person might have great interest in your opinions and concerns!

Change Board Approvals

So, Jamie has all this documentation to back up her request to upgrade 16 design lab computers to Windows 11. She has documented the purpose and scope of the change, the proposed date and time of the change, the affected systems and corresponding impact, and the level of risk the changes poses. Now she needs to submit this documentation to the change board to obtain their approval. The change board consists of techs and representatives from management, IT security, and administration who meet on a regular basis (quarterly is common). They review the change documentation and either approve or deny the change, but more often than not they first ask for more information or details, making a "proposal--rejection--fix--back to change board" cycle that repeats itself until everyone is satisfied.

Plan for the Change

If you receive approval from the change board, you'll need to plan for the change. What needs to be done before the change starts? What needs to be purchased? Where will new, uninstalled equipment be stored? On which days will you implement this change? During what time period? Who will cover your other duties while you're otherwise engaged? Anything that needs to be ready before you start is covered in the plan for the change.

End-User Acceptance

Part of successful change management is educating the end users in both the need for the change and how to adapt to changed systems. End-user acceptance is vital for successful change. More than anything else this means training. Do the users know how to use the new features on your super printer? What new features in this OS upgrade do end users need to learn? Are the end users versed in the new application (and know not to use the old one)?

Now let's shift gears and discuss how you and end users need to be aware of environmental impacts and how to control them so that your organization's existing technology is protected, as well as technology you may have proposed to implement in a potential change-management plan.

Environmental Impacts and Local Environmental Controls

Computers are surrounded by a host of dangers all just waiting to wreak havoc. In addition to power surges, brownouts, and blackouts, discussed in Chapter 7, there are other factors that could negatively affect your computer. Environmental factors such as chemicals stored near your computer, dust, heat, cold, wet...it's a jungle out there!

Managing environmental controls requires a person who can multitask. They must make sure the equipment is working properly and is maintained and monitored, and they must also be ready for any unexpected variables to pop up in the interim. A person in this type of position undoubtedly needs clear processes and procedures in place to make sure that a certain level of protection has been met.

EXAM TIP   Expect questions on environmental threats, impacts, and how to control them on the CompTIA A+ 220-1102 exam.

Temperature, Humidity, and Ventilation

Proper local environmental controls help secure servers and workstations from the environmental impact of excessive heat, dust, and humidity. Such environmental controls include air conditioning, proper ventilation, air filtration, and monitors for temperature and humidity. A CompTIA A+ technician maintains an awareness of temperature, humidity level, and ventilation, so that he or she can tell very quickly when levels or settings are out of whack.

A computer works best in an environment where the air is clean, dry, and room temperature. CompTIA doesn't expect you to become an environmental engineer, but it does expect you to explain and deal with how dirty or humid or hot air can affect a computer. We've covered all of these topics to some extent throughout the book, so let's just do a quick overview with security in mind.

Ventilation Patrol

Most computers are designed to operate at room temperature, which is somewhere in the area of 22°C (72°F) with the relative humidity in the 30--40 percent range. Colder and dryer is better for computers (but not for people), so the real challenge is when the temperature and the humidity go higher.

A modern office will usually have a good heating, ventilation, and air conditioning (HVAC) system, so your job as a tech is to make sure that nothing interferes with the proper functioning of your HVAC system. That means you're pretty much always on ventilation patrol. Watch for the following to make sure air is flowing:

-   Make sure ducts are always clear of obstructions.

-   Make sure duct dampers are adjusted for proper airflow (not too hot or too cold).

-   Make sure equipment is located in an area with proper ventilation.

Dirty Air

Dust and debris aren't good for any electronic components. Your typical office air conditioning does a pretty good job of eliminating the worst offenders, but not all computers are in nice offices. No matter where the computers reside, you need to monitor your systems for dirt. The best way to do this is observation as part of your regular work. Dust and debris will show up all over the systems, but the best place to look are the fans. Fans will collect dust and dirt quickly (see Figure 28-6).

Figure 28-6  Dirty fan

Dust Cleanup  All electronic components get dirty over time. To clean them, you need to use either compressed air or a nonstatic vacuum. So which one do you use? The rule is simple: If you don't mind dust blowing all over the place, use compressed air. If you don't want dust blowing all over the place, use a vacuum.

Airborne Particle Protection  Computers and the individuals operating them are typically in enclosed, indoor environments. Just as you would in your own home, changing the air filters on a regular basis reduces the amount of airborne particles coming through the filters. Dedicate a certain date to change all of the filters and make sure to always keep an inventory of the correct size filters ready for the next filter change. Another option to protect against airborne particles is to wear a mask such as the N95 masks sold in many home improvement and hardware stores.

Location/Equipment Placement  Equipment closets filled with racks of servers need proper airflow to keep things cool and to control dusty air. Make sure that the room is ventilated and air-conditioned (see Figure 28-7) and that the air filters are changed regularly.

Figure 28-7  Air-conditioning vent in a small server closet

If things are really bad, you can enclose a system in a dust shield. Dust shields come complete with their own filters to keep a computer clean and happy even in the worst of environments.

EXAM TIP   Always use proper ventilation, air filters, and enclosures. To protect against airborne particles, consider wearing a protective mask.

Hazardous Materials

Offices are filled with chemicals and substances that pose health risks. Some of these risks are immediate---hazardous materials can burst into flames or damage your skin, lungs, and eyes. Others may cause cancer or other health conditions through regular exposure over many years. The CompTIA A+ 1102 objectives want you to know about compliance to government regulations that apply to working with these substances.

Regulations may sound intimidating, but the goal here is simple: people who work with or around dangerous substances deserve to know what the risks are, what precautions they should take, and what to do if there's an accident. You'll need to consult and comply with local regulations, but you should at least be familiar with the material safety data sheet (MSDS)---a document that details the risks, precautions, and clean-up/disposal procedures---for any substances you work with regularly and know how to find the MSDS if something you aren't familiar with spills. For specific information on proper battery and toner disposal, and other device and asset disposal, take a look at Chapters 11 and 26.

Recycling E-Waste

Most U.S. cities have one or more environmental services centers that you can use to recycle electronic components. For your city, try a Google (or other search engine) search on the term "environmental services" and you'll almost certainly find a convenient place for e-waste disposal.

Prohibited Content/Activity and Privacy, Licensing, and Policies

Organizations need policies and procedures in place to deal with negative events that affect their networks and systems---an incidence response. The larger the organization, the more detailed the incidence response, ranging from the team involved to the planning and steps in every contingency. This is a gigantic topic that is covered in more advanced certifications, such as CompTIA Security+. From a CompTIA A+ tech's standpoint, you need to understand your role and what you should (and definitely should not) do when responding to an incident involving prohibited content or activity. This section explains how prohibited content, computer-related activity, and licensing can trigger negative events and also outlines the important steps to take in the unfortunate instance that such a negative event happens.

Try to stay away from any personal information on a PC. If you find something private (that isn't illegal), ignore it and forget about it. If you find something illegal, you must follow the proper procedures. If a device you work on becomes evidence in legal proceedings, isolate the system and document everything that happens going forward. Pay special attention to the chain of custody or whoever is currently in control of the machine.

Data Classification

Larger organizations, such as government entities, benefit greatly from organizing their data according to its sensitivity---what's called data classification---and making certain that computer hardware and software stay as uniform as possible. In addition, many government and internal regulations apply fairly rigorously to these organizations.

Data classification systems vary by the organization, but a common scheme classifies documents as public, internal use only, highly confidential, top secret, and so on. Using a classification scheme enables employees such as techs to know very quickly what to do with documents, the drives containing documents, and more. Your strategy for recycling a computer system left from a migrated user, for example, will differ a lot if the data on the drive was classified as internal use only or top secret.

Data classification goes hand in hand with data retention requirements, which dictate how long data needs to be kept by an organization, and is often related to how it has been classified. Customer data, security logs, and employee data, all can be covered under a company's data retention requirements. After the pre-determined period of retention, data can be disposed of, but until then, it needs to be kept just as safely as data that is currently still in use.

Regulated Data

Regulated data is data that requires specific privacy and security safeguards as mandated by federal, state, or local laws or regulations or by industry standards or regulations. An organization's technology policies must clearly address these privacy and security safeguards. There are four types of regulated data that IT departments must protect. Let's look at each.

Credit Card Transactions

The Payment Card Industry Data Security Standard (PCI DSS) is a rigorous set of rules for securing systems that accept, transmit, process, or store credit/debit card payments.

Personally Identifiable Information

Personally identifiable information (PII) is a big umbrella term for any data that can lead back to a specific individual. Regulating and protecting PII will continue to be an issue for industries and government organizations for a long, long time. The General Data Protection Regulation (GDPR) is a fairly new law that defines a broad set of rights and protections for the personal information of citizens living in countries in the European Union. Consult your superiors about your organization's policies for working with regulated data.

Laws protecting data have been developed so that organizations can create their own PII documentation for their employees to follow. The main premise behind these laws is that some information collected from individuals contains sensitive information that could easily identify who they are. Also, these regulatory laws specify that any PII data should be permanently deleted if there is no use for it. Never, in any circumstance, should PII be shared with anyone.

A sub-category of PII is personal government-issued information. Personal government-issued information consists of things like social security numbers, driver's license or passport numbers, a birth certificate, all of which, unsurprisingly, are issued by the government. These documents and the information they contain are sensitive and can leave someone vulnerable to serious identity theft if they fall into the wrong hands, and special care must be taken to protect them.

Protected Healthcare Data

Protected health information (PHI), or simply healthcare data, is basically any data that involves a person's health status, medical records, and healthcare services they have received. Like PII, PHI should never be shared unless given permission by the owner of that information.

Compliance

Compliance means that members of an organization must abide by or comply with all of the rules that apply to the organization. As we discussed earlier when we talked about standard operating procedures, the most common compliance issue revolves around software, such as what sort of software users are allowed to install on their computers. Compliance keeps technical support calls down and enables techs to focus on more serious problems---like an incident response.

Licensing, End-User License Agreement, and Digital Rights Management

Software licensing has many twists that can easily lead a user or a tech out of compliance. Like other creative acts, programmers are granted copyright to the software they create. The copyright owner then decides how he or she or it (the corporation) will license that software for others to use. Licenses can be for personal use or corporate use. They can also be valid licenses or non-expired licenses. Licenses can be closed source or open source. Each of these options has variations as well, so this gets complex. Let's start at the top and work through the variations.

Personal Use License Versus Corporate Use License

For moral or philosophical reasons, some developers want their software to be free for some or all purposes. When Linus Torvalds created the Linux operating system, for example, he made it freely available for everyone. GIMP image-editing software likewise is available to download and use for free.

Personal use licenses have variations. Many personal use programs are "free" only for personal use. If you want to use the excellent TeamViewer remote access program at your office, for example, you need to buy a corporate license. But if you want to log in to your home machine from your personal laptop, you can use TeamViewer for free. When software is released under a corporate use license, you have a legal obligation to pay money for access to it---but a lot of variations apply. Traditionally, you bought a copy of a program and could use it forever, sell it to someone else, or give it away. You bought copies for each user with a personal use license, or multiple users with an enterprise license.

Today, the picture is muddier. You can buy the use of Microsoft Office, for example, as long as you pay a monthly or yearly fee. The personal use license enables you to share the software with several other people or accounts and use it on several of your personal machines.

License Validity and Expiration

Many software licenses come with strings attached, and as techs we must pay careful attention to them. For example, a license might say how many systems you can install it on, how many human users it can have, how many CPUs you can run it on, whether you're allowed to use it for commercial purposes, whether someone who owns a valid license can transfer it to anyone else, which version(s) of the software the license is valid for, or even how long the license will remain valid.

A license is valid when your organization complies completely with these stipulations. Some programs that demand a license key may straight-up tell you if the license key itself is no longer valid---but confirmation that the license key is valid doesn't mean you're off the hook when it comes to complying with every last clause in the license. Some licenses stipulate that you can only use the software with a non-expired license. Other licenses permit you to keep using the installed version after the license has expired but cut off your access to updates and security patches until you renew the license.

EXAM TIP   At first glance, valid licenses and non-expired licenses seem to mean the same thing; however, it's important to know the distinctions between the two for the 1102 exam, objective 4.6.

Open Source Licenses

Another huge variation in software use and licensing is what you can do with the source code of an application. Open source licenses generally allow you to take the original code and modify it. Some open source licenses require you to make the modified code available for free download; others don't require that at all. Closed source licenses stipulate that you can't modify the source code or make it part of some other software suite.

End-User License Agreements

The end-user license agreement (EULA) that you must accept to be able to proceed when opening or installing new software obligates you to abide by the use and sharing guidelines stipulated by the software copyright holder. When you agree to the EULA, in other words, you're agreeing not to do things like make illegal copies of the software or attempt to reverse-engineer how it works. The EULA may also give the copyright holder permission to collect data on you and how you use the software and limit whether (or for how much) you can sue the copyright holder if it mangles your files or causes other problems.

Digital Rights Management

Software and media companies use various forms of digital rights management (DRM) technology to try to enforce their policies regarding when, where, and how we can use the software or access media such as video, music, and books. In short, DRM is one way the industry has tried to fight software and media piracy over the years. Many programs require activation over the Internet, for example, or a special account with the copyright holder. Some media files can only be opened by the provider's official app.

NOTE   The key for a tech is to know the specific licenses paid for by the tech's organization and ensure that the organization abides by those licenses. Using pirated software, exceeding the use limits set by a EULA, and using programs that aren't licensed for commercial use in a corporate setting all expose your organization to lawsuits.

Incident Response

Organizations have incident response policies and procedures to deal with negative events. CompTIA A+ techs might be members of the incident response team. As such they need to understand first response actions, identification and reporting of incidents, and chain of custody. Let's start by looking at first response actions.

First Response

First response means securing the area, determining the scope of the incident, and analyzing the impact the incident might have on the organization. If you're part of the incident response team, your first response duties will be spelled out in detail in the incident response plan. Most likely, your team's first action when something bad happens is to secure the area. Securing the area can mean physical lockdown---no one in or out---or other lockdown---no network traffic in or out of the affected section.

Incident Reporting

An incident report means telling your supervisor about the data you've gathered regarding a computer or network incident. This provides a record of what you've done and accomplished. It also provides information that, when combined with other information you may or may not know, could reveal a pattern or bigger problem to someone higher up the chain.

This can be accomplished with a documentation of incident. Many companies have pre-made forms that you simply fill out and submit. Other places are less formal. Regardless, you need to do this!

Tracking specific problems through incident reports documentation helps current and future techs deal with problematic hardware and individuals. If you have five identical color laser printers in five departments, for example, and one starts jamming regularly after 10,000 pages, documenting the problem---the incident---and the solution will point very clearly to the potential problems with the other four printers when they reach that same usage level.

Once you've gathered data about a particular system or dealt with a computer or network problem, what's next?

Inform Management/Law Enforcement as Necessary

So, you have documented all of the necessary information needed about the incident. Now it's time for you to make a decision. Is the incident at a low risk level and can be resolved at your level? Or, is it something that has escalated to a higher risk level where you need to inform your supervisor? Determine the scope of the incident (single system, whole group of users, and so on) and explore its seriousness and potential impact on the organization. Determining the scope of the incident can be accomplished by questioning users, reviewing log files, and so on. Your network and security people will handle possible impact scenarios and determine if the impact is serious enough to include law enforcement in the investigation.

Chain of Custody

When responding to an incident involving prohibited content or activity, there must be an end-to-end process for identifying who owns what, where it is, and who is liable for it. It asks and answers, "Whose responsibility is this?" when assets, digital or physical, transfer hands in an organization. For example, who is in charge and liable for data integrity (ensuring that the data is in its original and uncorrupted form) and data preservation (ensuring that the data is backed up and kept available)? Where is the data stored (i.e., drive, server)? This process, called the chain of custody, begins when the evidence is initially seized or collected and establishes a continuous accounting of where the evidence is at all times, who has possessed it, what activities were performed on it, and the details of its storage, use, and transfer. This process helps to ensure the integrity of evidence and minimizes the possibility that it has been altered or tampered with. Chain of custody contributes to the admissibility and value of evidence in court.

Beyond A+

Whew! You've just finished a book that covers everything you need to know to take and pass the CompTIA A+ 1101/1102 exams. Congratulations! What's next?

First, go back to the Introduction and review the study chart and guidelines. Review, review, review! Take the practice exams and look for exam sources online to get even more scoop on the types of questions you'll see.

Second, schedule your exams if you haven't already done so (pressure and diamonds and all that). Having that endpoint in sight helps focus.

Go back to my original question once you've taken and passed both CompTIA A+ exams: What's next? The two logical steps are to start studying for CompTIA Network+ and CompTIA Security+. These complete CompTIA's Core curriculum and round out tech skills needed for today's interconnected and security-heightened world. There are a lot of great writers and videographers out there who have excellent materials on CompTIA Network+ and Security+ (including me), so you won't find it hard to get study materials.

Good luck, my friend, and keep in touch!

Chapter Review

Questions

1\.   Henry gets a help desk call from Arthur in accounting who reports that his keyboard is not working. This seems like a familiar problem, one that another tech mentioned a short time back. Where should Henry look to find information on the problem?

A.   Change documentation

B.   Incident reports

C.   Asset management documentation

D.   Risk management documentation

2\.   Annie wants to mark several Mac laptops issued to salespeople so that she can set up a scanner at the office door to track each time the laptops enter and leave the building. What will help her accomplish this goal?

A.   Add a barcode sticker to each laptop.

B.   Add an RFID tag to each laptop.

C.   Submit a change document to the change board.

D.   It can't be done, because the laptops run macOS.

3\.   Joan has proposed upgrading the inkjet printers in the marketing department with color laser printers. The purpose of the change is to reduce the cost per page printed, because toner is less expensive than ink and the duty cycle of laser printers is longer than that of inkjet printers. The marketing department currently has three inkjet printers. What's her logical next step?

A.   She should complete the scope of change part of the change document to factor in the price of the printers.

B.   She should perform a risk analysis to determine any potentially negative consequences.

C.   She should download the documentation on the new printers and begin the education process for the marketing department on how to use them.

D.   She should contact the change board with her initial proposal.

4\.   Once the change board has reviewed and approved Joan's plan for the new printers, what's her next step?

A.   Create a rollback plan in case the quality of print with the laser printers isn't sufficient for the marketing materials.

B.   Test the rollback plan.

C.   Finalize the change documentation.

D.   Implement the change plan.

5\.   What broad term describes the process of creating a road map for current and future techs to make changes or repairs over time for an organization?

A.   Change documentation

B.   Change management

C.   Management documentation

D.   Network documentation

6\.   What broad term describes the process of enabling organizations to implement changes to IT infrastructure in a safe and cost-effective manner?

A.   Change documentation

B.   Change management

C.   Management documentation

D.   Network documentation

7\.   As part of the change-management process, educating users on new systems is an important component in which of the following?

A.   Rollback plan

B.   Accessibility training

C.   End-user acceptance

D.   Risk analysis

8\.   Which of the following is an example of an environmental control?

A.   HVAC system

B.   Temperature and humidity

C.   Surge protector

D.   Fire extinguisher

9\.   Which of the following is a detailed assessment of possible problems that could result from change?

A.   Acceptable use policy

B.   New-user setup checklist

C.   Regulatory requirements

D.   Risk analysis

10\.   What does an IT department use for a departing employee to ensure that all equipment has been returned, access has been removed, and, where possible, knowledge transfer has been facilitated?

A.   End-user termination checklist

B.   New-user setup checklist

C.   Network topology diagram

D.   Acceptable use policy

Answers

1\.   B. Henry should check the incident reports to see if there's a history of problems with the computer at that workstation.

2\.   B. Annie should add a radio frequency identification (RFID) tag to each laptop and install a scanner at the door to track when the laptops are taken out of the office and returned.

3\.   A. Joan hasn't finished the scope of change yet, so she should include the price of the printers.

4\.   A. Once the change board has approved the change plan, Joan should make sure to have a good rollback plan in place in case something unforeseen and negative happens.

5\.   D. The term network documentation describes the road map for current and future techs to make changes or repairs over time for the organization.

6\.   B. The term change management describes the process organizations use to implement changes to IT infrastructure in a safe and cost-effective manner.

7\.   C. Training users in new or updated systems leads to end-user acceptance of the changes.

8\.   A. An HVAC system is an example of an environmental control.

9\.   D. A risk analysis is a detailed assessment of possible problems that could result from change.

10\.   A. When an employee parts ways with an organization, the IT department uses an end-user termination checklist to ensure that the employee has returned all equipment, that their access has been removed, and, where possible, knowledge transfer has been facilitated.

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

Appendix B About the Online Content

Glossary

Index

42h 21m remaining
