Practicing Continuous Deployment
================================

**Presenter:** David Cramer (@zeeg)

**Track:** I

**Description:**

    Practice iterative development like the pros. Release sooner, faster, and more often.

    https://us.pycon.org/2012/schedule/presentation/12/

**Definition**

Shipping new code as soon as it's ready

When is it ready?
+++++++++++++++++

* Review by peers
* Passes automated tests
    * none of this works without testing
* Some level of QA

**Focus on stability and integration**

**Workflow**

Commit > review > integration (repeat if fails) > deploy > reporting (if bad, rollback)

The Good
+++++++++

* Develop features incrementally
* release frequently
* smallers does of QA

The Bad
+++++++

* Culture Shock
    * can be very hard to implement
    * this is a mindset
* Stability depends on test coverage
* Initial time investment

**Keep your development simple**

Development
+++++++++++

* Automate testing of complicated processes and architecture
* Simple can be better than complete
    * especially locally
* Packaging your app is a must
    * puppet, chef, buildout, fabric, etc.

Different environments can be setup a bit differently.

**Bootstrapping local**

* simplify local setup
    * git clone, then run a command to take care of everything
    * then spin up the services (django, flask, etc)
* Need to test dependancies? 
    * virtualbox + vagrant up
    * makes it easy for the developer to make a production like environment locally

**Progressive Rollout**

**Gargoyle**
https://www.github.com/disqus/gargoyle

Early adopters are free QA - use them.

All commits must go through code review.  Disqus uses phabricator.  phabricator.org

**Integration Requirements**

* Developers must know they broke something
* Support proper reporting
    * jenkins does a ton of this stuff for you
* Painless setup

**Shortcomings**

* False positives
* Test coverage
* Feedback delay

**Speeding up tests**

* Write true unit tests
* Mock external services (lots of love for Mock today)
* Distributed and parallel testing

**Meaningful Metrics**

* Rate of traffic (not just hits)
    * can find bugs this way
    * Sentry, graphite
* Response time (database, web)
* Twitter activity can let you know if your site is down

**Getting Started**

* Package your app
* Value code review
* Ease deployment; fast rollbacks
* Setup automated tests
* Gather some easy metrics

**Going further**

* Build an immune system
* Adjust to your culture
    * there is no "right way"
* SOA == great success



