# https://github.com/jianghaizhi/DELL-Alienware-Aurora-R7-macOS

# DELL-Alienware-Aurora-macOS (Update to support macOS Big Sur and above, 11.x )

Full working macOS for DELL Alienware Aurora R6/R7/R8/R9/R10/R11 (with Intel Processors). 

If you have any problem or improvement, you are weclome to share it through submitting an issue.   

My machine: Aurora R7 with i7-8700, 32GB memory, RX 580, 1TB nvme ssd, DW1830 wifi+bluetooth card


# Update log  

**2021/02/04**

Update to support macOS Big Sur, update clover to 5129, all kexts are also updated.



===Instruction on how to update your macOS:===
1. replace your EFI by this newest EFI, or following the Mannual EFL update instruction.
2. update macOS through Software Update in System Preferences
3. after the first reboot, select install macOS from [your hard drive] in clover start page
4. after the second reboot, select install Mac OS X for [your hard drive]-data from preboot in clover start page
5. the system will reboot mutiple times, always select install Mac OS X for [your hard drive]-data from preboot in clover start page
6. until the entry in clover start page change to Mac OS X from [your hard drive]-data, the update is finished.
7. select Mac OS X from [your hard drive]-data to enter your new macOS

===Manual EFL update instruction:===
1. update clover to newest version
2. replace AptioMemoryFixes (AptioMemoryFix.efi, OsxAptioFix3Drv.efi, OsxAptioFixDrv.efi and everyhing else containing "memoryfix".) by OpenRuntime.efi in EFL/Clover/drives/UEFI
3. remove preboot from Hide Volume in config.plist
4. following this figure to set Quirks in config.plist

![screenshot](https://raw.githubusercontent.com/jianghaizhi/DELL-Alienware-Aurora-R7-macOS/master/quirks.png)

**2020/04/16**

Update clover, kexts and drives to latest version. Now this configuratiuon can fully support macOS Catalina (10.15.x) by default. 

Change default theme to Catalina.

I have tested opencore on my machine. It seems Clover works better than opencore. So, currently I suggest to keep using Clover for Alienware Aurora. 


**2020/01/12**

This configuration works good in Catalina, but please install the latest Clover before you update to Catalina.

**2019/05/07**

Both the default case fans and PSU fan are very loud in Aurora. You can change them by yourself.

suggestion 1: change the top to ML120 PRO, this fan can pass the DELL system check. While a lot of other fans can not pass the DELL system check. Note that, the RGB version of ML120 PRO can not pass the check too, please select other color versions. This fan is very quiet.

suggestion 2: you can change the front fan to any silent fan.

suggestion 3: replace the PSU to a better brand PSU, > 500w, with smart fan control. Or change the PSU fan.

**2019/03/03** 

To fix kernel panic which is potentially caused by Intel graphics card: uncheck config.plist/Graphics/Inject Intel    

**2019/03/02** 

The newest USB port limit patches, you can choose to use either these patches or the customed SSDT patch.

Comment: USB port limit patch #1 10.14.x modify by DalianSky(credit ydeng)    
Name: com.apple.iokit.IOUSBHostFamily    
Find: 83FB0F0F    
Replace: 83FB3F0F    
MatchOS: 10.14.x    
    
Comment: USB port limit patch #2 10.14.x modify by DalianSky(credit PMHeart)    
Name: com.apple.iokit.IOUSBHostFamily    
Find: 83E30FD3    
Replace: 83E33FD3    
MatchOS: 10.14.x    
    
Comment: USB Port limit patch #3 10.14.x modify by DalianSky(credits PMheart)    
Name: com.apple.driver.usb.AppleUSBXHCI    
Find: 83FB0F0F    
Replace: 83FB3F0F    
MatchOS: 10.14.x    
    
Comment: USB Port limit patch #4 10.14.x modify by DalianSky(credits PMheart)    
Name: com.apple.driver.usb.AppleUSBXHCI    
Find: 83FF0F0F      
Replace: 83FF3F0F    
MatchOS: 10.14.x    


**2019/02/21**   

Change the default clover theme to Majove. 

Update kexts (EFI/CLOVER/kexts/Other) to latest version.  

Update UEFI drivers (EFI/CLOVER/drivers64UEFI) to latest version.    


**2019/01/28**   

The PSU noise issue.
  
The default PSU (460w, made by Delta)in my machine is defective, it produces loud noise when the load of the machine is high. If you have the same problem, you can ask DELL to replace this defective PSU by another PSU (460w, Part# WC1T4, made by HUNTKEY). HUNTKEY PSU is a little better than Delta one for noise controlling. There are also some people say that Delta psu's quality is better than HUNTKEY except the fan. You can also buy a more better PSU to replace it by yourself.    

**2019/01/22** 
    
New usb port limited patch (I tested them in my machine, they work good), you can choose to use either these patches or the customed SSDT patch.

This following patchs allow root hub port limit over 0xf to 0x3f. You need to add both these two pathes.     

> <font size="2">Comment: USB port limit patch 10.14.1 10.14.2 (credit ydeng).   
> <font size="2">Name: IOUSBHostFamily  
> <font size="2">Find: 00e0 83fb 0f0f 8716 0400  
> <font size="2">Replace: 00e0 83fb 3f0f 8716 0400   

> <font size="2">Comment: USB Port limit patch 10.14.1, 10.14.2.   
> <font size="2">Name: com.apple.driver.usb.AppleUSBXHCI  
> <font size="2">Find: 00 00 83 FB 0F 0F 83 8F 04 00 00  
> <font size="2">Replace: 00 00 83 FB 3F 0F 83 8F 04 00 00  

**2018/12/05**

Update my machine's MacOS to 10.14.2 successfully with this EFI settings.

**2018/11/22**

Update SSDT for USBInjectAll.kext, USB3 ports can now run at 5Gb/s. I do not have USB-C decives, so the two USB-C ports are not injected, you can modify ssdt by yourself to inject them.
> <font size="2">add: /EFI/CLOVER/ACPI/patched/SSDT-UIAC.aml    
> update: /EFI/CLOVER/config.plist</font>

**2018/11/18**  

Update to Mojave 10.14.x, The configuration and files for High Serria are moved to directory High-Serria-10.13.6**. 

Remove Nvidia Webdrive, replace Nvidia card by AMD card (RX 480,580,470,570,VEGA56, VEGA64, etc.). 

Replace SMBIOS imac 14,1 by macmini 8,1. mac mini 2018 natively support the 8th generation Intel cpu and UHD 630 graphics card. 

Remove HWPEnabler.kext. 

Add some useful tools.  



# Hardware
This clover setting should work for recent Alienware Aurora R6/R7/R8 desktops  (released on 2017 and 2018) which installed with Intel CPU and Nvidia GPU. It may need some minor modifications to completely fulfill your machine.

The hardware details for my machine: Aurora R7 with i7-8700, ~~GTX 1080~~, 32GB memory, RX 580, 480g nvme ssd, DW1830 wifi+bluetooth card

# Working condition
I connect two 4k monitors to the machine both through display port on RX 580, they work good. 

FaceTime and IMessage work good.

Bluetooth works good.

Airdrop works good.

Sleep and wake are good.

Usb ports are injected through SSDT-UIUC.aml

Intel integrated GPU UHD 630 is natively supported by Mojave when using macmini 8,1. 

I have no related devices, so I did not test USB-C ports and HDMI ports. 

Killer 1535 Wifi+bluetooth card does not work (need to be replaced).

Magic mouse and Trackpad work good.

# Issues
~~There is no suitable patches now, USB3 works on 480 M/s (Mojave 10.14.2)~~
Already fixed by adding SSDT for USBInjectAll.kext, USB3 ports can now run at 5Gb/s. See update log for details.   

For the USB problem, please not plug to the first one from left of the 4 usb3 ports in the back. These is no workable 15 port limit patch for Mojave now, therefore only less than 15 port are inject through SSDT. These injected ports include all the four ports in the front, the four usb2 ports in the second line in the back, and the 3 usb3 ports (except the first one from left) in the back.

The first one from left usb3 port in the back is indeed a usb 3.1 port, and controlled by a usb hub. While other usb3 ports are controlled by the motherboard.

# Installation

1. Following the general installation tutorial to install macOS. (Note that, you may need to update the /EFI/clover in your USB installer to the latest version, and copy paste all of my EFI files, then try to install MacOS. The default /EFI/clover version created by UniBeast is a bit old. Please plug your installation USB to a USB 2.0 port to install macOS.)

2. Install the bluetooth drive for DW1830 (BrcmPatchRAM)   
    Copy the two kexts in directory /bluetooth to /Library/Exetensions

3. Use Kext Utility to update cache for kexts, you can find this tool in directory /tools

4. Replace the default EFI by this one.

5. Setting Audio: Try to plug in your audio device to the centre connector in the second row and select Internal speakers in System Preferences>Sound




