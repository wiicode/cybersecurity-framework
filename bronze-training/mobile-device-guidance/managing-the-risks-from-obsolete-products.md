---
title: Obsolete products
description: Reducing the risks from using out of date smartphones, tablets, laptops, desktop PCs, appliances or software applications.
published: true
date: 2021-06-02T13:25:03.747Z
tags: guidance, bronze, mdm
editor: markdown
dateCreated: 2021-03-06T02:51:11.711Z
---

All software, including device operating systems, will eventually become out of date, after which point - ideally - it should not be used.

This guidance provides advice to organisations who are unable to fully migrate away from obsolete products before the end of their support dates.

### **NOTE**

This guidance does *not* provide a risk-free way of continuing to use obsolete products, but will help to reduce the risks of doing so.

The only fully effective way to mitigate this risk is to migrate away from the obsolete product.

---

## Why manage the risk from obsolete products?

Using obsolete products compounds two related problems:

1.  The product will no longer receive [security updates](https://www.ncsc.gov.uk/collection/mobile-device-guidance/keeping-devices-and-software-up-to-date) from its developers, increasing the likelihood that exploitable vulnerabilities will become known by attackers.
2.  The latest security mitigations are not present in older products, increasing the impact of vulnerabilities, making exploitation more likely to succeed, and detection of any exploitation more difficult.

In combination, these issues mean that high-impact security incidents become more likely to occur. This will include malware exploiting remotely-accessible vulnerabilities, which can cause catastrophic impacts across an entire organisation.

When a product is no longer supported by its developer, there are limits on the measures that will be effective in protecting against new threats. Over time, new vulnerabilities will be discovered that can be exploited by relatively low-skilled attackers.

No combination of the protective measures described below will remove the risks posed by vulnerable software remaining in active use. You should work in parallel to migrate away from the obsolete products.

---

## Preparation for the protection of obsolete products

When products become obsolete, you'll need to trade off the risks from continuing to use them with the costs of replacing or upgrading them.

Naturally, the NCSC would recommend upgrading instead of continuing at risk, but we recognise that this is not always feasible. If you decide to continue at risk in the short term, you should revisit this decision regularly, account for new threats and vulnerabilities that might have emerged, and reassess your risk appetite.

If you decide it's time to upgrade your applications, where possible consider moving to [Software-as-a-Service products](https://www.ncsc.gov.uk/collection/saas-security). Taking advantage of [cloud products](https://www.ncsc.gov.uk/collection/cloud-security) means much of the security risk from outdated software is managed for you. If you decide to accept the risk of using obsolete systems and software, the following recommendations will help you minimise that risk.

### **Choosing new hardware**

When [choosing new hardware or licensing new software](https://www.ncsc.gov.uk/collection/mobile-device-guidance/choosing-devices), always consider the support lifetime of the product. This will help you ensure that your systems remain supported for as long as possible.

---

## How to manage the risk from obsolete products

The following steps apply to any software which is approaching the end of its support period.

Apply short-term mitigations

Weaknesses found in unsupported products will remain unpatched and will be exploitable by relatively low skilled attackers.

There are two ways to reduce the risk:

-   **Reduce the** ***likelihood*** **of compromise** by preventing the devices from accessing untrusted content (effectively making it hard for malicious content to reach the device and exploit it)
-   **Reduce the** ***impact*** **of compromise** by preventing access to sensitive data or services from vulnerable devices (so even if the devices are compromised, the damage will be minimised)

You should implement a combination of these two approaches. In the long-term, moving away from obsolete systems should be the goal.

---

## Measures to reduce the likelihood of compromise

Exploits can only be successful if attackers are able to reach the vulnerable product. If untrusted data is prevented from reaching it, then exploitation via this route isn't possible. To achieve this, there are several steps you can take.

**Limit attackers' access to obsolete products**

Routes by which malicious data could reach obsolete products include email, web browsing, file shares, network ports, and removable media. We recommend that these routes are disabled as far as possible, possibly including the use of [network air gaps](https://en.wikipedia.org/wiki/Air_gap_(networking)). Data flows to obsolete servers should be carefully considered and reduced, wherever possible using a discrete network firewall.

Data and files sourced from the Internet should be treated as untrusted even if originating from a known third party. Data retrieved from enterprise storage services should also be treated as untrusted if its source was originally external.

#### **Prevent access to untrusted services from obsolete devices**

Implement technical controls to prevent access to external, untrusted services, from obsolete devices. This should include preventing access to external email and browsing of the Internet via a native web browser (indirect access e.g. via a thin client is possible). These controls will not be effective if they are not technically enforced.

If you cannot fully block access to untrusted services, you may be able to slightly reduce the risk of compromise by ensuring that access to externa content is either disabled, or requires a manual action. This is particularly true for active content or media, such as [macros](https://www.ncsc.gov.uk/guidance/macro-security-for-microsoft-office) and [browser plugins](https://www.ncsc.gov.uk/collection/mobile-device-guidance/managing-web-browser-security). This can reduce the risk of 'drive-by download' attacks.

There is no way to completely mitigate the exposure of an unpatched web browser to malicious web content, beyond blocking access to the Internet entirely. However, the risk can be lowered by blocking access to rich web content and running scripts. A gateway which scans all incoming data for malicious content is another sensible precaution.

#### **Prevent access to removable media**

Access to removable media should be prevented, as it can be used to transport untrusted content. It is also important to consider devices such as smartphones and tablets can be used to transfer media to obsolete devices, and, if compromised, can launch attacks against devices they are connected to.

Access to removable media and any connected devices can be controlled through numerous third-party products and through some [firmware configuration options](https://www.ncsc.gov.uk/collection/mobile-device-guidance/managing-mobile-device-firmware).

#### **Convert obsolete client devices to thin clients**

If your smartphones, tablets, laptops or desktop PCs cannot be upgraded to the latest software, you may want to convert them into "thin client" devices and use them only as an access mechanism to trusted internal services, such as remote desktop environments. By using obsolete systems as a thin client, it is possible to avoid the need for the device to directly process untrusted content.

Web browsing, for example, can be performed via a remote desktop environment running a patched modern browser. Business productivity applications can be accessed in a similar way. This allows the remote session to run supported, patched software, even if the client device used to access services cannot. The remote system should be configured to prevent transfer of data back to the client device through features such as clipboard sharing and file transfers.

This mitigation can be strengthened by ensuring that obsolete Windows client devices are in a separate Active Directory forest from the remote desktop service and other enterprise services.

#### **Remove unneeded services from obsolete servers**

Obsolete servers should be checked to ensure that the services they offer are minimised. Those services which are not essential to the business function of the server should be disabled.

Wherever possible, migrate required services from obsolete servers to modern, supported servers or cloud services. Obsolete servers should not be used to provide remote app services, or other remote desktop facilities. Nor should they be relied upon where there is any expectation of separation between users or where the remote desktop solution is being used to provide security separation, within a network.

---

## Apply mitigations to reduce the impact of compromise

An unpatched end user device that is directly exposed to malicious content is likely to end up compromised. The impact of compromise can be reduced by controlling access to enterprise services hosting sensitive data and improving the ability to detect attacks.

#### **Re-image/wipe devices regularly to attempt to remove any resident malware**

Obsolete platforms will be more likely to contain malware from a previous compromise, so they should be [regularly erased and re-imaged to remove any malware that may be present](https://www.ncsc.gov.uk/collection/mobile-device-guidance/erasing-mobile-devices). However, it is important to remember that this will only temporarily sanitise the device. The vulnerability which the malware used to gain a presence on the platform will continue to provide an attack route after the device has been re-imaged. The device will still be vulnerable to attack.

#### **Treat obsolete systems as unmanaged or untrusted**

Where obsolete devices continue to be used within an organisation, we recommend that they be treated as untrusted and given constrained access. Obsolete servers should be treated by the wider enterprise as being untrusted, and data and services they offer should be handled accordingly. This will likely be similar to [adopting a bring your own device (BYOD) approach.](https://www.ncsc.gov.uk/collection/mobile-device-guidance/bring-your-own-device)

#### **Network zoning**

By zoning the network it is possible to reduce the ability for malware to spread laterally through an enterprise. The traffic flows between zones should be well defined, providing the ability to block and prevent unauthorised communications, such as those made by malware trying to reach its command and control systems. You cannot assume that the software firewall on a compromised device will continue to work effectively.

#### **Improve protective monitoring, logging and auditing of obsolete components**

When using obsolete products, it is especially important to [ensure an effective and proactive protective monitoring capability](https://www.ncsc.gov.uk/collection/mobile-device-guidance/logging-and-protective-monitoring) is in place. Many organisations often have the ability to record security events but do not proactively alert or take action based upon these events.

#### **Anti-malware and intrusion detection products**

Products such as [antivirus, host-based and network-based intrusion detection systems](https://www.ncsc.gov.uk/collection/mobile-device-guidance/antivirus-and-other-security-software) can be used and will continue to offer some benefits in detecting malicious code. Their effectiveness may be reduced as the products may not be updated when running on an unsupported operating system and signatures may not be tuned to detect attacks targeted at obsolete systems.

#### **Incident response**

Timely response to security critical events becomes increasingly important if obsolete and vulnerable software is present within the enterprise environment. Actions to contain and eradicate the compromise should be swift to try and reduce any compromise spreading.

---

## Understand third-party connections

If third party organisations use their own devices within your environment, or to connect in to it, you should understand whether they are running obsolete and vulnerable software - and to take action to address such risks. This could be the situation, for example, where you have suppliers managing services within your enterprise environment.

### **Specific mitigations for Microsoft products**

Microsoft publish ‘end of support’ dates for products such as Windows and Office. You should plan for these dates and make effective plans for migration to alternative, supported products.

### **Office file types**

If you have a requirement to keep an obsolete version of Office installed on a small number of devices, consider applying controls to prevent the file types that Office can open being transferred through gateways. Alternatively, using online productivity suites such as Office 365 in the browser, and configuring email attachments to automatically open online, can lower the risk of exploitation.

### **Deploy EMET**

Some of the older Microsoft platforms still have a version of the [Enhanced Mitigation Experience Toolkit (EMET)](https://support.microsoft.com/en-gb/help/2458544/the-enhanced-mitigation-experience-toolkit) available. EMET makes it harder for some vulnerabilities in the platform to be exploited, but will not completely prevent attacks.

### **Consider a Custom Support Agreement (CSA)**

The CSA is a paid for service available to customers who have a Microsoft Premier Support agreement. Under such an agreement, Microsoft will supply both Critical and Important security updates (Important updates are available at an additional fee).

The types of updates that will be available via the CSA will be similar to those that would be available to a product in ‘extended support’, but will need to be installed manually as they will not come through Windows Update.

Once a product goes into extended support there is no guarantee that all future security vulnerabilities will be addressed and so it should not be seen as a long term alternative to full migration to a modern supported operating system.