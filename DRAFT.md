STRUCTURE IDEAS
===============

Server should serve a double side API
* CLI API - which should receive tasks and drive them to an head
* HEAD API - which should receive tasks, process them and return the results

### Tasks? Ok!
Since we have tasks, well, we should have tasks too.

### Heads
Head seems to be something very ambiguous, so i admit that we can have multiple types of HEADS.
With this, i'm not talking about Browser-detection but yes to platform running.
`neck-head-browser` should handle tasks-per-browser-type, then we should have later:
* `neck-head-android`
* `neck-head-ios`
* `neck-head-blackberry`
* and so on...

CLASSES
=======

* `Task` - A kind of `Promise` that delivers an **action** to an `Head`, and returns **result** to `Cli` **request**
* `Head`
  * `Browser` ( should detect and diverge `platform` and `browserName` )
  * `Android` ( maybe to test default WebView? )
  * `iOS` ( same as `Android` )
* `Cli` - I don't have sure how to structure this yet, just some ideas, let me sleep with them...
  * `Request`
  * `Response`

