---
title: Mitigating malware and ransomware attacks
description: How to defend organizations against malware or ransomware attacks
published: false
date: 2021-06-24T18:22:25.604Z
tags: silver, security-operations, silver-training, ransomware
editor: markdown
dateCreated: 2021-02-22T03:02:19.092Z
---

This guidance helps private and public sector organizations deal with the effects of malware (which includes ransomware). It provides actions to help organizations prevent a malware infection, and also steps to take if you're already infected.

Following this guidance will reduce:

-   the likelihood of becoming infected
-   the spread of malware throughout your organization
-   the impact of the infection

**If you've already been infected with malware,** [**please refer to our list of urgent steps to take**](/guidance/mitigating-malware-and-ransomware-attacks#stepsifinfected)

-   Smaller organizations should refer to the [BCSF's Small Business Guide](/collection/small-business-guide).
-   Larger organizations / enterprises should refer to the [BCSF's Mobile Device Guidance](/collection/mobile-device-guidance).
-   For information about protecting your devices at home, please read [our guidance especially written for individuals and families](/section/information-for/individuals-families#section_4).

---

## In this guidance

-   [What is malware?](#)
-   [Action 1: Make regular backups](#)
-   [Action 2: Prevent malware from being delivered and spreading to devices](#)
-   [Action 3: Prevent malware from running on devices](#)
-   [Action 4: Prepare for an incident](#)
-   [Steps to take if your organization is already infected](#)
-   [Further advice](#)


## What is malware?

Malware is _mal_icious soft_ware_, which - if able to run - can cause harm in many ways, including:

-   causing a device to become locked or unusable
-   stealing, deleting or encrypting data
-   taking control of your devices to attack other organizations
-   obtaining credentials which allow access to your organization's systems or services that you use
-   'mining' cryptocurrency
-   using services that may cost you money (e.g. premium rate phone calls).

### **What is ransomware?**

Ransomware is a type of malware that prevents you from accessing your computer (or the data that is stored on it). The computer itself may become locked, or the data on it might be stolen, deleted or encrypted.

Usually you're asked to contact the attacker via an anonymous email address or follow instructions on an anonymous web page, to make payment. The payment is invariably demanded in a cryptocurrency such as Bitcoin, in order to unlock your computer, or access your data. However, even if you pay the ransom, there is no guarantee that you will get access to your computer, or your files. Occasionally malware is *presented* as ransomware, but after the ransom is paid the files are not decrypted. This is known as [wiper malware](https://en.wikipedia.org/wiki/Wiper_(malware)). **For these reasons, it's essential that you always have a recent offline backup of your most important files and data**.

### **Should I pay the ransom?**

Law enforcement do not encourage, endorse, nor condone the payment of ransom demands. If you do pay the ransom:

-   there is no guarantee that you will get access to your data or computer
-   your computer will still be infected
-   you will be paying criminal groups
-   you're more likely to be targeted in the future

Attackers will also threaten to publish data if payment is not made. To counter this, organizations should take measures to minimize the impact of data exfiltration. 

### **Using a defense in depth strategy**

Since there's no way to **completely** protect your organization against malware infection, you should adopt a 'defense-in-depth' approach. This means using layers of defense with several mitigations at each layer. You'll have more opportunities to detect malware, and then stop it before it causes real harm to your organization. You should assume that some malware **will** infiltrate your organization, so you can take steps to limit the impact this would cause, and speed up your response.



## Action 1: Make regular backups

Up-to-date backups are the most effective way of recovering from a ransomware attack, you should do the following.

-   Make regular backups of your most important files - it will be different for every organization - check that you know how to restore files from the backup, and regularly test that it is working as expected.
-   Ensure you create offline backups that are kept separate, in a different location (ideally offsite), from your network and systems, or in a cloud service designed for this purpose, as ransomware actively targets backups to increase the likelihood of payment. 
-   Make multiple copies of files using different backup solutions and storage locations. You shouldn't rely on having two copies on a single removable drive, nor should you rely on multiple copies in a single cloud service.
-   Make sure that the devices containing your backup (such as external hard drives and USB sticks) are **not** permanently connected to your network. Attackers will target connected backup devices and solutions to make recovery more difficult.
-   You should ensure that your cloud service protects previous versions of the backup from being immediately deleted and allows you to restore to them. This will prevent both your live and backup data becoming inaccessible - cloud services often automatically synchronize immediately after your files have been replaced with encrypted copies.
-   Ensure that backups are only connected to known clean devices before starting recovery.
-   Scan backups for malware before you restore files. Ransomware may have infiltrated your network over a period of time, and replicated to backups before being discovered.
-   Regularly patch products used for backup, so attackers cannot exploit any known vulnerabilities they might contain.

There have been cases where attackers have destroyed copied files or disrupted recovery processes before conducting ransomware attacks. Ideally, backup accounts and solutions should be protected using Privileged Access Workstations (PAW) and hardware firewalls to enforce IP allow listing. [Multi-factor Authentication](/multi-factor-authentication-online-services) (MFA) should be enabled, and the MFA method should not be installed on the same device that is used for the administration of backups. [Privileged Access Management (PAM) solutions](/protecting-system-administration-with-pam) remove the need for administrators to directly access high-value backup systems.



## Action 2: Prevent malware from being delivered and spreading to devices

You can reduce the likelihood of malicious content reaching your devices through a combination of:

-   filtering to only allow file types you would expect to receive
-   blocking websites that are known to be malicious
-   actively inspecting content
-   using signatures to block known malicious code

These are typically done by network services rather than users' devices. Examples include:

-   [mail filtering](/email-security-and-anti-spoofing) (in combination with spam filtering) which can block malicious emails and remove executable attachments.
-   intercepting proxies, which block known-malicious websites
-   internet security gateways, which can inspect content in certain protocols (including some encrypted protocols) for known malware
-   safe browsing lists within your web browsers which can prevent access to sites known to be hosting malicious content

Ransomware is increasingly being deployed by attackers who have gained access remotely via exposed services such as Remote Desktop Protocol (RDP), or unpatched remote access devices. To prevent this organizations should:

-   enable [MFA](/collection/mobile-device-guidance/enterprise-authentication-policy) at all remote access points into the network, and enforce IP allow listing using hardware firewalls
-   use a VPN that [meets BCSF recommendations](/collection/mobile-device-guidance/virtual-private-networks), for remote access to services; Software as a Service or other services exposed to the internet should use Single Sign-On (SSO) where access policies can be defined (for more information read our [blogpost on protecting management interfaces](/blog-post/protect-your-management-interfaces))
-   use the least privilege model for providing remote access - use low privilege accounts to authenticate, and provide an audited process to allow a user to escalate their privileges within the remote session where necessary
-   patch known vulnerabilities in all remote access and external facing devices immediately (referring to our [guidance on how to manage vulnerabilities within your organization](/guidance/vulnerability-management) if necessary), and follow vendor remediation guidance including the installation of new patches as soon as they become available

Prevent malware spreading across your organization by following [BCSF guidance on preventing lateral movement](/guidance/preventing-lateral-movement). You should also:

-   use [MFA](/guidance/multi-factor-authentication-online-services) to authenticate users so that if malware steals credentials they can't easily be reused
-   ensure obsolete platforms (Operating Systems (OS) and apps) are properly segregated from the rest of the network - refer to [BCSF guidance on Obsolete Platforms](/collection/mobile-device-guidance/managing-the-risks-from-obsolete-products) for further details
-   regularly review and remove user permissions that are no longer required, to limit the malware's ability to spread
-   ensure system administrators avoid using their accounts for email and web browsing (to prevent malware being able to run with their high level of system privilege)
-   practice good asset management, including keeping track of which versions of software are installed on your devices so that you can target security updates quickly
-   keep devices and infrastructure patched, especially security-enforcing devices on the network boundary (such as firewalls and VPN products)



## Action 3: Prevent malware from running on devices

A 'defense in depth' approach assumes that malware will reach your devices. You should therefore take steps to prevent malware from running. The measures required will vary for each device type, OS and version, but in general you should look to use device-level security features. Organizations should:

-   centrally manage devices in order to only permit applications trusted by the enterprise to run on devices, using technologies including [AppLocker](/collection/mobile-device-guidance/platform-guides/windows-10/applocker-and-the-windows-app-store), or from [trusted app stores (or other trusted locations)](/collection/mobile-device-guidance/using-third-party-applications)
-   [consider whether enterprise antivirus or anti-malware products are necessary](/collection/end-user-device-security/eud-overview/common-questions#antivirusantimalware), and keep the software (and its definition files) up to date
-   provide security education and awareness training to your people, for example [BCSF's Top Tips for Staff](/blog-post/ncsc-cyber-security-training-for-staff-now-available)
-   disable or constrain scripting environments and macros, by:
    -   enforcing PowerShell Constrained Language mode via a User Mode Code Integrity (UMCI) policy - you can use [AppLocker](/collection/mobile-device-guidance/platform-guides/windows-10/applocker-and-the-windows-app-store) as an interface to UMCI to automatically apply Constrained Language mode
    -   protecting your systems from [malicious Microsoft Office macros](/guidance/macro-security-for-microsoft-office)
-   disable AutoRun for mounted media (prevent the use of removable media if it is not needed)

In addition, attackers can force their code to execute by exploiting vulnerabilities in the device. Prevent this by keeping devices well-configured and up to date. We recommend that you:

-   install security updates as soon as they become available in order to fix exploitable bugs in your products
-   enable automatic updates for OSs, applications, and [firmware](/blog-post/automating-uefi-firmware-updates) if you can
-   use the latest versions of OSs and applications to take advantage of the latest security features
-   configure host-based and network firewalls, disallowing inbound connections by default

The BCSF's [Mobile Device Guidance](/collection/mobile-device-guidance) provides advice on how to achieve this across a variety of platforms.

---

## Action 4: Prepare for an incident

Malware attacks, in particular ransomware attacks, can be devastating for organizations because computer systems are no longer available to use, and in some cases data may never be recovered. If recovery is possible, it can take several weeks, but your corporate reputation and brand value could take a lot longer to recover. The following will help to ensure your organization can recover quickly.

-   Identify your critical assets and determine the impact to these if they were affected by a malware attack.
-   [Plan for an attack](/collection/incident-management), even if you think it is unlikely. There are many examples of organizations that have been impacted by collateral malware, even though they were not the intended target.
-   Develop an internal and external communication strategy. It is important that the right information reaches the right stakeholders in a timely fashion.
-   Determine how you will respond to the ransom demand and the threat of your organization's data being published.
-   Ensure that incident management playbooks and supporting resources such as checklists and contact details are available if you do not have access to your computer systems.
-   Identify your legal obligations regarding the reporting of incidents to regulators, and understand how to approach this.
-   [Exercise your incident management plan](/guidance/effective-steps-to-cyber-exercise-creation). This helps clarify the roles and responsibilities of staff and third parties, and to prioritize system recovery. For example, if a widespread ransomware attack meant a complete shutdown of the network was necessary, you would have to consider:
    -   how long it would take to restore the minimum required number of devices from images and re-configure for use
    -   how you would rebuild any virtual environments and physical servers
    -   what processes need to be followed to restore servers and files from your backup solution
    -   what processes need to be followed if onsite systems and cloud backup servers are unusable, and you need to rebuild from offline backups
    -   how you would continue to operate critical business services
-   After an incident, revise your incident management plan to include lessons learnt to ensure that the same event cannot occur in the same way again.

The [BCSF’s free Exercise in a Box online tool](https://exerciseinabox.service.ncsc.gov.uk/), contains materials for setting up, planning, delivery, and post-exercise activity.



## Steps to take if your organization is already infected

If your organization has already been infected with malware, these steps may help limit the impact:

1.  Immediately disconnect the infected computers, laptops or tablets from all network connections, whether wired, wireless or mobile phone based.
2.  In a very serious case, consider whether turning off your Wi-Fi, disabling any core network connections (including switches), and disconnecting from the internet might be necessary.
3.  Reset credentials including passwords (especially for administrator and other system accounts) - but verify that you are not locking yourself out of systems that are needed for recovery.
4.  Safely wipe the infected devices and reinstall the OS.
5.  Before you restore from a backup, verify that it is free from any malware. You should only restore from a backup if you are **very** confident that the backup **and** the device you're connecting it to are clean.
6.  Connect devices to a clean network in order to download, install and update the OS and all other software.
7.  Install, update, and run antivirus software.
8.  Reconnect to your network.
9.  Monitor network traffic and run antivirus scans to identify if any infection remains.

The BCSF has jointly published an advisory: [Technical Approaches to Uncovering and Remediating Malicious Activity](https://us-cert.cisa.gov/ncas/alerts/aa20-245a), which provides more detailed information about remediation processes.

**Note:** Files encrypted by most ransomware typically have no way of being decrypted by anyone other than the attacker. However, the [No More Ransom Project](https://www.nomoreransom.org/en/index.html) provides a collection of decryption tools and other resources from the main anti-malware vendors, which may help.


