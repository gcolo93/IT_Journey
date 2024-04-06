
CHAPTER 27

Securing Computers

In this chapter, you will learn how to

-   Explain the threats to your computers and data

-   Describe key security concepts and technologies

-   Explain how to protect computers from network threats

Your PC is under siege. Through your PC, malicious people can gain valuable information about you and your habits. They can steal your files. They can run programs that log your keystrokes and thus gain account names and passwords, credit card information, and more. They can run software that takes over much of your computer processing time and use it to send spam or steal from others. The threat is real and immediate. Worse, they're doing these things to your clients as I write these words. You need to secure your computer and your users' computers from these attacks.

But what does computer security mean? Is it an anti-malware program? Is it big, complex passwords? Sure, it's both of these things, but what about the fact that your laptop can be stolen easily or that improper ventilation can cause hard drives and other components to die?

To secure computers, you need both a sound strategy and proper tactics. For strategic reasons, you need to understand the threat from unauthorized access to local machines as well as the big threats posed to networked computers. Part of the big picture is knowing what policies, software, and hardware to put in place to stop those threats. From a tactical in-the-trenches perspective, you need to master the details to know how to implement and maintain the proper tools. Not only do you need to install anti-malware programs in your users' computers, for example, but you also need to update those programs regularly to keep up with the constant barrage of new malware.

1102

Analyzing Threats and Vulnerabilities

Threats to your data and PC come from two directions: accidents and malicious people. All sorts of things can go wrong with your computer, from users getting access to folders they shouldn't see to a virus striking and deleting folders. Files can be deleted, renamed, or simply lost (what Nancy Drew might call "The Case of the Disappearing Files"). Hard drives can die, and optical discs get scratched and rendered unreadable. Accidents happen, and even well-meaning people can make mistakes.

Threats need some way to access a network or facility, whether they are accidental or malicious, internal or external, and that's where vulnerabilities come in. A vulnerability is a weak spot in your defenses that enables a threat to cause harm. Vulnerabilities can exist in an organization's physical security or in its networks. Understanding different types of vulnerabilities and the threats that will try to exploit them is vital to protecting your organization's data, reputation, and safety. We'll look at threats first, followed by vulnerabilities that threats exploit to do their harm.

Threats

Unfortunately, a lot of people out there intend to do you harm. Combine that intent with a talent for computers, and you have a dangerous combination. Let's look at the following issues:

-   Malicious actors

-   Unauthorized access

-   Social engineering

-   Insider threats

-   Data destruction, whether accidental or deliberate

-   Administrative access

-   System crash/hardware failure

-   Physical theft

-   Malware

-   Spam

Malicious Actors

In some cases, the threat in question is an individual, also known as a threat actor. Whether they're an external malicious actor like a hacker or an internal malicious actor like a disgruntled employee, threat actors need some way to use vulnerabilities to their advantage. This is known as an attack, or an exploit. The general order of operations goes something like this: a threat actor identifies one or more vulnerabilities in a network or physical security system, uses some combination of attacks to exploit the vulnerability or vulnerabilities, and proceeds to carry out their nefarious plans. You'll notice that I didn't say that a threat actor will use only one attack or exploit only one vulnerability. There's good reason for this. Very rarely will a malicious actor make use of only one method. For example, a malicious actor attacking from outside the organization may employ a phishing scam to gain user login credentials, use those credentials to gain initial access to a network, then deploy a zero-day attack to take over the network administrator's account.

If some of these terms sound unfamiliar now, don't worry. You're about to get a crash course in some of the many threats and attacks you'll encounter in the world of IT.

EXAM TIP   Be aware that while many of these terms are considered types of attacks, CompTIA's A+ 1102 exam objectives classify them all as social engineering or threats. For the purpose of the 1102 exam, threats and attacks are one and the same, but in most other contexts, threats and attacks are separate concepts.

Zero-Day Attack  A zero-day attack is an attack on a vulnerability that wasn't already known to the software developers. It gets the name because the developer of the flawed software has had zero days to fix the vulnerability. Microsoft, Apple, and other software developers regularly post patches to fix flaws as they're discovered.

Spoofing  Spoofing is the process of pretending to be someone or something you are not by placing false information into your packets. Any data sent on a network can be spoofed. Here are a few quick examples of commonly spoofed data:

-   Source MAC address and IP address, to make you think a packet came from somewhere else

-   E-mail address, to make you think an e-mail came from somewhere else

-   Web address, to make you think you are on a Web page you are not on

-   Username, to make you think a certain user is contacting you when in reality it's someone completely different

Generally, spoofing isn't so much a threat as it is a tool to make threats. If you spoof my e-mail address, for example, that by itself isn't a threat. If you use my e-mail address to pretend to be me, however, and to ask my employees to send in their usernames and passwords for network login? That's clearly a threat. (And also a waste of time; my employees would never trust me with their usernames and passwords.)

On-Path Attack  In an on-path attack, an attacker taps into communications between two systems, covertly intercepting traffic thought to be only between those systems, reading or in some cases even changing the data and then sending the data on. A classic on-path attack would be a person using special software on a wireless network to make all the clients think his laptop is a wireless access point. He could then listen in on that wireless network, gathering up all the conversations and gaining access to passwords, shared keys, or other sensitive information.

EXAM TIP   While CompTIA prefers and uses the term on-path attack, you'll more commonly hear it referred to by its original name, man-in-the-middle, out in the world. Just be aware that the two terms are interchangeable, and that on-path attack is how it will be referred to on the exam.

Session Hijacking  Somewhat similarly to on-path attacks, session hijacking tries to intercept a valid computer session to get authentication information. Unlike on-path attacks, session hijacking only tries to grab authentication information, not necessarily listening in like an on-path attack.

Brute-Force Attack  CompTIA describes brute force as a threat, but it's more of a method that threat agents use. Brute force is a method where a threat agent guesses many or all possible values for some data. Most of the time the term brute force refers to an attempt to crack a password, but the concept also applies to other attacks. You can brute force a search for open ports, network IDs, usernames, and so on. Pretty much any attempt to guess the contents of some kind of data field that isn't obvious (or is hidden) is considered a brute-force attack.

There are two other tools attackers use to brute force passwords: dictionaries and rainbow tables. A dictionary attack is a form of brute-force attack that essentially guesses every word in a dictionary. Don't just think of Webster's dictionary---a dictionary used to attack passwords might contain every password ever leaked online.

Before we can talk about rainbow tables, we need to look closer at password leaks. One (terrible!) way to authenticate users is to save a copy of their password in a database and check it every time they log in. Hackers love to steal these databases because they can go try the username and password on popular services, and use the passwords to improve the dictionaries they use to guess passwords.

In response to this threat, authentication systems only save a special value (called a hash) computed from the password; each time the user logs in, the system re-computes this special value and compares it with the saved copy. If an attacker steals one of these databases, they only get a bunch of usernames and hashes. Hashes are special because the computation that creates them is irreversible; the only way to figure out what password produced a given hash is to guess a password, perform the same computation, and see if the hashes match.

Attackers fought back by pre-computing large lookup tables---known as hash tables---of passwords and the corresponding hash. When they find a large database of hashed passwords, they can just look up the corresponding password in their hash table. Hash tables for passwords more than a few characters long eat tons of storage space, so they're turned into rainbow tables to save space (at the expense of a little speed and accuracy.) Rainbow tables use complicated math to condense dictionary tables with hashed entries dramatically. They're binary files, not text files, and can store amazing amounts of information in a relatively small size. Rainbow tables generally fall into the realm of CompTIA Security+ or even higher-level certifications, but the phrase has become common enough that CompTIA A+ techs need to know what it means.

Denial of Service  A denial of service (DoS) attack uses various methods to overwhelm a system, such as a Web server, to make it essentially nonfunctional. DoS attacks were relatively common in the early days of the Web. These days you'll see distributed denial of service (DDoS) attacks that use many machines simultaneously to assault a system. A DDoS attack is generally executed using a botnet. A botnet consists of any number (usually a large one) of systems infected with malware designed to allow them to be controlled by an attacker and used to send disruptive traffic designed to bring down a resource. You'll get a closer look at botnets and how they work later on in the chapter when we discuss malware.

Cross-Site Scripting  Most companies have Web sites, and Web sites can sometimes be very vulnerable to attacks by the bad guys. One such attack that can pose a threat to your Web applications is known as cross-site scripting. Cross-site scripting (XSS) is an attack in which the attacker injects malicious code into the Web app in order to trick it into sending things it shouldn't to other users of the Web site. Generally, this occurs due to errors in the application's code, which the attacker finds and exploits. XSS can lead to account takeovers, stolen data, or even a full takeover of the Web site or app. The nitty-gritty details of XSS, specific variants of the attack, and how to prevent them are things you'll learn more about in CompTIA Security+, but for the CompTIA A+ 1102 exam, be aware that cross-site scripting can pose a major threat to an organization's Web site(s).

SQL Injection  You've most likely deduced by now that accessing, stealing, and destroying data are common goals of malicious actors, so let's take a look at one of the favorite methods hackers use to achieve them. Before I can tell you about the dreaded SQL injection, I'm going to have to tell you what SQL is. SQL is an acronym for Structured Query Language. SQL is a language that enables a program to interact with a database using various commands and queries. If you've started thinking that attacking a database sounds like a dangerous threat, you're right. An SQL injection occurs when an attacker enters SQL commands into an input field like you'd see in a Web app, in order to gain access to data in a database that they shouldn't be able to see. You won't need to know the ins and outs of how SQL injection is performed, but know that preventing it is done at the programming level, with something known as input validation.

Unauthorized Access

Unauthorized access occurs when a person accesses resources without permission. "Resources" in this case means data, applications, and hardware. A user can alter or delete data; access sensitive information, such as financial data, personnel files, or e-mail messages; or use a computer for purposes the owner did not intend.

Not all unauthorized access is malicious---often this problem arises when users who are poking around in a computer out of curiosity or boredom discover they can access resources in a fashion the primary user did not have in mind. Unauthorized access becomes malicious when people knowingly and intentionally take advantage of weaknesses in your security to gain information, use resources, or destroy data!

One way to gain unauthorized access is intrusion. You might imagine someone kicking in a door and hacking into a computer, but more often than not it's someone sitting at a home computer, trying various passwords over the Internet. Not quite as glamorous, but it'll do. Another insidious method is manipulating people into giving privileged information or access that would be otherwise unavailable to a would-be attacker. This takes us into a discussion of one of the most common and dangerous categories of threats.

Social Engineering

Although you're more likely to lose data through accidents, the acts of malicious users get the headlines. Most of these attacks come under the heading of social engineering---the process of using or manipulating people inside the organization to gain access to its network or facilities---which covers the many ways humans can use other humans to gain unauthorized information. This information may be a network login, a credit card number, company customer data---almost anything you might imagine that one person or organization may not want outsiders to access.

NOTE   Social engineering attacks are often used together, so if you discover one of them being used against your organization, it's a good idea to look for others.

Social engineering attacks aren't hacking---at least in the classic sense of the word---but the goals are the same and the attacks will often be used by hackers in conjunction with other methods. Let's look at a few of the more classic types of social engineering attacks.

Infiltration  Hackers can use impersonation to enter your building physically disguised as cleaning personnel, repair technicians, messengers, and so on. They then snoop around desks, looking for whatever they can find. They might talk with people inside the organization, gathering names, office numbers, department names---little things in and of themselves but powerful tools when combined later with other social engineering attacks.

Dressing the part of a legitimate user---with fake badge and everything---enables malicious people to gain access to locations and thus potentially your data. Following someone through the door, for example, as if you belong, is called tailgating. Tailgating is a common form of infiltration.

To combat tailgating, facilities often install an access control vestibule at the entrance to sensitive areas, or sometimes at the entrance to the whole building. Traditionally called a mantrap, an access control vestibule is a small room with a set of two doors, one to the outside, unsecured area and one to the inner, secure area. When walking through the access control vestibule, the outer door must be closed before the inner door can be opened. In addition to the double doors, the user must present some form of authentication. For additional security, an access control vestibule is often controlled by a security guard who keeps an entry control roster. This document keeps a record of all comings and goings from the building.

Information Gathering  You're probably familiar with the old saying that "knowledge is power." The good news is that when it comes to securing systems and facilities, the saying is true. The bad news is that it's also true when someone is trying to compromise those systems and facilities. Social engineering is often used by threat actors to gather information that makes it easier for them to successfully gain access. Here are some common ways that they get ahold of information that they aren't supposed to have.

Dumpster diving is the generic term for searching garbage for information. This is also a form of intrusion. The amount of sensitive information that makes it into any organization's trash bin boggles the mind! Years ago, I worked with an IT security guru who gave me and a few other IT people a tour of our office's trash. In one 20-minute tour of the personal wastebaskets of one office area, we had enough information to access the network easily, as well as to seriously embarrass more than a few people. When it comes to getting information, the trash is the place to look!

Shoulder surfing is another technique for gathering information and gaining unauthorized access. Shoulder surfing is simply observing someone's screen or keyboard to get information, often passwords. As the name implies, it usually requires the bad guy looking over your shoulder to see what you are doing.

Vishing  Vishing is one of the most common social engineering attacks. In this case, the attacker makes a phone call to someone in the organization to scam them into revealing information gain information. The attacker attempts to come across as someone inside the organization and uses this to get the desired information. Probably the most famous of these scams is the "I forgot my username and password" scam. In this gambit, the attacker first learns the account name of a legitimate person in the organization, usually using the infiltration method. The attacker then calls someone in the organization, usually the help desk, in an attempt to gather information, in this case a password.

Hacker: "Hi, this is John Anderson in accounting. I forgot my password. Can you reset it, please?"

Help Desk: "Sure, what's your username?"

Hacker: "j_w_anderson."

Help Desk: "OK, I reset it to e34rd3."

Vishing certainly isn't limited to attempts to get network access. There are documented vishing attacks against organizations aimed at getting cash, blackmail material, or other valuables.

Phishing  Phishing is the act of trying to get people to give their usernames, passwords, or other security information by pretending to be someone else electronically. A classic example is when a bad guy sends you an e-mail that's supposed to be from your local credit card company asking you to send them your username and password. Phishing is by far the most common form of social engineering done today.

Phishing refers to a fairly random act of badness. The attacker targets anyone silly enough to take the bait. Spear phishing is the term used for targeted attacks, like when a bad guy goes after a specific celebrity. The dangerous thing about spear phishing is that the bait can be carefully tailored using details from the target's life. A particularly dangerous form of phishing specifically targets people who are high up in an organization, such as executives or administrators. This is known as whaling.

Evil Twin  One of the reasons infiltrations can be so dangerous is that a malicious actor may be able to plant devices inside an organization's network. A particularly dangerous example of this is known as an evil twin. An evil twin is a fake wireless access point configured to mimic the traits of a legitimate device and network, in order to lure unsuspecting users to connect to the attacker's device. By doing this, the attacker can snoop on Internet traffic, steal user credentials, and use this information to do additional damage.

Insider Threats

Threats to your network or facility don't only come from the outside. Sometimes, the threat exists within the organization itself. This is known as an insider threat. An insider threat is any security risk that originates from a person inside an organization. Sometimes, the insider in question is malicious, out to steal funds or information. They may also be a disgruntled current or former employee looking to get back at the company.

Don't make the mistake of thinking that all insider threats are malicious though---sometimes accidents happen, and the insider threat is a well-meaning person just trying to make their or someone else's job easier. The real threat here is the access to systems and facilities that they have and what they can do with it. There are several ways to mitigate the risks of insider threats, most which center on access control. Only giving users access to what they need to do their jobs and deleting relevant user and administrator accounts when someone leaves the company are both examples of insider threat mitigation. Some methods to mitigate the risk of insider threats will be discussed in greater detail later in the chapter in the "Logical Security" section.

Data Destruction

Often an extension of unauthorized access, data destruction means more than just intentionally or accidentally erasing or corrupting data. It's easy to imagine some evil hacker accessing your network and deleting all your important files, but authorized users may also access certain data and then use that data beyond what they are authorized to do. A good example is the person who legitimately accesses a Microsoft Access product database to modify the product descriptions, only to discover that she can change the prices of the products, too.

This type of threat is particularly dangerous when users are not clearly informed about the extent to which they are authorized to make changes. A fellow tech once told me about a user who managed to mangle an important database when someone gave him incorrect access. When confronted, the user said: "If I wasn't allowed to change it, the system wouldn't let me do it!" Many users believe that systems are configured in a paternalistic way that wouldn't allow them to do anything inappropriate. As a result, users often assume they're authorized to make any changes they believe are necessary when working on a piece of data they know they're authorized to access.

Administrative Access

Every operating system enables you to create user accounts and grant those accounts a certain level of access to files and folders in that computer. As an administrator, supervisor, or root user, you have full control over just about every aspect of the computer. This increased control means these accounts can do vastly more damage when compromised, amplifying the danger of several other threats. The idea is to minimize both the number of accounts with full control and the time they spend logged in.

Even if a user absolutely needs this access, uses strong passwords, and practices good physical security, malware installed by a convincing spear phishing attack could leverage that control to access files, install software, and change settings a typical account couldn't touch.

System Crash/Hardware Failure

As with any technology, computers can and will fail---usually when you can least afford for it to happen. Hard drives crash, the power fails . . . it's all part of the joy of working in the computing business. You need to create redundancy in areas prone to failure (such as installing backup power in case of electrical failure) and perform those all-important data backups. A security-specific example would be having redundant firewalls to protect the network in the event that one of them fails. Chapter 14 goes into detail about using backups and other issues involved in creating a stable and reliable system.

Physical Theft

A fellow network geek once challenged me to try to bring down his newly installed network. He had just installed a powerful and expensive firewall router and was convinced that I couldn't get to a test server he added to his network just for me to try to access. After a few attempts to hack in over the Internet, I saw that I wasn't going to get anywhere that way.

So, I jumped in my car and drove to his office, having first outfitted myself in a techy-looking jumpsuit and an ancient ID badge I just happened to have in my sock drawer. I smiled sweetly at the receptionist and walked right by my friend's office (I noticed he was smugly monitoring incoming IP traffic by using some neato packet-sniffing program) to his new server.

I quickly pulled the wires out of the back of his precious server, picked it up, and walked out the door. The receptionist was too busy trying to figure out why her e-mail wasn't working to notice me as I whisked by her carrying the 65-pound server box. I stopped in the hall and called him from my cell phone.

Me (cheerily): "Dude, I got all your data!"

Him (not cheerily): "You rebooted my server! How did you do it?"

Me (smiling): "I didn't reboot it---go over and look at it!"

Him (really mad now): "YOU <EXPLETIVE> THIEF! YOU STOLE MY SERVER!"

Me (cordially): "Why, yes. Yes, I did. Give me two days to hack your password in the comfort of my home, and I'll see everything! Bye!"

I immediately walked back in and handed him the test server. It was fun. The moral here is simple: Never forget that the best network software security measures can be rendered useless if you fail to protect your systems physically!

Protecting Laptops  Physical security for your systems extends beyond the confines of the office as well. The very thing that makes laptops portable also makes them tempting targets for thieves. One of the simplest ways to protect your laptop is to use a basic cable lock. The idea is to loop the cable around a solid object, such as a bed frame, and secure the lock to the small security hole on the side of the laptop.

Malware

Networks are without a doubt the fastest and most efficient vehicles for transferring computer viruses among systems. News reports focus attention on the many malicious software attacks from the Internet, but a huge number of such attacks still come from users who bring in programs on optical discs and USB drives. The "Network Security" section of this chapter describes the various methods of virus infection and other malware and what you need to do to prevent such attacks from damaging your networked systems.

Spam

If you have an e-mail address, there's a 100 percent chance that you've seen spam at some point in your life. Spam is the digital equivalent of junk mail; it's bulk e-mail sent out to as many people as possible in the hopes that at least some of them engage with it. Sometimes spam is just an annoyance, but it can also be a threat to your network. Phishing attempts, malicious links, and attachments that contain malware are just some of the dangers that spam can present. Spam management methods and tools were covered in detail back in Chapter 19.

Vulnerabilities

Threats to your computers and facilities can be scary, but they need some way to gain access before they can cause trouble. Threats compromise a system by exploiting vulnerabilities in a computer, network, company policy, or physical security to gain access. Once a vulnerability is exploited, whether by an outside hacker, a disgruntled employee, or even inadvertently by a well-meaning person just trying to make their job easier, chaos can ensue. Data deletion, data theft, extortion, and all sorts of other nasty things can happen if vulnerabilities aren't identified and addressed. As a CompTIA A+ technician, you likely won't be expected to know the nitty-gritty details of how to fix all vulnerabilities, but you should understand the fundamentals of different types of vulnerability, and how they can threaten an organization. Here are a few common vulnerabilities that you may run across while working as a technician.

Have you ever been working on your computer, playing a game, or having a Zoom meeting, and suddenly your operating system nags you to install updates that require a reboot? I know I have, and as disruptive as that can be, the disruptions that could result from ignoring those messages are even worse. That's because these warnings are telling you to patch your operating system, and oftentimes, those patches are intended to address a security risk. Unpatched systems are vulnerable to an ever-growing list of vulnerabilities that attackers know about and are actively exploiting. Leaving a system unpatched is like leaving a second-story window open while you go on vacation. Sure, you may get home and see that everything is fine, but you may also have been robbed blind. Patching systems is key and will be discussed in more detail later in this chapter when we address malware prevention.

If leaving your systems unpatched is like leaving a second-story window open when you go on vacation, an unprotected system is like leaving your front door open with a sign on the lawn inviting people to break in. An unprotected system lacks key security tools like anti-malware software and firewalls. Without these in place, there is nothing stopping a hacker from doing whatever they want in your network. They can send malware, try to connect directly to your internal network, and try to steal or destroy your sensitive information, and do all of this with a relatively low chance of being detected. An unprotected system is a serious vulnerability, whether it's at home, in a small business, or in a major corporation. If you must have unprotected systems, make sure to isolate and monitor them!

Operating systems also have lifespans. Over time, as new and sometimes improved operating systems launch, older ones are phased out. Once an old OS is phased out completely, it stops receiving security updates as new vulnerabilities are discovered. These operating systems are known as end-of-life (EOL) operating systems and can present a major vulnerability to a network if even one device is still using an EOL OS. It's a fairly common problem, because operating system upgrades can be expensive and disruptive to a business's operations. Regardless, making sure that operating systems are well supported and still receiving regular security updates is an important way to mitigate vulnerabilities.

While the concept of bring your own device (BYOD) was discussed in the context of securing mobile devices back in Chapter 25, the potential security risks extend past mobile devices to personal laptops as well. While BYOD may be popular with employees and more friendly to an organization's budget, BYOD can also be a security vulnerability. An external threat can use the fact that personal devices may not all be maintained with standard security features to gain access from the outside. Additionally, insider threats, whether malicious or accidental, can use personal devices to introduce malware, or remove privileged data from the security of the company's internal network.

In the best of all possible worlds, your organization will use a mix of policies, systems, and elbow grease to ensure the devices in your networks never have vulnerabilities like these. But in reality, a system may need to defer updates for weeks while it's busy rendering special effects. Users may need time to comply or need network access to do it. The accounting department might require software that only works on an EOL OS. A computer that serves as the interface to an old ICS system may not even have a software firewall (we'll look at these later in the chapter). Unless you check compliance continually, new violations will appear between checks. In short, compliance is an aspiration, and you'll often have to manage the vulnerabilities and risks that non-compliant systems represent (often by isolating them and monitoring them well).

Security Concepts and Technologies

Once you've assessed the threats to your computers and networks, you need to take steps to protect those valuable resources. Depending on the complexity of your organization, this can be a small job encompassing some basic security concepts and procedures, or it can be exceedingly complex. The security needs for a three-person desktop publishing firm, for example, would differ wildly from those of a defense contractor supplying top-secret toys to the Pentagon.

From a CompTIA A+ certified technician's perspective, you need to understand the big picture (that's the strategic side), knowing the concepts and available technologies for security. At the implementation level (that's the tactical side), you're expected to know where to find such things as security policies in Windows. A CompTIA Network+ or CompTIA Security+ tech will give you the specific options to implement. (The exception to this level of knowledge comes in dealing with malicious software such as viruses, but we'll tackle that subject in the second half of the chapter.)

Controlling access is the key. If you can control access to the data, programs, and other computing resources, you've secured your systems. Access control is composed of interlinked areas of physical and logical security that a good security-minded tech should think about: physical security, authentication, users and groups, and security policies. Much of this you know from previous chapters, but this section should help tie it all together as a security topic. The first step is understanding physical security, which includes methods of preventing physical access to facilities, systems, and information, and the second is understanding logical security to learn how to protect your network, authenticate users, and employ effective security policies.

Physical Security

For most people, when they hear the word security, the first thing they think of are things like guards, fences, security cameras, and the like. That's because they're thinking about physical security. Physical security is often the first line of defense for an organization. It includes the fences and gates that keep people off the property, the locks that keep people from entering a building or area they aren't supposed to, and the guards who use surveillance tools and alerts to keep an eye on things. Physical security is all about defending facilities and systems from---you guessed it---physical threats, both internal and external. There are layers to physical security that can and often do overlap with logical security tools to provide effective security coverage. Let's start our investigation by looking at some specific goals and methods of physical security.

Securing Facilities

The first order of security is limiting access to your physical hardware. The security market is huge, but the options basically boil down to fences, doors, locks, alarms, and keeping a close eye on things. The first step is understanding that all of these pieces can (and will) fail or be beaten; great security involves arranging and layering many pieces so that they can enhance each other's strengths and compensate for each other's weaknesses.

Think back to the access control vestibule introduced earlier in the chapter. A low-tech solution like a traditional door lock is just a speed-bump to someone with a lock-pick and a moment alone with the lock. Access control vestibules are great because they combine simple measures like doors, door locks, security guards, and an entry control roster in a way that is much harder to beat than one or two locked doors. Some facilities may enhance their entrance security further by adding a magnetometer, better known as a metal detector. As pointed out earlier in the chapter when we talked about different types of threats, some threats originate from inside the organization as well as outside. A metal detector is a good way to help prevent people from bringing in dangerous items that they could use to cause harm, and to prevent them from walking out with something that doesn't belong to them.

Sometimes access control needs to be extended past the door itself, out to the property. Many facilities have more than one entrance, or multiple buildings. As a result, organizations may add an additional line of defense to keep unauthorized people off company property altogether. Fences are often used to stop people from snooping around where they aren't supposed to. Bollards, those short concrete or metal posts that you'll sometimes see in areas with heavy foot traffic, can be used to prevent vehicles from getting too close for comfort (see Figure 27-1).

Figure 27-1  Example of a bollard

Security guards are great, but they can't be everywhere at once. They need some way to keep an eye on things. That's where the following tools come into play:

-   Video surveillance can be used by security personnel to monitor the facility from a centralized location.

-   Good lighting makes it harder for a would-be bad guy to avoid detection, with the added benefit of decreasing the likelihood of workplace accidents for staff.

-   Motion sensors can be used to let them know if someone or something is detected so they can take a closer look.

-   Alarm systems can serve a variety of functions, from warning the IT department of an attempted network breach, to informing staff of a security issue, to alerting security staff or law enforcement if a break-in happens after hours.

Any combination of these tools makes a great addition to a robust security plan, but it's also important to make sure that people inside the organization don't have access to things they aren't supposed to. This brings us to the next set of access control options.

Traditional door locks aren't terrible, but keys are easy to copy and the cost of frequently re-keying locks adds up fast. An organization ready to move beyond the basics can step up to a keyless lock system driven by employee ID badges---especially ones with authentication tools such as radio frequency identification (RFID) or smart cards (see "Authentication," later in this chapter)---to control building and room access. Figure 27-2 shows a typical badge.

Figure 27-2  Typical employee badge/smart card

Lock Down Systems

Once an attacker has physical access to the building, protecting your hardware gets a lot harder. There are some options here, but don't plan on them doing much more than slow someone down by a few minutes and make it obvious to anyone watching that they're up to no good:

-   Lock the doors to your workspaces. A fast, reliable keyless lock system can make it painless to lock them even when the user steps out for a moment.

-   Equipment locks can keep someone from quickly walking off with the hardware.

-   USB locks make it harder to plug in a USB drive to load malware for stealing data.

-   RJ45 locks limit an intruder's ability to gain access to the wired network.

-   Server locks limit access to a server's ports and drives. There are also locking rack doors to limit access to the front or back of an entire server rack.

These devices are meaningless if an intruder can walk in like they belong, sit down at an unattended, logged-in computer, and get to work. Don't leave a logged-in PC unattended, even if it's just a Standard or Guest user. May the gods help you if you walk away from a server still logged in as an administrator. You're tempting fate.

If you must step away for a moment, manually lock the computer (or screen) with a hotkey or the primary OS menu. On a Windows system, just press WINDOWS-L on the keyboard to lock it. It's also a good idea to set up a screensaver with a short wait time and configure it to show the logon screen on resume.

EXAM TIP   If you're in charge of multiple-user security best practices, using screensaver locks---configured to show the logon screen on resume---can help a lot with users who might forget to lock their systems when taking a break or going to lunch. Both Windows and macOS enable you to take this a step further and set automatic timeout and a screen lock, where the screen goes blank after a few minutes and a password is required for logon.

Protect Sensitive Information

Locking unattended systems is a great habit, but it won't help much if the intruder manages to watch the user enter their password or is able to read it off a sticky note on the monitor. Don't write down passwords and leave them in plain sight. Teach users to follow the strong password guidelines set forth in Chapter 13. Be aware of the risk of shoulder surfing. Ideally, the office layout should make it impossible for someone to watch the user without their knowledge.

If users need to work with sensitive information anywhere someone unauthorized could see the screen, they may need a privacy filter (also called a privacy screen)---a framed sheet or film that you apply to the front of your monitor. Privacy filters reduce the viewing angle, making it impossible to see the screen unless you're directly in front of it (see Figure 27-3). Lock up paper copies of critical, personal, or sensitive documents out of sight and shred any you don't need immediately.

Figure 27-3  Privacy filter

Logical Security

While physical security is focused on preventing unauthorized access to facilities and equipment, logical security is primarily focused on denying access to computers and data. Logical and physical security features are generally combined for maximum effectiveness. In some cases, like with biometrics, the security tool can be used for both logical and physical security applications. Let's dig deeper into some of the more commonly implemented logical security controls.

MAC Address Filtering

It's far from bulletproof, but if an attacker does gain physical access to your site, you may be able to throw up another hurdle to limit their ability to access your network with any of their own devices. Both wired and wireless networks can use MAC filtering to enable you to blacklist or whitelist devices based on their MAC address.

Use a blacklist to block specific computers, adding their MAC addresses to the ranks of the undesired. You can use a whitelist to pre-specify the only MAC addresses allowed access. I say this isn't bulletproof because a savvy attacker can spoof an address (they'll have a much easier time sniffing a valid Wi-Fi MAC address than a wired one, though) from another device accessing the network.

Keeping devices you don't control out of your network is a big win! If the attacker can't gain access to your network with one of their own devices (which they have probably preloaded with tools for attacking your systems or network), they'll have to resort to breaking into one of your devices to do the heavy lifting.

MAC addresses aren't the only way to filter traffic to and from your network. IP addresses can also be used to help keep unwanted traffic from entering or leaving your network. Like MAC filtering, IP filtering is a tool often available with routers and firewalls. IP filtering enables an administrator to set rules about whether packets should be sent or received based on the source or destination IP address. IP filtering isn't a surefire solution to security issues, but it can be an extra hurdle in the same way MAC filtering is.

Authentication

Security requires properly implemented authentication, which means in essence how the computer determines who can or should access it and, once accessed, what that user can do. A computer can authenticate users through software or hardware, or a combination of both.

You can categorize ways to authenticate into three broad areas: knowledge factors, ownership factors, and inherence factors. You read about multifactor authentication in detail in Chapter 25 in the context of mobile device security. It works the same way when securing a desktop computer, a laptop, a server, or a building. There's no reason to rehash it here. The only thing to add is that many organizations use two-factor authentication. An example is a key fob that generates a numeric key. A user authenticates by entering his or her username and password (something the user knows) and enters the key (something the user has) when prompted. Another popular method of authentication is to use an authenticator application. An authenticator application adds an additional layer of security similar to many multifactor authentication methods, by generating some form of key or password to be entered in conjunction with standard login credentials.

EXAM TIP   The CompTIA A+ 1102 exam will quiz you on multifactor and two-factor authentication. This applies to all computing devices.

Software Authentication: Proper Passwords  It's still rather shocking to me to power up a friend's computer and go straight to his or her desktop, or with my married-with-kids friends, to click one of the parents' user account icons and not be prompted for a password. This is just wrong! I'm always tempted to assign passwords right then and there---and not tell them the passwords, of course---so they'll see the error of their ways when they try to log on next. I don't do it but always try to explain gently the importance of good passwords.

You know about passwords from Chapter 13, so I won't belabor the point here. Suffice it to say that you must require that your users have proper passwords. Don't let them write passwords down or tape them to the underside of their mouse pads either!

It's not just access to Windows that you need to think about. There's always the temptation for people to do other mean things, such as change CMOS settings, open up the case, and even steal hard drives. Any of these actions renders the computer inoperable to the casual user until a tech can undo the damage or replace components. All modern CMOS setup utilities come with a number of tools to protect your computer, such as drive lock, intrusion detection, and of course system access BIOS/UEFI passwords such as the one shown in Figure 27-4. Refer to Chapter 5 to refresh yourself on what you can do at a BIOS level to protect your computer.

Figure 27-4  BIOS/UEFI access password request

Hardware Authentication  Gates, doors, and computers can make use of badge readers, smart card readers, and biometric scanners to authenticate users with more authority than mere passwords. Smart cards are credit card--sized cards with circuitry that can identify the bearer of the card. Smart cards are relatively common for tasks such as authenticating users for mass transit systems but are fairly uncommon in computers. Figure 27-5 shows a smart card and keyboard combination.

Figure 27-5  Keyboard-mounted smart card reader being used for a commercial application (photo courtesy of Cherry Corp.)

Security tokens are devices that store some unique information that the user carries on their person. They may be digital certificates, passwords, or biometric data. They may also store an RSA token. RSA tokens are random-number generators that are used with usernames and passwords to ensure extra security. Most security hard tokens come in the form of key fobs, as shown in Figure 27-6.

Figure 27-6  RSA key fob (photo courtesy of EMC Corp.)

Apps and services that use security codes usually prompt you to enter the code after you supply your username and password. Some offer to send you a code via e-mail, text message (via short message service [SMS]), or voice call. Figure 27-7 shows PayPal prompting me for a code from my authenticator app (left) and my bank offering to send me a security code (right).

Figure 27-7  Prompt for a security code (left) and offer to send a security code (right)

An authenticator application is a software security token (a soft token) that turns a mobile device into a security token. As shown in Figure 27-8, these apps can generate a security code like the one on the RSA key fob shown previously in Figure 27-6. Hardware tokens are more secure than soft tokens and send-a-code options.

Figure 27-8  Getting a security code from my authenticator app

People can guess or discover passwords, but it's a lot harder to forge someone's fingerprints. The Apple keyboard shown in Figure 27-9 authenticates users on a local machine by using a fingerprint scanner. Other devices that will do the trick are key fobs, retina scanners, and palmprint scanners. Devices that require some sort of physical, flesh-and-blood authentication are called biometric scanners or biometric locks. In some rare cases, an organization may decide that fingerprints just aren't enough authentication. In these cases, you may find the much newer palmprint reader. Palmprint is a bit of a misnomer, as what the scanner is actually doing is using infrared light to map the unique structure of veins in your palm. Advantages of a palmprint reader include being much more difficult, if not impossible, to fake, and the fact that it requires a person to have blood flow, which is a built-in guarantee that the person being authenticated is alive. The main disadvantage is cost, with palmprint readers often costing significantly more than their fingerprint scanning counterparts.

Figure 27-9  Apple TouchID fingerprint reader on a MacBook Air

Clever manufacturers have developed key fobs and smart cards that use RFID to transmit authentication information so users don't have to insert something into a computer or card reader. The Privaris plusID combines, for example, a biometric fingerprint fob with an RFID tag that makes security as easy as opening a garage door remotely!

Retina scanners loom large in media as a form of biometric security, where you place your eye up to a scanning device. While retina scanners do exist, I have been in hundreds of high-security facilities and have only seen one retina scanner in operation in almost 30 years as a tech. Figure 27-10 shows about the only image of a retina scanner in operation you'll ever encounter.

Figure 27-10  Retina scanner in Half-Life 2

Current smartphones and tablets use full facial recognition for identification and authentication, although they also use passcodes for when the recognition fails. Figure 27-11 shows a user logging in to an Apple iPhone via facial recognition. (Note the open lock. Hard to show the process in action because it happens so fast!)

Figure 27-11  Unlocking an iPhone via facial recognition

Users and Groups

Windows uses user accounts and groups as the bedrock of access control. A user account is assigned to a group, such as Users, Power Users, or Administrators, and by association gets certain permissions on the computer. Using NTFS enables the highest level of control over data resources.

Assigning users to groups is a great first step in controlling a local machine, but this feature really shines in a networked environment. Let's take a look.

NOTE   The file system on a hard drive matters a lot when it comes to security. On modern systems, the file system on the boot drive has support for an access control list (ACL), a rich form of user and groups permissions. But this security only extends to drives/cards formatted with modern file systems such as NTFS, APFS, HFS+, and ext3/4. If you copy a file to a drive/card formatted with exFAT or the older FAT32, such as many cameras and USB flash drives use, the OS will strip all permissions and the file will be available for anyone to read!

Access to user accounts should be restricted to the assigned individuals, and those who configure the permissions to those accounts must follow the principle of least privilege: accounts should have permission to access only the resources they need and no more. Tight control of user accounts is critical to preventing unauthorized access. Disabling unused accounts is an important part of this strategy, but good user account management goes far deeper than that.

Groups are a great way to achieve increased complexity without increasing the administrative burden on network administrators, because all operating systems combine permissions. When a user is a member of more than one group, which permissions does that user have with respect to any particular resource? In all operating systems, the permissions of the groups are combined, and the result is what you call the effective permissions the user has to access a resource. As an example, if Rita is a member of the Sales group, which has List Folder Contents permission to a folder, and she is also a member of the Managers group, which has Read and Execute permissions to the same folder, Rita will have both List Folder Contents and Read and Execute permissions to that folder.

Watch out for default user accounts and groups---they can become secret backdoors to your network! All network operating systems have a default Everyone group that can be used to sneak into shared resources easily. This Everyone group, as its name implies, literally includes anyone who connects to that resource. Windows gives full control to the Everyone group by default, for example, so make sure you know to lock this down! The other scary one is the Guest account. The Guest account is the only way to access a system without a username and password. Unless you have a compelling reason to provide guest access, you should always make sure the Guest account is disabled.

All of the default groups---Everyone, Guest, Users---define broad groups of users. Never use them unless you intend to permit all of those folks access to a resource. If you use one of the default groups, remember to configure it with the proper permissions to prevent users from doing things you don't want them to do with a shared resource!

NOTE   You can use directory permissions to limit access to sensitive information on a shared file server, protect user-specific files from snooping by other users on a multiuser system, and protect the system's own software from being compromised by any scripts or programs the user runs. The job doesn't end here, though! Anyone with physical access to a drive can ignore your controls. Use full-disk data-at-rest encryption to protect data (data in storage, not in use or moving around the network).

Security Policies

We've already discussed policies in Chapters 13 and 19, but let's do a quick review and then see how we put it all together to help secure a network. Although permissions control how users access shared resources, there are other functions you should control that are outside the scope of resources. For example, do you want users to be able to access a command prompt on their Windows system? Do you want users to be able to install software? Would you like to control what systems a user can log on to or at what time of day a user can log on? All network operating systems provide you with some capability to control these and literally hundreds of other security parameters, under what Windows calls policies. I like to think of policies as permissions for activities, as opposed to true permissions, which control access to resources.

A policy is usually applied to a user account, a computer, or a group. Let's use the example of a network composed of Windows systems with a Windows Server. Every Windows client has its own local policies program, which enables policies to be placed on that system only. Figure 27-12 shows the tool you use to set local policies on an individual system, called Local Security Policy, being used to deny the Guest account the capability to log on locally.

Figure 27-12  Local Security Policy

Local policies work great for individual systems, but they can be a pain to configure if you want to apply the same settings to more than one PC on your network. If you want to apply policy settings en masse, you need to step up to features of domain-based Windows Active Directory. You can use organizational units (OUs) that organize users and devices logically into a folder-like hierarchy; then exercise deity-like (Microsoft prefers the term granular) control to apply a different group policy to the network clients in each unit.

One important thing to keep in mind about Active Directory group policies is that they supersede local policies. For example, if you have a local policy in place that allows a specific user to install third-party software, then set a group policy for the domain that prevents all users from doing so, the user won't be able to install the software. If you run into a situation like this, you'll find that the gpupdate and gpresult commands we discussed back in Chapter 15 are helpful. They're a quick way to double-check which group policies are applied to which users and make changes if there's a conflict. Now let me explain group policy a little more and show you some examples of what it can do.

EXAM TIP   Group policy changes may not immediately apply to all systems. Windows will fetch the group policy when the system boots or someone logs in. It will also refresh the policy from time to time while running, though some policy changes won't apply without a reboot anyways. You can run gpupdate/force from the command line to update group policy for a specific computer immediately.

Want to set the default wallpaper for every PC in your domain? Group policy can do that. Want to make certain tools inaccessible to everyone but authorized users? Group policy can do that, too. Want to control access to the Internet, redirect home folders, run scripts, deploy software, or just remind folks that unauthorized access to the network will get them nowhere fast? Group policy is the answer. Figure 27-13 shows group policy; I'm about to change the default title on every instance of Internet Explorer on every computer in my domain!

Figure 27-13  Using group policy to make IE title say "Provided by Mike!"

That's just one simple example of the settings you can configure by using group policy. You can apply literally hundreds of tweaks through group policy, from the great to the small, but don't worry too much about familiarizing yourself with each and every one. Group policy settings are a big topic on most of the Microsoft certification tracks, but for the purposes of the CompTIA A+ exams, you simply have to be comfortable with the concept behind group policy.

Although I could never list every possible policy you can enable on a Windows system, here's a list of some commonly used ones:

-   Prevent Registry Edits If you try to edit the Registry, you get a failure message.

-   Prevent Access to the Command Prompt Keeps users from getting to the command prompt by turning off the Run command and the Command Prompt shortcut.

-   Log On Locally Defines who may log on to the system locally.

-   Shut Down System Defines who may shut down the system.

-   Minimum Password Length Forces a minimum password length.

-   Account Lockout Threshold Sets the maximum number of logon attempts a person can make before being locked out of the account.

-   Disable Windows Installer Prevents users from installing software.

-   Printer Browsing Enables users to browse for printers on the network, as opposed to using only assigned printers.

Although the CompTIA A+ exams don't expect you to know how to implement policies on any type of network, you are expected to understand that policies exist, especially on Windows networks, and that they can do amazing things to control what users can do on their systems. If you ever try to get to a command prompt on a Windows system only to discover the Run command is dimmed, blame it on a policy, not the computer!

EXAM TIP   Account management security policy best practices dictate that you should implement restrictive user permissions, login time restrictions, account lockout based on failed attempts, disable guest accounts, and disable the operating system's built-in AutoRun or AutoPlay features. Finally, you should always change default system usernames and passwords where possible.

Network Security

Networks are under threat from the outside as well, so this section looks at issues involving Internet-borne attacks, firewalls, and wireless networking. This content is the security bread and butter for a CompTIA A+ technician, so you need to understand the concepts and procedures and be able to implement them properly.

Malicious Software

The beauty of the Internet is the ease of accessing resources just about anywhere on the globe, all from the comfort of your favorite chair. This connection, however, runs both ways, and people from all over the world can potentially access your computer from the comfort of their evil lairs. The Internet is awash with malicious software that is, even at this moment, trying to infect your systems.

The term malware defines any program or code that's designed to do something on a system or network that you don't want done. Malware comes in quite a variety of guises, such as viruses, worms, ransomware, spyware, Trojan horses, keyloggers, cryptojacking, and rootkits. Let's examine all these forms of malware, look at what they do to infected systems, and then examine how these nasties get onto your machines in the first place.

Forms of Malware

Malware has been pestering PC users since the 1980s and has evolved into many forms over the years. From the classic boot sector viruses of the '90s to the more recent threats of ransomware and attacks on critical infrastructure, malware is an ever-changing threat to your users and data. To better understand these threats, you need to understand the different forms that malware can take.

Virus  A virus is a program that has two jobs: to replicate and to activate. Replication means it makes copies of itself, by injecting itself as extra code added to the end of executable programs, or by hiding out in a drive's boot sector. Boot sector viruses can be particularly nasty because they live inside your system's boot partition and activate their malicious code before the security software is able to start up and prevent it. Activation is when a virus does something like corrupting data or stealing private information. A virus only replicates to other drives, such as thumb drives or optical media. It does not self-replicate across networks. A virus needs human action to spread.

Worm  A worm functions similarly to a virus, except it does not need to attach itself to other programs to replicate. It can replicate on its own through networks, or even hardware like Thunderbolt accessories. If the infected computer is on a network, a worm will start scanning the network for other vulnerable systems to infect.

Trojan  A Trojan (named for the Trojan Horse) is a piece of malware that appears or pretends to do one thing while, at the same time, it does something evil. A Trojan horse may be a game, like poker, or ironically, a fake security program. The sky is the limit. Once installed, a Trojan horse can have a hold on the system as tenacious as any virus or worm; a key difference is that installed Trojan horses do not replicate.

Keylogger  Keylogger malware does pretty much what you might imagine, recording the user's keystrokes and making that information available to the programmer. You'll find keylogging functions as part of other malware as well. Keyloggers are not solely evil; a lot of parental control tools use keyloggers.

Rootkit  For malware to succeed, it often needs to come up with some method to hide itself. As awareness of malware has grown, anti-malware programs make it harder to find new locations on a computer to hide malware. A rootkit is a program that takes advantage of very low-level operating system functions to hide itself from all but the most aggressive of anti-malware tools. Worse, a rootkit, by definition, gains privileged access to the computer. Rootkits can strike operating systems, hypervisors, and even firmware (including hard drives and accessories . . . yikes!).

The most infamous rootkit appeared a while back as an antipiracy attempt by Sony on its music CDs. Unfortunately for the media giant, the rootkit software installed when you played a music CD and opened a backdoor that could be used maliciously.

Cryptominers  Malicious actors are often motivated by financial gain, so sometimes, they try to kill two birds with one stone by installing malware that can mine cryptocurrency. These cryptominers take control of a computer's hardware resources and use them to mine cryptocurrency, which is then deposited into a crypto wallet belonging to the attacker. A telltale sign a system is infected with this kind of malware may be inexplicably high GPU or CPU utilization. There are other problems that can lead to excessive hardware utilization, but if you see it, it might be a good idea to check for cryptominer malware.

Behavior

Knowing what form the malware takes is all well and good, but what really matters is how "mal" the malware will be when it's running rampant on a system. To get things started, let's dive into an old favorite: spyware.

Spyware  Spyware---malicious software, generally installed without your knowledge---can use your computer's resources to run distributed computing applications, capture keystrokes to steal passwords, or worse. Classic spyware often sneaks onto systems by being bundled with legitimate software---software that functions correctly and provides some form of benefit to the user. What kind of benefit? Way back in 2005, Movieland (otherwise known as Movieland.com and Popcorn.net) released a "handy" movie download service. They didn't tell users, of course, that everyone who installed the software was "automatically enrolled" in a three-day trial. If you didn't cancel the "trial," a pop-up window filled your screen demanding you pay them for the service that you never signed up for. The worst part, however, was that you couldn't uninstall the application completely. The uninstaller redirected users to a Web page demanding money again. (Movieland was shut down in 2007.)

For another classic example, look at Figure 27-14: the dialog box asks the user if she trusts the Gator Corporation (a well-known spyware producer from ages ago). Because everyone eventually knew not to trust Gator, they would click No, and the company faded away.

Figure 27-14  Classic Gator Corporation's acknowledgment warning

If Movieland was a problem back in 2005, what are the big spyware applications today? Unfortunately, I can't tell you---not because it's a secret, but because we don't know about them yet. You'll probably only run into spyware these days on the CompTIA A+ 1102 exam.

Ransomware  As bad as spyware can be, at least you still have access to your data. Ransomware, on the other hand, encrypts all the data it can gain access to on a system. To top it off, many versions of ransomware can even encrypt data on mapped network drives!

EXAM TIP   Know the various types of malware, including viruses, worms, Trojan horses, keyloggers, rootkits, cryptominers, spyware, and ransomware.

Once it has locked up all your data, the ransomware application pops up a message asking for money (often bitcoins) to decrypt your data (see Figure 27-15). Also, to encourage a faster payment, this ransom is presented with a timer that, when it reaches 0, triggers deletion of the encryption keys, leaving you with a drive full of scrambled data. In some particularly dastardly cases, the ransomware doesn't actually have the ability to decrypt built in, and will just leave your drives encrypted or wipe the data altogether when that clock hits 0.

Figure 27-15  Clean computer (top) and same computer (bottom) encrypted by Black Basta group malware (Courtesy of National Cyber Labs)

A Bot on the Net Full of Zombies  Another type of malware I want to talk about is the botnet ("bot" as in robot, get it!). As we touched on when we discussed Denial of Service attacks, a botnet, as "net" in its name implies, isn't a single type of malware, but rather, a network of infected computers (zombies) under the control of a single person or group. Botnets can be massive, easily growing into the millions of zombies for the largest networks.

With that many machines under their control, botnet operators have command of massive computing and network resources. Some of the most common uses of botnets are sending spam or launching distributed denial of service attacks. If you've ever wondered how spammers and hackers pay for all that bandwidth, they don't! They use the bandwidth of millions of zombie machines spread all around the world, from grandma's e-mail machine to hacked Web servers.

Spam is but one use of a botnet. The criminals who run these networks also use all that collective power to launch a DDoS attack against companies and governments and demand a ransom to call off the attack.

Malware Signs and Symptoms

If your PC has been infected by malware, you'll bump into some strange things before you can even run an anti-malware scan. Like a medical condition, malware causes unusual symptoms that should stand out from your everyday computer use. You need to become a PC physician and understand what each of these symptoms means.

Malware's biggest strength is its flexibility: it can look like anything. In fact, a lot of malware attacks can feel like normal PC "wonkiness"---momentary slowdowns, random one-time crashes, and so on. Knowing when a weird application crash is actually a malware attack is half the battle.

Slow performance in a PC can mean you're running too many applications at once, or that you've been hit with malware. Applications can crash at random, even if you don't have too many loaded. How do you tell the difference? In this case, it's the frequency. If it's happening a lot, even when all of your applications are closed, you've got a problem. This goes for frequent lockups, too---whether it seems to be PC- or OS-based lockups. If Windows starts misbehaving (more than usual), run your anti-malware application right away.

Malware, however, doesn't always jump out at you with big system crashes. Some malware tries to rename system files, change file permissions, or hide files completely. You might start getting e-mail messages from colleagues or friends questioning a message "you" sent to them that seemed spammy. You might get automated replies from unknown sent e-mail that you know you didn't send. An increase in desktop alerts that don't seem to have a legitimate cause, or unwanted notifications within the OS may also be signs that it's time to check for malware. You may even get false alerts regarding your computer's antivirus protection. Most of these issues are easily caught by a regular anti-malware scan, so as long as you remain vigilant, you'll be okay.

NOTE   While it's not necessarily a malware attack, watch out for hijacked e-mail accounts belonging either to you or to someone you know. Hackers can hit both e-mail clients and Webmail users. If you start receiving some fishy (or phishy) e-mail messages, change your Webmail username and password and scan your PC for malware.

Some malware even fights back, defending itself from your many attempts to remove it. If your Windows Update feature stops working, preventing you from patching your PC, you've got malware. (CompTIA speak: OS update failures.) If other tools and utilities throw up an "Access Denied" road block, you've got malware. If you lose all Internet connectivity, either the malware is stopping you or the process of removing the malware broke your connection. (CompTIA refers to this as being unable to access the network, which seems very polite.) In this case, you might need to reconfigure your Internet connection: reinstall your NIC and its drivers, reboot your router, and so on.

Even your browser and anti-malware applications can turn against you. If you type in one Web address and end up at a different site than you anticipated, this is known as a browser redirection and it means that a malware infection might have overwritten your hosts file. The hosts file overrules any DNS settings and can redirect your browser to whatever site the malware adds to the file. Most browser redirections point you to phishing scams or Web sites full of free downloads (that are, of course, covered in even more malware). In fact, some free anti-malware applications are actually malware---what techs call rogue anti-malware programs. You can avoid these rogue applications by sticking to the recommended lists of anti-malware software found online at reputable tech sites, like Ars Technica, Tom's Hardware, Anandtech, and others. Random/frequent pop-ups can be another annoying sign that your system is infected with some form of malware. Pop-up blocking has become fairly effective over the years, so if you've already ruled out the possibility that the browser isn't up to date or that the pop-up blocker is off, it may be time to start looking for malware.

Watch for security alerts in Windows, either from Windows' built-in security tools or from your third-party anti-malware program. Windows built-in tools alert you via the Action Center or the Windows Defender Security Center (Windows 10/11). The notification in Figure 27-16 is prompting us to activate Defender Antivirus. You don't configure much here; it just tells you whether or not you are protected. The Action Center or Security Center will pop up a notification in the notification area whenever Windows detects a problem.

Figure 27-16  Notification to activate Defender Antivirus in Windows 11

Malware Prevention and Recovery

The only way to permanently protect your PC from malware is to disconnect it from the Internet and never permit any potentially infected software to touch your precious computer. Because neither scenario is likely these days, you need to use specialized anti-malware programs to help stave off the inevitable assaults. Even with the best anti-malware tools, there are times when malware still manages to strike your computer. When you discover infected systems, you need to know how to stop the spread of the malware to other computers, how to fix infected computers, and how to remediate (restore) the system as close to its original state as possible.

Dealing with Malware

You can deal with malware in several ways: anti-malware programs, training and awareness, patch/update management, and remediation.

At the very least, every computer should run an anti-malware program. If possible, add an appliance that runs anti-malware programs against incoming data from your network. Also remember that an anti-malware program is only as good as its updates---keep everyone's definition file (explained a bit later) up to date with, literally, nightly updates! Users must be trained to look for suspicious ads, programs, and pop-ups, and understand that they must not click these things. The more you teach users about malware, the more aware they'll be of potential threats. Your organization should have policies and procedures in place so everyone knows what to do if they encounter malware. Finally, a good tech maintains proper incident response records to see if any pattern to attacks emerges. He or she can then adjust policies and procedures to mitigate these attacks.

NOTE   One of the most important malware mitigation procedures is to keep systems under your control patched and up to date through proper patch management. Microsoft, Apple, and the Linux maintainers do a very good job of putting out bug fixes and patches as soon as problems occur. If your systems aren't set up to update automatically, then perform manual updates regularly.

Anti-Malware Programs

An anti-malware program such as a classic antivirus program protects your PC in two ways. It can be both sword and shield, working in an active seek-and-destroy mode and in a passive sentry mode. When ordered to seek and destroy, the program scans the computer's boot sector and files for viruses and, if it finds any, presents you with the available options for removing or disabling them. Antivirus programs can also operate as virus shields that passively monitor a computer's activity, checking for viruses only when certain events occur, such as a program execution or file download.

NOTE   The term antivirus (and antispyware, or anti-anything) is becoming obsolete. Viruses are only a small component of the many types of malware. Many people continue to use the term as a synonym for anti-malware.

Antivirus programs use different techniques to combat different types of viruses. They detect boot sector viruses simply by comparing the drive's boot sector to a standard boot sector. This works because most boot sectors are basically the same. Some antivirus programs make a backup copy of the boot sector. If they detect a virus, the programs use that backup copy to replace the infected boot sector. Executable viruses are a little more difficult to find because they can be on any file in the drive. To detect executable viruses, the antivirus program uses a library of signatures. A signature is the code pattern of a known virus. The antivirus program compares an executable file to its library of signatures. There have been instances where a perfectly clean program coincidentally held a virus signature. Usually, the antivirus program's creator provides a patch to prevent further alarms.

Windows comes with Windows Defender (simply called Virus & threat protection in Windows 10/11, as shown in Figure 27-17), a fine tool for catching most malware, but it's not perfect. You can also supplement Windows Defender with a second malware removal program. My personal favorite is Malwarebytes.

Figure 27-17  Windows 11 Virus & threat protection

These applications work exactly as advertised. They detect and delete malware of all sorts---hidden files and folders, cookies, Registry keys and values, you name it. Malwarebytes is free for personal use. Figure 27-18 shows Malwarebytes in action.

Figure 27-18  Malwarebytes

Try This!

Malwarebytes

If you haven't done this already, do it now. Go to https://www.malwarebytes.com and download the latest copy of Malwarebytes. Install it on your computer and run it. Did it find any malware that slipped in past your defenses?

Now that you understand the types of viruses and how antivirus programs try to protect against them, let's review a few terms that are often used to describe virus traits.

SIM   Check out the excellent Challenge! sim, "Fixing Viruses," in the Chapter 27 sims over at https://www.totalsem.com/110X.

Polymorphic/Polymorphs  A polymorphic virus, often shortened to a polymorph, attempts to change its signature to prevent detection by antivirus programs, usually by continually scrambling a bit of useless code. Fortunately, the scrambling code itself can be identified and used as the signature---once the antivirus makers become aware of the virus. One technique used to combat unknown polymorphs is to have the antivirus program create a checksum on every file in the drive. A checksum in this context is a number generated by the software based on the contents of the file rather than the name, date, or size of that file. The algorithms for creating these checksums vary among different antivirus programs (they are also usually kept secret to help prevent virus makers from coming up with ways to beat them). Every time a program is run, the antivirus program calculates a new checksum and compares it with the earlier calculation. If the checksums are different, it is a sure sign of a virus.

Stealth  The term "stealth" is more of a concept than an actual virus function. Most stealth virus programs are boot sector viruses that use various methods to hide from antivirus software. The AntiEXE stealth virus hooks on to a little-known but often-used software interrupt, for example, running only when that interrupt runs. Others make copies of innocent-looking files.

User Education Regarding Common Threats

A powerful tool to prevent malware attacks and to reduce the impact of malware attacks when they happen is to educate your end users. Teach users to be cautious of incoming e-mail they don't clearly recognize and to never click on an attachment or URL in an e-mail unless they are 100 percent certain of the source. With the rise in ransomware attacks over time, good anti-phishing training has become an absolutely essential tool in the IT security toolbox. Anti-phishing training involves teaching users how to recognize and critically examine incoming e-mails to better avoid falling prey to phishing attempts. Anti-phishing training has benefits that extend beyond the confines of the organization, as phishing attacks happen in SOHO environments as well. Regardless of where or why a person is using their device, this is some very useful education.

Explain the dangers of going to questionable Web sites to your users and teach them how to react when they see questionable actions take place. All Web browsers have built-in attack site warnings like the one shown in Figure 27-19.

Figure 27-19  Attack site warning

Nobody wants their systems infected with malware. Users are motivated and happy when you give them the skills necessary to protect themselves. The bottom line is that educated and aware users will make your life a lot easier.

Malware Prevention Tips

The secret to preventing damage from a malicious software attack is to keep from getting malware on your system in the first place. One way to do this is with a variation on traditional DNS---secure DNS. Secure DNS can describe software or a remote DNS provider that implements some additional filtering to block your devices from visiting all kinds of malicious Web sites.

If you can't keep the malware from reaching your system, a good next step is catching it on the way in the door. All good antivirus/anti-malware programs (like the built-in Windows Defender Antivirus) include a virus shield that scans e-mail, downloads, running programs, and so on automatically (see Figure 27-20).

Figure 27-20  A Windows 10 virus shield (Defender Antivirus) in action

Use your antivirus shield. It is also a good idea to scan PCs daily for possible virus attacks. Last but not least, know the source of any software before you load it. Only install apps from trusted sources, such as the manufacturer's Web site, or well-known app stores like Valve's Steam service. Avoid untrusted software sources, like free registry cleaners from some support domain, at all costs.

Keep your antivirus and anti-malware programs (including Defender Antivirus) updated. New viruses and other malware appear daily, and your programs need to know about them. The list of virus signatures your antivirus program can recognize, for example, is called the definition file, and updated definitions play a critical role in keeping the latest malware out of your system. Fortunately, most antivirus programs update themselves automatically. Further, you should periodically update the core anti-malware software programming---called the engine---to employ the latest refinements the developers have included.

Boot Media Anti-Malware Tools

If you run anti-malware software and your computer still gets infected, especially after a reboot, you need a more serious anti-malware tool. Many anti-malware companies provide a bootable optical disc or USB flash drive (or show you how to make one) that enables you to boot from a known-clean OS and run the same anti-malware software, but this time not corrupted by the malware on your system.

Malware Recovery Tips

When the inevitable happens and either your computer or one of your user's computers gets infected by malware such as a computer virus, you need to follow certain steps to stop the problem from spreading and get the computer back up safely into service. The CompTIA A+ 1102 exam outlines the following multistep process as the best practice procedures for malware removal:

1\.   Investigate and verify malware symptoms.

2\.   Quarantine infected systems.

3\.   Disable System Restore in Windows.

4\.   Remediate infected systems.

A.   Update anti-malware software.

B.   Scanning and removal techniques (e.g., Safe Mode, Preinstallation Environment).

5\.   Schedule scans and run updates.

6\.   Enable System Restore and create a restore point in Windows.

7\.   Educate the end user.

EXAM TIP   In addition to this malware removal process, the CompTIA A+ 1102 objectives also mention OS reinstallation as another way to make sure your system is malware-free---just restore a full system backup (in Windows, you can take or restore one with the Backup and Restore utility). There are hurdles to using this approach.

You must have space to store one or more full backups, plan far enough ahead to have one or more recent backup available, know at least one is malware-free, and be prepared to either back up user files/data separately or lose any created/modified since the last backup. You won't always have this option, but a good way to get started is to back up user files and data separately and take a full backup of the system itself once you have all of the software you need installed and configured. If you attempt to reinstall your OS from a backup and you find that your system is still infected, it may be time to try what is known as a clean install, which means just starting from a fresh copy of Windows and treating it like a new device. This has disadvantages as well, since it means starting from scratch with your system's apps and data. In some cases, this may be your only choice, but it isn't always ideal.

Recognize and Quarantine  The first step is to identify and recognize that a potential malware outbreak has occurred. If you're monitoring network traffic and one computer starts spewing e-mail, that's a good indicator of malware. Or users might complain that a computer that was running snappily the day before seems very sluggish.

Many networks employ software such as the open source PacketFence that automatically monitors network traffic and can cut a machine off the network if that machine starts sending suspicious packets. You can also quarantine a computer manually by disconnecting the network cable. Once you're sure the machine isn't capable of infecting others, you're ready to find the virus or other malware and get rid of it.

At this point, you should disable System Restore. If you make any changes going forward, you don't want the virus to be included in any saved restore points. To turn off System Restore in Windows, open the Control Panel and then the System applet. Click the System protection link to open the System Properties window with the System Protection tab displayed. In the Protection Settings section, select a drive and click Configure. In the System Protection dialog box that opens, select Turn off system protection. Repeat the procedure for each hard drive on the system.

Search and Destroy  Once you've isolated the infected computer (or computers), you need to get to a safe boot environment and run anti-malware software. You can try the Windows Recovery Environment in Windows 10/11, because it doesn't require anything but a reboot. If that doesn't work, or you suspect a boot sector virus, you need to turn to an external bootable source, such as a bootable optical disc or USB flash drive.

Get into the habit of keeping around a bootable anti-malware flash drive or optical media. If you suspect a virus or other malware, use the boot media, even if your anti-malware program claims to have eliminated the problem. Turn off the PC and reboot it from the anti-malware disc or flash drive (you might have to change CMOS settings to boot to optical or USB media). This will put you in a clean boot environment that you know is free from any boot sector viruses. If you only support fairly recent computers, you will likely be booting to a USB flash drive, so you can put a boot environment on a thumb drive for even faster start-up speeds.

You have several options for creating the bootable optical disc or flash drive. First, some antivirus software comes in a bootable version. Second, you can download a copy of Linux that offers a live USB or DVD option such as Ubuntu. With a live bootable device, you boot to the device and install a complete working copy of the operating system into RAM, never touching or accessing the hard drive, to give you full Internet-ready access so you can reach the many online anti-malware sites you'll need for access to anti-malware tools.

Finally, you can download and burn a copy of the Ultimate Boot CD. Don't worry, you can use it with a USB drive. It comes stocked with several antivirus and anti-malware programs, so you won't need any other tool. Find it at https://www.ultimatebootcd.com. The only downside is that the anti-malware engines will quickly be out of date, as will their malware libraries.

Once you get to a boot environment, update your anti-malware software and then run its most comprehensive scan. Then check all removable media that were exposed to the system, and any other machine that might have received data from the system or that is networked to the cleaned machine. A virus or other malicious program can often lie dormant for months before anyone knows of its presence.

E-mail is still a common source of viruses, and opening infected e-mails is a common way to get infected. Viewing an e-mail in a preview window opens the e-mail message and exposes your computer to some viruses. Download files only from sites you know to be safe and avoid the less reputable corners of the Internet, the most likely places to pick up computer infections.

EXAM TIP   CompTIA considers the process of removing a virus part of the remediation step. Since you can't remediate a PC until after a virus is gone, I've laid out the steps as you see here.

Remediate  Malware infections can do a lot of damage to a system, especially to sensitive files needed to load Windows, so you might need to remediate formerly infected systems after cleaning off the drive or drives. Remediation simply means that you fix things the virus or other malware harmed. This can mean replacing corrupted Windows Registry files or even startup files.

If you can't start Windows after the malware scan is finished, you need to boot to the Windows Preinstallation Environment and use the Windows Recovery Environment/System Recovery Options.

With the Windows Recovery Environment (covered in detail in Chapter 16), you have access to more repair tools, such as Startup Repair, System Restore, System Image Recovery, Refresh, and Command Prompt (see Figure 27-21). Run the appropriate option for the situation and you should have the machine properly remediated in a jiffy.

Figure 27-21  System Recovery Options

EXAM TIP   Remember to re-enable System Restore and create a new restore point once the system has been repaired. Be aware that you may see recovery environment referred to as recovery mode on the exam, so don't let that throw you off.

Educate End Users  The best way to keep from having to deal with malware is education. It's your job as the IT person to talk to your users, especially the ones whose systems you've just spent an hour ridding of nasties, about how to avoid these programs. Show them samples of dangerous e-mails they should not open, Web sites to avoid, and the types of programs they should not install and use on the network. Any user who understands the risks of questionable actions on their computers will usually do the right thing and stay away from malware.

Finally, have your users run antivirus and antispyware programs regularly. Schedule them while interfacing with the user so you know it will happen.

1101

Firewalls

Much as anti-malware programs are essential tools in the fight against malicious programs on the Internet, firewalls are devices or software that protect an internal network from unauthorized access to and from the Internet at large. Firewalls use a number of methods to protect networks, such as hiding IP addresses and blocking TCP/IP ports.

A typical network uses one of two types of firewalls: hardware firewalls, often built into routers, and software firewalls that run on your computers. Both types of firewall protect your computer and your network. You also run them at the same time. Let's look at both a typical SOHO router's firewall features and your computer's software firewall to see how they protect your network and your computers.

Hardware Firewall Settings

Most SOHO networks use a hardware firewall, often as a feature built into a router like the ASUS model shown in Figure 27-22. A hardware firewall protects a LAN from outside threats by filtering the packets before they reach your internal machines, which you learned about back in Chapter 21. Routers, however, have a few other tricks up their sleeves. From the router's browser-based settings screen (see Figure 27-23), you can configure a hardware firewall. Let's walk through a few of the available settings.

Figure 27-22  ASUS router as a firewall

Figure 27-23  Default Web interface

A hardware firewall watches for and stops many common threats---all you have to do is turn it on (see Figure 27-24). Hardware firewalls use Stateful Packet Inspection (SPI) to inspect each incoming packet individually. SPI also blocks any incoming traffic that isn't in response to your outgoing traffic. You can even disable unused ports entirely, blocking all traffic in or out. But what if you want to allow outside users access to a Web server on the LAN? Because Network Address Translation (NAT) hides the true IP address of that system (as described in Chapter 21), you'll need a way to allow incoming traffic past the router/firewall and a way to redirect that traffic to the right PC.

Figure 27-24  SPI firewall settings with firewalls enabled

Port forwarding/mapping enables you to open a port in the firewall and direct incoming traffic on that port to a specific IP address on your LAN. In the case of the Web server referenced in the previous paragraph, you would open port 80 (for HTTP packets) and instruct the router to send all incoming traffic to the server machine. Figure 27-25 shows port forwarding configured to send all HTTP packets to an internal Web server.

Figure 27-25  Port forwarding

Port forwarding isn't the only way to open ports on a firewall. Port triggering enables you to open an incoming connection to one computer automatically based on a specific outgoing connection. The trigger port defines the outgoing connection, and the destination port defines the incoming connection. If you set the trigger port to 3434 and the destination port to 1234, for example, any outgoing traffic on port 3434 will trigger the router to open port 1234 and send any received data back to the system that sent the original outgoing traffic. Figure 27-26 shows a router set up with port triggering for an Internet Relay Chat (IRC) server.

Figure 27-26  Port triggering

If you want to go beyond port forwarding and port triggering and open every port on a machine, you need a screened subnet. A screened subnet puts systems with the specified IP addresses outside the protection of the firewall, opening all ports and enabling all incoming traffic (see Figure 27-27). If you think this sounds incredibly dangerous, you are right! Any PC inside the screened subnet will be completely exposed to outside attacks. Don't use it!

Figure 27-27  Screened subnet (DMZ) set up on a SOHO router

EXAM TIP   CompTIA uses the term screened subnet in the A+ 1102 exam objectives, so be ready in case you see it on the exam, but on the job, you'll more likely encounter the term demilitarized zone or DMZ (as shown in Figure 27-27).

Software Firewalls

While a hardware firewall does a lot to protect you from outside intruders, you should also use a software firewall, such as the firewalls built into each version of Windows, called (appropriately) Windows Defender Firewall or Windows Defender Firewall with Advanced Security. (Earlier versions of Windows just called the tool(s) Windows Firewall.) Windows Defender Firewall (see Figure 27-28) handles the heavy lifting of port blocking, security logging, and more.

Figure 27-28  Windows 10 Firewall settings

You can configure Windows Defender Firewall via the Windows Defender Firewall applet in Control Panel. Here you can fine-tune port security by setting up exceptions to open individual ports, or adjust application security by adding exceptions to let specific programs and services pass through the firewall. If you wanted to run a Minecraft server (a game that requires an Internet connection), for example, it would need to be on the list of exceptions for your firewall. Most programs you install add themselves to this list automatically, otherwise Windows Defender Firewall prompts you the first time you run it and asks if you want to add the program as an exception.

EXAM TIP   You can also manage Windows Defender Firewall through the Windows Security app. To activate or deactivate the firewall, visit the Firewall & network protection section. To activate, click the Turn on button under each network type you use. To deactivate, click the network name and then toggle Defender Firewall off.

When Microsoft first introduced Windows Firewall, way back in Windows XP, its biggest shortcoming was that it failed to consider that a single PC, especially a portable, might connect to multiple networks. You don't necessarily want the same firewall settings used for both public and private networks. Microsoft developed a way for you to separate trustworthy networks (like the one in your house or at the office) from non-trustworthy networks (like a public Wi-Fi Internet connection at the airport) by including three network types: Domain, Private, and Guest or Public.

-   A Domain network is a Windows network controlled by a Windows domain controller that runs Active Directory Domain Services. In this case, the domain controller itself tells your machine what it can and cannot share. You don't need to do anything when your computer joins a domain.

-   A Private network enables you to share resources, discover other devices, and allow other devices to discover your computer safely.

-   A Guest or Public network prevents your computer from sharing and disables all discovery protocols.

When your computer connects to a network for the first time, Windows will prompt you to choose the network type. Windows 10/11 asks if you want to allow other devices on the network to discover your PC (see Figure 27-29). It will mark the network Private if you answer yes; Public if you answer no. In either case, Windows uses your answer to decide whether to share files and resources or lock them down tight.

Figure 27-29  Windows 10 network options, public or private?

When your computer joins a domain, Windows automatically sets your network location to Domain (unless your domain controller chooses something different, which is unlikely).

When running on a Private (Home or Work) network, Windows enables Network Discovery and File and Printer Sharing as exceptions. When running on a Guest or Public network, Windows disables these exceptions.

EXAM TIP   The Network Discovery setting dictates whether a computer can find other computers or devices on a network, and vice versa. Even with Network Discovery activated, several firewall settings can overrule certain connections.

That's the end of the story if your Windows machine never changes networks, but what about machines (mainly laptops) that hop from one network to another (see Figure 27-30)? In that case, you need different firewall settings for each network the system might encounter.

Figure 27-30  Many machines need more than one network setting.

EXAM TIP   Expect a scenario question on home vs. work vs. public network options on the CompTIA A+ 1102 exam. Just remember that you trust home and work networks, but don't trust public ones.

Once you've picked a network type, you might want to customize the firewall settings further. If you click the Advanced settings option in the Windows Defender Firewall applet, you'll discover a much deeper level of firewall configuration. In fact, it's an entirely different tool called Windows Defender Firewall with Advanced Security (see Figure 27-31). You can also access it directly through the Administrative Tools in Control Panel.

Figure 27-31  Windows Defender Firewall with Advanced Security

From the Windows Defender Firewall with Advanced Security snap-in, you have much more control over how Windows treats exceptions. In the standard Windows Defender Firewall applet, you can only choose a program and make it an exception, giving it permission to pass through the firewall. But programs both send and receive network data, and the basic applet doesn't give you much control over the "inbound" and "outbound" aspect of firewalls. The Windows Defender Firewall with Advanced Security snap-in takes the exceptions concept and expands it to include custom rules for both inbound and outbound data. Figure 27-32 shows the outbound rules for a typical Windows system.

Figure 27-32  Outbound Rules list

A rule always includes at least the following:

-   The name of the program

-   Group: an organizational group that helps sort all the rules

-   The associated profile (All, Domain, Public, Private)

-   Enabled/disabled status

-   Remote and local address

-   Remote and local port number

You can add, remove, and customize any rule to your liking. It quickly gets complicated, so unless you need to set a lot of custom rules, stick to the standard Windows Defender Firewall applet.

Internet Appliances

The discussion of firewalls barely scratches the surface of tools used to secure a large network. While enterprise networking is generally beyond the scope of a CompTIA A+ tech's duties, the CompTIA A+ 1101 objectives cover a few devices critical to modern network security---IDS, IPS, and network taps---plus the concept of unified threat management. Let's take a look.

An intrusion detection system (IDS) is an Internet application that inspects packets, looking for active intrusions. An IDS functions inside the network, watching for threats that a firewall might miss, such as viruses, illegal logon attempts, and other well-known attacks. Plus, because it inspects traffic inside the network, the IDS can discover internal threats, like the activity of a vulnerability scanner smuggled in on a flash drive by a disgruntled worker planning an attack on an internal database server.

An IDS always has some way to let the network administrators know if an attack is taking place: at the very least the attack is logged, but some IDSs offer a pop-up message, an e-mail, or even a text message to an administrator's phone. An IDS can also respond to detected intrusions with action. The IDS can't stop the attack directly, but can request assistance from other devices---like a firewall---that can.

An intrusion prevention system (IPS) is very similar to an IDS, but an IPS sits directly in the flow of network traffic. This active monitoring has a trio of consequences. First, an IPS can stop an attack while it is happening. There's no need to request help from any other devices. Second, the network bandwidth and latency take a hit. Third, if the IPS goes down, the network link might go down too. Depending on the IPS, it can block incoming packets on-the-fly based on IP address, port number, or application type. An IPS might go even further, literally fixing certain packets on-the-fly.

A network tap is a piece of network monitoring hardware (although there are also smaller-scale software options) that sits between devices on the network and copies the traffic between them for later analysis. This comes in handy because, rather than directly interacting with the traffic and potentially interfering with it, a network tap allows the traffic to flow normally. The copied network traffic can then be inspected without the risk of network disruptions. Network taps can also be part of a virtual network, with a lot of additional flexibility in how they are used. Figure 27-33 shows an example of how a network tap might be used.

Figure 27-33  One potential configuration of a network tap

All these network Internet appliances, no matter how advanced and aware they become, are still singular tools in the box used to protect networks. That is why modern dedicated firewall/Internet appliances are built around providing unified threat management (UTM). UTM takes the traditional firewall and packages it with many other security services such as IPS, VPN, load balancing, antivirus, and many other features depending on the make and model. The UTM approach to building network gear helps build robust security deep into the network, protecting what really matters: our data.

1102

Authentication and Encryption

You know that the first step in securing data is authentication, through a username and password. But when you throw in networking, you're suddenly not just a single user sitting in front of a computer and typing. You're accessing a remote resource and sending login information over the Internet. What's to stop someone from intercepting your username and password?

Firewalls do a great job of controlling traffic coming into a network from the Internet and going out of a network to the Internet, but they do nothing to stop interceptor hackers who monitor traffic on the public Internet looking for vulnerabilities. Worse, once a packet is on the Internet itself, anyone with the right equipment can intercept and inspect it. Inspected packets are a cornucopia of passwords, account names, and other tidbits that hackers can use to intrude into your network. Because we can't stop hackers from inspecting these packets, we must turn to encryption to make them unreadable.

Network encryption occurs at many levels and is in no way limited to Internet-based activities. Not only are there many levels of network encryption, but each encryption level also provides multiple standards and options, making encryption one of the most complicated of all networking issues. You need to understand where encryption comes into play, what options are available, and what you can use to protect your network.

Network Authentication

Have you ever considered the process that takes place each time a person types in a username and password to access a network, rather than just a local machine? What happens when this network authentication is requested? If you're thinking that information is sent to a server of some sort to be authenticated, you're right---but do you know how the username and password get to the serving system? That's where encryption becomes important in authentication.

In a local network, authentication and encryption are usually handled by the OS. In today's increasingly interconnected and diverse networking environment, there is a motivation to enable different operating systems to authenticate any client system from any other OS. Modern operating systems such as Windows and macOS use standard authentication encryptions such as MIT's Kerberos, enabling multiple brands of servers to authenticate multiple brands of clients. These LAN authentication methods are usually transparent and work quite nicely, even in mixed networks.

Data Encryption

Encryption methods don't stop at the authentication level. There are a number of ways to encrypt network data as well. The encryption method is dictated to a large degree by what method the communicating systems will connect with. Many networks consist of multiple networks linked together by some sort of private connection, usually some kind of WAN connection such as old T1s or Metro Ethernet. Microsoft's encryption method of choice for this type of network is called IPsec (derived from IP security). IPsec provides transparent encryption between the server and the client.

A virtual private network (VPN) can also use IPsec, but VPNs typically use other encryption methods. Speaking of VPNs, if you're on an untrusted network, you can also protect your network traffic by tunneling it all through a VPN connection. Security-conscious organizations may even require all of their portable devices access the Internet through a VPN connection to one of their home offices.

Application Encryption

When it comes to encryption, even TCP/IP applications can get into the swing of things. The most famous of all application encryptions is the Secure Sockets Layer (SSL) security protocol, which was used to secure Web sites. Everyone uses Transport Layer Security (TLS) in HTTPS (HTTP over TLS) protocol these days. (SSL has been replaced by TLS, in other words.) These protocols make it possible to secure the Web sites people use to make purchases over the Internet. You can identify HTTPS Web sites by the https:// (rather than http://) included in the URL (see Figure 27-34).

Figure 27-34  A secure Web site

NOTE   HTTPS originally meant HTTP over SSL, so the "S" in HTTPS made sense. Most Web sites use the more robust TLS to encrypt connections. The Internet people just quietly switched TLS for SSL, but didn't make a new acronym such as "HTTPT." CompTIA refers to the "S" as standing for "secure," which is a great way to remember the main difference between HTTP and HTTPS.

To make a secure connection, your Web browser and the Web server must encrypt their data. That means there must be a way for both the Web server and your browser to encrypt and decrypt each other's data. To do this, the server sends a public key to your Web browser so the browser knows how to decrypt the incoming data. These public keys are sent in the form of a digital certificate. This certificate is signed by a trusted certificate authority (CA) that guarantees that the public key you are about to get is actually from the Web server and not from some evil person trying to pretend to be the Web server. A number of companies issue digital certificates, such as Verisign, Comodo, and many others.

Your Web browser has a built-in list of trusted certificate authorities, referred to as trusted root CAs. If a certificate comes in from a Web site that uses one of these highly respected companies, you won't see anything happen in your browser; you'll just go to the secure Web page, where a small lock icon will appear in the browser status bar or address bar. Figure 27-35 shows the list of trusted certificate authorities built into the Firefox Web browser.

Figure 27-35  Trusted certificate authorities

If you receive a certificate that your browser thinks is fishy, such as one that is expired or one for which the browser does not have a trusted root CA, the browser will warn you and usually give you some way to make an exception for the certificate, as shown in Figure 27-36.

Figure 27-36  Incoming certificate

We all have to make our own decisions here, but you should usually heed the browser's warning and advice. Most certificate warnings are invalid for boring reasons, like the site owner forgetting to update the certificate on time. But the certificate warnings could just as easily indicate that the site or your connection to it is compromised! Only add an exception if you know it's safe. You might, for example, need to add an exception to access a site on your organization's intranet.

Wireless Issues

Wireless networks add a whole level of additional security headaches for techs to face, as you know from Chapter 20. Here are a few points to consider:

-   Set up wireless encryption, at least WPA2 but preferably the more secure WPA3 if your device supports it, and configure clients to use it.

-   Disable DHCP and require your wireless clients to use a static IP address.

-   If you need to use DHCP, only allot enough DHCP addresses to meet the needs of your network, to avoid unused wireless connections.

-   Change the WAP's SSID from the default.

-   Filter by MAC or IP address to help limit network access to known clients only.

-   Change the default username and password. Even if the defaults are generated and look secure, knowledge of how they were generated might make them easier to guess.

-   Update the firmware as needed.

-   If available, make sure the WAP's firewall settings are turned on.

-   Configure SOHO router NAT/DNAT settings.

-   Use SOHO router content filtering/parental controls.

-   Consider physical security of SOHO router.

Chapter Review

Questions

1\.   What is the process for using or manipulating people to gain access to network resources?

A.   Cracking

B.   Hacking

C.   Network engineering

D.   Social engineering

2\.   Which of the following might offer good hardware authentication?

A.   Strong passwords

B.   Encrypted passwords

C.   NTFS

D.   Smart cards

3\.   Which of the following is used for biometric authentication?

A.   Motion sensor

B.   RSA token

C.   Palmprint scanner

D.   Kerberos

4\.   Which hardware firewall feature enables incoming traffic on a specific port to reach an IP address on the LAN?

A.   Port forwarding

B.   NAT

C.   Screened subnet

D.   Multifactor authentication

5\.   Zander downloaded a game off the Internet and installed it, but as soon as he started to play, he got a Blue Screen of Death. Upon rebooting, he discovered that his Documents folder had been erased. What happened?

A.   He installed spyware.

B.   He installed a Trojan.

C.   He broke the Group Policy.

D.   He broke the Local Security Policy.

6\.   Which of these choices would provide better security for Mary's Wi-Fi router?

A.   Secure DNS

B.   WEP

C.   WPA2

D.   WPA3

7\.   Malware that encrypts a hard drive and demands payment in exchange for decryption is known as what?

A.   Trojan

B.   Cryptominer

C.   Ransomware

D.   Keylogger

8\.   John dressed up in a fake security guard uniform matching the ones used by a company and then walked into the company's headquarters with some legitimate employees in an attempt to gain access to company resources. What kind of attack is this?

A.   Administrative access

B.   Data destruction

C.   Spoofing

D.   Tailgating

9\.   Andre, CEO of a midsized company, received an e-mail that appeared to be from a colleague that wanted to close a major deal. Suspicious because the deal in question didn't exist, he called in his IT security team who determined that it came from a spoofed IP address. Which of the following best describes this attempted attack?

A.   Phishing

B.   Whaling

C.   Zero-day

D.   Tailgating

10\.   Edna wants to put a policy in place at her company to prevent or at least limit viruses. What policies would offer the best solution?

A.   Install antivirus software on every computer. Teach users how to run it.

B.   Install antivirus software on every computer. Set up the software to scan regularly.

C.   Install antivirus software on every computer. Set up the software to update the definitions and engine automatically. Set up the software to scan regularly.

D.   Install antivirus software on every computer. Set up the software to update the definitions and engine automatically. Set up the software to scan regularly. Educate the users about sites and downloads to avoid.

Answers

1\.   D. Social engineering is the process of using or manipulating people to gain access to network resources.

2\.   D. Smart cards are an example of hardware authentication devices.

3\.   C. Palmprint scanners are a method of biometric authentication.

4\.   A. To open a port on your hardware firewall and send incoming traffic to a specific PC, use port forwarding.

5\.   B. Zander clearly installed a Trojan, a virus masquerading as a game.

6\.   D. Mary should set up WPA3 on her Wi-Fi router.

7\.   C. Malware that demands money in exchange for hard drive decryption is called ransomware.

8\.   D. John just practiced tailgating on the unsuspecting company.

9\.   B. Andre was the target of a whaling attempt.

10\.   D. The best policy includes updating the software engine and definitions, scanning PCs regularly, and educating users.

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

Chapter 27 Securing Computers

Chapter 28 Operational Procedures

Appendix A Mapping to the CompTIA A+ Objectives

42h 21m remaining
