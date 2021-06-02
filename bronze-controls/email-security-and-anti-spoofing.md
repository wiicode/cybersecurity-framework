---
title: Email security and anti-spoofing
description: A guide for IT managers and systems administrators
published: true
date: 2021-06-02T18:43:36.016Z
tags: bronze, bronze-training, bronze-controls, email
editor: markdown
dateCreated: 2021-06-02T15:12:04.641Z
---

This guidance is intended to help you secure your *organisation*'s email systems, in two distinct ways:

1.  **1**

#### **By making it difficult for fake emails to be sent from your** ***organisation*****'s domains.**

*This will be achieved by configuring effective anti-spoofing controls on your domains. In summary:*

• **Sender Policy Framework (SPF)** allows you to publish IP addresses which should be trusted for your domain.

• **Domain Keys Identified Mail (DKIM)** allows you to cryptographically sign email you send to show it’s from your domain. Although DKIM is not as widely supported as SPF, it has the advantage of being able to support forwarded email.

• **Domain-based Message Authentication, Reporting and Conformance (DMARC)** allows you to set a policy for how receiving email servers should handle email which doesn’t pass either SPF or DKIM checks. This includes untrusted emails, which should be discarded. DMARC also generates reports, which you can use to understand how your email is being handled.

1.  **2**

#### **By protecting your email in transit with TLS**

*Your service should be capable of sending and receiving email using Transport Layer Security (TLS).*

You should protect all of your *organisation*'s domains, including where your *organisation* uses common Cloud email providers, such as Google G Suite and Microsoft O365.

This guidance assumes readers have prior knowledge and experience of managing domains and email systems for their organisations.

We have provided links to guidance at the end of this article under Further reading.

---

## The benefits of securing your email

When you implement anti-spoofing measures and secure your email while in transit, you:

-   **Help protect the individuals and organisations you do business with** by making it difficult for cyber criminals to spoof your email address
-   **Help protect your brand and reputation**
-   **Reduce the costs of service down-time** and time spent on dealing with the consequences of email fraud