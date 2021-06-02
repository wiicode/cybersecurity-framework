---
title: Windows 10 with MDM
description: Secure configuration for Windows 10 (1803) with Mobile Device Management
published: true
date: 2021-06-02T22:09:13.774Z
tags: guidance, silver, platform-specific, silver-training
editor: markdown
dateCreated: 2021-03-10T02:24:42.173Z
---

This guidance has been updated to cover the 1803 "April 2018 Update" of Windows 10 Enterprise. It builds on the previous Windows 10 ALPHA Mobile Device Management (MDM) guidance.

**The BCSF has separate guidance on** [managing Windows 10 deployments using traditional Domain Controllers, Active Directory and Group Policies](/collection/end-user-device-security?curPage=/collection/end-user-device-security/platform-specific-guidance)**.** Both documents will continue to be maintained.

This guidance was developed following testing performed on a Dell XPS 9360 running Windows Enterprise version 1803 (April 2018 Update), managed with Microsoft Intune (MDM) and Azure Active Directory (AAD). It applies only to Windows 10 versions newer than the April 2018 Update (version 1803) and to devices that are explicitly managed by MDM. Whilst the configuration policies have only been tested on Intune, all the configuration steps described here are supported by Microsoft’s [Configuration Service Providers (CSP)](https://docs.microsoft.com/en-us/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers) interface. As such they will be applicable to any MDM solution which supports [this interface.](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference)

Note that recommendations here are not compatible with Windows 10 Mobile devices - see the [Windows 10 Mobile platform guidance documentation](/collection/end-user-device-security?curPage=/collection/end-user-device-security/platform-specific-guidance/windows-10-mobile) for recommended settings and configurations.

It's important to remember that this guidance has been conceived as a way to satisfy the [12 End User Device Security Principles](/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview/eud-security-principles). As such, it consists of *recommendations* and should not be seen as a set of mandatory instructions requiring no further thought.

Risk owners and administrators should agree a configuration which balances business requirements, usability and security.

| **Risk** | **Explanation of difference** |
| --- | --- |
| **Windows Defender Firewall** | On traditionally managed Windows devices, we recommend using the firewall to block outbound connections when the VPN is not active. This ensures all traffic from the device goes via the VPN. Currently, you can only partially manage the Windows Defender Firewall with the configuration service provider (CSP) interface [(Firewall CSP)](https://docs.microsoft.com/en-us/windows/client-management/mdm/firewall-csp). We will update this guidance once we believe the CSP can satisfy the configuration needs and can guarantee all traffic leaving the EUD will go via the VPN. |



## Risk owners’ summary

### **We recommend the following architectural choices for Windows 10:** 

-   All data from the device should be routed over a secure enterprise [Virtual Private Network (VPN)](/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview/vpns) to ensure the confidentiality and integrity of the traffic, and to allow the devices and data on them to be protected by enterprise protective monitoring solutions.
-   Users are not permitted to install arbitrary third-party application on the device. Applications should be authorized by an administrator and deployed via a trusted mechanism.
-   Most users should have accounts with no administrative privileges. Users that require administrative privileges should use a separate unprivileged account for email and web browsing. It is recommended that local administrator accounts have a unique strong password per device.

When configured in this way, risk owners should be aware of the following technical risks associated with this platform:

| **Security Principle** | **Explanation of risks** |
| --- | --- |
| **Assured data-in-transit protection** | Currently you cannot use MDM management to configure the built-in Windows firewall to explicitly block outbound connections when the VPN is not active. |
| **Secure boot** | Windows 10 can support secure boot, but this is dependent on supported and correctly configured hardware. |



## Administrators’ deployment guide

### **Overview**

To meet the principles outlined in the [End User Devices Security Framework](https://www.gov.uk/government/publications/end-user-device-strategy-security-framework-and-controls), several recommendations are given in the table below.

| **Security Principle** | **Explanation** |
| --- | --- |
| **Assured data-in-transit protection** | Use the [Windows 10 Built-In VPN Client](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/vpn-connection-type) configured as per the BCSF customisation guide (available from [enquiries@ncsc.gov.uk](mailto:enquiries@ncsc.gov.uk)).<br><br>Use certificates for user or machine credentials. [Windows Hello](https://support.microsoft.com/en-gb/help/17215/windows-10-what-is-hello) should be used to bind these credential to the device’s hardware.<br><br>Currently you cannot use MDM management to configure the built-in Windows firewall to explicitly block outbound connections when the VPN is not active. |
| **Assured data-at-rest protection** | Use one of the following configurations to provide full volume encryption:<br><br>-   BitLocker with a TPM and PIN configured in alignment with the [BitLocker configuration settings](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#bitlocker). Note you will need to be an Administrator on the platform to enable TPM and PIN.<br>-   An independently assured CPA Foundation Grade, Data at Rest encryption product that supports UEFI and Windows Secure Boot, configured in alignment with the security procedures for that product.<br><br>If using BitLocker, ensure to back up the recovery key to AAD. <br><br>Windows 10 1803 (April Update) introduces [automatic encryption upon AAD join](https://docs.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#AllowStandardUserEncryption). If you wish to set up pre-boot authentication such as BitLocker PIN, automatic encryption will need to be disabled and an administrator will need to set a BitLocker PIN on the device. <br><br>BitLocker is not [Foundation Grade](/information//foundation-grade-explained) certified. However, the BCSF has determined that the level of protection it provides is equivalent to Foundation Grade when configured as per this guidance. |
| **Authentication** | The user implicitly authenticates to the device by decrypting BitLocker on boot.<br><br>The user then has a secondary credential to use when authenticating to the platform after boot and when unlocking the device. A good user experience will be achieved by enabling [Windows Hello for Business](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-identity-verification) and allowing the user to log in with a [PIN code](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-why-pin-is-better-than-password), this PIN code can be the same as the one used to authenticate to BitLocker. For both Windows Hello and traditional passwords, the credential derives a key which protects other credentials that give access to corporate services.<br><br>In an enterprise environment, the user will also be issued with an Azure Active Directory credential which will be required when they use a device for the first time.<br><br>Windows Hello for Business also permits [biometric unlock of devices](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-biometrics-in-enterprise) but the strength of its security is difficult to measure. In cases where there is a business requirement to use biometric authentication, and the risks of doing so are understood, biometric authentication can be enabled.<br><br>Accounts with administrative privileges should only be present on End User Devices used to perform administrative functions.<br><br>User accounts with administrative privileges should have a strong password and ideally a second factor to authenticate them to the platform at logon and unlock time. |
| **Secure boot** | On Windows 10, this requirement is met on a correctly configured platform. Organizations deciding on new devices should aim for devices that meet the standards for firmware and hardware set out within this [Microsoft page](https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-highly-secure).<br><br>A UEFI password can make it more difficult for an attacker to modify the boot process. With physical access, the boot process can still be compromised. |
| **Platform integrity and application sandboxing** | No configuration is required. |
| **Application whitelisting** | An enterprise configuration can be applied to implement application control using [AppLocker](https://docs.microsoft.com/en-gb/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview). A recommended sample configuration that only allows Administrator-installed applications to run is [provided below](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#applocker).<br><br>[Windows Defender Application Control](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune) can also be used to reinforce application control rules. As it does not offer the same granularity as AppLocker, the two technologies should be used alongside one another. A recommended sample configuration has also been [provided below](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#defender), the sample configuration allows applications from the private [Microsoft Store for Business](https://docs.microsoft.com/en-us/microsoft-store/microsoft-store-for-business-overview) to also be installed. <br><br>[AppLocker](https://docs.microsoft.com/en-gb/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-policies-design-guide) can be used to restrict which pre-installed Windows Apps are available to users. If the public Microsoft Store is enabled it can control which applications a user can install. |
| **Malicious code detection and prevention** | Windows 10 includes [Windows Defender Antivirus](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) and [Windows Defender SmartScreen](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview). These attempt to detect malicious code for the platform. Cloud sample submission can be disabled. Alternatively, third party anti-malware products are available. If using a third-party product, those that implement the [Anti-Malware Scan Interface (AMSI)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn889587(v=vs.85).aspx) should be preferred, to improve compatibility with future Feature and Quality Updates.<br><br>The [Early Launch Anti-Malware (ELAM)](https://docs.microsoft.com/en-us/windows-hardware/drivers/install/early-launch-antimalware) driver provides signature checking for known bad drivers on ELAM compliant systems that are configured to use Secure Boot.<br><br>Microsoft Store for Business or a Company Store can be used to distribute user-installable universal apps. Such stores should only contain vetted apps. If the public Microsoft Store is enabled, AppLocker and Windows Defender Application Control can be used to control which applications a user is able to install. Content-based attacks can be filtered by scanning capabilities in the enterprise. |
| **Security policy enforcement** | Disable un-enrolllment from the MDM service. Settings applied to the device via the MDM service cannot then be modified or removed by unprivileged users. Organizations using [Autopilot](https://docs.microsoft.com/en-us/windows/deployment/windows-autopilot/windows-autopilot) can force wiped devices to automatically enrolll back into the MDM service, see the [Zero-touch provisioning section below](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#zero) for more details. |
| **External interface protection** | Interfaces can be configured using MDM policy. USB removable media can be blocked through MDM settings if required. Direct Memory Access (DMA) is possible from peripherals connected to some external interfaces including FireWire and Thunderbolt, unless disabled through MDM settings as detailed in [System Hardening](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#hard), or in the UEFI/BIOS. |
| **Device updates** | Configure Windows Update to automatically download and install updates. If the Microsoft Store is enabled, it should be configured to automatically update Microsoft Store apps.<br><br>Some devices will allow the UEFI firmware to be updated automatically via Windows Update. Devices that do *not* implement this will require updates via another mechanism whenever new firmware is released. |
| **Event collection** | Events such as sign-in information and general audit logs can be found within the AAD and Intune portal. More detailed diagnostic information from the device can be obtained using the [DiagnosticLog CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/diagnosticlog-csp). |
| **Incident response** | Windows 10 devices can be wiped remotely by an MDM. In the event that a device is compromised, a full device wipe is recommended - see the [BCSF Factory reset guidance](/collection/end-user-device-security?curPage=/collection/end-user-device-security/factory-reset-and-reprovisioning) for more details on how to achieve this on Windows 10. |

### **Preparation for deployment**

The steps below should be followed to prepare infrastructure for deployment of these devices:

1.  Procure, deploy and configure network components, including an approved IPsec VPN Gateway.
2.  Configure Azure Active Directory (AAD) with the appropriate accounts and licenses to meet your organization’s needs. Set up and approve your [MDM solution to be authoritative over the directory](https://docs.microsoft.com/en-us/windows/client-management/mdm/azure-active-directory-integration-with-mdm).
3.  Configure AAD to [automatically enrolll connected devices](https://docs.microsoft.com/en-us/intune/windows-enrollll#enable-windows-10-automatic-enrollllment) into the chosen MDM solution.
4.  Configure users and groups according to the principle of least privilege.
5.  Create MDM profiles for users in accordance with the settings later in this section.
6.  Deploy an AppLocker rule set using MDM settings following guidance in the [Application allow listing section](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#whitelist). A sample configuration which allows only applications installed by an Administrator to run, is outlined in the [AppLocker](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#applocker) settings below.

### **Device provisioning steps**

The steps below should be followed to provision each end user device, preparing it for distribution to end users:

1.  By default, the user who joins the device to AAD and enrollls into MDM is placed into the Local Administrators group on that device. As such, users should **not** be instructed to enrolll themselves. All device enrolllment should be performed by administrators using administrative accounts. Alternatively, if using a correctly configured zero-touch deployment programme such as [Autopilot](https://docs.microsoft.com/en-us/windows/deployment/windows-autopilot/windows-10-autopilot), users will not be given admin privileges.
2.  Update the system firmware to the latest version available from the vendor. This will be called either a UEFI or BIOS update. This may not be required if your devices receive firmware updates via Windows Update.
3.  Configure the system firmware to boot in UEFI mode, enable TPM, Secure Boot and virtualization extensions. Disable unused hardware interfaces, check the boot order to prioritize internal storage and set a password to prevent changes. Most of these settings will be available on devices that meet the standards set by [Microsoft for a highly secure Windows 10 device](https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-highly-secure).
4.  Deploy your organization’s standard desktop build using a clean [Windows 10 Enterprise image](https://www.microsoft.com/en-gb/software-download/windows10) or use a [Signature Edition](https://www.microsoft.com/en-PR/store/b/pcsignatureedition) device where re-imaging may not be needed.
5.  Join the device to AAD and enrolll it into your MDM either by:
    1.  Promoting a dedicated provisioning account to become a [Device Enrolment Manager](https://docs.microsoft.com/en-us/intune-classic/deploy-use/enrollll-corporate-owned-devices-with-the-device-enrollllment-manager-in-microsoft-intune). Use this account to join AAD and enrolll into your MDM.
    2.  Use the [Windows Configuration Designer tool](https://docs.microsoft.com/en-us/windows/configuration/provisioning-packages/provisioning-install-icd) which is part of the [Windows Assessment and Deployment Kit (ADK)](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit), to create a [provisioning package](https://docs.microsoft.com/en-us/windows/configuration/provisioning-packages/provisioning-packages). Apply the provisioning package during the out-of-box experience (OOBE). The first account used to sign in will be added to the list of local administrators.
    3.  Use an MDM-specific enrolllment app.

### **Zero-touch provisioning steps** 

Windows Autopilot is a collection of technologies used to set up and pre-configure devices directly from OEMs (Original Equipment Manufactures).

Autopilot explicitly requires MDM automatic enrolllment, details on how to set this up can be found [here](https://docs.microsoft.com/en-gb/intune/windows-enrollll), other requirements can be found [here](https://docs.microsoft.com/en-gb/partner-center/autopilot).

Organizations can use Autopilot on new or existing devices by:

### **New devices**

1.  Purchase new devices from OEM or via normal procurement route, ensuring they support the Windows Autopilot programme.
2.  Claim ownership of devices by uploading the device IDs provided by the OEM to Microsoft Store for Business, Intune or equivalent MDM.
3.  Configure Autopilot deployment profile and assign to devices, following the example profile [below](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#autopilot).
4.  Provide end users with AAD username and password to log into new devices.
5.  Ship devices directly to end users ensuring they are connected to the internet\* when they go through the OOBE for the first time.

### **Existing devices** 

1.  Reset or re-image existing devices
2.  Run the [Windows Autopilot Info PowerShell script](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo/1.3) to gather the required device IDs.
3.  Upload the device IDs to Microsoft Store for Business, Intune or equivalent MDM.
4.  Configure deployment profile and assign to devices. Follow the below [example configuration for Autopilot](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#autopilot).
5.  Provide end users with AAD username and password to log into new devices.
6.  Give devices to end users ensuring they connect to the internet\* when they go through the OOBE for the first time.

**\***Devices must connect to the internet when they go through OOBE. A device with no internet access will not be able to enrolll into your organization's MDM and apply security configuration. 

### **Recommended configuration profile for Autopilot:** 

The following options are automatically enabled for devices that are deployed with Autopilot:

-   Skip Work or Home usage selection
-   Skip OEM registration and OneDrive configuration
-   Skip user authentication in OOBE

The table below shows the additional recommended configuration admins should set for Autopilot:

| **Windows Autopilot deployment profile** | **Value(s)** |
| --- | --- |
| Device enrolllment - Windows enrolllment - Deployment Profiles | Deployment mode: User-Driven |
| Device enrolllment - Windows enrolllment - Deployment Profiles<br><br>Out-of-box experience (OOBE) | End user license agreement (EULA): Show <br><br>Privacy Settings: Show<br><br>User account type: Standard |



## Recommended policies and settings

This section details important security policy settings which are recommended for a Windows 10 MDM deployment. Remember, any guidance points given here are recommendations - they are not mandatory.

Risk owners and administrators should agree a configuration which balances business requirements, usability and the security of the platform. Settings not listed in this section are either not applicable to this mode, not currently available, or should be chosen according to your organization's policies and requirements.

Some of the configuration below utilises [ADMX-backed CSP polices](https://docs.microsoft.com/en-us/windows/client-management/mdm/understanding-admx-backed-policies), you should familiarise yourself with this structure before continuing. To enable these types of polices, read [this guide](https://docs.microsoft.com/en-us/windows/client-management/mdm/enable-admx-backed-policies-in-mdm). Some of these settings are specific to Microsoft Intune. When using other MDM solutions, the equivalent setting should be configured. Not that the text you see accompanying a setting may be different to that shown below. 

## Importable configuration scripts

Organizations using Microsoft Intune can [download the below configuration as a zipped JSON file](https://s3.eu-west-2.amazonaws.com/eud-security-guidance/BCSF+-+Windows+10+(1803)+-+MDM.zip). The configuration can then be imported into Intune using a [Microsoft-provided import script](https://github.com/microsoftgraph/powershell-intune-samples/blob/master/DeviceConfiguration/DeviceConfiguration_Import_FromJSON.ps1).

##   
  
 

## User Account Hardening

| **Device Configuration Profile** | **Value(s)** |
| --- | --- |
| Custom configuration<br><br>CredentialsUI –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/CredentialsUI/DisablePasswordReveal | Date type: String (XML)<br><br>Value: |

|     |     |
| --- | --- |
| Device Restrictions - General<br><br>Cortana | Block |
| Device restrictions – Cloud and Storage<br><br>Settings synchronisation for Microsoft account | Block |
| Device Restrictions - Password<br><br>Password | [As per Authentication Policy](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#auth) |
| Device Restrictions - Password<br><br>Maximum minutes of inactivity until screen locks | [As per Authentication Policy](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#auth) |
| Device Restrictions - Password<br><br>Simple passwords | [As per Authentication Policy](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#auth) |
| Device restrictions – Windows Spotlight<br><br>Windows Spotlight | Block |
| Device restrictions – Windows Spotlight<br><br>Apps Suggestions in Ink Workspace | Block |
| Device restrictions – General<br><br>Ink Workspace | Disabled on lock screen |
| Device restrictions – General<br><br>Manual unenrolllment | Block<br><br>Note - This policy setting is not applied if the computer is AAD joined and auto-enrolllment is enabled. |

##   
  
 


## Authentication Policy

Your organization should have a consistent authentication policy which applies to all users and devices capable of accessing its data. You can use our published [password guidance](/collection/passwords) to help inform any password policy.

An administrator should configure the relevant on-device settings in line with your authentication policy.

For further guidance on authentication policies, see the [BCSF EUD Authentication guidance](/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview/authentication-policy).

Intune, along with other MDMs, implement a number of relevant settings as Fine Grained Password Policies that should be configured.

| **Password Profile** | **Value(s)** |
| --- | --- |
| Device Restrictions - Password | Minimum password length<br><br>Number of sign-in failures before wiping device<br><br>Directly Applies To: AAD Users |
| Device Restrictions - Password | Minimum password length<br><br>Required password type: Alphanumeric<br><br>Password complexity: Numbers, lowercase, uppercase and special characters required<br><br>Number of sign-in failures before wiping device<br><br>Directly Applies To: Administrators |
| Device Restrictions - Password<br><br>Simple passwords | Block |

###   
**Azure Active Directory**

A user’s Azure Active Directory password will normally only be used when enrolllling against a device for the first time. It is not backed by a second factor or by [hardware-backed anti-hammer](https://docs.microsoft.com/en-us/windows/security/hardware-protection/tpm/tpm-fundamentals#anti-hammering), even when Credential Guard is deployed. Different requirements can be set for different account types using [Fine Grained Password Policies.](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770394(v=ws.10)) If the Azure Active Directory password is only used for device enrolllment, it needs to be easy to type in but does not need to be memorable.

###   
**Windows Hello for Business and Hardware Strengthening**

The user should log in to a device or unlock it using [Windows Hello for Business](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/manage-identity-verification-using-microsoft-passport). This user credential is tied to the physical device using a PIN or biometric. When run on [Windows 10 Certified devices](https://docs.microsoft.com/en-gb/windows-hardware/design/compatibility/whcp-specifications-policies) it provides hardware-backed [anti-hammer](https://docs.microsoft.com/en-us/windows/access-protection/hello-for-business/hello-overview). Windows Hello should only be enabled on devices that use a hardware security device.

Users can choose to set a PIN after they have logged on to the device for the first time. A number of settings can be used to configure the PIN requirements including:

-   Use a Trusted Platform Module (TPM)
-   Minimum PIN length
-   Maximum PIN length
-   Lowercase letters in PIN
-   Uppercase letters in PIN
-   Special characters in PIN
-   Use enhanced anti-spoofing, when available
-   Allow phone sign-in

Once a PIN is set, if the device has the right sensors, the user can also enrolll a biometric to unlock it. The strength of the security of the different types of biometric sensor is difficult to measure. If the risks of enabling biometrics are understood and accepted, biometric authentication can be enabled.

| **Device enrolllment > Windows enrolllment > Windows Hello for Business > Settings** |
| --- |
| Allow biometric authentication |

The configuration provided in this guidance enables [Virtual Secure Mode and Credential Guard](https://blogs.technet.microsoft.com/ash/2016/03/02/windows-10-device-guard-and-credential-guard-demystified/) on supported devices. Biometrics should not be used unless these features are installed and enabled. Biometrics are enabled by default on Windows 10, so MDM policy should be used to disable biometrics if Virtual Secure Mode and Credential Guard are not being used.

##   
  
 

## System Hardening

| **Device Configuration Profile** | **Value(s)** |
| --- | --- |
| Device restrictions – Reporting and telemetry<br><br>Share usage data | [Security](https://docs.microsoft.com/en-us/windows/configuration/configure-windows-telemetry-in-your-organization)<br><br>Note - If using Windows Update for Business this will need to be set to Basic.<br><br>See [Windows 10 feature updates](/collection/end-user-device-security?curPage=/collection/end-user-device-security/platform-specific-guidance) for more details. |
| Device restrictions – General<br><br>Device discovery | Block |
| Device restrictions – General<br><br>Add provisioning package | Block |
| Device restrictions – General<br><br>Remove provisioning packages | Block |
| Device restrictions – Locked Screen Experience<br><br>Cortana on locked screen | Block |
| Device restrictions – Locked Screen Experience<br><br>Toast notification on locked screen | Block |
| Device restrictions – App Store<br><br>Trusted app installation | Allow |
| Device restrictions – App Store<br><br>Developer unlock | Block |
| Device restrictions – App Store<br><br>Use private store only | Allow |
| Device restrictions – Cellular and connectivity<br><br>Automatically connect to Wi-Fi hotspots | Block |

|     |     |
| --- | --- |
| Custom configuration<br><br>ErrorReporting/DisableWindowsErrorReporting –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/ErrorReporting  <br>/DisableWindowsErrorReporting | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>DeviceInstallation/PreventInstallationOfMatchingDeviceIDs – <br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/DeviceInstallation  <br>/PreventInstallationOfMatchingDeviceIDs | Date type: String (XML)<br><br>Value:  <br><br>PCI\\CC\_0C0A |
| Custom configuration<br><br>DeviceInstallation/PreventInstallationOfMatchingDeviceSetup  <br>Classes –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/DeviceInstallation  <br>/PreventInstallationOfMatchingDeviceSetupClasses | Date type: String (XML)<br><br>Value: <br><br>{d48179be-ec20-11d1-b6b8-00c04fa372a7}<br><br>{7ebefbc0-3200-11d2-b4c2-00a0C9697d07}<br><br>{c06ff265-ae09-48f0-812c-16753d7cba83}<br><br>{6bdd1fc1-810f-11d0-bec7-08002be2092f} |
| Custom configuration<br><br>DataProtection/AllowDirectMemoryAccess –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/DataProtection  <br>/AllowDirectMemoryAccess | Date type: Integer<br><br>Value: 0<br><br>Not Allowed |
| Custom configuration<br><br>NetworkIsolation/EnterpriseProxyServersAreAuthoritative –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/NetworkIsolation  <br>/EnterpriseProxyServersAreAuthoritative | Date type: Integer<br><br>Value: 1 |
| Custom configuration<br><br>NetworkIsolation/EnterpriseIPRangesAreAuthoritative –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/NetworkIsolation  <br>/EnterpriseIPRangesAreAuthoritative | Date type: Integer<br><br>Value: 1 |
| Custom configuration<br><br>System/BootStartDriverInitialization –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/System  <br>/BootStartDriverInitialization | Date type: String (XML)<br><br>Enabled: Good, Unknown and bad but critical |
| Custom configuration<br><br>WindowsLogon/DontDisplayNetworkSelectionUI –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/WindowsLogon  <br>/DontDisplayNetworkSelectionUI | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>Power/AllowStandbyWhenSleepingPluggedIn –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/Power  <br>/AllowStandbyWhenSleepingPluggedIn | Date type: String<br><br>Value: |
| Custom configuration<br><br>Power/RequirePasswordWhenComputerWakesOnBattery –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/Power  <br>/RequirePasswordWhenComputerWakesOnBattery | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>Power/RequirePasswordWhenComputerWakesPluggedIn –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/Power  <br>/RequirePasswordWhenComputerWakesPluggedIn | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>RemoteAssistance/SolicitedRemoteAssistance –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/RemoteAssistance/SolicitedRemoteAssistance | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>RemoteProcedureCall/RestrictUnauthenticated  <br>RPCClients –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/RemoteProcedureCall/RestrictUnauthenticated  <br>RPCClients | Date type: String (XML)<br><br>Enabled: Authenticated |
| Custom configuration<br><br>Autoplay/DisallowAutoplayForNonVolumeDevices –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/AutoPlay/DisallowAutoplayForNonVolumeDevices | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>Autoplay/SetDefaultAutoRunBehavior –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/Autoplay/SetDefaultAutoRunBehavior | Date type: String (XML)<br><br>Enabled: Do not execute any AutoRun commands |
| Custom configuration<br><br>Autoplay/TurnOffAutoPlay –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/Autoplay/TurnOffAutoPlay | Date type: String (XML)<br><br>Enabled: All Drives |
| Custom configuration<br><br>RemoteDesktopServices/DoNotAllow  <br>DriveRedirection –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/RemoteDesktopServices/DoNotAllow  <br>DriveRedirection | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>RemoteDesktopServices/PromptFor  <br>PasswordUponConnection –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/RemoteDesktopServices/PromptFor  <br>PasswordUponConnection | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>RemoteDesktopServices/RequireSecure  <br>RPCCommunication –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/RemoteDesktopServices/RequireSecure  <br>RPCCommunication | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>RemoteDesktopServices/ClientConnection  <br>EncryptionLevel –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/RemoteDesktopServices/ClientConnection  <br>EncryptionLevel | Date type: String (XML)<br><br>Enabled: High |
| Custom configuration<br><br>Search/AllowIndexingEncryptedStoresOrItems –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/Search  <br>/AllowIndexingEncryptedStoresOrItems | Data type: Integer<br><br>Value: 0<br><br>Not allowed |
| Custom configuration<br><br>WindowsInkWorkspace/AllowWindowsInk  <br>Workspace –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/WindowsInkWorkspace/AllowWindowsInk  <br>Workspace | Data type: Integer<br><br>Value: 1<br><br>Enabled but the user cannot access it above the lock screen |
| Custom configuration<br><br>DeviceLock/PreventLockScreenSlideShow –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/DeviceLock/PreventLockScreenSlideShow | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>WindowsPowerShell/TurnOnPowerShellScript  <br>BlockLogging –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/WindowsPowerShell/TurnOnPowerShellScript  <br>BlockLogging | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>DeviceLock/PreventEnablingLockScreenCamera –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/DeviceLock/PreventEnablingLockScreenCamera | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>MSSecurityGuide/ApplyUACRestrictionsToLocal  <br>AccountsOnNetworkLogon –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/MSSecurityGuide/ApplyUACRestrictionsToLocal  <br>AccountsOnNetworkLogon | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>MSSecurityGuide/ConfigureSMBV1ClientDriver –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/MSSecurityGuide/ConfigureSMBV1ClientDriver | Date type: String (XML)<br><br>Value: Enabled - SMBv1 Driver Disabled |
| Custom configuration<br><br>MSSecurityGuide/ConfigureSMBV1Server –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/MSSecurityGuide/ConfigureSMBV1Server | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>MSSecurityGuide/EnableStructuredException  <br>HandlingOverwriteProtection –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/MSSecurityGuide/EnableStructuredException  <br>HandlingOverwriteProtection | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>MSSecurityGuide/TurnOnWindowsDefender  <br>ProtectionAgainstPotentially  <br>UnwantedApplications –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/MSSecurityGuide  <br>/TurnOnWindowsDefenderProtectionAgainst  <br>PotentiallyUnwantedApplications | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>MSSecurityGuide/WDigestAuthentication –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/MSSecurityGuide/WDigestAuthentication | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>LanmanWorkstation/EnableInsecureGuestLogons –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/LanmanWorkstation/EnableInsecureGuestLogons | Data type: Integer<br><br>Value: 0<br><br>Disabled |
| Custom configuration<br><br>Games/AllowAdvancedGamingServices –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/Games/AllowAdvancedGamingServices | Data type: Integer<br><br>Value: 0<br><br>Not Allowed |
| Custom configuration<br><br>ControlPolicyConflict/MDMWinsOverGP –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config  <br>/ControlPolicyConflict/MDMWinsOverGP | Data type: Integer<br><br>Value: 1<br><br>MDM policy overrides Group Policy |
| Custom configuration<br><br>SystemServices/ConfigureHomeGroupListener  <br>ServiceStartupMode –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/SystemServices  <br>/ConfigureHomeGroupListenerServiceStartupMode | Data type: Integer<br><br>Value: 4<br><br>Disabled |
| Custom configuration<br><br>SystemServices/ConfigureHomeGroupProvider  <br>ServiceStartupMode –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/SystemServices  <br>/ConfigureHomeGroupProviderServiceStartupMode | Data type: Integer<br><br>Value: 4<br><br>Disabled |
| Custom configuration<br><br>SystemServices/ConfigureXboxAccessoryManagement  <br>ServiceStartupMode –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/SystemServices  <br>/ConfigureXboxAccessoryManagementServiceStartupMode | Data type: Integer<br><br>Value: 4<br><br>Disabled |
| Custom configuration<br><br>SystemServices/ConfigureXboxLiveAuthManager  <br>ServiceStartupMode –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/SystemServices  <br>/ConfigureXboxLiveAuthManagerServiceStartupMode | Data type: Integer<br><br>Value: 4<br><br>Disabled |
| Custom configuration<br><br>SystemServices/ConfigureXboxLiveGameSave  <br>ServiceStartupMode –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/SystemServices  <br>/ConfigureXboxLiveGameSaveServiceStartupMode | Data type: Integer<br><br>Value: 4<br><br>Disabled |
| Custom configuration<br><br>SystemServices/ConfigureXboxLiveNetworking  <br>ServiceStartupMode –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/SystemServices  <br>/ConfigureXboxLiveNetworkingServiceStartupMode | Data type: Integer<br><br>Value: 4<br><br>Disabled |
| Custom configuration<br><br>MSSLegacy/AllowICMPRedirectsToOverrideOSPF  <br>GeneratedRoutes –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/MSSLegacy  <br>/AllowICMPRedirectsToOverrideOSPFGeneratedRoutes | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>MSSLegacy/AllowTheComputerToIgnoreNetBIOS  <br>NameReleaseRequestsExceptFromWINSServers –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/MSSLegacy  <br>/AllowTheComputerToIgnoreNetBIOSName  <br>ReleaseRequestsExceptFromWINSServers | Date type: String (XML)<br><br>Value: |
| Custom configuration<br><br>MSSLegacy/IPSourceRoutingProtectionLevel –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/MSSLegacy  <br>/IPSourceRoutingProtectionLevel | Data type: String (XML)<br><br>Value: <br><br>Highest Protection, source routing is completely disabled |
| Custom configuration<br><br>MSSLegacy/IPv6SourceRoutingProtectionLevel –<br><br>OMA-URI:<br><br>./Device/Vendor/MSFT/Policy/Config/MSSLegacy  <br>/IPv6SourceRoutingProtectionLevel | Data type: String (XML)<br><br>Value: <br><br>Highest Protection, source routing is completely disabled |

   
 

MDM policy can be used to limit user access to removable media such as USB mass storage devices, if required by organizational policy. The settings can be found in Device restrictions > General > Removable storage

MDM policy can also be used to fully allow elist all devices, or device classes, which are allowed to be installed. In this way you could allow, for example, basic peripherals such as mice, keyboards, monitors and network cards, but refuse the connection and installation of other devices. It is important to allow list enough classes of device to allow a successful boot on a variety of hardware.

Details on how to enable allow listing of specific devices can be found on [MSDN](http://msdn.microsoft.com/en-us/library/bb530324.aspx).

### **Windows Defender configuration**

See below for configuration on Windows Defender suite of protections.

**Windows Defender Antivirus configuration**

Configure Windows Defender Antivirus to enable [cloud-backed protections](https://technet.microsoft.com/en-gb/itpro/windows/keep-secure/windows-defender-block-at-first-sight) while limiting its ability to send sensitive data for analysis. Organizations should consider the [BCSF Cloud Security Principles](/collection/cloud-security) when accessing cloud enabled solutions. 

| **Device Configuration Profile** | **Value(s)** |
| --- | --- |
| Device Restrictions – Windows Defender Antivirus <br><br>Real-time monitoring | Enabled |
| Device Restrictions – Windows Defender Antivirus <br><br>Behaviour monitoring | Enabled |
| Device Restrictions – Windows Defender Antivirus <br><br>Network Inspection System (NIS) | Enabled |
| Device Restrictions – Windows Defender Antivirus <br><br>Scan all downloads | Enabled |
| Device Restrictions – Windows Defender Antivirus<br><br>Scan scripts loaded in Microsoft web browsers | Enabled |
| Device Restrictions – Windows Defender Antivirus<br><br>Scan archive files | Enabled |
| Device Restrictions – Windows Defender Antivirus<br><br>Scan incoming mail messages | Enabled |
| Device Restrictions – Windows Defender Antivirus<br><br>Scan removable drives during a full scan | Enabled |
| Device Restrictions – Windows Defender Antivirus<br><br>Cloud-delivered protection | Enabled |
| Device Restrictions – Windows Defender Antivirus<br><br>File Blocking Level | High |
| Device Restrictions – Windows Defender Antivirus<br><br>Time extension for file scanning by the cloud | 50  |
| Device Restrictions – Windows Defender Antivirus<br><br>Prompt users before sample submission | Send all data without prompting |
| Device Restrictions – Windows Defender Antivirus<br><br>Submit samples consent | Send safe samples automatically |

###   
  
 

### **Windows Defender SmartScreen configuration**

Windows Defender [SmartScreen](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview) can provide organizations with protective measures if a user visits a potentially harmful website or downloads a potentially malicious file, for more information see Microsoft's page on 

See below for a set of recommended settings:

| **Device Configuration Profile** | **Value(s)** |
| --- | --- |
| Device Restrictions – Windows Defender SmartScreen<br><br>SmartScreen for Microsoft Edge | Require |
| Device Restrictions – Windows Defender SmartScreen<br><br>Malicious site access | Block |
| Device Restrictions – Windows Defender SmartScreen<br><br>Unverified file download | Block |
| Endpoint protection – Windows Defender SmartScreen<br><br>SmartScreen for apps and files | Enable |
| Endpoint protection – Windows Defender SmartScreen<br><br>Unverified files execution | Block |

###   
  
 

### **Windows Defender Exploit Guard configuration**

Windows 10 1709 introduced Windows Defender Exploit Guard, which is Microsoft's successor to EMET. Microsoft has published a 

Some of Windows Defender Exploit Guard configuration is done with an XML file, this file is then uploaded to Intune or an equivalent MDM. The XML file can be generated using the [Windows Defender Security Center application](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml#create-and-export-a-configuration-file), [exported from EMET](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml#convert-an-emet-configuration-file-to-an-exploit-protection-configuration-file) or via [PowerShell](https://docs.microsoft.com/en-gb/windows/security/threat-protection/windows-defender-exploit-guard/customize-exploit-protection#cmdlets-table)

As Exploit Guard can cause compatibility issues with some applications, Microsoft recommends that Exploit Guard policies are thoroughly tested before they are enforced across an organization. [Audit mode](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/audit-windows-defender-exploit-guard) can be used to support this.

| **Device Configuration Profile** | **Value(s)** |
| --- | --- |
| **Attack Surface Reduction rules** |     |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>Flag credential stealing from the Windows local security authority subsystem | Enable |
| **Rules to prevent Office Macro threats** |     |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>Office apps injecting into other processes (no exceptions) | Block |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>Office apps/macros creating executable content | Block |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>Office apps launching child processes | Block |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>Win32 imports from Office macro code | Block |
| **Rules to prevent script threats** |     |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>Obfuscated js/vbs/ps/macro code | Block |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>js/vbs executing payload downloaded from Internet (no exceptions) | Block |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>Process creation from PSExec and WMI commands\* | Block |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>Untrusted and unsigned processes that run from USB | Block |
| **Rules to prevent email threats** |     |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions) | Block |
| **Rules to protect against ransomware** |     |
| Endpoint protection – Windows Defender Exploit Guard – Attack Surface Reduction<br><br>Advanced ransomware protection | Enable |
| **Controlled folder access** |     |
| Endpoint protection – Windows Defender Exploit Guard – Controlled folder access<br><br>Folder protection\*\* | Enable |
| **Network filtering** |     |
| Endpoint protection – Windows Defender Exploit Guard – Network filtering<br><br>Network protection | Enable |
| **Exploit protection** |     |
| Endpoint protection – Windows Defender Exploit Guard – Exploit protection<br><br>Upload XML\*\*\* |     |
| Endpoint protection – Windows Defender Exploit Guard – Exploit protection<br><br>User editing of exploit protection interface | Block |

\* Only use if you are explicitly using Intune or another MDM. Configuration manager utilises WMI calls for device configuration

\*\* If files stored outside of user and system directories should be protected with Controlled Folder access, these should be added to Exploit Guard with [Configuration service providers](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/customize-controlled-folders-exploit-guard).

\*\*\* Use either [Windows Defender Security Center application](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml#create-and-export-a-configuration-file), [EMET](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml#convert-an-emet-configuration-file-to-an-exploit-protection-configuration-file) or [PowerShell](https://docs.microsoft.com/en-gb/windows/security/threat-protection/windows-defender-exploit-guard/customize-exploit-protection#cmdlets-table) to generate an importable XML document that is representative of your system. Read this page from [Microsoft](https://docs.microsoft.com/en-gb/windows/security/threat-protection/windows-defender-exploit-guard/exploit-protection-exploit-guard) for a detailed look on how to generate this file.

[Microsoft provide a technical document](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/enable-attack-surface-reduction) which shows a table of the various attack surface reduction rules, and what restrictions they impose.

###   
  
 

### **Windows Defender Application Control configuration**

| **Device Configuration Profile** | **Value(s)** |
| --- | --- |
| Endpoint protection – Windows Defender Application Control<br><br>Application control code integrity policies | Enforce |
| Endpoint protection – Windows Defender Application Control<br><br>Trust apps with good reputation | Enable |

Only Windows components, Microsoft store apps, and reputable applications as defined by the [Intelligent Security Graph](https://www.microsoft.com/en-gb/security/intelligence) will be allowed to run.

###   
  
 

### **Windows Defender Firewall configuration**

| **Device Configuration Profile** | **Value(s)** |
| --- | --- |
| **Global settings** |     |
| Custom configuration<br><br>Global/DisableStatefulFtp –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/Global/DisableStatefulFtp | Boolean: True (Block Stateful FTP) |
| **Domain (workplace) network** |     |
| Custom configuration<br><br>DomainProfile/EnableFirewall –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/DomainProfile/EnableFirewall | Boolean: True (Enable the Domain Firewall) |
| Custom configuration<br><br>DomainProfile/DefaultInboundAction –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/DomainProfile/DefaultInboundAction | Integer: 1 (Block inbound connections) |
| Custom configuration<br><br>DomainProfile/AllowLocalPolicyMerge –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/DomainProfile/AllowLocalPolicyMerge | Boolean: False (Ignore local policy rules) |
| Custom configuration<br><br>DomainProfile/DisableInboundNotifications –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/DomainProfile/DisableInboundNotifications | Boolean: True (Disable inbound notifications) |
| **Private (discoverable) network** |     |
| Custom configuration<br><br>PrivateProfile/EnableFirewall –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/PrivateProfile/EnableFirewall | Boolean: True (Enable the Private Firewall) |
| Custom configuration<br><br>DomainProfile/DefaultInboundAction –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/PrivateProfile/DefaultInboundAction | Integer: 1 (Block inbound connections) |
| Custom configuration<br><br>PrivateProfile/AllowLocalPolicyMerge –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/PrivateProfile/AllowLocalPolicyMerge | Boolean: False (Ignore local policy rules) |
| Custom configuration<br><br>PrivateProfile/DisableInboundNotifications –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/PrivateProfile/DisableInboundNotifications | Boolean: True (Disable inbound notifications) |
| **Public (non-discoverable) network** |     |
| Custom configuration<br><br>PublicProfile/EnableFirewall –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/PublicProfile/EnableFirewall | Boolean: True (Enable the Public Firewall) |
| Custom configuration<br><br>PublicProfile/DefaultInboundAction –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/PublicProfile/DefaultInboundAction | Integer: 1 (Block inbound connections) |
| Custom configuration<br><br>PublicProfile/AllowLocalPolicyMerge –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/PublicProfile/AllowLocalPolicyMerge | Boolean: False (Ignore local policy rules) |
| Custom configuration<br><br>PublicProfile/DisableInboundNotifications –<br><br>OMA-URI:<br><br>./Vendor/MSFT/Firewall/MdmStore  <br>/PublicProfile/DisableInboundNotifications | Boolean: True (Disable inbound notifications) |

### **AppLocker configuration**

This example set of AppLocker rules implements the principle outlined in [Enterprise Considerations](/collection/end-user-device-security/platform-specific-guidance/windows-10-1803-with-mobile-device-management#ent) below. It can be modified to allow the user to install and run apps from either an enterprise software center or the Microsoft Store.

All the below configurations require an exported AppLocker XML profile to be uploaded into Intune.

Scripting languages such as Visual Basic Scripting should be disabled unless they are specifically needed. The Australian Cyber Security Center [describe how to secure Powershell in the enterprise](http://www.asd.gov.au/publications/protect/securing-powershell.htm) if it is to be used.

| **Device Configuration Profile** | **Value(s)** |
| --- | --- |
| EXE Enforcement Mode | Enabled |
| Custom configuration<br><br>OMA-URI:<br><br>./Vendor/MSFT/AppLocker  <br>/ApplicationLaunchRestrictions  <br>/*GROUPNAME*/EXE/Policy<br><br>Data type: String (XML file) | Allow Everyone: All files located in the [Windows Defender\\Platform](https://support.microsoft.com/en-us/help/4052623/update-for-windows-defender-antimalware-platform) folder -<br><br>%OSDrive%\\ProgramData\\Microsoft\\Windows Defender\\Platform\\\*<br><br>Allow Everyone: All files located in the Program Files folder - with exceptions<br><br>Exception: (Path) %PROGRAMFILES%\\Windows Kits\\\*\\Debuggers\\\*<br><br>Allow Everyone: All files located in the Windows folder - with exceptions<br><br>Exception: (Path) %SYSTEM32%\\com\\dmp\\\*<br><br>Exception: (Path) %SYSTEM32%\\FxsTmp\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\drivers\\color\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\PRINTERS\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\SERVERS\\\*<br><br>Exception: (Path) %SYSTEM32%\\Tasks\\\*<br><br>Exception: (Path) %SYSTEM32%\\microsoft\\crypto\\rsa\\machinekeys\\\*<br><br>Exception: (Path) %WINDIR%\\tasks\\\*<br><br>Exception: (Path) %WINDIR%\\temp\\\*<br><br>Exception: (Path) %WINDIR%\\tracing\\\*<br><br>Exception: (Path) %WINDIR%\\registration\\crmlog\\\*<br><br>Exception: (Path) %WINDIR%\\servicing\\packages\\\*<br><br>Exception: (Path) %WINDIR%\\servicing\\sessions\\\*<br><br>Exception: (Publisher) %SYSTEM32%\\WMIC.exe,\*<br><br>Exception: (Publisher) %SYSTEM32%\\cmstp.exe,\*<br><br>Exception: (Publisher) %SYSTEM32%\\mshta.exe,\*<br><br>Exception: (Publisher) %SYSTEM32%\\PresentationHost.exe,\*<br><br>Exception: (Publisher) %SYSTEM32%\\windbg.exe,\*<br><br>Exception: (Publisher) %SYSTEM32%\\cipher.exe,\*<br><br>Exception: (Publisher) %Microsoft.NET%\\Framework64\\\*\\IEExec.exe<br><br>Exception: (Publisher) %Microsoft.NET%\\Framework64\\\*\\InstallUtil.exe<br><br>Exception: (Publisher) %Microsoft.NET%\\Framework\\\*\\regsvcs.exe<br><br>Exception: (Publisher) %Microsoft.NET%\\Framework\\\*\\msbuild.exe<br><br>Exception: (Publisher) %Microsoft.NET%\\Framework\\\*\\regasm.exe<br><br>Allow Administrators: All files |
| Windows Installer Enforcement Mode | Enforced |
| Custom configuration<br><br>OMA-URI:<br><br>./Vendor/MSFT/AppLocker  <br>/ApplicationLaunchRestrictions  <br>/*GROUPNAME*/MSI/Policy<br><br>Data type: String (XML file) | Allow Administrators: All Windows Installer files<br><br>Allow Everyone: %WINDIR%\\Installer\\\* |
| Script Enforcement Mode | Enforced |
| Custom configuration<br><br>OMA-URI:<br><br>./Vendor/MSFT/AppLocker  <br>/ApplicationLaunchRestrictions  <br>/*GROUPNAME*/Script/Policy<br><br>Data type: String (XML file) | Allow Everyone: All Scripts located in the Program Files folder<br><br>Allow Everyone: All Scripts located in the Windows folder - with exceptions<br><br>Exception: (Path) %SYSTEM32%\\com\\dmp\\\*<br><br>Exception: (Path) %SYSTEM32%\\FxsTmp\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\drivers\\color\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\PRINTERS\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\SERVERS\\\*<br><br>Exception: (Path) %SYSTEM32%\\Tasks\\\*<br><br>Exception: (Path) %WINDIR%\\registration\\crmlog\\\*<br><br>Exception: (Path) %WINDIR%\\tasks\\\*<br><br>Exception: (Path) %WINDIR%\\temp\\\*<br><br>Exception: (Path) %WINDIR%\\tracing\\\*<br><br>Exception: (Path) %WINDIR%\\servicing\\packages\\\*<br><br>Exception: (Path) %WINDIR%\\servicing\\sessions\\\*<br><br>Exception: (Path) %SYSTEM32%\\microsoft\\crypto\\rsa\\machinekeys\\\*<br><br>Allow Administrators: All scripts |
| DLL Enforcement Mode | Enforced |
| Custom configuration<br><br>OMA-URI:<br><br>./Vendor/MSFT/AppLocker  <br>/ApplicationLaunchRestrictions  <br>/*GROUPNAME*/DLL/Policy<br><br>Data type: String (XML file) | Allow Everyone: All DLLs located in the [Windows Defender\\Platform](https://support.microsoft.com/en-us/help/4052623/update-for-windows-defender-antimalware-platform) folder -<br><br>%OSDrive%\\ProgramData\\Microsoft\\Windows Defender\\Platform\\\*<br><br>Allow Everyone: All DLLs located in the Program Files folder<br><br>Allow Everyone: All DLLs located in the Windows folder - with exceptions<br><br>Exception: (Path) %SYSTEM32%\\com\\dmp\\\*<br><br>Exception: (Path) %SYSTEM32%\\FxsTmp\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\drivers\\color\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\PRINTERS\\\*<br><br>Exception: (Path) %SYSTEM32%\\Spool\\SERVERS\\\*<br><br>Exception: (Path) %SYSTEM32%\\Tasks\\\*<br><br>Exception: (Path) %SYSTEM32%\\microsoft\\crypto\\rsa\\machinekeys\\\*<br><br>Exception: (Path) %WINDIR%\\registration\\crmlog\\\*<br><br>Exception: (Path) %WINDIR%\\tasks\\\*<br><br>Exception: (Path) %WINDIR%\\temp\\\*<br><br>Exception: (Path) %WINDIR%\\tracing\\\*<br><br>Exception: (Path) %WINDIR%\\servicing\\packages\\\*<br><br>Exception: (Path) %WINDIR%\\servicing\\sessions\\\*<br><br>Allow Administrators: All DLLs |
| Packaged app Enforcement Mode | Enforced |
| Custom configuration<br><br>OMA-URI:<br><br>./Vendor/MSFT/AppLocker  <br>/ApplicationLaunchRestrictions  <br>/*GROUPNAME*/StoreApps/Policy<br><br>Data type: String (XML file) | Allow Everyone: All signed packaged apps<br><br>Exception: (Publisher) Microsoft.Getstarted<br><br>Exception: (Publisher) Microsoft.MicrosoftOfficeHub<br><br>Exception: (Publisher) Microsoft.SkypeApp<br><br>Exception: (Publisher) Microsoft.WindowsFeedback |

###   
  
 

### **BitLocker configuration**

The following settings should be configured to use full volume encryption in TPM and PIN mode.

| **Device Configuration Profile** | **Value(s)** |
| --- | --- |
| **Windows settings** |     |
| Endpoint protection – Windows Encryption<br><br>Encrypt devices | Require |
| **BitLocker base settings** |     |
| Endpoint protection – Windows Encryption<br><br>Configure encryption methods | Enable\* <br><br>Encryption for operating system drives: XTS-AES 256-bit<br><br>Encryption for fixed data-drives: XTS-AES 256-bit<br><br>Encryption for removable data-drives: AES-CBC 256-bit |
| **BitLocker OS drive settings** |     |
| Endpoint protection – Windows Encryption<br><br>Require additional authentication at startup | Require<br><br>Block BitLocker on devices without a compatible TPM chip: Block<br><br>Compatible TPM startup: Do not allow TPM<br><br>Compatible TPM startup PIN: Require startup PIN with TPM<br><br>Compatible TPM startup key: Do not allow startup key with TPM<br><br>Compatible TPM startup key and PIN: Do not allow startup key and PIN with TPM |
| OS drive recovery | Enable |
| User creation of recovery password | Allow 48-digit recovery password |
| User creation of recovery key | Allow 256-bit recovery key |
| Recovery options in the BitLocker setup wizard | Block |
| Save BitLocker recovery information in Azure Active Directory | Enable |
| BitLocker recovery Information stored to Azure Active Directory | Backup recovery passwords only |
| Store recovery information in Azure Active Directory before enabling BitLocker | Require |
| **BitLocker removable data-drive settings** |     |
| Write access to removable data-drive not protected by BitLocker | Block |
| Write access to devices configured in another organization | Block |

\*Devices that support automatic encryption may use a different encryption method for BitLocker such as XTS-AES 128-bit.

The BitLocker PIN should be in line with your organization’s password policy. The BCSF has published [password guidance](/collection/passwords/) to inform this. Please [contact us](/section/about-this-website/contact-us) if you need help devising an appropriate password policy.

Users can change the PIN after they have logged on to the device for the first time. A number of MDM policies can be used to configure the PIN requirements including:

| **Device configuration > Endpoint protection > Windows Encryption** |
| --- |
| Minimum PIN Length > Minimum characters |

###   
  
 

### **VPN configuration**

You should deploy VPN infrastructure configured either to support the PRIME or Foundation profiles as detailed in the [BCSF's IPsec Guidance](/guidance/using-ipsec-protect-data). Customisation guides are available for the Windows 10 Built-In VPN Client. Contact [BCSF enquiries](/section/about-this-website/contact-us) to obtain a copy.

[PRIME](/guidance/using-ipsec-protect-data) is the recommended IPsec cipher suite profile for protecting information, and it requires a PKI infrastructure configured to support Elliptic Curve cryptography. A non-authoritative summary is provided in the table below:

| **IKEv2** | **Selection** |
| --- | --- |
| Encryption | AES with 128-bit keys in GCM-128 mode |
| Pseudo-Random Function | HMAC-SHA-256 (RFC4868) |
| Diffie-Hellman Group | Group 19 256-bit random ECP (RFC5903) |
| Authentication | X.509 certificates with ECDSA signatures (256-bit) on the P-256 curve and SHA-256 (RFC4945 and RFC4055) |
| **ESP** | **Selection** |
| Encryption | AES-128 in GCM-128 mode |

  
If you are using a third-party VPN client, you should prefer one that has been built on top of the Windows 10 UWP VPN plug-in platform. These will likely integrate better into the platform and be more reliable, as the Windows platform is regularly updated.




## Enterprise Considerations

The following points are in addition to the common enterprise considerations, and contain specific issues for Windows 10 MDM deployments.

### **Windows 10 feature updates**

The Windows 10 [Semi-Annual Channel](https://blogs.technet.microsoft.com/windowsitpro/2017/07/27/waas-simplified-and-aligned/) receives feature updates twice-per-year. These feature updates will be serviced for 18 months from the date of release and will replace Current Branch (CB) and Current Branch for Business (CBB) concepts.

You should deploy feature updates immediately to a targeted deployment in order to validate that apps, devices and infrastructure work well with the new release. Once validation is complete, begin deploying broadly. You can defer feature updates for up to 365 days from release. To help with this approach organizations using Azure Active Directory may deploy Insider builds to a select group of devices via the [Windows Insider Program for Business](https://insider.windows.com/en-us/for-business/).

Monthly Quality Updates which include security, critical and driver updates should be downloaded and installed automatically.

If your organization is using Windows Update for Business you will need to set the Telemetry level from 0 (Security) to 1 (Basic) for update policies to be honoured, as no Windows update information is gathered when set to 0. For more information on Windows telemetry settings see [this Microsoft technical document](https://docs.microsoft.com/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization) and for more information on configuring [Windows Update for Business see this Microsoft document](https://docs.microsoft.com/en-us/windows/deployment/update/waas-configure-wufb).

When choosing third party products that alter the behavior of the platform (such as VPN clients, anti-malware tools, management agents and auditing tools), it is important to consider that these may also need to be updated to remain compatible with newer versions of Windows 10. Products are more likely to be supported on future versions of Windows 10 if they use legitimate API’s such as the Anti-Malware Scan Interface and the Windows Runtime API for VPN’s.

This guidance may be updated in the future to cover significant new features in Windows 10 if they can improve the usability of the platform, while best addressing each of the security recommendations. The Windows 10 Long-Term Servicing Channel is designed for devices that never change, such as medical equipment and components in industrial control systems. It should not be deployed on End User Devices that are used to browse the web or use enterprise productivity software.

### **Device selection**

Windows 10 can run on a wide variety of device types with a wide variety of internal hardware. However, many of the newer Windows security mitigations require the device to have specific hardware components and for these to be turned on.

Even if you are not deploying these mitigations at the moment, you should seek to buy a Windows Hardware Compatibility Program device that support TPM 2.0, UEFI v2.3.1 or higher and have a processor with virtualization extensions.

The BCSF recommends devices that support InstantGo. Devices that are InstantGo certified will not have ports that allow DMA access and will have TPM 2.0 or later. InstantGo will maintain network connectivity when your screen is off in standby mode and will automatically have device encryption enabled.

If you are using Windows Hello with biometric authentication, you will need to buy special hardware, see [Microsoft's blog](https://blogs.windows.com/windowsexperience/2015/03/17/making-windows-10-more-personal-and-more-secure-with-windows-hello/#RCyAP8aetlQZ8WR6.97) for more information. 

[Signature Edition](https://www.microsoft.com/en-us/store/b/pcsignatureedition) devices can be used if the required hardware is available. If using these devices, you may not need to reinstall Windows. 

### **Device firmware**

You should ensure that devices are configured to boot from UEFI with Secure Boot enabled when initially installing Windows 10 – even if you choose to not configure some of the features that require it. This will make future version upgrades and adoption of those features easier.

The Windows 10 Secure Boot process (on supported and correctly configured hardware) alerts a user when an attempt to subvert the security controls has taken place. It is important that users know how to [identify](http://technet.microsoft.com/en-us/library/dn441535.aspx) and respond to this alert.

Firmware updates can be automated via Windows Update and you should prefer devices that support this. If your OEM (original equipment manufacturer) is not choosing to use that mechanism, you will need to periodically check with them to see what the most recent version of the firmware is and how to deploy it across an enterprise. 

### **Application allow listing** 

When configuring additional application allow lists for a Windows device, it is important that the following conditions are considered:

-   Users should not be allowed to run programs from areas where they are permitted to write files.
-   Care should be taken to ensure that application updates do not conflict with allow listing rules.
-   Applications should be reviewed before being approved enterprise-wide, to ensure they don’t undermine application allow listing. This is especially important for scripting languages which have their own execution environment.

The suggested AppLocker configuration in this guidance will implement those rules if using software that adheres to the requirements of Microsoft’s [Desktop App Certification Program](http://msdn.microsoft.com/en-us/library/windows/desktop/hh749939.aspx). If the rules do need to be customised, follow Microsoft's Design Guide to minimize operational impact.

### **Universal applications**

The configuration given above prevents users from accessing the public Microsoft Store to install applications, but an organization can still host its own store to distribute in-house applications to their employees if required. This can be implemented either using Microsoft Store for Business in the cloud, or via a Company Store app deployed to devices.

If the Microsoft Store is enabled, users should explicitly use their corporate Microsoft ID to sign into the Store app rather than associating their work device with their personal Microsoft ID. AppLocker can be configured to only allow installation of apps that are on an enterprise-configured “allow” list. The Microsoft Store can be configured to automatically update any installed Universal applications. The same mechanism can also be used to remove Universal Apps that come with Windows – ones that the user is not allowed to run will be disallowed and removed from the Start menu.

### **Desktop applications**

Enterprise software that handles data downloaded from the Internet needs additional protections.

Application sandboxing and content rendering controls should be considered essential. For applications such as Microsoft Office, or Adobe Acrobat, the use of their enterprise security controls should be considered. These security controls aim to help protect the end user when processing these potentially malicious files.

As well as providing a trusted platform to run enterprise web apps, modern web browsers have to process a wide variety of rich content from the Internet – some of which must be considered untrustworthy. You should consider the security controls available when choosing a web browser. If choosing a Microsoft browser, Edge should be preferred, with Internet Explorer only being used for specific website compatibility. If it is feasible, remove Internet Explorer from the installed image.

The update mechanisms built into Windows can be used to deploy and update Microsoft products but cannot keep third party products up to date. Where available, the auto-update mechanism built into third party products should be use to install updates – where this is not available it will be necessary to deploy updates using an enterprise system management service.

### **Cloud integration**

Windows 10 devices do not need to be associated with a Microsoft ID to operate as required within an enterprise. Users should not enable personal, non-enterprise Microsoft ID (Live ID) accounts on the device, as this may allow data to leak through Microsoft cloud services backup and application storage.

However, organizations wishing to use cloud based services such as OneDrive can use the [BCSF Cloud Security Guidance](/collection/cloud-security) to help them understand both the benefits and risks of using online services.