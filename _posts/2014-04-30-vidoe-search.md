---
layout: post
title: "Building a video search engine exploiting the video content"
date: 2016-05-20
category: search
tags: [elasticsearch, kibana]
---
![video_search]({{ site.baseurl }}/public/posts_imgs/video_search.png)
I was part of a group that did this work. The other group members are ([Evan Durfee](durfee@kth.se), [Magnús Þór Benediktsson](bened@kth.se), [Nick Anderson](nanderso@kth.se) and [Sofia Broomé](sbroome@kth.se));

When it comes to indexing video databases (e.g. youtube), the majority of existing search engines uses the textual metadata associated with the videos to index them (I don't about youtube). This metadata includes things like the title of the video, the description, the uploader, the upload date, etc. The quality of returned videos (in term of satisfying the user need) for search queries depends to a large extend on how good the videos metadata describes to the videos.

Different from traditional video search engines (in the previous paragraph), the objective of this work was to build a video search engine that uses the video content (not the metadata) to index the videos, assuming the video content better describes the videos. 

The first challenge is how to extract the video content.

To be continued ...
