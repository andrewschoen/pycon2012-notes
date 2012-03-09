Throwing Together Distributed Services With Gevent
==================================================

**Presenter:** Jeff Lindsay (@progrium)

**Track:** V

**Description:**

    In this talk we learn how to throw together a distributed system using gevent and a simple framework called gservice. We'll go from nothing to a distributed messaging system ready for production deployment based on experiences building scalable, distributed systems at Twilio.

    https://us.pycon.org/2012/schedule/presentation/288/

Jeff works at twilio. twilio uses a service oriented architecture. Twilio as a high level service is made up of many subservices - sms, voice, client.  Each made up of other services.  Mostly written in tornado, gevent.  Going to use a framework called Ginko.

* services are nested modules than can start, stop and reload
* going to build a scalable gateway around a self-organizing messaging system.
* first we'll build a simple number client
* next a pubsub service
* then combine both into a gateway service
* and finally make it all distributed

Number Server
-------------

* a basic gevent StreamServer
* for every connection generate a random number, sleep for 60 seconds
* configuration is a python file
* ginko has start / stop services
* start the number server in the background

Number Client
-------------

* spawns a greenlet relative to your service
* makes services self contained
* gets the numbers from the server and puts it in a queue

PUBSub
------

* uses httpstreamer
* subscription wraps a queue
* posts are publishes, gets are subscribes

MessageHub
----------

* hub is now responsible for managing subscriptions

If you're in a loop that doesn't use IO, run gevent.sleep(0) to make sure it yields

Code for the example is up here: https://github.com/progrium/ginkgotutorial

