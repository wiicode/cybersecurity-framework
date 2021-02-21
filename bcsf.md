---
title: Bento Cyber Security Framework
description: BCSF provides guidance for organizations responsible for vitally important services and activities.
published: true
date: 2021-02-21T02:36:41.481Z
tags: bcsf, bronze, framework
editor: markdown
dateCreated: 2021-02-21T02:36:41.481Z
---

# Cyber & safety introduction
An introduction to cyber-related risks to safety, how to manage them, and resources related to cyber and safety provided by the NCSC.

## General introduction
Increasingly, computerised systems are performing vital safety-related functions designed to protect human lives. For example, such systems are controlling the safe operation of industrial sites processing and storing dangerous chemicals, and play a key role in the safety of aviation, rail transportation etc.

Computerised safety systems could, potentially, be adversely affected by a cyber incident – either as a side-effect of a compromise not intended by the perpetrators to affect safety, or as a result of highly targeted cyber attack, specifically aimed at reducing the effectiveness of safety mechanisms. This is not just a theoretical possibility. There has been at least one well-documented example of a safety-related targeted cyber incident.

Where the possible impact of a safety-related incident is sufficiently serious, certain industrial sites are designated Critical National Infrastructure (CNI). In some cases, where organisations are subject to specific regulation aimed at protecting public safety such as the Control Of Major Accidents & Hazards regulation (COMAH), there may be a regulatory requirement to manage cyber-related risks to safety. Consequently, maintenance of public safety is an essential function for some organisations, and this includes managing the cyber-related risks to safety

## Managing cyber-related risks to safety
The successful management of cyber-related risks to safety is based on the same fundamental principles that underpin effective cyber risk management more generally. However, an integrated approach is needed which combines the established good practices of both the security and safety communities. There are recognised challenges associated with achieving such an integrated approach, and NCSC is actively working with others to develop additional guidance. For example, at the CYBERUK 2019 conference there was an entire stream devoted to safety and cyber security, and work is currently under way with the IET to produce a Code of Practice for cyber security and safety.

## Resources related to cyber and safety provided by the NCSC
The NCSC has developed some resources that organisations managing cyber-related risks to public safety are likely to find useful. These are:

- a set of cyber security and resilience principles for managing cyber-related risks to safety
- a collection of supporting guidance
- a Cyber Assessment Framework (CAF) incorporating indicators of good practice

Collectively, these resources are known as the NCSC CAF collection and can be found on the website by following the link below. Please note that the use of CAF collection extends beyond organisations managing cyber-related risks to public safety. For that reason, the terminology of the CAF collection is intended to be quite general and cover more than cyber-related safety risks. Specifically, in the CAF collection:

- ‘essential function’ may refer to maintenance of public safety or to another important activity carried out by an organisation (eg. operation of an essential service in the context of the NIS Directive etc).
- ‘organisation responsible for an essential function’ may refer to an organisation responsible for the maintenance of public safety, or to another type of organisation (eg. an organisation designated as an Operator of Essential Services in the context of the NIS Directive, or an organisation identified as forming part of the UK Critical National Infrastructure, etc).

Please note that, as used in the CAF collection, the term ‘essential function’ may or may not refer to an activity subject to cyber regulation.

If your organisation is subject to regulation in relation to the maintenance of public safety you should consult your regulator concerning the use of the NCSC CAF collection in relation to meeting regulatory requirements.

# A.1 Governance
Putting in place the policies and processes which govern your organisation’s approach to the security of network and information systems.

## Principle
*The organisation has appropriate management policies and processes in place to govern its approach to the security of network and information systems.*

## Description
Effective security of network and information systems should be driven by organisational management and corresponding policies and practices. There should be clear governance structures in place with well-defined lines of responsibility and accountability for the security of network and information systems.

Senior management should clearly articulate unacceptable impacts to the business (often called risk appetite), which should take into account the organisation’s role in the operation of essential functions, so decision makers at all levels can make informed decisions about risk without constantly referring decisions up the governance chain.

There should be an individual(s) who holds overall responsibility and is accountable for security. This individual is empowered and accountable for decisions regarding how essential functions are protected. For small organisations, the governance structure can be very simple.

## Guidance
Your organisation's approach to security governance needs to be an appropriate fit for your organisation. Good security governance is integrated with your business's usual decision making structures and processes.

Decisions about risk can be made at all levels of your organisation when delegated effectively to people with the right security, business and technical knowledge, skills and experience. Clear lines of communication are also necessary.

## Risk management standards
Following a standardised risk management approach can help in achieving good cyber security governance. There are many such standards to choose from. Some of the most well-known are:

### ISO 27001
*An Information Security Management System can aid governance of cyber security risk*

An Information Security Management System (ISMS) is a set of policies, procedures, and roles designed to ensure cyber security risks are identified and managed. Traditionally an ISMS is considered to be an information risk management system, however it can be used to manage cyber security risks to essential functions.

A properly scoped and implemented ISMS can help your organisation to meet requirements your organisation might have to protect essential functions by putting in place policies, procedures, and roles which govern the organisational approach to managing cyber security risks to those functions.. 

ISO 27001 is one of many standards you can use to implement an ISMS. If your organisation is intending to use ISO 27001, you should consider which elements will help achieve your organisational objectives - full compliance and certification may be unnecessary. 

Your organisation must incorporate into the ISMS any relevant external requirements, for example direction from a regulator.  You should also set appropriate cyber security requirements for your supply chain to ensure their support in achieving yourcyber security and resilience objectives (see A4 Supply Chain Security).

### IEC 62443-2-1:2010
An industrial automation and control system (IACS) cyber security management system (CSMS) that is relevant to organisations responsible for essential functions in some particular sectors.

The CSMS defined in IEC 62443-2-1 is designed to build on ISO 27001 & 27002 for IACS environments, with the aim of aligning cyber security risk management with existing safety risk management practices. A management system framework is provided as a baseline, which organisations are encouraged to tailor for their own context.

# A.2 Risk management
Identification, assessment and understanding of security risks. And the establishment of an overall organisational approach to risk management.

## Principle
*The organisation takes appropriate steps to identify, assess and understand security risks to the network and information systems supporting the operation of essential functions. This includes an overall organisational approach to risk management.*

## Description
There is no single blueprint for cyber security and therefore organisations need to take steps to determine security risks that could affect the operation of essential functions and take measures to appropriately manage those risks.

Threats can come from many sources, in and outside the organisation. A good understanding of the threat landscape and the vulnerabilities that may be exploited is essential to effectively identify and manage risks. Such information may come from sources including NCSC, information exchanges relevant to the organisation's sector, and reputable government, commercial, and open sources, all of which can inform the organisation's own risk assessment process. Organisations may contribute to the understanding of threats and vulnerabilities in their sector by participating in relevant information exchanges and liaising with authorities as appropriate.

There should be a systematic process in place to ensure that identified risks are managed and the organisation has confidence mitigations are working effectively. Confidence can be gained through, for example, product assurance, monitoring, vulnerability testing, auditing and supply chain security.

## Guidance
Our Risk Management guidance aims to help you to choose an approach that's right for your organisation.Organisations responsible for essential functions are likely to benefit from a combination of a system-based approach, which looks at the interactions between components of the function, and a component-driven analysis, which considers the threats, vulnerabilities, and impacts relevant to particular critical components.

Your organisation should choose a method or framework for managing risk that fits with the organisation's business and technology needs. 

Whichever approach you choose, the scope of your programme must include all systems relevant to the operation of essential functions. Simply following the minimum requirements of a standard or applying blanket controls across the organisation is unlikely to adequately manage risks to critical systems.

Where industrial control and automation systems are in scope of the essential function, you should keep in mind that controls suitable for managing risks on the corporate IT network may be inappropriate or damaging in an operational technology environment. These systems will likely require a more tailored approach, and some frameworks and standards address specific concerns relating to such systems.

# A.3 Asset management
Determining and understanding all systems and/or services required to maintain or support essential functions.

## Principle
*Everything required to deliver, maintain or support networks and information systems  necessary for the operation of essential functions is determined and understood. This includes data, people and systems, as well as any supporting infrastructure (such as power or cooling).*

## Description
In order to manage security risks to the network and information systems supporting essential functions, organisations require a clear understanding of service dependencies. This understanding might include physical assets, software, data, essential staff and utilities. These should all be clearly identified and recorded so that it is possible to understand what things are important to the delivery of the essential function and why.

## Guidance
Whichever risk management method your organisation uses, asset management will play a key role as you cannot effectively manage risks without understanding what assets are part of the essential function. Your asset management regime should consider all relevant assets, and dependencies between them. Dependencies may be identified between assets under your organisation's control (including IT and OT domains), elements of the supply chain (including power), and key staff who are critical to operations. Assets in an operational technology environment may need a more tailored approach than the corporate IT assets.

For asset management to be effective, up to date knowledge of your assets must be maintained throughout their lifecycle.

### ISO 27001/2
*Asset management is part of an ISO 27001 ISMS, but management of critical assets may require a tailored approach*

An Information Security Management System (ISMS) is a set of policies, procedures, and roles designed to ensure cyber security risks are identified and managed. Traditionally an ISMS is considered to be an information risk management system, however it can be used to manage cyber security risks to essential functions.

If your organisation is using an ISMS as a tool for compliance with cyber regulation, you must ensure the scope includes all systems relevant to the operation of the essential function covered by the regulation. Asset management is a key part of an ISMS, although critical services may need more attention than the minimum requirements of the standard. Further guidance is detailed in ISO 27002.

### ISO 55001 - Asset Management

This standard aligns with ISO 27001 and can be used in conjunction with it or independent of it. It outlines requirements for a generic asset management system. An organisation following this standard as a tool for compliance with cyber regulation must ensure the scope encompasses all the relevant systems. Section 4.2 covers needs and expectations of stakeholders, which must include any requirements from regulators..

### ITIL

ITIL best practice recommends a staged approach to IT asset management. You may find this useful for improving management of your IT assets, but must keep in mind that there may be assets and dependencies beyond the corporate IT domain as outlined above.

# A.4 Supply chain
Understanding and managing the security risks to networks and information systems which arise from dependencies on external suppliers.

## Principle
*The organisation understands and manages security risks to networks and information systems supporting the operation  of essential functions that arise as a result of dependencies on external suppliers. This includes ensuring that appropriate measures are employed where third party services are used.*

## Description
If an organisation relies on third parties (such as outsourced or cloud based technology services) it remains accountable for the protection of any essential function. This means that there should be confidence that all relevant security requirements are met regardless of whether the owning organisation or a third party operates the function.

For many organisations, it will make good sense to use third party technology services. Where these are used, it is important that contractual agreements provide provisions for the protection of things upon which the essential function depends.

## Guidance
Organsations responsible for essential functions need to ensure that when third party suppliers are used, all relevant security requirements are met. This means that a number of specific supply chain related security considerations should be addressed where relevant to the provision of the essential function. This might include:

- Ensuring the protection of data shared with a third party. This includes protecting data from actions such as unauthorised access, modification, or deletion that may cause an adverse impact on any essential functions (see Principle B3).
- Effective specification of the security properties of products or services procured from a third party that are important for the protection of the essential function. This should include the security requirements derived from the rest of these Principles.
- Ensure that any network connections or data sharing with third parties do not introduce unmanaged vulnerabilities that have the potential to affect the security of the essential function.
- Confidence that third party suppliers are trustworthy such that malicious attempts to subvert the security of products or systems that could affect the essential function are managed.

# B.1 Service protection policies and processes
Defining and communicating appropriate organisational policies and processes to secure systems and data that support the operation of essential functions.

## Principle
*The organisation defines, implements, communicates and enforces appropriate policies and processes that direct its overall approach to securing systems and data that support the operation of essential functions.*

## Description
The organisation’s approach to securing network and information systems that support essential functions should be defined in a set of comprehensive security policies with associated processes. It is essential that these policies and processes are more than just a paper exercise and steps must be taken to ensure that the policies and processes are well described, communicated and effectively implemented.

Policies and processes should be written with the intended recipient community in mind. For example, the message or direction communicated to IT staff will be different from that communicated to senior managers. There should be mechanisms in place to validate the implementation and effectiveness of policies and processes where these are relied upon for the security of the essential function. Such mechanisms should also support an organisational ability to enforce compliance with policies and processes when necessary.

To be effective, cyber security and resilience policies and processes need to be realistic, i.e. based on a clear understanding of the way people act and make decisions in the workplace, particularly in relation to security. If they are developed without this understanding there is a significant risk that service protection policies and processes will be routinely circumvented as people use work-arounds and shortcuts to achieve their work objectives.

## Guidance
### Developing policies and processes
The policies and processes needed by an organisation depend upon its function and should integrate with the organisation’s approach to governance and risk management. Organisations responsible for essential functions should have a range of policies and processes, including:

- An organisational security or service protection policy: endorsed by senior management, this high-level policy should include the organisation’s overarching approach to governing security and managing risks, the organisation’s aims and intents for security and what is of key concern.
- Supporting policies and processes: contextual lower-level definitions controlling, directing and communicating organisational security practice.
- Compliance policies and processes for sector regulations, standards, etc.: specific policies and processes appropriate to the compliance regime; these may be defined by the regulation, standard, etc. For example, to comply with ISO/IEC 27001, organisations should have in place certain security policies and procedures relevant to what the organisation does, how it does it, and what their ISO/IEC 27001 information security management system covers (see ISO/IEC 27002 for detail).

### People-focussed practical approach
There is a growing body of evidence that people have a limit to the effort available to comply with security and there are recognisable costs to security behaviours. Exceeding human limits of compliance is likely to result in non-compliance, such as workarounds or circumventing controls.

Organisations should understand how people work with the systems and data they use to support the operation of essential functions to ensure security and people work together. Discover how people and security really need to work together to achieve the organisation’s objectives and desired productivity. Engage in and continue security conversations with staff, partners, contractors, any other system users, security and technical experts, plus organisational representatives such as HR, change and communications experts. These conversations can be enabled through, for example:

- personal interviews,
- staff security attitude surveys,
- promoting security reporting culture without fear of blame or recrimination,
- engaging people in the design of processes and policies

Use your understanding of how people work to develop practical security policies and processes and, wherever possible, reduce the human effort required to comply.

There are many resources available intended to help organisations decide what their cyber security and resilience protection policies should look like; for example, SANS provide various [information security policy templates](https://www.sans.org/information-security-policy/).

### Personnel security
You should ensure that individuals authorised to access networks and information systems supporting the operation of essential functions are trustworthy. To be fully effective, link personnel security with identity and access control. Further information can be found in CPNI's Personnel and People Security and ISO/IEC 27002.

### Implementing and communicating policies and processes
Implementation of a new or improved cyber security and resiliencepolicy or process requires communication to those under its scope and evaluation of its effectiveness.

Effectively communicate the policies and information on how  processes work to everyone who can affect the security of the system, so that they can readily understand the contribution they make and their responsibilities to essential function security and resilience.

Communication can be achieved through continued security conversations and staff awareness and training programmes. However, it should be noted that having a staff awareness and training programme alone, without an understanding of how people work with security, is unlikely to result in improved compliance with cyber security and resilience policies and processes. Refer to B6. Staff Awareness & Training for further information on effective staff awareness and training programmes.

Suitable data and metrics should be defined prior to implementation to evaluate the previous condition and assess the impact of the new or updated policy or process. Information may be drawn from security incidents, technical measurements, surveys, customer feedback, etc.

### Improving policies and processes
Cyber security and resilience policies and processes should be designed to be adaptable, to fit the needs of the changing environment. Organisations should regularly review their policies and processes in light of any recorded security breaches so that these documents and the organisation’s security can be continually improved.

