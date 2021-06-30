---
title: Using peripherals securely
description: Advice for IT system administrators on the secure management of peripherals for smartphones, tablets, laptops and desktop PCs
published: true
date: 2021-06-02T02:41:06.879Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:42:19.832Z
---

Most modern mobile devices allow you to connect peripheral devices such as external hard drives, printers and cameras. This is achieved through short range wireless connections like [Bluetooth](https://en.wikipedia.org/wiki/Bluetooth) as well as physical interfaces such as [USB](https://en.wikipedia.org/wiki/USB) and [Thunderbolt](https://www.intel.com/content/www/us/en/products/docs/io/thunderbolt/thunderbolt-technology-general.html).

These interfaces have many benefits. But, they also provide an additional route through which attackers can reach your device and the data it holds.

This guidance will help you plan for the security implications of peripherals, balancing their required use against the additional risks they can introduce to mobile device security.

---

## Why manage peripheral use?

Risks related to peripherals and their interfaces include [direct memory access attacks (DMA)](https://blogs.technet.microsoft.com/motiba/2017/05/24/locking-up-your-bitlocker/), [debugging attacks](https://eclypsium.com/2018/07/23/evil-maid-firmware-attacks-using-usb-debug/) or alternative boot paths that can result in the [loading of malicious code from peripheral devices](https://trmm.net/Thunderstrike), as well as data transfer over wireless protocols that may lack confidentiality and integrity protection.

Access and use of these interfaces should, therefore, be carefully considered. Organizations should assess the benefits against the risk of allowing users to connect devices over external interfaces.

It is important that organizations educate users on the security risks from connecting peripheral devices *and* apply technical controls to restrict or disable access from peripheral devices if not required.

---

## Preparation for peripheral management

The risks from peripheral devices and external interfaces come in a variety of forms. We have broadly classified these risks based on external interface type in the table below.

Your organization will need to consider these risks carefully when determining whether to permit use of peripheral devices or external interfaces. This will require a careful balance of user requirement vs. security risk, alongside any mitigations available on the mobile device.

**Table 1: Interfaces and associated risks**

| **External Interface** | **Risk** |
| --- | --- |
| Removable media (including USB & SDcard) | Removeable media including USB drives and SD cards can provide a convenient means of backing up or sharing data between devices. Allowing removable media access also opens up risks of data theft or data loss. Data stored on removeable devices may not necessarily be encrypted or protected by any form of device authentication, and therefore if lost, could result in data loss, with no way of restricting access to that data or wiping it from the device. It also offers an additional path from which malicious software could be installed, outside of approved software installation processes. |
| Other USB | Beyond removeable media, USB devices can provide additional capabilities that could be abused for malicious purposes. A good example of this is the [USB Rubber Ducky](https://github.com/hak5darren/USB-Rubber-Ducky/wiki). This tool masquerades as a USB keyboard, allowing its user to execute malicious commands on the device it is connected to. This could present additional risk of device exploitation or data loss. |
| DMA-capable interfaces, such as<br><br>Thunderbolt and Firewire | Certain ports support a feature known as direct memory access (DMA). This feature allows devices to access main memory outside of the control of the CPU, allowing faster data rates. DMA can be abused though. For example, a rogue DMA device could be used to scan physical memory to extract cryptographic keys and passwords or install or run malicious software through memory modification attacks.<br><br>External PCI devices can include external boot modules, often referred to as 'option ROMs', that can be executed by system firmware. This functionality is designed to provide additional support for hardware devices, but it can be abused to execute malicious code during boot. This could subvert the secure boot process, modify system code or data, or allow for installation of persistent malware, outside the visibility of the operating system. |
| Wireless - Bluetooth/other proprietary | Wireless interfaces such as Bluetooth can provide a very simple and convenient means of pairing of devices for data sharing. They can also permit attackers unauthenticated access to devices, potentially resulting in data loss or execution of malicious code.<br><br>Pairing of untrusted or unmanaged peripherals could result in the extraction of data outside of your control. Short range wireless protocols may also not support strong encryption and many devices will still accept older versions of wireless protocols, if requested by a peripheral. This could lead to data loss, for example, through interception of a wireless keyboard’s keystrokes. |
| Syncing interfaces | Most modern mobile devices including iOS and Android provide features for syncing of device data to external devices. For example, a  laptop backing up data via external interfaces, such as USB. For organizations, there's a risk that devices will be transferring data to external devices that they do not control. |
| Debugging interfaces | Debugging is the process by which computer programs can be examined and profiled for the means of analyzing their functionality, often for the purpose of ensuring their correct functionality. Techniques can be interactive, allowing direct access to main memory and critical system structures. Debugging is not exclusive to software alone, and many devices can also allow for debugging of hardware devices through external interfaces, although the ability to perform debugging using these interfaces should be closed after manufacturing.   <br>  <br>Abuse of this functionality can lead to data loss, memory modification, or the installation and execution of malicious code. At the hardware level, proof of concept examples exist that show cases where hardware protections have not been correctly configured to prevent debugging after manufacturing and therefore provide the ability to re-write system firmware, opening up the ability to install persistent malware that operates outside of the visibility of the operating system. |
| Bootable interfaces | Certain interfaces, such as USB and Thunderbolt can provide support for alternate boot paths and boot devices. Booting operating systems from external devices could allow for unauthenticated access to device data and data theft. |

---

## How to manage peripherals

In deciding whether or not to allow use of peripheral devices, you should follow a risk assessment process which balances business need against security risk.

You should:

-   Assess the business requirement for use of each type of external interface.
-   Assess the security risks posed by access to external interfaces from peripheral devicesbalanced against the mitigations that are available on the device.
-   Determine technical controls available on the mobile device to restrict access to external interfaces.
-   Set a security policy for connection of peripheral devices, balancing user needs with technical risk.
-   Where possible, use mobile device management to manage access to peripheral devices and external interfaces. Or, consider using third-party software that provide additional management options for external interfaces.
-   Provide guidance to users within the organization on the use of peripherals, security risks, and the associated security policy.

Depending on the device, operating system and remote management capabilities, we would recommend applying the following technical controls where available:

-   If access to external physical interfaces is not required, then disable access to these interfaces.
-   For short range wireless interfaces such as Bluetooth, if not required then disable them. Otherwise, don't allow pairing to new peripherals, or only managed peripherals.
-   For mobile devices, which have external interfaces that support DMA, installation of new DMA devices should be prevented when the device is locked.
-   Device interfaces that can provide alternate boot paths or debugging capabilities should also have these features disabled if not required.
-   Access to change required device settings should be restricted to admin users only. This includes operating system and firmware settings.
-   External interface adapters, such as USB data blockers, can also be purchased for different physical connections that can block data transfer, while still allowing for limited functionality such as charging support.

It should be noted that some of these technical controls may have to be managed and configured through the [device firmware settings](/bronze-training/mobile-device-guidance/managing-mobile-device-firmware), as well as through the operating system.

Where technical controls are not available, procedural controls must be used instead, possibly supported by logging and auditing.

Specific technical controls will vary between types of devices and not all devices will provide technical controls that can mitigate all risks. We've listed some of these aspects below, and grouped them by device type for **Android**, **iOS**, **macOS** and **Windows 10** devices.

**Table 2: Technical controls available by operating system**

| **Operating System** | **Technical controls** |
| --- | --- |
| **Android** | [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) can be used to disable USB debugging and [Developer Options](https://developer.android.com/studio/debug/dev-options.html).   <br>  <br>Addtional [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) settings can be used in [work-managed mode](https://developers.google.com/android/work/requirements/fully-managed-device) to disallow USB file-transfer and mounting of physical media, such as SD cards. MDM can also prevent users from configuring Wi-Fi and Bluetooth. |
| **iOS** | Administrators can use [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) settings on [supervised devices](https://support.apple.com/en-gb/HT202837) to control [connection of external devices](https://support.apple.com/en-gb/guide/mdm/mdmc622d929c/1/web/1), as well as restrict pairing to other hosts.   <br>  <br>[Apple AirDrop](https://support.apple.com/en-gb/HT204144) can also be disabled, and modification of Bluetooth settings restricted. |
| **macOS** | USB and other removable media can be blocked through [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) if required.   <br>  <br>Most macOS devices have external interfaces which permit [Direct Memory Access (DMA)](https://en.wikipedia.org/wiki/Direct_memory_access) from connected peripherals. An [EFI password](https://www.apple.com/business/resources/docs/macOS_Security_Overview.pdf) should be set, as this prevents DMA when the device is locked.   <br>  <br>Devices with a [T2 chip](https://www.apple.com/mac/docs/Apple_T2_Security_Chip_Overview.pdf) include additional configuration options that can be set to restrict booting from external devices. |
| **Chrome OS** | [Bluetooth can be disabled](https://support.google.com/chrome/a/answer/1375678?ref_topic=9028500) using [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) policy settings.<br><br>[External storage devices, including USB flash drives, external hard drives and SD cards can be disabled](https://support.google.com/chrome/a/answer/2657289?ref_topic=9028500) or made read-only using [MDM](/collection/mobile-device-guidance/choosing-and-using-mobile-device-management-services) policy settings. <br><br>[MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) device policies can be used to prevent users enabling *developer mode* by [forcing re-enrollment](https://support.google.com/chrome/a/answer/1375678?ref_topic=9028500) of devices. This also ensures that devices use verified boot mode, which disables support for booting from USB by default. |
| **Linux** | It may be possible to disable Bluetooth and access to external ports such as USB through the settings UI or through the operating system configuration files. It may also be possible to disable some interfaces through [device firmware settings](/bronze-training/mobile-device-guidance/managing-mobile-device-firmware) .<br><br>Many devices that run Linux will have external interfaces that support [Direct Memory Access (DMA)](https://en.wikipedia.org/wiki/Direct_memory_access) including FireWire and Thunderbolt. Depending on the Linux distribution, it may be possible to restrict access to these interfaces through the settings UI or operating system configuration files. [UEFI firmware settings](/bronze-training/mobile-device-guidance/managing-mobile-device-firmware) can also be used to set a minimum [Thunderbolt security level](https://www.kernel.org/doc/html/v4.15/admin-guide/thunderbolt.html) to require authorisation when new Thunderbolt devices are connected. <br><br>Beyond DMA protections, additional settings, including USB boot support, may be required to be disabled through [device firmware settings](/bronze-training/mobile-device-guidance/managing-mobile-device-firmware).<br><br>Additional third-party management solutions may also be available that can enhance management of security of external devices. |
| **Windows 10** | Device connectivity restrictions for Bluetooth can be configured through [MDM policy settings](https://docs.microsoft.com/en-gb/windows/client-management/mdm/policy-csp-connectivity).   <br>  <br>Access to removable storage devices can be prevented or restricted using device installation settings, via group policy or [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services).  <br>  <br>Many Windows devices will have external interfaces that support [Direct Memory Access (DMA)](https://en.wikipedia.org/wiki/Direct_memory_access).<br><br>A range of options are available to [protect against DMA attacks](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-control/control-usb-devices-using-intune#protect-against-direct-memory-access-dma-attacks): <br><br>-   Depending on hardware and firmware, the latest versions of Windows 10 support [Kernel DMA protection](https://docs.microsoft.com/en-us/windows/security/information-protection/kernel-dma-protection-for-thunderbolt), which provides built-in protection against Thunderbolt DMA attacks.<br>-   System settings can also be applied to [disable new DMA devices when the device is locked](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings#disable-new-dma-devices-when-this-computer-is-locked).<br>-   UEFI firmware settings should also be configured to require a minimum [Thunderbolt security level](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-countermeasures) of user authorisation if [Kernel DMA protection](https://docs.microsoft.com/en-us/windows/security/information-protection/kernel-dma-protection-for-thunderbolt) is not supported.<br>-   For completely disabling DMA devices, [installation can be prevented](https://support.microsoft.com/en-gb/help/2516445/blocking-the-sbp-2-driver-and-thunderbolt-controllers-to-reduce-1394-d) by [device id](https://docs.microsoft.com/en-gb/windows-hardware/drivers/install/device-identification-strings) or [device setup class](https://docs.microsoft.com/en-us/windows-hardware/drivers/install/overview-of-device-setup-classes) using [MDM policy settings](https://docs.microsoft.com/en-gb/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) or [group policy](https://docs.microsoft.com/en-us/previous-versions/dotnet/articles/bb530324(v=msdn.10)).<br><br>Beyond DMA protections, additional settings, including pre-boot support and debugging may be required to be disabled through [device firmware settings](/bronze-training/mobile-device-guidance/managing-mobile-device-firmware).  <br>  <br>Additional third-party enterprise management solutions are also available which have the ability to enhance the management of external devices. 