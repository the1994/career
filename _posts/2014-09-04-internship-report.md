---
layout: post
title: "Internship Report at Sutoiku, Inc."
description: "Internship Report at Sutoiku, Inc. for my third year of study of Ecole des Mines de Nancy."
category: "Programming"
tags: ["AngularJS", "JavaScript", "Node.js", "Ionicframework", "CSS", "Wikipedia", "d3.js"]
---

>This report is not an official version.
>
>It is for my "stage de fin d'étude à Ecole des Mines de Nancy".
>
>All screenshots are taken by myself or taken from [sutoiku.com](https://db.tt/dhTrnpEu). Please feel free to use them for non commercial usage.

# 1. Introduction

## 1.1 Introduction of STOIC (Sutoiku, Inc.)

STOIC is changing the way people think about business applications. With STOIC, anyone can develop a cloud application, as easily as using a spreadsheet. Whether you start from scratch or from an existing template, you can build the application that will perfectly suit your needs. And you can do that yourself, without having to learn programming or getting help from an expert.

![pic](https://googledrive.com/host/0Bx3dPnCQn7k4TTFpZ1VQNnRPcVk)

# 2. Projects of Internship

Throughout the internship, the main project is to develop Mobile application for STOIC platform with Ionicframework as UI (User Interface) framework. Besides this, I also took part in the Web UI development, in details I implemented 17 form-controllers for different datatypes, ranging from mathmatiques equations to custom map, etc. In addition, I also developed some tools for internal usage and implemented some functions for Formula.js, an open-source repository in Github with more than 1000 stars.

## 2.1 Mobile Application Development

Mobile Application development(Mobile UI) is the main project that I worked on, which consists in refactoring our previous prototype using the Ionic framework, with dynamic client-side AngularJS pages served by static server-side CircularJS pages for localization and theming.

### 2.1.1 Introduction to AngularJS

AngularJS is a JavaScript framework that makes it easier to implement RIA (Rich Internet Application) web applications. AngularJS is created by Google.

AngularJS is based on the MVC pattern (Model View Control). Therefore AngularJS separates your RIA application into models, views and controllers. The views are specified using HTML + AngularJS's own template language. The models and controllers are specified via JavaScript objects and JavaScript functions. Thus, the views are specified declaratively, as HTML normally is, and the models and controllers are specified imperatively, as JavaScript normally is. Just as it is described in its official website:

> AngularJS is a structural framework for dynamic web apps. It lets you use HTML as your template language and lets you extend HTML's syntax to express your application's components clearly and succinctly. Angular's data binding and dependency injection eliminate much of the code you currently have to write. And it all happens within the browser, making it an ideal partner with any server technology.

### 2.1.2 Introduction to Ionicframework

Ionic framework is quite young, as the beta was released in late May 2014, current version is v1.0.0-beta.11. Built on top of the popular AngularJS framework from Google, Ionic utilizes AngularJS to provide the application structure, while Ionic itself focuses on the user interface. In other words, we see a match between the power of Angular and the beauty of Ionic UI.

Ionic provides a set of Angular directives (custom HTML elements) for its own components, making it as easy to use the widgets as writing a line of HTML code. In addition to directives, Ionic uses Angular's touch recognizers, view animation logic, HTML sanitation, and asynchronous communication.

### 2.1.3 Main Use Caces of Mobile UI

#### 2.1.3.1 Home Page

Accorrding to the previous Mobile UI, the home page contained a google map and a list of recent activities. Here's the first version after refactoring with Ionicframework.

[Angular Google Maps](https://angular-ui.github.io/angular-google-maps/#!/) is integrated to mark current user's location due to connection IP.

In the list of current activities, data are extracted from ElasticSearch directly, sorting by update date. In the right top conor, the search button allows user to search globally.

![pic](https://db.tt/370QpbLz)

For the Web UI, the main page is consited of several widgets, for example, a widget can be a chart, a map perspective or even a web page. It can also be applied in Mobile UI. The biggest advantage of WebApp is that libraries can be shared between Web UI and Mobile UI. After integration of widgets, here are the captures for charts widget and activity widget.

![pic](http://38.media.tumblr.com/acf0850e0a83da08071ac86854a0b62c/tumblr_n9jyfdIxmd1rsjz40o2_1280.png)

![pic](https://db.tt/jJPIp3Ng)

#### 2.1.3.2 Applications Page

With the help from Ionicframework, we can easily implement a slide menu like this, which displays the list of applications for current tenant.

![pic](https://db.tt/6jxy0lal)

#### 2.1.3.3 Objects Page

Application is consisted of several objects, once we click on an application, the list of objects will display with the animation. In this case the top search button allows user to search objects inside current list. Thanks to AngularJS filter, it is really easy to filter items inside a list.

![pic](https://db.tt/ww8lZqYY)

#### 2.1.3.4 Records Page

It's the same UI and use case as Objects Page, an object contains several records.

![pic](https://db.tt/NuhCt1VW)

#### 2.1.3.5 Dashboard Page

In this page, we call it Dashboard Page, it's because in this page you can see a Stoic Sheet, a widget that dynamically displays charts or data. Below is the number of records and the button for creating new record.

![pic](http://33.media.tumblr.com/6793c61bcaf0c38dc813317bcc54a524/tumblr_n8to2kaZss1rsjz40o1_1280.png)

#### 2.1.3.6 Details Page

Details Page is the most difficult task among all these use cases, which requires to support Rich Text Form. That means we need to support many types of input box, like text box, check box, date box, imgage box, etc. Even though Ionicframework offers some css templates, but the use cases are far more complicated than these simple framework.

Another problem is I have no experience with css, at the very begining it was really difficult to manipulate DOM component with CSS, jQuery and AngularJS. Maybe it could be better if I started with Web UI development, then I could get familiar with how to code more sophisticatedly with CSS and JavaScript.

The last but not the least, due to the asynchronous programming in JavaScript, I always had the problem with updating data. For example, in order to update a text box, I shouldn't update data each time when user edit a text, it consums lots of connection resource and the delay can not be ignored. So I need to watch user's action, when an user starts to edit, the watch process will hung up and wait util user stops editing for certain milliseconds, like 500 ms or more. Once data is updated, I need to refresh the page.

The capture below is a typical Details Page for an hotel:

![pic](https://db.tt/awv8BoDH)

This is details information page. You can see owner and copyright information and so on.

![pic](https://db.tt/X2r2R7oh)

#### 2.1.3.7 Color Page

I developed this color page for color box. At the moment when I implemented this color selector, I didn't know that in Web UI we were using Tinycolor2 for color calculation. By all means, at least I practiced the color conversion algorithm:

	R' = R/255
	G' = G/255
	B' = B/255
	Cmax = max(R', G', B')
	Cmin = min(R', G', B')
	Δ = Cmax - Cmin

Hue calculation:

![pic](http://www.rapidtables.com/convert/color/rgb-to-hsv/hue-calc.gif)

Saturation calculation:

![pic](http://www.rapidtables.com/convert/color/rgb-to-hsl/sat-calc.gif)

Lightness calculation:

![pic](https://db.tt/MUwBRsS1)

In addition, another key point here is data exchange between two controllers. Here is a simple architecture of AngularJS, as suggested by the team of AngularJS, it's better to change data by using shared service between controllers, as illustrated in the read line blow:

![pic](https://db.tt/9cu8rPgv)


#### 2.1.3.8 Map Page

In Map Page, we use [Angular Google Maps](https://angular-ui.github.io/angular-google-maps/#!/) to draw maps according to given address.

![pic](https://db.tt/bBsDqT4Y)

#### 2.1.3.9 Camera Page

Thanks to the FileAPI and StreamAPI of modern browser, we can access local files or take picture directly from browser and send it to server.

File access is not difficult by comparing with stream development, one tricky part is that we can not modify the style sheet of input button, which has a original appearence without design. The solution is I hide it outside the page and create another button, who can trigger the click event on input button once itself is clicked.

![pic](https://db.tt/xdWNWROe)

For the camera streaming development, I used HTML canvas to draw instant image from camera stream. Once the "camera" button is clicked, canvas will stop drawing and convert base64 pictures to png or jpg format. With the help of Stoic.connector, I can easily upload pictures to AWS server.

By the way, maybe this is a bug of AWS, when I tried to upload a picture to its server, I need to remove the header information of the picture, otherwise the server can not distinguish the file type. Before that I thought I need to modify the header data so as to tell the server about which format it is, but actually what I need to do is just remove this piece of information.

![pic](https://db.tt/rOeUsb16)

![pic](https://db.tt/zxPLc08Q)

#### 2.1.3.10 Icons Page

In this Icons Page, about 3.5k icons are categorized by their tag. In this page, user can search icon by name.

![pic](https://db.tt/z1gpLt4o)

There are two main difficulties in this implementation, some of them are not solved yet:

- Since the amount of icons is really large, we can not diplay all of them in a single page. So I implemented an accordion list by which user can expand a label if he in interested in a certain domian. Actually this is an implementation with pure CSS3, a second level list is embeded in the first level list.
- There's some problem with the garbage collection mechanism of JavaScript, eachtime when we reload this page, it will consume an extra 100MB memory. We tried to trace the consumption of memory but nothing found. I still don't know why Google's V8 engine dosen't take those memory back.

#### 2.1.3.11 Creation Page

The creation page is similar to Details Page, actually they share the same form controllers.

However, the difference is obvious and clear, the action workflow for creating an item dose not equal to display an item.

For example, in order to display an image box, what I need to do is to create a container and fill it with an image. But, for create an image, I need to allow user to take a photo directly from mobile camera or upload a photo from local gallery. They don't have the same use case, neither the user interface.

Here is a sample Creation Page:

![pic](https://db.tt/ftYKGZX7)

## 2.2 Web User Interface Development

### 2.2.1 Introduction to Node.js

JavaScript's rising popularity has brought with it a lot of changes, and the face of web development today is dramatically different. The things that we can do on the web nowadays with JavaScript running on the server, as well as in the browser, were hard to imagine just several years ago, or were encapsulated within sandboxed environments like Flash or Java Applets.

Before digging into Node.js, you might want to read up on the benefits of using JavaScript across the stack which unifies the language and data format (JSON), allowing you to optimally reuse developer resources. As this is more a benefit of JavaScript than Node.js specifically, we won't discuss it much here. But it's a key advantage to incorporating Node in your stack.

As Wikipedia says:

> Node.js is a packaged compilation of Google's V8 JavaScript engine, the libuv platform abstraction layer, and a core library, which is itself primarily written in JavaScript." Beyond that, it's worth noting that Ryan Dahl, the creator of Node.js, was aiming to create real-time websites with push capability, "inspired by applications like Gmail". In Node.js, he gave developers a tool for working in the non-blocking, event-driven I/O paradigm.

After over 20 years of stateless-web based on the stateless request-response paradigm, we finally have web applications with real-time, two-way connections.
In one sentence: Node.js shines in real-time web applications employing push technology over websockets. What is so revolutionary about that? Well, after over 20 years of stateless-web based on the stateless request-response paradigm, we finally have web applications with real-time, two-way connections, where both the client and server can initiate communication, allowing them to exchange data freely. This is in stark contrast to the typical web response paradigm, where the client always initiates communication. Additionally, it's all based on the open web stack (HTML, CSS and JS) running over the standard port 80.

One might argue that we've had this for years in the form of Flash and Java Applets—but in reality, those were just sandboxed environments using the web as a transport protocol to be delivered to the client. Plus, they were run in isolation and often operated over non-standard ports, which may have required extra permissions and such.

With all of its advantages, Node.js now plays a critical role in the technology stack of many high-profile companies who depend on its unique benefits.

### 2.2.2 Introduction to Require.js

RequireJS is a JavaScript file and module loader. It is optimized for in-browser use, but it can be used in other JavaScript environments, like Rhino and Node. Using a modular script loader like RequireJS will improve the speed and quality of your code.

### 2.2.3 Custom Form Controllers

Stoic supports 83 types of data, like textual data, temporal data or geological data, etc. So we create a Showcase in order to make it a whole lot easier to properly test all our new form controls. This form organizes all datatypes by families, with one form section per family for all controls that can be displayed on a single row. All other controls are added at the end of the form. With such an organization, it will also make it easier for new users to learn about our 81 datatypes, by simply looking at their respective controls.

#### 2.2.3.1 CRON Controller

CRON Controller allows users to specify scheduling rules without having to learn the atrocious CRON syntax.

At first we were considering to reuse the plugin [jquery-cron](http://shawnchin.github.io/jquery-cron/), but then I found that the code is wrapped with jQeury and can not be modified directly. So I implemented a plugin, angular-Cron, to interpret basic cron text to human-readable text, for example:

    # This is Cron text
    50 23 1 6 *
    # This is human readable text
    Every year on July 1st at 23:50

![pic](http://38.media.tumblr.com/06af061dc8e9c000803cbf3bdb567aa3/tumblr_na0o40FZgB1rsjz40o4_1280.png)

#### 2.2.3.3 Math Controller

The Math control is powered by [MathJax](http://www.mathjax.org/), an open source JavaScript display engine for mathematics that works in all browsers. It does not support the full LaTeX syntax though, it’s just TeX, but for most equations, it should be plenty enough, and we can easily add it later if users really need it.

![pic](http://31.media.tumblr.com/ac07735259fee3fb588425868e0638e8/tumblr_na2gw9x3oe1rsjz40o1_1280.png)

![pic](http://38.media.tumblr.com/4fe573c4953d69dbce5b562d0b1a4550/tumblr_na0z2fohEF1rsjz40o1_1280.png)

#### 2.2.3.4 Google Docs Controller

Powered by Google Docs API, we can fetch and display the thumbnail of google docs by a given id. User can click on the thumbnail so as to redirect to a new tab, which gives user access to read or edit in Google Docs.

![pic](http://38.media.tumblr.com/d1a1e8c2da625882bceb274604e4d505/tumblr_nabwwsIpZZ1rsjz40o1_1280.png)

#### 2.2.3.5 Video/Audio Controller

Thanks to jPlayer, a media library written in JavaScript, which allows you to rapidly weave cross platform audio and video into your web pages. I integrated this plugin into Stoic platform and customized some style sheets and themes.

![pic](http://38.media.tumblr.com/ba92325168b784919cb1340230af5519/tumblr_navv7e2pDU1rsjz40o1_1280.png)

In addition, we also support Youtube, Vimeo as video player and SoundCloud as audio player.

The problem for Youtube is its URL varies too much, it could be any of the examples below:

- latest short format: [http://youtu.be/NLqAF9hrVbY](http://youtu.be/NLqAF9hrVbY)
- iframe: [http://www.youtube.com/embed/NLqAF9hrVbY](http://www.youtube.com/embed/NLqAF9hrVbY)
- iframe (secure): [https://www.youtube.com/embed/NLqAF9hrVbY](https://www.youtube.com/embed/NLqAF9hrVbY)
- object param: [http://www.youtube.com/v/NLqAF9hrVbY?fs=1&hl=en_US](http://www.youtube.com/v/NLqAF9hrVbY?fs=1&hl=en_US)
- object embed: [http://www.youtube.com/v/NLqAF9hrVbY?fs=1&hl=en_US](http://www.youtube.com/v/NLqAF9hrVbY?fs=1&hl=en_US)
- watch: [http://www.youtube.com/watch?v=NLqAF9hrVbY](http://www.youtube.com/watch?v=NLqAF9hrVbY)
- users: [http://www.youtube.com/user/Scobleizer#p/u/1/1p3vcRhsYGo](http://www.youtube.com/user/Scobleizer#p/u/1/1p3vcRhsYGo)
- ytscreeningroom: [http://www.youtube.com/ytscreeningroom?v=NRHVzbJVx8I](http://www.youtube.com/ytscreeningroom?v=NRHVzbJVx8I)
- any/thing/goes!: [http://www.youtube.com/sandalsResorts#p/c/54B8C800269D7C1B/2/PPS-8DMrAn4](http://www.youtube.com/sandalsResorts#p/c/54B8C800269D7C1B/2/PPS-8DMrAn4)
- any/subdomain/too: [http://gdata.youtube.com/feeds/api/videos/NLqAF9hrVbY](http://gdata.youtube.com/feeds/api/videos/NLqAF9hrVbY)
- more params: [http://www.youtube.com/watch?v=spDj54kf-vY&feature=g-vrec](http://www.youtube.com/watch?v=spDj54kf-vY&feature=g-vrec)
- query may have dot: [http://www.youtube.com/watch?v=spDj54kf-vY&feature=youtu.be](http://www.youtube.com/watch?v=spDj54kf-vY&feature=youtu.be)
- nocookie domain: [http://www.youtube-nocookie.com](http://www.youtube-nocookie.com)

So we can use the regular expression to extract video's id:

```
re = /https?://(?:[0-9A-Z-]+\.)?(?:youtu\.be/|youtube(?:nocookie)?\.com\S*[^\w\s-])([\w-]{11})(?=[^\w-]|$)(?![?=&+%\w.-]*(?:[\'"][^<>]*>|</a>))[?=&+%\w.-]*/ig;
```

![pic](http://38.media.tumblr.com/b2e4f5794f8b725736870c8504dc639f/tumblr_naw2tsmqWQ1rsjz40o1_1280.png)

It seems that Vimeo is simpler than Youtube, actually that’s true, at leaste url sample is less than Youtube:

![pic](http://31.media.tumblr.com/7b70b2595b4b5fde61395bfb757eeece/tumblr_navv7e2pDU1rsjz40o3_1280.png)

Actually it’s the first time for me to hear [Soundcloud](https://soundcloud.com/), as there are many online music providers, which are much more famous than Soundcloud. You know what, the url that you have only contains the name of the track and author’s name, while for embeding soundcloud you must have the track id. Since I need to finish my current task in PT, I tried to find something useful from their official document. Oh god, it’s really complex to understand the differences between “SDK” and “Developer” or other columns. Most importantly, I need to register a developer key so as to use their SDK. No way, that’s too much work!

Actually, someone found another way to use their giant database, [https://developers.soundcloud.com/docs/oembed#introduction](https://developers.soundcloud.com/docs/oembed#introduction). Believe me, you can’t find the page within ten minutes, if you don’t use Google and you are new to Soundcloud.

![pic](http://38.media.tumblr.com/9c525165de7384ce1b93d38549b31019/tumblr_naw2uhUPHw1rsjz40o1_1280.png)

#### 2.2.3.6 Score Controller

In Score editor, we have a algorithm to calculate the completeness of each record, correspondingly we will also give suggestions to improve.

![pic](http://38.media.tumblr.com/df75d0cc812b3863fbb03e4291404687/tumblr_na9t0pQC8P1rsjz40o1_1280.png)

#### 2.2.3.8 Duration Controller

Thanks to [Bootstrap-timepicker](https://github.com/jdewit/bootstrap-timepicker/), we can display time duration.

![pic](http://33.media.tumblr.com/cd4b446947395046d73261002a6ce824/tumblr_naac6tlBEN1rsjz40o2_1280.png)

#### 2.2.3.9 Geo Location Related Controller

Powered by Leaflet and OpenStreet Map, this controller supports geocoding function, that means you can type a name of the city, it can normalise the address and give a exact geolocation point.

![pic](http://31.media.tumblr.com/6f2d0547e2ae5756aa82d7662e7d7214/tumblr_naiehrsVxS1rsjz40o2_1280.png)

Thanks to Geojson, a format for encoding a variety of geographic data structures, we could display lines, polygons or multipolygon in a map.

![pic](http://33.media.tumblr.com/c0e1bc9ad6a2bfe66b5d96cc0e1bf25c/tumblr_nbaq7yeVLG1rsjz40o1_1280.png)

With the help of leaflet, the Geoshape control supports auto-centering and auto-zooming. What this means is that the map is automatically centered and focused on the geoshape being displayed, by finding the arithmetic center of the shape, creating a rectangular bounding box for it, and fitting the map to this box.
By the way, the shape is customizable, like border color, background color, opacity, etc.

![pic](http://33.media.tumblr.com/18f379b7db7c4a00315b518f17586876/tumblr_nb1qpwj86k1rsjz40o2_1280.png)

#### 2.2.3.10 Music Controller

Music datatype uses the [VexFlow](https://github.com/ringw/vexflow/tree/musicxml) library. Without a WYSIWYG editor, this control isn’t super useful, but it’s a great proof of concept.

![pic](http://33.media.tumblr.com/8f0222e874be89eecaff8b1153867c80/tumblr_naio60YWmj1rsjz40o2_1280.png)

![pic](http://31.media.tumblr.com/9d6e1ffa3a36023247df5ae0d503919a/tumblr_naio60YWmj1rsjz40o1_1280.png)

#### 2.2.3.11 IP Controller

We’ve improved the IP control. We now display a link to visit the IP, as well as one form input per component of the IP v4 address, plus the ability to copy and past an entire IP address. This only works for IP v4, but support for IP v6 will be added soon.

![pic](http://38.media.tumblr.com/78878d00e0baedb5919e85500deb734f/tumblr_nan0r4n8Cm1rsjz40o2_1280.png)

#### 2.2.3.12 Barcode Controller

Thanks to [BWIP-JS](https://code.google.com/p/bwip-js/), a barcode writer in pure JavaScript, we support 84 types of barcode.

![pic](http://33.media.tumblr.com/61c94159924f1a480d4471697a7c0ef4/tumblr_naqxn2II2K1rsjz40o3_1280.png)

### 2.2.4 Map Perspective

#### 2.2.4.1 Dimension and Parameters

![pic](http://33.media.tumblr.com/754ed6c5402e751e625492379837bd23/tumblr_nb727oJIJX1rsjz40o2_1280.png)

This is an overview of Map perspective. In order to enable users to customize the map, we provide Dimensions and Parameters, with which user can easily set the propertities of map.

**Dimensions**

-  **Location**, with support for Address, Geopoint, and Geoshape
-  **Color** for the color of markers and shapes
-  **Artifact** for using an artifact like image or video in lieu of a marker
-  **Iconography** for using the icons of categories, objects, or workflows
-  **Size** for the size of markers or artifacts
-  **Style** for styling markers and shapes
-  **Title** for adding titles to markers and shapes

**Parameters**

-  **Attribution** for customizing the attribution notice
-  **Show Title** for enabling the display of marker and shape titles
-  **Center** for centering the map
-  **Zoom** for setting the default zoom level
-  **Map** for selecting which map to use for background tiles
-  **Map** Style for styling the background map
-  **Popup** for defining the template of marker and shape popups

#### 2.2.4.2 Iconography

![pic](http://38.media.tumblr.com/c7c2212894ef682b5ff1e47601963ec0/tumblr_nazo53Gs671rsjz40o2_1280.png)

![pic](http://38.media.tumblr.com/c4215333054c8b73d678054b992e0635/tumblr_nazo53Gs671rsjz40o1_1280.png)

Instead of simple monotonous red markers that we can often find in Google Map, we support multiple types of marker, it can be a font icon or an image. Certainly user can edit the propertities of marker, for example the color, size, etc.

#### 2.2.4.3 Popup

![pic](http://33.media.tumblr.com/5ea52cbecfdc8986f39d48a123195461/tumblr_nb65xbiXo41rsjz40o2_1280.png)

Since we have implemented the iconography, why not go further? Instead of normal hover event which displays illustrational text, we support stoic pages as popup, like the capture above, we can customize the pages by giving the url of stoic pages.

#### 2.2.3.4 Choropleth Map

![pic](https://db.tt/dhTrnpEu)

A choropleth map is a thematic map in which areas are shaded or patterned in proportion to the measurement of the statistical variable being displayed on the map, such as population density or per-capita income.

With the help of geo shape, we can easily implement a choropleth map for population density of different regions.

# 3 Project Management

## 3.1 Agile Software Development

Agile software development is a group of software development methods in which requirements and solutions evolve through collaboration between self-organizing, cross-functional teams. It promotes adaptive planning, evolutionary development, early delivery, continuous improvement and encourages rapid and flexible response to change. It is a conceptual framework that focuses on frequently delivering small increments of working software.

![pic](http://www.pixeldust.net/wp-content/uploads/2013/12/Agile.png)

We break tasks into small increments with minimal planning. Iterations are short time frames (timeboxes) that typically last from one to four weeks. Each iteration involves a cross-functional team working in all functions: planning, requirements analysis, design, coding, testing. At the end of the iteration a working product is demonstrated to stakeholders. This minimizes overall risk and allows the project to adapt to changes quickly. An iteration might not add enough functionality to warrant a market release, but the goal is to have an available release (with minimal bugs) at the end of each iteration.

A common characteristic of our agile development is daily working report. In a brief session, team members report to project manager what they did the previous day, what they intend to do today, and what their roadblocks are.

## 3.2 Bugs Fixing vs New Features Implementation

As with all business decisions, it's a cost/benefit problem. What is the benefit of fixing a bug or adding a feature? What will it cost, including the opportunity cost of not doing something else?

For example, after the development of Mobile UI, I started to work on form controllers. As the requirements changed and some more tests were processed, a serious problem was found that we can not run Mobile UI in iPhone. Even though I was involved in Web UI development at that time, I have to fix the bug of Mobile UI first, because this is more important than new features implementation and I am the one who was familiar with the whole project. If a Mobile App can not run in a real phone, no one can aford to put it off.

## 3.3 Management Tool - Pivotal Tracker

Pivotal Tracker is Pivotal Labs' software as a service product for agile project management and collaboration.

Pivotal Tracker simplifies collaborations across time zones and departments. When the development team is scattered, or when product managers and executives want to jump in, the work is already organized in one spot. People stay in sync and projects stay on course.

In addition, Pivotal Tracker crystallizes priorities. It helps you constantly monitor project scope and focus on what’s essential. So your team is always moving in the right direction and the product takes the most efficient path to market.

Maintaining constant velocity makes milestones more predictable and grounds decisions in what’s real and tangible. Need to know when a new feature might actually be delivered? Tracker has an estimate based on your past performance.

## 3.4 Choices of Technologies

### 3.4.1 Mobile UI Framework

The reasons why we choose cross platform framework are mainly as below:

- With cross platform framework, it is possible to make such an app that can run on all platforms with little efforts with Cordova or PhoneGap.
- Since in STOIC, all of us are JavaScript developers, cross platform development is Cheaper than native development, developers can easily start to work.
- Cross platform development may help in decreasing the time of app development. A simple todo-list can be implemented with two hours from scratch.

Before using Ionicframework I tested some popular frameworks, like Kendo UI, jQuery Mobile, Sencha Touch, OnsenUI, etc. By compare the pros and cons, we finally decided to use Ionicframework as the main front-end framework.

#### 3.4.1.1 jQuery Mobile

jQuery Mobile is arguably the most widely used mobile framework, benefiting from association with the nearly ubiquitous jQuery project. Due to its recognition and association with jQuery-based open source development, jQuery Mobile boasts a huge number of 3rd party plugins, extensions, tools, themes and more.

However developers writing mobile and hybrid mobile apps using jQuery Mobile will encounter the following problems:

However, despite its popularity, jQuery Mobile has been criticized for performing poorly in mobile browsers. The jQuery Mobile team continues to work to improve the framework, including performance issues. If your team opts for jQuery Mobile, avoiding deeply nested DOM structures & unnecessary reflows and investigating the use of libraries like FastClick can help you avoid some of the typical pitfalls that have earned jQuery Mobile the slow label.

In addition, jQuery Mobile provides a light application framework, primarily covering navigation, transitions between views. This can be extended via plugins, or through integration with more comprehensive frameworks. If your app framework needs extend beyond transitions and navigations (for example, templating, two-way binding and more), jQuery Mobile alone may not be a good fit.

#### 3.4.1.2 KendoUI

Telerik's Kendo UI Mobile framework has emerged as a powerful and performance-minded framework for mobile web and hybrid mobile applications. Kendo UI Mobile provides both UI widgets and app framework functionality. Kendo UI Mobile is part of a larger Kendo UI framework that can target both desktop and mobile devices. In addition, Kendo UI Dataviz is arguably one of the best data visualization libraries available for both desktop and mobile web clients.

However, as KendoUI is under commercial license, in the mean time, due to its out-of-date UI design, we decided not to use this framework.

#### 3.4.1.4 Sencha Touch

Sencha will be a recognizable name to many web & mobile developers, likely due to their response to Mark Zuckerberg's assertion that "HTML5 Wasn't Ready". Sencha went on to prove that HTML5 is, indeed, ready for many complex use cases in mobile applications. Sencha Touch focused HTML5 development platform, goes much further than providing only widget-focused features.

Sencha recently updated Sencha Touch so that their device APIs fully support Apache Cordova (i.e. PhoneGap). Similar to Kendo UI Mobile, Sencha Touch makes use of HTML5 and CSS3, taking advantage of hardware acceleration where possible, to create web-based UIs for mobile apps that aim to rival native UI performance.

Apparently Sencha Touch is a powerful framework, howevery just as this, Sencha is heavy for us, and it is not easy to customize if we want to integrate our APIs.

#### 3.4.1.5 Ionicframework

The Ionic framework is an open source framework available from Ionic. This framework offers a library of mobile optimized HTML, JS Components and CSS to allow developers to build highly interactive apps. Ionic is built is SASS and based on and optimized for AngularJS which is part of what makes it so popular.

The UI is clean, simple and based on functionality and speed. That does not mean that the framework lacks display though. Websites and apps are designed to work and display beautifully on all mobile devices and the framework offers a number of mobile components all based on a stunning extensible base theme.

Ionic was built with the latest mobile devices in mind and it uses minimal DOM manipulation and zero jQuery. It uses AngularJS which allows developers to develop serious, robust mobile applications.

This is the most important factor that leads us to make the decision to use Ionicframework. In WebUI the whole UI was developed under AngularJS, with which plenty plugins are integrated and customized. We can share most of the plugins if we use Ionicframework.

## 3.5 Existing Problem and Possible Solution

### 3.5.1 Mobile UI

#### 3.5.1.1 Memory Leaks

An obvious problem is that each time when all icons are loaded, an extra 100MB memory will be consumed, even when we return back to previous page, the garbage collection will not collect this amount of resource. I tried to track the consumption of memory usage during the whole workflow, but I didn't find the exact problem.

#### 3.5.1.2 Launching Time and Large Cache

After optimization, like loading libraries asynchronously, currently the launching time is around 5s for desktop browser and 50 seconds for a real mobile phone. Obviously this launching time is inacceptable.

The problem is we have a really large local cache to load during launching, whose size is more than 40MB. Before loading Mobile UI pages, we need to write cache into local storage, which requires a considerable time. One point must be explained here is, in priorit we use IndexedDB as local storage by default. However as the picture below indicates, currently Safari and iOS Safari don't support IndexedDB, so we use IndexedDBShim, which exposes the IndexedDB API in unsupported browsers using WebSQL. This shim is basically an IndexedDB-WebSql adapter.

![pic](https://db.tt/8p1I3uWu)

Fortunately，the next version of Safari will support IndexedDB, coming with OS X 10.10 and iOS 8.

### 3.5.2 Form Controllers

#### 3.5.2.1 Cron Controller

As time is limited, I implemented a simple cron box that only supports basic syntax of CRON data. Cron syntax supports special characters Asterisk (\*), Slash (/), Comma (,), Hyphen (\-), Percent (%) and "L", "W", etc. The difficulty relies on the transformation from Cron text to human readable text.

#### 3.5.2.2 Map Related Controller

We are changing our map plugin from Google to Leaflet and OpenStreetMap, which are open-sourced and customizable. But in the same time, there are also quite many problems.

For example, as you can see in the screenshot below, even thought the map repeats, but the markers only display in a single interval. This is an open issue of leaflet, and there's no appropriate solution for this bug.

![pic](https://db.tt/ZAKDNeZr)

# 4 Summary

## 4.1 Gains

### 4.1.1 Technical Skills

The biggest gain from the internship is I learnt asynchronous programming, both for the user interface and server. Node.js is a powerful tool that massively improves the I/O performance thanks to its Non-blocking I/O.

Besides the programming language, I also learnt many pratical frameworks and related plugins, for example, AngularJS, require.js, lodash.js, etc. In open source community there are plenty fantastic libraries, which is developed and maintained by many brilliant developers from all around the world. The Stoic team also contributed a lot to many open source libraries. I did learnt a lot by reading their source code.

### 4.1.2 Tasks Management

As I am the one who works on Mobile UI for almost 5 months, Ismael and I started the project by designing the UI and defining basic requirements. We made a plan for the whole developing process and gave priorities to each task.

With the help from Ismael and Jacques, I learnt how to handle the conflict between fixing existing bugs and implementing new features. In a startup like us, we use agile development that requires fast interation. We need to ensure that implemented code can run without bugs firstly, then add more new features.

### 4.1.3 Cooperation in a Team

During the whole internship, I have cooperated with almost everyone in this team, by which I get familiar with the whole stoic platform quickly. Ismael is my tutor of internship, we discussed everyday about my work and we work togather for the Mobile UI and some meta data. Jacques keeps testing the Mobile UI and form controllers and gives me bug reports. Besides we also worked togather about image loading to Amazon AWS. Florian always gives me help in AngularJS and helps me to improve the code quality. I worked with Pascal and Yves about stoic authentication for Mobile UI. Jim helped me to integrating some functions into Formula.js. I worked with Huges to test the performance of IndexedDB and at last, I also worked with Francois to refactory the map perspective.

From the cooperation, I get familiar with the whole stoic platform quickly.







