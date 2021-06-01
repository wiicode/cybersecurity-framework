---
title: Mobile Device Management
description: Advice on the selection and implementation of Mobile Device Management within your enterprise
published: true
date: 2021-06-01T20:13:37.168Z
tags: guidance, bronze, bronze-training, mdm, favorite
editor: markdown
dateCreated: 2021-03-06T02:31:31.365Z
---

A Mobile Device Management (MDM) service combines device applications, built-in device management features and infrastructure services. Together, these components allow your organization to remotely control, monitor, and enforce policies on employee devices.

This guidance will discuss the importance of MDM, our recommendations when choosing an MDM, and how best to use them to securely manage smartphones, tablets, laptops and desktop PCs.

## Why use MDM?

Mobile Device Management is designed to simplify management of devices within an organization.

Typical functionality includes device enrollment, the ability to control device configuration, protect data, monitor the status and compliance of devices, and manage enterprise approved apps. All across a range of platforms and operating systems.

Most MDM services work over the internet, allowing devices to be managed and **remotely controlled** wherever they are in the world. This means staff can work off-premises, securely.

Some example use cases include **enforcing policies** on a device, such as the use of a [VPN](https://www.ncsc.gov.uk/collection/mobile-device-guidance/virtual-private-networks), performing a [remote device wipe](https://www.ncsc.gov.uk/collection/mobile-device-guidance/erasing-mobile-devices) if the device is lost. MDM would also allow the **monitoring** of devices, to help determine [if the they have been kept up to date](https://www.ncsc.gov.uk/collection/mobile-device-guidance/keeping-devices-and-software-up-to-date), been jail broken, or if a policy violation has occurred.  Additionally, it is important to keep MDMs secure as they hold the keys to unlock, decrypt and remote wipe all the devices within your enterprise.

## Preparing for mobile device management

There are several things to consider before choosing an MDM for your organization.

## Deployment model

MDM services can be on-premises or in the cloud, for example as SaaS solutions. Some products come in both flavors, others only one.

There may also be significant differences and trade-offs in terms of feature support between the two approaches. For example, it may be slower patching with an on-premises service so you will not always have the latest features. 

If you choose to use a cloud MDM service, the BCSF's [Cloud Security Guidance](/silver-training) may help you assess its suitability.  

For on-premises MDM deployments, in [walled garden architecture](/bronze-training/mobile-device-guidance/infrastructure/network-architectures-for-remote-access), you should decide whether you want the service to be deployed *inside* or *outside* the boundary firewall.

If you put the MDM service inside the network boundary, a high-value asset containing cryptographic keys that can control, access and wipe your device is more protected from external attackers, but can make it harder to remotely wipe a lost devices if you also want to revoke its VPN credentials.

## Device and Feature Support

Individual MDM services will often only support *some* device types, security features, and management options. This being so, it's important to ascertain whether the following features are supported for the devices that you use:

### **Device Enrollment**

The enrollment options you require will vary depending on your approach to device management. If your organization owns and fully manages devices your needs are likely to be more easily satisfied than if you run a [BYOD](/bronze-controls/byod-guidance) scheme.

For enterprise owned devices, you should use an MDM platform which supports [zero touch enrollment](/bronze-training/mobile-device-guidance/zero-touch-enrollment). If you choose to use a technical approach that also permits [admin enrollment or self enrollment](/bronze-training/mobile-device-guidance/provisioning-and-distributing-devices), it is important to consider available methods of [authentication](bronze-training/mobile-device-guidance/enterprise-authentication-policy) during enrollment, including MFA for user and device authentication.

### **Device Configuration**

The technical controls that will be available, and that you can enforce, will vary depending on the devices that you use in your organization.

You will need to consider which device configuration polices you need to enforce and whether these are available in the MDM that you choose. You could develop a candidate configuration and see which MDM services are able to deploy that configuration.

### **Device Compliance and Monitoring**

MDMs can provide options for [monitoring of mobile devices](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) and reporting on device compliance. This can tell you things such as whether the device and applications are up to date, detect jailbreak or the presence of banned apps. Some MDMs also include more advanced reporting, using device attestation, which can provide stronger assertions of device compliance and device health.

If these features are available, and your authentication service supports it, they can be integrated with your authentication process to provide finer grained access policies. This would enable you to check for device compliance before allowing it to access your organizational data and applications.

### **Application Management and Data Isolation**

Some MDMs provide custom app store functionality. You can use this to ensure users only [install applications from an allowed](/bronze-training/mobile-device-guidance/using-third-party-applications) list, such as an enterprise application catalogue.

This will often be the preferred option where devices are fully managed, meaning corporately owned and business only (COBO) or corporately owned and personally enabled (COPE). If using a fully managed approach, it is important to consider support for [automatic updates](bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date) and the ability to [monitor and report](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) on the status of installed apps on mobile devices.

If using a [BYOD](/bronze-controls/byod-guidance) approach to device management, it may not be possible to enforce device wide restrictions. In this case, you should consider support for alternative approaches that combine both mobile device management (MDM) and [mobile application management (MAM)](https://en.wikipedia.org/wiki/Mobile_application_management). Together, this may provide isolation of work and personal apps and data and to protect against data loss if the device is lost or stolen.   

## Further considerations

Other desirable characteristics of MDM services are responsiveness and reliability. High responsiveness is essential in instances where policies must be rapidly applied, for example - wiping a device that has been lost or stolen. 

## How to choose an MDM service

When choosing and using a Mobile Device Management service, based on the considerations above, you should:

-   Select an MDM service that supports the devices and features you require, based on the technical approach that your organization uses. It should be noted that if using a [BYOD approach](/bronze-controls/byod-guidance), this may significantly limit the technical controls you are able to enforce and the features that are available.
-   If possible, pilot a range of MDM services and assess support for the devices and features that you require. You should also factor in accessibility, reliability and responsiveness during this pilot phase.
-   Choose an MDM service that provides automatic updates to the service itself and ensure that the MDM software is kept up to date.
-   Depending on whether you choose to deploy the MDM service completely on-premises or in the cloud using an IaaS or SaaS model, ensure that robust patching processes are in place to keep back-end infrastructure up to date. In an IaaS model, you have more responsibility for patching services yourself.
-   Prefer MDM services that use built in platform management features and integrate with existing app stores, as opposed to those requiring additional client-side agents.
-   If you are using an enterprise application catalogue, then this should support automatic application updates. These updates should be applied as soon as apps are updated in the public store.
-   Where possible, device configuration policies should be applied to reflect the BCSF platform specific guides for mobile platforms.
-   Device enrollment should support strong methods of authentication for users and devices for both [zero touch enrollment](/bronze-training/mobile-device-guidance/zero-touch-enrollment) and self-enrollment, including support for [multi-factor authentication (MFA)](/bronze-training/mobile-device-guidance/enterprise-authentication-policy).
-   Admin interfaces and user self service portals should have strong methods of [enterprise authentication](/bronze-training/mobile-device-guidance/enterprise-authentication-policy).
-   Choose an MDM service that supports [logging and monitoring](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) of devices. This should include the ability to configure appropriate device compliance policies to monitor the state of devices. If device attestation is supported, this can be used to provide stronger assertions on the state and health of devices.

## More information

For detailed guidance on how to securely use a particular MDM service, consult the documentation available from the service provider.

It may also be worth looking at [Common Criteria assessment](https://www.niap-ccevs.org/Profile/Info.cfm?PPID=428&id=428) reports of MDM services, and third-party reviews or guides of these services for more detailed information. Many MDM services provide trials so the service can be tested first.