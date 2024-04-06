CHAPTER 25

Maintaining and Securing Mobile Devices

In this chapter, you will learn how to

-   Troubleshoot common mobile device and application issues

-   Explain basic mobile device security

-   Describe typical mobile OS and application security issues

Mobile devices are packed with tightly integrated hardware, aren't designed to be upgraded by their users, and come with mobile-oriented operating systems. Because of these major differences, the troubleshooting and security practices for mobile devices differ a lot from those for desktop computers, and somewhat from those for other portable devices. This chapter explores general troubleshooting of mobile devices and their apps first, then covers security features and capabilities of devices common in the mobile market. The chapter finishes by jumping into preventing, detecting, and addressing security issues with mobile operating systems and applications. CompTIA loves those performance-based scenario questions, so get ready for some real-world issues when it comes to security and application troubleshooting.

1101/1102

Troubleshooting Mobile Device Issues

The CompTIA A+ exam objectives divide mobile device problems into two groups: general issues with mobile device hardware and software (1101 exam), and security issues (1102 exam) with the mobile OS and apps. In this section we're going to cover tools for troubleshooting general hardware, OS, and app issues, and apply these tools to common problems. These common problems happen across all varieties, types, and manufacturers of mobile devices. This chapter includes references to Apple's iOS and iPadOS, as well as Google Android. We talked about the differences between iOS and iPadOS in Chapter 24, and while they are very similar, there are some areas where troubleshooting may differ, so keep both their similarities and differences in mind.

NOTE   Few mobile devices have components you can service in the field. In the event of a hardware problem, send the device to a service center for repair. Companies like iFixit (https://www.ifixit.com) are making some components field-replaceable, but usually only for skilled techs.

Troubleshooting Tools

Because mobile device hardware typically can't be repaired or replaced by a user or field tech, mobile device troubleshooting focuses on ruling out software issues. The few things you can try are common to almost all mobile devices, and it's best to start with ones that inconvenience the user least. Sometimes these tools will fix the problem, but other times they'll just restore normal functionality until the problem recurs, or help you rule out causes.

Just because you'll troubleshoot a mobile device a little differently doesn't mean you should throw out what you already know. Reflect on the troubleshooting methodology covered in Chapter 1, and use the troubleshooting tools you learn about here to help you work through that process. If the troubleshooting process doesn't fix the problem or identify a cause you can resolve in-house, the next step is to take or send the device to an authorized service center.

Keep in mind that the steps you'll need to take to perform any of these operations will depend on the specific device, its operating system, and the OS version. Be prepared to consult manufacturer and OS resources for exact steps. Let's dive in.

NOTE   Most of these tools either are guaranteed to erase data and customizations or have some risk of doing so under the right circumstances. Remember to communicate with the device's user what steps you'll be taking, including what kinds of data loss it can entail, and give the user a chance to back up his or her data.

Try This!

Practice on the Real Deal

If you have access to a smartphone or tablet, practice getting to the tools used for troubleshooting mobile devices. You're going to read about a bunch of places to adjust things such as screen brightness, close or uninstall apps, and much more. Access the device's Settings and explore. Just don't do anything specifically to any device without proper permissions.

Check and Adjust Configuration/Settings

Modern mobile operating systems have tons of configurable settings, as do many of the apps users install on them. Always be on the lookout for "problems" that sound a lot like a simple configuration issue and investigate these early if they seem likely. It won't cost you much (except time) to check relevant settings, but it might save you from having to perform later steps that require backing up and restoring user data.

If the issue isn't likely related to configuration, save your time and revisit configuration after you've tried rebooting the device, which we'll discuss in the upcoming "Soft Reset" section; you don't want to waste tons of time toggling settings if a reboot could fix the problem. If you find a setting that doesn't seem right and want to see if a change resolves the issue, make sure to keep track of what you changed and what the previous setting was!

Close Running Apps

All of the mobile operating systems provide at least one way to close running applications---the most common is to swipe the app in a particular direction from the device's list of recent apps. If you come at this with a traditional mindset shaped by how desktop operating systems work, there's a chance you'll misunderstand when and why we close mobile apps, so let's consider a much-simplified version of what goes on under the hood.

On a traditional computer, you open an application when you need it, and it will run until it completes its work, crashes, or you close it. Because mobile devices have more limited computing resources and battery power, you don't want open apps eating up big chunks of resources and burning power while they aren't in focus or the device isn't even being used. To address this problem, modern mobile OS versions manage running apps to optimize performance and battery life.

The catch is that the way they manage apps makes the term "running" a little slippery. While your current app may be running in the traditional sense, the various processes that power your recent out-of-focus apps may keep running if they have work to do, be cached until you return to the app, or get killed if the OS needs its resources for other apps. For the most part the OS will do a good job of managing well-designed apps, but you may still need to close an app if it has frozen, begins to malfunction, or you suspect it is causing the device to misbehave.

NOTE   When closing an app, keep in mind that the user may lose unsaved data when you close it, and (depending on the app) that their device may lose certain functionality they expect it to have until the app is restarted.

Some apps may (intentionally or accidentally) leave background processes running even after the GUI has closed. In Android, the Application Manager will let you force stop an app, also killing its background processes (Figure 25-1). In iOS and iPadOS, a swipe will generally do the job.

Figure 25-1  Force stop in Android

Soft Reset

To maintain mobile devices, it's important to understand the terminology surrounding resets, especially if you're coming at this from a desktop-oriented mindset. On a desktop, you typically initiate a soft reboot from within the operating system or trigger it by pressing a button dedicated to restarting the system; the hallmark of a soft reboot is that the machine never powers all the way down. In contrast, you can perform a hard reboot by holding down the system's power button for several seconds until it turns completely off; you don't want to reboot this way if you can avoid it, but you'll need to if the system is frozen.

On mobile devices, the term soft reset describes restarting the device, whether you do it from within the OS or with hardware buttons on the device. If the device still won't restart, confirm the soft reset procedure in the manufacturer resources; if you know you're performing it correctly, and the device allows for it, you can force a device with a removable battery to power down by removing the back cover and the battery.

Much like a reboot on a traditional computer, you can fix all kinds of strange behavior on a mobile device with a soft reset. I'm listening to Spotify on my Android device as I write this section, for example, and when I got started this morning the playback was stopping every few songs; I performed a soft reset and now it's working fine. The soft reset is the easy reset, but there's another reset you need to know; we'll continue this discussion in the "Reset to Factory Default" section coming up in a moment.

Uninstall/Reinstall Apps

Uninstalling and reinstalling apps can be an important troubleshooting process. You can uninstall apps through either the app store they were installed with or the device's application manager; you can also, of course, reinstall them via the app store. If the user started having trouble shortly after installing a new app, uninstalling it to see if the problem goes away is an obvious way to rule out a potential cause. If they've been successfully using the app, make sure to jot down important settings and back up their data if possible before you uninstall it.

The problems you can fix or troubleshoot by uninstalling and reinstalling aren't always as obvious as this. If a user has had an app for a long time and it only recently started acting up, it's possible the app's developers released a bad update; after a bad update, the app might not work at all, or it might work fine if you uninstall and reinstall it. Sometimes this can be a no-win situation for a tech---what if the only fix to a user's problem is removing an app they use daily until its developers fix a problem?

Reset to Factory Default

This other reset---known by many names such as hard reset, factory reset, or reset to factory default---will clear all user data and setting changes, returning the device (well, its software) to the state it was in when it left the factory. Take extra care not to confuse a hard reset with a hard reboot; if you're reading documentation or a how-to page that uses the terms reboot and reset interchangeably, pay close attention to what the author intends you to do---and consider finding a less-ambiguous resource.

Because the hard reset removes all of a user's data and settings changes, it's the most disruptive option here---typically one you won't perform until after backing up the user's data (which we'll discuss later in the chapter). The big exception is when you're intentionally performing a factory reset in order to clear user data off a device before it is sold, recycled, or assigned to a new user.

Despite the inconvenience, resetting a device to factory defaults is an important troubleshooting step on the way to determining whether it should be sent to a service center. If a factory reset fixes the device's issues but they return some time after restoring a backup of user data and programs, return to earlier steps for tracking down the troublemaking app.

Touchscreen and Display Issues

Modern mobile devices are almost all screen, and some provide little beyond a touchscreen and a power button for interacting with the device. While display issues tend to be urgent for most devices, the touchscreen's integral role in controlling a modern mobile device makes it all the more so. We already touched on some important steps for troubleshooting a touchscreen in the "Input Problems" section at the end of Chapter 23, so be prepared to integrate those steps with the more mobile-centric issues discussed here.

Dim Display

Mobile devices have a brightness control that can be set to auto mode or controlled manually. These settings don't always work perfectly, and sometimes apps that need special control over brightness settings can cause the device's display to be too dark or bright for the user's comfort.

A dim display might be a sign that there's a problem with the panel, but first you need to check the display settings. Turn off any auto-adjustment setting and manually change the display brightness from the dimmest to brightest setting and observe whether it covers an appropriate range of output. If it doesn't, there may be a problem with the display panel; if it does, there may be something keeping the auto-adjustment from working right.

The auto-adjustment is affected by how much light a sensor or camera on the front of the device can detect. Make sure the sensor isn't covered with dirt or some other obstruction. If the display is too bright in a dim room, check the surroundings for bright light that isn't close enough to illuminate the area, but that the sensor might pick up if pointed in the right direction.

Be on the lookout for apps that tinker with the display's brightness. These apps may use distinct brightness settings, or they may modify system-wide brightness. Reading apps, like Amazon Kindle, are one example. See if a soft reset returns the display to normal operation, and then investigate whether using these apps causes the brightness issue to return. Every once in a while, Kindle on my Android tablet will interfere with the system's auto-brightness, causing all sorts of strange brightness changes until I restart the tablet by performing a soft reset. The solution in this case may be as simple as teaching the user to reset their device when an app like this has caused a problem.

Autorotation Problems

Much like brightness controls, mobile devices also have automatic and manual controls for rotating the screen. The autorotate mode uses the device's accelerometer to change the screen between portrait and landscape orientations when the user rotates the device. When the screen does not autorotate, usually either autorotation is off (the screen orientation is locked) or the app currently being used does not support both portrait and landscape orientations, which is necessary for autorotation to work.

You might also run into an autorotation problem caused by OS, resource, or hardware problems on the device. If autorotation doesn't work after a soft reset, you may need to wait for an OS update or take the device in for service.

Touchscreen Responsiveness

When a user tries to interact with a mobile device but finds the touchscreen nonresponsive or gets an inaccurate touchscreen response, there are a few simple things to rule out first: dirt, accidental touches, and performance issues. Any of these can cause digitizer issues (we talked about what a digitizer is in more detail in Chapter 24), some of which can be resolved quickly, others require specialist diagnostic and repair. With those out of the way, we'll turn to more catastrophic causes.

Accidental Touch  The simplest issue to resolve is an accidental touch. Sometimes a user will hold a device in such a way that its touchscreen detects some part of their arm or hand as an intentional touch, and it may not react at all when they try to manipulate it intentionally. Oversensitive sensors or bad design might exacerbate this, but the fix is always the same: show the user how the sensors pick up an accidental touch and teach them how to hold the device to avoid them.

Dirty Screen  Another simple issue to resolve is a dirty screen. Sometimes simply wiping the touchscreen down with a dry microfiber cloth to get rid of fingerprints, dust, dirt, grease, and other foreign objects will fix a responsiveness problem (see Figure 25-2).

Figure 25-2  Cleaning a smartphone

Performance Problems  Much like a mouse cursor may slow, freeze, or move erratically when a traditional computer is having performance issues, a touchscreen may appear not to work at all or have severe accuracy and response problems if the mobile device is performing poorly. Be patient with the device and look for signs it is struggling to keep up. Is it displaying the right time? If it has an animated lock screen or wallpaper, are the animations playing smoothly?

If the device appears to have network connectivity, are weather or stock widgets on the lock screen updating? Is it slow to respond when you press unrelated hardware buttons? If the device can receive them, see if it responds normally when you call or text it. If the problem seems to be performance related, perform a soft reset and see if the touchscreen starts working.

A lot of users add a screen protector to their mobile devices to give a little extra help in case of a drop. A poorly installed screen protector can cause touchscreens not to work properly. Check the guidelines from the manufacturer and remove and replace a subpar screen protector.

Calibration and Diagnostics  If a soft reset doesn't get the touchscreen working, look online for information about whether the device has a hidden diagnostics menu or service menu. You might reach this menu by inputting a series of digits into the device's dialer, or by holding specific buttons while the device is booting up during a soft reset. If the device has a touchscreen diagnostic here, it should help you decide whether the touchscreen itself is in good working order. Some Android devices may also have a setting in either the primary OS settings menu or a hidden device menu for calibrating the touchscreen.

Physical Damage  While we covered the previous issues when we discussed portable devices in Chapter 23, smaller mobile and wearable devices have a greater risk of some problems that are rarer with larger portables. Everyone knows a quick dip in a toilet, margarita glass, or swimming pool can kill a mobile device, but sometimes getting one wet or dropping it on a hard surface can cause trouble short of complete death. A smartphone in your pocket when you get caught in the rain, or on a table when you spill a drink, could end up with liquid in all sorts of nooks and crannies.

Although some mobile devices can handle a little bit of moisture, most can't handle immersion at all. Dropping a smartphone in a toilet makes for a very bad day. Without removable batteries, there's not much you can do to save a liquid-soaked mobile device, and as a result, this level of liquid damage is often a death sentence for mobile devices.

If you rule out the simplest explanations and fixes in this section and the touchscreen is still not responding properly, it's time to inspect the device for evidence it has been dropped or gotten wet. There's always the old-fashioned way---ask the user. Just be aware that it may be hard to get someone to admit their touchscreen stopped working after they sprayed milk through their nose because they tried to read XKCD while eating breakfast.

NOTE   For a good dose of tech-oriented humor, check out the comics at https://xkcd.org. Geeky fun at its finest!

A broken screen doesn't require the glass itself to be cracked; drops or impacts can break internal connections, rendering the device difficult or impossible to use. Moisture can cause internal shorts, and lingering liquid could cause sensors to behave in really strange ways. Most mobile devices will contain a few liquid contact indicator (LCI) stickers that change color when exposed to water, as shown in Figure 25-3. While these are really so the carrier or manufacturer can refuse to cover water damage under warranty, look up their locations online and then check them on the device. There's often one on the battery or in the battery compartment, if it's accessible; it'll usually be white if it hasn't gotten wet.

Figure 25-3  Pristine LCI sticker (top) and LCI sticker absorbing a drop of water (bottom)

Apps Not Launching

A mobile device app may fail to launch or install correctly for a few reasons. First, the app may not be compatible with some combination of the mobile device's hardware, operating system version, or vendor/carrier customizations to the OS. With Android devices, for example, different manufacturers can tweak the OS to suit their own needs, which may cause compatibility issues with other vendors' apps.

NOTE   This section details reasons an app may always fail to launch or install correctly. Remember, an app may fail to install or launch correctly before you perform a soft reset, but do so fine afterward. Perform a soft reset and then try reinstalling and launching the app.

Another reason an app may not launch is that the device doesn't meet the app's hardware requirements. These might be more traditional requirements such as amount of available RAM, storage space, and processor type, but the app might also require a sensor or radio your device lacks or requires capabilities that your device's camera doesn't support. It's always a good idea to review an app's requirements before installing it (or when you run into trouble).

Both Apple and Android devices track errors with applications. You'll need third-party tools to access app log errors---or what I assume are logs of app errors (thanks, CompTIA!). Something to keep in mind if a senior tech or app programmer (in the case of custom apps for an organization) needs help with troubleshooting.

Overheating

Just as with the portable devices discussed in Chapter 23, overheating can cause permanent damage to a mobile device; most of the recommendations given there still apply. That said, our relationship with mobile devices is a little different. They are usually on, spend more time in our hands and pockets, and we take them places we wouldn't dream of taking a larger portable. A mobile device is more likely to get left on the car seat on a hot summer day or be nestled close to our body in well-insulated winter clothing.

Focus on overheating as a combination of the heat a mobile device produces itself, heat added to it by external sources like the sun or a lamp, and how well its environment dissipates or retains heat. Since we handle these devices more often, we have a lot of chances to notice what's normal and what isn't; when a device is hot, combine these three factors and see how well they explain the device's temperature. The process of looking for a good explanation can help you catch performance problems before they drain the battery, prevent heat damage to components, or identify problems with the battery or power systems before they become dangerous.

Charging, large data transfers, frozen apps, recording HD video, and other intensive tasks can all make a mobile device much hotter than normal; avoid letting the device do intense work in hot or well-insulated spaces. If you can avoid it, don't bring mobile devices into very hot environments; if you can't, minimize risk by turning the device off altogether. If the device is hot to the touch in a cool environment, you can put it into airplane mode, close all running programs, and see if it cools down. If it doesn't, turn it off until it cools and then try again.

Your biggest concerns are a device that overheats for no obvious reason or gets hot enough that it could burn someone. These problems are usually caused by some sort of hardware issue, possibly a defective battery or other power circuit within the device. There's really not much you can do; turn it off to protect the device from further damage and take it to a service center.

The dangers of not addressing an overheating mobile device---even one that is overheating for otherwise benign reasons---are, at best, an eventual device failure and requisite data loss. At worst, a severely overheating device can become a safety risk with the potential to burn or shock a user and, especially if the battery ruptures, cause a fire or explosion.

Update Failures

Ideas like app stores and regular automatic updates are now common on computer operating systems, but these things cut their teeth in the world of iPhone, Android, and even the failed Windows Phone. Ease of use rules this world, so installing software and updates on a mobile device is dead simple. But don't think it's too simple to fail! If you manage enough mobile devices, you'll see a case where the OS fails to update or an application fails to update.

Usually, the reason an update fails is that the device doesn't have enough free space to install the update. It might auto-purge some files to make room, but you'll have to jump in to remove some apps or files (back them up first) if it fails. Corrupt downloads won't install; check your device's documentation on how to delete the bad update and retry with a strong connection. Running out of battery mid-update can cause big trouble; it's best to plug in the device before updating the OS.

Slow Response

Mobile devices can be slow to respond like regular desktop computers and laptops, and often for the same reasons. Response issues can be caused by storage space being almost filled up on a mobile device, making it unable to save data or install apps efficiently. Mobile devices can also be slow to respond when there are too many apps running at the same time, eating up RAM.

Usually, the mobile device's OS has configuration settings that enable you to stop apps or view their resource usage, including memory and storage space. If storage space is an issue, you may have to uninstall some apps, or reinstall them so that they are stored on removable storage devices, such as microSD or miniSD memory cards.

A device with response issues will often be running hot, and this heat can be a big clue. Use the recommendations in the previous section to evaluate whether the device or the environment is the source of this heat. A hot, sluggish device could be using thermal throttling to protect the device's CPU from heat damage by reducing its power; in this case, performance should pick up as it cools.

One of the first troubleshooting steps you can take in resolving response issues is to perform a soft reset of the device; this clears running apps---perhaps even ones that are frozen or malfunctioning---from RAM. As far as troubleshooting tools go, you can use the device settings or third-party apps to measure the device's performance. Sometimes those apps can help point the way to what's causing the performance problems. If you ultimately determine that a hardware issue is causing performance problems, you should take the device to an authorized repair facility.

Battery Life

Just like the portable devices discussed in Chapter 23, modern mobile devices use Lithium-Ion (Li-Ion) batteries. It's usually not too hard to make use of a more traditional portable computer while it's charging, but the ergonomics of mobile devices can make it miserable to use one while it's charging---so it's even more important to make sure your device has power when you need it. Our purpose here is to look at how you can manage any battery to get the most out of it, but first we need to talk about the cornerstone of good battery management.

Meeting User Power Needs

Mobile devices are rated in terms of how long their battery should power a device during "normal" use, how long the device can go between battery charges, and the levels of power that both the battery provides and requires in order to charge. Make sure you and your users have mobile devices that have a chance to last long enough to perform normal activities for an adequate amount of time.

The battery life numbers advertised by a device's maker are a good start, but be suspicious of these figures. Mobile device review sites will benchmark the performance of more popular mobile devices and tell you how long they survived while performing some battery-sucking tasks like playing HD video. Know how long a given user's device will need to last on a charge, and try to make sure they get a device that can last at least 20 percent longer to account for how the battery's capacity will dwindle over its lifetime, known as its battery life.

If there's no existing device that can meet the user's needs most of the time, make sure they either have a device with a removable battery and a spare or have a portable external battery recharger. You can plug a mobile device into a portable battery recharger (sometimes called external battery, power pack, or portable charger) to recharge when there's no available outlet.

Managing Battery Life

There are two ways to think about battery life: how long it will last on each charge, and how long the battery can meet your needs before you have to replace it. Luckily, you can optimize both of these at the same time. When you waste battery life on device features you aren't using, not only will your device need to recharge sooner than necessary, but the extra recharge cycles will also shorten the useful life of your battery, also known as your battery health. Let's take a look at the biggest battery drains while keeping in mind that these are generalizations: check your device's battery usage monitor to see what is consuming most of its power.

Display  While it depends somewhat on how big your device's screen is and what kind of display it uses, the fastest way to drain most modern mobile devices is leaving the screen on. Keep the display off when you can, and use the lowest acceptable brightness setting. Because the screens look so much more vibrant at full brightness, there's a good chance this will be their default setting. The battery savings from using the lowest setting may be enticing, but the best compromise is usually to configure the device to control brightness automatically. Figure 25-4 displays the battery usage for an iPhone 13 Pro. Notice how much of the battery is being drained by the screen alone!

Figure 25-4  Battery usage for a smartphone

There are more options for optimizing how much power your display uses, though some of these differ by device or manufacturer. You can usually adjust how long the screen will stay on without input, and whether it will turn on when you receive a notification. Some devices have power-saving modes and may even be able to save power by displaying grayscale instead of full color. OLED displays use less power to display darker colors; if your device uses an OLED panel, you can also reduce power consumption by using black wallpapers and configuring apps to use a dark theme if the option is available.

Wireless Communication  To paint with a very broad brush, another big battery drain is the process of communicating without wires. It's good to keep in mind that every form of wireless communication your mobile device is capable of (such as cellular voice, cellular data, Wi-Fi, Bluetooth, Near-Field Communication [NFC], etc.) corresponds to a radio inside the device. In order to use that type of communication, the radio needs to be on and drawing power. If you aren't actively using that mode of communication but the radio is on, you're wasting power. Each communication technology draws varying amounts of energy under different circumstances, but here are two helpful guidelines: searching for signals is power intensive, and your device's apps will do more work in the background when connections are available.

Especially when traveling outside of populated areas, a mobile device can use lots of power talking with distant towers and base stations; this constant search can significantly drain battery power. You may be able to control this power drain through configuration changes that limit device roaming or searching for new wireless networks, but another approach is disabling these communications technologies until you need them or are back in an area with good coverage. You don't want to get stuck in the snow on a rural highway only to discover that your phone has almost completely drained its battery searching for cellular signals.

Even when the device maintains a strong connection, it constantly uses power to transmit and receive data. Having the connection available is often worth this slow drain, but beware that some of your apps will lightly sip power while disconnected and burn through much more doing background work when a connection is present. The easy way to rein this in is to disable communication, but the operating system (and sometimes the app itself) will have settings for controlling when an app can send and receive data in the background, and what connections it can use.

Location  While you can apply the same guidelines for managing GPS or location services, some small differences make it worth discussing separately. When location services are on, the device's apps can query the location of the device. Depending on how you've configured the device, it may approximate your location using low-power (less-accurate) methods like nearby cellular and Wi-Fi networks, higher-accuracy (higher-power) methods like GPS, or combine both of these. This could be for apps that require location data in the background, or for active apps, such as mapping software, that use the GPS receiver. The power drain here can vary widely between an app occasionally checking approximate location in the background, and one constantly requesting high-quality updates.

The simplest solution is to keep location services off when they aren't required, but you may be able to find a happy medium by setting per-app restrictions. When an app requires location data (common examples are apps for navigating, mapping, geocaching, or finding nearby users, restaurants, garage sales, or movie theaters) but location is disabled, the device will usually prompt you to turn it on.

Because apps for which location data is less critical may happily use a stale location, the best combination of trade-offs will ultimately depend on how you use your device and what apps you have running. If you regularly use the device to take location-tagged pictures cataloging graffiti or potholes, you may want the highest quality location data available at all times, regardless of the battery drain. Another tip is to review configuration settings for apps that use location services and disable the ones that don't need to have immediate location data.

EXAM TIP   Be familiar with the factors that can reduce battery power and battery life.

Charging Issues

Charging a mobile device is one of the most regular interactions a user will have with it. As a result, charging issues can arise, leading to inconvenience and frustration. There are a range of possible causes for improper charging, from something as simple as having too many apps running in the background, all the way to broken hardware in the device. Depending on the source of the problem, the device may charge slowly or not at all. Let's have a look at some of the main causes, how to identify them, and most importantly, how to fix them.

If your device is charging more slowly than usual, there are a few possibilities. The first thing to check is whether anything is using an unusually high amount of battery. Sometimes, resolving the issue is as simple as closing out of some background apps.

Slow charging can also be caused by issues with your charger or cable. If the charger you're using wasn't designed with the device in mind, or you're just using a cable you grabbed out of a drawer, it may not be able to provide enough power. You'll know fairly quickly if the phone is charging slowly; most devices display the estimated charging time somewhere, either on the home screen or in the battery menu in Settings. If you encounter slow charging and you've ruled out background apps, grab a different charger, preferably one that you know works with the device. If it charges normally, the issue was almost certainly with the charger or cable. If it doesn't, you may have bigger problems and should look to the device hardware.

NOTE   In Chapter 24 we talked about different types of ports you'll find on smartphones and tablets. Issues related to charging cables are especially common, particularly for smartphones, because people often use their devices while they are plugged in. The result is that the cables can end up fraying, or the connector can become damaged. If a charging cable that worked well suddenly starts charging slowly, it's very possible that it just didn't hold up to the higher amount of wear and tear mobile devices experience. If the cable is micro-USB, the odds of this being the problem are especially high.

If you've already ruled out issues with background battery usage, chargers, and cables, it's time to explore the possibility that the charging port itself has a problem. For example, you may have a physically damaged port. This is the worst-case scenario, because, as we discussed when we addressed field repair, mobile device hardware repair is very difficult without access to specialized tools and parts. If you closed out the extraneous apps, restarted the device, tested a few different charging cables, and the device still won't charge, there's really one more thing that you can test before its time to take it to a specialist. It may sound silly but try plugging the charger into a different outlet. I've plugged in my charger to one outlet, felt the creeping despair that comes with potential hardware issues, moved it to another outlet, and had the device charge normally. Sometimes the issue isn't with the device at all. If none of these steps work though, the device may require some form of specialized diagnostic or repair.

Swollen Battery

As we discussed in Chapter 23, one of the more insidious problems you'll see in mobile devices is a swollen battery. The main cause is overcharging, usually when the circuits designed to prevent overcharging fail. Non-OEM chargers or batteries, especially if they aren't rated for the correct voltage and wattage, represent an additional risk, as does overheating. Sometimes the battery is just bad. Overcharging has become less common as mobile device manufacturers continue to improve their hardware and implement software that helps to prevent it, but swollen batteries can still be a serious problem.

Prevention may be the best cure. Don't let batteries overheat, especially while charging. Prefer OEM chargers and batteries. Check the manufacturer's documentation for specific actions to take or avoid. Regardless, prevention can't always work, and swollen batteries may rupture, leak, and catch fire. It's important to be aware it can happen, vigilant for signs it is occurring, and careful when disposing swollen batteries.

Look for subtle clues, like changes in how the device's frame and screen come together, how it sits on a flat surface, how the back cover sits on the device, weird creaking or popping, inexplicable heat, and so forth. If the device has a removable cover, it's pretty simple to check the battery. If it doesn't, you may need to find a service center or a mobile technician who is comfortable taking the device apart to check.

When you encounter a swollen battery, dispose of it according to the recommendations in the "Try This! Recycling Old Portable Device Batteries" section of Chapter 23 and replace it with a known-good battery, preferably from the original device vendor.

CAUTION   You should never try to repair a battery under any circumstances, let alone when it's swollen, as it can cause bodily harm and damage to equipment.

Random Reboots and Freezes

A mobile device can randomly reboot or freeze up just like a desktop system (and for the same reasons). The main difference is that there aren't as many ways to successfully deal with a frozen mobile device. In that case, the immediate goal is getting the device back to a usable state. If the device isn't responding, you'll need to perform a soft reset, and without access to the OS you'll have to follow the manufacturer's steps for performing a soft reset---probably either by holding the power button for a few seconds or removing the battery.

NOTE   When a device seems to be frozen, there's also a chance the touchscreen just isn't responding. Check if the device responds normally to hardware button presses or enabled voice and gesture commands before assuming it is frozen.

If the device is still at least partially responsive, you can try to close an offending process from your list of recent apps. Even if you get the app to close, you may find the device unstable again as soon as you reopen the app. It's often best to save yourself wasted time: close the offending app, save any work in other open apps, and perform a soft reset.

When the device is usable again, there may be more steps to take. If you know the device rebooted or froze when you opened a newly installed or updated app, you may need to uninstall it and consider waiting for an update or looking for a replacement. Sometimes operating system issues can cause reboots and freezes, especially right after a device update, so look for follow-up OS patches correcting these types of issues. If the device randomly (and with increased frequency) reboots or freezes up, whenever using apps performing similar tasks (any app that uses the GPS or camera, for example), then your device likely has a hardware issue and needs service.

There's also a chance you'll find that the device is still unusable after the soft reset, in which case you'll need to look for the manufacturer's documentation on how to boot the device into any special modes that enable you to either remove an offending app, repair the OS installation, or reset the device to factory default. If this process also fails to render the device stable, you'll need to send it to a service center.

Cannot Broadcast to an External Monitor

Back in Chapter 24 we saw that some mobile devices have video output that enables you to broadcast the display onto an external monitor or projector. When done correctly, this is usually an almost automatic process: plug some adapter into your mobile device, plug that adapter into your external monitor's VGA, DVI, DP, or HDMI port, and it all just works.

Well, that's the theory. In reality, broadcasting your mobile device's screen to an external monitor is fraught with problems. While these vary by type of device, here are a few tried-and-true things to check when your device cannot broadcast to an external monitor:

-   Is your source correct on the external monitor? All monitors, TVs, and projectors have lots of inputs. Is the external monitor pointing at the right source?

-   Do you have the right adapter for your device? Apple alone has come out with five different types of video adapters in the last few years---and don't even get me started on the many adapters for Android! Make sure you have an adapter that is known to work for your device.

-   Does your adapter need its own power source?

-   For HDMI: Did the HDMI recognize your device and your external monitor? Depending on the make and model, you may need to reset one or both devices to give the HDMI time to see connections and set itself up.

No Sound from Speakers

Sound issues are also common on mobile devices. The most obvious (and probably most common) is that the volume was turned down or muted through software configuration or an app. This is easy to fix, but sometimes you have to go through many configuration settings for both the device and apps to figure out which one is controlling the volume at the moment or which one may actually be muting the speakers. A device may have separate settings for media, call volume, notifications, and more---and sometimes it's easy to change the wrong one.

The versatile nature of mobile devices means that we are often switching from one use to another. This can sometimes lead to people forgetting that their device was paired with some peripheral. One of the most common peripherals you'll see with mobile devices are wireless Bluetooth headphones. If you aren't getting any sound from the speakers, it may be a good idea to double-check for paired audio devices---the sound may just be coming from somewhere you didn't expect.

Some mobile devices also have hardware volume controls on them, so check them. If that doesn't work, then start going into the configuration settings for the device and apps. If none of these steps works, then you may have a hardware issue: the speakers have been damaged or come disconnected inside the device. As with all other hardware issues, you'll likely have to take the device to a service center for repair.

Connectivity and Data Usage Issues

General network connectivity issues---the kind that can affect all devices---have been covered elsewhere within the book. For mobile devices in particular, you should be aware of some additional network connectivity issues that you will likely encounter at some point. We'll discuss these in respect to cellular signals, but the first issue applies to Wi-Fi and Bluetooth network connections as well. For the most part you can't directly fix these connection issues, but you'll inevitably find a connection issue is responsible for some problem, or at least need to rule it out on the way to the ultimate cause.

One of the most prominent connection issues plaguing mobile devices is weak signal. The signal might be weak because you're deep inside a building, nestled between skyscrapers, crossing the no-man's-land between cell towers in sparsely populated areas, or any of a wide array of similar situations. The primary symptoms of a weak signal are dropped connections, delays, slow transmission speeds, battery drain, and frequent indications that the device is searching for a signal.

There isn't much you can do to troubleshoot a weak signal except monitor it. There are cellular signal boosters you can purchase, but these are of dubious value in some situations. These are most effective when the user is stationary in a location far from the cell tower, and usually aren't useful while the user is on the move.

NOTE   In addition to signal issues, performance problems on the device itself can cause the symptoms of slow data connectivity. We've covered these already, but they include high utilization of resources such as CPU, RAM, and network bandwidth, and a device's struggle to maintain a solid network connection.

Even if your signal is good, you may still run into connectivity problems---and they may be tricky to spot if you aren't aware of them. The first of these is an overloaded network, which is common during large public gatherings (such as a sporting event) or a widespread emergency that causes a surge in network use. Your device might have full bars but be unable to place calls, send texts, or transfer data. Another explanation for connectivity problems despite a strong signal are restrictions and limits the carrier enforces. You may experience slow data speeds while roaming just because the carrier of the network you are roaming on limits data rates for nonsubscribers. Exceeding the data usage limits that your carrier sets can also lead to slow data speeds.

The carrier will usually notify the user by e-mail or text message, but the user might not notice. What happens next is up to the carrier and the terms of the user's plan. Some carriers stop cellular data use beyond the preset limits, bill the user for additional data, or throttle the speed of the connection. Each causes complications, but you can minimize them by recognizing data caps. Configure data hogs like cloud storage apps to synchronize only on Wi-Fi, monitor data use and disable cellular data usage in the configuration settings of the device (see Figure 25-5) as needed, or pay to raise the data cap.

Figure 25-5  Option to disable cellular data in iOS

While the abstract side of data usage limits is important, the essential part is that you think about how these various scenarios could manifest on real devices. If you have a corporate plan, knowing the data limits and what happens when they're exceeded will give you a big leg up. What should you suspect when a user turns up at the end of the month with a device that suddenly has terrible call quality in Skype while using cellular data but works fine over Wi-Fi? Or a traveling employee says she keeps getting calls from colleagues asking why she hasn't weighed in on an important e-mail discussion that hasn't turned up on her device, despite a good connection? A quick check to see whether the user is over the plan limit could spare both of you hours of troubleshooting.

GPS and Location Services Problems

Sometimes the location services on mobile devices will be better at finding where you aren't than where you are. Some inaccuracy can be explained by the hardware a device has available; a Wi-Fi-only tablet with no GPS can get only a general location.

Symptoms of location issues can vary depending on what apps are trying to use location services. Photos might end up tagged with the wrong location, or the coffee shop you picked because it was closest might actually be further away than your device suggests. A navigation app might have trouble identifying your location at all, or it might be sure it knows where you are even when you know you're blocks away. Other symptoms can include prompts and error or informational messages from the OS or apps that rely on location data (see Figure 25-6).

Figure 25-6  GPS prompt

Troubleshooting location problems begins with simple actions such as making sure that your GPS, cellular data, and Wi-Fi are turned on and functioning properly, as sometimes these services can be inadvertently turned off by the user or by an app, and have to be periodically reactivated. Typically, a warning message will indicate that GPS or data services are turned off, so this is easy to identify and fix. Specific apps may have trouble if they are configured not to access or use location services. This is usually a matter of going into the app configuration or location settings and allowing the app to make use of those services.

EXAM TIP   If you run into GPS error questions on the exam, remember that all apps will tell you if GPS is turned off and usually ask you if want to turn on GPS. Otherwise, before digging deeper, first consider simple issues such as whether you are in a place where you can get a good GPS signal.

Once you've checked the obvious software reasons for location trouble, it's a good idea to think about the physical environment before you go on a wild-goose chase. GPS won't work underground, will probably be spotty indoors unless you're near a window, and can really struggle in dense urban areas with tall buildings. Don't be spooked into a long search for subtle GPS problems if your device occasionally has trouble deciding which downtown street you're strolling along.

When you're sure there are frequent location problems unexplained by the environment, it's time to dig deeper. Along with the OS issues discussed previously, incorrect OS configuration settings for GPS, cellular, and Wi-Fi services may prevent location services from functioning properly. These configuration items should be checked when multiple apps are having location issues.

If the issues persist, there's a good chance the problem is in the actual GPS or network hardware inside the device, or the OS code that interfaces with it. Look online to see if other device owners report similar trouble on the same device software versions. If you don't see other reports of trouble, the device likely needs a trip to the service center. Although mobile devices may have removable network or GPS modules in them, most of these components are not user serviceable and have to be replaced or repaired by authorized service technicians.

Encryption Problems

Methods to secure e-mail messages from anyone but the intended recipient generally fall well outside the accepted parameters of the CompTIA A+ certification, but it's useful to know how to troubleshoot mobile device encryption issues. To understand the issue, we'd need to dive into a number of topics you won't see until you take the CompTIA Security+ exam. Instead, let's focus on the basics.

For an e-mail message to be secure, it must be encrypted---scrambled according to some kind of standard, such as Pretty Good Privacy (PGP) or Secure/Multipurpose Internet Mail Extensions (S/MIME). For the recipient to read the e-mail message, he or she needs to have software that can unscramble or decrypt the message. To ensure the sender and recipient alone can access the contents of the e-mail message, both people need specific keys that enable encryption and decryption. A key is a string of bits used by a computer program to encrypt or decrypt data.

In practice, there are a few reasons a mobile device won't be able to decrypt an e-mail. The simplest of these is that the e-mail client or application doesn't support the encryption standard used to encrypt the message; the fix may be a plug-in or an entirely new client. Once you confirm that the e-mail client or app supports this encryption method, follow any steps for configuring the client to use it. Finally, the e-mail client will need access to keys for decrypting the message. With some standards, keys may always be exchanged manually; someone will need to contact the sender to exchange keys. In other cases, keys may be exchanged automatically in at least some circumstances (if you're part of the same organization, for example).

Securing Mobile Devices

Just like any computer we use to input or access sensitive data and network resources, we need to secure our mobile devices. Whether the device is company owned or personal, we still need to protect ourselves from the needless inconvenience of easily prevented damage, theft, or malware infections, as well as from the chance of important data being lost completely or falling into the wrong hands.

BYOD Versus Corporate-Owned Devices

The bring your own device (BYOD) war was briefly fought and lost by organizations hoping to continue the long-held tradition that IT assets belonged to (and were strictly controlled by) the company, not the individual. As mobile devices proliferated, however, IT folks realized the genie was out of the bottle; they couldn't control these new technologies completely. Some companies enforce a policy prohibiting the use of personal devices to access corporate data and resources, particularly in high-security environments. Companies at the other end of the spectrum allow (and even encourage) the use of personal devices to save corporate IT dollars and keep employees happy.

Most organizations fall in the middle of the spectrum and have a mixed environment with both corporate-owned and employee-owned mobile devices. Some organizations institute a cost-sharing program, subsidizing an employee's personally owned device with a monthly phone stipend or discount agreement with mobile device and telecommunications vendors. Regardless of how comfortable an organization is with BYOD, there are important questions to answer.

One question is how much control the corporation has versus the individual. If corporate data is processed or stored on the device, the organization should have some degree of control over it. On the other hand, if the device also belongs to the employee, then the employee should have some control. Another question is who pays for the device and its use. If the organization allows the user to use her own device for company work, does the organization help pay for the monthly bill or compensate the user for its use? Again, this issue is best solved via formal policy and procedures. Yet another important question in a BYOD environment is how to handle employee privacy. If policy allows the organization some degree of control over the device, what degree of privacy does the user maintain on her own device? Can the organization see private data, or have the ability to remotely access a user's personal device and control its use?

The proliferation of mobile devices in the workplace has led to the development of mobile device management (MDM) policies that often combine a specialized app on the devices and specialized infrastructure to deal with those devices. These policies also inform corporate versus end-user device configuration options; in other words, who should make configuration decisions on things such as e-mail, wireless access, and so forth. As you might imagine, MDM policies are a big deal at the big organization level (the enterprise) because of the scale and complexity of the issues. A CompTIA A+ technician comes in to facilitate the installation of the MDM app, for example, or to help fix key infrastructure problems (like an overloaded WAP because all 25 members of a department bought Apple Watches at the same time). Mobile device management isn't always necessary. Sometimes, the organization is concerned just with a specific app or group of apps. In this case, you'll find the use of mobile application management (MAM).

EXAM TIP   Both mobile device management and mobile application management are included in the CompTIA A+ exam objectives for a reason. They sound similar but serve different purposes. MDM is for entire devices, while MAM is for specific applications used by the organization. Keep this in mind so that you don't get them mixed up on the exams.

Profile Security Requirements

A profile is a collection of configuration and security settings that an administrator has created in order to apply those settings to particular categories of users or devices. A profile can be created in several different ways, including through the MDM software, or in a program such as the Apple Configurator, for example. Profiles are typically text-based files, usually in an eXtensible Markup Language (XML) format, and are pushed out to the different devices that require them. Profiles should be developed based on the needs of the organization. You can develop a profile specific to certain platforms, operating systems, or devices, so that a particular type of device will get certain settings.

You can also develop profiles that are specific to different user categories or management groupings (such as mobile sales representatives, middle managers, senior managers, and executives). Your senior organizational executives might have a specific profile applied to their devices granting them additional permissions and access to special apps or connections.

You might also apply group-specific profiles to external users, such as consultants or business partners. These users may require limited access to organizational resources using their own mobile device, their organization's mobile devices, or even mobile devices temporarily issued by your organization. A group-specific profile applied to these external users may give them particular network configuration and security settings so that they can access a business extranet, for example, or use specific VPN settings. They may also require access to particular enterprise or business-to-business (B2B) apps hosted on your organization's servers. In any case, both device- and user-specific profiles can be very helpful in managing larger groups of users, delivering uniform security and configuration settings to their devices based on different mission or business requirements.

Depending on your organizational needs, you could conceivably apply several different profiles to a device at once, based on platform, user group, and so forth. When multiple profiles are applied, there's a chance some settings will conflict. For example, some restrictive settings for a device profile may not be consistent with some less-restrictive ones in a group or user profile. When both are applied to the device, the different configuration settings may conflict and overwrite each other. The solution is to pay special attention to profile precedence and configure the MDM server to resolve conflicts using criteria such as user group membership or security requirements.

You should also develop profiles that apply to corporate-owned versus employee-owned devices. A profile applied to a device in a BYOD environment may be considerably different than one applied to a company-owned device. This would be based on policy settings affecting privacy, acceptable use of the device, and so on. Figure 25-7 shows how you can conceptually apply different profiles to different device and user groups.

Figure 25-7  Applying profiles to different device and user groups

Preventing Physical Damage

For something shaped a lot like a bar of soap and sometimes almost as slippery, mobile phones can cost a lot of money. That means you need to take steps to prevent damage. The first step you should take to protect your slippery investment is a case, protective cover, or sleeve for the mobile device. It doesn't help the HD camcorder in your new iPad if you get a scratch across the lens! You'll get a scratched, blurry movie even though the camcorder is capable of much, much more. Apple makes very nice covers for iPhones and iPads, plus you can get many third-party covers and sleeves (see Figure 25-8).

Figure 25-8  Putting an Apple Smart cover on an iPad

Depending on the amount of money you're willing to spend, you can get a cover that helps protect your screen from scratches, impacts, and small amounts of water. Like to scuba with your Android device? Get a specialty waterproof case and go post your deep thoughts to Facebook from 40 feet underwater.

Do the obvious to protect your devices. Don't get them anywhere near liquids. Don't run your smartphone through the wash in your trousers. Don't even think about placing heavy objects on that ~$600 tablet! Use common sense.

Combating Malware

Malware on mobile devices is an interesting issue. Tight controls on the OS and apps make traditional malware infections almost impossible on iOS and Android devices. When malware strikes, the OS maker supplies periodic OS updates, automatic updates and operating system patches. Android's more open nature means there are third-party antivirus and anti-malware single-user (user-level) and enterprise-level solutions available if you have corporate regulations that require such software. Figure 25-9 shows an example of user-level antivirus software for an Android device.

Figure 25-9  Antivirus app for Android

NOTE   We discuss operating system updates and their importance to security in detail in Chapter 27. Be aware that OS updates are just as important for mobile device security as they are for desktops and laptops.

In an ideal world, your mobile anti-malware software will cover all threats and work on all the devices used in your corporate network. In a heterogeneous real-world infrastructure, because there may be a variety of mobile devices from different vendors using different operating systems, a one-size-fits-all anti-malware solution probably won't work. Multiple solutions may be necessary for the different devices present on a network, or different modules covering specific types of devices may be available from the vendor to integrate with an enterprise-level anti-malware solution.

In any case, the most important part of an enterprise-level anti-malware solution is delivering timely updates to the devices on a routine basis. Network access control (NAC) solutions can ensure a device is checked for the latest anti-malware signatures and updated as necessary when it attempts to connect to the network. In the case of user-managed devices, you may need policy, NAC, and other technical solutions to ensure users are updating their own devices in a timely manner.

NOTE   Chapter 27 goes into much depth on malware, including the types of malware as well as the most common sources and symptoms of malware infections.

Dealing with Loss

The best way to make sure you're ready to survive losing a mobile device is to assume it's inevitable. Say it to yourself: every mobile device will get lost at least once. I hope most of your users will prove you wrong, but the odds are good we'll all misplace every device we own at least once. Most of us will be lucky and find it right where we left it, but it could just as easily go the other way.

When you start with the assumption that your device will end up at the mercy, kindness, or ignorance of strangers at least once, it's obvious: you should protect your data from access by putting a good screen lock on the device. Most mobile devices enable you to set a screen lock through Settings (see Figure 25-10). Do it right now! There are many types of these locks; the most common require you to input a password, PIN code, pattern, fingerprint, or successful facial recognition to unlock the mobile device so you can use it. Modern iOS and Android use device encryption to protect the built-in storage, so even a "finder" who dismantles the device to access the drive will not get your documents.

Figure 25-10  Passcode (screen lock) option in Settings

As we discussed in the "System Lockout" section earlier, mobile devices may also have failed login attempt restrictions which restrict the number of login attempts that can fail before system lockout occurs. This system lockout slows down someone trying to guess the passcode of a found mobile device while you use locator applications or services to recover or remotely wipe it.

EXAM TIP   For the purposes of the CompTIA A+ 1102 exam, know that fingerprint lock, facial recognition, pattern lock, swipe lock, and PIN code are screen lock methods used to secure mobile devices.

Apple and Google offer locator services for discovering the whereabouts of a misplaced mobile device. Using Apple's iCloud as an example, log in to your iCloud account and click the Find My iPhone button (despite the name, it also works for iPads). As soon as the device in question accesses the Internet (and thus receives an IP address and posts its MAC address), iCloud will pinpoint the location within a few yards (see Figure 25-11). Very slick!

Figure 25-11  Locating a phone in iCloud

Recovering from Theft

If your mobile device gets stolen and contains sensitive information, then you have a couple of options for dealing with it. Locator applications and services help, but if you have credit card information or other risky data on your mobile device, you need to act quickly.

First, make sure you keep your data backed up. You should have everything synced to a local machine and, if possible, backed up to one of the remote backup applications---like Microsoft's OneDrive cloud service---to put your data beyond the reach of even a disaster that takes out your house. With Apple devices, for example, you back up and restore with one of several services, such as iCloud or iTunes, or use the Apple Configurator to handle a fleet of iOS devices. Android devices use the Google Sync feature to back up and restore.

Second, you can remotely wipe your mobile device. Apple, for example, makes it supremely easy through your Apple account. Log in, locate, and nuke your device (see Figure 25-12). You may never get the device back, but at least the bad guys won't have your data. It's equally simple with Android devices. Log in and follow the same process---locate and nuke.

Figure 25-12  Erase iPad

Securing Your Data

Every security scenario we've discussed so far (remote wipe excepted) was designed to secure the device itself. Let's turn to how we can protect our actual data.

Multifactor Authentication

The terms multifactor and single-factor authentication make the difference obvious enough: the number of factors used to authenticate the user. What the terms don't make obvious is what exactly an authentication factor is, and why one of the most popular authentication schemes---a username and password---is a kind of single-factor authentication. Let's start with the factors. First, there is the knowledge factor: something the user knows, such as a username, password, date of birth, Social Security number, and so on. The second factor is ownership or possession: something the user has in her possession, such as a smart card or token. A third factor is inherence: something the user either is or something they do. An example of an inherence factor is a biometric identifier, such as a fingerprint or retinal pattern. You commonly hear these three factors referred to as something the user knows, something the user has, and something the user is.

Other authentication factors exist but are not as commonly considered in security authentication. For example, there's the location factor: somewhere you are. This can be used if the individual's location can be pinpointed via GPS or some other method. The individual may be required to be at a certain location in order to log in to the system, for example. Yet another is the temporal factor. As the name implies, schemes using the temporal factor may require logon at a certain time of day, or even within so many seconds or minutes of another event. Token methods of authentication also use time factors, as the PIN displayed on a token is only good for a finite amount of time.

Armed with the factors, let's consider authenticating with a single factor. The most common schemes require a username and password; both are something you know, so the scheme uses a single factor. You can also think of a traditional door lock as single-factor authentication; the key it requires is something the user has---a possession factor.

During the initial push to move beyond single-factor authentication, the term two-factor authentication grew common---and you'll still hear people use this term. Over the years, however, authentication methods using more than two factors have grown increasingly common, so it has become more correct to say multifactor authentication. Multifactor authentication (MFA) can use a variety of methods, as long as it uses more than one.

Just because the term sounds fancy and might make us think of complex systems at secret government installations, don't assume multifactor authentication hasn't played a role in everyday life for decades. For example, when you use a bank's ATM, you're using MFA: something you possess (the ATM card) and something you know (the correct PIN).

EXAM TIP   Don't confuse the username and password combination with multifactor authentication. Only one factor is being used here, the knowledge factor, making this a form of single-factor authentication.

Biometric Authentication

Combined with other authentication factors, biometric elements can provide a very secure multifactor authentication mechanism. An example of biometric authentication is presenting a smartcard to a proximity badge reader and then placing your finger on a fingerprint reader to access a secure area.

NOTE   Not every type of biometric authentication is a good fit for mobile devices. You'll get a closer look at the different types and other uses for them in Chapter 27.

Mobile devices use biometrics, too. Laptops have included fingerprint readers for several years already, and they are common in other mobile devices such as smartphones. A prime example is Apple's Touch ID; starting with the iPhone 5s, the iPhone can unlock with a fingerprint. Current iOS devices use facial recognition to identify and authenticate users. Check out Figure 25-13.

Figure 25-13  Face ID options

Authenticator Applications

Access to third-party or corporate networks often requires strong authentication methods. Access to a corporate VPN, for example, may require a specific app, approved and published by the organization, configured with the correct security settings. Generic apps have the ability to use multiple sets of credentials to access different Web sites, networks, or network-based services (for example, corporate e-mail, VPN access, and so forth). There are also apps that can act as tokens or issue temporary session PINs for multifactor authentication. The key to these apps is configuration; settings vary per app, but might include network configuration, authentication or encryption settings, and properly registering a given service with the authenticator app. You'll get a further look at authenticator applications in Chapter 27 as well.

Trusted Sources Versus Untrusted Sources

For the most part, getting software from trusted sources---legitimate app stores run by the major vendors, such as Apple, Google, Microsoft, and Amazon---is both easy and secure. Different vendors have their own requirements (including security) that developers must meet in order to get an app into the vendor's store. Most differences stem from the development and support model used by the vendor.

Apple strictly controls all aspects of the device and the apps available in the App Store (though organizations have some freedom to distribute apps developed in-house to their own devices). For example, Apple has exact requirements for how developers must create an app sold via the App Store. Android, on the other hand, has much less central control. One way Android's relaxed controls manifest is the ability to install apps from untrusted sources.

The operating system flavors developed by different Android device makers can change which sources are and aren't trusted. What may run on devices sold by one vendor isn't necessarily guaranteed to run on another vendor's device, even though they all use variations of the Android operating system. A prime example is Amazon's line of Fire devices (including products like Fire TV and Fire Tablet), which can only get apps from the Amazon Appstore. Additionally, even apps from the Google Play store aren't subject to guidelines as strict as the ones Apple uses. That doesn't mean they are necessarily less secure, but it does make security issues more likely.

The security weakness third-party app stores create is essentially apps from unapproved or unofficial sources. There are definitely legitimate app sources outside of Google Play, such as device manufacturers, communications carriers, and in-house corporate development sources. Some sources are not so legitimate, and are usually unapproved by the vendors, manufacturers, and corporate customers. You may also need to modify your mobile OS to run some apps you obtain through unofficial channels. These third-party apps may be perfectly fine, or they may be malicious and pose a security risk to your device or organization. See "Unauthorized Root Access, Developer Mode, and Sideloading," later in the chapter, for more details.

When getting apps from questionable sources, risks include apps that contain malware or steal personal data and transmit it to a third party. Additionally, some apps require replacing the operating system with one that's not approved by the vendor; this not only invalidates the warranty on most devices, but could cause the device to be unstable and not operate properly.

Firewalls

While we'll discuss them in greater depth in Chapter 27, for now it's enough to know that software firewalls on individual hosts protect them from network-based threats. It isn't completely clear what CompTIA expects you to know about firewalling mobile devices. Generally, mobile devices don't use a firewall, because they don't have lots of services listening on open ports (like a traditional computer would). But, because they aren't listening, you can think of them as having a de facto firewall. The cellular and Wi-Fi networks mobile devices use also employ firewalls to protect all networked devices.

Depending on the OS, you may be able to find and install more traditional software firewall packages. One example of a software firewall for Android is shown in Figure 25-14. Android software firewall packages include basic rule elements for constructing rules to filter specific traffic coming into the host. Many of these packages also include solutions for anti-malware and basic intrusion detection.

Figure 25-14  An Android firewall app

Some of these software firewall solutions are standalone and must be configured and managed by the user, whereas some are enterprise-level solutions and can be centrally configured, updated, and managed by the systems administrator. Keep in mind that software firewall packages work at a very basic level and can't possibly contain every single network threat. Still, they serve as a second line of defense for the host, and are part of any good, layered, defense-in-depth security design.

Mobile OS and Application Security Issues

Security is a complicated, ever-evolving topic. We've already discussed aspects of mobile device security at various points in the chapter, but there are some additional security issues the user and organization need to be aware of and take steps to prevent. We'll begin with a discussion of tools you can use to troubleshoot mobile OS and application security issues broadly, and then turn to some of the common risks, symptoms, and clues related to mobile security issues.

Troubleshooting Tools

While the foundation of good security is staying informed of new threats and being vigilant about the patches, configuration updates, policy changes, anti-malware updates, and user re-education required to address these new threats, this foundation boils down to not giving attackers an easy win. Beyond this, we have to cope with security issues that require constant vigilance: novel threats, avoiding insecure applications, and irresolvable vulnerabilities.

Though your greatest assets are your own curiosity, instincts, and persistence, you can augment these with a variety of technical tools for troubleshooting mobile security issues. Let's look at some of these tools, grouped in terms of the issues they are most useful in addressing: network attacks and app security.

Network Attacks

Device makers originally designed mobile devices to be gregarious by nature---they are more useful this way---but network attacks can exploit such openness. We'll consider specific issues a little later in the "Unintended Connections" section and focus now on tools for identifying and mitigating risks: device security settings, user training, Wi-Fi analyzers, and cell tower analyzers.

Device Security Settings  Because network attacks generally prey on devices that are overeager to connect, the first step to mitigating these threats is to make sure your devices won't automatically connect to any open Wi-Fi network or nearby Bluetooth device. You can apply these settings manually on each device, but you can also use MDM software or similar software made for managing more than one device, such as Apple Configurator.

User Training  It won't help (much) to configure your devices to avoid automatic connections if your users still select any open Wi-Fi network or agree to any pairing request without considering the consequences. Similarly, your network will be at risk if your users don't recognize any of the warning signs that their connection to your organization's secure Wi-Fi network has been intercepted by an evil-twin wireless access point (WAP). Teach them what is normal, and train them to stop and report anything that seems out of place.

Wi-Fi Analyzer  In addition to using a Wi-Fi analyzer for tasks such as figuring out what channel a network should use, optimizing WAP placement, or finding dead spots, you can use one to map out nearby networks (see Figure 25-15). Most of these are probably genuine networks in neighboring buildings or offices, but there's always a chance someone will set up a WAP for the wrong reasons.

Figure 25-15  A Wi-Fi analyzer app on Android showing several SSIDs in the area

Cell Tower Analyzer  Like a Wi-Fi analyzer, a cell tower analyzer helps identify nearby cellular signals, estimate their distance and direction (see Figure 25-16), measure their signal strength, and collect other information such as the technologies they are using, network names, and more. A simple use might be to confirm signal quality for a user having trouble connecting, or to map out access in the building. There's also a chance you'll spot an illegitimate tower operating nearby---and your organization might be the target.

Figure 25-16  My Android-based cell tower analyzer estimating the location of a cell tower

App Security

One of the important things to understand about malware is that the "best" malware accomplishes its objective without anyone detecting it. Almost anyone could figure out that malware is to blame for a device that runs like it's full of molasses and constantly redirects your searches or Web requests to sites that announce that you've won a round-trip to Mars. Because the most dangerous malware is subtle, you need to use tools to help you catch the easy stuff, freeing your attention to see subtle signs something is amiss.

Anti-Malware and App Scanners  Mobile anti-malware apps, much like their desktop counterparts, use signatures and lists to scan a device in order to identify, block, remove, or warn about known malware. An app scanner, by contrast, looks through the permissions requested by your installed apps to assess the risk they pose to security and privacy. You may find some separate apps for performing each of these tasks, or combined apps that can do both. You won't find these apps available for iOS, but many of the same features are available through the Settings app.

App scanners typically run before an app is installed or updated and can give you information such as what network connectivity the app requires, what permissions it needs, and what access the app has to certain hardware and functions on your device. App scanners can also tell you what type of data access the app has to your personal information, such as contacts and media files (see Figure 25-17).

Figure 25-17  Combined anti-malware and app scanner

The usefulness of app scanners as a security tool becomes more apparent if you think of every installed app as posing a few different risks. First, there's the direct risk that the app is designed to spy on you or steal your data. Next, there's the risk that the app maker will lose control of your personal information once it leaves your device. Finally, there's the risk that a vulnerability in the app will allow an attacker to use it against you.

Some users are savvy enough to avoid directly installing malware. But how many of those users know enough to assess the risk that an attacker in the future will be able to exploit a vulnerability in an app they're installing today? And what about malware that doesn't require the user to do anything at all for it to find its way onto their device?

NOTE   Malware is always evolving, and always being developed. Sometimes, the software isn't necessarily intended to be used maliciously. A high-profile example of this was software known as Pegasus. Originally designed to be used by law enforcement agencies to address terrorism and organized crime, it also ended up being used to spy on journalists, activists, and even world leaders. The scariest part was that it didn't require the user to click or install anything in order to get to a mobile device and start spying. This is an example both of how insidious malware can be and how important it is to stay vigilant in securing and monitoring devices.

Remote Backup Applications  Maintaining a current backup of your device is one measure you need to take in case all else fails. Different tools used to perform remote backups and restore data include MDM software, iTunes, and the various synchronization tools for Android; another option is to back up the data to the manufacturer's or third-party user cloud storage, such as Microsoft OneDrive or Apple iCloud.

Some malware can put down deep roots and be hard to expunge. A recent full backup predating the infestation can give you the confidence to focus on making sure you get rid of the malware, rather than focusing on being sure you don't lose important data.

App Troubleshooting Tools  We've already looked at tools for troubleshooting general mobile device and app issues: force stop, uninstalling and reinstalling apps, and a factory reset. You can also use these tools to pinpoint and address app security issues.

Whenever you see clues or symptoms of malware or another app security issue, remember that one way you can isolate the cause is to stop apps until you identify the cause. When you know what is causing the symptoms, uninstall it. If the app is reputable and the symptoms could be non-malicious, reinstall it to see if this fixes the problem. If these steps don't resolve the behavior, use a factory reset to cleanse the device.

Risks, Symptoms, and Clues

The value of your curiosity, intuition, and persistence begins to show in a big way when we look at the risks, symptoms, and clues that malware or some other security problem is present. When you read about a potential risk here, don't assume you'll only see it by itself. Because malware and other attacks can be creative, complex, and multifaceted, view the scenarios discussed in the following sections as risks to understand and manage, symptoms of malware or an attack, or merely clues of an attack underway.

Much like you shouldn't assume you'll see these things as isolated incidents, you shouldn't assume when you encounter one or more of them that malware or an attack is necessarily present. In fact, we've already discussed many of the issues in this section as they relate to other kinds of mobile device problems.

Unexpected Resource Use

If you think about it, malware is just software or a program that uses your device for work or tasks you don't want it to do. Like any program working hard, malware can cause resource issues. Because resource issues can also be relatively benign problems fixed by a soft reset, it's easy to shrug them off. Be suspicious, especially if you see patterns and can't find an obvious explanation; the first clues of an ongoing attempt to spy on your company may well be an uptick in data outbound from affected cellular devices.

Sluggish Response Time  A hot phone, high resource use, and excessive power drain can be common signs that an app is frozen or malfunctioning, but they might also be symptoms that your device is doing precisely what a malware developer intends. The device might be hot, have sluggish response time, or be low on battery because it's a live recording device uploading everything it records in real time, or because it's copying files available on the network to a remote location.

High Network Traffic  Likewise, high network traffic can cause network issues, signal-quality problems, frozen apps, regular syncing of large files---or a sign the device is busy uploading or downloading something without your knowledge. High network traffic may also clue you in to one or more devices that are attempting to use an illegitimate WAP or cell tower that has a lower capacity than its official counterpart.

Data-Usage Limit Notification  As discussed earlier, a data transmission limit is a line in the sand that indicates when a device has used more data than its plan or carrier allots for it. Perhaps the user drove across the country while listening to Spotify, or perhaps the device is uploading stolen data from the device and other networked locations. If you see an inexplicable data-usage limit notification, it may be time to start checking the mobile device for malware.

Unexpected Behaviors

Security threats don't only cause unexpected resource usage, they can also cause unexpected device and application behavior. Much like their desktop counterparts, mobile devices can start to behave strangely when they are infected with malware. A high number of ads, fake security warnings, and unexpected application behavior from individual apps can all be indicators of a security issue, whether it's malware or breached credentials. These issues will be explored in greater detail in Chapter 27, but be aware when you take the CompTIA A+ exams that these issues can also indicate that your mobile device is compromised. As with other computing devices, if you start to see any of these signs, consider scanning for malware as part of your troubleshooting efforts.

Unintended Connections

A major security issue is unintended network connections (such as cellular, Wi-Fi, and Bluetooth). Unintended cellular network connections aren't common since these are preprogrammed into the phone by the carrier and periodically updated, but there is a technique called tower spoofing that involves setting up equipment to spoof a carrier's tower and infrastructure and cause a cellular device to use it instead of the normal tower equipment. It requires overpowering the nearest legitimate cell signal, causing the cellular device to lock onto it instead. Equipment used in tower spoofing can also eavesdrop on any conversation, even if it is encrypted. In some cases, the equipment can fool the device into turning off encryption completely---and sophisticated attacks can even install malware on the device.

Just as hackers have been using this technique for a few years, law enforcement officials have been reportedly using it as well. Since 2010, there have been numerous court cases highlighted in the media questioning the admissibility of evidence obtained from cell signal interception. Media reports say various federal, state, and local law enforcement agencies use a device called a "Stingray" to intercept a suspect's cell traffic using tower spoofing equipment and techniques. There's even an aircraft-mounted version, known as a "Dirtbox."

NOTE   Though much of the news coverage on tower spoofing focuses on U.S. law enforcement agencies using the Stingray, you could just as easily encounter malicious cellular or Wi-Fi networks run (for a variety of reasons) by individuals, businesses, organized crime, and governments anywhere in the world.

Unintended Wi-Fi connections and unintended Bluetooth pairings can enable malicious people to access, steal, or modify data. Configure your mobile device not to connect to unknown Wi-Fi networks or automatically pair with other Bluetooth devices. This will require you to manually connect to known and trusted Wi-Fi networks, and manually pair with Bluetooth devices---but it's worth it. If the device is centrally managed, MDM software can enforce these protections via profile settings.

Connectivity Issues

Earlier, we looked at dropped and weak signals in terms of their impact on battery life, power management, and running apps. Sometimes these signal issues go unnoticed or are only a minor inconvenience. When it comes to cellular signals, they can also be one of the few clues you'll get that your device is interacting with a spoofed cell tower.

If you or your users are in an area where the signal quality should be (and usually is) excellent, be curious---especially if you have multiple reports of difficulty. Check with the relevant cellular providers to see if they have any known tower issues in the area. Fire up a cell tower analyzer and compare nearby signals with what you've seen in the past, or with third-party resources online.

If users are suddenly reporting that Wi-Fi quality is low in an area where it was high, or you notice your device sees a network with a strong signal and the correct SSID in what used to be a dead spot, check it out. There may be a rogue WAP on the loose. Limited or no Internet connectivity can be a tricky problem to troubleshoot. As you've seen both earlier in the book and here in this chapter, there are many potential causes, but if you've ruled out hardware problems and provider issues and are still having limited or no connectivity, it may be time to investigate a security issue as the potential culprit.

Unauthorized Data Access

Securing data stored on a mobile device is hard. The building's security guards might stop a courier from walking out with a desktop under his arm, but they probably won't notice an extra phone in his pocket. Even if they do, he might just confidently claim he has to carry an extra phone for work and go on his way. If I accidentally leave my phone behind at lunch, there's a chance I won't notice until I head to my car that evening. Device locks and remote wipe can usually prevent unauthorized users from accessing data on a mobile device---as long as you wipe the device before it is compromised.

Data can leak out other ways, though, such as removable memory storage cards, and data sharing settings in the device's OS or applications. Removable memory cards should be encrypted if they contain sensitive data, so an unauthorized person can't access data if they are removed from the device. Security and privacy settings on the device can help protect personal data, and the same settings can be configured in different apps that need to access personal data.

One of the more obvious risks to every networked app with access to data is the possibility that it will leak some of that data (whether intentionally or not). In some cases, it can be hard to figure out where the leak is. If an attacker used tax returns you stuck in Dropbox to obtain a loan in your name, where and when did the data go? You had local copies on your phone, laptop, and desktop, plus what was available if your Dropbox credentials were compromised, and any copies that transited over the network. Perhaps the attacker stole them directly from the company that did your taxes.

The point is that leaked files are a risk, a potential symptom of an ongoing security issue, and a possible clue to what that issue might be. A full audit of the many ways an important file could've leaked out of a networked environment is beyond what can be expected of a CompTIA A+ tech, but he or she may well get the first chance to escalate the issue or write it off as a compromised login and make the user change passwords.

EXAM TIP   Portable and mobile devices present amazing opportunities for your personal information to become much less personal and a lot more public. The CompTIA A+ 1102 exam calls this "leaked personal files/data," but it could just as easily be translated as "your phone password wasn't strong and you left the phone in a kiosk at the ski resort." (Not that this has ever happened to me.)

Unauthorized Account Access

Unauthorized account access is a big deal not only for the mobile device itself, but also for all organizational networks it can connect to. If someone steals the account credentials or is able to access a mobile device configured to remember the credentials, then they have an entry point into an organizational network. As discussed earlier, you should plan based on the assumption every device will be lost.

To keep VPN and e-mail connections secure, the device should not store usernames and passwords for connecting automatically. This way, lost or stolen devices can't be used to access these services (at least not without also stealing credentials) because they still require authentication. Unauthorized account access can lead to a malicious person stealing or accessing data not only on the device, but also on the larger network.

When a device is lost, act with an abundance of caution. Treat the previously described precaution as something to protect you until the device is reported missing. Once you know it is missing, change the user's credentials. Keep in mind that compromised account credentials could also be a clue that one of the user's devices itself has been compromised and may be an ongoing threat to the organization.

Unauthorized Root Access, Developer Mode, and Sideloading

To help secure the device, mobile operating systems all restrict the actions (such as installing apps or changing settings) that a user can normally perform. There are ways around these restrictions, though the name of each method differs by OS, depending on how the OS restricts what the user can do. To fully remove these restrictions, a user may have to jailbreak (iOS) or root (Android) the device. Android also has two less intrusive options: developer mode and sideloading. Let's take a look at each.

EXAM TIP   Know jailbreak, root access, and the OS associated with each, but keep in mind that it's common to see both of these terms used in relation to removing access restrictions from any given device.

Jailbreaking means the user installs a program on the iOS device that changes settings Apple didn't intend for users to change. Jailbreaking allows a user to install blocked software, such as apps that don't come from the App Store or apps that don't meet Apple's legal and quality requirements. Jailbreaking also enables a user to unlock functionality on the device.

Rooting an Android device is a similar procedure to grant the user full administrative access to the lower-level functionality of the device. As in the case of jailbreaking, this is also done to install software or enable functions that could not otherwise be used on the device. Although none of the popular Android device vendors condone rooting, they have little recourse beyond voiding the warranty if the user owns the device.

Developer mode is another Android-specific mode, but unlike rooting, it doesn't present the same level of catastrophic risk that rooting can. You don't void your warranty, you don't leave your phone unusable if you make a mistake, and you don't introduce major security risks. However, a user who isn't familiar with developer mode options may end up changing settings that make using the device more difficult. Developer mode gives users access to features like USB debugging, more advanced resource monitoring, and the ability to go a step farther by rooting the device. As a result, developer mode doesn't present its own security risks, but it does give Android users access to functionality that might.

In the same vein, another unique aspect of Android when compared to Apple's mobile OSs is the ability to sideload applications without using a dedicated app store. Sideloading allows an Android user to use a file called an Android package (APK) to install an app that they got from a Web site or source other than the Google Play store onto their device. Sideloading can have some advantages like allowing a user to bypass geographic limitations or install software that was previously available on the app store and removed for whatever reason.

Sideloading also comes with security risks. Some APKs can be bootleg applications, which can pose legal issues. Other APKs may be malicious applications, designed to act similarly to a Trojan horse (explained in more detail in Chapter 27). Application spoofing can be a very dangerous attack method when used against mobile devices, as many people wrongly assume that mobile devices aren't vulnerable the same way desktop and laptop computers are. As with any other class of devices, a false sense of security can lead to real-world security problems.

The important thing to keep in mind with jailbreaking, rooting, and sideloading is that they give the user more power at the expense of disabling protections that limit the damage malicious apps can do to the device. There are some things you just can't use a device for without removing these restrictions, but the benefit should always be weighed against the risk, especially when it comes to deciding whether to allow jailbroken/rooted devices on your network.

NOTE   Organizational networks may use MDM software to detect and block devices that have used one of these methods to remove restrictions.

The manufacturer or service provider may prevent a device from connecting to their services if they detect the change. There are also immediate risks: a failed attempt could brick the device, or perhaps just render it unusable until you restore it completely from a backup (removing the jailbreaking/rooting software in the process).

Unauthorized Location Tracking

We discussed the benefits of GPS and location tracking earlier, but there are also risks involved. Configuration settings in the OS and apps may allow a user's location to be sent to third parties, sometimes without explicit consent or knowledge. The best way to prevent this is to turn off the GPS function or location services unless they are needed. Another way is to configure the device and apps that use geotracking to prevent unauthorized tracking, if the device allows it. Some apps---or specific features---simply won't work until geotracking is enabled (see Figure 25-18).

Figure 25-18  Four Android apps prompting the user to enable location services

Keep in mind that the GPS functionality in a mobile device is not the only way to track its location; cellular networks and Wi-Fi are also used to track device location, although not as precisely as GPS. Some of the network attacks in the "Unintended Connections" section can also be used to locate or track a device.

Unauthorized Camera and Microphone Activation

App features, malware, and unauthorized network connections can potentially be used to activate (or disable!) some features on a mobile device. Any built-in cameras and microphones are of particular concern, because they enable an attacker to move beyond sensitive data on the device and effectively spy on anyone near it.

NOTE   Some of the most sophisticated attacks using methods discussed in the earlier "Unintended Connections" section can reportedly cause a device to appear to power down while still leaving its microphone active. Attacks of this quality may be unavoidable until carriers and device makers secure their networks and devices against them, but you can still be on the lookout for strange behavior.

The ways to prevent these exploits are by restricting camera and microphone permissions in apps or operating systems (when they allow it), taking steps previously described to prevent unauthorized network connections, and using anti-malware solutions on the device. Even when you're looking at a popular app by a trustworthy developer, such as the iOS apps with camera permissions in Figure 25-19, keep in mind that any vulnerabilities in a networked app with camera and microphone permissions could allow an attacker to listen in.

Figure 25-19  Apps with permission to access my iPhone's camera

Chapter Review

Questions

1\.   After five minutes of struggling with a painfully sluggish device, you finally manage to close the offending application. What's the best next step?

A.   Reopen the application and hope it doesn't freeze again.

B.   Uninstall the application and look for a replacement.

C.   Perform a soft reset and see if the app runs smoothly afterward.

D.   Close all open applications and attempt to reopen the application to see if it freezes again.

2\.   Which of the following would be a legitimate reason a mobile device is running slowly?

A.   Incorrect calibration

B.   RAM too slow

C.   Lack of storage space

D.   Incorrect version of application

3\.   Joyce notices her GPS map app gives the error "GPS coordinates not available." What should she try first?

A.   Run another GPS app.

B.   Stop and start GPS on the mobile device.

C.   Move to a place where she can get a good GPS signal.

D.   Update the mobile device's firmware.

4\.   You've lost your iPhone. What would you use to try to find it?

A.   iTunes

B.   iFind

C.   Location Services

D.   iCloud

5\.   Fred wants to play World of Warcraft on his desktop system. He logs in and then the game asks for a code that is generated by an authenticator app on his Android phone. This is an example of ___________.

A.   Multifactor authentication

B.   Factor authorization

C.   Multifactor authorization

D.   Factor authentication

6\.   Jailbreaking an iPhone gives access to ____________.

A.   The administrator account

B.   The root account

C.   The /bin folder

D.   The system BIOS

7\.   A great way to protect data on a removable media card is to ___________.

A.   Encrypt it

B.   Lock it

C.   Remove it when unneeded

D.   Format it

8\.   What type of file would you use to sideload an app onto an Android device?

A.   APK

B.   ZIP

C.   GIF

D.   EXE

9\.   Users bringing personally owned mobile devices into an enterprise environment is called ___________.

A.   Importing

B.   CYMK

C.   Providing

D.   BYOD

10\.   What do app scanners do?

A.   Scan QR codes and barcodes for hidden codes

B.   Analyze the traffic into and out of an application for suspicious behavior

C.   Analyze the permissions used by installed applications to highlight security risks

D.   Analyze Wi-Fi signals to identify evil-twin WAPs

Answers

1\.   C. After five minutes of struggling with a painfully sluggish device, definitely perform a soft reset and see if the app runs smoothly afterward.

2\.   C. Lack of storage space would be a legitimate reason a mobile device is running slowly.

3\.   C. Joyce needs to move to a place where she can get a good GPS signal.

4\.   D. Apple's iPhone uses the Find My iPhone feature of iCloud.

5\.   A. Using both a password and a security code is an example of multifactor authentication.

6\.   B. Jailbreaking is unique to iOS to provide access to the root account.

7\.   A. A great way to protect data on a removable media card is to encrypt it.

8\.   A. An Android Package (APK) is the file type that is used to sideload applications onto Android devices.

9\.   D. Users bringing personally owned mobile device into an enterprise environment is known as bring your own device (BYOD).

10\.   C. App scanners analyze the permissions used by installed applications to highlight security risks.

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

Chapter 25 Maintaining and Securing Mobile Devices

Chapter 26 Printers and Multifunction Devices

Chapter 27 Securing Computers

42h 21m remaining
