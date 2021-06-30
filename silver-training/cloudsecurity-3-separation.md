---
title: 3. Separation between users
description: A malicious or compromised user of the service should not be able to affect the service or data of another.
published: true
date: 2021-06-30T18:48:57.652Z
tags: silver, cloud-security-principles, silver training
editor: markdown
dateCreated: 2021-06-30T18:47:11.687Z
---

# 3\. Separation between users

A malicious or compromised user of the service should not be able to affect the service or data of another.

## Factors affecting user separation include:

-   where the separation controls are implemented – this is heavily influenced by the service model (e.g. IaaS, PaaS, SaaS)
-   who you are sharing the service with - this is dictated by the deployment model (e.g. public, private or community cloud)
-   the level of assurance available in the implementation of separation controls

Note: In an IaaS service you should consider separation provided by compute, storage and networking components. Also, SaaS and PaaS services built upon IaaS may inherit some of the separation properties of the underlying IaaS infrastructure.

For more information on the importance of separation requirements in cloud services, please refer to the [Separation Guide](/bronze-training/background-topics/cloud-security-3-separation)

## Goals

You:

-   understand the types of user you share the service or platform with
-   have confidence that the service provides sufficient separation of your data and service from other users of the service
-   have confidence that management of your service is kept separate from other users (covered separately as part of [Principle 9](/silver-training/cloudsecurity-9-management)

## Implementation approaches – Separation of users

Note that combinations of the following approaches can be complementary. When used in combination, they can provide greater confidence in the strength of separation within a service.

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Virtualization technologies (e.g. a hypervisor) provide separation between users | Compute separation is provided by a hypervisor. Network and storage virtualization techniques are also employed. | Assuming popular and well-designed virtualization technologies are used, then this is likely to provide stronger separation than other software controls.<br><br>Some virtualization products have been assessed against well-defined security standards, such as the Certified Product Assurance scheme. |
| Other software provides separation between users | Other software controls, such as operating systems, web servers or other applications, provide separation between users of the service. | In this scenario the attack surface available to a rogue user is much greater. Vulnerabilities or misconfiguration issues could lead to breaches.<br><br>In this scenario you should look to gain confidence in the implementation of separation controls. Look for evidence of:<br><br>-   regular penetration tests of infrastructure and any relevant web applications<br>-   security reviews of the design of the service<br>-   an engineering approach that ensures security is a key consideration in developing the service |

## Additional notes – Who you are sharing the service with

The degree of confidence you need to establish in the user separation measures employed in a cloud service will depend on your intended use, and the deployment model of the service.

-   For **private** cloud services.

Because a single organization should have a good understanding of all its uses for the cloud environment you may be comfortable with only having quite limited assurance in the separation of the service.

-   For **community** cloud services.

Where you trust the community, and its members are known to practice a good level of hygiene (perhaps even bound by a code of conduct), evidence that well scoped penetration tests are regularly conducted may give you sufficient confidence in the separation provided.

-   For **public** cloud services.

You should consider the strength of separation required, given that other consumers of the service may be actively hostile towards you. If a higher level of confidence is needed, in addition to penetration testing, it may be desirable to gain assurance in the design of the service and the engineering practices of the service provider.

## Additional notes – Penetration testing

A well-scoped penetration test (and implementation of its recommendations) can give confidence that products and security controls tested have been configured in accordance with good practice and that there are no common or publicly known vulnerabilities in the tested components, *at the time of the test*.

A penetration test will not normally assess products or components for previously unknown vulnerabilities.

Ensure that your penetration testers are appropriately qualified. For example, individuals certified under the CHECK, CREST or Tiger schemes.

Independent review of the scope of a penetration test, and review of the mitigations it identified, will give a higher degree of confidence that penetration testing successfully achieved the objectives set out above.