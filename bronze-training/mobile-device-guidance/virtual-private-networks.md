---
title: Virtual Private Networks (VPNs)
description: Choosing, deploying and configuring VPN technologies
published: true
date: 2021-06-02T20:59:19.119Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:54:13.763Z
---

Virtual Private Networks (VPNs) allow organisations to provide secure connectivity between devices in physically separate locations. This guidance helps administrators within choose, deploy and configure VPNs for their organisation.

Individuals typically use VPNs for different reasons, which are not covered in this guidance.

---

## Why use a VPN?

VPNs are encrypted network connections. These allow remote users to securely access an organisation's services. VPNs are one way to guarantee the security of 'data in transit' across an untrusted network, but they also provide several other benefits.

For example, an organisation with offices in multiple locations can use VPNs to provide its remote users with access to corporate email and file services.

### **Additional advantages of VPNs**

1.  Enabling legacy systems to work remotely, even when not design for such scenarios. For example, SMB file servers
2.  Providing a second layer of defence against misconfigured, unpatched, or poorly designed internal services. For example, intranet websites that aren’t well maintained, or use legacy cryptography
3.  Protecting internal network servers from external, unauthenticated attackers, by limiting network access to authenticated devices. For example, file stores or databases
4.  Protecting user devices from network attack by preventing direct connections to and from the local network. For example, ARP spoofing attacks, or attacking open network interfaces on the mobile device
5.  Forcing traffic between a device and external services through internal, protective monitoring tools, guarding against a variety of threats. For example, inspecting web content for malicious code
6.  Enabling business monitoring and/or filtering of users’ network traffic for legal reasons, discipline, and duty of care. For example, blocking access to illegal websites

Protecting data in transit is one of the most important security aspects to consider when using mobile devices. Attackers with access to unprotected data (or inadequately-protected data) may be able to intercept and modify data, potentially causing harm. It is therefore important to decide which of the above benefits are relevant to your organisation **before** deciding which VPN technology to use, and how to use it.

---

## Preparation for VPN use

### **Do you need a VPN?**

Whether you require a VPN will depend on the [network architecture](https://www.ncsc.gov.uk/collection/mobile-device-guidance/infrastructure/network-architectures-for-remote-access) you use. For example, there would be little benefit in using a VPN if you've fully adopted a [zero-trust approach to networking](https://www.ncsc.gov.uk/collection/mobile-device-guidance/infrastructure/network-architectures-for-remote-access).

Also, if none of the advantages of VPNs mentioned above apply to you, there is no need to use one. Even if some of those reasons apply to you, there may be alternative ways to address the base problem. Legacy services may not be needed on devices outside the firewall, or blocking access to illegal websites could be done on-device, if required.

VPNs are complex to set up, require maintenance, and failure of a VPN could easily cause organisation-wide outages.

If you're using a [walled garden architecture](https://www.ncsc.gov.uk/collection/mobile-device-guidance/infrastructure/network-architectures-for-remote-access), or other architecture that requires end users' traffic to traverse untrusted networks and external firewalls then you should consider using a VPN. However, there are many aspects of a VPN to consider. These are addressed next.

### **Protocols**

The protocols most widely used for VPNs are Transport Layer Security (TLS) and Internet Protocol Security (IPsec). There are a variety of others, some of which ([PPTP](https://en.wikipedia.org/wiki/Point-to-Point_Tunneling_Protocol) for example) have fallen out of use because of security concerns. Other protocols, such as Wireguard are growing in popularity and seem promising, but are yet to be proven in enterprise contexts.

Our recommendation is that IPsec be used for VPN access. IPsec is an open standard, meaning that anyone can build a client or server which will work with other IPsec implementations.

As an IPsec VPN client is built into many operating systems, no additional products are required to deploy a VPN. However, some third-party networks restrict or block IPsec traffic, so your mobile devices may, in certain situations, be unable to create the VPN connection.

TLS VPNs can also be used, though you will likely need to use a third-party client and server. In addition, products from different vendors will rarely inter-operate, so you will need to use both from the same vendor. Whilst TLS is standardised in a variety of [RFCs](https://en.wikipedia.org/wiki/Request_for_Comments), exactly how those protocols are used to create a VPN is not. However, TLS VPN connections can be more reliable when traversing Network Address Translation (NAT) devices, or enterprise firewalls.

From a security perspective, with all other things equal, there is very little difference in risk between using an IPsec and a TLS VPN.

### **Cryptography**

We recommend client certificates for machine authentication, when using a VPN. Certificates have several advantages over Pre-Shared Keys (PSKs), including the ability to revoke just one certificate on your network and to store private keys securely (e.g. in a TPM or TEE), which we strongly recommend, when possible.

For specific guidance on configuring cryptographic parameters, see the NCSC's separate guidance on [Using IPsec to protect data](https://www.ncsc.gov.uk/guidance/using-ipsec-protect-data) and [Using TLS to protect data](https://www.ncsc.gov.uk/guidance/tls-external-facing-services). As these recommended configurations are not always fully supported by built-in VPN clients on mobile operating systems. We also give per-platform recommendations in the per-platform mobile device guidance.

By using weaker profiles or algorithms than those recommended below, you will increase the risk of data compromise while in transit over untrusted networks.

### **Integrated vs third-party VPN clients**

Most operating systems have a built-in VPN client available which can either be configured on the device or managed remotely. Integrated clients are normally free to use, work reliably, and are updated automatically, but can also be relatively limited in functionality. For example, there’s often no ability to configure routing rules, exceptions, or split tunnelling.

We recommend using the native client where possible, and our platform specific guidance provides configuration details. However, a range of commercially available third-party VPN clients exists.

Using a third-party VPN client increases the risk that operating system integration will be poor, and that consequently, some data may be sent outside the VPN. It also increases the number of software packages that need to be kept up to date, adding to the likelihood that some out-of-date software will be in use.

### **Forced vs optional**

Only traffic which is routed over the VPN will be protected by it, so you might want to force all traffic to be routed via the VPN, and for no user traffic to transit outside that connection. This will require either the VPN client itself to enforce this, or a client firewall configured to prevent connections being established outside of the VPN. If a forced VPN is unable to connect, then no network traffic from the device will be possible, unless the VPN is disabled.

Our guidance generally recommends forcing traffic down the VPN, and where possible, the per-platform guidance provides ways of achieving this. Where it's not possible to force traffic, this represents a risk to your data. However, forced connections can sometimes cause incompatibilities with captive portals on public Wi-Fi networks, unless the platform offers a solution for authenticating to them.

Using an optional VPN allows users to disable the VPN and evade [protective monitoring and auditing](https://www.ncsc.gov.uk/collection/mobile-device-guidance/logging-and-protective-monitoring) services. This increases the risk of mobile devices being attacked over the network, and of users circumventing corporate policy restrictions.

### **Initiating a VPN connection**

To provide benefits, a VPN must establish a connection, remain connected while the device is in use, and reconnect if the connection is temporarily lost. Typically, there are three ways of implementing this behaviour: automatic, triggered, and manual.

-   Automatic VPNs are brought up by the device whenever a network connection is requested by software on the device.
-   Triggered VPNs are brought up whenever certain network connections from a defined list are made (internal intranet sites, for example).
-   Manual VPNs require the user of the device to initiate the VPN by explicitly deciding to take an action (such as launching an application and clicking connect). The user will likely need to take this step again if the connection drops during or after use.

### **Distinguishing automatic from forced VPNs**

We distinguish automatic from forced because on some platforms it is possible for the user to disable the automatic VPN, whilst the platform still enforces VPN routing. This effectively prevents network connections from the device until the user re-enables automatic connections.

Depending on whether the VPN is forced or optional, choosing between automatic, triggered and manual could be a usability decision rather than security.

If the VPN is forced, but the initiation is manual, this will be a poor user experience as the device will not have any connectivity until the user manually starts the VPN. Conversely, if the VPN is optional, and the initiation is manual, then there is a risk of compromise from local attackers on an untrusted network, during the period when the device is not connected.

We advise you to use an automatic VPN, and where possible our per-platform guidance outlines a way of achieving this.

### **Full-device vs per-app VPN**

Some operating systems and many third-party applications allow you to configure only certain applications to use a VPN on the device. This is mostly useful in a [Bring Your Own Device (BYOD) scenario](https://www.ncsc.gov.uk/collection/mobile-device-guidance/bring-your-own-device), where enterprises do not want network traffic from personal apps to traverse the corporate network. This approach can be used to prevent malicious personal apps attacking the corporate network, or to limit bandwidth consumption from data-intensive personal apps. A per-app VPN also enables latency-sensitive apps (such as VoIP applications) to avoid any increase in network latency from the VPN.

However, if deploying in this way, you need to define all the applications you want protected by the VPN in advance. As this is generally used in a BYOD scenario, users can always download another application to work around the per-app VPN restrictions. In some cases, it may not be possible to force system applications to use a per-app VPN.

Our per-platform guidance recommends - and provides a configuration for - setting up a full-device VPN. Using a per-app VPN increases the risk that sensitive data may be sent outside the VPN by an application that is not included in a per-app VPN, or by a misconfiguration in the platform.

### **Split tunnelling**

Like a per-app VPN, split tunnelling is a way of having some traffic use the VPN, whilst other traffic is permitted direct connectivity. This is generally achieved by only defining certain network routes (e.g. internal IP address ranges) as available via the VPN. The default gateway for all other traffic is then left as a direct connection.

This is generally used when the VPN is providing access to internal services on a corporate network, without attempting to prevent other connections. For example, high-bandwidth applications could be permitted direct access to the internet without being routed via corporate infrastructure, to save on bandwidth costs. And, as with per-app VPNs, latency-sensitive applications, such as a VoIP client, could minimise network latency by connecting directly.

Split tunnelling is generally not supported on native VPN clients, which typically have relatively simple configuration options. Windows operating systems can be configured to split tunnel by the VPN's CSPv2 XML. However, on other platforms, clients built into smartphones and tablets rarely support this configuration. Third-party clients are sometimes able to support this option.

Enabling split tunnelling increases the risk that sensitive data will be exposed to an unprotected network, and could enable external attackers to access internal resources by ‘pivoting’ through the mobile device. In a scenario where you are relying on the VPN to route traffic for protective monitoring or duty of care reasons, enabling split tunnelling will undermine the benefit gained from those protections.

### **Managed tunnels**

If there are specific services that you want to access outside of the VPN, you can do this through the use of managed tunnels. This involves traffic to that particular endpoint being sent outside of the configured VPN. Sensible reasons for doing this include reduction of the load on networks caused by video conferencing services or where the function of an application requires it to communicate directly on the network, such as Wi-Fi captive portal helpers.

We only recommend the use of managed tunnels in situations where the provider of the service that will be connected to outside the tunnel, provides:

1.  Information demonstrating that connections to the service are protected as well as they would be by the VPN (e.g. the use of mutual TLS authentication).
2.  Definitive statements that the service uses dedicated IP endpoints, so that only traffic to that specific service will pass outside of the VPN.

**And** where there’s a business requirement for users to access the service outside of the VPN - i.e. high-bandwidth services such as those [used for video conferencing](https://www.ncsc.gov.uk/guidance/video-conferencing-services-security-guidance-organisations). We would also recommend this approach to enable Wi-Fi captive portal helpers to function

### **Captive portals**

Captive portals are the login pages present on some public Wi-Fi networks. To use a captive portal, the device is required to establish a direct connection from a web browser to the portal before it has established a VPN connection. For this, one of two things must be configured

**Either:**

1\. The user can disable any forced VPN configuration, so they can manually navigate to the portal in their main web browser.

**Or**

2\. The platform itself can detect the presence of a captive portal and present the user with a captive portal assistant application to authenticate with before re-establishing the VPN. Some platforms, such as iOS and macOS have such an application built in. Assistants are available as a third-party application for some other platforms, such as Windows 10. We include a link to one we have developed in our [Windows 10 guidance](https://www.ncsc.gov.uk/collection/mobile-device-guidance/platform-guides).

The use of a captive portal assistant application is less risky and should be preferred if captive Wi-Fi networks are to be used. The risks of disabling forced VPNs are described earlier in this guidance.

---

## Wider considerations

There are certain issues which are not directly related to the configuration of the VPN, but which will be affected by your choice of technologies and configurations, as outlined in the previous section.

There are certain issues which are not directly related to the configuration of the VPN, but which will be affected by your choice of technologies and configurations, as outlined in the previous section.

### **Client and Server security updates**

As with all software, both the client and server component will need to be regularly updated. On devices where the client is integrated into the operating system, these updates will naturally happen as a result of regular platform updates. Third-party software will need to be updated in some other way.

VPN services will be part of the internet-exposed attack surface of your organisation, so will need to be swiftly updated as soon as security patches are released

### **Tethering to devices with a VPN**

Tethering, or mobile hotspots, involve connecting an external device to your smartphone in order to use the smartphone’s internet connection.

However, full-device VPNs can often have an impact on how tethering works on the underlying platform. Some platforms will route tethered devices’ connections outside of the smartphone’s VPN connection, while some smartphones will not route tethered traffic if there is a full-device VPN connected. If your users rely on tethering, an appropriate configuration should be selected to enable it.

---

## How to use a VPN

There are two components to decide on: the Client and the Server.

You may wish to use the same vendor for both components, or adopt an open standard and use different vendors. Regardless, you should consider each aspect of VPN configuration described above.

The NCSC recommends:

-   Use the **IPsec** protocol to give you the flexibility to choose from a wide variety of inter-operable products.
-   Use **certificate authentication**. Store private keys in hardware-protected storage (TPM or TEE) if possible.
-   Use the **native client** for your particular platform(s), if possible.
-   Use a **forced VPN** to ensure apps cannot evade enterprise monitoring solutions (if you use them).
-   Use a VPN which **automatically connects**, so the device user is not required to manually enable it.
-   Use a **full-device** VPN and **avoid split tunnelling** to minimise the risk of data leaking outside the VPN.
-   Use the platform's built-in captive portal helper, if there is one, or deploy a third-party one.
-   Follow the NCSC's recommended cryptographic profiles for [IPsec](https://www.ncsc.gov.uk/guidance/using-ipsec-protect-data) or [TLS](https://www.ncsc.gov.uk/guidance/tls-external-facing-services), as appropriate.

The NCSC recommends that you test several VPNs to find which meet your requirements, are robust and resilient. As devices configured as suggested here will be largely unusable if the VPN service has an outage. It's especially important that the architecture is resilient and has backup options, if components within the service fail.