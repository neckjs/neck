# Neck

A multi-browser test tool that fills the gap between headless and head-only browser-driven tests.

## How does it work?


We have:
* Heads - Browsers that could run tests into.
* Neck - Neck :)
* Body - Things you want to test.
* Legs and arms - Test units, some cases are so random that causes kicks and punches into heads. Developers call them **bugs**.

## Instalation

* Step 1: Start a Neck server:

```bash
	npm install -g neck;

	# start Neck server
	neck --port=5000;

	# Neck is now running on http://localhost:5000
```

You could optionaly start a server by `require( 'neck' ).Server`

* Step 2: Connect some devices:

Access from a browser to: http://neck.server.ip.address:5000

You can connect browsers running on tablets, phones, computers, virtual machines, etc.
We expect to be compatible with all of them (even IE 6, we hope!!)

* Step 3: Run tests:

See [API](./API.md) and [EXAMPLES](./EXAMPLES.md) for further implement information.

## Developing Stage

Developing our first pre-release

## Developing plugins for Neck

Neck uses [findhit-hotplug](https://github.com/findhit/findhit-hotplug) as Plugin Management System.
If you want to develop an Head for Neck check please how we made `neck-head-browser`.

Feel free to provide some Documentation for this! :)


## INTERFACE

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

### They are all based on `findhit-class`!!1

Imagine how it would be if all Interfaces were extendable, well, they are! :)

In case you are creating your own module you are free to interact and use your own classes, how awesome is that?
To learn more you have to understand how [findhit-class](/findhit/findhit-class) works.

## Ownership

**Neck** is an open-source project started and owned by **Junglecloud**, the company that owns [findhit](https://www.findhit.com/).
Give a peek at [findhit's github page](http://findhit.github.io/) for more projects.
