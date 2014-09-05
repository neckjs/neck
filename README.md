neck.js
=======

neckjs is a multi-browser test suite, that fills the gap between headless and head-only browser-driven tests.

How does it work?
-----------------

We have:
* Heads - Browsers that could run tests into.
* Neck - neck.js :)
* Body - Things you want to test.
* Legs and arms - Test units, some cases are so random that causes kicks and punches into heads. Developers call them **bugs**.

Instalation
-----------

```bash
  npm install --save neck;
  
  # start neck.js server
  neck serve;
```

Usage case on mocha test example:
```js
  var neck = require('js'),
      head = neck.head('ios'); // picks up an ios head ( iPad, iPhone, or other iDevice like connected to neck )
  
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
