---
layout: post
title: "Local Jekyll Environment Installation"
description: ""
category: "Programming"
tags: ["jekyll"]
---

# Local Jekyll Environment Installation

If you have installed Ruby ou Rubygems, you can jump to 'gem install' directly. Besides, all the installation is under Fedora 19.

## Install Ruby and Rubygems

    sudo yum install ruby-devel
	sudo yum install rubygems

## Install gcc

    sudo yum install gcc

## Install jekyll

    gem install jekyll

## Install pygments

It is a tool to enable code highlight.

    sudo yum install python-pygments

# Debug and local test

## Debug

    jekyll build

If you have some bug, you can use

    jekyll build --trace

to trace the bug.

## Local test

    jekyll serve

Then in your browser, type in

    http://localhost:4000





*Reference* : http://www.soimort.org/posts/101/

*Note* : In this reference, there are some commands are too old to execute, as jekyll has updated recently. For example, rdiscount is no longer working,

    jekyll --rdiscount

You will get this error,

    Deprecation: Jekyll now uses subcommands instead of just switches. Run \`jekyll help\' to find out more.

Please refer to the [official site](http://jekyllrb.com/docs/installation/) for more details about installation and configuration.

