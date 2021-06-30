---
title: 11. External interface protection
description: All external or less trusted interfaces of the service should be identified and appropriately defended.
published: false
date: 2021-06-30T18:51:18.044Z
tags: silver, cloud-security-principles, silver training
editor: markdown
dateCreated: 2021-06-30T18:47:01.154Z
---

# 11\. External interface protection

All external or less trusted interfaces of the service should be identified and appropriately defended.

If some of the interfaces exposed are private (such as management interfaces) then the impact of compromise may be more significant.

You can use different models to connect to cloud services which expose your enterprise systems to varying levels of risk.

## **Goals**

You:

-   understand what physical and logical interfaces your information is available from, and how access to your data is controlled
-   have sufficient confidence that the service identifies and authenticates users to an appropriate level over those interfaces [(see Principle 10](/guidance/cloud-security-principle-10-identity-and-authentication))

### **Implementation – External interface protection**

Services can protect their data by limiting an attacker’s opportunity to connect. This can be done by only providing the service to a limited set of networks, locations or devices.

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Internet | Users connect to the service directly over the internet. | Since the service can be accessed from any internet connected device, attacks can be launched from anywhere. It is important therefore that the service provider has designed the external interfaces of their service to be robust to attack. The service provider should have a regime of continuous testing in place to ensure any publicly exposed interfaces remain secure. |
| Community network | Some cloud services (particularly community cloud services) may only connect directly to private community networks (e.g. the Public Services Network) | If the cloud service is dedicated for the community, and only accessible via the community network, the service is likely to be less exposed to remote attackers. For an attacker to target your connection into the cloud service they would need to have access to the community network, through being part of the community or through having compromised someone who is. |
| Private network | Some services may provide dedicated connections in to your network. | Depending on the service design, attackers targeting cloud services only exposed to private networks may be forced to first compromise a private network.<br><br>However if the service also offers internet connectivity, then you should also review the guidance above. |

### **Additional notes – Authentication in external interfaces**

Internet accessible services, particularly those which accept connections from any location, are more exposed to attacks, so having high confidence in the strength of authentication and access control will be particularly important.

[Principle 10](/guidance/cloud-security-principle-10-identity-and-authentication) details common approaches to identification and authentication and explains the risks associated with each.
