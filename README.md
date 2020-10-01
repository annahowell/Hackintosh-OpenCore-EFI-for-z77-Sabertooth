# OpenCore 0.5.9 EFI for Asus z77 Sabertooth

This is mostly a raw dump of the EFI I use for my z77 Sabertooth running Catalina 10.15.6 with OpenCore 0.5.9. I have chosen to host the files here incase it helps someone struggling with their own z77 Sabertooth hackintosh.   

The included files and config were pieced together from several excellent guides and are owned by their respective authors; I simply created the config.plist, SSDT .aml files and USBMap.kext.

### What works:
Everything basically, including point release updates, USB mapping and power states/sleep. Handoff and continuity work with a Fenvi T919 too. From all I can tell the only things not working are sidecar (presumably due to a lack of x265 hardware encoding on the 3770K), and the filevault unlock screen uses a slightly wrong aspect ratio on the RX570 and my 4K Monitors.

### My current setup:
- Asus z77 Sabertooth (BIOS 2104)
- 3770K (stock under MacOS, HD4000 disabled in BIOS)
- Sapphire Nitro+ RX570 (first PCI-E slot, stock vBIOS, all output work)
- EVGA Hybrid 1070 (OPTIONAL: second PCI-E slot, disabled by SSDT)
- Intel SATA SSD (connected to a chipset port - NOT ASMedia port)
- Onboard ALC892 Audio (For headset)
- Sabrent AU-EMAC USB Soundcard (OPTIONAL: External speakers, saves having to unplug headset)
- Onboard 82579V 1Gbe LAN
- Fenvi T919 (Wireless/ Bluetooth)
- ASUS XG-C100C PCI-E (OPTIONAL: Not flashed for use by MacOS and thus ignored by it)
- Apple magic keyboard and trackpad2 (OPTIONAL)

### Disabling unsupported GPUs
Currently the included `/EFI/OC/ACPI/SSDT-GPU-DISABLE.aml` file disables PCI-E slot 2 (second closest to CPU). If instead your other MacOS unsupported GPU is plugged in to PCI-E slot 1 (closest to CPU), rename `/PCIE-Disable-SSDTs/SSDT-GPU-DISABLE-slot1.aml` to `SSDT-GPU-DISABLE.aml` and put it in the `/EFI/OC/ACPI/` folder, thus overwriting the file that currently exists there.


### Serial number
I have removed my Mac serial number etc from the config.plist, how to find your own is beyond the scope of this readme, sorry.

### Misc
1. If you don't have a 3770K CPU you should remake your SSDT-PM.aml. How to do so is included in [this excellent guide](https://dortania.github.io/OpenCore-Install-Guide/).
2. The included config.plist has verbosity disabled during startup, you can google how to enable it if you have issues.
3. All bootloader and kext files are release rather than debug versions.   
   
**This will not work with opencore 0.6.0, I'll migrate post Big Sur and release an update then**
