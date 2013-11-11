---
layout: post
title: "NoSQL 4 - Strorage Layout"
description: "NoSQL Database Basic Concepts"
category: "Programming"
tags: ["NoSQL"]
---

Extracted from **Christof Strauch, [NoSQL Databases](http://www.christof-strauch.de/nosqldbs.pdf), P44-,  2010**.

#3.3 Storage Layout

- Row-based Storage Layout
- Columnar Storage Layout
- Columnar Storage Layout with Locality Groups
- Log Structured Merge Trees (LSM-trees)

![pic](http://media-cache-ec0.pinimg.com/originals/00/69/33/0069337528e345a649b2ed4ef7935d36.jpg)

![pic](http://media-cache-ec0.pinimg.com/originals/89/96/a1/8996a1c5cd4b477487cd263fcec1cde5.jpg)

#3.4 Query Model

- Companion SQL database
- Scatter/Gather Local Search
- Distributed B+ Trees
- Prefix Hash Table (aka Distributed Trie)
- OR Junctions
- AND Junctions

#3.5 Distributed Data Processing via MapReduce

MapReduce, brought up by Google employees in 2004 (cf. [DG04]), splits a task into two stages, described by the functions map and reduce. In the first stage a coordinater designates pieces of data to process a number of nodes which execute a given map function and produce intermediate output. Next, the intermediate output is processed by a number of machines executing a given reduce function whose purpose it is to create the final output from the intermediate results, e. g. by some aggregation. Both the map and reduce functions have to be understood in a real functional manner, so they do not depend on some state on the machine they are executed on and therefore produce identical output on each execution environment given the identical input data. The partitioning of the original data as well as the assignment of intermediate data is done by the coordinator according to Google’s original paper.

Figure 3.18 depicts and summarzies the MapReduce fashion of distributed data processing.

![pic](http://media-cache-ec0.pinimg.com/originals/b6/ae/16/b6ae1671fe4647ed23530006432df457.jpg)