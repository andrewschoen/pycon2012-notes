Fake It Til You Make It: Unit Testing Patterns With Mocks and Fakes
===================================================================

**Presenter:** Brian K. Jones

**Track:** I

**Description:** 

    In this talk, aimed at intermediate Pythonistas, we'll have a look at some common, simple patterns in code, and the testing patterns that go with them. We'll also discover what makes some code more testable than others, and how mocks and fakes can help isolate the code to be tested (and why you want to do that). Finally, we'll touch on some tools to help make writing and running tests easier.

    https://us.pycon.org/2012/schedule/presentation/336/
   
github.com/bkjones
jonesy on freenode (join #python-testing)

What's Covered
+++++++++++++++

* Definitions
* Patterns
* Tools

unittest module is not going to be covered. 

What is a unit test?
++++++++++++++++++++

A unit test is a test that does not require larger parts of the system to run.

* unit tests are granular
* unit tests are isolated
* unit tests are localized
* not a unit test if something outside of the code you care about has to be included for it to pass
    * if so, it's an intergration test

Coverage is a loaded term.  Generically referred to as "code coverage".  Cover all the conditions around the execution of the code, not lines of code.

**coverage.py**

* Integrates well with nosetest
* super easy to use

**Nose**

Nose is a great discovery tool.  Running nosetests --with-coverage will use coverage.py.  Nice HTML reporting and integrates well with Jenkins.

Why Unit Tests?
+++++++++++++++

* They're fast
* They're simple
* They provide greater localization of problems than other types of tests often can.
* running unit tests create the entire execution environment.

Unit Tests Aren't Enough

* They're one component of the complete testing regime.  They don't test how things work together.

Mock
++++

**Mock is cool.  Use it.**

http://mock.readthedocs.org/en/latest/index.html

Mock handles harder stuff

* make assertions about what methods on a mock were called, with arguments
* puts objects back the way it found them after a test
* tons more, check out mock
* makes code more testable

Low-hanging Fruit
+++++++++++++++++

Making unit tests easier

* limit the scope of responsibility
    * will make code flexible and easier to unit test
* create local wrappers
    * that talk to external resources
    * better encapsulation, switching libraries without chaning api
* deduplicate the code

Well factored code should be easy to test.  

Yes! You do need to test!

**Unit tests can be a great form of documentation**

Follow the one test, one assertion rule.  Overall unit test will be better off.  Care for your unit tests like you do your production code.

Tox is cool, check it out later.  Testing across multiple python versions.









