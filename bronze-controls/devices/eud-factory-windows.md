---
title: Reset and reprovision - Windows devices
description: Discover the ways in which organizations can restore Windows devices from a misconfigured or potentially compromised state to a known-good state.
published: true
date: 2021-06-24T18:21:55.862Z
tags: bronze, bronze-training, sourced
editor: markdown
dateCreated: 2021-02-22T00:30:32.279Z
---

# Reset and reprovision - Windows devices

Discover the ways in which organizations can restore Windows devices from a misconfigured or potentially compromised state to a known-good state.

This guidance is for organizations deploying or redeploying Windows devices onto their networks. It describes the ways in which devices can be restored from a misconfigured or potentially compromised state to a known-good state, using Windows' native functionality.

## Windows devices can be reset using the following methods.

**1.  'Reset this PC' - keep my files
2.  'Reset this PC' - remove everything
3.  Manual re-install
4.  Clearing the TPM (trusted platform module)**
     

Each of these methods is explained in full alongside the risks of using them. We then recommend methods to use in each of the following four common scenarios:

**Scenario 1: Sanitising a device believed to be compromised with malware**  
Use this reset method if a user has reported that their device behaving strangely, or has executed potentially malicious code on the device. This method will remove any malware from the device so that it can be reused.

**Scenario 2: Preparing a device which has not previously been managed**  
Use this reset method if a device is to be provisioned onto the corporate network, but the history of the device is unclear. This method will restore the device to an 'out-of-box' state so that it can be provisioned as per existing guidance on deploying new devices.

**Scenario 3: Reissuing a device to a different user in the same security environment**  
Use this reset method where a device is to be transferred between different employees, and is to be reset to factory settings so that the reprovisioning steps for that platform can be followed as if the device were new.

**Scenario 4: Sanitising a device for release to lower security domain or sale**  
Use this reset method if the device is to be transferred out of a secure environment and you wish to perform a best-endeavours sanitization of the device.

**Note:** Malware exists with the ability to infect the firmware of components, such as the BIOS of a motherboard. While the persistence of such malware is beyond the scope of this guidance, it is known to exist and its removal cannot be guaranteed with any of the methods discussed below.

## 'Reset this PC' - keep my files

This [system refresh](http://windows.microsoft.com/en-gb/windows-8/restore-refresh-reset-pc) functionality is primarily aimed at fixing a Windows installation that no longer functions properly, or has slowed down significantly since initial installation, without affecting the user’s data. User files and personalisation settings (such as wallpapers and themes are left unchanged).

To perform a system refresh, use the following option.

`PC Settings --> Update & security --> Recovery --> Reset this PC --> Keep my files`

###   
**What happens**

During the refresh, the PC first boots into the Windows Recovery Environment. From here, user files and applications to be retained are marked for exclusion from the refresh process. A new copy of Windows is then installed, after which the retained data is restored.

Some system settings are maintained. However, some settings that are deemed by Microsoft to be commonly misconfigured (and therefore could potentially cause issues) are intentionally reset back to the system default. The following table shows some examples of which settings are kept, and which are deleted.

| **Settings kept** | **Settings deleted** |
| --- | --- |
| Wireless network connections | Mobile broadband connections |
| BitLocker and BitLocker To Go settings | Drive letter assignments |
| Personalisation settings such as lock screen background, and wallpaper | File type associations |
| Display settings | Windows firewall settings |
| Microsoft-approved applications from the Windows store | All third party applications, including applications installed from removable media and non-Microsoft locations on the internet |

Note that after the refresh, a list of removed applications is created on the desktop. Further details can be found at the [Recover Options in Windows 10 support website](https://support.microsoft.com/en-us/help/12415/windows-10-recovery-options).   
 

### **Malware removal**

By default, this method will remove all third party applications, including any malicious applications that may have been previously installed by the user. These will be backed up into the **Windows.old** folder which can then be removed manually.

Note that:

-   if malware was distributed through the Microsoft app store, it could persist through the re-installation of this 'approved' application
-   all user files are retained and malicious files on the disk will persist through this process  
     

### **Risks**

-   This method does **not** alter or remove any user data, which could allow malicious files to persist. Malicious files and malware could persist in various areas untouched by the refresh process and re-infect the device after resetting.
-   This method only selectively removes configurations and settings. To ensure all settings are subsequently set to their expected values, the machine should have a full set of policies applied to it though Active Directory or other mechanism.
-   This process relies on the integrity of the recovery environment. Malware which had compromised the recovery partition could persist into the new environment.

## 'Reset this PC' - remove everything

This [reset method](http://windows.microsoft.com/en-gb/windows-8/restore-refresh-reset-pc) provides a simple ‘one click’ method of erasing user data and reinstalling the operating system to its default state. All configurations and settings are cleared, so any post-installation system hardening or security configuration will need to be re-applied.

To perform a system reset, use the following option.

`PC Settings --> Update & security --> Recovery --> Reset this PC --> Remove everything`

The user is provided with two options for the reformatting of the drive.

1.  **Just remove my files**  
    Using this option, all references to files are removed and the files are marked as deleted (and therefore may be overwritten in future). However the data for the actual file is not removed until it is overwritten. This makes it possible for forensic software to easily recover the previously deleted files.
2.  **Remove files and clean the drive**  
    This option removes data in a more secure way, and writes data over every sector of the drive before formatting it for use. This makes it much more difficult to recover files from the drive.  
     

### **What happens**

With both options, all user data and files are removed. Additionally, all installed applications are removed, including official Microsoft applications and any software installed from the Microsoft app store. Only default or stock applications are reinstalled.

When using **Reset this PC** on a drive with BitLocker full disk encryption or ‘Device Encryption’ enabled, the process will simply delete the decryption key, making recovery of the encrypted data impossible. BitLocker can also provide protection against boot sector malware, by using the TPM to verify the integrity of boot files.  
 

### **Malware removal**

The **Remove files and clean the drive** option will write data to all sectors of the drive. This includes all partitions, destroying all data on the disk, preventing any malware persisting the reset process.

The **Just remove my files** option may not wipe all sectors of the disk and could allow malware to persist after the process. For example, if malware were to infect the boot sector of the drive, it may not be sanitised using **Just remove my files** option and therefore may persist. The Secure Boot feature on supported devices should mitigate this.  
 

### **Risks**

-   Since all PC settings are removed and changed back to default, any security settings would have to be re-applied. To ensure all settings are subsequently set to their expected values, the machine should have a full set policies applied to it though Active Directory or other mechanism.
-   The **Just remove my files** option will **not** securely remove all data, allowing basic forensic tools to recover many of the files.
-   The **Remove my files and clean the drive** option may not encompass the entire drive, which could allow malware to reside in areas such as the boot sector. This process relies on the integrity of the recovery environment. Malware which had compromised the recovery partition could persist into the new environment.

## Manual re-install

Reinstalling Windows manually involves the following:

-   manually wiping hard drive using a tool such as ‘[dd](https://en.wikipedia.org/wiki/Dd_(Unix))’
-   generating a new partition table
-   formatting those partitions
-   [re-installing Windows](http://windows.microsoft.com/en-gb/windows-8/clean-install) from installation media

All configurations and settings are cleared, so any post-installation system hardening or security configuration will need to be re-applied.  
 

### **What happens**

Manual re-instal is in many ways similar to the [Reset this PC](http://cesgdet.atlassian.net/#remove) option described above (which essentially automates the manual process, and presents it in a way that allows non-technical users to perform the same tasks).

However, a manual re-install provides some benefits over the automated process. By manually wiping the drive, steps such as writing the drive with random data can be performed or omitted as necessary. This can save a large amount of time if the secure removal of data is not an issue. While this is offered in the **Just remove my files** option, manually performing these tasks also provides certainty that all sectors of the drive have been overwritten.  
 

### **Malware removal**

This method removes all malware, provided that all sectors of the drive are wiped before formatting and installation.  
 

### **Risks**

-   All PC settings are removed and changed back to default. Any security settings have to be re-applied.
-   There's potential for certain configuration settings to be forgotten or missed.
-   All partitions must be wiped to ensure that no malware persists.

## Clearing the TPM (trusted platform module)

This feature will only be of use if the device is encrypted using a key stored in the TPM, such as when usingBitLocker. When the TPM is cleared, it wipes any keys that are stored on the TPM so that any data that has been encrypted using those keys will not be accessible without the BitLocker Recovery Key.

Exactly how to clear the TPM will vary per device manufacturer, but will generally approximate the following process:

`BIOS/UEFI Setup menu --> Security --> TPM Security --> Tick the "Clear" box`

A new OS will need to be installed, meaning that all settings will then be the defaults.  
 

### **What happens**

TPM clearing will wipe any keys stored within the TPM, so that any data that has been encrypted using those keys will not be accessible without the BitLocker Recovery Key.  
 

### **Malware removal**

Any malware that was present on the encrypted disk will be effectively deleted.   
 

### **Risks**

-   TPM clearing does not strictly erase data on the device; it makes reading that data impossible without the recovery key.
-   The user will need to manually delete any backups of the recovery key (saved to external media, backed up in the cloud, etc.), otherwise recovery of the data will be possible.

## Reprovisioning scenarios for Windows devices

For the four common reprovisionining scenarios outlined above, the BCSF recommend the following methods.  
 

### **Scenario 1: Sanitising a device believed to be compromised with malware**

When removing malware, we recommend that each sector of the hard drive is completely overwritten to ensure no malicious files persist. This is because some advanced malware has the ability to infect the boot sector.

-   Both **Reset this PC (Remove everything)** and **Manual re-install** offer the above functionality.
-   If using, **Reset this PC (Remove everything)** , ensure you choose **Remove files and clean the drive**, as this option wipes all sectors of the drive.
-   **Manual re-install** will provide additional certainty when removing malware, as steps can be performed and verified manually.  
     

#### **Risks**

-   **Manual re-install** provides the most certainty with regards to malware removal, but also takes more time and effort. However, it also presents the opportunity for mistakes to be made, or steps to be missed.
-   **Reset this PC (Remove everything)** must use the **Remove files and clean the drive** option, as the **Just remove my files** option may not clear the boot sector of the drive.

### **Scenario 2: Preparing a device which has not previously been managed**

When preparing a device that has not been managed, you should assume it's carrying malware, and treat as described in scenario 1 above.  
 

#### **Risks**

-   **Manual re-install** provides the most certainty with regards to malware removal, but also takes more time and effort. However, it also presents the opportunity for mistakes to be made, or steps to be missed.
-   **Reset this PC (Remove everything)** must use the **Remove files and clean the drive** option, as the **Just remove my files** option may not clear the boot sector of the drive.

### **Scenario 3: Reissuing a device to a different user in the same security environment**

**Reset this PC (Remove everything)** is sufficient to transfer a device in which personal data is not available to the new user, but the new user would be able to recover the data using forensic software. If the new user should in no way be able to recover personal data from the device, then you should use the **Remove files and clean the drive** option, or **Manual re-install**.

#### **Risks**

-   The **Just remove my files** option of **Reset this PC (Remove everything)** will **not** attempt to securely wipe data, allowing it to be recovered using forensic tools and techniques.
-   **Manual re-install** provides the most certainty with regards to malware removal, but also takes more time and effort. However, it also presents the opportunity for mistakes to be made, or steps to be missed.

### **Scenario 4: Sanitizing a device for release to lower security domain or sale**

Microsoft recommend their **Reset this (Remove everything)** option when sanitizing a device for sale. Use this provided the **Remove files and clean the drive** option method is selected, which makes forensic file recovery difficult.

If the drive is using BitLocker encryption, we recommend using **Reset this PC (Remove everything)**, as encryption metadata will be deleted making data recovery impossible. Or Clearing the TPM, as this removes the keys in the TPM used to decrypt the data.

Where sensitive data resides on the hard drive of the machine (this includes the data that resides on a device after clearing the TPM) we recommend **Manual re-install**. This allows the number of random data passes to be customised, providing additional protection against advanced data recovery techniques.

**Reset this PC (Remove everything)** requires significantly less time and effort to perform, as Microsoft have automated the majority of this process. However **Manual re-install** provides additional security surrounding the secure removal of sensitive data.

#### **Risks**

-   If using **Reset this PC (Remove everything)**, ensure that the **Just remove my files** option is **not** used. This option does **not** securely remove data from the drive, making it easy to recover using forensic tools.
-   Even when using the **Remove files and clean the drive** option, note that only one pass of data will be written to the drive. While this makes it much more difficult to recover any meaningful data from the drive, a process of 3 passes of random data to each sector of the drive is recommended for the secure removal of data.
-   TPM clearing does not strictly erase data on the device; if the recovery key or other credential still exists for the encrypted disk then data may be recoverable.