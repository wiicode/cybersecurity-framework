---
title: Securing macOS
description: 
published: true
date: 2021-06-02T21:06:09.207Z
tags: bronze, bronze-training, security-operations
editor: markdown
dateCreated: 2021-01-08T05:15:52.652Z
---

# macOS

Secure configuration of macOS devices

macOS is the default operating system on Apple's Mac, iMac, and Macbook devices. Whilst this guide does not apply to any specific version of macOS, it was last tested on macOS 10.15 in November 2019.

## Securing macOS

There are a number of configuration options which you can use to make the platform work within your company. However, we specifically recommend you implement technical and procedural controls relating to the following areas.

### General recommendations

For an enterprise deployment of macOS devices, you should:

-   Decide which macOS devices your company will use:
    -   Devices with a T2 security processor should be preferred, as they provide better full disk encryption, stronger secure boot and better resistance to physical attacks. Secure erase is also much more effective.
    -   macOS devices typically receive software updates for around 6-7 years after first release. Once a device is vintage or obsolete, it no longer receives updates. At this point, you should purchase newer devices.
-   Use one of the recommended network architectures to enable remote access to enterprise services.
-   Use a Mobile Device Management service to configure, monitor and enforce technical controls on your macOS devices. Enable any logging and monitoring features.
-   Use Apple Business Manager (ABM) to enroll and provision devices via zero touch enrollment. Using zero touch enrollment, the MDM can be configured to automatically provision the initial administrator account, and users will create non-administrative accounts during setup assistant.
-   Consider whether you will deploy antivirus or other security software on macOS. A combination of Gatekeeper settings and the built-in Xprotect service is normally sufficient, but in some cases you may want additional protection.

### Device configuration

Once you have chosen your MDM service, architecture and approach to applications, you should then develop a device configuration which you can apply to enforce your technical controls. In particular, you should include policies that manage:

-   The use of biometrics, as well as passcodes and authentication policies. For devices without a [_T2 security processor_](https://support.apple.com/en-gb/HT208862), we recommend you use complex passcodes for user accounts as they directly protect disk encryption keys.
-   Setting a [_firmware password_](https://support.apple.com/en-us/HT204455) to help mitigate a variety of physical attacks, including cold boot and direct memory access (DMA).
-   Configuration of [_FileVault encryption_](https://support.apple.com/en-gb/HT204837) settings to prevent data extraction using physical attacks. Configure escrow of recovery keys so you can reset forgotten passwords.
-   External interface protection, including wired and wireless peripherals (e.g. disabling USB accessories when the device is locked).
-   Automatic operating system and application updates.
-   The built-in IKEv2 virtual private network (VPN) if a VPN is required. However, always-on mode is not supported for any built-in VPNs on macOS.
-   Third-party apps for work use from an enterprise app catalogue, delivered via MDM. Alternatively, you can use tools like [_Munki_](https://github.com/munki/munki) to manage software installation on your devices.
-   Your approach to iCloud accounts on users' devices, enabling or disabling the specific iCloud features that your need.