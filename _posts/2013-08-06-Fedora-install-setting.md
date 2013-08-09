---
layout: post
title: "Basic setting for Fedora installation"
description: ""
category: "Programming"
tags: ["Vim"]
---

## Close AMD Graphics Card

Firstly check your status

    cat /sys/kernel/debug/vgaswitcheroo/switch

Maybe luck enough, you can see the information below

    0:IGD:+:Pwr:0000:00:02.0
    1:DIS: :Off:0000:01:00.0

IGD is Integrated Graphics Device, and DIS is AMD graphics card. We should disable it by typing:

    echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
    echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

These two commands indicate the working card and disable another one. It can be checked by typing the first command. In order to disable AMD card forever, you need to modify */etc/rc.d/rc.local*

    echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

At last, change the file rights to be executable
    
    sudo chmod +x rc.local

## Add Ctrl+Alt+T

In short cut menu, add a new shortcut by setting *gnome-terminel* with Ctrl+Alt+T.

## Installation

### Basic tools

    sudo su
    yum install vim
    yum install git
    yum install gnome-tweak-tool
    ...

### Sublime text

Download the latest version of Sublime text, unzip it and new a desktop shortcuts.

    [Desktop Entry]
    Name=Sublime
    Comment=Sublime Text 2
    Exec=/home/zhipeng/Develop/tools/Sublime_Text_2/sublime_text
    Icon=/home/zhipeng/Develop/tools/Sublime_Text_2/Icon/48x48/sublime_text.png
    Terminal=false
    Type=Application
    Categories=Application
    StartupNotify=true

Then add this desktop shortcuts to */usr/share/application*

### VLC/Skype

It needs to download the rpm from official website.

## Appearence

### Font

There are pre-built packages for Fedora users. Run these commands instead of installing these files manually. It is recommended to restart your system after installation. If you've already run these commands before, then your normal system updates will keep your packages up to date.

    sudo rpm -Uvh http://www.infinality.net/fedora/linux/infinality-repo-1.0-1.noarch.rpm 
    sudo yum install freetype-infinality fontconfig-infinality

### Top pannel

A dirty fix for that can be editing the panel section in gnome-shell.css. But after every update to the shell this customization will get lost, so its beter to keep a backup copy of what changes you are making.

Edit the file `/usr/share/gnome-shell/theme/gnome-shell.css`

Find the panel section and modify the code like this:

    #panel {
        color: #ffffff;
        background-color:rgba(0,0,0,0.5);
        font-weight: bold;
        height: 1.86em;
    }

Here's my desktop

![desktop](http://media-cache-ak0.pinimg.com/736x/81/bb/8d/81bb8dff8d7bc71f905ec09e69119784.jpg)

