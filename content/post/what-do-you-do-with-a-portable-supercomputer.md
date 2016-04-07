+++
date = "2016-04-06T23:59:59-04:00"
description = "My initial ideas on what to do with it now that I have it"
draft = false
tags = ["planing", "hadoop", "parallel computer", "distributed computing", "raspberry pi"]
title = "What Do You Do With a Portable Supercomputer?"
topics = ["Ideas"]

+++

While I wait for the replacement cables, I can spend some time
thinking about what I will actually do with this portable
supercomputer once I have it up and running.

To start, the portable supercomputer is a cluster of 4 nodes in a
single, small frame with integrated power and internal network.
Each node of this cluster is a Raspberry Pi 3 B, so calling it a
supercomputer is a bit of a stretch.  The important thing is that
each of these systems has separate memory and storage.  All nodes
are connected together with a network switch.  The head node will
use it internal wifi or a USB network adapter for connections with
external systems.  The only required physical connection will be
power.

My first idea was to create a distributed build environment.
There used to be a distributed make that would spread the work out
over multiple cooperating systems.  This seems to have
disappeared.  Another take on this was some kind of single system
image configuration.  There was a system called Amoeba that
managed processes over multiple compute resources, but there has
been no recent work on it.  There are a few systems that appear to
be similar, but they are only supported on x86 architecture CPUs.
In this space is Plan 9 from Bell Labs.  There is a port of Plan 9
to the RPi environment.  It is currently 32-bit and not really
single system image, but it is interesting, designed for a
distributed computing environment, and light weight.  Plan 9 is
definitely worth considering as a path of investigation using this
cluster.

Another possibility is to create a Hadoop cluster.  This is an
important framework in the big data space and learning more about
it will be beneficial.  There are walk-throughs and tutorials for
the RPi environment, so the initial cycle could be quite easy. I
may do this as it has such a low bar to entry.  Next steps would
depend on what I want to do and if a Hadoop environment is the
appropriate place to do it.  Just adding another tool for the
toolkit is good enough.

Finally, I'm considering doing something like a Beowulf cluser.
The task in this case would be to investigate parallel
programming.  A tool for this investigation would be to see how to
distribute the simulations used in the Go (game) program I wrote
Go (language) across the cluster.  Learning what contributes to
any improvement and what blocks improvement would be the purpose
here.  As a systems guy, I would want to know how I can tell what
my limiting resource is.  Am I constrained by the limited
compute power, the lack of memory, or the slow network?  What is
the improvement curve.  How linear, or not, is it?

Regardless of which of these, if any, I work on, I plan to see if
I cannot make a 64-bit ARM version of a current Linux kernel run
on this hardware.
