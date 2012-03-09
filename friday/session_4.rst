Code Generation in Python: Dismantling Jinja
============================================

**Presenter:** Armin Ronacher

**Track:** III

**Description:**

    For many DSLs such as templating languages it's important to use code generation to achieve acceptable performance in Python. The current version of Jinja went through many different iterations to end up where it is currently. This talk walks through the design of Jinja2's compiler infrastructure and why it works the way it works and how one can use newer Python features for better results.

    https://us.pycon.org/2012/schedule/presentation/246/
    
bit.ly/codegeneration for feedback

Why Code Generation?
++++++++++++++++++++

* Why is eval evil?
    * Security & Performance
* Can be avoided if done properly
* Possible security issues
    * Code Injection
    * Namespace pollution
* Performance
    * no bytecode
    * code makes code that code runs
* use responsibly

Eval 101
++++++++

* compile an arbitrary string into code
* you get a code object back
* must exec code in a namespace
* in Python 2.6+ you can use ast.  import ast
* Need to specify line numbers and columns on every note
    * use ast.fix_missing_locations
* don't pass strings directly to eval
    * can keep the code object around

Template engine architecture (Jinja)
++++++++++++++++++++++++++++++++++++

* 2nd iteration of jinja
* generate python code
* python semantics
* different scoping

How it works
------------

* Lexer > Parser > identier analyzer > code generator

Complexities
------------

* Different scoping
* WSGI & Generating
* Debug-ability
* Restricted Environments

How does it work?
+++++++++++++++++

* art of code generation.  low level vs high level
* ast was introduced after jinja was created
* high level would be using ast
* low level is bytecode
* biggest problems with bytecode is that it's undocumented and implemention specific
    * doesn't work on GAE
* ast is more limited, but easier to debug
* as of python 2.7 you can not segfault the interpreter with ast

Jinja is fast because it operates on the fast aspects of the python virtual machine. Code run at the global scope is slower.  Local scope is much faster.

Semantics
+++++++++

* jinja tracks every identifier 
* context in jinja is a data source
* context in django is a data store
* impossible in jinja to have a function that modifies context

