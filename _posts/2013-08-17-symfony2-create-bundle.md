---
layout: post
title: "Symfony2 (1) - 新建一个bundle"
description: "从头开始学symfony，先创建一个bundle，初始化页面，了解symfony基本工作原理"
category: "Programming"
tags: ["Symfony2", "PHP"]
---

*随着使用symfony的深入，越来越发现symfony很厉害，有自己的kernal，还支持console，这是典型的操作系统的节奏阿。废话不多说，直接上干货了。*

# 新建一个bundle 

<pre class="prettyprint linenums">
php app/console generate:bundle --namespace=Acme/SearchBundle --format=yml
</pre>

`Acme/SearchBundle` 指的是在src目录下会生成一个Acme/SearcBundle的路径，而SearchBundle是新建Bundle的名字。通常默认情况下，我们使用`yml`作为配置文件的语言。

在Symfony2里可以选择三种语言作为配置语言，分别是`yml`，`php`和`xml`。

--------------------------------------------------------------------------

这里补充一下，app/console还支持其他一些操作，比如最常用的清除缓存，可以用

<pre class="prettyprint linenums">
php app/console cache:clear
</pre>

其他的一些命令可以通过以下命令查找

<pre class="prettyprint linenums">
php app/console
</pre>

-------------------------------------------------------------------------

# 查看生成结果

默认地，此时你可以查看`SearchBundle/Resource/config/routing.yml`文件，里面会有当前路由配置的具体内容。我的文件内容如下，

<pre class="prettyprint linenums">
acme_search_homepage:
    pattern:  /hello/{name}
    defaults: { _controller: AcmeSearchBundle:Default:index }
</pre>

这里pattern的意思就是在网址后面按照这里约定的方式传入参数，name是一个变量参数。

比方说，我的网址可以是，`http://localhost/api-article/app_dev.php/hello/zhipeng`：

- `api-article`是project的名字
- `app_dev.php`是默认加载的路径，不用修改
- `hello`就是上面配置文件约定的路径，你可以自己定义
- `zhipeng`便是传入的参数。

再看看具体bundle做了什么，在`SearchBundle/Controller/DefaultController.php`

<pre class="prettyprint linenums">
&lt;?php

namespace Acme\SearchBundle\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\Controller;

class DefaultController extends Controller
{
    public function indexAction($name)
    {
        return $this->render('AcmeSearchBundle:Default:index.html.twig', array('name' => $name));
    }
}
</pre>

也就是说，这里仅仅加载了一个通用的模版，然后输出了作为参数的变量`$name`的值。你可以在浏览器里输入相应的网址来获得一个简单的输入输出功能页面。下面是我的测试输出，

    Hello zhipeng!


