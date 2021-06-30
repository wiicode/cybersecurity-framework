---
title: . Continuous improvement
description: How to ensure that legitimate emails aren't lost once your DMARC policy is at 'reject' and that old systems can't be used to spoof email from your domains.
published: true
date: 2021-06-30T19:41:12.345Z
tags: bronze, bronze-controls, email
editor: markdown
dateCreated: 2021-06-30T19:41:12.345Z
---

> Most organizations will regularly add and remove email sending services as they introduce, refresh, and retire IT.
{.is-info}


In order to ensure that legitimate emails aren't lost, and that old systems can't be used to spoof email from your domains, you should put processes in place to ensure that your SPF and DKIM configurations are up to date.


## There are 2 main update mechanisms:

1\. Ensure that those responsible for adopting or retiring technology are aware the necessary processes. To help with this you can publish internal documentation which explains the need to enable new services and disable retired ones using SPF and DKIM. You should regularly review whether changes should be made to your SPF/DKIM configurations. 

2\. Use your *DMARC report processing tool* to identify any new systems which might be in use, but do not have the necessary SPF/DKIM configuration in place. You can then contact relevant teams and add SPF/DKIM configurations if appropriate.

# E-mail security and anti-spoofing

- [Choose an anti-spoofing management tool](/bronze-controls/email-security-and-anti-spoofing/choose-anti-spoofing-management-tool)
- [Protect email in transit](/bronze-controls/email-security-and-anti-spoofing/protect-email-in-transit)
- [Configure anti-spoofing controls](/bronze-controls/email-security-and-anti-spoofing/configure-anti-spoofing-controls-)
- [Send spoof emails to spam](/bronze-controls/email-security-and-anti-spoofing/mark-spoof-emails-as-spam)
- [Spoof emails being rejected](/bronze-controls/email-security-and-anti-spoofing/reject-spoof-emails)
- [Continuous improvement](/bronze-controls/email-security-and-anti-spoofing/continuous-improvement)
{.grid-list}