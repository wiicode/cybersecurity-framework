---
title: 14. Secure use of the service
description: The security of cloud services and the data held within them can be undermined if you use the service poorly. 
published: true
date: 2021-06-30T02:55:47.827Z
tags: silver, cloud-security-principles, silver-training
editor: markdown
dateCreated: 2021-02-22T01:44:56.987Z
---

# 14\. Secure use of the service

The security of cloud services and the data held within them can be undermined if you use the service poorly. Consequently, you will have certain responsibilities when using the service in order for your data to be adequately protected.

The extent of your responsibility will vary depending on the deployment models of the cloud service, and the scenario in which you intend to use the service. Specific features of individual services may also have bearing. For example, how a content delivery network protects your private key, or how a cloud payment provider detects fraudulent transactions, are important security considerations over and above the general considerations covered by the cloud security principles. 

With [IaaS and PaaS](https://www.ncsc.gov.uk/collection/cloud-security?curPage=/collection/cloud-security/standards-and-definitions) offerings, you are responsible for significant aspects of the security of your data and workloads. For example, if you procure an IaaS compute instance, you will normally be responsible for installing a modern operating system, configuring that operating system securely, securely deploying any applications and also maintaining that instance through applying patches or performing maintenance required.

### **Goals**

You:

-   understand any service configuration options available to you and the security implications of your choices
-   understand the security requirements of your use of the service
-   educate your staff using and managing the service in how to do so safely and securely

### **Implementation**

We have published [a separate guide on your responsibilities when configuring IaaS securely.](https://www.ncsc.gov.uk/collection/cloud-security?curPage=/collection/cloud-security/iaas)

-   We also have published configuration guidance for some SaaS products.
-   You should also consider the end user devices which can connect to the cloud service

| **Approach** | **Description** | **Guidance** |
| --- | --- | --- |
| Enterprise managed devices | The service is accessed from devices under your control | A single compromised device would have access to any data, functionality or credentials accessible to authorised users of that device. However since the devices are under your control you can configure them securely.<br><br>See our [End User Devices Security Guidance](https://www.ncsc.gov.uk/collection/end-user-device-security) for advice in this area. |
| Partner managed devices | The service is accessible from devices you understand the configuration of, or have some control over. For example, via contractual clauses or conformance with your security requirements. | A single compromised device would have access to any data, functionality or credentials accessible to authorised users of that device, so it’s important to ensure the configuration is adequate.<br><br>If you rely on contracts to enforce your security requirements with partners, then they need to be well written to ensure they will be effective. |
| Unknown devices | You have little knowledge of the configuration or state of devices accessing the service. | It is impossible for you to identify compromised devices, so you should assume that a non-zero percentage of devices will be compromised. |

### **Additional Notes - End user devices connecting to the service**

As well as risks to the cloud service, anything you build upon the service and your data, you should consider the risks relating to your enterprise networks and the end user devices connected to the service.

For some of your data and workloads it may be appropriate to require the use of enterprise-issued and managed devices with an appropriate configuration to ensure sufficient security. Risks associated with different options are described in the table above.