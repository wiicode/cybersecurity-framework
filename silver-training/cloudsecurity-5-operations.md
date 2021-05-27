---
title: 5. Operational security
description: The service needs to be operated and managed securely in order to impede, detect or prevent attacks. Good operational security should not require complex, bureaucratic, time consuming or expensive processes.
published: true
date: 2021-05-27T20:52:28.368Z
tags: silver, cloud-security-principles, silver-training
editor: markdown
dateCreated: 2021-02-22T01:36:44.187Z
---

# 5\. Operational security

The service needs to be operated and managed securely in order to impede, detect or prevent attacks. Good operational security should not require complex, bureaucratic, time consuming or expensive processes.

## There are four elements to consider:

-   [Configuration and change management](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/operational-security#config) – you should ensure that changes to the system have been properly tested and authorised. Changes should not unexpectedly alter security properties
-   [Vulnerability management](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/operational-security#vulnerability) – you should identify and mitigate security issues in constituent components
-   [Protective monitoring](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/operational-security#protective) – you should put measures in place to detect attacks and unauthorised activity on the service
-   [Incident management](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/operational-security#incident) – ensure you can respond to incidents and recover a secure, available service

## 5.1 Configuration and change management

You should have an accurate picture of the assets which make up the service, along with their configurations and dependencies.

Changes which could affect the security of the service should be identified and managed. Unauthorised changes should be detected.

Where change is not effectively managed, security vulnerabilities may be unwittingly introduced to a service. And even where there *is* awareness of the vulnerability, it may not be fully mitigated.

### **Goals**

You should have confidence that:

-   The status, location and configuration of service components (both hardware and software) are tracked throughout their lifetime.
-   Changes to the service are assessed for potential security impact. Then managed and tracked through to completion.

### **Implementation - Configuration and change management**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Assertion that the goals are met | The service provider asserts the above goals are met. | As with all service provider assertions, you need to decide whether you are content with the level of confidence this gives you. |
| Conformance with a recognised standard | A number of standards include controls which cover the need for configuration and change management processes:   <br>[CSA CCM v3.0](https://www.ncsc.gov.uk/collection/cloud-security/standards-and-definitions)  <br>[ISO/IEC 27001](https://www.ncsc.gov.uk/collection/cloud-security/standards-and-definitions) | Good change and configuration management processes reduce (but do not eliminate) the chance of vulnerabilities being introduced to the configuration of a service.<br><br>Standards differ in terms of the level of detail applied, and those referenced cover the need for configuration and change management, rather than validation of the process. It is worth checking the scope of any certification to verify that configuration and change management processes were covered as part of the assessment.<br><br>Without good governance of the service (see [Principle 4](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/governance-framework)) it is likely that change and configuration management practices will be ineffective. |

### **Additional notes - Prioritising changes**

It’s important to have effective change management processes in place. But you must also realise that until the process is complete, your service remains vulnerable. Consequently, changes must be prioritised according to severity of risk.

## 5.2 Vulnerability management

Service providers should have a management processes in place to identify, triage and mitigate vulnerabilities. Services which don’t, will quickly become vulnerable to attack using publicly known methods and tools. See our guide on [vulnerability management](https://www.ncsc.gov.uk/guidance/vulnerability-management) for more detail.

### **Goals**

You should have confidence that:

-   Potential new threats, vulnerabilities or exploitation techniques which could affect your service are assessed and corrective action is taken
-   Relevant sources of information relating to threat, vulnerability and exploitation techniques are monitored by the service provider
-   The severity of threats and vulnerabilities is considered within the context of the service and this information is used to prioritise the implementation of mitigations.
-   Using a suitable change management process, known vulnerabilities are tracked until mitigations have been deployed
-   You know service provider timescales for implementing mitigations and are happy with them

### **Implementation - Vulnerability management**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Assertion that the goals are met | The service provider asserts the above goals are met. | As with all service provider assertions, you need to decide whether you are content with the level of confidence this gives you. |
| Conformance with a recognised standard | A number of standards are appropriate to support vulnerability management. These have their own certification mechanisms:ISO/IEC 30111:2013   <br>[CSA CCM v3.0](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/governance-framework)  <br>[ISO/IEC 27001](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/governance-framework) | No vulnerability management process can defend against unknown (‘zero day’) vulnerabilities.<br><br>None of the standards referenced explicitly set out acceptable timescales for mitigation, so it is worth considering your requirements.<br><br>As a minimum, we advise that you seek services which support patching or vulnerability management within the timescales set out below. |

### **Additional notes – Mitigation timescales**

Exploits for known vulnerabilities are frequently available, across the internet, within hours of release. *Organisations which mitigate and patch vulnerabilities in their services quickly have smaller windows of vulnerability.*

You should know whether your service provider patches vulnerabilities within acceptable timescales.

If there is evidence to suggest that a vulnerability is being actively exploited in the wild, service providers will need to put mitigations in place **immediately**.

If there is no evidence that a vulnerability is being actively exploited, the following timescales should be considered minimum good practice:

-   ‘Critical’ patches should be deployed within hours
-   ‘Important’ patches should be deployed within 2 weeks of a patch becoming available
-   ‘Other’ patches deployed within 8 weeks of a patch becoming available

‘Critical’, ‘Important’ and ‘Other’ are aligned to the following common vulnerability scoring systems:

-   National Vulnerability Database Vulnerability Severity ratings: ‘High’, ‘Medium’ and ‘Low’ respectively (these in turn are aligned to CVSS scores as set out by NIST)
-   Microsoft’s Security Bulletin Severity Rating System ratings: ‘Critical’, ‘Important’ and the two remaining levels (‘Moderate’ and ‘Low’) respectively.

## 5.3 Protective Monitoring

A service which does not effectively monitor for attack, misuse and malfunction will be unlikely to detect attacks (both successful and unsuccessful). As a result, it will be unable to quickly respond to potential compromises of your environments and data.

### **Goals**

You should have confidence that:

-   The service generates adequate audit events to support effective identification of suspicious activity
-   These events are analysed to identify potential compromises or inappropriate use of your service
-   The service provider takes prompt and appropriate action to address incidents

### **Implementation – Protective monitoring**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Assertion that the goals are met | The service provider asserts the above goals are met. | As with all service provider assertions, you need to decide whether you are content with the level of confidence this gives you. |
| Conformance with a recognised standard | A number of standards include controls which cover the need for effective protective monitoring processes:  <br>[CSA CCM v3.0](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/governance-framework)  <br>[ISO/IEC 27001](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/governance-framework) | Standards differ in terms of the level of detail applied, and those referenced cover the need for effective protective monitoring, rather than validation of the controls in place. It is worth checking the scope of any certification to verify that protective monitoring controls were covered as part of the assessment.<br><br>It is also advisable to check that any certification was performed by an independent and expert party. |

### **Additional notes – Monitoring and analysis**

Services which do not collect relevant accounting and audit information are unlikely to detect and respond quickly to attacks, or attempted attacks.

And where attacks are detected through other mechanisms, it will be difficult to identify the extent, duration and severity of compromise if relevant audit data is not available.

Services which collect accounting and audit information *but do not have effective analysis* of that information are *equally unlikely to detect and respond quickly to attacks*. There’s no way of knowing whether unexamined data will be sufficient to support an investigation or prosecution, should one occur.

### **Additional notes – Monitoring responsibility**

In IaaS and PaaS services users run their applications or software on top of the service. Providers are *unlikely* to offer protective monitoring for these applications, *unless* the consumer and service provider have worked together to design an appropriate solution.

In these scenarios, it’s typically you, the service user, who will be responsible (and often best placed) to identify attacks against your applications or software. For this you will need your own monitoring systems.

## 5.4 Incident management

Unless carefully pre-planned incident management processes are in place, poor decisions are likely to be made when incidents do occur, potentially exacerbating the overall impact on users.

These processes needn’t be complex or require large amounts of description, but good incident management will minimise the impact to users of security, reliability and environmental issues with a service.

### **Goals**

You should have confidence that:

-   Incident management processes are in place for the service and are actively deployed in response to security incidents
-   Pre-defined processes are in place for responding to common types of incident and attack
-   A defined process and contact route exists for reporting of security incidents by consumers and external entities
-   Security incidents of relevance to you will be reported in acceptable timescales and formats

### **Implementation – Incident management**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Assertion that the goals are met | The service provider asserts the above goalsare met. | As with all service provider assertions, you need to decide whether you are content with the level of confidence this gives you. |
| Conformance with a recognised standard | A number of standards include the need for incident management in line with the stated goals. These have their own supporting certification processes:   <br>ISO/IEC 27035-1:2016  <br>[CSA CCM v3.0](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/governance-framework)  <br>[ISO/IEC 27001](https://www.ncsc.gov.uk/collection/cloud-security/implementing-the-cloud-security-principles/governance-framework) | The standards referenced differ in terms of the level of detail applied. Some cover incident management controls in detail, whereas others simply require an incident management process to exist. It is worth checking the scope of any certification to verify what was actually assessed.<br><br>It is also advisable to check that any certification was performed by an independent and expert party. |

### **Additional notes – Significant attacks and high availability**

Anyone publishing services which may be subjected to significant attacks (in terms of volume or technical capability) should use providers who can demonstrate robust, well tested and rehearsed incident management procedures.

Denial of service attacks against public facing infrastructure by ‘hacktivist’ groups or serious criminals for financial gain can be a particularly demanding test of incident response processes, especially for users with a high availability requirement.