---
layout: post
title: "NoSQL 3 - Partitioning"
description: "NoSQL Database Basic Concepts"
category: "Programming"
tags: ["NoSQL"]
---

Extracted from **Christof Strauch, [NoSQL Databases](http://www.christof-strauch.de/nosqldbs.pdf), P37-,  2010**.

#3.2 Partitioning#

- Memory Caches
- Clustering
- Separating Reads from Writes
- Sharding

##3.2.1 Consistent Hashing##

Figures 3.4 and 3.5 illustrate the idea behind the consistent hashing approach. In figure 3.4 there are three red colored nodes A, B and C and four blue colored objects 1–4 that are mapped to a hash-function’s result range which is imagined and pictured as a ring. Which object is mapped to which node is determined by moving clockwise around the ring. So, objects 4 and 1 are mapped to node A, object 2 to node B and object 3 to node C. When a node leaves the system, cache objects will get mapped to their adjacent node (in clockwise direction) and when a node enters the system it will get hashed onto the ring and will overtake objects. An example is depicted in figure 3.5 where compared to figure 3.4 node C left and node D entered the system, so that now objects 3 and 4 will get mapped to node D. This shows that by changing the number of nodes not all objects have to be remapped to the new set of nodes but only part of the objects.

![pic](http://media-cache-ak0.pinimg.com/originals/e6/af/0a/e6af0aaed3aab954d2bbc1ffaaaf74c0.jpg)

##3.2.2 Read and Write Operations on Partitioned Data###

The Project Voldemort team points out that three parameters are specifically important regarding read as well as write
operations (cf. [K+ 10b]):

- **N** The number of replicas for the data or the piece of data to be read or written.
- **R** The number of machines contacted in read operations.
- **W** The number of machines that have to be blocked in write operations5 .

In the interest to provide e. g. the read-your-own-writes consistency model the following relation between the above parameters becomes necessary:

<center><b> R+W > N </b></center>

###3.2.3Membership Changes###

When a new node joins the system the following actions have to happen (cf. [Ho09a]):

1. The newly arriving node announces its presence and its identifier to adjacent nodes or to all nodes via broadcast.
2. The neighbors of the joining node react by adjusting their object and replica ownerships.
3. The joining node copies datasets it is now responsible for from its neighbours. This can be done in bulk and also asynchronously.
4. If, in step 1, the membership change has not been broadcasted to all nodes, the joining node is now announcing its arrival.

In figure 3.8, this process is illustrated. Node X joins a system for which a replication factor of three is configured. It is hashed between A and B, so that the nodes H, A and B transfer data to the new node X and after that the nodes B, C and D can drop parts of their data for which node X is now responsible as a third replica (in addition to nodes H, A and B).

![pic](http://media-cache-ec0.pinimg.com/originals/b8/d7/50/b8d75006aa547edf5788f6806339a96f.jpg)

When a node leaves the system the following actions have to occur:

1. Nodes within the system need to detect whether a node has left as it might have crashed and not been able to notify the other nodes of its departure. It is also common in many systems that no notifications get exchanged when a node leaves. If the nodes of the system communicate regularly e. g. via the Gossip protocol they are able to detect a node’s departure because it no longer responds.
2. If a node’s departure has been detected, the neighbors of the node have to react by exchanging data with each other and adjusting their object and replica ownerships.

Figure 3.9 shows the actions to be taken when node B—due to a crash—leaves the system. Nodes C, D and E become responsible for new intervals of hashed objects and therefore have to copy data from nodes in counterclockwise direction and also reorganize their internal representation of the intervals as the RangeAB and RangeBC now have collapsed to RangeAC .

![pic](http://media-cache-ec0.pinimg.com/originals/84/5c/7a/845c7af504f4f4b85d04cd67c7f6042c.jpg)