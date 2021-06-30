---
title: Intelligent security tools
description: Assessing intelligent tools for cyber security
published: false
date: 2021-03-03T19:39:34.324Z
tags: guidance, bronze, bronze-training, security-operations
editor: markdown
dateCreated: 2021-02-21T03:52:24.497Z
---

# Introduction
Artificial Intelligence (AI) is fast becoming the 'next big thing' in security. There are a huge number of 'intelligent' tools coming to market, each one promising to solve problems better and faster than traditional approaches.

But do intelligent tools actually outperform humans in every case? How can you determine whether an intelligent tool is right for you? And who would fix your intelligent systems if they were to let you down? This guidance will help you find answers to these, and many other questions.

Though the future will likely see AI making significant contributions to many fields, the picture at present is far from clear. Intelligent tools are not without their limitations. Poorly trained AI can have biases and vulnerabilities that we are only just beginning to understand.

Ultimately, if you buy the wrong tool for the job, your problem will remain unsolved.

# How this guidance helps
This guidance is designed for those looking to use an off the shelf security tool that employs AI as a core component. It may also be of use to those developing in-house AI security tools or when considering AI for some non-security business function.

If you are thinking of incorporating AI into your security systems, there are a few things you need to understand first. You should clarify your own needs, understand the nature of the technology underlying any products you're considering, and finally, determine whether an 'intelligent' solution will give you a net gain in security. 

Following a brief primer on AI, this guidance divides the consideration of intelligent security tools in four sections.

Each section poses a series of questions which will help you determine whether an intelligent solution is practical and advantageous for your particular security needs.

# Defining artificial intelligence
Discover what AI is, it's various methods and implementations, the kind of problems it's good at solving and those it's not well equipped for.
Before we move on to a detailed consideration of the issues related to intelligent security products, it's worth taking a moment to think about Artificial Intelligence (AI) as a technology.

This section is intended to give you a broad brush introduction to AI, it's various methods and implementations, the kind of problems it's good at solving and those it's not well equipped for. We'll also highlight some of the most important vocabulary.

There are many definitions of AI in use, and very little agreement. Here we describe how we will use the term.

## The essentials
### How AI works in simple terms
Modern AI is usually built using machine learning algorithms. These find complex patterns in data, which can be used to form rules which are useful to us.

For example, a machine learning algorithm could find similarities in pictures of cats. If you tell it which pictures are of your cat, this can form rules that allows the system to recognize your cat. When you show it a new picture, it will be able to predict whether the new image is your cat or not, based on it's learned definition.

For us, a key part of AI is that it takes those patterns and definitions and uses them to automate a decision. For example, you could just use this to automatically file your photos. Or you could build this into your cat flap, along with a camera, with the action that it only unlocks when it recognizes your cat. The decision to let cats in, and therefore your 'security', has been automated.

### What can AI currently do?
AI is very good at solving well bounded problems, where the solution, and the method to find it, iscompletely contained within the data and feedback provided. Here they regularly excel beyond human abilities, for both speed and accuracy.

A good example of this is game playing, an area where AI has had some great successes. Chess and Go being two highlights. When playing a game, the rules form the bounds of the problem. The data from which the AI learns is all the previous games it has played. The game board becomes the AI's whole world, nothing else needs to impact the decisions it makes while playing.

Another fruitful field for AI has been image recognition and generation, where the problems are to predict which group a new image belongs to, or create a new image of that type. All the information required to classify, or create an image, is contained in the image data provided.

### What is AI not so good at today?
AI is less good at solving problems where you need additional context to reach an answer, even if that context would be 'common sense' for a person. It may be possible to provide some of this context to an AI in the form of additional data, a model, or feedback from a human, but expanding the bounds of the problem is often expensive and may result in poor performance if expanded too far. At this point, the decision should be passed to a person who is able to use their knowledge of the context to reach a decision.

Cyber security often involves situations where context is important. Accessing a sensitive document might be a suspicious action for one person, but normal behavior for another. Installing updates is essential for most of your business, but a business risk where it causes compatibility issues with critical software. This is why it is important to find a tool that can work within the context of your business. And why you may need to ensure that a person has the opportunity to step in and apply their knowledge.

The technology underpinning AI is constantly evolving, and we can expect any limitations to be continually tested and redefined. Despite it's rapid pace of change, you need to be aware that there will be some areas where it is too difficult (or expensive) to develop AI capable of solving the problem.

### Intelligent tools for cyber security
If we want to automate cyber security tasks at scale, we need the ability to process data in quantities beyond the capability of any human being.

To do this we have a wide range of tools available, things like AV and firewalls. Until recently, however, these have worked on manually developed rules. Now, the tools are increasingly learning the rules for themselves, using intelligent algorithms to derive these rules directly from our data.

These new rules can make the tool very powerful, but they also make them less predictable.

## AI Terminology
A brief primer on some of the most common AI-related language.

### Rules
A standard rule in automation may take the basic form, 'if this, then that'.

In traditional automation, we would have to identify and explicitly program the 'this' and 'that'. AI looks for patterns in data to find it's own 'this'.

This is powerful because we often find it very difficult to identify and describe the 'this' in a way that the computers understand.

For example, how could we describe an image of a cat to a computer with sufficient accuracy to satisfy the condition, 'if the image is of my cat...?' 

In cyber security, the condition could be, 'if the website is suspicious', 'if the image is of an employee', or 'if network activity is abnormal'. These, and many other things, are impossible to define manually.

#### If this then that

In many intelligent tools, we still manually program the 'that', because we know what we want the possible actions to be. In the cat example, we want to unlock the cat flap. So, the AI takes care of, 'if the image is of my cat'. Then we manually add the rest of the rule, 'then unlock the cat flap'. In cyber security this could be 'if the website is suspicious, then block', 'if the image is of an employee, then give access', or 'if network activity is abnormal, then show a warning message'.

#### Beyond that

Some modern AIs find their own 'that' by trial and error, using an ultimate goal as the criteria for a successful rule. For example, winning a chess match. This needs a huge number of trials to learn and usually can't be done in real time. Results are achieved by modelling the environment and simulating the trial and error process.

This is not commonly used in cyber security tools, because the ultimate goal of cyber security is difficult to measure and we cannot model all the variables necessary to allow the AI to learn through trial and error. There is also a risk that the AI will find a novel solution that is detrimental. For example, keeping all the computers switched off would fulfilll the goal of preventing attacks, but our common sense tells us this is not a viable option.

### Model
The rules are stored in a trained model. An AI can be made up of multiple trained models, each with their own rules, which are then combined to make the decision.

### Learning and Training
Learning and training are the terms we use to describe the process whereby an AI finds or updates its rules. AI does not learn like a human. People can learn a fact by simply being told a few times. An AI has to 'see' this fact in the data at a high enough frequency to detect a pattern. This is the reason why you need such high quantities of data to train an AI. It is also why it's difficult to correct a mistake.

Machine learning algorithms are the computer algorithms that perform this learning process.

### Data
The data used by an AI can take many forms, such as a traditional data set, feedback from interactions with humans, or the experience of success/failure during the trial and error process.

#### Data quality

The quality of an AI is highly dependent on the quality of the data used during training and operation. There are certain attributes we look for in high quality data, such as:

- **Completeness** - If there are blanks in the data - for example fields left incomplete - the AI will only have part of the information it needs to train or make decisions. This will lower the accuracy of any output, as some of the patterns in the data can't be discovered. 
- **Diversity** - If all of the examples an AI uses to train look the same, then the capability for the AI to learn anything outside of those few cases is limited. A diverse data set for training will look to have a wide variety of both desirable and non-desirable characteristics for the AI to learn from. A system can only be as good as the data that it's trained on, having a diverse data set will mean that a greater variety of cases can be addressed in the trained system. 
- **Accuracy** - The way data is presented to train an AI is important. Misrepresenting the data being processed by the AI - for example through incorrect labelling - will result in a less reliable trained system. In the live system, this will result in misclassifications and unwanted behaviors from the AI.

### Intelligence
AI today, and for the foreseeable future, is not intelligent in the same way as humans. They cannot reason, feel or apply common sense to a problem.

Current AI is just a new way of processing data in our computers, where data goes in, a handle is turned and information comes out. True intelligence or 'Artificial General Intelligence' is still the stuff of science fiction.

### Black boxes
A black box is part of a program where we cannot see or understand what is happening. The input data goes into the black box and the output comes out. We don't understand how the output is derived from the input. The trained models produced by many machine learning algorithms are black boxes by nature. The science simply has not advanced to the point where we can really understand the process.

The models produced by some machine learning algorithms are not black boxes - it is possible to understand how their decisions are made. In addition, there is extensive research underway in academia and industry into explainable AI. In other words, looking to make black box algorithms understandable.

### Impact
Most intelligent tools will be carrying out some sort of automation, but the way this affects the real world will vary.

For example, some tools will automate the process of deriving information from the raw data, providing a warning or a suggested action. How that information is used will ultimately depend on the person who receives the information.

In other cases, the tool will be the one acting, automatically, on the information. There will be no human in the loop.

### Adaptation
One of the big selling points of many intelligent tools is that they can continue to learn from new data and feedback as you use them, allowing them to adapt to new scenarios. This makes them more resilient to new situations, but it also means that your tool may behave in a way that is unpredictable, making it more difficult to gain assurance that it is working correctly.

### Bias
While learning, an AI will learn any biases contained within the data provided. This could be from the original training data, or feedback provided by an operator.

Biases impact the quality of data being used to train the AI. AI trained with biased data are essentially being given erroneous patterns to find, which can prevent them from finding the real patterns that we want them to find. This can reduce the accuracy of the AI.

For example, if you give feedback on only half the problem, the AI will continue to learn based on the assumption that the other half was correct. This could potentially create problems as these issues would remain undetected.

AI can also learn the prejudices of operators. If, for example, an operator provides biased feedback against certain individuals, this may get embedded into your system, leading to discriminatory (and potentially illegal) decisions.

# Establishing the need
Understand if an intelligent tool is right for the cyber security problem you are facing and discover some key points to consider when choosing one.
Intelligent tools are often sold as the solution to many of the problems and challenges we face in cyber security. They can perform with accuracy levels far beyond simple rule based tools and can automate processes on a scale that would be impossible for people to achieve.

However, there are many reasons why an AI-enabled tool may not be right for the issues you face.

The principles detailed in this section cover some of the key points you should consider when choosing an intelligent tool.

## Comparing intelligent tools
When searching for security products you will naturally want to compare the relative merits of the solutions available to you. 

In mature tool classes, such as antivirus, it's possible to compare like for like when purchasing.

However, this is not always possible with new intelligent tools, since:

- Their purpose may be to solve problems where there is no existing solution
- They might share the purpose of a well established tool, but aim to do this in a new 'intelligent' way
- They may be the only product on the market that has this purpose


## Responsibility
We cannot advise on the utility of every possible function promised by new tools. However, it should be noted that tools will generally have an impact on your system in one of two ways. Either they will give people information to inform their decisions and actions, or the action will be fully automated. In both cases there is a question about who is responsible for the actions taken.

On the face of it, a tool which simply supplies the user with information leaves overall control in the hands of the person acting on that information. However, there is no guarantee that the operator will detect mistakes and may just become accustomed to following the tool's recommendations. In this scenario, effective control and responsibility have been given over to the tool.

## Principles
These principles will help you identify tools which have functionality suited to your problem and way of working. They also highlight the risks of handing over tasks to a tool that may sometimes be unpredictable.

### 1. Does the product aim to solve a problem that is important to you?

Before considering an intelligent tool, you need to think about the kinds of security problems that you face as an organization.

It's important to be sure you have a real problem which is not being addressed by other means. You should explore whether augmenting your current approaches would be a sufficient remedy. This entails a clear understanding of the risk which your problem poses to your organization.

Maintaining your current solution in tandem with any intelligent systems will not only ensure you have a fallback you understand, it will also give you a baseline against which to measure the outcomes produced by the AI based approach.

You should also think about how a solution might impact your business functionality, ensuring it will not impede core operations.

Once you have an intelligent tool in use, you will want to establish whether it is performing it's intended task. Understanding your issue, and your current mitigations, before implementing a new tool, will help you establish the value of the tool once it's up and running. You should also take the time to consider if it is better to use the new tool to augment your current processes, rather than replacing them entirely.

#### Establishing utility

- How does the decision, task, or automated action of the tool, contribute to the security of your organization? What is the impact of this being incorrect?
- If the tool provides information, who will be using this information? Will this information help them make decisions or perform their task? 
- How would the tool improve on the information already available? How will it improve the actions already taken?
- What process is currently used to make the decision, or undertake the task, or action? Is the tool going to augment this process, or replace it?

### 2. Is an intelligent tool right for this problem?

Sometimes an intelligent tool will not be the right solution for your problem.

There are some problems that AI will struggle with. And, even if a problem is solvable by AI, you may still find that it's quicker and cheaper for a task to be undertaken by a person.

There are also some problems that cannot be fully automated for legal reasons. For example, GDPR puts restrictions on automated decision making.

#### Complexity

AI is much better than simple rule-based automation at handling complex tasks. In fact, this is the primary purpose of many intelligent tools.

However, AI will also introduce additional complexity into your system, reducing your ability to understand the behavior of your system, making it potentially more unpredictable.

This unpredictability could introduce new vulnerabilities to your systems, and these could potentially be exploited by attackers.

#### Black box syndrome

You may face scenarios where you need to understand or justify how a security-related decision was made. This can be extremely difficult with intelligent tools, since the algorithms used in many of them are 'black boxes'. This is not just a proprietary problem - we simply do not understand enough about how these algorithms reach their decisions to give a full elaboration of 'why' a particular choice was made.

As the complexity of the tools increases, there is a risk that it will become more difficult to understand how decisions are reached. Ongoing research into Explainable AI may be able to provide more insight in the future, but for now, it remains one of the limitations of the technology.

If you feel that understanding how a decision was made is a requirement of your problem, then you should look for a tool that offers this ability, or you should use an alternative method to reach that decision.

#### Establishing appropriateness

- Is this a task that should be automated by AI? Are there any legal considerations?
- Is there any advantage in using AI to automate this process, or is it best done by a person?
- Do you need to understand how decisions are reached? Is this information available in the tool?

### 3. Consider the governance of this information or action

Handing over actions to an intelligent tool means key decisions may be taken without a human having the opportunity to intervene.

Even if, in practice, a person is ultimately responsible for carrying out the action suggested by the tool, they may not be given sufficient information to understand when they should challenge the decision, or might not feel supported enough to do so. 

This could be particularly difficult where decisions are being made in real time and the operator needs to respond quickly.

#### When to intervene
You need to understand how the intelligent tool will impact decisions made within your organization, and who may be expected to intervene, to prevent mistakes.

Ultimately, you should know who is accountable for decisions and actions made or influenced by the intelligent tool. This person, or persons, should have the opportunity to act to change the decision made by the tool, and feel enabled to do so.

Unfortunately, some tools provide little or no opportunity to intervene. Whenever this is the case, the associated risk must be recognized by a suitable risk owner, when choosing the tool. Where intervention isn't part of the design, the only way to change a decision is to bypass the intelligent tool entirely. You should consider the alternative ways of making those decisions independent of the tool.

#### Sensitive information
You should think carefully about the information produced by the tool. It could be personal or sensitive, or require actions beyond the capabilities of the person receiving the information. 

For example, tools observing the behavior of your staff may inadvertently reveal information about their personal lives, and tools scanning for vulnerabilities may report far more than can be acted upon.

Those receiving this information need to be supported so that the information is properly handled, and they don't inadvertently end up carrying the risk of holding that information.

#### Understanding the risks

- Consider the potential consequences of handing over control of an action to the tool. What could happen if it doesn't perform correctly?
- What opportunities do the operators have to prevent or change the action taken by the tool? What processes are in place to ensure errors don't have catastrophic impacts?
- Who will need to account for the decisions made by the tool? Do they have the information needed to understand how the tool reached its decision? Do they have the ability to ensure mistakes are not repeated?
- Who is responsible for carrying out actions suggested by the tool? Is that person able to take a different action if needed, and will they be supported to make that decision?
- What are the handling requirements for the information produced by the tool? What processes will need to be put in place to ensure it is handled correctly?
- Who is responsible for the information discovered by the tool? Are they sufficiently trained to know how to handle and act on the information? 

# Dealing with data
Discover some guiding principles that will give your intelligent tool the best chance of working effectively, using the right data and handling it correctly.
Many intelligent tools require data about your organization in order to function. This data is processed by the tool to either determine an action, or provide information to the user. It may also be used to further train the tool, allowing it to adapt to new situations.

Having the right data, and ensuring it's handled correctly, is a very important consideration forintelligent tools generally, because the quality and quantity of this data will determine the how effectively your tool functions.

## Principles
Following the principles in this section will give your intelligent tool the best chance of learning its task well.

### 1. Ensure you have the data your tool requires

The function and value of many intelligent tools will be completely dependent on the data you provide.

Initially, you will need to understand what specific data will be used by the tool, why it is needed, and what format it needs to be presented in.

Following this, you need to find out what parts of this data are currently being collected and ensure they can be made available to the tool. If the data is not currently available, then the method by which that data can be collected needs to be made clear.

Before you purchase any tool, you should have a defined method for obtaining all the data it requires. 

#### Quality and quantity
While you may have access to the right type of data, you should also check that you have access to data of sufficient quality and in sufficient quantity, for the tool to work.

#### Rules and regulations
Care needs to be taken in verifying that you are able to use the data required by the tool.

Check that the use of any sensitive data complies with your organization's data handling processes and associated regulations. For those unclear wanting further support, the Information Commissioners Office (ICO) have provided some insights and advice for how to approach this.

You should consider whether you can anonymise the data, such that it is no longer sensitive. If this isn't possible, then look to minimize the number of data fields needed for the tool to operate, especially those involving sensitive data. You should verify with the vendor that the tool can still provide the desired functionality without using some or all sensitive data.

#### Priorities
There may be some data that is absolutely essential to the operation of the tool, while other data may simply enhance its accuracy, or enable additional features.

For essential data, it is important to know why it is needed, and what will not operate correctly without it.

For non-essential data, you should understand what extra performance is enabled.

#### Establishing data requirements
- What data does the tool need to function correctly/effectively?
- Are you able to use this data in this way? Are there any legal (or ethical) restrictions on how you can use the data?
- Discuss how resilient the tool is to poor quality data with the vendor. Ensure your data is available in sufficient quantities, and at a suitable quality, to get good performance from the tool.
- What data could you use to gain additional functionality? What functionality does that data get you?

### 2. Understand the costs and risks involved in collecting the data

For some tools, your systems will already be producing the data you need. For others, it may need to be specially collected. This could entail additional expense.

You should determine the costs associated with collecting and storing the data, as these might not be included in the cost of the tool itself.

You should also understand how you will collect and store the data your tool requires before purchase. This way you can be sure you'll be able to use it as planned.

Note that the stored data itself may be a target for attackers. If you can gain valuable insights from it, so can your attackers. In addition to data theft, there is also a concern with data tampering. If an attacker can tamper with the data that's being collected, it's possible that the data could be manipulated to influence the decisions being made by the tool.  

#### Determining data availability

- New tools may be required to collect the data - if it's not already available on your system. This cost should be factored into your purchase
- For additional data sets, decide if the added functionality is worth the additional collection, storage and protection costs
- For more information on collecting, storing, and protecting data, see our logging guidance

### 3. Ensure that the data will be handled correctly

Once collected, the data needs to be passed to the tool for processing. Some tools run within your system and the data does not leave your estate, whether this is on site or in the cloud. But in some cases, your data may be sent to and stored by the vendor for processing.

Here, your data may be combined with other's to build a much broader picture of threats. This could potentially create a much more powerful tool, but, since AI and machine learning are still new technologies, there are still unanswered questions about how much might be revealed about your data to those with access to the trained tool. This could include other customers of that vendor.

Depending on your data, and your business sector, there may also be important considerations about where and how this data is sent. 

It's important that potentially sensitive data you send to a third party is treated in a way that complies with any regulations surrounding data privacy or protection. This might involve knowing how to work with training data that includes Personal Identifiable Information. This includes usage or destruction of data after the end of a tools life or data relating to an individual that has left the organization.

Many of these issues are consistent with other Software as a Service (SaaS) concerns, more details of which can be found in the current BCSF guidance on the topic.

#### Correct handling of data
- Will the processing be done within your existing system, in the vendor's system, or on a third party platform? If your data is sent out, where will it be hosted? Is the processing secure?
- What security is applied to data in transit?
- Will the data be stored by the vendor? How will it be stored?
- Does this comply with all the data handling requirements for your sector and data type?

# Available skills and resources
Discover some guiding principles to help you evaluate what skills and resources you need to effectively support the use of an intelligent tool.
One of the most significant factors determining the effectiveness of any intelligent tool is the availability of resources needed to support its use, and skills required to set-up or manage it.

Identifying and implementing intelligent tools should be seen as a step that will improve the security operations of an organization, by complementing current activity. 

## Interaction
Although intelligent tools may act autonomously, there are often many forms of interaction required for them to be effective.

If no one understands, or is able to act on the information that a tool produces, then it will have no value. Likewise, a tool which automates some activity can have a detrimental effect if it can’t be configured correctly.

## Support costs
Intelligent security tools are new. As a result, you may be dependent on the vendor for support. This could limit the availability of support for installation, training and maintenance.

Using and maintaining the tool could require some very specialised expertise. As with many roles in cyber security, it can be difficult to find and recruit people with these skills. For this reason, you should not consider intelligent cyber security tools to be a replacement for skilled people, but rather a way of further augmenting their capabilities.

## Principles

### 1. Ensure the required resources are available

As well as the requirements for collecting and storing data, you may need to consider other hardware and software upgrades to ensure the tool will function correctly. AI can be computationally expensive and is often run in the cloud for this reason. 

With intelligent tools, there is no guarantee that installation will be as simple as plug and play. It's likely that there will be some configuration needed. This may be manual, requiring appropriate skills and knowledge about your organization. Or it may be automatic, meaning the tool 'learns' about how your organization works. If the tool needs to learn about your organization, it can take some time to become operational.

It's important to know what purpose the tool serves and ensure that it's configured appropriately. There is a generally acknowledged trade-off between fast computation of results and the accuracy of the results produced. 

The overheads for getting the desired results from some intelligent tools are very high. 

#### Being prepared

- Do you have all the appropriate hardware and software available to make use of the tool?
- Do you know what the implementation of the solution entails?
- Do you understand how to configure the tool? Do you know who will install and configure the tool?
- Do you know how the system will be maintained?

### 2. Ensure that all relevant members of staff have appropriate skills

When introducing a new tool, you will need to ensure that relevant members of staff are able to interact with it correctly. 

In many cases, the number of people who will directly interact with the tool will be just those in (or acting as) a security operations centre (SOC). But in some cases, the tool may be interacting with your entire workforce, and different people may be required to interact in different ways.

At this stage, the nature of the interaction needs to be considered. Specifically, what is expected of the user if they are to get what they need from the tool.

In most cases this will just be familiarization with the functionality and interfaces, however in some cases it might require specific skills.

Working with intelligent devices is a new experience for many people, so you may find your current user base requires training. Ask your vendor what skills are required and whether training is available. Your current people may not find the tools easy to adapt to, and you may need to hire additional specialist operators to work directly with the tool.

#### Making the necessary skills available

- Identify who will use the tool
- Identify any specific skills that are needed. Are people with those skills readily available?
- Ensure that you can access appropriate training for users

### 3. Identify the support that is available for the product

It's almost a certainty that you will need support at some point during the life of an intelligent product. Knowing where to go for that support and how much is available will be vital for getting the most out of any tool. 

Whether you choose to accept the potential impact of any support gaps or employing outside expertise, there will be an associated cost. This should be factored in when purchasing an intelligent tool.

Due to the dynamic nature of the underlying technology, intelligent tools may change more rapidly than static ones. As a result, support requirements can be more pronounced. Since working with AI based tools may require specialist knowledge, you could be almost totally reliant on the vendor for this support.

#### Securing support

- Do you know what support is provided for the tool across its lifetime?
- Have you identified what documentation and support material is available?
- Do you know where gaps in support exist? Have you identified how those gaps can be filled?

# Getting the most from artificial intelligence
Understand what factors may affect an intelligent tool's ability to perform the task it was built for, including reliability and resilience.
When considering the use of any kind of tool, intelligent or otherwise, you need to understand what factors may affect the tool's ability to perform the task it was built for.

You should enquire how and why aspects of your intelligent system work, and what happens when they don't.

Your research should cover the training of the intelligent system, how issues with the tool might impact your organization, and the fundamental limitations of the tool.

## Principles

### 1. How reliable is the tool?

Intelligent tools make decisions based on rules they've learned from data, and many tools will continue to learn throughout their use. A basic grasp of how this works can help you establish if the tool will do what is expected of it.

#### Training data

What data is used to train the system? This may just be data from your organization, but could also involve data from other sources, including the vendor's proprietary data.

If other data sources are used, you may want to question how relevant that data is to your organization. Synthetic data, or data from significantly different operational processes, might not provide a useful baseline for your organization. Likewise, if the training data is too narrow, it is less likely to work well in a live environment. 

#### Static tools

For static tools - which do not adapt after their initial training - can you be confident that the system remains accurate over time?

If the problem and the environment remain the same, then initial training should be sufficient. For these systems, updates and changes only need to be considered when there is a significant improvement in the underlying technology.

#### Adaptation and stability

For security tools, adaptation is likely to be important. For example, being able to train your tool to recognize new types of attack will be essential, if it is to remain relevant. 

If the system updates, you will want to be sure that it is going to remain stable. Updates to the system will change the performance of the tool, which may cause it to become unpredictable. This happens because a change to an intelligent tool can fundamentally alter the background processes used to make decisions. This means that it can be difficult to gain assurance in adaptive tools.

Ensuring that intelligent tools remain stable and accurate as they update is an open question for researchers, so it's unlikely the vendor will have all the answers.

However, you should try and understand how and when new data is incorporated into the tool. You should also look for assurance that the tool is performing as expected. It could be important for you to understand how long it takes to establish a new baseline that fits your needs once new data is added.

#### Ensure stability

- Do you know how the system was trained? Was the data representative of your organization?
- Do you know if the system continues to adapt. Do you know how it does this?
- Is the adaptability of the system sufficient for your use case?

### 2. Is the system resilient enough for the task?

Intelligent tools can have vulnerabilities and these vulnerabilities might not be related to the coding of the program, but may exist as part of the tool's process. Some will be the result of weaknesses in design or configuration, others could come about as a result of data manipulation. 

It's not possible to catalogue all the potential vulnerabilities of an intelligent tool, but you should tryto understand the impact of a tool not performing correctly, either through accident or attack.

#### Failing safely

Regardless of the type of tool, it is important to know that it fails safely. In other words, should the tool go wrong, there is no significant risk to a person or your organization.

From this perspective, it is also important to know what interventions are in place in the event of a failure, and how to shut the system down safely. 

#### Fixes and fallbacks

Where possible, you should be able to reliably fix a tool, or it's underlying model, if things go wrong. You should also be prepared for cases where it's simply not possible to fix the problem. 

You should also know if there's a way to rollback to a known good configuration. Where this is possible, you should understand what the impact might be. It could, for example, result in a loss of accuracy when processing current data.

#### Be clear about weaknesses and failures

- Be aware of any vulnerabilities that might be introduced by using the tool.
- Is the tool safe to fail?
- Can the tool be fixed if it fails? What is the process for diagnosing and fixing issues?
- Can the system be rolled back? What is the impact of doing so?

### 3. What are the limitations?

AI is not capable of solving every problem. It is therefore important to understand that while there are many uses for AI, the promises of the tool need to line up with what is currently possible with AI techniques.

A particular tool will be designed and trained to solve a particular problem. Outside of this training it has limited use, so you need to understand the bounds that your tool has been designed to work within. 

Since there are so many ways that an intelligent tool can work, it’s difficult to define a complete set of limitations for each approach. But there are some general concepts.

#### Does the data do enough?

Consider whether the data used contains enough detail to make the decision you are asking the tool to handle. For example, the data may contain sufficient information to detect anomalies, but further detail may be required to understand if a threat is real.

If the system offers functionality that seems too good to be true, ask the vendor to explain how it achieves this. They should be able to provide some assurance without diving into the detail of how the technology works.

#### The limits of the tool

You should consider the point at which the functionality of the tool ends. In development, there would have been a set of bounds for the testing data and what can be represented and understood from the tool's output.

A system will be limited by its design.  If the data and evaluation are specifically designed to identify or act on certain properties, then that is all it will do.  If something comes along that is malicious, but doesn't exhibit the signs that would be spotted by the system, then it will have no reason to consider it a threat.

These bounds need to be made clear because there can be no guarantee of accuracy if the tool is working beyond the scope it was designed and tested for.

#### Determine the scope of the tool

- What are the limitations of the system?
- Does the solution seem too good to be true?
- Is there a defined scope of the tool?  Does that fit your use case?
