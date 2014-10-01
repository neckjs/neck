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
* `Server`
* `Client`

Working example
===============

## Server side
* Server Initialization
  * Heads definition

* Server receives a Client
* Client class sets up an instance
* client instance gathers for available heads and their instances
  * Available heads and instances data are sent to client instance
* client instance receives a task data targeting a specific head instance

  * Task class sets up an instance
  * Head handles data from task instance and updates task state
  * task instance syncs data with client on state change
  