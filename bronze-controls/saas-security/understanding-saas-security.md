---
title: Understanding Software as a Service (SaaS) security
description: An outline of the BCSF's approach to understanding the security of Software as a Service (SaaS) offerings.
published: true
date: 2021-06-02T21:15:51.651Z
tags: bronze, bronze-controls, saas-security
editor: markdown
dateCreated: 2021-05-29T19:53:28.322Z
---

This guidance introduces the approach the *BCSF* have developed to help you understand the security of Software as a Service (SaaS) offerings, and gain [confidence](/bronze-training/background-topics/cloud-security-2-confidence) using them.

Please note that this guidance is primarily aimed at risk owners and IT deployment teams, **not** the end users of SaaS offerings. More specifically, this guidance is aimed at people looking to help their organizations:

-   make use of SaaS offerings
-   carry out due diligence on the security of a chosen SaaS offering before deployment
-   understand the risks of an already deployed SaaS offering

We've used this approach to investigate the security of a number of popular SaaS offerings. However, if you're interested in a service not covered in this first release, you can use our approach to perform your own security review.

The SaaS business model involves consumers accessing centrally hosted software applications via the Internet. SaaS is one of the main three categories of cloud computing. The other two - Infrastructure as a Service (IaaS) and Platform as a Service (PaaS) - are **not** covered by this guidance.



# How we investigated SaaS security

Working with a developed set of SaaS security principles (derived from the larger [*BCSF* Cloud Security Principles)](/bronze-controls/saas-security/saas-security-principles), we examined a SaaS offering to find out how it measures up against the SaaS security principles.

To establish how well each principle is met, we intentionally ask questions which can be answered without requiring in-depth research, or direct consultation with the service provider. Having answers to these questions can help give confidence that the SaaS provider is:

-   protecting your data in transit between clients and the service, as well as within the service
-   protecting user accounts by recommending authentication and authorisation policies
-   providing logging and auditing to maintain user experience and flexibility for the majority of responsible users (this approach is preferable to prevention and control, which some users may try to work around)

You can also use the SaaS security principles to help understand if the SaaS provider is protecting your information against phishing, hacking, and password guessing.

# SaaS for sensitive work

If you are going to use a service for more sensitive workloads (such as processing large amounts of personal data, or as part of a larger more trusted system) you should conduct a more thorough analysis of the service using the full [cloud security framework](/silver-conrols).

Some cloud providers, such as [Amazon](https://d0.awsstatic.com/whitepapers/compliance/AWS_CESG_UK_Cloud_Security_Principles.pdf), [Atlassian](https://www.atlassian.com/trust/policies/cloud-security), [Google](https://gsuite.google.co.uk/intl/en_uk/faq/security/), and [Microsoft](https://gallery.technet.microsoft.com/14-Cloud-Security-Controls-670292c1) publish detailed information about the security of their products. Whether in the form of security white papers or direct responses to our cloud principles, these can help inform your decision making.



# Using our service-specific advice

The services covered by this first publication were chosen using Government Digital Service research on applications frequently used across government. The inclusion or exclusion of a service does **not** imply it is more or less secure than any other. Depending on the types and amount of information being moved to the service, you may want to take extra steps to protect your data.

More importantly, this guidance is not simply about configuring **a particular SaaS offering**. The goal is to encourage you to make informed information-risk decisions about **any** SaaS offering.

Note that we have deliberately **not** considered the geographical location at which a service resides or processes information. Ultimately this is a decision for your *organization*; you should be confident that the protections offered by the service **are suited to your needs,** and that any restrictions you place on the data are met. 


# General recommendations

There is a shared responsibility between both the SaaS provider and the *organization* consuming the service to ensure that the service is correctly used and secured.

Regardless of the type of service being consumed, the *BCSF* recommend that:

-   the SaaS offering should be centrally managed and users given the correct level of access
-   the SaaS offering should be accessed using up-to-date and regularly patched software
-   devices accessing the SaaS offering should be configured in line with the [*BCSF* EUD Guidance]((/silver-training/end-user-device-guidance)
-   users should be made aware of the appropriate use of the service prior to receiving their credentials
-   user accounts on the service should be suspended when no longer required
-   audit logs should be monitored and any suspicious activity investigated
-   SaaS providers publish their security claims in a publicly accessible and easy-to-find location



# Disclaimers

-   This guidance uses a subset of the Cloud Security Principles, appropriate to SaaS services with a more limited access to data.
-   This guidance does **not** directly consider some potentially important issues regarding cloud security and risk management. 
-   The guidance for each SaaS offering was written and published at the time shown on the page for that service. At the time of writing, all information was accurate. However, SaaS services can evolve very rapidly, so before deployment you should check the service to ensure it is still consistent with our findings.
-   The existence of *BCSF* guidance for a specific service does **not** imply endorsement or guarantee the security of said service.