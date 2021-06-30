---
title: 13. Audit information for users
description: You should be provided with the audit records needed to monitor access to your service and the data held within it.
published: true
date: 2021-06-30T18:52:02.874Z
tags: silver, cloud-security-principles, silver training
editor: markdown
dateCreated: 2021-06-30T18:47:06.415Z
---

# 13\. Audit information for users

You should be provided with the audit records needed to monitor access to your service and the data held within it. The type of audit information available to you will have a direct impact on your ability to detect and respond to inappropriate or malicious activity within reasonable timescales.

## Goals

You should be:

-   aware of the audit information that will be provided to you, how and when it will be made available, the format of the data, and the retention period associated with it
-   confident that the audit information available will meet your needs for investigating misuse or incidents

## **Implementation - Audit information for users**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| None | The service provider does not offer audit information to users. | Failure to provide audit information can prevent you from identifying misuse of your service and data.<br><br>You should consider whether the inability to determine how, when or where a service is accessed could result in legal or regulatory issues. |
| Data made available by negotiation | The service provider offers users limited audit information as a result of negotiation. | You should consider whether the audit data provided is adequate to support your needs.<br><br>The provision of audit information does not in itself give you any protection. The information will require analysis to uncover evidence of compromise or misuse. |
| Data made available | The service provider makes specific audit data available to users. The timetable, method, format and retention period of the data is specified. | You should consider whether the audit data provided is adequate to support your needs.<br><br>The provision of audit information does not in itself give you any protection. For this, the information will require analysis to uncover evidence of compromise or misuse. |

## **Additional notes - Usability of audit data**

Audit data is of limited value unless used as part of an effective [monitoring regime](/guidance/introduction-logging-security-purposes). Good monitoring requires a thorough understanding of the expected service usage.

For IaaS and PaaS services, the service provider or a third party may offer value-add protective monitoring services for workloads you've deployed. When considering these services, think about what support the service provider or third party would need to deliver an insightful service.

Consider whether you require audit records to be held to specific standards, or be suitable for specific circumstances.