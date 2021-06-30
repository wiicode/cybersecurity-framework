---
title: Basecamp security review
description: Basecamp is a web-based project management and company-wide communication tool designed to improve the administration of small and large projects alike.
published: true
date: 2021-06-30T20:58:17.711Z
tags: bronze, saas-security, saas
editor: markdown
dateCreated: 2021-06-30T20:58:06.327Z
---

[Basecamp](https://basecamp.com/) is a web-based project management and company-wide communication tool designed to improve the administration of small and large projects alike. It offers a place for users to collaborate on projects through the uploading and sharing of documents within teams, as well as chat functionality and message boards for knowledge sharing amongst teams. Scheduling for meetings can also be managed within Basecamp, which integrates with third party email providers.

| **Question** | **Answer** | **Detail** |
| --- | --- | --- |
| Does the SaaS provider protect external data in transit using TLS? | Yes | Basecamp uses [HTTPS to transmit and receive data](https://basecamp.com/about/policies/security). [TLS 1.2 is used to encrypt data](https://basecamp.com/about/policies/privacy) whilst in transit between Basecamp's servers and the user’s browser. |
| Does the SaaS provider protect external data in transit using correctly configured certificates? | Yes | Basecamp meets the recommended cryptographic profiles for TLS as published by the BCSF. Basecamp currently gets an '[A' rating from SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=3.basecamp.com&latest). Note that this was performed on their top level domain, and not all subdomains that may be used for API calls. |
| Does the SaaS provider protect internal data in transit between services using encryption? | Unknown | At this time, it is unknown whether Basecamp protects internal data in transit between services using encryption. However, Basecamp does state that [project data, messages, text documents and TODOs are **not** encrypted at rest](https://basecamp.com/about/policies/security). |
| Does the SaaS provider protect internal data in transit between services using correctly configured certificates? | \>Unknown | At this time, it is unknown whether Basecamp protects internal data in transit using correctly configured certificates. |
| If APIs are available, does the SaaS provider protect both internal and external APIs through an authentication method? | Yes (version dependent) | All Basecamp 3 APIs enquire the use of [OAuth 2.0 for authentication](https://github.com/basecamp/bc3-api). All public integrations of Basecamp 2 require the use of [OAuth 2.0 for API authentication](https://github.com/basecamp/bcx-api). Basecamp 2 does support HTTP basic authentication for private integrations. Basecamp Classic does [**not** require the use of OAuth 2.0](https://github.com/basecamp/api/blob/master/sections/authentication.md). Public integrations of Basecamp Classic are compatible with OAuth 2.0, but do not require it. |
| If there is a concept of privilege levels in the service, does the SaaS provider have the ability for low privilege users to be created? | Yes (version dependent) | Basecamp offers various account [roles](https://basecamp.com/help/3/guides/account/adminland): Admin, Owner and Non-admin user accounts. |
| If there is a concept of privilege levels, does the SaaS provider provide 2FA/multi-factor authentication on at least the high privileged accounts? | Yes | Basecamp offers 2 factor authentication (2FA) in the form of ‘[Phone Verification](https://help.basecamp.com/sign-in/questions/460-how-do-i-set-up-and-use-phone-verification-for-logging-in) (SMS)’ for all users. In the event the user loses access to their phone, security questions are set during the 2FA setup process which the user can use to unlock their account. They also support sign-in via Google accounts which support non-SMS 2FA. |
| Does the SaaS provider collect logs of events? *Types of log may include security logs and resource logs* | Unknown | At this time, it is unknown whether Basecamp collects logs of events. |
| Does the provider make logs available to the client? | Partial | Currently, the only logs visible to Basecamp's clients are [uptime statistics](https://status.basecamp.com/) of each of the Basecamp versions. |
| Does the SaaS provider have a clear incident response and patching system in place to remedy any publicly reported issues in their service, or libraries that the service makes use of? *The provider’s previous track record on this is a good metric to see how they’ll cope with a new issue occurring.* | Yes | Basecamp have a [security response procedure](https://basecamp.com/about/policies/security/response) whereby they encourage security researchers to email them vulnerability details using their public key. From here, Basecamp will correspond with the bug finder until the issue is resolved. |
| Does the SaaS provider give clear and transparent details on their product and the implemented security features (i.e. how easy has it been to answer the above questions) ? | Yes | Basecamp publishes the majority of the answers to the above security questions. They have recently released a [security whitepaper](https://basecamp.com/about/policies/security) on their security pages, that bring together information covered above. |



## Exporting data

-   All Basecamp users in the consumer *organisation* have the ability to download individual documents that have been uploaded to projects.
-   Basecamp message posts can be copied out and pasted into a separate document, whilst making a note of the date and time it was posted.
-   Scheduling appointments can be downloaded in a variety of calendar formats so that users can add them to their calendar app of choice e.g. Outlook and Google Calendar.
-   Additionally Basecamp allows administrators to export and [download the entire *organisation*'s Basecamp](https://basecamp.com/help/2/guides/account/exports) dashboard for offline viewing.