---
layout: post
title: "Python Note (6) - 简单的单线程爬虫实现"
description: "这篇博文主要介绍了如何用python构造一个简单的单线程爬虫"
category: "Programming"
tags: ["Python", "Spider"]
---

# 单线程爬虫的实现

* * *

终于要开始动手写python代码了。就从实际出发吧，写一个简单的单线程爬虫。


## 代码

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

## 代码说明

总的来说，这里稍微高级一点点的就是用到了BeautifulSoup这个模块，这样做数据提取方便了很多。

### BeautifulSoup安装

因为我使用的是fedora19，不能保证下面的方法在所有的pc上都适用。

    sudo yum install pip
	sudo pip install beautifulsoup4

需要注意的是，安装完成之后，代码里不能直接使用import，不然会报错找不到module。应该写成`from bs4 import BeautifulSoup`。

### 具体使用

我们先看一下需要提取的数据所在的html源码，

	<ul>
		<li><span>August 22, 2013</span>  : <a href="/blog/2013/08/22/python-module" class="post">Python Note (6) - 简单的单线程爬虫实现</a></li>

		<li><span>August 21, 2013</span>  : <a href="/blog/2013/08/21/symfony2-test" class="post">Symfony2 (4) - atoum进行单元测试</a></li>

		<li><span>August 20, 2013</span>  : <a href="/blog/2013/08/20/za" class="post">发一点怨念</a></li>

		<li><span>August 19, 2013</span>  : <a href="/blog/2013/08/19/symfony2-test" class="post">Symfony2 (3) - atoum进行单元测试</a></li>

		<li><span>August 17, 2013</span>  : <a href="/blog/2013/08/17/symfony2-generate-doc" class="post">Symfony2 (2) - NelmioApiDocBundle自动生成文档(译)</a></li>

		<li><span>August 17, 2013</span>  : <a href="/blog/2013/08/17/symfony2-create-bundle" class="post">Symfony2 (1) - 新建一个bundle</a></li>

		<li><span>August 17, 2013</span>  : <a href="/blog/2013/08/17/jekyll-bootstrap-code-highlighting" class="post">Jekyll-bootstrap添加代码高亮</a></li>

		<li><span>August 16, 2013</span>  : <a href="/blog/2013/08/16/symfony2-install" class="post">Symfony2 (0) - installation and configuration</a></li>

		<li><span>August 15, 2013</span>  : <a href="/blog/2013/08/15/python-data-structure" class="post">Python Note (5) - data structure</a></li>

		<li><span>August 14, 2013</span>  : <a href="/blog/2013/08/14/python-template" class="post">Python Note (4) - template</a></li>
	</ul>

代码结构还是很清楚的。

在执行完获取html源码的操作后，`siteUrls = soup.findAll('a',attrs={'class':'post'})`把所有`a`标签中`class`为`post`的数据抽取出来放到siteUrls这个数组中。
