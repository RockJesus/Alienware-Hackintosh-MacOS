# Alienware-Aurora-R11-Hackintosh
 Full working OpenCore version for 10th Gen Intel and macOS (Z370 and Z470)
 
**My Hardware: Alienware Aurora R11**
 - 10th Gen Intel Core i9 10900KF (10-Core, 20MB Cache, 3.7GHz to 5.3GHz) Commet Lake
 - 32GB Dual Channel HyperX FURY DDR4 XMP 3200MHz 
 - AMD Radeon RX 580 Saphire 8Gb 
 - 1TB Samsung 970 EVO Plus NVMe M.2 SSD 
 - Broadcom M.2 NGFF BCM94360NG WiFi+Bluetooth - Perfect!
 - Lunar Light chassis with High-Performance CPU Liquid Cooling and 1000W Power Supply
 
This is a collection of files that worked for my setup. The credit for these files go to the resource owners used over the time it took to compile something that worked. 
The config.plist was updated using ProperTree and following the Ice Lake Documentation provided by Dortania (Thanks a ton!)

Mostly this area is for me so that I have documentation and access. your performance and setup may not work
 
**Some issues**:
  - Killer Wi-Fi AX1650 - did not work ~~(Changed to Fenvi FV-T919 then to DW1830)~~
    - Broadcom M.2 NGFF WiFi Wireless Card BCM94360NG (All working correctly, unlock with apple watch, Apple KB & Mouse) 
  - Hynix 1Tb NVMe SSD did not work (Changed to 970 Evo Plus)
  - ~~Bluetooth not working properly (Not much time spent in troubleshooting)~~
  
**BIOS Settings**: (These are my current settings, yours may be different)
 - Reset to Optimized Defaults
 - Advanced -> PCIe Resizable Base Address Register - Disabled
 - Advanced -> Power Options -> Deep Sleep Control - Disabled
 - Advanced -> Power Options -> USB PowerShare (S4/S5) - Disabled
 - Advanced -> Performance Options -> Overclocking Feature - Enabled
 - Advanced -> Performance Options -> Core Overclocking Level - OC LV 2
 - Advanced -> Performance Options -> XMP Memory - XMP1
 - Security -> Absolute - Disabled
 - Security -> Firmware TPM - Disabled
 - Security -> Windows SMM Security Mitigations Table (WSMT) - Disabled
 - Security -> Secure Boot -> Secure Boot - Disabled
 - Save and Reset (F10 + Enter)
 
**Installation**:
 - Create the bootable USB via method used in Dortani Documentation (Follow the Guide, it works)
 - Copy the EFI Folder to mounted EFI Drive (I used ESP Mounter Pro)
 - Reset NVRAM on First Boot (Use Opencore Menu Option)
 - Select Install <OS You Are Installing>
 - First Reboot - Select New Installation Drive
 - Second Reboot - Select new OS Drive
 - Enjoy!

**Update 12/01/2021**
I purchased from ebay the M.2 NGFF Card "Broadcom M.2 NGFF BCM94360NG WiFi+Bluetooth" which installed in place of the Killer AX1650 I had. You can find that here:
https://www.ebay.com/itm/194178222777?hash=item2d35ec8ab9:g:UzIAAOSwKZxfDru0

For the sleep issues, I installed a tool called "Amphetamine" which is free (But I donated $20). This allows the monitors to sleep. Since I replicate data from this system overnight to a different system, I do not let the system fully sleep.
I also got the chime to work so it all looks and sound just like my old 2012 Mac Pro when it boots up.

**Update 11/16/2021**:
Installed Broadcom M.2 NGFF WiFi Wireless Card BCM94360NG Dual Band Network adapter BT4.0 purchased from ebay and now all wireless and bluetooth abilities work perfectly. Installed right where the Killer AX1650 and DW1830 was. removed the Fenvi FV-T919 from PCI Slot.

<img width="549" alt="Monerey" src="https://user-images.githubusercontent.com/3057585/141327390-5a9cde50-4d75-4625-b98b-7e81feabb56b.png">
<img width="543" alt="High Sierra" src="https://user-images.githubusercontent.com/3057585/141327453-4cbd65c5-2100-4f5e-988e-44c0ce0d91b3.png">
 
**Resources**:
 - https://dortania.github.io/OpenCore-Install-Guide/
 - https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/icelake.html
 - https://github.com/acidanthera/OpenCorePkg/releases/
 - https://www.insanelymac.com/forum/files/file/566-esp-mounter-pro/
 - https://github.com/corpnewt/ProperTree
 - https://github.com/corpnewt/GenSMBIOS
 - https://www.olarila.com/topic/5676-hackintosh-efi-folders-for-all-chipsets-clover-and-opencore/
 - https://github.com/jianghaizhi/DELL-Alienware-Aurora-R7-macOS
 - https://github.com/osxfuse/osxfuse/wiki/NTFS-3G
