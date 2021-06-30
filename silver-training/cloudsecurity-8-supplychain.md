---
title: 8. Supply chain security
description: The service provider should ensure that its supply chain satisfactorily supports all of the security principles which the service claims to implement.
published: false
date: 2021-06-30T18:50:10.811Z
tags: silver, cloud-security-principles, silver training
editor: markdown
dateCreated: 2021-06-30T18:47:23.883Z
---

# 8\. Supply chain security

The service provider should ensure that its supply chain satisfactorily supports all of the security principles which the service claims to implement.

Cloud services often rely upon third party products and services. Consequently, if this principle is not implemented, supply chain compromise can undermine the security of the service and affect the implementation of other security principles.

## Goals

You understand and accept:

-   How your information is shared with, or accessible to, third party suppliers and *their* supply chains.
-   How the service provider’s procurement processes place security requirements on third party suppliers.
-   How the service provider manages security risks from third party suppliers.
-   How the service provider manages the conformance of their suppliers with security requirements.
-   How the service provider verifies that hardware and software used in the service is genuine and has not been tampered with.

### **Implementation – Supply chain security**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Commitments | The service provider reassures you that the security controls which are important to you are transited through their supply chain | In this scenario you will need to carry out your own assessment of whether the controls in place are appropriate. |
| Assessed through application of appropriate standard | Security controls are implemented in the supply chain through the application of a relevant standard.<br><br>A number of security standards with supporting certification mechanisms exist. These include:   <br>[ISO/IEC 27001](#)   <br>[ISO/PAS 28000:2007](#) | It is advisable to check that any certification has been performed by an appropriately independent and recognized party and that the scope of the assessment included the supply chain aspects required. |

### **Additional notes – Layered services**

Cloud services are often built on top of third party IaaS or PaaS products. This is a valuable opportunity to reuse trusted components, but it’s important to identify which party is responsible for implementing which security functions.

These layered services may result in a more complex situation when it comes to understanding [separation](#). For example, a community SaaS may separate different users with application software controls. However, it may have been built on top of a public cloud IaaS offering, where the separation controls are implemented in the hypervisor. Thus the actual controls may be different in practice to what they first appear.

If your application or data is particularly sensitive, you will need to consider the entire underlying stack of services as part of any security assessment. It will be difficult to gain a high degree of confidence in the security of any service built on foundations you do not understand.