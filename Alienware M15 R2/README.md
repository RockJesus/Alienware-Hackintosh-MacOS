@alectardy
This thread has been updated to refect my current build with open core, note that you should not use my open core files directly, and instead just use them as a reference, as open core is vary picky and is deferent per system

New Opencore files for Big Sur 11.2.2
This is a perfect install, and all things that can work seem to be working well, including thunderbolt and sleep

What is working:
-Intel HD graphics hardware execration
-Intel wifi 6 AX200 using OpenIntelWireless
-Audio and internal mic and headphone port using AppleALC using ID 11 (thank you macpeet)
-Keyboard and touchpad with gesture support
-Backlight and Volume control
-Battery in the status bar
-Webcam
-Full sleep support and power button for sleep menu (in terminal use "Sudo pmset hibernatemode 0")
-Thunderbolt 3 (with hutplug) (See Bios photos for my settings)
-Bluetooth
-USB 3.0 and 2.0 differentiation and recognition (USB Inject All With SSDT-UIAC-ALL)
-CPU Fan Control using HW Monitor
-Ethernet for the Killer E3000 (See Ethernet Info)

Whats not working
-Nvidia 2080 MaxQ (not supported)
-HDMI (directly connected to Nvidia)
-Display Port (directly connected to Nvidia)
-GPU Fan Control using HW Monitor (but temps can be viewed)
-Keyboard Backlight Control

Problems I came across:
-My computer came with a sk hynix pc601 NvmeSSD and the drive is not compatible so I had to disable the drive from being detected from boot. I disabled the second NVME port (if you don't need this then remove SSDT-DiscreteSpoof-EVO-Plus.aml from ACPI/patched)
-I couldn't get the windows key to work, and after pulling my hair out I found out that Function keys are set in the bios. I was playing with function keys and pressed Fn+f6 Which locks the windows key. Just press Fn+f6 again to unlock
-I am quad booting Windows 10, Manjaro, Kali, and Mac OS. I have all three other operating systems on one NVME and Mac OS on the other. For the longest time I would sometimes restart my computer and get a Support Assist - Pre Boot System Performance Check before I was able to Start Clover. I believe that I was getting this issue because I did not have my clocks set properly in each OS. To fix this I corrected my clocks for each os, (in windows using Regedit) and have not got the problem again.


I hope this helps
-My current EFI folder below
-Make sure to change SMBIOS info to get iMessage and FaceTime to work
