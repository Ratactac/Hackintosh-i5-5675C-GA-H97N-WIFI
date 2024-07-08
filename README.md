# Hackintosh MacOS Monterney 12.0.0 - Intel i5 5675C (Broadwell) + GigaByte GA H97N-Wifi


![https://github.com/Ratactac/Hackintosh-i5-5675C-GA-H97N-WIFI/blob/main/Untitled-1.jpg](https://github.com/Ratactac/Hackintosh-i5-5675C-GA-H97N-WIFI/blob/main/Untitled-1.jpg)

## OpenCore 1.0.0  - Kext Updated July 2024

This is my own clean EFI for H97N-Wifi created by zero, and for my Broadwell Cpu. Not ready for Haswell. Adapted method for Hasweel is explain below. Fully working for my condition. I have following the Elite Guide, and Dortania. It includes some features below. Use it responsibly. Add your own Smbios close of your build ( CPU, iGPU). Usb map is ok.

## macOS: 12.0.0 - Smbios 16,2 (i5-5675R same to my 5675C CPU)
Dual boots Windows 11 and macOS Monterney.

## Complete hardware specs:
  + CPU: Intel i5 5675C ( Broadwell )
  + Motherboard: GigaByte H97N-Wifi
  + GPU: Internal Gpu ( Iris 6200 )
  + Wifi Works.
  + Sound Works.
  + Usb mapping properly.  
  + Ethernet: * Intel GbE LAN chip 
              * Atheros GbE LAN chip 
  + RAM: 16GB @ 1600 MHz DDR3
  + NVME & SATA SSD:
      + 500GB Sangung SSD 860 evo PCIe SSD ( MacOs )
      + 500GB Sangung SSD 860 evo PCIe SSD ( Windows )

## What's Works
+ Accelerated graphics on supported Intel Broadwell IGPUs. Adapt if you are using Haswell Cpu. Explain below.
+ Audio ( ALC892 ) ( alcid=1, changing layout if any problem -> layout 1, 2, 3, 4, 5, 7, 11, 12, 15, 16, 17, 18, 20, 22, 23, 28, 31, 32, 90, 92, 97, 99, 100 ) 
+ 2 ethernet differents ports works, one use AtherosE2200Ethernet, other RealtekRTL8111.
+ Wifi working with [itlwm installed](https://github.com/OpenIntelWireless/itlwm/releases) & [Heliport Wifi app](https://github.com/OpenIntelWireless/HeliPort/releases) , you have to install it on MacOs, cause you cant use wifi app from macos.
+ Airport and Bluetooth, are not included, you can install kext -> [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases)
+ USB
+ CPU power management
+ System wake, sleep, and shutdown
+ macOS installation and updates
+ System stability

## BIOS DETAILS Version Bios: F9b
+ Memory XMP Profile 1: Enabled (if supported by RAM)

## BIOS Features
+ Fast Boot = 	Disabled
+ VT-d =  Enabled
+ Windows 8 Features =	Windows 8 WHQL
+ CSM Support = 	Never
+ Secure Boot = 	Disabled

## Peripherals
+ XHCI Mode = 	Enabled
+ Intel Processor Graphics =	Enabled
+ Intel Processor Graphics Memory Allocation =  96M*
+ DVMT Total Memory Size =  MAX
+ Legacy USB Support =	Disabled
+ XHCI Handoff =	Enabled
+ Super IO Configuration → Serial Port A =	Disabled

          
## Note EFI

* Cfg lock Disabled not available in motherboard ->  AppleXcpmCfgLock is check in config.plist Kernel > Quirks .

* Vt-D activated    -> disableIOmapper is enabled.

* To adapt Framebuffer Video for Haswell CPU, You must determine family of your cpu & follow Patching Guide & setting important iGPU properties : 
first  step is to catch info > Google > Ark intel + name of your Cpu. Note your code name + iGpu name.

If you have Haswell, & according of your Igpu and your choice, open OCAuxiliaryTools, mount EFI partition and open with EFI/OC/config.plist. Go to DP > Add > PciRoot(0x0)/Pci(0x2,0x0) > Change AAPL,ig-platform-id broadwell value "07002216" :

* Haswell, AAPL,ig-platform-id is 04001204, for dGpu (amd) + iGpu computing tasks.
* Haswell, AAPL,ig-platform-id is 0300220D, for iGpu display & computing tasks.
* If only your CPU uses hd 4400 Igpu, add a new key below AAPL,ig-platform-id, > Device ID, data, value = 12040000.

* Broadwell, AAPL,ig-platform-id is 07002216, for iGpu drive display & computing tasks.

* [More info > WhateverGreen's Framebuffer Patching Guide](https://github.com/acidanthera/WhateverGreen/blob/master/Manual/FAQ.IntelHD.en.md)
* [dortania guide](https://dortania.github.io/OpenCore-Post-Install/gpu-patching/intel-patching/#getting-started)

## Note Usb Map 

This is my own EFI created by zero with my own Usb Map. Use it responsibly. I think it's pretty clean.
  
## Tool you need

[OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools)

## Credits 

[EliteForum](https://elitemacx86.com/)

[Bible](https://dortania.github.io/docs/latest/Configuration.html)
