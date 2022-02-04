![200627962_601033467536488_7690653762214029783_n](https://user-images.githubusercontent.com/23656651/152617253-65163747-1a77-4290-a6ae-aad78a309005.jpeg)

https://www.tonymacx86.com/threads/guide-11-2-3-alienware-m17-r4-2021-opencore-0-6-9.313024/

Hi,

I would like to report that I was successfully able to install Mac OS Big Sur on my Alienware m17 R4 (latest model as of May 2021).

Specs

Intel Core i7-10870H
Nvidia RTX 3080 (disabled)
17,3" FHD (1920x1080) 144Hz
Wi-Fi 6 AX1650
SSD: 2x1TB Western Digital SN750 (Original were Hynix, I doubt they were compatible)

What works

Sound (AppleALC with layout-id 11)
Intel UHD (IGPU). Advanced Nvidia Optimus but be enabled! Fn+F7 in Windows.
Bluetooth (OpenIntelWireless / IntelBluetoothFirmware)
Wifi (OpenIntelWireless / itlwm)
Ethernet (out of the box)
USB (Mapping was hard, see notes below)
Keyboard (It uses USB instead of PS/2! Was hard to get working, see notes below)
TrackPad (Gestures + Very Smooth with Voodoo2lc. Must disable Force click and haptic feedback in System Preferences) (Laggy if used with VoodooPS2Controller)
Sleep (See below)
Brightness (-igfxblr flag fixes very low brightness at boot. Fixes itself after 5 minutes otherwise)
External monitor using Display Link USB adapter.

What doesn't work

Thunderbolt 3 to Display Port but I believe it's wired to dGPU.
Mini DP Port but I believe it's wired to dGPU.
HDMI but I believe it's wired to dGPU

USB & Keyboard

The keyboard is wired by USB internally instead of using usual PS/2. At first, I couldn't get the keyboard to work at all. The reason was because Mac OS was not detecting the USB HS10 port which the keyboard is connected to. The only way I could get Mac OS to finally detect that missing port was with an SSDT RHUB Patch. I attached it to the thread. Once the port mapping is properly done, the SSDT can be removed.

Sleep

The sleep didn't work perfectly out of the box. Nvidia dGPU must be properly disabled (-wegnoegpu). I also used the flag (igfxonln=1) to make sure the display would always turn back on.

That first part only fixed the sleep/wake, but the laptop would never sleep for longer than 3-5 seconds before turning back on. I had to follow this guide here "GPRW/UPRW/LANC Instant Wake Patch" https://dortania.github.io/OpenCore...t-wake.html#gprw-uprw-lanc-instant-wake-patch

By searching into my DSDT.aml, I found I had the mention of "Method (GPRW, 2". This mean I needed the path SSDT-GPRW.aml + ACPI patch to add in config.plist "GPRW to XPRW Patch".
