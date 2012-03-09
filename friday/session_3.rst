Practical Machine Learning in Python
====================================

**Presenter:** Matt Spitz

**Track:** II

**Description:**

    There are a plethora of options when it comes to deciding how to add a machine learning component to your python application. In this talk, I'll discuss why python as a language is well-suited to solving these particular problems, the tradeoffs of different machine learning solutions for python applications, and some tricks you can use to get the most out of whatever package you decide to use.

    https://us.pycon.org/2012/schedule/presentation/119/


Why Python?
+++++++++++

* Python is great for data processing and analytics
* Versatile
* Also has Mature ML Packages

Terms
+++++

* Data points
    * feature sets and label
* Classification
    * training set

SluggerML
+++++++++

* baseball stats and machine learning
* feature sets represent game state for a plate appearance
    * day game, night game, at-bat, batter/pitcher
* using training sets and classifier predictions
* Gathering Data
    * retrosheet.org
    * sean lahman's baseball archive
* Coalescing
    * 1st pass, Lahman: create player database
    * 2nd pass, Retrosheet: track game state, join on player db
* Scrubbing
    * ensure consistency
* Training Set
    * regular season games from 1980 - 2011
* Selecting a Toolkit, tradeoffs
    * Speed
    * Transparency
    * Support
* High-Level Options for Toolkit
    * External bindings
    * Python implementations
    * DIY

Python Toolkits
+++++++++++++++

* Python Implementations
    * nltk
        * focus on NLP
    * mlpy
        * regression, classification, clustering
    * PyML
        * foscus on SVM
    * PyBrain
    * mdp-toolkit

Feature Selection
+++++++++++++++++

* Identifies predictive features
* uses scikit-learn
* Visualizing significance

Tips and Tricks
+++++++++++++++

* Persistent classifier internals
    * once trained, save and reuse
    * depends on implementation
* Using generators where possible
    * avoid keeping data in memory
* Multicore text processing