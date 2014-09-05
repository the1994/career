---
layout: post
title: "Internship Report at Sutoiku, Inc."
description: "Internship Report at Sutoiku, Inc. for my third year of study of Ecole des Mines de Nancy."
category: "Programming"
tags: ["AngularJS", "JavaScript", "Node.js", "Ionicframework", "CSS", "Wikipedia", "d3.js"]
---

# 1. Introduction

## 1.1 Introduction of STOIC (Sutoiku, Inc.)

STOIC is changing the way people think about business applications. With STOIC, anyone can develop a cloud application, as easily as using a spreadsheet. Whether you start from scratch or from an existing template, you can build the application that will perfectly suit your needs. And you can do that yourself, without having to learn programming or getting help from an expert.

// Introduction of Stoic

// Introduction of Mobile UI / Ionicframework / Cordova / AngularJS / Node.js

// Introduction of Formula.js / mdCache / GatewayJS

// Methodology, agile development / fast iteration / pair programming


# 2. Projects of Internship

Throughout the internship, my main task is to develop Mobile application for STOIC platform with Ionicframework as UI (User Interface) framework. Secondly, I also took part in the Web UI development, in details I developped the form-controllers for different datatypes, ranging from mathmatiques equations to custom map, etc. In addition, I also developed some tools for internal usage, such as GEOCODING tool, which formatter address by Google Map API and Leaflet Geocoding API.

## 2.1 Mobile Application Development

Mobile Application development is the main project that I worked on, which consists in refactoring our previous prototype using the Ionic framework, with dynamic client-side AngularJS pages served by static server-side CircularJS pages for localization and theming. This allows us to test this architecture before we apply it to our refactored web user interface once we implement localization and theming for it.

The reasons why we choose cross platform framework are mainly as below:

- With cross platform framework, it is possible to make such an app that can run on all platforms with little efforts with Cordova or PhoneGap.
- Since in STOIC, all of us are JavaScript developers, cross platform development is Cheaper than native development, developers can easily start to work.
- Cross platform development may help in decreasing the time of app development. A simple todo-list can be implemented with two hours from scratch.

### 2.1.1 Introduction of AngularJS

AngularJS is a JavaScript framework that makes it easier to implement RIA (Rich Internet Application) web applications. AngularJS is created by Google.

AngularJS is based on the MVC pattern (Model View Control). Therefore AngularJS separates your RIA application into models, views and controllers. The views are specified using HTML + AngularJS's own template language. The models and controllers are specified via JavaScript objects and JavaScript functions. Thus, the views are specified declaratively, as HTML normally is, and the models and controllers are specified imperatively, as JavaScript normally is. Just as it is described in its official website:

> AngularJS is a structural framework for dynamic web apps. It lets you use HTML as your template language and lets you extend HTML's syntax to express your application's components clearly and succinctly. Angular's data binding and dependency injection eliminate much of the code you currently have to write. And it all happens within the browser, making it an ideal partner with any server technology.

### 2.1.2 Introduction of Ionicframework

Ionic framework is quite young, as the beta was released in late May 2014, current version is v1.0.0-beta.11. Built on top of the popular AngularJS framework from Google, Ionic utilizes AngularJS to provide the application structure, while Ionic itself focuses on the user interface. In other words, we see a match between the power of Angular and the beauty of Ionic UI.

Ionic provides a set of Angular directives (custom HTML elements) for its own components, making it as easy to use the widgets as writing a line of HTML code. In addition to directives, Ionic uses Angular's touch recognizers, view animation logic, HTML sanitation, and asynchronous communication.

While you can use Ionic straight after cloning or unpacking the library zip, you can also install their Node.js-based CLI through NPM and start quickly with their seed project.

Even though Angular is currently the Ionic's workhorse, the developers are keeping their (and ours) options open with plans to support other frameworks such as Knockout or EmberJS. This particular review is strongly influenced by AngularJS and it doesn't vouch for the accuracy with other frameworks when Ionic support emerges.

### 2.1.3 Framework comparison

Before changing to Ionicframework, I also tested several popular frameworks, like Kendo UI, jQuery Mobile, Sencha Touch, OnsenUI, etc. 

#### 2.1.3.3 jQuery Mobile

jQuery Mobile is arguably the most widely used mobile framework – benefiting from association with the nearly ubiquitous jQuery project. Due to its recognition and association with jQuery-based open source development, jQuery Mobile boasts a huge number of 3rd party plugins, extensions, tools, themes and more.

Developers writing mobile and hybrid mobile apps using jQuery Mobile will encounter the following:

- Heavy use of HTML "data-\*" attributes. For example, a page in a jQuery Mobile application is simply a DOM element with a data-role attribute value like this: <div data-role="page"></div> Experienced web developers will pick up these kinds of framework conventions quickly.
- jQuery Mobile provides a light application framework – primarily covering navigation, transitions between views. This can be extended via plugins, or through integration with more comprehensive frameworks. If your app framework needs extend beyond transitions and navigations (for example, templating, two-way binding and more), jQuery Mobile alone may not be a good fit.
- It's designed to work within a Responsive Web Design (RWD) context – enabling developers to target a wide range of devices.
- A wide array of device and browser support as well as a helpful theme roller to help with quickly customizing the otherwise clone look and feel.

However, despite its popularity, jQuery Mobile has been criticized for performing poorly in mobile browsers. The jQuery Mobile team continues to work to improve the framework, including performance issues. If your team opts for jQuery Mobile, avoiding deeply nested DOM structures & unnecessary reflows and investigating the use of libraries like FastClick can help you avoid some of the typical pitfalls that have earned jQuery Mobile the slow label.

#### 2.1.3.2 KendoUI

Telerik's Kendo UI Mobile framework has emerged as a powerful and performance-minded framework for mobile web and hybrid mobile applications. Kendo UI Mobile provides both UI widgets and app framework functionality. Kendo UI Mobile is part of a larger Kendo UI framework that can target both desktop and mobile devices. In addition, Kendo UI Dataviz is arguably one of the best data visualization libraries available for both desktop and mobile web clients.

Developers writing mobile and hybrid mobile apps will encounter the following:

- Theming that matches the ‘native' look and feel of iOS, Android, Blackberry and Windows Phone 8, as well as a flat theme that looks nice across multiple devices.
- Similar to jQuery Mobile, Kendo UI Mobile makes use of HTML5 `data-*` attributes. For example, a `view` in a Kendo UI Mobile application is a DOM element with an attribute/value of `data-role="view"`. This naturally extends to Kendo UI Mobile's widgets as well, since (for example) an unordered list element can be made into a listview element simply by adding `data-role="listview"` to the element.
- Two-way binding, with a declarative syntax. Kendo UI Mobile provides some fairly sophisticated application framework features, with MVVM (model-view-viewmodel) infrastructure included. Application state is typically maintained in ‘view models', which are bound to views (DOM templates). As data in views change, the view models are automatically updated (and vice versa). By declarative we mean that the metadata necessary to enable two-way binding can be provided in the actual markup. For example, to bind the text content of a span to the firstName value of a view model, developers simply include this in the markup: <span data-bind="text: firstName"></span> Frameworks supporting two-way binding often help eliminate the same tired boilerplate code necessary in traversing DOM structures to retrieve state (user input, etc.). This can be a big productivity boost for your team.
- Also included in the application framework features: view transitions, navigation & layout templates (which can be highly customized) as well as DataSources – an abstraction over retrieving data from multiple kinds of sources (for example, simple HTTP services, local data or even some Back-end-as-a-Service offerings). The Kendo UI team has gone quite a ways further than primarily UI/widget focused frameworks like jQuery Mobile in providing more substantial application architectural help.

However, because KendoUI is under commercial license, in the mean time due to its old UI design, we decided to abandon this framework.



#### 2.1.3.4 Sencha Touch

Sencha will be a recognizable name to many web & mobile developers – likely due to their response to Mark Zuckerberg's assertion that "HTML5 Wasn't Ready". Sencha went on to prove that HTML5 is, indeed, ready for many complex use cases in mobile applications. Sencha Touch – Sencha's mobile focused HTML5 development platform – goes much further than providing only widget-focused features.

Sencha recently updated Sencha Touch so that their device APIs fully support Apache Cordova (i.e. PhoneGap). Similar to Kendo UI Mobile, Sencha Touch makes use of HTML5 and CSS3 (taking advantage of hardware acceleration where possible) to create web-based UIs for mobile apps that aim to rival native UI performance. Developers building projects with Sencha Touch can expect the following:

- Sencha Touch leans more heavily towards "full app framework" than many other popular options. It provides an MVC style architecture, complete with storage, device profile and top-level application abstractions.
- Sencha Touch ships with 50 built-in components (and developers can create their own as well).
- It's my understanding that Touch shares some common code with ExtJS (and common conceptual paradigms), so developers familiar with ExtJS will pick things up quickly. I would also argue that developers used to frameworks like Backbone.js will also pick up the concepts more readily than developers used to UI frameworks that focus on declarative bindings in markup.
- Sencha Touch provides its own abstractions for things like history management and XHR – which is in line with expectations of any framework seeking to be a more "one stop/full-stack" option.

Apparently Sencha Touch is a powerful framework, howevery just as this, Sencha is heavy for us, and it is not easy to customize if we want to integrate our APIs.


### 2.1.4 Main Use Caces of Mobile Application

#### 2.1.4.1 Home Page

Accorrding to the previous Mobile UI, the home page contained a google map and a list of recent activities. Here's the first version after refactory with Ionicframework.

[Angular Google Maps](https://angular-ui.github.io/angular-google-maps/#!/) is integrated to mark current user's location due to connection IP.

In the list of current activities, data are extracted from ElasticSearch directly, sorting by update date. In the right top conor, the search button allows user to search globally.

![pic](https://db.tt/370QpbLz)

For the Web UI, the main page is consited of several widgets, for example, a widget can be a chart, a map perspective or even a web page. It can also be applied in Mobile UI. The biggest advantage of WebApp is that libraries can be shared between Web UI and Mobile UI. After integration of widgets, here are the captures for charts widget and activity widget.

![pic](http://38.media.tumblr.com/acf0850e0a83da08071ac86854a0b62c/tumblr_n9jyfdIxmd1rsjz40o2_1280.png)

![pic](https://db.tt/jJPIp3Ng)

#### 2.1.4.2 Applications Page

With the help from Ionicframework, we can easily implement a slide menu like this, which displays the list of applications for current tenant.

![pic](https://db.tt/6jxy0lal)

#### 2.1.4.3 Objects Page

Application is consisted of several objects, once we click on an application, the list of objects will display with the animation. In this case the top search button allows user to search objects inside current list. Thanks to AngularJS filter, it is really easy to filter items inside a list.

![pic](https://db.tt/ww8lZqYY)

#### 2.1.4.4 Records Page

It's the same UI and use case as Objects Page, an object contains several records.

![pic](https://db.tt/NuhCt1VW)

#### 2.1.4.5 Dashboard Page

In this page, we call it Dashboard Page, it's because in this page you can see a Stoic Sheet, a widget that dynamically displays charts or data. Below is the number of records and the button for creating new record.

![pic](http://33.media.tumblr.com/6793c61bcaf0c38dc813317bcc54a524/tumblr_n8to2kaZss1rsjz40o1_1280.png)

#### 2.1.4.6 Details Page

Details Page is the most difficult task among all these use cases, which requires to support Rich Text Form. That means we need to support many types of input box, like text box, check box, date box, imgage box, etc. Even though Ionicframework offers some css templates, but the use cases are far more complicated than these simple framework.

Another problem is I have no experience with css, at the very begining it was really difficult to manipulate DOM component with CSS, jQuery and AngularJS. Maybe it could be better if I started with Web UI development, then I could get familiar with how to code more sophisticatedly with CSS and JavaScript.

The last but not the least, due to the asynchronous programming in JavaScript, I always had the problem with updating data. For example, in order to update a text box, I shouldn't update data each time when user edit a text, it consums lots of connection resource and the delay can not be ignored. So I need to watch user's action, when an user starts to edit, the watch process will hung up and wait util user stops editing for certain milliseconds, like 500 ms or more. Once data is updated, I need to refresh the page.

The capture below is a typical Details Page for an hotel:

![pic](https://db.tt/awv8BoDH)

This is details information page. You can see owner and copyright information and so on.

![pic](https://db.tt/X2r2R7oh)

#### 2.1.4.7 Color Page

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


#### 2.1.4.8 Map Page

In Map Page, we use [Angular Google Maps](https://angular-ui.github.io/angular-google-maps/#!/) to draw maps according to given address.

![pic](https://db.tt/bBsDqT4Y)

#### 2.1.4.9 Camera Page

Thanks to the FileAPI and StreamAPI of modern browser, we can access local files or take picture directly from browser and send it to server.

File access is not difficult by comparing with stream development, one tricky part is that we can not modify the style sheet of input button, which has a original appearence without design. The solution is I hide it outside the page and create another button, who can trigger the click event on input button once itself is clicked.

![pic](https://db.tt/xdWNWROe)

For the camera streaming development, I used HTML canvas to draw instant image from camera stream. Once the "camera" button is clicked, canvas will stop drawing and convert base64 pictures to png or jpg format. With the help of Stoic.connector, I can easily upload pictures to AWS server.

By the way, maybe this is a bug of AWS, when I tried to upload a picture to its server, I need to remove the header information of the picture, otherwise the server can not distinguish the file type. Before that I thought I need to modify the header data so as to tell the server about which format it is, but actually what I need to do is just remove this piece of information.

![pic](https://db.tt/rOeUsb16)

![pic](https://db.tt/zxPLc08Q)

#### 2.1.4.10 Icons Page

![pic](https://db.tt/z1gpLt4o)

#### 2.1.4.11 Creation Page

![pic](https://db.tt/ftYKGZX7)

### 2.1.5 Difficulties

#### 2.1.5.1 New Technologies

Before the internship, even though I had developed several android applications, I had very little experience in JavaScript programming, neither jQuery nor AngularJS. Thanks for Ismael, we started the internship by doing pair programming, from which I learnt the basic grammar of JavaScript and some of STOIC's libraries, like mdCache, a middleware for local cache management.

At the beginning of Mobile App development, I went to a meetup organised by Ionic team in San Francisco. The author of Ionic gave me many pratical suggestions and presented me the plan of future development, which gives me a berif idea of what is cross platform application and what is the average architecture.

In addition, it's super difficult for me to get used to asynchronize programming. We use Require.js to arrange third-party libraries, which helps us to solve the problem of asynchronize loading.

For example, a common problem is that Ionic depends on AngularJS, we need to ensure that AngularJS is fully loaded before Ionic. The loading time can not be ignored since a single file is large enough. Currently we have integrated more than 40 kinds of thrid-parties libraries, all of them are under MIT license.

#### 2.1.5.2 Complex Concept of STOIC

The complexity of STOIC is far more than I could imagine. It was difficult for me to understand the whole system, which has many abstract concepts and complicated relationships. It was getting better when I finished the first version of Mobile Application.

### 2.1.6 Brief Summary

## 2.2 Web User Interface Development

### 2.2.1 Introduction of Node.js

JavaScript's rising popularity has brought with it a lot of changes, and the face of web development today is dramatically different. The things that we can do on the web nowadays with JavaScript running on the server, as well as in the browser, were hard to imagine just several years ago, or were encapsulated within sandboxed environments like Flash or Java Applets.

Before digging into Node.js, you might want to read up on the benefits of using JavaScript across the stack which unifies the language and data format (JSON), allowing you to optimally reuse developer resources. As this is more a benefit of JavaScript than Node.js specifically, we won't discuss it much here. But it's a key advantage to incorporating Node in your stack.

As Wikipedia says:

> Node.js is a packaged compilation of Google's V8 JavaScript engine, the libuv platform abstraction layer, and a core library, which is itself primarily written in JavaScript." Beyond that, it's worth noting that Ryan Dahl, the creator of Node.js, was aiming to create real-time websites with push capability, "inspired by applications like Gmail". In Node.js, he gave developers a tool for working in the non-blocking, event-driven I/O paradigm.

After over 20 years of stateless-web based on the stateless request-response paradigm, we finally have web applications with real-time, two-way connections.
In one sentence: Node.js shines in real-time web applications employing push technology over websockets. What is so revolutionary about that? Well, after over 20 years of stateless-web based on the stateless request-response paradigm, we finally have web applications with real-time, two-way connections, where both the client and server can initiate communication, allowing them to exchange data freely. This is in stark contrast to the typical web response paradigm, where the client always initiates communication. Additionally, it's all based on the open web stack (HTML, CSS and JS) running over the standard port 80.

One might argue that we've had this for years in the form of Flash and Java Applets—but in reality, those were just sandboxed environments using the web as a transport protocol to be delivered to the client. Plus, they were run in isolation and often operated over non-standard ports, which may have required extra permissions and such.

With all of its advantages, Node.js now plays a critical role in the technology stack of many high-profile companies who depend on its unique benefits.

In this post, I'll discuss not only how these advantages are accomplished, but also why you might want to use Node.js—and why not—using some of the classic web application models as examples.

### 2.2.2 Introduction of Require.js

RequireJS is a JavaScript file and module loader. It is optimized for in-browser use, but it can be used in other JavaScript environments, like Rhino and Node. Using a modular script loader like RequireJS will improve the speed and quality of your code.

### 2.2.3 Custom Form Controllers

#### 2.2.3.1 CRON Controller

#### 2.2.3.2 CSV Controller

#### 2.2.3.3 Math Controller

#### 2.2.3.4 Google Docs Controller

#### 2.2.3.5 Video/Audio Controller

#### 2.2.3.6 Score Controller

#### 2.2.3.7 Link Related Controller

#### 2.2.3.8 Duration Controller

#### 2.2.3.9 Geo Location Related Controller

#### 2.2.3.10 Music Controller

#### 2.2.3.11 IP Contrller

### 2.2.4 Map Perspective

### 2.2.5 Difficulty

### 2.2.6 Brief Summary

## 2.3 Formula.js Development

### 2.3.1 Introduction of Formula.js

### 2.3.2 Wikipedia Infobox Parser Function

### 2.3.3 Geocoding Function

### 2.3.4 Other Functions

### 2.3.5 Difficulties

### 2.3.6 Brief Summary






