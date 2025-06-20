# OpenCore config for the HP ProDesk 600 G2 Mini
## Device Specs
**CPU:** Intel Core i5-6500T\
**GPU:** Intel HD Graphics 530\
**Chipset:** Intel Q150\
**Storage:** NVMe WDC PC SN520, SATA SSD Samsung 870 EVO\
**Ethernet:** Intel Ethernet Connection I219-LM\
**WiFi/Bluetooth:** Intel Dual Band Wireless-AC 7265\
**Audio:** Realtek ALC221, **alcid=11**
## Version
Tested on macOS 12.7.6 and 15.5, but anything from 10.11 up to even 26 should work if you know how to\
BIOS Version is N22 Ver 02.60, latest from HP's website
## Status
### ✅ - Fully supported
### ⚠️ - Partially supported
### ❌ - Not supported
|Feature|Status|Notes |
|:-----:|:----:|:----:|
|CPU power management|✅|
|Audio|✅|
|SATA storage|✅|
|NVMe storage|✅|
|USB Ports|✅|
|Graphics|✅|
|DisplayPort|✅|
|VGA Port|❌|Screen loses signal when GPU driver is loaded|
|Wi-Fi|✅|
|Bluetooth|⚠️|Can't seem to connect earphones?|
|Sleep|✅|

## Config
[OpenCore](https://github.com/acidanthera/OpenCorePkg) version used is 1.0.4, if you want to go higher follow the [updating guide](https://dortania.github.io/OpenCore-Post-Install/universal/update.html#updating-opencore)\
Download required files according to the Dortania OpenCore guide (Drivers, Tools, etc.). The ones i used are listed in the config. Make sure to use regular HFSPlus driver from [OCBinaryData](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi).\
Kexts used are listed in the **Kexts** section below. USB map is there too, but if it doesn't work for you, [map USB ports yourself.](https://github.com/USBToolBox/tool)\
ACPI patches used are included in the repo and listed in the **ACPI Patches** section below. If they don't work for you, [make your own.](https://dortania.github.io/Getting-Started-With-ACPI/ssdt-methods/ssdt-methods.html)\
If using OpenCanopy and/or enabling the boot chime, also extract Resources from [OCBinaryData](https://github.com/acidanthera/OcBinaryData)\
Copy the config to your EFI/OC folder, then open it in ProperTree and do an OC Snapshot (Ctrl+R).\
**Don't forget to download the appropriate version of macOS recovery if installing for the first time.**

Finally, try to boot OpenCore. If all goes well, you should see macOS/Recovery Mode.\
After installing, [disable verbose startup if you want to](https://dortania.github.io/OpenCore-Post-Install/cosmetic/verbose.html)
## ACPI Patches (made with SSDTTime)
- SSDT-PLUG (PluginType)
- SSDT-EC (FakeEC)
- SSDT-USBX
- SSDT-HPET (Fix HPET)
- DMAR (Fix DMAR, **used if VT-d is enabled in BIOS**)
## Kexts (download separately)
- [Lilu](https://github.com/acidanthera/Lilu)
- [VirtualSMC](https://github.com/acidanthera/VirtualSMC)
   - SMCProcessor (CPU clock & temperature monitoring)
   - SMCSuperIO (fan speed monitoring)
- [WhateverGreen](https://github.com/acidanthera/WhateverGreen)
- [AppleALC](https://github.com/acidanthera/AppleALC)
- [USBMap](https://github.com/corpnewt/USBMap) (included in repo)
- [AirportItlwm/itlwm](https://github.com/OpenIntelWireless/itlwm) (for wifi)
- [IntelMausi](https://github.com/acidanthera/IntelMausi) (for ethernet port)
- [BlueToolFixup](https://github.com/acidanthera/BrcmPatchRAM) (for Bluetooth)
- [IntelBluetoothFirmware, IntelBTPatcher](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) (for Bluetooth)
- [NVMeFix](https://github.com/acidanthera/NVMeFix) **(only if NVMe storage is used)**
- [RestrictEvents](https://github.com/acidanthera/RestrictEvents) **(used for OTA updates on Ventura and newer,** +misc fixes)
- [HibernationFixup](https://github.com/acidanthera/HibernationFixup) (self-explanatory)
- [RTCMemoryFixup](https://github.com/acidanthera/RTCMemoryFixup) (fixes CMOS Checksum Mismatch startup error after macOS use)
- [FeatureUnlock](https://github.com/acidanthera/FeatureUnlock) (optional, see details on repo)
