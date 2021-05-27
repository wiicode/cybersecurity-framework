---
title: 6. Personnel security
description: Where service provider personnel have access to your data and systems you need a high degree of confidence in their trustworthiness. 
published: true
date: 2021-05-27T20:55:51.277Z
tags: silver, cloud-security-principles, silver-training
editor: markdown
dateCreated: 2021-02-22T01:38:04.727Z
---

# 6\. Personnel security

Where service provider personnel have access to your data and systems you need a high degree of confidence in their trustworthiness. Thorough screening, supported by adequate training, reduces the likelihood of accidental or malicious compromise by service provider personnel.

The service provider should subject personnel to security screening and regular security training. Personnel in these roles should understand their responsibilities. Providers should make clear how they screen and manage personnel within privileged roles.

## Goals

You should be confident that:

-   the level of security screening conducted on service provider staff with access to your information, or with ability to affect your service, is appropriate
-   the minimum number of people necessary have access to your information or could affect your service

### **Implementation - Personnel security**

| **Approach** | **Description** | **Guidance** |     |
| --- | --- | --- | --- |
| Personnel screening not performed | Some organisations may be unwilling or unable to perform personnel screening checks. | Unscreened individuals may have the ability to access your information or affect your service. |     |
| Personnel screening performed but does not conform with BS7858:2012 | [BS7858:2012](https://www.ncsc.gov.uk/guidance/cloud-security-standards-and-definitions) sets out a basic standard for personnel screening. Many multinational companies will perform background checks on staff that encompass the requirements of this standard, though in some countries it is not possible to perform all of the checks. | In these cases we recommend you ask the service provider to describe the personnel security screening functions they carry out on staff with access to your data, or the ability to affect user services. You will need to make a judgement over whether that is sufficient.<br><br>Where service providers are unable to verify the identity, check for unspent criminal convictions, and right to work of staff there is an increased risk of insider threat. | ## ! |
| Personnel screening performed which conforms to BS7858:2012 | Personnel screening is in place which includes or exceeds the requirements of [BS7858:2012](https://www.ncsc.gov.uk/guidance/cloud-security-standards-and-definitions). | Whilst personnel screening is valuable, it’s worth noting that it’s extremely difficult to design systems capable of defending data from attack by a privileged user who is both skilled and motivated.<br><br>It is likely that service provider personnel with privileged roles will be able to gain access to your data and/or affect the reliability of your service.<br><br>If possible, you may find it valuable to understand the service provider’s approach to detecting potential malicious insiders and use this information as part of your risk management decision. |     |

### **Additional information - Authenticating and securing service administration**

Anyone working for the service provider who has access to your data, or has the ability to affect your service needs to be strongly authenticated. They also need to administer your use of the service in a secure manner. It is worth considering these users as a special case when you review [Principle 10 - Identity and authentication](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/identity-and-authentication), and whether they will administer the service securely as part of [Principle 12 - Secure service administration](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/secure-service-administration).