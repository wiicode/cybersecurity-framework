---
title: Security operations centre (SOC) buyers guide
description: Guidance is for organisations that are considering procuring a Security Operations Centre (SOC) from a third party.
published: true
date: 2021-06-24T18:15:07.005Z
tags: silver, sourced, security-operations, silver-training
editor: markdown
dateCreated: 2021-02-22T00:42:28.037Z
---

## Introduction

This guidance is for organisations that are considering procuring a Security Operations Centre (SOC) from a third party. It is equally applicable for those seeking to establish their own in-house SOC. It summarises the core functions of a SOC, and includes the different deployment options available, the SOC lifecycle, and other high-level considerations.

---

## What does a SOC do?

The key aims of a SOC are:

-   **to detect and respond to threats**, keeping the information held on systems and networks secure
-   **to increase resilience** by learning about the changing threat landscape (both malicious and non-malicious, internal and external)
-   **to identify and address negligent or criminal behaviours**
-   **to derive business intelligence about user behaviours** in order to shape and prioritise the development of technologies

---

## Why might you need a SOC?

Some examples of why you might need a SOC include:

-   you are running an online service for the public
-   you host a number of sensitive databases which are accessed by staff on your premises, by remote staff, or by customers or partners
-   you have several different office locations and a unified security function delivers cost savings
-   you share large quantities of sensitive data with other organisations
-   you require a single point of visibility for all your threats

---

## What type of SOC is best for you?

SOCs come in a variety of flavours and can cover the entire incident management process. This can include:

-   integration, management and review of traffic feeds
-   protective monitoring
-   initial triage and analysis
-   vulnerability management
-   alerting and response
-   incident management
-   root cause analysis
-   patching & remediation
-   correlation management, Security Information and Event Management (SIEM) tuning
-   continuous improvement
-   key management

The functions that **your** organisation require will depend on a number of factors, including but not limited to:

-   your budget
-   whether or not you choose a third party supplier
-   your willingness to share your information feeds with a commercial supplier
-   your own willingness/capability to perform forensic investigations
-   how you manage business continuity
-   whether you need an on-premise or an off-premise service (or a hybrid of the two)
-   if you outsource your SOC, it will likely be multi-tenanted. This means that any threat intelligence generated from your data feeds will be used to improve the service delivered to other customers. Consider the sensitivity of your data, your requirements and whether you'd be comfortable with a multi-tenanting arrangement (noting the higher costs of a dedicated service and the potential benefits to you derived from being a co-tenant).
-   how well you know the range of threats posed to your organisation
-   whether your requirements are unique - a generic service may suffice if your requirements are typical of other organisations

---

## Top tips before you start

When defining your SOC requirements, we recommend you consider the following:

-   **Logs are not an end in themselves**. It’s tempting to think they are, but it’s the way they are *correlated* that provides the power of a SOC. Logs must be collected, aggregated, analysed, stored and minimised. Most importantly, they must be available to your SOC at all times.
-   **SIEM is not a panacea**. Be wary of any supplier that tells you that security information and event management (SIEM) is a panacea for all your analytic needs. Good SOC analysts don’t develop anything in the SIEM until they've proved an idea using scripts and logs first. A good supplier will have a content development checklist and a standard process for proposing, justifying and implementing rulesets in your SIEM.
-   **Don’t assume your business wants to hear what the SOC finds**. Your SOC has detected something; who will care and what you do next? Work back from the end of the incident and verify you can achieve each stage before levying a requirement upon your SOC. Ensure the action you wish to take is legal and covered by internal policy.
-   **Review regularly which SIEM content is providing benefit**, and use stats to justify its existence. Your SOC is an invaluable source of business intelligence and management information.
-   **Establish the basics**. Don't bother with advanced concepts until you're confident you have the basics covered. Expensive and complex SIEM tools are all the rage, often the temptation is to jump from zero to 'behavioural analytics' using an expensive SIEM that nobody understands properly. Well trained and quality staff are crucial.

---

## A secure SOC protects itself

An SOC exists to help manage your risks more effectively, which means the SOC itself must be protected adequately. A SOC must have mechanisms, processes and procedures to ensure that it can protect itself against threats comparative to those being faced by its customers. This includes protecting the service itself, and also the data within it.

The SOC provider **must** be able to demonstrate that they understand the architecture of their monitoring system. A supplier ought to be able to provide documentation to include:

-   an overview of the system elements, such as perimeter, host and network, and specific application-based agents
-   clearly annotated network diagrams, which demonstrate a comprehensive understanding of how the SOC architecture is designed and managed
-   related technical documentation which demonstrates how architectural components are used to actively monitor the environment
-   mechanisms for managing the control of privileged user access
-   the monitoring and control of privileged user access, demonstrating an understanding of who has access and their activity
-   which parts of the architecture allow for automation, and which parts require analysts
-   descriptions of what the sensors within the monitoring service actually do

---

## Feeding your SOC

Where will your information feeds come from? What inputs will you feed into your SOC? It depends on the kind of services you are running, but it might include:

-   data from the organisation's [vulnerability management](https://www.ncsc.gov.uk/guidance/vulnerability-management)
-   records of high-value database commands
-   requests made to your web servers
-   records of high-value privileged administrator commands
-   outputs from web content filters
-   logs from the mail gateway
-   logs of DNS requests made by your internal systems and servers
-   logs from your federated authentication system
-   if you use cloud, you may need to incorporate any alerting provided by the cloud service into your SOC, e.g. breaches of Data Loss Prevention policy

A fuller picture of the logs and other outputs which can feed your SOC are shown below (this can also be downloaded at the bottom of the page). Discuss with your supplier how you will determine which inputs are required to deliver the best service to your business.

![](https://www.ncsc.gov.uk/static-assets/images/NCSC_Soc_Feeds.JPG)

---

## The SOC lifecycle

A good SOC needs you to work with it. It's not uncommon for SOC suppliers to send their customers alerts, but to never receive a reply. Obviously, an organisation should not derive any security from simply knowing that a SOC is in place.

A successful SOC will undergo some transformations during its lifetime, from requirements capture at start-up, through to effective operations. To adapt to the ever-changing threat landscape and to the introduction of new technologies, a SOC must learn from what it finds. As a result, false positives will be reduced, the reporting process will become smoother, and high impact threats will be detected sooner. A good contract with a SOC provider will not concentrate solely on initial requirements but will incorporate the ability of the SOC to evolve and adapt.

### **Start-up and requirements capture**

In many cases, the service you are offered will be multi-tenanted, with other organisations benefiting from the threat intelligence generated from your feeds and vice versa. Provided you can gain assurance from your supplier that:

-   sensitive information about your business is kept in the strictest of confidence
-   your data is subject to appropriate levels of logical separation within the provider’s environment

\- you may judge the benefits to outweigh the risks.

The starting point for negotiations may be the default service offered by a supplier. It is normal for organisations new to SOC to think that their business is somehow unique, but do not underestimate the benefits which a default service can deliver. Listen to what is provided by default and use your technical experts to analyse and identify any adaptations needed in order to meet your own business requirements. This is the cheapest and easiest approach to take.

Ensure your prospective provider understands your business. This involves a significant commitment of your time and expertise. Make sure you’re conveying to your provider:

-   your business objectives
-   your operational environment
-   your risk appetite and incident reporting thresholds
-   how long you need data retained

In return, your provider needs you to understand:

-   its core offering, so you understand what you need over and above that offering
-   that it depends on you to tell it when and to whom to send alerts
-   what third parties it's reliant on to deliver its service to you

Together the ‘supplier’ and the ‘authority’ need to agree:

-   how SOC-related tasks will be divided; well-defined governance and ownership is essential to agree responsibilities
-   business continuity priorities/business impacts
-   escalation matrix/incident workflows
-   establishment of SLAs and KPIs, to set levels of expectation
-   rules and responsibilities around data sharing (including MI)
-   the boundary interfaces and inter-relationships with any network operations or incident response capabilities within your organisation

### **Operations and data sharing**

During operation of your SOC service, your supplier is processing and analysing security monitoring data and applying your policy, compliance and business rules to identify and verify security incidents. Should an incident occur, the supplier’s job is to respond according to the agreements in place with you, working to return the service to normal operations. As a SOC enters the operational phase, your resourcing overheads will diminish, but expect a number of false positives to occur while the supplier learns to understand the way your business operates.

For example, you may have a small number staff who are constantly on the move. For these staff, a logon from an IP geolocated in Dubai (from a user who logged on six hours earlier from an IP in the UK) may at first *seem* suspicious, but is in fact not. Over time, a good supplier will learn what constitutes genuinely anomalous behaviour. Until then, false positives can be a good opportunity to test the reporting chain.

### **Continuous improvement**

SOC providers need to appreciate the different operational environments and business objectives of their customers. They should be able to adapt their offering in order to meet any changes in these requirements, in order to deliver a service which can continue to meet a customer’s needs. This involves learning from past experiences to deliver an improving service that strikes the right balance between cost of operations, security and customer fatigue.

Suppliers should generate comprehensive and meaningful management information to help customers understand the patterns in incidents, near misses, root cause and methods of resolution. Retaining the right data, at the right level of detail, for the appropriate periods of time is therefore an important requirement. Note some data may be subject to UK statutory laws on retention.

---

## Tools and technologies

The tools employed as part of a SOC capability are key to ensuring that a SOC provider is able to actively monitor and detect the latest threats. New SOC technologies are constantly emerging, so it is unlikely that the technologies in your SOC will remain the same over the duration of a typical contract. The tools deployed by the SOC should be properly commissioned and managed appropriately. The toolset should not only take into account technological developments in the marketplace, but more importantly changes in customer requirements. If the cost of your SOC services increases in the wake of a new tool, it will be prudent to ask your supplier to:

-   explain the business and technical reasons for implementing new technologies
-   demonstrate that the tool(s) is configured in line with developer’s recommendations
-   ensure SOC staff are trained in the use of the tools
-   ensure SOC have a strategic understanding of how the tools contribute to the customers’ overall SOC needs