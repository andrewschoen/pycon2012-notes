Introduction to Metaclasses
===========================

**Presenter:** Luke Sneeringer

**Track:** IV

**Description:**

    Python's metaclasses grant the Python OOP ecosystem all the power of more complex object inheritance systems in other languages, while retaining for most uses the simplicity of the straightforward class structures most developers learn when being introduced to object-oriented programming. This talk is an explanation of metaclasses: first, what they are, and second, how to use them.

    https://us.pycon.org/2012/schedule/presentation/64/

* Metaclasses can be a big scary word
* Typically newcomers are told to stay away from metaclasses
* Some truth to this, but not completely
* This talk is an attempt to teach people about metaclasses who don't understand them and make them understand at a basic level
* When to use them and why

Terminology
+++++++++++

Know the difference between class and instances.  For this talk object and instance is interchangeable.

* Classes are objects too
* They are first class objects ( can be passed around )
* you can pass callables around
* The ability to pass callables is the key to reusable code

Instances
+++++++++

* Class variables are assigned as references back to the class
* Any method on the class are bound to the instance
    * This makes ``self`` work
* Instances are constructed at runtime from the classes
* Classes work the same way (they are instances)
* Objects are instances of their class; classes are instances of their metaclass

**Terminology**

* Meta is a greek prefix meaning "after"
* Now we use the prefix to refer to a special kind of self-reference
* Therefore metaclasses are classes about classes
* Metaclasses provide code for the creation and execution of classes
* instance are to classes are classes are to metaclasses

The Details
+++++++++++

* When making a class inherit from ``object``
* Metaclasses inherit from ``type``
* Python has multi-inheritance
* First calls __new__ and then __init__

Writing Metaclasses
+++++++++++++++++++

* ``type`` is the true top of the chain
* type(type) is type
* To create a metaclass inherit from type
* Use __metaclass__ in python 2
* Most straightforward case is to override __new__ or __init__
* These run when the class is created, not the instances
* This is how Django models work

When Metaclasses
++++++++++++++++

* If you're writing an API or interface of classes or subclasses
* They are useful for making other classes more straightforward
* Sometimes metclasses aren't the right answer
* Class factory functions are more expensive than metaclasses
    * But still often useful if you don't know something until execution

Practicing Wisdom
+++++++++++++++++

* Some justification for running away from metaclasses
* Don't go meta if you don't need to - there is complexity added
* But use it if you need to
* The key advantage is that they can me be much clearer and cleaning than the alternatives
* Used inproperly it's the exact opposite
* If you're not sure when to use them, ask or research
* The problem defines the solution, not your skill set
* If it is the right solution, make sure you know them well