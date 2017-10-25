---
layout: post
title: "Cleaning up an Inaccessible VirtualBox Machine"
date: 2014-05-20 -0400
comments: true
categories: [virtualbox]
---

I had a really difficult time coming up with a title for this post, but essentially what I'm trying to convey is:

* You created a VirtualBox machine
* You deleted/removed/transferred the VM files on your HDD
* VirtualBox will no longer let you manage that machine - indicates "inaccessible" (can't even remove it).

I found myself in this predicament earlier this evening. All I wanted to do was remove the VM from the list of machines in VirtualBox, but it wouldn't let me because it couldn't find any of the files in the given location. After a few hacks, I found a solution. Hopefully, this might help someone.

Given a VirtualBox machine - let's call him "Test Machine", that resides on your host machine's file system
![Setup - Image 1](https://www.calvinallen.net/images/2015/cleaning-up-an-inaccessible-virtualbox-machine/TheSetup.png)
![Setup - Image 2](https://www.calvinallen.net/images/2015/cleaning-up-an-inaccessible-virtualbox-machine/TheSetup2.png)

You, accidentally or purposefully, delete the folder containing the VM
![Folder is gone](https://www.calvinallen.net/images/2015/cleaning-up-an-inaccessible-virtualbox-machine/FolderRemoved.png)

Suddenly, you can no longer access the VM from within the VirtualBox Manager
![Machine Invalid](https://www.calvinallen.net/images/2015/cleaning-up-an-inaccessible-virtualbox-machine/MachineNowInvalid.png)

And, any attempts to remove it are futile
![Cannot Remove](https://www.calvinallen.net/images/2015/cleaning-up-an-inaccessible-virtualbox-machine/CannotRemove.png)

If you can deal with the 'clutter' of an orphaned VM, yay. If not, like me, we gotta get rid of that thing. 

Here's how I did it. 

* Shut down ALL VMs, and close VirtualBox Manager 
* Navigate to your personal VirtualBox settings file (Mine is IN my Users folder - `C:\Users\Calvin\.VirtualBox\VirtualBox.xml`) 
* Edit the file IN Notepad/Notepad2/Notepad++/WhateverEtcPad++2
* Find the `MachineRegistry` section, and remove the `MachineEntry` for the offending machine
![VirtualBox Configuration](https://www.calvinallen.net/images/2015/cleaning-up-an-inaccessible-virtualbox-machine/VirtualBox-Configuration.png)
* Save the file, close, and reopen VirtualBox Manager. If successful, you should no longer see the machine.
![Invalid Machine Gone](https://www.calvinallen.net/images/2015/cleaning-up-an-inaccessible-virtualbox-machine/InvalidMachineGone.png)

That's it! Hope it helps someone! 