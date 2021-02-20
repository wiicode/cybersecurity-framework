---
title: The Tale of the Hostage
description: Quick background to ransomware
published: true
date: 2021-02-20T18:42:59.751Z
tags: bronze, bronze-training
editor: markdown
dateCreated: 2021-02-20T18:42:59.751Z
---

# The Tale of the Hostage.

Debbie was doing her work, at Nelson & Murdock, PLLC, when an email, seemingly from a co-worker, arrived with instructions to urgently review a document. She opened it, did not notice anything unusual, and became distracted by a phone call.

A few hours later Lee attempts to open a document stored on the file server and receives a warning that it had been encrypted along with a poorly written ransom demand. Surely this is just some malware, time to call Steve and tell him another computer has gotten infected. Steve triggers an anti-virus scan which has little to report, so he proceeds to verify an infection but finds none.

A little later, more reports come in, and panic ensues: “the server is infected!”  More frantic calls to Steve reveal that there is no infection on the server, but the evidence is piling up. There are files encrypted everywhere and it is now obvious that this is ransomware.
Like most small companies, this business is busy doing things, and those things do not include preparing for such eventualities. However, the lack of awareness is the tip of the iceberg, leaving much more to be discovered.

Debbie was at first oblivious to the event, while Lee mis-interpreted the incident. Only partially useful information reached Steve, clobbered with the assumption the server was infected. As the focus turned on the server, Debbie may have connected the dots, but chose to say nothing. Steve will fix it.
Although proper awareness training could have stopped the spread early by the crudest measure of unplugging the machine or the server from the network, by this point documents and databases are encrypted and it is too late. Meanwhile, Steve is still in the process of verifying the source.

While attempting to verify the choices not to invest time and money into more sophisticated technologies become obstacles. Nelson & Murdock does not have a sophisticated web filter and firewall that can more easily show traffic and attempt to stop bad things. They do not have mobile device management software to help inventory all the systems and audit simple things like anti-virus installations. Business anti-virus software is present on some systems, but unfortunately not all; it is unlikely to have stopped the infection but it could have logged an event if it was installed on Debbie’s machine. Steve is operating with blinders on struggling to find the culprit.

Operating with binders on is only a part of the struggle. Steve requests password resets for all users to try to secure the accounts, but that triggers a torrent of ancillary support issues. Nelson & Murdock has used “justice” as their password since 1999, for everything. Suddenly staff cannot access their email, including the one from Steve that alerts them of the crisis.

If only it stopped there, but Steve is horrified to learn that a Mark, also a paralegal is a domain administrator, and soon realizes everyone else is too. Taking a moment to inquire about this curiosity, Steve learns that privilege was elevated for all staff because they were unable to access the Christmas Card List stored on the server; it was saved to a protected share and this “solved” it. Although the elevated privileges have little impact on the power of the ransomware, they just made verifying and isolating the problem exponentially more difficult.

Steve knows that there may be a computer that is under the control of the attackers, and any effort now to restore is pointless. The quest to find it continues, although he knows the ransomware erased itself fully after completing the encryption process. It is gone, and little trace of it will ever be found.
Steve does get lucky, as he discovers Debbie’s user folder has a few encrypted files while the others do not: a clue. A short bit of digging and it becomes evident Debbie’s computer was the cause, but she has chosen to remain silent on the topic. At least Steve knows the source of the machine, and isolates it. Time for recovery to begin.

This is where things go from bad to worse. The image backups were saved to a network attached storage device with file shares which were accessible to the ransomware. The backups are also encrypted. In the absence of a restore capability, and much anguish, Steve and management decide that the only choice is to pay the ransom and get the encryption key.

The FBI’s IC3 lab recommends paying ransom when no restore is possible, although they caution that doing so has no guarantee that a decryption key will work. They follow the instructions in the ransom note, and choose to pay the ransom in BitCoin as instructed.

Steve has never purchased a BitCoin, nor is he willing to start now. Nelson and Murdock carry the burden of resolving this piece of the puzzle. Fast forward, and Nelson and Murdock are meeting a teenager in the parking lot of a local McDonalds trading several thousand dollars in cash for a scribble with information about a BitCoin wallet that has the anonymous and untraceable internet currency. At least they are contributing to the local economy.

The decryption key works, but takes time to complete the job. By now the firm has paid $8,421 in ransom, $6,600 in Steve’s time, and committed to $18,000 system upgrades to beef up the network, firewall, storage, threat detection, and recovery capabilities. All of it, however, is trivial compared to the business losses suffered over a period of a week unable to do any work.

As they later found out, none of it was covered by insurance, as the business and data protection coverage had sufficient exclusions. Nelson & Murdock failed to mitigate risks. Among the many failures they cite in their review, is the failure to adequately secure their e-mail system with aggressive spam filtration and DomainKeys Identified Mail (DKIM) that could have helped stopped the email message before it ever arrived in the mailbox.

Unknown to anyone at the firm, shortly after Debbie first opened that attachment, an e-mail reply came from a contact in her address book with the question “I can’t see anything in the attachment, can you please resend?”.

## Lesson: Ransomware.

Ransomware is a form of malware that targets both human and technical weaknesses in organizations and individual networks in an effort to deny the availability of critical data and/or systems. Ransomware is frequently delivered through spear phishing emails to end users, resulting in the rapid encryption of sensitive files on a corporate network. When the victim organization determines they are no longer able to access their data, the cyber actor demands the payment of a ransom, typically in virtual currency such as BitCoin, at which time the actor will purportedly provide an avenue to the victim to regain access to their data. Recent iterations target enterprise end users, making awareness and training a critical preventative measure. In 2015, the IC3 received 2,453 complaints identified as Ransomware with losses of over $1.6 million.