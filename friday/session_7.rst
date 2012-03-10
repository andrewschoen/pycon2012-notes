Python Metaprogramming for Mad Scientists and Evil Geniuses
===========================================================

**Presenter:** Walker Hale

**Track:** IV

**Description:**

    This talk covers the power and metaprogramming features of Python that cater to mad scientists and evil geniuses. This will also be of interest to others who just want to use of Python in a more power (hungry) way. The core concept is that you can synthesize functions, classes and modules without a direct correspondence to source code. You can also mutate third-party objects and apps.

    https://us.pycon.org/2012/schedule/presentation/380/

Python is an ideal language for both Mad Scientists and Evil Geniuses.

Mad Scientist:  creating new things because it's cool

Evil Genius: has a goal and will get there no matter who gets in their way

Mad Scientist Goal:

* Create new living code from scraps of other open source code
* Mutate third party code to suit our needs

A class is just a dictionary wearing a class.  Python is just dictionaires all the way down.

type's job is to construct other classes.  When initiating a class Python is basically just handing you an empty dictionary.  

A module is even less than a class.  

**Applications**

* Integrating user-specific formulae
* Domain-specific languages
* GUI Frameworks
* Object-Relational Mappers
* Monkey patching

**Monkey Patching**

* functions, classes and modules are just objects in memory
* and they can be modified
* Very similar to Aspect-Oriented Programming
* Patching third-party objects is more robust than patching third-party code
    * altering the code on the fly

**Monkey Patching Modules**

* Modify an existing module
* Synthesize a replacement

With either approach you must do this before other code imports the module.  Modify the code an then insert that back into sys.modules

**Monkey Patching a Class**

* use new.instancemethod to add a method to a class
* operates at the class level.
* can monkey patch a specific instance of a class by using new.instancemethod as well

If sitecustomize.py exists anywhere in your code python will import that very early.  Can be used to monkey patch executables

When to do this:

* patch a module written in C
* Patch just a few functions you think you need.
* Create an object that actls like a module but really synthesizes teh functions it needs by implementing a custom __getattr__

**Limitations**

* Patching third-party code can confuse co-workers
    * Do it seldom
    * Do it publicly
* Updates to third-party code can still break a monkey-patch
* You can't monkey patch most code that rsides below Python(C, Java) but you can synthesize a replacement

**For the evil geniuses**

* Networks code - ww.metasploit.com
* Selenium is a man-in-the-middle attack
* Speed up with things like Cython, ctypes, pypy

We live in a golden age where reason and science can triumph over convention and superstition.

**Todo:**

* Revel in your power
* Laugh your most diabolical laugh
* Bend code to your will

