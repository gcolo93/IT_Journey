CHAPTER 24

Mobile Devices

In this chapter, you will learn how to

-   Explain the features and capabilities of mobile devices

-   Describe the major mobile operating systems

-   Describe how to configure mobile devices

It's hard to imagine that most of the mobile devices we use today (in particular the popular iPhone, iPad, and Android devices) at one time sounded like science fiction rather than reality. Mobile devices have revolutionized the way we work and play. Devices such as smartphones and tablets enable people to access unique tools and features from just about anywhere and accomplish essential tasks on the go.

As amazing as mobile devices are, it's not easy to find a definition of mobile device that everyone agrees on. If you ask folks who are comfortable with these devices, you'll get lots of descriptions of functions and capabilities as opposed to what they are. In essence, the following aspects make a device mobile (and even these will sometimes create debate):

-   Lightweight, usually less than two pounds

-   Small, designed to move with you (in your hand or pocket)

-   Touch or stylus interface; no keyboard or mice

-   Sealed unit lacking any user-replaceable parts

-   Non-desktop OS; mobile devices use special mobile operating systems

The last one is important---as discussed in Chapter 23, a device's OS is the easiest way to differentiate between something like a 2-in-1 laptop in a tablet form factor and a plain tablet mobile device. Your typical portable computer runs a desktop OS such as Windows, macOS, or some Linux distribution such as Ubuntu. A true mobile device will typically run Apple iOS, iPadOS, or some form of Google's Android.

EXAM TIP   CompTIA A+ 1102 objective 1.8 lists iPadOS, iOS, and Android under cell phone/tablet OSs. The same objective lists Windows, Linux, macOS, and Chrome OS under workstation OSs. Be aware that while there are some tablets that run versions of Windows, for exam purposes, Windows is treated as a desktop operating system rather than a mobile one.

This chapter explores mobile devices in detail. We'll first look at the hardware features and capabilities of devices common in the mobile market. Next, we'll examine mobile operating system software. The chapter finishes with the details of configuring the devices for personal use. We'll save mobile device troubleshooting and security for Chapter 25. The CompTIA A+ certification exams are serious about mobile devices and we have a lot of ground to cover, so let's get started.

1101

Mobile Computing Devices

The specialized hardware of mobile devices defines to a large degree the capabilities of those devices. This first section examines smartphones and tablets and then looks at specific hardware common to many of these devices.

Device Variants

Most modern mobile devices fall into one of a few categories, including smartphones, tablets, and wearable technology, which all have similar features and capabilities. There are a few other mobile device types, and they are best understood as devices purpose-built to be better at some task than a general-purpose device such as a smartphone or tablet; an e-reader is a good example. The CompTIA A+ 1101 exam objectives focus on smartphones and tablets, but be aware that these other types of mobile devices exist.

Smartphones

One of the earliest types of mobile device was the personal digital assistant (PDA), such as the Compaq iPaq from the late 1990s. PDAs had the basic features of today's mobile devices but lacked cellular connectivity, so you couldn't make a phone call. Many people, your author included, spent close to ten years carrying a mobile phone and a PDA, wondering when somebody would combine these two things. Starting around 2003--2005, companies began marketing PDAs that included cellular telephones (although cool features like using the PDA to access Internet data weren't well developed). Figure 24-1 shows an early PDA-with-a-phone, the once very popular RIM BlackBerry.

Figure 24-1  RIM BlackBerry (courtesy of the TotalSem Tech Museum)

While these tools were powerful for their time, it wasn't until Apple introduced the iPhone (see Figure 24-2) in 2007 that we saw the elements that define a modern smartphone:

Figure 24-2  Early Apple iPhone

-   A multi-touch interface as the primary input method for using the smartphone

-   A well-standardized application programming interface (API) enabling developers to create new apps for the system

-   Tight consolidation of cellular data to the device, enabling any application (Web browsers, e-mail clients, games, and so on) to exchange data over the Internet

-   Synchronization and distribution tools that enable users to install new apps and synchronize or back up data

Since then, smartphones have developed many more features and uses. They have come to play a big role in the trend toward ever-present connectivity and seamless data access across all of our devices. Because smartphones do so much more than simply make and receive phone calls---we surf the Web with them, stream music and video, send and receive e-mail, and even do work with them---the infrastructure and technologies that connect smartphones with a mesh of networked data and services must be fast, robust, and secure.

Most smartphones run one of the big two operating systems: Google Android or Apple iOS (see Figure 24-3). iOS runs exclusively on Apple hardware, such as the iPhone. Phones running Android come from a multitude of manufacturers. Smartphones typically have no user-replaceable or field-replaceable components, and have to be brought into specialized (and in some cases, authorized) service centers for repair.

Figure 24-3  Examples of the big two smartphone OSs: Android (left), iOS (right)

Tablets

Tablets are very similar to smartphones; they run the same (or at least similar in the case of Apple's tablets) OSs and apps, and use the same multi-touch screens. From a tech's perspective, they are like large smartphones (without the phone). While a typical smartphone screen is around 5 to 6 inches, tablets run around 7 to 12.9 inches (see Figure 24-4).

Figure 24-4  Typical tablet

Unlike smartphones, tablets generally lack a cellular data connection (unless you buy a model specifically designed for it), instead counting on 802.11 Wi-Fi to provide Internet connectivity. Tablets are available at many price points, from more budget-friendly options that sacrifice performance and build quality in favor of affordability, all the way to high-end devices that use cutting-edge hardware, premium materials, and the most advanced available features. Tablets have come a long way since they debuted, and are now fairly ubiquitous not only for individual users but also in business settings.

Mobile Hardware Features

Much of the usefulness of mobile devices is driven by the many hardware features they include. This section explores the basics: screen technologies, cameras, microphones, digitizers, and GPS connectivity.

Screen Technologies

Mobile devices use a variety of screen types. Most tablets use some type of LCD panel, just like portable devices and desktop monitors. The less expensive ones use twisted nematic (TN); the better ones, like the Apple iPad, use an in-plane switching (IPS) panel for richer colors and better viewing angles. Refer back to Chapter 17 if you need to review the difference between these panel types. We'll take a look at the technology that turns these screens into touch interfaces in the upcoming "Digitizers" section.

Some smaller devices, like the better smartphones, use a related technology---organic light-emitting diode (OLED)---that lights the screen with an organic compound. Applying an electric current causes the organic layer to glow in the precise spots desired. Displaying a checkerboard pattern of black and white, in other words, only lights up the white squares. OLEDs and AMOLEDs don't use backlights at all, which means they can display true black, they're lighter, and they use less electricity than LCDs.

EXAM TIP   OLED screens use an organic compound exposed to electrical current for lighting; they don't have a traditional backlight.

NOTE   Some devices use active matrix OLED (AMOLED), which adds a TFT layer for more control over the screen. AMOLED is more expensive than OLED, but provides a better picture that uses less electricity.

Cameras

Many mobile devices have distinct front-facing and rear-facing cameras. These cameras enable chatting with Grandma over Facetime, tearful YouTube confessionals, and Instagram selfies! Devices with a camera can transmit video over cellular and IP-based networks (such as the Internet) just like dedicated or built-in webcams on full-fat desktops and laptops.

Smartphone cameras have come a long way since the grainy, low-resolution images of yesteryear. Many of them now rival all but the high-end dedicated point-and-shoot cameras used by advanced hobbyists and professional photographers (see Figure 24-5).

Figure 24-5  Author's camera app on his iPhone

Modern smartphone camera features include high dynamic range (HDR), light compensation, and other functions that enable the user to finely tune a photo or video. Manufacturers have even incorporated advances in artificial intelligence to their image-processing software to enhance the end results. Higher-end and even midrange devices often have more than one camera lens built in, allowing for more versatile photography. Additionally, these cameras offer a variety of options when taking photos and video; some cameras enable you to take "bursts" of shots (like ten in a single second) to make sure you capture faster-moving objects and action shots, as well as slow-motion video. When coupled with the multitude of apps available for mobile devices, you can edit photos and videos on-the-fly, adding light-filter effects, cleaning up shots, and even adding special effects.

Microphones

Almost all mobile devices incorporate at least one microphone. Smartphones certainly wouldn't be of much value without a microphone, and you wouldn't be very effective at communicating over Skype or FaceTime without them. Additionally, many people use mobile devices to dictate speech or record other sounds, so microphones serve many purposes on mobile devices.

As with the portable devices discussed in the previous chapter, mobile devices commonly have more than one microphone to enable noise-cancelling routines to work their magic. In contrast to those more traditional portables, you may need to take more care to avoid blocking any of the microphones on a mobile device.

Digitizers

When electrical engineers talk about a digitizer, they refer to a component that transforms analog signals into digital ones; that is to say, it digitizes them. That's not what we techs talk about when discussing digitizers on mobile devices. A digitizer refers to the component that provides the "touch" part of a touch screen. When your finger contacts a touch screen, the digitizer's fine grid of sensors under the glass detects your finger and signals the OS its location on the grid. As with modern trackpads, you can use one or more fingers to interact with most touch screens.

EXAM TIP   The CompTIA A+ 1101 exam objectives mention touch-screen configuration as something you do on a laptop or mobile device. While this used to only really apply to touch-screen laptops, some configuration options for touch screens have made their way to tablets and smartphones as well.

Location Services

One major feature of mobile devices is the ability to track the device's location through global positioning system (GPS) services, cellular, or Wi-Fi connections. Users rely on cellular location services to conveniently find things near them, such as stores and restaurants, or to determine when their Uber driver will show up. This section discusses some of what a mobile device such as a smartphone can do with GPS capability, followed by a look at privacy concerns associated with location tracking.

A great example of how smartphones can use GPS is the traffic and navigation app Waze (see Figure 24-6). Waze not only navigates, but its crowd-sourced data collection provides you with amazing real-time knowledge of the road ahead.

Figure 24-6  Waze in action

Another cool use of GPS is finding your phone when it's missing. The iPhone offers the Find My iPhone app (see Figure 24-7), for example. This feature is part of the iCloud service that comes free with any iOS device.

Figure 24-7  Find My iPhone app

Location Tracking and Privacy  Tracking your location is generally a good thing...when you want to be tracked. By default, mobile OSs track and in many cases record your location for an extended amount of time. This is called geotracking, and not everyone likes it. If you don't like this feature, turn it off. Figure 24-8 shows turning off Location on an Android phone.

Figure 24-8  Turning off Location

EXAM TIP   Because mobile devices tap into the Internet or cellular phone networks, the devices have identifying numbers such as a MAC address. The cell phone companies and government agencies can use the ID or MAC address to pinpoint where you are at any given time. Geotracking has a lot of room for abuse of power.

1102

Mobile Operating Systems

Most mobile devices run either Apple iOS or Google Android. This section discusses their development and implementation models, as well as some of their major features, including how their app stores work.

Development Models

Before we look at each mobile operating system in detail, let's step back to consider the big picture. The different underlying philosophies inspiring these operating systems---and guiding the companies that make them---help us understand why they do something one way instead of another. We'll start with a look at closed source and open source as development models. You may have heard these terms regarding how software is released and licensed (if not, Chapter 28 will discuss how these terms apply to licensing), but they also provide an interesting framework for looking at how products are developed and released. Then we'll discuss how these models apply to operating systems.

Closed Source

When it comes to development models, it may help to think of closed source as another way to refer to the traditional practice of making and selling a product without telling anyone how you made it. The traditional model makes intuitive sense, at least in our culture; how your product is made is a trade secret---something that gives you a competitive edge---and sharing it could inspire competitors to use your design, or potential customers to make it themselves.

Vendor-Specific and Proprietary  We sometimes apply the terms vendor-specific or proprietary to a closed-source product or technology, most often when we're trying to highlight something that doesn't use common, open standards. The terms are related to closed source, but don't confuse them; they aren't interchangeable. These labels often imply that the product may not play nice (or be interoperable) with other products, may have connectors and cables that are hard to find or expensive, may not be friendly to users who want to tinker with or modify it, may be harder to repair, and may pose a host of other problems.

The concept behind and use of these terms is sometimes slippery. As you'll see later in the chapter, a device maker may use a common standard such as USB 3.0, but design its own connector. Even though the device maker is technically using part of the open USB 3.0 standard, we'll still call the device's ports and cables proprietary.

Open Source

In this broader sense, you can think of a product as open source if its maker releases the instructions for making it---it doesn't have to be software (though that's usually the context). When a company commits to open sourcing one or more products, it has to operate differently than companies using a closed-source model. Secrecy, for example, is necessarily a smaller part of its business; knowing that anyone could make its products, the company has to focus on other factors (such as price, service, support, convenience, quality, innovation, etc.) to stay competitive.

Just because a company releases these instructions to the public doesn't mean anyone else gets to own them. Much as artists and authors set terms that specify whether the rest of us can legally copy or modify their work, the owners or authors of the instructions for making a product will specify terms for how others are allowed to use them. Sometimes the owners or authors may just say they're releasing the instructions for personal use or educational purposes---you can study what they've done and make your own product, but you can't start selling copies. When it comes to open-source software, these terms commonly dictate whether companies who modify the software are obliged to publish their changes, and whether they're allowed to profit from how they use it.

Development Models and the Mobile OS

The development model is one of many choices that reflect underlying company philosophy and goals. A company that makes an open-source mobile operating system like Google Android has little control over how the OS will be used and who can modify it. A company that makes a closed-source operating system like Microsoft Windows but licenses the OS to device makers has more control---the company knows the OS won't be modified and can be picky about which devices to license it for. A company making a closed-source OS like Apple iOS for its own devices can tailor-fit the software to the hardware it will run on. A company that builds an OS others can use and modify as they see fit and a company that builds an OS handcrafted exclusively for its own hardware obviously have very different underlying philosophies and goals.

The big thing to keep in mind with an open-source operating system like Android is that companies building devices that use the OS don't have to share the OS developer's underlying philosophy---they can have wildly varying goals and development models of their own. If the operating system's license allows it, each of the device makers could modify the OS before installing it on their own device---and never release those modifications. The modifications might just enable special hardware to work, but they could also install apps you don't want and can't remove, cause third-party apps coded without knowledge of the modifications to malfunction, or collect information about how you use the device.

To bring this all together, the point is that a manufacturer can put an open-source operating system on an otherwise closed-source device---don't assume a device is itself open source just because the mobile OS it uses is. In fact, vanishingly few of the devices with an open-source OS are best seen as open-source products.

Think back to the earlier discussion of an open-source development process and apply it to a smartphone. The most extreme interpretation of an open-source smartphone is that the maker has released all of the instructions and code someone else would need to manufacture an identical smartphone and all of the components inside it. A more likely (but still exceptional) scenario is that all of the software on the device when it leaves the factory is open sourced, including the operating system, drivers, and the firmware powering its components.

Apple iOS and iPadOS

Apple's closed-source mobile operating system, iOS (see Figure 24-9), runs on the iPhone. (The Apple iWatch runs a different OS, called watchOS. It is also closed source.) The Apple model of development is very involved: Apple tightly controls the development of the hardware, OS, developer tools, and app deployment platform. Apple's disciplined development model is visible in its strict development policies and controls for third-party developers, and this control contributes to the high level of security in iOS.

Figure 24-9  iOS 15

iOS apps are almost exclusively purchased, installed, and updated through Apple's App Store. An exception is providers of line-of-business apps specific to a particular organization. These internal development groups reside within an organization and can develop iOS apps, but deploy them only to devices that are under the organization's control, skipping the public App Store. They still have to undergo a type of Apple partnering and enterprise licensing approval process.

Apple's famous iPad tablet used to run iOS, but over time, the needs of tablet users evolved, and it now runs iPadOS (see Figure 24-10) The differences between iOS and iPadOS are slight, and the experience of using an iPad is very similar to that of using an iPhone. The average user may not notice the differences, but there are some important distinctions between the two that a good tech should aware of.

Figure 24-10  iPadOS in action

One key difference is in touch pen compatibility. Touch pens are, in general, an advanced version of the traditional stylus, which usually is just a plastic pointer with some kind of rubber point. Apple's touch pen is called the Apple Pencil and only works with iPadOS-equipped devices. Beyond keeping the screen clear of fingerprints, a touch pen can be used to effectively handwrite notes and draw precise and often professional-caliber artwork. Tablet users have gravitated toward using tablets as laptop substitutes in some cases, so iPadOS accommodates this by incorporating some of the features more commonly associated with macOS, such as multitasking functionality, mouse and keyboard support, and the ability to connect external storage via USB-C. On the flipside, there are things that iOS does that iPadOS doesn't. Most notably, iOS allows direct pairing with Apple's smartwatch, while iPadOS does not.

Google Android

For simplicity, think of Android and iOS as opposites. Android (see Figure 24-11) is an open-source platform, based on yet another open platform, Linux, and is owned by Google. Because Android is open source, device manufacturers can (and do!) alter or customize it as they see fit; there are differences among the implementations from various vendors. Google writes the core Android code and occasionally releases new versions (naming each major update after a dessert or candy of some sort), at which point vendors customize it to add unique hardware features or provide a branded look and feel.

Figure 24-11  Android 12 (Snow Cone)

Android apps are available to purchase and download through various app stores, such as Google Play and the Amazon Appstore. Android app stores tend to be fairly open in contrast to the high standards and tight control Apple applies to its third-party app developers, and Android makes it easier to install arbitrary applications downloaded from a Web site.

NOTE   Android-based devices may be more open than iOS ones on average, but it isn't a given. How open or closed an individual Android device is will depend greatly on how its manufacturer has modified the OS.

Mobile OS Features

Mobile operating systems come in a variety of flavors and sometimes have different features as well as different interfaces. But they also have a great deal in common, because consumers expect them to perform most of the tasks they are used to seeing in other mobile devices, regardless of operating system. Whether you are using an iPhone, an Android phone, or a smart watch, you still expect to be able to send texts, check your e-mail, and make video calls. Because of this, mobile OS differences boil down to hardware and app support, look and feel, and philosophical differences that manifest in how the OS goes about a common task. We'll take a quick look at some of the features common to all mobile operating systems and point out differences along the way.

User Interfaces

All mobile OSs have a graphical user interface (GUI), meaning you interact with them by accessing icons on the screen. Current models do not offer a command-line interface. Each OS usually has either a major button or a row of icons that enables the user to navigate to the most prominent features of the device. They also all support touch gestures, such as swiping to navigate between screens or pinching to zoom in or out. Most mobile OSs have some type of menu system that enables the user to find different apps and data.

iOS offers some customization of the user interface. You can group apps together into folders, for example, and reposition most apps for your convenience. The iOS look and feel, however, will remain consistent.

Android offers a very different GUI experience by employing programs called launchers that enable users to customize their Android device extensively. Many companies make launchers, and different manufacturers ship devices preloaded with launchers they make or prefer. Samsung devices use the TouchWiz launcher, for example. I use the Nova launcher on my Android phone. The launcher enables you to change nearly every aspect of the GUI, including icon size, animations, gestures, and more.

Most mobile devices include an accelerometer and a gyroscope, one to measure movement in space and the other to maintain proper orientation of up and down. These extend the user interface to include how you move the device itself; a common use is changing the screen orientation when you rotate a device from vertical to horizontal, for example, to enhance watching videos on YouTube.

Wi-Fi Calling

While every mobile device that calls itself a phone must have support for cellular wireless, another feature that many mobile devices include is Wi-Fi calling, the capability to make regular phone calls over Wi-Fi networks. Wi-Fi calling is very useful if you often find yourself in a place with poor cellular coverage but good Wi-Fi. To use Wi-Fi calling, first both your phone and carrier need to support it, then you need to enable it in your phone settings (see Figure 24-12). Once Wi-Fi calling is enabled, the phone will use any Wi-Fi network it's connected to (assuming the performance is acceptable) for all phone calls.

Figure 24-12  Option to enable Wi-Fi calling on an iPhone 13 Pro

Virtual Assistants

"Hey, Siri!"

"Yes, Mike?"

"What's the weather like today?"

"Always sunny where you are, Mike."

Okay, maybe they're not quite that cool, but the virtual assistants on smartphones and tablets enable quick, vocal interaction to accomplish common goals. For example, one only has to ask Siri (Apple's virtual assistant) how to find the nearest restaurant or tourist attraction, and she (Siri's voice is female by default) will respond with the information sought. Virtual assistants can also be useful in performing Internet searches and, in some cases, even activating and using certain apps on the mobile device. This helps people who may have certain disabilities that may prevent them from tapping or typing on the device, by enabling them to use voice commands.

A virtual assistant is also useful if you must use your smartphone while driving (although anything that diverts your attention from the road is discouraged for safety reasons). You can speak to the smartphone's virtual assistant to place a call or get directions while driving, especially if the smartphone is paired with the car's Bluetooth system. The Windows 10/11 equivalent to Siri is called Cortana, and essentially serves the same functions and provides the same services and features. Google's virtual assistant, Google Assistant, is also available for iOS and any of Google's many platforms like Google Home and Android TV. In addition to the big three's virtual assistants, there are also apps you can download that provide other virtual assistant services, depending upon your platform.

Software Development Kits

Most mobile operating systems come with some sort of software development kit (SDK) or application development kit that you can use to create custom apps or add features to existing apps on the device. Figure 24-13 shows the development (programming) environment for the iOS SDK, Xcode, with the code for an iOS app open in the background window, and the same app code running in an iPhone simulator on top.

Figure 24-13  Xcode running an app written with the iOS SDK

Each mobile OS poses its own challenge to app developers. Apple's rigid development model makes it such that your app must pass a rigorous testing program before it is allowed into the App Store. Microsoft's development model, while not typically as rigid, is similar in nature. Google, on the other hand, allows anyone to create Android apps and distribute them to the masses without much interference.

Emergency Capabilities

One feature almost all currently marketed smartphones have built in is the emergency notification feature that enables them to receive broadcasts from national emergency broadcast systems, such as the Emergency Alert System (EAS) in the United States. This can be a very useful feature during severe weather, enabling you to receive warning text messages. In the event someone reports a child missing in your immediate area, it enables you to get AMBER Alerts. Many of these emergency broadcast system alerts also force your phone to emit a very loud sound or vibrate incessantly in order to get your attention.

While modern smartphones can place 911 calls effectively, the old 911 system relied on the Public Switched Telephone Network (PSTN) to trace a call and determine its location, in order to dispatch emergency responders to the correct address quickly. This was problematic with mobile devices, so legislation was passed (the Wireless Communications and Public Safety Act of 1999) requiring carriers to be able to pinpoint the location of a mobile device, such as a smartphone. The Enhanced 911 (E911) system uses GPS and cellular networks to triangulate the location of a phone by its distance from cell towers, its transmission delay time, and other factors.

Mobile Payment Service

As smartphones and other mobile devices have become so much more commonplace in our daily lives, we've become very reliant on them to store our personal and sensitive information such as passwords, credit card numbers, financial documents, receipts, and more. Over time, smartphone manufacturers, as well as merchants, realized that the next logical step was to enable you to pay for goods and services simply by scanning your smartphone or using an app.

The app connects to your bank information and automatically transfers the funds from your bank to the merchant. This feature is called mobile payment service. Near field communication (NFC) applications refine the process further: simply place your device on or near the special pad at the register in order to authorize payment to the merchant. (See "NFC," later in this chapter, for the scoop on these tiny networks.)

Additionally, smartphone manufacturers produce their own payment systems. The Apple payment system, called Apple Pay, was first implemented with the iPhone 6, and support has been integrated into the Apple Watch. Apple Pay supports major credit card payment terminals and point-of-sale systems, including those fielded by Visa, MasterCard, and American Express. Apple Pay can use contactless payment terminals with NFC and supports in-app payments for online purchases.

Mobile payment systems have become a lot more popular over time. Since Apple saw success with Apple Pay, other software companies and mobile manufacturers followed suit. Samsung, one of the most prominent manufacturers of Android smartphones, released Samsung Pay in 2015. Google released their version in 2018, and predictably named it Google Pay. These apps have expanded their functionality to serve as full-blown digital wallets, allowing you to do more than just pay for things. One of the coolest features is that users can now store and transfer digital tickets for concerts and sporting events, making forgotten or lost tickets largely a thing of the past.

Airplane Mode

Airplane mode is simply a switch (either an actual hardware switch located on the mobile device or a software switch that can be located in the device's configuration settings) that turns off all cellular and wireless services, except Bluetooth (see Figure 24-14). The aptly named mode disables these communications so passengers can comply with restrictions protecting aircraft instruments from interference, though you can also use it as a shortcut for turning off communication functions.

Figure 24-14  Airplane mode enabled on iOS 15

VPN

As you'll recall from earlier chapters, VPNs establish secure connections between a remote client and the corporate infrastructure, or between two different sites, such as a branch office and the corporate office. VPNs are typically implemented using tunneling methods through an unsecure network, such as the Internet. In a client VPN setup, the host has client VPN software specially configured to match the corporate VPN server or concentrator configuration. This configuration includes encryption method and strength, as well as authentication methods.

A site-to-site VPN scenario uses VPN devices on both ends of the connection, configured to communicate only with each other, while the hosts on both ends use their respective VPN concentrators as a gateway. This arrangement is usually transparent to the users at both sites; hosts at the other site appear as if they are directly connected to the user's network.

VPNs can use a variety of technologies and protocols. The most popular ways to create a VPN are to use either a combination of the Layer 2 Tunneling Protocol (L2TP) and IPsec (see Figure 24-15), or Secure Sockets Layer (SSL)/Transport Layer Security (TLS). When using the L2TP/IPsec method, UDP port 1701 is used and must be opened on packet-filtering devices. In this form of VPN, users connect to the corporate network and can use all of their typical applications, such as their e-mail client, and can map shares and drives as they would if they were actually connected onsite to the corporate infrastructure.

Figure 24-15  Configuring a VPN

An SSL/TLS-based VPN, on the other hand, uses the standard SSL/TLS port, TCP 443, and is typically used through a client's Web browser. SSL/TLS-based VPNs don't normally require any special software or configuration on the client itself, but they don't give the client the same direct access to resources on the corporate network. Therefore, users may have to access these network resources through the client browser via an access portal.

NOTE   SSL has been entirely replaced by TLS, but you'll often still see things referred to as SSL/TLS or SSL. VPNs are one example where this is the case.

1101

Configuring a Mobile Device

Mobile devices require some setup and configuration to function seamlessly in your life, though the industry is constantly refining and simplifying this process. Mobile devices typically come preconfigured with everything but your user account and network credentials. Just because you don't have to do much to get up and running anymore doesn't mean you're out of the woods, though. You may well need to configure corporate e-mail accounts, device add-ons, apps, synchronization settings, and other advanced features.

You can add capabilities by enhancing hardware and installing productivity apps. You also need to set up network connectivity, add Bluetooth devices, configure e-mail account(s), and enable the devices to synchronize with a computer. Plus you have a lot of add-on options; let's take a look.

Enhancing Hardware

A mobile device is a computer, just like your desktop or laptop, with the same basic components doing the same basic things. The construction centers on a primary circuit board, the motherboard, onto which every other component is attached. The biggest of these components is often the system on a chip (SoC), a wonder of miniaturization combining a CPU, GPU, and sundry other support logic onto a single silicon die, saving a lot of space and power in the process. An interesting aside about the CPUs used in these devices is that they are rarely Intel x86 based; instead, you are much more likely to run across an ARM architecture chip when perusing the spec sheets of your new tablet or smartphone. The iPad uses Apple-designed ARM A-series or M-series chips, for example, while Samsung's smartphones and tablets generally use ARM chips from Qualcomm's Snapdragon line-up.

Mobile devices use storage, though you'll never see one using a traditional magnetic hard disk drive (HDD) with spinning platters. Mobile devices use flash media such as a solid-state drive (SSD) or microSD card because they are smaller, use less power, and are much, much faster than spinning HDDs. Plus they're cooler, just like you.

Mobile devices differ from their larger brethren in two very significant areas of importance to techs. First, none of them offer any user-replaceable parts. If something breaks, you send the device back to the manufacturer, visit a local manufacturer-supported retail outlet such as the Apple Store, or take it to a specialized repair shop. Second, you can't upgrade mobile devices at all. Even a laptop enables you to upgrade RAM or a mass storage drive, for example, but the mobile device you buy is exactly what you get. You want something better? Buy a new one.

That said, every mobile device enables you to attach some kind of peripheral or external storage device. But every device offers different expansion capabilities, so it's hard to generalize about them. The closest you can get is the audio jack, but many smartphones no longer include them, in favor of Bluetooth connectivity. That being said, audio jacks are still around on some devices (see Figure 24-16).

Figure 24-16  Earbuds plugged into a smartphone

Note this is quickly changing as Apple dropped the jack as of the iPhone 7, and many Android devices have started leaving the port off as well, as Bluetooth wireless earbuds and speakers continue to become more popular, reliable, and affordable. Current iPhones and most iPads use the Lightning jack or USB-C, respectively, for physical external connections.

Apple Expansion Options

Apple devices offer the least expansion capability of all mobile devices, so even though they dominate the U.S. marketplace, there's not much to say about them. Most of the expansion on Apple devices is limited to proprietary cables and devices. The iPhone and iPad have historically used a single proprietary Lightning port for charging the device and connecting to the few external devices available. Figure 24-17 shows the typical use for the port: connecting to a USB AC adapter to charge.

Figure 24-17  USB charger connected to proprietary Lightning port

While the vast majority of Apple's iOS devices stick with the proprietary Lightning connector, Apple has switched to USB Type-C with most iPad variants. Who knows what this means for the iPhone line, but it is nice to see Apple expanding its use of the industry standard. We'll return to USB Type-C, along with a number of other connectors, later in the chapter.

iPhones and iPads enable you to mirror the screen to a multimedia device such as a projector or a smart TV. This enables seamless presentations, for example, through the excellent Apple Keynote program (see Figure 24-18). The multimedia connection originally required another adapter (see Figure 24-19), but if you're using your device with a smart TV or another Apple device like an iMac, you can achieve this wirelessly with a feature called AirPlay.

Figure 24-18  Apple Keynote on an iPad and a projector

Figure 24-19  Apple Digital AV Adapter

Android Expansion Options

Devices that use Google Android come with a variety of connections and expansion capabilities. Some offer microSD slots for adding storage in the form of these tiny flash memory cards (see Figure 24-20), but this is becoming less common.

Figure 24-20  microSD card and slot

Android devices used to have a more diverse range of connectors available, both for charging and connecting peripherals. Older devices sometimes used miniUSB, or proprietary power connectors, and some Android smartphones even had a tiny Micro-HDMI port. This has largely gone the way of the dinosaurs though, and most Android devices you'll see today make use of USB-C or occasionally still use microUSB.

Finally, some tablets (but rarely smartphones) sport a connector for attaching the device to an external monitor, such as a big screen or projector. Figure 24-21 shows a Micro-HDMI port and connector.

Figure 24-21  Micro-HDMI port and connector

Bluetooth

The last way that mobile devices expand their physical capabilities is wirelessly, most often using the Bluetooth standard (if you need a refresher on Bluetooth, refer back to Chapter 20). Traditionally, extending a mobile device with Bluetooth has meant adding a headset, mouse (though not with Apple iOS products), keyboard, or speaker. Figure 24-22 shows a diminutive Apple keyboard for the iPad and the iPad resting in a stand to make typing a little easier than using the virtual keyboard. With Bluetooth-enabled wearable devices growing in popularity, it can be tricky to decide how self-sufficient one of these must be before it stops counting as a mobile enhancement and enters the realm of full-fledged mobile device.

Figure 24-22  Keyboard associated with iPad

NOTE   See the "Bluetooth" section toward the end of this chapter for the steps to set up a mobile device with a Bluetooth speaker.

Installing and Configuring Apps

Mobile devices come from the manufacturer with a certain number of vital apps installed for accessing e-mail, surfing the Web, taking notes, making entries in a calendar, and so on. Almost all mobile devices offer multimedia apps to enable you to listen to music, take pictures, watch YouTube videos, and view photos. You'll find instant messaging tools and, in the case of smartphones, telephone capabilities.

Beyond these essentials, you'll install most other apps through an app store. As you read about the app ecosystem for each mobile OS, consider how well the details of each ecosystem mesh with the development models discussed earlier in the chapter. Even though the rules of each app ecosystem usually reflect this development model, don't assume the apps on offer will follow suit---you'll find plenty of closed-source apps available on Android and open-source apps available for iOS.

iOS/iPadOS Apps

Apple iPhone and the iPad use the iOS and iPadOS operating systems, respectively. Apple exerts more control over the user experience than any other manufacturer by insisting all app developers follow strict guidelines.

Apple maintains strict control over what apps can be installed onto iOS/iPadOS devices, meaning that if you want to get an app for your iPhone or iPad, you can only get it from the Apple App Store (see Figure 24-23). Apple must approve any app before it goes into the App Store, and Apple reserves the right to refuse to distribute any app that fails to measure up.

Figure 24-23  App Store

To add an app, select the App Store icon from the home screen. You can explore featured apps in the Today tab or peruse by category. You can check out the popular games, or simply search for what you want (see Figure 24-24).

Figure 24-24  Searching for Monument Valley 2

The first time you try to purchase an app through the App Store, you'll be prompted to set up an account. You can use an account that you created previously through the Apple iTunes music and video store or create a new Apple ID account. You can create a new Apple ID account with a few quick steps (see Figure 24-25) and a valid credit card.

Figure 24-25  Creating an Apple ID for iCloud and App Store purchases

Another iCloud feature, the iCloud Keychain, builds on the Keychain feature in macOS to synchronize user information, passwords, payment information, and other credentials with all of your Apple devices. (See "Synchronization," a little later in the chapter.) Keychain can seamlessly store many non-Apple credentials as well, such as logins for Facebook, Amazon, and other providers, and use them to auto-complete repetitive forms in both device apps and on Web sites. The real benefit is that you can authorize Apple to save this sensitive information, instead of authorizing each individual app or site to keep a copy.

Android Apps

Google Android powers many smartphones and a solid portion of tablets. Unlike Apple iOS, Google gives core Android away, enabling manufacturers to differentiate their Android devices from those of other manufacturers. A Samsung tablet, in other words, uses a version of Android that differs somewhat from the Android an ASUS tablet uses. Likewise, OnePlus developed a custom interface called OxygenOS to change the look and feel of Android on its devices.

Because of these modifications, few Android users ever use "stock" or unmodified Android. Despite the shared core OS, Android users familiar with devices from one manufacturer may get tripped up by the different interface on Android devices from a different maker. These differences make it important to combine knowledge of the Android version a smartphone or tablet runs with knowledge about the manufacturer and its modifications to Android. The manufacturer will typically assign a version number to each release of its modifications.

Android devices can usually get apps from more than one source. The most common is Android's default app store, Google Play (which offers well over 2 million apps)---but some manufacturers (such as Amazon, for its line of Fire devices) modify Android to change this.

Many manufacturers offer a store with apps developed or customized to work with their devices. These vendor-specific stores enable you to get apps that should work well with your Android smartphone or tablet.

You can also go to a third-party app store or market for apps developed "for Android" that probably will work with your device, but there's no guarantee that they'll work on all Android devices. This Wild West approach to apps makes the Android smartphone or tablet experience vastly different from the experience on iOS.

Network Connectivity

Mobile devices connect to the outside world through the cellular networks or through various 802.11 Wi-Fi standards. You learned specifics about the standards in Chapter 20, so I won't rehash them here. This section looks at standard configuration issues from the perspective of a mobile device.

When you want to connect to a Wi-Fi network, you need to enable Wi-Fi on your device and then actively connect to a network. If the network is properly configured with WPA2, or WPA3 encryption, then you also need to have the logon information to access the network. The most common way to connect is through the Settings app (see Figure 24-26).

Figure 24-26  Selecting the Settings icon

The Settings app enables you to do the vast majority of configuration necessary to a mobile device. To join a network, for example, tap the Wi-Fi (or Networks) option to see available networks (see Figure 24-27). Simply select the network you want to join and type in the passphrase or passcode. Give the mobile device a moment to get IP and DNS information from the DHCP server, and you're on the network.

Figure 24-27  Browsing available networks

After you connect to a network successfully, all mobile devices store that network access information automatically, creating a profile for the network based on its SSID. This works just like with any other device that connects to a Wi-Fi network. If the SSID of a network changes after you've connected to that network, your mobile device will fail to connect to the rechristened network. You need to delete the profile and reconnect. Delete the profile through the Settings app by choosing the Wi-Fi network and selecting Forget this network.

EXAM TIP   You can use the Settings app to turn off Wi-Fi or to go into airplane mode to stop the device from sending any signals out.

Cellular Data Networks

Anyone with a smartphone these days can enjoy the convenience of using wireless cellular technology. Who doesn't love firing up an Android phone or an iPhone and cruising the Internet from anywhere? As cell-phone technology converges with Internet access technologies, competent techs need to understand what's happening behind the scenes. That means tackling an alphabet soup of standards. Regardless of the standard, the voice and data used on smartphones and some tablets (unless you have 802.11 wireless turned on) moves through a cellular wireless network with towers that cover the world. Back in Chapter 21, we discussed the technologies that make up cellular networking, so now we're going to talk about how it can be enabled and disabled on most mobile devices.

As discussed earlier in this chapter in the context of mobile operating systems, Android and iOS have a lot in common and that includes similar ways to enable and disable your cellular network. The way to accomplish it is fairly simple: swipe down from the top of the screen to check for a quick option, labeled with something like Data or Cellular. Alternatively, you can use the Settings app (introduced in the previous section). Once you've found it, look for the menu option that says Data or Cellular, and toggle it on or off.

Radio Firmware

Mobile devices use a wide variety of radio technologies to access the Internet, e-mail, and corporate infrastructures. Generally, mobile devices have two types of radios: 802.11 and Bluetooth. If the device can make calls, it also has some form of cellular radio.

PRL, PRI, and Baseband Updates  As mobile devices travel, they frequently have to pass through areas that don't have strong signals, or into areas that the carrier does not service. When a mobile device connects to different carriers' networks, we say it is roaming; roaming may result in additional service charges, depending upon the carriers involved.

Your phone's firmware will receive occasional automatic updates to its Preferred Roaming List (PRL) from the carrier; the PRL is a priority-ordered list of the other carrier networks and frequencies it should search for when it can't locate its home carrier's network. Updates to this list are sent via your phone's cellular connection (called baseband updates, or over-the-air updates) or, in some cases, through firmware updates during normal operating system and firmware upgrades via synchronization.

CDMA devices may also receive product release instruction (PRI) updates, which modify a host of complex device settings. Don't worry about specifics, here---these settings can pertain to the intricacies of many functions such as GPS, cellular connectivity, and messaging---but instead focus on the fact that carriers use these product release instructions to ready the device for deployment on their networks, enable the network to route calls or messages to the device, and more. As such, PRI updates may be needed if the network is evolving during the lifetime of a device, the device needs to be moved to a new network, or the device has a new owner.

EXAM TIP   PRL updates are handled automatically during firmware/OS updates. They are only for CDMA networks. No one but the nerdiest of nerds will ever see these updates.

IMEI, ICCID, and IMSI  There are three particular identifiers you will need to understand in order to effectively manage mobile devices. The International Mobile Equipment Identity (IMEI) number is a 15-digit number used to uniquely identify a mobile device. IMEI numbers are unique to devices using the Global System for Mobile Communications (GSM) family of technologies, including its present-day descendants: 4G LTE and 5G. You can typically find this number printed inside the battery compartment of the mobile device, but you may not need to take the device apart: some operating systems enable you to view it inside the device configuration settings (see Figure 24-28).

Figure 24-28  IMEI settings on an Android phone

The IMEI number can be used to identify a specific device and even to block that device from accessing the carrier's network. If the device is lost or stolen, the user can notify her carrier, and the carrier can make sure the device can't be used on the network.

NOTE   Always write down your IMEI number when you get a new phone, as it can prove you are the actual owner if the phone is stolen or lost.

The ICCID number, which stands for Integrated Circuit Card Identifier, uniquely identifies a subscriber identity module (SIM). The SIM contains information unique to the subscriber (the owner of the phone), and is used to authenticate the subscriber to the network. SIMs can be moved from phone to phone, usually with no problems.

The third number is the International Mobile Subscriber Identity (IMSI) number. It is also included on the SIM, but represents the actual user associated with the SIM. This number is not normally accessible from the phone, but is usually available from the carrier, to ensure that stolen phones are not misused. The IMSI number can also be used to unlock a phone.

You might want to record these numbers for each managed device in the enterprise, whether for inventory purposes or so that you have them handy when you work with your mobile device management (MDM) software (look for a more in-depth explanation about MDM software in Chapter 25). The MDM software typically collects these identifiers along with other device information (such as the telephone number or MAC address) during the provisioning process and stores them in the mobile device inventory for you. Figure 24-29 shows how IMEI and ICCID numbers are listed for a newer Android device in the device settings.

Figure 24-29  IMEI and ICCID numbers

Data

Many mobile devices can use the cellular data services discussed in Chapter 20 to access the Internet. This way you can use your smartphone, tablet, or other mobile devices to get e-mail or browse the Web pretty much anywhere.

By default, mobile devices that use cellular networks for Internet connectivity use data roaming, meaning they'll jump from cell tower to cell tower and from your provider to another provider without obvious notice. This is no big deal when you travel within your own country where competing providers have inexpensive roaming agreements.

Watch out for data roaming outside your country! If you travel to another country, your mobile device will happily and seamlessly connect via another cell provider if one is available. This can lead to some shockingly huge bills from your cell phone company when you get back from that cruise or international trip. If you're going outside your cell provider's coverage area, get a plan that specifies that you're traveling. It'll still be more expensive than your regular plan, but not nearly as crazy as an accidental roaming charge.

If you don't need to connect when out of country, turn data roaming off. You'll find the feature in the Settings app, as you might expect. You can also turn off cellular data entirely or only turn off cellular services selectively if your device can do more than one type. You would want to turn off cellular data, for example, if you don't have an unlimited data plan and are getting near your limits. There are also some security reasons to disable cellular connections while traveling, which we'll explore further in Chapter 25.

E-mail

Every mobile device uses an e-mail service set up specifically from the mobile OS developer. Plus, you can configure devices to send and receive standard e-mail as well. Let's look at the integrated options first.

All mobile devices offer e-mail services from the manufacturer or the OS developer. iOS and iPadOS devices integrate perfectly with iCloud, Apple's one-stop shop for e-mail, messaging, and online storage. Android devices assume a Gmail account, so they feature a Gmail option front and center.

Aside from the integrated e-mail options, mobile devices enable you to set up standard corporate and ISP e-mail configurations as well. The process is similar to that of setting up e-mail accounts that you learned about in Chapter 21. Apple devices go through the Settings app, tap Mail, then tap the Accounts option (see Figure 24-30). Tap the Add Account option to bring up the default e-mail options (see Figure 24-31). If you want to connect to a Microsoft Exchange Server--based e-mail account, tap the appropriate option here and type in your e-mail address, domain, username, password, and description.

Figure 24-30  Accounts screen on iPhone

Figure 24-31  Default e-mail types on iPhone

Neither POP3 nor IMAP4 is one of Apple's suggested options, so if you want to set up an account of either type, you'll need to tap the Other option on the initial Add Account screen. Eventually you'll get prompted to choose POP3 or IMAP and type in addresses for the sending (SMTP) and receiving servers.

Android-based devices assume you'll have a Gmail account as your primary account, so you'll find Gmail's distinctive app icon on the home screen (see Figure 24-32). Gmail also can talk to other, non-Gmail e-mail services for setting up Exchange, POP3, or IMAP4 accounts; you configure it the same way as you would a desktop e-mail application, including putting in the port number and security type, in this case, TLS, if the server lacks autoconfigure (see Figure 24-33).

Figure 24-32  Gmail app

Figure 24-33  Setting up a secure IMAP account

EXAM TIP   The latest versions of Android simply query the e-mail server to configure port numbers and security types automatically, just like modern desktop-based e-mail clients. Even though current devices automate this process, the CompTIA A+ 1101 objectives include port numbers, so you need to know them.

The CompTIA A+ 1101 exam will hit you pretty hard on e-mail settings, specifically on TCP port numbers for the various e-mail protocols. We've covered these in earlier chapters, but here's a quick cheat sheet and a few alternative numbers for real-world applications:

-   POP3 uses TCP port 110.

-   IMAP4 uses TCP port 143.

-   SMTP uses TCP port 25.

Many servers block these default ports; plus, when you move to more secure versions of the protocols, you need to use other port numbers. I have no clue whether CompTIA will quiz on the secure ports for POP3, IMAP4, and SMTP, but here they are:

-   Secure POP3 uses TCP port 995.

-   Secure IMAP4 uses TCP port 993.

-   Secure SMTP uses TCP port 465 or 587.

Finally, you may also have to configure other settings, such as Secure/Multipurpose Internet Mail Extensions (S/MIME) standard, used to configure digital signature settings for e-mail, and contacts from the corporate address book, depending on how the corporate e-mail server is set up.

EXAM TIP   Be familiar with corporate e-mail configuration settings for Gmail, Yahoo, Outlook, and iCloud (You'll get a closer look at them in Chapter 25). Know the corporate and ISP e-mail configuration settings for POP3, IMAP4, port and security settings, and Exchange.

Synchronization

From the first day mobile devices came into existence there was a problem: synchronizing data. People don't want their contacts on their mobile devices to be different than the contacts on their desktop---or online contacts. People don't want to edit e-mail on their mobile device and then have to go online to make the same changes. People only want one calendar. If you have a mobile device, you're going to want a method for all these different sets of data to synchronize so you only have one set of contacts, one e-mail inbox, one calendar, and so forth.

To keep files and data up to date, smartphones and tablets can synchronize, or sync, with cloud-based servers over the Internet or with local machines. These files and data include personal documents, Internet bookmarks, calendar appointments, social media data, e-books, and even location data. Older devices, such as BlackBerry and Palm Pilot, had a specialized sync program you installed on your computer to sync contacts, calendars, and so on. Today's devices sync through the cloud or optionally use a dedicated program.

Various mobile devices sync differently, depending upon the device vendor and software required. iOS/iPadOS devices use Apple iCloud to sync iPhones, iPads, and Macs via the cloud. Android devices can use Google's many services to sync certain configuration settings, apps, photos, texts, and so on. In some cases individual apps will synchronize directly; for example, a podcast app might synchronize data such as subscribed shows. Older versions of iOS needed to sync to a laptop or desktop computer via Apple's iTunes application. While this is still fully supported, most users will just let iCloud handle everything in the background.

EXAM TIP   Synchronization enables mobile devices to keep up to date with a lot of essential information. You should know the types of data typically synced, including contacts, e-mail, photos, and calendar information for the exam, and other types of data to be a great tech. It's a lot. You can do this!

Synchronize to the Automobile

Automobile makers know you will talk on the phone while driving. While inherently dangerous---a good conversation can distract you from surroundings, including other 3000-pound death machines---everyone does it. Modern automobiles come equipped with voice communication systems, hands-free calling that uses your smartphone via Bluetooth (see Figure 24-34). Synchronizing to the automobile enables voice-activated contact calling, among other things, and often hooks up with a car's navigation system to help you get from point A to point B.

Figure 24-34  Calling via an iPhone using a car's built-in entertainment system

Exchange ActiveSync

Exchange ActiveSync (EAS) is a Microsoft protocol used to synchronize Microsoft Exchange e-mail, contacts, and calendars that has become widely used across a range of mobile OS platforms and hardware vendors, including Apple and Android devices. It was originally developed as a synchronization protocol for Microsoft Exchange corporate users, but has evolved over time to include more device control and management features. EAS not only has the capability to set up and configure network connectivity and secure e-mail options for clients that connect to Microsoft Exchange corporate servers, but also has the capability to control a much wider range of functions. Some of these functions include the ability to set password policies, remotely wipe or lock a mobile device, and control some device settings.

Synchronization Methods

In the old days, mobile devices were synchronized to a desktop (uphill, both ways, in the snow!), using a specific type of synchronization software provided with the device. Also, the type of data was typically limited to contact information, but we liked it because it was all we had. Now, there are newfangled ways you can sync device contacts, media files, and even apps. You can also get updates and patches from the device manufacturer by syncing your device.

With faster cellular and Wi-Fi networking technologies, you can skip the desktop and sync even large amounts of data to the cloud. Each phone vendor has its own cloud technology that can tie to your user account and store personal data from your mobile device. Apple has iCloud, Microsoft has OneDrive, and Google has Google Drive, as do some of the individual manufacturers that make Android devices.

There are also independent cloud providers that enable you to store your personal data, and even share it with others. Dropbox is a prime example of this type of provider, although there are many others. Most cloud storage services require you to set up security measures to protect your data, such as requiring a username and password for authentication. Some cloud providers also allow you to encrypt data stored in their cloud.

Synchronizing your data to a personal computer (or laptop) has both advantages and disadvantages. Some advantages of syncing to a personal computer are that you can be in full control of storing and protecting your own data, encrypted any way you choose, and can also move it to portable storage in case you need a backup of it later. A disadvantage is that you must be able to connect to your computer---a small problem if you can't bring it with you.

Syncing to the cloud also has its advantages and disadvantages. If you have a good cellular or wireless signal, you can sync from anywhere. You do have to be careful of syncing over insecure public wireless networks, however, since there is a possibility that your data could be intercepted and read over these insecure networks. Another disadvantage of syncing to the cloud is that once your data is in the cloud, you no longer fully control it. You are at the mercy of the security mechanisms and privacy policies of your provider. You have to accept whatever security mechanisms they use, such as encryption strength (or lack thereof), and you have to abide by their privacy policies, which may allow them to turn your data over to other companies for marketing, or even to law enforcement. Additionally, some cloud providers may limit the type and amount of data you are allowed to store in their cloud. These restrictions are typically in place to prevent software, movie, and music piracy.

These are all considerations you'll have to think carefully about when choosing whether to sync to the desktop, the cloud, or both.

EXAM TIP   The CompTIA A+ 1102 objectives cover synchronization extensively, and this overlaps with an 1102 objective, single sign-on (SSO). Be aware that a properly coded application on a modern mobile device can enable you to log in with one of the other accounts you're probably already logged into, such as Google, Apple ID, Facebook, Twitter, etc. The process for using your active authenticated session with one of these common services to sign you into other services is called single sign-on (SSO). This may come up on the 1101 exam in the context of mobile device synchronization or on the 1102 exam in the context of single sign-on.

Synchronization Issues

The most common synchronization issue is a connectivity, device, or remote infrastructure problem that leaves data partially synced. A partial sync could result in incompletely downloaded e-mail or even duplicate messages as the device tries over and over to successfully sync, repeatedly downloading the same e-mail messages. A device may attempt to sync to download an OS patch or update and may fail. The most likely culprit is connectivity issues with Wi-Fi or cellular connections, and the problem can usually be resolved by moving the device to an area with a stronger signal. This doesn't prevent upstream connectivity issues, which may also have to be examined.

There are other problems that prevent synchronization, including authentication issues, OS version issues, or incorrect configuration settings. If a device won't sync even after getting it to a stronger, more stable connection, these are some of the things you should examine. Another problem may be the remote end of the connection. This may be the enterprise e-mail server, or even the entry point into the enterprise network. Failure to properly authenticate or meet the requirements of the entry device may prevent a device from synchronizing.

Another issue you may want to examine when you have synchronization trouble is that multiple sources may be trying to sync the same data. A device can synchronize from an enterprise app store, for example, as well as the vendor app store; personal e-mail services, such as Gmail and Yahoo Mail; and even from third-party providers of "whatever-as-a-service" and cloud storage. This could be as simple as a configuration change you had to make for one service preventing another from working---or the sources might be independently trying to sync different data to the same location. In the enterprise environment, it's the mobile device management team's job to put together a management and technical strategy that will ensure minimal conflict between different synchronization sources.

Account Setup and Management

If you or someone you know uses mobile devices for work, you've most likely done or at least seen some form of account setup or management. Most productivity apps, like Microsoft 365, Google Workspace, and Apple's suite of apps that use iCloud, are designed to be synchronized across multiple devices. This means that the document you were reviewing or the e-mail you were carefully writing on your laptop before you had to leave for an appointment can be paused, synchronized, and resumed on another computer or, you guessed it, a mobile device. This sort of cross-platform synchronization has become essential to businesses and it's going to be something you'll encounter on the CompTIA A+ exam, as well as on the job in IT.

The big question you probably have now is about how to synchronize these accounts. In this regard, mobile devices work mostly in the same way as a desktop or a laptop. The mobile versions of productivity apps generally mimic most of the functionality of their desktop counterparts, with optimized user interfaces to account for things like the smaller display, touchscreen, screen rotation, and other mobile device characteristics. They're also optimized to make it as easy as possible to synchronize. In many cases, it's as simple as installing the mobile version of an app like Microsoft 365, entering the e-mail and password associated with the account, and waiting a few seconds until your Teams chat or Outlook e-mails are available to you on the go.

Most of these apps give users or administrators the ability to make adjustments, including to synchronization settings. Some device synchronization settings may, for example, cause your device to save things you're working on in local storage. If this happens, you may be happy about it, or you may wonder why your smartphone suddenly started displaying a notification that your storage is full. You may also notice that your accounts aren't synchronizing. In this case, one of the first places you should look is your account settings; the fix may be as simple as turning on synchronization in your mobile app.

Mobile Device Communication and Ports

Mobile devices wouldn't be nearly as useful if they didn't have ways to interconnect with the outside world. This section looks at the many technologies and connections mobile devices use to get data flowing to the Internet and other devices.

MicroUSB/MiniUSB

If you have an Android device made before 2017, it's very likely it has either a micro- or mini-USB port to charge, connect to laptops or desktops, and sync between those devices. MicroUSB or miniUSB connectors were standard on most Android devices. That's not to say that you won't be able to find devices using proprietary connectors; Google makes the OS available to multiple device manufacturers, and some manufacturers do maintain a proprietary connector.

Lightning Connector

With the iPhone 5, Apple introduced its most recent proprietary connector, known as the Lightning connector. It replaced the older 30-pin dock connector that Apple used on previous iPhones and iPads. The Lightning connector is an 8-pin connector (see Figure 24-35) that can be inserted without regard to proper orientation; in other words, it's not "keyed" to insert a specific way (such as right-side up or upside down, as traditional USB connectors are) into the device.

Figure 24-35  Lightning connector

NOTE   Earlier-model iPads made use of the Lightning connector, but in 2018, Apple released the first USB-C iPad Pro. Since then, Apple has gradually transitioned its various other iPad models, like the Air and Mini, to USB-C. You'll only find Lightning connectors in use on older models, or the basic iPad still sold by Apple at the time of writing.

The proprietary nature of the Lightning cable means it's more expensive than a normal USB cable. It is licensed to other manufacturers through the Made for iPhone (MFi) program, but to prevent widespread production of fake Lightning connectors by unlicensed manufacturers, it contains a small chip that identifies it as a true Lightning connector, and cables without that chip typically won't work or will only have limited use.

NOTE   The Apple Lightning standard is the epitome of proprietary vendor-specific ports and connectors. Only iOS devices use Lightning for communication and power. Android devices typically use industry-standard, vendor-neutral ports and connectors.

USB Type-C

USB Type-C (see Figure 24-36), the newest iteration of USB connectors, is quickly becoming the de facto standard port on Android devices today, which is awesome because you can use one charger for your laptop and phone. As we touched on earlier, Apple has gradually adopted USB-C for its iPad lineups since 2018 due to its compatibility with a huge number of peripherals and its higher power handling that provides faster charging.

Figure 24-36  USB Type-C connector

Like the Lightning connector, the USB Type-C connector is not keyed, allowing it to be inserted right-side up or upside down. It can (but doesn't have to) support USB 3.1 technology with very fast data transfer rates of up to 10 Gbps. Don't assume Type-C is synonymous with a specific version of USB---some devices using a Type-C connector are using it with USB 2.0.

EXAM TIP   You will likely see micro- and mini-USB, USB-C, and Lightning mobile device connection types on the exams. Know their characteristics and differences.

Bluetooth

While we discussed Bluetooth at some length, including configuring and pairing, in Chapter 20, let's review an outline of how the process will work on a mobile device. You can pair a Bluetooth device with a mobile device using a simple process that begins with enabling Bluetooth on the mobile device (if it isn't already enabled). Steps vary, but you can accomplish this in the quick settings menu or the full device settings menu. Next, power on the other Bluetooth device (or ensure Bluetooth is enabled if the device is already on). Return to the mobile device to discover and select the Bluetooth device for pairing, and then enter the appropriate personal identification number (PIN) code (see Figure 24-37). To add Bluetooth speakers, for example, the smartphone or tablet will display a set of characters for you to type on the keyboard. Once you type in the PIN code, the devices connect.

Figure 24-37  Prompting for PIN

EXAM TIP   Not all Bluetooth pairings require a PIN code, but there's always some kind of pairing action to perform on both devices.

Always remember to test the connectivity between a mobile device and a newly added Bluetooth accessory. If you've added a speaker, open up your favorite music app or podcast and tap play to make sure it works.

EXAM TIP   Most mobile devices have Bluetooth discovery disabled by default to conserve battery life. An active search for devices to pair with uses electricity, as does completed pairing, so use Bluetooth only when you need to use it and be prepared for the battery hit.

NFC

Near Field Communication (NFC) uses chips embedded in mobile devices that create electromagnetic fields when these devices are close to each other. The typical range for NFC communications is anywhere from a very few centimeters to only a few inches. The devices must be very close to or touching each other, and can be used to exchange contact information, small files, and even payment transactions through stored credit cards using systems like Apple Pay and Google Pay. This technology is seeing widespread adoption in newer mobile devices, as well as the infrastructures and applications that support them. Tap pay devices are increasingly common, using NFC and your phone so your credit cards stay in your wallet or purse.

Magnetic Readers and Chip Readers

Merchants can attach a magnetic reader or a chip reader to a smartphone to enable very quick credit card transactions via the cellular network. Vendors appreciate the portability of credit card readers, for example, which take credit card payments from a mobile device for goods and/or services rendered (see Figure 24-38). It's not unusual to see a food truck use a portable credit card reader plugged into the headphone port on an iPad, or being used at the Texas Renaissance Festival to take the Totalsem crew's money when they dressed up and went to play (see Figure 24-39). Cheers!

Figure 24-38  Magnetic credit card reader attached to smartphone

Figure 24-39  Totalsem crew at the Texas Renaissance Festival

Infrared

Now largely replaced by other, faster technologies, such as Bluetooth and 802.11 wireless, infrared (IR) was previously used to transfer data between mobile devices, such as laptops and some older PDAs. Infrared was used to create the first real personal area networks (PANs). Infrared uses the wireless Infrared Data Association (IrDA) standard, and at one time was widely used to connect devices such as wireless remotes, printers, wireless mice, digitizers, and other serial devices. IrDA requires line of sight, meaning that devices have to be directly facing each other, requires very short distances (sometimes inches) between devices, and has very slow data rates.

EXAM TIP   You may have noticed that CompTIA included serial interfaces on the A+ 1101 objectives. A serial interface is a connection that sends data one bit at a time. The venerable RS232 port found on legacy devices is one example, but infrared is also a type of serial interface. You can also get adapters to convert another port into a serial port, and these exist for many different types of devices. Keep all of these possible types of serial interfaces in mind because you may see them on the exam.

Hotspots and Tethering

A mobile hotspot is a small device that shares access to cellular technologies such as 4G, 4G LTE via Wi-Fi, and 5G. Most of these devices can be purchased from wireless providers such as Verizon, Sprint, AT&T, T-Mobile, or other carriers, and are usually specific to their type of broadband network. A mobile hotspot is basically a wireless router that routes traffic between Wi-Fi devices and broadband technologies, providing wireless access for up to five to ten devices at a time.

Depending upon the carrier, many cellular phones, as well as tablets, can act as portable hotspots. You'll recall this from Chapter 21. When used in this manner, it's called tethering to the cell phone. While some devices configured as hotspots can use your existing data plan with your carrier, some carriers separate out and limit the amount of data that can be used for tethering.

To configure a device as a hotspot, you typically enable its cellular data connection and turn on an additional hotspot setting that causes the device to broadcast a Wi-Fi network. Now the mobile device serves as a router between the cellular network and the traditional Wi-Fi network it is broadcasting. Then any devices that you wish to tether to the hotspot simply see the device as a wireless router. You can also configure a password so that not just anyone can connect to the hotspot. Figure 24-40 shows a screenshot of an Android phone serving as a portable hotspot.

Figure 24-40  An Android phone acting as a portable hotspot

Accessories

Mobile device accessories come in a wide variety of types, packing a huge range of features. Some of the most common accessories that people want for their mobile device, particularly smartphones and tablets, include devices that wirelessly connect to them, typically using Bluetooth technologies. It's not unusual to find Bluetooth headsets and high-quality external speakers for users to listen to music and chat with friends.

Game controllers, including gamepads and other accessories that plug into tablets via a USB port or connect via Bluetooth, are also common, effectively turning tablets into full-scale gaming platforms. Additionally, cloud gaming has started to materialize as a viable option, and people are now able to use some mobile devices to stream their console and PC games and play on the go.

One feature that some Android mobile devices offer is the ability to use removable external storage, such as miniSD or microSD memory cards, effectively upgrading the storage capacity of the device. This is something Apple hasn't embraced with its devices, and in fact has become less common with Android devices as well.

There are also accessories no mobile device user should be without, including an external power bank or a phone or device charger. To recharge mobile devices, device chargers either plug into a wall outlet and the mobile device, or plug into a computer and the mobile device, while power banks are just portable batteries that you can charge up and plug your phone or tablet into to get some extra juice when you don't have the ability to plug into the wall.

Some chargers don't require connection to the device at all; they simply require you to lay the device on top of a special pad that recharges the battery wirelessly. Specifics differ a little depending on whether the device was designed for wireless charging or the capability is being added with an aftermarket kit---but in either case the pad creates an electromagnetic field for transmitting power to an antenna in the device. Despite being a wireless technology, the range is measured in centimeters and charging works best when the mobile device is on the pad.

The marketplace has settled on the Qi (pronounced "chee") standard from the Wireless Power Consortium (WPC) as the wireless charging standard of choice. Apple's 2017 decision to adopt the Qi standard and become a member of that consortium sealed the fate of early rival standards. Apple has even expanded wireless charging functionality to include power banks for some iPhone models.

Some devices also have specialized accessories, including docking stations (much like the docks discussed for portables in Chapter 23). Although these docking stations are typically used for tablets, they are also used for credit card readers.

Another important accessory is a case for the device. These include an almost unimaginable variety of designer cases, as well as hardened cases designed to withstand falls and other impacts. There also screen protectors---protective covers---that range from flimsy plastic all the way to hardened glass that can protect a mobile device screen from scratches and impact. You can find cases made of plastic, leather, rubber, wood, metal, and unicorn horn. Some of these cases are even waterproof, allowing the more adventurous folks to take their phones with them while they are diving in oceans or river-rafting.

We've covered only a few of the hundreds of accessories that are available for mobile devices. Many accessories also come with apps to help control or get the most out of the accessory.

Chapter Review

Questions

1\.   Which of the following is used in mobile devices to convert analog video and sound to digital video and sound?

A.   Calibrator

B.   SDK

C.   Virtual assistant

D.   Digitizer

2\.   John has a high-resolution image on his iPad of his two-year-old son and the family dog. The image initially displays smaller than the screen, so he wants to zoom in to get the details of his son's expression. What gesture can he use to accomplish this task?

A.   Click the mouse in the middle of the picture to select it, then use the scroll wheel on the mouse to zoom in.

B.   Tap the picture with his index finger on his son's face.

C.   Long-press on the image and select zoom from the pop-up menu.

D.   Touch his son's face on the screen with his thumb and finger, then pinch outward to scroll in.

3\.   Which mobile device screen technology uses no backlight?

A.   BYOD

B.   LCD

C.   LED

D.   OLED

4\.   What can a government use to determine your location at a specific time as long as you're using your mobile device?

A.   Multifactor authentication

B.   Geotracking

C.   Google Earth

D.   Authenticator applications

5\.   What are the steps involved in pairing a Bluetooth speaker with a tablet?

A.   Enable Bluetooth on the tablet; turn on the Bluetooth speaker; find the device with the tablet; enter a PIN code or other pairing sequence.

B.   Turn on the Bluetooth speaker; find the device with the tablet; enter a PIN code or other pairing sequence.

C.   Search for the Bluetooth speaker from the tablet; select pair from the options to enable the speaker.

D.   Enable Bluetooth on the tablet; turn on the Bluetooth speaker; find the device with the tablet; select pair from the options to enable the speaker.

6\.   Which of the following connectors is unique to Apple devices?

A.   Lightning

B.   USB-C

C.   Molex

D.   USB-A

7\.   John returned from a cruise to the Bahamas and got a bill from his cell phone company (Sprint) that was over $1000. What could have happened?

A.   John connected to the Internet with his smartphone using the cruise ship company's Wi-Fi.

B.   John's smartphone connected to the Internet in the Bahamas via a cell provider that wasn't Sprint.

C.   John used his smartphone to do Internet gambling, and Sprint frowns on that activity.

D.   Bills after international trips are always reported in the currency of the country visited. When translated from Bahamian dollars to U.S. dollars, the amount is the same he normally pays.

8\.   Leonard just purchased a very expensive comic book and paid for it using the stored credit card information on his smartphone. What technology did he use to make the transaction?

A.   Swipe lock

B.   Wi-Fi calling

C.   NFC

D.   BitLocker To Go

9\.   What information do you need to connect an Android-based tablet to an IMAP account?

A.   POP3 server DNS name

B.   Username and password

C.   Username, password, sending and receiving server addresses

D.   Exchange server name, username, and password

10\.   Which mobile OS enables device manufacturers to customize it to better suit their specific devices?

A.   Android

B.   Blackberry

C.   iOS

D.   iPadOS

Answers

1\.   D. Digitizers are used in mobile devices to convert analog video and sound to digital video and sound, or to interpret analog signals associated with touch movement on a screen into digital equivalents.

2\.   D. John should touch his son's face on the screen with his thumb and finger, then pinch outward to zoom in.

3\.   D. OLED technology does not use a backlight.

4\.   B. Geotracking can locate you and your GPS-equipped mobile device.

5\.   A. To pair a Bluetooth speaker with a tablet, enable Bluetooth on the tablet, turn on the Bluetooth device, find the Bluetooth device in the tablet's settings screen, then enter a PIN code or finalize the pairing.

6\.   A. Lightning connectors are an Apple proprietary connector type developed to be used with Apple's mobile devices.

7\.   B. John's smartphone connected to the Internet in the Bahamas via a cell provider that wasn't Sprint, causing him to incur high data roaming charges.

8\.   C. Leonard likely purchased his comic book using Near Field Communication (NFC) technology, which can be used for payment transactions through stored credit card information in mobile applications.

9\.   C. To connect an Android-based tablet to an IMAP account, you need a username and password and the sending and receiving server addresses.

10\.   A. Google Android is open source, enabling manufacturers to make modifications to better suit their specific devices.

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

Chapter 24 Mobile Devices

Chapter 25 Maintaining and Securing Mobile Devices

Chapter 26 Printers and Multifunction Devices

42h 21m remaining
