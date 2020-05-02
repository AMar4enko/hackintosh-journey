My new Catalina Hackintosh build, OpenCore 0.5.8:  
*Price levels are for early 2020*

## Hardware:
- `Supermicro X9DRi-LN4F+` **~$300**
- `Xeon E5-2690v2 3Ghz` x2  **~$400**, sourced from Aliexpress
- `1866Mhz ECC RAM 4x32Gb` **~$250**, sourced from Aliexpress
- `XFX ATI Radeon RX 570 8Gb` **~$100**
- `Asus HYPER M.2 X16 CARD` **$60**
- `Fresco-based USB 3.0 card` **~$35** 2 rear panel ports + internal socket for case frontpanel connection, sourced from Aliexpress
- `BCM94360CD-based WiFi + Bluetooth adapter` **~$50** sourced from Aliexpress
- `XPG Gammix 1Tb NVMe SSD` **~$150**
- `Samsung PM961 1Tb NVMe SSD` **~$90** sourced from Aliexpress. No native macOS support, replaced in favour of XPG Gammix, using for Windows 10 dual boot
- `Samsung EVO 860 SATA SSD` **can't remember** extra garbage storage for macOS

## BIOS
[version 3.3, patched to add boot from NVMe feature:](BIOS.zip)
  - Advanced -> Chipset Configuration -> North Bridge:  
    * Asus M.2 X16 card slot bifurcation set to x4
  - Advanced -> Chipset Configuration -> South Bridge:  
    * Legacy USB Support - Disabled
    * EHCI Hand-off - Enabled
  - Advanced -> SATA Configuration:
    * SATA Mode - AHCI Mode
  - Advanced -> PCIe/PCI/PnP:
    * Launch storage OpROM policy - UEFI only
    * Above 4G Decoding - Enabled
    * VGA Priority - Offboard

## ACPI
[ACPI F4 clover dump](ACPI.zip)

## Difficulties
- Initially, Intel I350 Gigabit ethernet used to work with IntelIGB.kext, then all of sudden i started to get KPs at boot time, indicating it in the backtrace. So i did extra search and found out i can do device rename to get it to work natively as I250. The only drawback of the approach i got only 1 port of 4 available to work. Fine by me.
- VIA VL805/VL812 based ORICO USB 3.0 claimed to be supported natively, didn't function properly. GenericXHCI kext turned it into USB 2.0, replaced with Fresco-based one, works OOB
- Intel Power Gadget doesn't work on dual-cpu builds

## No solution yet
### CPU power management 
By all evedences system doesn't leverage full CPU performance.  
Steps to get PM to work had been taken - created SSDT using Pike's script, patched xcpm bootstrap to support Ivy Bridge (this part appeared not to work) - below is an excerpt from OC boot log:
```
06:361 05:583 OC: Kernel patcher result 10 for kernel (_xcpm_bootstrap (Ivy Bridge) 10.15) - Not Found
06:666 00:305 OC: Kernel patcher result 8 for com.apple.driver.AppleIntelCPUPowerManagement (Fix CPU PM 6) - Not Found
```

- [kextstat](kextstat.txt)
- [AppleIntelInfo](AppleIntelInfo.MD)
- `sysctl -n machdep.xcpm.vectors_loaded_count` - 0
- `sysctl -n machdep.xcpm.mode` - 0


## Geekbench 4:
  single CPU: ~2800  
  multi CPU: ~3600