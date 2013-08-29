---
layout: post
title: "Android Develop Record(09) - SQLite3 commands"
description: "Android Develop Record"
category: "Programming"
tags: ["Android", "SQLite"]
---

# Preface

* * *

If you want to access SQLite database by `adb shell` from terminal, please make sure that you have the rooted your phone, otherwise you could not use `sqlite3` by defaut. 

*Actually, you can find your database list by `run-as [package name]`, e.g., `run-as com.zhipeng.color`.*

# Useful commands

* * *

**1) Show all tables**

    .tables

**2) Show table structure**

    .schema [tablename]

For example, I have a table named as "folder"

    .schema folder

**3) Get limit rows for each query**

If you only need 20 results for each query,

    select * from [tablename] limit 20;

**4) Get random results**

    select * from [tablename] order by random();


