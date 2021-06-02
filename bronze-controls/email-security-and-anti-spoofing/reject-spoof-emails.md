---
title: 5. Reject spoof emails
description: When and how to update your DMARC policy to 'reject', and recommendations for keeping everyone in your organization informed and monitoring your records.
published: true
date: 2021-06-02T20:16:11.130Z
tags: bronze, bronze-controls, email, dmarc
editor: markdown
dateCreated: 2021-06-02T15:21:41.820Z
---

At this point you should have identified and resolved any issues arising during the [“quarantine phase”](https://www.ncsc.gov.uk/collection/email-security-and-anti-spoofing/mark-spoof-emails-as-spam). As soon as you are confident DKIM and SPF are continuing to work correctly, you should move to a DMARC policy of *‘reject’*. 

Having a DMARC policy of ‘*reject*’ on all of your domains is the best way to prevent spoofing of your email. The goal for this section is to help you get to that point.

Many organisations report being able to move on from a DMARC policy of ‘*quarantine*’ to one of *'reject'* after about 3 months.

---

## Iterating a DMARC record

At this point, you should be confident that you have an accurate SPF record and are DKIM signing outbound messages. You should also have identified that all legitimate email is passing freely, while illegitimate email is being quarantined.

We recommend you now update your DMARC record to a policy of *p=reject* and apply it to a small percentage of your email.

Implementing a policy of *p=reject* will instruct recipients to reject any of the email sample that doesn't pass DMARC checks. 

Starting with a small percentage will help ensure any mistakes don’t affect all email delivery. Gradually increase the percentage to 100 as you confirm genuine email is being delivered, using the DMARC processing tool chosen in [Step 1](https://www.ncsc.gov.uk/collection/email-security-and-anti-spoofing/choose-anti-spoofing-management-tool).

**An example record applied to 50% of your email looks like this:**

`v=DMARC1;p=reject;sp=reject;fo=1;pct=50;rua=mailto:dmarc@yourdomain.gov.uk`

### **Reject and quarantine**

If you have *pct=50* in your *reject* record, a policy of *quarantine* will be applied to all remaining email. 

---

## Keep everyone informed

Notify your *organisation*’s management team of your implementation plan and ask that they alert you to any planned peak email traffic flows (for example, mass mailings).

If you experience any problems, you can revert to the DMARC policy of *p=quarantine* until you are ready to progress again.

---

## Closely monitor and update your records

After updating your DNS records with a DMARC policy of 'reject', we recommend that you closely monitor your reports for at least a 2 week period.

As 'reject' is the final DMARC policy to implement, we recommend that you continue to monitor your controls, as detailed in [Continuous Improvement.](https://www.ncsc.gov.uk/collection/email-security-and-anti-spoofing/continuous-improvement)