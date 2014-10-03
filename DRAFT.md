STRUCTURE IDEAS
===============

INTERFACE
=========

Server should serve a double-side API Interface, as usual:
* CLIENT API
* SERVER API

They should share the same interface:
* Heads
* Devices
* Windows
* Tasks


### Heads

**Head** seems to be something very ambiguous. **Head** is a core of an interface, we could have a **Browser-based Head**, **iOS-based Head**, **Android-based Head**, and so on.

Heads are meant to be stackable, so we could have multiple heads running at the same time on the same server. For instance, we could create 2 instances of a **Browser-based Head** so we can separate tests from two different apps. Got it?

Since `Neck` is "only" a bridge, we want you to create the next-gen **Head**, so if you got any idea don't hesitate to try and contribute! :)


### Devices

You should connect multiple **Device**s to one **Head**, they belong to them! // 1:M
You could have Google Glass connected into it, literally!

Each `Device` should have specific properties so the test developers could filter some to choose where they want to run their tests.

I could give a pratical example with a **Browser-based Device**, do you know which properties it should have?

* Platform - linux, darwin, windows ...
* OS - Android 4.4.3, Mac OS 10.10, Ubuntu 14.10, Windows XP... // hehhe
* Browser - Chrome, Safari, Mozilla ...
* Device Manufacturer - Apple, Samsung, OEM ...
* Device Model - iPhone 5, iPhone 4s, Galaxy S4, Galaxy S7, OEM ...

I won't place here all examples but, you got the idea! :)

`next();`

### Windows

You should connect multiple **Window**s to one **Device**, they belong to them! // 1:M

Well, sorry windows fans, this has nothing to do with Microsoft® Windows®, the best example i can get you to understand this is: a Browser! On a browser you separate environments with `window` instances, doesn't matter if they are windows, tabs or f*cking popups.

This should serve to run **Task**s on a specific environment, you could do async or sync **Task**s once you prepare your environment.

`do();`

### Tasks

You should connect multiple **Task**s to one **Window**, they belong to them! // 1:M

This is the final and ultimate awesomeness of Neck. Tasks should work-a-like, or be, Promises!
When you create a `Task` it should transport:
* How fast it has to be, or how much time it has to wait.
* What it should do.
* Which **Window** should it run into.

Then it should work as a Promise!

CLASSES
=======

Imagine how it would be if all Interfaces were extendable, well, they are! :)

In case you are creating your own module you are free to interact and use your own classes, how awesome is that?
To learn more you have to understand how `findhit-class` works.
  