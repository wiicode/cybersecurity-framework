---
title: 3. Configure anti-spoofing controls
description: Configure anti-spoofing controls by implementing DMARC, creating and iterating an SPF record and creating and managing a DKIM record.
published: true
date: 2021-06-30T19:40:13.307Z
tags: bronze, bronze-controls, email
editor: markdown
dateCreated: 2021-06-30T19:37:14.259Z
---

## The following controls can be applied concurrently:

-   Implement a **DMARC** policy of ‘none'
-   Create and iterate an **SPF** record including your mail email senders
-   Create and manage a **DKIM** record for all of your mail email senders

# Implement a DMARC policy of ‘none’

Understand how to create the DMARC record for all of your domains, and see our recommendation for how to apply DMARC effectively and safely.

All of your domains, including parked domains, should have DMARC records in place, regardless of whether the domain is used for email or not.

We recommend you apply DMARC gradually, iterating your DMARC configuration over time.

Start by implementing a DMARC policy of ‘*none*’. You can view this policy as a ‘monitoring phase’, during which the DMARC processing tool you selected in Step 1 collects and reports on which systems and services are sending emails from your domains. *This does not interfere with your email traffic in any way.*

The list of email senders collected by your processing tool during this stage will probably include your legitimate internal email users and any third parties you use for things like marketing email campaigns. *It will also include any sources which are spoofing your domain.*

### **Take your time**

A DMARC policy of `none` will give you time to understand whether you have configured DKIM and SPF correctly.


## How to create the DMARC record

> **Note** In this example, we have used [***bentosecurity.org***](http://bentosecurity.org/)***.*** You should replace [***bentosecurity.org***](http://bentosecurity.org/) with your actual domain (which can be .gov, .com etc.). 
{.is-warning}


Update your public DNS record as detailed below.

Your DMARC record name is:

`_dmarc.bentosecurity.org`

It should be configured as a TXT record, with an initial value similar to this:

`v=DMARC1;p=none;rua=mailto:dmarc-rua@bentosecurity.org`

The 'p=none' part of the record above specifies the requested policy that mail receivers should apply.  A policy of 'none' means this DMARC record won’t affect the delivery of your email, but it will provide you with reports on where your outbound email appears to be coming from. 

The email address in the record should be provided by the DMARC processing tool you've chosen *(noting that dmarc-rua@bentosecurity.org shown above is fictional)*. If the tool does not provide one, it should be a mailbox you have chosen or created for this purpose.

“rua” is a comma separated list of URI(s) for aggregate report delivery.  This report contains details of the emails being sent from your domain, including whether they passed or failed the SPF and DKIM authentication checks. You can include up to 2 email addresses for which to send the aggregated data reports. If you’re eligible to use Mail Check and do, you need to include our email address, to ensure that you send the aggregated data to Mail Check - details are provided within Mail Check.

> **Note** In this ‘monitoring only phase’ we recommend keeping your DMARC record as simple as shown above.  You do not need to add additional ‘DMARC tags’ (see [https://tools.ietf.org/html/rfc7489#page-17](https://tools.ietf.org/html/rfc7489#page-17)) at this stage.
{.is-info}


Semi-colons are used to separate the tags.  Commas are used to separate multiple email addresses (where more than one is used). 

You do not need a semi-colon (or full stop) at the end of the DMARC record. 

### **DMARC Reports**

Within 24 hours of publishing your records you’ll start receiving email reports from [major email recipient domains](http://dmarc.io/sources/). These will come to the two addresses you specified in your DMARC record.

**The information in the reports will show**

-   Where the outgoing email from your domains originates.
-   How it's being handled by the major recipients. In other words, whether it has passed or failed the DKIM and SPF checks undertaken by the recipient.

# Create and manage a DKIM record

DKIM provides email authentication, which can be used to give the recipient server confidence an email came from a given address.

When DKIM is in use, the sending email service adds a DKIM signature to its outbound email. The receiving email service retrieves the sender's DKIM public key, which has been published in its DNS records.

The receiving email server verifies the signature on the email using the DKIM public key. If the signature is successfully verified, the DKIM check is marked as passed, which will contribute to the DMARC policy check.

You should configure DKIM on domains you send email from, as it's a stronger authentication mechanism than SPF. It will help recipients validate the legitimacy of email which has passed through an email relay en-route.

### **If you already have DKIM records**

If you already have DKIM records, you'll need to know the [DKIM selector](http://dkim.org/info/dkim-faq.html) to find the record. You can find the selector in the [header](https://support.google.com/mail/answer/22454?hl=en) of any email you send.



## Creating a DKIM record and signing email

### **Generate the key**

How you go about creating and implementing a DKIM key will vary depending on your email service. If you use a cloud-based email service, your DKIM configuration will be automated to some extent. Look for a DKIM option in your administration panel, or contact your service provider.

If you are configuring DKIM on your email servers directly, you will need to generate an RSA public/private key pair. We recommend you use a 2048-bit key. There are several good guides on how to generate RSA key pairs for [Windows](https://winscp.net/eng/docs/ui_puttygen) or [Linux](https://lxadm.com/Generating_DKIM_key_with_openssl).

DKIM keys do not expire, but you should rotate them periodically (we suggest every 12 months). Create a new key with a new selector and follow the same steps as above. Keep the old DNS record live for a few days after making changes, to give the DNS time to update.

### **Create an entry in the public DNS record**

Add the DKIM signature to a TXT record in your DNS record. This is made up of a selector (the name of your record), the version, the key type, and the public key itself.

Anyone receiving email which claims to be from you can verify the signature on the email with the key from your DNS. A successful verification proves the message hasn’t been tampered with in transit.

### General Configuration 
Your DNS record should have the host, or record name of:

```
selector._domainkey.bentosecurity.org
```

and the value:

```
v=DKIM1, k-rsa,
```

You can check this has been applied using a [DKIM lookup service](http://mxtoolbox.com/dkim.aspx) and your selector. The result should look like:

```
v=DKIM1; k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCG26OM/bk0vNm/TM2DnOQjPZNLIWspF4xtIX12LGHHjfushjsaudfysuf+DUigzM6h2oJMEdNt1S/CWVXW0pUBqfU0fzdw90+jyqOduh4cCnEk0z0w1w1j4xOYy0FLHhKoeoZJwWQFtwrlhrjxD6jM+sGeeRnbn2rQIDAQAB
```

### Microsoft 365 Exchange Online

Microsoft 365 guidance is confusing, and we recommend following our process over the mix of documentation.  We recommend leveraging `CNAME` records instead of `TXT` records and pointing them at your `onmicrosoft.com` domain that has a validated DKIM configuration.

> Substitute `bentosecurity.org` and `bentosecurity` for your domain and be extremely careful as your `onmicrosoft.com` domain may be different from your primary.
{.is-warning}


```
CNAME
Host:  selector1._domainkey.bentosecurity.org
TTL: 3600
Value: selector1-bentosecurity-org._domainkey.bentosecurity.onmicrosoft.com
```
```
CNAME
Host:  selector2._domainkey.bentosecurity.org
TTL: 3600
Value: selector2-bentosecurity-org._domainkey.bentosecurity.onmicrosoft.com
```

### **Apply DKIM signatures to outbound email**

How you achieve this will vary, depending on your email service. DKIM signatures may be applied by your filtering service rather than your email server. Ask your service provider for details.

A DKIM signature should be the last addition to a message before it is released by an email server. Since modifying the email or its headers will change its cryptographic hash, it is necessary for any signatures or standard disclaimers to be applied **before** it is signed with DKIM.

When using email scanning services on outbound email, ensure they are configured in a way that does not break the DKIM signature (e.g. through adding a disclaimer line to the bottom of the email body).

# Create and iterate an SPF record

Sender Policy Framework (SPF) is a system of email authentication.

SPF works by providing domain owners a way to publish a list of the IP addresses which should be trusted for a given domain. A receiving email service can then check that a sending email service has an IP address which appears in the sender's published list.

If the IP address appears in the list of acceptable IPs, the receiving email service will forward the email to the recipient's inbox. If the receiving email service cannot confirm the IP address is valid, then it marks the email in accordance with the DMARC policy you have implemented on the domain the email is being sent from.

## Create an SPF record

Create an SPF record in your public DNS, using all the IP addresses or address ranges from which you send email. You can use both IPv4 and IPv6 addresses. 3 examples of what an SPF record could look like are below:

1\. An example of a basic SPF record to be added to an *organization's public DNS where it uses Google would look like this:  
 

```
v=spf1 include:_spf.google.com ~all
```
 

2\. This SPF record includes Google's IP ranges and a sending service with an IP address range:  
 

```
v=spf1 include:_spf.google.com ip4:80.88.21.0/20 ~all
```
 

3\. An example of a more complex record, with additional services and some dedicated IP addresses:  
 

```
v=spf1 include:spf.protection.outlook.com include:mail.zendesk.com ip6:2001:db8::/32 ip4:203.0.113.6 ~all
```
 

> **NOTE:** These examples are unique - you cannot just "copy and paste" them into your DNS for your *organization*. If you use other email sending services, you need to add their domain or IP range to this record.
{.is-info}


You will need to check with your supplier to find the exact value in your case as it will not necessarily take this form (you can usually do this online, we recommend you search your email sending service and how to setup SPF records).

### **Choosing emailing services**

When choosing services, look for ones that can provide an SPF record you can include, or a stable IP range. This will make it easier to maintain your SPF record.


## Add all legitimate sources of email to your SPF records

You should ensure that all legitimate IP addresses are added to your SPF records.  We recommend that you consult all departments across your *organization* and ask, for example, whether they use any 3rd party mailing agents.  If your *organization* sends mass emails (for example, e-newsletters, e-magazines or e-bills), then it probably uses a 'mass marketing email service'.

### **Mass marketing email services**

Email marketing services allow bulk-sending of emails to targeted mailing lists. If your communications, sales and/or marketing staff make use of this kind of service, you need to ensure they are sending authenticated mails, as this will make it less likely your *legitimate* marketing emails will end up as spam. That is, you need to ensure that you add the IP addresses to your SPF records and set up DKIM.


## Understanding and overcoming SPF limitations

### **SPF record size limit of 450 bytes or fewer**

The SPF protocol limits the size of its record to 450 bytes (ie characters) or fewer.  If your software does not provide a character count, which should include spaces, we recommend you search online for 'character counter' and confirm that your proposed SPF record is 450 bytes or fewer.  

Where your SPF record is greater than 450 bytes, we recommend that you create one or more sub-domains (see below).

### **DNS lookup restrictions**

As part of evaluating whether an email message passes SPF authentication, a receiving mail server may have to make one or more DNS lookups.

To check whether an email passes SPF authentication, receiving mail servers invariably have to undertake DNS lookups.  The SPF protocol has some built-in protection – it protects receiving mail servers from **denial of service attacks** by limiting the number of domain lookups to 10.

The DNS lookup limit is often breached by 'nested' lookups caused by the use of an 'include'.  In the example above, whereby the SPF record includes `_spf.google.com`, looking up the contents of this record in DNS we find that it includes 3 `google.com` subdomains (ie a total of 4 lookups). However, 'includes' are useful because they help overcome the above mentioned SPF record limit of 450 bytes or fewer.

Your *organization* might use a number of cloud services, Zendesk, Google Apps, mass mailing services, and so on – rapidly the 10 lookup restriction is breached. 


### **Creating sub-domains**

**Sub domains will help you overcome the 450 bytes and maximum of 10 DNS lookup restrictions**

Each sub-domain makes its own DNS request, and so has its own lookup and character limits. This gives you a tool to split off your various business functions into their own subdomains, each with 10 lookups and 450 characters.

If you use 3rd party suppliers to send emails for you, we recommend creating a sub-domain each. For example, `marketing.bentosecurity.org` for your mass mail outs and newsletters.

Not only do you solve the SPF problem, but by doing this, you gain greater visibility and control of each domain. And, if you identify fraudulent use, for example, you will be able to take quicker preventative action, limiting the negative impacts of legitimate email traffic on your other domains.


### **SPF Errors**

SPF syntax is very sensitive to white space. This is one of the most common causes of errors in SPF records. In particular, the failure to put a spaces between the SPF terms (eg between IP addresses).

We recommend that you either leave your draft public DNS record for a few hours and then double-check it, or ask a colleague to double-check it, before you publish it. 


# Monitor, *analyze* and update your DNS records

Advice for when you have set up a DMARC policy of `none`, including monitoring your reports for at least two weeks and correcting any failures.

Implementing a DMARC policy of `none` on your domains won’t affect the delivery of your email but neither will it prevent illegitimate emails being sent from your domains. For this, you must at least implement a DMARC policy of `quarantine`.

Before you do this, you must ensure that you have correctly configured DMARC ***and*** SPF ***and*** DKIM on your domains.

### **The roles of SPF, DKIM and DMARC**

SPF provides host authenticity and DKIM provides a mechanism for checking message integrity.

These protocols do not tell organizations how to handle email, nor do they provide feedback to you, as the sending *organization*.

This is the role of DMARC, which builds on top of SPF and DKIM.



## When you have setup a DMARC policy of ‘none’

-   The receiving *organization* will not change how it processes email sent from your domain – legitimate or illegitimate
-   But you will get feedback from the recipient

Within 24 hours of publishing your DNS records with a DMARC policy of `none`, you’ll start receiving email reports from major email recipient domains. These will come to the two addresses you specified in your DMARC record. 

The information in the reports will show:

-   Where the outgoing email from your domains originates (eg IP address)
-   The outcome of SPF and DKIM checks by the recipient – simply, whether it has passed or failed the SPF and DKIM checks.



## Monitor your reports for at least 2 weeks

During this time, you might see a lot a `fail` notices against the SPF and DKIM checks. You should also see a lot of legitimate sources passing checks. For example, you will *recognize* the IP addresses belonging to your *organization*.

The reports will contain information about:

-   Legitimate email received directly
-   Legitimate email which has been forwarded by intermediary systems, such as mailing lists
-   Spoofed emails

You should use your anti-spoofing management tool to identify legitimate emails which are *not* passing either SPF or DKIM checks. You should then update your SPF or DKIM configurations so that they do.



## Correcting failures

To correct SPF failures you should add the sending systems you use to your SPF record, either by IP address, or by reference to another SPF record.  
To correct DKIM failures, you should ensure a valid DKIM key is published in the correct place in DNS, and that outbound emails are being signed with it.

You may not *recognize* all of the sending systems listed in your reports. When this happens you should investigate to determine if a particular sending service is in use by your *organization*.

It will likely take a few iterations of investigating, updating records, and waiting to review reports will be needed before you can gain enough confidence that you've got SPF and DKIM working for all of your sending systems.

> Once you've reached this stage, you're ready to move to a DMARC policy of `quarantine` which will provide anti-spoofing protections for your domain.
{.is-success}

# E-mail security and anti-spoofing

- [Choose an anti-spoofing management tool](/bronze-controls/email-security-and-anti-spoofing/choose-anti-spoofing-management-tool)
- [Protect email in transit](/bronze-controls/email-security-and-anti-spoofing/protect-email-in-transit)
- [Configure anti-spoofing controls](/bronze-controls/email-security-and-anti-spoofing/configure-anti-spoofing-controls-)
- [Send spoof emails to spam](/bronze-controls/email-security-and-anti-spoofing/mark-spoof-emails-as-spam)
- [Spoof emails being rejected](/bronze-controls/email-security-and-anti-spoofing/reject-spoof-emails)
- [Continuous improvement](/bronze-controls/email-security-and-anti-spoofing/continuous-improvement)
{.grid-list}
