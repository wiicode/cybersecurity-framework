---
title: Mailchimp security review
description: MailChimp is an email service provider which allows users to send automated messages, marketing emails and targeted campaigns.
published: true
date: 2021-06-30T20:59:13.611Z
tags: bronze, saas-security, saas
editor: markdown
dateCreated: 2021-06-30T20:59:05.860Z
---

| **Question** | **Answer** | **Detail** |
| --- | --- | --- |
| Does the SaaS provider protect external data in transit using TLS? | Yes | MailChimp uses TLS 1.2 but only specifies SSL within their documentation. |
| Does the SaaS provider protect external data in transit using correctly configured certificates? | Yes | MailChimp meets the [recommended cryptographic profiles for TLS](https://www.ncsc.gov.uk/guidance/tls-external-facing-services) as published by the *NCSC*. In addition, MailChimp currently gets an ['A' rating from Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=mailchimp.com) (Intermediate Certificate uses SHA1). Note that this was performed on their top level domain, and not all subdomains that may be used for API calls. |
| Does the SaaS provider protect internal data in transit between services using encryption? | Yes | MailChimp specifies that [SSL is supported](https://kb.mailchimp.com/accounts/management/i-got-a-security-alert-in-my-browser) throughout the entire application and that [sensitive data](https://mailchimp.com/about/security/?_ga=1.103645440.1840623753.1488291707) is transmitted via SSL. |
| Does the SaaS provider protect internal data in transit between services using correctly configured certificates? | Unknown | At this time, it is unknown whether MailChimp protects external data in transit using correctly configured certificates. |
| If APIs are available, does the SaaS provider protect both internal and external APIs through an authentication method? | Partial | All API requests made to MailChimp support authentication using [HTTP Basic Authentication and OAuth2](http://developer.mailchimp.com/documentation/mailchimp/guides/get-started-with-mailchimp-api-3/#authentication). However, this is not enforced. |
| If there is a concept of privilege levels in the service, does the SaaS provider have the ability for low privilege users to be created? | Yes | MailChimp has a number of different [roles](http://kb.mailchimp.com/accounts/manage-users/manage-user-levels-in-your-account) available. |
| If there is a concept of privilege levels, does the SaaS provider provide 2FA/multi-factor authentication on at least the high privileged accounts? | Yes | MailChimp currently provides [multi-factor authentication](http://kb.mailchimp.com/accounts/login/set-up-a-two-factor-authentication-app-at-login) via SMS or a specified app. Multi-factor authentication is not mandatory however, to encourage users MailChimp offers a discount to paying customers. |
| Does the SaaS provider collect logs of events?<br><br>*Types of log may include security logs and resource logs* | Unknown | MailChimp does not comment about any detailed logging. However, [notifications](http://kb.mailchimp.com/accounts/account-setup/activate-account-notifications?_ga=1.40152738.1840623753.1488291707) can be enabled for specific events. |
| Does the provider make logs available to the client? | Unknown | At this time, it is unknown whether MailChimp provide logs to the client. |
| Does the SaaS provider have a clear incident response and patching system in place to remedy any publicly reported issues in their service, or libraries that the service makes use of?<br><br>*The provider’s previous track record on this is a good metric to see how they’ll cope with a new issue occurring.* | Unknown | At this time, it is unknown whether MailChimp has a clear incident response and patching system in place. |
| Does the SaaS provider give clear and transparent details on their product and the implemented security features (i.e. how easy has it been to answer the above questions) ? | Partial | From MailChimp's [security page](https://mailchimp.com/about/security/): "From time to time, companies ask us security questions about MailChimp. In general, we don't like to expose much information about our security practices, because it only helps the very people we're securing ourselves against.” However some information is made available but not in detail. As we [have mentioned in the past](https://www.ncsc.gov.uk/studio/blog-post/cloudy-chance-transparency) we would like to see vendors being as transparent as possible when it comes to their security. |

---

## Exporting data

MailChimp allows an administrator or owner to [backup and export](http://kb.mailchimp.com/accounts/management/export-and-back-up-account-data) the entire account once every 24 hours.