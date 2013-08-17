---
layout: post
title: "Symfony2 (0) - installation and configuration"
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

If everything goes well, you can continue to update or install vendors and configure caches and logs.

    $ php ../composer.phar update
	$ setfacl -R -m u:apache:rwx -m u:`whoami`:rwx app/cache app/logs
	$ setfacl -dR -m u:apache:rwx -m u:`whoami`:rwx app/cache app/logs
	$ sudo ln -s ~/[project path]/web /var/www/html/[project name]
	$ sudo setfacl -m u:apache:x /home/`whoami`

But, if unluckly, you came across with some problem during the update, such as this,

    [UnexpectedValueException]                                                   
	'/home/zhipeng/projects/sites/api-article/vendor/symfony/icu/Symfony/Component/Icu/70ba4a12bda6a6bd714ec1cddd087038.0' is not a zip archive.

I'm not sure where is the problem, some one told me it is because the cache of composer, some one said it is because the problem of symfony version. Well, I have not  found the solution. So at last I downloaded the tar pkg **with vendors** from [website](http://symfony.com/download). Unpack it and continue your command from `setfacl`,

	$ setfacl -R -m u:apache:rwx -m u:`whoami`:rwx app/cache app/logs
	$ setfacl -dR -m u:apache:rwx -m u:`whoami`:rwx app/cache app/logs
	$ sudo ln -s ~/[project path]/web /var/www/html/[project name]
	$ sudo setfacl -m u:apache:x /home/`whoami`

Now you can test your project from this page, for me it is [http://localhost/api-article/app_dev.php/](http://localhost/api-article/app_dev.php/). It depends on the path of your soft lien in `/var/www/html/[project name]`.

## Configure SELINUX

SELINUX is the security policies manager that can prevent the Apache server to access to a home directory, or to successfully write into the app/cache and app/logs directories.

We have two options:

-  Disable SELINUX; It’s an option, although not the optimal for those that like of security on their systems. You disable SELINUX following this [tutorial](http://ashu-geek.blogspot.com.es/2011/12/how-to-disable-selinux-on-fedora-16.html).

-  If you like the SELINUX protection, these are the commands you need to type to allow the Apache server to access on R/W to our project directories:

	$ sudo setsebool -P httpd_enable_homedirs true
	$ sudo setsebool -P httpd_read_user_content true
	$ sudo setsebool allow_httpd_anon_write true
	$ sudo chcon -t chcon -t public_content_rw_t app/cache
	$ sudo chcon -t chcon -t public_content_rw_t app/logs
