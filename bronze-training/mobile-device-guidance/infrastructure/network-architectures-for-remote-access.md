---
title: Network architectures
description: Advice for network architects and systems administrators on the design of remote access architecture for enterprise services
published: true
date: 2021-06-02T21:04:51.042Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:55:47.973Z
---

When deciding how to enable remote users to access enterprise resources, there are a number of security issues to take into account. This guidance outlines two approaches to this problem, *a traditional VPN-based remote access architecture*, and *a zero trust architecture*. 

> If you have on-premises resources, using a **traditional VPN-based remote access architecture** - the *walled garden approach -* is one way of balancing remote usability with the risk of compromise.
{.is-success}


> If you have few or no on-premises services, the **zero trust architecture** can be very effective.
{.is-success}


These two approaches are not the only options for enabling remote access, nor are they mutually exclusive. A hybrid approach can be taken if required, adopting properties from each.

If a traditional remote access approach is necessary, adopting some of the principles and defenses from the *zero trust architecture* will help you mitigate additional threats, and make a transition to full *zero trust networking* easier in future.

# 1. Traditional VPN-based remote access architecture

The traditional remote access architecture separates a remote access architecture into a strong outer perimeter and multiple internal layers that are separated using firewalls. 


### **Key components**

At a high level, these layers of this *walled garden* are:

-   The access layer, authenticating remote devices. Network traffic from remote devices is trapped here unless it can subsequently authenticate to local services
-   The presentation layer, brokering access to internal services based on corporate policy
-   A core network, comprising of on-premise services
-   An internet gateway, providing proxy access to remote websites and enterprise cloud services

### **How to set up a traditional remote access architecture**

Firstly, if you are designing a new network, consider following the *zero trust network* approach instead. The traditional architecture still makes sense where there is a considerable on-premises deployment and/or legacy services to use. However, a *zero trust* approach will likely be better for organizations predominantly consuming cloud services.

With the traditional architecture, the solution – comprising all layers – should require both user and machine authentication before allowing access to enterprise services. Both of these should be tied together so that a particular user can only access their assigned device. Typically, the access layer will perform *machine* authentication, and the presentation layer will perform *user* authentication.

#### **Access layer**

Some deployments will have a single set of services that are accessible to all remote users (and hence be very simple in design), others will require more complex authentication and authorisation solutions to enable different remote users to access specific services, potentially depending on device type. Which services the user and device can access will depend on the rules enforced within the access layer.

The access layer should authenticate clients and terminate their virtual private network (VPN) connection. The access layer also provides defenses against network-level attack on internal services, from the Internet. These defenses may be included as part of the VPN service. If not, you may require a separate device, such as a firewall, on the network boundary, permitting only VPN traffic into the access layer.

Routing rules should be in place within the access layer to stop remote devices communicating with one another, unless explicitly required.

#### **Presentation layer**

The presentation layer presents a subset of enterprise services to devices, authenticating users as they connect to enterprise services.

If practically possible, you should attempt to provide a layer of abstraction between the remote device and your central services. This will usually involve breaking end-to-end encryption (as happens in a reverse proxy or load balancer). Examples include:

-   a read-only domain controller (RODC)
-   remote desktop/app services
-   a reverse authenticating proxy brokering access to an internal intranet site

The use of abstraction in the presentation layer lowers the risk of a network attack on enterprise services from a compromised device. Protective monitoring tools can be used here if required.

#### **Internet gateway**

Some organizations require proxy servers to intercept traffic for monitoring or to block access to internet services. An internet gateway is typically used to achieve this, and will use custom CA certificates deployed to devices to enable it to inspect encrypted traffic.

While organizations  might be required by legislation to monitor users' traffic in a gateway, protective monitoring, for security reasons, is often more effective when deployed to devices via security configuration (see [detailed platform guides](/collection/mobile-device-guidance/platform-guides)) or [security applications](/collection/mobile-device-guidance/antivirus-and-other-security-software). Several other reasons to use intercepting proxies are given in the [VPN guidance](/collection/mobile-device-guidance/virtual-private-networks).

# 2. Zero trust architecture

A zero trust architecture removes the inherent trust from the network while building confidence in each request. This is achieved through building context through strong authentication, authorisation, device health, and value of the data being accessed.

Each connection is strongly authenticated and checked against permissible policies, with the connection being dropped if it is not explicitly allowed.

This approach has many advantages if adopted correctly, but also presents additional risk if mistakes are made.

While this article will not go into detail about how to implement a *zero trust* approach, we will give some high-level recommendations.

### **Preparing for a zero trust architecture**

While the architectural components look much simpler in a zero trust network approach, it is still important to implement authentication and encryption mechanisms to the same or to a greater standard. It also becomes more important to have a [strong device configuration](/collection/mobile-device-guidance/platform-guides), as the device is exposed to a larger set of risks. This section details some things you should think about when developing a zero trust architecture.

#### **Single strong source of user identity**

User identities are the foundation of a zero trust approach. By consolidating users' roles into a single source of truth, you can build reliable rules for users accessing data. The usual approach would be to use a single user directory for your organization and create accounts that are linked to individuals. Then to enable granular access control you can create specific roles for each user. The directory can then be used across all services you plan to use, both internally and externally.

#### **User authentication**

Users should be [strongly authenticated](/collection/mobile-device-guidance/enterprise-authentication-policy), using multi-factor authentication to mitigate password attacks. The authentication should use an enterprise single sign on (SSO) service, which accesses your single source of user identity. This automates and simplifies credential management for users. It also simplifies your joiners/movers/leavers processes. 

#### **Machine authentication**

Machine authentication can take place at the same time as user authentication, and can be implicit. For example, a device issued to a single user, which itself performs user authentication can ‘pass along’ that trust to a service when it performs machine authentication.

Credentials used for machine authentication should be as tightly bound to the device as possible, using hardware protected storage (e.g. TPM). Private keys should be kept within the TPM and key attestation used, where possible.

#### **Additional context, such as policy compliance and device health**

Many authentication services can integrate with one or more mobile device management services to ensure that authenticating devices are compliant with corporate policy, before being allowed to access corporate data. This is typically implemented by issuing a short-lived certificate to devices which are compliant, and distributing the certificate using MDM. The certificate is then used for device authentication, implicitly asserting compliance.

Some authentication services are starting to include *device health attestation* as part of their compliance decision. This is a powerful technique which can be used to make strong assertions that a connecting device has booted securely and remains in a good state when accessing enterprise data. Device health attestation features should be enabled if they’re supported in your environment.

#### **Authorisation policies to access an application**

In the *traditional remote access architecture*, the presentation layer is used to restrict direct access to enterprise applications that should not be accessible to remote devices.

In the *zero trust network approach*, it is not possible to control network routing like this, so authorisation enforcement must be implemented elsewhere. Typically, this will be at the authentication point. This could achieved with a reverse proxy service in front of an enterprise application, or a single sign-on service, which issues tokens to access enterprise applications. In either case, the service would decline to authorize access to the application if the access request was not compliant with policy.

Authentication services might also require specific preconditions to be satisfied before access is granted to an enterprise application. For example, you can require multi-factor authentication for *some* of your enterprise applications but not others. Similarly, you may authorize out-of-date devices to access MDM, but not corporate email.

#### **Access control policies within an application**

Within an enterprise application, you may want to further control access to specific resources, using access control. Most services will allow you to grant access to specific authorized users, but a *zero trust network* approach also lets you incorporate more context into that access decision.

For example, you may wish to require multi-factor authentication before users can access sensitive corporate documents held in your file store. Meanwhile, single factor authorisation could be used for low security documents within the same file store. This might be beneficial in a *bring your own device* (BYOD) deployment, where personal devices may be allowed to access a subset of corporate data.

This model requires the authentication service to pass on details of the authorisation context to the enterprise application using technologies like [SAML](https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language) or [*OpenID Connect*](https://openid.net/connect/). This type of configuration is not currently widely implemented, so you should check what is supported with your authentication service and enterprise application provider.

### **How to set up a zero trust network**

If you choose to develop a zero-trust architecture, keep in mind that:

-   Zero trust networking is relatively new and best practices are likely to evolve over time. It’s important to regularly revisit your approach to ensure that you’re taking advantage of the latest features and your policies are still effective.
-   Your enterprise applications are now exposed beyond your perimeter. Each one of your internet-accessible services needs to be hardened against attack. You should follow best practices for deployments in the cloud, as well as ensuring that each service requires strong user and machine authentication.
-   Implement strong user authentication, requiring multi-factor authentication for ***every*** exposed service, including management services. Consider using password-less authentication to mitigate attacks on your users’ passwords.
-   Implement machine authentication, with credentials rooted in hardware, taking into account compliance and health attestation, if possible.
-   Monitor logs from authentication services and enterprise applications.

Where a full zero trust network approach cannot be adopted, implement the traditional remote access architecture and as many *zero trust networking* recommendations as possible.