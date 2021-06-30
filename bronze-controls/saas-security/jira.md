---
title: Jira security review
description: Atlassian Jira is an issue tracking and planning tool, primarily aimed at software development.
published: true
date: 2021-06-30T20:55:53.251Z
tags: bronze, saas-security, saas
editor: markdown
dateCreated: 2021-06-30T20:53:16.691Z
---

| **Question** | **Answer** | **Detail** |
| --- | --- | --- |
| Does the SaaS provider protect external data in transit using TLS? | Yes | Atlassian uses [TLS 1.2 and perfect forward secrecy](https://www.atlassian.com/trust/faq) to protect external data. |
| Does the SaaS provider protect external data in transit using correctly configured certificates? | Yes | Atlassian meets the recommended cryptographic profiles for TLS as published by the BCSF. In addition, the Atlassian Jira domain currently gets an ['A' rating from Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=atlassian.net). Note that this was performed on their top level domain, and not all subdomains that may be used for API calls. |
| Does the SaaS provider protect internal data in transit between services using encryption? | Yes | In Atlassian's [Consensus Assessment Initiative Questionnaire (CAIQ)](https://cloudsecurityalliance.org/star-registrant/atlassian/), they state that the Atlassian Cloud Platform uses SSH for data and images transported between networks. |
| Does the SaaS provider protect internal data in transit between services using correctly configured certificates? | Unknown | At this time, it is unknown whether Atlassian protects external data in transit using correctly configured certificates. |
| If APIs are available, does the SaaS provider protect both internal and external APIs through an authentication method? | Yes | Jira offers basic authentication, OAauth and JWTs to protect its external [REST API.](https://developer.atlassian.com/cloud/jira/platform/jira-cloud-platform-rest-api/) |
| If there is a concept of privilege levels in the service, does the SaaS provider have the ability for low privilege users to be created? | Yes | Jira provides the ability to create both [groups and roles](https://confluence.atlassian.com/adminjiracloud/managing-project-roles-776636382.html). |
| If there is a concept of privilege levels, does the SaaS provider provide 2FA/multi-factor authentication on at least the high privileged accounts? | Yes | Atlassian [supports](https://confluence.atlassian.com/cloud/secure-your-account-with-two-step-verification-939505063.html) both the use of SMS codes as well as OTP applications to provide a second factor for authentication. |
| Does the SaaS provider collect logs of events?<br><br>*Types of log may include security logs and resource logs* | Yes | Jira's [auditing feature](https://confluence.atlassian.com/adminjiraserver071/auditing-in-jira-applications-802593030.html) tracks key activities in Jira applications. These activities are recorded in an audit log that can be viewed in the Jira administration console. |
| Does the provider make logs available to the client? | Unknown | At this time, it is unknown whether Atlassian provide logs to the client. |
| Does the SaaS provider have a clear incident response and patching system in place to remedy any publicly reported issues in their service, or libraries that the service makes use of?<br><br>*The provider’s previous track record on this is a good metric to see how they’ll cope with a new issue occurring.* | Yes | Atlassian indicate on their CAIQ that they have a clear incident response and patching system for all their services. They also have a [responsible disclosure](https://www.atlassian.com/trust/security) program. |
| Does the SaaS provider give clear and transparent details on their product and the implemented security features (i.e. how easy has it been to answer the above questions) ? | Yes | Atlassian's CAIQ is available to view and they have published a list of [Trust FAQs](https://www.atlassian.com/trust/faq). |

---

## Exporting data

Jira allows an administrator to [backup and export](https://confluence.atlassian.com/adminjiraserver072/importing-and-exporting-data-829827150.html) the following:

-   issues
-   users and user group settings
-   issue attachments, user avatars, and project logos (if selected)