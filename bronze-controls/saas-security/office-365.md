---
title: Office 365 security review
description: Microsoft Office 365 is a set of cloud-based productivity tools including word processing, spreadsheets and calendars
published: true
date: 2021-06-30T20:56:26.559Z
tags: bronze, saas-security, saas
editor: markdown
dateCreated: 2021-06-30T20:50:56.521Z
---

| **Question** | **Answer** | **Detail** |
| --- | --- | --- |
| Does the SaaS provider protect external data in transit using TLS? | Yes | According to their [Trust Centre Documentation](https://www.microsoft.com/en-us/trustcenter/security/office365-security#Secure-infrastructure) Office 365 uses TLS. Even though it isn't explicitly stated, hands-on testing suggests that this is using TLS 1.2. |
| Does the SaaS provider protect external data in transit using correctly configured certificates? | Yes | Office 365 meets the recommended cryptographic profiles for TLS as published by the BCSF. In addition the Office domain currently gets an ['A' rating from Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=office.com). Note that this was performed on their top level domain, and not all subdomains that may be used for API calls. |
| Does the SaaS provider protect internal data in transit between services using encryption? | Yes | According to their [Trust Centre Documentation](https://www.microsoft.com/en-us/trustcenter/security/office365-security#Secure-infrastructure) Microsoft encrypts all traffic in transit within their network using TLS and IPSec. |
| Does the SaaS provider protect internal data in transit between services using correctly configured certificates? | Yes | According to their [Azure encryption overview](https://docs.microsoft.com/en-us/azure/security/security-azure-encryption-overview) Microsoft uses TLS to protect all traffic in transit between services. |
| If APIs are available, does the SaaS provider protect both internal and external APIs through an authentication method? | Yes | All API requests [must be authorized by the user and use OAuth](https://developer.microsoft.com/en-us/graph/docs/concepts/auth_v2_user). |
| If there is a concept of privilege levels in the service, does the SaaS provider have the ability for low privilege users to be created? | Yes | Users can have one of several roles with varying levels of permissions. Microsoft provides a set of prebuilt admin roles. This is described in the [Office 365 documentation](https://support.office.com/en-us/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d). |
| If there is a concept of privilege levels, does the SaaS provider provide 2FA/multi-factor authentication on at least the high privileged accounts? | Yes | Office 365 currently [provides multi-factor authentication via SMS or the Microsoft Authenticator app](https://support.office.com/en-gb/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6). This can be enforced by Administrators for users within their domain. Office 365 also [integrates with Single Sign On (SSO)](https://technet.microsoft.com/en-us/library/jj631606.aspx) options each of which may provide 2FA options. |
| Does the SaaS provider collect logs of events?<br><br>*Types of log may include security logs and resource logs* | Yes | As stated below, Microsoft stores a variety of logs - these are made available to a domain administrator. It is unknown as to the extent of internal logging. |
| Does the provider make logs available to the client? | Yes | Microsoft [makes a variety of logs available to administrators](https://support.office.com/en-gb/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c), this is all collated into an "audit log" including areas such as login and administrator actions on various individual parts of Office 365. |
| Does the SaaS provider have a clear incident response and patching system in place to remedy any publicly reported issues in their service, or libraries that the service makes use of?<br><br>*The provider’s previous track record on this is a good metric to see how they’ll cope with a new issue occurring.* | Yes | Microsoft has a dedicated security team, they also have a [public bug bounty program](https://technet.microsoft.com/en-us/security/dn425036). |
| Does the SaaS provider give clear and transparent details on their product and the implemented security features (i.e. how easy has it been to answer the above questions) ? | Yes | Microsoft publishes details of their security architecture in their [white paper](https://www.microsoft.com/en-us/download/details.aspx?id=26552) and within the FAQs and TechNet articles on their site. |



## Exporting data

For information on exporting data from Office 365, refer to the [Office 365 Trust Center](https://products.office.com/en-us/business/office-365-online-data-portability).