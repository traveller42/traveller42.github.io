+++
date = "2016-04-04T23:59:59-04:00"
description = "Things that just don't work"
draft = false
tags = ["old computers", "virtualbox", "crashplan", "windows", "oops"]
title = "Bad Ideas"
topics = ["Mistakes"]

+++

## Bad Ideas
* Trying to launch a two-years dormant VM on a current version of
VirtualBox on a 7 year old computer that is definitely showing
its age.

This was prompted by a change in policy by Code 42 Software, the
owners of CrashPlan, a very good backup program and service.
The new policy is to delete cloud repositories for computers that
have not connected in over 6 months.  This is only an issue as I
have a couple of Windows VMs that I keep for the rare times I need
a Windows environment.  Each of these VMs has not been active in
two years as I have had no need to run a program on Windows in that
time.

Unfortunately, there are a couple resources that I would like to
maintain that require Windows.  Therefore, I decided to launch one
of the VMs and update the CrashPlan software and let it refresh the
repository.  It has now been trying to launch the VM for almost an
hour.  It has also effectively locked up the GUI for the old computer.

This is being composed on my Chromebook where I have duplicated the
git repo for the site.  I should document the steps needed as someone
may want to do it again some day.

I'm going to leave the poor system trying to run the VM.  Hopefully, I
can either log into a shell, or get control back on the GUI enough to
shutdown the VM.  I do have a good backup, so I could just move the
data.
