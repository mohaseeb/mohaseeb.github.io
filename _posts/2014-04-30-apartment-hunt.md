---
layout: post
title: "New rental apartments alert system"
date: 2016-06-19
category: other
tags: [web crawling]
---
If you live in (or have been to) Stockholm, I bet you know [how fierce it is to rent a place](http://www.bbc.com/capital/story/20160517-this-is-one-city-where-youll-never-find-a-home), and you would appreciate the piece of software I wrote. Using this software, I got a first hand contract within a month ... YESSS!. This was in 2014.

[Rental houses in Sweden](http://www.sabo.se/om_sabo/english/Sidor/Publichousing.aspx) are either owned by private companies or by the municipalities. The process of renting the houses to the public is controlled by the owners, or in many cases by broker companies. Due to the huge demand and the supply shortage, rental seekers have to wait in queues for years (~6 to get a place in a Stockholm suburb). Most housing brokers use a first-apply-first-served queues (bostadssnabben in swedish) to rent some of the less favourable apartments: short term rents, far from city center, some of the new built apartments (I guess this is because these are more expensive). These apartments are though scarce and hugely sought after. I targeted one of such queues managed by the biggest housing broker in Stockholm.

The plan was to build an agent that monitor the housing broker's first-apply-first-served queue and notify me as soon as new apartments are posted there. So I wrote a a software that has: 1) a [web crawler](https://en.wikipedia.org/wiki/Web_crawler) that crawls the queue web page and returns the available apartments list, 2) a logic that identify if the returned list contained a new apartment or not (this logic relies on a database for persistance), and 3) a notifier, that send emails if a new apartment was found. Since I was only interested on whether new apartments were added or not, I used to calculate the hash value of the returned apartment list and compare it the hash value of the previously returned list (the previously returned list is stored in the database).The application was written in Java and [jsoup](https://jsoup.org/) was used for the crawler. To have the app running 24/7, it was deployed in [Google cloud app engine product](https://cloud.google.com/appengine/) and hence the app engine data store was used for persistance. 

I am always observant to the rules, so at the time of writing the software, I checked and did not find any policy mentioned by that broker which prevents robots from crawling that page (i.e. there was no [robot.txt](http://www.robotstxt.org/robotstxt.html) regarding that).

