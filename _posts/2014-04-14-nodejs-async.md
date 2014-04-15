---
layout: post
title: "NodeJS Asnyc, Callback and SetTimeout"
description: ""
category: "Programming"
tags: ["Javascript", "NodeJS"]
---

### Async waterfall flow

<pre class="prettyprint linenums">
var async = require('async');

// Async waterfall flow
async.waterfall([
  function(callback){
    callback(null, 'one', 'two');
  },
  function(arg1, arg2, callback){
    // arg1 now equals 'one' and arg2 now equals 'two'
    callback(null, 'three');
  },
  function(arg1, callback){
    // arg1 now equals 'three'
    callback(null, 'done');
  }
], function (err, result) {
  console.log(result); 
});
</pre>

Result

  one
  two
  three
  done

### Function setTimeout

<pre class="prettyprint linenums">
// setTimeout illustration.
function calculateFibonacci(number) {
  if (number === 0 || number === 1) 
    return number;
  return (calculateFibonacci(number - 1) + calculateFibonacci(number - 2));
}

function doSomthing(number, successCB, errorCB) {
  setTimeout(function() {
    try {
      var result = [];
      for (var i = 0; i &lt; number; i++) {
        var res = calculateFibonacci(i);
        // console.log(res);
        result.push(res);
      }
      console.log('for finished');

      if (typeof successCB === 'function') {
        successCB(result.join(', '));
      }
    } catch (ex) {
      if (typeof errorCB === 'function') {
        errorCB(ex.message);
      }
    }
  }, 100);
}

console.log('Initialization');

doSomthing(30, function(result) {
  console.log('The result is: ', result);
}, function(err) {
  console.log(err);
});
</pre>

Result

  Initialization
  for finished
  The result is:  0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597, 2584, 4181, 6765, 10946, 17711, 28657, 46368, 75025, 121393, 196418, 317811, 514229

### Function callback

<pre class="prettyprint linenums">
// Function injection
function do_a( callback ){
  setTimeout( function(){
    // simulate a time consuming function
    console.log( '`do_a`: this takes longer than `do_b`' );
    // if callback exist execute it
    if(callback) callback();
  }, 3000 );
}
 
function do_b(){
  console.log( '`do_b`: now we can make sure `do_b` comes out after `do_a`' );
}
 
do_a( function(){
  do_b();
});
</pre>

Result

  `do_a`: this takes longer than `do_b`
  `do_b`: now we can make sure `do_b` comes out after `do_a`
