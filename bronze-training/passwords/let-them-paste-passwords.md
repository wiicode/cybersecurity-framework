---
title: Let them paste passwords
description: Allow your website to accept pasted passwords - it makes your site more secure, not less.
published: true
date: 2021-06-30T02:54:56.668Z
tags: bronze, passwords
editor: markdown
dateCreated: 2021-05-28T02:15:23.345Z
---

Why do organizations do some websites prevent pasting of passwords into forms? Often no reason is given, but when one is, that reason is 'security'. The *BCSF* don't think the reasons add up. We think that **stopping password pasting** (or SPP) is a bad thing that *reduces* security. We think customers should be allowed to paste their passwords into forms, and that it *improves* security.

## No one knows where it came from

It is a mystery where SPP came from. No one has pointed to a paper, a rule, an RFC (a technical standards document to plan how the Internet should work) or anything else that started it off. If you know of one, let us know using the comments form below. We believe it's one of those 'best practice' ideas that has a common sense instant appeal that may have made sense once. Considering the bigger picture today, it really doesn't make sense.

## So why is password pasting a good thing?

The main reason why password pasting improves security is because it helps to reduce password overload, something that we cover in our [Password Guidance](bronze-raining/passwords). Allowing the pasting of passwords makes web forms work well with *password managers.* Password managers are software (or services) that choose, store and enter passwords into online forms for you. Password managers are very useful because they:

-   make it much easier to have different passwords for each website site you use
-   improve your productivity and reduce frustration by preventing typing errors during logins
-   make it simple to use long, complex passwords

Disclaimer: although password managers can offer better protection than - for example - keeping your passwords in a normal (and so unprotected) document on your computer, they are not a silver bullet to solve all of an *organization*'s password problems. We'll write more in a future blogpost about things to consider when picking a password manager.

Imagine if you didn't have a password manager, or even that unprotected document on your computer with your passwords in it. Without password managers, it would be pretty much impossible to remember all your passwords. To cope without them you'd have to do some of these bad things:

-   re-use the same passwords on different websites
-   choose very simple (and so easy to guess) passwords
-   write passwords down in places that are easy to find (like post-it notes next to the screen)

This is why we think SPP is bad, and allowing password pasting is good. The pros outweigh the cons, and by a lot.

## Why stopping password pasting (SPP) is wrong

There are other reasons that are used to justify SPP. The small and misleading grain of truth in these reasons can sound very persuasive. Here's why they're wrong.

### **Justification 1: 'Password pasting allows brute force attacks'**

If password pasting is allowed, that represents a vulnerability where malicious software or web pages could repeatedly paste password guesses into the password box until they break your password.

This *is* true, but it's also true that there are other ways to make guesses (for example through an API) that are just as easy for attackers to set up, but are **much** faster at guessing. The risk of brute force attacks using copy and paste is very small.

### **Justification 2: 'Pasting passwords makes them easier to forget, because you have fewer chances to practice them'.**

It's true - in principle - that the more times you recall something, the easier it is next time.

In the real world though, people are made to have passwords for things that they hardly ever use. This means there isn't enough time to practice, and therefore little chance of remembering. This whole justification only works if you assume, to begin with, that users *should* always have to try and remember their passwords - and that's not always true.

People are also made to have passwords for things they use so often they couldn't forget the password even if they wanted to (which is quite inconvenient if you're forced to change the password regularly), and typing in the rotten thing again and again eats into their day. Password managers are a stick these people lean on, and SPP kicks it away.

### **Justification 3: 'Passwords would hang around in the clipboard'**

When anyone copies and pastes, the copied content is kept in a 'clipboard' where it can be pasted as many times as they want. Any software installed on the computer (or any person operating it) has access to the clipboard, and can see what's in there. Copying anything usually writes over what was already in the clipboard and destroys it.

Many password managers copy your password to the clipboard so they can paste it into the password box on websites. The possible risk is that an attacker (or malware) will steal your password before it's erased from the clipboard.

Passwords remaining in the clipboard might be more of an issue if you're manually copying and pasting your passwords from a document you have on your computer. You might forget to clear the clipboard. However it's not much of a risk because:

-   Most password managers erase the clipboard as soon as they have pasted your password into the website, and some avoid the clipboard completely by typing in the password with a 'virtual keyboard' instead.
-   Viruses installed on your computer can have clipboard copiers on them, and grab your pasted passwords. That's still not a good reason for SPP though; when your computer gets infected you can't trust it *at all*. Viruses and other malware that copy the clipboard nearly always also copy every letter, number and symbol typed on your computer, including your passwords. They would steal your password whether or not it was in the clipboard, so you're not really gaining much by SPP.

Rather than stopping password pasting, help your computers to avoid catching viruses in the first place by following our [guidance on securing enterprise IT](/bronze-training/background-topics/enterprise-technology-security). And install software updates - the IT version of eating your fruit and veg. It's one of the very best ways of securing your computer.

## Don't just take our word for it

You don't have to take our word for it that stopping password pasting is bad. See [Troy Hunt's blog (with a History lesson for us all)](https://www.troyhunt.com/the-cobra-effect-that-is-disabling/), or [this article in Wired](https://www.wired.com/2015/07/websites-please-stop-blocking-password-managers-2015/).

**Improve your security by supporting your users. Let them paste passwords.**