+++
date = "2016-04-02T23:10:04-04:00"
description = "teaching helps one learn"
draft = false
tags = ["tcp", "learning", "teaching"]
title = "It Takes Three"
topics = ["Network"]

+++

I've always heard that the best way to really understand something is to explain
it to someone else.  Today, I learned a related truth:  *Trying* to explain something
to another is a good way to find out what you *do not* know.

I've been dealing with data communications for pretty much my entire professional
career.  I understand how a signal travels along a wire, and have used this to find
where that wire is broken.  I have tapped serial lines for gather data in parallel
with the primary system.  I once was able to get an ancient mainframe and a PC to
communicate when much more experienced consultants had declared it wasn't possible.
I've deployed, monitored, analyzed IP networks.  I've written programs that operated
at all levels of the stack.  If asked, I would have said I had a firm grasp of the
low-level operation of the Transmission Control Protocol (TCP).

Today was the first time I had tried to explain the initiation of a TCP connection.
I knew it used a three-way handshake.  I could recognized the handshake when looking
at a packet trace.  I just never thought about it.  I knew it could break.  I knew the
effects of a break, deliberate or otherwise.  I've always had this part handled by
a library call, so I never had to implement it myself.  It just worked, or it didn't.
I could handle either case in my code.  I never had to work with the steps in
isolation.

I was asked about the details of the initiation of a TCP connection by another
computer programmer with experience with using networks, but not with network programming.
I got several things wrong and created much confusion before actually getting the
gist of the process explained and the knowledge successfully imparted.

Since I was reviewing packet traces today, I had plenty of opportunity to look at
the process as implemented.

[If you truly have a solid understanding of the three-way handshake, you can stop
reading now.]

The TCP Three-way handshake
1. SYN from client
2. SYN-ACK from Server
3. ACK from client

The SYN flag is set to indicate that the packet includes the starting sequence number
from the client.  The SYN-ACK acknowledges the receipt of the previous packet and
includes the starting sequence number from the server.  The client then sends an ACK to
indicate that it has received the packet.  From this point on, all packets between
the client and the server should have the ACK flag set.

The Wikipedia [page on TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)
, as usual, has more detail than most of us will ever need on TCP and the details of
the three-way handshake to start the connection and the **four-way** handshake for tearing
down the connection.
