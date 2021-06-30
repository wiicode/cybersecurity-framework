---
title: Password manager buyers guide
description: A guide to choosing the right type of password manager for your organization, and the security features you need to consider.
published: false
date: 2021-05-28T02:43:37.672Z
tags: bronze, passwords
editor: markdown
dateCreated: 2021-05-27T22:10:11.136Z
---

This guide contains advice for system owners responsible for setting security policies, who are considering deploying a password manager within their *organization*.

There are many password management products on the market, with different features, benefits and limitations. This guide explains both the security and usability principles you should consider, so that you can:

-   assess how password managers can benefit your *organization*
-   chose the right type of password manager


## About password managers

The typical user has dozens of passwords to remember – not just ones used at work. To cope with this overload, users resort to insecure workarounds (such as password reuse or using common passwords), and these are exploited by attackers. Password managers offer an alternative, more secure, way of coping with password overload.

Password managers help users create and store the credentials they use to access services, typically a username and password. The credentials are securely stored in a 'vault', which is accessed via a master password.

## Benefits of using password managers

Using a password manager means that:

-   it's easier for staff to use unique passwords that are harder for an attacker to guess (this increases the quality of passwords in your *organization*)
-   your staff don't need to remember as many passwords - reducing this burden can reduce their reliance on insecure workarounds
-   you can understand how passwords are used in your *organization*

## Risks of using password managers

It's important to understand the risks involved in using password managers:

-   like any other piece of software, password managers may have vulnerabilities 
-   password managers are a natural target for someone trying to gain *unauthorized* access to your accounts, because a successful attack provides access to *all* of a user's stored passwords
-   password managers will be new to many of your users, so they may be reluctant to use them or need some help to get started

This last point explains why **usability** is such an important consideration when choosing a password manager. If users do not find the password manager easy to use and useful, they won't use it, workarounds will persist, and its benefit and costs will go to waste. 

While password managers aren't perfect, we believe that the benefits outweigh the risks, and password managers will improve your security overall.


## Which password manager should I use?

There are many different password managers, and the best one for you will be the one that is useful and usable for the people in your *organization*, and also provides a suitable level of protection for the stored credentials. The features listed below are factors that will affect this.

There is no set way to use password managers in your *organization*, and how it will be used will be a key part of your decision as it will impact your choice of product. For example, you may consider:

-   modifying your password policy to allow staff to save passwords in browsers
-   recommending a particular product, but use is optional
-   including password managers as part of your wider authentication strategy, where use is mandatory
-   promoting the use of password managers in the user's home lives

You may decide that a password manager is not required in your *organization*. For example, if you have an effective single sign-on process, staff may not need to remember many work passwords, so may find a password manager unnecessary.

As well as finding out how your users might use a password manager before choosing a product, we recommend you periodically review how people are using the product once it's been implemented, to ensure that it is still the right solution for your *organization*


## Types of password manager

There are different types of password manager. They may be a standalone application, or built into the browser or operating system. There are two key types of password managers that may share similar features. This may help you narrow down your choice of password manager:


#### **On-device managers**

These store password data on a single device. An attacker would need to have access to that device in order to steal the passwords stored on it. However, as the passwords can only be used on the device where they are stored, they are not ideal for users who need to access the same service from different devices (e.g. laptop, smart phone, or desktop workstation).


#### **Cloud-sync managers**

These store password data on a remote server so it can be accessed from several devices. This allows you to sync your passwords across multiple devices, and many include optional features that allow an admin to centrally monitor and manage the *organization*'s passwords.

However, they have additional security considerations, such as the security of the passwords in transit, and the possibility of a remote attacker gaining access to the password manager account. More general cloud security principles can be found in the [*BCSF*'s Advanced Security Principles](/silver-training/iaas-implementing-principles)

---

## Considerations for all types of password manager

This section summarises important security features you should consider when choosing a password manager, **regardless of the type used**.

### **1\. Credentials at rest**

Credentials at rest should be encrypted to prevent attackers from reading sensitive information. Using no (or poor) encryption would mean attackers could access the password manager data. This means that the **passwords** stored on a device (or in a cloud service) should be encrypted at rest using encryption algorithms recommended by the *BCSF*. In addition, you may also want **other data fields** (such as the domains you've saved passwords for) to be encrypted.

**In summary:**

-   Protect passwords at rest using good encryption. Most password managers will describe which encryption algorithms they use and you can compare these to [our guidance on recommended algorithms](#).
-   Check how each data field that you consider to be sensitive is stored and protected.

### **2. Access to credentials and account recovery**

Ideally, the stored credentials in a password manager should **only** be accessible to the individual user, using their decryption key (which is usually derived from their password manager's master password). This decryption key should not be accessible to anyone else, including the service provider in the case of cloud-sync password managers.

However, this means that if the user forgets their master password, they will lose access to all their saved passwords, and will have to spend considerable time and effort to reset passwords for all their saved accounts. For this reason, some managers offer methods to recover an account. These methods vary, but may involve other authorized parties (such as other members of a team, an admin or the service provider) to enable the password recovery. Be aware that the recovery method may be exploited to gain access to the credentials, especially if the service provider is responsible for account recovery.

**In summary:**

-   **Nobody** should be able to access passwords without the correct decryption key.
-   The decryption key should not be accessible to others, including the cloud service provider
-   If the decryption key is lost, it should **not** be possible to reset it and recover vault data.
-   Decide if you want a recovery option, weighing the risks against the costs of losing access to a vault.
-   Understand **how** the password manager enables password recovery, and **who** will have this ability.

### **3. Multi-factor authentication**

Some password managers support multi-factor authentication (MFA) to better protect users and their passwords. To access credentials with multi-factor enabled, an attacker would need to *know* the master password *and* be in possession of the second factor. Multi-factor support should be used on **all** cloud-sync password managers, and wherever password managers are being used to store passwords that protect access to privileged or other sensitive accounts (such as administrator passwords). 

**In summary:**

-   Ensure the multi-factor options available are suitable for your users, your *organization* and your other policies; for more information refer to the *BCSF*'s guidance on [multi-factor authentication](/bronze-training/passwords/multi-factor-authentication-online-services).
-   Some options may require a setup cost (such as buying tokens).

### **4\. Data export**

Some password managers can export all the stored passwords as a plain text file. This allows you to easily export data from one manager to another if you decide to replace your current product. However once exported, by either a legitimate user or an attacker, the passwords are unprotected.

**In summary:**

-   If data export is supported, the function should be protected to avoid accidental or malicious export.
-   An administrator should be able to disable or audit the export function.
-   You should have a clear policy on when it is acceptable to use this feature, and guidelines on how the export file is handled.  
     

### **5\. Vulnerability disclosure and patching**

Like all software, password managers may contain vulnerabilities that can be exploited by attackers. You should consider a vendor's approach to patching vulnerabilities, and how the products will be updated.

**In summary:**

-   Check that the vendor's response to a previous vulnerability was timely and sufficient.
-   Ensure the vendor provides regular updates and has good disclosure policy in place.
-   Check how the software gets updated; this needs to work with your *organization*'s patching processes so that updates to the password manager are installed quickly.

### **6\. 'Auto-fill' browser extensions**

Most password managers can automatically enter a user's credentials in websites, often through a browser extension. This makes it much quicker and easier for a user to  - for example -  log in. It can also protect against phishing, as password managers can be better than humans at detecting fake websites. Password managers should only share your password with the correct website, and should prevent malicious websites from accessing all your passwords.

**In summary:**

-   The password manager should only offer credentials for the site that they are saved for.
-   The password manager should never offer all stored credentials to any website that the user visits.

### **7. Password generation**

Many password managers can generate random passwords for users. This makes it easier for your staff to use unique, long and random passwords across all their accounts. It's important that this feature is clearly signposted to staff when they create passwords.

**In summary**:

-   Ensure the password manager can create passwords that conform to the password policies of the services where they will be used.
-   Ensure that its straightforward for staff to *realize* this feature is available from within the password manager.

### **8\. Security auditing**

Some password managers can assess the quality of a user's passwords, and suggest changes to improve them. These can include:

-   Providing users with an indication of the overall quality of their passwords.
-   Allowing users to automatically reset passwords for commonly used sites and services.
-   Warning users if a website or service they use has been compromised.
-   Highlighting if a password has been reused.

Some password assessments may rate the complexity of passwords, or recommend that older passwords are changed. If these are enforced as policies, they place a huge burden on users. This ultimately encourages insecure workarounds that undermine any security value from these policies. However, enforcing complexity requirements does not place the same burden on people **if supported by password managers**. For more information, please refer to the [*BCSF* Password Policy guidance](/bronze-training/passwords/updating-your-approach).

**In summary**:

-   Encourage people to act on recommendations given by the password manager to improve the quality of their passwords.

### **9. Platform support**

Password managers supported by all your current (and intended) platforms will provide the best user experience. Choosing a product that doesn't work on all your devices will force users to find an alternative password management approach, that may lead to insecure workarounds.

**In summary:**

-   Ensure the password manager is supported on all current and intended platforms (for example Windows, macOS, iOS, Android).
-   Ensure it's compatible with all current and intended browsers (Chrome, Microsoft Edge, Firefox, Safari).
-   Check that key features (such as auto-fill) are available wherever they will be regularly used.
-   Check there's a similar user experience across all the platforms to make it easier to adapt to using it on new platforms.

### **10\. Credentials in transit**

For cloud-sync password managers, sensitive data will be traversing untrusted networks between cloud and client, and vice versa. Data should only be transmitted to your authorized devices and not those of potential attackers. If this data is not protected, an attacker could intercept and read (or modify) the contents.

Due to the varied usage of cloud-sync, the mobile device may be locked while information is being *synchronized* with it. This received data should also be securely protected until it can be added into the vault at unlock/decryption. Insecure encryption will render the vault contents accessible to attackers if they get access.

**In summary:**

-   Ensure that data is protected in transit, for example by adhering to the [*BCSF* guidance for protecting data in transit using TLS](/silver-training/topic-tls).
-   Check that the password manager client (either software or browser based) properly authenticates any devices and users attempting to access the credentials. The *BCSF* recommend strong user authentication (such as multi-factor).
-   Ensure that any received data is protected until it is added to the vault.

---

## Security features to consider for enterprise password managers

Some products now offer *centralized* management of passwords across an *organization*. Unlike some of the other products, enterprise solutions are usually a paid for service. If you are looking to use a product that offers this functionality, there are other security principles to consider.

### **11\. Password sharing between individuals**

The *BCSF* do **not** recommend sharing passwords between individuals, but many organizations face situations where they are not yet able to use the alternatives to sharing, (such as delegating privileges, or alternative authentication methods). Until these changes can be made, enterprise password managers can help mitigate some of the risks of sharing. This might include monitoring usage and making it easier to update the password if someone no longer has permission to use it. For more information about password sharing, please refer to our [password guidance](/bronze-training/passwords/updating-your-approach).

**In summary:**

-   Ensure users can see the difference between shared and individual passwords.
-   Check that the password manager logs who has accessed the shared password, and when.
-   Ensure an authorized person (such as an administrator) can control over who can (and can't) access a password.
-   Ensure that password changes automatically sync between users that can access the password.

### **12\. Access for administrators**

Enterprise password managers usually have someone in an administrator or team lead role, who has escalated privileges. For example they may be able to recover passwords, add or remove people from shared password groups, or assess the quality of people's passwords.

**In summary:**

-   Administrators should **not** be able to see or use individual passwords (unless they are part of a shared password group), but may have the ability to trigger a password reset.
-   Administrator access should be audited.
-   Ensure there's a joiners/leavers process so that when an administrator leaves or changes role, all the passwords they can see (and use) are changed.

### **13\. Policies and auditing**

*Centralised* management allows administrators to set policies on how password managers are used within an *organization*. They may also be able to see an overview of the user's password use.

**In summary:**

Useful controls include that you may wish to consider include:

-   overview of which accounts are in a user's vault (including shared passwords) to assist with the movers/leavers process
-   visibility of a user's password audit score (as described in 8), allowing them to support users to improve their password management
-   auditing and/or mandating the use of multi-factor authentication to access the vault
-   setting the global policies for the master password (this password will need to be remembered so these policies should be designed appropriately)

### **14\. Personal vaults**

Some enterprise password managers offer a personal vault that staff can use for their personal/home accounts, as well as for work accounts. This will help them manage their full portfolio of passwords covering both work and personal accounts, and reduce their overall password burden. Even if you decide not to use an enterprise manager with a personal vault feature, you could still support your users who want to use a password manager in their home lives.

However, there needs to be good separation of home and work passwords. Work passwords should not be accessible from the home vault and vice versa. **It should be very difficult to save a password to the wrong vault by accident**. You will need to consider how this works for your *organization*. For example, if you operate a BYOD policy, or your policies permit the use of personal accounts at work, it may not always be obvious to the user which vault they are currently using.

**In summary:**

-   Ensure it's easy for staff to use the correct password vault. 
-   Check that it's **not** possible to access passwords across vaults.

### **15\. Logs**

Many enterprise password managers provide auditing on how passwords and password managers are being used in your *organization*. To find out more about logging, read the [*BCSF*'s Introduction to logging for security purposes](/bronze-controls/designing-controls/logging-for-security).

**In summary:**

If you intend to make use of logging, we recommend you capture:

-   when password vaults are accessed.
-   what passwords were viewed and/or used
-   the *enrollment* of new devices where the manager will be used
-   the resetting of master passwords
-   failed attempts to unlock

### **16\. Directory integration**

Many enterprise managers offer [Active Directory](https://en.wikipedia.org/wiki/Active_Directory) integration.

**In summary:**

If you intend to include Active Directory integration, the implementation should:

-   be set up so that a user can only see their own credentials.
-   use a well understood, open specification
-   **not** interfere with the directory service's other functions