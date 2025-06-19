# OpenCore config for the HP ProDesk 600 G2 Mini
## Device Specs
**CPU:** Intel Core i5-6500T\
**GPU:** Intel HD Graphics 530\
**Chipset:** Intel Q150\
**Storage:** NVMe WDC PC SN520, SATA SSD Samsung 870 EVO\
**Ethernet:** Intel Ethernet Connection I219-LM\
**WiFi/Bluetooth:** Intel Dual Band Wireless-AC 7265\
**Audio:** Realtek ALC221
## Version
Tested on macOS 12.7.6 and 15.5\
BIOS Version is N22 Ver 02.60, latest from HP's website
## Config
OpenCore version used is 1.0.4
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
- [IntelBluetoothFirmware, IntelBTPatcher](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)
- [NVMeFix](https://github.com/acidanthera/NVMeFix) **(if NVMe storage is used)**
- [HibernationFixup](https://github.com/acidanthera/HibernationFixup)
- [RTCMemoryFixup](https://github.com/acidanthera/RTCMemoryFixup) (fixes CMOS Checksum Mismatch startup error after macOS use)
- [FeatureUnlock](https://github.com/acidanthera/FeatureUnlock) (optional, see details on repo)
