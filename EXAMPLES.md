Examples
========

1. Mocha Examples
-----------------

### 1.1 Pick browser head instances and select a random on each test

```js
	var Neck = require( 'neck' );

	describe( "my browser tests", function () {

		before( function ( done ) {
			var self = this;

			// Get head-browser if available
			Neck.Heads.pick( 'browser' )
				.then(function ( Browser ) {

					self.Browser = Browser;

					// Get all Browser instances
					return Browser.all();

				})
				.then(function ( browsers ) {
					self.browsers = browsers;
				})
				.done( done );

		});

		// Now that we got All Browser instances, let's open a tab on a random to run tests

		it( "login", function ( done ) {

			browsers.random()
				.open( 'https://www.findhit.com/' )
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
				.then(function ( tab ) {

					// Until we get support from `findhit-promise` to
					// fire an event when a promise chain is ended, we must close tabs
					return tab.close();

				})
				.done( done );

		});

		it( "login", function ( done ) {

			// Another test, another tab

			browsers.random()
				.open( 'https://www.findhit.com/about' )
				.then(function ( tab ) {

					// Another test, just to POC

				})
				.then(function ( tab ) {

					// Until we get support from `findhit-promise` to
					// fire an event when a promise chain is ended, we must close tabs
					return tab.close();

				})
				.done( done );

		});


	});

```

### 1.2 Get filter Browser instances that match a device (iPhone on this case)

```js
	var Neck = require( 'neck' );

	describe( "my iPhone browser tests", function () {

		before( function ( done ) {
			var self = this;
			
			// Get head-browser if available
			Neck.Heads.pick( 'browser' )
				.then(function ( Browser ) {

					self.Browser = Browser;

					// Return all instances
					return Browser.pick({

						// All variables above are optional, if none is specified, it will result same as `.all()`

						device: 'iPhone', // 'Samsung', 'HTC', ..., undefined

						// platform: 'iOS', // 'Windows', 'Mac OS', 'Android', ..., undefined
						// engine: 'webkit', // 'gecko', ..., undefined
						// app: 'Chrome', // 'Firefox', 'Safari', ..., undefined

					});

				})
				.then(function ( browsers ) {

					if( ! browsers || ! browsers.length ) {
						throw new Error("there aren't iPhone instances available :(");
					}

					self.browsers = browsers;
				})
				.done( done );

		});

		// ... test units ...

	});

```
