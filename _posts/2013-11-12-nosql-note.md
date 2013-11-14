---
layout: post
title: "NoSQL 5 - Amazon's Dynamo"
description: "NoSQL Database, Key/Value stores"
category: "Programming"
tags: ["NoSQL"]
---

Extracted from **Christof Strauch, [NoSQL Databases](http://www.christof-strauch.de/nosqldbs.pdf), P52-62,  2010**.

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

###Data Versioning

Figure 4.2 illustrates the usage of vector clocks as well as the detection and reconciliation of concurrent versions.

In this illustration a client first creates a data item and the update request is handled by a storage host Sx, so that the vector clock ([Sx,1]) will be associated with it. Next, a client updates this data item and this update request leading to version 2 is also executed by node Sx. The resulting vector clock will be ([Sx,2]), as a casual ordering between [Sx,1] and [Sx,2] can be determined as the latter clearly succeeds the former (same storage host, ascending version numbers). As [Sx,1] has only one successor ([Sx,2]) it is no longer needed for casual reasoning and can be removed from the vector clock.

Next, one client issues an update for version D2 that gets handled by storage host Sy and results in the vector clock ([Sx,2],[Sy,1]). Here, the element [Sx,2] of the vector clock cannot get omitted. This is because the example assumes3 that a client issuing it has read version D2 from a node (say Sx) while storage host Sy has not yet received this version from its companion nodes. So the client wants to update a more recent version than node Sy knows at that time which is accepted due to the “always writeable”-property of Dynamo. The same happens with another client that has read D2 and issued an update handled by storage host Sz which is unaware of the version D2 at that time. This results in version D4 with the vector clock ([Sx,2],[Sz,1]).

![pic](http://media-cache-ec0.pinimg.com/originals/19/5a/cd/195acd6d336aba803fbeb1d8974ad045.jpg)

In the next read request both D3 and D4 get delivered to a client along with a summary of their vector clocks—in particular: ([Sx,2],[Sy,1],[Sz,1]). The client can detect that versions D3 and D4 are in conflict, as the combined vector clock submitted in the read context does not reflect a linear, subsequent ordering. Before a client can issue another update to the system it has to reconcile a version D5 from the concurrent versions D3 and D4. If this update request is handled by node Sx again, it will advance it’s version number in the vector clock resulting in ([Sx,3],[Sy,1],[Sz,1]) as depicted in figure 4.2.

###Execution of get() and put() Operations

###Membership

###Handling of Failures

##4.1.4 Implementation and Optimizations

##4.1.5 Evaluation

To conclude the discussions on Amazon’s Dynamo, a brief evaluation of Bob Ippolito’s talk “Drop ACID and think about Data” shall be presented in table 4.2.

![pic](http://media-cache-ec0.pinimg.com/originals/b7/63/d7/b763d75fb06ca33aebaa33149cccf99d.jpg)

