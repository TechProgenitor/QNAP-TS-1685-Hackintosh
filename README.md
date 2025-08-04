<img src="https://www.qnap.com/i/_attach_file/product/photo/1000_625/267_1487217574_TS-1685_Right-angle-of-elevation.png" width="497" height="349">

[![](https://img.shields.io/badge/Bootloader-OpenCore_1.0.3_RELEASE-blue)](https://github.com/acidanthera/OpenCorePkg/releases/tag/1.0.3) [![](https://img.shields.io/badge/macOS-Sequoia%2015.4.1-148F77)](https://apps.apple.com/us/app/macos-sequoia/id6596773750?mt=12) [![](https://img.shields.io/badge/QNAP-TS--1685-1F618D)](https://www.qnap.com/en-us/product/ts-1685)

# Images
PCIe Slots  |  PSU Upgrade
:--:|:--:
The storage card was shaved down with sandpaper in order to fit inside the casing.<br><img src="Assets/QNAP_Slots.png" style="width: 667px; height: 500px;"> |  A custom cable was created to power the backplane with the new supply.<br><img src="Assets/QNAP_PSU.png" style="width: 375px; height: 500px;">

# Tests
## 2/5/2025
[![QNAP TS-1685 Hackintosh Test #1](https://img.youtube.com/vi/eVvyXmYADU4/0.jpg)](https://www.youtube.com/watch?v=eVvyXmYADU4 "QNAP TS-1685 Hackintosh Test #1")

# Please Note

The 16 bays on the front of the NAS currently don't work. Until a solution is discovered, you'll need to use the internal M.2 SATA slots or add a PCIe storage card in order to install and run macOS.

# Limitations

The QNAP BIOS won't let you add items to the boot order. If OpenCore is installed on the EFI partition, you'll need to boot into a Linux distro and run the following command. Be sure to update the `-d` and `-p` values to reflect your actual bootloader location:

`sudo efibootmgr -c -d /dev/nvme0n1 -p 1 -L "OpenCore" -l '\EFI\OC\OpenCore.efi'`

# ⚠️ Warning

The default PSU that came with my NAS was 250W. If you decide to add a graphics card, you'll need to upgrade to a higher wattage. QNAP sells a 550W PSU, but I instead upgraded to the [Corsair SF1000](https://www.corsair.com/us/en/p/psu/cp-9020257-na/sf-series-sf1000-fully-modular-80-plus-platinum-sfx-power-supply-cp-9020257-na?srsltid=AfmBOoovL2eX4BIqp2PZLZlaP9VSegQAGZZRrlZb8xMsjBT6iEyEVkF3) which is 1KW. I had to then create a custom cable in order to power the backplane of this NAS with the new supply. If you would like to do the same, here's the parts and pinout that you'll need to follow. 

**I am not responsible for any damage, injury, or malfunction that may result from improper crimping or assembly. Proceed at your own risk.**

<img src=Assets/Type_5_Custom_ATX.png>

| Housing | Connector | Part Number | Quantity |
| ------------- | ------------- | ------------- | ------------- |
| 6-pin | Micro-Fit 3.0 Receptacle Housing, Dual Row, 6 Circuits, UL 94V-0, Low-Halogen, Black | 43025-0600 | 3 |
| 8-pin | Micro-Fit+ Receptacle Housing, Dual Row, 8 Circuits, UL 94V-0, Glow-Wire Capable, Black | 206461-0800 | 1 |
| 20-pin | Mini-Fit Jr. Receptacle Housing, Dual Row, 20 Circuits, UL 94V-2, Natural | 39-01-2200 | 1 |

| Crimp | Connector | Part Number | Quantity |
| ------------- | ------------- | ------------- | ------------- |
| 6-pin | Micro-Fit 3.0 Crimp Terminal, Female, with Tin (Sn) Plated Phosphor Bronze Contact, 18 AWG, .073in / 1.85mm Max Insulation Outside Diameter, Reel | 43030-0038 | 12 |
| 8-pin | Micro-Fit+ Crimp Terminal, Female, Tin (Sn) Plating, 18 AWG | 43030-0038 | 8 |
| 20-pin | Mini-Fit Female Crimp Terminal, Tin (Sn) over Copper (Cu) Plated Brass, Double 22+22 or Single 24-18 AWG, Reel. | 39-00-0038 | 20 |
#
I personally used [18AWG UL1007 stranded hookup wire](https://www.amazon.com/dp/B00NB3TCQG?ref=ppx_yo2ov_dt_b_fed_asin_title) to create the cable. Anything thinner than 20 AWG will be insufficient for the load. Below are the correct tools to crimp the wire, however, I personally used a [cheap kit](https://www.titanrig.com/alphacool-eistools-crimping-kit.html?gad_source=1&gad_campaignid=20570235782&gbraid=0AAAAADgn6DVrV8aLjZXIrpTOn7iBzczok&gclid=CjwKCAjwkbzEBhAVEiwA4V-yqoCuLUXQ4hHpIPiAzBZZs9-BEazncC4dMtFlUTJj05wLucF5K-N1jhoC5CwQAvD_BwE) to save money.
#
| Tool | Part Number |
| ------------- | ------------- |
| Hand Crimp Tool for Micro-Fit 3.0 Female Crimp Terminals, 0.75mm² and 18AWG (UL1061) wires | 63828-0200 |
| Hand Crimp Tool for Micro-Fit Plus Crimp Terminals, 18-16 AWG, UL1061 Wire | 213309-4400 |
| PremiumGrade Hand Crimp Tool for Mini-Fit Jr. Male and Female Terminals, 24-18 AWG | 63819-0901 |

# Specifications

| Hardware | QNAP TS-1685 |
| ------------- | ------------- |
| CPU | Intel Xeon D-1531 |
| GPU | AMD Radeon RX 6950 XT |
| Chipset | Intel C220 Series Chipset |
| Memory | 4x - Samsung M393A4K40BB0-CPB<br>32GB DDR4 2133MHz |
| Storage | StarTech PEX8M2E2<br>Dual M.2 PCIe SSD Adapter Card
| USB | Genesys Logic, Inc. USB 2.0 Hub<br>Intel 8 Series/C220 Series Chipset |
| WiFi/BT | Fenvi FV-HB1200|
| LAN | Intel X550 10Gbit Ethernet Controller<br>Intel i211 1Gbit Ethernet Controller |
| Audio | KAB-001 |

# Issues
| | |
| --- | --- |
| Wake not working across all operating systems.| Likely ACPI or BIOS related. Sleep was fixed universally with `SSDT-SLEEP.aml` and the Enable S3 ACPI Patch in the `config.plist` |
| Storage bays not working. | The backplane uses a Marvell 88SE1475 chip. It doesn't seem to be supported in macOS, and would require writing a kext to work properly. Otherwise, it might be possible to purchase a backplane from QNAP with the Asmedia ASM1164 chip which is fully supported in macOS. Another solution is purchasing a PCIe x8 HBA card such as the LSI 9400-16i.
| i2c display always says "Booting..." | Seems like QNAP's firmware is supposed to change the text on the display when its OS loads. Since we're running macOS, it likely requires a script in userspace to update it.
| Copy button and i2c buttons don't do anything. | Will need to determine the protocol and add OS functionality. |