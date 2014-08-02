---
layout: post
title: "Wikipedia Infobox Parser in NodeJS"
description: "Wikipedia infobox parser in NodeJS"
category: "Programming"
tags: ['NodeJS']
---

A simple parser in node.js for wikipedia infobox, like the box in the right of picture below:

![pic](https://db.tt/woGRt6a3)

Due to the aweful lexical grammar, sorry I don't mean to be offensive, but this information box is really **mal-organisé**. There are many third party parsers, but none of them is perfect. After trying developing this parser, I realized that it's hyper difficult to take all conditions into consideration. So, [this parser](https://github.com/jesusjzp/wikiparser) is far  from perfection.

**Just fork the [repo](https://github.com/jesusjzp/wikiparser) and do whatever you can help!**

## Install

	npm install

## Test

	npm test

## Usage

	var parseWiki = require('wiki-infobox-parser');

	parseWiki('France', function(err, result) {
		if (err) { console.error(err); }
	  console.log(JSON.stringify(result));
	});


## TODO

- Redirction
- Multiple opetions redirection
- Multiple languages support

## Examples

![pic](https://db.tt/imZd0cyb)


	{
	    "name": "node.js",
	    "logo": "frameless",
	    "author": "Ryan Dahl",
	    "developer": "[http://github.com/ry/node/blob/master/AUTHORS Node.js Developers], Joyent, [https://github.com/joyent/node/graphs/contributors Github Contributors]",
	    "operating system": "Mac OS X, Linux, Solaris, FreeBSD, OpenBSD, Windows (older versions require Cygwin), webOS",
	    "status": "Active",
	    "released": "{{release date|2009|05|27}}",
	    "latest release version": "0.10.29",
	    "latest release date": "{{release date|2014|06|16}}",
	    "latest preview version": "0.11.13",
	    "latest preview date": "{{release date|2014|05|01}}",
	    "programming language": "C, C++, JavaScript",
	    "genre": "Event-driven networking",
	    "license": "MIT",
	    "website": "{{URL|http://nodejs.org}}"
	}


![pic](https://db.tt/USdvntLJ)


	{
	    "settlement_type": "City",
	    "image_skyline": "Downtownpacom.JPG",
	    "image_caption": "Palo Alto",
	    "flag_size": "100px",
	    "image_seal": "Palo_Alto_Seal.gif",
	    "seal_size": "100x100px",
	    "image_map": "Santa_Clara_County_California_Incorporated_and_Unincorporated_areas_Palo_Alto_Highlighted.svg",
	    "mapsize": "250x200px",
	    "map_caption": "Location in Santa Clara County and the state of California",
	    "coordinates_region": "US-CA",
	    "subdivision_type": "Country",
	    "subdivision_name": "United States",
	    "subdivision_type1": "State",
	    "subdivision_name1": "California",
	    "subdivision_type2": "County",
	    "subdivision_name2": "Santa Clara",
	    "government_type": "Council-Manager",
	    "leader_title": "Mayor",
	    "leader_name": "Nancy Shepherd",
	    "leader_name1": "Mark Berman",
	    "leader_title2": "Council Member",
	    "leader_name2": "Karen Holman",
	    "leader_title3": "Council Member",
	    "leader_name3": "Larry Klein",
	    "leader_title4": "Council Member",
	    "leader_name4": "Gail A. Price",
	    "leader_title5": "Council Member",
	    "leader_name5": "Gregory Scharff",
	    "leader_title6": "Council Member",
	    "leader_name6": "Greg Schmid",
	    "leader_title7": "Council Member",
	    "leader_name7": "Patrick Burt",
	    "leader_title8": "Vice Mayor",
	    "leader_name8": "Liz Kniss",
	    "established_title": "First Settled",
	    "established_date": "1769",
	    "established_title3": "Incorporated as City",
	    "established_date3": "April 16, 1894",
	    "area_total_sq_mi": "25.787",
	    "area_land_sq_mi": "23.884",
	    "area_water_sq_mi": "1.903",
	    "area_total_km2": "66.787",
	    "area_land_km2": "61.858",
	    "area_water_km2": "4.929",
	    "area_water_percent": "7.38",
	    "population_as_of": "2010",
	    "population_total": "64,403",
	    "population_density_km2": "auto",
	    "population_density_sq_mi": "auto",
	    "timezone": "PST",
	    "utc_offset": "-8",
	    "timezone_DST": "PDT",
	    "utc_offset_DST": "-7",
	    "coordinates_display": "display=inline,title",
	    "elevation_m": "9",
	    "elevation_ft": "30",
	    "postal_code_type": "ZIP codes",
	    "postal_code": "94301, 94303, 94304, 94306",
	    "area_code": "650",
	    "area_code_type": "Area code",
	    "blank_name": "FIPS code",
	    "blank_info": "06-55282",
	    "blank1_name": "GNIS feature ID",
	    "blank1_info": "0277572",
	    "website": "[http://www.cityofpaloalto.org/ www.cityofpaloalto.org]"
	}



## Reference

- [Wikipedia API](http://en.wikipedia.org/w/api.php)

- [Syntax of Wiki Markup](http://en.wikipedia.org/wiki/Help:Wiki_markup)