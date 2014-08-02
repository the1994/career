---
layout: post
title: "Wikipedia Infobox Parser in NodeJS"
description: "Wikipedia infobox parser in NodeJS"
category: "Programming"
tags: ['NodeJS']
---

A simple parser in node.js for wikipedia infobox, like the box in the right of picture below:

![pic](https://db.tt/woGRt6a3)

Due to the aweful lexical grammar, sorry I don't mean to be offensive, but this information box is really **mal-organisé**. There are many third party parsers, but none of them is perfect. After trying developing this parser, I realized that it's hyper difficult to take all conditions into consideration. So, [this parser](https://github.com/jesusjzp/wikiparser) is far  from perfection.

**Just fork the [repo](https://github.com/jesusjzp/wikiparser) and do whatever you can help!**

## Install

	npm install

## Test

	npm test

## Usage

```JavaScript
var parseWiki = require('wiki-infobox-parser');

parseWiki('france', function(err, result) {
	if (err) { console.error(err); }
  console.log(result);
});
```

## TODO

- Redirction
- Multiple opetions redirection
- Multiple languages support

## Examples

![pic](https://db.tt/imZd0cyb)

	{
	    "name": "node.js",
	    "logo": "frameless",
	    "author": "Ryan Dahl",
	    "developer": "[http://github.com/ry/node/blob/master/AUTHORS Node.js Developers], Joyent, [https://github.com/joyent/node/graphs/contributors Github Contributors]",
	    "operating system": "Mac OS X, Linux, Solaris, FreeBSD, OpenBSD, Windows (older versions require Cygwin), webOS",
	    "status": "Active",
	    "released": "{{release date|2009|05|27}}",
	    "latest release version": "0.10.29",
	    "latest release date": "{{release date|2014|06|16}}",
	    "latest preview version": "0.11.13",
	    "latest preview date": "{{release date|2014|05|01}}",
	    "programming language": "C, C++, JavaScript",
	    "genre": "Event-driven networking",
	    "license": "MIT",
	    "website": "{{URL|http://nodejs.org}}"
	}

![pic](https://db.tt/88TGYsfh)

	{
	    "name": "JavaScript",
	    "paradigm": "Multi-paradigm: scripting, object-oriented (prototype-based), imperative, functional",
	    "year": "{{start date and age|1995}}",
	    "logo": "70px",
	    "designer": "Brendan Eich",
	    "developer": "Netscape Communications Corporation, Mozilla Foundation",
	    "latest_release_version": "1.8.5",
	    "latest_release_date": "{{start date and age|2011|3|22}}",
	    "latest_preview_date": "{{start date and age|2010|7|27}}",
	    "typing": "dynamic, duck",
	    "implementations": "KJS, Rhino, SpiderMonkey, V8, Carakan, Chakra",
	    "influenced_by": "Scheme, Self, Java, C, Python",
	    "influenced": "ActionScript, CoffeeScript, Dart, JScript .NET, Objective-J, QML, TypeScript, Node.js, LiveScript",
	    "wikibooks": "JavaScript",
	    "logo caption": "Unofficial JavaScript logo}}",
	    "icon": "150px",
	    "extension": ".js",
	    "mime": "application/javascripttext/javascript ;(obsolete)",
	    "uniform type": "com.netscape.javascript-source{{cite web",
	    "publisher": "Apple Inc.",
	    "url": "}}",
	    "title": "System-Declared Uniform Type Identifiers",
	    "work": "Mac OS X Reference Library",
	    "accessdate": "2010-03-05",
	    "genre": "Scripting language"
	}


## Reference

- [Wikipedia API](http://en.wikipedia.org/w/api.php)

- [Syntax of Wiki Markup](http://en.wikipedia.org/wiki/Help:Wiki_markup)