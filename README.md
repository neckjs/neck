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

```bash
  npm install --save neck;
  
  # start Neck server
  neck serve;
```

Usage case on mocha test example:
```js
  var Neck = require('neck'),
      head = Neck.head('ios'); // picks up an ios head ( iPad, iPhone, or other iDevice like connected to Neck )
  
  head.open( 'https://www.findhit.com/' )
    .then(function () {
      return head.navigate( '/auth/login' );
    })
    .then(function () {
      expect( head.document.path ).to.be.equal( '/auth/login' );
    });
```

Developing Stage
----------------
Developing our first pre-release

Ownership
---------

neckjs is an open-source project started and owned by [findhit](https://www.findhit.com/)
