+++
date = "2016-04-03T23:40:35-04:00"
description = "What does Hugo do with random files in the source root"
draft = false
tags = ["hugo", "github"]
title = "Hugo Root"
topics = ["Testing"]

+++

**tl;dr** Hugo doesn't do anything with a file that it hasn't been told how to handle.

I host the source for this blog in a [Github repository](https://github.com/traveller42/traveller42.github.io).  Github will place a
notice suggesting a Readme if one doesn't exist.  In general, this is a good idea.  
It let's the developer describe what the code hosted in the repository is intended
to do or support.  It can be used as initial documentation for a small project and
a jumping-off point for a larger project.

I have now added such a file to the source branch of my blog repository.  The real
reason for this is to test what will happen with files created in the source root.
My next task is to create a deploy script.  Now, I know I can just leave it in the
source root.  This helps to keep things simple.

This script won't do much.  It is only a few steps and I have been doing them from
memory since the first build.
