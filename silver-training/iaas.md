---
title: IaaS - Managing your responsibilities
description: An introduction to our 13 Infrastructure as a Service (IaaS) principles, the aims of the guidance, and how the guidance is structured.
published: false
date: 2021-06-30T02:09:54.865Z
tags: silver, iaas, silver-training
editor: markdown
dateCreated: 2021-02-22T01:23:14.446Z
---

As the name suggests*, Infrastructure as a Service (IaaS)* provides just one thing: Infrastructure. The platform and application stack built on top of the service architecture is generally the responsibility of you, the service user.

Along with the responsibility for designing and building these systems comes the need to ensure they are properly protected. And once again this duty falls to you, the service user.

In practice, this entails securely configuring the infrastructure you deploy and anything you build upon it.

### **Questions and answers**

This situation throws up some questions: What do I need to secure? How secure do things need to be? How can I be sure the measures I put in place are working? The guidance set out below will help you find answers to these questions and many others related to the security of your IaaS systems.

### **A familiar methodology**

The guidance follows a familiar pattern, addressing each of the Cloud Security Principles in turn. The aim is to equip you with the information required to make informed decisions about the security of your applications and data in an IaaS scenario.

## The 13 IaaS Principles

# 1: Data in transit protection

Data transiting networks should be adequately protected against tampering and eavesdropping through a combination of network protection and encryption.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| For data in transit **between your end user devices or systems and the service**, consider the following options:<br><br>-   use the remote access solution provided by the service (if available)<br>-   build your own remote access solution using virtual security appliances<br>-   deploy TLS as the primary data in transit protection for exposed interfaces from your service<br>-   deploy TLS to complement the data in transit protections provided by the service<br><br>Consider the following options to protect **data in transit within the IaaS service**:<br><br>-   rely on the network separation offered by the service to protect data in transit within the service<br>-   configure IPsec or TLS between compute instances |     |

# 2: Asset protection and resilience

Your data, and the assets storing or processing it, should be protected against physical tampering, loss, damage or seizure.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| You should understand the resilience and failover model of your IaaS provider, and how you can build upon their infrastructure in a way that gives you the level of availability that you need. | Failure to design appropriate redundancy into an application may result in unexpected outages. |
| The IaaS provider may be able to offer assurance that your data (disk images and other storage) is appropriately protected - physically, logically or cryptographically.<br><br>Where satisfactory protection *is not provided* by the IaaS provider, or if you want additional confidence, you can implement your own encryption of the data you store. For example using volume encryption. | Failure to implement or assure appropriate data at rest and sanitization protections may result in the unauthorized disclosure of information to third parties.<br><br>Management of encryption keys is likely to be the biggest challenge when attempting to encrypt storage in an IaaS service. You need the keys to be readily available (for resilience reasons) but you don’t want them to be available to an attacker. |
| Where an IaaS provider delivers dedicated physical storage infrastructure you may need to ensure it is erased prior to giving it up for reuse. You should verify with the IaaS provider where responsibility for erasing data lies. | Failing to properly erase your data could result in data becoming exposed to future users of the service. |
| When leaving a service, you may need to take action (such as wiping block storage, or marking data for deletion) to ensure your data is not retained, or accessible to other service users.<br><br>The actions you need to take will depend on what the IaaS provider does for you, and the level of confidence you need that your data is no longer with the provider. | Failing to properly erase your data could result in data becoming exposed to future users of the service. |

# 3: Separation between consumers

Separation should exist between service users to prevent one malicious or compromised user from affecting the service or data of another.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| You should comply with any requirements that the IaaS provider stipulates as necessary for the overall security of their infrastructure. This may include requirements to maintain, patch, audit and manage the platforms and applications you host on the service. | Failure to properly maintain and configure your infrastructure places your service (and maybe that of others) at risk. Depending on the terms and conditions of service usage, it could lead to suspension or termination of service. |
| The IaaS provider may implement mechanisms to support sharing of data or resources with other users of the service, or to make information widely available. You should ensure that access controls are appropriately set to prevent inadvertent data sharing or leakage. | Incorrect configuration of separation controls within the infrastructure may inadvertently lead to the exposure of data to unauthorized parties, which could have legislative, reputation or other consequences. |
| Where data is intentionally shared with other users, you should have procedures in place to ensure it does not contain information which could give an attacker access to the service.<br><br>For example, encryption keys, certificates or other credentials may be contained in disk images, templates, configuration files or other service-related data. | Unintentional leakage of access credentials can give privileged access to components of the service. |

# 4: Governance framework

The service provider should have a security governance framework which coordinates and directs their management of the service and information within it.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| As well as ensuring your service provider has the right governance framework in place it is important for you to also have the right governance in place around managing information risk associated with what you deploy into the IaaS. | In IaaS, responsibilities will be split between the IaaS provider and the user. Without clear delineation of responsibilities, there is a risk that each assumes the other is managing specific risks. It is important that information risk governance covers the whole application. |

# 5: Operational security

The service provider should have processes and procedures in place to ensure the operational security of the underlying IaaS service.

However, you will be responsible for much of the operational security of your applications.

The way you manage this may differ from traditionally provisioned IT, but the risks and activities remain very similar.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| **Configuration and change management**   <br>You may need to instruct your IaaS provider to provision your infrastructure in a specific configuration.<br><br>You may do this through a help desk or a ‘self-service’ application. In either case, it is important that new deployments and changes to infrastructure are well managed. | Failing to securely manage configuration and change may result in your platform or application becoming insecure because of unauthorized or defective changes. It may also make investigating and recovering from incidents and outages time consuming and expensive. |
| **Vulnerability management**   <br>You are responsible for vulnerability management of the platforms and applications you run within the infrastructure.<br><br>You should have processes in place to identify, prioritize, test and deploy security patches for these components. | Failing to adequately manage vulnerabilities in platforms or applications may make it very easy for an attacker to gain access to an application via a publicly disclosed vulnerability. |
| **Protective monitoring**  <br>You are responsible for the protective monitoring of platforms and applications which you run on service infrastructure.<br><br>You should ensure that appropriate security events are passed to a suitable log and audit system and that there are analysis tools in place to identify suspicious behavior. | Failing to adequately monitor applications will mean that successful or attempted attacks, and incidents of misuse, will not be detected. This increases the impact of any attack. |
| **Incident management**   <br>You should have clearly identified support routes for incidents reported by the IaaS provider. You should also be aware of the monitoring performed by the IaaS provider and ensure that they have appropriate contact details for reporting incidents.<br><br>You should have business continuity plans in place to handle any disruptions to the cloud service. The IaaS provider may recommend good practices relating to running robust and reliable services using the constructs they make available.<br><br>Incident management plans for the infrastructure service (and the platforms and applications that run on it) should be in place. | Failing to adequately manage incidents may result in information on an attack (or incident) being lost and increase the cost, duration and business impact of recovery. |

# 6: Personnel security

Service provider staff should be subject to security screening and education appropriate to their role.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| Some individuals in your organization will require privileged roles to manage the infrastructure, and the platforms and applications which you run on it.<br><br>You should consider the personnel security measures required for these privileged roles. | Abuse of privileged access can breach the confidentiality and integrity of an application in ways that can be difficult to detect. |
| Separation of privilege is a useful control to prevent and detect malicious activity and mistakes.<br><br>Where practical, separation of infrastructure, platform and application administration can help reduce the opportunity for mishap or abuse of privilege by a single individual. | Abuse of privileged access can breach the confidentiality and integrity of an application in ways that can be difficult to detect. |

# 7: Secure development

Services should be designed and developed to identify and mitigate threats to their security.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| You are responsible for the design, delivery and maintenance of platforms and applications built on top of any infrastructure supplied by an IaaS.<br><br>Development processes should follow the good practices IaaS providers would be expected to follow. These are set out in the section on implementing [Principle 7: Secure Development](/collection/cloud-security/implementing-the-cloud-security-principles/secure-development) | Insecure applications present attackers with opportunities.<br><br>Depending on the architecture, insecure applications and platforms may also offer a stepping stone for attacks on other services, applications and data. |

# 8: Supply chain security

The service provider should ensure that its supply chain supports all of the security principles which the service claims to implement.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| You will be responsible for securely provisioning and updating your platform and application software.<br><br>You should ensure that updates are retrieved via a secure channel from a reputable vendor and verify that they have not been tampered with.<br><br>Verification can be achieved by checking that software signatures match those of the publishing organization. | ‘Trojanised’ software media is a common distribution mechanism for malware. Failing to verify the source of software may lead to installation of trojanised versions, which compromise the security of the whole application. |
| IaaS providers may make libraries of platform images available. Before using these, care should be taken to ensure the images were generated from a trustworthy installation source and that the software in the image was produced by the original vendor.<br><br>Be particularly cautious of community supplied images where it may be difficult to get confidence in their trustworthiness. | ‘Trojanised’ software media is a common distribution mechanism for malware. Failing to verify the source of software may lead to installation of trojanised versions, which compromise the security of the whole application. |
| When using any template image (whether directly generated, or obtained from a third party), be particularly careful to ensure that security secrets (e.g. encryption or authentication keys) are changed from defaults and security settings are set to those required. | Failing to reinitialise security secrets on library images may allow an attacker to gain access to the platform or application, or to infer sensitive information, such as private encryption keys. |

# 9: Secure user management

Users should be provided with the tools required to help them securely manage their service.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| Most IaaS services will provide tools, APIs or interfaces for users to provision and manage their virtual infrastructure.<br><br>This management activity should be conducted by appropriate individuals - see [Principle 6: Personnel security](/collection/cloud-security/implementing-the-cloud-security-principles/personnel-security). It should also be conducted using appropriately secure devices (see our [End User Device Security Guidance](/collection/end-user-device-security)) and networks, from appropriately secure locations. | Failing to manage an administration account securely could give an attacker opportunity to gain privileged access to the platform or application. |
| Management accounts should be assigned to individuals using the principle of ‘least privilege’. Role-based access control should be carried out where possible. | The use of shared administration accounts makes it difficult to attribute management activity and implement good practice around least privilege and role-based access control.<br><br>This may make it difficult to identify, attribute and react to security incidents. |
| Strong authentication mechanisms (e.g. multi-factor authentication) should be used to authenticate staff to service management portals. | Weak authentication of management systems makes the compromise of privileged roles more likely. |

# 10: Identity and authentication

Access to all service interfaces (for users and providers) should be constrained to authenticated and authorized individuals.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| You are responsible for designing and implementing identity and authentication controls in your platforms and applications. For a discussion of authentication options and risks, refer to the implementation section on [Principle 10: Identity and authentication.](/collection/cloud-security/implementing-the-cloud-security-principles/identity-and-authentication)<br><br>You should ensure that you set any password complexity requirements under your control in line with good practice.<br><br>Use of passphrases rather than passwords should be encouraged and enforced with technical controls where possible. Controls to prevent brute force attacks should also be employed where available. | Weak identity and access control can allow unauthorized access to platforms and applications. The implications are particularly serious for privileged accounts. |
| IaaS providers may offer a means for service users to access their virtual infrastructure. This could, for example, take the form of a ‘virtual console’, or pre-provisioned keys on virtual infrastructure.<br><br>These features can give privileged access to infrastructure and platforms, so you should ensure they are protected by suitable authentication and access control. | Privileged access to virtual infrastructure could provide an attacker with complete control of consumers’ platforms and applications. |

# 11: External interface protection

All external or less trusted interfaces of the service should be identified and protected.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| Some IaaS services may directly expose your compute instances to external networks, such as the Internet. To minimize the service’s attack surface you should ensure that appropriate firewalls and other boundary protections are used at the infrastructure and platform level.<br><br>Virtual network security appliances may be useful where the IaaS provider does not offer the granularity of control required over the interfaces exposed in your services or applications. | Exposing unnecessary attack surface increases the likelihood an attacker can find and exploit vulnerabilities to gain access to the service.<br><br>Failure to correctly configure and protect platform or application interfaces increases the attack surface available and may allow unauthorized access to your platforms, applications and/or data. |
| You should consider using virtual networking to separate management and back-end functionality from interfaces exposed to end-users.Similar security architecture principlesto those used for physical deployments should be used in virtual deployments. | Failing to use layered architectures can significantly increase the impact of a compromised component. |

### **Connecting to the cloud service safely**

You may need to make changes to networks or end user devices in order to safely access the service. It is important to understand and manage the risks associated with any changes. The following table describes the risks associated with various approaches you can implement.

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| No changes made | n/a | Not considering changes made by end users may expose existing services, devices and networks to a greater risk of compromise. |
| Updated risk statement | Any additional interfaces or software are added to your risk management process. | Without a technical assessment it is difficult to determine the level of additional risk. |
| Architectural design review | Review of the design and architecture by an appropriately qualified individual, such as a CCP certified IA Architect at the ‘Senior’ or ‘Lead’ level. | An architectural design review will identify design level issues, but is not likely to identify misconfigurations or undocumented interfaces. |
| Penetration test | Penetration testing of the solution by [qualified testers](/guidance/penetration-testing). | Penetration testing should identify issues such as insecure configuration or vulnerable software components but will not necessarily identify architectural issues in the design of the service. |

# 12: Secure service administration

The methods used by the IaaS provider’s administrators to manage the operational service should be designed to mitigate any risk of exploitation.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| You are responsible for the secure administration of your platforms and applications. The same good practice management processes used for physical infrastructure and platforms should be applied to virtual infrastructure and platforms. | Compromise or misuse of administrative systems can bypass or modify many other security controls. |

# 13: Audit information provision to users

You should be provided with the audit records needed to monitor access to your service and the data held within it.

| **Recommendation** | **Risk management guidance** |
| --- | --- |
| As an IaaS user, you are responsible for collecting and reviewing audit data from your own platforms and applications. | Failure to maintain adequate accounting and audit information may make it difficult to detect or respond to security incidents. |
| You should also review security-related audit data shared with you by the IaaS provider. For example, checking that management activities performed were authorized. | Failure to review audit data may mean attacks or misuse are not detected. |