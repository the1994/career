---
layout: post
title: "Python Note (6) - 简单的单线程爬虫实现"
description: "这篇博文主要介绍了如何用python构造一个简单的单线程爬虫"
category: "Programming"
tags: ["Python", "Spider"]
---

## 单线程爬虫的实现

* * *

终于要开始动手写python代码了。就从实际出发吧，写一个简单的单线程爬虫。


### 代码

先上代码吧，各位大牛看了代码就知道这个示例有多么简单了。

<pre class="prettyprint linenums">
#!/usr/bin/python
# Filename: httpGet.py

import urllib2
from bs4 import BeautifulSoup
import re
siteUrls = " "

url = "http://jesusjzp.github.io/"
def getContent(url):
    content = urllib2.urlopen(url).read()
    #print content

    soup=BeautifulSoup(content)
    global siteUrls
    siteUrls = soup.findAll('a',attrs={'class':'post'})
    #nextUrl = soup.find('div',attrs={'class':'topicListFooter'})
    #print siteUrls
    #print str(nextUrl)
    strip_tag_pat=re.compile('&lt;/?\w+[^&gt;]*&gt;')

    f = file('info.txt','w')
    for i in siteUrls:
        i0 = re.sub(strip_tag_pat,' ',str(i))
        i1 = str(i).split(' ')
        #print i1
        html = i1[2][6:-1] 
        #print html + i0
        f.write(html+i0+'\n')
    f.close()


getContent(url)
</pre>
