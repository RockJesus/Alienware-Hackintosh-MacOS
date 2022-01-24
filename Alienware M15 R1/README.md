# Hackintoshing Alienware m15 r1
## IMPORTANT
Read everything before attempting else you'll look like a clown. I spent hours getting this to work and this was my first time making this so if there are any issues or modifications to be made, do tell!
## Details
Tested with macOS Mojave 10.14.6 (11th November 2021)
![Screenshot 2021-11-03 at 5 54 55 PM](https://user-images.githubusercontent.com/32519167/140059946-cc5722b3-8612-4098-98bf-48050e59450a.png)
### Hardware Details
* CPU: Intel Core i7-8750H
* iGPU: Intel UHD Graphics 630
* dGPU: NVIDIA GeForce RTX 2060 (Disabled with -wegnoegpu)
* WiFi Chip: Killer Wireless AC-1550 (9260NGW)
* Ethernet: Killer E2500
* Audio: Realtek ALC289
### BIOS
* Version 2.9.0
* Secure Boot: Off
## Working
* Wi-Fi
* Bluetooth
* Audio
* Headphones (Headset mic doesn't seem to be working)
* Front Camera
## Tutorial Used
https://dortania.github.io/OpenCore-Install-Guide/prerequisites.html
## Tools Used
* [OpenCore v0.7.5-Debug](https://github.com/acidanthera/OpenCorePkg/releases) The heart and soul
* [gibMacOS](https://github.com/corpnewt/gibMacOS/) Used for downloading MacOS (You can also use the method OpenCore uses too)
* [proprTree](https://github.com/corpnewt/ProperTree) Plist editing
* [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) Generate SMBIOS Data
## Ktexts Used
* WiFi - [Airportltlwm v2.0.0](https://github.com/OpenIntelWireless/itlwm/releases)
* Audio - [AppleALC v1.6.6](https://github.com/acidanthera/AppleALC/releases)
* Bluetooth - [IntelBluetoothFirmware v2.0.1](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases)
* Required for AppleALC, WhateverGreen, VirtualSMC and many other kexts - [Lilu v1.5.7](https://github.com/acidanthera/Lilu/releases)
* Ethernet - [RealtekRTL8111 v2.4.2](https://github.com/Mieze/RTL8111_driver_for_OS_X/releases)
* USB - [RehabMan-USBInjectAll v2018-1108](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/)
* Emulate SMC Chip - [VirtualSMC v1.2.7](https://github.com/acidanthera/VirtualSMC/releases)
* I2C/USB HID Devices - [VoodooI2C v2.6.5](https://github.com/VoodooI2C/VoodooI2C/releases)
* PS2 Keyboards/Trackpads - [VoodooPS2Controller v2.2.7](https://github.com/acidanthera/VoodooPS2/releases)
* Graphics - [WhateverGreen v1.5.5](https://github.com/acidanthera/WhateverGreen/releases)
## SSDT Used
https://dortania.github.io/Getting-Started-With-ACPI/ssdt-methods/ssdt-prebuilt.html#laptop-coffee-lake-8th-gen
## Config.plist Editing
Followed this
https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/coffee-lake.html#starting-point
and it's pretty much good except for:
#### 1.
In `Booter -> Quirks` it should be
* EnableWriteUnprotector -> True
* RebuildAppleMemoryMap -> False
* SyncRuntimePermissions -> False

as I had [OCABC: MAT support is 0](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/extended/kernel-issues.html#kernel-panic-on-invalid-frame-pointer)
#### 2.
In `PlatformInfo -> Generic`,
Change SystemSerialNumber, MLB and SystemUUID from the ones generated in GenSMBIOS.
## EFI and USB is ready, yay!
You are ready padawan. Run the installer from the USB to install MacOS and follow the [post install](https://dortania.github.io/OpenCore-Post-Install/) guide to boot directly from hard drive instead of USB, use GUI based boot screen, audio issues, etc. You can also replace the [Debug version of Opencore with Release](https://caizhiyuan.gitee.io/opencore-install-guide/troubleshooting/debug.html) to prevent creation of log files and remove the delay at start
