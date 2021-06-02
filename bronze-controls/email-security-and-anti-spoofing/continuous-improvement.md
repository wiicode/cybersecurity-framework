---
title: 6. Continuous improvement
description: How to ensure that legitimate emails aren't lost once your DMARC policy is at 'reject' and that old systems can't be used to spoof email from your domains.
published: true
date: 2021-06-02T20:15:45.433Z
tags: bronze, bronze-training, bronze-controls, dmarc, emails
editor: markdown
dateCreated: 2021-06-02T15:27:00.573Z
---

Most organisations will regularly add and remove email sending services as they introduce, refresh, and retire IT.

In order to ensure that legitimate emails aren't lost, and that old systems can't be used to spoof email from your domains, you should put processes in place to ensure that your SPF and DKIM configurations are up to date.

---

## There are 2 main update mechanisms:

1\. Ensure that those responsible for adopting or retiring technology are aware the necessary processes. To help with this you can publish internal documentation which explains the need to enable new services and disable retired ones using SPF and DKIM. You should regularly review whether changes should be made to your SPF/DKIM configurations. 

2\. Use your [DMARC report processing tool](https://www.ncsc.gov.uk/collection/email-security-and-anti-spoofing/choose-anti-spoofing-management-tool) to identify any new systems which might be in use, but do not have the necessary SPF/DKIM configuration in place. You can then contact relevant teams and add SPF/DKIM configurations if appropriate