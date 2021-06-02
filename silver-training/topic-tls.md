---
title: Using TLS to protect data
description: How to configure the services that must be able to receive incoming connections from unknown clients or services.
published: true
date: 2021-06-02T21:59:42.572Z
tags: silver, sourced, silver-training
editor: markdown
dateCreated: 2021-02-22T00:32:05.089Z
---

# Using TLS to protect data

How to configure the services that must be able to receive incoming connections from unknown clients or services.

This guidance outlines how to configure the services that must be able to receive incoming connections from unknown clients or services. Specifically it covers the scenarios of: operating a public website; embedded devices which need to communicate securely back to online services where certificate management and the overhead of IPsec would be too great; and supporting email transfer using Simple Mail Transfer Protocol (SMTP). This guidance does **not** address use of TLS for Virtual Private Networks (VPNs). The NCSC recommends the use of [IPsec to protect data in transit](https://www.ncsc.gov.uk/guidance/using-ipsec-protect-data) in line with the [Cabinet Office End User Device Strategy](https://www.gov.uk/government/uploads/system/uploads/attachment_data/file/261980/EUD_Security.pdf) as IPsec is a mature set of standards, widely available across many vendors of end user devices and networking equipment.

---

## About TLS

Transport Layer Security (TLS) is a protocol which provides privacy between communicating applications and their users, or between communicating services. When a server and client communicate, well-configured TLS ensures that no third party can eavesdrop or tamper with any message.

At the time of writing, the current version of TLS is version 1.2, which includes security improvements over version 1.0. The predecessor to the TLS protocol was the Secure Sockets Layer (SSL) protocol, all versions of which are now regarded as insecure.

---

## Deploying TLS for web servers

Users accessing an organisation’s digital public services need to have confidence that they are accessing a legitimate service and that their communications remain private and free from interference. TLS is a protocol that provides this security.

TLS used in the context of web servers is known as HTTPS (that is HTTP over TLS).

### **Selecting protocol versions, cryptographic algorithms and parameters**

There are many configuration options that affect the security of a service and communications with it. Unfortunately, selecting the most secure configuration may mean some users are unable to connect to your service. For this reason, you may need to find a balance between security and those users that it's essential the service can reach.

In Mozilla’s [advice on Server Side TLS](https://www.ssllabs.com/projects/best-practices/index.html), several TLS configurations are described (‘Modern’, ‘Intermediate’, and ‘Old’) that refer to some of the 'best' security settings possible, depending on the versions of the browsers that need to be supported. Supporting the ‘Old’ profile is risky and should be avoided, as it would mean supporting the insecure SSL protocol.

You should configure the web server to prefer more recent versions of protocols and more secure options first. The server should also be configured **not** to revert to an older standard after the initial negotiation. [Mozilla’s guide](https://wiki.mozilla.org/Security/Server_Side_TLS#Prioritization_logic) provides some good recommendations on how to configure the prioritisation logic of your web server.

For web services that will only be accessed by known (well-maintained) end user devices, then it should be possible to deploy a strict cryptographic profile. In these situations we recommend you use one of the [preferred TLS configurations given below](https://www.ncsc.gov.uk/guidance/tls-external-facing-services#profiles).

### **Secure configuration recommendations**

There are a number of good guides that provide configuration advice for HTTPS:

[Qualys - SSL/TLS Deployment Best Practices](https://www.ssllabs.com/projects/best-practices/index.html)

[Google - Webmasters: Secure Your Site with HTTPS](https://support.google.com/webmasters/answer/6073543)

[Mozilla Security/Server Side TLS](https://wiki.mozilla.org/Security/Server_Side_TLS#Modern_compatibility)

We also recommend the following when deploying your services:

publish services only using HTTPS

automatically redirect users who visit the HTTP version of your service to the HTTPS version

use the latest versions of TLS libraries and supporting web frameworks; implementation issues can introduce vulnerabilities in the libraries which can quickly be exploited if not patched promptly

follow the guidance on secure application design from Qualys (see [section 4](https://github.com/ssllabs/research/wiki/SSL-and-TLS-Deployment-Best-Practices) of Qualys - SSL/TLS Deployment Best Practices)

enable [HTTP Strict Transport Security (HSTS)](https://www.owasp.org/index.php/HTTP_Strict_Transport_Security) to help the browser secure connections to your service; one or both of the following steps should be taken:

-   add the Strict-Transport-Security HTTP header when the site is accessed over HTTPS - this instructs the browser to only request the HTTPS version in future (until the expiration time in the header elapses)
-   add your sites to the HSTS preload lists which modern browsers use to automatically redirect HTTP traffic to HTTPS ( [Chrome’s preload list](https://hstspreload.org/) is included in many of the other browsers’ lists)

design new applications to use [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/Security/CSP/Introducing_Content_Security_Policy), as it can be difficult to retrofit later

server certificates should be acquired from [trustworthy and reputable sources](https://www.ncsc.gov.uk/guidance/tls-external-facing-services#choosing-a-certificate-authority)

publish [DNS Certificate Authority Authorization](https://en.wikipedia.org/wiki/DNS_Certification_Authority_Authorization) (CAA) records to manage which Certificate Authorities will issue certificates for your domain.

-   ensure you have a means of revoking compromised certificates for your services - you should be able to do this through your chosen Certificate Authority (CA)
-   consider advising users if their web browsers are not supporting a sufficient set of TLS algorithms, and providing them with information on how to upgrade their web browser or operating system if appropriate

---

## Deploying TLS for mail servers

TLS for mail servers guidance can be found [here](https://www.ncsc.gov.uk/guidance/email-security-and-anti-spoofing).

---

## Choosing a Certificate Authority

TLS uses X.509v3 certificates to cryptographically validate identities presented by one or both of the communicating parties. If the connecting party is able to validate that the certificate presented to it is issued by a CA it trusts, then secure communications should be established. It is therefore important to choose a CA that is widely trusted by those likely to connect to your services. If selecting a less common CA, it is possible that the certificates presented by your service may not be able to be validated by the connecting party, and the other party may choose not to continue the session.

In order to verify the certificate presented by your server, the web browser or mail server may use its own store of trusted root CAs, or it may refer to the CAs trusted by the operating system. As there is no universal list of trusted CAs, you will need to research support for your chosen CA in the likely web browsers or mail servers and services expected to connect to your service.

Further good advice on what to look for in a CA is set out in section 1.4 of the [Qualys - SSL/TLS Deployment Best Practices guide](https://www.ssllabs.com/projects/best-practices/index.html).

### **Requesting a certificate**

In order to have an X.509v3 certificate signed by a CA, you would normally generate your own private key, and send a Certificate Signing Request (CSR) to the CA to be signed, thus keeping your private key secret. There are several parameters you can choose for your private key and signing request. The main choice is whether to support RSA certificates and keys, or Elliptic Curve Cryptography (ECC); either can offer acceptable security. Some mail and web servers support both ECC and RSA, and will select the appropriate certificate based upon the TLS negotiation with the connecting party.

If generating an RSA certificate, we recommend using the following parameters:

2048-bit RSA with SHA256

If generating an ECC certificate, we recommend using the following parameters:

ECDSA-256 with SHA256 on the P-256 curve

---

## Testing

Given the wide range of configuration options available for TLS, we recommend that you regularly test the configuration of your web servers and mail servers by running automated scans. There are a number of publicly available tools to help test the TLS configuration of your web or mail server. Some tools you may find useful are:

[Qualys SSL Server Test](https://www.ssllabs.com/ssltest/)

Check TLS services from [checktls.com](http://www.checktls.com/index.html)

These scans will identify most common issues and configuration problems. They should not be seen as a replacement for skilled penetration testing of your services, but if you have already used tools such as these to help identify and mitigate common issues, then penetration testers will have more time to spend ensuring there are not more subtle or unique flaws in your service.

Note that whilst it is possible for others to test the ability for you to receive email securely, it is **not** possible for others to test the ability of your services to send email securely without your cooperation. You have to send an email to a testing service, such as that offered by [checktls.com](http://checktls.com/).

---

## Recommended cryptographic profiles for TLS

Where support for legacy browsers or applications is not an issue, we recommend you select one of the two cryptographic profiles for TLS:

### **Combination 1 of the Suite B profile for TLS**

A summary of the Suite B profile for TLS is below:

| **Algorithm type** | **Description** |
| --- | --- |
| Protocol | TLS v1.2 |
| Encryption | AES with 128-bit key in GCM mode |
| Pseudo-random function | TLS PRF (with SHA-256) |
| Authentication | ECDSA-256 with SHA-256 on P-256 curve |
| Key exchange | ECDH using P-256 curve |

### **Foundation Profile for TLS**

Depending on equipment and infrastructure support, deploying Combination 1 of the Suite B profile for TLS may not be achievable. A suitable alternative is the Foundation Profile for TLS. This profile consists of an RFC-compliant implementation of TLS using the algorithms given in the table below:

| **Algorithm type** | **Description** |
| --- | --- |
| Protocol | TLS v1.2 |
| Encryption | AES with 128-bit key in CBC mode |
| Pseudo-random function | TLS PRF (with SHA-256) |
| Authentication | X.509 certificates with RSA signatures (2048 bits) and SHA-256 |
| Key exchange | DH Group 14 (2048-bit MODP Group) |
| Integrity | SHA-256 |

Deviation from this profile, such as through the use of GCM rather than CBC mode, or the use of Perfect Forward Secrecy (PFS), may be required or desirable, and is acceptable.