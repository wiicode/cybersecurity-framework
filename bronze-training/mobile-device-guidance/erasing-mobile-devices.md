---
title: Erasing mobile devices
description: Advice for IT admins and individuals on the secure removal of data or malware from smartphones, tablets, laptops and desktop PCs
published: true
date: 2021-06-02T14:33:01.053Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:45:31.040Z
---

> Very often an organization falsely believes they can wipe a device in the event of an **employee termination** using a **remote wipe command**.  While remote wipe technology may be available for some/all mobile devices, it is unlikely you can use this feature during an employee departure.  As you will learn from this guide, remote wipe is intended to be used for lost/stolen or compromised devices.  We strongly recommend that, for cases where a data-wipe is required, your company maintain procedures and request that company applications and accounts are removed in the presence of a manager/owner during termination.  
{.is-warning}

For more information on this topic, please see “[Employee is being fired: an explanation for why wiping a device is likely not an option](https://www.techbento.com/2021/03/07/employee-fired-wipe-device/).”

Our devices contain more work, personal, and financial data than ever before. So it's essential we can remove all this data if we suspect they've been lost, stolen or hacked, (or if we simply want to re-issue them to another user). 

However, because of the way data storage on devices works, simply deleting files is often not enough to prevent this data from being recovered. Similarly, if the device has been infected with malware, running an [antivirus scan](/bronze-training/mobile-device-guidance/antivirus-and-other-security-software) or deleting the app causing the infection might not be enough to completely remove the infection.

---

## Why use secure erase?

You may need to wipe your device if you:

-   are **selling** it (or giving it to a family member or friend)
-   think you've **lost** it (or it's been **stolen**) and you want to erase it remotely.
-   suspect it has viruses or malware and you need to **disinfect** it
-   are **returning** it to the manufacturer (for repair or replacement)
-   are **re-purposing** it so another member of staff can use it
-   are **preparing** a device you've recently acquired so that you know it's in a good state before you start using it

**Note:** *The methods described here will prevent almost everyone from recovering data. However, these methods do not **guarantee** complete removal; a determined expert, using specialist techniques, may be able to recover some of it in some circumstances. If you want to completely erase a device so there is no chance of data being recovered, or your organization's policy requires it, please refer to our guidance on* [*Secure sanitization of storage media*](/guidance/secure-sanitization-storage-media)*. Note that some of the methods described there are destructive, so you may not be able to use the device afterwards.*

---

## Preparation for secure erasure

Before you start the process of erasing data, there are a number of things you need to consider.

**Back up your important data**

The most convenient way of securely erasing mobile devices is to use the built in *Restore*, *Factory Reset*, or *Erase all content and settings* feature of your device. The exact name of the feature depends on which type of device you have. However, these features will erase all content from your device - including messages, contacts and photographs - so you'll want to make sure you have a [backup of all your important data](/bronze-training/background-advanced/10-steps-risk-data-security) first.

**If things go wrong**

In nearly all cases, this kind of factory reset is all you'll need to do. However, if something goes wrong (such as the device failing to start up correctly afterwards) then this might not be an option. In those cases, you might need to re-install the operating system on your devices. This is an advanced task and should only be tried if you know what you are doing. We've included links to some guides online at the end of this article.

**Remotely erasing lost devices**

If you've lost your device or it has been stolen, then there may be options to *remotely* erase your device. This is typically part of your [device's cloud services](/bronze-training/mobile-device-guidance/using-built-in-cloud-services), or part of your organization's [mobile device management](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) services, so might not be available to you if you've not used either of these.

**Selling used devices**

If you are planning on selling your device, you may also need to disable [activation lock (iOS)](https://support.apple.com/en-gb/HT201441) or [factory reset protection (Android)](https://support.google.com/nexus/answer/6172890?hl=en-GB) so that the recipient is able to use the device.

---

## How to securely erase mobile devices

Back-up data, passwords and credentials

If you want to securely erase your device, firstly you'll need to [make backups of all the important data](/bronze-training/background-advanced/10-steps-risk-data-security) on the device. Much of this data may already be stored in [online cloud services](/bronze-training/mobile-device-guidance/using-built-in-cloud-services) or your organization's servers, so this might not be a difficult task. However, you'll want to make sure that you have the passwords and other credentials for these services available so that you're able to log in after the device has been erased.

**Choose from secure, remote and advanced options**

If the device or devices have been enrollled into your organization's [mobile device management (MDM)](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services), you can send the device a *remote wipe* command. This will cause the device to securely erase itself – if it’s turned on and has a data connection.

If you've previously signed into a [built-in cloud account](/bronze-training/mobile-device-guidance/using-built-in-cloud-services) on the device, then you can log back into that account from another computer to also send a *remote wipe* command.

Without MDM or cloud accounts, you will need physical access to the device. The table below has details on the approaches you can use in either case. There are also links to the guides on the exact process, for each major Operating System (OS). Typically, erasure takes a few minutes, though on older devices it can take an hour or so.

If you are selling, giving away, or trading in your device then you should follow the *Recommended secure wipe* for your particular device.

If your device has been lost or stolen, follow the *Recommended remote wipe*.

If you want to attempt to fully remove any malware from your device you may wish to consider some of the *Advanced options*.

In any case, if you want to be completely certain that data cannot be recovered, also consult the BCSF guidance on [Secure sanitization of storage media](/guidance/secure-sanitization-storage-media).

| **Device type** | **Recommended secure wipe** | **Recommended secure remote wipe** | **Advanced options** |
| --- | --- | --- | --- |
| Android | [Erase all data (factory reset)](https://support.google.com/android/answer/6088915?hl=en) | [Android remote erase](https://support.google.com/accounts/answer/6160491?hl=en) or [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) | Re-install Android using stock images available from some OEMs, e.g. [Google](https://developers.google.com/android/images), [Sony](https://developer.sony.com/develop/open-devices/get-started/flash-tool/how-to-flash/) |
| Chrome OS | [Reset to Factory Settings](https://support.google.com/chromebook/answer/183084?hl=en-GB) | [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) | [Recover your Chromebook](https://support.google.com/chromebook/answer/1080595) |
| iOS | [Erase all content and settings](https://support.apple.com/en-gb/HT201274) | [Find my iPhone](https://support.apple.com/en-gb/HT201472) or [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) | [DFU mode restore](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf#page=6) (PDF) |
| macOS | [Manually erase your hard disk](https://support.apple.com/en-gb/HT208496), choosing the *Secure erase* option | [Find my iPhone](https://support.apple.com/en-gb/HT201472) or [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) |     |
| Windows | [Reset your PC](https://support.microsoft.com/en-gb/help/12415#section3), choosing the *Remove everything* option | Use [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) if using MDM-managed Windows | Use [Recovery drive](https://support.microsoft.com/en-gb/help/12415#section4) or [Installation media](https://support.microsoft.com/en-gb/help/12415#section5) to reset your PC, choosing the *Remove everything* option; or [clear your TPM](https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/initialize-and-configure-ownership-of-the-tpm#clear-all-the-keys-from-the-tpm) |

**Once erased**

Once your device has been securely erased, you can follow the set-up process to get back working again, or pass the device on knowing that the data will not be recovered.

---

## Technical notes

For Mac devices

For Mac devices without the [T2 security chip](https://support.apple.com/en-us/HT208862), if encryption was not enabled before the device was first used, it cannot be guaranteed that the secure erase will remove all sensitive data so that it cannot be recovered. In these cases, [BCSF media sanitization guidance](/guidance/secure-sanitization-storage-media) should be followed.

For both devices with and without the T2 security chip, you should consider erasing and re-flashing the [device firmware](/bronze-training/mobile-device-guidance/managing-mobile-device-firmware).