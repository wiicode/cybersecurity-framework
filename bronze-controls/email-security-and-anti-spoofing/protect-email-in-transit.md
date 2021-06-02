---
title: 2. Protect email in transit
description: Where email is transferred over untrusted networks, such as the internet, its integrity and confidentially should be protected.
published: true
date: 2021-06-02T20:40:32.423Z
tags: bronze, bronze-controls, email
editor: markdown
dateCreated: 2021-06-02T15:15:55.745Z
---

Although it is possible to encrypt individual emails using protocols like [PGP](https://en.wikipedia.org/wiki/Pretty_Good_Privacy) or [S/MIME](https://en.wikipedia.org/wiki/S/MIME), this requires the sender and recipient to have the necessary trust infrastructure in place. This is not likely to be possible for all the parties you communicate with. So, your email servers should be configured to support encryption of the communications channel that the email is sent over. This task is best handled by TLS.

### **TLS and cloud providers**

Where you use a cloud provider for your email, such as Microsoft’s O365 or Google’s G-Suite, this will likely already be in place.


## Implementation details

-   Configure all your email servers to support TLS, regardless of whether they are accessible from the internet or private networks only.
-   Ensure your email servers present a certificate with suitable cryptographic properties and that it is signed by a well-known Certificate Authority.
-   Ensure your email servers *prefer* to use a good cryptographic profile, but that lesser cryptographic profiles are supported too. You should support the case where TLS is not used at all, if you want to be confident you can receive emails from *any* entity.
-   Where possible, consider configuring your email service to *force* TLS between you and the organizations you regularly communicate with.


## How TLS works with email transmission

Email servers communicate using the SMTP protocol - specifically, email servers performing the Mail Transfer Agent (MTA) function.

The SMTP connection between two MTAs can be secured when the connecting party issues the 'STARTTLS' command. When the servers of both parties are well configured, the STARTTLS command will convert an insecure SMTP connection into a secure one, and the TLS protocol will protect subsequent SMTP commands and responses sent between them.


## Selecting protocol versions, cryptographic algorithms and parameters

We recommend configuring mail servers to *prefer* our [Preferred TLS Profile](/silver-training/topic-tls)

However, other mail servers may not be configured to support the same profile, or may not support the use of TLS at all. Your server should negotiate the best profile supported by the connecting mail server. You will need to be able to receive email without TLS if you want to be confident you can receive email from *any* party.


## When to force TLS

STARTTLS is not a flawless technique - it is susceptible to a downgrade attack by a 'man in the middle' sitting between the two communicating parties.

With parties that you contact regularly by email (e.g. partner organizations), it is possible to configure connections so that TLS will always be used and the certificates presented by both mail servers are authenticated, verifying the identities of both parties.


## Mail server certificates

In order for TLS connections to be established, the application connecting to your service will need to validate the identity of your server using the X.509v3 certificate which it presents.

This means your service will need an X.509v3 certificate which is signed by an authority that the party connecting to your service recognizes and trusts. If you are using a cloud-based email provider, this is likely to be done for you, and can be easily tested. However, if you operate your own MTA, you should follow our advice on generating a private key and requesting a certificate from a Certificate Authority.