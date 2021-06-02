---
title: Keeping devices and software up to date
description: Advice for individuals and organisations on keeping software on smartphones, tablets, laptops and desktop PCs up to date.
published: true
date: 2021-06-02T14:29:51.810Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:46:26.042Z
---

Modern mobile devices run a huge amount of software. This includes operating systems such as Android and iOS and the applications we install to do just about everything, from word processing, to photo retouching and sound recording.

To prevent known vulnerabilities from being exploited, all of this software must be kept up to date. This means installing patches released by the software developers to close security holes found in their products. Hence the name 'patching'.

This guidance will help you understand the security risks posed by out of date devices, and advise you on how best to secure devices against the latest cyber security threats.

---

## Why keep your devices up to date?

Device manufacturers and app developers will usually release software updates regularly until they decide their product is unsupported. These updates will often contain new features, fixes for bugs and performance improvements.

They will often also contain **security patches** and **new security features**, both of which it's important to install**.** 

Patches matter because they fix known flaws in products that attackers can use to compromise your devices. New security features make it harder for attackers to successfully compromise your devices.

Attackers who succeed in compromising your devices could potentially steal data, encrypt your files or prevent your device from working at all.

Many devices and apps can install updates automatically, but sometimes they'll need a bit of help from the device user, so you'll need to keep an eye on updates in case they stop working.

---

## Preparation for installing updates

There are a number of things which everyone should keep in mind when updating their devices. There are some [additional considerations](https://www.ncsc.gov.uk/collection/mobile-device-guidance/keeping-devices-and-software-up-to-date#orgs1) for Organisations.

### **What to keep up to date**

You should make sure you have ways of keeping each of the following important types of software up to date:

-   **Operating System (OS):** Most operating systems support automatic updates but will need the feature to be enabled. It's normally enabled by default, but could have been turned off.
-   [**Web browser and extensions**](https://www.ncsc.gov.uk/collection/mobile-device-guidance/managing-web-browser-security)**:** Web browsers are particularly vulnerable, as they are very complex pieces of software and the sites you visit could potentially exploit flaws in them.
-   [**Third-party apps**](https://www.ncsc.gov.uk/collection/mobile-device-guidance/using-third-party-applications) **- especially office apps:** Apps you install yourself will need to be kept up to date. Some apps will update themselves, some will update through your device's app store, but some might need you to install updates yourself.
-   **Anti-virus:** If you use [anti-virus or endpoint security apps](https://www.ncsc.gov.uk/collection/mobile-device-guidance/antivirus-and-other-security-software), you'll want to ensure that these are updated regularly. Like other software, anti-virus updates include bug fixes and new features, but also include new *signatures* which can be used to detect new malware that's recently been detected by the AV companies.

### **Device support**

Devices, operating systems and apps are generally supported for a limited time before they are considered obsolete and no longer updated.

It can be difficult to find out exactly when a product will go out of support. Nonetheless, for each device you use, you should try to ensure that all [the important software on those devices](https://www.ncsc.gov.uk/collection/mobile-device-guidance/keeping-devices-and-software-up-to-date#important), is still supported by the developer or manufacturer. You should replace unsupported software and devices as soon as you are able.

### **Automatic updates**

Most devices will now have *automatic updates* turned on by default, however things can go wrong with automatic updates, for example:

-   Users might have disabled the automatic update option on their device.
-   Automatic updates might only occur if the device is connected to Wi-Fi, connected to power, powered on at a specific time of day, has sufficient storage, and/or isn't too far out of date.
-   Some updates might require the device to be manually restarted. If a device hasn't been restarted in a while then the update might not be installed.

### **Back up and testing**

-   It is always a good idea to have backups of your data, and [before you update](https://www.ncsc.gov.uk/blog-post/offline-backups-in-an-online-world) is an ideal time to do this
-   If you have a large number of devices, you might want to test updates on a small number of them before updating all of your devices to make sure the apps you use continue to work after the updates. If you do this, don't take too long testing as once the updates become available to install, attackers can work out what the original flaws were that have been patched in the update and start attacking devices that haven't had the updates installed. See our blog post on [installing software updates without breaking things](https://www.ncsc.gov.uk/blog-post/ncsc-it-installing-software-updates-without-breaking-things) for more information on testing pre-release software, to ensure your apps continue to work. 

## Additional considerations for organisations

Users can often defer or decline updates - you might want to look into how you can [check compliance using Mobile Device Management (MDM)](https://www.ncsc.gov.uk/collection/mobile-device-guidance/choosing-and-using-mobile-device-management-services).

-   If your organisation permits [Bring Your Own Device](https://www.ncsc.gov.uk/collection/mobile-device-guidance/bring-your-own-device), you may not be able to force users to update their software - either because you don't have permission, or because their device is no longer supported. If this is the case, you might want to consider taking steps to restrict access to enterprise resources from out of date devices.
-   It's increasingly important to manage firmware updates. You should consider how your organisation will deploy and [manage updates to firmware.](https://www.ncsc.gov.uk/collection/mobile-device-guidance/managing-mobile-device-firmware)
-   Some enterprise networks might block update servers. Network administrators should make sure that devices on their networks can reach update servers.
-   When designing a device configuration, you should make sure that you don't lock down permissions to the point where apps can't be updated. Make sure you do thorough testing of a new configuration to ensure that updates work reliably.
-   Many MDMs allow you to create an Enterprise application catalogue. These often include the ability to automatically update apps deployed through the catalogue.

---

## How to keep your devices up to date

-   Ensure that automatic updates are enabled for all software on your devices, where possible. Take special care around the operating system, [web browser](https://www.ncsc.gov.uk/collection/mobile-device-guidance/managing-web-browser-security), any office apps or document readers, and [anti-virus products](https://www.ncsc.gov.uk/collection/mobile-device-guidance/antivirus-and-other-security-software) (if you're using one).
-   Some updates might require that your device is connected to Wi-Fi or power, has sufficient storage, or is rebooted. If this is the case, make sure you follow any instructions your device gives you.
-   Install updates promptly when notified - ideally within a few days.
-   Check occasionally that your device is keeping itself up to date, as automatic updates can sometimes break (e.g. if you have low storage on your device).
-   Configure automatic backups or back up your data regularly so that you can update your device with confidence.
-   When [choosing which new device(s)](https://www.ncsc.gov.uk/collection/mobile-device-guidance/choosing-devices), consider how long the manufacturer typically supports its products. This ensures you'll receive updates for a longer period of time.

## Additional Recommendations for organisations

-   Enforce the use of automatic updates through your organisation's [Mobile Device Management](https://www.ncsc.gov.uk/collection/mobile-device-guidance/choosing-and-using-mobile-device-management-services) service.
-   Monitor the status of device and software updates using MDM logs or compliance policies. If you adopt a [BYOD approach](https://www.ncsc.gov.uk/collection/mobile-device-guidance/bring-your-own-device), restrict access to corporate data for devices that are not kept up to date.
-   [Include advice in your User Guidance](https://www.ncsc.gov.uk/collection/mobile-device-guidance/advising-end-users) about how users can ensure that software updates are installed.
-   If you are a large organisation, deploy a staged approach to update management so that nothing breaks when your devices update. For an example of how the NCSC has achieved this, you can read our blog on [updating without breaking things](https://www.ncsc.gov.uk/blog-post/ncsc-it-installing-software-updates-without-breaking-things).
-   In addition to OS and application updates, ensure that processes are also in place to [automate firmware updates](https://www.ncsc.gov.uk/collection/mobile-device-guidance/managing-mobile-device-firmware).

---

## More information

Information on keeping software up to date for individual platforms can be found on the various manufacturer websites:

| **Platform** | **Updates guidance** |
| --- | --- |
| Android | [Check and update your Android version](https://support.google.com/android/answer/7680439?hl=en-GB) |
| Chrome OS | [Update your Chromebook's operating system](https://support.google.com/chromebook/answer/177889?hl=en-GB) |
| iOS, macOS | [Update your iPhone, iPad, or iPod touch](https://support.apple.com/en-gb/HT204204) |
| Samsung | [How do I check for Operating System updates on my Samsung Galaxy device?](https://www.samsung.com/uk/support/mobile-devices/how-do-i-check-for-operating-system-updates-on-my-samsung-galaxy-device/) |
| Windows | [Update Windows 10](https://support.microsoft.com/en-gb/help/4027667/windows-10-update) |

For organisations, you can also check for information on monitoring and patching devices that may be available from your [Mobile Device Management](https://www.ncsc.gov.uk/collection/mobile-device-guidance/choosing-and-using-mobile-device-management-services) service provider.