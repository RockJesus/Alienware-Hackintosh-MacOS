# https://github.com/rpelorosso/Alienware-15R3-High-Sierra-Hackintosh
# Alienware-15R3-High-Sierra-Hackintosh

Think of this as a notepad for now. I'll organize this better once everything works fine.

I've tested this on the Alienware 15R3 with the i7 6700HQ processor.

## Reaching the installer

I couldn't reach the installer, first it would't boot, then it would boot to a black screen.

- I used [OsxAptioFix2Drv-free2000.efi](https://github.com/koush/EFI-X99/blob/master/CLOVER/drivers64UEFI/OsxAptioFix2Drv-free2000.efi) and deleted the original OsxAptioFix2Drv.
- Changed ig-platform-id for Intel to 0x12345678 (this fixed the black screen)

## Installing

I installed to a mechanical hard drive using a hfs+ partition. Nothing weird happened here.

## After the install

### Display

After the installation it would boot to a black screen. I changed ig-platform-id back to 0x12160000.

I used [this guide](https://www.tonymacx86.com/threads/guide-laptop-backlight-control-using-applebacklightinjector-kext.218222/) in order to make the brightness control work.
For some reason it wont't reach the minimum brightness necesary to turn off the display.
It's a shame beause I use an external display and would like to have the laptop display off.


### Audio

I used [this](https://github.com/insanelydeepak/cloverHDA-for-Mac-OS-Sierra-10.12/files/1050120/ALC298.AlienWare.zip), which someone
linked [here](https://github.com/insanelydeepak/cloverHDA-for-Mac-OS-Sierra-10.12/issues/16). Just put AppleHDA.kext for clover to use,
and run ALCPlugFix. This fixes the sound for headphones.

### Power management

[HWPEnable](https://www.tonymacx86.com/threads/skylake-hwp-enable.214915/) works fine.

Some profiles for HWPValue:

- 80002301 - middle point
- 64002301 - little more performance (moderate mode)
- 94002301 - little more battery saving (same setting as on real MacBook9,1)


