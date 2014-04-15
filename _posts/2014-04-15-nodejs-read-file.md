---
layout: post
title: "Read file line by line with Node.js"
description: ""
category: "Programming"
tags: ["Javascript", "NodeJS"]
---

Read text from file line by line with Node.js.

<pre class="prettyprint linenums">
var fs = require('fs');

function readLines(input, func) {
  var remaining = '';

  input.on('data', function(data) {
    remaining += data;
    var index = remaining.indexOf('\n');
    while (index &gt; -1) {
      var line = remaining.substring(0, index);
      remaining = remaining.substring(index + 1);
      func(line);
      index = remaining.indexOf('\n');
    }
  });

  input.on('end', function() {
    if (remaining.length &gt; 0) {
      func(remaining);
    }
  });
}

function func(data) {
  console.log('Line: ' + data);
}

var input = fs.createReadStream('lines.txt');
readLines(input, func);
</pre>
