---
layout: post
title: "NoSQL 5 - Amazon's Dynamo"
description: "NoSQL Database, Key/Value stores"
category: "Programming"
tags: ["NoSQL"]
---

Extracted from **Christof Strauch, [NoSQL Databases](http://www.christof-strauch.de/nosqldbs.pdf), P52-,  2010**.

#4.1 Amazon's Dynamo

Amazon Dynamo is one of several databases used at Amazon for different purposes (others are e. g. SimpleDB or S3, the Simple Storage Service, cf. [Ama10b], [Ama10a]). Because of its influence on a number of NoSQL databases, especially key-/value-stores, the following section will investigate in more detail Dynamo’s influencing factors, applied concepts, system design and implementation.

##4.1.1 Context and Requirements at Amazon

##4.1.2 Concepts Applied in Dynamo

##4.1.3 System Design

###Cosiderations and Overview

![pic](http://media-cache-ec0.pinimg.com/originals/81/57/72/815772e1217b54735ea219dd79ef376c.jpg)

###System Interface

- **get(key)**, returning a list of objects and a context
- **put(key, context, object)**, with no return value

###Partitioning Algorithm

To provide incremental scalability, Dynamo uses **consistent hashing** to dynamically partition data across the storage hosts that are present in the system at a given time. DeCandia et al. argue that using consistent hashing in its raw form has two downsides: first, the random mapping of storage hosts and data items onto the ring leads to unbalanced distribution of data and load; second, the consistent hashing algorithm treats each storage node equally and does not take into account its hardware resources. To overcome both difficulties, Dynamo applies the concepts of **virtual nodes**, i. e. for each storage host multiple virtual nodes get hashed onto the ring (as described in subsection 3.2.1) and the number of virtual nodes per physical node is used to take the hardware capabilities of storage nodes into account (i. e. the more resources the more virtual nodes per physical node, cf. [DHJ+ 07, p. 209–210]).

###Replication

![pic](http://media-cache-ec0.pinimg.com/originals/68/2f/d5/682fd5df2359f6f4cd4923f025e233d5.jpg)