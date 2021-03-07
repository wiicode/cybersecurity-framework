---
title: Mobile Device Guidance
description: Help for organizations, from choosing and purchasing devices to the advice you give the end users.
published: true
date: 2021-03-07T22:45:44.949Z
tags: guidance, bronze, bronze-training, mdm, rmm, msp
editor: markdown
dateCreated: 2021-03-07T22:44:35.128Z
---

> Securing mobile devices is an essential part of guarding your organisation against a variety of threats, many of which herald from the internet.
{.is-info}

Mobile devices come in many different shapes and sizes: smartphones, tablets, laptops and even desktop PCs. When thinking about how to secure these devices, a number of questions come to mind, such as:

- Which devices should I buy?
- How should I configure these devices?
- What security software should I load onto them?

# Structure of the Mobile Device Guidance
Taken as a whole, our Mobile Device Guidance covers the full range of concerns, from choosing and purchasing devices, right through to advising end users. Each of these questions has it's own page, so you can easily find the advice you need for a particular problem. The questions have been arranged under four headings, representing the major areas of concern:

- Getting ready
- Policies and settings
- Managing deployed devices
- Infrastructure
- Devices and platforms

# Managed Services Providers
Shared responsibility between your organizationa and a managed services provider is the most effective method for implementing a robust Mobile Device Management program. While it is possible to offload all MDM resposibility to a provider, most organizations find this method is not as effective as the shared model.  There are numerous capabilities such as Apple Busines Manager, Windows AutoPilot, Azure AD Join, Self-Service, and many others that depend on your organization owning MDM infrastructure.  With shared responsibility

- **Mobile Device Management (MDM)** including enrollment certificates is owned and generated from your company's MDM platform such as Meraki System Manager, Windows Intune, Addigy, JAMF, etc. 
- **Remote Management and Monitoring Plaform (RMM)**, patch management, and monitoring is performed by the MSP usng their automation technology.

There is a grey area, however as many RMM technologies inch towards integrating or providing MDM services as well. While some have built sensible capabilities for managed service providers, all have had to make compromises and back-paddle capabilities with privacy and security changes from Apple and Microsoft.  Generally speaking, a hybrid approach can be used but should be limited to ad-hock/small-scale (few) devices. 

# Audience
These guides are aimed primarily at business users, with a focus on those deploying or managing large IT estates. However, the advice holds good for all users, and all operating systems. So if you only have a few devices to look after this guidance can still be very useful.