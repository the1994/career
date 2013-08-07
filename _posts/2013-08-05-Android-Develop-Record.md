---
layout: post
title: "Android Develop Record(06) - Action Bar"
description: ""
category: "Programming"
tags: ["android"]
---

# Action Bar

From Android 3.0, Action bar has become a popular design widget for users.

![actionbar](http://developer.android.com/images/ui/actionbar@2x.png)

However we can't apply this design to those previous version, such as android 2.2, 2.3, etc. Although recently android-support-v* has published as a official solution, this compatibility problem has not been solved perfectly.

[ActionBarSherlock](http://actionbarsherlock.com/) is a open source library, which can handle this problem far more than android-support-v4 or v13.

## How to add ActionBarSherlock



## Customize your ActionBarSherlock

With this library, you can extend it as parent and customize your personal action bar.

In your */res/value/styles.xml*, you can modify the theme configuration, here is my example

{% highlight xml %}
<resources>

    <style name="Theme.MyTheme" parent="Theme.Sherlock.Light">
	<item name="actionBarStyle">@style/Theme.MyTheme.ActionBar</item>
	<item name="android:actionBarStyle">@style/Theme.MyTheme.ActionBar</item>
    </style>

    <style name="Theme.MyTheme.ActionBar" parent="Widget.Sherlock.ActionBar">
	<item name="android:background">@drawable/bg_header</item>
	<item name="background">@drawable/bg_header</item>
	<item name="android:titleTextStyle">@style/Theme.MyTheme.ActionBar.TitleTextStyle</item>
	<item name="titleTextStyle">@style/Theme.MyTheme.ActionBar.TitleTextStyle</item>
    </style>

    <style name="Theme.MyTheme.ActionBar.TitleTextStyle" parent="TextAppearance.Sherlock.Widget.ActionBar.Title">
	<item name="android:textColor">#ffffff</item>
    </style>

</resources>
{% endhighlight %}

From this xml file, you can see it extends from parent Theme.Sherlock.light, what I customized is just the background.

Note, don't forget to modify your *AndroidManifest.xml*, change the theme to `"@style/Theme.MyTheme"`.

Good luck!


