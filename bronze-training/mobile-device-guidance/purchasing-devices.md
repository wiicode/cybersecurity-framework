---
title: Purchasing devices
description: Managing supply chain security when buying smartphones, tablets, laptops and desktop PCs
published: true
date: 2021-06-01T20:11:40.891Z
tags: bronze, bronze-training, mdm
editor: markdown
dateCreated: 2021-03-06T02:27:05.808Z
---

There are many sourcing options available to organizations when buying mobile devices, including buying directly from the device manufacturer, a mobile network operator, or an independent third party.

When buying from any of these sources, you should consider how threat actors within the supply chain may be able to affect the security of your organization, and what steps - if any - you will take to defend against them.

This article will not help you decide *which* devices you should buy. We have separate guidance on [choosing mobile devices](/bronze-training/mobile-device-guidance/choosing-devices) which covers this topic. The goal here is to help you buy devices securely.

# Why manage supply chain security?

Supply chain attacks are rare but not unheard of, and there are sensible steps you can take to minimize your exposure to them. For example, buying devices directly from a reputable vendor is likely to result in a better outcome than sourcing second hand devices from online marketplaces.

If your device is compromised before you have a chance to apply security configurations, it can be very difficult to detect. However, there are some sensible precautions you can take to minimize the likelihood of these attacks succeeding against your organization.

Additionally, most mobile devices now come with options for [zero touch enrolllment](/bronze-training/mobile-device-guidance/infrastructure/network-architectures-for-remote-access) programs such [Windows Autopilot](https://docs.microsoft.com/en-us/windows/deployment/windows-autopilot/windows-autopilot) and [Apple Business Manager](https://help.apple.com/businessmanager/#/apdd344cdd9d). These programs are highly recommended as they both minimize the administrative burden of enrollling new devices, as well as improving the overall security of the enrolllment process, by making unenrollled devices secure in transit and reducing the likelihood of manual error. They may also provide additional benefits. For example, on [iOS](/bronze-training/mobile-device-guidance/platform-guides/ios-and-ipados), devices deployed through [Apple Business Manager](https://help.apple.com/businessmanager/#/apdd344cdd9d) can be prevented from unenrollling from [mobile device management](/gold-policies/mobile-device-management).

Use of these programs will often require you to partner with a device supplier who will automatically register newly purchased devices to your organization's zero touch enrolllment program.

# Preparation for device purchase

When deciding how to buy devices, you should:

-   Consider which [**zero touch enrolllment program(s)**](/bronze-training/mobile-device-guidance/zero-touch-enrolllment) you want to use
-   Look for **manufacturers** who have good [supply chain security](/bronze-training/supply-chain-security)
-   Consider which **supplier(s)** you will buy your devices from. From a security perspective, you may wish to specifically think about:
    -   The security reputation of the device supplier
    -   If they can supply the range of devices your organization has chosen to use
    -   How [up to date](/bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date) the devices they supply will be
    -   How they will handle returns of faulty devices. For example, you may need to return devices which contain corporate data, so make sure you agree a [sanitization process](/bronze-controls/topic-sanitization) with them
    -   If they support your zero-touch enrolllment program(s)
    -   At what point they assign devices to you in their supply chain. Some suppliers may use just-in-time manufacturing for large orders and consequently overseas factories may be aware of the end customer for devices. Other suppliers may use domestic storage facilities and therefore provide a more limited opportunity for supply-chain attacks
-   How any of your **overseas users** might source devices while abroad
-   How you will [**distribute devices**](/bronze-training/mobile-device-guidance/provisioning-and-distributing-devices) to your end users. Depending on configuration, devices may be vulnerable if intercepted while being distributed.

# How to purchase devices

We recommend the following steps for purchasing mobile devices within an organization:

-   Decide [which devices you're going to use](bronze-training/mobile-device-guidance/choosing-devices)
-   Sign up for [zero touch enrolllment](/bronze-training/mobile-device-guidance/zero-touch-enrolllment) for those devices
-   Decide which supplier(s) you will use to buy your devices
-   Discuss the security considerations related to the devices you're going to use with your chosen supplier(s)
-   Deploy and test procedures for enrollling new devices into your [mobile device management](/bronze-training/mobile-device-guidance/choosing-and-using-mobile-device-management-services) infrastructure
-   Develop secure device handling processes for [distributing devices](/bronze-training/mobile-device-guidance/provisioning-and-distributing-devices) to users within your organization
-   Where corporately-owned devices are purchased outside of a trusted supplier, [securely erase](/bronze-training/mobile-device-guidance/erasing-mobile-devices) the devices to reduce the risk from supply chain attacks and enroll them manually
-   Provide [user guidance](/bronze-training/mobile-device-guidance/advising-end-users) which informs users how to complete enrolllment on their new devices, including:
    -   What to expect from the enrolllment process, including screenshots
    -   When and where to enter their corporate credentials
    -   How to [update their new device](/bronze-training/mobile-device-guidance/keeping-devices-and-software-up-to-date) - it will likely be out of date by the time it is enrollled

Using a [zero-touch enrolllment program](/bronze-training/mobile-device-guidance/zero-touch-enrolllment) typically means that the end customer of a device is known when the device is being manufactured - which will likely be overseas, whereas *without* zero-touch enrolllment the devices may not be assigned to the customer until they have reached a local storage and distribution facility. If this causes concerns for your organization then you may wish to *not* use the various zero-touch enrolllment programs.