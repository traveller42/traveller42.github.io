+++
date = "2016-04-01T23:04:47-04:00"
draft = false
title = "Start of a New Blog"
tags = ["blog", "hugo", "github", "plans"]
topics = ["Starting"]

+++

# Building a Portable Supercomputer
While I am starting on April 1, this is actually something I am working on.

# Hugo
I'm using [Hugo](http://gohugo.io/) to generate these pages.  This is actually
the second site I've created using Hugo.  The first is a [site](http://traveller42.github.io/ogs-notifier/) for a Chrome
Extension I support.

Once everything is in place, this is quick and easy to maintain.  However, there
are many fiddly bits that need to accounted for before it all works as desired.

# Github
Since this site and the source used to create it are hosted on Github, part of
getting everything working involved arranging and populating the proper repository
in the correct manner.  I've got this working manually for now, but my next task
will be to create a script to automate the deployment of the new pages.  Once that
is stable, I intend to leverage a Continuous Integration tool to automagically
generate and deploy the new pages when I push new source to the repository.
