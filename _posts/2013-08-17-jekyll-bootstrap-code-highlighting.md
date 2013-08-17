---
layout: post
title: jekyll-bootstrap添加代码高亮
category: javascript
tags: ["Jekyll", "Javascript"]
description: "jekyll bootstarp 写博文, 让markdown支持代码高亮"
---

首先非常非常感谢lzf同学的教程，下面的文章转自他的博客，[jekyll-bootstrap添加代码高亮](http://heroin.so/javascript/2012/05/22/jekyll-bootstrap-code-highlighting/)，我在他教程的内容上加了些自己的收获。

jekyll是用`markdown`写博文的, 但是markdown默认不支持`pre`加class属性。但是, 支持直接在`markdown`中写`html`代码, [传送门](http://daringfireball.net/projects/markdown/syntax#html) 所以，我们就直接修改default模版，通过css和js代码来实现语法高亮。

修改`/includes/themes/twitter/default.html`, 添加几行代码

<pre class="prettyprint linenums">
&lt;link href="{\{ ASSET_PATH }\}/google-code-prettify/prettify.css" rel="stylesheet" type="text/css" media="all"&gt;
&lt;script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"&gt;&lt;/script&gt;
&lt;script type="text/javascript" src="{\{ ASSET_PATH }\}/google-code-prettify/prettify.js"&gt;&lt;/script&gt;
</pre>

其中上传了2个文件, 请对应放好相对应的目录下。

再添加一份`js`文件, 让其生效, js代码如下

<pre class="prettyprint linenums">
!function ($) {
    $(function(){
        window.prettyPrint &amp;&amp; prettyPrint();
    });
}(window.jQuery);
</pre>

代码可以保存在assert path下，但别忘了在`default.html`再加上一行，把刚刚写的js代码include进去。

<pre class="prettyprint linenums">
&lt;script type="text/javascript" src="{{ ASSET_PATH }}/js/application.js"&gt;&lt;/script&gt;
</pre>

写文章的时候而不是用markdown语法, 直接将要高亮的代码用`pre`标签包围

<pre class="prettyprint linenums">
&lt;pre class="prettyprint linenums"&gt;
    &lt;!-- 包围其中 --&gt;
&lt;/pre&gt;
</pre>
