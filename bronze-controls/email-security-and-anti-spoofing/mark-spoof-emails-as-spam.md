---
title: 4. Mark spoof emails as spam
description: When and how to update your DMARC policy to 'quarantine', and recommendations for keeping everyone in your organization informed of this change
published: true
date: 2021-06-02T20:26:44.609Z
tags: bronze, bronze-controls, dmarc
editor: markdown
dateCreated: 2021-06-02T15:20:35.580Z
---

> You should move to a DMARC policy of `quarantine*` as soon as you are confident DKIM and SPF are configured correctly, and all known legitimate sources of email for your domain have been added to your records. Only then will spoof email be hampered.
{.is-info}


During the *‘quarantine phase,’* any failed email will be sent to spam/junk (where the recipient has this enabled). This means the messages are **recoverable by the recipient**.

If you stop feeling confident about your controls, you can revert to the basic DMARC policy of *'none'* (and progress again to 'quarantine' when you gain confidence).

> Many organizations report being able to move on from a DMARC policy of ‘*none*’ after about 6 to 8 weeks.
{.is-success}


### **The effect of 'quarantine'**

Successfully applying a DMARC policy of `quarantine` means that emails being sent from your domains, and failing the DKIM and SPF authentication checks, will be sent to the recipient's spam/junk folders.


## Iterating a DMARC record

Your DMARC record will only start affecting the delivery of spoofed emails once you have a record of p=quarantine. The goal for this section is to help you get to that point.

Once you’re confident you have a comprehensive SPF record and are DKIM signing outbound email, update your DMARC record to have a policy of `p=quarantine` and apply it to *a small percentage of your email*. This will instruct recipients to quarantine your chosen percentage of the emails which fail DMARC checks. 

Starting with a small percentage will help ensure any mistakes don’t affect all email delivery. Gradually increase the percentage to `100` as you confirm genuine email is being delivered using the anti-spoofing management tool.

**An example record – applying a DMARC quarantine policy to 50% of your email - with these modifications applied looks like this:**

```
v=DMARC1; p=quarantine; pct=50; rua=mailto:dmarc@bentosecurity.org
```

**An example record – applying a DMARC quarantine policy to 100% of your email - with these modifications applied is:**

```
v=DMARC1; p=quarantine; rua=mailto: dmarc@bentosecurity.org
```


## Keep everyone informed

[While your DMARC policy was set to 'none'](/bronze-controls/email-security-and-anti-spoofing/configure-anti-spoofing-controls-), you will have identified most - if not all - of your legitimate sources of emails and modified your SPF and DKIM to include them.

We recommend that you alert your management teams – especially marketing / communications – of your intention to progress to the DMARC policy of `quarantine`. 

Ask that they alert you to any planned mass mailing campaigns (especially when using tools such as MailChimp). This will help you monitor and *analyze* activity as you move to `quarantine`.

You should also implement a process to ensure that your SPF and DKIM configurations are current, as the email sending systems you use are likely to change over time.


## Monitor and update your records

After updating your DNS records with a DMARC policy of `quarantine` at `100%`, you should monitor your reports for at least 4 weeks to gain confidence that legitimate emails aren't being quarantined.

### **Progressing to a DMARC policy of** ***‘reject’***

We recommend that you progress to a DMARC policy of `reject` when you are confident that you have correctly configured your DKIM and SPF records in your public DNS.