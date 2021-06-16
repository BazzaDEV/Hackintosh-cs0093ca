# Hackintosh - HP Pavilion 15-cs0093ca

## Hardware Specifications

*Disclaimer: I have upgraded some parts in this system. They are annotated as such.*

### Processor
![](https://img.shields.io/badge/-OEM-green) **CPU**: Intel Core i7-8550U @ 1.80GHz w/ Turbo Boost up to 4.00GHz (Kaby Lake R) (8.0 MB L3 cache, 2400-MHz FSB, 15 W)  

### Graphics
![](https://img.shields.io/badge/-OEM-green) **iGPU**: Intel UHD Graphics 620  
![](https://img.shields.io/badge/-OEM-green) **dGPU**: NVIDIA GeForce MX150  

### Memory
![](https://img.shields.io/badge/non--OEM-red) GSkill Ripjaws 16GB 2400MHz DDR4 SO-DIMMs (2x8GB)  

### Storage
![](https://img.shields.io/badge/non--OEM-red) WD Black SN750 M.2 NVMe SSD - 500GB *For Windows*  
![](https://img.shields.io/badge/non--OEM-red) Kingston SA400S37 SATA SSD - 240GB *For macOS*  

### Connectivity
![](https://img.shields.io/badge/-OEM-green) **Ethernet**: Realtek 8168   
- (*Realtek PCIe GbE Family Controller* is shown, but I extracted the exact model by looking at "Properties", navigating to "Details", then selecting "Drive node strong name" from the "Property" dropdown)  

![](https://img.shields.io/badge/-OEM-green) **WLAN/Bluetooth**: Intel Dual Band Wireless-AC 7265 802.11ac 2 × 2 Wi-Fi + Bluetooth 4.2 Combo Adapter (non-vPro)  
![](https://img.shields.io/badge/-OEM-green) **Audio**: Realtek ALC295

## Important Notices

- Make sure you follow the guide for **Laptop Kaby Lake**. There is some conflicting information on the Internet about this (mostly saying to follow Coffee Lake guide), I asked people who know what they're doing and they've confirmed my initial statement - [**follow the guide for Laptop Kaby Lake**](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/kaby-lake.html#laptop-kaby-lake).

## USB Creation

### ACPI

| SSDT                | Version     | Download Link                                                                                                                | Other Information                                                                                                                                                       | Last Updated (By Me) |
|---------------------|-------------|------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| SSDT-PLUG           | May 28 2020 | [Click here](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-PLUG-DRTNIA.aml)    |                                                                                                                                                                         | June 15 2021         |
| SSDT-EC-USBX-LAPTOP | May 28 2020 | [Click here](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-EC-USBX-LAPTOP.aml) |                                                                                                                                                                         | June 15 2021         |
| SSDT-PNLF           | May 28 2020 | [Click here](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-PNLF.aml)           |                                                                                                                                                                         | June 15 2021         |
| SSDT-GPI0           | Manual      | [Link to local file](/EFI/OC/ACPI/SSDT-GPI0.aml)                                                                             | Follow the instructions [here](https://dortania.github.io/Getting-Started-With-ACPI/Laptops/trackpad-methods/manual.html#finding-the-acpi-path) to build this manually. | June 15 2021         |
| SSDT-dGPU           | Manual      | [Link to local file](/EFI/OC/ACPI/SSDT-dGPU-Off.aml)                                                                         | Follow the instructions [here](https://dortania.github.io/Getting-Started-With-ACPI/Laptops/laptop-disable.html#optimus-method) to build this manually.                 | June 15 2021         |

### Drivers
| Driver          | Version    | Download Link                                                                             | Last Updated (By Myself) |
|-----------------|------------|-------------------------------------------------------------------------------------------|--------------------------|
| HfsPlus.efi     | May 5 2021 | [Click here](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi) | June 15 2021             |
| OpenRuntime.efi |   ----->   | *Packaged with OC 0.7.0*                                                                  | June 15 2021             |

### Kexts

When initially setting up your Hackintosh, please use the DEBUG version of these kexts where applicable.

| Kext                   | Version        | Download Link                                                                                                   | Other Information                                                                                                   | Last Updated (By Myself) |
|------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|--------------------------|
| VirtualSMC             | 1.2.4          | [Click here](https://github.com/acidanthera/VirtualSMC/releases/tag/1.2.4)                                      |                                                                                                                     | June 15 2021             |
| Lilu                   | 1.5.3          | [Click here](https://github.com/acidanthera/Lilu/releases/tag/1.5.3)                                            | Using SMCProcessor, SMCSuperIO, SMCBatteryManager                                                                   | June 15 2021             |
| WhateverGreen          | 1.5.0          | [Click here](https://github.com/acidanthera/WhateverGreen/releases/tag/1.5.0)                                   | Only add `WhateverGreen.kext`, ignore the rest                                                                      | June 15 2021             |
| AppleALC               | 1.6.1          | [Click here](https://github.com/acidanthera/AppleALC/releases/tag/1.6.1)                                        | Only add `AppleALC.kext`, ignore the rest                                                                           | June 15 2021             |
| RealtekRTL8111         | 2.4.2          | [Click here](https://github.com/Mieze/RTL8111_driver_for_OS_X/releases/tag/2.4.2)                               |                                                                                                                     | June 15 2021             |
| USBInjectAll           | 2018-1108      | [Click here](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/)                                     |                                                                                                                     | June 15 2021             |
| Airportltlwm           | 1.3.0          | [Click here](https://github.com/OpenIntelWireless/itlwm/releases/tag/v1.3.0)                                    | Download the ZIP for the correct version of macOS (We're on Big Sur right now)                                      | June 15 2021             |
| IntelBluetoothFirmware | 1.1.3          | [Click here](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases/tag/1.1.3)                    | Add both kexts (`IntelBluetoothFirmware.kext` and `IntelBluetoothInjector.kext`)                                    | June 15 2021             |
| NVMeFix                | 1.0.8          | [Click here](https://github.com/acidanthera/NVMeFix/releases/tag/1.0.8)                                         |                                                                                                                     | June 15 2021             |
| VoodooPS2              | 2.2.3          | [Click here](https://github.com/acidanthera/VoodooPS2/releases/tag/2.2.3)                                       |                                                                                                                     | June 15 2021             |
| VoodooSMBus            | 2.2            | [Click here](https://github.com/VoodooSMBus/VoodooSMBus/releases/tag/v2.2)                                      |                                                                                                                     | June 15 2021             |
| ECEnabler              | 1.0.1          | [Click here](https://github.com/1Revenger1/ECEnabler/releases/tag/1.0.1)                                        |                                                                                                                     | June 15 2021             |
| BrightnessKeys         | 1.0.2          | [Click here](https://github.com/acidanthera/BrightnessKeys/releases/tag/1.0.2)                                  |                                                                                                                     | June 15 2021             |
| CtlnaAHCIPort          | August 22 2020 | [Click here](https://github.com/dortania/OpenCore-Install-Guide/blob/master/extra-files/CtlnaAHCIPort.kext.zip) | Try booting without this first. You'll know if you need it if you boot into the installer but can't see your drive. | June 15 2021             |

## Config

Honestly, this was pretty straight forward. Most of what I did was straight up copying the guide.

Follow the guide for [Laptop Kaby Lake](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/kaby-lake.html#laptop-kaby-lake) and you should be good to go.

I will mention a few things below, which were either unclear, ambiguous, or super important and I will highlight them again:

- `DeviceProperties -> Add -> PciRoot(0x0)/Pci(0x2,0x0)`:
  - Make sure you use a device-id spoof as mentioned.

- `DeviceProperties -> Quirks`:
  - Double-check `LapicKernelPanic` is set to `FALSE`.

- `UEFI -> Quirks`:
  - `UnblockFsConnect` is set to `TRUE`. This is only explicity mentioned at the end of the guide, and I almost missed it.  
  *(In their defence, there is a comment when we first run into it in the guide saying it's needed mainly by HP motherboards but I missed that too.)*

- `NVRAM -> Add -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> boot-args`:
  - For `alcid=1`, replace `1` with the correct value to fix audio. You need to find which audio codec your PC is using first - this was quite difficult for me and I had to resort to booting Ubuntu from a USB, then using `cat /proc/asound/card0/codec#0 | less` to find the codec. 
  - **Mine was Realtek ALC295.**
  - For proper guidance, please follow [this section](https://dortania.github.io/OpenCore-Post-Install/universal/audio.html#finding-your-layout-id) of the post-install guide for complete instructions.

## BIOS

This was straight forward as well, but more so because the majority of these options are non-existent for us.

Still, make sure you either don't have those options or you've toggled them on/off accordingly.

*(I forgot to disable Secure Boot, if that helps anyone.)*  

## Post-Install

### Fixing Audio

Follow the official section of the post-install guide regarding this section [here](https://dortania.github.io/OpenCore-Post-Install/universal/audio.html#finding-your-layout-id).
## Random Notes

*These are for me to come back to if necessary. They may or may not apply to your case, so just try to go through the guide normally and come back here to see if there's anything useful for you to look into.*

### Kexts
- If installing to SATA drive but you can't see the SATA drive in macOS, add the [`CtlnaAHCIPort`](https://github.com/dortania/OpenCore-Install-Guide/blob/master/extra-files/CtlnaAHCIPort.kext.zip) kext.

### ACPI
- Dumped my DSDT [here](/dump/DSDT.aml)
- Apparently should be avoiding `SSDT-XOSI.aml` and should use `SSDT-GPIO.aml` instead, but regardless here it is if necessary: https://dortania.github.io/Getting-Started-With-ACPI/Laptops/trackpad-methods/prebuilt.html
- dGPU path in BIOS -> `\_SB.PCI0.RP01.PXSX`
