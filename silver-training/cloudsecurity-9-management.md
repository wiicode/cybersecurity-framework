---
title: 9. Secure user management
description: Your provider should make the tools available for you to securely manage your use of their service. 
published: true
date: 2021-05-27T22:02:12.926Z
tags: silver, cloud-security-principles, silver-training
editor: markdown
dateCreated: 2021-02-22T01:40:26.794Z
---

# 9\. Secure user management

Your provider should make the tools available for you to securely manage your use of their service. Management interfaces and procedures are a vital part of the security barrier, preventing unauthorized access and alteration of your resources, applications and data.

## The aspects to consider are:

-   Authentication of users to management interfaces and support channels
-   Separation and access control within management interfaces

### **9.1 Authentication of users to management interfaces and support channels**

In order to maintain a secure service, users need to be properly authenticated before being allowed to perform management activities, report faults or request changes to the service.

These activities may be conducted through a service management web portal, or through other channels, such as telephone or email. They are likely to include such functions as provisioning new service elements, managing user accounts and managing consumer data.

Service providers need to ensure that all management requests which could have a security impact are performed over secure and authenticated channels. If users are not strongly authenticated then an imposter may be able to successfully perform privileged actions, undermining the security of the service or data.

#### **Goals**

You should have sufficient confidence that:

-   you are aware of all of the mechanisms by which the service provider would accept management or support requests from you (telephone phone, web portal, email etc.)
-   only authorized individuals from your organization can use those mechanisms to affect your use of the service ([Principle 10](/silver-training/cloudsecurity-10-auth) can help you consider the strength of user identification and authentication in each of these mechanisms)

#### **Implementation – Authentication to management Interfaces and support**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Strong authentication in place | The service provider claims to have sufficient controls in place to ensure that only authorized users from your organization can affect your account via support channels | It’s worth asking your service provider how they check that only your authorized users can affect your account. You may wish to carry out your own testing to confirm you are happy with the safeguards in place. |
| Strong authentication in place, which is subject to regular exercising | As above, but the service provider can demonstrate that they regularly test their security via these channels (e.g. through using social engineering techniques) | Whilst exercising the strength of authentication is a good way of gaining confidence, you should note that it only tests the authentication mechanisms at a given point in time, so it's important that it testing occurs often.<br><br>Unfortunately there are no recognized standards to assess the quality of social engineering testing. It’s best to ensure that [experienced and reputable testers](/silver-training/cloudsecurity-9-management) are used. |

### **9.2 Separation and access control within management interfaces**

Many cloud services are managed via web applications or APIs. These interfaces are a key part of the service’s security. If users are not adequately separated within management interfaces, one user may be able to affect the service, or modify the data of another.

Your privileged administrative accounts probably have access to large volumes of data. Constraining the permissions of individual users to those absolutely necessary can help to limit the damage caused by malicious users, compromised credentials or compromised devices.

Role-based access control provides a mechanism to achieve this and is likely to be a particularly important capability for users managing larger deployments.

Exposing management interfaces to less accessible networks (e.g. community rather than public networks) makes it more difficult for attackers to reach and attack them, as they would first need to gain access to one of these networks. Guidance on assessing the risks of exposing interfaces to different types of networks is provided under [Principle 11](/silver-training/cloudsecurity-11-externalinterface)
#### **Goals**

You should:

-   have confidence that other users cannot access, modify or otherwise affect your service management
-   manage the risks of privileged access using a system such as the ‘principle of least privilege’
-   understand how management interfaces are protected (see [Principle 11](/silver-training/cloudsecurity-11-externalinterface)) and what functionality they expose

#### **Implementation - access control within management interfaces**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| No digital service management interface for users to administer their service | Some services may have no digital interface for users to administer their use of the service. This could be because the service is very simple or has no aspects that users manage. | \-  |
| Access control implemented in software | The separation between users of digital service management interfaces is performed in software | Service management interfaces are typically highly privileged, it is therefore important for you to be confident that they are well designed and well maintained. |
| Access control implemented in software, subject to regular testing | As above, but regular testing, including penetration tests, are used to assess the strength of separation within digital service management interfaces. | Penetration testing needs to be well scoped to ensure it is providing confidence in the security of the service management interfaces.<br><br>It's worth noting that a penetration test will normally detect common or publicly known weaknesses at the time of the test, rather than look for novel or previously unknown classes of vulnerability.<br><br>Appropriately qualified penetration testers should be used. For example, individuals certified under the CHECK, CREST or Tiger schemes. |

Note: For guidance on the risks of exposing the management interface to different networks, refer to [Principle 11 - External interface protection](/silver-training/cloudsecurity-11-externalinterface).