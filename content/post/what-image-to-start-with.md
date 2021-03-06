+++
date = "2016-04-07T21:38:03-04:00"
description = "Deciding which load to use "
draft = false
tags = ["raspbian", "arch", "linux", "os", "plan 9", "jessie"]
title = "What Image to Start With"
topics = ["Planning"]

+++

# Decisions, Decisions, Decisions

Since a single system image OS is not a viable options, I need to decide what
system image to start with.

As interesting as Plan 9 is, I think I will wait an look at that one after I
have more experience with the capabilities of the more travelled path.

I will use a Linux load of some kind.  This environment is very efficient and I
am very familiar with building and maintaining system using Linux.  This
narrows the choice down to two main alternatives: Raspbian and Arch.

# Raspbian

The most popular load of the Raspberry Pi series is Raspbian, a derivative of
the Debian Linux family.  This is not much of a surprise as Raspbian is
designed to support the primary goal of the Raspberry Pi program, education.
It is quite friendly in its implementation.  It presents a graphical desktop,
includes many applications in the base load, and uses the same Apt package
management tools as Ubuntu, another Debian derivative.  The current release
supports all variants of the Raspberry Pi from the original ARMv6 models to
the most recent ARMv8 model.  This consistency will simplify configuration
and could allow using some of the older devices I have with the nodes in the
cluster.  The current version of Raspbian is based on the Debian Jessie
release.  There is also a Raspbian Jessie Lite image that has only the base
OS and a minimal set of tools.  These can be used to the nodes other than the
head node.  (It can also be used for the head node once I know what I want
packages I want to use.)

# Arch

Arch Linux on ARM (ALARM) is another option.  Arch uses a different image for
the original models of Raspberry Pi and the new models, 2 and 3.  This starts
as a minimal collection of tools expecting the user to install those items
needed for the task at hand.  This project requires more knowledge of Linux
than Raspbian which shouldn't be a major issue for me.  It also uses a
different package management tool, pacman, that I do not have experience with.
There will be more building of tools from source, but that also allows more
control.  This may eventually lead to a better system and improved performance
relative to Raspbian.  It might be easier to adapt a 64-bit kernel using Arch
as a basis.

# Current Plan

I've downloaded each of the images available.  I will create a boot image for
each and see what that looks like.  I will use that review to guide where I go
next.
