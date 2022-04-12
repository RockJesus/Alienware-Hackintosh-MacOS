# https://github.com/kingo132/a51m-r2-5700m-hackintosh
[![](https://img.shields.io/badge/Chat-Alienware%20Hackintosh-critical)](https://gitter.im/Alienware-hackintosh/community)

WARNNING!!⚠⚠⚠ Mac OS Monterey will break the backlight patch. Because Monterey removed all the C style symbol in AMDRadeonX6000Framebuffer.kext, it need to rewrite the patch to call by address instead of symbol. Stay at Big Sur if you want this patch. 

# a51m-r2-5700m-hackintosh
Hackintosh for alienware area 51m r2 with 5700m gpu, currently I'm running Big Sur 11.5.2

# The specification
```
CPU Brand Name:      10900K
Video Chipset:       Intel UHD 630
Built-in Monitor:    1920x1080@144hz, changed to B173ZAN06.1 (4k@120hz)
Touch Pad:           I2C HID Device
Audio Adapter:       RealTek ALC215
Wireless Adapter:    Changed to BCM94352Z
DGPU:                AMD RX57000M
Card Reader:         Realtek RTS5260 PCI-E Card Reader, 10EC:5260, 1028:099B
```

# Everything works except

- [x] Internal display does not support brightness adjustment
  * fixed! See my modified version of Whatevergreen for more detail: https://github.com/acidanthera/WhateverGreen/pull/90
- [x] Geekbench 5 Metal score only get 20000 under mac os, which compared to Windows 10 will get 50000
  * fixed! Modify the vBIOS using this tool ([RED BIOS EDITOR](https://www.igorslab.de/en/red-bios-editor-and-morepowertool-adjust-and-optimize-your-vbios-and-even-more-stable-overclocking-navi-unlimited/3/)) and use that vBIOS to add ATY,bin_image property. See [Unlock the performace of rx5700m in MacOS section](#unlock-the-performace-of-rx5700m-in-macos)
- [ ] Trackpad not support guesture
  * May need to modify the code of voodooi2c, too difficult for me to fix.
- [x] Audio output will reset to headphone on every boot, and the quality of headphone output is terrible
  * Fixed. Swaped the positions of the headphone and speaker in pin config data, then when mac os auto select headphone, it is speaker. And use this kind of adapter to connect you headphone.
  ![image](https://user-images.githubusercontent.com/46492291/136552568-8a17c49b-2185-47d0-b085-ef00d7c1b2a4.png)
- [x] Cardreader
  * Fixed! Use this driver: https://github.com/0xFireWolf/RealtekCardReader
- [ ] Thunderbolt hotplug
  * Haven't tested: https://github.com/RockJesus/macOS-IOElectrify
- [ ] Sleep / Wake
  * Sleep will crash with "Sleep Wake failure in EFI" error. Seems not easy to fix.
- [x] Eye tracking
  * Won't work.

# AlienFX for Mac

I wrote a mac program to adjust the keyboard backlight brightness under Mac os, you can test it here

https://github.com/kingo132/AlienFX-For-MacOS

# Unlock the performace of rx5700m in MacOS

By default, this rx5700m can only get 20000 Geekbench Metal score in MacOS, compared to Windows it can get 50000+ score. Here is the step to unlock it's performance. No need to modify any thing. Just resave the vBIOS using RED BIOS EDITOR tool. After the modification, the score will be 60000, enough for the performance of this rx5700m under MacOS.

1. Dump the original vBIOS using a tool called amdvbflash.exe, save it to a51m.orig.rom.
2. Download the RED BIOS EDITOR tools here: https://www.igorslab.de/en/red-bios-editor-and-morepowertool-adjust-and-optimize-your-vbios-and-even-more-stable-overclocking-navi-unlimited/3/
3. Run MorePowerTool, open a51m.orig.rom, click save to save a mpt file a51m.orig.mpt
4. Run Red BIOS Editor, open a51m.orig.rom, then load a51m.orig.mpt, then save to a51m.resave.rom
5. run command "head -c 65536 a51m.resave.rom > a51m.resave.rom.64k" to get the first 64k of the rom
6. run command "xxd -p a51m.resave.rom.64k | tr -d '\n' > a51m.resave.rom.64k.txt" to get the txt of the hex value of this 64k rom
7. open a51m.resave.rom.64k.txt, copy all the content to ATY,bin_image

![image](https://user-images.githubusercontent.com/46492291/135756058-862ded94-3ab1-4f23-af80-e03ec185085d.png)

Here is the binary comparation of the original vBIOS rom and the resaved vBIOS rom.

![image](https://user-images.githubusercontent.com/46492291/135636806-20596fd7-f66b-4ea6-8cdc-1a2807e9f9a4.png)

As you can see, although we didn't modify anything when resave the vBIOS file using RED BIOS EDITOR, it still has some modifications. I don't know what it modified, if you know, please tell me. And anyway, the performance is unlocked.

# Replace the built-in display to 4k@120hz

I replaced the built-in display to B173ZAN06.1, which is 4k@120hz. And the stock dp cable (DC02C00JU00, 0.5mm gap 40 pin connector) is not compatible. It needs to be changed to DC02C00MY00, which has a 0.4mm gap 40 pin connector.

And there's another panel, B173ZAN06.0, which is 4k@60hz, is capatible with the stock dp cable. There's no need to buy a new cable if you change to this panel.

And there's some small issue with B173ZAN06.1.
* First, the newest AMD driver will giltch in windows 10, you have to use the AMD driver come with dell which is an old version that can be downloaded in dell website.
* Second, in mac os it can only get 4k@60.03hz, I don't know the reason, may be need to patch Apple AMD driver. (Fixed, see [HERE](https://github.com/kingo132/a51m-r2-5700m-hackintosh/blob/main/fix_navi10_4k_120hz.md) for more detail.)

# Releated issue

* https://www.tonymacx86.com/threads/compatibility-alienware-area-51-i7-10700k-amd-radeon-tm-rx-5700m.308933/
* https://www.tonymacx86.com/threads/alienware-area51m-r2-near-fully-working-problems-with-display-and-sound.309032/
* https://www.reddit.com/r/hackintosh/comments/onqr4r/alienware_area_51_r2_with_rx_5700m_works_on_big/
* https://www.reddit.com/r/hackintosh/comments/af646k/alienware_area_51m_as_hackintosh_laptop/
* https://www.reddit.com/r/hackintosh/comments/oml3un/alienware_area_51m_r2_with_rx_5700m_compatible/
