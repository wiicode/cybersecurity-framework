---
title: Managing web browser security
description: Advice for IT Admins on the management of security settings for web browsers
published: true
date: 2021-06-02T02:34:56.474Z
tags: guidance, bronze, bronze-training, mdm
editor: markdown
dateCreated: 2021-03-06T02:40:36.791Z
---

> BCSF is focused on providing high-level guidance will help you develop an approach to secure web browsing that works for your organization.
{.is-info}


---

## Why manage web browser security?

Web browsers are widely used within organizations to access a variety of online content, including corporate data held within enterprise web services and intranet sites. This broad access to sensitive data on one hand and exposure to public internet sites on the other, makes browsers an attractive target for attackers. Moreover, browsers are highly configurable and extensible, so it's important to ensure that they use a configuration which minimizes your organization's exposure to risk.

The good news is that the most popular browsers are largely *secure by default. S*o, your job as an enterprise admin is to *prevent them from becoming insecure*. This entails a combination of keeping them up to date and managing a small number of settings. If plugins or extensions are used, you'll also need to manage their configuration.

---

## Preparation for browser management

In many respects, browsers should be managed in much the same way as any other [third party application.](/bronze-training/mobile-device-guidance/using-third-party-applications) This includes using your approvals process to choose a web browser, ensuring a legitimate version of the browser is installed with secure app distribution, and ensuring updates are installed promptly.

However, there are some additional factors:

### **Choosing a web browser**

Firstly, you will need to decide on which web browser or browsers to use.

When deciding, you should consider:

-   **Compatibility:** Whilst much less of a concern than it used to be, some of your corporate tools may only support a subset of browsers. However, if one of your web applications requires an old, unsupported browser and you can't migrate away from the application, then you should investigate ways of using a separate browser for accessing that web application and using a modern, secure web browser for everything else.
-   **Performance**, including impact on battery life for mobile devices.
-   **Security features:** Most popular web browsers have similar security features, but you may want to look specifically for:  
    -   Integration with safe browsing list services, so that known malicious or fraudulent sites are blocked (including known phishing sites)
    -   Sandboxing, including virtualization-based security (e.g. Windows Defender Application Guard)
-   **Platform support** for the devices and operating systems you use. If you make use of multiple operating systems in your organization, you may want to use a cross-platform browser to simplify management. Equally, if you're using obsolete platforms, you may want to use a more up-to-date third-party browser which supports the platform.
-   **Enterprise management** capabilities, Including integration into the mobile device management service(s) you use.
-   **Support dates:** Some browser developers support their products for longer, or have extended support versions. If you intend on having the same browser for a while, make sure you choose one that will be supported throughout the period.

### **Managing web browsers**

We advise that you investigate the security of the browsers you use on your devices and configure settings to mitigate risks in the following areas.

-   Enterprise management of the following features:
    -   **Updates:** Users may [not have the most up-to-date](/bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date) version of the browser. If your browser is not updated, it may have known vulnerabilities that can be exploited by an attacker, resulting in the device becoming compromised. You may wish to consider a method to monitor which version of the browser your users have on their device.
    -   **Malware protection:** Browsers are one of your first lines of defense against malware. Depending on your platform configuration, users may be able to download and run malicious executables. You should consider how this can be mitigated either with the use of [anti-virus software](/bronze-training/mobile-device-guidance/antivirus-and-other-security-software) configured to scan downloads, or by [enforcing an application whitelisting policy.](/bronze-training/mobile-device-guidance/using-third-party-applications)
    -   **Critical security features** such as preventing users bypassing certificate warnings.
    -   **Sign-in to cloud synchronisation accounts:** like [built-in cloud accounts on mobile devices](/bronze-training/mobile-device-guidance/using-built-in-cloud-services), third-party browsers often also have cloud accounts that users can sign in to. If you are concerned about risks from synchronisation of work data to personal accounts you might want to limit the ability to sign into those accounts from your devices' browsers.
    -   **Browser plug-ins,** such as Java, Flash and Silverlight are one of the top ways that users devices are compromised. They are also rarely needed on the modern web, so you should think about how necessary they are to your organization.
    -   **Third-party extensions:** Browsers have many third party plugins/extensions available, but should you allow their use? A common example is an *advertisement blocker* extension. While such software may be useful, you should consider the following security risks:
        -   As with any third-party software, you should consider the likelihood and impact should the application be malicious or vulnerable. This is a similar approach to considering which [third-party applications](/bronze-training/mobile-device-guidance/using-third-party-applications) to allow on your devices.
        -   Extensions typically have permissions to read or change the data on any websites a user visits. This could include sensitive or personal data.
        -   Extensions will increase the potential attack surface of your web browser, as this software may also contain security vulnerabilities. You should think about how you might keep users' extensions up to date.
-   Many users will want to use their browser's built-in password manager to save passwords and credentials, making it easy to use strong authentication strategies. For more information see broader guidance on the use of password managers.
-   Configuration of privacy-related settings including cookies, *do not track,* and pop-up blocking might be useful to your organization, but are not required from a security perspective.
-   Developer features such as the JavaScript Console might be useful to some users but can be used to facilitate social engineering attacks. You might want to disable them for users who don't need them.
-   Some organizations may have a legal or policy need to configure users' browsers to enable traffic inspection. If this applies to you, you might want to also configure trusted certificates and/or proxy settings for the browser.

---

## How to manage browsers

- [Start managing Chrome Browser *As an IT admin for a business or school, you can deploy Chrome Browser to users across Microsoft® Windows®, Apple® Mac®, and Linux computers. You can then manage 200+ policies that govern people's use of Chrome, such as the apps and extensions they can use, data security and privacy, their browsing experience, and more.*](https://support.google.com/chrome/a/answer/188446?hl=en)
- [Configure Microsoft Edge using Mobile Device Management *Microsoft Edge enhances and extends the browser experience. It runs on Windows, macOS, iOS and Android devices.*](https://docs.microsoft.com/en-us/deployedge/configure-edge-with-mdm)
{.links-list}

When choosing and using a web browser, based on the considerations above, we recommend the following steps:

-   Choose which browser or browsers meet your organizational needs using the considerations above. This may be the one built in to your operating system (e.g. Edge or Safari), or a third-party product installed separately.
-   Review the [third-party applications guidance](/bronze-training/mobile-device-guidance/using-third-party-applications), and apply the advice about reviewing and distributing third-party software to your browser deployment
-   Review any enterprise management guidance from the developers for the browser(s) that you have chosen to use.
-   Develop the settings and policies that you deem important enough to enforce on your users' devices. Specifically, develop a policy around the installation of third-party extensions on your browser.
-   Where possible, use [Mobile Device Management (MDM)](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) to enforce those policies.
-   Ensure [automatic updates](/bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date) are turned on for both the browser and it's extensions.
-   You may wish to include some security tips for browsing the web securely within your [user guidance](/bronze-training/mobile-device-guidance/advising-end-users). These should include 'do *not browse the web when logged in as an administrator*', and *'install updates when prompted*'.

We recommend **not** disabling crucial usability features like JavaScript and Password Auto-fill. Whilst there have been security vulnerabilities in these features in the past, using the web reliably and securely can be very difficult without them enabled. 

---

## More information

Enterprise management of browsers documentation:

| **Web browser** | **Additional information** |
| --- | --- |
| Google Chrome | [Chrome Browser: Manage your browsers](https://cloud.google.com/chrome-enterprise/browser-management/) |
| Mozilla Firefox | [Deploying Firefox in an enterprise environment](https://developer.mozilla.org/en-US/docs/Mozilla/Firefox/Enterprise_deployment) |
| Apple Safari | [Managing Devices & Corporate Data on iOS](https://www.apple.com/business/docs/resources/Managing_Devices_and_Corporate_Data_on_iOS.pdf)<br><br>(Safari management is integrated with iOS and macOS management) |
| Microsoft Edge | [Microsoft Edge: Microsoft Edge Group Policy configuration options](https://docs.microsoft.com/en-us/microsoft-edge/deploy/) |