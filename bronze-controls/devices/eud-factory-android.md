---
title: Reset and reprovision - Android devices
description: Discover the ways in which organisations can restore Android devices from a misconfigured or potentially compromised state to a known-good state.
published: true
date: 2021-06-02T13:23:31.921Z
tags: bronze, bronze-training, sourced
editor: markdown
dateCreated: 2021-02-22T00:28:50.527Z
---

# Reset and reprovision - Android devices

Discover the ways in which organizations can restore Android devices from a misconfigured or potentially compromised state to a known-good state.

The methods described here are not guaranteed data sanitization methods; they may not completely erase data so it cannot be recovered. For more information about how to sanitize affordably, please refer to the BCSF guidance on [Secure sanitization of storage media](/bronze-controls/topic-sanitization).

This guidance is for organizations deploying or redeploying Android devices onto their networks. It describes the ways in which devices can be restored from a misconfigured or potentially compromised state to a known-good state, using Android's native functionality.

Android devices can be reset using two methods.

1.  Factory reset
2.  Re-installation of stock firmware
     

Each of these methods is explained in full alongside the risks of using them. We then recommend methods to use in each of the following four common scenarios:

**Scenario1: Sanitizing a device believed to be compromised with malware**  
Use this reset method if a user has reported that their device behaving strangely, or has executed potentially malicious code on the device. This method will remove any malware from the device so that it can be reused.

**Scenario 2: Preparing a device which has not previously been managed**  
Use this reset method if a device is to be provisioned onto the corporate network, but the history of the device is unclear. This method will restore the device to an 'out-of-box' state so that it can be provisioned as per existing guidance on deploying new devices.

**Scenario 3: Reissuing a device to a different user in the same security environment**  
Use this reset method where a device is to be transferred between different employees, and is to be reset to factory settings so that the reprovisioning steps for that platform can be followed as if the device were new.

**Scenario 4: Sanitizing a device for release to lower security domain or sale**  
Use this reset method if the device is to be transferred out of a secure environment and you wish to perform a best-endeavours sanitization of the device.

## Factory reset

A factory reset wipes the user data partition. Any modifications made to the system partition (including operating system updates) are left untouched and not restored to factory state. The user’s data can be recovered using simple forensics tools and malware could persist in other partitions.  
 

### **Performing a factory reset**

According to [Android documentation](https://support.google.com/nexus/answer/2936226), a device can be restored to factory settings from the settings menu, remotely with [Google Device Manager](https://support.google.com/a/answer/173390?hl=en) or from the device’s recovery menu.

The following option allows a user to delete all data from the data partition.

`Settings --> System --> Reset --> Factory data reset`

If the device has a pre-boot recovery menu, then you can use this to perform a factory reset. This performs the same underlying actions as the factory reset option from the `Settings` menu.

Finally, if the user has Google Sync configured, or has the Google Apps Device Policy app installed, then this method can be called remotely using [Google’s remote wipe](https://support.google.com/a/answer/173390).  
 

### **What happens**

The factory reset function reboots the device into recovery mode and re-formats the data partition (and Cache partition if present). This is the same function as a manual wipe command from the recovery menu. With this method, the data partition is overwritten. The data partition holds all application data, including device settings. After performing a factory reset, the device returns to default settings.   
 

### **Malware removal**

This method will remove all apps installed by the previous user, including any malicious Java based apps. If a malicious application was previously able to elevate its privileges to root, it would be able to place malicious root binaries on the system partition. If this has occurred, then this method would fail to remove the malware.  
 

### **Rooted devices**

If a device had been rooted, then it would have modified the system partition to maintain root between handset resets. As this method does not touch the system partition, it would be likely that the device would remain rooted. If the bootloader of a device was unlocked, it would remain so after this method was used.  
 

### **Risks**

-   This method does not delete data outside the **/data** partition folder so some data may persist.
-   The external SD card is not wiped during the factory reset.
-   The data removed can sometimes be recovered using forensics tools.

## Re-installation of stock firmware

The most comprehensive method for assuring all partitions contain only original files is to reinstall the stock firmware. This method is the only option that will overwrite the system partition. Any device that has been rooted (or infected with malware running as root) would likely have altered the system partition. This option, although offering a more complete reset, varies per device and in some cases may void the manufacturer’s warranty.  
 

### **Reinstalling the stock firmware**

-   Stock firmware for the device OEM is available from [https://developers.google.com/android/images](https://developers.google.com/android/images).
-   For Nexus and Pixel devices, a guide is available at [https://developers.google.com/android/images#instructions](https://developers.google.com/android/images#instructions).  
     

### **What happens**

The exact process to flash a device with the official firmware will vary per device and may, in some cases void the warranty. For example, the Samsung Galaxy devices can be flashed with official firmware using the Odin application without unlocking the bootloader, however the others may require the user to unlock the bootloader first.

Overwriting the partitions with the stock firmware means that the user can guarantee that any data including malware will be overwritten regardless of the partition it is on. We recommend that if the bootloader needs to be unlocked for this process, that it's re-locked on completion.

As part of this method, the data partition is overwritten. The data partition holds all application data, including device settings. After performing a factory reset in this way, the device returns to default settings.   
 

### **Malware removal**

This method will remove all apps installed by the previous user, including all Java based malware.

If a malicious application was able to elevate its privileges to root, it would be able to place malicious root binaries on the system partition. If this has occurred, then this method would be effective in removing malware from the device.  
 

### **Rooted devices**

This method will overwrite the system partition, undoing modifications made by rooting tools. If the bootloader of a device was unlocked, the only way to relock it is to install a signed firmware image. If the device was left unlocked, then an attacker would in theory be able to load the device in recovery mode and bypass any lock screen the user had placed on the device.  
 

### **Risks**

-   This method will vary per manufacturer and device in terms of method, difficulty, availability of resources and effect on warranty. We strongly recommend you seek official guidance from the manufacturer before attempting; if done incorrectly it can lead to permanent damage to the device.
-   All flashing relies on trusting at least one component of the device to correctly install the firmware. This means that sufficiently advanced malware on a device could manipulate the process and persist in spite of the factory reset.
-   Re-installing the firmware may not work in all cases.

## Reprovisioning scenarios for Android devices

For the four common reprovisioning scenarios outlined above, the BCSF recommend the following methods.  
 

### **Scenario 1: Sanitizing device believed to be compromised with malware**

Malware within malicious applications can be removed using **factory reset**.

Malware with root exploits that have compromised the system partition can be removed by **re-installing firmware**. Advanced malware cannot be removed as the wiping process must rely on code held on the boot sector of the device itself.

#### **Risks**

-   Sufficiently advanced malware cannot be removed from a device.
-   It is difficult to determine how advanced the malware is, and which partitions are compromised. Therefore, in high security environments, a device with suspected malware should not be used, even after a full factory reset.  
     

### **Scenario 2: Preparing a device which has not previously been managed**

The device should be assumed to be carrying malware. The only guarantee for removing this is to **re-installing firmware** as a **factory reset** will only remove all Android application based malware, and all user data from the previous user. Following either method, the device will need to be configured with appropriate security settings.

#### **Risks**

-   **Factory reset** will not remove malware that has infected any partition other than the data partition.
-   **Re-installing firmware** may not remove malware that has infected the boot partition.
-   **Re-installing firmware** may void warranty and relies on stock firmware images being made available by the manufacturer.  
     

### **Scenario 3: Reissuing a device to a different user in the same security environment**

Performing a **factory reset** is sufficient to transfer a device in which personal data is not available to the new user, but the new user would be able to recover the data using forensic software. If the new user should in no way be able to recover personal data from the device, then you should **re-install firmware**.

#### **Risks**

-   **Factory reset** may allow application malware which has escalated privilege to persist on the device.
-   **Factory reset** assumes that the new user will not use forensic tools to recover and restore the previous data, or would not benefit from doing so.
-   **Re-installing firmware** may allow advanced malware to persist on the device.
-   **Re-installing firmware** may void the warranty and relies on stock firmware images being made available by the manufacturer.  
     

### **Scenario 4: Sanitizing a device for release to lower security domain or sale**

As Android does not offer an official method to securely remove data from a device, it is recommended that an Android device is never released to lower security domain or sale.

#### **Risks**

-   Android documentation makes no guarantees that either method can securely wipe a device.
-   **Re-installing firmware** could wipe the user’s data partition so that it could not be recovered with forensics tools, but it is thought that this is device dependent and therefore should not be relied upon.