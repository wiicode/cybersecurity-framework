---
title: 7. Secure development
description: Services should be designed and developed to identify and mitigate threats to their security. Those which aren’t may be vulnerable to security issues which could compromise your data, cause loss of service or enable other malicious activity.
published: true
date: 2021-05-27T21:58:13.983Z
tags: silver, cloud-security-principles, silver-training
editor: markdown
dateCreated: 2021-02-22T01:38:56.609Z
---

# 7\. Secure development

Services should be designed and developed to identify and mitigate threats to their security. Those which aren’t may be vulnerable to security issues which could compromise your data, cause loss of service or enable other malicious activity.

## Goals

*You should be confident that:*

-   New and evolving threats are reviewed and the service improved in line with them.
-   Development is carried out in line with industry good practice regarding secure design, coding, testing and deployment.
-   Configuration management processes are in place to ensure the integrity of the solution through development, testing and deployment.

### **Implementation – Secure development**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Engineering approaches consider security as an important factor | The service provider asserts that they implement a number of controls to ensure the security of their service. | In this scenario you will need to carry out your own assessment of whether the controls in place are appropriate. |
| Engineering approach adheres to a secure development standard or recognized good practice | A number of security standards or good practice guides exist which service providers could claim support their achievement of the goals outlined above. These include:<br><br>-   Safecode ‘Fundamental Practices for Secure Software Development’<br>-   [ISO/IEC 27034](#) | It’s reassuring that the service provider claims to implement one of these standards, but without independent confirmation of that you will need to make a judgement on whether that gives you sufficient confidence in whether all parts of the system are securely engineered. |
| Independent review of engineering approach against recognized secure development standard | A number of security standards with supporting certification mechanisms exist which could be used to demonstrate conformance with the goals outlined above. These include:<br><br>-   [CPA Build Standard](#)<br>-   [ISO/IEC 27034](#)<br>-   [ISO/IEC 27001](#)<br>-   [CSA CCM v3.0](#) | It's advisable to check that any certification has been performed by an appropriately independent and recognized party and that the scope of the assessment included the incident management aspects required. |

### **Additional notes – Secure development requirements**

Secure development does not mean that all development must be done in-house, at secure facilities or by highly vetted personnel. Whilst these approaches may be appropriate for specialised components, it will often be better to choose mature, independently supported, off the shelf components.

Security should be considered throughout the design and development of the service. For example, during development of new features, potential attacks should be evaluated and effective mitigations designed to address them. Care must be taken to balance security, cost and usability.

Service providers should ensure when they purchase services, software components or development services from third parties, that the development practices of the supplier are suitably secure. This should be achieved through an established supply chain process (see below).