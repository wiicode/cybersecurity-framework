---
title: Using third-party applications
description: Advice on the assessment, distribution and use of third-party applications on smartphones, tablets, laptops and desktop PCs
published: false
date: 2021-06-02T02:49:46.486Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:43:20.060Z
---

All modern mobile devices support third-party applications. Most also offer an online marketplace from which to install them. There are clear advantages in allowing your users and devices to access a broad range of applications. However, it's important to think about the risks to your devices and data from these applications.

This guidance will help risk owners and administrators create organizational policies for the use of third party applications which minimizes risk, without limiting utility.

---

## Why secure your third party apps?

Third-party software is regularly installed on mobile devices and will typically be able to read and/or modify some or all of the user's data on that device.

In some cases, applications will also have access to your organization's data too. Once a third-party application has had the chance to access data, it is very difficult to know exactly what has been done with that data. Some applications will helpfully sync your local data to cloud services, some may handle it in insecure ways, and others may use third-party libraries within the application which have their own security risks.

By developing an organizational policy which outlines the types of application permitted, you'll be able to more effectively manage risks associated with running third-party code.

---

## Preparing for third party applications

Your organization will naturally want to take advantage of the productivity benefits provided by third-party applications, so you will need to develop a policy which balances the business need with the information risk.

We advise thinking about this in two steps:

1.  [Minimising the *likelihood*](bronze-training/mobile-device-guidance/using-third-party-applications) that you will come to have malicious or insecure applications on your devices
2.  [Minimising the *impact*](bronze-training/mobile-device-guidance/using-third-party-applications) of any application being malicious or insecure

---

## 1\. Minimize the likelihood of using malicious or insecure applications

Ideally you will prevent malicious and insecure code from reaching your devices at all. In practice it's very hard to be 100% certain, but there are several measures you can take.

**Allow lists and deny lists**

One of your main defenses against malicious applications is to prevent known-malicious applications from executing on your devices.

Most platforms enable you to strongly enforce which applications can run, but this can involve an administrative burden as it will require manual approval for exactly which applications can run. That said, it is a highly effective strategy for preventing malicious code from running, and can be well worth the cost.

On platforms with an application marketplace, you will be able to configure the device so that it will not run applications from any other source. You can then apply policies to only allow approved apps to install and run, what's know as *an allow list*. Conversely, you can specify a *deny list* of applications that are specifically prohibited.

*Allow lists* are a much better strategy than *deny lists*. They can be joined up with software licensing and procurement activities in a lightweight approvals process. Allow/deny lists on most platforms can be configured using [Mobile Device Management](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services).

On some platforms, applications can be delivered through a variety of mechanisms, not just official marketplaces. In these cases, you may be required to manually configure trusted code signers, or allow specific application hashes. For example, on Windows 10 you will likely want to use a combination of [App Locker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Windows Defender Application Control](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) to ensure that only applications you trust will run. You can usually run these features in a 'reporting' mode, which won't actually block any applications, but will help you adopt the feature by reporting back the range of applications that are currently in use across your organization and *would* be blocked if you ran the features in 'enforcing' mode. 

#### **Formal assessment and assurance**

One way of getting confidence in the security of third-party applications is to undertake a formal assessment of the application or take advantage of an existing third-party assessments. However these can be expensive, short-lived, and may not give you the assurances you need.

Many organizations provide databases of app assessments, sometimes including 'risk scores' which you can use to inform your policy.

You can also use:

-   [Common criteria](https://www.niap-ccevs.org/) assessments
-   [Commercial product assurance](/bronze-controls/saas-security) evaluated product reports

You can perform in-house assessments using something like the [NIST approach](https://csrc.nist.gov/publications/detail/sp/800-163/rev-1/final), or contract out an assessment to a third party, who might follow a similar approach.

If your policy relies on an up-to-date assessment of an application before you approve a new version, you need to consider how you will handle security vulnerabilities within an application and how you can quickly adopt the new version.

#### **Reputation assessment**

Formal assessments are often expensive, slow, and can have limited benefit. One cost-effective way to assess the risk of an application is to conduct a risk assessment of the developer behind application. By understanding the security maturity of the developers, including historic security breaches, you can estimate the likelihood that you will be affected by a future security breach.

Ultimately you should aim to understand three aspects of the developer's security:

-   *The likelihood that the application or developer is malicious*

Applications from large, well-known developers are less likely to be malicious than an application from a developer you've never heard of.  
 

-   *The likelihood that there will be a security breach involving that developer or application*

Using mature, popular applications from a developer with a good track record will minimize the risk that your applications are vulnerable.  
 

-   *What impact a compromise would have*

You should aim to minimize the amount of sensitive data you allow an application to access. You can also take into account which other types of organization are using that application, so that your data is a small part of a much larger data set if that application is breached.  
 

#### **Application store checks**

Most application stores make checks that applications are not malicious when they are added and updated. By getting your applications from such a store, you are reducing the risk that the application is malicious. However, this is not a guarantee. Most stores have hosted malware at some point, and you should take additional steps to reduce the risk further.

You should consider what application store checks look for. Most checks are for outright malcious behavior, such as SMS fraud. Certain behaviors - like syncing private data to cloud services - might be permitted under store policy, but not permitted under your enterprise policy. Reading an application's privacy policies might help you decide. These can also usually be obtained from within the application stores that distribute the application.

#### **Security apps**

On platforms where you can install applications from outside an application store, you might want to consider using [security apps or antivirus](/bronze-training/mobile-device-guidance/antivirus-and-other-security-software) to lower the risk of executing malicious code. However, this approach only lowers the risk and does not remove it entirely.

#### **Support and security updates**

When using third-party applications on your devices, you should regularly update them to ensure that the latest security fixes are included. See [*keeping your devices and applications up-to-date*](/bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date) for further advice on this.

---

## 2\. Minimize the impact of using malicious or insecure applications

The second part of your approach should to reduce the impact of compromise, should an application you use be found to be malicious or insecure.

#### **Splitting work and personal apps into different spaces**

Most platforms provide a way for organizations to configure *containers* or *work profiles* that provide separation between personal apps and work data.

While these spaces are not impermeable, they lower the risk that arbitrary third-party applications can access and potentially compromise sensitive work data. Your organization's third-party application policies can be more liberal if you are happy with the security level that this separation provides.

These spaces are often part of a platform's bring your own device (BYOD) features. You should read our [guidance on BYOD](/bronze-controls/byod-guidance) if you are considering that approach.

#### **Policies on limiting risky apps to only the individuals that need them**

Many [mobile device management](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) products allow you to decide exactly which users are allowed to install and use an application.

If there are applications which you consider risky, but some users have a strong business need for them, you can consider allowing access for these users only.

For example, if you want to enable your social media team to use applications which sync contact lists to the cloud, you may want to enable those applications only for the social media team and put in place some procedural controls to limit the content of those users' contact lists.

#### **Network architectures which limit access to third-party applications**

When third-party applications are used, certain network architectures may become riskier.

For example, if your devices have device-wide VPN access to a core network, then all third-party applications will also be able to access that core network. If there is any unprotected data on that network, then those applications may be able to access that data.

[If you have adopted a zero-trust approach to your network design,](/bronze-training/mobile-device-guidance/infrastructure/network-architectures-for-remote-accesss) which requires authentication for every connection, your systems will be more resilient to this kind of attack.

#### **High-privilege applications**

Certain applications, such as security products and management services, will run with higher privileges. These applications pose a higher risk to your data as they may have broader access, or be subject to fewer controls to limit the impact from compromise. You should more carefully consider the security of these applications.

---

## How to manage third party applications

To help you use third-party applications on your organizations' devices, you should:

**Agree an acceptable level of risk with stakeholders**

Firstly, you should agree with key stakeholders what the acceptable level of risk is for your organization. For example:

-   What app behaviors will be prohibited or high-risk (e.g. accessing contacts on devices that sync with your global address list)?
-   How will you assess a vendor as reputable?
-   Might the application make it difficult to comply with any regulations for auditing stored data?

**Develop an applications approval process**

You can develop a process for assessing applications against your agreed level of acceptable risk (see previous point).

You should balance your assessment against user productivity needs:

-   The process should include someone from procurement, legal, security, IT admin, and user representatives, as required.
-   Integrate this process into your standard software asset management routine and run assessments in parallel.
-   Make the process fast, lightweight and responsive, to ensure users feel well-served by the process.
-   You can use third-party assessments to help inform your decision, but don't wholly rely on them.
-   Decide how you will handle updates to software. Most popular mobile applications update at least once per month and you should be able to handle this.
-   Regularly re-review apps you have approved, in case things have changed.
-   You should be able to approve most regular business apps into your app catalogue for anyone to use.
-   For applications you consider risky, you may wish to only allow users with a strong business need to install them.
-   As part of the security review, look at historic security incidents involving the application or developer, as well as any other sources you feel are relevant.

**Use architectural approaches to limit risk**

Where there are user requirements for applications that may present unacceptable levels of risk, there may be architectural approaches which can bring down the risk level:

-   Some platforms may provide the ability to enterprise manage which permissions a third-party application can request, [using MDM](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services). You can use these features to prevent risky apps accessing work data.
-   If the platform supports it, we recommend not allowing users to install arbitrary software from outside of curated app stores. Follow our [platform-specific guidance](/bronze-training/platform-guides) for recommendations about how to achieve this. Enterprise app catalogues typically provide a good balance of security and flexibility for the platform.
-   Don't allow third-party apps to access work data unless they are doing a work-related function. This can be achieved by using a [*Corporately Owned, Personally Enabled (COPE)*](/bronze-training/platform-guides) approach, or a [*Bring Your Own Device (BYOD)*](/bronze-controls/byod-guidance) approach. In both of these cases, you can enable users to install riskier apps outside of the trusted work space, prohibiting those applications from accessing work data.
-   Some platforms may provide additional [logging features](/bronze-training/mobile-device-guidance/logging-and-protective-monitoring) that may enable you to take a *trust and verify* approach.
-   If using containers, the ideal approach is to have the personal container as part of the work profile (e.g. the [fully managed device with a work profile configuration of Android Enterprise](https://developers.google.com/android/work/terminology#fully_managed_device_with_a_work_profile)) rather than the converse of having work containers on a personal device, but the converse is often simpler. You might be able to have separate virtual machines for personal usage or riskier behavior as a compromise (e.g. for developers who need admin rights).