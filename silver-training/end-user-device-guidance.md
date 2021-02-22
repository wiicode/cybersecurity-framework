---
title: End user device (EUD) security guidance
description: Guidance for organisations deploying a range of end user device platforms as part of a remote working solution
published: true
date: 2021-02-22T00:05:36.507Z
tags: silver, silver training, device management
editor: markdown
dateCreated: 2021-02-22T00:05:36.507Z
---

# Introduction
Modern smartphones, laptops and tablets provide users with great flexibility and functionality, and include security technologies to help protect information.

This security guidance is general to all End User Device (EUD) deployments and aims to help organisations harness these security technologies in a way that does not significantly reduce their functionality.

# Who is this guidance for?
This guidance is for any organisation wishing to secure the EUDs they use, but it is primarily to help system administrators make informed decisions about the configuration, management and use of EUDs, and risk owners understand the overall risk to their networks presented by their use.

# What does this guidance do?
It builds upon the most important elements of the strategic goals described in 

make optimum use of native security functions, avoiding third-party products wherever possible

- allow greater user responsibility to reduce security complexity, maintaining user experience for the majority of responsible users
- logging and audit preferred over prevention and control, to maintain user experience and flexibility for the majority of responsible users
- enable greater interoprability of IT systems through a more common and consistent approach to securing information

# Platform-specific advice
There are also guidance documents for specific platforms (we'll put a collection link in here). Each platform we provide guidance for has been considered as part of a remote working deployment to see how effectively it is able to protect information. The guidance is not simply about applying settings to a device, but is also about making informed network architecture decisions; providing appropriate guidance and training for users; and performing operational maintenance, monitoring and defence of the network.

System Administrators may also use this guidance as a starting point for other security configurations for different devices such as desktops and servers. Consideration should be given to how applicable the recommendations are to their particular scenario and the guidance customised accordingly.

# Assumptions
- devices are corporately-managed and issued to users individually
- only a single user account will be present on each device. Multi-user devices are not addressed in this guide.
- devices will be used to access corporate services (email, calendar, collaboration tools...) both in and out of the office. 
- the devices will be used to access various Internet-based services, both for work and some personal use
- users will be made aware of the appropriate use of the system prior to receiving the device
- some devices will inevitably be lost or stolen (though precautions in this guidance should help ensure that data loss is minimised)
- devices will connect to a range of networks. Not just those provided by the organisation itself
- networks to which the device connects will not necessarily be trustworthy, so protection of the data in transit on these networks is important
- devices will be deprovisioned when no longer used for their original purpose.

# Cautions
Although devices are expected to be corporately managed, the ownership model is not particularly relevant here. The critical aspect is that your administrators take over the management of the device via a provisioning process and are able to control all relevant aspects of it throughout the time it accesses your organisation’s data.

Since we assume only a single user account, you will need to think about customising the configurations given here if dealing with multi-user scenarios.

We recommend that you carefully consider the risks from allowing EUDs into high-security locations. This guidance doesn't cover the use of these devices in that type of environment.

# How to get the most from this guidance
1. Read the guidance for your selected device(s) in full. 
1. Consider how applicable the usage scenario and recommendations are for your intended use.
1. Set up a pilot of devices in a non-operational environment before deployment. 
1. Try to simulate the environment where the devices will be deployed.
1. Determine the business functions that devices need to perform before deciding on theconfiguration. 
1. Apply security configurations to the device or supporting infrastructure where applicable.
1. Produce security operating procedures, user education packages and training documents. 
1. This will help your staff to keep information secure on mobile devices.
1. Establish a helpdesk facility to respond to the loss or theft of devices. 
1. Remotely lock or wipe devices, and revoke their ability to access your organisation's information.
1. Prepare a system management plan to deal with security critical updates and patches.
1. Updates will be released by the vendor throughout the lifecycle of the deployment.
1. Regularly iterate your design, architecture and configuration.
1. Base any changes on your experience of using and managing the network.


# EUD Security principles
> These principles provide the basis for our guidance on the configuration of specific EUDs.
{.is-info}

The EUD Security Framework describes twelve principles for securing devices, all of which must be considered when deploying a particular solution.

| Principle | Description |
| --------- | ----------- |
| Data-in-transit protection | Data should be protected as it transits from the EUD to any services the EUD uses. IPsec VPNs provide the most standards-compliant way of doing this, but TLS VPNs or per-app TLS connections can also be used. Formal assurance of this function to Foundation Grade against the appropriate Security Characteristic is strongly recommended. |
| Data-at-rest protection | Data stored on the device should be satisfactorily encrypted when the device is in its “rest” state. For always-­on devices like smartphones, this is when the device is locked. Formal assurance of this function to Foundation Grade against the appropriate Security Characteristic is strongly recommended. |
| Authentication | Each of the three types of authentication described here should be considered - User to device: the user is only granted access to the device after successfully authenticating to the device. - User to service: The user is only able to access enterprise services after successfully authenticating to the service, via their device. - Device to service: Only devices which can authenticate to the enterprise are granted access. - Each stage of the authentication process should be designed to complement the others, as part of your organisation’s authentication policy. Further guidance on devising an authentication policy can be found in this collection. |
| Secure boot | An unauthorised entity should not be able to modify the boot process of a device, and any attempt to do so should be detected. |
| Platform integrity and application sandboxing | The device can continue to operate securely despite potential compromise of an application or component within the platform, and you have the ability to restrict the capabilities of applications on the device. |
| Application allow listing | The enterprise can define which applications are able to execute on the device, and these policies are robustly enforced on the device. |
| Malicious code detection and prevention | The device can detect, isolate and defeat malicious code which is present on the device. |
| Security policy enforcement | Security policies set by your organisation are robustly implemented across the platform. The organisation can technically enforce a minimal set of security-critical policies on the device. These cannot be overridden by the user. |
| External interface protection | The device is able to constrain the set of ports (physical and logical) and services exposed to untrusted networks and devices. Any software exposed in this way is robust to malicious attack. |
| Device update policy | You are able to issue security updates and can remotely validate the patch level of your entire device estate. |
| Event collection for enterprise analysis | The device reports security-critical events to your audit and monitoring service. The user is prevented from tampering with this reporting. |
| Incident response | Your organisation has a plan in place to respond to and understand the impact of security incidents. This should be supported by appropriate functionality within the devices and your organisation. In the case of a lost device, this might entail sending a wipe command to the device and revoking credentials. |

# Common questions
> Items covered include use of Wi-Fi, device management and browser security
{.is-info}

You should read and understand all the points raised by this section before proceeding with a new deployment of EUDs within your organisation's network.

# Wi-Fi
In general, devices which support Wi-Fi can be used securely on any Wi-Fi network which allows VPN traffic to transit the network. However, there are risks associated with using Wi-Fi which must be considered and accepted before its use is permitted.

Many devices expose a rich set of services when connected over Wi-Fi. Risk owners of deployments which use Wi-Fi should be content that the increased attack surface of these devices is within the bounds of acceptability. For example, some devices may expose synchronisation services over Wi-Fi to allow media and data to be synchronised.

Others may present a screen sharing service which allows the contents of the device’s screen to be shared with networked peripherals. Services may also be accessible locally when the VPN is connected, effectively causing a split tunnel. These attack surfaces should be considered on a device-by-device basis and only permitted where the risk is acceptable.

Many public hotspots redirect web traffic to a ‘captive portal’ page at first connection. User interaction (agreeing to terms and conditions, or entering a passcode) is required before an internet connection is allowed. Captive portals require devices to browse to a website outside of the VPN connection. During this time, devices can be targeted for attack by the network itself, or by hostile users on that network.

Configuring current devices to enable this type of connection requires a mechanism to allow the user to disable or circumvent the VPN, increasing the risk to data in transit. Allowing captive portal interactions is not recommended where users are not trusted to manage their own connections appropriately.

# Captive Portals
Devices that have an always-on VPN will not be able to connect to Wi-Fi hotspots that use captive portals unless the always-on VPN is disabled. Connecting to a Wi-Fi hotspot with a captive portal will need to use an untrusted connection that is not protected by the VPN. There are several risks to EUDs that organisations need to be aware of if they enable the use of captive portals on their devices:

## Risks from using captive portals
### Unencrypted data can be read by the Wi-Fi hotspot
The Wi-Fi hotspot will be able to read any data that is not encrypted in transit. The wireless connection used by most public Wi-Fi hotspots is also not encrypted, meaning that anybody nearby will be able to read data being sent between the device and the hotspot. This could include sensitive information such as passwords, cookies and personally identifiable data.

### Data held in a browser could be stolen by a malicious hotspot
Web browsers are commonly used to access trusted services. Consequently, they are often configured to automatically authenticate against web applications in order to provide a seamless user experience. In order to do this they will save credentials and website content for future use.

An untrusted Wi-Fi hotspot can alter or re-route traffic as it is sent to the web browser. This can allow the hotspot to access data stored by the browser such as authentication cookies, browsing history and data temporarily cached by the browser.

### Your organisation's Internet gateway will be bypassed
Some organisations use security functions on their external gateway to supplement the controls on their end user device. This might include:

- logging all web access to audit compliance with corporate policy, and provide more situational awareness when an attack is detected elsewhere on the network
- anti-malware scans on files and web pages before they are loaded on the end user device
- reputational filtering to block potentially malicious sites based on data from cloud anti-malware services
- filtering out categories of sites deemed inappropriate for the workplace
- applying data loss protection rules to attempt to block sensitive data being accidentally sent to the Internet
- preventing the user from installing an untrusted root Certificate Authority's certificate

These capabilities will not be available while the VPN is disabled in order to allow access to the captive portal. This can result in unmonitored and less protected Internet access until the user manually establishes the VPN connection.

## Mitigating the risks from captive portals
You can adopt a variety of approaches to mitigate the risks from captive portals, some providing more confidence than others.

Some approaches attempt to make accessing the captive portal safer, before falling back to using a VPN to protect data in transit once connected to the Internet. Others provide alternative ways of connecting to public Wi-Fi networks.

The residual risk of each approach will vary depending on the platform being used and the exact solution chosen. You should choose a solution that balances usability, cost and platform features with residual risk. Where these risks are unacceptable to the users and the organisation, you should consider providing an alternative means of data connection, such as a mobile connection.

## Alternative ways of authenticating to Wi-Fi
Some technologies allow devices to authenticate to a Wi-Fi hotspot without using a web browser. These include:

- Wi-Fi CERTIFIED Passpoint (previously known as Hotspot 2.0) and WISPr which authenticate to the hotspot using a simple protocol and don’t require the use of a web browser.
- per-user WPA2 passwords which authenticate to the hotspot at the same time as the device connects to the Wi-Fi, allowing the VPN to automatically connect as soon as the device connects to the Wi-Fi hotspot.
- Wi-Fi network branded apps that automatically authenticate to a network of Wi-Fi hotspots. The exact functionality varies per app, though they usually run in a sandbox and use a separate web browser to let the user log in.
- agreements with Wi-Fi networks for specified devices to bypass the captive portal, and therefore allow the VPN to connect automatically when the device connects to the Wi-Fi hotspot.

## Device patching and configuration
Well maintained and configured devices, following the concepts outlined in this guidance, are an essential part of any effective mitigation strategy.

A device that has security patches applied promptly to both platform and all installed applications will be more resistant to malware and so less susceptible to attack.

This approach is most effective when combined with other mitigations, such as procedural controls to protect any corporate data stored on the device. Appropriate procedural controls include:

- minimising the time between connecting to the public WiFi and connecting the VPN
- not accessing sensitive data on the device until after the VPN has connected

Particular attention should be paid to:

- patching all software installed on the device including the platform itself
- enabling sandboxing mechanisms to separate the captive portal from sensitive data
- effective use of application whitelisting to reduce the risk of drive-by downloads
- making use of on-device reputational site filtering and malware detection
- ensuring that security configuration cannot be altered by the captive portal or the user
- using modern encryption standards including certificate pinning on services that send sensitive data over the network
- ensuring that the VPN automatically establishes a connection once the Internet is accessible 

## On-device sandboxing
Most of the risks listed above can be mitigated by providing separation between the captive portal and the rest of the platform. This can be achieved with a sandboxed app, virtualisation tools or even just a modern web browser configured to use a non-persistent profile.

Solutions should prioritise providing smooth and intuitive user experience between connecting to the Wi-Fi network and the device establishing the VPN connection. This approach can remove the reliance on procedural controls.

Preferred solutions should:

- protect the platform from any malicious content on the captive portal. Separation is usually best achieved when using the sandboxing that is built into the platform’s app framework (designed to protect apps from each other and protect the platform itself) or using hardware-backed virtualisation.
- prevent the captive portal from accessing data on the device. Sensitive data can include credentials, user’s files and data in other apps. As different users may treat different data as sensitive, this mitigation is most effective when the captive portal cannot access any data stored on the device.
- prevent the captive portal from accessing data stored in the browser which is used to access your organisation's data. Sensitive data in the browser can include cookies, saved passwords and data intentionally cached by web apps.
- be non-persistent. Configuration or cached data should be cleared each time a captive portal is accessed to minimise the impact of connecting to a malicious hotspot.
- ensure that the captive portal cannot reconfigure the device. This includes installing new trusted certificates into the browser or platform.
- use technical controls rather than procedural controls to enforce separation between the captive portal and the browser used to access your organisation's web applications.

## Device management
Device management products are used to remotely administer, configure and audit end user devices. In the context of EUDs, these services are generally referred to as Mobile Device Management (MDM) or Enterprise Mobility Management (EMM) products.

When deciding which MDM to use with your deployment, there are several key considerations.

### Product features and policies supported
Ensure that the selected MDM product can enforce the security policies that are recommended in the per-product security guidance. The range of capabilities varies between devices, so check that the MDM product can support all the platforms used by your organisation.

### Product security
MDM products are attractive targets for attackers. If they are able to compromise the MDM server an attacker will be able to perform remote administration and password resets on all enrolled devices. Compounding this, MDM servers are often placed in internet-accessible locations within the corporate network, directly exposing them to external attackers. Consequently, the reliability, robustness and security practices of the MDM product are extremely important.

When choosing an MDM product, consider its development lifecycle and your resultant confidence in the security of the product. Is there a good track record of fixing security issues? Are security incident management procedures in place to handle future problems? MDM products can be independently evaluated and certified to Foundation Grade, and details of such products can be found in the CPA certified products list.

### On-premise or cloud deployment
Many MDM product vendors offer hosted versions of their product. Using cloud-based MDM products may decrease costs, but can increase risk. For example, other users of cloud services may be able to more easily attack or degrade the management service for your devices. If you’re considering using cloud-based MDM services, read the Cloud Security Guidance for information on managing the risks associated with using public cloud services.

### Bring Your Own Device (BYOD)
Whilst ownership of a device makes many information security aspects much simpler, it is not a prerequisite of this guidance. What is necessary is that the device is placed under the management authority of the organisation for the complete duration it is permitted to access the organisation’s information.

To ensure information security when using devices not owned by the organisation, they should take control of device management at the point of provisioning, ensuring that the device is placed into a ‘known good’ state prior to allowing it to access information. Limitations of current technology mean that a ‘health check’ or ‘device status’ check is not sufficient to verify ‘known good’ - malware can easily subvert such a check. If possible, consider returning to an understood state such as by a firmware reinstall or wipe to factory state and replacing any existing configuration on it.

### Device interfaces
Some devices allow administrators to exert control over their external interfaces - such as Bluetooth and NFC - which either prevents them from functioning, or restricts their functionality to a subset (such as restricting what the interface can be used to connect to).

Using these controls can help to reduce the overall attack surface of a device, and prevent information disclosure from the device (such as by removing the ability of the user to share information directly). However, the impact on the usability of the device can be significant, so administrators are urged to carefully consider the necessity of applying such controls.

We strongly recommended that the use of these interfaces should be limited to non-sensitive information, and that information which an organisation wishes to protect should not be transmitted over these protocols. For example the use of Bluetooth headsets for non-sensitive voice communications presents a lower risk to data than the use of Bluetooth keyboards connected to the device would. In the latter case, sensitive typed data is transmitted over an unassured protocol.

### Browsers
Many organisations deploying this guidance will want to access internal and external web services using a web browser. There are many web browsers available for most platforms, so it's important to consider the risks associated with each type of browser, and to balance that against the useful functionality provided by the browser.

Modern browsers are feature-rich interfaces which enable users to be highly productive with their time online, but these features often have an impact to the security of the device and its data when used. For example:

- Browsers may cache credentials by offering a save password facility. You should ensure that your organisation is content with how this information is protected on the device, or disable any information caching functionality.
- Browsers may permit the concurrent browsing of Internet and intranet web pages in separate tabs. This may mean that the browser process is handling untrusted code and sensitive data at the same time, with the browser required to enforce separation between the two domains. This presents a large and rich attack surface to the tab running untrusted code and the browser must therefore be robust to attacks from that code.
- Browsers may allow plugins to be installed. Typically these plugins run with the same permissions as the browser itself, so plugins must be fully audited and trusted before their use is permitted.
- Browser vendors regularly release updates to add features and fix security issues. As the attack surface of browsers is very large, and the chances of encountering malicious code is high, these security updates must be installed regularly and quickly following their release.

Ultimately, devices used for web browsing should use a modern, regularly-updated, and well-supported product which takes advantage of the native security features of the underlying platform.

### Anti-virus and anti-malware protection
The EUD Security Principles note the importance of reducing the risk from malicious software and content based attacks. On a number of platforms this is achieved by using anti-virus or anti-malware software which will usually be purchased from a third-party, but several platforms will meet this requirement through other mechanisms.

When deciding if a third-party anti-malware product is necessary, you should assess the risk of malicious code being able to get onto the device and run. The extent to which application whitelisting is available and configured on the platform will be a significant factor, as will the ability to ensure incoming content is always routed through enterprise defences. The use of software restriction policies (or other security controls) native to the platform will also be a factor in deciding whether anti-malware or anti-virus products are necessary.

If you decide a third-party product is necessary, we recommend you:

- consider the management tools available. Specifically consider whether configuration policies can be centrally managed, and whether software and signature updates can be automatically rolled out across the device estate
- consider the audit tools available to the enterprise. Events from the product should be captured into a central location where they can be prioritised and investigated as part of an incident response plan
- consider whether the product provides heuristic and/or signature-based scanning
- consider the usability impact of the product on the platform (battery life, performance, etc), and do not layer multiple anti-malware products on top of each other – there is little evidence to suggest this lowers the risk of malware infections, but this can impact hugely on performance of the device.

Many products now expect to be able to communicate with online services provided by the vendor in order to gain access to better analysis capabilities. You will need to consider whether these communications are able to transit via the enterprise and whether sensitive data could leak through these channels.

### Security updates
Manufacturers will regularly release security updates and patches for their products. These updates should be applied regularly to ensure that devices are not compromised by known security issues.

For larger patches or feature releases, the security impact of any new features not yet described in this guidance should be considered before their use.


# Authentication policy
You should create a consistent policy for authenticating both users and devices before granting access to systems and resources (including information).

There are three important parts to authentication that you should consider:-

- User to device: the user is only granted access to the device after successfully authenticating to it.
- User to service: The user is only able to access enterprise services after successfully authenticating to the service, via their device.
- Device to service: Only devices which can authenticate to the enterprise are granted access.

For each, a number of decisions must be made about which authentication mechanisms are appropriate, taking into account both security and usability:

## Passwords
Passwords are the most common way users authenticate to devices and services. We have separate Password Guidance for details on how to create an appropriate password policy for your organisation. 

Many EUDs include technology that strengthens user to device passwords against an offline brute force attack. This includes combining passwords with a cryptographic key held in hardware-protected storage, as well as limiting the ability for an attacker to attempt to repeatedly manually guess passwords.

This means that passwords for user authentication to the device can simpler and shorter, although it is important for users to take care they are not overlooked entering their password.

## Biometrics 
For user to device authentication, many EUDs now come with biometric sensors such as fingerprint readers, facial recognition or iris scanners.

These technologies can vary in the false positive and negative rates as well as their ability to detect a spoof biometric. There is significant variation in how biometric capabilities are implemented in different EUDs, so it is important to assess the security of both how biometric data is stored and decisions are made within a particular device. 

Some devices have hardware-protected storage which can be used to release a cryptographic key following successful biometric authentication. This provides a strong level of protection for the biometric authentication process against physical attacks.

## Certificates
Certificates are long-term credentials which contain a private key and signed public key. Access to the private key is required to authenticate to other services, and can be used to either authenticate the device or the user to that service.

The private key should be protected from access by malicious software (via sandboxing or other access control mechanism), and should be protected from hardware extraction (via the device’s data-at-rest encryption, or protecting the private key with an encryption password if it can’t otherwise be protected).

## Keys or tokens
Keys or tokens are often short-lived credentials used to provide access to a service. Typically another user-to-service authentication mechanism is used to acquire a key or token which is then used for subsequent re-authentication attempts. This is common for web based services

---

These authentication mechanisms should be chosen and combined in a way which maximises the usability of a device, whilst offering appropriate security.

For example a single user to device password authentication mechanism can be used, which subsequently allows access to a token or certificate used for time bounded device or service authentication.

Where one authentication mechanism provides insufficient security, multi-factor authentication can be used.

Further details about how each type of EUD supports authentication approaches can be found in the device-specific EUD Security Guidance documents.