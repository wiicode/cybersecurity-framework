---
title: Domain Name System
description: 
published: false
date: 2021-06-02T21:08:36.276Z
tags: bronze, bronze-training, dns
editor: markdown
dateCreated: 2020-10-31T18:35:44.902Z
---

**Policy**: Use a dedicated DNS provider such as RackSpace Cloud DNS or Amazon Route53 to manage DNS records independent of the organization's website host, mail host, and domain registrar.   For some organizations two exceptions can be made:
- Office365 based organizations with GoDaddy will find that the convenience of automatic record management is so beneficial that managing DNS independently is difficult to justify.   Customers should note that GoDaddy is not SOC2 or ISO certified and should review vendor docs for security risks.
- Google Domains based organizations will find that the convenience of the entire system is too valuable to trade for the additional security. 
- e-Commerce only business that sees value and benefits from the e-Commerce platform controlling the DNS. 

**Convenience**:
Organizations often will choose to use the webhost's DNS because they area lead to believe that is necessary or simply hand over control.   Alternatively, organizations frequently will frequently leave the DNS at the registrar.  In both cases this makes web hosting and management extremely easy, but it leaves the mail-record management at risk and the domain subject to compromise.  

**Control**:
Choosing RackSpace Cloud DNS or Amazon Route 53  (or in some cases GoDaddy's DNS or Google Domains DNS) provides the most secure form of  DNS management in that it: 
- Provides adequate MFA and security capabilities to prevent unauthorized changes.  
- Provides a streamlined platform for experienced MSPs and managers to make necessary changes.
- Provides redundant and resilient DNS infrastructure mitigating risks associated with availability.  
- Enables infrastructure as code capabilities. 

**KEY CONCERNS**:
The primary concern here is supply chain compromise.  Domain registrations and DNS work collectively to supply a number of critical functions including:
- Brand presence
- Email Routing
- Website Routing
- Web Application Routing
- Verification for key services
- Email Authentication and Anti-Spoofing
- Privacy controls
All of those are rooted in DNS. While they do not change often, they are the most critical components of your business.  Losing control over an account or domain could expose your company to reputation problems, fraud, and financial loss.  

Web site hosts are usually the first to ask for DNS control out of convenience.  This is self-serving, they reduce support requests by owning the domain name system.  Their convenience is your loss of control, and thus your loss of security.   

BCSF recommends all small companies maintain DNS control outside of web host or mail host and often outside of registrar.  Exceptions are noted in the opening section of this document. 

Additionally, it is important to consider:
- Web hosts, no matter how large, do not have the same capabilities as Amazon, Azure, or RackSpace to withstand outages or attacks.  Web host DNS can be mis-used to conduct fraud or leak data.  Compromise of confidentiality and integrity.  Additionally, a DNS problem at web-host would affect all other items listed in the Key Concerns section above.  
- Companies frequently apply inadequate protections for DNS records.   In fact, it is extremely common for the domain registrations to be completed by an insecure account or lack sufficient protections such as security questions, PINs, and MFA.   Compromise of integrity. 
- Registrar changes can be cumbersome and prone to human error.  Compromise of availability and integrity. 


