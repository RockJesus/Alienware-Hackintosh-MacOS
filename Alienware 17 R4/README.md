



![black.jpg](http://r1o2otara.hd-bkt.clouddn.com/black.jpg)
![aw17.jpg](http://r1o2otara.hd-bkt.clouddn.com/17r4.gif)


>http://bbs.pcbeta.com/viewthread-1797200-1-1.html

>https://www.tonymacx86.com/threads/guide-alienware-17-r4-dual-gpu-macos-mojave.263577/

>**My hardware**
Alienware 17 R4
1080p
i7-7700HQ
Intel HD 630 & Nvidia GeForce GT 1060
16G RAM
SM961 Samsung NVME 256
REALTEK ALC298
KILLER E2500
Dell DW1560 (Broadcom BCM94352Z)
BIOS version 1.5.0


>**BIOS Configuration**
SATA MODE AHCI
SECURE BOOT NO
BOOT UEFI


>**Overview**
I've got dual-gpu working good on 10.13.6,Now just waiting for the webdriver for 10.14.
*In windows OS press FN+F7 to change graphic mode:
1.dual gpu mode:Indisplay connects to hd630,Exdisplay connects to nvidia 1060
2.nvidia gpu only mode:Indisplay & Exdisplay both connects to nvidia 1060
![about.png](http://r1o2otara.hd-bkt.clouddn.com/about.png)
![pci.png](http://r1o2otara.hd-bkt.clouddn.com/pci.png)


>**What Works**
CPU Power Management
Battery Support
Intel HD 630 & Nvidia GeForce GT 1060(when webdriver has installed)
HDMI out (with hotplug) & Audio out(when webdriver has installed)
Audio ALC298 (2.1ch with subwoofer)
Headphone
Brightness & volume Keys
Keyboard
AlienFX keyboard & logo LED lights (follow the settings on windows os but using vmware boot to windows and load the aw1517 usb device could change Alienfx light on macos)
Trackpad with Gestures
Webcam
WiFi and Bluetooth
Ethernet
iCloud Services
Continuity and Hand-off
USB 3.0 & TYPE-C
Thunderbolt devices with hotplug before sleep
Sleep & Wake (only power button could wakeup system)

>**What Doesn't Work**
Keyboard & mouse wakeup sysytem
Thunderbolt devices with hotplug after wake
ALIENFX light control on Macos
Webcam IR function
Trackpad light (Bios touchpad backlight=auto with no light ,but Bios touchpad backlight=on with light always on)

>**What Needs Improvement**
Backlight auto adjust (ALS0 device)
HWsensor for more info
LPCB,SBUS,Thermal subsystem controllers seems not working normally
Things under "What Doesn't Work"

>**Install**
If you can't see install partition try to press F3 on clover boot screen

>**Post Install**
**HIDPI**
Run script in Terminal:
Code:
sh -c "$(curl -fsSL https://raw.githubusercontent.com/xzhih/one-key-hidpi/master/hidpi.sh)"

>**Change ur own productid & vendorid in kext's info.plist ()**
AppleMouseKeyboard.kext
Applesmcmotion.kext (KIOX device)
UVC2FaceTimeHD.kext (cam)
VoodooHDA.kext (nvidia hdmi controller id)

>**Nvidia webdriver**
copy and paste the following in a terminal:
Code:
bash <(curl -s https://raw.githubusercontent.com/Benjamin-Dobell/nvidia-update/master/nvidia-update.sh)

>**Audio**
ALC298: layout-id=11 https://github.com/acidanthera/AppleALC
Headphone/Headset volume ALCplugfix(deprecated):
Code:
cd alc_fix
chmod +x install.sh
./install.sh
Headphone/Headset volume fix Combojack(newway):
Code:
cd ComboJack
chmod +x install.sh
./install.sh
Install Boom 3D APP to get better audio output



>**Change log**
hdmi audio changed to hotpatch from dsdt patch
usbports.kext
cpu pm 800-3800mhz
Add smcmotionsensor
Fixed BT issue by droping DMAR table
change virtualsmc to fakesmc for getting more sensors (Fan & nvidia temp)
Add intel & nvidia GPU PM
alcplugfix seems not working on 10.14,changed to verstub(combojack) for headset fix
smbios=mbp15,1
New released lilu & whatevergeen etc,No need to hotpatch hdmi audio any more,but still need voodoohda to make hdmi audio work
changed to virtualsmc

>**Dump request**
I really need a dump of real Macbookpro 14,3's full acpi dsdt/ssdt & IOREG & system report.spx , Any help will be appreciated!

>**Updates on my github:https://github.com/RockJesus/Alienware-17-R4-Dual-GPU-MacOS-Mojave-10.14-Hackintosh**

# 如有疑问请进QQ群 If u need help >> https://gitter.im/Alienware-hackintosh/community

| 外星人黑苹果QQ群：308469644                                                                                                                                                              | 外星人黑苹果微信公众号                                                                                                                                                          | 外星人黑苹果微信小程序                                                                                                                                                          |
| ----------------------------------------------------------   |  ----------------------------------------------------------   |  ----------------------------------------------------------   |
| ![image](http://r1o2otara.hd-bkt.clouddn.com/qq.png) |![image](http://r1o2otara.hd-bkt.clouddn.com/gzh.jpg) |![image](http://r1o2otara.hd-bkt.clouddn.com/xcx.jpg) |


# 如果文章对你有帮助，欢迎打赏作者. If u like, Buy me a coffee  :)
| 支付宝打赏                                                                                                                                                              | 微信打赏                                               |微信赞赏                                            |
| ----------------------------------------------------------   | ---------------------------------------------------- | ---------------------------------------------------- |
| ![image](http://r1o2otara.hd-bkt.clouddn.com/zfb.png) | ![image](http://r1o2otara.hd-bkt.clouddn.com/wx.png) | ![image](http://r1o2otara.hd-bkt.clouddn.com/zsm.png) |
