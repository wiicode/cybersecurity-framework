---
title: Confluence security review
description: Atlassian Confluence is a group collaborative writing tool.
published: true
date: 2021-06-30T20:55:29.812Z
tags: bronze, saas-security, saas
editor: markdown
dateCreated: 2021-06-30T20:54:21.255Z
---

| **Question** | **Answer** | **Detail** |
| --- | --- | --- |
| Does the SaaS provider protect external data in transit using TLS? | Yes | Atlassian uses [TLS 1.2 and Perfect Forward Secrecy](https://www.atlassian.com/trust/faq) to protect external data. |
| Does the SaaS provider protect external data in transit using correctly configured certificates? | Yes | Atlassian meets the Recommended cryptographic profiles for TLS as published by the BCSF. In addition, the Confluence domains currently get an '[A' rating from Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=atlassian.net). Note that this was performed on their top level domain, and not all subdomains that may be used for API calls. |
| Does the SaaS provider protect internal data in transit between services using encryption? | Yes | In Atlassian's [Consensus Assessment Initiative Questionnaire (CAIQ)](https://cloudsecurityalliance.org/star-registrant/atlassian/), they state that the Atlassian Cloud Platform uses SSH for data and images transported between networks. |
| Does the SaaS provider protect internal data in transit between services using correctly configured certificates? | Unknown | At this time, it is unknown whether Atlassian protects internal data in transit using correctly configured certificates. |
| If APIs are available, does the SaaS provider protect both internal and external APIs through an authentication method? | Yes | Confluence allows Basic access authentication and JWT [for all its API REST calls](https://developer.atlassian.com/static/connect/docs/latest/concepts/authentication.html). |
| If there is a concept of privilege levels in the service, does the SaaS provider have the ability for low privilege users to be created? | Yes | Confluence has a number of different [roles](https://confluence.atlassian.com/doc/global-permissions-overview-138709.html) within a site structure. |
| If there is a concept of privilege levels, does the SaaS provider provide 2FA/multi-factor authentication on at least the high privileged accounts? | Yes | Confluence [supports](https://confluence.atlassian.com/cloud/secure-your-account-with-two-step-verification-939505063.html) both the use of SMS codes as well as OTP applications to provide a second factor for authentication. |
| Does the SaaS provider collect logs of events?<br><br>*Types of log may include security logs and resource logs* | Yes | Atlassian provide an [audit log](https://confluence.atlassian.com/confcloud/audit-log-802164269.html) from the service which keep a record of important events, such as changes to global permissions. |
| Does the provider make logs available to the client? | Unknown | At this time, it is unknown whether Atlassian provide logs to the client. |
| Does the SaaS provider have a clear incident response and patching system in place to remedy any publicly reported issues in their service, or libraries that the service makes use of?<br><br>*The provider’s previous track record on this is a good metric to see how they’ll cope with a new issue occurring.* | Yes | Atlassian indicate on their CAIQ that they have a clear incident response and patching system for all their services. They also have a [responsible disclosure](https://www.atlassian.com/trust/security) program. |
| Does the SaaS provider give clear and transparent details on their product and the implemented security features (i.e. how easy has it been to answer the above questions) ? | Yes | Atlassian's CAIQ is available to view and they have published a list of [Trust FAQs](https://www.atlassian.com/trust/faq). |

---

## Exporting data

-   "You can [export all or part of a Confluence space](https://confluence.atlassian.com/doc/export-content-to-word-pdf-html-and-xml-139475.html) to various formats, including Microsoft Word, HTML, PDF and XML."
-   "To use the space export functionality, you need the 'Export Space' permission. See the guide to [space permissions](https://confluence.atlassian.com/doc/space-permissions-overview-139521.html)."