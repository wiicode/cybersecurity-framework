---
title: Using built-in cloud services
description: Secure use of built-in cloud services on smartphones, tablets, laptops and desktop PCs.
published: true
date: 2021-06-01T20:49:47.161Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:41:28.193Z
---

Most modern devices and browsers are able to sync user data and settings across devices, using *built-in cloud services.* [Microsoft](https://account.microsoft.com/account?lang=en-us), [Apple](https://www.apple.com/uk/icloud/), and [Google](https://myaccount.google.com/intro) all offer the ability to sync data in this way.

This guidance will help anyone who uses a mobile device to evaluate the benefits of these services and features, as well as the security risks they can pose.

For organisations, we discuss the additional security controls required to prevent data leaking through these services, to the outside world.

---

## Why secure built-in cloud services?

Built-in cloud services typically allow for the syncing of user data and settings across devices, with access also provided through an online interface. They also provide some remote device management features, including remote locking or remote wipe if a device is lost or stolen.

For individuals, built-in cloud services can provide security benefits. For example, browsers such as [Edge](https://support.microsoft.com/en-gb/help/4028534/microsoft-edge-save-or-forget-passwords), [Chrome](https://support.google.com/chrome/answer/95606?co=GENIE.Platform%3DDesktop&hl=en-GB), and [Safari](https://support.apple.com/en-gb/guide/safari/sfri40599/mac) include built-in [password managers](https://www.ncsc.gov.uk/blog-post/what-does-ncsc-think-password-managers) which are usable 'out of the box.' In combination with cloud services, these allow syncing of passwords across devices to help individuals cope with the challenge of account password management. Additionally, if a device is lost or stolen, the ability for the device owner to remotely lock it or wipe it can provide protection against unauthorised access to the device and its data.

Organisations will likely want to restrict or control the use of these services, to prevent corporate data being synced to personal accounts. For organisations that own and issue mobile devices, applying technical controls using [Mobile Device Management](https://www.ncsc.gov.uk/collection/mobile-device-guidance/choosing-and-using-mobile-device-management-services) can restrict or prevent the use of built-in cloud services.

If using a [Bring Your Own Device (BYOD)](https://www.ncsc.gov.uk/collection/mobile-device-guidance/bring-your-own-device) strategy for mobile devices, restricting access to these services is more complex. In these scenarios, it is highly likely that access to both work and personal accounts and data will be available on the same device. This presents a greater challenge for organisations to maintain separation between work and personal profiles, accounts, apps and data.

---

## Preparation for secure use of built-in cloud services

When using built-in cloud services on mobile devices, many of the considerations listed below will be equally relevant to individuals and organisations. However, your choices may well differ.

For organisations, there are important additional considerations. Your choices here will depend on business need, isolation and separation of data, and the ownership model of the device.

We have listed questions below that will help you assess whether or not to allow the use of built-in cloud services.

## For individuals

-   What cloud services are built into the device?
-   How do I setup and configure cloud-based services and accounts?
-   What data synchronisation and back up services are available?
-   What device settings are available to configure built-in cloud services?
-   Where and how can the data be accessed?
-   How can I protect against unauthorised access to back-ups of my data, stored in the cloud?
-   How can I protect access to data stored on my device if it is lost or stolen?

## For organisations:

-   Do users need access to built-in cloud services on mobile devices?
-   What cloud services are built into devices used within your organisation?
-   What additional features on devices might become enabled as a result of signing into a built-in cloud service (e.g. find my device). What risks arise as a result?
-   What device settings are available to configure built-in cloud services?
-   What device settings are available for isolating work and personal data to prevent data leaking outside of the organisation?
-   What device settings for built-in cloud services and data isolation policies can be controlled and enforced using [mobile device management](https://www.ncsc.gov.uk/collection/mobile-device-guidance/choosing-and-using-mobile-device-management-services)?
-   If deploying devices using a BYOD strategy, it is likely that both personal data and enterprise data will be stored on the same device, with users requiring access to built-in cloud services for personal use. This presents a particularly complex challenge. Further guidance can be found on our [Bring Your Own Device](https://www.ncsc.gov.uk/collection/mobile-device-guidance/bring-your-own-device) page.

---

## How to use built-in cloud services securely

### **For individuals:**

-   Choose which services to enable or disable on the device for cloud backup and syncing.
-   Setup and enable multi-factor authentication for the account you use to log in to built-in cloud services and enrol new devices. More information on multi-factor authentication can be found in the [NCSC multi-factor authentication guidance](https://www.ncsc.gov.uk/guidance/multi-factor-authentication-online-services).
-   Built-in password managers will usually support syncing of passwords across trusted devices, making it easier for you to use passwords securely. For more information on password managers, see this [NCSC blog post](https://www.ncsc.gov.uk/blog-post/what-does-ncsc-think-password-managers) on why we see them as a good thing.
-   Enable remote management features which allow you to remotely lock and wipe your devices if they are lost or stolen.

### **For organisations:**

-   Determine organisational policy for use of built-in cloud services on mobile devices.
-   If deploying enterprise owned and managed devices, where possible, use Mobile Device Management to disable built-in cloud services using personal accounts. This will reduce the risk of data leaking out of the enterprise.
-   Some manufacturers allow enterprises to create accounts that can be managed by the owning organisation. For example, [Apple Managed ID](https://eud.psrlab.co.uk/link-link) and [Google Managed Accounts](https://eud.psrlab.co.uk/link-link) can be used to help manage the risk more effectively.
-   If employees are required to have access to both personal and work data on the same device, where possible apply technical controls to provide separation of work and personal profiles, preferably using [mobile device management](https://www.ncsc.gov.uk/collection/mobile-device-guidance/choosing-and-using-mobile-device-management-services) to control, monitor and enforce this separation.

---

## More information

#### **For individuals**

We have provided links below to details on built-in services for the most popular mobile devices used today, including **Windows 10**, **iOS**, **macOS**, **Android**, and **Chromebook.**

| **Provider** | **Account** | **Syncing Settings** | **Syncing Passwords** | **Remote Management** | **Protecting Your Account** | **Apps** |
| --- | --- | --- | --- | --- | --- | --- |
| **Microsoft** | [Microsoft Account](https://account.microsoft.com/account?lang=en-us) | [Sync settings on Windows 10](https://support.microsoft.com/en-gb/help/4026102/windows-10-about-sync-settings) | [Sync settings on Windows 10](https://support.microsoft.com/en-gb/help/4026102/windows-10-about-sync-settings) | [Find and lock a lost Windows device](https://support.microsoft.com/en-gb/help/11579/microsoft-account-find-and-lock-lost-windows-device) | [Turning two-step verification on or off for your Microsoft account](https://support.microsoft.com/en-gb/help/4028586/microsoft-account-turning-two-step-verification-on-or-off) | [Microsoft Apps](https://account.microsoft.com/account?lang=en-us) |
| **Google** | [Google Account](https://myaccount.google.com/intro) | [Google Chrome – Sync account data and settings across devices](https://support.google.com/chromebook/answer/165139?hl=en-GB&ref_topic=2586064) | [Google Chrome - Sync passwords across devices](https://support.google.com/accounts/answer/6197437?co=GENIE.Platform%3DDesktop&hl=en) | [Google – Find, lock, or erase your lost phone or computer](https://support.google.com/chrome/answer/7177579?hl=en-GB) | [Google Account – Turn on 2-step verification](https://support.google.com/accounts/answer/185839?co=GENIE.Platform%3DDesktop&hl=en) | [Google Apps](https://get.google.com/apptips/apps/#!/all) |
| **Apple** | [Apple ID](https://support.apple.com/en-gb/HT203993) | [Configure your iCloud feature settings](https://support.apple.com/en-gb/HT207689) | [Setup Apple iCloud Keychain](https://support.apple.com/en-gb/HT204085) | [Apple Find my iPhone - Track and find your missing Apple device](https://support.apple.com/en-gb/explore/find-my-iphone-ipad-mac-watch) | [Two-factor verification for your Apple ID](https://support.apple.com/en-gb/HT204915) | [Apple iCloud](https://www.apple.com/uk/icloud/) |

#### **For organisations**

The [NCSC Cloud Security Guidance](https://www.ncsc.gov.uk/collection/cloud-security) provides detailed guidance for organisations on assessing the security of cloud services. This may help with assessing whether you permit use of built-in cloud services.

In scenarios where devices are enterprise owned and fully managed, the [NCSC detailed platform guidance](https://www.ncsc.gov.uk/collection/mobile-device-guidance/platform-guides) provides recommended settings for disabling access to built-in cloud services, if they are not required.

In scenarios where devices require access to work *and* personal data, it will be likely that users, at least for personal accounts, will require access to use built-in cloud services. Most device manufacturers provide mechanisms for isolating work and personal data which can be managed with MDM.

We have provided some links below for detail on the controls offered by **Windows 10**, **iOS**, and **Android**. 

It's important to note that, if malware is present on the device, these technical controls can be circumvented. More extensive information can be found in the [bring your own device](https://www.ncsc.gov.uk/collection/mobile-device-guidance/bring-your-own-device/collection/mobile-device-guidance/bring-your-own-device) guidance.

| **Platform** | **Feature** |
| --- | --- |
| **Windows 10** | [Windows Information Protection](https://docs.microsoft.com/en-us/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) |
| **iOS** | [Managing Devices and Corporate Data on iOS](https://www.apple.com/business/docs/resources/Managing_Devices_and_Corporate_Data_on_iOS.pdf)  <br>[Managed Apps](https://help.apple.com/deployment/ios/#/iorf4d72eded) |
| **Android** | [Android Enterprise](https://developers.google.com/android/work/overview)  <br>[Android Work Profile](https://support.google.com/work/android/answer/6191949?hl=en) |