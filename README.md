#  HackPro X99 System

Until Apple blesses us with the MacPro7,1 – this is for those who require tools to do their work. An appropriate bicycle for the mind.

## Build

### X99-8D3 Xeon V3 Haswell-EP Clover Mojave 10.14.6

#### Hardware:

CPU: Intel Xeon E5-2678 v3 (12 core, 2.5 GHz / 3.3 GHz Boost)
Motherboard: SZMZ X99-8D3
RAM: 16GB DDR3-14900R 1866Mhz ECC RDIMM modules
GPU: Radeon RX Vega 64 8GB
Storage: Phison E12 m.2 NVMe PCI-E 3.0 x4 SSD
Water blocks: BARROW CPU + GPU
Radiator: 360mm x 25mm slim
Pump: DDC

Case dimensions: 431 mm x 342 mm x 177 mm

#### Software

macOS Mojave 10.14.6

### BIOS

Reset to defaults (F9)

### Clover

 Install Clover_v2.5k_r5066 (tested).

If you try a newer version, post your experience.


UEFI

    ApfsDriverLoader.efi
    HFSPlus.efi
    AptioMemoryFix.efi
    SMCHelper.efi
    AudioDxe.efi


Kexts

    Lilu
    WhateverGreen
    FakeSMC
    AppleALC
    RealtekRTL8111
    USBInjectAll

 config.plist

ACPI > DSDT > Patches > "change AZAL to HDEF"

Boot > Arguments =
        Debug: -v dart=0 npci=0x2000 keepsyms=1 debug=0x100
        Production: dart=0 npci=0x2000

CPU > Type = 0x0A01



KernelAndKextPatches > KernelToPatch



xcpm_pkg_scope_msrs © Pike R. Alpha

find <31d2e8b4 fcffff>

replace <31d29090 909090>



_xcpm_ performance_patch © Pike R. Alpha

find <c1e30848 63d389d0 48c1ea20>

replace <c1e308b8 00ff0000 31d29090>



_xcpm_SMT_scope_msrs 1 © Pike R. Alpha

find <be0b0000 005de908 000000>

replace <be0b0000 005dc390 909090>



_xcpm_SMT_scope_msrs 2 © Pike R. Alpha

find: <31d2e87e fcffff>

replace: <31d29090 909090>



KernelAndKextPatches > KextsToPatch



IOPCIFamilyPatch ©PMHeart

find: <483d0000 0040>

InfoPlistPatch: NO

name: IOPCIFamily

replace: <483d0000 0080>



RtVariables

BooterConfig: 0x28

CsrActiveConfig: 0x67

ROM: UseMacAddr0



************************** [ IMPORTANT ] **************************



Must specify:  SMBIOS > Memory > Modules



Otherwise, system will not boot past / get stuck at / freeze at :



End RandomSeed

+++++++++++++++++++++++++++++++++



******************************************************************


## Benchmarks


 MacPro 6,1

 XCPM OFF
 XCPM ON

 iMacPro1,1
OpenCL

NVMe

 Win 10 x64 v1809
AIDA64 - Cache & Memory

Geekbench 5 benchmarks

    current: https://browser.geekbench.com/v5/cpu/207919 

        Single-Core Score: 757

        Multi-Core Score: 4681


    (Possible) all core unlocked : https://browser.geekbench.com/v5/cpu/213050 

        Single-Core Score: 776

        Multi-Core Score: 7589


Reference

    iMacPro1,1 / Intel Xeon W-2195 2300 MHz (18 cores) https://browser.geekbench.com/v5/cpu/241767 

        Single-Core Score:  1149

        Multi-Core Score:  13586

    iMacPro1,1 / Intel Core i9-7920X 2904 MHz (12 cores)  https://browser.geekbench.com/v5/cpu/241618 

        Single-Core Score:  1160

        Multi-Core Score:   13030

## Project Status

### Whats working

Video
Sleep / Wake
XCPM / Idle, TurboBoost

### Issues


### TODO

+ USB SSDT
+ FileVault 2
+ Boost 3.3 GHz
          Memory read
                     Win 10 x64 ~ 55,204 MB/s (3.3GHz)
                     macOS 10.14 ~ 34,000 MB/s (3.0 GHz)
+ All core 3.3GHz boost
+ Resume from sleep not instant, takes ~ 20s
+ Overclock

### Changelog

2019-09-25            add geekbench 5 benchmarks

2019-09-19            initial guide

### Thank you

Apple

뉴해킨

sixflow

ZISQO

Clover developers

acidanthera

Diego

Anyone else I forgot
