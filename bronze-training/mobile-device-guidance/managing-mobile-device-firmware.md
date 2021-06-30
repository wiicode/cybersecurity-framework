---
title: Managing mobile device firmware
description: Advice for IT system administrators on firmware management for smartphones, tablets, laptops and desktop PCs
published: false
date: 2021-06-02T14:07:49.401Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:49:20.202Z
---

All modern mobile devices include firmware that is critical to the secure function of the device.

This guidance will help you understand how firmware on mobile devices can be managed. It also provides recommendations on steps you can take to manage any associated security risks. 


## Why manage mobile device firmware?

Firmware is typically code that performs configuration and control of hardware components that make up a mobile platform. As such, firmware is usually the first code that runs when a mobile device is powered on, and therefore provides the foundation from which trust in the system is built.

Firmware also plays a major role in setting up many of the protections necessary to secure the device and operating system. This includes configuring hardware security settings, verified boot, and hand off to the operating system.

Although firmware attacks would have to be highly targeted, a successful attack could provide long term, persistent access or be destructive in nature. The outcome could include data loss, system modification or permanent denial of service. 


## Preparation for firmware management

There are several aspects of firmware management which you should keep in mind when planning your management regime.

### **Firmware Updates**

Firmware updates allow bug fixes, new functionality and security updates to be applied to a device. As such, they are an essential element of [keeping devices up to date](/bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date).

You will need to consider how your organization will deploy and manage firmware updates. Mobile phones, including Android and iOS, typically package and distribute firmware updates alongside operating system and software updates. If you are already following the recommendations for [keeping devices up to date](/bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date), then firmware updates should happen as a matter of course.

On laptops and PCs, support for automated firmware updates will vary depending on the device, manufacturer, and operating system. If devices do not support automated updates as part of the operating system update mechanism, then you will need to consider what [mobile device management (MDM)](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) services or [enterprise tools are available to automate and distribute firmware updates](/blog-post/automating-uefi-firmware-updates).

### **Firmware Settings**

Mobile device firmware will have settings that can be modified to configure the functionality of the overall system. Some firmware settings, such as *secure boot* and *boot path*, are critical to the secure operation of the device. Others allow for functional control of devices by, for example, enabling or disabling the microphone, or [managing access to peripheral interfaces](/bronze-training/mobile-device-guidance/using-peripherals-securely) but may still be considered as security settings.

On mobile phones, separate management of firmware settings is typically not required, whereas on PCs and laptops it might be. Settings may have to be managed independently through local firmware management consoles, mobile device management (MDM), or custom enterprise management tools.

In all cases it is important that the ability to modify critical firmware and boot settings is restricted to administrators only.  

### **Firmware Monitoring**

You should consider what firmware logging and monitoring capabilities are available on the devices your organization uses. 

Effective [logging and monitoring](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) could include information and events such as:

-   firmware version
-   modification of device firmware settings
-   firmware update events
-   compliance of device firmware settings
-   boot status
-   boot measurements

In practice, many mobile devices have only very limited support for logging these types of events.

On PCs and laptops, support will vary. Some devices may be able to provide basic feedback on firmware. On Chromebooks, for example, [mobile device management](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) can be used to enforce [device reporting](https://support.google.com/chrome/a/answer/1375678?hl=en&ref_topic=9028500), which includes firmware and boot state information.

It may also be possible to use additional enterprise management tools or services to generate custom logs. On Windows, for example, agent based management tools such as [System Center Configuration Manager (SCCM)](https://www.microsoft.com/en-gb/cloud-platform/system-center-configuration-manager) or [Azure log analytics](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/log-analytics-agent) could be used to [deploy and report on custom device compliance rules](https://docs.microsoft.com/en-us/sccm/compliance/deploy-use/create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-client) or generate [custom logs](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/data-collector-api).

Device manufacturers may also provide separate tools or features that can extend logging capabilities. [HP Sure Start](https://www8.hp.com/en/solutions/computer-security.html) is one example. This enhanced firmware protection system, available on HP business laptops, can generate additional Windows event logs for firmware-related security events. These logs can then be forwarded to a remote store using [Windows event forwarding](https://docs.microsoft.com/en-gb/windows/win32/wec/windows-event-collector) or your choice of logging agent, as part of your device [logging and monitoring](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) process.

### **Firmware Resilience**

Some devices will support enhanced protections for firmware code and critical configuration data against attacks or corruption. Typically, these devices will use separate hardware-backed *roots of trust* and key stores to provider stronger cryptographic verification of firmware code and data, as well as secure recovery.

On mobile phones, in many cases these protections are built in as standard. On PCs and laptops, typically these types of enhanced protections will depend on the manufacturer, device and hardware support. Examples include [HP Sure Start](https://www8.hp.com/en/solutions/computer-security.html) and Intel Boot Guard on Windows, and the [T2 security chip](https://support.apple.com/en-gb/HT208862) on macOS. You could factor in these requirements when [choosing which devices to use in your organization](/bronze-training/mobile-device-guidance/choosing-devices).

---

## How to manage device firmware

Your organization will likely use more than one type of mobile device, ranging from PCs and laptops to mobile phones and tablets. These will likely cover a range of hardware manufacturers and operating systems. For each of these devices you should do the following:

-   Determine which firmware management features are available for the device and management infrastructure you are using. Keep this in mind when [choosing which mobile devices to use in your organization](/bronze-training/mobile-device-guidance/choosing-devices).
-   Put processes in place to keep device firmware up to date, automating this where possible. Check if the operating system's automatic update system can also update firmware. If it cannot, set up the device manufacturer's proprietary automatic update service if there is one,or use enterprise management tools to [automate firmware updates](/blog-post/automating-uefi-firmware-updates).
-   Where necessary, enable and configure critical device security settings such as secure boot, allowed boot paths and authenticated updates. You should also apply any additional settings required by your organization’s device configuration policy, such as enable/disable microphone. Use your [mobile device management](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) service to enforce device firmware settings where possible. If this is not supported, separate manufacturer-provided enterprise management tools may be required for remote management. As a last resort , settings may have to be configured via local device management consoles.
-   Restrict access to management interfaces, both local and remote. This will help to protect against unauthorized changes to device settings or device firmware.
-   Where possible, [log and monitor](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) the state of device firmware, and related security events. [Device Health Attestation](https://docs.microsoft.com/en-us/windows/security/threat-protection/protect-high-value-assets-by-controlling-the-health-of-windows-10-based-devices#detect-unhealthy) should be preferred where possible to verify the state of the device. Our [logging and monitoring guidance](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) provides specific recommendations on available platform l[ogging and monitoring](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) mechanisms, including attestation services that in some cases can help monitor firmware integrity.
-   Organizations requiring their firmware to have a higher resiliency should prefer devices that provide stronger integrity protection of firmware code and critical security settings, detection of compromise/tampering, and the ability to securely recover device firmware in the case of unauthorized changes or corruption. Keep these factors in mind when [choosing which mobile devices to use in your organization](/bronze-training/mobile-device-guidance/choosing-devices).
-   Make sure your users can recognize the kind of device warnings that could indicate tampering or corruption of  firmware. Have policies in place for users to report incidents.

When implementing the recommendations above, the process will be different for each platform. We've listed some of these differences below, and where relevant, provided some specific platform recommendations. 

### **Firmware Updates**

On mobile devices such as Android and iOS, firmware updates will usually be applied automatically, as part of wider operating system updates.

However, on PCs and laptops running Windows and Linux operating systems, support for automating firmware updates will vary. To help with this, we have provided some specific recommendations below for these platforms.

| **Operating System** | **Recommendation** |
| --- | --- |
| Windows | Firmware updates can be automated via [Windows Update](https://docs.microsoft.com/en-us/windows-hardware/drivers/bringup/windows-uefi-firmware-update-platform). PCs and laptops must support the [Windows UEFI Firmware Capsule Update](https://docs.microsoft.com/en-us/windows-hardware/drivers/bringup/windows-uefi-firmware-update-platform). This requirement is met for all devices that are compliant with the [Windows Hardware Compatibility Program](https://docs.microsoft.com/en-us/windows-hardware/design/compatibility/whcp-specifications-policies). This simplifies the automation of firmware updates. You should prefer devices that support this. If your OEM (original equipment manufacturer) is not choosing to use that mechanism, you will need to consider alternative enterprise client management solutions that meet your needs. More detailed guidance for firmware update management on Windows can be found in the [Windows 10 platform specific guidance](/bronze-training/mobile-device-guidance/platform-guides). |
| Linux | Support for automated firmware updates will vary between equipment manufacturer and Linux distribution. The [Linux Vendor Firmware Service](https://fwupd.org/) provides an automated solution for firmware updates on Linux devices. |

### **Firmware Settings**

On many mobile devices, such as Android and iOS, separate management of device firmware settings is not required.

However, it is still important for organizations to apply critical device security settings to enforce verified boot modes. This can be achieved using [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services).

On Windows and Linux devices, many firmware settings may have to be managed outside of operating system settings. This includes critical security settings such as secure boot and allowed boot paths. Support for remote management will vary.

We have provided some platform-specific recommendations below.

| **Operating System** | **Recommendation** |
| --- | --- |
| Android | [Developer options](https://developer.android.com/studio/debug/dev-options) should be disabled to prevent unlocking of the device boot loader and debug features. |
| macOS | An EFI password should be set to prevent unintended modifications of firmware settings on a specific system. |
| ChromeOS | [Verified Mode](https://support.google.com/chrome/a/answer/1375678?hl=en) should be enforced to prevent users switching the device into [Developer Mode](https://www.chromium.org/chromium-os/chromiumos-design-docs/developer-mode). |
| Linux | Configurable device settings will vary between device types, models, and manufacturers. At a minimum, they should be managed through the device pre-boot firmware management console. For guidance on recommended security settings, see the firmware section of the [Windows platform specific guidance](/bronze-training/mobile-device-guidance/platform-guides). |
| Windows | Available settings will vary between device types, models, and manufacturers. At a minimum, firmware settings should be managed through the device pre-boot firmware management console. Various options may also be available for remote management, including [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services), or separate manufacturer enterprise management tools. For guidance on recommended settings, see the device firmware section of our [Windows platform specific guidance](/bronze-training/mobile-device-guidance/platform-guides). Many of these settings should be enabled by default by the OEM, as part of the [Windows Hardware Compatibility Program](https://docs.microsoft.com/en-us/windows-hardware/design/compatibility/whcp-specifications-policies). |