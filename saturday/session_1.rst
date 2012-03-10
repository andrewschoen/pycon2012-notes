Why PyPy by example
===================

**Presenters:** Maciej Fijalkowski , Alex Gaynor , Armin Rigo

**Track:** II

**Description:**

    One of the goals of PyPy is to make existing Python code faster, however an even broader goal was to make it possible to write things in Python that previous would needed to be written in C or other low-level language. This talk will show examples of this, and describe how they represent the tremendous progress PyPy has made, and what it means for people looking to use PyPy.

    https://us.pycon.org/2012/schedule/presentation/244/

**We've failed to convince you all that we aren't crazy**

PyPy project has been around for 9 years.  Used to be slower than CPython, now is faster.

**If it's not faster, it's a bug.  How much is dependant on your program**

PyPy is fast, but is not a silver bullet.  Measure and complain so that PyPy can get better.

**Going to show some programs written in PyPy**

Showing an example of edge detection with a webcam in PyPy.  Then shows the example in Python.  Took over 10 seconds to get a single frame.

**Numerics in PyPy is pretty fast**

Next example is Tracebin

Tools for understanding what our programs are doing is very important.  Tracebin is a JIT viewer tool.

* Records every instruction the JIT compiled.
* For each line of python code
* Being able to expose this type of information to developers will be super powerful

**numpy**

They are working on implementing numpy.  Stay tuned, will be a few months until it's complete.

**transactional memory**

This was given 30 years ago at PascalCon

"solution": put everything in the GC-managed memory.  

the theoretical answer: horrible for performance (memory and speed)

**real programers can deal with explicit garbage collection**

**Now, 30 years later we don't even talk about garbage collection** instead we talk about how to use multiple cores.

mess with locks, reentrant locks, semaphorse, events...

in Python we have the GIL, but also the threading module

transactional memory promised to give multi-core usage

**using pypy has as reasearch on software transactional memory**

