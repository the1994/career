---
layout: post
title: "Word / number conversion in Javascript"
description: "Word to number conversion and number to word conversion in Javascript"
category: "Programming"
tags: ["Javascript"]
---

## Intro

Word to number and number to word conversion in Javascript.

Word -> Number

    "one" -> 1
    "one thousand" -> 1000

Number -> Word

    1 -> "one"
    1000 -> "one thousand"

## Code

##Word to number##

<pre class="prettyprint linenums">
/*
 * @overview    Word to number conversion
 * @author      Zhipeng Jiang
 */
var Small = {
  'zero': 0,
  'one': 1,
  'two': 2,
  'three': 3,
  'four': 4,
  'five': 5,
  'six': 6,
  'seven': 7,
  'eight': 8,
  'nine': 9,
  'ten': 10,
  'eleven': 11,
  'twelve': 12,
  'thirteen': 13,
  'fourteen': 14,
  'fifteen': 15,
  'sixteen': 16,
  'seventeen': 17,
  'eighteen': 18,
  'nineteen': 19,
  'twenty': 20,
  'thirty': 30,
  'forty': 40,
  'fifty': 50,
  'sixty': 60,
  'seventy': 70,
  'eighty': 80,
  'ninety': 90
};

var Magnitude = {
  'hundred':      100,
  'thousand':     1000,
  'million':      1000000,
  'billion':      1000000000,
  'trillion':     1000000000000,
  'quadrillion':  1000000000000000,
  'quintillion':  1000000000000000000,
  'sextillion':   1000000000000000000000,
  'septillion':   1000000000000000000000000,
  'octillion':    1000000000000000000000000000,
  'nonillion':    1000000000000000000000000000000,
  'decillion':    1000000000000000000000000000000000,
};

var arr, res, num;

function word2num(str) {
    arr = str.toString()                            // change to string
                 .toLowerCase()                     // change to lower case
                 .replace(/(^\s*)|(\s*$)/g, "")     // trim space in head and tail
                 .split(/[\s-]+/);                  // split word with space
    res = 0;
    num = 0;
    arr.forEach(feach);
    return res + num;
}

function feach(word) {
  var base = Small[word];
  if (base != null) {
    num = num + base;                           // add the quantity
  } else {
    base = Magnitude[word];                     // get the base
    if (base != null) {
        res += num * base;
        num = 0;
    }
    else { 
      alert("Unknown number: "+word);
    }
  }
}


/*
 * For test
 */
console.log('one: ' + word2num('one') + '\n');
console.log('sixteen: ' + word2num('sixteen') + '\n');
console.log('SiXtEen: ' + word2num('sixteen') + '\n');
console.log('one thousand two hundred thirty four: ' + word2num('one thousand two hundred thirty four ') + '\n');
console.log('One Thousand Two Hundred Thirty Four: ' + word2num('One Thousand Two Hundred Thirty Four') + '\n');
console.log('four hundred fifty four million three hundred fifty two thousand three hundred forty five: ' + word2num('four hundred fifty four million three hundred fifty two thousand three hundred forty five') + '\n');
</pre>

##Number to Word##

<pre class="prettyprint linenums">
/*
 * @overview    Number to word conversion
 * @copyright   Sutoiku, Inc. 2014
 * @author      Zhipeng Jiang
 */
var th = ['', 'thousand', 'million', 'billion', 'trillion', 'quadrillion'];

// 0~9
var singleNumber = ['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine'];
// 10~19
var tenPlus = ['ten', 'eleven', 'twelve', 'thirteen', 'fourteen', 'fifteen', 'sixteen', 'seventeen', 'eighteen', 'nineteen'];
// 20~90
var tens = ['twenty', 'thirty', 'forty', 'fifty', 'sixty', 'seventy', 'eighty', 'ninety'];

function num2word(str) {
  str = str.toString()
       .replace(/[\, ]/g, '');

  if (str != parseFloat(str)) {
        return 'not a number';
  }

  var strLength = str.indexOf('.');
  if (strLength == -1) {
        strLength = str.length;
  }

  var n = str.split('');
  var result = '';
  var skip = 0;
  for (var i = 0; i &lt; strLength; i++) {

    if ((strLength - i) % 3 == 2) {
      if (n[i] == '1') {
        result += tenPlus[Number(n[i + 1])] + ' ';
        i++;
        skip = 1;
            } else if (n[i] != 0) {
                result += tens[n[i] - 2] + ' ';
        skip = 1;
      }
        } else if (n[i] != 0) {
      result += singleNumber[n[i]] + ' ';
            if ((strLength - i) % 3 == 0)
                result += 'hundred ';
      skip = 1;
    }

    if ((strLength - i) % 3 == 1) {
      if (skip) {
        result += th[(strLength - i - 1) / 3] + ' ';
        skip = 0;
      }
    }
  }

  // For decimal
  if (strLength != str.length) {
    var y = str.length;
    result += 'point ';
    for (var i = strLength + 1; i &lt; y; i++) 
      result += singleNumber[n[i]] + ' ';
  }
  
  return result.replace(/\s+/g, ' ');
}

console.log('1: ' + num2word(1) + '\n');
console.log('12: ' + num2word(12) + '\n');
console.log('12456: ' + num2word(12456) + '\n');
console.log('1233456: ' + num2word(1233456) + '\n');
// console.log('1000000000000000000000: ' + num2word(1000000000000000000000) + '\n');
console.log('1123231: ' + num2word(1123231) + '\n');
console.log('12.31123434: ' + num2word(12.31123434) + '\n');
console.log('1137523847562: ' + num2word(1137523847562) + '\n');

</pre>