---
title: Secure Configuration
description: Having an approach to identify baseline technology builds and processes for ensuring configuration management can greatly improve the security of systems.
published: true
date: 2021-05-29T19:02:03.505Z
tags: bronze, bronze-training, 10-steps, sourced, security-operations
editor: markdown
dateCreated: 2021-02-21T15:54:59.854Z
---

> Having an approach to identify baseline technology builds and processes for ensuring configuration management can greatly improve the security of systems. You should develop a strategy to remove or disable unnecessary functionality from systems, and to quickly fix known vulnerabilities, usually via patching. Failure to do so is likely to result in increased risk of compromise of systems and information.
{.is-info}

> Design, build, maintain and manage systems securely.
{.is-success}


# Summary
The technology and cyber security landscape is constantly evolving. To address this, organizations need to ensure that good cyber security is baked into their systems and services from the outset, and that those systems and services can be maintained and updated to adapt effectively to emerging threats and risks.

Having an approach to identify baseline technology builds and processes for ensuring configuration management can greatly improve the security of systems. You should develop a strategy to remove or disable unnecessary functionality from systems, and to quickly fix known vulnerabilities, usually via patching. Failure to do so is likely to result in increased risk of compromise of systems and information.


# What is the risk?
Establishing and actively maintaining the secure configuration of systems should be seen as a key security control. Systems that are not effectively managed will be vulnerable to attacks that may have been preventable. Failure to implement good configuration and patch management can lead to the following risks:

- Unauthorized changes to systems: The protections you believe you have in-place may be changed by unauthorized individuals, either internal or external, leaving information at risk.

- Exploitation of software bugs: Attackers will attempt to exploit unpatched systems to provide them with unauthorized access to system resources and information. Many successful attacks exploit vulnerabilities for which patches have been issued but not applied.

- Exploitation of insecure system configuration: An attacker could exploit a system that has been poorly configured by:
	- gaining access to information they are not authorized to see
	- taking advantage of unnecessary user rights or system privilege
	- exploiting unnecessary functionality that has not been removed or disabled
	- connecting unauthorized equipment that is then able to compromise information or introduce malware
	- creating a back door to use in the future for malicious purposes
  
# How can the risk be managed?
Organizations need to ensure that they have put in place measures to minimize the risk of poor system configuration. The following security controls should be considered:

**Use supported software**: Use versions of operating systems, web browsers and applications that are vendor (or community) supported.

**Develop and implement policies to update and patch systems**: Implement policies to ensure that security patches are applied in an appropriate time frame, such a 14 days for critical patches. Automated patch management and software update tools might be helpful. In cases where it is not possible to patch a vulnerability steps should be taken to make it very difficult to exploit. This might include making it difficult for an attacker to communicate with the system.

**Create and maintain hardware and software inventories**: Create inventories of all authorized hardware and software used across the organization. Ideally the inventory should capture the physical location, business owner and purpose of hardware together with the version and patch status of all software. Tools can be used to help identify unauthorized hardware or software.

**Manage your operating systems and software**: Implement a secure baseline build for all systems and components, including hardware and software. Any functionality or application that does not support a user or business need should be removed or disabled. The secure build profile should be managed by a configuration control process and any deviation from the standard build should be documented and approved.

**Conduct regular vulnerability scans**: Regularly run automated vulnerability scanning tools against all networked devices and remedy or manage any identified vulnerabilities within an agreed time frame.

**Establish configuration control and management**: Implement policies that set out a configuration control and change management process for all systems.

**Disable unnecessary peripheral devices and removable media access**: Assess the need for access to peripheral devices and removable media. Disable ports and system functionality that does not support a user or business need.

**Implement white-listing and execution control**: Create and maintain a whitelist of authorized applications and software that can be executed. In addition, systems should be capable of preventing the installation and execution of unauthorized software by employing process execution controls.

**Limit user ability to change configuration**: Provide users with the permissions that they need to fulfillll their business role. Users with ‘normal’ privileges should be prevented from installing or disabling any software or services running on the system.

**Limit privileged user functionality**: Ensure that users with privileged system rights (administrators) have constrained internet and email access from their privileged account. This limits exposure to spear phishing and reduces the ability of an attacker to achieve wide system access through exploiting a single vulnerability.

# What are the benefits?

> Getting security right at the start of any development helps to create systems that are easier to keep secure, and can reduce the need for any costly rework in the future
{.is-success}

> A well architected and configured system or service will help you gain confidence that your security controls are mitigating the risks that your organization cares about
{.is-success}

> Being able to manage your systems securely, and maintain their security over time
{.is-success}

## Understand what you are building and why
Understand the context before designing a system, including the risks your organization are, and are not, willing to accept, and the threat model for your system. Identifying the most critical systems and components in relation to your organizational objectives will help you focus your effort in the right places. Choose security controls based on the risks identified, and how effective they are at mitigating the types of attacks you expect, based on that threat model
Consider the expected lifetime of your systems, and how they can adapt to an evolving context. The cyber security landscape changes rapidly, so systems will need to adapt to new and emerging threats to remain secure. Ensure that your approach to system development and delivery can help you evolve your security controls to keep pace.

## Make systems easy to maintain and update
Before designing a system, consider if there are existing, securely designed products or services that you can make use of (instead of investing in the resource and expertise necessary to implement it all yourself). For example, consider how to benefit from the shared responsibility model of cloud services. Using concepts such as Platform as a Service (PaaS) and Software as a Service (SaaS) allows you to shift some of the responsibility for the management of the underlying technology and its security to the service provider, allowing you to focus more of your effort on the applications and services that are bespoke to you. You will also benefit from the vendor’s investment and expertise in security. You should still seek assurance that the service delivered by the cloud provider meets your needs.
Design systems so that security updates can be applied as soon as they become available, in ways that minimize your exposure to vulnerabilities without adversely affecting the availability of your system.
Use configuration management technologies such as Mobile Device Management systems and use Infrastructure as Code to formalizesystem deployments so that it is easier to track, update and re-deploy systems over time.

## Make compromise and disruption difficult
- Make compromise harder by adopting a layered approach to security so that an attacker would have to get through multiple controls to be successful. Consider using a framework such as MITRE ATT&CK to help identify possible ways of disrupting an attacker at different stages of an attack.
- Reduce the attack surface by protecting external interfaces and removing or disabling configurations and features that aren’t required such as accounts, software and demo capabilities. This should include:
	- applying secure configurations to servers and end user devices to restrict the options available to an attacker
	- not trusting data from external sources; where required, transform, validate or safely render data from external or less trusted sources (so that it can’t be used to craft an attack against your systems)
	- making it harder for email from your domains to be spoofed to make convincing phishing emails by employing anti-spoofing controls, including DMARC, SPF and DKIM
- Choose products and services that are designed to be secure by default. This reduces the effort required to deploy products in a secure manner, and gives greater confidence that they will remain secure over time.
- Make it easy for users to do the right thing. Security breaches often occur because users have developed workarounds for system inadequacies. Be sure to consider the potential for this and identify any methods users might resort to when circumventing security features.
- Understand the limitations of your systems and consider how you will deal with Denial of Service attacks, whether or not they are malicious. This could include upstream defenses via your service providers, options for scaling your systems, and what response planning and testing should cover. Ensure you consider cost protections (for example to limit spending when enabling auto-scaling cloud resources).
- Prefer tried and tested approaches to security and ensure you have the right expertise when building a bespoke solution. Avoid commonly used architectural anti-patterns which can reduce system security.
- Gain confidence that the security controls chosen are genuine and effective at mitigating your risks, and seek independent validation for the most critical controls.

## Reduce the impact of compromise
- Reduce the impact of compromise by preventing lateral movement and making it easier to recover. After an initial compromise, attackers will typically attempt to gain access to other systems and data. Make it harder for an attacker to reach their target once in the network by protecting your data and communications, and ensuring critical components are more isolated using segregated networks or adopting a zero trust architecture.
- Prevent malware from running on devices if it does reach you. Use antivirus applications that can detect threats based on known signatures and behavioral analysis to increase the chance of spotting emerging threats. Configure application controls to only allow authorized executables to run and disable macros for users and applications if they are not required.
- Plan for backup and recovery. Ensure that your plans include data and services, such as relevant configurations and accounts, and that you have tested your plans so that you are able to respond effectively in the event of a major incident such as a ransomware attack. You should have backups that remain protected and can be accessed in the event of a significant incident.

## Make it easy to detect and investigate compromises
- Design your communication flows so that it is easier for you to detect a compromise. Use clearly defined and tightly constrained communication methods between components and restrict flows using allow and deny lists so that malicious behavior is more likely to stand out from normal operations.
- Collect logs and monitor your systems to help you detect and investigate possible compromises. Ensure that your logging and monitoring systems are sufficiently separated so that it is hard for an attacker to hide their tracks by deleting or altering logs.

## Safely develop and manage systems
- Control and manage the way changes to your systems and services are made. Use a combination of technical and policy controls to ensure that all changes are authorized and have undergone appropriate checks to gain confidence that they will not adversely affect live services. Design these controls to make it easy and quick to apply security updates and fix vulnerabilities, so that exposure to known vulnerabilities can be minimized.
- Secure your development and deployment processes. Make it hard for accidental or malicious changes to impact your systems by protecting your code repositories and your pipelines for build and deployment. You should include human and machine-based checks (such as code review and automated code analysis) to detect unauthorized changes and help prevent vulnerabilities from being introduced. Ensure credentials and secrets are protected and separated from source code.
- Gain trust in the devices used to manage your systems. If an attacker compromises one of these devices (for example through a phishing attack), they could inherit the same level of access. Use Privileged Access Workstations for managing any systems you deem critical for your organization.
- Protect your management interfaces to make it harder for an attacker to access critical functions. Restrict access to administrative interfaces, including SSH, RDP and web consoles, to trusted locations or devices and ensure multi-factor authentication is enabled for administrative accounts. Ensure you can still gain access in an emergency by having a ‘break-glass’ procedure in the event of a system or device failure.
- 