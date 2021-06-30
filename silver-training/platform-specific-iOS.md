---
title: iOS 12
description: Secure configuration for iOS 12
published: true
date: 2021-06-02T22:02:30.050Z
tags: silver, sourced, silver-training
editor: markdown
dateCreated: 2021-02-22T00:25:28.184Z
---

> Secure configuration for iOS 12
{.is-info}


This guidance was developed following testing performed on an iPhone X running iOS 12.0.

It's important to remember that this guidance has been conceived as a way to satisfy the [12 End User Device Security Principles](/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview/eud-security-principles). As such, it consists of recommendations and should *not* be seen as a set of mandatory instructions requiring no further thought.

Risk owners and administrators should agree a configuration which balances business requirements, usability and security.


## Risk owners’ summary

### **We recommend the following architectural choices for iOS 12:**

-   All data should be routed over the native IKEv2 always-on VPN to ensure the confidentiality and integrity of traffic. This also allows the devices, and data on them, to be protected by your organization’s protective monitoring solutions.
-   Users should not be permitted to install arbitrary third-party applications on the device. Your organization’s application catalogue should be used to distribute in-house applications and suitable, assessed, third-party applications.
-   Unless your organization decides to use a particular third-party VPN, third-party VPN extensions should not be installed by users. Although VPN extension providers require entitlements to be granted by Apple when developing the extension, it may be possible that a malicious or poorly written VPN extension could be used to capture and log network traffic.

When configured in this way, risk owners should be aware of the following technical risks associated with this platform:

| **Security principle** | **Explanation of risks** |
| --- | --- |
| Assured data-at-rest protection | Applications can choose [classes of data encryption](https://www.apple.com/business/docs/iOS_Security_Guide.pdf) on a per-file basis. By default, only a limited number of files remain encrypted while the device is locked. This includes email and attachments (within the mail app), managed books and location data. Files belonging to other applications may not be encrypted when the device is locked, and could be extracted without knowledge of the password, if a suitable vulnerability were found in the platform.<br><br>Third-party applications are automatically opted in to the encryption class which protects their data when the device is in a powered-off state (but not when locked). This class protects data from attacks which require a reboot. Developers can then choose whether to opt out of this encryption class into a class which is always available, or opt in to the highest encryption class (encrypted when locked). |
| Platform integrity and application sandboxing | Sensitive data generated within one application may potentially be accessible to another if those applications are part of an app group. Application allow listing can help mitigate this. |
| Application allow listing | Not all classes of application extension respect managed to unmanaged application restrictions (e.g. a sharing extension may allow sensitive data to be shared to a social network).<br><br>To ensure it's not trivial to share managed documents outside of managed applications, administrators should pay particular attention to the extensions installed by allow listed applications. |
| Security policy enforcement | Policy settings applied through Apple Configurator cannot be overridden (when using recommended security settings). However, Mobile Device Management (MDM) profiles can be removed by the user (unless DEP is used - see below).<br><br>[Apple's Device Enrolment Program](http://www.apple.com/business/dep/) (DEP) can allow devices to be enrollled over-the-air during the device setup process. DEP can be used to limit the time a device is in a potentially hostile environment or configuration, and prevent removal of the MDM profile.<br><br>Custom keyboards should not be deployed via MDM. Keyboards deployed via MDM are considered managed and can then be used within other managed applications such as the mail app. If the user allows "full access" to the keyboard extension (which may be required for its correct operation), it is then not restricted from logging and sending keystrokes to external servers.<br><br>Procedural controls must be used to achieve some of the requirements where technical controls are not possible. This means that users have to be trusted not to alter certain settings on the device, or perform actions which may impact the security of the device. These controls are discussed in later sections. |
| External interface protection | Limited options exist to control radio interfaces such as Wi-Fi and Bluetooth.<br><br>iOS has MDM settings that allow the use of Wi-Fi to be restricted to networks deployed through the MDM. This could be used to restrict the attack surface of the device, but may limit legitimate functionality.<br><br>It is possible to restrict Bluetooth modification. This could be set to further reduce the attack surface, but would prevent legitimate functionality.<br><br>Enabling external interfaces means increasing the exposed attack surface, and data could be inadvertently or maliciously leaked without organization visibility. Therefore a risk based decision should be made to determine if this control is appropriate. |
| Event collection for enterprise analysis | There is no facility for collecting logs remotely from a device, and collecting forensic log information from a device is very difficult. |
| Incident response | iOS devices can be remotely locked, wiped, and reconfigured by their MDM. |

---

## Administrators’ deployment guide

### **Overview**

To meet the principles outlined in the [End User Devices Security Framework](https://www.gov.uk/government/publications/end-user-device-strategy-security-framework-and-controls), several recommendations are given in the table below.

| **Security Principle** | **Recommendation and Explanation** |
| --- | --- |
| Assured data-in-transit protection | The iOS native IKEv2 VPN client can be configured in an 'Always On' mode to guarantee all traffic is routed through your organizational infrastructure for inspection. This can protect data-in-transit and quickly switch between cellular and Wi-Fi networks.<br><br>Alternatively, you also have the option to use a third-party VPN supporting the VPN Extension Point API. These extensions should be installed from an allow list, if required by your organization. This minimizes the risk of a malicious or poorly-configured VPN extension finding its way onto a device. |
| Assured data-at-rest protection | iOS data protection is enabled by default. The Mail application uses Data Protection APIs to encrypt emails and attachments when the device is locked. By default, this level of protection also extends to location data and app launch images. Third-party developers need only request this protection class to gain its benefits. |
| Authentication | The user should be required to authenticate to the device in line with your organization’s authentication policy (see [Authentication Policy](/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview/authentication-policy)).<br><br>Authenticating to the device unlocks a key whichencryptscertificates and other credentials, giving access to the organization’s services.<br><br>Touch ID and Face ID permit biometric unlock of devices but the strength of its security is difficult to measure. In cases where there is a requirement to use biometric authentication, and the risks of using biometrics as the sole authentication mechanism are understood, Touch ID or Face ID can be enabled. |
| Secure boot | No configuration is required; this is provided by default. |
| Platform integrity and application sandboxing | No configuration is required; this is provided by default. |
| Application allow listing | You can establish an organizational application catalogue which permits users access to an approved list of applications developed in-house, and an approved list on the App Store.<br><br>Alternatively, the full App Store can be enabled, and Mobile Device Management(MDM) can be used toretrospectively monitor which applications a user has installed.<br><br>Extensions are installed along with a containing application, and cannot be installed alone. It is therefore possible to apply application allow listing rules that target these applications in order to restrict extensions.<br><br>Administrators should be aware of the extensions installed by their allow listed applications, to ensure that they do not introduce unexpected methods for sharing data outside of managed applications. It is not currently possible to define granular rules that block extensions, but permit the containing application (beyond implementation of managed/unmanaged application boundaries). |
| Malicious code detection and prevention | When configured as per this guidance, iOS will only be able to execute allow listed applications from the App Store or Enterprise App Catalogue. Apps in the App Store have been scanned by Apple and any malicious content found is removed. Therefore, there is little additional value to be gained from any third-party anti malware products on the platform. |
| Security policy enforcement | A combination of either Configurator+MDM or DEP+MDM should be used to configure users’ devices. Settings applied through Apple Configurator can be configured such that they cannot be removed by the user.<br><br>Policy applied through an MDM can be removed completely by an end user through removal of the Remote Management profile. This can be prevented if aDevice Enrolment Program (DEP)is used.<br><br>However, removing the Remote Management profile will also remove any data stored as part of accounts configured through MDM (e.g. email and credentials). When configuring an MDM, it should be configured such that:<br><br>(i) arbitrary devices cannot be enrollled,<br><br>(ii) end users are prevented from re-enrollling.<br><br>Users should not be allowed to directly re-enroll, as it may be possible for the user to affect the security of the device by:<br><br>(i) removing the MDM profile,<br><br>(ii) modifying the on-device configuration options,<br><br>(iii) re-enrollling the device through a self-service portal.<br><br>Apple's Device Enrolment Program should be considered to enable devices toregister with the MDM Server during the setup process, decreasing the risk of a compromised device enrollling.<br><br>Email accounts should be provisioned via MDM too, as only email accounts provisioned via MDM will operate correctly with restrictions to disallow opening documents in unmanaged applications ("Managed Open In"). This also means that if the MDM profile is removed, all credentials and data associated with that profile will also be removed. |
| External interface protection | The Configurator should be used to put the device into supervised mode, after which the user is only able to use the USB interface for charging their device.Technical controls can be used to restrict which Wi-Fi access points devices can connect to if required.<br><br>USB Restricted Mode should be used to minimize the attack surface from connected USB hosts and peripherals. |
| Device Update Policy | Users are free to update applications and firmware when they wish, though your organization can block this at the proxy server if desired. In addition, an MDM can be used to monitor the iOS versions currently installed and access could be revoked if necessary. |
| Event collection for enterprise analysis | iOS does not support remote or local historic event collection. Limited information regarding device state can be retrieved from the device. The features may depend on the MDM. |
| Incident Response | iOS devices can be locked, wiped, and configured remotely by their MDM. |

### **Recommended network architecture**

All remote or mobile working scenarios should use a typical remote access architecture with a VPN terminating into a DMZ.The following network diagram describes this set up.

![](/static-assets/images/iOS11%20image%201_0.png)

##### **IOS RECOMMENDED NETWORK ARCHITECTURE**

A Mobile Device Management server is required. macOS Server with Profile Manager is sufficient for this purpose. Alternatively, many third-party products exist which may offer additional functionality over and above Profile Manager.

---

## Preparation for deployment

The steps below should be followed to prepare your organizational infrastructure to host a deployment of these devices:

1.  Deploy macOS 10.14+ and [Apple Configurator 2.8](https://itunes.apple.com/gb/app/apple-configurator-2/id1037126344) onto a dedicated provisioning terminal.
2.  Procure, deploy and configure other network components, including an approved [IPsec VPN Gateway.](/static-assets/documents/CPA%20SC%20IPsec%20VPN%20Gateway%20v2-5.pdf)
3.  Set up the MDM and create policies for users and groups in accordance with the settings detailed later in this section.

### **Device provisioning steps**

The steps below should be followed to provision each end user device onto your organization’s network, preparing it for distribution to end users:

1.  Use Configurator 2 to supervise the iOS devices (this is necessary for the "supervised only" restrictions enforced via the MDM to be effective).
2.  Enrol the devices into the MDM deployed earlier and install the predefined configuration profile.
3.  Apply any additional, required security controls by using the Restrictions menu locally on the device.

Alternatively, devices can be purchased through the [Device Enrollment Program](http://www.apple.com/business/dep/) (DEP) which means that the devices will be supervised 'out of the box', and can be configured to automatically enrolll with the MDM server when first activated.

Devices that have not been purchased pre-enrollled into DEP can be enrollled post-purchase using Apple Configurator. This can be done when preparing the device to make it supervised. It should however be noted that users will have the option to opt-out of DEP for 30 days after the enrolllment is performed.

---

## Recommended policies and settings

This section details important security policy settings which are recommended for an iOS deployment. Other settings (e.g. server address) should be chosen according to the relevant network configuration.

Remember, any guidance points given here are recommendations - they are not mandatory. Risk owners and administrators should agree a configuration which balances business requirements, usability and the security of the platform. 

#### **Configurator settings**

In cases where Device Enrollment Program (DEP) is being used to enroll devices into the MDM server, this step can be omitted. In other cases, these settings should be applied to the device by creating profiles in the Configurator utility:

|     |     |
| --- | --- |
| General Group |     |
| Security (user can remove profile) | Never |
| Automatically Remove Profile | Never |
| Supervision | On  |
| Allow devices to connect to other Macs | No  |

If not using the always-on IKEv2 VPN, the Global HTTP Proxy settings should also be set to match the network configuration for when the device is connected to the VPN.

#### **MDM settings**

These settings should be applied to the device by creating profiles on the MDM server:

|     |     |
| --- | --- |
| Security & Privacy |     |
| Privacy: Allow sending diagnostic and usage data to Apple, and sharing crash data and statistics with app developers | No  |
| Restrictions Group |     |
| Allow installing apps using Apple Configurator and iTunes | No  |
| Allow screenshots and screen recording | No  |
| Allow installing configuration profiles (supervised devices only) | No  |
| Allow adding VPN Configurations (supervised devices only) | No  |
| Allow iCloud backup | No  |
| Allow iCloud documents & data | No  |
| Allow iCloud keychain | No  |
| Allow shared albums | No  |
| Allow iCloud Photos | No  |
| Allow backup of enterprise books | No  |
| Allow managed apps to store data in iCloud | No  |
| Allow Handoff | No  |
| Allow notes and highlights sync for enterprise books | No  |
| Force encrypted backups | Yes |
| Allow users to accept untrusted TLS certificates | No  |
| Allow Siri while device is locked | No  |
| Allow modifying account settings (supervised devices only) | No  |
| Allow documents from managed sources in unmanaged destinations | No  |
| Allow sending diagnostic and usage data to Apple | No  |
| Allow pairing with non-Configurator hosts (supervised devices only) | No  |
| Allow AirDrop (supervised devices only) | No  |
| Show Control Centre in Lock screen | No  |
| Show Today view in Lock screen | No  |
| Show Notification Centre in Lock screen | No  |
| Require TouchID/Face ID authentication for AutoFill | Yes |
| Allow password sharing | No  |
| Allow proximity based password sharing requests | No  |

If using Profile Manager, ensure that the option to sign configuration profiles is selected. Other MDMs may have a similar option which should be selected.

#### **On-device notifications menu**

To prevent sensitive data appearing on the lock screen, the following settings should be applied on each device:

|     |     |
| --- | --- |
| Configuration Rule | Recommended Setting |
| Show Previews | Never |

#### **On-device restrictions menu**

These settings should be applied on each device.

|     |     |
| --- | --- |
| Configuration Rule | Recommended Setting |
| Contacts - Don't allow changes | Enabled |
| Calendars - Don't allow changes | Enabled |
| Photos - Don't allow changes | As per organizational policy |
| Share My Location - Don't allow changes | Enabled |
| Bluetooth Sharing - Don't allow changes | Enabled |

Allowing changes to these restrictions will enable applications on the device to request access to the named data store. Any that are not required should be disabled.

To make the provisioning steps less onerous, the risks mitigated by these settings could also be met in other ways. Contacts, Calendars, Photos and Bluetooth permissions are only risky if third-party applications which use these permissions are installed on the device. Some users' locations may not be sensitive, in which case Location Services may be enabled.

But where the user's location *is* sensitive, Location Services should be disabled. In these scenarios, the use of the above restriction settings are not necessary.

#### **VPN profile**

The deployed VPN should be configured according to the [PRIME profile for IPSEC](/guidance/using-ipsec-protect-data).

The recommended IPsec cipher suite profile for protecting information is called PRIME. A non-authoritative summary is provided in the table below:

|     |     |
| --- | --- |
| IKEv2 | Selection |
| Encryption | AES-128 in GCM-128 (and optionally CBC) |
| Pseudo-random function | HMAC-SHA256 |
| Diffie-Hellman Group | 256bit random ECP (RFC5903) |
| Group 19 Authentication | ECDSA-256 with SHA256 on P-256 curve |

|     |     |
| --- | --- |
| ESP | Selection |
| Encryption | AES-128 in GCM-128 |

|     |     |
| --- | --- |
| VPN Settings | Value |
| Enable perfect forward secrecy | True |
| Enable certificate revocation check | True |
| VPN On Demand | Always |

The deployed VPN solution should be configured to negotiate the parameters below. Not all of these settings can be configured on the device or MDM VPN profile, therefore the configuration also needs to be enforced from the VPN server.

Note that for an iOS device to verify the VPN server certificate, the certificate must have a Subject Alternative Name (SAN) entry that matches the common name. Further information on the supported server configurations can be found at [http://help.apple.com/deployment/ios/](http://help.apple.com/deployment/ios/)

---

## Authentication policy

Your organization should have a consistent authentication policy which applies to all users and devices capable of accessing its data.You can use the published [password guidance](/collection/passwords?curPage=/collection/passwords/updating-your-approach) to help inform any password policy.

An administrator shouldconfigure therelevant on-devicesettingsin line with your authentication policy.

For further guidance on authentication policies, see the [BCSF EUD Authentication guidance](/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview/authentication-policy).

To enforce this policy on iOS devices, the following settings are available, and should be set according to the policy:

-   Allow simple value
-   Require alphanumeric value
-   Minimum passcode length
-   Minimum number of complex characters
-   Maximum Auto-Lock
-   Passcode history
-   Maximum grace period for device lock
-   Maximum number of failed attempts
-   Allow Touch ID / Face ID to unlock device

#### **Hardware strengthening**

All devices since the iPhone 5S have a Secure Enclave Processor (SEP) which handles secure storage of cryptographic keys. A successful authentication against the SEP is required to grant access to the device and its data. This prevents offline, brute force attacks against data-at-rest keys. Online brute-force attacks are also prevented by the SEP, which locks after 10 unsuccessful attempts.

#### **Biometrics**

iOS devices can useTouch IDor Face ID for biometric authentication which happens within the Secure Enclave Processor. This means that a physical attack on a locked device should not result in compromise of data.

The fingerprint reader has a 0.002% false acceptance rate for a random fingerprint, but there have beenpublished attackson the feature using artefacts taken from the device. No independent information on the security posture of the facial recognition capabilities has been published at present. Using such attacks, a targeted physical attack on a specific user could result in the attacker gaining access to the device. You should consider these limitations when devising an authentication policy which permits the use of biometrics.


## Other considerations

The following points are in addition to the common organization considerations, and contain specific issues for iOS deployments.

#### **Cloud integration**

iOS devices do not need to be associated with an Apple ID to operate as required within an organization. For example, it is still possible to receive push notifications, and to install organization applications without an associated account. In addition, in iOS 9 Apple has removed the need for an Apple ID when installing applications using the Volume Purchase Program (VPP), further reducing the requirement for each user to have a provisioned Apple ID.

If an Apple ID is used to enable iCloud services on the device, then documents and other sensitive data may be inadvertently synchronized with iCloud. As a mitigation, organizations that wish to prevent this should implement controls to prevent users from enabling unneeded iCloud services on their device, thereby preventing organization data from being synchronized with iCloud servers.

#### **App groups**

Apps and extensions that are produced by the same developer can potentially share content when configured as part of an 'app group'. Sensitive application data could therefore be made available to another application on the device, potentially being shared from managed to unmanaged applications. Third-party applications should be reviewed to identify membership of an app group, and appropriate allow listing should be applied where necessary.

#### **Unmarked email domains**

"Unmarked" email domains can be configured so that when a user is composing an email using the system email client, any email address entered which does not match the configured domains will be highlighted (marked) in red. Administrators should consider using this functionality, to warn users who may be inadvertently attempting to send sensitive information to untrusted email addresses.

#### **Managed Safari web domains**

A list of domains can be configured that the device will treat as "managed" in the Safari web browser. Documents downloaded from these domains are subject to “Managed Open In” rules and should not be accessible to unmanaged applications. Configuring these domains can help to stop sensitive documents from being shared to other applications.

#### **Lock screen widgets**

A widget is an extension which can display content or information provided by an application. On iOS 10+ a number of widgets are turned on by default and can expose information to the lock screen. In order to prevent data leakage via the lock screen, widgets can be disabled. This can be enforced via MDM policies. Unticking the “Show Today view in Lock screen” option prevents this behavior.

#### **Universal Clipboard**

Universal Clipboard allows sharing clipboard data between multiple devices registered on an iCloud account. Ensuring that handoff is disallowed in the MDM settings prevents the functionality of Universal Clipboard. As noted in the earlier section on iCloud integration, it is recommended that all iCloud settings are reviewed to ensure they are configured to prevent inadvertent synchronisation of data to iCloud.

#### **Control Centre and Notifications**

In its default configuration, Notification Center could expose information to the lock screen. To prevent data leakage via the lock screen, previews can be disabled via the on-device "Notifications" settings menu.

Additionally, the options within Control Centre to disable Wi-Fi and Bluetooth disconnect from any existing devices, but do not turn the radios off; which may cause issues in some environments. Guidance should therefore be issued to users instructing them to use the Settings app to disable Wi-Fi or Bluetooth if this is required.

#### **Require Touch ID/Face ID for ‘autofill passwords’**

A new restriction is available that will require a valid face to be presented to allow the autofill passwords function to work. However it should be noted that this does not take effect if there is no Touch ID/Face ID configured. As such, if this is enforced but no Touch ID/Face ID is configured, autofill passwords will still work. Currently there is no way to force users to configure Touch ID/Face ID.