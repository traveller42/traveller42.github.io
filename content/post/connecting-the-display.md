+++
date = "2016-04-09T21:31:42-04:00"
description = "Have to connect first"
draft = false
tags = ["oops", "lcd", "usb"]
title = "Connecting the Display"
topics = ["display"]

+++

Not much progress today.  The LCD I am using for the display on the head unit
requires a mini USB connector.  I only have micro USB connectors right now.
Getting the initial connection with the new LCD display will have to wait.

The USB connector for the ezLCD display I am using provides power, control, and
access to storage for fonts and images directly in the display.

There is another connector that can be used using direct serial access.  This
connector can also provide power.  It uses a specific connector and provides
many other capabilities, but this will require custom programming to leverage.

Current plan is to use USB.  I will also create a library to make interfacing
with the display easier.
