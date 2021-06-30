---
title: Using biometrics
description: Advice for IT system administrators on using biometric authentication on smartphones, tablets, laptops and desktop PCs.
published: true
date: 2021-06-01T20:47:26.095Z
tags: guidance, bronze, bronze-training, mdm
editor: markdown
dateCreated: 2021-03-06T02:38:31.201Z
---

Biometrics are biological characteristics of an individual, such as face or fingerprint, which can be used to verify their identity.

Use of fingerprint or face recognition for device authentication is now commonplace on smartphones and tablets. It is also increasingly becoming available on laptops. This guidance will present the benefits of using biometrics while also highlighting potential security risks.


## Why use biometrics?

On mobile devices, authentication is the primary method for verifying a user’s identity and protecting against unauthorized access.

Use of biometrics on mobile devices is becoming increasingly common, as most recent smartphone models have at least one built-in mechanism for biometric authentication, most commonly face or fingerprint recognition. These can offer a secure and convenient alternative to passwords or PINs.

However, vulnerabilities do still exist in biometric systems, including spoofing of biometrics, or attacks against the systems and devices themselves.

This guidance will help organizations assess the benefits of using biometrics on mobile devices against potential security risks.


## Preparing for biometrics

The most common methods of biometric authentication on smartphones, tablets, PCs and laptops are face and fingerprint recognition. Other examples include iris, vein or voice recognition.

### **How do they work?**

Biometrics work in a slightly different way to something like a PIN or password. In the case of a PIN or a password, an access control system will compare the stored value with the one entered by an individual. If they are identical, access will be granted.

However, in the case of biometrics, no two captures of biometric data can produce truly identical results. So, verification of a user’s identity is not a simple comparison. Instead, biometric data captured at login is compared to the enrolllled biometric data, stored on the device. The system then *judges* whether these two biometrics are sufficiently similar to be the same person.

Stored samples are normally held in such a way that they cannot be reversed to reproduce the original face or fingerprint that was initially enrolllled.

### **What are the benefits?**

Biometric authentication on mobile devices can offer significant benefit.

Most users are already very familiar with biometric authentication for device unlock, so the system's ease of use will likely make uptake high.

Biometrics can also provide a secure alternative to passwords and in most cases are far more convenient than passwords, particularly on most modern smartphones.

On mobile devices, the device passcode is still required as a fallback. However, because passcodes will be entered far less often, organizations can enforce more complex passcodes without causing a huge dip in usability.

On some devices and operating systems, biometrics can replace passwords completely. [Windows Hello for Business](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-identity-verification), for example, allows use of biometrics to protect access to hardware protected cryptographic keys. This system provides passwordless multi-factor [enterprise authentication](/bronze-training/mobile-device-guidance/enterprise-authentication-policy) on Windows, to Active Directory or Azure Active Directory.

### **What are the risks?**

As with any authentication mechanism, biometrics can have vulnerabilities and common attack methods do exist. Some of the risks you should consider are as follows:

#### **Presentation attacks**

A presentation attack involves an attempt by an impostor, using an artefact of some kind, to impersonate a valid user. Modern mobile devices usually include additional protections, such as 'liveness' checks, to prevent this sort of attack from working. Additionally, only a small number of biometric authentication attempts are allowed before a PIN or password must entered, protecting against brute-force attack.

In some cases, weaknesses have been shown to exist in biometrics on smartphones. Examples include facial recognition not testing for alertness, making it possible for a device to be unlocked while a user is asleep, or has their eyes shut. You should research these weaknesses when choosing to use biometrics, or when [choosing which devices to use in your organization](/bronze-training/mobile-device-guidance/choosing-devices).

#### **Replay attacks**

If a biometric data sample can be captured or stolen from a device, it may be possible to replay it to authenticate to the device. Most modern devices are well protected against this type of attack.

#### **Fall back mechanisms**

Before a user can register a biometric on a mobile device, a PIN or password must be set. This will be used in situations where biometric authentication fails. The security of this mechanism and the security policies associated with it should be strong enough to protect the device by itself. Otherwise, attackers can force the device to fall back to this more easily guessed or forced alternative.

#### **Performance**

On most mobile devices today, the expected false acceptance rate is usually less than one in a thousand.

As an example, [Apple report](https://support.apple.com/en-gb/HT208108) the probability that a random person could unlock your iPhone or iPad using Face ID is less than 1 in 1,000,000. However, when assessing manufacturer published performance metrics, it should be noted that they are usually based on optimal testing conditions, so may not actually be achievable in real world conditions.

#### **Privacy**

Biometric data is classed as personally identifying information and therefore is subject to regulation, such as GDPR. On mobile devices, explicit consent to use biometrics must be gained since the user must choose to enrolll a biometric.

For the built-in biometric authentication features, the processing and capture of data is also usually performed entirely on the device. It will not, for example, be backed up to [built-in cloud services](/bronze-training/mobile-device-guidance/using-built-in-cloud-services) If you are using third-party apps that implement a separate biometric authentication step you should investigate how those biometric templates will be protected.


## How to use biometrics

Unless you have specific users with a particularly high physical attack risk, we recommend biometrics be enabled for users who wish to use them. More specifically, when using biometrics on mobile devices, you should:

-   Assess the security risks, privacy and performance of biometrics based on the considerations above. Manufacturer documentation can help with this, as well as researching any published vulnerabilities in the particular [device(s) you are intending to use](/bronze-training/mobile-device-guidance/choosing-devices).
-   Provide [guidance to your users](/bronze-training/mobile-device-guidance/advising-end-users) on the use of biometrics, security risks, and the associated security policy.
-   Where necessary and if possible, use [mobile device management (MDM)](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) to manage use of biometrics in line with your organization’s [authentication](/bronze-training/mobile-device-guidance/enterprise-authentication-policy) policy. More detailed guidance for particular operating systems can be found in the BCSF platform specific guidance..
-   Ensure appropriate fallback mechanisms, such as device PIN or device password, are configured and security policies enforced, if possible, using [MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services)