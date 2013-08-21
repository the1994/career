---
layout: post
title: "Symfony2 (4) - atoum进行单元测试"
description: "atoum是php测试的一个开源工具，结合symfony我们可以直接安装此bundle并进行测试。与PHPUnit类似，这个bundle也可以进行单元测试和mock测试。除此之外，atoum还支持代码覆盖率检查"
category: "Programming"
tags: ["Symfony2", "PHP", "atoum"]
---

# 测试示例

先上一段代码，然后再讲讲具体代码做了什么。

<pre class="prettyprint linenums">
&lt;?php

use atoum\AtoumBundle\Test\Controller;

/******************************************
 * ATOUM TESTS
 * To run them :
 * cd /path/to/the/project/
 * php app/console atoum BundleName
 *****************************************/

class FolderController extends Controller\ControllerTest
{

    private $userName = "unknown";

    public function setUp() 
    {
        // delete all the data stored in Mongo for this test
    }

    public function beforeTestMethod($testMethod)
    {
        // do something before each test method
    }

    public function testFolderCanBeCreated()
    {
        $client = $this-&gt;createClient();
        $client-&gt;request('POST', '/folders', array('title' =&gt; $title, 'abstract' =&gt; $abstract, 'idp' =&gt; ''));
        $response = $client-&gt;getResponse();

        $this-&gt;integer($response-&gt;getStatusCode())
             -&gt;isEqualTo(200)
             -&gt;string($response-&gt;headers-&gt;get('Content-Type'))
             -&gt;isEqualTo('application/json');

        $json = json_decode($response-&gt;getContent(), true)[0];
        // var_dump($json);
        $this-&gt;string($json['title'])-&gt;isEqualTo($title);
        $this-&gt;string($json['abstract'])-&gt;isEqualTo($abstract);
        $this-&gt;string($json['owner'])-&gt;isEqualTo($this-&gt;userName);
    }
</pre>

- `use`和`namespace`这两个部分根据实际情况自己决定，注意，`use atoum\AtoumBundle\Test\Controller;`是一定要添加的。

- `extends Controller\ControllerTest`不要忘记添加，这里包含了所有的断言语句的实现。

- 跟一般的测试工具类似，这里也包括了`setUp()`函数和`tearDown()`函数，注意，这两个函数不是必须的。在atoum里，还有一个是`beforeTestMethod()`和`afterTestMethod()`函数，同样，这两个函数也不是必须的，但他们的功能与之前两个不同。一般的测试流程如下：

        setUp()

        beforeTestMethod()
        testXXXXXXXX()
        afterTestMethod()

        beforeTestMethod()
        testYYYYYYYY()
        afterTestMethod()

        ...

        tearDown()

- 在具体的测试函数里，首先需要create一个client出来，用来给api发送request，一般的request分成四种，分别是`GET`, `POST`, `PUT`和`DELETE`，分别对应了查增改删。

- 在request函数中，第二个参数是api的route，第三个参数是api需要传入的参数，用array传进去。

- atoum的断言语句比较多，这里通常用到的有以下几个：

<pre class="prettyprint linenums">
// 判断整数值知否相等，大于，大于等于，...
$this-&gt;integer($a)-&gt;isEqualTo($b);
$this-&gt;integer($a)-&gt;isGreaterThan($b);

// 判断字符串是否相等
$this-&gt;string($a)-&gt;isEqualTo($b);

// 判断布尔值
$this-&gt;boolean($a)-&gt;isTrue();
$this-&gt;boolean($a)-&gt;isFalse();
</pre>


