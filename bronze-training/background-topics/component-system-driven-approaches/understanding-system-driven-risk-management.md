---
title: Understanding system-driven risk management
description: The principles of system-driven risk management in cyber security.
published: false
date: 2021-03-05T01:44:03.812Z
tags: risk-management, bronze, bronze-training, sourced, component-system-risk
editor: markdown
dateCreated: 2021-03-05T01:32:42.158Z
---

This sections explains the core concepts involved in system-driven risk analyzes, what value these techniques can add, and where they are less useful.

- This piece doesn't aim to provide you a blueprint for implementing these kinds of technique. However, once you've understood these basics, you should be able to use systems-driven standards or frameworks (as they are based on a similar perspective on risk) and understand how they differ from component-driven approaches.
- If you've not already done so, please read Introducing component-driven and system-driven risk assessments before reading this section.

> **Note**: You don't always need to use systems-driven approaches. They can be time-consuming and resource intensive, particularly when you're developing simple IT infrastructure (or using known patterns of development) as these techniques will add little value.
{.is-info}

# What is system-driven risk analysis good for?
System-driven risk analyzes are best suited to identifying risks which emerge from the interaction of all a system's components. These risks can occur without any individual component breaking or being compromised, so they identify risks that component-driven approaches cannot. In small, simple systems, it is possible to identify these interaction risks without any particularly formal approach. However, this becomes unfeasible with larger, more complex systems, which is where system-driven approaches add real value.

The end product of this kind of technique is a set of security requirements for the system you're analyzing. System-driven risk management techniques should enable you to trace these requirements back to a specific outcome that you are trying to avoid, which helps you to prioritize potential security improvements against each other, as well as other types of requirement.

# What is a system?
For the purpose of this guidance, the word 'system' refers to something which aims to achieve a specified function. This function could be achieved by technology, but equally a 'system' could be a group of people, a building or a naturally-occurring pattern of weather. For this reason, it makes little sense to speak about 'systems' without referring to their function, or their purpose. Using this definition, when analyzing a system, it is up to you (and your stakeholders) to define the function of the system you're looking at, before analyzing it.

For example, you could be performing a risk assessment on your organization's website. The server on which your site resides would be an important part of that system, but it wouldn't represent all of it. The system which allows your organization to host a website would include a range of other things, including (but not limited to):

- your Internet connection
- the people who maintain the website
- the database which holds your clients' records as a part of the site
- the organizational policies which govern how the website is managed

In this example, the system you're interested in is not the website alone; it is the system which allows your customers and partners to learn about your organization via the Internet. Defining that system function is the core part of doing a system-driven risk analysis.

# Defining 'function'
If you're talking about systems it is essential that you first state the function that you are trying to analyze. Otherwise, you might end up only analyzing a single system component (such as the website server in the example above) and ignoring the rest. Examples of system functions might be:

- to enable customers to use the Internet to buy our products
- to enable people to travel from London to Birmingham in under one hour
- to enable an organization's staff to produce and share documents collaboratively
- One of the defining features of systems-driven approaches to risk management is that they require a clear statement of the system's function at an early stage of development. A common mistake at this stage is to confuse the system's function with a statement of the problem that the system contributes to solving.

For example, you might state that the function of an online sales website is 'to improve your organization's sales figures'. Strictly speaking, the website's function would be better described as 'to enable customers to identify and purchase your products online, and to enable your logistics division to dispatch them promptly'. This function will contribute to solving the problem of 'improving sales', but it will not completely solve it, and other solutions will also impact upon solving that problem.

A good statement of function needs to be achievable, and it must be possible to verify that you have achieved it. Getting this statement of function correct is an essential part of conducting a system-driven risk analysis.

# Defining a system's 'losses'
In the introduction to system and component-driven techniques, we learnt how the high-level purposes that your system should not achieve (or contribute to achieving) are known as losses. In order to perform a system-driven risk analysis, you need to enumerate the high-level outcomes that you don't want to occur in the operation of your system. In this context, we are just concerned with the actual outcome of a loss.

Here, we are talking about top-level losses that the organization cares deeply about. This works most effectively if you identify a small number of highly significant losses, rather than a large number relatively small ones.

Examples of losses include:

- injury or loss of life
- large-scale fraud against your organization
- breaking the law
- key organizational processes being disrupted

An important part of any system-driven risk analysis is clearly defining precisely which losses that you are concerned about in the context of the system you are operating or designing. Importantly, we're not talking about the way in which a loss could be realized, just the outcome itself. The result of this stage should be a list of losses which you have decided are relevant to your system.

# Putting these principles into practice
In cyber security, system-driven risk analysis techniques are nowhere near as established as component-driven techniques. As such, there are fewer formalized techniques for implementing these principles, and there is greater variation between them. This guidance introduces what the BCSF see as the common features of these techniques, and explains what value they can add.

Any system-driven risk analysis techniques should start with an articulation of function, and the losses you wish to avoid. You would usually expect to see an iterative process of adding complexity to that statement of function, by breaking it down into sub-systems, each of which have their own functions, and by demonstrating how these subsystems control and communicate with each other. At each of these iterative stages, you would explore any possible exposures to losses, and in doing so, you would develop security requirements to avoid these exposures.

One final note of caution: our team has conducted a number of field trials of different system-driven risk analysis techniques over the last few years. On every occasion, there has been a huge cultural barrier to talking about cyber risks to technology systems in terms of high-level losses. Discussions very quickly move on to component-level vulnerabilities before the system-level has been properly analyzed.

# Commonly used system-driven cyber risk management methods and frameworks
This section provides a brief description of some system-driven cyber risk management methods and frameworks.

- We have provided links to specific guidance for each technique. These provide more detail about how each technique works, and how they add value.
- There are many more techniques (not listed here) which apply these principles. The three included below (we believe) best illustrate the differences between these types of technique. If you think there are others which should be included in this page, please get in touch.

## STAMP
STAMP (Systems-Theoretic Accident Model and Process) is a collection of techniques for modeling the causation of accidents. It has been developed by Professor Nancy Leveson and her colleagues at the Massachusetts Institute of Technology. While STAMP originally focused on safety, the STAMP concepts have been adapted into a number of other contexts, some of which accommodate cyber security requirements.

A lot of the language and concepts we introduced in our piece on the principles of system-driven risk assessments have been drawn from the STAMP framework.

## TOGAF
TOGAF (The Open Group Architectural Framework) is a commercially available architectural framework developed by The Open Group. It is an Enterprise Architecture Standard designed to improve business efficiency and manage risk, for instance seeking to provide better return on investments, reducing overheads and improving procurement processes. The framework is based on an iterative process model that can be implemented at different levels across the organization either on its own or integrated with other frameworks. TOGAF supports both the top down (system-driven) approaches and bottom up (component) approaches to risk management described in our guidance.

## SABSA
SABSA is a business-driven security architecture framework with a high-level focus on how organizations generate value for stakeholders. Starting with the organization’s unique configuration of their value chain, the SABSA framework assists analysts in decomposing the process down through number of business architectural layers. The layers progress down through business capabilities, business processes, business services, and from there down into technology services.

SABSA requires analysts to address risk at every layer so that requirements defined at the top of the ‘stack’ are inherited down through the layering and addressed at each layer. High-level, value-generating opportunities could be compromised at any of the lower layers, but this layer-by-layer analysis ensures that a range of different cyber risk perspectives are considered.