# Android Privacy setup

We live in a world full of free services that you pay with your data or your time. They bring convenience, but also cause annoyance. I wanted to describe my Android setup that tries to minimize privacy concerns and protects kids and other non tech native users from dangers of internet.

Even tough these steps help, its more important to understand that these steps will not protect you if you don't actively protect yourself.
- Don't put out your information to the world.
- Don't use applications that are free, but want to know everything about you. You are paying usually with your privacy.

## What are we trying to achieve

Android setup that will:
1. Minimize the amount of data collected on user by using privacy respecting software
2. Minimize amount of advertisement and other malware taking up users time and mental energy
3. Keep the device as usable as a default Android device would be

Even though privacy is nice, human contact is more important. In many cases mobile device is the primary way we achieve this human contact. We all have groups that we cannot loose and cannot move to a secure platform. Don't overdo it. Educate people where you can and limit your exposure.

## Contributing

This is a work in progress and if I am missing or wrong about something, please do submit a PR with a fix. Also if you know some tooling that works for you, please suggest it.

## Android

First of all this can only be done with Android. iOS is a closed system that does not allow the tooling needed to take control of your data. Apple enforces privacy, but this is true only if you trust Apple without seeing the products code. I might be wrong, correct me if you know better.

## Phone brand/model

Some are good and some are bad. Generally I prefer brands and models that allow installation of Lineage OS ([device list][lineage_devices]). Installation of a custom ROM is a technical process that is out of scope for this document. 

Custom ROM as Lineage OS gives you the choice not to include Google software. Not including Google software means that Google has no visibility to your data, but it also means that some google services are not usable. Biggest downside is that most notification services will not work properly.

## Firefox

Firefox is my goto browser on mobile. Once installed, open Firefox browsers settings and change default search engine to [DuckDuckGo][duckduckgo] and in addons section install [uBlock][ublock]. There are other addons for privacy, but I feel that uBlock is enough. Defaults are sane enough to work out of the box.

## F-Droid

[F-Droid][f_droid] Google Play Store like application that contains most of applications used in this guide and does not require login. It is a catalogue of FOSS (Free and Open Source Software). F-Droid can be downloaded from F-droid website.

## Netguard

First thing I usually install on any phone is [Netguard][netguard]. Netguard is a software firewall that lets you control what applications can communicate with the outside world. It can also be used to block Google software if you are not able to install Lineage OS. 

Once installed remember to set default policy to block in settings and allow the applications that you want to use. You can define that some apps can communicate only when the screen is on and some can do background work when screen is off. This permission should be given sparsely.

When you install a new application Netguard will show a notification for you to configure permissions. 

In my setup I have three distinct levels. Communications apps (Signal and Slack) get the background permission so I get notified of incoming. Most frequently used apps like Firefox get the screen on permission. Rest are blocked until I need to use them.

## Signal

FB and WhatsApp terms of service are getting out of hand. You have all seen the buzz. Luckily there is a privacy focused alternative with a better user experience in general. [Signal][signal] is my go to app for communication. Has everything WhatsApp offers without owning your phone.

#### "But I still need WhatsApp, Messenger or some other app that I don't want on my phone tracking me?"

Luckily if you have a computer you can sandbox these applications. Android emulator you can run an Android device on your computer. Install whatever applications you need to still use on the emulator, verify WhatsApp phone number using your real phone and continue using it in a controlled environment.

To run an Android emulator:
1. [Install Android Studio][studio]
2. [Setup Emulator][emulator]

There are other alternatives to android emulators. This is the one I use.

## Aurora store

Using F-Droid you can install Aurora store. Aurora store is a replacement for Play Store that does not require authentication. So you can download all the apps you need anonymously. 

## OpenBoard

Use F-Droid to install [OpenBoard][openboard] as replacement for Googles onscreen keyboard. Default keyboards are closed source and we don't know what they are doing under the hood. Better to use a good open source alternative. Keyboard is an element that you use constantly and type in all your secrets with. 

After installation OpenBoard guides you through the setup. If you already enabled NetGuard remember to permit the traffic to download any languages you might need. After download deny all traffic. Your keyboard does not need to talk to outside world. Not even for updates.

## OpenLauncher

Use F-Droid to install [OpenLauncher][openlauncher]. Similarly as your keyboard, launcher is your second most used application that has visibility to your whole phone. It should be trusted and should not talk to outside.

## Simple Camera

Use F-Droid to install [Simple Camera][simple_camera]. Same as Launcher and Keyboard. Usually one of the most used features of a smartphone and no idea what factory installed software does. Camera app should not have access to outside.

## Simple Mobile Tools

[Simple Mobile Tools][simple_tools] is a family of tools that Simple Camera is a part of. They have a open source replacement for all the default Android applications like a File Manager.

## NewPipe

If you plan on consuming content from YouTube, you should use Firefox browser to do so. Or download [NewPipe][newPipe]. NewPipe YouTube client gives you access to the content without ads and tracking. As a added benefit it has a feature that lets you playback content with screen off.

## SMBSync2

To backup my files or photos I use [SMBSync2][smbsync]. For this you need a Samba share in your home network. It can be quite technical, but the minimum setup can be done with most mid range wifi routers. Find out does your router support Samba, connect a usb drive to it and enable Samba in routers admin. 

After this you can define sync tasks for SMBSync2 like: "If you are in a specific wifi with specific ip address and charging, sync images from photo folder to samba share every night at 2am". Bit hard to use due to amount of possible configuration, but once you figure it out it servers you very well

## DNS

If you don't want your kids to surf unsavoury sites on their phone, we can prevent some of the traffic by setting up [CloudFlares family DNS][family]. Open Android settings, select Advanced settings and select private DNS (or search for DNS). Android does not accept IP so well have to use hostname:

Malware blocking (1.1.1.2, 1.0.0.2):
malware.cloudflare-dns.com
Malware and adult content blocking (1.1.1.3, 1.0.0.3):
family.cloudflare-dns.com

## Finally

These are some of the steps I use to improve privacy and security of my Android devices. 


[lineage_devices]: https://wiki.lineageos.org/devices/
[f_droid]: https://f-droid.org/
[netguard]: https://netguard.me/
[duckduckgo]: https://duckduckgo.com/
[ublock]: https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/
[openboard]: https://github.com/dslul/openboard
[openlauncher]: https://github.com/OpenLauncherTeam/openlauncher
[newPipe]: https://newpipe.net/
[smbsync]: https://github.com/Sentaroh/SMBSync2
[simple_camera]: https://github.com/SimpleMobileTools/Simple-Camera
[simple_tools]: https://github.com/SimpleMobileTools
[signal]: https://github.com/signalapp
[emulator]: https://developer.android.com/studio/run/managing-avds
[studio]: https://developer.android.com/studio/install
[family]: https://blog.cloudflare.com/introducing-1-1-1-1-for-families/