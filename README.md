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

### Step 1: Start a Neck server

```bash
  npm install --save neck;
  
  # start Neck server
  neck serve --port=5000;

  # Neck is now running on http://localhost:5000
```

### Step 2: Connect some devices into http://neck.server.ip.address:5000

You can connect browsers on tablets, phones, computers, virtual machines, etc.

### Step 3: Run tests!!!

This is just a POC wrote to show how easy is to target a platform or app.

```js
  var Util = require( 'findhit-util' ),
      Neck = require( 'neck' );

  describe( "my browser tests", function () {

    before( function ( done ) {
      var self = this;

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

          self.Browser = Browser;

          return Browser.getAll();

        })
        .then(function ( browsers ) {
          self.browsers = browsers;
        })
        .done( done );

    });

    describe( 'iPhone', function () {

      before( function ( done ) {
        var self = this;

        this.Browser.getBy({

          // All variables above are optional, if none is specified, it will result same as `.getAll()`

          platform: 'iOS', // 'Windows', 'Mac OS', 'Android', ..., undefined
          device: 'iPhone', // 'Samsung', 'HTC', ..., undefined
          engine: 'webkit', // 'gecko', ..., undefined
          app: 'Chrome', // 'Firefox', 'Safari', ..., undefined

        })
          .then(function ( browsers ) {

            if( ! browsers || ! browsers.length ) {
              throw new Error("there aren't iPhone instances available :(");
            }

            return Util.Array( browsers ).get( 'random' ); // It could be index, 'first' or 'last'
    
          })
          .then(function ( iPhone ) {

            this.iPhone = iPhone;

          })
          .done( done );

      });

      it( "login", function ( done ) {

        this.iPhone.open( 'https://www.findhit.com/' )
          .then(function ( tab ) {
          
            expect( tab.title ).to.be.equal( 'findhit' );

            return tab.eval( 'injectSomeVariable = "YOLO Fag, code faster";' );
          
          })
          .then(function ( tab ) {
          
            return tab.input('#login', 'username');
          
          })
          .then(function ( tab ) {
          
            return tab.input('#pass', 'my precious');
          
          })
          .then(function ( tab ) {
          
            return tab.submit('#login_form');
          
          })
          .then(function ( tab ) {
          
            expect( tab.title ).to.be.equal( 'My Network' );
          
          })
          .done( done );

      });

      it( "login", function ( done ) {

        this.iPhone.open( 'https://www.findhit.com/about' )
          .then(function ( tab ) {

            // Another test, just to POC

          })
          .done( done );

      });


    });

  });

```

Developing Stage
----------------
Developing our first pre-release

Ownership
---------

neckjs is an open-source project started and owned by [findhit](https://www.findhit.com/)
