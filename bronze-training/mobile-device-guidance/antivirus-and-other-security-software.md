---
title: Antivirus and other security software
description: Advice on the selection, configuration and use of antivirus and other security software on smartphones, tablets, laptops and desktop PCs
published: true
date: 2021-06-02T02:25:59.545Z
tags: guidance, bronze, bronze-training, mdm
editor: markdown
dateCreated: 2021-03-06T02:39:26.668Z
---

Antivirus (AV) software are types of software products which attempt to detect, quarantine and/or block malware from running on devices.

AV works in conjunction with network defenses, device configuration and App Store scanning to try and block malware before it can cause harm to you or your organization.

This guidance covers when AV might be beneficial, and gives some tips on how to manage AV products within an organization.


## Why use antivirus?

Getting infected with malware - often ransomware - is one of the most common ways that IT systems can be compromised.

Malware infection can result in theft of intellectual property, ransoming of data, and/or disruption to services provided by your organization. As such, it's important for organizations try and prevent malware from infecting your devices.

Using AV is one way of helping prevent infection, but there are many things to think about. Which product(s) should you use? How should you configure your AV? And how might AV interact with other defenses your organization deploys?


## Preparation for antivirus use

AV products traditionally worked by scanning every file on a device and looking for malware by spotting known signatures. However, advances in malware and changes in underlying platforms have limited the effectiveness of this approach.

Whilst malware is more capable now than in the past, many risks that traditional AV products protected against are now mitigated by default when the correct settings are implemented at the operating system level.

**What to look for in AV**

Given the improvements in the security measures built into operating systems, what do you actually need from AV products?

In particular, you should understand and think about:

**1. If you are confident that** ***your devices cannot execute known malware*** **that might be present,** then AV offers very limited value.

This will be true when:

-   Devices can only run software that is delivered through a public App Store which monitors for malicious code - e.g. the default configuration on most smartphones
-   Devices can only run software that is delivered through an enterprise app catalogue, and you have a process for ensuring known malware is not added to that catalogue.
-   You have software execution policies on your devices that prevent code from non-trusted signers from executing.
-   You enforce policies that prevent users from executing code from writable locations (including [non-application code such as macros](/guidance/macro-security-for-microsoft-office)), and trust all code that is present in read-only locations.

This means you should not need to use AV products on platforms like Chrome OS, Android and iOS in their default configuration.

You can find advice on how to do achieve the same effect on other platforms in our [third-party applications guidance](/bronze-training/mobile-device-guidance/using-third-party-applications), and in the [detailed platform guides](/bronze-training/mobile-device-guidance/platform-guides) for the specific platforms.

**2\. If you decide you need to use AV products on your devices, you need to decide which one(s).**

Windows, macOS and Android include built-in AV products by default and these will meet the needs of many organizations, but you may also wish to look at commercial third parties.

When deciding on which products to use, think about:

-   Is third-party software required in order to protect your devices from malware?
-   How will you keep the AV product up to date, including new signatures?
-   Using third-party AV that is still supported on [obsolete platforms](/bronze-training/mobile-device-guidance/managing-the-risks-from-obsolete-products) might help manage some of the risks.
-   There are a variety of commercial paid and free products available, and some may have additional features you may find useful. Conduct a survey to find out which ones meet your needs.
-   We don't recommend using more than one AV product on any device, the security benefit of doing so is minimal and the products may conflict with each other, potentially causing device stability issues.
-   An infected device within an organization may quickly spread malware through your entire fleet of devices within your network, you should consider methods of [preventing lateral movement](/bronze-controls/preventing-lateral-movement) if they become compromised.

---

## How to choose and use AV

When choosing and configuring an AV or endpoint security application:

-   If you are relying on built-in AV, you should ensure that it is enabled within your device configuration settings.
-   Decide which of your devices need AV products using the considerations above. This will mostly depend on the platforms used within your organization.
-   Choose an AV product - or selection of products - that meets your organization's needs and is compatible with the devices you use.
-   Ensure you [update the AV software](/bronze-training/mobile-device-guidance/antivirus-and-other-security-software) when a new version is released and configure automatic updates where possible.
-   Test the AV product on your devices, and ensure that it does not conflict with existing AV or endpoint security applications.

---

## Platform-specific recommendations

### **Android**

Use an *allow lists* to manage [permitted third-party applications](/bronze-training/mobile-device-guidance/using-third-party-applications) on Android. Disable installation of applications from unknown sources using your MDM.

However, there’s also [Play Protect](https://support.google.com/accounts/answer/2812853?hl=en) which acts much like a traditional AV product and regularly scans apps, reducing the risk of malware being loaded onto the platform from an untrusted source.

Ensure your Android devices are [kept up to date](/bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date) and are supported by the manufacturer so that you have the latest defenses against malware. Security updates in Android 10 will be distributed via Google Play. However, OEM-specific updates will still require independent patches from the manufacturer.

### **iOS**

The risk of becoming infected by malware on iOS is minimal, though we still recommend the use of an *allow list* to manage [permitted third-party applications](/bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date) on iOS.

Apple app review and your own third-party assessment process should combine to prevent malware from infecting your devices.

In addition, as each application runs in a sandbox, AV products are unable to perform meaningful scans, so their use is of very limited value. 

The only other ways to load applications are using Enterprise Developer accounts which should be blocked using MDM policies. The other route is by jailbreaking the device.. 

### **Windows**

Windows 10 includes [Windows Defender Antivirus](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) and [Windows Defender SmartScreen](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview). These attempt to detect malicious code on Windows devices.

Alternatively, third party anti-malware products are available. If using a third-party product, those that implement the [Anti-Malware Scan Interface (AMSI)](https://docs.microsoft.com/en-gb/windows/win32/amsi/antimalware-scan-interface-portal) should be preferred, to improve compatibility with future Feature Updates. Older versions of Windows will benefit from third-party AV products. 

### **macOS**

[XProtect, macOS’s inbuilt security software](https://www.apple.com/macos/security/) is reasonably effective at preventing malware on the platform, but some users may still wish to install a third-party product.

XProtect has a limited signature set, which is maintained by Apple to detect widespread malware. XProtect will also restrict vulnerable plugin versions (such as Java) to limit exposure.

### **Chrome OS**

There is little evidence to suggest that AV is effective or necessary on Chrome OS.

Enterprise administrators can (and should) enforce application control policies based on code signatures, as described in our [detailed platform guidance](/bronze-training/mobile-device-guidance/platform-guides), reducing the risk of malware infection.

Furthermore, Chrome OS only allows you to install software that has been authorized in their store (including Android store), so applications have been through the various checks that are implemented there.

Users who configure their Chrome OS into Developer Mode may still be able to run malicious code, so Developer Mode should be prevented using [mobile device management](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services), unless needed.

### **Linux**

Linux is a highly configurable platform and can be deployed in many ways. As such, there is no best practice for which AV products or configurations to use.>

Linux is often used for servers and services, so the need for AV and security software is of limited value here since servers should only run the software they have been configured to run. On general-purpose devices, Linux can be hardened to prevent arbitrary applications from running (see the detailed platform guidance), meaning the risk from malware is very low. AV can be used to augment this protection, or as a mitigation by itself if required.