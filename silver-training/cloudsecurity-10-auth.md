---
title: 10. Identity and authentication
description: All access to service interfaces should be constrained to authenticated and authorised individuals.
published: true
date: 2021-06-30T18:50:26.782Z
tags: silver, cloud-security-principles, silver training
editor: markdown
dateCreated: 2021-06-30T18:46:58.475Z
---

# 10\. Identity and authentication

All access to service interfaces should be constrained to authenticated and authorised individuals.

Weak authentication to these interfaces may enable unauthorised access to your systems, resulting in the theft or modification of your data, changes to your service, or a denial of service.

Importantly, authentication should occur over secure channels. Email, HTTP or telephone are vulnerable to interception and social engineering attacks.

## **Goals**

You should have confidence that identity and authentication controls ensure users are authorised to access specific interfaces.

## **Implementation – Identity and authentication**

| **Approach** | **Description** | **Guidance** |     |
| --- | --- | --- | --- |
| Two factor authentication | Users authenticate with a username and either a hardware/software token, or ‘out of band’ challenge (e.g. SMS). | This approach is considered good practice, assuming that standard, and well tested, authentication schemes are used. |     |
| TLS client certificate | The service supports authentication over TLS using an X.509v3 client certificate that identifies an individual user. | This method provides strong cryptographic protection. It’s strength, however, is dependent on the secure creation and management of certificates, and on the safeguards in place on end user devices to protect them. If a client certificate is stolen by malware from a device then it can be re-used by an attacker to gain access to the service - only an additional factor of authentication (see below) would prevent that.<br><br>Processes will be needed to revoke lost or compromised credentials. |     |
| Identity federation with your existing identity provider | The service supports federating to another authentication scheme, such as a corporate directory, an OAuth or SAML provider. | Using federated identity approaches can give you the benefit of only having to manage a single identity and authorisation scheme, rather than many. However, beware that federated identity solutions acquire the risks of the source identity solution. Compromise of that source identity solution will give access to any resources protected by federated identities. For example, a source identity solution based solely on username and password authentication would have the risks described below. |     |
| Limited access over dedicated link, enterprise or community network | Access to a service is limited to a private or community network. | This method on its own is not sufficient to protect your service, but can be used in addition to other methods. In those cases it will reduce the opportunity for an attacker to exploit stolen credentials, since they would also need access to the enterprise or community network to do so.<br><br>Very large networks should normally be treated as though they are public. |     |
| Username and password | Authentication is via basic username and password with no capability for consumers of the service to enforce strong password selection. | Usernames and passwords are susceptible to compromise through phishing or malware on end user devices. The lack of a second factor of authentication means any compromised credentials can be re-used by an attacker to gain access to the service.<br><br>Credentials passed over unencrypted channels are at particular risk of interception, so it’s important to send them over encrypted connections. | ## **!** |

## **Additional notes – Authentication risks**

The risks associated with a compromised user account will vary depending on the privileges granted to the account. Highly privileged accounts, with access to large volumes of user data (or the ability to alter service configuration and security) are of high potential value to an attacker. Weak authentication of these privileged accounts is normally a higher risk than that of regular service users.

Very long passwords, complexity requirements or change frequencies can increase the chances of users handling passwords badly, storing them insecurely, sharing or reusing them. Alternative protections (such as two-factor authentication) are often a better choice than requiring very long passwords. [See our password guidance for more specific advice](https://www.ncsc.gov.uk/guidance/password-collection).

Active monitoring and protection can be a valuable mitigation against authentication risks. The hampering of brute force attacks through locking, blocking or rate limiting provides useful mitigation and can aid detection.

Providing risk-based triggers (such as asking for re-authentication for significant actions, or demanding additional authentication information from unknown locations or devices) can also help to detect and mitigate the threat from compromised credentials.