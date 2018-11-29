## OS-X-HP-EliteDesk-800-G3-DM-Clover
This repository contains the files and scripts to install macOS on the HP EliteDesk 800 G3 Desktop Mini Business PC (35 W/65 W).

![HP EliteDesk 800 G3 Desktop Mini Business PC](https://support.hp.com/doc-images/700/c05373338.jpg)

## Hardware Specs
### Basic info
Here is my EliteDesk 800 G3 DM specs:
- Product Number: Y3A18AV
- Product Name: HP EliteDesk 800 G3 DM 65W
- BIOS: P21 Ver.02.22 07/17/2018

### Specs:
- CPU: Intel® Core i7-7700 @ 3.60 GHz processor (65 W model only)
- GPU: Integrated Intel® HD Graphics 630
- Memory: 2 x 4GB Samsung DDR4-2400
- Storage: Intel® 256 GB SSD, PCI-E Gen3 x 4, Turbo Drive G2 TLC SSD
- LAN: Intel® I219LM Gigabit Network Connection LOM
- WLAN: Intel® 8265 802.11ac 2x2 Wi-Fi with Bluetooth M.2 Combo Card Vpro (802.11ac Wave 2 supported)
- Audio: Conexant CX20632 Audio Codec (all ports are stereo, 1 internal speaker, 1 front headphone, 1 front CITA port)

Full specs you can get from [HP Website](https://support.hp.com/us-en/document/c05371240?jumpid=reg_r1002_cnzh_c-001_title_r0002).

## Configure BIOS Settings
To start, set BIOS to defaults.
Then insure:
- Advanced -> Boot Options
  - Disable **Fast Boot**
  - Disable **CD-ROM Boot**
  - Enable **USB Storage Boot**
  - Disable **Network (PXE) Boot**
  
- Advanced -> Secure Boot Configuration
  - Select **Legacy Support Enable and Secure Boot Disable**, press **F10** to save changes, system will reboot and lead you to Secure Boot and ask you to input a 4 digits security code for authorization, type in the code shows on the screen and enter to reboot and then press **F10** again to enter BIOS configuration
  - Uncheck **Enable MS UEFI CA key** if you don't use Windows

- Advanced -> System Options
  - Disable **Virtualization Technology (VTx)**
  - Disable **Virtualization Technology for Directed I/O (VTd)**
  - Enable **M.2 SSD** if you're using a NVME SSD
  - Uncheck **M.2 WLAN/BT** if you're using a Intel 8265NGW or other unsupported card
  - Check **Allow PCIe/PCI SERR# Interrupt** (Uncheck it if have interruption issues)

#### Advanced -> Built-in Device Options
- Disable **Wake on LAN**
- Set Video memory size to **64MB** or larger
- Disable **LAN/WLAN Auto Switching**
- Disable **Wake on WLAN**

#### Advanced -> Port Options
- Enable **all** if no specific reasons.

#### Advanced -> Power Management Options
- Disable **Extended Idle Power States**

Press **F10** to save changes.

## Installation
- To be updated

### Tested OS
- macOS High Sierra 10.13.6 

### Clover
- Clover r4726

### Kexts
- FakePCIID_XHCIMux.kext (1.3.15) 
- FakeSMC.kext (6.26-357-gceb835ea.1800)
- IntelMausiEthernet.kext (2.4.1d1)
- Lilu.kext (1.2.8)
- VoodooHDA.kext (2.9.1)
- WhateverGreen.kext (1.2.4)
- XHCI-unsupported.kext (0.9.2)

## Known Issues:
- Audio codec CX20632 is not supported yet, using VoodooHDA instead.
