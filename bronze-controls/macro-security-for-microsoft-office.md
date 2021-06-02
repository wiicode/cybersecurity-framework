---
title: Macro Security for Microsoft Office
description: Why macros are a threat, and the approaches you can take to protect your systems.
published: true
date: 2021-06-02T20:46:56.957Z
tags: guidance, bronze, bronze-controls
editor: markdown
dateCreated: 2021-06-02T13:28:42.279Z
---

This guidance describes how administrators can help protect their systems from malicious Microsoft Office macros. It outlines why macros are a threat, and the approaches you can take to protect your devices.

## What are macros, and why are they a problem?

A macro is a small program that is often written to automate repetitive tasks in Microsoft Office applications. Macros have been historically used for a variety of reasons - from an individual automating part of their job, to organizations building entire processes and data flows. Macros are written in Visual Basic for Applications (VBA) and are saved as part of the Office file.

Macros are often created for legitimate reasons, but they can also be written by attackers to gain access to or harm a system, or to bypass other security controls such as application allow listing. In fact, exploitation from malicious macros [is one of the top ways that organizations around the world are compromised today](https://cofense.com/microsoft-office-macros-still-leader-malware-delivery/). Malicious macros can do almost anything that other malware can do to your system, including emulating ransomware, stealing data, and emailing itself out to your contacts.

Malicious macros are not new; the underlying attack has remained unchanged since the 1990s, and they still form the majority of attacks targeting Microsoft Office. However, obfuscation and dynamic content loading has made malicious documents more difficult for traditional antivirus to detect.

Macros are often part of phishing or spear phishing campaigns. In this, an attacker sends emails and attempts to convince the user to open the attached file and run the malicious macro. Techniques (such as [these seen by Microsoft](https://twitter.com/JohnLaTwC/status/775689864389931008)) successfully use social engineering to trick well-intentioned users into enabling malicious Office macros. The [*BCSF* phishing guidance](/bronze-controls/phishing) discusses how you can defend your *organization* against phishing attacks.

---

## Protecting your systems from malicious macros

The only effective way to protect your systems against malicious macros is to disable macros across Office apps, and ensure users cannot re-enable them.

Many organizations currently rely on Office macros for day-to-day business functions, including where they’re used to interact with external partners. Organizations that are still using macros should develop a strategy for replacing them - we've included a few tips below for [how you might do this](/guidance/macro-security-for-microsoft-office#reduce).

If you can’t yet turn macros off, you will need to find the combination of mitigations listed below that are most effective for you, as different organizations use macros in different ways. That said, for **all** installations of Microsoft Office you should:

-   disable Office macros except in the [specific](https://docs.microsoft.com/en-gb/DeployOffice/plan-office-365-proplus#step-3---choose-your-update-channels) apps where they are required
-   only enable macros for staff that rely on them every day
-   use an anti-malware product that integrates with the [Anti Malware Scan Interface (AMSI)](https://docs.microsoft.com/en-us/windows/win32/amsi/antimalware-scan-interface-portal) on Windows 10
-   use the latest version of Office ([ideally the Monthly Channel](https://docs.microsoft.com/en-gb/DeployOffice/plan-office-365-proplus#step-3---choose-your-update-channels)) on the latest version of the platform

#### **Tip 1. Disable macros where they're not used**

If your *organization* does not use macros, they should be turned off entirely. If you cannot yet turn macros off, you should work on replacing the macros that your business relies on, so that you can turn them off entirely in the future. Larger organizations should consider only enabling macros for the specific groups or teams that need them. This allows training to be better-focused and appropriately targeted for these smaller sets of users, to help them understand social engineering techniques and agree sensible protective measures.

The cloud-based [Security Policy Advisor](https://docs.microsoft.com/en-us/deployoffice/overview-of-security-policy-advisor) can help you identify groups that can have macros disabled with minimal impact, and optionally integrate with [Office 365 ATP](https://docs.microsoft.com/en-gb/microsoft-365/security/office-365-security/office-365-ti) to identify the top users of macros, and the top users who are targeted by documents with malicious macros. The service relies on telemetry sent to Microsoft from your devices. You will need to be comfortable with at least [required service data](https://docs.microsoft.com/en-gb/deployoffice/privacy/required-service-data) being collected by Microsoft and ensure that those data flows are enabled. If diagnostic telemetry is enabled, we recommend disabling the additional [optional diagnostic data](https://docs.microsoft.com/en-us/deployoffice/privacy/optional-diagnostic-data).

You should note that:

-   Recent versions of Microsoft Office have macros **enabled by default**, but rely on the user to click a button before any macros can run. It is relatively simple to trick the user into clicking this button, so you cannot rely on it as a mitigation.
-   **Macros on Windows** are configured per-application. If you use macros in some Office applications and not others, you should disable them in the applications where they are not used. For example, if your *organization* only uses macros in Excel, you can disable them in Word, PowerPoint, Visio, Access and Publisher. Note that OneNote does not support macros.
-   **Macros on macOS** are configured for the entire Office suite so you should aim to entirely disable them.

#### **Tip 2. Reduce your dependency on macros**

If you cannot turn off macros because you currently use them, you should work to reduce your dependency on them. You should *prioritize* replacing macros that are incompatible with the [attack surface reduction (ASR) rules](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction) listed below. Recent alternatives to office automation that can replace macros include:

-   using off-the-shelf [Office Add-ins](https://docs.microsoft.com/en-us/office/dev/add-ins/overview/office-add-ins) to add new functionality to Office applications
-   automating data flows using modern SaaS alternatives such as [Forms](https://support.office.com/en-gb/forms), [Flow](https://powerapps.microsoft.com/en-us/automate-processes/) and [PowerApps](https://powerapps.microsoft.com/en-us/)
-   building custom Web Applications that support business processes
-   building on off-the-shelf serverless cloud components

#### **Tip 3. Disable high-risk macro capabilities**

Exploit Guard [attack surface reduction (ASR) rules](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction) on Windows 10 can be configured to disable some of the abilities of malicious macros. Exploit Guard can be initially [run in audit mode](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/audit-windows-defender) to allow you to confirm that the macros that your *organization* uses will continue to work properly. ASR rules also affect the *behavior* of other Office features (such as Add-ins), so will require testing prior to broad deployment in organizations that rely on third party Office plugins.

Office on macOS uses the platform’s sandbox to limit the damage caused by a malicious document. We recommend [strengthening the default configuration of the Office sandbox](https://docs.microsoft.com/en-us/deployoffice/mac/deploy-preferences-for-office-for-mac) to further reduce the impact of running malicious macros.

#### **Tip 4. Use an antimalware product to detect malicious** ***behavior*** **in macros**

You can reduce the chance of a malicious macro reaching a user if you use an anti-malware product that includes behavioral analysis for macro-enabled Office documents. It could be a part of your email service, or a feature of the anti-malware software on the user’s device.

Organizations using an antivirus that uses [Microsoft’s AMSI interface](https://docs.microsoft.com/en-us/windows/win32/amsi/antimalware-scan-interface-portal) (as recommended in the *BCSF*'s [EUD Guidance for Windows 10](/silver-training/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management) )) can detect malicious macros even if the malicious intent is cleverly disguised. You should configure the feature to **scan all documents**, as the default is to only scan those that Office has identified as having come from the Internet.

![](/static-assets/images/guidance/malicious%20behavior.png)

We recommend that devices connected to the Internet are configured in line with the *BCSF*’s [End User Devices Security Guidance](/silver-training/end-user-device-guidance). While application allow listing is unlikely to prevent malicious macros themselves from running, a configuration such as the one suggested in the guidance for [Windows 10](/silver-training/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management)) and [macOS](/silver-training/platform-specific-macOS) is often effective in blocking malware that is downloaded/extracted from the macro.

#### **Tip 5. Disable macros unless they are in trusted files**

Organizations that have a code signing service can choose to configure Office on Windows to only allow digitally signed macros to run. This is lower risk than allowing an Office application to open any macro, as malicious macros are not usually signed by their authors.

Office on Windows can also be configured to only allow macros if the file is loaded from a trusted location, such as a specific folder, file share or website. Your *organization* will need to define that list of trusted locations. We recommend that macros are only permitted to run from a trusted location, such as a network share that only trusted administrators have write access to.

The antivirus integration described above does not apply to macros in trusted files by default, as many organizations rely on macros that exhibit similar behaviors to malware.

#### **Tip 6. Block macros from the Internet**

Office 2016 on Windows introduced the ability for an *organization* to [block macros in files received from the Internet](https://blogs.technet.microsoft.com/mmpc/2016/03/22/new-feature-in-office-2016-can-block-macros-and-help-prevent-infection/). This makes it more difficult to trick the user into bypassing the warning. Macros are blocked from the Internet by default on [Windows 10 in S mode](https://www.microsoft.com/en-gb/windows/s-mode). This feature is **not** available on macOS.

Note that it is usually **not** practical to block the file types that can contain macros as they can be found in commonly used legacy formats (such as .RTF .DOC and .DOT), as well as the newer formats that explicitly mark themselves as containing a macro (such as .DOCM and .DOTM).

---

## Configuration options for Windows devices managed by the cloud

Most of the mitigation options above can be configured using the [Office Cloud Policy Service](https://docs.microsoft.com/en-us/deployoffice/overview-office-cloud-policy-service) (OCPS) for users that have signed into their Office applications using their work identity. This includes devices that are joined to Azure Active Directory. Some settings apply to Windows rather than Office, and can be configured via MDM.

Some settings can be applied separately for each Office application that you have installed. Organizations using OCPS can apply Office settings to different groups of users, allowing macros to be enabled for a specific subset of the people in your *organization*.

The service implements a subset of the user-based policies that are available in group policy. Microsoft publishes [documentation explaining the group policy settings](https://technet.microsoft.com/en-us/library/ee857085%28v=office.16%29.aspx) available for Office 365 ProPlus, Office 2016, and Office 2019.

### **Configuration to disable the Office macro engine**

You can set a policy to disable macros across all Office applications:

| **OCPS policy** | **Application** | **Configuration** |
| --- | --- | --- |
| Disable VBA for Office applications | Office | True |

If you choose to leave macros enabled for some applications, you should set the policies to disable them for the other Office applications. You should also configure the recommended security mitigations in the following section (this is not necessary if you disable macros for all applications using the configuration below).

| **OCPS policy** | **Application** | **Configuration** |
| --- | --- | --- |
| For each of Access, Excel, PowerPoint, Publisher, Project, Visio and Word:<br><br>VBA Macro Notification Settings | \[Application name\] | Disable all without notification |
| Security settings for macros | Outlook | Never warn, disable all |

### **Configuration to only allow digitally signed macros**

You will need to set a group policy for each Office application that you want to configure. We suggest also configuring the recommended security mitigations in the following section, even if you only allow digitally signed macros across the Office suite.

| **OCPS policy** | **Application** | **Configuration** |
| --- | --- | --- |
| For each of Access, Excel, PowerPoint, Publisher, Project, Visio and Word:<br><br>VBA Macro Notification Settings | \[Application name\] | Disable all without notification |
| Security settings for macros | Outlook | Warn for signed, disable unsigned |

### **Configuration to enable recommended macro security mitigations**

These settings are recommended for all Office deployments that allow any use of macros.

| **OCPS policy** | **Application** | **Configuration** |
| --- | --- | --- |
| Macro runtime scan scope | Office | Enable for all documents |
| For each of Access, Excel, PowerPoint, Visio and Word:<br><br>Block macros from running in Office files that come from the Internet | \[Application Name\] | True |

| **MDM Device Configuration Profile** | **Configuration** |
| --- | --- |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction Attack Surface Reduction Office apps launching child processes | Block |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction Office apps/macros creating executable content | Block |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction Office apps injecting into other processes (no exceptions) | Block |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction Win32 imports from Office macro code | Block |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions) | Block |

### **Configuration to limit service data sent to Microsoft**

If your *organization* is using the Security Policy Advisor, you will need to configure Office to allow just the required service data to be collected:

| **OCPS policy** | **Application** | **Configuration** |
| --- | --- | --- |
| Allow the use of connected experiences in Office | Office | Enabled |

You can optionally also prevent diagnostic data from being sent to Microsoft:

| **OCPS policy** | **Application** | **Configuration** |
| --- | --- | --- |
| Configure the level of diagnostic data sent by Office to Microsoft | Office | Neither |

---

## Configuration options for Windows devices managed by Group Policy

Most of the mitigation options above can be configured using Group Policy across an enterprise, or Local Group Policy on an individual machine.

Some settings will need to be configured separately for each Office application that you have installed on devices. Enterprises using Active Directory can apply group policies to different Organizational Units, allowing macros to be enabled for a specific subset of the people in your *organization*.

-   Microsoft publishes [documentation explaining the group policy settings](https://technet.microsoft.com/en-us/library/ee857085%28v=office.16%29.aspx) available for Office 2016, Office 365 ProPlus and Office 2019.
-   Microsoft also publishes a [security baseline for Office 2016 and Office 365 ProPlus](https://blogs.technet.microsoft.com/secguide/2018/02/13/security-baseline-for-office-2016-and-office-365-proplus-apps-final/). Their baseline includes their recommended security settings for the whole of the Office suite on Windows, including some of the settings recommended by this guidance.
-   You may need to [install the Administrative Template Pack](https://www.microsoft.com/en-us/download/details.aspx?id=49030) for Office 365 ProPlus, Office 2019 and Office 2016 to be able to configure the Group Policies below.

### **Configuration to disable the Office macro engine**

You can set a policy to disable macros across all Office applications:

| **Group policy** | **Value** |
| --- | --- |
| User Configuration > Administrative Templates > Microsoft Office 2016 > \[*Application name*\] Settings > Security Disable VBA for Office applications | Enable |

If you choose to leave macros enabled for some applications, you should set the policies to disable them for the other Office applications. You should also configure the recommended security mitigations in the following section (this is not necessary if you disable macros for all Office applications):

| **Group policy** | **Value** |
| --- | --- |
| For each of Access, Excel, PowerPoint, Project, Visio and Word:<br><br>User Configuration > Administrative Templates > Microsoft \[*Application name*\] 2016 > \[*Application name*\] Settings > Security > Trust Center > VBA Macro Notification Settings | Enabled<br><br>Disable all without notifcation |
| For Access:<br><br>User Configuration > Administrative Templates > Microsoft Access 2016 > Application Settings > Security > Trust Center > VBA Macro Notification Settings | Enabled<br><br>Disable all without notifcation |
| For Outlook:<br><br>User Configuration > Administrative Templates > Microsoft Access 2016 > Security > Trust Center > Security settings for macros | Warn for signed, disable unsigned |
| For Publisher:<br><br>User Configuration > Administrative Templates > Microsoft Publisher 2016 > Security > Trust Center > VBA Macro Notification Settings | Enabled<br><br>Disable all without notification |

### **Configuration to only allow digitally signed macros**

You will need to set a group policy for each Office application that you want to configure. We suggest also configuring the recommended security mitigations in the following section, even if you only allow digitally signed macros across the Office suite.

| **Group policy** | **Value** |
| --- | --- |
| For each of Access, Excel, PowerPoint, Project, Visio and Word:<br><br>User Configuration > Administrative Templates > Microsoft \[*Application name*\] 2016 > \[*Application name*\] Settings > Security > Trust Center > VBA Macro Notification Settings | Enabled<br><br>Disable all except digitally signed macros |
| For Access:<br><br>User Configuration > Administrative Templates > Microsoft Access 2016 > Application Settings > Security > Trust Center > VBA Macro Notification Settings | Enabled<br><br>Disable all except digitally signed macros |
| For Outlook:<br><br>User Configuration > Administrative Templates > Microsoft Access 2016 > Security > Trust Center > Security settings for macros | Never warn, disable all |
| For Publisher:<br><br>User Configuration > Administrative Templates > Microsoft Publisher 2016 > Security > Trust Center > VBA Macro Notification Settings | Enabled<br><br>Disable all except digitally signed macros |

### **Configuration to enable recommended macro security mitigations**

These settings are recommended for all Office deployments that allow any use of macros.

| **Group policy** | **Value** |
| --- | --- |
| Compute Configuration > Windows components > Windows Defender Antivirus > Windows Defender Exploit Guard > Attack surface reduction > Configure Attack surface reduction rules | Enabled<br><br>D4F940AB-401B-4EFC-AADC-AD5F3C50688A = 1<br><br>3B576869-A4EC-4529-8536-B80A7769E899 = 1<br><br>75668C1F-73B5-4CF0-BB93-3ECF5CB7CC84 = 1<br><br>92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B = 1<br><br>BE9BA2D9-53EA-4CDC-84E5-9B1EEEE46550 = 1 |
| User Configuration > Administrative templates > Microsoft Office 2016 > Security Settings > Macro Runtime Scan Scope | Enable for all documents |
| For each of Excel, PowerPoint, Project, Visio and Word:<br><br>User Configuration > Administrative Templates > Microsoft \[*Application name*\] 2016 > \[*Application name*\] Settings > Security > Trust Center > Block macros from running in Office files from the Internet | Enabled |
| For Outlook:<br><br>User Configuration > Administrative Templates > Microsoft \[*Application name*\] 2016 > Security > Trust Center > Block macros from running in Office files from the Internet<br><br>User Configuration > Administrative Templates > Microsoft Publisher 2016 > Security > Trust Center > VBA Macro Notification Settings | Enabled |

### **Configuration to limit diagnostic data sent to Microsoft**

If your *organization* is using the Security Policy Advisor, you will need to configure Office to allow just the *required diagnostic data* to be collected:

| **Group policy** | **Value** |
| --- | --- |
| User Configuration > Administrative Templates > Microsoft Office 2016 > Privacy > Trust Center > Configure the level of diagnostic data sent by Office to Microsoft | Enabled<br><br>Required |

If not using the service, you can prevent diagnostic data from being collected entirely:

| **Group policy** | **Value** |
| --- | --- |
| User Configuration > Administrative Templates > Microsoft Office 2016 > Privacy > Trust Center > Configure the level of diagnostic data sent by Office to Microsoft | Enabled<br><br>Neither |

---

## Configuration options for macOS devices

The mitigation options available on macOS can be deployed using an MDM across an enterprise. The recommended settings are available on version 16.16 of Office for Mac or newer.

Microsoft publishes [documentation explaining preference settings](https://aka.ms/macvbsec) available for Office 2016 and Office 2019.

### **Configuration to disable the Office macro engine**

This setting will configure all Office applications that support macros; macros cannot be disabled per-application.

| **Domain** | **Key** | **Configuration** |
| --- | --- | --- |
| com.microsoft.office | VisualBasicMacroExecutionState | DisabledWithoutWarnings |

### **Configuration to enable recommended macro security mitigations** 

These settings are recommended for all Office deployments that allow any use of macros.

This setting will configure all Office applications that support macros; macros cannot be disabled per-application.

| **Domain** | **Key** | **Configuration** |
| --- | --- | --- |
| com.microsoft.office | AllowVisualBasicToBindToSystem | No  |
| com.microsoft.office | DisableVisualBasicExternalDylibs | Yes |
| com.microsoft.office | DisableVisualBasicToBindToPopen | Yes |
| com.microsoft.office | DisableVisualBasicMacScript | Yes |

---

## Comparison of Microsoft Office versions

Some of the security-enabling features described above are only available in newer versions of Microsoft Office. Some features may also rely on Office being installed on a recent version of Windows 10 or macOS.

-   we recommend that you use the most recent version of Microsoft Office, and that all patches are applied
-   we recommend that you use the most recent version of macOS or Windows 10, and that all patches are applied
-   where possible, we recommend using the [monthly channel of Office 365 ProPlus](https://docs.microsoft.com/en-us/deployoffice/overview-of-update-channels-for-office-365-proplus) in preference to Office 2019 or earlier
-   we **strongly recommend** that you do **not** use versions of Microsoft Office that are no longer supported, including Office 2003 and Office 2007

|     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- |
| **Versions** | **Default Macro** ***Behavior*** | **Disable Macros** | **Disable high risk capabilities** | **Macro execution scanned by AV** | **Block from the internet** | **Trusted files (signature or location)** |
| Office 365 on Windows 10 | Block until the user clicks the *Enable Macros* button.<br><br>Macros from untrusted locations will be scanned by compatible AV.<br><br>Macros from untrusted locations are entirely blocked when using Windows 10 in S Mode. | Per application | Yes | Yes | Yes | Yes |
| Office 365 on macOS | Block until the user clicks the *Enable Macros* button | For all applications | Yes | No  | No  | No  |
| Office 2019, 2016, 2013<br><br>Office 365 on earlier versions of Windows | Block until the user clicks the *Enable Macros* button | Per application | No  | No  | Yes | Yes |

\* this feature was added to Office 2013 by Microsoft Update

Macros are supported by Office for Mac and offer similar functionality to Office running on Windows. They use a slightly different language and are run inside Apple’s sandbox. Therefore, malicious macros that are targeted at Windows versions of Office are less likely to be dangerous in Office for Mac.

Macros are not supported by Office Mobile apps and the Office Online browser-based document editors.