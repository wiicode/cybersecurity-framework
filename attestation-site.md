---
title: Attestation Service
description: BCSF subscriptions include attestation services and validation.  
published: true
date: 2020-08-06T23:49:55.930Z
tags: attestation
editor: markdown
---

# Process Explained

```mermaid
sequenceDiagram
    Customer ->> Bob: Hello Bob, how are you?
    Other Party-->>John: How about you John?
    Bob--x Alice: I am good thanks!
    Bob-x John: I am good thanks!
    Note right of John: Bob thinks a long<br/>long time, so long<br/>that the text does<br/>not fit on a row.

    Bob-->Alice: Checking with John...
    Alice->John: Yes... John, how are you?
```