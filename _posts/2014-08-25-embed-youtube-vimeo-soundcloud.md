---
layout: post
title: "Youtube, Vimeo and Soundcloud"
description: "Embed Youtube, Vimeo and Soundcloud Player"
category: "Programming"
tags: ['JavaScript']
---

As the main video/audio online services, it's not easy to embed their videos/audios into your web page. Sometimes you have uncompleted url, sometimes you need to register a developer key so as to get the audio id, which can not be found directly from url, etc. Ok, let's do it.

## Youtube

<object width="100%" height="400"><param name="movie" value="//www.youtube.com/v/fiore9Z5iUg?version=3&amp;hl=en_US&amp;rel=0"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="//www.youtube.com/v/fiore9Z5iUg?version=3&amp;hl=en_US&amp;rel=0" type="application/x-shockwave-flash" width="100%" height="400" allowscriptaccess="always" allowfullscreen="true"></embed></object>

Thanks for the perfect answer, the best version you can find from stackoverflow: [http://stackoverflow.com/questions/5830387/how-to-find-all-youtube-video-ids-in-a-string-using-a-regex/5831191#5831191](http://stackoverflow.com/questions/5830387/how-to-find-all-youtube-video-ids-in-a-string-using-a-regex/5831191#5831191).

	re = /
	    https?://         // Required scheme. Either http or https.
	    (?:[0-9A-Z-]+\.)? // Optional subdomain.
	    (?:               // Group host alternatives.
	      youtu\.be/      // Either youtu.be,
	    | youtube         // or youtube.com or
	      (?:-nocookie)?  // youtube-nocookie.com
	      \.com           // followed by
	      \S*             // Allow anything up to VIDEO_ID,
	      [^\w\s-]       // but char before ID is non-ID char.
	    )                 // End host alternatives.
	    ([\w-]{11})      // $1: VIDEO_ID is exactly 11 chars.
	    (?=[^\w-]|$)     // Assert next char is non-ID or EOS.
	    (?!               // Assert URL is not pre-linked.
	      [?=&+%\w.-]*    // Allow URL (query) remainder.
	      (?:             // Group pre-linked alternatives.
	        [\'"][^<>]*>  // Either inside a start tag,
	      | </a>          // or inside <a> element text contents.
	      )               // End recognized pre-linked alts.
	    )                 // End negative lookahead assertion.
	    [?=&+%\w.-]*      // Consume any URL (query) remainder.
    /ig;

The expression above can solve almost every possibility of youtube url, including:

- latest short format: http://youtu.be/NLqAF9hrVbY
- iframe: http://www.youtube.com/embed/NLqAF9hrVbY
- iframe (secure): https://www.youtube.com/embed/NLqAF9hrVbY
- object param: http://www.youtube.com/v/NLqAF9hrVbY?fs=1&hl=en_US
- object embed: http://www.youtube.com/v/NLqAF9hrVbY?fs=1&hl=en_US
- watch: http://www.youtube.com/watch?v=NLqAF9hrVbY
- users: http://www.youtube.com/user/Scobleizer#p/u/1/1p3vcRhsYGo
- ytscreeningroom: http://www.youtube.com/ytscreeningroom?v=NRHVzbJVx8I
- any/thing/goes!: http://www.youtube.com/sandalsResorts#p/c/54B8C800269D7C1B/2/PPS-8DMrAn4
- any/subdomain/too: http://gdata.youtube.com/feeds/api/videos/NLqAF9hrVbY
- more params: http://www.youtube.com/watch?v=spDj54kf-vY&feature=g-vrec
- query may have dot: http://www.youtube.com/watch?v=spDj54kf-vY&feature=youtu.be
- nocookie domain: http://www.youtube-nocookie.com

Here's a complete js example to test the regular expression:

	var regex_youtube = /https?:\/\/(?:[0-9A-Z-]+\.)?(?:youtu\.be\/|youtube(?:-nocookie)?\.com\S*[^\w\s-])([\w-]{11})(?=[^\w-]|$)(?![?=&+%\w.-]*(?:['"][^<>]*>|<\/a>))[?=&+%\w.-]*/ig;
	var url           = 'https://www.youtube.com/watch?v=qQkBeOisNM0';
	$scope.youtube    = "//www.youtube.com/embed/" + regex_youtube.exec(url)[1] + "?rel=0";

Here's html:

	<iframe width="100%" height="280" src={{youtube}} frameborder="0" allowfullscreen></iframe>


## Vimeo

It seems that Vimeo is simpler than Youtube, actually that's true, at leaste url cases is fewer. Let's see the example:

	var regex_vimeo = /^.*(vimeo\.com\/)((channels\/[A-z]+\/)|(groups\/[A-z]+\/videos\/))?([0-9]+)/;
	var url         = 'http://vimeo.com/104270416';
  $scope.vimeo    = "//player.vimeo.com/video/" + regex_vimeo.exec(value)[5] + "?title=0&amp;byline=0&amp;portrait=0";

Here's the html for Vimeo:

	<iframe src={{vimeo}} width="100%" height="280" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>


## Soundcloud

Actually it's the first time for me to hear [Soundcloud](https://soundcloud.com/), as there are many online music providers, which are much more famous than Soundcloud. You know what, the url that you have only contains the name of the track and author's name, while for embeding soundcloud you must have the track id. Since I need to finish my current task in PT, I tried to find something useful from their official document. Oh god, it's really complex to understand the differences between "SDK" and "Developer" or other columns. Most importantly, I need to register a developer key so as to use their SDK. No way, that's too much work!

Actually, someone found another way to use their giant database, [https://developers.soundcloud.com/docs/oembed#introduction](https://developers.soundcloud.com/docs/oembed#introduction). Believe me, you can't find the page within ten minutes, if you don't use Google and you are new to Soundcloud.

Here we go, as the documentation says, you can access the data by `curl` like this:

	$ curl "http://soundcloud.com/oembed" \\
		-d 'format=json' \\
		-d 'url=http://soundcloud.com/forss/flickermood'

The response is a json data:

	{
	  "version": 1.0,
	  "type": "rich",
	  "provider_name": "Soundcloud",
	  "provider_url": "http://soundcloud.com",
	  "height": 81,
	  "width": "100%",
	  "title": "Flickermood by Forss",
	  "description": "test",
	  "html": "test"
	}

As we are using javascript, you might need jQuery to send API request. Assuming that you have jQuery loaded already:

	$.getJSON('http://soundcloud.com/oembed?callback=?',
	  {
	    format        : 'js',
	    url           : value,
	    maxheight     : 230,
	    show_comments : false
	  }, function(data) {
	    console.log('>>data', data);
	  }
	);

Here's the response:

	{
	  "version": 1,
	  "type": "rich",
	  "provider_name": "SoundCloud",
	  "provider_url": "http://soundcloud.com",
	  "height": 450,
	  "width": "100%",
	  "title": "Somewhere Else EP by Zeds Dead",
	  "description": "Buy Somewhere Else EP on iTunes: smarturl.it/SomewhereElseEP\r\n\r\nwww.facebook.com/zedsdead\r\nwww.twitter.com/whoszed\r\nwww.instagram.com/zedsdeadofficial",
	  "thumbnail_url": "http://i1.sndcdn.com/artworks-000083944897-jacl5v-t500x500.jpg?e76cf77",
	  "html": "<iframe width=\"100%\" height=\"450\" scrolling=\"no\" frameborder=\"no\" src=\"https://w.soundcloud.com/player/?visual=true&url=http%3A%2F%2Fapi.soundclou…k=true&callback=jQuery203016278377058915794_1409013256693&_=1409013256697\"></iframe>",
	  "author_name": "Zeds Dead",
	  "author_url": "http://soundcloud.com/zedsdead"
	}

And then, do whatever you want.

## Extra benefits - [oEmbed](http://oembed.com/)

Only for curiosity, I searched the plugin oEmbed, to my surprise, what a useful plugin it is!

If you are still tired with tons of documentation and annoying developer key, it's really a perfect choice for you. Simple interface, stable service, united interface! More importantly, they support almost everything, like IFTTT, YouTube, Flickr, Hulu, Vimeo, etc. You can check the list from here: [oEmbed](http://oembed.com/). 

Have fun guys!

