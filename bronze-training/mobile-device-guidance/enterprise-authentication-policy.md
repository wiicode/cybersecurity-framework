---
title: Enterprise authentication policy
description: Implementing effective authentication on smartphones, tablets, laptops and desktop PCs
published: false
date: 2021-06-02T20:14:34.353Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:52:59.274Z
---

Authentication is the process of verifying the identity of either a user or a device, before authorizing access to devices or services.

In each case, the authentication methods available will depend on what *service* is being accessed and from what *type of device*. Each authentication method will have its own strengths and weaknesses.

As an organization, it is important to implement authentication steps that balance both the usability and the security of your devices and services. This guidance will present a range of different use cases and the common authentication methods that are available, highlighting both the security benefits and security risks. This will help you to design and deploy an effective authentication policy for your organization's mobile devices.

## Why authenticate?

On mobile devices, user authentication is the main method for protecting against unauthorized access to devices and the data stored on them. It also plays an important part in protecting against unauthorized changes to device settings.

Given that most enterprise services will be accessed from mobile devices, it is important that:

-   The identity of the user of a mobile device be verified. This will ensure that only those people who are meant to have access are authorized.
-   If the service contains data you consider sensitive, the identity and health of a device should also be verified. This allows you to prevent devices that are not compliant with enterprise policy from accessing your services.

Attackers will always look to target weaknesses in authentication systems. Many common attacks look for simple ways to guess or steal user or device credentials.

With these credentials, attackers can impersonate valid users and devices, gaining access to data stored on devices, and connecting remotely enterprise services. They will also use this foothold to penetrate further into corporate networks.

Given these potential consequences, it should be clear that implementing effective authentication is essential for organizations wishing to protect against account, device or network compromise.

## Preparation for effective authentication

First and foremost, you need to consider the risks to the assets that you are trying to protect, the data they hold and the authentication use cases that you face. This information will allow you to formulate an appropriate policy for authenticating both users and devices, before granting access to systems and services.

For each authentication use case, you should consider both the usability and security of the available authentication methods.

### **Authentication use cases**

The main use cases to consider are:

-   **User to device** - The user is only granted access to the device after successfully authenticating to it.
-   **User to service** \- The user is only able to access enterprise services after successfully authenticating to the service, via their device.
-   **Device to service** - Only devices which can authenticate to the enterprise are granted access.

For each of the use cases above, when deciding on appropriate authentication mechanisms, it is important to consider which of the available authentication mechanisms are most appropriate to use, taking into account both security and usability.

### **User to device**

In the case of **user to device** authentication, common methods of authentication include:

| Authentication Method | Consideration |
| --- | --- |
| Passwords or PINs | On mobile devices, passwords or PINs are usually the primary method for user to device authentication. They do still suffer from the risks of being guessed or brute forced. However, most mobile devices include technology that strengthens user to device passwords or PINs against an offline *brute force* attack, limiting the ability of an attacker to repeatedly guess passwords or PINs.<br><br>In addition to these protections, if the the PIN or password is used only for authentication to the device, then knowledge of it is only useful if the attacker also has physical access to the device. |
| Biometrics | Many mobile devices now also have biometric authentication features such as fingerprint and face recognition. These can offer convenient and secure alternatives to passwords. Biometrics can vary in the false positive and negative rates they produce, and in their ability to detect a spoofed biometric. <br><br>We provide more detailed advice and recommendations in the separate [biometric guidance](/bronze-training/mobile-device-guidance/using-biometrics-on-mobile-devices). |

### **User to service / device to service**

In the case of **user to service** authentication and **device to service** authentication, common authentication methods include 

| Authentication Method | Consideration |
| --- | --- |
| Passwords | This is still by far the most common method used today for user to service authentication as passwords are relatively easy to implement. Passwords do suffer from some major weaknesses though.<br><br>Requiring users to remember and manage significant numbers of passwords often leads to [password reuse](/bronze-training/passwords/living-password-re-use), as well as use of common passwords that can make services vulnerable to [password spraying attacks](/bronze-training/passwords/spray-you-spray-me-defending-against-password-spraying-attacks), or brute forcing. They are also vulnerable to [phishing](/bronze-controls/phishing), spear-phishing, and server-side credential theft, as evidenced by many recent data breaches. <br><br>BCSF has extensive advice surrounding passwords, including password deny lists, setting a [password policy](/bronze-training/passwords/updating-your-approach) for your organization, and how to select an appropriately [secure password](/bronze-training/passwords/three-random-words-or-thinkrandom-0), that users should find easier to implement. |
| Certificates | These are long-term credentials which contain a private key and signed public key. Access to the private key is required to authenticate to other services and can be used to authenticate the device or the user to the service.<br><br>The private key should be protected from access by malicious software (via sandboxing or other access control mechanism, including marking it non-exportable). The private key should also be protected from hardware extraction by the device’s data-at-rest encryption, or a strong encryption password if it can’t be otherwise protected.<br><br>|
| FIDO 2 authenticators | [FIDO2](https://fidoalliance.org/fido2/) is a set of standards that provides cryptographic authentication using public-key credentials and protocols to provide more secure alternatives to passwords for accessing online services. It also mitigates many of the security risks associated with passwords, including phishing, credential theft and replay attacks.<br><br>[FIDO2](https://fidoalliance.org/fido2/) authenticators can be a smartphone, a hardware security key, or a trusted platform module (TPM) on a PC or laptop. Authenticators can support user to device verification, using a local PIN or biometric. This means that access to stored keys for authenticating to online services is only possible if user verification is first successful. Some authenticators provide further protection of stored keys using hardware protected cryptographic storage and anti-hammer, to protect against brute force attacks on local user verification. <br><br>[Windows Hello](https://fidoalliance.org/microsoft-achieves-fido2-certification-for-windows-hello/) and devices running [Android 7+](https://fidoalliance.org/android-now-fido2-certified-accelerating-global-migration-beyond-passwords/) are examples of FIDO2 certified platform authenticators. There is also a growing ecosystem of hardware security keys that support FIDO2, such as [Yubikeys](https://www.yubico.com/) or [Google Titan keys](https://cloud.google.com/titan-security-key/). <br><br>In enterprise scenarios for example, [Windows Hello for Business](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-overview) already makes use of FIDO2. It to requires use of a PIN or biometric (something you know/are) for user to device authentication, which allows access to public key based credentials, bound to the device's TPM (something you have). The allows users to authenticate to Windows Active Directory, or Azure Active Directory, and gain access to enterprise services. [Google accounts](https://support.google.com/accounts/answer/6103523?co=GENIE.Platform%3DDesktop&oco=1) also now support [external security keys and the built in authenticator on Android](https://support.google.com/accounts/answer/6103523?co=GENIE.Platform%3DDesktop&oco=1) devices as a second factor, when authenticating to a google account. |

### **Single factor vs Multi-factor Authentication for services**

The security of any authentication mechanism will depend on the specific implementation and combination of factors that are chosen.

In some scenarios, use of a single factor may be appropriate. For example, in the case of user to device authentication, use of a single factor to authenticate to the device may be enough when taking into account mitigations such as brute force protection or hardware protected storage, available on many of today's mobile devices.

For service level authentication though, in cases where a single factor of authentication does *not* provide an appropriate level of security, [multi-factor authentication (MFA)](/bronze-training/passwords/multi-factor-authentication-online-services) can significantly strengthen security..

Built-in device authentication mechanisms that can be extended to integrate directly with your chosen identity provider to provide both [passwordless](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/passwordless-strategy) and [multi-factor authentication](/bronze-training/passwords/multi-factor-authentication-online-services) using public key based credentials bound to the device can often provide the best balance of usability and security. A good example of this is [Windows Hello for Business](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-overview). Use of FIDO2 security keys may offer similar benefits where users have more than one device. However, you will need to investigate support for this on the devices and with your identity provider.

Some enterprise authentication services can also be integrated with [mobile device management (MDM)](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) to factor in environmental factors such as [network location](https://docs.microsoft.com/en-us/intune/protect/use-network-locations), [device compliance](https://docs.microsoft.com/en-us/intune/protect/device-compliance-get-started), and [device health attestation](https://docs.microsoft.com/en-us/windows/security/threat-protection/protect-high-value-assets-by-controlling-the-health-of-windows-10-based-devices#detect-unhealthy), before granting access to enterprise services. This type of [conditional access](https://docs.microsoft.com/en-us/intune/protect/conditional-access) can be extremely useful in [zero-trust network architectures](/bronze-training/mobile-device-guidance/infrastructure/network-architectures-for-remote-access) or [bring your own device (BYOD)](/bronze-training/mobile-device-guidance/bring-your-own-device) scenarios.

### **Single sign on to services**

Enterprise single sign on can be used to sign in to online services using the single source of identity managed through your chosen identity provider. This can significantly improve the user experience by reducing the number of times authentication is required and to reducing reliance on passwords. It also makes managing joiners, movers and leavers much simpler and less error prone.

### **Logging and monitoring**

In addition to authentication mechanisms, [appropriate logging should also be in place](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) to enable monitoring of authentication and access to devices and services. Attacks on authentication systems are amongst the most prevalent you'll face, so capturing these events into your audit logs is a highly effective way of detecting potential issues.


## How to authenticate effectively

When designing and implementing enterprise authentication, you should:

-   Choose an enterprise identity provider that supports [multi-factor authentication](/bronze-training/passwords/multi-factor-authentication-online-services) for both users *and* the devices your organization uses. Configure your online services to use single sign on authentication using your identity provider.
-   Choose authentication factors that maximise usability and provide appropriate security based on the considerations above and make sure that devices you use support them when [choosing what mobile devices to use in your organization](/bronze-training/mobile-device-guidance/choosing-devices).
-   Provide clear authentication policies and [guidance for users](/bronze-training/mobile-device-guidance/advising-end-users).
-   Implement pragmatic user to device authentication policies, including the use of [biometrics](/bronze-training/mobile-device-guidance/using-biometrics-on-mobile-devices) and [usable password policies](/bronze-training/passwords).
-   Where possible, reduce reliance on passwords and implement passwordless authentication, such as [Windows Hello](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/passwordless-strategy).
-   Where passwords are required for access to services, encourage use of [password managers](/bronze-training/passwords/password-managers).
-   For machine authentication, deploy mechanisms that use hardware-protected public key based credentials that are uniquely bound to the device. Consider, where possible, combining this with other context (e.g. on Windows you can use [network location](https://docs.microsoft.com/en-us/intune/protect/use-network-locations), [device compliance](https://docs.microsoft.com/en-us/intune/protect/device-compliance-get-started) and [device health attestation](https://docs.microsoft.com/en-us/windows/security/threat-protection/protect-high-value-assets-by-controlling-the-health-of-windows-10-based-devices#detect-unhealthy)). This is discussed more in the [zero trust networking](/bronze-training/mobile-device-guidance/infrastructure/network-architectures-for-remote-access) guidance.
-   Deploy enterprise single sign on for access to services. Combine this with strong user and device authentication, using [multi-factor authentication](/bronze-training/passwords/multi-factor-authentication-online-services) or [conditional access](https://docs.microsoft.com/en-us/intune/protect/conditional-access).
-   Implement appropriate [logging and monitoring](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) of authentication successes and failures.