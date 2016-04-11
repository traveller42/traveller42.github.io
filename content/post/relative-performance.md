+++
date = "2016-04-10T21:06:13-04:00"
description = "A review of the different systems I use"
draft = false
tags = ["go", "golang", "performance", "unixbench", "benchmark", "linux"]
title = "Relative Performance"
topics = ["Performance"]

+++

I've been quite impressed with the performance of the Chromebook that has
become my primary portable system.  It is an Acer Chromebook 11 C740.  The CPU
is a dual-core Celeron 3205U running at a nominal 1.5 GHz.  It has 4 GB of RAM
and a 256 GB SSD drive.  I'm running this system in Developer mode which gives
shell access.  I've created a chroot that is running a current version of
Ubuntu.  This is running within the ChromeOS system.  I decided to do some
testing to see what the real values were.  This is the **new** system.

The **big** system was custom built a few years ago and has multiple spinning
disks, the smallest of which is 400 GB, and 16 GB of RAM.  The CPU is an
eight-core AMD FX-8120.

The **old** system is a Dell Insprion E1405 purchsed nearly 9 years ago.  The CPU
is a dual-core Core 2 Duo T7200 running at a nominal 2.0 GHz.  It has 3.2 GB of
RAM and a 320 GB spinning disk.  This has become my primary desktop as its
hinge has broken and it is no longer usable as a laptop.

# Michi-Go

The process that got my attention is a program I translated from Python to the
Go language that plays the Go game.  This program reads a couple of large files
once at the start, but is processor-bound for the rest of execution.

There are a couple benchmark test built into the program.  The first,
mcbenchmark, reads the pattern files and then does 20 playouts of the initial,
empty, board.  This benchmark is single-threaded.  The second, tsbenchmark, starts
with the initial, empty, board and generates a move.  This requires 1400 playouts
in the current version of the program.  This benchmark is multi-threaded.

The results for this set of test are:

System | mcbenchmark | tsbenchmark
-------|------------:|-------------:
Old | 7.689s | 28,584s
New | 7.452s | 24.709s
Big | 4.966s | 8.802s

There is some indication that the Chromebook, new system, may be faster per thread
in the **tsbenchmark** than the big system.  I'll need to look at this in more
detail.

# Unix Bench

This is an old series of benchmarks used to evaluate the relative performance of
servers.  This is version 5.1.3 of the Byte Unix Benchmarks.  I'm only reporting
the overall score for each system.  The default is to do a single-threaded run
and a multi-threaded run with the number of parallel processes equal to the
number of cores available.

These are the results:

System | 1 thread | 2 threads | 8 threads
---|---:|---:|---:
Old | 671.4 | 1312.8 | -
New | 777.1 | 1495.0 | -
Big | 832.6 | - | 2169.1

I should probably try to fill in some of the gaps in this data to better
understand the differences in the operation of these three systems.

# Conclusions

Not too much to draw at present, but one thing is pretty clear:  The modern
Celeron is better than the old mobile Core 2 Duo, even at a slower clock speed.
