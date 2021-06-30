---
title: Component-driven and system-driven approaches
description: An overview of component-driven (bottom up) and system-driven (top down) risk management techniques.
published: false
date: 2021-06-30T01:59:42.304Z
tags: risk-management, bronze, bronze-training, sourced, component-system-risk
editor: markdown
dateCreated: 2021-03-05T01:08:38.314Z
---

# Introducing component-driven and system-driven risk assessments

> An overview of component-driven (bottom up) and system-driven (top down) risk management techniques.
{.is-info}

{.grid-list}
- [Click here for detailed information on component-driven management.*Component-driven risk assessments are the most mature and common types of assessment within the cyber security profession. This section describes what component-driven techniques have in common, where they add value, and where they don't.*](/bronze-training/background-topics/component-system-driven-approaches/understanding-component-driven-risk-management)
- [Click here for detailed information on system-driven risk management.*System-driven risk analyzes are best suited to identifying risks which emerge from the interaction of all a system’s components. These risks can occur without any individual component breaking or being compromised, so they identify risks that component-driven approaches cannot. In small, simple systems, it is possible to identify these interaction risks without any particularly formal approach. However, this becomes unfeasible with larger, more complex systems, which is where system-driven approaches add real value.*](/bronze-training/background-topics/component-system-driven-approaches/understanding-system-driven-risk-management)
{.links-list}

## About component-driven approaches
In cyber security, risk is usually described in terms of the component parts of a system. In this view, risk is assessed as being some combination of the value of a given system component, and the likelihood that it will be compromised in some way. More specifically, this requires an assessment of the threat that these components face, their vulnerabilities and the business impact that a compromise would cause.

This type of approach allows analysts to identify specific risks faced by specific components within the system. It then allows these risks to be prioritized according to the severity of the risk's impact or the ease with which the vulnerability could be exploited by a threat. The purpose of prioritizing risks in this way is to mitigate the worst risks first, where possible.

## About system-driven approaches
An alternative approach focuses primarily on the goals or purposes of the system (rather than components). We call such approaches system-driven views of risk, because they focus primarily on the whole system, rather than individual components.

System-driven approaches require risk analysts to start by stating a system’s high-level purpose. From there, you iteratively add more detail to that statement, as a way of designing how the high-level purpose may be achieved. There is a focus on understanding how parts of the system interact with each other. Approaches like this will be very familiar to systems engineers, and others involved in iterative design techniques, where these ideas are commonplace.

Where does risk come into this? As well as thinking about the purposes that a system should serve, a system-driven risk management technique would also consider the high-level purposes that the system should not serve. We talk about these in terms of 'losses' which could occur in the course of a system's operation. For example, if you are designing a system which controls an automated security door, the system’s purpose is probably to let people in and out. A loss that you might care about would be letting through unauthorized people, or injuring people by trapping them in the door’s mechanism.

This concept of losses might seem obvious. However, our experience shows that these high-level descriptions of what the system must not do are very rarely considered at the beginning of a project life-cycle, unlike purpose, which is considered. Losses are usually only considered when a system’s design is reasonably mature, when you already have an understanding of what the system might logically look like. This is part of the reason for the common complaint that security 'is bolted on, not baked in'.

## Using Rasmussen's hierarchy to distinguish risk assessment techniques
To help examine how component-driven and system-driven techniques relate to each other, we can draw on Jens Rasmussen’s Abstraction Hierarchy, which is illustrated below.

![jens.png](/article_images/jens.png)

This model introduces the idea that you can look at systems at different levels of abstraction. Considering just the top three layers of illustration allows us to think about the system in conceptual terms. That is, we're focusing our analysis on what should be achieved by the system (rather than how it should work). Component-driven techniques are about analyzing what could go wrong at the bottom two layers of this hierarchy. Here, you are concerned with things that physically exist, or their representations, such as detailed architecture diagrams detailing specific technology decisions.

Separately, system-driven techniques consider the system's high-level purpose and losses. The aim is to identify ways in which losses could be realized, as a consequence of the conceptual design of your system. At this level of abstraction, concepts such as threat and vulnerability, as they are used in component-driven methods, don't make sense. Here, you are looking for ways in which the system could realize any losses

The reason for introducing this framework is to demonstrate that component-driven and system-driven risk management techniques analyze risk in fundamentally different ways, but that they both support each other. They are both valuable risk management tools, when applied to the right kind of problem.

## When to use component and system driven technqies
Component-driven and system-driven techniques add value in different ways; neither is 'better' than the other. However, each technique is better suited to certain kinds of risk management problem:

- Component-driven approaches are useful for exploring your exposure to known technical vulnerabilities. For example, there might be a single computer in your organization that you are unable to patch or upgrade for operational reasons. This is common with some types of operational technology. A component-driven risk analysis can be used to explore how the vulnerabilities in that unpatched machine could impact on your organization. This kind of analysis can identify safeguards which can be put in place around this unavoidably vulnerable computer.
- System-driven approaches are useful when analyzing large and complex systems. In particular, they can help you to explore interaction failures. These occur when individual components within the system are working precisely as they should, but that there is some flaw in the way in which these components interact with one another which makes it possible for a security breach to occur.

This is summarised in the following table.

![component_vs_system.png](/article_images/component_vs_system.png)

Component-driven and system risk management techniques can be used alongside each other. For example, you might use a system-driven approach to ensure that security risks are conceptually identified before any specific technology decisions are made, and then switch to component-driven analysis once you are committed to adopting a particular solution.

## Find out more
If you're keen to get stuck into practicalities, we have produced separate guidance which lists some common frameworks which apply the principles of component-driven and system-driven risk analyzes.