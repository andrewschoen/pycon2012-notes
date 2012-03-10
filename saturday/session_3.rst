Testing and Django
==================

**Presenter:** Carl Meyer (@carljm)

**Track:** V

**Description:** 

    A deep dive into writing tests with Django, covering Django's custom test-suite-runner and the testing utilities in Django, what all they actually do, how you should and shouldn't use them (and some you shouldn't use at all!). Also, guidelines for writing good tests (with or without Django), and my least favorite things about testing in Django (and how I'd like to fix them).

    https://us.pycon.org/2012/schedule/presentation/412/

**Examples will be using the lastest django 1.4 rc**

Running the tests for django 1.4 takes 14 seconds, get's two errors.  Not very good.  The tests fail because the tests assume two databases.

**Not all apps are created equal**

It's a waste of time to run tests for apps you don't really care about.  

* Django insists that all your tests exists in a tests module
* Django's test discovery
    * Wastes times with apps I don't care about
    * Forces intermingling of tests and non-test code
    * It's easy to change
        * unittest2, nose
        * TEST_RUNNER settings

**Types of test**

* Unit tests
    * test one unit of code.  fast, focused
    * helps you structure your code better
* Integration test
    * tests that the whole integrated system works
    * tend to be slow
    * less useful failures
    * write fewer of these
* The database makes your tests slow
    * try to write tests that don't hit it at all
    * separate db-independent model-layer functionality from db-dependant functionality
    * mocking the database usually isn't worth it
    * don't run tests on a method that does a self.save().  remove the code you want to test into a different method and test that method

TransactionTestCase is slow.

**Don't use fixtures to test with, just say no**  

* fixtures are hard to maintain and update
* fixtures increase test interdependence
* fixtures are slow to load


**Alternatives to fixtures are Model Factories**

* Using a factory you can give just the data you care about
* Use a factory that can create a saved object or not

**Use factory_boy as an alternative**

* FactoryObject.create (saves) FactoryObject.build (does not save)
* Test data is lcoal to test code (explicit) using factories
* easy to maintain
* dont' create any data you don't need for that test
* works great even on large/complex test data sets

**Imposing no-DB discipline**

**Use Mock**

**Testing Views**

* Unit testing vies is hard
* Views have many collaborators / dependancies
* Write less view code is the solution
* Use RequestFactory
* Call the view callable directly
    * unit tests do not use the test client
* Set up dependancies manually (request.user, etc.)
* or just don't test views
    * I write less view code, and cover it via functional tests

**Integration testing views**

* use WebTest
* The markup matters
    * it can especially break forms
* django-webtest provides integration

**In-browser testing**

* using something like Selenium
* Is easier than you think
* inherit from LiveServerTestCase (takes care of running a server for you)

**What type of tests to write**

* Write system tests for your views
* Write Selenium tests for Ajax, other JS/server interactions
* Write unit tests for everything else
* Test each case (code branch) where it occurs
* One assert/action per test case method
* Should avoid multi-step tests

**Testing Documentation**

"We have always been at war with doctests"

* not entirely fair
* doctest are great
* you can turn code examples in Sphinx into tests.  DocFileSuite

@override_settings - check this out in 1.4

