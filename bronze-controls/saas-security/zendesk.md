---
title: Zendesk security review
description: Zendesk is a ticketing system whose primary aim is to improve customer relations. It offers the ability to create, handle and track tickets, supported by multiple platforms. It also keeps a record of all communication for every ticket.
published: true
date: 2021-06-30T20:55:16.158Z
tags: bronze, bronze-controls, saas-security, saas
editor: markdown
dateCreated: 2021-06-30T20:48:15.415Z
---

Zendesk is a ticketing system whose primary aim is to improve customer relations. It offers the ability to create, handle and track tickets, supported by multiple platforms. It also keeps a record of all communication for every ticket.

| **Question** | **Answer** | **Detail** |
| --- | --- | --- |
| Does the SaaS provider protect external data in transit using TLS? | Yes | Zendesk uses HTTPS to transmit and receive data. TLS 1.2 is used to encrypt data whilst in transit between Zendesk servers and the user’s browser. |
| Does the SaaS provider protect external data in transit using correctly configured certificates? | Yes | Zendesk meets the recommended cryptographic profiles for TLS as published by the BCSF. In addition the Zendesk domain currently gets an '[A' rating from Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=zendesk.com). Note that this was performed on their top level domain, and not all subdomains that may be used for API calls. |
| Does the SaaS provider protect internal data in transit between services using encryption? | Unknown | At this time, it is unknown whether Zendesk protects internal data in transit using encryption. |
| Does the SaaS provider protect internal data in transit between services using correctly configured certificates? | Unknown | At this time, it is unknown whether Zendesk protects internal data in transit using correctly configured certificates. |
| If APIs are available, does the SaaS provider protect both internal and external APIs through an authentication method? | Yes | Zendesk only allows [verified users](https://developer.zendesk.com/rest_api/docs/core/introduction?_ga=1.100574360.784646381.1488377881#security-and-authentication) to make API requests. |
| If there is a concept of privilege levels in the service, does the SaaS provider have the ability for low privilege users to be created? | Yes | [Multiple roles](https://support.zendesk.com/hc/en-us/articles/203661776-Understanding-Zendesk-Support-user-roles) are available within the support user roles and end-users. |
| If there is a concept of privilege levels, does the SaaS provider provide 2FA/multi-factor authentication on at least the high privileged accounts? | Yes | Zendesk currently provides [2FA](https://support.zendesk.com/hc/en-us/articles/206373587-Using-2-factor-authentication) when using standard Zendesk support authentication. It is not available for agents or administrators using Google Authentication Services, JWT or SAML. However, other third-party applications can be employed when using these services. Zendesk also supports [SSO](https://support.zendesk.com/hc/en-us/articles/203663826-Single-sign-on-SSO-options-in-Zendesk) (Single Sign On). |
| Does the SaaS provider collect logs of events?<br><br>*Types of log may include security logs and resource logs* | Yes | Zendesk states that logging is performed by their [Security Incident Event Management (SIEM)](https://www.zendesk.com/product/zendesk-security/) System. These logs are then sent to the security teams who respond to triggered events. |
| Does the provider make logs available to the client? | Yes | Zendesk offers administrators access to audit logs. A full breakdown of the information they can see is available from the [Zendesk developer site](https://developer.zendesk.com/rest_api/docs/core/audit_logs). |
| Does the SaaS provider have a clear incident response and patching system in place to remedy any publicly reported issues in their service, or libraries that the service makes use of?<br><br>*The provider’s previous track record on this is a good metric to see how they’ll cope with a new issue occurring.* | Yes | Zendesk have an on call [24/7 security team](https://www.zendesk.com/product/zendesk-security/). Alongside this, Zendesk offer a bug bounty program via [HackerOne](https://hackerone.com/zendesk). |
| Does the SaaS provider give clear and transparent details on their product and the implemented security features (i.e. how easy has it been to answer the above questions) ? | Yes | Zendesk answer most security questions through [various pages on their website](https://www.zendesk.com/product/zendesk-security/). |



## Exporting data

Data can be exported from Zendesk in CSV or XML form by the administrator in versions Professional and Enterprise. A request can be put in for export of ticket data (CSV format) or user data (XML format) or a full data export (XML format). This feature is not activated by default, to enable the service the user must contact [support@zendesk.com](mailto:support@zendesk.com). More information on this can be found in the [Zendesk documentation](https://support.zendesk.com/hc/en-us/articles/203662346-Exporting-data-to-a-CSV-or-XML-file-Professional-and-Enterprise-).