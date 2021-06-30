---
title: Spray you, spray me: defending against password spraying attacks
description: How organizations can protect users' accounts from password spraying.
published: true
date: 2021-06-30T19:31:49.744Z
tags: bronze, passwords
editor: markdown
dateCreated: 2021-06-30T19:31:49.744Z
---

One common way that online accounts are breached is through *password spraying*, whereby lists of a small number of common passwords are used to brute force large numbers of accounts. These attacks are successful because for any given large set of users there will likely be some who are using very common passwords, and these attacks can slip under the radar of protective monitoring which only look at each account in isolation.

To understand how much of a problem this is, our resarch team has conducted a study which allowed participating organizations to assess how vulnerable they would be to a password spraying attack. The PowerShell script we used to collect data is [still available to download](https://s3-eu-west-1.amazonaws.com/cesg-security-guidance/pwauditor-v1.2.1.zip) for your own use if needed, but since the study is now over we can't provide support. From the study we found:

-   75% of the participants’ organizations had accounts with passwords that featured in the top 1,000 passwords
-   87% had accounts with passwords that featured in the top 10,000

This data suggests that password spraying attacks are likely to have some success against these organizations, and many other organizations. While account lockout policies may limit attackers to trying (for example) 10 passwords against a single account per day, the account lockout counters usually **reset** over time. This allows persistent attackers to try more passwords, and they can (and do) end up trying hundreds or even thousands of common passwords.

Because of this, one of the questions the *BCSF* frequently get asked is how to mitigate password spraying attacks. High password complexity doesn’t guarantee that passwords will be more difficult for attackers to break, but it usually does make them harder for users to remember - thus driving weaker passwords and more password reuse overall. So instead, we often encourage users to disable complexity requirements and adopt other strategies such as [three random words](t(/bronze-training/passwords/three-random-words-or-thinkrandom-0). However, this means that the onus is now even more on users to pick 'good' passwords (that is, passwords that cannot easily be guessed), and network administrators ostensibly have very limited *defense* against password spraying attacks.

Fortunately, there are actually a variety of approaches organizations can take to mitigate these attacks, and the number of available options is growing regularly. As a starting point, we recommend making sure that you do some of the following:

-   configure protective monitoring over externally-reachable authentication endpoints to look for password spraying attacks (some ideas are given in [the password guidance](/bronze-training/passwords));
-   deploy alternatives to passwords where possible 
-   enforce multi-factor authentication on your externally-reachable authentication endpoints
-   provide **pragmatic** advice to users on how to choose 'good' passwords
-   regularly audit user passwords against common password lists, using free or commercial tools (or the [*BCSF* PowerShell script](https://s3-eu-west-1.amazonaws.com/cesg-security-guidance/pwauditor-v1.2.1.zip))

One of the most effective approaches to stopping these attacks is to prevent users from using common passwords in the first place. Over the last few months, we’ve been talking to several developers of software that uses passwords, and asking them to think about how to prevent their users from setting common ones. Some plan to use something like [Troy Hunt’s HIBP service](https://www.troyhunt.com/ive-just-launched-pwned-passwords-version-2/) to prevent common passwords, or have user-configurable deny lists in their products (or support third party software that does the same).

Many of our customers use Microsoft technologies for user authentication. The good news here is that they've announced a [_variety of mitigations for password spraying attacks_](https://cloudblogs.microsoft.com/enterprisemobility/2018/03/05/azure-ad-and-adfs-best-practices-defending-against-password-spray-attacks/). I’d encourage all admins of hybrid or cloud-only Azure AD networks to have a look at these mitigations and employ them where possible.

However, not all authentication services will provide mitigations for password spraying attacks. If you come across such products, please do suggest to their developers that they should include such mitigations, and point them at this blog if you think it would help. Commercial third party products might help you in the interim. And of course, if your products do have these mitigations, turn them on and monitor your logs!