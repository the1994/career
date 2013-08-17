---
layout: post
title: "Symfony2 (2) - 利用NelmioApiDocBundle自动生成API/DOC(译)"
description: "NelmioApiDocBundle是一个开源的Symfony组建，能够自动生成每个bundle以及内部每个action的document，并支持sandbox测试，非常方便api开发"
category: "Programming"
tags: ["Symfony2", "PHP"]
---

# NelmioApiDocBundle

NelmioApiDocBundle是一个开源的Symfony组建，能够自动生成每个bundle以及内部每个action的document，并支持sandbox测试，可以手动变量输入，非常方便api的开发。

Github的地址是 [https://github.com/nelmio/NelmioApiDocBundle](https://github.com/nelmio/NelmioApiDocBundle).

# 如何安装

把下面的代码添加到`composer.json`文件中

    {
        "require": {
            "nelmio/api-doc-bundle": "dev-master"
        }
    }

在内核文件中`app/AppKernel.php`添加相应的bundle信息

    // app/AppKernel.php
    public function registerBundles()
    {
        return array(
            // ...
            new Nelmio\ApiDocBundle\NelmioApiDocBundle(),
        );
    }

修改路由配置文件`routing.yml`，添加路径，以后就可以通过`api/doc`直接访问

    # app/config/routing.yml
    NelmioApiDocBundle:
        resource: "@NelmioApiDocBundle/Resources/config/routing.yml"
        prefix:   /api/doc


修改配置文件`app/config/config.yml`，使其生效:

    # app/config/config.yml
    nelmio_api_doc: ~


# 具体在代码中如何添加

我们平时做开发最头疼的一个问题就是如何使得文档能够跟开发保持同步，如果修改文档也像修改代码那样频繁，一定需要花费大量的时间和精力去维护。这就是为什么我推荐**NelmioApiDocBundle**自动文档生成工具。

所有的API接口都写在代码的annotation中，非常方便。

(由此可见，我们的代码的注释也不一定是完全没有用的，这一点在其他语言里体现的也比较多，比如java。)


## ApiDoc() 注释 

这个bundle为你的每个controller提供了`ApiDoc()`annotation

<pre class="prettyprint linenums">
&lt;?php

namespace Your\Namespace;

use Nelmio\ApiDocBundle\Annotation\ApiDoc;

class YourController extends Controller
{
    /**
     * This the documentation description of your method, it will appear
     * on a specific pane. It will read all the text until the first
     * annotation.
     *
     * @ApiDoc(
     *  resource=true,
     *  description="This is a description of your API method",
     *  filters={
     *      {"name"="a-filter", "dataType"="integer"},
     *      {"name"="another-filter", "dataType"="string", "pattern"="(foo|bar) ASC|DESC"}
     *  }
     * )
     */
    public function getAction()
    {
    }

    /**
     * @ApiDoc(
     *  description="Create a new Object",
     *  input="Your\Namespace\Form\Type\YourType",
     *  output="Your\Namespace\Class"
     * )
     */
    public function postAction()
    {
    }
}
?>
</pre>

在注释部分，有以下几个属性我们可以使用:

* `section`: 允许给资源分组

* `resource`: 是否这个函数描述了一个主要资源，默认是否

* `description`: 用来描述当前的函数

* `deprecated`: 允许把当前函数设置成deprecated，默认是否

* `filters`: 一个过滤数组

* `input`: the input type associated to the method (currently this supports Form Types, classes with JMS Serializer metadata, and classes with Validation component metadata) useful for POST|PUT methods, either as FQCN or as form type (if it is registered in the form factory in the container).

* `output`: the output type associated with the response.  Specified and parsed the same way as `input`.

* `statusCodes`: 状态码，如404，500等。比如下面的代码，

<pre class="prettyprint linenums">
&lt;?php

class YourController
{
    /**
     * @ApiDoc(
     *     statusCodes={
     *         200="Returned when successful",
     *         403="Returned when the user is not authorized to say hello",
     *         404={
     *           "Returned when the user is not found",
     *           "Returned when somehting else is not found"
     *         }
     *     }
     * )
     */
    public function myFunction()
    {
        // ...
    }
}
</pre>    

这个bundle也可以通过定义的路由来获取信息，比如`requirements`, `pattern`, 等等，所以为了最好地使用这个bundle，你应该严格定义每个函数的requirements等信息。




*本文翻译自[NelmioApiDocBundle](https://github.com/nelmio/NelmioApiDocBundle)的github主页的官方文档*
