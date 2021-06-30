---
title: Separation and cloud security
description: Learn about the two factors determining your security and assurance requirements when assessing the separation measures of a given cloud service.
published: true
date: 2021-06-30T19:59:55.079Z
tags: risk management, bronze, bronze-training, cloud-security-guidance, favorite
editor: markdown
dateCreated: 2021-06-30T19:20:10.462Z
---

When assessing the separation measures of a given cloud service, there are two factors determining your security and assurance requirements: The *deployment model* and the *service model.*

We have isolated three deployment models: **public cloud**, **community cloud** and **private cloud** deployments.

And three service models: Infrastructure as a Service **(IaaS)**, Platform as a Service **(PaaS)** and Software as a Service**(SaaS).**

# Separation and deployment models

## **Public cloud**

Public cloud services can normally be accessed by anyone in possession of a credit card. For some services, an email address is all that’s required to access free trial versions.

So, if you are using public cloud service, you have to accept that your adversaries can legitimately purchase a service ‘next door’ to yours.

In such instances, you probably want a high level of confidence in the controls separating your data from that of others.

## **Community cloud**

Community cloud services host users from a specific community, such as the public sector.

These communities often have a shared risk appetite and generally expect members to conform to an agreed minimum standard or legal agreement.

Community cloud providers can often tailor their offerings to match community requirements. For example, a service provider could choose to meet specific government standards for personnel security screening, or conform to the required standard to connect to a government community network. These tailored offerings can sometimes reduce risks relating to one or more of the [Advanced Security Principles](/silver-training).

Dedicating a service to a single community (where there is trust between members of that community) reduces the risks associated with separation between users.

The level of trust between users will depend upon the standards community members are obliged to conform to. Along with the types of applications deployed, this trust level will determine whether a community cloud service meets the required separation controls.

## **Private cloud**

Private cloud services are deployed to support a single organization. They normally offer the ability to tailor the architecture to meet specific security and business requirements. For example, if all consumers of the service are well known and low risk, then the level of assurance in separation required may be low.

For processing untrusted (possibly malicious) or very sensitive data you may require higher confidence in the separation controls. You will need to manage, monitor and maintain the infrastructure, unless an agreement exists with the cloud service provider to do this.

In many situations a private cloud service will operate within a single security domain (for example providing a virtual desktop, or test and development resources). In such scenarios, the cloud platform is simply another part of the enterprise IT environment and should be configured, managed and monitored as such.

Security controls in private cloud environments normally do not need high levels of assurance, *unless you have particularly challenging security requirements.*

# Separation and cloud service models

The technical controls required to provide separation will vary depending on the service model employed. We’ll consider these for each service type in turn.

## **Infrastructure as a Service (IaaS)**

IaaS products generally provide compute, networking and storage services. User separation needs to be enforced in all of these elements.

**IaaS: compute separation**

Within the compute environment, separation between users is typically enforced by a hypervisor (though in some circumstances it may also be achieved by allocating physical hardware to consumers).

The strength of separation usually depends on the virtualization technology in use. Using hardware virtualization and **assured virtualization products** should provide higher confidence in the separation within the compute environment. Obviously, this depends on the correct configuration and operation of the product.

The administration tools supporting the virtualization product should be secured too, as they are fundamental to the security provided by the product.

**IaaS: network separation**

It is important to understand the network separation model of an IaaS offering since users will normally be constructing their own virtual networks on multi-tenanted network infrastructure.

A number of technologies could be used by the service provider to enforce network separation. These include the use of virtual LANs (VLANs), virtual routing and forwarding (VRF) technologies, or virtual networking capabilities within the compute environment.

If you cannot gain sufficient confidence in the separation provided by an IaaS service within the networking layer, you may enhance your confidentiality protection with your own encryption. This is described in our IaaS configuration guide.

You may also need to consider whether the service protects or reserves your share of network resources, so that an attack (such as a DDoS) on another user does not affect your service provision.

**IaaS: storage**

In an IaaS model, users may have direct control over some portion of a multi-tenanted storage environment. Providing users with this direct control makes it possible for a malicious or compromised user to attack the storage components of the service in order to gain access to another user’s data. Effective separation within the storage of the service will help tackle this problem.

IaaS users can reduce their reliance on the cloud service provider's storage separation by encrypting their own data. This presents its own challenges, and will only be effective if the encryption keys for the data can be stored in such a way that they would not be accessible to an attacker who has access to the storage.

## **Platform as a Service (PaaS)**

PaaS offerings can provide users with rich and complex interfaces. They cover a wide range of implementation technologies, and are likely to be at different levels of security maturity.

Depending on the technologies involved, it may be difficult, time-consuming and expensive to gain high levels of assurance in the separation provided by a PaaS offering.

Applications wanting more assurance in the separation provided by a PaaS offering may instead build upon an IaaS offering which has sufficient assurance in such a way that separation will be enforced by the underlying IaaS. Alternatively, it may be appropriate to run the PaaS solution within a private or community cloud service.

Two common PaaS approaches, with different associated risks, are described below.

**Shared application hosting**

A common PaaS model, particularly for the delivery of web application hosting, involves the hosting of users’ applications on top of a shared operating system. In this model, the operating system and application host (eg the web server and the scripting host or runtime) are responsible for preventing users from affecting each other.

If attackers can legitimately run an application on the same host, they have access to a large attack surface to attempt to escalate privileges and gain unauthorized access.

**Managed host services**

Another common PaaS model is the provision of managed operating system services. In this model, the user has a dedicated physical or virtual machine, but rather than manage the operating system themselves, they purchase this as a service from the service provider.

The risks in this model are very similar to that of an IaaS service, since the separation enforcement is likely to be based on the same underlying technology (typically a hypervisor).

There are two key additional risks (compared to an equivalent IaaS service) to bear in mind when considering the suitability of this model:

-   The service provider’s administrators will have privileged access to the operating system. This means it is easier for them to access your data than if they only had access to disk images.
-   In providing the management service, additional connections between your machines and the management infrastructure are likely. This infrastructure is an additional attack vector compared to the simple IaaS case.

## **Software as a Service (SaaS)**

In SaaS offerings the separation between users is often enforced by software controls running within a single instance of an application. The strength of the separation is dependent on the application architecture and implementation.

The underlying platform and infrastructure is not usually relied upon to enforce separation, which makes it difficult to gain high degrees of confidence in the strength of separation. In SaaS offerings it may be difficult to understand where and how your data is protected.

Some SaaS offerings may be dedicated to a single consumer, leveraging the controls of an IaaS or PaaS solution to give users confidence in the separation of their data.

In SaaS offerings the service provider will typically rely on application level controls rather than controls in the infrastructure or platform - meaning that if a component in the service is compromised then the data of many users may be visible to that component.

If you need more assurance in the separation provided by an SaaS offering you may want to build upon an IaaS or PaaS offering which has sufficient assurance in the underlying separation controls. Alternatively, it may be appropriate to run the SaaS solution within a private or community cloud service.

# Risks associated with service models

The following table summarizes the main risks associated with each of the service models.

| **Service model** | **Associated risks** |
| --- | --- |
| Infrastructure as a Service (IaaS) | Offerings implemented using hardware virtualization and leading virtualization products can provide a good level of separation between workloads and data in community and public cloud platforms.<br><br>However, like all complex software, IaaS offerings will never be free from vulnerabilities and the risks that these bring.<br><br>IaaS services also have a much greater burden on the user to configure and operate well. |
| Platform as a Service (PaaS) | PaaS offerings tend to have a larger attack surface than IaaS offerings since the separation between users is normally provided in higher level software rather than by a hypervisor. Community cloud PaaS offerings may provide some additional comfort for users where an acceptable use policy is in place that has been designed to reduce the risk of malicious workloads.<br><br>PaaS technologies are evolving rapidly and you should regularly verify that your platform choice meets your business and security needs. |
| Software as a Service (SaaS) | SaaS offerings tend to implement separation at a higher level than both IaaS and PaaS, meaning the potential attack surface for a would-be attacker is much greater.<br><br>Unless architected well these services will often present a potentially higher risk than deploying software packages for a dedicated user within an IaaS or PaaS service. |