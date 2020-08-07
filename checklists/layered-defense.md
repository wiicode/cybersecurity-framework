---
title: Checklist: Layered Defense
description: Check the items that you would like to engage.
published: true
date: 2020-08-07T12:57:33.326Z
tags: zta, layered-defense, checklist, nist-sp-800-53, multitiered, risk-management
editor: markdown
---

# Layered Defense

<img src="/article_images/base6428667aaf500fb4c9.png" align=right width="350px">

The current version of Bento Cyber Security Framework suggests small companies focus on a sound **Layered Defense** strategy while being aware for the increasing need to adopt **Zero Trust Architecture**. The recommendation is to build layered defenses around systems and application swhile increasingly demanding that third-party vendors and SaaS providers practice **Zero Trust Architecture** allowing for incremental improvements and adoption.

**Layered Defense** breaks information security into seven key areas and attempts to guide an organization into building a strategy that protects each layer.  Any system, person, or application granted access into a layer is allowed to perform operations in that layer.  *For example, an office worker allowed into a space can use a comptuer avaialble in that space.*

**Zero Trust Architecture** is a thread model where every action requires validation. Going back to the office worker example above, theoretically that employee would need to receive approval every step of the way.  While that may not work on humans, it is quickly becomin the standard for applications/systems/code.

## Covered Areas:
> Understanding scope is a critical step in using the list below effectively.  Materially signficant people, processes, systems, and devices are they key subject. If the entire list feels overwhelming, rethink your scope.
{.is-success}


1. People, Policies, and Procedures
1. Physical Security
1. Perimeter
1. Internal Network
1. Host/Device
1. Application
1. Data


# People, Policies, and Procedures

- [ ] Employees undergo background checks. 
- [ ] Employees must sign NDAs.
- [ ] Employees must sign BYOD policy.
- [ ] Employees must sign Information Security policy.
- [ ] Employees receive onboarding cybersecurity training.
- [ ] Employees receive routine security awareness training.
- [ ] Employees security risk is tested routinely.
- [ ] Employees are allowed to use personal mobile devices at work.
- [ ] Employees are required to enable MFA whenver possible.
- [ ] Password reset requires administrator.
- [ ] Password change is available.
- [ ] Vendors must meet attestation requirements. 
- [ ] Third-party access to data is controlled. 
- [ ] Everyone is familiar with security incident reporting.
- [ ] Incident communication method established.
- [ ] Alarms and monitoring are used to safeguard data. 

#### **Additionally...**
> **Bento Cyber Security Framework** is deveoped specifically to cover people, policies, and procedures. It can be adopted in part or as a whole to meet and exceed all requirements in this category.
{.is-info}

- [ ] Organization has chosen to adopt BCSF.

## Training
The following special topics are essential to every business, big and small. They play a vital role in safeguarding data and systems.  

- [ ] Phishing.
- [ ] Ransomware.
- [ ] Spoofing.
- [ ] USB drives.
- [ ] WiFi.
- [ ] Password sharing.
- [ ] Password change and rotation.
- [ ] MFA.
- [ ] OAUTH.
- [ ] Incident response.
- [ ] Shared Responsibility.
- [ ] Support procedures.
- [ ] Shadow IT.
- [ ] File exchange.

# Physical Security
#### Key Terms:
- **Equipment** collectively refers to servers, network switches, access points, routers/firewalls, and critical hardware.

#### Policy Checklist (**choose your options**) 
- [ ] Employees work in a safe environment. 
- [ ] Inventory of all equipment is maintained. 
- [ ] Visitors cannot access servers or network equipment.
- [ ] Visitor log is maintained. 
- [ ] Visitors are escorted and monitored. 
- [ ] Individual access must be granted.
- [ ] Equipment uses redundant power systems.
- [ ] Emergency power is avaialble. 
- [ ] Unauthorized network devices are detected.
- [ ] Alternate work-site is available for key staff. 
- [ ] Failover site(s) is/are available for mission-critical systems.
- [ ] Data destruction equipment is availble. 
- [ ] Fire protection.
- [ ] Water damage protection. 
- [ ] Temperature and Humidity control.


# Perimeter
#### Key Terms:
- **Equipment** collectively refers to servers, network switches, access points, routers/firewalls, and critical hardware.

#### Policy Checklist (**choose your options**) 

- [ ] Firewalls with advanced-malware and IDS/IPS are deployed.
- [ ] Firewall traffic reports are reviewed periodically.
- [ ] Firewalls nofity of configuration changes and anomalies.
- [ ] Firewall firmware is kept current. 
- [ ] Firewall performance meets requirements. 
- [ ] Firewalls support high-level logging in case of incident.
- [ ] Outbound traffic is under content filtration.
- [ ] Secure browsing is available for remote workers.
- [ ] Remote access requires two or more connection methods. 
- [ ] Firewalls pass URL/traffic to additional processing.
- [ ] Shadow IT applications are discovered and monitored. 

- [ ] Domains are configured to prevent spoofing.
- [ ] DKIM/DMARC is used to validate email.
- [ ] Domain registrations use dedicated email accounts.
- [ ] Domains prevent transfer.
- [ ] Domain registrar access is secured.


- [ ] Email is scanned for phishing and malware.
- [ ] Email (external) is marked accordingly.
- [ ] Signatures are controlled centrally.
- [ ] Signatures have been optimized.


# Internal Network
#### Key Terms:

#### Policy Checklist (**choose your options**) 
- [ ] Guest network is isolated from data network.
- [ ] Guests are isolated from each-other.
- [ ] WiFi access points are out of reach. 
- [ ] WiFi network traffic is encrypted.
- [ ] WiFi networks require at least a password.
- [ ] Guests require additional login.
- [ ] Segmentation technology exists to isolate desired systems.


# Host/Device

#### Key Terms:
> "**Systems**" is used to collectively represent devices, computers, and hosts.
{.is-info}

- **Device** refers to a computer, mobile phone, tablet,  smartwatch, network printer, or an IoT device.
- **Computer** refers to any computer or laptop, regarless of operating system.
- **Host** refers to virtual machines or cloud instnces. 


#### Policy Checklist (**choose your options**) 

- [ ] Default passwords are immediately changed. 
- [ ] Firmware is kept current.
- [ ] Bring Your Own Device (BYOD) is restricted (see BYOD recommendations).
- [ ] All devices purchased through existing vendor agreeements.
- [ ] Device enrollment and provisioning program is used to provision new devices.
- [ ] Each computer has company managed anti-malware (see anti-malware recommendations). 
- [ ] Anti-malware uses behavior monitoring in addition to scanning.
- [ ] Devices are part of a Mobile Device Management deployment.
- [ ] Devices receive all operating system updates (ref: patch-management) 

- [ ] Computers have remote management and monitoring.
- [ ] Computers have employee monitoring solution.
- [ ] Devices connect to office WiFi using certificate/RADIUS instead of a password.
- [ ] Devices have the ability to be wiped when lost or stolen. 
- [ ] Computers prohibit administrative actions by users.
- [ ] Devices have encrypted hard drives.
- [ ] Devices restrict file sharing.
- [ ] Devices restrict personal cloud accounts.
- [ ] Devices are audited automatically for compliance.
- [ ] Devices are audited and reviewed manually for compliance. 
- [ ] Systems require multi-factor authentication to login.
- [ ] Systems have configured and immutable timeout/logoff settings.
- [ ] System transfer or "dump" events are detected. 


# Applications
#### Key Terms:

#### Policy Checklist:

##### Internal
- [ ] Default passwords are changed. 
- [ ] Generic accounts are removed. 
- [ ] Business Continuity plan covers critical apps.
- [ ] Maintenance and support is current on all critical apps.
- [ ] Application updates (ref: patch-management).
- [ ] Security vulnerabilities are patched. 

##### SaaS
- [ ] Default passwords are changed.
- [ ] Business Continuity plan considers SaaS.
- [ ] All authentication events are tracked and monitored. 
- [ ] MFA is enforced where available. 
- [ ] Zero Trust Access is in use.
- [ ] No account sharing is allowed.
- [ ] Suspicious activity is detected.
- [ ] Audit trails are required. 
- [ ] Data protection policies are documented and reviewed.
- [ ] Backups/export automation is in place. 

# Data

- [ ] Data is classified.
- [ ] Data has established owners.  
- [ ] Personally identifiable information is treated with care.
- [ ] Data Loss Protection policies are in place.
- [ ] Insider threat policies are in place. 
- [ ] Security access control is established by job role.
- [ ] Least-privilige principles are used to assign access.
- [ ] Unique passwords dominate.
- [ ] Secrets storage sharing procedures are established.
- [ ] Privacy first methodology.
- [ ] Controls exist to prevent unauthorized storage of data.




