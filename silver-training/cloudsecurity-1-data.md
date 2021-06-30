---
title: 1. Data in transit protection
description: User data transiting networks should be adequately protected against tampering and eavesdropping.
published: true
date: 2021-06-30T18:48:22.435Z
tags: silver, cloud-security-principles, silver training
editor: markdown
dateCreated: 2021-06-30T18:46:55.789Z
---

# 1\. Data in transit protection

User data transiting networks should be adequately protected against tampering and eavesdropping.

*This should be achieved through a combination of:*

-   **network protection** - denying your attacker the ability to intercept data
-   **encryption** - denying your attacker the ability to read data

## Goals

*You should be sufficiently confident that:*

-   Data in transit is protected between your end user device(s) and the service
-   Data in transit is protected internally within the service
-   Data in transit is protected between the service and other services (e.g. where APIs are exposed)

## Implementation approaches - Data in transit protection

Additional notes:

Points of attack to compromise data in transit, an attacker would need access to infrastructure over which the data transits. This could take the form of physical access, or logical access if the attacker has compromised software components within the service. It’s more likely that attackers would access infrastructure between the user and the service, as opposed to infrastructure within the service. However, the impact of an attacker accessing communications internal to the service would likely be significantly greater. Additional notes – TLS in addition to network layer protections across internal or community networks, you should use TLS protection for the following scenarios:

-   if additional confidentiality of data within your organization or community is required
-   to support end user authentication and access control within applications

Joiners and Leavers:  
  
On-boarding and off-boarding of users and workloads may involve the transfer of bulk data into or out of the service. In this scenario, you should consider the protection of data during transit using one of the approaches described above. If storage media is being used to transit data, this should be protected in line with [asset protection and resilience](/silver-training/cloudsecurity-resilience)

| **Approach** | **Description** | **Guidance** |     |
| --- | --- | --- | --- |
| Private WAN service | You access the service via a private WAN circuits offered by a telecommunications provider.Privacy between different customers of private WAN services is typically by virtue of the routing protocols used, such as MPLS. | Using private circuits will make it more difficult for an attacker to gain access to communications. These connections do not normally provide cryptographic protectionbut are likely to be hard to intercept and process, which may be adequate for your needs.<br><br>Cryptographic protections, should you choose to deploy them, would provide greater confidence in the protection of the confidentiality and integrity of your communications.<br><br>Public sector organizations can procure circuits which connect to the Public Services Network (PSN). This WAN, and the providers who give access to it, have had their services assessed against the CESG Assured Service (Telecoms) scheme. |     |
| Legacy SSL and TLS | The service is accessed using SSL or legacy versions of TLS (including TLS versions below 1.2). | Use of SSL or TLS versions earlier than version 1.2 is not recommended. There are known vulnerabilities in protocols which could be manipulated by an attacker to access your data. |     |
| TLS (Version 1.2 or above) | Use of TLS, configured to use cipher suites and certificate sizes recommended in our [TLS guidance](/silver-training/topic-tls). | The lack of formal assurance in TLS implementations means there may be implementation weaknesses. Using recent, supported and fully patched versions of TLS implementations from reputable sources will help to manage this risk. |     |
| IPsec or TLS VPN gateway | The service exposes a TLS or IPsec VPN Gateway which can be configured to support a strong cryptographic profile. | See our advice on [IPsec](/silver-training/topic-IPSec) and [TLS](/silver-training/topic-tls) configuration to ascertain whether the gateway supports a good profile.<br><br>Also, a list of VPN products which have been assessed against our Commercial Product Assurance scheme is available here. |     |
| Bonded fibre optic connections | Bonded fibre optic connections between physically protected locations can be used to provide private connections between data centres. | Independent validation of the service provider’s implementation of their bonded fibre optic connections by a recognized expert is advisable.<br><br>Note that the security of these links is dependent on effective monitoring - this should be one of the considerations for any [independent validation](/bronze-training/background-topics/cloud-security-2-confidence) of the security provided. |     |