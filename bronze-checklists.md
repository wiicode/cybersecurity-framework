---
title: BCSF Checklists for Controls (Core)
description: Checklists Home Page
published: true
date: 2021-04-22T14:29:18.052Z
tags: bronze, home
editor: markdown
dateCreated: 2021-02-20T19:51:26.918Z
---

BCSF provides a series of core and advanced check-lists for securing your environments.  These checklists, also known as control sets, describe activities ranging from **Asset** all the way to **Vulnerability** Management.  Before diving into checklists, be sure to review the [Learning and Training](/bronze-training) for critical understanding of why these controls exist and what they can do for your organization.

{.grid-list}
- [BCSF Layered Defense Example *This checklist is a relatively common example of activities/controls used by our customers. While it does not meet minimum standards for cyber security, it is a list that offers substantial value in risk-reduction when implemented.*](/bronze-checklists/layered-defense)
- [BCSF NIST SP 800-171 Controls *Governmentwide Controlled Unclassified Information (CUI) 3 Program to standardize the way the executive branch handles unclassified information that requires protection. The CUI Program is designed to address several deficiencies in managing and protecting unclassified information to include inconsistent markings, inadequate safeguarding, and needless restrictions, both by standardizing procedures and by providing common definitions through a CUI Registry.*](/bronze-checklists/compliance-checklist-NIST-800-171)
- [BCSF Advanced Controls - Complete Guide *Extensive cyber security control environment. We maintain a significant set of controls common to our environments and those of our customers.  Collectively, this section informs small companies on what actions to take to meet specific policy areas.  It is highly recommended that you develop your Policies before starting on checklists.*](/bronze-checklists/bcsf-advanced-control-checklists)
{.links-list}

# Starting at zero? Here are actions You Can Take Right Now
> It's normal to feel overwhelmed by cyber security.  There are no shortcuts, no silver bullets, no cheap fixes.  Fortunately, information security is fundamentally layered and incremental.  Below is the **most basic set of actions** your company can do to start improving your cyber security posture. If these seem a little too simple for you, great!, head over to [BCSF Advanced Controls](/bronze-checklists/bcsf-advanced-control-checklists) for the comprehensive list. 
{.is-info}


## Policy actions 

> These actions should be carried out by staff responsible for determining the overall cyber security policy.
{.is-success}


- [ ] Identify and record essential data for regular backups. 
- [ ] Create a password policy. 
- [ ] Enforce a strong password policy and but avoid using forced/scheduled password changes.  
- [ ] Enable user ability to change and rotate passwords on their terms.
- [ ] Decide what access controls your users need so they can access only the information and systems required for their job role (least privilege principle). 
- [ ] Decide what staff need access to USB drives Sign up to threat alerts and read cyber local advice e.g. briefing sheets/threat reports from www.bentosecurity.org/us-cert
- [ ] Create an inventory of approved USB drives and their issued owners, and review whether the ownership is necessary periodically

## Technical actions 

> These actions should be carried out by technical staff responsible for the setup and configuration of devices, networks and software.
{.is-success}

- [ ] Use separate administrative accounts on separate administration workstations.
- [ ] Implement the principle of least privilege on data access.
- [ ] Enable a personal firewall on organization workstations that is configured to deny unsolicited connection requests.
- [ ] Install and monitor centralized on Anti-virus software (endpoint defense tools)
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

### Special Recommendations
- [ ] If your organization has ever used SolarWinds Orion versions 2019.4 through 2020.2.1 HF1, refer to CISA’s Emergency Directive ED 21-01, associated supplemental guidance, and CISA’s Activity Alert AA20-352A for additional guidance prior to applying patches.  Although ED 21-01 and associated guidance only apply to Federal Civilian Executive Branch agencies, CISA encourages non-federal entities to review them for recommendations on operating the SolarWinds Orion platform.


## Training and awareness actions

> These actions should be carried out by staff responsible for implementing staff training and awareness. Every member of the team (including board members) needs enough knowledge to understand how cyber security impacts on their area of focus.
{.is-success}

- [ ] Provide secure physical storage (e.g a locked cupboard) for your staff to write down and store passwords. 
- [ ] Create a Cyber Security training plan that you can use for all staff. 
- [ ] Include details of your ‘Password’ policy explaining how to create a non-predictable. 
- [ ] Include how to spot the obvious signs of phishing. 
- [ ] Include details of your reporting process if staff suspect phishing. 
- [ ] Include details on how your business operates and how they deal with requests via email. Include details of Wi-Fi hotspot vulnerabilities and how to use alternative options (e.g VPN/ Mobile network).