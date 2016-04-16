+++
date = "2016-04-15T23:11:26-04:00"
description = "The Law of Diminishing Returns"
draft = false
tags = ["golang", "performance", "testing", "go", "benchmark"]
title = "Unexpected Overhead of Extra Threads"
topics = ["Performance"]

+++

Earlier, I had mentioned that it appeared that the individual threads on the
Chromebook seemed to be faster than the threads on the 8-core server running at
a clock speed over 50% higher.  I've done the deeper look I suggested then, and
I have found something interesting:  For the program I used (my Go playing
program, michi-go), reducing the number of threads results in each thread doing
more work.

Michi-go is written in the Go language.  This language has concurrency as a
first-class concept.  Allowing concurrent routines to operate at the same time
results in some parallelism.  This concurrency is present in michi-go even when
the current process is conceptually "single-threaded".  The search aspect of the
program is explicitly written to be "multi-threaded".  The two benchmarks in the
code are **mcbenchmark** and **tsbenchmark**.  **mcbenchmark** is the
"single-threaded" test.  It runs a playout, a random game, a specified number
of times.  These playouts are run sequentially.  **tsbenchmark** is the
"multi-threaded" test.  It essentially generates a move from an empty board, just
like the first move of the game.  To determine what that move should be, michi-go
will do a specified number of different playouts and pick the one that has the
highest likelihood of a win.  Since each playout is independent of any other, the
work is spread out across multiple workers.

I know there is some overhead for handling the extra workers and I already knew
I wasn't saturating the CPU when allowing the program to use parallel threads
equal to the number of cores (8 in the case of the test system).  I didn't expect
any significant impact on the "single-threaded" test, but any change I would
expect to be beneficial.

My initial test was to limit the program to 2 processes, so I would be testing
the same situation as the 2-core Chromebook.  The **tsbenchmark** test took less
than twice as long with this limit.  This is a significant improvement in
efficiency.  This was much more than I was expecting.  What I did not expect was
the result of the **mcbenchmark** test.  This test was actually faster when the
program with the limit in place.

I've now completed a more detailed series of tests to see how this change in
operation develops.  I ran the each test 10 times and reported the mean elapsed
time.  I repeat this starting with a limit of 1 process and increasing by one
until I run with 8, the number of physical cores on the system.  Here are the
results:

Processes | mcbenchmark | tsbenchmark
:--------:|------------:|------------:
1 | 4.24 | 29.81
2 | 4.25 | 15.61
3 | 4.28 | 11.95
4 | 4.30 | 10.47
5 | 4.29 | 9.65
6 | 4.28 | 9.16
7 | 4.29 | 8.73
8 | 4.27 | 8.56
**9** | 4.27 | 8.55
**10** | 4.27 | 8.61
**11** | 4.29 | 8.60
**12** | 4.26 | 8.67

All values are in seconds and the standard deviation is +/- .01s.

Over-subscribing the cores clearly did not help and the extra work creating and
managing the extra workers eventually becomes noticeable.

One thing that may be causing some of the observed effects is my use of channels
for communication between parts of the program.  These are first-class objects in
the Go language and are *thread safe*.  This means any critical section in the
supporting code is protected to ensure that only one thread access that section
at a time.  This can lead to other threads waiting to enter that section. Some
of this effect may be mitigated as I spend time trying to make the program more
efficient and make changes to avoid situations requiring a wait.
