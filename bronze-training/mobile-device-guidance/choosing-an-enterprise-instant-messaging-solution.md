---
title: Enterprise instant messaging
description: Advice on assessing the security features of enterprise instant messaging systems for smartphones, tablets, laptops and desktop PCs
published: true
date: 2021-06-02T20:50:40.650Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:44:11.033Z
---

Enterprise Instant Messaging (IM) is widely used by organizations to facilitate efficient communications between employees.

There are a variety of enterprise IM services, and features can vary between them, so it's important to choose the right one.

This guidance outlines some of the important security-related aspects you'll need to consider when selecting which product(s) meet your needs.


# Why secure your enterprise instant messaging?

Instant messaging is fast, convenient, and enables rich communications between collaborators. However, these communications may contain sensitive corporate or personal data. Without understanding the security of these services, it is impossible to assess the risks to your data from using them.

If users are not given formal guidance on which services to use, they may turn to insecure methods of communication, such as SMS.

Regulated industries and public sector organizations may have additional strictures to comply with, including the need to audit communications between staff, or respond to information requests. If data is held within IM applications that don't permit enterprise audit, you may be unable to comply.



# Preparation for secure instant messaging

Various features of a messaging service need to be considered before you choose a specific IM service. In particular, you should consider:

-   The same things you would consider for any [third-party application](/bronze-training/mobile-device-guidance/using-third-party-applications) running on your mobile devices. This includes assessing the reputation of the vendor, the likelihood that the application is insecure or malicious, and the impact to your organization should it be found to be so.
-   The security features provided by the IM service. This includes end-to-end encryption and enterprise single sign on. You may also want to look to see if any independent assessments have been performed on the application or protocols it uses, as well as any historic security issues there might have been.
-   What data-loss prevention features do you want from an IM service, if any?
-   What [enterprise audit and monitoring](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) features are offered by the service? This can improve threat detection and will be needed for business practice monitoring, as well as complying with any regulations you are required to obey.
-   Is the information about your use of the messaging service exposed unnecessarily for monetisation or advertising purposes? Look for a clear privacy policy on how your information is used.
-   How and where are messages stored during transit? Our [Cloud security guidance](/silver-training) can help inform your assessment.
-   How does backup and recovery of messages work, if devices are lost or stolen?
-   If you decide to use or enable built-in messaging services on mobile platforms, you should think about the implications of using [built-in cloud accounts](/bronze-training/mobile-device-guidance/using-built-in-cloud-services) that this may require.



# How to choose the right IM solution

To choose the correct Instant Messaging service for yourself or your organization, you should:

-   Decide on which features are important to your organization's stakeholders.
-   Build a shortlist of IM services that meet your business and regulatory requirements.
-   Conduct a security assessment of your potential Instant Messaging services, to ensure they comply with your requirements. Use the [BCSF Cloud Security Principles](/silver-training), or [BCSF SaaS Guidance](/bronze-controls/saas-security/understanding-saas-security) as well as internal reviews and third-party assessments.
-   Select, test and pilot an IM service from your shortlist that meets your requirements.
-   Develop an acceptable use policy for your chosen IM service, and test it with with user community representatives.
-   Follow BCSF guidance on [deploying third-party applications securely](/bronze-training/mobile-device-guidance/using-third-party-applications) when distributing the applications to your users. In particular, the use of enterprise application catalogues and automatic updates are recommended.

The BCSF has performed security assessments of several applications which implement the [Secure Chorus](https://www.securechorus.com/) protocol. 



# More information

Most enterprise instant messaging products, and some consumer instant messaging products include in-depth documentation explaining how they work. Some are open source. You can use this information to help perform security assessments.