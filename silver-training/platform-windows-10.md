---
title: Windows 10
description: Secure configuration for Windows 10
published: false
date: 2021-06-30T02:02:45.660Z
tags: silver, sourced, platform-specific, silver-training
editor: markdown
dateCreated: 2021-02-22T00:22:49.581Z
---

This guidance has been updated to cover the 1809 “October 2018 Update” of Windows 10 Enterprise. It builds on the previous 1803 “April 2018 Update” guidance.

Testing was performed on a [Windows Hardware Certified](http://msdn.microsoft.com/en-US/library/windows/hardware/dn423132.aspx) device, running Windows 10 Enterprise. The hardware was a Dell Latitude E7490, managed with Active Directory on Server 2019. This guidance is not applicable to Windows devices managed via an MDM or Windows To Go. We have separate guidance on how to configure devices with MDM. 

It's important to remember that this guidance has been conceived as a way to satisfy the [12 End User Device Security Principles](silver-training/end-user-device-guidance). As such, it consists of *recommendations* and should *not* be seen as a set of mandatory instructions requiring no further thought.

Risk owners and administrators should agree a configuration which balances business requirements, usability and security.

## Risk owners’ summary

We recommend the following architectural choices for Windows 10:

All data should be routed over a secure enterprise VPN to ensure the confidentiality and integrity of the traffic. This also allows the devices, and data on them, to be protected by [enterprise protective monitoring solutions](/bronze-controls/designing-controls/logging-for-security).

-   Installation of arbitrary third-party applications by users is not permitted on the device. Applications should be authorized by an administrator and deployed via a trusted mechanism.
-   Most users should have accounts with no administrative privileges. Users that require administrative privileges should use a separate unprivileged account for email and web browsing. Administrator accounts should have a unique strong password per device.

When configured in this way, risk owners should be aware of the following technical risks associated with this platform:

| **Associated security principle** | **Explanation of risks** |
| --- | --- |
| Secure boot | Windows 10 can support secure boot, but is dependent on supported and correctly configured hardware |

## Administrators’ deployment guide

### **Overview**

| **Security principle** | **Explanation** |
| --- | --- |
| **Assured data-in-transit protection** | Use the [Windows 10 Built-In VPN Client](https://docs.microsoft.com/en-gb/windows/security/identity-protection/vpn/vpn-connection-type?redirectedfrom=MSDN) configured as per customization guide.<br><br>Configure the built-in Windows firewall to block outbound connections when the VPN is not active. An example firewall profile is provided in the [Firewall configuration](/silver-training/end-user-device-guidance) section.<br><br>Use certificates for user or machine credentials. We recommend that [Windows Key Attestation](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/manage/component-updates/tpm-key-attestation) or [Windows Hello for Business](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/manage-identity-verification-using-microsoft-passport) should be used to bind these credentials to the device’s hardware.<br><br>Alternatively, use a third-party, correctly configured, CPA Foundation grade VPN app which makes use of the UWP ([Universal Windows Platform](https://docs.microsoft.com/en-gb/windows/uwp/get-started/universal-application-platform-guide)) VPN plug-in platform. |
| **Assured data-at-rest protection** | Use one of the following configurations to provide full volume encryption:<br><br>· BitLocker with a TPM and PIN configured in alignment with the BitLocker configuration settings.<br><br>· An independently assured CPA Foundation Grade, Data at Rest encryption product that supports UEFI and Windows Secure Boot, configured in alignment with the security procedures for that product.<br><br>If using BitLocker, deploy the configuration settings before encryption is started.<br><br>[Device Encryption](https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-bitlocker) introduced for Connected Standby devices in Windows 10 does not allow the use of a passphrase to unlock the disk and so does not support some of the mandatory requirements expected from assured disk encryption products. BitLocker, or an independently assured CPA Foundation Grade product, should be used instead. |
| **Authentication** | The user implicitly authenticates to the device by entering the [BitLocker PIN](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-countermeasures#pre-boot-authentication) at boot time.<br><br>The user then has a secondary credential to use when authenticating to the platform after boot and when unlocking the device. You should use Windows Hello for Business and allow the user to log in with a PIN code or Biometric. For both Windows Hello and traditional passwords, the credential derives a key which protects other credentials, which give access to corporate services.<br><br>In an enterprise environment, the user will also be issued with an Active Directory credential which will be required when they use a device for the first time. You should use [Credential Guard](https://docs.microsoft.com/en-us/windows/security/identity-protection/credential-guard/credential-guard) to best protect this credential. The user should also be a member of the [Protected Users Security Group](https://docs.microsoft.com/en-us/windows-server/security/credentials-protection-and-management/protected-users-security-group) on the domain and that domain should be running a minimum of 2016 Functional Domain Level.<br><br>Windows Hello for Business also permits [biometric unlock](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-biometrics-in-enterprise) of devices that have the necessary hardware. This can be used if desired.<br><br>Accounts with administrative privileges should only be present on End User Devices used to perform administrative functions and should take advantage of the [Restricted Admin](https://blogs.technet.microsoft.com/canitpro/2016/06/23/step-by-step-enabling-restricted-admin-mode-for-remote-desktop-connections/) feature of Remote Desktop Connections. User accounts with administrative privileges should have a strong password and ideally a second factor to authenticate them to the platform at logon and unlock time. The credentials will be best protected if the administrative user is a member of the Protected Users Security Group on the domain, and have [Authentication Policy Silos](https://docs.microsoft.com/en-us/windows-server/security/credentials-protection-and-management/authentication-policies-and-authentication-policy-silos) applied.<br><br>Microsoft provides guidance on the use of [administrative workstations](https://aka.ms/cyberpaw), [delegation of privilege](https://aka.ms/tiermodel) and other [good administrative practices](https://aka.ms/privsec). |
| **Secure boot** | On Windows 10, this requirement is met on a correctly configured platform deployed on the [Hardware Compatibility Program](https://docs.microsoft.com/en-us/windows-hardware/design/compatibility/whcp-specifications-policies).<br><br>A UEFI password can make it more difficult for an attacker to modify the boot process. With physical access, the boot process can still be compromised. |
| **Platform integrity and application sandboxing** | No configuration is required. |
| **Application whitelisting** | An enterprise configuration can be applied to implement application control using [AppLocker](https://docs.microsoft.com/en-gb/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview). A recommended sample configuration that only allows Administrator-installed applications to run is provided below.<br><br>Device Guard can also be used to reinforce application control rules. As it does not offer the same granularity as AppLocker, [the two technologies should be used alongside one another](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/windows-defender-device-guard-and-applocker).<br><br>[AppLocker](https://docs.microsoft.com/en-gb/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-policies-design-guide) can be used to restrict which pre-installed Windows Apps are available to users, and if the public Windows Store is enabled it can control which applications a user can install. |
| **Malicious code detection and prevention** | Windows 10 includes [Windows Defender Antivirus](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) and [Windows Defender SmartScreen](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview) that attempt to detect malicious code for the platform. Cloud sample submission can be disabled. Alternatively, third party anti-malware products are available. If using a third-party product, those that implement the [Anti-Malware Scan Interface (AMSI)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn889587(v=vs.85).aspx) should be preferred to improve compatibility with future Feature Updates.<br><br>The [Early Launch Anti-Malware (ELAM)](https://docs.microsoft.com/en-us/windows-hardware/drivers/install/early-launch-antimalware) driver provides signature checking for known bad drivers on ELAM-compliant systems that are configured to use Secure Boot.<br><br>Microsoft Store for Business, or a Company Store, can be used to distribute user-installable universal apps. Such stores should only contain vetted apps. If the public Microsoft Store is enabled, AppLocker can be used to control which applications a user is able to install. Content-based attacks can be filtered by scanning capabilities in the enterprise.<br><br>[Windows Defender Exploit Guard](https://docs.microsoft.com/en-us/configmgr/protect/deploy-use/create-deploy-exploit-guard-policy) can be used to help prevent vulnerabilities in older software from being successfully exploited. |
| **Security policy enforcement** | Settings applied through Group Policy cannot be modified by unprivileged users. |
| **External interface protection** | Interfaces can be configured using group policy. USB removable media can be blocked through Group Policy if required. Direct Memory Access (DMA) is possible from peripherals connected to some external interfaces including FireWire and Thunderbolt unless disabled through group policy as detailed below, or in the UEFI/BIOS. With *Windows 10 Connected Standby* devices, part of the hardware compliance mitigates DMA attacks by disallowing these interfaces. |
| **Device updates** | Windows Update can automatically download and install updates. If the Microsoft Store is enabled, it should be configured to automatically update Microsoft Store apps.<br><br>Some devices will allow the UEFI firmware to be updated automatically via Windows Update. Devices that do not implement this will require updates via another mechanism whenever a new firmware is released.<br><br>[Windows Update for Business](http://blogs.windows.com/windowsexperience/2015/05/04/announcing-windows-update-for-business/) or [Windows Server Update Services (WSUS)](https://docs.microsoft.com/en-us/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) can, optionally, be used to monitor and enforce updates of the core platform, system firmware and any Windows applications. |
| **Event collection** | Event collection can be carried out using Windows Event Forwarding for central event log collection. |
| **Incident response** | The combination of BitLocker drive encryption and enterprise revocation of user credentials are appropriate for managing this security recommendation. |

## Recommended network architecture

For all remote or mobile working scenarios, you should consider using a typical remote access architecture based on the Walled Garden Architectural Pattern. The following network diagram describes the recommended architecture for this platform. The remote device will need Active Directory access in order to authenticate and retrieve group policy.

Alternatively, consider a reduced presentation layer that allows direct access from the VPN gateway to internal services via the internal firewall. The inner firewall should be used to restrict access where possible.

The risk of allowing more direct access to the core network can be reduced by binding the authentication certificate to the end user device, ensuring that it is only possible for legitimate devices to connect.

## Preparation for deployment

The steps below should be followed to prepare your organizational infrastructure to host a deployment of these devices:

1.  Procure, deploy and configure network components, including an approved IPsec VPN Gateway.
2.  Configure the [Microsoft Deployment Toolkit](https://technet.microsoft.com/en-us/windows/dn475741.aspx) to deploy your organization's standard desktop build, using a clean Windows 10 Enterprise image. Consider including credential management tools such as [LAPS](https://technet.microsoft.com/en-us/mt227395.aspx) and [MBAM](https://technet.microsoft.com/en-us/windows/hh826072.aspx).
3.  Create Group Policies for user and computer groups in accordance with the settings later in this section, ensuring that the Microsoft Baseline settings have the lowest precedence when being deployed.
4.  Deploy an AppLocker rule set using Group Policy following guidance in the [Application Whitelisting section](/collection/end-user-device-security/platform-specific-guidance/eud-security-guidance-windows-10-1809#whitelist). A sample configuration, which allows only applications installed by an Administrator to run, is outlined in the Group Policy settings
5.  Create Event Forwarding Subscriptions and configure Group Policy to forward at least AppLocker, Application, System and Security logs that have a level of Critical Error or Warning, to an event management system. 
6.  Configure user groups according to the principle of least privilege. Where available, configure these users to be in the Protected Users group and apply Restricted Admin and Authentication Policy Silos to privileged users.
7.  Deploy [System Center Configuration Manager (SCCM](https://docs.microsoft.com/en-us/sccm/index)) or additional OEM-dependent infrastructure if you wish to implement remote management of device firmware.

### **Device provisioning steps**

The steps below should be followed to provision each end user device onto your organization’s network, preparing it for distribution to end users:

1.  Update the system firmware to the latest version available from the vendor. This may be called a UEFI or BIOS update.
2.  Configure the system firmware to boot in UEFI mode
3.  Enable TPM, Secure Boot and virtualization extensions
4.  Disable unused hardware interfaces
5.  Check the boot order to prioritize internal storage and set a password to prevent changes. Most of these settings will be pre-configured on a Windows Hardware Compatibility Program device.
6.  [Install a clean version of Windows](https://www.microsoft.com/en-gb/software-download/windows10) from a known good source.

### **Recommended policies and settings**

This section details important security policy settings which are recommended for a Windows 10 deployment. Other settings (e.g. server address) should be chosen according to the relevant network configuration.

Remember, any guidance points given here are recommendations - they are not mandatory. Risk owners and administrators should agree a configuration which balances business requirements, usability and the security of the platform. 

Settings not listed in this section are either not applicable to this mode or should be chosen according to your organizational policy and requirements.

### **Microsoft baselines**

The configuration below builds on the enterprise baselines distributed by Microsoft. [Microsoft Security Compliance Toolkit 1.0](https://www.microsoft.com/en-us/download/details.aspx?id=55319) can be used to help assess the differences between security configurations. The configuration below has been tested to work with the Windows 10 version 1809 baselines.

You should use the following Microsoft baseline GPO settings:

-   MSFT Windows 10 and Server 2019 Member Server - Credential Guard
-   MSFT Windows 10 and Server 2019 – Defender Antivirus
-   MSFT Windows 10 and Server 2019 – Domain Security
-   MSFT Windows 10 1809 - BitLocker
-   MSFT Windows 10 1809 - Computer
-   MSFT Windows 10 1809 - User

## User account hardening

| **Group Policy** | **Value(s)** |
| --- | --- |
| Computer Configuration > Administrative Templates > Network > Network Connections > Require domain users to elevate when setting a network’s location | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Credential User Interface > Do not display the password reveal button | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > OneDrive > Prevent the usage of OneDrive for file storage | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Sync your settings > Do not sync | Enabled<br><br>Allow users to turn syncing on: Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Search > Allow Cortana | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Search > Don’t search the web or display web results in Search | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Store > Disable all apps from Microsoft Store | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Store > Turn off Automatic Download and Install of updates | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Store > Turn off the Store application | Enabled |
| User Configuration > Administrative Templates > Control Panel > Personalization > Screen saver timeout | 600 seconds |
| Computer Configuration > Administrative Templates > System > Logon > Turn off picture password sign-in | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Hello for Business > Use a hardware security device | Enabled |

### **Authentication policy**

Your organization should have a consistent authentication policy which applies to all users and devices capable of accessing its data. You can use our published [password guidance](/collection/passwords?curPage=/collection/passwords/updating-your-approach) to help inform any password policy.

An administrator should configure the relevant on-device settings in line with your authentication policy.

Windows 10 Enterprise implements a number of relevant settings as Fine Grained Password Policies that should be configured on the Domain Controller.

| **Group Policy** | **Value(s)** |
| --- | --- |
| CN=System > CN=Password Settings Container > CN=Granular Password Settings Users | Precedence: 2<br><br>Enforce minimum password length<br><br>Enforce lockout policy<br><br>Account will be locked out: Until an administrator manually unlocks the account<br><br>Directly Applies To: Domain Users |
| CN=System > CN=Password Settings Container > CN=Granular Password Settings Administrators | Precedence: 1<br><br>Enforce minimum password length<br><br>Password must meet complexity requirements<br><br>Enforce lockout policy<br><br>Account will be locked out: Until an administrator manually unlocks the account<br><br>Directly Applies To: Domain Admins<br><br>Protect from accidental deletion: Enabled |

### **Active Directory**

A user’s Active Directory password will normally only be used when enrollling against a device for the first time. It is not backed by a second factor or by hardware-backed [anti-hammer](https://docs.microsoft.com/en-us/windows/security/hardware-protection/tpm/tpm-fundamentals#anti-hammering), even when Credential Guard is deployed.

Different requirements can be set for different account types using [Fine Grained Password Policies](https://technet.microsoft.com/en-us/library/cc770394(v=ws.10).aspx). If the Active Directory password is only used for device enrollment, it needs to be easy to type in but does not need to be memorable.

### **Windows Hello and Hardware Strengthening**

We recommend that users should log in to and unlock devices using Windows Hello for Business instead of a Windows password. This creates a user credential that is tied to the physical device using a PIN or biometric. When used on Windows 10 Certified devices, it provides hardware-backed anti-hammer. Windows Hello should only be enabled on devices that use a TPM. Detailed guidance on Hello for Business deployment can be found in the [Microsoft Hello for Business deployment guide](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-deployment-guide).

Users can choose to set a PIN after they have logged on to the device for the first time. A number of group policies should be used to configure the PIN requirement.

|     |
| --- |
| **Group Policy > Computer Configuration > Administrative Templates > System > PIN Complexity** |
| PIN Complexity > Maximum PIN length |
| PIN Complexity > Minimum PIN length |
| PIN Complexity > Require digits |
| PIN Complexity > Require lowercase letters |
| PIN Complexity > Require special characters |
| PIN Complexity > Require uppercase characters |

The configuration provided in this guidance enables [Virtual Secure Mode and Credential Guard](https://blogs.technet.microsoft.com/ash/2016/03/02/windows-10-device-guard-and-credential-guard-demystified/) on supported devices. Biometrics can be used if these features are installed and enabled. Biometrics are enabled by default on Windows 10, so group policy should be used to disable biometrics if they are not being used. For more information see Microsoft’s paper on [credential guard](https://technet.microsoft.com/en-gb/itpro/windows/keep-secure/credential-guard).

## System hardening

|     |     |
| --- | --- |
| **Group Policy** | **Value(s)** |
| Computer Configuration > Administrative Templates > Windows Components > Data Collection and Preview Builds > Allow Telemetry | Enabled:<br><br>0 - Security<br><br>Note - If using Windows Update for Business this will need to be set to 1 (Basic).<br><br>See [Windows 10 feature updates](/collection/end-user-device-security/platform-specific-guidance/eud-security-guidance-windows-10-1809#enterpriseconsiderations) for more details. |
| Computer Configuration > Administrative Templates > Windows Components > Windows Error Reporting > Disable Windows Error Reporting | Enabled |
| Computer Configuration > Administrative Templates > System > Device Installation > Device Installation Restrictions > Prevent installation of devices that match these device IDs<br><br>*This policy prevents all Thunderbolt devices from being used and provides the strongest protection from DMA attacks. If organizations require the use of Thunderbolt devices, they should first check if the host supports* [*Kernel DMA protection*](https://docs.microsoft.com/en-us/windows/security/information-protection/kernel-dma-protection-for-thunderbolt) *and has it enabled. If it is not supported, follow the* [*Microsoft guidance*](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-countermeasures) *to* [*disable new DMA devices when the computer is locked*](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings#disable-new-dma-devices-when-this-computer-is-locked). | Enabled: PCI\\CC\_0C0A<br><br>Also apply to matching devices that are already installed: Disabled |
| Computer Configuration > Administrative Templates > System > Device Installation > Device Installation Restrictions > Prevent installation of drivers matching these device setup classes | Enabled:<br><br>{d48179be-ec20-11d1-b6b8-00c04fa372a7}<br><br>{7ebefbc0-3200-11d2-b4c2-00a0C9697d07}<br><br>{c06ff265-ae09-48f0-812c-16753d7cba83}<br><br>{6bdd1fc1-810f-11d0-bec7-08002be2092f}<br><br>Also apply to matching devices that are already installed: Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Store > Turn off Automatic Download and Install of updates | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > App runtime > Block launching Universal Windows apps with Windows Runtime API access from hosted content. | Enabled |
| Computer Configuration > Administrative Templates > Network > Network Isolation > Proxy definitions are authoritative | Enabled |
| Computer Configuration > Administrative Templates > Network > Network Isolation > Subnet definitions are authoritative | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Portable Operating System > Windows To Go Default Startup Options | Disabled |
| Computer Configuration > Preferences > Windows Settings > Registry > Replace > HKLM\\Software\\Microsoft\\Windows\\CurrentVersion\\policies\\system\\ | (DWORD) SafeModeBlockNonAdmins = 1 |
| Computer Configuration > Preferences > Windows Settings > Registry > Replace > HKLM\\System\\CurrentControlSet\\Control\\SafeBoot\\Network | (REG\_SZ)<br><br>Appid = Service |
| Computer Configuration > Preferences > Windows Settings > Registry > Replace > HKLM\\System\\CurrentControlSet\\Control\\SafeBoot\\Network | (REG\_SZ)<br><br>Appid.sys = Driver |
| Computer Configuration > Preferences > Windows Settings > Registry > Replace > HKLM\\System\\CurrentControlSet\\Control\\SafeBoot\\Network | (REG\_SZ)<br><br>discache.sys = Driver |
| Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options > Accounts: Block Microsoft accounts | Users can't add or log on with Microsoft accounts |
| Computer Configuration > Policies > Windows Settings > Security Settings > Public Key Policies > Certificate Path Validation Settings > Stores > Allow user trusted root Certificate Authorities (CAs) to be used to validate certificates | Disabled |
| Computer Configuration > Policies > Windows Settings > Security Settings > Public Key Policies > Certificate Path Validation Settings > Stores > Allow users to trust peer trust certificates | Disabled |
| Computer Configuration > Policies > Windows Settings > Security Settings > Public Key Policies > Certificate Path Validation Settings > Stores > Root CAs that client computers can trust | Third-Party Root Certification Authorities and Enterprise Root Certification Authorities |
| Computer Configuration > Policies > Windows Settings > Security Settings > Public Key Policies > Certificate Path Validation Settings > Stores | CAs must also be compliant with user principal name (UPN) constraints = Disabled |
| Computer Configuration > Administrative Templates >Network > Network Connections > Require domain users to elevate when setting a network's location | Enabled |
| Computer Configuration > Administrative Templates > System > Group Policy > Phone-PC linking on this device | Disabled |
| Computer Configuration > Administrative Templates > System > OS Policies > Allow upload of User Activities | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Microsoft Edge > Allow a shared Books folder | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Microsoft Edge > Allow configuration updates for the Books Library | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Microsoft Edge > Allow extended telemetry for the Books tab | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > Turn off Windows Defender Antivirus | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Logon Options > Sign-in last interactive user automatically after a system-initiated restart | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > BitLocker Drive Encryption > Disable new DMA devices when this computer is locked | Enabled |
| Computer Configuration > Administrative Templates > System > Group Policy > Continue experiences on this device | Disabled |
| Computer Configuration > Administrative Templates > System > Kernel DMA Protection > Enumeration policy for external devices incompatible with Kernel DMA Protection | Enabled:<br><br>Enumeration policy: Block all |
| Computer Configuration > Administrative Templates > System > OS Policies > Allow Clipboard History | Disabled |
| Computer Configuration > Administrative Templates > System > OS Policies > Allow Clipboard synchronization across devices | Disabled |
| Computer Configuration > Administrative Templates > System > OS Policies > Allow publishing of User Activities | Disabled |
| Computer Configuration > Administrative Templates > System > OS Policies > Enabled Activity Feed | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Data Collection and Preview Builds > Configure collection of browsing data for Microsoft 365 Analytics | Enabled<br><br>Configure telemetry collection: Do not allow sending intranet or internet history |
| Computer Configuration > Administrative Templates > Windows Components > Data Collection and Preview Builds > Disable diagnostic data viewer. | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Microsoft Edge > Allow Microsoft Edge to start and load the Start and New Tab page at Windows startup and each time Microsoft Edge is closed | Enabled<br><br>Configure tab preloading: Prevent tab preloading |
| Computer Configuration > Administrative Templates > Windows Components > Microsoft Edge > Allow Sideloading of extensions | Disabled |

Group Policy can be used to limit user access to removable media such as USB mass storage devices, if required by organizational policy. The settings can be found in Computer Configuration > Administrative Templates > System > Removable Storage Access.

Group Policy can also be used to fully allow list all devices or device classes which are allowed to be installed. In this way you could allow, for example, basic peripherals such as mice, keyboards, monitors and network cards, but refuse the connection and installation of other devices. It is important to allow list enough classes of device to allow a successful boot on a variety of hardware.

Details on how to enable allow listing of specific devices can be found on [MSDN](http://msdn.microsoft.com/en-us/library/bb530324.aspx).

### **Windows Defender configuration**

If using Windows Defender, configure it to enable [cloud-backed protections](https://technet.microsoft.com/en-gb/itpro/windows/keep-secure/windows-defender-block-at-first-sight) while limiting its ability to send sensitive data for analysis.

|     |     |
| --- | --- |
| **Group Policy** | **Value(s)** |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > MAPS > Configure the ‘Block at First Sight’ feature | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > MAPS > Join Microsoft MAPS | Enabled: Advanced |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > MAPS > Send file samples when further analysis is required | Enabled: Send safe samples automatically |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > Real-time Protection > Turn off real-time protection | Disabled |

### **AppLocker configuration**

This example set of AppLocker rules implements the application allow listing principles outlined in Enterprise Considerations below. It can be modified to allow the user to install and run apps from either an enterprise software center or the Microsoft Store.

Scripting languages such as Visual Basic Scripting should be disabled unless they are specifically needed.

|     |     |
| --- | --- |
| **Group Policy** | **Value(s)** |
| Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker > Enforcement > Executable Rules | Configured: True Enforce Rules |
| Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker > Executable Rules | Allow Everyone: All files located in the [Windows Defender\\Platform](https://support.microsoft.com/en-us/help/4052623/update-for-windows-defender-antimalware-platform) folder -<br><br>%OSDrive%\\ProgramData\\Microsoft\\Windows Defender\\Platform\\\*<br><br>Allow Everyone: All files located in the Program Files folder - with exceptions<br><br>Exception: (Path) %PROGRAMFILES%\\Windows Kits\\\*\\Debuggers\\\*<br><br>Allow Everyone: All files located in the Windows folder - with exceptions<br><br>Exception: (Path) %SYSTEM32%\\com\\dmp\\\*<br><br>Exception: (Path) %SYSTEM32%\\FxsTmp\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\drivers\\color\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\PRINTERS\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\SERVERS\\\*<br><br>Exception: (Path) %SYSTEM32%\\Tasks\\\*<br><br>Exception: (Path) %SYSTEM32%\\microsoft\\crypto\\rsa\\machinekeys\\\*<br><br>Exception: (Path) %WINDIR%\\tasks\\\*<br><br>Exception: (Path) %WINDIR%\\temp\\\*<br><br>Exception: (Path) %WINDIR%\\tracing\\\*<br><br>Exception: (Path) %WINDIR%\\registration\\crmlog\\\*<br><br>Exception: (Path) %WINDIR%\\servicing\\packages\\\*<br><br>Exception: (Path) %WINDIR%\\servicing\\sessions\\\*<br><br>Exception: (Publisher) %SYSTEM32%\\WMIC.exe,\*<br><br>Exception: (Publisher) %SYSTEM32%\\cmstp.exe,\*<br><br>Exception: (Publisher) %SYSTEM32%\\mshta.exe,\*<br><br>Exception: (Publisher) %SYSTEM32%\\PresentationHost.exe,\*<br><br>Exception: (Publisher) %SYSTEM32%\\windbg.exe,\*<br><br>Exception: (Publisher) %SYSTEM32%\\cipher.exe,\*<br><br>Exception: (Publisher) %Microsoft.NET%\\Framework64\\\*\\IEExec.exe<br><br>Exception: (Publisher) %Microsoft.NET%\\Framework64\\\*\\InstallUtil.exe<br><br>Exception: (Publisher) %Microsoft.NET%\\Framework\\\*\\regsvcs.exe<br><br>Exception: (Publisher) %Microsoft.NET%\\Framework\\\*\\msbuild.exe<br><br>Exception: (Publisher) %Microsoft.NET%\\Framework\\\*\\regasm.exe<br><br>Allow Administrators: All files |
| Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker > Enforcement > Windows Installer Rules | Configured: True Enforce Rules |
| Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker > Windows Installer Rules | Allow Administrators: All Windows Installer files<br><br>Allow Everyone: (PATH) %WINDIR%\\Installer\\\* |
| Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker > Enforcement > Script Rules | Configured: True Enforce Rules |
| Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker > Script Rules > Enforce rules of this type | Allow Everyone: All Scripts located in the Program Files folder<br><br> Allow Everyone: All Scripts located in the Windows folder - with exceptions<br><br>Exception: (PATH) %SYSTEM32%\\com\\dmp\\\*<br><br>Exception: (PATH) %SYSTEM32%\\FxsTmp\\\*<br><br>Exception: (PATH) %SYSTEM32%\\Spool\\drivers\\color\\\*<br><br>Exception: (PATH) %SYSTEM32%\\Spool\\PRINTERS\\\*<br><br>Exception: (PATH) %SYSTEM32%\\Spool\\SERVERS\\\*<br><br>Exception: (PATH) %SYSTEM32%\\Tasks\\\*<br><br>Exception: (PATH) %WINDIR%\\registration\\crmlog\\\*<br><br>Exception: (PATH) %WINDIR%\\tasks\\\*<br><br>Exception: (PATH) %WINDIR%\\temp\\\*<br><br>Exception: (PATH) %WINDIR%\\tracing\\\*<br><br>Exception: (PATH) %WINDIR%\\servicing\\packages\\\*<br><br>Exception: (PATH) %WINDIR%\\servicing\\sessions\\\*<br><br>Exception: (PATH) %SYSTEM32%\\microsoft\\crypto\\rsa\\machinekeys\\\*<br><br>Allow Administrators: All scripts |
| Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker > Enforcement > DLL Rules | Configured: True Enforce Rules |
| Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker > DLL Rules | Allow Everyone: All DLLs located in the [Windows Defender\\Platform](https://support.microsoft.com/en-us/help/4052623/update-for-windows-defender-antimalware-platform) folder -<br><br>%OSDrive%\\ProgramData\\Microsoft\\Windows Defender\\Platform\\\*<br><br>Allow Everyone: All DLLs located in the Program Files folder<br><br>Allow Everyone: All DLLs located in the Windows folder - with exceptions<br><br>Exception: (PATH) %SYSTEM32%\\com\\dmp\\\*<br><br>Exception: (PATH) %SYSTEM32%\\FxsTmp\\\*<br><br>Exception: (PATH) %SYSTEM32%\\Spool\\drivers\\color\\\*<br><br>Exception: (PATH) %SYSTEM32%\\Spool\\PRINTERS\\\*<br><br>Exception: (PATH) %SYSTEM32%\\Spool\\SERVERS\\\*<br><br>Exception: (PATH) %SYSTEM32%\\Tasks\\\*<br><br>Exception: (PATH) %SYSTEM32%\\microsoft\\crypto\\rsa\\machinekeys\\\*<br><br>Exception: (PATH) %WINDIR%\\registration\\crmlog\\\*<br><br>Exception: (PATH) %WINDIR%\\tasks\\\*<br><br>Exception: (PATH) %WINDIR%\\temp\\\*<br><br>Exception: (PATH) %WINDIR%\\tracing\\\*<br><br>Exception: (PATH) %WINDIR%\\servicing\\packages\\\*<br><br>Exception: (PATH) %WINDIR%\\servicing\\sessions\\\*<br><br>Allow Administrators: All DLLs |
| Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker > Enforcement > Packaged app Rules | Configured: True Enforce Rules |
| Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker > Packaged app rules | Allow Everyone: All signed packaged apps<br><br>Exception: (Publisher) Microsoft.Getstarted<br><br>Exception: (Publisher) Microsoft.MicrosoftOfficeHub<br><br>Exception: (Publisher) Microsoft.SkypeApp<br><br>Exception: (Publisher) Microsoft.WindowsFeedback |

### **BitLocker configuration**

The following settings should be configured to use full volume encryption in TPM and PIN mode.

|     |     |
| --- | --- |
| **Group Policy** | **Value(s)** |
| Computer Configuration > Administrative Templates > Windows Components > BitLocker Drive Encryption > Operating System Drives > Enforce drive encryption type on operating system drives | Enabled<br><br>Select the encryption type: Full encryption |
| Computer Configuration > Administrative Templates > Windows Components > BitLocker Drive Encryption > Operating System Drives > Configure use of hardware-based encryption for operating system drives | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > BitLocker Drive Encryption > Operating System Drives > Require additional authentication at startup | Enabled<br><br>Allow BitLocker without a compatible TPM (Requires a password or startup key on a USB flash drive): Unticked<br><br>Configure TPM startup: Do not allow TPM<br><br>Configure TPM startup PIN: Allow startup PIN with TPM<br><br>Configure TPM startup key: Do not allow startup key with TPM<br><br>Configure TPM startup key and PIN: Allow startup key and PIN with TPM |

The BitLocker PIN should be in line with your organization’s password policy. Deployments that include fixed-location workstations may prefer to use [BitLocker Network Unlock](https://technet.microsoft.com/en-us/library/jj574173.aspx) as an alternative to a PIN.

Users can change the PIN after they have logged on to the device for the first time. A number of group policies can be used to configure the PIN requirements including:

|     |
| --- |
| **Group Policy > Computer Configuration > Administrative Templates > Windows Components > Operating System Drives** |
| Allow enhanced PINs for startup |
| Configure minimum PIN length for startup |
| Configure use of passwords for operating system drives |

### **Windows Defender Exploit Guard configuration**

The majority of Exploit Guard configuration is performed using an XML file, the location of which is specified through Group Policy. The XML file can be generated using the [Windows Defender Security Center application](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml#create-and-export-a-configuration-file), or [exported from EMET](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml#convert-an-emet-configuration-file-to-an-exploit-protection-configuration-file).

As Exploit Guard can cause compatibility issues with some applications, Microsoft recommends that Exploit Guard policies are thoroughly tested before they are enforced across an organization. "Audit mode" can be used to support this.

|     |     |
| --- | --- |
| **Group Policy** | **Value(s)** |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > Windows Defender Exploit Guard > Controlled folder access | Enabled<br><br>Mode: Block |
| Computer Configuration > Administrative Templates > Windows Components > Window Defender Exploit Guard> Use a common set of exploit protection settings | Enabled.<br><br>A *UNC path to an XML file containing any desired settings should be configure*d. |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > Windows Defender Exploit Guard > Attack Surface Reduction > Configure Attack Surface Reduction rules<br><br>*Details on these policies can be found at* [*https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard*](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) | d4f940ab-401b-4efc-aadc-ad5f3c50688a: 1<br><br>9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2: 1<br><br>3b576869-a4ec-4529-8536-b80a7769e899: 1<br><br>5beb7efe-fd9a-4556-801d-275e5ffc04cc: 1<br><br>92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B: 1<br><br>b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4: 1<br><br>75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84: 1<br><br>d3e037e1-3eb8-44c8-a917-57927947596d: 1<br><br>be9ba2d9-53ea-4cdc-84e5-9b1eeee46550: 1<br><br>26190899-1602-49e8-8b27-eb1d0a1ce869: 1<br><br>7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c: 1<br><br>d1e49aac-8f56-4280-b9ba-993a6d77406c: 2 |

If files stored outside of user and system directories should be protected with Controlled Folder access, these should be added to Exploit Guard with [Group Policy](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/customize-controlled-folders-exploit-guard). A table of the various attack surface reduction rules, and what restrictions they impose, can be found [here](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/enable-attack-surface-reduction).

### **Windows Defender Device Guard and Application Control configuration**

[Windows Defender Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control#how-windows-defender-device-guard-features-help-protect-against-threats) includes [Windows Defender Application Control](https://docs.microsoft.com/en-gb/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) (WDAC), which allows administrators to permit only digitally signed applications to run on user devices. Where unsigned line of business applications are also used, administrators can permit these using a signed catalog file containing details of the trusted unsigned applications. It should however be noted that Windows Defender Device Guard rules will apply to all users, so it is not possible to allow administrators to run some applications that users cannot. Consequently, [Microsoft recommends that administrators deploy WDAC alongside AppLocker policies](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control#windows-defender-device-guard-with-applocker).

Organizations should create their own WDAC policies using gold builds of each device type, [and thoroughly test them prior to deployment](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/device-guard-deployment-guide). Guidance on how to achieve this can be found on the [Microsoft website](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/steps-to-deploy-windows-defender-application-control). The rules should include the exclusion list given by Microsoft in their WDAC guidance.

Organizations should also enable Virtualization Based Security to guard against malicious software being loaded into the Windows kernel. This can be achieved with the following Group Policy settings:

|     |     |
| --- | --- |
| **Group Policy** | **Value(s)** |
| Computer Configuration > Administrative Templates > System > Device Guard > Turn On Virtualization Based Security | Enabled:<br><br>Platform Security: Secure Boot and DMA Protection<br><br>Virtualization Based Protection of Code Integrity: Enabled with UEFI Lock<br><br>Require UEFI Memory Attributes Table: Enabled\*<br><br>Credential Guard Configuration:  Enabled with UEFI Lock<br><br>Secure Launch Configuration: Enabled |

\*Please note - setting this value to Enabled will require UEFI 2.6+. See [this page from Microsoft](https://docs.microsoft.com/en-us/windows/security/identity-protection/credential-guard/credential-guard-requirements#2017-additional-security-qualifications-starting-with-windows-10-version-1703) for more details. Microsoft have also [provided tools to check whether](https://www.microsoft.com/en-us/download/details.aspx?id=53337) devices are ready for deploying Device Guard and Credential Guard. 

### **Windows Defender Application Guard configuration**

[Windows Defender Application Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-guard/wd-app-guard-overview) uses Microsoft's Hyper-V virtualization technology to load untrusted websites.

We recommend that this is configured in Enterprise Mode, with the following Group Policy settings:

|     |     |
| --- | --- |
| **Group Policy** | **Value(s)** |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Turn on Windows Defender Application Guard in Enterprise Mode | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Allow data persistence for Windows Defender Application Guard | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Allow auditing events in Windows Defender Application Guard | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Prevent enterprise websites from loading non-enterprise content | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Configure Windows Defender Application Guard clipboard settings | Enabled:<br><br>Enable clipboard operation from an isolated session to the host. Clipboard content options: 3 (Allow text and image copying) |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Configure Windows Defender Application Guard print settings | Enabled:<br><br>Allowed Print types in Application Guard: 11 (Allow network, PDF and XPS printing) |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Allow files to download and save to the host operating system from Windows Defender Application Guard | Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Configure additional sources for untrusted files in Windows Defender Application Guard | Enabled:<br><br>Removable media: Enabled<br><br>Network shares: Enabled<br><br>Files with Mark of the Web: Enabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Allow Windows Defender Application Guard to use Root Certificate Authorities from the user’s device | Disabled |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Allow users to trust files that open in Windows Defender Application Guard | Enabled:<br><br>0\. Do not allow users to manually trust files |
| Computer Configuration > Administrative Templates > Windows Components > Windows Defender Application Guard > Allow camera and microphone access in Windows Defender Application Guard | Disabled |
| Computer Configuration  > Administrative Templates > Network > Network Isolation > Enterprise resource domains hosted in the cloud | Enabled: |
| Computer Configuration  > Administrative Templates > Network > Network Isolation > Private network ranges for apps | Enabled:<br><br>Any IP address ranges that are used for internal applications. These can be specified in CIDR notation. |

### **Windows Defender Firewall configuration**

This firewall configuration is used to enforce the use of an always-on VPN.

You may also need to add rules to allow your VPN client to make outbound connections when the device is in either a public or private profile. Sample rules are provided with the BCSF configuration guide.

If you need to add firewall exceptions to allow for remote management, they should only be applied to the Domain profile.

|     |     |
| --- | --- |
| **Group Policy** | **Value(s)** |
| Computer Configuration > Windows Settings > Security Settings > Windows Firewall with Advanced Security > Windows Firewall Properties > Domain Profile | Firewall State : On (Recommended)<br><br>Inbound connections : Block (default)<br><br>Outbound connections : Allow (default) |
| Computer Configuration > Windows Settings > Security Settings > Windows Firewall with Advanced Security > Windows Firewall Properties > Domain Profile > Settings > Customize > Apply local firewall rules | No  |
| Computer Configuration > Windows Settings > Security Settings > Windows Firewall with Advanced Security > Windows Firewall Properties > Private Profile | Firewall State : On (Recommended)<br><br>Inbound connections : Block (default)<br><br>Outbound connections : Block |
| Computer Configuration > Windows Settings > Security Settings > Windows Firewall with Advanced Security > Windows Firewall Properties > Private Profile > Settings > Customize > Apply local firewall rules | No  |
| Computer Configuration > Windows Settings > Security Settings > Windows Firewall with Advanced Security > Windows Firewall Properties > Public Profile | Firewall State : On (Recommended)<br><br>Inbound connections : Block (default)<br><br>Outbound connections : Block |
| Computer Configuration > Windows Settings > Security Settings > Windows Firewall with Advanced Security > Windows Firewall Properties > Public Profile > Settings > Customize > Apply local firewall rules | No  |
| Computer Configuration > Windows Settings > Security Settings > Windows Firewall with Advanced Security > Outbound Rules | Enabled<br><br>Allow outbound DHCP<br><br>General > Action: Allow the connection<br><br>Programs and Services > Programs > This Program > %SystemRoot%\\system32\\svchost.exe<br><br>Allow Programs and Services > Service > Apply to this service > DHCP Client (Dhcp)<br><br>Advanced > Profiles: Private, Public<br><br>Protocols and Ports > Local port: UDP 68<br><br>Protocols and Ports > Remote port: UDP 67<br><br>Allow outbound DNS<br><br>General > Action: Allow the connection<br><br>Programs and Services > Programs > This Program > %SystemRoot%\\system32\\svchost.exe<br><br>Allow Programs and Services > Service > Apply to this service > DNS Client (Dnscache)<br><br>Advanced > Profiles: Private, Public<br><br>Protocols and Ports > Remote port: TCP 53, UDP 53<br><br>Allow outbound Kerberos<br><br>General > Action: Allow the connection<br><br>Programs and Services > Programs > This Program > %SystemRoot%\\system32\\lsass.exe<br><br>Advanced > Profiles: Private, Public<br><br>Protocols and Ports > Remote port: All TCP and UDP ports<br><br>Allow outbound LDAP<br><br>General > Action: Allow the connection<br><br>Programs and Services > Programs > This Program > All programs that meet the specified conditions<br><br>Advanced > Profiles: Private, Public<br><br>Protocols and Ports > Remote port: TCP 389, UDP 389<br><br>Allow outbound NCSI Probe<br><br>General > Action: Allow the connection<br><br>Programs and Services > Programs > This Program > %SystemRoot%\\system32\\svchost.exe<br><br>Allow Programs and Services > Service > Apply to this service > Network Location Awareness (NlaSvc)<br><br>Advanced > Profiles: Private, Public<br><br>Protocols and Ports > Remote port: TCP 80 |

### **VPN configuration**

You should deploy VPN infrastructure configured either to support the PRIME or Foundation profiles as detailed in the BCSF's [IPsec Guidance](/silver-training/topic-IPSec) and following our platform independent guidance on VPNs. 

Since version 1709, Windows 10's built-in VPN client has supported [Device Tunnel](https://docs.microsoft.com/en-us/windows-server/remote/remote-access/vpn/vpn-device-tunnel-config) mode. This allows the computer to establish a tunnel prior to users logging in, so that policy or software updates can be obtained at startup. However, an always-on user VPN will still need to be configured to allow users to access corporate resources.

If you are using a third-party VPN client, you should prefer one that has been built on top of the Windows 10 UWP VPN plug-in platform. These will likely integrate better into the platform and be more reliable, as the Windows platform is regularly updated.

## Device firmware

Devices should meet the minimum required Unified Extensible Firmware Interface (UEFI) specification 2.3.1c, boot in UEFI mode, and enable secure boot by default. UEFI legacy fall back options and direct memory access (DMA) ports should also be disabled during boot. Devices certified under the [Windows 10 Hardware Compatibility](https://docs.microsoft.com/en-us/windows-hardware/design/compatibility/whcp-specifications-policies) program implement these features by default.

You should also ensure that purchased devices implement signed manufacturer firmware updates by default. This should be checked with the manufacturer as part of your procurement process.

### **Management of UEFI firmware settings**

There are several ways in which you can manage the firmware settings of your devices:

-   Manage them locally on the device using the pre-boot UEFI console.
-   Use OEM-provided tools for management of firmware settings locally from within the running OS. Examples include [HP BIOS Configuration Utility](http://www8.hp.com/us/en/ads/clientmanagement/overview.html#manageability-tools) and [Dell Command Configure](http://en.community.dell.com/techcenter/enterprise-client/w/wiki/7532.dell-command-configure).
-   Use these same tools in conjunction with device management infrastructure such as [System Center Configuration Manager (SCCM)](https://docs.microsoft.com/en-us/sccm/index) to remotely manage devices’ firmware settings.
-   Manage them remotely using enterprise management features provided by the OEM that are integrated specifically in to device management infrastructure such as [System Center Configuration Manager (SCCM)](https://docs.microsoft.com/en-us/sccm/index). An example is [HP Manageability Integration Kit (MIK)](http://www8.hp.com/us/en/ads/clientmanagement/overview.html#manageability-tools).

One of these approaches should be taken, and used to configure the settings below.

### **Recommended settings**

The following UEFI settings should be applied. Some of these settings are hardware dependent and may not be available on all platforms.

|     |     |
| --- | --- |
| **Setting** | **Value** |
| Administrator/Setup Password + UEFI Lockout | A UEFI administrator or setup password should be set and UEFI console lockout enabled to prevent unauthorized changes to UEFI settings. |
| Boot Mode | UEFI |
| Secure Boot | Enabled |
| Legacy Boot Options and Legacy Option ROMs | Disabled |
| Manufacturer Signed Firmware Updates | Enabled |
| Trusted Platform Module (TPM) | Enabled |
| UEFI Firmware Rollback | Disabled |
| Boot Options | Restricted to only those that are required. Priority should be given to internal storage. |
| Boot Order | Locked |
| No Execute (NX) | Enabled |
| Virtualization Extensions | Enabled |
| Input/Output Memory Management Unit (IOMMU) | Enabled |
| Thunderbolt | Ports should be disabled if not required <br><br>If required<br><br>·              Disable Thunderbolt boot support if not required.<br><br>·              Disable Thunderbolt pre-boot module support.<br><br>·              Set a minimum Thunderbolt Security Level of User Authorization. |

### **Automating Updates**

Device firmware updates should be automated where possible. The BCSF recommends one of the following techniques for automating system firmware updates:

-   Windows 10 can support firmware updates via [Windows Update](https://docs.microsoft.com/en-us/windows-hardware/drivers/bringup/system-and-device-firmware-updates-via-a-firmware-driver-package). This simplifies the automation of firmware updates. You should check with your OEM that they support this update mechanism, as it is typically only used with Microsoft’s own hardware.
-   Some OEMs, including [Dell](http://en.community.dell.com/techcenter/enterprise-client/w/wiki/7536.dell-command-update-catalog) and [HP](http://www8.hp.com/us/en/ads/clientmanagement/overview.html#microsoft), distribute firmware updates as third-party Windows Server Update Services (WSUS) update package catalogues. [System Center Configuration Manager (SCCM)](https://docs.microsoft.com/en-us/sccm/index) and [System Center Update Publisher (SCUP)](https://docs.microsoft.com/en-us/sccm/sum/tools/updates-publisher) can be used to import these catalogues. The firmware updates can then be published directly in to SCCM and deployed as a [software update](https://docs.microsoft.com/en-us/sccm/sum/understand/software-updates-introduction).

**Note:** In some cases, additional client agent software may be required to support the deployment. This is dependent on the OEM - their documentation should be consulted in addition to the steps described above.

-   Firmware update utilities that are available from the OEM as Microsoft Installer Packages (.msi) can be deployed directly as a required application through an Enterprise Management solution such as [System Center Configuration Manager (SCCM)](https://docs.microsoft.com/en-us/sccm/apps/understand/introduction-to-application-management).
-   [Custom Task Sequences](https://docs.microsoft.com/en-us/sccm/osd/deploy-use/create-a-custom-task-sequence) in [System Center Configuration Manager (SCCM)](https://docs.microsoft.com/en-us/sccm/index) can also provide a method to deploy firmware updates. They provide a flexible deployment option if built-in features in SCCM - such as application installation and software updates - cannot be used to deploy the firmware update. A typical task sequence would comprise steps to target the firmware update, perform a silent installation of the firmware update utility, an option to suspend BitLocker and a forced device restart.

Note that there can be significant variation in the command line flags that are required to perform a silent installation for a specific OEM device and corresponding system firmware update utility. You should consult OEM documentation when designing the custom task sequence.

-   OEMs in many cases also provide their own client solutions that include management of firmware updates. You should refer to your OEM to determine if these solutions meet your needs.

### **Firmware Integrity and Recovery**

Some OEM devices provide support for automated firmware recovery if an update fails or the firmware becomes corrupted. These features should be enabled if supported.

In addition, some OEMs provide enhanced hardware-backed protection for the integrity of firmware, which can detect unauthorized changes to the firmware and alert or automatically recover from these changes. Devices with these features (e.g. [Intel Boot Guard](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/security-technologies-4th-gen-core-retail-paper.pdf) or [HP Sure Start](http://h10032.www1.hp.com/ctg/Manual/c05163901?_sm_au_=iVV41QpLvNQFRv0M)) should be preferred, if available.

## Enterprise considerations

The following points are in addition to the [common enterprise considerations](/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview/common-questions) and contain specific issues for Windows 10 deployments.

### **Windows 10 Enterprise feature updates**

The Windows 10 [Semi-Annual Channel](https://blogs.technet.microsoft.com/windowsitpro/2017/07/27/waas-simplified-and-aligned/) receives [feature updates twice-per-year](https://support.microsoft.com/en-gb/help/4462896/updates-to-servicing-and-support-for-windows-10). All currently supported feature updates will be supported for 30 months from their original release date. All future feature updates with a targeted release month of September (starting with 1809) will be supported for 30 months from their release date. All future feature updates with a targeted release month of March (starting with 1903) will only be supported for 18 months from their release date.

The BCSF recommends organizations deploy feature updates immediately to a targeted deployment to validate that the apps, devices and infrastructure used work well with the new release. Once validation is complete, begin deploying broadly. You can defer feature updates for up to 365 days from release. To help with this approach organizations using Azure Active Directory may deploy *Insider* *builds* to a select group of devices via the [Windows Insider Program for Business](https://insider.windows.com/en-us/for-business/).

|     |     |
| --- | --- |
| **Group Policy** | **Value(s)** |
| Computer Configuration  > Administrative Templates > Windows Components > Windows Update > Remove access to “Pause updates” feature | Enabled |
| Computer Configuration  > Administrative Templates > Windows Components> Windows Update > Windows Update for Business > Manage preview builds | Disabled |
| Computer Configuration  > Administrative Templates > Windows Components > Windows Update > Windows Update for Business > Select when Preview Builds and Feature Updates are received | Select the Windows readiness level for the updates you want to receive: Semi-Annual Channel<br><br>After a Preview Build or Feature Update is released, defer receiving it for this many days: 0 |

**Monthly Quality Updates**, which include critical security and driver updates should be downloaded and installed automatically.

If your organization is using Windows Update for Business you will need to set the Telemetry level from 0 (Security) to 1 (Basic) for update policies to be honored, as no Windows update information is gathered when set to 0. If you are using Windows Server Update Services (WSUS) or System Center Configuration Manager (SCCM) you will not be affected. For more information on Windows telemetry settings see [this document from Microsoft](https://docs.microsoft.com/en-us/windows/configuration/configure-windows-telemetry-in-your-organization) and for more information on configuring Windows Update for Business see [here](https://docs.microsoft.com/en-us/windows/deployment/update/waas-configure-wufb).

When choosing third party products that alter the behavior of the platform (such as VPN clients, anti-malware tools, management agents and auditing tools), it is important to realize that these may also need to be updated to remain compatible with newer versions of Windows 10. Products are more likely to be supported on future versions of Windows 10 if they use legitimate API’s such as the Anti-Malware Scan Interface and the Windows Runtime API for VPN’s.

This guidance may be updated in the future to cover significant new features in Windows 10 if they can improve the usability of the platform, while best addressing each of the security recommendations. The Windows 10 Long-Term Servicing Channel is designed for devices that never change, such as medical equipment and components in industrial control systems. It should not be deployed on End User Devices that are used to browse the web or use enterprise productivity software.

### **Device selection**

Windows 10 can run on a wide variety of device types with a wide variety of internal hardware. Many of the newer Windows security mitigations require the device to have specific hardware components and for them to be turned on.

Even if you are not deploying these mitigations at the moment, you should seek to buy a Windows Hardware Compatibility Program device that supports TPM 2.0, UEFI v2.3.1 or higher and has a processor with virtualization extensions.

The BCSF recommends devices that support InstantGo. Devices that are InstantGo certified will not have ports that allow DMA access and will have TPM 2.0 or later. InstantGo will maintain network connectivity when your screen is off in standby mode and will automatically have device encryption enabled.

If you are using Windows Hello with biometric authentication, you will need to buy special hardware, see [Microsoft's blog](https://blogs.windows.com/windowsexperience/2015/03/17/making-windows-10-more-personal-and-more-secure-with-windows-hello/#RCyAP8aetlQZ8WR6.97) for more information.

Signature Edition devices can be used if the required hardware is available. If using these devices, you may not need to reinstall Windows.

### **Application allow listing**

When configuring additional application allow lists for a Windows device, it is important that the following conditions are considered:

-   Users should *not* be allowed to run programs from areas where they are permitted to write files.
-   Care should be taken to ensure that application updates do not conflict with allow listing rules.
-   Applications should be reviewed before being approved enterprise-wide, to ensure they don’t undermine application allow listing. This is especially important for scripting languages which have their own execution environment.

The suggested AppLocker configuration in this guidance will implement those rules if using software that adheres to the requirements of Microsoft’s [Desktop App Certification Program](http://msdn.microsoft.com/en-us/library/windows/desktop/hh749939.aspx). If the rules do need to be customized, follow [Microsoft's Design Guide](https://docs.microsoft.com/en-us/windows/security/threat-protection/applocker/applocker-policies-design-guide) to minimize the impact to enterprise operations.

### **Universal applications**

The configuration given above prevents users from accessing the Windows Store to install applications, but an organization can still host its own store to distribute in-house applications to their employees, if required. This can be implemented either using the Microsoft Store for Business in the cloud, or via a Company Store app deployed to devices.

If the Windows Store is enabled, users should explicitly use their corporate Microsoft ID to sign into the Store app rather than associating their work device with their personal Microsoft ID. AppLocker can be configured to only allow installation of apps that are on an enterprise-configured “allow” list. The Windows Store can be configured to automatically update any installed Universal applications. The same mechanism can also be used to remove Universal Apps that come with Windows – ones that the user is not allowed to run will be disallowed and removed from the Start menu.

### **Desktop applications**

Enterprise software that handles data downloaded from the Internet needs additional protections.

Application sandboxing and content rendering controls should be considered essential. For applications such as Microsoft Office, or Adobe Acrobat, the use of their enterprise security controls should be considered. These security controls aim to help protect the end user when processing these potentially malicious files.

As well as providing a trusted platform to run enterprise web apps, modern web browsers have to process a wide variety of rich content from the Internet – some of which must be considered untrustworthy. You should consider the security controls available when choosing a web browser. If choosing a Microsoft browser, Edge should be preferred, with Internet Explorer only being used for specific website compatibility. If feasible, remove Internet Explorer from the installed image.

The update mechanisms built into Windows can be used to deploy and update Microsoft products but cannot keep third party products up to date. Where available, the auto-update mechanism built into third party products should be use to install updates. Where auto-update is not available, it will be necessary to deploy updates using an enterprise system management service.

### **Cloud integration**

Windows 10 devices do not need to be associated with a Microsoft ID to operate as required within an enterprise. Users should not enable personal, non-enterprise Microsoft ID (Live ID) accounts on the device, as this may allow data to leak through Microsoft cloud services backup and application storage.