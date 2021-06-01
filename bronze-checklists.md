---
title: BCSF Checklists for Controls (Core)
description: Checklists Home Page
published: true
date: 2021-06-01T19:15:58.759Z
tags: bronze, home
editor: markdown
dateCreated: 2021-02-20T19:51:26.918Z
---

BCSF provides a series of core and advanced check-lists for securing your environments.  These checklists, also known as control sets, describe activities ranging from **Asset** all the way to **Vulnerability** Management.  Before diving into checklists, be sure to review the [Learning and Training](/bronze-training) for critical understanding of why these controls exist and what they can do for your organization.

{.grid-list}
- [BCSF Layered Defense Example *This checklist is a relatively common example of activities/controls used by our customers. While it does not meet minimum standards for cyber security, it is a list that offers substantial value in risk-reduction when implemented.*](/bronze-checklists/layered-defense)
- [NIST SP 800-171 Controls *Governmentwide Controlled Unclassified Information (CUI) 3 Program to standardize the way the executive branch handles unclassified information that requires protection. The CUI Program is designed to address several deficiencies in managing and protecting unclassified information to include inconsistent markings, inadequate safeguarding, and needless restrictions, both by standardizing procedures and by providing common definitions through a CUI Registry.*](/bronze-checklists/compliance-checklist-NIST-800-171)
{.links-list}

# BCSF Core Controls List
> It's normal to feel overwhelmed by cyber security.  There are no shortcuts, no silver bullets, no cheap fixes.  Fortunately, information security is fundamentally layered and incremental.  Below is the **most basic set of actions** your company can do to start improving your cyber security posture. If these seem a little too simple for you, great!, head over to [Advanced Controls](/silver-controls) for the comprehensive list. 
{.is-info}


## Policy actions 

> These actions should be carried out by staff responsible for determining the overall cyber security policy.
{.is-success}


- [ ] Identify and record essential data for regular backups. 
- [ ] Create a password policy. 
- [ ] Enforce a strong password policy and but avoid using forced/scheduled password changes. 
- [ ] Enable user ability to change and rotate passwords on their terms.
- [ ] Decide what access controls your users need so they can access only the information and systems required for their job role (least privilege principle). 
- [ ] Develop an incident response plan. 
- [ ] Inventory, review, and document all of your materially signifcant vendors/applications/systems and develop a continuity policy for each. 
- [ ] Conduct risk assessments of your critical apps and services.
- [ ] Develop a training plan for staff. 
- [ ] Determine how personal devices (BYOD) should be used and how will they be managed in the future as Microsoft and Google change support for unmanaged devices. 
- [ ] Determine the approppriate level of insider threat detection. 
- [ ] Write a clear procedure for onboarding staff (and workstations)
- [ ] Write a clear procedure for offboarding staff (and retiring hardware)

## Technical actions 
> These actions should be carried out by technical staff responsible for the setup and configuration of devices, networks and software.
{.is-success}
- [ ] Secure the domain registrar account by randomizing the password, storing it safely, and enabling all available security features such as PIN, MFA, and security questions.
- [ ] Configure anti-spoofing systems (DMARC, DKIM, and SPF) on your domains.
- [ ] Purchase/Deploy advanced security protection for e-mail. 
- [ ] Pirchase/Deploy an advanced authentication management technology for SaaS. 
- [ ] Enable "external" email notification on inbound email. 
- [ ] Purchase/Deploy a CASB system to monitor your Microsoft 365/G-Suite/DropBox/SharePoint/OneDrive.
- [ ] Purchase/Deploy a third-party backup for your Microsoft/Google e-mail system.
- [ ] Purchase/Deploy an insider threat detection product. 
- [ ] Configure Data Loss Protection features of your Microsoft 365/Google Workspace environment. 
- [ ] Use separate administrative accounts on separate administration workstations.
- [ ] Implement the principle of least privilege on data access.
- [ ] Enable a personal firewall on organization workstations that is configured to deny unsolicited connection requests.
- [ ] Install and monitor centralized on Anti-virus software (endpoint defense tools)
- [ ] Deploy sufficient environment/system/application monitoring and alerts to meet your expectations for uptime, detection, and resolution of issues.
- [ ] Maintain up-to-date antivirus signatures and engines.
- [ ] Block access to physical ports for staff who do not need them. 
- [ ] Consider making a password manager available to your staff to secure their passwords. 
- [ ] Review the star ratings before choosing one from an app store. 
- [ ] Ensure data is being backed up to a backup platform e.g. portable hard drive and/or the cloud. 
- [ ] Set automated back-up periods relevant to the needs of the business. 
- [ ] Switch on password protection for all available devices. 
- [ ] Change default passwords on all internet-enabled devices as per password policy. 
- [ ] Install and turn on tracking applications for all available devices e.g. Find my iPhone. 
- [ ] Enable two-factor authentication (MFA) for all important accounts (e.g email). 
- [ ] Implement Local Administrator Password Solution (LAPS).
- [ ] Apply restrictions to prevent users downloading 3rd party apps. 
- [ ] Check for instances of common executables executing with the hash of another process (e.g., splunklogger.exe with the hash of procdump).
- [ ] Install the latest software updates on all devices and switch on automatic updates with periodic checks. 
- [ ] Ensure all applications on devices are up to date and automatic updates have been set to download as soon as they are released. 
- [ ] Schedule regular manual checks on updates. 
- [ ] Set up encryption on all office equipment. 
- [ ] Use products such as Bitlocker for Windows using a Trusted Platform Module (TPM) with a PIN, or FileVault (on mac OS).
- [ ] Secure Remote Desktop Protocol (RDP) and other remote access solutions using MFA and “jump boxes” for access.
- [ ] Disable unnecessary services on organization workstations and servers.

## Hardware
- [ ] Purchase and deploy cloud-controlled security appliance(s).
- [ ] Purchase and deploy cloud-controlled end-user gateways for mobile workers.
- [ ] Purchase and deploy cloud-controlled enterprise WiFi access points.
- [ ] Purchase and deploy cloud-controlled smart switch(es).
- [ ] Give each teleworker a company owned and managed computer.
- [ ] Purchase hardware MFA keys. 

## Special Recommendations
- [ ] If your organization has ever used SolarWinds Orion versions 2019.4 through 2020.2.1 HF1, refer to CISA’s Emergency Directive ED 21-01, associated supplemental guidance, and CISA’s Activity Alert AA20-352A for additional guidance prior to applying patches.  Although ED 21-01 and associated guidance only apply to Federal Civilian Executive Branch agencies, CISA encourages non-federal entities to review them for recommendations on operating the SolarWinds Orion platform.
- [ ] If using Apple products, sign up for Apple Business Manager (with DEP)

## Training and awareness actions

> These actions should be carried out by staff responsible for implementing staff training and awareness. Every member of the team (including board members) needs enough knowledge to understand how cyber security impacts on their area of focus.
{.is-success}

- [ ] Provide secure physical storage (e.g a locked cupboard) for your staff to write down and store passwords. 
- [ ] Create a Cyber Security training plan that you can use for all staff. 
- [ ] Include details of your ‘Password’ policy explaining how to create a non-predictable. 
- [ ] Include how to spot the obvious signs of phishing. 
- [ ] Include details of your reporting process if staff suspect phishing. 
- [ ] Include details on how your business operates and how they deal with requests via email. Include details of Wi-Fi hotspot vulnerabilities and how to use alternative options (e.g VPN/ Mobile network).
- [ ] Test their compliance. 