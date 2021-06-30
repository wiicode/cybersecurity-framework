---
title: End user device (EUD) security guidance
description: Guidance for organizations deploying a range of end user device platforms as part of a remote working solution
published: false
date: 2021-06-30T03:00:00.314Z
tags: silver, device-management, silver-training
editor: markdown
dateCreated: 2021-02-22T00:05:36.507Z
---

# Introduction
Modern smartphones, laptops and tablets provide users with great flexibility and functionality, and include security technologies to help protect information.

This security guidance is general to all End User Device (EUD) deployments and aims to help organizations harness these security technologies in a way that does not significantly reduce their functionality.

# Who is this guidance for?
This guidance is for any organization wishing to secure the EUDs they use, but it is primarily to help system administrators make informed decisions about the configuration, management and use of EUDs, and risk owners understand the overall risk to their networks presented by their use.

# What does this guidance do?
It builds upon the most important elements of the strategic goals described in 

make optimum use of native security functions, avoiding third-party products wherever possible

- allow greater user responsibility to reduce security complexity, maintaining user experience for the majority of responsible users
- logging and audit preferred over prevention and control, to maintain user experience and flexibility for the majority of responsible users
- enable greater interoprability of IT systems through a more common and consistent approach to securing information

# Platform-specific advice
There are also guidance documents for specific platforms (we'll put a collection link in here). Each platform we provide guidance for has been considered as part of a remote working deployment to see how effectively it is able to protect information. The guidance is not simply about applying settings to a device, but is also about making informed network architecture decisions; providing appropriate guidance and training for users; and performing operational maintenance, monitoring and defense of the network.

System Administrators may also use this guidance as a starting point for other security configurations for different devices such as desktops and servers. Consideration should be given to how applicable the recommendations are to their particular scenario and the guidance customised accordingly.

# Assumptions
- devices are corporately-managed and issued to users individually
- only a single user account will be present on each device. Multi-user devices are not addressed in this guide.
- devices will be used to access corporate services (email, calendar, collaboration tools...) both in and out of the office. 
- the devices will be used to access various Internet-based services, both for work and some personal use
- users will be made aware of the appropriate use of the system prior to receiving the device
- some devices will inevitably be lost or stolen (though precautions in this guidance should help ensure that data loss is minimized)
- devices will connect to a range of networks. Not just those provided by the organization itself
- networks to which the device connects will not necessarily be trustworthy, so protection of the data in transit on these networks is important
- devices will be deprovisioned when no longer used for their original purpose.

# Cautions
Although devices are expected to be corporately managed, the ownership model is not particularly relevant here. The critical aspect is that your administrators take over the management of the device via a provisioning process and are able to control all relevant aspects of it throughout the time it accesses your organization’s data.

Since we assume only a single user account, you will need to think about customizing the configurations given here if dealing with multi-user scenarios.

We recommend that you carefully consider the risks from allowing EUDs into high-security locations. This guidance doesn't cover the use of these devices in that type of environment.

# How to get the most from this guidance
1. Read the guidance for your selected device(s) in full. 
1. Consider how applicable the usage scenario and recommendations are for your intended use.
1. Set up a pilot of devices in a non-operational environment before deployment. 
1. Try to simulate the environment where the devices will be deployed.
1. Determine the business functions that devices need to perform before deciding on the configuration. 
1. Apply security configurations to the device or supporting infrastructure where applicable.
1. Produce security operating procedures, user education packages and training documents. 
1. This will help your staff to keep information secure on mobile devices.
1. Establish a helpdesk facility to respond to the loss or theft of devices. 
1. Remotely lock or wipe devices, and revoke their ability to access your organization's information.
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
| Authentication | Each of the three types of authentication described here should be considered - User to device: the user is only granted access to the device after successfully authenticating to the device. - User to service: The user is only able to access enterprise services after successfully authenticating to the service, via their device. - Device to service: Only devices which can authenticate to the enterprise are granted access. - Each stage of the authentication process should be designed to complement the others, as part of your organization’s authentication policy. Further guidance on devising an authentication policy can be found in this collection. |
| Secure boot | An unauthorized entity should not be able to modify the boot process of a device, and any attempt to do so should be detected. |
| Platform integrity and application sandboxing | The device can continue to operate securely despite potential compromise of an application or component within the platform, and you have the ability to restrict the capabilities of applications on the device. |
| Application allow listing | The enterprise can define which applications are able to execute on the device, and these policies are robustly enforced on the device. |
| Malicious code detection and prevention | The device can detect, isolate and defeat malicious code which is present on the device. |
| Security policy enforcement | Security policies set by your organization are robustly implemented across the platform. The organization can technically enforce a minimal set of security-critical policies on the device. These cannot be overridden by the user. |
| External interface protection | The device is able to constrain the set of ports (physical and logical) and services exposed to untrusted networks and devices. Any software exposed in this way is robust to malicious attack. |
| Device update policy | You are able to issue security updates and can remotely validate the patch level of your entire device estate. |
| Event collection for enterprise analysis | The device reports security-critical events to your audit and monitoring service. The user is prevented from tampering with this reporting. |
| Incident response | Your organization has a plan in place to respond to and understand the impact of security incidents. This should be supported by appropriate functionality within the devices and your organization. In the case of a lost device, this might entail sending a wipe command to the device and revoking credentials. |

# Common questions
> Items covered include use of Wi-Fi, device management and browser security
{.is-info}

You should read and understand all the points raised by this section before proceeding with a new deployment of EUDs within your organization's network.

# Wi-Fi
In general, devices which support Wi-Fi can be used securely on any Wi-Fi network which allows VPN traffic to transit the network. However, there are risks associated with using Wi-Fi which must be considered and accepted before its use is permitted.

Many devices expose a rich set of services when connected over Wi-Fi. Risk owners of deployments which use Wi-Fi should be content that the increased attack surface of these devices is within the bounds of acceptability. For example, some devices may expose synchronisation services over Wi-Fi to allow media and data to be synchronized.

Others may present a screen sharing service which allows the contents of the device’s screen to be shared with networked peripherals. Services may also be accessible locally when the VPN is connected, effectively causing a split tunnel. These attack surfaces should be considered on a device-by-device basis and only permitted where the risk is acceptable.

Many public hotspots redirect web traffic to a ‘captive portal’ page at first connection. User interaction (agreeing to terms and conditions, or entering a passcode) is required before an internet connection is allowed. Captive portals require devices to browse to a website outside of the VPN connection. During this time, devices can be targeted for attack by the network itself, or by hostile users on that network.

Configuring current devices to enable this type of connection requires a mechanism to allow the user to disable or circumvent the VPN, increasing the risk to data in transit. Allowing captive portal interactions is not recommended where users are not trusted to manage their own connections appropriately.

# Captive Portals
Devices that have an always-on VPN will not be able to connect to Wi-Fi hotspots that use captive portals unless the always-on VPN is disabled. Connecting to a Wi-Fi hotspot with a captive portal will need to use an untrusted connection that is not protected by the VPN. There are several risks to EUDs that organizations need to be aware of if they enable the use of captive portals on their devices:

## Risks from using captive portals
### Unencrypted data can be read by the Wi-Fi hotspot
The Wi-Fi hotspot will be able to read any data that is not encrypted in transit. The wireless connection used by most public Wi-Fi hotspots is also not encrypted, meaning that anybody nearby will be able to read data being sent between the device and the hotspot. This could include sensitive information such as passwords, cookies and personally identifiable data.

### Data held in a browser could be stolen by a malicious hotspot
Web browsers are commonly used to access trusted services. Consequently, they are often configured to automatically authenticate against web applications in order to provide a seamless user experience. In order to do this they will save credentials and website content for future use.

An untrusted Wi-Fi hotspot can alter or re-route traffic as it is sent to the web browser. This can allow the hotspot to access data stored by the browser such as authentication cookies, browsing history and data temporarily cached by the browser.

### Your organization's Internet gateway will be bypassed
Some organizations use security functions on their external gateway to supplement the controls on their end user device. This might include:

- logging all web access to audit compliance with corporate policy, and provide more situational awareness when an attack is detected elsewhere on the network
- anti-malware scans on files and web pages before they are loaded on the end user device
- reputation filtering to block potentially malicious sites based on data from cloud anti-malware services
- filtering out categories of sites deemed inappropriate for the workplace
- applying data loss protection rules to attempt to block sensitive data being accidentally sent to the Internet
- preventing the user from installing an untrusted root Certificate Authority's certificate

These capabilities will not be available while the VPN is disabled in order to allow access to the captive portal. This can result in unmonitored and less protected Internet access until the user manually establishes the VPN connection.

## Mitigating the risks from captive portals
You can adopt a variety of approaches to mitigate the risks from captive portals, some providing more confidence than others.

Some approaches attempt to make accessing the captive portal safer, before falling back to using a VPN to protect data in transit once connected to the Internet. Others provide alternative ways of connecting to public Wi-Fi networks.

The residual risk of each approach will vary depending on the platform being used and the exact solution chosen. You should choose a solution that balances usability, cost and platform features with residual risk. Where these risks are unacceptable to the users and the organization, you should consider providing an alternative means of data connection, such as a mobile connection.

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

- minimizing the time between connecting to the public WiFi and connecting the VPN
- not accessing sensitive data on the device until after the VPN has connected

Particular attention should be paid to:

- patching all software installed on the device including the platform itself
- enabling sandboxing mechanisms to separate the captive portal from sensitive data
- effective use of application whitelisting to reduce the risk of drive-by downloads
- making use of on-device reputation site filtering and malware detection
- ensuring that security configuration cannot be altered by the captive portal or the user
- using modern encryption standards including certificate pinning on services that send sensitive data over the network
- ensuring that the VPN automatically establishes a connection once the Internet is accessible 

## On-device sandboxing
Most of the risks listed above can be mitigated by providing separation between the captive portal and the rest of the platform. This can be achieved with a sandboxed app, virtualization tools or even just a modern web browser configured to use a non-persistent profile.

Solutions should prioritize providing smooth and intuitive user experience between connecting to the Wi-Fi network and the device establishing the VPN connection. This approach can remove the reliance on procedural controls.

Preferred solutions should:

- protect the platform from any malicious content on the captive portal. Separation is usually best achieved when using the sandboxing that is built into the platform’s app framework (designed to protect apps from each other and protect the platform itself) or using hardware-backed virtualization.
- prevent the captive portal from accessing data on the device. Sensitive data can include credentials, user’s files and data in other apps. As different users may treat different data as sensitive, this mitigation is most effective when the captive portal cannot access any data stored on the device.
- prevent the captive portal from accessing data stored in the browser which is used to access your organization's data. Sensitive data in the browser can include cookies, saved passwords and data intentionally cached by web apps.
- be non-persistent. Configuration or cached data should be cleared each time a captive portal is accessed to minimize the impact of connecting to a malicious hotspot.
- ensure that the captive portal cannot reconfigure the device. This includes installing new trusted certificates into the browser or platform.
- use technical controls rather than procedural controls to enforce separation between the captive portal and the browser used to access your organization's web applications.

## Device management
Device management products are used to remotely administer, configure and audit end user devices. In the context of EUDs, these services are generally referred to as Mobile Device Management (MDM) or Enterprise Mobility Management (EMM) products.

When deciding which MDM to use with your deployment, there are several key considerations.

### Product features and policies supported
Ensure that the selected MDM product can enforce the security policies that are recommended in the per-product security guidance. The range of capabilities varies between devices, so check that the MDM product can support all the platforms used by your organization.

### Product security
MDM products are attractive targets for attackers. If they are able to compromise the MDM server an attacker will be able to perform remote administration and password resets on all enrollled devices. Compounding this, MDM servers are often placed in internet-accessible locations within the corporate network, directly exposing them to external attackers. Consequently, the reliability, robustness and security practices of the MDM product are extremely important.

When choosing an MDM product, consider its development lifecycle and your resultant confidence in the security of the product. Is there a good track record of fixing security issues? Are security incident management procedures in place to handle future problems? MDM products can be independently evaluated and certified to Foundation Grade, and details of such products can be found in the CPA certified products list.

### On-premise or cloud deployment
Many MDM product vendors offer hosted versions of their product. Using cloud-based MDM products may decrease costs, but can increase risk. For example, other users of cloud services may be able to more easily attack or degrade the management service for your devices. If you’re considering using cloud-based MDM services, read the Cloud Security Guidance for information on managing the risks associated with using public cloud services.

### Bring Your Own Device (BYOD)
While ownership of a device makes many information security aspects much simpler, it is not a prerequisite of this guidance. What is necessary is that the device is placed under the management authority of the organization for the complete duration it is permitted to access the organization’s information.

To ensure information security when using devices not owned by the organization, they should take control of device management at the point of provisioning, ensuring that the device is placed into a ‘known good’ state prior to allowing it to access information. Limitations of current technology mean that a ‘health check’ or ‘device status’ check is not sufficient to verify ‘known good’ - malware can easily subvert such a check. If possible, consider returning to an understood state such as by a firmware reinstall or wipe to factory state and replacing any existing configuration on it.

### Device interfaces
Some devices allow administrators to exert control over their external interfaces - such as Bluetooth and NFC - which either prevents them from functioning, or restricts their functionality to a subset (such as restricting what the interface can be used to connect to).

Using these controls can help to reduce the overall attack surface of a device, and prevent information disclosure from the device (such as by removing the ability of the user to share information directly). However, the impact on the usability of the device can be significant, so administrators are urged to carefully consider the necessity of applying such controls.

We strongly recommended that the use of these interfaces should be limited to non-sensitive information, and that information which an organization wishes to protect should not be transmitted over these protocols. For example the use of Bluetooth headsets for non-sensitive voice communications presents a lower risk to data than the use of Bluetooth keyboards connected to the device would. In the latter case, sensitive typed data is transmitted over an unassured protocol.

### Browsers
Many organizations deploying this guidance will want to access internal and external web services using a web browser. There are many web browsers available for most platforms, so it's important to consider the risks associated with each type of browser, and to balance that against the useful functionality provided by the browser.

Modern browsers are feature-rich interfaces which enable users to be highly productive with their time online, but these features often have an impact to the security of the device and its data when used. For example:

- Browsers may cache credentials by offering a save password facility. You should ensure that your organization is content with how this information is protected on the device, or disable any information caching functionality.
- Browsers may permit the concurrent browsing of Internet and intranet web pages in separate tabs. This may mean that the browser process is handling untrusted code and sensitive data at the same time, with the browser required to enforce separation between the two domains. This presents a large and rich attack surface to the tab running untrusted code and the browser must therefore be robust to attacks from that code.
- Browsers may allow plugins to be installed. Typically these plugins run with the same permissions as the browser itself, so plugins must be fully audited and trusted before their use is permitted.
- Browser vendors regularly release updates to add features and fix security issues. As the attack surface of browsers is very large, and the chances of encountering malicious code is high, these security updates must be installed regularly and quickly following their release.

Ultimately, devices used for web browsing should use a modern, regularly-updated, and well-supported product which takes advantage of the native security features of the underlying platform.

### Anti-virus and anti-malware protection
The EUD Security Principles note the importance of reducing the risk from malicious software and content based attacks. On a number of platforms this is achieved by using anti-virus or anti-malware software which will usually be purchased from a third-party, but several platforms will meet this requirement through other mechanisms.

When deciding if a third-party anti-malware product is necessary, you should assess the risk of malicious code being able to get onto the device and run. The extent to which application whitelisting is available and configured on the platform will be a significant factor, as will the ability to ensure incoming content is always routed through enterprise defenses. The use of software restriction policies (or other security controls) native to the platform will also be a factor in deciding whether anti-malware or anti-virus products are necessary.

If you decide a third-party product is necessary, we recommend you:

- consider the management tools available. Specifically consider whether configuration policies can be centrally managed, and whether software and signature updates can be automatically rolled out across the device estate
- consider the audit tools available to the enterprise. Events from the product should be captured into a central location where they can be prioritized and investigated as part of an incident response plan
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
Passwords are the most common way users authenticate to devices and services. We have separate Password Guidance for details on how to create an appropriate password policy for your organization. 

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

These authentication mechanisms should be chosen and combined in a way which maximizes the usability of a device, while offering appropriate security.

For example a single user to device password authentication mechanism can be used, which subsequently allows access to a token or certificate used for time bounded device or service authentication.

Where one authentication mechanism provides insufficient security, multi-factor authentication can be used.

Further details about how each type of EUD supports authentication approaches can be found in the device-specific EUD Security Guidance documents.

# Virtual Private Networks (VPN)
> A Virtual Private Network (VPN) is a mechanism for securely connecting devices or networks together, even if geographically separated.
{.is-info}


A Virtual Private Network (VPN) is a mechanism for securely connecting devices or networks together, even if geographically separated. They are popular for enabling remote working from end-user devices (EUDs).

This guidance provides risk owners and administrators with more generic advice than the per-platform guidance, which recommends a specific configuration for each type of EUD. It can be used to understand the risks and benefits of using a different configuration from the one we recommend.

While anyone can use a VPN to secure their network usage, this guidance is aimed at organizations supporting remote working. It therefore assumes a degree of technical understanding and knowledge of topics related to the use and management of VPNs.

We'll be discussing various types of VPN, but we won’t be focusing on individual products in this guidance. Instead, we discuss aspects of VPN technology and configuration so you can compare and contrast different products. Platform-specific recommendations are kept in the EUD Guidance for those platforms.

## Why use a VPN?
Regardless of the technologies involved, there are several common reasons why you may use VPNs to connect between EUDs and remote networks.

When choosing network security technologies, keep in mind which of these you are trying to achieve:

1. Protection of sensitive data in transit that would otherwise be unencrypted and vulnerable to interception (e.g. metadata, traffic to internal HTTP services)
1. Enabling legacy systems to work remotely that were not designed to operate in such scenarios (e.g. SMB file servers)
1. Providing a second layer of defense against misconfigured, unpatched, or poorly designed internal services (e.g. SSL intranet website with legacy cryptography)
1. Protecting internal network servers from external, unauthenticated attackers by limiting network access to authenticated devices (e.g. file stores or databases)
1. Protecting EUDs from network attack by preventing direct connections to/from the local network (e.g. ARP spoofing attacks, or attacking open network interfaces on the EUD)
1. Forcing traffic between EUDs and external services through internal, protective monitoring tools guarding against a variety of threats (e.g. inspecting web content for malicious code)
1. Enabling business monitoring and/or blocking of users’ network traffic for legal reasons, discipline, and duty of care (e.g. deny listing websites)

## Aspects of VPN configurations
BCSF’s EUD guidance recommends an automatic, always on, IPsec VPN, which routes traffic through a remote network for inspection. That guidance also provides a configuration for the platform to make that work.

This section highlights some aspects of VPN configuration you may wish to change, and the resulting impact on risks.

### Protocols
The protocols most widely used for VPNs are Transport Layer Security (TLS) and IPsec. There are a variety of others, some of which (PPTP for example) have fallen out of use because of security concerns.

Our recommendation is that IPsec be used for VPN access. IPsec is an open standard, meaning that anyone can build a client or server which will interoperate with other IPsec implementations. The EUD Security Strategy advocates interoperability, open standards, and the use of native security controls.

As an IPsec VPN client is built in to many operating systems, no additional products are required to deploy a VPN. However, some networks restrict or block IPsec traffic, so your EUDs may, in certain situations, be unable to create the VPN connection.

TLS VPNs can also be used, though you will likely need to use a third-party client and server. In addition, products from different vendors will rarely interoperate, so you will need to use both from the same vendor – while TLS is standardized in a variety of RFCs, exactly how those protocols are used to create a VPN is not. However, TLS VPN connections tend to be more reliable when traversing Network Address Translation (NAT) devices, or enterprise firewalls.

From a security perspective, with all other things equal, there is very little difference in risk between using an IPsec and a TLS VPN.

### Cryptography
We recommend that client certificates are used for machine authentication when using a VPN. Certificates have several advantages over Pre-Shared Keys (PSKs), including the ability to revoke just one certificate on your network and to store private keys securely (e.g. in a TPM or TEE).

Links to recommended configurations are provided at the end of this guidance, including details on the cryptographic algorithms we recommend are used in VPNs. As these recommended configurations are not always fully supported by built-in VPN clients on EUD operating systems, we also give per-platform recommendations in the per-platform EUD guidance.

By using weaker profiles or algorithms than those recommended below, you will increase the risk of data compromise while in transit on the network.

### Integrated vs third-party VPN clients
Most operating systems have a built-in VPN client available which can either be configured on the device or managed remotely via enterprise management. Integrated clients are normally free to use, work reliably, and are updated automatically, but can also be relatively limited in functionality. For example, there’s often no ability to configure routing rules, exceptions, or split tunnelling.

Our guidance recommends using the native client where possible, and provides a configuration for that client. However, a range of CPA Foundation Grade approved IPsec third-party clients, and other commercially available third-party VPN clients exist.

Using a third-party VPN client increases the risk that operating system integration will be poor, and that some data may be sent outside the VPN. It also increases the number of software packages that need to be kept up to date, adding to the likelihood that some out-of-date software will be in use.

### Forced vs optional
Only traffic which is routed over the VPN will be protected by it, so you might want to force all traffic to go via the VPN, and no user traffic to transit outside that connection. This will require either the VPN client to enforce this, or a client firewall, configured to prevent connections being established outside of the VPN. If a forced VPN is unable to connect, then no network traffic from the device will be possible unless the VPN is disabled.

Our guidance generally recommends forcing traffic down the VPN, and where possible, the per-platform EUD guidance provides ways of achieving this. Where it's not possible to force traffic, this is highlighted as a risk. However, forced connections can sometimes cause incompatibilities with captive portals on public Wi-Fi networks, unless the platform offers a solution for authenticating to them.

Using an optional VPN allows users to disable the VPN and evade protective monitoring and auditing services. This increases the risk of EUDs being attacked over the network, and of users circumventing corporate policy restrictions.

### Initiating a VPN connection
VPNs need to be established in order to provide benefits, remain connected while the device is in use, and reconnect if the connection is temporarily lost. Typically, there are three ways of implementing this behavior: automatic, triggered, and manual.

- Automatic VPNs are brought up by the device whenever a network connection is requested by software on the device
- Triggered VPNs are brought up whenever certain network connections from a defined list are made (internal intranet sites, for example)
- Manual VPNs require the user of the device to initiate the VPN by explicitly deciding to take an action (such as launching an application and clicking connect). The user will likely need to take this step again if the connection drops during or after use

> **Note**: We distinguish automatic from forced (in the previous section) because on some platforms it is possible for the user to disable the automatic VPN, while the platform still enforces VPN routing. This effectively prevents network connections from the device until the user re-enables automatic connections.
> Depending on whether the VPN is forced or optional, choosing between automatic, triggered and manual could be a usability decision rather than security. If the VPN is forced but the initiation is manual, this will be a poor user experience as the device will not have any connectivity until the user manually starts the VPN. Conversely, if the VPN is optional, and the initiation is manual, then there is a risk of compromise from local attackers on an untrusted network, during the period when the device is not connected.
{.is-warning}

Our guidance generally is to use an automatic VPN, and where possible our per-platform EUD guidance gives a way of achieving this.

### Full-device vs per-app VPN
Some operating systems, and many third-party applications, provide the ability for you to configure only certain applications to be able to use a VPN on the device. This is mostly useful in a Bring Your Own Device (BYOD) scenario, where enterprises do not want network traffic from personal apps to traverse the corporate network. This approach can be used to prevent malicious personal apps attacking the corporate network, or to limit bandwidth consumption from data-intensive personal apps. A per-app VPN also enables latency-sensitive apps (such as secure voice) to avoid any increase in network latency from the VPN.

However, if deploying in this way, you need to define all the applications you want protected by the VPN in advance. As this is generally used in a BYOD scenario, users can always download another application to work around the per-app VPN restrictions. In some cases, it may not be possible to force system applications to use a per-app VPN.

BCSF’s per-platform EUD guidance recommends - and provides a configuration for - setting up a full-device VPN. Using a per-app VPN increases the risk that sensitive data may be sent outside the VPN by an application that is not included in a per-app VPN, or by a misconfiguration in the platform.

### Split tunnelling
Like a per-app VPN, split tunnelling is a way of having some traffic use the VPN, while other traffic is permitted direct connectivity. This is generally achieved by only defining certain network routes (e.g. internal IP address ranges) as available via the VPN. The default gateway for all other traffic is then left as a direct connection.

This is generally used when the VPN is providing access to internal services on a corporate network, without attempting to prevent other connections. For example, high-bandwidth applications could be permitted direct access to the internet without being routed via corporate infrastructure to save on bandwidth costs. And, as with per-app VPNs, latency-sensitive applications, such as a secure voice client, could minimize network latency by connecting directly.

Split tunnelling is generally not supported on EUD native clients, which have very simple configuration options. Windows operating systems can be configured to split tunnel by using custom routing rules, but the clients built into smartphones and tablets rarely support this configuration. Third-party clients are sometimes able to support this option.

Enabling split tunnelling increases the risk that sensitive data will be exposed to an unprotected network, and could enable external attackers to access internal resources by ‘pivoting’ through the EUD. In a scenario where you are relying on the VPN to route traffic for protective monitoring or duty of care reasons, enabling split tunnelling will undermine the benefit gained from those protections.

### Captive portals
Captive portals are the login pages present on some public Wi-Fi networks. To use a captive portal, the EUD is required to establish a direct connection from a web browser to the portal before it has established a VPN connection. For this, one of two things must be configured:

The user can disable any forced VPN configuration, so they can manually navigate to the portal in their main web browser.
The platform itself can detect the presence of a captive portal and present the user with a captive portal helper application to authenticate with before (re)establishing the VPN. Some platforms, such as iOS and macOS have such a helper built in. Helpers are available as a third-party application for some other platforms, such as Windows 10.
The use of a captive portal helper application is less risky and should be preferred if captive Wi-Fi networks are to be used. The risks of disabling forced VPNs are described earlier in this guidance.

Further details on the risks of using captive portals can be found in EUD Guidance: Common Questions – Captive Portals.

## Wider considerations
This section discusses some of the wider considerations when deploying a VPN onto your EUDs. These are not directly related to the configuration of the VPN, but are features which will be affected by your choice of technologies and configurations, as outlined in the previous section.

### Client and Gateway security updates
As with all software, both the client and server component will need to be regularly updated. On devices where the client is integrated into the operating system, these updates will naturally happen as a result of regular platform updates. Third-party software will need to be updated in some other way.

### Tethering to devices with a VPN
Tethering, or mobile hotspots, involve connecting an external device to your smartphone in order to use the smartphone’s internet connection. However, full-device VPNs can often have an impact on how tethering works on the underlying platform. Some platforms will route tethered devices’ connections outside of the smartphone’s VPN connection, while some smartphones will not route tethered traffic if there is a full-device VPN connected. If your users rely on tethering, an appropriate configuration should be selected to enable it.

## Platform compatibility summary
The table below gives the configuration we recommend be used with the native clients on each platform. Generally, this is the configuration we have found which best provides the benefits described at the start of this guidance. For full details of these recommendations, see the per-platform EUD guidance.

As with all our EUD guidance, the configurations we recommend are not mandatory. It is possible to configure VPNs to behave differently than given in the matrix below. You are free to do this, but if you choose a different configuration, you should consider the risks of doing so.

| Features of integrated VPN client | Windows | iOS | macOS | Android | ChromeOS | Ubuntu |
| --- | --- | --- | --- | --- | --- |
| Protocol | IPsec | IPsec | IPsec | IPsec | IPsec | IPsec |
| Product | Integrated | Integrated (IKEv2) | Integrated (IKEv2) | Integrated | Integrated (OpenVPN) | strongSwan |
| Forced or Optional | Forced | Forced | Optional | Forced | Optional | Forced |
| Initiation | Automatic | Automatic | Triggered | Automatic | Automatic | Automatic |
| Full-device or Per-app | Full-device	 | Full-device	 | Full-device | Full-device | Full-device | Full-device |
| Split tunnelling | Via firewall rules configured with Group Policy | Not supported | Via custom network routing rules | Not supported | Not supported | Via custom network routing rules and strongSwan configuration |
| Tethering supported | n/a | No | n/a | No | n/a | n/a |
| Captive-portal support | Via third-party app and custom firewall rules | Built-in helper | Built-in helper | None | Chrome browser | None |

## Recommended configurations
The BCSF has some additional guidance documents which provide advice on other aspects of configuring VPNs, including cryptographic profiles, and advice on managing a Certificate Authority (CA). These documents are:

Using TLS to protect data
{.grid-list}

- [Using TLS to protect data *Including recommended cipher suites for TLS.*](#)
- [Using IPsec to protect data *Including recommended cryptographic transforms for IPsec*](#)
- [Provisioning and securing security certificates](#)
{.links-list}

# Advice for end users
> This advice will need to be tailored to the particular device(s) being used, and matched to the local business procedures and activities.
{.is-info}

This advice will need to be tailored to the particular device(s) being used, and matched to the local business procedures and activities. Some advice to users is common across all types of device, and this is provided here as a suggestion.

## General advice
Some of the settings on your device have been configured by your system administrator to help keep the information on it secure. Changing or circumventing these settings could put information at risk. If you are unsure about any of the settings, or what to do in particular situations, please contact your IT helpdesk.

This device is valuable and so it is attractive to thieves. Take sensible precautions to prevent its loss or theft - but don’t put yourself at risk. Don’t leave the device unattended in an insecure location (e.g. outside of your house or office) - lock it away if possible, or keep it on your person.

If your device is lost or stolen contact your IT helpdesk immediately to report this. You won’t be in trouble - it is better to report such a loss as quickly as you can. The faster you get in contact, the better - there is more that can be done to prevent information being accessed.

When you are using your device be aware of who might be able to see your screen, and consider, if applicable, using a screen privacy protector. Devices which have ‘touch screens’ are particularly easy for bystanders to see what you are typing - even passwords.

## Physical connections
You should only use the specific device(s) that your organization has approved, this includes all of the peripherals that come with the device(s).

Your device should only ever be recharged with trusted power adapters and cables.

Don’t physically connect your device to any computer without the approval of your IT helpdesk. This includes USB, HDMI, Firewire etc.

Any ability to bridge connections using your device (e.g. internet connection sharing) must not be used unless specifically approved by your IT administration.

## Passwords
Whatever the reason, you must never disclose your password to anyone (including IT support staff, your manager, or a colleague), either in person, by phone, or by email or text message.

It is acceptable to write your password down, but it must be stored securely - and never with the device itself. For example, if you write your password down, seal it into an envelope, and then store it according to its sensitivity (e.g. kept in a secure, locked, cabinet). Under no circumstances should you ever carry this copy of the password with your device.

Your organization may set some rules about what you can use for a password. The most important thing is that it should be difficult for somebody else to guess that password, even if they know you well. Never share the same password across different systems or devices.

## Overseas use
In general, it is acceptable for you to take and use your device overseas, provided that your organization has approved this.

As highlighted above, you must be extra vigilant and take extra care to ensure that no one overlooks you when you are using your device, and must take all possible precautions to prevent the theft of your device.

## If things go wrong
When something goes wrong, or you suspect your device or its data may be compromised, it is important to take action promptly.

If you have any reason to suspect that someone else knows your password then it must be changed immediately - either on the device itself or by contacting your IT helpdesk.

If you forget the password for your device you should contact your IT helpdesk, who will confirm your identity before a password reset can take place.

If your device stops functioning as normal, and/or experiences a significant decrease in performance or battery life, contact your IT helpdesk for further advice.

If you are experiencing problems with the device, you must never give your device to anyone else (e.g. a commercial repairer) to try to fix; always contact your IT helpdesk.

If you think someone may have tampered with your device (such as accessing the inside of it, or removing / replacing parts of it), stop using it immediately, turn it off, and contact your IT helpdesk for assistance.

