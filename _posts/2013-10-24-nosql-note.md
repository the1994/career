---
layout: post
title: "NoSQL 2 - Basic Concepts"
description: "NoSQL Database Basic Concepts"
category: "Programming"
tags: ["NoSQL"]
---

Extracted from **Christof Strauch, [NoSQL Databases](http://www.christof-strauch.de/nosqldbs.pdf), P30-32,  2010**.

#Consistency#

##The CAP-Theorem##

- Consistency
- Availability
- Partition Tolerance

##ACID vs. BASE

**ACID**

- Atomicity
- Consistency
- Isolation
- Durability

**BASE**

- Basically available
- Soft-state
- Eventual consistency

![pic](https://dl-web.dropbox.com/get/Blog/Selection_008.png?w=AACG3vhypLAVq0XNeENXvK5lKt6-xsg96ByOVm455bs3jQ)

##Versioning of Datasets in Distributed Scenarios##

If datasets are distributed among nodes, they can be read and altered on each node and no strict consistency is ensured by distributed transaction protocols, questions arise on how “concurrent” modifications and versions are processed and to which values a dataset will eventually converge to. There are several options to handle these issues:

- Timestamps
- Optimistic Locking
- Vector Clocks
- Multiversion Storage

**Verctor Clocks**

A vector clock is defined as a tuple V [0], V [1], ..., V [n] of clock values from each node (cf. [Lip09, slide 18]). In a distributed scenario node i maintains such a tuple of clock values, which represent the state of itself and the other (replica) nodes’ state as it is aware about at a given time (Vi [0] for the clock value of the first node, Vi [1] for the clock value of the second node, . . . Vi [i] for itself, . . . Vi [n] for the clock value of the last node). Clock values may be real timestamps derived from a node’s local clock, version/revision numbers or some other ordinal values.

![pic](https://dl-web.dropbox.com/get/Blog/Selection_002.png?w=AAAbyWJg2je8STxoa8MxJ8U_VPUgNRXBKlOJTs-Dg_dxfg)

