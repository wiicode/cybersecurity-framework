---
title: iOS and iPadOS
description: Secure configuration and use of iOS and iPadOS devices
published: true
date: 2021-03-10T01:04:55.071Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-10T01:04:55.071Z
---

iOS is the operating system which powers the iPhone and iPod Touch. iPadOS is a very similar platform and the security considerations are identical to iOS, so this guide refers to both platforms as "iOS". Whilst this guide does not apply to any specific version of iOS, it was last tested on iOS 13.1 in October 2019.


# Securing iOS and iPadOS
## General recommendations
- Decide which iOS devices your organization will use. iOS devices typically receive software updates for around 5 years after first release. Once a device is vintage or obsolete, it no longer receives updates. At this point you should purchase newer devices.
- Devices should be supervised by your organization to ensure you have the most control over which policies to enforce on your devices.
- If possible, use Apple Business Manager (ABM) to supervise, enroll and provision devices using zero touch enrollment. This prevents users from un-enrolling devices, once deployed. Alternatively, use Apple Configurator to manually supervise devices before provisioning to enable more control.
- Once supervised, iOS devices should be managed using a Mobile Device Management service, to enforce technical controls.
- Also configure the logging and monitoring capabilities of the MDM.
- Use one of our recommended network architectures to enable remote access to enterprise services.
- If a virtual private network (VPN) is required, use the built-in IKEv2 VPN, as this provides a high-performance, always-on mode and strong cryptography.
- Third-party apps for work use ("managed apps") should be approved centrally into an enterprise app catalogue and delivered via MDM, to keep data separate from non-work apps.
- Consider your approach to enabling iCloud accounts on users' devices, using on-device policies to manage specific iCloud features.
- Antivirus and other security software are not normally required on iOS

## Work applications
Most organizations will want to offer their users a range of productivity and business applications so they can consume, create and collaborate remotely. We recommend the use of the built-in apps where possible (e.g. Mail and Calendar) as this gives you the most flexibility to subsequently open work attachments in any managed third-party applications, as well as optimising usability and performance. It also enables accounts to be managed by MDM, minimising administrative overheads.

If you are using third-party apps for work, we recommend using an enterprise application catalogue of approved apps that users can choose to install at will, delivered through MDM. Apps deployed in this way will be 'managed' apps and have access to work data. Apps installed through the App Store will be 'unmanaged' and will not have access to the same data. See our third-party applications guidance for more information on this approach.

We recommend that care is taken with high-privilege applications, such as third-party keyboard apps and network extensions. These types of application might be able to access large amounts of work data, so present a higher risk to your organization.

## Device configuration
Once you have chosen your MDM service, architecture and approach to applications, you should then develop a device configuration you can apply to enforce your technical controls.

In particular, you should include policies that manage:

- External interfaces, including wired and wireless peripherals (e.g. disabling USB accessories when the device is locked) 
- The use of biometrics, as well as passcodes and authentication policies
- The iCloud (and other cloud) services that you want to allow
- Device OS and application updates, including automatic updates
- Configure your device passcode policy to be in line with your organization's authentication policy
