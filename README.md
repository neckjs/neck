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
  var Util = require('findhit-util'),
      Neck = require('neck');

  describe( "my browser tests", function () {

    before( function ( done ) {

      // Get all available heads
      Neck.getHeads()
        .then(function ( heads ) {

          // We got browser, but lets check
          if ( Util.hasnt( 'Browser', heads ) ) {
            throw new Error("No browser head?");
          }

          return heads.Browser;
        })
        .then(function ( Browser ) {
        
          // We just want to run into an iPhone, so lets search for an iPhone head
          return Browser.searchInstance( 'iPhone' )
        
        })
        .then(function ( browserInstances ) {
         
          if( ! browserInstances || ! browserInstances.length ) {
            throw new Error("there aren't iPhone instances available :(");
          }

          return Util.Array( browserInstances ).get( 'random' ); // It could be index, 'first' or 'last'
        })
        .then(function ( browser ) {
        
          return browser.open( 'https://www.findhit.com/' );
        
        })
        .then(function ( browser ) {
        
          expect( browser.title ).to.be.equal( 'findhit' );

          return browser.eval( 'injectSomeVariable = "YOLO Fag, code faster";' );
        
        })
        .then(function ( browser ) {
        
          return browser.input('#login', 'username');
        
        })
        .then(function ( browser ) {
        
          return browser.input('#pass', 'my precious');
        
        })
        .then(function ( browser ) {
        
          return browser.submit('#login_form');
        
        })
        .then(function ( browser ) {
        
          expect( browser.title ).to.be.equal( 'My Network' );
        
        })
        .done( done );

    });

```

Developing Stage
----------------
Developing our first pre-release

Ownership
---------

neckjs is an open-source project started and owned by [findhit](https://www.findhit.com/)
