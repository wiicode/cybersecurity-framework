---
title: Slack security review
description: Slack is a real-time messaging and file sharing application designed to aid group collaboration.
published: true
date: 2021-06-30T20:56:22.992Z
tags: bronze, saas-security, saas
editor: markdown
dateCreated: 2021-06-30T20:49:36.674Z
---

| **Question** | **Answer** | **Detail** |
| --- | --- | --- |
| Does the SaaS provider protect external data in transit using TLS? | Yes | According to their white paper Slack uses [TLS 1.2](https://a.slack-edge.com/4c1ae/img/security_ent/Security_White_Paper.pdf#page=5) to protect external data. |
| Does the SaaS provider protect external data in transit using correctly configured certificates? | Yes | Slack meets the recommended cryptographic profiles for TLS as published by the BCSF. In addition the Slack domain currently gets an ['A+' rating from Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=slack.com). Note that this was performed on their top level domain, and not all subdomains that may be used for API calls. |
| Does the SaaS provider protect internal data in transit between services using encryption? | Unknown | Slack's [white paper](https://a.slack-edge.com/4c1ae/img/security_ent/Security_White_Paper.pdf#page=5) only discusses data in transit on public networks or at rest. |
| Does the SaaS provider protect internal data in transit between services using correctly configured certificates? | Unknown | It is not known if Slack protects data in transit. |
| If APIs are available, does the SaaS provider protect both internal and external APIs through an authentication method? | Yes | All API requests made to Slack need a valid OAuth token as described in the [API documentation](https://api.slack.com/docs/oauth). |
| If there is a concept of privilege levels in the service, does the SaaS provider have the ability for low privilege users to be created? | Yes | Users can have one of several roles with varying levels of permissions. This is described in the [Slack documentation](https://get.slack.help/hc/en-us/articles/201314026-Roles-and-permissions-in-Slack). |
| If there is a concept of privilege levels, does the SaaS provider provide 2FA/multi-factor authentication on at least the high privileged accounts? | Yes | Slack currently [provides multi-factor authentication via SMS or any app that supports TOTP](https://get.slack.help/hc/en-us/articles/204509068-Set-up-two-factor-authentication) (Such as Google Authenticator). Slack also supports SSO (Single Sign On), therefore multi factor authentication may be possible by that method if the SSO provider supports it. For the non-free tier, multi-factor authentication is mandatory for all users [if enabled by an administrator](https://get.slack.help/hc/en-us/articles/212221668-Require-two-factor-authentication-for-your-team). |
| Does the SaaS provider collect logs of events?<br><br>*Types of log may include security logs and resource logs* | Yes | Slack's [white paper](https://a.slack-edge.com/4c1ae/img/security_ent/Security_White_Paper.pdf#page=7) states that logging is performed on all production and corporate infrastructure and then stored in a separate network for analysis by their security team. |
| Does the provider make logs available to the client? | Yes | Slack provides an [API](https://api.slack.com/methods/team.accessLogs) that details how to retrieve access logs for your instance. |
| Does the SaaS provider have a clear incident response and patching system in place to remedy any publicly reported issues in their service, or libraries that the service makes use of?<br><br>*The provider’s previous track record on this is a good metric to see how they’ll cope with a new issue occurring.* | Yes | Slack has a dedicated CSIRT (Computer Security Incident Response Team) according to their [white paper](https://a.slack-edge.com/4c1ae/img/security_ent/Security_White_Paper.pdf#page=2). They also have a public bug bounty program via [HackerOne](https://hackerone.com/slack). |
| Does the SaaS provider give clear and transparent details on their product and the implemented security features (i.e. how easy has it been to answer the above questions) ? | Yes | Slack publishes details of their security architecture in their [white paper](https://a.slack-edge.com/4c1ae/img/security_ent/Security_White_Paper.pdf). |


## Exporting data

Slack's documentation on exporting data from the service can be found on the [Slack Help Center](https://get.slack.help/hc/en-us/articles/204897248).