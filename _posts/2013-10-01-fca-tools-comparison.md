---
layout: post
title: "FCA Tools Comparison"
description: "Formal Concept Analyze Tools Comparison, including Galicia, Lattice Miner and OpenFCA"
category: "Programming"
tags: ["Formal Concept Analyze"]
---

# 1. Tools list

- Galicia, [http://www.iro.umontreal.ca/~galicia/](http://www.iro.umontreal.ca/~galicia/)
- Lattice Miner, [http://sourceforge.net/projects/lattice-miner/](http://sourceforge.net/projects/lattice-miner/)
- Open FCA, [https://code.google.com/p/openfca/](https://code.google.com/p/openfca/)

# 2. Data Resource

In fact I haven’t found the appropriate database from online data service, I have tried a lot of online database and download csv or cxt files. But they can not be imported or opened by either Galicia or Lattice Miner, so I generate the random data by Galicia:

![fig](https://lh5.googleusercontent.com/EY0U0rA7laCpzK38dukiMZ6M5w0MgjXZFrV4adAq9W4Yv7Zv1k4s92bTQFYXl01i4J6zR3IAHn7Rj8ekOdECeK_bmzCzeT6jAsErnncgyzd-GAUmiriUeWp4)

**Figure 1: Generate Random Database By Galicia**

Input  the number of objects and attributes, then a new binary table is generated:

![fig](https://lh6.googleusercontent.com/Zeg-i-373lHnNIuMiHUcunR9PGtzY7k_sa5lD0LU9BzC2Zg97oY5YnQcs9DogKC9GApos2BKs1dIu1axI0C1RUmwRjBwq1zHFKSKr8scoYv1enXSwXMlwo1m)

**Figure 2: Random Table in Galicia**

# 3. Comparison

## 3.1 Galicia

### 3.1.1 Create or import data

Just as has mentioned above, we can create a new random table in galicia.

### 3.1.2 Construct the lattice

Algorithms->Construct the lattice:

