---
title: Managing user privileges
description: Giving users unnecessary system privileges or data access rights means that if the account is misused or compromised the impact will be more severe than it needs to be.
published: false
date: 2021-05-29T19:08:32.987Z
tags: bronze, bronze-training, 10-steps, sourced, access-control
editor: markdown
dateCreated: 2021-02-21T16:04:07.910Z
---

> Control who and what can access your systems and data.
{.is-info}


# Summary 
Access to data, systems and services need to be protected. Understanding who or what needs access, and under what conditions, is just as important as knowing who needs to be kept out. You must choose appropriate methods to establish and prove the identity of users, devices, or systems, with enough confidence to make access control decisions. A good approach to identity and access management will make it hard for attackers to pretend they are legitimate, while keeping it as simple as possible for legitimate users to access what they need.

Giving users unnecessary system privileges or data access rights means that if the account is misused or compromised the impact will be more severe than it needs to be.

# What is the risk?
Organizations should understand what level of access employees need to information, services and resources in order to do their job otherwise it won't be possible to manage rights appropriately. Failure to effectively manage user privileges could result in the following risks being realized:

- Misuse of privileges: Users could either accidentally or deliberately misuse the privileges assigned to them. This may result in unauthorized access to information to either the user or a third party or to unauthorized system changes having a direct security or operational impact.
- Increased attacker capability: Attackers may use redundant or compromised user accounts to carry out attacks and, if able, they may return to reuse the compromised account or possibly sell access to others. The system privileges provided to the original user of the compromised account will be available to the attacker to use which is why they particularly seek to gain access to highly privileged or administrative accounts.
- Negating established security controls: Where attackers have privileged system access they may make changes to security controls to enable further or future attack or might attempt to cover their tracks by making changing or audit logs.

# How can the risk be managed?
Organizations should determine what rights and privileges users need to effectively perform their duties and implement a policy of 'least privilege'.

**Establish effective account management processes:** Manage user accounts from creation, through-life and eventually revocation when a member of staff leaves or changes role. Redundant accounts, perhaps provided for temporary staff or for testing, should be removed or suspended when no longer required.

**Establish policies and standards for user authentication and access control**: A corporate password policy should be developed that seeks an effective balance between security and usability as set out in our password guidance. For some accounts an additional authentication factor (such as a token) may be appropriate.

**Limit user privileges**: Users should be provided with the reasonable minimum rights and permissions to systems, services and information that they need to fulfilll their business role.

**Limit the number and use of privileged accounts**: Strictly control the granting of highly privileged system rights, reviewing the ongoing need regularly. Highly privileged administrative accounts should not be used for high risk or day to day user activities, for example web browsing and email. Administrators should use normal accounts for standard business use.

**Monitor**: Monitor user activity, particularly access to sensitive information and the use of privileged account actions. Respond where activities are outside of normal, expected bounds (such as access to large amounts of sensitive information outside of standard working hours).

**Limit access to the audit system and the system activity logs**: Activity logs from network devices should be sent to a dedicated accounting and audit system that is separated from the core network. Access to the audit system and the logs should be strictly controlled to preserve the integrity of the content and all privileged user access recorded.

**Educate users and maintain their awareness**: All users should be aware of the policy regarding acceptable account usage and their personal responsibility to adhere to corporate security policies.

# What are the benefits?

> Only individuals and systems that are authorized to have access to data or services are allowed to do so
{.is-success}

> Less impact on staff's workday by getting identity and access management right across an organization
{.is-success}

> Smoother collaboration with customers, suppliers, and partners
{.is-success}

> More effective security monitoring and other controls that require identity and access management to function effectively
{.is-success}

# What should you do?
## Develop appropriate identity and access management policies and processes
- In the first place, consider how you establish identity. Ensure you have an identity and access management policy that covers who should have access to which systems, data or functionality, why, and under what circumstances. Make sure you consider all potential types of user including full and part-time staff, contractors, volunteers, students and visitors.
- Ensure the policy covers what and how audit records are acquired, and how they are safeguarded against tampering, and an identification of which actions or processes, if any, should require more than one person to perform or authorize them.
- Policies should not just cover systems you control, but also wherever your organizational identities can be used (for example, what websites or online services can staff create an account by using their work email address). Single sign-on (SSO) may be available using your organizational identity for some online services to help you control access to those services (and revoke access along with someone's work account when they leave your organization).
- Ensure your account management processes includes a ‘joiners, movers and leavers’ policy, so access can be revoked when no longer needed, or changed for movers. Temporary accounts (perhaps created to test processes) should also be removed or suspended when no longer required.
- If third parties require access to your systems, make sure that you have non-disclosure agreements in place and can revoke any accesses when necessary.

## Consider multi-factor authentication for all user accounts
- Choose authentication methods that are proportionate to the risk and support the ways in which people naturally work. Ensure you consider user-to-service, user-to-device, and device-to-service authentication.
- Implement multi-factor authentication (MFA) - also known as or two-factor authentication - on any accounts for online services to protect against password guessing and theft. Where appropriate, offer people a choice of factors to self authenticate, as no single method will suit everyone (or all environments or devices). These may include SMS or email messages, biometrics or physical tokens.
- Where passwords are required, implement a password policy that appropriately balances usability and security. You should aim to minimize the number and complexity of passwords that your users need to remember, for example, by using single sign-on or allowing password managers. This will help to discourage insecure practices (such as reusing passwords, choosing easy-to-guess passwords, or writing them down). Implement technical controls such as MFA, account throttling or lockouts, monitoring for suspicious behavior, and preventing the use of weak or exposed passwords to help prevent and detect password-based attacks.
Ensure credentials are adequately protected both at rest and in transit.

## Use MFA and other mitigations for privileged accounts
- Use a tiered model for administrative accounts and only use accounts with full privileges (like domain admin, global admin, or cloud admin accounts) when absolutely necessary.
- Ensure multi-factor authentication is enabled for administrative accounts and consider the use of strong authentication methods such as hardware security tokens and factors such as location or time for making a risk-based decision to allow access, depending on the circumstances and attempted activity.
- Ensure admins have separate user accounts for day-to-day business (such as email and internet browsing) and another for activities requiring their administrative privileges. These accounts should adequately separated, for example by using separate devices or a browse-down approach, and consider blocking any unnecessary web and email access on those devices. This limits exposure to spear phishing, and makes it harder to achieve wide system access through a single vulnerability. These considerations may also apply to other users with greater accesses, for example those approving financial payments or developers who can commit changes to any software your organization relies on.
- Review user accounts and systems for unnecessary privileges on a regular basis, and ensure privileged accesses are revoked when no longer required.

## Employ security monitoring to detect potential malicious behavior
- Ensure authentication and authorisation events are logged and monitored for suspicious behavior that may indicate a potential compromise. Indicators of malicious behavior could include login attempts that fail the second step of MFA, attempts from unexpected geographical areas, brute-forcing of account passwords (including password spraying), or reports of unexpected account throttling or lockouts.
- Design your access control systems to allow for easy monitoring of account usage and accesses, and ensure you can associate all actions in the system to the person or account that performed them (for example, in a web service all API calls performed might be linked to access tokens).

