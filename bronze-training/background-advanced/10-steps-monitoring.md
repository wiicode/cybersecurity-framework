---
title: Monitoring
description: System monitoring provides a capability that aims to detect actual or attempted attacks on systems and business services.
published: true
date: 2021-05-29T18:37:56.109Z
tags: bronze, bronze-training, 10-steps, sourced, security-operations
editor: markdown
dateCreated: 2021-02-21T16:05:27.930Z
---

> System monitoring provides a capability that aims to detect actual or attempted attacks on systems and business services. Good monitoring is essential in order to effectively respond to attacks. In addition, monitoring allows you to ensure that systems are being used appropriately in accordance with organizational policies. Monitoring is often a key capability needed to comply with legal or regulatory requirements.
{.is-info}

# Summary
System monitoring provides a capability that aims to detect actual or attempted attacks on systems and business services. Good monitoring is essential in order to effectively respond to attacks. In addition, monitoring allows you to ensure that systems are being used appropriately in accordance with organizational policies. Monitoring is often a key capability needed to comply with legal or regulatory requirements.

# What is the risk?
Monitoring provides the means to assess how systems are being used and whether they are being attacked. Without the ability to monitor your systems you may not be able to:

- Detect attacks: Either originating from outside the organization or attacks as a result of deliberate or accidental user activity. Attacks may be directly targeted against technical infrastructure or against the services being run. Attacks can also seek to take advantage of legitimate business services, for example by using stolen credentials to defraud payment services.
- React to attacks: An effective response to an attack depends upon first being aware than an attack has happened or is taking place. A swift response is essential to stop the attack, and to respond and minimize the impact or damage caused.
- Account for activity: You should have a complete understanding of how systems, services and information are being used by users. Failure to monitor systems and their use could lead to attacks going unnoticed and/or non-compliance with legal or regulatory requirements.

# How can the risk be managed?
**Establish a monitoring strategy and supporting policies**: Develop and implement a monitoring strategy based on business need and an assessment of risk. The strategy should include both technical and transactional monitoring as appropriate. The incident management plan as well as knowledge of previous security incidents should inform the approach.

**Monitor all systems**: Ensure that all networks, systems and services are included in the monitoring strategy. This may include the use of the use of network, host based and wireless Intrusion Detection Systems (IDS). These solutions should provide both signature-based capabilities to detect known attacks, and heuristic capabilities to detect unusual system behavior.

**Monitor network traffic**: Inbound and outbound traffic traversing network boundaries should be monitored to identify unusual activity or trends that could indicate attacks. Unusual network traffic (such as connections from unexpected IP ranges overseas) or large data transfers should automatically generate security alerts with prompt investigation.

**Monitor user activity**: The monitoring capability should have the ability to identify the unauthorized or accidental misuse of systems or data. Critically, it should be able to tie specific users to suspicious activity. Take care to ensure that all user monitoring complies with all legal or regulatory constraints.

**Fine-tune monitoring systems**: Ensure that monitoring systems are tuned appropriately to only collect events and generate alerts that are relevant to your needs. Inappropriate collection of monitoring information and generation of alerts can mask the detection of real attacks as well as be costly in terms of data storage and investigatory resources required.

**Establish a centralized collection and analysis capability**: Develop and deploy a centralized capability that can collect and analyze information and alerts from across the organization. Much of this should be automated due to the volume of data involved, enabling analysts to concentrate on anomalies or high priority alerts. Ensure that the solution architecture does not itself provide an opportunity for attackers to bypass normal network security and access controls.

**Provide resilient and synchronized timing**: Ensure that the monitoring and analysis of audit logs is supported by a centralized and synchronized timing source that is used across the entire organization to support incident response and investigation.

**Align the incident management policies**: Ensure that policies and processes are in place to appropriately manage and respond to incidents detected by monitoring solutions.

**Conduct a 'lessons learned' review**: Ensure that processes are in place to test monitoring capabilities, learn from security incidents and improve the efficiency of the monitoring capability.

# What are the benefits?

Good logging practices provides the ability to understand, trace and react to system and security events

Security monitoring provides insight into systems, and allows for the active detection of threats and potential security incidents

Security monitoring introduces an additional layer of defense to systems

Actively monitoring systems affords the opportunity to react to early signs of compromise, meaning organizations can respond effectively

# What should you do?
## Understand your objectives for logging and monitoring
- When designing a monitoring solution, it should be proportionate to the context of the system, the threat that your organization faces and the resources available to you. Doing this will build a picture, which will enable you to determine what is actually proportionate. This picture will help you decide the level of monitoring that is appropriate to your system. There is no one-size-fits-all solution, the case might be that simply be collecting logs in case of a security incident is the right fit for you.
- Conversely, your organization might be subject to frequent cyber attacks, or may need to address risks with monitoring controls, which may require a security operations center (SOC) with the ability to detect and respond to advanced attacks.
- At all levels, the main priority should be the ability to respond to incidents and to do this, logs are required. The BCSF’s Introduction to logging for security purposes guidance provides a good place to start and will help organizations devise an approach to logging that will help answer the most critical questions during an incident.
- The BCSF’s ‘What exactly should we be logging’ blog post introduces the MITRE ATT&CK framework and how it can be used to help define monitoring strategies. It also touches on outcome based and threat modelling approaches that can be used
## Make sure your logs are available for analysis when you need them
- Understand where your logs are stored and ensure you have the appropriate access to be able to search through them.
- Ensure logs are held for long enough to be able to answer the questions you'll be asked during an incident. It can be months before incidents are detected so BCSF recommends storing your most important logs for at least 6 months. The amount of time you keep log data may vary for each source depending on things like cost and availability of storage, and the volume and usefulness of different data types. Plan for storage to roll-over, avoiding disks filling and the service failing.
- Consider which logs you want to draw into a centralized location for analysis across data sets. For some data sets it may be suitable to just call out to those log stores as required. If sending logs to a central log service, use transport encryption and one-way flow control where appropriate.
- Develop a method for ensuring that logs are still being captured as expected. This could be an automated alert when log messages stop arriving centrally, or an alert for when a periodic test event isn’t captured (when it should be).
- Protect your logs from tampering so that is it hard for an attacker to hide their tracks and you can be confident that they accurately represent what has happened.
## Use your logs to generate useful insights
- Setting security policies that define appropriate use and configuring systems based on business need (combined with an assessment of risk) will enable you to develop a monitoring service that analyzes logs to verify that those policies are being enforced or followed as you expect. This is also useful in ensuring that all user activity complies with relevant legal or regulatory constraints.
- Use your understanding of the context of your system to create detection alerts based on the expected threats. This helps ensure the alerts generated will be relevant to your organization's needs and that the action is relevant to inform the risks.
- Consider where you need to be monitoring, this should include on your network, devices and cloud services, as applicable. Monitoring solutions can provide both signature-based capabilities to detect known attacks, and heuristic capabilities to detect unusual system behavior.
## Develop an incident response plan
- Test your ability to detect incidents with exercising, and incorporate any lessons learnt from actual incidents into your monitoring solutions. Many organizations only realize their logging and monitoring systems are broken or insufficient when an actual incident occurs. Active exercising can help avoid you being caught out and improve your systems.
- Ensure your organization's incident management plan is aligned with your logging and monitoring strategy so you already have a plan to deal with any incident that can be detected by your monitoring systems. This plan can then be exercised to ensure that any issues with communication and capability are highlighted and resolved, and practice will enable the team to react more confidently to any real incidents.
## Stay informed
- Make use of threat intelligence. 