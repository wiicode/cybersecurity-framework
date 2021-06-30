---
title: Supply chain attack examples
description: Constantly evolving attacks mean organizations should ensure they also evolve defenses
published: true
date: 2021-06-01T19:57:48.751Z
tags: guidance, bronze, supply-chain
editor: markdown
dateCreated: 2021-03-10T01:54:57.644Z
---

Outlined in this section are examples of supply chain attacks that illustrate the challenges organizations face. Attacks are constantly evolving and you should ensure you keep up to date with these. While these are primarily cyber attacks it is important to also consider threats such as fraud, theft and insiders.

# Third party software providers
> Learn about an example of a supply chain attack through a third party software provider, where a legitimate industrial control system is 'trojanised'.
{.is-info}


Since 2011, the cyber-espionage group known as Dragonfly (also known as Energetic Bear, Havex, and Crouching Yeti) has allegedly been targeting companies across Europe and North America, mainly in the energy sector. This group has a history of targeting companies through their supply chains.

![third_party_software_provider.png](/article_images/third_party_software_provider.png =500x)

In their latest campaign, Dragonfly successfuly “trojanised” legitimate industrial control system (ICS) software. To do so, they first compromised the websites of the ICS software suppliers and replaced legitimate files in their repositories with with their own malware infected versions.

Subsequently, when the ICS software was downloaded from the suppliers’ websites it would install malware alongside legitimate ICS software. The malware included additional remote access functionalities that could be used to take control of the systems on which it was installed.

Compromised software is very difficult to detect if it has been altered at the source, since there is no reason for the target company to suspect it was not legitimate. This places great reliance on the supplier, as it's not feasible to inspect every piece of hardware or software in the depth required to discover this type of attack.

# Website builders

> Learn about an example of a supply chain attack where legitimate websites were compromised through websites builders used by creative and digital agencies.
{.is-info}


Cyber criminals also target supply chains as a means of reaching the broadest possible audience with their malware. Identifying and compromising one strategically important element is an efficient use of resources and may result in a significant number of infections.

![website_builder.png](/article_images/website_builder.png =500x)

The Shylock banking trojan is as a good example of this. Focused on e-banking in the UK, Italy and the USA, the threat from the group behind this virus was reduced by a joint operation between law enforcement agencies and the cyber-security community, in July 2014.

The Shylock attackers compromised legitimate websites through website builders used by creative and digital agencies. They employed a redirect script, which sent victims to a malicious domain owned by the Shylock authors. From there, the Shylock malware was downloaded and installed onto the systems of those browsing legitimate websites.

The economy of effort makes this a very successful endeavour. By integrating a multitude of different features adopted from other malware, Shylock was capable of performing customisable ‘man-in-the-browser’ attacks, avoiding detection and protecting itself from analysis.

Rather than compromising a number of legitimate sites individually, the attack targeted the core script of a website template designed by a UK-based creative, digital agency.


# Third party data stores
> Learn about a supply chain attack through a third party data storer where networks belonging to large data aggregators were reported as compromised.
{.is-info}

Many modern businesses outsource their data to third party companies which aggregate, store, process, and broker the information, sometimes on behalf of clients in direct competition with one another.

Such sensitive data is not necessarily just about customers, but could also cover business structure, financial health, strategy, and exposure to risk. In the past, firms dealing with high profile mergers and acquisitions have been targeted. In September 2013, a number of networks belonging to large data aggregators were reported as having been compromised.

![third_party_data_stores.png](/article_images/third_party_data_stores.png =500x)

A small botnet was observed exfiltrating information from the internal systems of numerous data stores, through an encrypted channel, to a botnet controller on the public Internet. The most high profile victim was a data aggregator that licenses information on businesses and corporations for use in credit decisions, business-to-business marketing and supply chain management. While the attackers may have been after consumer and business data, fraud experts suggested that information on consumer and business habits and practices was the most valuable.

The victim was a credit bureau for numerous businesses, providing “knowledge-based authentication” for financial transaction requests. This supply chain compromise enabled attackers to access valuable information stored via a third party and potentially commit large scale fraud.

# Watering hole attacks
> Learn what supply chain attacks known as watering hole attacks are, how they work, and real-world examples of this type of attack.
{.is-info}

A watering hole attack works by identifying a website that's frequented by users within a targeted organization, or even an entire sector, such as defense, government or healthcare.That website is then compromised to enable the distribution of malware.

The attacker identifies weaknesses in the main target’s cyber-security, then manipulates the watering hole site to deliver malware that will exploit these weaknesses.

![watering_hole.png](/article_images/watering_hole.png =500x)

The malware may be delivered and installed without the target realising (called a ‘drive by’ attack), but given the trust the target is likely to have in the watering hole site, it can also be a file that a user will consciously download without realising what it really contains. Typically, the malware will be a Remote Access Trojan (RAT), enabling the attacker to gain remote access to the target’s system.

Attackers are increasingly exploiting ‘watering hole’ sites to conduct espionage attacks against a host of targets, across a variety of industries. The VOHO campaign is a good example of this.


# Further Reading

Below are some external links to further reading which compliment this collection.

[Pharmaceuticals, Not Energy, May Have Been True Target Of Dragonfly, Energetic Bear](https://www.darkreading.com/pharmaceuticalsnot-energy-may-have-been-true-target-of-dragonfly-energetic-bear/d/d-id/1316869)

['Shylock' malware hit by authorities](https://www.bbc.com/news/technology-28245598)

[Hacking The Street? Fin4 Likely Playing The Market](http://www2.fireeye.com/rs/fireye/images/rpt-fin4.pdf)

[Data Broker Giants Hacked by ID Theft Service](https://krebsonsecurity.com/2013/09/data-broker-giants-hacked-by-id-theft-service/)

[Espionage Hackers Target ‘Watering Hole’](https://krebsonsecurity.com/2012/09/espionage-hackers-target-watering-hole-sites/)