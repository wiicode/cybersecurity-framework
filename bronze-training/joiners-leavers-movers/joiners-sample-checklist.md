---
title: Joiners: Sample checklist for onboarding staff or contractors.
description: This list is developed for smaller organizations.
published: true
date: 2021-07-01T21:06:09.301Z
tags:
editor: markdown
dateCreated: 2021-07-01T20:41:14.767Z
---

# New Employee or Contractor
> BCSF strongly recommends a "two key" approach to authorization and granting of access controls.  In most cases a manager requests specific items, an operations admin implements them, and then the permssions should be audited.  We provide additional guidance on this in our [Joiners Sample Worfklow](#) article.
{.is-warning}

 
1. Request is assembled and includes:
   - [ ] Full name required for establishing the username.
   - [ ] Start date
   - [ ] Job Role
   - [ ] Equipment Preferences (new or re-assignment)
2. Basic documentation procedures:
   - [ ] User is added to a database or employee management system.
   - [ ] [Sysem of record](#) is started and updated along the way.
3. Provisioning process is started:
   - [ ] Primary identity system entry is created.
     - [ ] Examples include Azure Directory, on-premise Active Directory, Okta, Amazon Directory.
     - [ ] **NOTE**: [Advanced Identity systems](#) can automatically provision many of the items listed below.
   - [ ] Provision data storage and sync accounts.
       - [ ] Example include Apple Business Manager iCloud accounts, DropBox, etc.
   - [ ] Create & License Microsoft 365 / Google Workspace account
     - [ ] Add to Groups
     - [ ] Add to Calendars.
     - [ ] Add to Teams
   - [ ] Provision/Grant access to desired SaaS accounts.
     - [ ] These may include remote desktop services, core business applications, or applications linked to the specific job role or individual.
     - [ ] Examples include Zoom, Monday, TeamWork, ZenDesk, Slack.
   - [ ] Provision/Grant access to desired on-premise accounts.
     - [ ] These may include local client/server applications, core business applications, or applications linked to the specific job role or individual.
4. Assign rights.
   - [ ] Beyond creating accounts, your business applications may have specific procedures for granting access to resources. This section would store those.
5. Verify MFA enrollment status.
6. Perform necessary activation tasks.
   - [ ] While we discourage logging into Microsoft/Google and other critical accounts, BCSF acknowledges that your environment may have special requirements to expedite onboarding.  This section is for such tasks.
7. Send "Welcome Document", you have to create a "Welcome FIRST LAST!"  in Messages.  Welcome document will contain additional steps for the user including enabling MFA on their accounts.


# New macOS Device
> macOS devices on 10.15 or above run strict privacy controls. Despite Device Enrollment, MDM, and profiles a user must manually consent to applications which record/transmit screen or allow remote access.  This is normal and organizations should plan accordingly.
{.is-info}

1. [ ] Go to `provide your link` start the Mobile Device Management (MDM) installation process; be sure to complete the install/approval of the configuration profile.
2. [ ] Install the necessary Remote Administration and Management Tool by `provide your steps.` You may also have specific instructions to install an MDM Agent application that extends MDM capabilities.
3. [ ] Install corporate anti-malware software.
4. [ ] Set Energy Setting to Never sleep if you expect a delay or need extra time.
   - [ ] Note: BCSF recommends managing energy through MDM.
5. [ ] Rename device (override device facts). Our preferred naming convention for macOS devices is `firmname-unit-name`
6. [ ] Configure basline settings.
   - [ ] Deploy a secondary administrator profile.
   - [ ] Deploy employee monitoring tools.
   - [ ] Enable FileVault
   - [ ] Enable Firewall
   - [ ] Verify Gatekeeper
   - [ ] Verify System Integrity Protection
   - [ ] Remove local admin rights if necessary/required.
     - [ ] Note: for macOS compensating controls are often preferred.
   - [ ] Deploy Printers
   - [ ] Deploy VPN Profiles
7. [ ] Deploy primary software.
   - [ ] We encourage the use of **Apps & Games** (formerly known as the Apple Volume Purchase Program (VPP)) to push business applications.  Your list may include:
     - [ ] Outlook, Word, Excel, PowerPoint
       - [ ] Note: Microsoft Teams presently requires the Office package or use of special MDM Configuration Profile.
     - [ ] Zoom Meetings
     - [ ] Parallels Client
     - [ ] Chrome or Microsoft Edge
       - [ ] Note: BCSF recommends Safari, Chrome, Or Microsofot Edge while using managment/enterprise features.
8. [ ] Help the user perform the initial onboarding tasks:
   - [ ] Sign into ABM iCloud
   - [ ] Verify all Profiles are approved.
   - [ ] Launch Office Apps and Sign-In
   - [ ] Launch File sync apps, sign in, and verify startup on login.
   - [ ] Configure e-mail.
   - [ ] Set preferred Mail app
   - [ ] Set preferred Browser app
   - [ ] Remove unused Dock items.

# New Windows Device using Azure AD Join
> Windows Devices are best managed through MDM which supports Group Policy Administration templates and Windows Autopilot.
{.is-warning}


1. [ ] Verify system is Windows 10 (or 11) Pro/Business.
2. [ ] If asked during initial setup "Set up for an organization"
Sign in using the Microsoft Online for Work account into the computer, this process is known as "Azure AD Domain Join"
3. [ ] In Windows settings, navigate to 'Settings > Accounts > Access work or school.' You can also search 'Connect to work or school' in your Windows menu to find the below page. On native Windows 10, click 'Enroll only in device management'.
   - [ ] Your organization process may have additional options.
   - [ ] Be awre that Windows 10 21H1 asks for an email address during this process.  The email address may result in one of three behaviors and you may need to control for them.
     - [ ] Behavior 1: Device successull joins Windows Intune and this is along your expectations.
     - [ ] Behavior 2: Device fails because organization is using Microsoft 365 for productivity but uses another MDM system for device management. In this case, we recommend you enter an email address with a false domain name, such as `flast@yoruorganization.false` to bypass the reverse lookup.
     - [ ] Behavior 3: Device is directory joined but this step is skipped, resulting in an out-of-compliance device.
4. [ ] Install the necessary Remote Administration and Management Tool by `provide your steps.`
5. [ ] Install corporate anti-malware software.
6. [ ] Go to Settings > System > Power & sleep; set the machine to Always On.  You can disable this after device is handed over to the user.
   - [ ] Note: BCSF recommends managing energy through MDM.
7. [ ] Configure basline settings.
   - [ ] Deploy a secondary administrator profile.
   - [ ] Deploy employee monitoring tools.
   - [ ] Enable BitLocker
   - [ ] Verify Firewall
   - [ ] Verify System Integrity Protection
   - [ ] Remove local admin rights if necessary/required.
     - [ ] Note: for macOS compensating controls are often preferred.
   - [ ] Deploy Printers
   - [ ] Deploy VPN Profiles
8. [ ] Deploy primary software.
   - [ ] We encourage the use of **Windows Store** to push business applications and leverage deployment tools as much as possible.  Your list may include:
     - [ ] Microsoft Office (suite) often preinstalled but is best configured using the **Office Deployment Tool**.
     - [ ] Zoom Meetings
     - [ ] Adobe Creative Cloud apps (best deployed via custom packages built in the Adobe Admin Console)
     - [ ] Parallels Client
     - [ ] Chrome or Microsoft Edge
       - [ ] Note: BCSF recommends Chrome, Or Microsofot Edge while using managment/enterprise features.
9. [ ] Help the user perform the initial onboarding tasks:
   - [ ] Launch Office Apps and Sign-In
   - [ ] Launch File sync apps, sign in, and verify startup on login.
   - [ ] Configure e-mail.
   - [ ] Set preferred Mail app
   - [ ] Set preferred Browser app
   - [ ] Remove unused Task Bar items and Pin preferred apps.


# New Windows Device using local Active Directory domain.
> Unless using Windows Autopilot, it is exponentially easier to deploy Windows devices by refusing to connect to WiFi when they first power up.  By refusing WiFi connection Windows will offer a choice to create a local user setup which will then simplify the process known as "Domain Join."  Once WiFi is connected, that choices is no longer possible and the machine will complete a Microsoft 365 sign-in.
{.is-danger}


1. [ ] Verify system is Windows 10 (or 11) Pro/Business.
2. [ ] Do not connect to WiFi and attempt to select all "local" or "skip" choices to arrive at a local user.  This procedure has changed frequently so prepare `your own steps` and maintain them.
3. [ ] In Windows settings, navigate to 'Settings > Accounts > Access work or school.' You can also search 'Connect to work or school' in your Windows menu to find the below page. On native Windows 10, click 'Enroll only in device management'.
   - [ ] Your organization process may have additional options.
   - [ ] Be awre that Windows 10 21H1 asks for an email address during this process.  The email address may result in one of three behaviors and you may need to control for them.
     - [ ] Behavior 1: Device successull joins Windows Intune and this is along your expectations.
     - [ ] Behavior 2: Device fails because organization is using Microsoft 365 for productivity but uses another MDM system for device management. In this case, we recommend you enter an email address with a false domain name, such as `flast@yoruorganization.false` to bypass the reverse lookup.
     - [ ] Behavior 3: Device is directory joined but this step is skipped, resulting in an out-of-compliance device.
4. [ ] Install the necessary Remote Administration and Management Tool by `provide your steps.`
5. [ ] Install corporate anti-malware software.
6. [ ] Go to Settings > System > Power & sleep; set the machine to Always On.  You can disable this after device is handed over to the user.
   - [ ] Note: BCSF recommends managing energy through MDM.
7. [ ] Configure basline settings.
   - [ ] Deploy a secondary administrator profile.
   - [ ] Deploy employee monitoring tools.
   - [ ] Enable BitLocker
   - [ ] Verify Firewall
   - [ ] Verify System Integrity Protection
   - [ ] Remove local admin rights if necessary/required.
     - [ ] Note: for macOS compensating controls are often preferred.
   - [ ] Deploy Printers
   - [ ] Deploy VPN Profiles
8. [ ] Deploy primary software.
   - [ ] We encourage the use of **Windows Store** to push business applications and leverage deployment tools as much as possible.  Your list may include:
     - [ ] Microsoft Office (suite) often preinstalled but is best configured using the **Office Deployment Tool**.
     - [ ] Zoom Meetings
     - [ ] Adobe Creative Cloud apps (best deployed via custom packages built in the Adobe Admin Console)
     - [ ] Parallels Client
     - [ ] Chrome or Microsoft Edge
       - [ ] Note: BCSF recommends Chrome, Or Microsofot Edge while using managment/enterprise features.
9. [ ] Help the user perform the initial onboarding tasks:
   - [ ] Launch Office Apps and Sign-In
   - [ ] Launch File sync apps, sign in, and verify startup on login.
   - [ ] Configure e-mail.
   - [ ] Set preferred Mail app
   - [ ] Set preferred Browser app
   - [ ] Remove unused Task Bar items and Pin preferred apps.
