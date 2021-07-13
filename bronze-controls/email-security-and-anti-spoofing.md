---
title: Email security and anti-spoofing
description: A guide for IT managers and systems administrators
published: true
date: 2021-07-13T22:45:44.390Z
tags: bronze, bronze-controls, favorite, email
editor: markdown
dateCreated: 2021-06-30T19:36:39.618Z
---

<img align="right" width="50%" src="/article_images/common-web-attacks.png">
This guidance assumes readers have prior knowledge and experience of managing domains and email systems for their organizations and it is intended to help you secure your *organization*'s email systems, in two distinct ways:

1. #### **By making it difficult for fake emails to be sent from your** ***organization*****'s domains.**

> *This will be achieved by configuring effective anti-spoofing controls on your domains.*
{.is-info}


- **Sender Policy Framework (SPF)** allows you to publish IP addresses which should be trusted for your domain.

- **Domain Keys Identified Mail (DKIM)** allows you to cryptographically sign email you send to show it’s from your domain. Although DKIM is not as widely supported as SPF, it has the advantage of being able to support forwarded email.

- **Domain-based Message Authentication, Reporting and Conformance (DMARC)** allows you to set a policy for how receiving email servers should handle email which doesn’t pass either SPF or DKIM checks. This includes untrusted emails, which should be discarded. DMARC also generates reports, which you can use to understand how your email is being handled.

2.  ### **By protecting your email in transit with TLS**

> *Your service should be capable of sending and receiving email using Transport Layer Security (TLS).*
{.is-info}


You should protect all of your *organization*'s domains, including where your *organization* uses common Cloud email providers, such as Google G Suite and Microsoft O365.


# The benefits of securing your email

When you implement anti-spoofing measures and secure your email while in transit, you:

-   **Help protect the individuals and organizations you do business with** by making it difficult for cyber criminals to spoof your email address
-   **Help protect your brand and reputation**
-   **Reduce the costs of service down-time** and time spent on dealing with the consequences of email fraud

# Implementation Plan
> You should create a basic plan for your implementation.
{.is-success}


We recommend a phased approach to securing your email:

- [Choose an anti-spoofing management tool](/bronze-controls/email-security-and-anti-spoofing/choose-anti-spoofing-management-tool)
- [Protect email in transit](/bronze-controls/email-security-and-anti-spoofing/protect-email-in-transit)
- [Configure anti-spoofing controls](/bronze-controls/email-security-and-anti-spoofing/configure-anti-spoofing-controls-)
- [Send spoof emails to spam](/bronze-controls/email-security-and-anti-spoofing/mark-spoof-emails-as-spam)
- [Spoof emails being rejected](/bronze-controls/email-security-and-anti-spoofing/reject-spoof-emails)
- [Continuous improvement](/bronze-controls/email-security-and-anti-spoofing/continuous-improvement)
{.grid-list}

The size and complexity of your organization, the amount of change occurring and resources available to you will determine exactly how long you need.

Once you have secured your emails in transit, and implemented a DMARC policy of 'reject' on all of your domains, you should regularly conduct health checks and fix any problems which show up.

# Other resources in this collection.
- [Protect against phishing, malware, and frauds.](/bronze-controls/phishing)
- [Manage inbound requests, website contact forms, and the like](/bronze-controls/email-security-and-anti-spoofing/website-mass-mail-forms)
{.links-list}





