---
title: BYOD Guidance
description: 
published: true
date: 2020-11-14T18:31:03.690Z
tags: draft, guidance
editor: markdown
---

Guidance for organizations on enabling staff to use their own smartphones, tablets, laptops and desktop PCs to access work information. This guidance is for organizations considering a ‘Bring Your Own Device’ (BYOD) approach. It describes the key security issues you'll need to consider in order to maximize the advantages of BYOD, while also minimize the risks.

Note that whilst we talk in this article about device ownership as distinguishing BYOD from more traditional management, it’s really device management that is important. If your users are happy to allow traditional full-device management of devices they own (effectively making it corporately issued), then you can continue to follow our detailed platform guidance.

Why use BYOD?
Workers often want to use their own laptops, smartphones and tablets to carry out their business functions. One clear advantage is that the user will be familiar with the device and will be saved the trouble of carrying both work and personal devices. It can also minimize overheads for the business.

However, organizations should still apply proportionate security controls and monitoring these devices if they are to be adequately secured.

Balancing your organization's need to protect its data and systems against the expectations of the device owner can be difficult. Without careful consideration, you will either end up with your users rejecting BYOD, or finding other ways to do their job using shadow IT.
Preparing for BYOD
When getting ready to deploy a BYOD solution you should first understand the additional risks involved and then develop a policy which will balance security for your organization with acceptability for your users.

Additional risks from BYOD
It's to be expected that you will have less control and visibility of a user's personal devices than you would corporate IT. As a result, BYOD deployments may come with greater security risks than a traditional setup.

However, with the right technical and procedural controls, many of these risks can be managed. How you might achieve this depends on the mix of technology you use. This includes any corporately owned devices and authentication solutions. You should think about how much the following risks matter to you before deciding to allow BYOD within your organization.

Easier user-initiated deliberate data loss (e.g. copying data from work app to personal)
Higher potential for accidental data loss (e.g. device backups containing work data, users sharing their device with family)
Malicious exfiltration of data (e.g. malicious application leaking data that users have consented it to access)
Malicious exploitation of devices as a result of weak security configuration (e.g. no data at rest encryption leading to data extraction)
Higher likelihood of unsupported or out-of-date devices, leading to exploitation of known security vulnerabilities
Malicious exploitation of devices remains undetected due to lack of monitoring, potentially leading to further spread of malware
Additional exposure of devices to threats as a result of being used in a broader personal context, such as user sharing devices or passwords with others
Developing a BYOD policy
Once you have established your tolerance for the types of risk associated with BYOD you should start developing your BYOD policy.

Your BYOD policy should clarify both organizational and employee responsibilities.

There are two stages to developing a BYOD policy. First you establish your policy goals, then you determine the controls you can use to achieve them

These questions will help you develop your policy goals:

What tasks will employees be permitted or encouraged to do, from their own devices?
For example, you may want your employees to submit expense reports from their personal devices but not access emails. 
What services will you expose to personal devices? And, what data you will expose from within those services?
For example, you might permit users to submit expenses to your HR tool from personal devices, but not change their bank details. Or you might permit access to the holiday booking tool, but not allow access to your sensitive financial documents store.
How much control will your employees be willing to grant you over their devices?
If you expect users to reject any control of their devices, your ability to manage risks will be compromised. For example, users may not like the idea of their employer being able to remotely wipe their entire device.
How enforceable are your policies?
If your policies rely entirely on users following specific procedures to keep devices secure, you should also consider what happens if users don’t follow those procedures, and how you might respond in such circumstances.

Enforcing your policy with technical controls
It is likely that you’ll need to develop your policy in conjunction with the technical controls you will use to implement the policy.

What types of access are permitted?
For example, phones with native apps, third-party container apps, web browsers – see technical approaches for more detail
What minimum standards for hardware and software versions will you enforce?
Older or unsupported platform versions are more likely to contain security weaknesses and lack modern mitigations which makes them harder to exploit.
What device policies will you enforce, and how will you enforce them?
You may be able to enforce some policies, including minimum passcode length and preventing copy and paste between work and personal apps. You will need to check your MDM service documentation for what policies are supported on your chosen devices.
What service access policies will you enforce?
For example, you could use compliance policies and strong authentication to verify devices before they are allowed access to enterprise services if supported. Either way, strong user authentication including MFA is especially important for BYOD as it may not be possible to implement strong machine authentication for personal devices.
How will individual services prevent personal devices from accessing sensitive data?
You might want to restrict access from personal devices to certain areas of a single service. For example, you may block access from personal devices to the most sensitive internal documents within your file storage services, whilst still allowing them to access less sensitive material in the same service.
How and where will you enforce these policies?
They could be enforced at an authentication service, network firewall, or on specific services.
Security controls which adversely effect the usability of a device will drive down adoption and so undermine your approach.

Overly restrictive controls may even encourage staff to find workarounds, which might increase your security risk.


Protecting against data loss
Where it's reasonable to do so, you should provide workers with a ‘presentation’ of information on their device, rather than storing it locally. You could do this using remote apps or remote desktop technology.

This minimizes the amount of data that can be easily accessed if the device is lost or stolen, and helps prevent bulk data theft if the device is infected. Be aware that security solutions, such as encryption or container products, can be circumvented if malware is present on the device.


Strongly authenticating users and devices
Staff should be made to strongly authenticate themselves before being given access to business data.

Since you may not be able to ensure that all personally owned devices are up to date, some authentication credentials could become compromised as a result.

You should consider using separate credentials for BYOD access to business systems. For example, usernames and passwords should not be shared between personally owned devices and the business desktop environment. Multi-factor authentication is also highly recommended.

As BYOD has very different enrollment processes to corporately owned devices – BYOD typically uses self-enrollment – securing device authentication to the same level as corporately owned devices may not be possible, and you will likely need to adopt a trust on first use approach for these devices. Nonetheless, using machine certificates stored in the dedicated, tamper-resistant hardware, present in many modern devices, can help improve machine authentication security. Alternatively, you can achieve similar results using applications which support secure storage for authentication credentials.