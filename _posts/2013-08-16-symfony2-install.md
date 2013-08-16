---
layout: post
title: "Symfony2 installation and configuration"
description: "Symfony2 installation and configuration in Fedora19, including the installation of apache, php, MySQL server, phpMyAdmin, composer and other tools"
category: "Programming"
tags: ["Symfony2", "PHP", "MySQL", "Fedora"]
---

The installation includes Apache, MySql, PhpMyAdmin, Git, and every necessary libraries to work.

# Installation

## Apache on Fedora 18

	$ sudo yum install httpd
	$ sudo chkconfig httpd on
	$ sudo service httpd start

After the last command, you can type `http://localhost` to check the local httpd service. If you see the welcome page of apache, it is done.

## MySQL

	$ sudo yum install mysql-server mysql
	$ sudo service mysqld start
	$ sudo chkconfig mysqld on
	$ sudo mysql_secure_installation

## PHP

	$ sudo yum install php php-mysql php-pecl-apc php-gd php-intl php-xml php-process php-pecl-xdebug

Even it is necessary to specify the Time Zone into a config file within the `/etc/php.d` directory, in a new file called `timezone.ini`:

    $ sudo gedit /etc/php.d/timezone.ini


    [Date]
    ; Defines the default timezone used by the date functions 
    date.timezone = "Europe/Paris"

and restart the apache server

    $ sudo service httpd restart

## PHPMyAdmin

	$ sudo yum install phpmyadmin
	$ sudo service httpd restart

The phpMyAdmin will be available at [http://localhost/phpmyadmin](http://localhost/myphpadmin).

## Git

    $ sudo yum install git

## Symfony2

Choose your work directory,

    $ mkdir sites
	$ cd sites

Install composer

    $ curl -sS https://getcomposer.org/installer | php
    $ mv composer.phar /usr/local/bin/composer

**Note**: If the above fails due to permissions, run the `mv` line again with `sudo`.

Then, just run composer in order to run `composer` instead of `php composer.phar`.

Create your symfony project

    $ composer create-project symfony/framework-standard-edition api-article 2.3

Here api-article is the name of project, 2.3 is the latest version of symfony.

