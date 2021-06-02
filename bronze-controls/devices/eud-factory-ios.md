---
title: Reset and reprovision - iOS devices
description: Discover the ways in which organisations can restore iOS devices from a misconfigured or potentially compromised state to a known-good state.
published: true
date: 2021-06-02T13:22:41.158Z
tags: bronze, bronze-training, sourced
editor: markdown
dateCreated: 2021-02-22T00:29:48.858Z
---

# Reset and reprovision - iOS devices

Discover the ways in which organizations can restore iOS devices from a misconfigured or potentially compromised state to a known-good state.

The methods described here are not guaranteed data sanitization methods; they may not completely erase data so it cannot be recovered. For more information about how to sanitize affordably, please refer to the BCSF guidance on [Secure sanitization of storage media](/bronze-controls/topic-sanitization).

This guidance is for organizations deploying or redeploying iOS devices onto their networks. It describes the ways in which devices can be restored from a misconfigured or potentially compromised state to a known-good state, using iOS native functionality.

There are several ways to restore an iOS device. However, the underlying procedures performed are not publicly documented, so the BCSF cannot give complete assurance to the extent of malware removal.

-   Erase all content and settings]
-   Restore iOS to factory settings through iTunes
-   DFU mode restore
-   Remote wipe

Each of these methods is explained in full alongside the risks of using them. We then recommend one of the methods to use in each of the following four common scenarios:

**Scenario 1: Sanitizing a device believed to be compromised with malware**  
Use this reset method if a user has reported that their device behaving strangely, or has executed potentially malicious code on the device. This method will remove any malware from the device so that it can be reused

**Scenario 2: Preparing a device which has not previously been managed**  
Use this reset method if a device is to be provisioned onto the corporate network, but the history of the device is unclear. This method will restore the device to an 'out-of-box' state so that it can be provisioned as per existing guidance on deploying new devices.

**Scenario 3: Reissuing a device to a different user in the same security environment**  
Use this reset method where a device is to be transferred between different employees, and is to be reset to factory settings so that the reprovisioning steps for that platform can be followed as if the device were new.

**Scenario 4: Sanitizing a device for release to lower security domain or sale**  
Use this reset method if the device is to be transferred out of a secure environment and you wish to perform a best-endeavours sanitization of the device.

**Note**: Many of the security-related features in iOS, including erase methods, are discussed in detail in the [iOS Security Whitepaper](https://www.apple.com/business/docs/iOS_Security_Guide.pdf).

## Erase all content and settings

To [erase all content and settings](http://support.apple.com/kb/HT2110), choose the following option:

`Settings --> General --> Reset --> Erase all Content and Settings`.

You can also configure your device to automatically erase all content if a passcode is entered incorrectly 10 times, by enabling the Erase Data option.

Note that:

-   If the **Find My iPhone** setting is turned on, the user’s Apple ID and password will be required.
-   If the **Restrictions** options are in use, the restrictions PIN will also be required.  
      
     

### **What happens**

Devices supporting hardware encryption will delete the key used to encrypt data. Deleting this key makes the encrypted data no longer accessible, effectively deleting all user data and settings. By performing this action all existing settings on the device will be removed, including any security settings previously configured. Apple recommends this method before selling or giving away an iOS device.  
 

### **Malware removal**

Any malware from apps executing at user-level will be deleted using this method. Malware exploiting a root-level vulnerability to achieve persistence (like a jailbreak would do) may persist by using this reset method.  
 

### **Rooted devices**

This method successfully deletes all user content, however the jailbreak can persist.  
 

### **Risks**

-   Malware exploiting a root-level vulnerability to achieve persistence may persist by using this reset method.
-   A root-level exploit or malware may change system functionality, including that used to reset a device.

## Restore iOS to factory settings through iTunes

Using this method, the device is restored to factory settings, deleting all data and content from the device. The latest version of iOS - if not already in use - is also installed. Once restored, it can be configured as a new device, or can recover previous content by restoring a backup.

To restore devices using iTunes, you'll need to install the latest version of iTunes, and also turn off the **Find my iPhone** feature (if active) in `Settings --> iCloud` on the device, in order to disable Activation Lock.

To [restore the device through iTunes](http://support.apple.com/kb/ht1414), connect the device to a computer running iTunes. In the device’s **Summary** pane, click **Restore**. You'll be prompted to confirm the action.  
 

### **What happens**

By performing this method and setting the device as 'new', all existing settings on the device will be removed, including any security settings previously configured. However, by performing this method and restoring a previous backup, security settings may also be recovered.

Note: The technical procedure to restore a device to factory settings by this method has not been disclosed, so it is not publicly known if every component of the system is completely restored to a trusted state or if malware may circumvent this procedure by any means. Therefore the BCSF can't guarantee that any high privileged malware will not persist after performing this reset method.  
 

### **Malware removal**

Any malware from apps executing at user-level will be deleted using this method.  
 

### **Rooted devices**

This method successfully deletes all content, including any exploits used to jailbreak the device.  
 

### **Risks**

-   It cannot be completely guaranteed that malware exploiting a root-level vulnerability to achieve persistence will be removed by following this method.

## DFU mode restore 

Restoring a device using DFU mode ensures that only unmodified Apple-signed code will be present on the device.

To enter Device Firmware Upgrade (DFU) mode:

1.  Connect the device to a computer.
2.  Hold down both the **Home** and **Sleep/Wake** buttons.  
    If there's no **Home** button, hold down the **Sleep/Wake** and **Volume Down** buttons.
3.  After 8 seconds, release the **Sleep/Wake** button while continuing to hold down the **Home** / **Volume Down**.  
    If DFU mode has been activated, the screen will be black. If the Apple logo is displayed (or there's other signs indicating the device is on) means that the process was not performed correctly.  
     

### **What happens**

Restoring a device using DFU mode ensures that only unmodified Apple-signed code will be present on the device. After restoring device in DFU mode, the latest version of the operating system is also installed. By performing this action all existing settings on the device will be removed, including any security settings previously configured.  
 

### **Malware removal**

Only unmodified Apple-signed code is present on the device, it is highly unlikely that malware will be able to persist when using this reset method.  
 

### **Rooted devices**

This method deletes all content, including any exploits used to jailbreak the device.  
 

### **Risks**

-   Errors If may occur if an older version of iTunes is used to perform this restore procedure.

## Remote wipe

There are three methods to remotely wipe an iOS device:

-   Resetting from a Mobile Device Management (MDM) server. An MDM server allows the management of iOS devices enrollled to an enterprise environment. Such a server can be built in-house by an organization or purchased by a third party.
-   Using an iCloud account. [Remote Wipe through iCloud](http://support.apple.com/kb/PH2701) is an option available for users to reset their devices in case they're lost or stolen, provided they've linked the device with an iCloud account, and enabled the **Find My iPhone** feature.
-   [Using Microsoft ActiveSync](https://technet.microsoft.com/en-us/library/aa998614(v=exchg.160).aspx).  
     

### **What happens**

The effects of this method are similar to the **Erase all contents and settings** procedure. It deletes all user data and settings by deleting the key used to encrypt such data. The device can then be set up as new, or restored from a backup. By performing this action, all existing settings on the device will be removed, including any security settings previously configured.  
 

### **Malware removal**

Any malware executing at user-level will be deleted by this method. However, malware exploiting a root-level vulnerability to achieve persistence may persist by using this reset method.  
 

### **Rooted devices**

This method successfully deletes all user content, however the jailbreak can persist.  
 

### **Risks**

-   Malware exploiting a root-level vulnerability to achieve persistence may persist by using this reset method.
-   A root-level exploit or malware may change system functionality, including that used to reset a device.
-   A root-level exploit or malware may remove configuration profiles enforced by enterprise policies and prevent the reset.

## Reprovisioning scenarios for iOS devices

For the four common reprovisioning scenarios outlined above, the BCSF recommend the following methods.  
 

### **Scenario 1: Sanitizing a device believed to be compromised with malware**

If malware is believed to reside in an application installed from the App Store:

-   **Erase all contents and settings** can be used and does not require the device to be connected to a computer.
-   **Restore to factory settings** can also be used but requires the device to be connected to a computer with iTunes installed.
-   **DFU mode restore** is intended for restoring a device that cannot be booted, however it can also be used.
-   **Remote wipe** is intended for scenarios where a device is lost or stolen, however it can also be used.

If malware is believed to reside in an application installed from a jailbreak source:

-   Use **Restore to factory settings**.
-   **DFU mode restore** is intended for restoring a device that cannot be booted; however it can also be used.
-   **Remote wipe** is intended for scenarios where a device is lost or stolen; however it can also be used.

If malware is believed to execute at root level:

-   Use **DFU mode restore** to restore the device.
-   **Restore to factory settings** may successfully remove a root level exploit or malware, however this cannot be guaranteed.  
     

#### **Risks**

-   **Erase all contents and settings** and **Remote wipe** may not correctly reset the device if it is jailbroken.
-   If the device is affected by a root-level exploit or malware without knowledge of the user, this may persist by using the **Erase all contents and settings** and **Remote wipe** methods.
-   Although **restore to factory settings** successfully recovers a jailbroken device, we can't guarantee that malware exploiting a root-level vulnerability to achieve persistence will be removed using this method.

### **Scenario 2: preparing a device which has not previously been managed**

When preparing a device that has not been managed, you should assume it's carrying malware, and treat as described in scenario 1 above.

#### **Risks**

-   **Erase all contents and settings** and **Remote wipe** may not correctly reset the device if it is jailbroken.
-   If the device is affected by a root-level exploit or malware without knowledge of the user, this may persist by using the **Erase all contents** and settings and **remote wipe** methods.
-   Although **restore to factory settings** successfully recovers a jailbroken device, we cannot guarantee that malware exploiting a root-level vulnerability to achieve persistence will be removed by following this method.

### **Scenario 3: Reissuing a device to a different user in the same security environment**

None of the reset methods allow settings to be kept. The only way to restore settings are from a backup, downloading a configuration profile, or manually re-entering them.

-   **Erase all contents and settings** can be used and does not require the device to be connected to a computer. **Restore to factory settings** can also be used but requires the device to be connected to a computer with iTunes installed. In both these cases, the new user will have to activate the device through the network, either using a wireless connection or connecting to a computer and using iTunes. The device can either be set up as new, or previous settings can be restored by restoring a backup, in which case the passcode is not restored. In an enterprise environment, the device will have to be re-enrollled with the MDM service.
-   **DFU mode restore** is intended for restoring a device that cannot be booted, however it can also be used.
-   **Remote wipe** is intended for scenarios where a device is lost or stolen, however it can also be used.  
     

#### **Risks**

-   **Erase all contents and settings** and **Remote wipe** may not correctly reset the device if it is jailbroken.
-   If the device is affected by a root-level exploit or malware without knowledge of the user, this may persist by using the **Erase all contents and settings** and **Remote wipe** methods.
-   Although **restore to factory settings** successfully recovers a jailbroken device, we can't guarantee that malware exploiting a root-level vulnerability to achieve persistence will be removed using this method.

### **Scenario 4: Sanitizing a device for release to lower security domain or sale**

-   **Erase all contents and settings** can be used and does not require the device to be connected to a computer.
-   **Restore to factory settings** can also be used but requires the device to be connected to a computer with iTunes installed.
-   **DFU mode restore** is intended for restoring a device that cannot be booted, however it can also be used.
-   **Remote wipe** is intended for scenarios where a device is lost or stolen, however it can also be used.  
     

#### **Risks**

-   **Erase all contents and settings** and **Remote wipe** may not correctly reset the device if it is jailbroken.
-   If the device is affected by a root-level exploit or malware without knowledge of the user, this may persist by using the **Erase all contents and settings** and **Remote wipe** methods.
-   Although **restore to factory settings** successfully recovers a jailbroken device, we can't guarantee that malware exploiting a root-level vulnerability to achieve persistence will be removed using this method.