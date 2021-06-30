---
title: Google Workspace security review
description: Google Workspace is a collection of productivity tools including spreadsheets, word processing and calendar.
published: true
date: 2021-06-30T20:55:59.180Z
tags: bronze, saas-security, saas
editor: markdown
dateCreated: 2021-06-30T20:52:08.243Z
---

| **Question** | **Answer** | **Detail** |
| --- | --- | --- |
| Does the SaaS provider protect external data in transit using TLS? | Yes | According to Google's [encryption white paper](https://storage.googleapis.com/gfw-touched-accounts-pdfs/google-encryption-whitepaper-gsuite.pdf) G Suite uses TLS 1.2 with Perfect Forward Secrecy by default. |
| Does the SaaS provider protect external data in transit using correctly configured certificates? | Yes | G Suite meets the Recommended cryptographic profiles for TLS as published by the BCSF. In addition, the G Suite domain currently gets an ['A' rating from Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=gsuite.google.com). Note that this was performed on their top level domain, and not all subdomains that may be used for API calls. |
| Does the SaaS provider protect internal data in transit between services using encryption? | Yes | According to their [security FAQ](https://gsuite.google.com/faq/security/) Google encrypts all traffic in transit within their network. |
| Does the SaaS provider protect internal data in transit between services using correctly configured certificates? | Yes | Section 1 of Google's [published](http://services.google.com/fh/files/blogs/uk-cloud-security-principles-and-google-cloud-oct-2017.pdf) response to the *NCSC*'s Cloud Security Principles confirms that data is protected with TLS 1.2 with Perfect Forward Secrecy between internal services and APIs. |
| If APIs are available, does the SaaS provider protect both internal and external APIs through an authentication method? | Yes | All API requests [must be authorized by the user and use OAuth](https://developers.google.com/apps-script/guides/services/authorization). |
| If there is a concept of privilege levels in the service, does the SaaS provider have the ability for low privilege users to be created? | Yes | Users can have one of several roles with varying levels of permissions. Google provides a set of prebuilt admin roles, or you can create your own. This is described in the [G Suite documentation](https://support.google.com/a/answer/2405986?hl=en). |
| If there is a concept of privilege levels, does the SaaS provider provide 2FA/multi-factor authentication on at least the high privileged accounts? | Yes | G Suite currently [provides multi-factor authentication via SMS or any app that supports TOTP](https://support.google.com/a/answer/184711?hl=en) (Such as Google Authenticator). This can be enforced by Administrators for users within their domain. G Suite also [integrates with Single Sign On (SSO)](https://support.google.com/a/answer/60224?hl=en) options each of which may provide 2FA options. [Google's website describes how to enable their 2FA options](https://www.google.com/landing/2step/). |
| Does the SaaS provider collect logs of events?<br><br>*Types of log may include security logs and resource logs* | Yes | Google stores a variety of logs - these are made available to a domain administrator. [Google's support pages provide an overview of the logging services](https://support.google.com/a/answer/4579579?hl=en). |
| Does the provider make logs available to the client? | Yes | G Suite [makes a variety of logs available to administrators](https://support.google.com/a/answer/4580120?hl=en&ref_topic=3259623), including areas such as login and administrator actions. |
| Does the SaaS provider have a clear incident response and patching system in place to remedy any publicly reported issues in their service, or libraries that the service makes use of?<br><br>*The provider’s previous track record on this is a good metric to see how they’ll cope with a new issue occurring.* | Yes | Google has a dedicated security research team (Project Zero) according to their [white paper](https://static.googleusercontent.com/media/gsuite.google.com/en//intl/en/files/google-apps-security-and-compliance-whitepaper.pdf), who attempt to find vulnerabilities in their service. They also have a public bug bounty program. Google have also published their [Application Security Policy](https://www.google.com/about/appsecurity/) which details how they handle vulnerability reporting and management. |
| Does the SaaS provider give clear and transparent details on their product and the implemented security features (i.e. how easy has it been to answer the above questions) ? | Yes | Google publishes details of their security architecture in their [white paper](https://static.googleusercontent.com/media/gsuite.google.com/en//intl/en/files/google-apps-security-and-compliance-whitepaper.pdf) and within the FAQs on their site. Google's SOC3 [audit report](https://storage.googleapis.com/gfw-touched-accounts-pdfs/2017-google-apps-system-SOC3-report.pdf) provides details around the implemented security features in their products. |

---

## Exporting data

For information on exporting data from the service, refer to the [G Suite Administrator Help](https://support.google.com/a/answer/100458?hl=en).