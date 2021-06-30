---
title: Ubuntu 18.04 LTS
description: Secure configuration for Ubuntu 18.04 LTS
published: true
date: 2021-06-30T02:06:47.030Z
tags: silver, sourced, silver-training
editor: markdown
dateCreated: 2021-02-22T00:26:26.123Z
---

# Ubuntu Secure Configuration

> This guidance was developed following testing on devices running Ubuntu **18.04** LTS.
{.is-info}


It's important to remember that this guidance has been conceived as a way to satisfy the [12 End User Device Security Principles](/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview/eud-security-principles). As such, it consists of recommendations and should not be seen as a set of mandatory instructions requiring no further thought.

Risk owners and administrators should agree a configuration which balances business requirements, usability and security.

## Risk owners' summary

We recommend the following architectural choices for Ubuntu 18.04 LTS:

-   All data should be routed over a secure enterprise VPN to ensure the confidentiality and integrity of the traffic, and to benefit from enterprise protective monitoring solutions.
-   Users should not be allowed to install arbitrary applications on the device. Applications should be authorized by an administrator and deployed via a trusted mechanism.
-   Most users should have accounts with no administrative privileges. Users that require administrative privileges should use a separate unprivileged account for email and web browsing. It is recommended that local administrator accounts have a unique strong password per device.

When configured in this way, risk owners should be aware of the following technical risks associated with this platform:

| **Security principle** | **Explanation of risks** |
| --- | --- |
| Data in transit | Users may choose to ignore certificate warnings leaving data in transit vulnerable to interception and alteration. |
| Data at rest | The Linux Unified Key Setup (LUKS)/dm-crypt disk encryption solutions have not been independently assured to Foundation Grade, and do not support some of the [mandatory requirements expected from assured full disk encryption products](/static-assets/documents/CPA%20SC%20Software%20Full%20Disk%20Encryption%20v1-23.pdf). Without assurance there is a risk that data stored on the device could be compromised. However, the tpm-luks project can enable usage of Trusted Platform Modules (TPMs) by LUKS which may help meet more of these requirements. |
| Secure boot | Secure boot validates the bootloader, kernel and kernel modules. However, some boot-related files are not protected by default and could be modified by an attacker to tamper with the boot process. Hardening of the boot process can help mitigate the risk.<br><br>Ubuntu does not use any dedicated hardware to protect its disk encryption keys. If an attacker can get physical access to the device, they can perform an offline brute-force attack to recover the encryption password.<br><br>Encryption keys protecting sensitive data remain available to an attacker when the device is locked. This means that if the device is attacked while powered on and locked, keys and data on the device may be compromised without the attacker knowing the password. |
| External interface protection | Whilst not specific to Ubuntu itself, many devices which can run Ubuntu have external interfaces which permit Direct Memory Access (DMA) from connected peripherals. This presents a local attacker with an opportunity to exfiltrate keys and data.<br><br>Software configuration of the FireWire and Thunderbolt interfaces can reduce the risk for these interfaces.  As of 18.04.1 this can be managed through the settings UI. |

## Administrators' deployment guide

### **Overview**

To meet the principles outlined in the [End User Devices Security Framework](https://www.gov.uk/government/publications/end-user-device-strategy-security-framework-and-controls), several recommendations are given in the table below.

| **Security Principle** | **Explanation** |
| --- | --- |
| Data in transit | Use a Prime or Foundation Grade IPsec VPN client configured as per that product’s security procedures to give data-in-transit protection. |
| --- | --- |
| Data at rest | Use LUKS/dm-crypt to provide full volume encryption. |
| --- | --- |
| Authentication | The user has a different password to authenticate themselves to the device once they have entered the decryption password.<br><br>Alternatively, the user can implicitly authenticate to the device by decrypting the disk at boot time with their LUKS/dm-crypt password. This password unlocks a key which encrypts certificates and other credentials, giving access to enterprise services.<br><br>The user should be required to authenticate to the device in line with your organization’s authentication policy (see [Authentication Policy](/collection/end-user-device-security?curPage=/collection/end-user-device-security/eud-overview/authentication-policy)). |
| --- | --- |
| Secure boot | Enable secure boot. Ubuntu validates the boot process but does not verify all boot-related files against tampering. Security benefit can be obtained by applying the configuration given in the [Recommended Policies and Settings section below](/collection/end-user-device-security/platform-specific-guidance/ubuntu-18-04-lts#Policies), but this will not fully satisfy the secure boot recommendation. |
| --- | --- |
| Platform integrity and application sandboxing | These requirements are met implicitly by the platform. Where available, [AppArmor](https://wiki.ubuntu.com/AppArmor) profiles limit applications’ access to the platform. Other applications can be configured to use AppArmor if required. Snap applications run confined in a [restricted sandbox](https://docs.ubuntu.com/core/en/guides/intro/security). |
| --- | --- |
| Application whitelisting | Permissions can be configured at install time to ensure users cannot execute applications from any disk partition that they can write to. All application installation should be performed by an administrator. |
| --- | --- |
| Malicious code detection and prevention | The platform implicitly provides some protection against malicious code being able to run when configured as recommended.<br><br>Several third-party anti-malware products exist which attempt to detect malicious code for this platform. Content-based attacks can be filtered by your in-house scanning capabilities. |
| --- | --- |
| Security policy enforcement | The enforcement of security policies will be conducted by various operating system components and third-party products, based upon configuration files contained in specific directories. These include Policy Kit rules, `DConf` settings, `PackageKit` rules, `gksu` settings and `gksudo` settings.<br><br>These configuration changes can be managed centrally from a Software Configuration Management server by using custom Ubuntu packages or deploying suitable configuration files.<br><br>Settings applied by the administrator cannot be modified by the user. |
| --- | --- |
| External interface protection | Interfaces can be configured using standard platform configuration files.<br><br>DMA is possible from some external interfaces including FireWire and Thunderbolt, as of 18.04.1. These interfaces can be managed through the settings UI. It is advisable to procure hardware which does not have external DMA interfaces present. If that’s not possible, we recommend [disabling the SBP-2 FireWire protocol](/collection/end-user-device-security/platform-specific-guidance/ubuntu-18-04-lts#ext) and configuring a restrictive security level for Thunderbolt version 2 and above. |
| --- | --- |
| Device updates | Operating system security updates can be configured to be automatically applied. Using the [recommended software update settings](/collection/end-user-device-security/platform-specific-guidance/ubuntu-18-04-lts#softup), application updates are installed automatically when the device is switched on and fully booted. Snap applications are automatically updated by default multiple times a day. Additionally [Canonical LivePatch](https://www.ubuntu.com/server/livepatch) can be configured to dynamically patch the kernel at runtime, otherwise kernel updates are effective upon restart. |
| --- | --- |
| Event collection | By default, the majority of applications on Ubuntu will use RSyslog to output event logs. RSyslog can forward logs to a remote server which is most reliable when using TCP or the RELP protocol and can be secured with TLS encryption. RSyslog can also be configured to queue log messages when the remote server is unavailable and flush this queue to disk when the system is shutdown. This can avoid messages being discarded when connectivity to the central log server is unavailable.<br><br>Additional auditing can also be performed with `auditd` for specific events of interest to an administrator. |
| --- | --- |
| Incident response | There is no native remote wipe functionality available for Ubuntu, but remote wipe functionality can be implemented with a configuration management system such as [Puppet](https://puppet.com/). This system could also destroy key material for encrypted hard drives or use a secure erase feature of the drive, if present.<br><br>Access to the enterprise network can be prevented by revoking the VPN client certificate associated with a lost or stolen device. Additionally, the client certificates for any other enterprise servers (such as email) that are stored on the device should be revoked. |
| --- | --- |

###   
**Recommended network architecture**

All remote or mobile working scenarios should use a typical remote access architecture with a VPN terminating into an access layer (or DMZ). The following network diagram describes this set up. 

![](/static-assets/images/Ubuntu_PSN.PNG)

**Preparation for deployment** 

It is possible to deploy Ubuntu with the recommended configuration either via a Software Configuration Management (SCM) service or to deploy this configuration with the installer [“preseed” file](/collection/end-user-device-security/platform-specific-guidance/ubuntu-18-04-lts#files) and the [post-install script](/collection/end-user-device-security/platform-specific-guidance/ubuntu-18-04-lts#files) provided with this guidance.

An automated deployment and SCM service are recommended to manage a large number of machines with differing requirements from a central location. Deployment by manually preseeding the installer and running a post-install script can be sufficient for small scale deployments.

If using a Software Configuration Management (SCM) service, the following steps should be taken:

1\. Procure and provision an SCM server, such as [Puppet](https://puppet.com/), [Chef](https://www.chef.io/chef/) or [Ansible](https://www.ansible.com/). Optionally, install [Landscape](https://landscape.canonical.com/) as the system management tool and install a Preboot Execution Environment (PXE) to automate device provisioning from the network.

2\. Produce and provision an Ubuntu repository mirror and a repository to hold custom packages and configurations. This can be installed on the same host as the Software Configuration Management server.

3\. Install and configure Ubuntu 18.04 LTS x86\_64 on a dedicated system for the purpose of building configuration packages.

4\. Create signed packages to push the security configuration settings, and upload them to the custom repository. Update the list of packages in the Software Configuration Manager by re-synchronising with the repositories if required.

### **Device provisioning steps**

The following steps detail how to provision Ubuntu 18.04 LTS using the [preseed install file](/static-assets/documents/ubuntu_seed_.txt) and the [post-install script](/static-assets/documents/ubuntu1804_post_install.sh_.txt) provided with this guide. It is assumed that the preseed file and the post-install script are hosted on the network. As an example we will use the following URLs:

-   [https://provisioning.example.com/ubuntu.seed](https://provisioning.example.com/ubuntu.seed)
-   [https://provisioning.example.com/post-install.sh](https://provisioning.example.com/post-install.sh)

For medium-large scale deployments consider implementing a Preboot Execution Environment and using a Software Configuration Management system to perform a fully automated provisioning of a device.

1\. With the device configured to use UEFI mode, with no support for Legacy booting, and Secure Boot enabled, boot the device using the latest x86\_64 Ubuntu 18.04 LTS Desktop Live DVD, PXE boot server, or using a bootable Ubuntu USB stick as described in[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0).  When downloading ISO files, it is recommended that the [SHA-256 hash is checked](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) against the one shown on the official Ubuntu website.

2\. At the GRUB menu\*:

-   Highlight the “Install Ubuntu” menu item and press ‘e’ to edit the boot options.
-   Replace the following kernel boot options:

`file=/cdrom/preseed/ubuntu.seed` and only-ubiquity  
respectively with:  
`url=`[`https://provisioning.example.com/ubuntu.seed`](https://provisioning.example.com/ubuntu.seed) and automatic-ubiquity.   
The final line should read:  
`linux /casper/vmlinuz url=`[`https://provisioning.example.com/ubuntu.seed`](https://provisioning.example.com/ubuntu.seed) `boot=casper automatic-ubiquity quiet splash ---`   
This will instruct the installer to use the options defined in the preseed file.

3\. Press F10 to boot the installer with the preseeded settings.

4\. Once the installer has loaded, follow the on-screen instructions to proceed with the installation. The installer will ask to provide:

a) A password to encrypt the filesystem. Ensure the use of a strong password.

b) The details for the administrative local account. Additional low privilege accounts should be created for the end users at a later stage.

5\. The provided preseed configuration will automatically:

a) Clear any existing partitions from the disk and create a GUID Partition Table (GPT).

b) Create an EFI partition at the start of the disk followed by a Linux Native boot partition. The remaining free space will be allocated as a Linux Unified Key Setup (LUKS) encrypted partition. The LUKS partition will be configured as a Linux Logical Volume Manager (LVM) partition.

c) Within the LVM group, create logical volumes for swap, /home and root (/) mount points\*\*.

6\. Reboot the system and login using the administrative account configured during installation.

a) Run the post-install.sh script provided with this guide to apply the recommended policies and settings. The script should be reviewed and customised for the specific environment.

b) Alternatively, if using an SCM, manually register the device with the SCM. It is possible to automate the registration process by configuring post installation commands in the preseed installation file\*\*\*.

7\. Create a VPN certificate for the device, along with a certificate for the intended user and copy both of these to the device over a secure network connection.

8\. Configure StrongSwan to connect to the VPN gateway using the relevant profile and certificate files, and then restart the StrongSwan daemon. Example StrongSwan configuration files are provided with this guidance but these will usually need to be customised for the specific environment.

9\. Harden the UEFI configuration by setting an administrator/setup password and disabling boot from devices other than the internal Hard Disk Drive (HDD)/Solid State Drive (SSD).

**\* Alternatively the preseed file can be loaded manually.** This can be useful when troubleshooting issues:

1\. At the GRUB menu select “Try Ubuntu without installing”.

2\. Once Ubuntu has started, open a Terminal and instruct the installer to use the preseeded settings with the following commands:

-   wget [https://provisioning.example.com/ubuntu.seed](https://provisioning.example.com/ubuntu.seed)
-   sudo debconf-set-selections ubuntu.seed
-   ubiquity -d –automatic

3\. Ubuntu’s graphical installer will be launched. The installer will only prompt for settings not included in the preseed file.

##### **\*\* IT IS POSSIBLE TO CUSTOMISE THE PARTITIONING LAYOUT BY FOLLOWING THE INSTRUCTIONS IN THE “### PARTITIONING ###” SECTION OF THE PROVIDED** [**PRESEED FILE**](/static-assets/documents/ubuntu_seed_.txt)**.**

##### **\*\*\* EXAMPLE COMMANDS ARE PROVIDED IN THE “### POST INSTALLATION COMMANDS ###” SECTION OF THE** [**PRESEED INSTALLATION FILE**](/static-assets/documents/ubuntu_seed_.txt)**.**

## Recommended policies and settings

This section details important security policy settings that are recommended for an Ubuntu deployment. Other settings (e.g. server address) should be chosen according to the relevant network configuration.

Remember, any guidance points given here are recommendations - they are not mandatory. Risk owners and administrators should agree a configuration which balances business requirements, usability and the security of the platform. 

### **Authentication policy**

Your organization should have a consistent authentication policy which applies to all users and devices capable of accessing its data. You can use the published [password guidance](/collection/passwords/updating-your-approach) to help inform any password policy. An administrator should configure the relevant on-device settings in line with your authentication policy. 

For further guidance on defining an authentication policy, see the [EUD Security Guidance introduction](/collection/end-user-device-security).

The password requirements in Ubuntu Desktop can be configured in the `/etc/login.defs` file and via the Pluggable Authentication Module (PAM),

To enforce password complexity requirements install the PAM 'password quality' module with the following command:

sudo apt install libpam-pwquality

The PAM password quality module improves over the older PAM cracklib module by supporting additional password checks and by using a configuration file for its settings.

The default settings are:

-   Minimum password length 8 characters
-   Check against weak known passwords
-   Check if the username is included in the password

Adjust the settings according to fit your policy by modifying the file `/etc/security/pwquality.conf`.

For example, to enforce the use of different classes of characters the option 'minclass' can be used. Setting minclass=3 will enforce the use of 3 classes of character, such as lowercase character, uppercase characters and numbers.

Other authentication-related settings such as password ageing can be configured in the `/etc/login.defs` file.

Refer to the following man pages for further information: `login.defs`, `pwquality.conf`, `pam_unix(8)`, `pam.d`, and `pam.conf`.

In addition, you should enforce a maximum screen lock timeout (idle delay) and Enable lock on screen off (screensaver lock enabled) for the Gnome environment. By default, Ubuntu 18.04 LTS locks the screen after 5 minutes of inactivity, but this can be changed by users.

This can be achieved with the following steps:

1\. Create the directory `/etc/dconf/db/local.d/` and place a file named `00_screensaver-lock` inside the directory, with the following contents:

\[org/gnome/desktop/session\] idle-delay=600 \[org/gnome/desktop/screensaver\] lock-enabled=1 lock-delay=0

2\. Create the directory `/etc/dconf/db/local.d/locks` and place a file named `00_screensaver-lock` inside the directory, with the following contents:

/org/gnome/desktop/session/idle-delay /org/gnome/desktop/screensaver/lock-enabled /org/gnome/desktop/screensaver/lock-delay

3\. Update the `dconf` database with:

sudo dconf update

For further information about configuring and locking down Gnome settings, refer [to the Gnome documentation](https://help.gnome.org/admin/system-admin-guide/stable/dconf-lockdown.html.en).

## Boot process hardening

When Secure Boot is enabled, the boot chain is verified from UEFI down to the GRUB bootloader, the Linux kernel and the modules loaded by the kernel. While this provides mitigation against unauthorized changes to the boot process, in its default configuration, Ubuntu does not protect against all changes of boot-related files. For example, an attacker can modify the contents of the `grub.cfg` file.

To minimize the risk of unauthorized changes to the boot process, consider implementing all of the following mitigations:

1.  Configure UEFI with no support for legacy BIOS and legacy boot option, and ensure Secure Boot is enabled
2.  Configure a UEFI administration/setup password so that the UEFI configuration cannot be changed
3.  After installation disable booting from all devices other than the internal HDD/SSD
4.  Configure a GRUB password to prevent runtime changes to the grub configuration
5.  Ensure Ubuntu is booting in Secure Boot mode

By default GRUB allows all users to edit boot entries, thus making it important to secure the configuration with a password. Use the following steps to achieve that.

1\. Run `grub-mkpasswd-pbkdf2` to generate a password. The format of the output is located on the last line as`“pbkdf2.sha512.10000.XXX”`.

2\. Open `/etc/grub.d/40_custom` and add the following:

set superusers="sysadmin" password\_pbkdf2 sysadmin grub.pbkdf2.sha512.10000.XXX

3\. Open `/etc/grub.d/10`\_linux and change the lines starting with:

echo "menuentry...

To

echo "menuentry --unrestricted...

4\. Open `/etc/default/grub` and:

-   Update `GRUB_CMDLINE_LINUX_DEFAULT` to include `“module.sig_enforce=yes”` in its value, for example as `“quiet splash module.sig_enforce=yes”`
-   Add `GRUB_SAVEDEFAULT=false` to the file.

5\. When all changes have been made, run `update-grub` and restart the system.

To verify that Ubuntu is booting in secure mode, the following command can be used:

sudo mokutil --sb-state

When secure boot is disabled, the following message will be displayed by GRUB at boot time, alerting the user that secure boot has been disabled:

"Booting in insecure mode"

For further information about working with Secure Boot in Ubuntu and using third party kernel modules, refer to the man page of `“mokutil”`, to the output of the `“update-secureboot-policy --help”` command and to the following articles:

-   [https://blog.ubuntu.com/2017/08/11/how-to-sign-things-for-secure-boot](https://blog.ubuntu.com/2017/08/11/how-to-sign-things-for-secure-boot)
-   [https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS](https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS)

## Software management and automatic updates

Ubuntu 18.04 LTS supports installation of software using DEB packages (via the APT package manager) and using snaps.

The two packaging formats can co-exist in the same environment, however they differ in the way they are installed, executed and updated.

The snap packages are self-contained application binaries and they include any dependencies needed to run. A snap package will install to its own directory and it will run in application confinement, hence access to the system resources is restricted based on snap-specific security policies such as AppArmor profiles and seccomp filters.

Authorised snap packages are available through the Ubuntu Store. When a snap is uploaded on the Ubuntu Store, it undergoes automatic reviews, which involve examining the snap package’s manifest files to verify the libraries used as well as the requested interfaces by reviewing the associated security policy. Where a known security issue affects a library in a snap, the developer is automatically informed that the snap requires an update. Applications that do not update in a timely manner can be removed from the store. Auditing is also configured for the installed application to ensure logging of unauthorized operations.

In order to ensure that the installation of snap packages does not introduce any risk to the security posture of your system, it is recommended that snap packages are only installed from the authorized Ubuntu Store and from trusted developers.

An additional security concern arises from the fact that the snap packages can bundle their own versions of system libraries, so they will not depend on the installation of other packages or libraries. In the event that a vulnerability in a system library is discovered, any snap packages that include the affected system library as a dependency will be vulnerable until the snap package’s developers push a secure version of the package. In traditional deployments i.e. using DEB packages, this would have been resolved when the distribution released security updates addressing the vulnerable system library.

It is advised that any installed snap packages are updated in a timely manner to their latest, secure version available on the Ubuntu Store.

APT automatic updates should be enabled by executing the following command and selecting “yes”:

\# dpkg-reconfigure unattended-upgrades 

Alternatively:

-   Create the `/etc/apt/apt.conf.d/20auto-upgradesfile` with the following content:

APT::Periodic::Update-Package-Lists "1"; APT::Periodic::Unattended-Upgrade "1";

-   Create the `/etc/apt/apt.conf.d/10periodicfile` with the following content:

APT::Periodic::AutocleanInterval "7";

The default configuration will only permit security-related updates to be automatically installed. This can be changed by editing the `/etc/apt/apt.conf.d/50unattended-upgrades` file to enable additional sources for automatic updates.

To enable additional non-security automatic updates, uncomment the line `"${distro_id}:${distro_codename}-updates";`. The `Unattended-Upgrade::Allowed-Origins` should then contain the `-security` and `-updates` origins. Note that `-security` updates are also added to the `-updates` archive shortly after release in `-security`.

Additional configuration settings are available in `/etc/apt/apt.conf.d/50unattended-upgrades`.

The upgrade schedule is managed via a `systemd` timer.

The restriction that removes all executable permissions under `/tmp` (as mentioned in the “[Software restriction](/collection/end-user-device-security/platform-specific-guidance/ubuntu-18-04-lts#rest)” section) may cause issues with the update process. When updates are running, the service may use the `/tmp` directory to store and execute files. To bypass this issue, the following lines can be added to `/etc/apt/apt.conf.d/99tmpexec`:

DPkg::Pre-Invoke{"mount -o remount,exec /tmp";}; DPkg::Post-Invoke {"mount -o remount /tmp";};

In addition, the following permissions need to be set on that file:

chmod 644 /etc/apt/apt.conf.d/99tmpexec

These instructions will mount the /tmp folder as executable before the update begins and restore it to the state it was after the update is complete.

Snaps are automatically updated (refreshed) by default four times a day. The schedule can be verified using the following command:

sudo snap refresh --time

The update status can be verified using the following command:

sudo snap refresh –list

If a proxy is required for Internet connectivity to download/refresh snaps, this can be set in `/etc/environment` (this will affect the entire system) by adding the following lines:

http\_proxy=[http://proxyhostname:8080/](http://proxyhostname:8080/) https\_proxy=[https://proxyhostname:8080/](http://proxyhostname:8080/)

Then restart the snapd service with:

sudo systemctl restart snapd

Upgrade of the kernel version normally requires a reboot for the changes to be effective. It is possible to configure the [Canonical Livepatch Service](https://www.ubuntu.com/server/livepatch) so that critical kernel patches are automatically applied at runtime, without rebooting.

Livepatch requires subscription to Ubuntu Advantage. It is free for up to 3 machines for Ubuntu Community members.

To enable Livepatch using the command line:

1\. Generate credentials via the [Canonical Livepatch Portal](https://auth.livepatch.canonical.com/)

2\. Install the `canonical-livepatch` snap with:

sudo snap install canonical-livepatch

3\. Enable Livepatch using the generated credentials with the following command:

sudo canonical-livepatch enable \[TOKEN\]

The status and configuration of Livepatch can be verified with the following commands:

sudo canonical-livepatch status --verbose sudo canonical-livepatch config

## Software restriction

A separate partition should be created for 

/home defaults,noexec,nosuid,nodev 0 0 none /tmp tmpfs noexec,nosuid,nodev 0 0 none /run/shm tmpfs rw,noexec,nosuid,nodev 0 0

Any additional locations on the file system that the non-administrator user can both write to and execute from should be identified and locked down by changing group membership or directory permissions where possible.

Known problematic locations on an Ubuntu **18.04** LTS install configured as per this guidance are `/var/crash`, `/var/metrics`, `/var/tmp`. All but the latter can be addressed by removing the "other" write permission using the following commands:

chmod o-w /var/crash chmod o-w /var/metrics chmod o-w /var/tmp

#### **/var/tmp**

According to the Filesystem Hierarchy Standard (FHS), the /tmp and the `/var/tmp` directories are used to store temporary files. However, the `/var/tmp` directory offers persistence between system reboots. In deployments where persistence in `/var/tmp` is not required, an option could be to bind the `/var/tmp` folder to the `/tmp` folder. This will allow the `/var/tmp` directory to inherit the same mount settings as the `/tmp` directory during the system startup, hence securing the `/var/tmp` directory in the same manner `/tmp` is protected. This could be achieved by adding the following to `/etc/fstab`:

/tmp /var/tmp bind 0 0

#### **/var/crash**

Please note that the `/var/crash` directory is used by the “apport” service for which instructions exist under the “Privacy” section in this document. Every time the “apport” service starts, it resets the permissions of this folder to 777, which reverts the removal of the “other” write permission mentioned previously in this document. This may leave the system at risk and extra consideration needs to be taken if there’s a requirement to keep the “apport” service running.

#### **AppArmor**

Remaining locations, if any, should be added to the deny rules in the AppArmor configuration as shown below. The following command can be used to identify directories where a user can write files when run as that user. Locations on partitions where execution is not possible can be ignored.

find / -type d –writable

Install additional AppArmor profiles and set ones for software installed into enforce mode. The extra profiles can be obtained by executing

sudo apt-get update  sudo apt-get install apparmor-profiles apparmor-utils

Then execute the following to put specific profiles for software that is installed in the recommended configuration into enforce mode:

sudo aa-enforce /etc/apparmor.d/usr.bin.firefox sudo aa-enforce /etc/apparmor.d/usr.sbin.avahi-daemon sudo aa-enforce /etc/apparmor.d/usr.sbin.dnsmasq sudo aa-enforce /etc/apparmor.d/bin.ping sudo aa-enforce /etc/apparmor.d/usr.sbin.rsyslogd

#### **Shell Access**

Also note that ensuring the end user's account does not have sudo access is also important to ensure proper software restriction. More details on this can be found in the User Setup section below.

If shell access is not required it can be disabled. To do this, before creating any users, set the default shell to `/usr/sbin/nologin` in both `/etc/default/useradd` and `/etc/adduser.conf`. This prevents users gaining access to the shell via the console, SSH, or the GUI:

\# Disable shell access. sed -ie '/^SHELL=/ s/=.\*\\+/=\\/usr\\/sbin\\/nologin/' /etc/default/useradd sed -ie '/^DSHELL=/ s/=.\*\\+/=\\/usr\\/sbin\\/nologin/' /etc/adduser.conf

## User setup

The default Ubuntu installer, Ubiquity, will create a user account during install. For the recommended configuration this user account should be considered to be the administrator of the system and not be assigned to the end user of the device. This user account will have sudo access with which it can perform administration tasks.

After install, another user account should be created with the adduser command with default options. This user account should not have sudo access and the password can be provided to the end user of the device. As a further step, this user account can be prevented from executing the su command by running `# dpkg-statoverride --update --add root adm 4750 /bin/su` to change the commands permissions. Similar protection can also be applied to `gksu`, `gksudo`, `pkexec`, `pkcon` and so on, as appropriate.

Remove read access to user home directories and set a more secure default umask:

-   For any existing home directories, use chmod 700.
-   In /etc/adduser.confensure the DIR\_MODE1 setting is set to 0700. This will prevent users on the system from accessing the home directories of other users.
-   In /etc/login.defsensure the line UMASK setting is set to 077. This configures the default permissions of new files to be accessible only by the owner of the file.

\# Protect home directories sed -ie '/^DIR\_MODE=/ s/=\[0-9\]\*\\+/=0700/' /etc/adduser.conf sed -ie '/^UMASK\\s\\+/ s/022/077/' /etc/login.defs

## Privacy

By default Ubuntu has some features enabled which can be a privacy concern. To disable these features take the following steps:

#### **Disable Apport error reporting service**

Ensure that `/etc/default/apport` contains enabled=0

Stop and disable the service by running:

sudo systemctl stop apport.service sudo systemctl disable apport.service sudo systemctl mask apport.service

In addition, the following commands need to be executed as the primary device user (not the administrator):

gsettings set com.ubuntu.update-notifier show-apport-crashes false ubuntu-report -f send no

#### **Disable the Whoopsie service**

Stop and disable the service by running

sudo systemctl stop whoopsie.service sudo systemctl disable whoopsie.service sudo systemctl mask whoopsie.service

#### **Remove Popularity Contest service**

Uninstall the service by running:

sudo apt-get remove -y popularity-contest

So users cannot unset them, these settings should be locked using the following steps:

-   Create a `/etc/dconf/profile/userfile` containing:

user-db:user system-db:local        

Then run

\# dconf update

#### **Disable Connectivity Checker**

The "Connectivity Checker" sends pings to a Canonical server to check if it's online. This is enabled by default and can be turned off in the privacy section of the settings menu.  Alternatively, it can be configured to ping a different server by editing `/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf.`

## VPN

Use a Prime or Foundation Grade IPsec VPN client to provide data-in-transit protection in line with the [Using IPsec to protect data](/guidance/using-ipsec-protect-data) guidance.

Recommended IPsec profile configuration summary:

|     |     |
| --- | --- |
| **ESP** |     |
| Encryption | AES-128 in GCM-128 |
| **IKEv2** |     |
| Encryption | AES-128 in GCM-128 (and optionally CBC\*) |
| Pseudo-random function | HMAC-SHA256-128 |
| Diffie-Hellman group | 256-bit random ECP (RFC5903), Group 19 |
| Authentication | ECDSA-256 with SHA-256 on P-256 curve |

\* If supporting CBC for IKEv2 encryption, the integrity algorithm that should be used is HMAC-SHA256-128.

The post-install script provided with this guide does not attempt to configure a VPN profile because this is dependent on the remote access infrastructure in use; however a sample configuration for StrongSwan is provided below that can be used as a starting point.

The configuration settings should be updated according to the remote access infrastructure in use.

The following StrongSwan default section and VPN definition can be included in the `/etc/ipsec.conf` configuration file (replace `<client_public_certificate.crt>`, `<vpn_server_ip>` and  with suitable values for your environment):

conn %default     keyexchange=ikev2     ike= aes128gcm128-sha256-prfsha256-ecp256!     esp= aes128gcm128-sha256-ecp256!     ikelifetime=24h     lifetime=20m     margintime=3m     keyingtries=%forever     closeaction=restart     dpdaction=restart conn vpn-Prime     leftsourceip=%config     leftid=ubuntu-client1     leftauth=pubkey     leftcert=<client\_public\_certificate.crt>     right=<vpn\_server\_ip>     rightsubnet=0.0.0.0/0     rightid=%any     rightauth=pubkey     auto=start

The file `/etc/ipsec.secrets` should contain the following reference to the certificate:

: ECDSA 

Appropriate certificates for the client device should be generated and deployed to the following locations:

-   CA Public Certificate to `/etc/ipsec.d/cacerts/`
-   Client Public Certificate to `/etc/ipsec.d/certs/`
-   Client Private Key to `/etc/ipsec.d/private/`

The `resolvconf` package can be installed and used to perform automated configuration of DNS settings pushed upon connection\*.

\* Adjustments to the Apparmor policy for StrongSwan’s charon daemon may be required depending on the configuration.

## Firewall

The firewall should be enabled and configured to block incoming connections.

This can be done using the following command:

sudo ufw enable

Restrict outgoing access solely to the VPN server (replace `<vpn_server_ip>`  with the IP of the VPN server):

sudo ufw allow out proto udp to <vpn\_server\_ip> port 500 sudo ufw allow out proto udp to <vpn\_server\_ip> port 4500 sudo ufw default deny outgoing

Normal traffic will be able to flow down the IPsec tunnel once the security association is established (`leftfirewall=yes` must be set in the StrongSwan configuration file).

In order for DHCP on the LAN to function, UDP ports 67 and 68 must be allowed:

sudo ufw allow out from any port 67 to any port 68 proto udp sudo ufw allow out from any port 68 to any port 67 proto udp

Alternatively, for more fine-grained configurations, the `iptables-persistent` package may be used:

sudo apt-get install -y iptables-persistent

The post-install script provided with this guide enables the firewall using ufw with the default policy that allows outgoing connections and denies all incoming connections.

## Other considerations

The following points are in addition to the common organizational considerations, and contain specific issues for Ubuntu deployments.

#### **Application whitelisting**

Ubuntu can be configured such that users cannot run programs from areas where they are permitted to write files. This ensures users can only access programs provisioned by an administrator, although this also prevents users from installing pre-approved software by themselves.

In addition, it is recommended that users do not have access to script interpreters such as Python, Perl, or shells including bash. Access to these can be restricted using a combination of AppArmor, file permissions, and file attributes.

Snap applications run confined under a restricted sandbox that limits access for the applications to only certain areas of the system. However, depending on permissions, apps may be able to access sensitive user information.

#### **Auditing**

Auditing can be enabled and configured via an application called auditd. Rules can be configured which enable auditing of various system events.

This can be installed with the following command:

sudo apt-get install -y auditd

Additional configuration is required in order for auditd to monitor for events. The following examples can be used.

##### **MONITORING CHANGES AND EXECUTION WITHIN /TMP**

In `/etc/audit/rules.d/tmp-monitor.rules`, place the following configuration:

\# Monitor changes and executions within /tmp -w /tmp/ -p wa -k tmp\_write -w /tmp/ -p x -k tmp\_exec

##### **MONITORING ADMINISTRATOR ACCESS TO /HOME DIRECTORIES**

In `/etc/audit/rules.d/admin-home-watch.rules`, place the following configuration:

\# Monitor administrator access to /home directories -a always,exit -F dir=/home/ -F uid=0 -C auid!=obj\_uid -k admin\_user\_home

If files are created or modified within `/etc/audit/rules.d/` then `sudo augenrules` must be run to merge the changes to the main auditd configuration. Once run, restart auditd with  `sudo systemctl restart auditd.service`

Audit events are then recorded in `/var/log/audit/audit.log`. This file can be parsed with various tools, such as aureport. Example usage of this command is `# aureport --input /var/log/audit/audit.log`

To test the above configuration, the following commands will trigger the auditing rules:

touch /tmp/audit\_test\_file chmod u+x /tmp/audit\_test\_file /tmp/audit\_test\_file sudo -i ls /home

#### **External interface protection**

DMA access is possible from interfaces such as FireWire, Thunderbolt, ExpressCard, PCI and PCI Express. DMA attacks can be used to read system memory and extract information such as cryptographic keys and credentials.

It is possible to limit access to DMA features for external interfaces such as FireWire and Thunderbolt via software, which can mitigate this type of attacks for devices that provide such external interfaces.

Deny list the firewire-sbp2 module by adding the following line to the file `/etc/modprobe.d/blacklist.conf`

blacklist firewire-sbp2 

This will disable the SBP2 module, which is responsible for setting up DMA communication via FireWire.

For devices supporting Thunderbolt 2 and above, it is possible to configure a security level. To disable tunnelling of PCIe over Thunderbolt and only allow USB and Display Port protocols configure the security level as dponly. For further information [refer to the kernel documentation](https://www.kernel.org/doc/html/v4.15/admin-guide/thunderbolt.html).