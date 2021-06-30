---
title: 12. Secure service administration
description: Systems used for administration of a cloud service will have highly privileged access to that service.
published: false
date: 2021-06-30T18:51:37.871Z
tags: silver, cloud-security-principles, silver training
editor: markdown
dateCreated: 2021-06-30T18:47:03.777Z
---

# 12\. Secure service administration

Systems used for administration of a cloud service will have highly privileged access to that service. Their compromise would have significant impact, including the means to bypass security controls and steal or manipulate large volumes of data.

The design, implementation and management of administration systems should follow enterprise good practice, while recognizing their high value to attackers.

## Goals

You should:

-   understand which service administration model is being used by the service provider to manage the service
-   be content with any risks the service administration model in use brings to your data or use of the service

### **Implementation - Secure service administration**

*This table references our guidance on the* [*five basic systems administration models*](/guidance/systems-administration-architectures)

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Unknown service management architecture | The service provider has not disclosed this information. | In this case it would be prudent to assume that the risks associated with the *Direct service administration* approach are present. |
| Known service management architecture | The service provider has identified [which systems administration model](/guidance/systems-administration-architectures) is used to administer the service. | To understand the risks associated with different systems administration models see the corresponding row in [our guide](/guidance/systems-administration-architectures).<br><br>The level of assurance you have that the service provider’s assertions are correct can vary. You can obtain independent assurance from a suitably qualified security architect. |
| Other | The service provider may believe that their systems administration approach is not covered by one of the models described in [our guide](/guidance/systems-administration-architectures). | In this case it will be for you to make your own assessment about the risks associated with the service provider's administration approach. |

### **Additional notes – Protecting administration devices**

An important aspect of securing privileged administration interfaces is the security of the end user devices used for administration. It is important for you, as well as the service provider, to ensure that devices used for particularly privileged activities as well protected. For example, they should not be used for directly browsing the web or reading email, as these are high risk activities for someone to perform from a device used for administration.