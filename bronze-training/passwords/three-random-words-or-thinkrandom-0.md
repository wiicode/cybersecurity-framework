---
title: Three random words or #thinkrandom
description: 
published: true
date: 2021-05-28T02:48:50.513Z
tags: bronze, passwords
editor: markdown
dateCreated: 2021-05-27T22:13:14.345Z
---

You're probably aware that there’s a lot of guidance out there on what makes a good password — and it can be incredibly confusing. This blog post should help.

For home users we are working with Cyber Aware, advising that you [create passwords using three random words](n/bronze-training/passwords/use-a-strong-and-separate-password-for-email). You just put them together, like '`coffeetrainfish`' or ‘`walltinshirt`’.

You can choose words that are memorable but should avoid those which might be easy to guess, such as 'onetwothree' or are closely related to you personally, such as the names of family members or pets.

Ultimately, the choices you make regarding passwords are up to you. This blog post is intended to help inform you as you make password decisions and explain a little bit of the cyber security rationale behind our three random words guidance.

---

## Attacking your account

There are some common ways that cyber criminals might try to compromise your user accounts. Many of these relate to the passwords you use, so let's take a look at a few of them:

### **It's obvious**

You should try to ensure that your password isn't easy to guess. We all know that passwords protect things that are valuable to us but that doesn't stop the most common passwords consistently including '`password`', '`123456`', '`qwerty`', '`football`' and so on. Take a look at one of the many 'top 100' password lists to see what form the most common ones take.

### **Somebody else's bad**

There are frequently stories in the media about cyber-criminals breaking large numbers of passwords from sites that have failed to protect them properly. If you are reusing the same password across multiple sites and cyber-criminals crack one site, they might try the recovered passwords on the other sites you use.

### **Keylogging**

There is a type of malicious software that, once on your system, attempts to log the keystrokes you make — including passwords. Of course, this will compromise any password entered, no matter how complex. The best *defense* here is keeping your software current and up to date.

### **Smash the hash**

When you choose a password, if the site is reasonably diligent it won't store that password in a form that can be read directly. It will have been processed by a clever maths function called ‘hashing’.

This function turns the readable password into what appears to be gobbledegook. This is the password hash and it is this that the website stores. The clever thing about hashing is that it's very hard to turn the hash back into the password. As a user, when you return to a website and enter your password, the hash is calculated and compared to the one already stored. If they match, you're in.

If a cyber criminal somehow gets hold of the list of password hashes there are some attacks they can use to try to recover passwords. Firstly they might try a ‘dictionary attack’ — putting lists of known words (including common substitutions such as '1' instead if 'i') through the same function and see if they result in the same hash. If they do, you have the password.

This might sound like a lot of work but with modern computing it really only takes seconds. If this doesn't work the cyber criminal could try to ‘brute force’ the hash. This means trying every possible combination of characters until the password is found. Long random passwords and the inclusion of special characters make this harder for a computer to work out.


## Three random words

If stopping a cyber criminal breaking your password relies on long and complex passwords, where does three random words come from? Well, super-long and complex passwords aren't necessarily the best option for a number of reasons:

### **It's not all maths**

Maths is great, but not at the expense of the users. It is really, really hard for a user to remember lots of complex, unique passwords. What happens is that we come up with coping mechanisms which are well known to cyber-criminals, and which they can and do exploit in order to attack our accounts.

So, ironically, using long and complex passwords sometimes just plays right into attackers' hands. For example using ‘Pa55word!’ may follow the rules of a website, but is a bad password as it's quite guessable. Typically if a cyber-criminal has the hashes to attack they will break them whatever rules are put in place.

### **Salt with that?**

Actually, when a website processes your password it stirs in some other information as well, like your username. This is called salting. Combined with three random words, this provides a reasonable amount of protection from attack.

### **How did they get the hash?**

I glossed over the cyber criminals getting hold of the files containing all of the password hashes. If a website is well designed this should be really hard for a cyber-criminal to do. This is also why we recommend separate passwords for sites that are important to you (like your email) to things like web forums, that aren't. If one website doesn't look after the password hashes properly, that shouldn't allow easy access to the things that are important to you.

### **Hard to guess**

Three well-chosen random words can be quite memorable but not easy to guess. It provides a good compromise between protection and usability.

Ultimately it's your choice of course, but hopefully this blog post has helped to make your password choices a little bit more informed.