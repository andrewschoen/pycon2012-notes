Keynote: Guido Van Rossum
=========================

* Thank you PSF!
* There are alot of Trolls in the real world
* What is a Troll?
    * a question that isn't meant as a question, but to heckle
* What have trolls said about python?
    * used to be most common "you gotta be kidding about the whitespace"
    * trolls have evolved now
    * "Python Sucks. Ruby Rules"
        * apples and oranges
        * this is mostly all bullshit
        * python, ruby, perl are mostly the same language at 10k feet
        * don't get pulled into language comparissons
        * be proud of your language, but don't diss other languages
    * don't worry, be happy - there are tons of people here
    * "When will you admit Python 3 is a mistake?"
        * unicode literals are back in Python 3
        * Python 3 is doing fine
        * numpy is being ported to Python 3
    * "Since PyPy is so much faster than CPython, why not abandon CPython"
        * asks people to raise their hands who use PyPy in production - almost nobody
        * now CPython - everybody
        * guido sees many possibilities with PyPy
    * Dynamic Typing
        * "I don't want my app to fail witn an AttributeError after running for 4 hours"
        * type checking in compilers is actually very weak
        * don't trust your compiler to find all your errors for you
            * if you do, you haven't done software engineering that long
        * the only way to fix this is to test, think about it, audit it, hire smart people.  especially smart people who know they can still get smarter.  work with a team with different capabilities.
        * dynamic typing is incredibly important and useful in many ways
        * dynamic languages have become so important that the static community is designing new languages with dynamic features
    * Speed
        * "Python is to slow for real work"
        * "Why don't you write a compiler?"
        * Anytime he writes something in Python, it's fast enough
        * In languages that are fast, the development is too slow
    * The GIL
        * "Python is useless because of the GIL"
        * "You can't use iton a multi-core computer"
    * Async I/O and Concurrency
        * Likes gevent, but is hesitant to add it to the stdlib
        * guido is not a callback fan
    * The Browser
        * why don't you put Python in the browser
        * because nobody would want to use it
        * introducting a new language to replace javascript is a huge political problem
    * Mobile
        * "You work for Google.  Why didn't you make Python the language of choice for Android"
        * There are enough tools out there that people can use to make this happen
    * Functional Programming
        * "Why did you kill reduce()"
        * "Please fix lambda"
        * "Please add more functional features"
        * Python is not a functional language for a very specific reason
            * it's very pragmatic
        * What you can do is learn a functional language, get excited about the functional features.  And when you are writing python and when you see an oppurtunity to write in a functional style, use it.
        * Guido likes functional programming as a challenge and a fresh idea
    * The standard Library
        * "Why hasn't <my favorite package> been added to teh standard library yet?"
        * You're better off.  Once it's in stdlib you're stuck with the API you have because of backwards compatability.  You're stuck on a release cycle
    * Garbage Collection
        * Python has gotten a long way with reference counting
        * Python does have garbage collection
    * Language Evolution
        * "Stop changing the language already!"
        * will never be solved for everybody
        * as your userbase grows you become more conservative with changes 