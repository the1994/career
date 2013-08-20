---
layout: post
title: "Symfony2 (3) - atoum进行单元测试与mock测试"
description: "atoum是php测试的一个开源工具，结合symfony我们可以直接安装此bundle并进行测试。与PHPUnit类似，这个bundle也可以进行单元测试和mock测试。除此之外，atoum还支持代码覆盖率检查"
category: "Programming"
tags: ["Symfony2", "PHP", "atoum"]
---

# Atoum Bundle

--------------

## 简单介绍

atoum是php测试的一个开源工具，结合symfony我们可以直接安装此bundle并进行测试。与PHPUnit类似，这个bundle也可以进行单元测试。除此之外，atoum还支持代码覆盖率检查。

## 开源项目地址

- [Atoum](https://github.com/atoum/Atoum)

- [AtoumBundle](https://github.com/atoum/AtoumBundle)

## 安装教程

根据symfony的习惯，bundle需要通过composer安装

	{
		"require": {
			"atoum/atoum": "dev-master",
			"atoum/atoum-bundle": "dev-master"
		}
	}

修改好composer.json文件后，还需要修改app/AppKernal.php

    if (in_array($this->getEnvironment(), array('dev', 'test'))) {
        //.....
        $bundles[] = new atoum\AtoumBundle\AtoumAtoumBundle();
    }

## 常用命令

重用的几条命令也很简单，跟symfony的console结合得很好，直接用

	$ php app/console atoum FooBundle --env=test # launch tests of FooBundle
	$ php app/console atoum FooBundle BarBundle --env=test # launch tests of FooBundle and BarBundle
	$ php app/console atoum acme_foo --env=test # launch tests of bundle where alias is acme_foo
	$ php app/console atoum --env=test # launch tests from configuration.

## 示例

- - -

**ps**，最近几天过得实在太狼狈了，因为昨天失误，结果把钥匙忘在屋子里。明明家就在眼前，可就是回不去。以后一定要引以为戒，生于忧患，死于安乐。

希望今晚不会再被冻得睡不着。


