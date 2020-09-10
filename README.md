# Hackintosh-ASUS-A455LF-Notebook

My EFI Folder for ASUS-A455LF-WX039D Series with Clover/OpenCore Legacy or UEFI
 
<img src="/Images/Sept-Ulchre-MacBook-Pro-Catalina.png?raw=true" alt="macOS Mojave" align="center">
 
### How to Get it?

- Open Terminal with Command: $ `git clone https://github.com/asepms92/Hackintosh-ASUS-A455LF-Notebook.git`
- Or Just [Clone/Download](https://github.com/asepms92/Hackintosh-ASUS-A455LF-Notebook.git) with Specific Folder Only
 
--------------------------------------------------------------------------------------------
 
### Specs :

- [x] <b>BIOS</b>: v300 (2016/12/2) American Megatrends Inc,
- [x] <b>Model Laptop/Notebook</b>: Asus A455LF-WX039D Series
- [x] <b>Processor</b>: Intel Core i5-5200U (4) @ 2.2GHz up to 2.7Ghz Broadwell
- [x] <b>Graphics</b>: Intel HD Graphics 5500 + Nvidia Geforce 930M
- [x] <b>RAM</b>: 8 GB 1600 MHz DDR3L
- [x] <b>HDD</b>: 500GB SATA HDD (GUID Partition Table) will be replaced to SSD
- [x] <b>Audio</b>: Conexant CX20751/2
- [x] <b>Wifi+BT</b>: Qualcomm Atheros QCA9565/AR9565 Wireless Network Adapter + AR3012 (Azurewave Tech)
- [x] <b>Ethernet</b>: Realtek RTL8111GU/8168GU/8411GU PCI Express Gigabit Ethernet
- [x] <b>Others</b>: USB3.0 + USB2.0 ports WebCam, FocalTech TouchPad PS/2, ports HDMI/VGA, Alcor Micro USB Card Reader, etc..

--------------------------------------------------------------------------------------------

### BIOS Configuration

Bios Config | Setting 
:---:| :---:
Security -> Secure Boot | Disabled
Intel Virtualization    | Enabled OK / Disabled if you have issues
VT-d | Disabled / Enabled with boot-args "dart=0"
Graphics Configuration -> DVMT Pre-Allocation | 64M / default 32M but need pre-alloc patches
USB Configuration -> XHCI Pre-Boot Mode | Smart Auto / Enabled
SATA Mode | AHCI
Boot -> Launch CSM | Enabled (For Reducing boot graphics glitch)
 
--------------------------------------------------------------------------------------------
 
### What's Working?

- [x] QE/CI Intel HD Graphics 5500 with VRAM 3,5 GB (3584 MB), Nvidia Geforce 930M (Disable)
- [x] Audio Conexant CX20751/2 with layout-id 21 + Internal Microphone (SSDT-CX207512.aml + Lilu.kext + AppleALC.kext)
- [x] Display brightness PNLF and Fn Keys (DSDT Patch Fix Graphics Broadwell from RehabMan Repo + ASUS DSDT Patches Brightness FN Key + AsusSMC.kext)
- [x] Qualcomm Atheros AR9565 Wifi (ATH9KFixup.kext + ATH9KInjector.kext + Lilu.kext)
- [x] LAN Ethernet Realtek RTL8111GU/8168GU/8411GU (RealtekRTL8111.kext)
- [x] FocalTech TouchPad PS/2 (ApplePS2SmartTouchpad.kext)
- [x] Battery Indicator (DSDT RehabMan Battery Laptop Patch for ASUS + SMCBatteryManager.kext)
- [x] WebCam for Facetime HD Camera Built-In (CustomPeripheral.kext)
- [x] USB3.0 Port + Power/Speed (Rename XHCI to XHC in config.plist + SSDT-EC-UIAC.aml + USBInjectAll.kext + Remove Port Limit Kext to Patches in config.plist)
- [x] Native Power Management CPU (SSDT.aml combine from [ssdtPRGen.sh](https://github.com/Piker-Alpha/ssdtPRGen.sh) Pike R. Alpha and [ssdt_data](https://github.com/acidanthera/CPUFriend/blob/master/Instructions.md#data-combination) PMheart + CPUFriend.kext + CPUFriendDataProvider.kext)
- [x] Apple Graphics Power Management (AGPM) edit Info.plist VirtualSMC.kext for Macbook Pro 12,1
- [x] Etc..
 
--------------------------------------------------------------------------------------------
 
### Not Working?

- Nvidia Geforce 930M (Optimus Tech) not supported by hackintosh
- AirDrop, Handoff, Continuity, Because this chipset and module not supported
- Bluetooth Atheros AR3012 v4.0 Controller, ID Vendor 0x13D3 (5075), ID Product 0x3423 (13347), Because no Firmware Key or Kext for this Chipset, Alternatively must be Load to Windows for Pairing or use Sleep and Wake Method with BTFirmwareUploader.kext (Edited Info.plist)
- Etc..

--------------------------------------------------------------------------------------------

### Not Tested?

- HDMI
- Etc..
 
--------------------------------------------------------------------------------------------
 
### Notes

1. OC Folder still under development, because version 0.6.0 DSDT not included anymore, maybe many not works/issues for laptop such as ADBG, AC0/ADP1, Log Battery issues, and other
2. Don't use my patch [DSDT.aml and SSDT.aml](https://github.com/asepms92/Hackintosh-ASUS-A455LF-Notebook/tree/master/CLOVER/EFI/CLOVER/ACPI/patched) if you have different <b>ACPI Tables/BIOS Version and Model/Freq CPU PM</b>
3. To get match on/off my BT, edit Info.plist (BTFirmwareUploader.kext + BluetoothDevQAtherosInjector.kext + BluetoothDevBroadcomInjector.kext) then add for Product ID (3423) and Vendor ID (13D3), and install to /Library/Extensions But need Sleep and WakeUp for load firmware bluetooth, or use another method, follow [this tutorial](https://osxlatitude.com/forums/topic/10127-updated-nov-2017-fix-btfirmwareuploader-in-macos-high-sierra/), not for Catalina

<img src="/Images/Sept-MacBook-Images-Bluetooth.png?raw=true" alt="macOS Mojave" align="center">

4. For Wifi Atheros AR9565 need boot args "-ath9565" to load ATH9KFixup.kext + ATH9KInjector.kext in /Library/Extensions
5. "XX-MASKED-XX" in My [config.plist](https://github.com/asepms92/Hackintosh-ASUS-A455LF-Notebook/tree/master/CLOVER/EFI/CLOVER/config.plist#L896) just cosmetics, You need regenerate of them or find another serial number for your mac, Use Clover Configurator
6. And many more [apps](https://github.com/asepms92/Hackintosh-ASUS-A455LF-Notebook/tree/master/Tools/Apps)
--------------------------------------------------------------------------------------------
 
### Special Thanks and Credits to :

[Apple](https://www.apple.com) | [Clover](https://sourceforge.net/projects/cloverefiboot) | [Acidanthera](https://github.com/acidanthera) | [Rehabman](https://github.com/RehabMan/Laptop-DSDT-Patch) | [Mieze](https://github.com/Mieze/RTL8111_driver_for_OS_X) | [Mirone](https://github.com/Mirone/AppleHDAPatcher) | [EmlyDinesh](https://osxlatitude.com/forums/topic/1948-elan-focaltech-and-synaptics-smart-touchpad-driver-mac-os-x) | [AnV](https://github.com/andyvand/FixEDID_Devel) | [Piker R. Alpha](https://github.com/Piker-Alpha/ssdtPRGen.sh) | [InsanelyMac](https://www.insanelymac.com/forum), [Olarila](http://olarila.com/forum) and [OSXLatitude](https://osxlatitude.com/forums) Forum | <b>And Other Developers</b> who aren't mentioned.
