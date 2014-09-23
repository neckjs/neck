Neck
====

A multi-browser test tool that fills the gap between headless and head-only browser-driven tests.

How does it work?
-----------------

We have:
* Heads - Browsers that could run tests into.
* Neck - Neck :)
* Body - Things you want to test.
* Legs and arms - Test units, some cases are so random that causes kicks and punches into heads. Developers call them **bugs**.

Instalation
-----------

##### Step 1: Start a Neck server

```bash
	npm install --save neck;
	
	# start Neck server
	neck serve --port=5000;

	# Neck is now running on http://localhost:5000
```

##### Step 2: Connect some devices

Access from a browser to: http://neck.server.ip.address:5000

You can connect browsers running on tablets, phones, computers, virtual machines, etc.
We expect to be compatible with all of them (even IE 6, we hope!!)

##### Step 3: Run tests!

See [API](./API.md) and [EXAMPLES](./EXAMPLES.md) for further implement information.

Developing Stage
----------------

Developing our first pre-release

Ownership
---------

**Neck** is an open-source project started and owned by **Junglecloud**, the company that owns [findhit](https://www.findhit.com/).
Give a peek at [findhit's github page](http://findhit.github.io/) for more projects.
