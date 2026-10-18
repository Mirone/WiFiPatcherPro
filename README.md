<p align="center">
  <img alt="MyKextInstaller" src=https://i.ibb.co/9XNrysP/Wi-Fi-Patcher-Pro.png" width="200">
</p>
<h3 align="center">Wi-Fi Patcher Pro</h3>

<p align="center">
<img src="https://img.shields.io/github/stars/Mirone/WiFiPatcherPro?style=flat&label=Stars&color=64748b" />
<img src="https://img.shields.io/github/downloads/Mirone/WiFiPatcherPro/total?style=flat&label=Downloads&color=64748b" />
<img src="https://img.shields.io/github/v/release/Mirone/WiFiPatcherPro?style=flat&label=Version&color=64748b" />
</p>

**Wi-Fi Patcher Pro** is a macOS application designed to automate and simplify the implementation of patches and compatibility fixes for Broadcom and Intel Wi-Fi adapters in Hackintosh systems using OpenCore or Clover bootloaders.

This tool provides an intuitive interface and a fully automated workflow, allowing you to apply necessary patches with a single click. The process includes the installation, configuration, and integration of essential components to restore or enable Wi-Fi functionality on compatible versions of macOS, including **macOS Sonoma, Sequoia, and Tahoe**.  

## How it Works

Wi-Fi Patcher Pro leverages **OCLP Root Patching** to bypass limitations introduced by Apple in recent macOS versions, where native support for many legacy Broadcom chipsets was removed. Through automated patching, system adjustments, and component injection during the boot process, the application restores support for previously incompatible wireless hardware.

Additionally, the tool assists in implementing compatibility solutions for **Intel Wi-Fi controllers** via the AirportItlwmkext (macOS Ventura version), significantly reducing the complexity of manual configuration and minimizing potential errors during installation and system maintenance.

## Key Features

-   **Automated Correction:** Optimizes your config.plist automatically.
-   **Bootloader Support:** Full compatibility with **OpenCore** and **Clover**.
-   **Smart Detection:** Automatically detects your bootloader and compatible Broadcom/Intel adapters.
-   **Kext Management:** Automated installation and copying of required kexts.
-   **Patching Logic:**

-   _OpenCore:_ Automatically patches Kernel (Add/Block), NVRAM, Misc (Security), and DeviceProperties.
-   _Clover:_ Automatically handles KextsToBlock, RtVariables, Boot Arguments, and Devices (Properties).

-   **System Integrity:** Automatically configures **System Integrity Protection (SIP)** settings required for patches.
-   **OS-Specific Tuning:** Includes specific boot arguments for **macOS Tahoe** only when required.
-   **Universal Compatibility:** Supports both Intel and AMD platforms.
-   **Safety First:** Automatically disables AirportBrcmFixup.kext on AMD systems if incompatible settings are detected.
-   **Recovery & Logs:** Includes automatic config.plist backups, full patch rollback functionality, and a real-time log system for diagnostics.

## Intelligent Configuration Management

The application implements validation and synchronization mechanisms that:

-   Preserve the correct order of kext loading.
-   Prevent duplicate entries in config.plist.
-   Update existing configurations when necessary.
-   Maintain the structural integrity of your OpenCore/Clover configuration.

## macOS Tahoe Support
> [!IMPORTANT]
On macOS Tahoe, Wi-Fi Patcher Pro automatically applies the following boot arguments to enable Broadcom Wi-Fi patches:
 ```
-amfipassbeta
```
_These parameters are applied exclusively when Tahoe is detected._

## Security & Workflow

Wi-Fi Patcher Pro operates locally. It **does not** collect data, upload files, or send telemetry. User password authorization is requested only to mount the EFI partition and install RootPatches.

## The patching workflow

1.  Mount EFI Partition
2.  Validate EFI folder configuration (Kexts & config.plist)
3.  Mount APFS Volume
4.  Install Frameworks (OCLP RootPatches)
5.  Synchronize Frameworks
6.  Rebuild Kernel Caches & Update Auxiliary KC
7.  Create Snapshot

> [!TIP]
> ## Emergency Recovery: 
> If you encounter a boot loop after patching, boot into **Recovery Mode** and restore the snapshot to the last sealed state using these terminal commands:
```
mount -uw /Volumes/YourDiskName

bless --mount /Volumes/YourDiskName --bootefi --last-sealed-snapshot (Replace "YourDiskName" with the actual name of your drive)
```
## Credits

-   **Acidanthera Team**
-   **OCLP Team**
-   **DhinakG**
-   **EduCovas**
-   **zxystd**

> [!NOTE]  
> **Disclaimer:** This tool is intended for educational and Hackintosh-related purposes only. Compatibility may vary depending on your specific hardware, bootloader version, and macOS version. **Always create a backup of your EFI folder and system configuration before applying any changes.**
