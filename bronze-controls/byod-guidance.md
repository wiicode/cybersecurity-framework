---
title: Bring Your Own Device (BYOD) Guidance
description: Guidance for personal devices in organization environments.
published: true
date: 2021-06-30T03:01:09.866Z
tags: bronze, bronze-training, security-operations, byod
editor: markdown
dateCreated: 2021-01-08T05:05:29.692Z
---

Guidance for companies on enabling staff to use their own smartphones, tablets, laptops and desktop PCs to access work information. This guidance is for companies considering a ‘*Bring Your Own Device*’ (BYOD) approach. It describes the key security issues you'll need to consider in order to maximize the advantages of BYOD, while also minimizing the risks.

Note that while we talk in this article about device *ownership* as distinguishing BYOD from more traditional management, it’s really device *management* that is important. If your users are happy to allow traditional full-device management of devices they own (effectively making it corporately issued), then you can continue to follow our detailed platform guidance.

## Why use BYOD?

Workers often want to use their own laptops, smartphones and tablets to carry out their business functions. One clear advantage is that the user will be familiar with the device and will be saved the trouble of carrying both work and personal devices. It can also minimize overheads for the business relating to procurement and provisioning.

However, companies should still apply proportionate security controls and monitoring to these devices if they are to be adequately secured. 

Balancing your company's need to protect its data and systems against the expectations of the device owner can be difficult. Without careful consideration, you will either end up with your users rejecting BYOD, or finding other ways to do their job using [_'shadow IT.'_](https://en.wikipedia.org/wiki/Shadow_IT)

## Preparing for BYOD

When getting ready to deploy a BYOD solution you should first understand the additional risks involved and then develop a policy which will balance security for your company with acceptability for your users.

## Additional risks from BYOD

It's to be expected that you will have less control and visibility of a user's personal devices than you would corporate IT. As a result, BYOD deployments may come with greater security risks than a traditional setup.

However, with the right technical and procedural controls, many of these risks can be managed. How you might achieve this depends on the mix of technology you use. This includes any corporately owned devices and authentication solutions. You should think about how much the following risks matter to you before deciding to allow BYOD within your company.

-   Easier user-initiated deliberate data loss (e.g. copying data from work app to personal)
-   Higher potential for accidental data loss (e.g. device backups containing work data, users sharing their device with family)
-   Malicious exfiltration of data (e.g. malicious application leaking data that users have consented it to access)
-   Malicious exploitation of devices as a result of weak security configuration (e.g. no data at rest encryption leading to data extraction)
-   Higher likelihood of unsupported or out-of-date devices, leading to exploitation of known security vulnerabilities
-   Malicious exploitation of devices remains undetected due to lack of monitoring, potentially leading to further spread of malware
-   Additional exposure of devices to threats as a result of being used in a broader personal context, such as user sharing devices or passwords with others

### NOTE

Many of these risks can also be present in corporately - managed solutions.

## Developing a BYOD policy

Once you have established your tolerance for the types of risk associated with BYOD you should start developing your BYOD policy.

Your BYOD policy should clarify both company *and* employee responsibilities.

There are two stages to developing a BYOD policy. First you establish your policy goals, then you determine the controls you can use to achieve them

These questions will help you develop your policy goals:

1.  **What tasks will employees be permitted or encouraged to do,** ***from their own devices?***   
    For example, you may want your employees to submit expense reports from their personal devices but not access emails. 
2.  **What services will you expose to personal devices? And, what data you will expose from within those services?**  
    For example, you might permit users to submit expenses to your HR tool from personal devices, but not change their bank details. Or you might permit access to the holiday booking tool, but not allow access to your sensitive financial documents store.
3.  **How much control will your employees be willing to grant you over their devices?**  
    If you expect users to reject any control of their devices, your ability to manage risks will be compromised. For example, users may not like the idea of their employer being able to remotely wipe their entire device.
4.  **How enforceable are your policies?**  
    If your policies rely entirely on users following specific procedures to keep devices secure, you should also consider what happens if users don’t follow those procedures, and how you might respond in such circumstances.

## Enforcing your policy with technical controls

It is likely that you’ll need to develop your policy in conjunction with the technical controls you will use to implement the policy.

1.  **What types of access are permitted?** For example, phones with native apps, third-party container apps, web browsers – see *technical approaches* for more detail
2.  **What minimum standards for hardware and software versions will you enforce?**
3.  Older or unsupported platform versions are more likely to contain security weaknesses and lack modern mitigations which makes them harder to exploit.
4.  **What device policies will you enforce, and how will you enforce them?** You may be able to enforce some policies, including minimum passcode length and preventing copy and paste between work and personal apps. You will need to check your MDM service documentation for what policies are supported on your chosen devices.
5.  **What service access policies will you enforce?** For example, you could use compliance policies and strong authentication to verify *devices* before they are allowed access to enterprise services if supported. Either way, strong *user* authentication including Multi-Factor Authentication is especially important for BYOD as it may not be possible to implement strong machine authentication for personal devices.
6.  **How will individual services prevent personal devices from accessing sensitive data?** You might want to restrict access from personal devices to certain areas of a single service. For example, you may block access from personal devices to the most sensitive internal documents within your file storage services, while still allowing them to access less sensitive material in the same service.
7.  **How and where will you enforce these policies?** They could be enforced at an authentication service, network firewall, or on specific services.

Security controls which adversely effect the usability of a device will drive down adoption and so undermine your approach. 

Overly restrictive controls may even encourage staff to find workarounds, which might increase your security risk.

## Good practices for BYOD

Where possible, the BCSF recommends using fully corporate-managed devices, which you could enable for personal use in a risk-managed way. This can be done using built-in technologies on modern smartphone platforms. 

Regardless of the technical approach chosen, you need to take special care around the following two areas:

## Protecting against data loss

Where it's reasonable to do so, you should provide workers with a ‘presentation’ of information on their device, rather than storing it locally. You could do this using remote apps or remote desktop technology.

This minimizes the amount of data that can be easily accessed if the device is lost or stolen, and helps prevent bulk data theft if the device is infected. Be aware that security solutions, such as encryption or container products, can be circumvented if malware is present on the device.

If you use a third-party container application as your BYOD solution you should ensure that the product uses good practice cryptography. You may want to also consider using a Virtual Private Network (VPN) to further protect data in transit. 

## Strongly authenticating users and devices

Staff should be made to strongly authenticate themselves before being given access to business data.

Since you may not be able to ensure that all personally owned devices are up to date, some authentication credentials could become compromised as a result. 

You should consider using separate credentials for BYOD access to business systems. For example, usernames and passwords should not be shared between personally owned devices and the business desktop environment. Multi-factor authentication is also highly recommended. 

As BYOD has very different enrolllment processes to corporately owned devices – BYOD typically uses self-enrolllment – securing device authentication to the same level as corporately owned devices may not be possible, and you will likely need to adopt a *trust on first use* approach for these devices. Nonetheless, using machine certificates stored in the dedicated, tamper-resistant hardware, present in many modern devices, can help improve machine authentication security. Alternatively, you can achieve similar results using applications which support secure storage for authentication credentials.

## Technical approaches for smartphones and tablets

Managing smartphone and tablet access to corporate resources means finding the right mixture of device ownership, management and technical control. This section looks at three popular approaches, presented broadly in increasing order of risk. For each, we consider the basic architecture and outline strengths and weaknesses before pointing out places to go for more information.

### Access on and off device

With each of these approaches, consider not only what access personal applications will have to corporate data *on* the device, but also what access those applications will have to corporate data *accessible from* the device.

For example, if your devices have full-device VPNs and you enable them for personal use, then you might be providing users' personal applications with a direct network connection to your enterprise services, and any malware present might also have the same access.

### No COBO

You may come across *Corporately Owned, Business Only (COBO)* modes of operation when reading up on BYOD. These don't have a personal space, so we don't consider them here. Our platform specific guides provide a base COBO configuration you can build on using the BYOD guidance.

### 1\. Corporately owned/managed, personally enabled (COPE)

![](https://lh3.googleusercontent.com/JxUdMK9n-xxiMpzloUKuM_bidrAksffplJdQbMO2Is3IZ6MvONaFdQeKeoLQSNof3LRuemamYxyIC_30hMjZAxkRnlXFf1ntd7CFfgWpaVMoVcwHTxywEtvWqxXzq-RMJtHPr_jW)

The recommended way to enable personal use of work devices is to take full enterprise control of the device, then allow personal use for the cases you're happy with, in a manner you approve of.

This mode can also be applied to personally owned devices where the company takes on a full device management role.

Both Android and iOS provide ways to achieve a COPE setup natively. However, both require you to wipe the device before you can put it into this mode. You can use:

-   Apple iOS [Mobile Device Management (with Supervision)](https://support.apple.com/en-gb/HT202837)
-   Android Enterprise - [Fully managed with a work profile](https://developers.google.com/android/work/overview)

In these modes, you can enable whatever policies and monitoring the platform supports.

This granularity typically provided in COPE configurations allows you to implement the technical controls you need to, mitigating more risk than the other approaches.

### 2\. Personally owned, partially enterprise managed

![](https://lh6.googleusercontent.com/Ekhl-jyoGv5GYUlyU3c1as2Mv1XTXrrTs3aaDpt-OIUbHMi2pYUQXWe0Eq83SZhoWvixnL8OiDCSoN27ccsG8ZUZJFL0DH5q5ry5UjNMtYxS39Ua3LHe9xnwt602m1tT4Nsf7Ixs)

You can also use a management mode which provides less control to your company, but does not require the device to be wiped.

This is a more risky approach because you have less control over each device.

The corresponding features for this mode are:

-   Apple iOS [Device Management (without Supervision) (PDF),](https://www.apple.com/business/docs/resources/Managing_Devices_and_Corporate_Data_on_iOS.pdf) or User enrolllment (iOS 13+ only)
-   Android Enterprise - [Work profile](https://developers.google.com/android/work/overview)

These modes let you enforce *some* device-wide configuration policies, as well as policies which protect corporate data within apps, or managed accounts.

Some of the stronger security policies will not be available, so you may be unable to mitigate certain risks you care about. For example, you will not be able to prevent users from [_installing new configuration profiles_](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf) on iOS in this mode, which can change security settings of the device. 

![](https://lh5.googleusercontent.com/rdtpvw_JlprSkHo62mUypKFJ5VcT1lWLFCJQBJ7O6iPrq9CbDb7QQxluiISUUEeKziAcgx5FXFDyknbxRmJiqQtSbQJS-R3kjAbFPsMDagBy6_Mrg95F1j-6WWsmVL9VRiZRriM6)

### 3\. Personally owned, with managed container application

A variety of third-party vendors – typically MDM vendors – also provide *container applications,* where users are expected to perform work-related tasks within a single application provided by one vendor. These can be managed using [_Mobile Application Management (MAM)_](https://en.wikipedia.org/wiki/Mobile_application_management). 

Sometimes there may be multiple container applications from the same vendor, which appear as separate apps, but behave as if they were one container.

In general, while a container application approach provides less control of whole device settings, it tends to offer stronger controls for you to protect and isolate corporate data from the user’s personal applications. Many container applications can, for example, prohibit copy and paste actions across the container boundary.

Container apps also allow for some monitoring of the device, including checking operating system versions. 

Some users may view the container approach as having worse usability than the native BYOD technologies. For example, users generally won't be able to use a platform’s built-in Mail and Calendar apps. Some users may appreciate the clear separation of personal and work spaces created by the container approach.

Some MDM vendors provide a hybrid of models 2 and 3. In this set up there is partial MDM management of the device, but most work data is held within a container. This approach can help manage more of the risks of using container applications, but may also require the user to accept more enterprise control of their devices as a result.

Microsoft and Google have published some guidance to assist companys with the configuration of access to Office 365 and G Suite, from personal devices:

-   Microsoft has published a [technical guide which provides BYOD access patterns for Office 365](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4zeV7)
-   Google has provided [guidance to help IT admins safely use BYOD in G Suite](https://cloud.google.com/blog/products/g-suite/use-byod-safely-in-g-suite-with-these-6-controls-)

## Technical approaches for desktop and laptop PCs

Things like container apps and MDM/MAM management are much less common on PCs than they are on smartphones and tablets.

On PCs, remote apps, remote desktop, web access, and bootable media are much more common. This section discusses some high level recommendations for traditional PCs.

### 1\. Bootable managed operating system  
 

![](https://lh6.googleusercontent.com/G58YAsRmYif3K6Fc-uMNv-LcJ2WbBHOyKiD37ztrya13ajW7SjcUxdjypdydl2OGoEx8YAmGIvhy-b_7mSUbb_8VNZ_z9xwmyMTG48skonsPuJEKOT5tJpkwmPPGxhvCA5sSoxSu)

One approach for reducing risk is to boot the users’ device into a managed environment using bootable media, typically USB.

There are a variety of third-party products that can do this, as well as Windows to Go, which is built into Windows. 

This approach is arguably the lowest risk way of enabling home PCs to be used, but is still vulnerable to firmware attacks on the host device. You may need to reconfigure the device’s firmware to enable booting from removable media.

### 2\. Remote desktop or remote apps

![](https://lh5.googleusercontent.com/QqdZmTg1ZC2lJe0l20zJcvd4z6WUWlGXEuE8ua0Ks9B5ivveRRsjR2EXFI1ftgG2tmBnUJzL9mFWuAHElW_Th3iGT3bB7-Cl2YN6t1gzbOeW_ahIkdXKU8oShcVoeepr_WJuz1sg)

There are a variety of products that enable users to connect to a remote view of a desktop, or applications running on a remote server. They enable users to work remotely but are still vulnerable to malware that may be present on the users device, which can scrape content as the user accesses it.

However, these ‘thin client’ services are less risky than ‘thick client’ services as they:

-   Provide limited access to corporate data for any malware on the device - it can only screen scrape and key log to access data.
-   Effectively prevent downloading of bulk enterprise data as the files themselves are not exposed.
-   Require minimal amounts of data to be stored on the endpoint, so loss or theft of devices is less problematic.
-   Some remote desktop or remote app software may be able to do simple compliance checks, such as verifying the presence of anti-virus software on the device.

### 3\. Web access to work data 

![](https://lh6.googleusercontent.com/xB1_1WRT7uhpFfImDR1q8TlAfTHi3JNYevAqAEY8Ul4kjHi5EzYU0VjY97zbA9EhnzsswzAf-b7WDk7-GNqslOuespQt6Ih0BThgZmuFjQHmJ8jcEp5caUPBeYvB0RPmr8CLYK5s)

You may consider allowing personal devices to access corporate data through the web browser. This is typically used to enable employees to access work email using their personal PCs and tablets.

This is a particularly risky approach, as you cannot get any confidence in the security or configuration of the device. There are no technical controls you can enforce to reliably prevent data loss or access from insecure or out-of-date devices, so this approach gives rise to the most technical risk.

## Special observations for BYOD

A BYOD approach involves additional complexity and cost when designing or managing your networks, services and devices. We describe some of these below.

### Increased support costs

Security controls previously applied to corporately owned devices may now needing applying to a variety of hardware and software combinations.

This will increase your support demand in several ways, for example:

-   the need to support a greater number of device types
-   keeping multiple operating systems patched and up to date
-   responding to security incidents across a variety of devices and operating systems

As your BYOD implementation expands, ensure you have sufficient IT support capability and expertise to manage a growing range of devices and device platforms.

The associated cost of supporting a variety of devices, operating systems and user devices, which may change rapidly in response to technical advances or user preferences, should also be considered.

### Increased reliance on procedural controls

You might communicate your _BYOD policy_ through employee training, user security procedures and education. If you do this, you will need to ensure that your staff understand their responsibilities when using their own devices for business.

This is important because people often approach security differently when using their own device rather than a corporately owned laptop or PC. Plus, you will be increasingly reliant on procedural controls where technical controls are unavailable. For example, staff may be happy to let family members use their own device, or provide credentials (including passwords) to a third party for maintenance or repair.

You should also conduct regular audits of the business data stored on devices *and* accessible to devices - technical solutions can help with this. When staff leave your company or replace their device, you should ensure all business data is removed and credentials to access business systems are revoked.

### Potential legal issues

From a legal perspective, the responsibility for protecting personal information rests with the data controller, not the device owner. As such, you should be aware of laws relating to your business data, in particular:

In addition, consider how your company’s other obligations can be met if personal devices are being used as part of your business. Regulated industries in particular may face a number of additional regulatory obstacles to implementing BYOD successfully.

You may also need to consider how any commercial or second party agreements are affected by adopting BYOD. For example, there may be existing commercial agreements between companies that restrict the running of business software accessing business data on personally owned devices.