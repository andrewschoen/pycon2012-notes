Keynote: David Beazley
======================

Let's talk about something diabolical.  The best part of PyCon is learning about new stuff.

We're going to talk about PyPy.  PyPy is python implemented in Python.  Faster than normal python by some types of magic.

* Just in time compilation
* Translation to C

Thinking about Tinkering
++++++++++++++++++++++++

Tinkering is something that is very important.  Using a VW bug has an example of different types of Python.

* Started with Python because they could hack on it
* Easy to work with and change

**Is PyPy something you can tinker with?**

**A Confession**

* PyPy scares him.  Because of complexity.
* Started an experiment to answer that question.
    * Use nothing but the source

**Tinkering with PyPy != Using PyPy**

* Start by downloading the source. pypy.org.  build it yourself
* type python py.py in the bin directory of source to run it
* To get the "real" version you have to translate it.
    * Go to /translator/goal/ - run translate with some options
    * Builds pypy from source

**Building PyPy**

* Takes a few hours to build
* It takes > 4GB of ram to build
* Translation of PyPy to C ~10.5 million lines of C
* It might break your C compiler

**This is Amazing**

* Implemented in a subset of python called RPython
    * it is a restricted subset of Python
    * "RPython is everything that our translation toolchain can accept"
    * Documentation are on readthedocs.org
* 454 directories in source
* ~1.2 million lines

**Running a live example of RPython**

* Had a def target to set the entry point in the code
* Must translate the script to run it.  Using translate.py from PyPy
    * creates a C file
* Trying a fibonachi sequence as an example
    * takes about 8 seconds to run in Python
    * Now runs the file through the translate.py
    * .17 seconds to run after translation to C
    * a raw C example is slower than the rpython (pypy) version

**Limitations of RPython**

* Do not get the dynamic features of Python
* Must have consistent types

* Can call external functions in C
* Uses Type inference
    * Looks at your code and applies types across it
    * This is what's happening in the build process

**Understnading Translation**

* Will blow your mind
* Insight: Python already parsed the code.
    * doesn't even operate off source code
    * operates entirely of of code objects
    * translater code looks at the bytecode
* CPython has a bytecode interpreter
* PyPy does this as well, the bytecode interpreter is written in Python
* Bytecode interpreter is modular
* PyPy compiles itself using itself
* Runs the bytecode of the object "in the abstract"
* The full details are "hairy"

**Problems**

* As an outsider coming to PyPy.  Everything is Python, makes it difficult to sort his head around it.
* Two different languages co-exist (Python, RPython)

**What if PHP has the same syntax as HTML, that's PyPy**

Uses docstrings to tell the difference between RPython and Python in the source

**Looking at some RPython**

* opens ll_thread.py
* specifies C header files, calling out to C
* Lots of decorator usage

**A realization, he still doesn't know how it works**

**PyPy: 1, Dave: 0**

**Doesn't know CPython either, but he does know how to use the tools that make up CPython**

PyPy has a different set of tools.  Need to learn about the tools before you can understand how PyPy works.  It's a different vocabulary.

**Figuring out how PyPY works is left as an exercise of us**

* He loves breaking GILS
* Showing an example of Ruby, Ruby is 3600x slower than Python

**Still not sure if you can tinker with PyPy** but you should try.

