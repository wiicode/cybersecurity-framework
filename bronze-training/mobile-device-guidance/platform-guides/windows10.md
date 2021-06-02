---
title: Securing Windows10
description: 
published: true
date: 2021-06-02T21:05:13.920Z
tags: bronze, bronze-training, security-operations
editor: markdown
dateCreated: 2021-01-08T05:21:01.224Z
---

# Windows 10

Security guidance for organisations on the secure configuration of Windows 10.

Whilst this guide does not apply to any specific version of Windows, it was last tested on Windows 10 2004 Enterprise Edition, which has more features available than some [other versions of Windows 10](https://www.microsoft.com/en-gb/windowsforbusiness/compare).

## Securing Windows 10

There are a number of configuration options which you can use to secure this platform within your organisation. However, we specifically recommend you implement technical and procedural controls relating to the following areas.

### General recommendations

-   Decide which Windows 10 devices your organisation will use:
-   Devices with hardware requirements to enable features such as Virtualization-Based Security and full disk encryption are preferred.
-   Windows 10 devices typically receive software updates multiple times a year, with major updates twice a year. We recommend keeping devices as up to date as your organisation allows. Microsoft's [Windows lifecycle fact sheet](https://support.microsoft.com/en-gb/help/13853/windows-lifecycle-fact-sheet) can help you plan upgrades to keep your organisation using supported versions.
-   Use one of the recommended network architectures to enable remote access to enterprise services.
-   Use a Mobile Device Management service to configure, monitor and enforce technical controls on your Windows 10 devices. Enable any logging and monitoring features.
-   If you are moving from on-premises only to include cloud, a hybrid network deployment is recommended initially. This can be done using [Azure Connect](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/whatis-azure-ad-connect). Some [help on hybrid architecture](https://docs.microsoft.com/en-us/learn/modules/design-a-hybrid-network-architecture/) can be found on the Microsoft website.
-   Use [Windows Autopilot](https://docs.microsoft.com/en-us/windows/deployment/windows-autopilot/windows-autopilot) to enrol and provision devices via zero touch enrolment with a trusted Windows 10 base image. Provision non-administrative accounts during setup, removing the need for local admin accounts.
-   Configure [Windows Defender](https://www.microsoft.com/en-gb/windows/comprehensive-security) to help protect against malicious software.If you wish to use a 3rd party Antivirus, we’d recommend one that uses [cloud detection](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus) and hooks into the [Anti-Malware Scan Interface (AMSI)](https://docs.microsoft.com/en-us/windows/win32/amsi/antimalware-scan-interface-portal).
-   Cameras are enabled to allow for [Windows Hello](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-overview) and video conferencing. However, this may not be appropriate for your specific deployment environment - in which case these features should be disabled.
-   Disable Microsoft Office macros, if this is not possible then only allow macros for specific apps or users where absolutely required. See macro security for Microsoft Office for further guidance.

### Device configuration

Once you have chosen your MDM service, architecture and approach to applications, you should then develop a device configuration profile, which can be used to enforce your technical controls.

You should include policies which cover the following:

-   The use of biometrics, as well as passcodes and authentication using Windows Hello for Business.
-   For devices without a TPM, we advise using a [modern authentication standard](https://docs.microsoft.com/en-us/office365/enterprise/hybrid-modern-auth-overview#what-is-modern-authentication).
-   Configuration of [BitLocker encryption](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-overview) settings to prevent data extraction using physical attacks. Using a TPM with PIN and Full Disk Encryption is recommended.
-   External interface protection, including wired and wireless peripherals. Use Direct Memory Access protections, such as ensuring new Direct Memory Access capable devices cannot be enumerated when the device is locked.
-   Automatic updates to your operating system and applications, along with firmware and drivers where applicable. We recommend configuring [Windows Update for Business](https://docs.microsoft.com/en-us/windows/deployment/update/waas-configure-wufb) to enable this.
-   The built-in Always on, IKEv2 virtual private network (VPN) (if a VPN is required), along with the use of hardware-backed storage for VPN credentials, through Windows Hello for Business, or the use of [Windows Key Attestation](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/manage/component-updates/tpm-key-attestation).
-   We recommend configuring the [Windows 10 Built-In VPN Client](https://docs.microsoft.com/en-us/windows/security/identity-protection/vpn/vpn-connection-type) configured as per customisation guide, available for public sector organisations by contacting NCSC enquiries (this archive also includes the NCSC Captive Portal Helper app for always-on VPNs).
-   If using a 3rd party VPN, configure in line with the NCSC's IPsec Guidance or TLS Guidance and following our platform independent guidance on VPNs.
-   AppLocker to help defend against malware and ransomware - a recommended sample configuration is provided in the configuration pack. Additionally, you should include policies that manage third-party apps for work use from an enterprise app catalogue, delivered via MDM, through a private store.
-   The security of Cloud accounts on users' devices, by using conditional access to control access to the sensitive features and services that are required by your organisation.
-   Removal of Internet Explorer. However, if you want to utilise Windows Defender Application Guard, Internet Explorer is a [requirement](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-guard/reqs-wd-app-guard). 
-   Configuration of Windows Defender Firewall to help reduce unwanted connections on Private/Public networks. By default, block outbound traffic on these networks, adding rules to allow specific exceptions for the services and protocols your organisation requires.