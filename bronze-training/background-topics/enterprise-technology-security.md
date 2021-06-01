---
title: Approaching enterprise technology with cyber security in mind
description: How organisations can approach enterprise technology in order to deter cyber attacks.
published: true
date: 2021-06-01T18:29:32.564Z
tags: bronze, bronze-training, sourced, security-operations, favorite
editor: markdown
dateCreated: 2021-02-21T22:09:10.059Z
---

The majority of cyber attacks an organization faces will be ineffective if enterprise technology is deployed, operated, and maintained with cyber security in mind. This guidance explains how organizations should approach enterprise technology in order to deter cyber attacks.

By 'enterprise technology', we mean the IT used to run your organization. This includes:

- the devices staff have in their hands
- the systems and services that hold and process information
- the networks which connect them together
- the way in which these are operated

The recommendations here are suitable for the vast majority of information. You may further enhance the security recommendations, but doing so will add to the cost whilst adding little benefit. If you believe this guidance is not sufficient to protect your data, please contact us so we might improve future versions of this guidance.

# Principles for cyber secure enterprise technology
In developing this guidance for enterprise, the following principles are assumed:

{.grid-list}
- Enterprise technology requires sensible and pragmatic security which supports the users of the technology. Security which interferes in the way that users expect to interact with technology is bad security.
- The decisions you make about securing enterprise technology will be based on risk management, validated and enforced by the right governance arrangements.
- Any recommendations made will require adjustment to meet particular circumstances, and so should be treated as a sensible starting point, not as a mandatory checklist.
- A percentage of devices will be lost or stolen during their deployed life; someone who has unauthorized access to such a device should not be able to access information stored on it, or the systems the device can access.
- Products and services will have vulnerabilities discovered during their lifecycle; your approach should ensure that a single vulnerability is not catastrophic to your organization's security.
- Your approach will not provide perfect protection against zero-day attacks, but it will avoid a zero-day causing too much harm, with vulnerabilities mitigated as swiftly as possible.
- A percentage of websites and applications are deliberately designed to trick users, or to harm their devices which interact with them. Expecting users to know in advance which applications, attachments, links, and services are unsafe is unlikely to succeed. The approach will minimize the chances that such events can occur, and minimize the harm if they do.
- Untrusted networks will be used more frequently. As we increasingly use the internet and mobile network to connect to services, it's no longer useful to consider the office network as a 'physically secured' link . The approach will protect sensitive data as it travels between devices and services, and protect devices and services against network-based attacks.
- Cyber security mitigations will not be infallible; occasionally attackers will be successful. Taking steps to ensure that you can detect when cyber attacks have occurred (and knowing how to quickly recover from them) will pay dividends in the long run.
{.links-list}

# End user computing
The first step in securing your enterprise technology is selecting, configuring, and operating the devices that your staff will use every day.

Different platforms, (such as Microsoft Windows or Apple iOS) have different security properties, and the way they are configured will also effect the security they provide. Our End User Device guidance will help you understand the security properties of a wide range of devices, and help you make informed decisions. It also includes recommended configurations for you to adopt as a starting point when you're first deploying devices.

As well as the devices your organization provides, you may want allow staff to use their own devices to access some of your enterprise services. This is known as 'Bring Your Own Device' (BYOD). There are some extra things to consider if you're thinking about adopting BYOD, and these are covered in our BYOD guidance.

# Networking
The function of networking is to connect devices to services. As a general principle, the network should not be trusted. The network should be treated as an untrusted bearer.

To keep sensitive information protected, encryption should be used between devices, and the applications on them, and the services which we are accessing. There are situations in which trusting the network can be useful (such as linking together legacy services within a data centre). Use physical and personnel security controls to provide this protection.

- If you need to protect all data traveling between two points on a network (such as between a remote working device and your enterprise network, or between two sites) we recommend implementing IPsec, using our guidance on Network Encryption.
- If you need to protect one data stream, such as from an application to a service, then Transport Layer Security (TLS) is more appropriate (please refer to our TLS configuration guidance).
- Peer-to-peer enterprise applications may use TLS, but some applications — such as Voice over IP (VOIP) — are often better met with tailored solutions such as MIKEY SAKKE for real-time media encryption.

An over-reliance on a particular network service (or provider) means there's a higher risk of disruption from service problems, some of which can be caused by cyber security incidents.

# Enterprise services
Enterprise services are the things which power your enterprise IT; they're the places where your data is stored and made available to your users for processing and action. We use the term to cover common services such as email, document storage, file stores, communication services, as well as line-of-business services which are tailored to your organization's needs (such as internal web applications, databases, and workflow systems).

There is a choice between hosting these services in-house (on your own premises), or in a commercial cloud environment, or a hybrid model spanning both. Security will be one of many considerations when deciding where to run such services.

Running services in-house means you can take responsibility for all aspects of their security. This can be desirable, but depends on having the necessary skills resources available. Using a competent cloud service provider can mean you benefit from their scale and security knowledge. When selecting cloud services, we recommend evaluating them against our cloud security principles, to ensure you understand how they will help you protect your information.

# Security operations
There's no point investing in securing your devices, networks, and services, if you don't maintain and enhance their cyber security throughout the period that they are deployed.

It's important not to treat security as a one-off event, but instead as something that needs continuous investment. Security operations describes the activities required to keep an organization's enterprise technology protected against the latest threats, as well as on-going monitoring and management of security incidents as they occur.

The most important activity to prevent common cyber attacks is to keep your enterprise technology up to date, and to apply the latest security patches as they're made available. Our guidance on patching can help you understand the importance of this, and how to prioritize patching.

Security operations can be run in-house or be provided by a third party. Our security operations guidance can help you make this decision, and describes the activities that an effective operations team should carry out.

