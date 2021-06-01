---
title: Choosing mobile devices
description: Advice on how to choose which smartphones, tablets, laptops or desktop PCs to use in your organization.
published: true
date: 2021-06-01T20:09:55.403Z
tags: bronze, bronze-training, mdm
editor: markdown
dateCreated: 2021-03-06T02:26:13.051Z
---

When choosing laptops, mobile phones and tablets for use by your organization, there will be many competing factors to consider. Price, functionality and portability will all play a part in your decision-making process, and security should too.

This guidance will help you properly assess the security aspects of the devices you are considering. The goal is to ensure you purchase and use devices which are able to provide the level of security your work requires.

## Why choose devices with security in mind?

Nearly all modern mass-market mobile devices are secure enough for nearly all users. So, most organizations won't need to worry about security until a shortlist of devices has been drawn up that meet your other requirements.

Your shortlist will have been decided on the basis of numerous non-security considerations. Which devices are within budget and support the apps you'll be using? Do these meet your users' accessibility requirements? These questions will need to be asked first.

If your users can't work effectively with the devices you give them, they will find other ways to do their jobs. This could mean resorting to insecure alternatives.

## Preparation for device procurement

Once you know that the devices under consideration will fulfilll all the needs of your users, you should apply some thought to the security of the machines, and the systems they run.

We've listed the most important aspects you should consider below. These are grouped by device type, for Android, macOS and Windows. In the most part, iOS and Chrome OS devices do not have specific security considerations to distinguish between them. Linux device considerations, including Ubuntu, are mostly the same as Windows devices.

### **For all types of device**

| **Consideration** | **Explanation** |
| --- | --- |
| **Support duration of devices** | You should ensure that the device will be supported by the manufacturer for the entire time you intend to use it. This way you will receive [security updates and bug fixes](/bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date). Some manufacturers do not publish end-of-life dates for devices. You may be able to look at the historic lifespans of devices from the same manufacturer to estimate how long the current device will be supported. |

### **For Android devices**

Android devices include a wide range of smartphones and tablets from various Original Equipment Manufacturers (OEMs).

| **Consideration** | **Explanation** |
| --- | --- |
| **Android Enterprise Recommended** | The [Android Enterprise Recommended (AER)](https://androidenterprisepartners.withgoogle.com/devices/) program contains devices that have been subjected to more stringent testing and security requirements than non-recommended devices. These additional requirements include minimum software versions, hardware performance, [MDM capabilities](/mobile-device-guidance/choosing-and-using-mobile-device-management-services) and delivery of Android security updates within 90 days of release from Google for a minimum of three years. |
| **Monthly patch updates** | As of Android 10, Google now allows security updates and patches via Google Play rather than requiring each OEM to deploy their own dedicated updates. Google currently schedule security updates [every month for their own devices](https://source.android.com/security/bulletin) and minor version updates as and when they’re ready, with OEMs releasing updates on their own individual schedules. Update files are downloaded with the new .apex file format, which allows updates to be installed without user interaction, or on next power on. |
| **Major release updates** | Some manufacturers commit to releasing one or more future versions of Android on their devices. These manufacturers can be preferred if you want to ensure access to future major releases of the platform. Google have published the guaranteed support dates for Pixel and Nexus devices in [their support pages](https://support.google.com/pixelphone/answer/4457705).  Additional version support is at the discretion of the OEM, however Google have compiled a [linked list for other manufacturers](https://support.google.com/android/answer/3094742) who use Android. |
| **Hardware-backed keystore** | [Hardware-backed keystores](https://source.android.com/security/keystore) significantly strengthen the encryption features of an Android device and should be selected when available. Any device that was released with Android 8.0 or higher pre-installed, or has a fingerprint reader, will have a hardware-backed keystore. |
| **Reputable vendor** | There are many Original Equipment Manufacturers (OEMs) within the Android ecosystem, and each will have its own security reputation. Before choosing an OEM to supply your devices, investigate their security reputation, including how they have handled vulnerabilities in the past and what bundled apps they pre-install on their devices (and what permissions those apps have). |
| **Play Protect Certified** | [Google Play Protect certified](https://www.android.com/intl/en_in/certified/) devices have been tested to ensure they do not contain any pre-installed malware, and come with Google Play Protect, which includes automatic virus scanning. Devices that are not Google Play Protect certified have not been verified by Google, so their security or functionality cannot be confirmed. We recommend you choose devices carrying the Google Play Protect certification. |
| **Additional security features** | Several OEMs also include additional features in their variant of Android. For example, [Knox Platform for Enterprise](https://www.samsungknox.com/en/solutions/it-solutions/knox-platform-for-enterprise) features many security enhancements over the standard build of Android. The latest Google devices contain a [Titan M chip](https://www.blog.google/products/pixel/titan-m-makes-pixel-3-our-most-secure-phone-yet/), which improves the security of the device |

### **For Chrome OS devices**

Chrome OS devices include a wide range of Chromebooks and tablets from various manufacturers.

| **Consideration** | **Explanation** |
| --- | --- |
| **Reputable Vendor** | A device from a reputable vendor, or OEM should be chosen. Google's [Auto Update policy](https://support.google.com/chrome/a/answer/6220366?hl=en) will help you determine which devices may be in support for the longest. |

### **For macOS devices**

macOS devices include MacBook, MacBook Air, MacBook Pro, iMac, and Mac Mini devices.

| **Consideration** | **Explanation** |
| --- | --- |
| **Apple T2 Security Chip** | Most macOS devices sold since early 2019 include the [Apple T2 Security Chip](https://support.apple.com/en-gb/HT208862). This chip significantly improves the physical security of the device. Devices with a T2 chip should be preferred where possible. |

### **For Ubuntu devices**

Ubuntu devices include desktops and laptops, some of which may come pre-installed with Ubuntu or have Ubuntu installed by an Administrator. [Ubuntu certified hardware](https://certification.ubuntu.com/desktop/models?query=&category=Desktop&category=Laptop&level=&release=20.04+LTS) is recommended, as these devices include benefits such as full support for security patches, bug fixes, and Ubuntu features, for the duration of the Ubuntu support cycle.

However, there are some cases in which features of these devices may require further security hardening, as detailed below:

| **Consideration** | **Explanation** |
| --- | --- |
| **External Interfaces** | [DMA is possible from some external interfaces](/bronze-training/mobile-device-guidance/using-peripherals-securely), including FireWire and Thunderbolt. These interfaces can be managed through the Ubuntu settings UI.<br><br>You should consider whether you need hardware with DMA interfaces, as part of the procurement process. If DMA interfaces are required, we recommend disabling the SBP-2 FireWire protocol and configuring a restrictive security level for Thunderbolt version 2 and above. Devices manufactured post-2018 may have Kernel DMA Protection, which goes some way to protect against DMA attacks. |
| **Trusted Platform Module** | A TPM is a separate cryptographic co-processor that provides hardware-backed security features. These significantly improve the physical security of the device, and are required for the use of data at rest encryption in its most secure configuration. Devices that include a TPM 2.0 should be preferred where possible. |

### **For Windows devices**

Windows devices include a wide range of desktop PCs, tablets and laptops that may either come pre-installed with Windows, or have Windows installed by an administrator.

Support for the latest Windows 10 security features should be met by OEMs as part of the [Windows Hardware Compatibility Program](https://docs.microsoft.com/en-us/windows-hardware/design/compatibility/whcp-specifications-policies).

Devices that are *Modern Standby* certified must meet all the requirements for UEFI secure boot and ship with it enabled. They should not have [ports that allow DMA access](/bronze-training/mobile-device-guidance/using-peripherals-securely) and will have TPM 2.0 or later.

In some cases though, certain security features require a combination of specific processor, firmware and hardware features and therefore may not be supported on all devices. We highlight some of these considerations below.

| **Consideration** | **Explanation** |
| --- | --- |
| **UEFI version** | Device firmware should meet the minimum required Unified Extensible Firmware Interface (UEFI) specification 2.3.1c. This is a foundation requirement for many of the security features included in Windows 10, including [Secure Boot, Windows Defender Credential Guard, and Device Guard](https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-uefi). To meet enhanced standards, as set out by [Microsoft for a highly secure Windows 10 device](https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-highly-secure), systems must have firmware that implements UEFI version 2.6 or later. |
| **Hardware and firmware security features** | Virtualization features including both virtual machine extensions and input/output device memory management should be supported. Many of the latest security features of Windows 10, including [Windows Defender Credential Guard](https://docs.microsoft.com/en-us/windows/security/identity-protection/credential-guard/credential-guard) and [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) rely on this hardware support being available.<br><br>The device should be configured to boot in UEFI mode and secure boot should be enabled by default. To provide enhanced platform boot protection, you may wish to consider devices that include hardware-backed cryptographic protection of unauthorized changes to the firmware and alert or even automatically recover from these changes. Examples include [Intel Boot Guard](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/security-technologies-4th-gen-core-retail-paper.pdf) or [HP Sure Start](https://www8.hp.com/uk/en/solutions/computer-security.html).<br><br>The latest versions of Windows 10 can now also support a feature known as [System Guard Secure Launch](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-system-guard/system-guard-secure-launch-and-smm-protection). This provides a verified and measured launch environment of the Windows Hypervisor which protects against the risk to Windows devices from compromised platform firmware as well as additional protections for System Management Mode (SMM) on Intel platforms. This feature has [specific hardware requirements](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-system-guard/system-guard-secure-launch-and-smm-protection) to support the additional protections for SMM on Intel platforms, as well as to provide a dynamic root of trust for verification and measurement e.g. Intel Trusted Execution Technology (TXT). |
| **Trusted Platform Module** | A TPM is a separate cryptographic co-processor that provides hardware-backed security features which significantly improve the physical security of the device, and are required to use BitLocker in its most secure configuration. Devices that include a TPM 2.0 should be preferred where possible. |
| **Firmware patching and support** | Devices should support the [Windows UEFI Firmware Capsule Update](https://docs.microsoft.com/en-us/windows-hardware/drivers/bringup/windows-uefi-firmware-update-platform). This enables Firmware updates to be automated via Windows Update and you should prefer devices that support this. Alternatively, OEMs may provide their own client solutions that include management of firmware updates. You should refer to your OEM to determine if these solutions meet your needs. You should also ensure that the OEM implements signed manufacturer firmware updates by default. This should be checked with the manufacturer as part of your procurement process. |
| **Windows 10 S** | [Windows 10 S](https://support.microsoft.com/en-gb/help/4020089/windows-10-in-s-mode-faq) is a version of Windows 10 designed specifically to increase the security of a Windows 10 device by only allowing apps to be installed from the Microsoft store. This makes code signing mandatory. It also restricts use of default admin user accounts. This is in addition to the existing security features already built in to Windows 10. |
| **Windows Hello for Business** | Windows Hello for Business can make use of biometrics for device unlock. This will require [biometric hardware support](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-biometrics-in-enterprise) on the device that meets the Microsoft requirements for Windows Hello. |
| **Secured-Core PC Range** | [Secured-Core PC's](https://www.microsoft.com/en-us/windowsforbusiness/windows10-secured-core-computers) come equipped with all the latest security features. |

### **BYOD**

If you're permitting [Bring Your Own Device (BYOD)](/bronze-controls/byod-guidance) within your organization, you might not be able to choose your users' devices.

In this case, it's likely not possible to impose any of the above security measures on your users, and your security may suffer as a result.

Read our [Bring Your Own Device (BYOD) guidance](https://www.ncsc.gov.uk/collection/mobile-device-guidance/bring-your-own-device) for further details on this.

## How to buy secure devices

Ultimately, the process for deciding which devices to use is a few short steps.

You should:

-   Assess which operating systems support the software features and apps your users need to use to get their jobs done
-   Decide on device manufacturer(s) that can meet the security requirements for your organization as described above
-   Decide on device types(s) that have the performance and hardware features that your users need, and that come within your budget
-   Pilot devices before deploying them widely to ensure you have covered all aspects of the device selection that are relevant to your organization.
-   Select the device or devices that best meet your business requirements and budget.
-   Develop a strategy for updating your list of approved devices.

## More information

There are many buyer's guides for mobile devices available online. You should also consult with your device supplier(s) for their advice.

In addition, each manufacturer produces a security guide, explaining the security features of their platforms. You can use these guides to determine which particular platforms might meet your security needs:

| **Device type** | **Security guide** |
| --- | --- |
| Android | [https://source.android.com/security](https://source.android.com/security) |
| Chrome OS | [https://www.chromium.org/chromium-os/chromiumos-design-docs/security-overview](https://www.chromium.org/chromium-os/chromiumos-design-docs/security-overview) |
| iOS | [https://www.apple.com/business/docs/iOS\_Security\_Guide.pdf](https://www.apple.com/business/docs/iOS_Security_Guide.pdf) (PDF) |
| macOS | [https://www.apple.com/business/resources/docs/macOS\_Security\_Overview.pdf](https://www.apple.com/business/resources/docs/macOS_Security_Overview.pdf) (PDF) |
| Samsung devices | [https://www.samsungknox.com/en/solutions/it-solutions/knox-platform-for-enterprise](https://www.samsungknox.com/en/solutions/it-solutions/knox-platform-for-enterprise) |
| Windows | [https://www.microsoft.com/en-gb/windows/comprehensive-security](https://www.microsoft.com/en-gb/windows/comprehensive-security) |