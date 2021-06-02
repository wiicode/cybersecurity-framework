---
title: macOS 10.14 Mojave
description: Secure configuration for macOS 10.14 Mojave
published: true
date: 2021-06-02T22:02:55.278Z
tags: silver, sourced, silver-training
editor: markdown
dateCreated: 2021-02-22T00:24:14.551Z
---

# macOS 10.14 Mojave

Secure configuration for macOS 10.14 Mojave

This guidance was developed following testing performed on MacBook Pro and MacBook Air devices running macOS 10.14 (Mojave)

It's important to remember that this guidance has been conceived as a way to satisfy the [12 End User Device Security Principles](https://www.ncsc.gov.uk/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview/eud-security-principles). As such, it consists of recommendations and should not be seen as a set of mandatory instructions requiring no further thought.

Risk owners and administrators should agree a configuration which balances business requirements, usability and security.

---

## Risk owners' summary

We recommend the following architectural choices for macOS 10.14 as part of a remote working scenario:

-   All data should be routed over a secure enterprise VPN to ensure the confidentiality and integrity of the traffic, and to benefit from enterprise protective monitoring solutions.
-   User accounts should be created locally on macOS devices and managed remotely using Mobile Device Management (MDM).
-   Users should not be permitted to install arbitrary third-party applications on the device. Applications which users require should be pre-installed, provisioned as part of the device image, or installed using MDM.

When configured in this way, risk owners should be aware of the following technical risks associated with this platform:

| **Security principle** | **Explanation of risks** |
| --- | --- |
| Data-in-transit protection | The built-in VPN cannot be configured into an 'always-on' mode. Whilst triggers can be used to cause the VPN to connect regularly, users can disable these triggers and disconnect the VPN. Without a supported always-on mode, there is a risk that data in transit can be compromised. |
| Data-at-rest protection | On devices **without** a [T2 security processor](https://support.apple.com/en-gb/HT208862), FileVault 2 does not use any dedicated hardware to protect its keys. If an attacker can get physical access to the device, they can extract password hashes and perform an offline brute-force attack to recover the encryption password. As a result, passwords need to be much stronger to reduce this risk. |
| Secure boot | On devices **without** a [T2 security processor](https://support.apple.com/en-gb/HT208862), secure boot is not supported, making it easier for malware or a physical attacker to compromise the boot process and for such a compromise to be undetectable. |
| External interface protection | Most macOS devices have external interfaces which permit Direct Memory Access (DMA) from connected peripherals. Whilst the configuration in this section limits DMA to times when the user is logged in and the screen is unlocked, this still presents an opportunity for a local attacker to extract keys and data. |
| Device update policy | You cannot force the user to update their device or software remotely. However, it is possible to turn on automatic updates locally. Third-party utilities may be available that can mitigate this issue. |

---

## Administrators' deployment guide

### **Overview**

To meet the principles outlined in the [End User Devices Security Framework](https://www.gov.uk/government/publications/end-user-device-strategy-security-framework-and-controls), several recommendations are given in the table below.

|     |     |
| --- | --- |
| **Security Principle** | **Recommendation and Explanation** |
| Data-in-transit protection | Use a Foundation Grade IPsec VPN client configured as per that product's security procedures to provide data-in-transit protection, or the native IPsec VPN client. |
| Data-at-rest protection | Use FileVault 2 to provide full-volume encryption. As the disk encryption password on non-T2 devices is not tied to hardware, it needs to be strong enough to resist an offline brute-force attack. The required strength should be determined by your organisation’s authentication policy. Use *recovery key escrow* to store encrypted copies of device recovery keys for occasions when users forget their disk encryption passwords.<br><br>[Some MacBook Pro and Mac Pro devices](https://support.apple.com/en-gb/HT208862) from late 2017 and newer have a T2 security processor. The T2 processor is used to strengthen user authentication to the device by preventing brute force and physical attacks. No action is required to enable this behaviour on these devices. |
| Authentication | On devices **without** a [T2 security processor](https://support.apple.com/en-gb/HT208862), either:<br><br>-   Users have two passwords – one for FileVault 2, and one to login and unlock their device (see Provisioning Steps for how to achieve this)<br>-   Or users have one password which fulfills both requirements.<br><br>The user should be required to authenticate to the device in line with your organisation’s authentication policy (see Authentication Policy).<br><br>This user’s login password derives a key which encrypts certificates and other credentials, giving access to organisational services.<br><br>[Some MacBook Pro and Mac Pro devices](https://support.apple.com/en-gb/HT208862) from late 2017 and newer have a T2 security processor, which is used to provide brute-force and physical attack protection for cryptographic keys. As a result, devices with a T2 processor can use much shorter login passcodes at no additional risk. Having a separate disk encryption passcode is not necessary. |
| Secure boot | Set an EFI (firmware) password to make it more difficult for an attacker to modify the boot process. However, with physical access to a device without a T2 processor, the boot process can still be compromised. |
| Platform integrity and application sandboxing | System Integrity Protection (SIP) prevents users and applications from modifying files in several high-level directories. This feature is enabled by default in the OS and no user configuration is required. |
| Application allow listing | Use the MDM to allow list default macOS applications. Use GateKeeper to prevent the installation and running of unsigned applications. An organisation application catalogue can also be used which only contains enterprise-approved or in-house applications. These should be verified to have valid Developer ID certificates, apps should have been properly [notarised](https://www.ncsc.gov.uk/collection/end-user-device-security/platform-specific-guidance/macos-10-14#notarised). |
| Malicious code detection and prevention | XProtect is built into macOS. It has a limited signature set which is maintained by Apple to detect widespread malware. XProtect will also restrict vulnerable plugin versions (such as Java) to limit exposure. Several third-party anti-malware products also exist, which attempt to detect malicious code for this platform. Content-based attacks can be filtered by scanning capabilities in the organisation.<br><br>Further protection can be achieved by forcing apps to be **notarised**. A notarised app has been approved and confirmed by Apple that it does not contain malware. It also makes it easy for Apple to revoke any specific application if it subsequently found to be compromised after installation. |
| Security policy enforcement | Mark MDM profiles as non-removable so the user cannot remove them and alter their configuration. |
| External interface protection | USB removable media can be blocked through MDM if required. If an EFI password is set, DMA is only possible when the device is booted and unlocked. |
| Device Update Policy | MDM can be used to audit which App Store software and OS versions are installed on a device. The attached script will turn on automatic updates, but this cannot be achieved remotely with MDM. |
| Event collection for enterprise analysis | macOS logs can be viewed by a local administrator on device, or from a distance using remote administration tools. Third-party software can also be used to automate log collection. |
| Incident Response | macOS devices can be locked, wiped, and configured remotely by their MDM. |

**Recommended network architecture**

All remote or mobile working scenarios should use a typical remote access architecture with a VPN terminating into an access layer (or DMZ). The following network diagram describes the recommended architecture for this platform.

![](https://www.ncsc.gov.uk/static-assets/images/macos1013.png)

A Mobile Device Management server is required. Apple's macOS Server Profile Manager is sufficient for this purpose. Alternatively, third-party products exist which may offer additional functionality over and above Profile Manager.

---

## Preparation for deployment

The steps below should be followed to prepare your organisation's infrastructure for hosting a deployment of these devices:

-   Set up an MDM server (e.g. Profile Manager on macOS Server). This may require setting up the Open Directory component of a macOS Server.
-   Ensure all Configuration Profiles are signed to prevent modification in transit, or post install
-   Create policies on Profile Manager for:
    -   Ensure 'Use SSL' is selected for all server settings
    -   VPN
    -   Passcode
    -   Disk encryption and key escrow
    -   Exchange/Mail/Calendar Settings.
    -   Disabling access to the Preference Panes in Restrictions (macOS) for iCloud and Network as access to these could be used to disable the VPN.

See the [Recommended Policies and Settings](https://www.ncsc.gov.uk/collection/end-user-device-security/platform-specific-guidance/macos-10-14#policies) section for more detail on the above.

You can also consider creating policies in other sections of Profile Manager. In particular, we recommend that administrators:

-   Allow list applications to further reduce the risk of malicious code being executed
-   Tighten permissions on USB mass storage and optical devices to help prevent data loss through removable media
-   Use Restrictions to deny list locations from which users should not run applications, or allow list trusted applications that users are allowed to run
-   Include internal CA Certificates where appropriate to ensure users can authenticate network services
-   Include corporate network profiles (e.g. 802.1X or Wi-Fi) to ensure that network access credentials are distributed securely

**Device provisioning steps**

Follow these steps to provision each end user device onto your organisation’s network in preparation for distribution to end users.

These instructions assume the device is new or the operating system has been wiped and reinstalled.

1.  On first boot, the device will present a number of prompts. In these prompts:
    -   Firstly, create a local Administrator account. This will be used to locally manage the device. Credentials should not be given to the end user. A strong password should be entered at this stage.
    -   Secondly, skip the Apple ID creation and entry.
    -   Location Services can be enabled if required.
    -   The device can be registered with Apple if required.  
         
2.  Local settings should now be set. A script is provided to automatically provision these settings, but they can also be configured manually.
    -   Disable any non-required services (e.g.infrared)
    -   Enable low-overhead security features (e.g. firewall, updates)
    -   Set user security policies (e.g. timeouts, screen lock, password hints)
    -   Create a standard user account
    -   Make the user's home folder accessible only to that user
    -   Lock down the user's Terminal/Shell access. The user should have a limited Bash profile, which can be set as part of .bash\_profile. This file should be owned by the root user so that modifications cannot be made. The user's PATH should be set to a folder in the user's directory and required applications symlinked to this directory
    -   If MDM policies are not used to enforce FileVault and key escrow, manually configure disk encryption on the device. Either:
        -   Create a separate Disk Encryption user which will have a strong password used to decrypt the disk.
            -   Only give the Disk Encryption user access to decrypt the disk
            -   Part of this password could be from a password entry token such as a YubiKey
        -   Allow the primary user to unlock the disk using their login passcode.
    -   Turn on automatic updates via System Preferences -> Software Update settings
    -   Turn off initial iCloud login prompt for first user login. This will stop the user being prompted to use iCloud.
    -   To help prevent DMA and cold-boot attacks, set a Firmware Password  
         
3.  The device should now be enrolled with the MDM server and the configuration profiles applied, including those to enforce FileVault and key escrow if not set locally
4.  At this stage, any additional third-party applications can be installed (e.g. productivity apps)
5.  Distribute the device, disk encryption password and user password separately to the user
6.  The user should then change their password and skip the Apple ID registration step at the next time they log on

  
**Device imaging**

Instead of provisioning each device individually, an alternative option is to produce a master device image which can be deployed onto devices. The recommended approach for creating a standard disk image is to install the OS, create a local admin account and apply local policies, then install any required applications on a client machine.

The client machine is then connected to an imaging server in target disk mode. Apple's System Image Utility can then be used to create a NetRestore or NetBoot image of the device. The image can then be used to provision other machines. NetBoot images can also be created from macOS installers downloaded from Apple, though care should be taken to ensure that the version downloaded can be deployed on the specific hardware you are using.

*Note*

Enabling FileVault 2 and MDM enrolment must only be done after the device has been imaged. This ensures that the cryptographic keys involved in these security features are unique. This, however, can be achieved during MDM enrolment using options under the 'FileVault' tab within the 'Security and Privacy' submenu, including the configuration of recovery key escrow.

Apple's website has a support article that contains details about [creating images for device-specific versions of macOS](http://support.apple.com/kb/HT5599).

---

## Recommended policies and settings

This section details important security policy settings which are recommended for a macOS deployment. Other settings (e.g. server address etc.) should be chosen according to the relevant network configuration. These settings should be applied through a profile (or combination of profiles) created on the MDM server.

The settings below are named as they appear in Apple Configurator and Profile Manager. Other products may use different names for these settings.

|     |     |
| --- | --- |
| **General Group** |     |
| Automatic Push | Yes |
| Security (when can profile be removed) | Never |
| Automatic profile removal | Never |
| **Mail/Exchange/Calendar Groups (as appropriate)** |     |
| Allow messages to be moved | No  |
| Use Only in Mail | Yes |
| Use SSL (for internal and external host) | Yes |
| **VPN Group (if using the native VPN client)** |     |
| Connection Type | IKEv2 |
| Machine Authentication | Certificate |
| Enable VPN on Demand | Yes |
| **Restrictions Group** |     |
| Restrict which system preferences are enabled | Yes<br><br>Profiles, Sharing and iCloud should be disallowed. Other panes may be disabled at the organisation's discretion. |
| Allow use of Game Center | No  |
| Allow App Store app adoption | No  |
| Restrict App Store to MDM installed apps and software updates | Yes |
| Restrict which apps are allowed to launch | Yes<br><br>Add a list of approved applications permitted by the business |
| Allow only the following Dashboard widgets to run | Yes  <br>Do not add any widgets. This will stop any widgets from being able to access the Dashboard. |
| Allow use of iCloud password for local accounts | No  |
| Allow iCloud documents & data | No  |
| Allow iCloud Keychain | No  |
| Allow iCloud Mail | No  |
| Allow iCloud Contacts | No  |
| Allow iCloud Calendars | No  |
| Allow iCloud Reminders | No  |
| Allow iCloud Bookmarks | No  |
| Allow iCloud Notes | No  |
| **Security & Privacy Group** |     |
| Do not allow user to override Gatekeeper setting | Yes |
| Allow user to unlock the Mac using an Apple Watch | No  |
| Send diagnostic and usage data to Apple | No  |

The media access settings can be used to limit user access to removable media such as USB drives, writeable optical media and AirDrop.

---

## Authentication policy

Your organisation should have a consistent authentication policy which applies to all users and devices capable of accessing its data. You can use the [NCSC's published password guidance](https://www.ncsc.gov.uk/collection/passwords) to help inform any password policy. An administrator should configure the relevant on-device settings in line with your authentication policy.

For further guidance on defining an authentication policy, see [the EUD Security Guidance introduction](https://www.ncsc.gov.uk/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview).

To enforce this policy on macOS devices, the following settings are available, and should be set according to the policy:

-   Allow simple value
-   Require alpha-numeric value
-   Minimum passcode length
-   Minimum number of complex characters
-   Maximum Auto-Lock
-   Maximum number of failed attempts

**Hardware strengthening**

On macOS devices *without* a T2 processor, passwords for FileVault 2 are not strengthened using hardware. As such, it must be sufficiently complex to prevent offline brute force attacks. Account login attempts are limited by policy, so user account passwords need to be strong enough to resist manual guessing attempts. If one password is used for both FileVault 2 and account login, it should be sufficiently complex to prevent offline brute force attacks.

For devices *with* a T2 processor, the login password cannot be brute forced offline or extracted with a physical attack, so only needs to resist simple guessing attacks.

**VPN profile**

The deployed VPN should be configured according to [NCSC PRIME profile for IPsec](https://www.ncsc.gov.uk/guidance/using-ipsec-protect-data).

The recommended IPsec cipher suite profile for protecting information is called PRIME. A non-authoritative summary is provided in the table below:

Encryption

AES-128 in GCM-128 (and optionally CBC)

| **IKEv2** | **Selection** |
| --- | --- |
| Pseudo-random function | HMAC-SHA256 |
| Diffie-Hellman Group | 256bit random ECP (RFC5903) |
| Group 19 Authentication | ECDSA-256 with SHA256 on P-256 curve |

| **ESP** | **Selection** |
| --- | --- |
| Encryption | AES-128 in GCM-128 |

|     |     |
| --- | --- |
| **VPN Settings** | **Value** |
| Dead peer detection interval | Medium |
| Enable perfect forward secrecy | True |
| Disable redirects | False |
| Disable mobility and multihoming | True |
| Enable certificate revocation check | True |
| VPN On Demand | Always |

The deployed VPN solution should be configured to negotiate the parameters below. Not all of these settings can be configured on the device or MDM VPN profile, therefore the configuration also needs to be enforced from the VPN server.

In OS X 10.9, the mechanism for configuring the *VPN On Demand* settings changed, and none of the tested MDM utilities currently have a GUI for this new mechanism. To configure the *VPN On Demand* to trigger for all outgoing connections, follow the steps below:

-   Configure the VPN settings using the MDM and test the profile on the device to ensure it connects manually
-   Export the VPN configuration profile (unsigned) from the MDM as a .mobileconfig file. Convert this to text using \`plutil\` if required.
-   Using a text editor, modify the XML configuration inside the exported file. Within the IKEv2 key, add rules for OnDemandEnabled & OnDemandRules as shown below:

IKEv2

OnDemandEnabled

1

OnDemandRules

Action

Connect

-   Import the modified configuration to the MDM and deploy to the device

In Profile Manager, it is possible to set the option 'Always on VPN (supervised only)'. However, this causes the profile install to fail on macOS devices, so the approach described above should be used instead. Note also that for a macOS device to successfully verify the VPN server certificate, the certificate must have a Subject Alternative Name (SAN) entry that matches the common name.

---

## Other considerations

The following additional points address issues specific to macOS deployments.

**iCloud**

We recommend that users do not use iCloud as this may allow data to leak through iCloud backup and application storage. This can be achieved by not signing into the Apple ID when prompted by the operating system. Other Apple applications such as iTunes can be used with an Apple ID without enabling iCloud integration if they are required.

**FileVault**

In order for the enterprise to retain the ability to access the device in the event the FileVault 2 encryption password is lost, it should be ensured that the local administrator user has permission to unlock the FileVault encryption. This option is available within the Security & Privacy section of System Settings, under FileVault with the option to escrow recovery keys set under the 'Escrow Personal Recovery Key' option.

If key escrow is not possible or multiple versions of macOS need to be supported, a keychain can also be created by setting a Master Password (from the Users & Groups service menu). This keychain can be distributed to all managed macOS devices before enabling FileVault and will be acknowledged during the process of enabling FileVault. [Apple support has more information on this process](http://support.apple.com/kb/ht5077).

**Extensions**

In OS X 10.10, the extension feature was added. This allows application developers to extend the functionality of their application to third parties. As an example, the sharing extension could allow a user to share information to social network sites from an application.

Your organisation should control which applications are installed in the environment and limit the ability for applications to interface to the user via Extensions. This can partially be configured as part of your organisation's MDM solution.

**Firewall Configuration**

The Security & Privacy options allow additional configuration of the firewall. MDM policies can be used to give finer grained control over firewall rules on the system, if required. As an example, a policy can be enabled to block all incoming connections to the device.