---
title: 2. Asset protection and resilience
description: User data, and the assets storing or processing it, should be protected against physical tampering, loss, damage or seizure.
published: true
date: 2021-06-30T02:56:38.728Z
tags: silver, cloud-security-principles, silver-training
editor: markdown
dateCreated: 2021-02-22T01:33:08.105Z
---

# 2\. Asset protection and resilience

User data, and the assets storing or processing it, should be protected against physical tampering, loss, damage or seizure.

## The aspects to consider are:

-   Physical location and legal jurisdiction
-   Data center security
-   Data at rest protection
-   Data sanitzsation
-   Equipment disposal
-   Physical resilience and availability

## **2.1 Physical location and legal jurisdiction**

In order to understand the legal circumstances under which your data could be accessed without your consent you must identify the locations at which it is stored, processed and managed.

You will also need to understand how data-handling controls within the service are enforced, relative to regulations. Inappropriate protection of user data could result in legal and regulatory sanction, or reputation damage.

### **Goals**

You should understand:

-   In which countries your data will be stored, processed and managed. You should also consider how this affects your compliance with relevant legislation e.g. Data Protection Act (DPA)
-   Whether the legal jurisdiction(s) within which the service provider operates are acceptable to you
     

### **Implementation approaches - Physical location and legal jurisdiction**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Unknown processing and storage locations | Service provider offers no information on data centre locations for storage and processing of information and workloads | (lightning bolt)<br><br>In this scenario you do not know the locations your data is accessible from, so it will not be possible for you to fully understand the legal jurisdiction your data is subject to. |
| Known locations for storage only | Service provider presents detailed information on data centre locations | Only knowing the storage locations for your data is a potential risk. The data may also be available in other locations, such as where it's processed or managed. |
| Known locations for storage, processing and management | Service provider presents detailed information on all locations wheredata is stored and processed and where they manage the service from | This is the complete set of physical locations. You need this in order to fully understand the risks around physical access to your data.<br><br>The level of confidence you have in the lists provided will vary depending on whether you're reliant on the supplier's assertions or have additional assurance through independent validation.<br><br>Another important factor is whether the supplier is contractually committed to notify you of changes to the list. |

### **Additional notes – Legal Jurisdiction**

Understanding the legal jurisdiction(s) to which your data is subject may be more complex than simply clarifying the physical locations where data is stored, processed or accessed by the service. It’s also necessary to consider the legal base and operating locations of the service provider, the governing legislation of any contracts, and the terms of use - or other agreements - between users of the service (or their suppliers) and the provider. It is important for organizations consuming cloud services to consider this topic and seek legal advice as necessary.


### **Additional notes – Use of your data**

You should consider the implications of any rights the service provider will have relating to data stored within the service. Some usage agreements allow the service provider to employ user data for marketing or other purposes. You should also check whether any agreements with the service provider relating to their use of your data are acceptable to you and also not contrary to relevant legislation, such as the DPA.

## **2.2 Data center security**

Locations used to provide cloud services need physical protection against unauthorized access, tampering, theft or reconfiguration of systems. Inadequate protections may result in the disclosure, alteration or loss of data.

### **Goals**

You should be confident that the physical security measures employed by the provider are sufficient for your intended use of the service.

### **Implementation approaches - Data centre security**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Unknown | The service provider does not disclose how their data centres are secured. | In this scenario you will be taking the suppliers word for it that their data centres are appropriately secured. Whether you choose to do that will depend on the intrinsic trust you have in the service provider.  |
| Known controls | The service provider discloses information on the security controls around their (or their suppliers’) data centres. | If no recognized standard is referred to by the service provider you will need to make your own assessment of the physical controls protecting their data centres. |
| Conforms to a recognized standard | The service provider has had their data centre protections certified against a recognized and appropriate standard that covers physical security.<br><br>Appropriate standards include:   <br>[CSA CCM v3.0](#)   <br>[SSAE-16 / ISAE 3402](#) | Standards differ in terms of the level of detail applied to physical controls. The scope of the assessment must be relevant to locations where your data can be accessed.<br><br>Independent validation that the scope of a certification is correct can be obtained to provide reassurance in this area. |

## **2.3 Data at rest protection**

To ensure data is not available to unauthorized parties with physical access to infrastructure, user data held within the service should be protected regardless of the storage media on which it’s held. Without appropriate measures in place, data may be inadvertently disclosed on discarded, lost or stolen media.

### **Goals**

You should have sufficient confidence that storage media containing your data are protected from unauthorized access.

### **Implementation approaches - Data at rest protection**

Service providers could use encryption, physical security controls, or a combination of both, to protect data at rest within the service.

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Physical access control | A number of standards are appropriate when validating physical access control protections. These are backed by a variety of certification schemes:  <br>[CSA CCM v3.0](#)   <br>[SSAE-16 / ISAE 3402](#) | Levels of control differ between physical security standards. The scope of the assessment must be relevant to those locations where your data can be accessed. |
| Infeasibility of finding a specific customer’s data on physical media | The service provider states that their scale, obfuscation techniques, or data storage ‘sharding’ make it infeasible for a determined attacker with physical access to a data centre to locate a specific customer’s data. | It is unlikely that independent assurance will be available to support the service provider’s claims that it is infeasible for someone to target your data in a theft of a physical disk. Therefore it may be worth also understanding what confidence you can gain from one of the two other approaches described. |
| Encryption of all physical media | The service provider employs encryption to ensure that no data is written to disk in an unencrypted form. | Management of the keys used to encrypt data before it is stored is the biggest challenge with this approach. Errors in use of cryptography or poor key management could result in exposure of your data.<br><br>It's also important to understand whether the encryption products used provide the confidence you’d expect. Products which have been assessed against a good standard are recommended. |

### **Additional notes - Joiners and Leavers**

To support onboarding and offboarding processes it may be necessary for storage media to be transferred between you and the service provider. If this is the case, the storage media should be protected using one of the approaches given above.

## **2.4 Data sanitisation**

The process of provisioning, migrating and de-provisioning resources should not result in unauthorized access to user data.

Inadequate sanitisation of data could result in:

-   your data being retained by the service provider indefinitely
-   your data being accessible to other users of the service as resources are reused
-   your data being lost or disclosed on discarded, lost or stolen media

### **Goals**

You should be sufficiently confident that:

-   Your data is erased when resources are moved or re-provisioned, when they leave the service or when you request it to be erased
-   Storage media which has held your data is sanitised or securely destroyed at the end of its life

### **Implementation approaches - Data sanitisation**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| None/unknown | The service provider is not able to explain how storage is sanitised when it is released by a user. | It may be that the service provider's approach to their own data at rest protection (see section 2.3) gives you confidence that reallocated storage would not contain cleartext data if it was allocated to another user. If that's not the case, then you could choose to employ encryption of data that you store in the service. |
| Assurances media can't be directly addressed | The service provider may be able to provide assurances that previously stored data cannot be addressed by others after the it is released. | It may be that the service provider's approach to their own data at rest protection (see section 2.3) gives you confidence that reallocated storage would not contain cleartext data if it was allocated to another user. If that is the case, then their assurances around how data is reallocated may provide you all of the confidence you need. However, depending on the service, you could also employ encryption to additionally protect your stored data. |
| Explicit overwriting of storage before reallocation | Storage which is no longer required is sanitised according to a specified policy before being reallocated to another user. | If you know that data you have previously used is overwritten before it is reallocated to another user of the service, then that will help provide reassurance that another user could not access your data. As with the other approaches described above, you can gain additional confidence if the service provider encrypts all stored data under user-specific keys, or if you encrypt your own data that you store in the service. |

## **2.5 Equipment disposal**

Once equipment used to deliver a service reaches the end of its useful life, it should be disposed of in a way which does not compromise the security of the service, or user data stored in the service.

### **Goals**

You should be sufficiently confident that:

-   All equipment potentially containing your data, credentials, or configuration information for the service is identified at the end of its life (or prior to being recycled).
-   Any components containing sensitive data are sanitised, removed or destroyed as appropriate.
-   Accounts or credentials specific to redundant equipment are revoked to reduce their value to an attacker.

### **Implementation approaches – Equipment disposal**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Unknown or proprietary techniques used | \-  | In this scenario you will need to trust the service provider orcarry out your own assessment of whether the controls in place are appropriate. |
| A recognized standard for equipment disposal is followed | A number of standards include controls which cover the need for secure equipment disposal.  | The standards referenced cover the need for secure equipment disposal, rather than validation of the process. It is worth checking the scope of any certification to verify that the existence of appropriate controls was covered as part of the assessment.<br><br>Independent validation is likely to play an important part in providing confidence that remnants of your data cannot be easily retrieved from equipment that has been disposed of. |
| A third party destruction service is used | A destruction service which specialises in secure disposal of equipment is used. | A number of these services have been assessed against a recognized standard, such as the CESG Assured Service (Destruction) scheme. |

## 2.6 Physical resilience and availability

Services have varying levels of resilience, which will affect their ability to operate normally in the event of failures, incidents or attacks. A service without guarantees of availability may become unavailable, potentially for prolonged periods, regardless of the impact on your business.

### **Goals**

You should be sufficiently confident that the availability commitments of the service, including their ability to recover from outages, meets your business needs.

### **Implementation approaches - Physical resilience and availability**

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| The service provider commits to a Service Level Agreement (SLA) | Contractual commitments or Service Level Agreements (SLAs) are used by the service provider to make commitments about the level of service availability. | This approach may provide a mechanism for compensation in event of outages, but outages will not be prevented if the service design is not appropriate.<br><br>It is additionally beneficial to review the supplier’s historical records of service availability (see next point). |
| Review of historical data | The service provider may present historical evidence of service availability. | You should evaluate this evidence and draw your own conclusions on whether this, together with the service provider’s commitments and reputation, give you sufficient confidence. |
| Analysis of the design | The service provider may be willing to share information on how they have designed their service to be resilient. | Having this information reviewed by a specialist security expert would provide additional confidence. |

### **Additional notes - Resilience**

You should evaluate whether the service provider can meet the availability and resilience requirements you have. Services procured with ‘best endeavours’ support should be considered to have no guaranteed support.
