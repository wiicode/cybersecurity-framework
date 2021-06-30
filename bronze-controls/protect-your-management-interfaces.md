---
title: Protect your management interfaces
description: Why it's important to protect the interfaces used to manage your infrastructure, and some some recommendations on how you might do this.
published: false
date: 2021-05-28T03:15:04.106Z
tags: guidance, bronze
editor: markdown
dateCreated: 2021-05-28T03:14:14.294Z
---

When it comes to architecture design, one area that is often not given due consideration is the protection of the management interfaces used by administrators or operators to configure their infrastructure. These are the interfaces used to perform privileged actions on systems, and as such they're a valuable prize for an attacker who wants to gain total control of your system.

There are a wide variety of management interfaces for different technologies. These include more traditional management interfaces (such as consoles and remote desktops), browser-based admin interfaces to configure infrastructure, and web-based interfaces to configure many cloud services.

**This blog focuses on the more traditional management interfaces for managing servers and network infrastructure.** Some of the points will be equally applicable to protecting cloud-based services too, and we'll follow up with a blog that covers protecting the management interfaces of cloud services at a later date.


## Three main problems...

There are three main problems to tackle here. The first problem relates to human nature. Systems administrators, like everyone else, want an easy life. They probably need to work as a normal user for much of their day, with access to email and corporate IT. When they need to administer their system, they’d like to simply fire up a terminal session (or a browser) on their local machine, and connect to the management interfaces for their infrastructure. In this scenario, life is convenient for the user, but it’s also convenient for an attacker.

If the user gets their device compromised by a phishing or watering-hole attack, then the attacker can steal the credentials they use to connect to the management interface, or they could take over management sessions once the user is finished with them.

The second problem is about technology. Management interfaces are written in software, and like all software, can contain vulnerabilities. If you can avoid exposing management interfaces then you're reducing your attack surface; the bad guys will have to attack your system via the front door.

Thirdly, there's the need for a trail of breadcrumbs. Without an audit record of the actions carried out via management interfaces, you'll struggle to figure out what happened in event of an incident.

Let’s examine these problems in more detail.


## 1: Protecting devices used for administration

Techies - particularly systems administrators - tend to have the best accesses of anyone in an *organization*. If an attacker can get hold of privileged accesses from the get-go, then they’ll save themselves a lot of work later on.

An attacker looking to breach an *organization* will typically start researching potential victims on the Internet. They’ll search company and conference websites and trawl social media looking for their preferred targets. Finally, they'll select the victims they believe will have the best accesses.

Attacks from adversaries of all skill levels are often launched with a phishing email. Depending on the depth of background research the attacker has carried out, the email could be crude or very well crafted. The aim of it is to entice the user into opening a malicious attachment, or clicking a link that will load malicious content into their browser.

If the attack is successful, then the attacker will be able to run code on the victim's device and perform the same actions they could on their system. If they want to impersonate the victim, they can either steal the credentials of the victim or steal their active sessions. Either way, if the victim is a systems administrator who manages their infrastructure from that device, then the attacker has struck gold; they'll have the same accesses as the victim.

It’s best to assume that your system administrators will be targeted and that occasionally, a very well-researched and well-crafted phishing email will trick even the most cyber-savvy of users.

### **Tips to reduce the impact of successful attacks against privileged users:**

1.  Ensure privileged users carry out their administrative duties in a ‘clean’ (more trusted) environment.
2.  Ensure privileged users handle their email and web browsing in a separate ‘dirty’ (less trusted) environment.
3.  Consider the ‘dirty’ environment to be sacrificial, and design it in a way that anticipates compromise. When it **is** compromised, you’d like to be able to find out *when* and *how* (and be able to easily recover it into a good state), but the breach shouldn't have a big impact on your important systems.
4.  Use strong authentication mechanisms, such as 2-factor authentication.

Now, I know asking anyone to use two devices isn't popular, which is why it's important to come up with a smart approach to meeting these requirements. You might simply use a KVM, or create separation between the the 'management' and 'corporate' worlds using virtual machines, a remote desktop style approach, or something else. If you go down the virtual machine or remote desktop path, then we’d advise you to treat the end user device as part of the clean admin environment, and that the virtual machine or remote desktop as part of the dirty environment. This way, if the dirty environment gets compromised, then it’s not underneath the clean environment in the processing stack.

We tend to refer to this as a 'browse-down' architecture, and in our experience it makes a **big** difference to the amount of work an attacker has to do to get privileged accesses. 


## 2: Reducing the exposure of management interfaces

The term 'management interface' could cover a wide range of protocols and technologies. Obviously there are some scenarios (such as when using cloud services) where it won't be possible to avoid the need to use a management interface that is exposed to the Internet. In these scenarios a diligent service provider will make sure their management interfaces are hard targets, and it'll be easy for you to secure your accounts with strong authentication and fine-grained access controls.

For more traditional network interfaces (such as with networking and server infrastructure), making your management interfaces hard to reach for an attacker can be an effective mitigation. Even an attacker who has stolen the most privileged of credentials can be thwarted if they can be prevented from accessing the interfaces they would need to use them.

Networking and server infrastructure is typically managed from a console (e.g. via SSH), a remote desktop interface, or through a web-based interface. However there are other interfaces that can be powerful and are often forgotten, such as baseboard management controllers or 'integrated lights-out' functionality used for out-of-band management of hardware. And of course, there are the protocols which aren't normally used for administration but *could* be used for administration in some configurations – examples would include the SMB protocol for file shares or SNMP for networking.

A common way to prevent access to management interfaces is to only expose them to a dedicated management network. This is often achieved with separate network interfaces on the managed infrastructure being connected to an isolated management VLAN.

If you can't avoid the need to expose *some* of your management interfaces to an untrusted network, then think about using a jump server. Jump servers (sometimes known as a bastion hosts) can be used to provide secure and strongly authenticated access. The various other management interfaces for your infrastructure can then be connected to a management network that is only reachable via the jump server. It goes without saying that these servers need to be well-secured and aggressively maintained to ensure they themselves are a difficult target.

Finally, if you do create a separate management network, it's important to re-create the same tiers or layers in the management network that you have in the systems being managed. This way your management network won't be the easiest patch through your system.

### **Tips to protect management interfaces:**

1.  Expose management interfaces to dedicated management networks where you can. At the very least, limit authorized inbound IP addresses to those used by dedicated management devices.
2.  Deploy jump servers where you need to expose management interfaces to less trusted networks. Ensure these are very well configured and maintained.
3.  Use only the latest versions of secure protocols and configure them to use strong authentication mechanisms. For example, use the latest version of SSH rather than Telnet, and use public-key authentication to secure access.
4.  Create similar tiers in your management networks to those in the systems being managed.
5.  Collect and automatically alert on security-relevant events against your management infrastructure.

## 3\. Ensuring there's a trail of breadcrumbs

If an attack occurs (despite taking the steps above), it can be hard to find out what damage has been done. This is because an attacker with admin privileges can not only change your infrastructure, but potentially cover their tracks too. One way to resolve this is to send log files to secure storage in real time. However, it can still be hard to re-construct actions from logs alone.

If your infrastructure is managed via jump servers as described above, then they can be a handy place to record commands executed from them. There are various tools and software packages that can help you automate analysis of these logs for potentially dangerous activity.

### **Tips to improve your chances of detecting an attack (or** ***analyzing*** **what happened):**

1.  Record the commands issued by users on jump servers, and store them securely.
2.  Ensure all network and server infrastructure audit records are also kept securely.
3.  Send these records to a service that administrators don't have readily available access to, and would need multiple people to modify.
4.  Automate the analysis of logs to identify suspicious *behavior*.

If you want to take a more proactive approach to securing privileged access to your infrastructure, then there are some great techniques emerging where access keys are held in escrow and administrators are only permitted to use them on a time-bounded basis in connection with an open service desk ticket. If you do this, ensure you have a good backup plan for 'break-glass' access, just in case.