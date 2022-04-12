# https://github.com/rajverma1985/Alienware-15R4-Catalina
# This is a guide for getting OSX on Alienware 15r4 specifically for GSYNC models

# Getting Started

## So You Want A Vanilla Install?

#### What does that even mean?

A vanilla setup implies that the OS itself remains relatively untouched - and that the bulk of the Hackintosh-related kexts, patches, etc are contained on the EFI partition. For all intents and purposes, a vanilla install's main partition is _identical_ to that of an official Apple computer.

**Quick Terms Glossary**

There's a number of terms you'll be seeing throughout this guide - I'll outline a few of them and their definitions here:

**_Clover_** - this is the bootloader we'll be using.  Real macs have a custom firmware that allows them to boot macOS.  PC hardware needs a little help to get this working; Clover helps us achieve that.  It also handles kext injection, ACPI renames, kext patches, and a ton of other functions.
**_Kexts_** - the word "kext" is actually the combination of **K**ernel **Ext**ension; and you can think of kexts simply as drivers for macOS.
**_Config.plist_** - this is the file that tells Clover what to do.  It's an XML formatted property list \(looks very similar to HTML\) and is one of the most important parts of setting up your Hackintosh.


## PreRequisites

This guide focuses Alienware 15r4 gsyc LAPTOP _ONLY_. There are other guides out there for laptops \(see [RehabMan's guide](https://www.tonymacx86.com/threads/guide-booting-the-os-x-installer-on-laptops-with-clover.148093/) at TMac\) - but they're often _much more specific_ than this guide will be.

**_IMP: CATALINA DOES NOT install on a 8gb usb its bigger than 8gigs so have yourself a 8+ gigs USB._**
**_(Assuming you already have 16gb or bigger USB drive.)_**
**_NOTE_:** (Please do not share or ask questions on pirated copies of the software, it will not be entertained.)

1. Vanilla image of Catalina (You can download this from various sources, i would strongly suggest use a working mac and download it from
the apple store as it will untouched and clean image.
2. Clover Bootloader (ref to clover.zip)
3. Clover Configurator(ref to clover.zip)
4. All the required kexts(Pre and POST ref to the zip file "Working_clover_aw15r4_gsyc.zip")
5. Some basic software post install, i.e BOOM3D for audio, Atom for text edits etc.(optional)


## **Instructions:**

**_Creating a bootable drive from the downloaded image_:**

1. For creating a bootable drive just use the below command, make sure the USB is plugged into the mac hardware(you can also use a VM but at time it corrupts the install and there is no surety if it will work)
2. Now go ahead and open up the terminal and use the below command:

**sudo /Applications/Install\ macOS\ High\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume**

_Where MyVolume is the name of the USB drive(formatted on a MAC, if not formatted you need to go to the disk utility and format it as MACOS Extended Journaled)._

3. Now step 2 takes around 10 to 15 min depending upon your hardware.
4. Once the bootable drive is created successfully, please make sure these options are enabled in the BIOS:

  - SATA operation under ADVANCED tab should be on AHCI and NOT RAID.
  - sometime VT causes an issue on Alienware so disable it as well, you can try and re-enable it later after the install is         finished.

  - Once the bios settings are done, please go ahead and restart the system with USB drive plugged on the USB 2.0 port(LEFT  side  port next to the headphone jack) IMP: DO NOT use the right side USB port for installs and make sure if you have any other devices plugged into the right USB, unplug them.

5. Now boot with f12, and then choose the USB drive to boot from.
6. Choose the option to boot from Install Mac OS sierra(USB drive)
7. It will boot into the setup pane in about 5 to 7 minutes(again depending upon hardware, i'm using ssd's).
8. Once this is done, go to disk utility, from top left corner of the disk utility screen choose VIEW >> SHOW ALL DEVICES.
9 Once this is done you will have to choose the disk you want to install mac OS on. Now make sure to have a spare drive(dedicated once for dual boot with WINDOWS), NOTE: DO NOT TRY AND INSTALL THE MAC OS On the same WINDOWS drive. >>>> This is due to the EFI partition size on mac which is required to be more than 100MB.
10. Assuming you have another hdd, ssd for mac install or another disk where windows is not installed(e.g If you have a hdd which can be partitioned like mine, I'm using another ssd which has 100gb partition for MAC and rest i have formatted in windows for other usage).
11. Now select the drive and choose ERASE from top(middle section), erase this drive(CHOOSE Mac OS Extended (Journaled)) and in case you want to create a partition create a partition as well, the GUI is pretty self explanatory.
12. Now go ahead and close the disk utility, you will see the option to Install mac OS. choose it and follow the instructions(basically next>>next).
13. Once the install completes, the system will reboot, use f12 to boot from USB and on the clover screen choose boot from High Sierra, or the drive where you intalled the MAC os. The idea is to use to the EFI bootloader of the USB and boot into the hdd where the OS is installed.

14. Once the system boots it will ask you to setup some basic stuff, personal details, email etc.
15. Once you are booted into the HIGH SIERRA OS, we need to do POST install configs.


POST INSTALL:
============

1. Assuming the system has now booted into the OS(high sierra), install clover bootloader(ref to clover.zip folder of this repo).
2. On the install screen choose to install UEFI and install on ESP partition, those are the 2 most IMP things to choose. Others can be ignored as well.
3. Once the clover install finishes you will see an EFI hdd listed on your desktop, navigate into the EFI partition, go TO EFI>EFI and then delete the clover folder.
4. Copy the clover folder from my working clover zip file and then paste it there.
5. Once done, go ahead and run the clover bootloader again, no need to choose anything just finish the clover install and reboot.
6. This time we will directly boot from the hdd, so we have to add the boot option in the BIOS.

ADD BOOT OPTION in the BIOS:
===========================

_Take out the USB from the laptop_

1. On reboot, go to the bios and then go to boot options, choose delete boot options and delete the one that says anything related to MAC OS etc. DO NOT DELETE WINDOWS boot option.

2. Now go ahead and choose add boot option, choose the hdd where you have installed MAC, its a little tricky as the hdd are numbered in unix format, so try and use the first one, and then navigate to EFI>CLOVER>CLOVERX64.efi.
3. Hit enter and choose a name, i have named is HIGH SIERRA.
4. Go down and change the sequence of boot priority, choose HIGH SIERRA boot option as the first one and then choose windows for the second one.
5. Hit f10 to save and exit.


POST configs:
============

1. Now after changing the boot options, system will reboot to the clover boot screen, choose OS high sierra option.
2. The system will boot into High sierra.
3. copy the contents of POST install from the working clover in this repo and paste them into /Library/Extensions/
4. Once copied, go ahead and run the kext utility to update the cache, kext utility can be downloaded from different source. Make sure you use ethernet for now to connect to the internet.
5. You can freely use a external dongle like I do for wireless, TP-LINK 725W. Works just fine.


Feel free to let me know in case you have any questions.

**Author: Raj verma**
