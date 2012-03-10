Using fabric to standardize the development process
===================================================

**Presenter:** Ricardo Kirkner

**Track:** IV

**Description:**

    By ensuring consistency and repeatability in setting up the development environments of a team of developers, errors can be avoided (by automating repetitive tasks). It also helps by lowering the entry barrier for new developers, and letting existing developers focus on development tasks without having to worry about infrastructure or process issues.

    https://us.pycon.org/2012/schedule/presentation/25/

Currently employeed at Cononical

What is Fabric?
+++++++++++++++

* fabric is a python library for streamling the use of SSH for application deployment and system tasks
* use a run command from fabric.api to run commands on remote servers
    * use fab from the command line and run method written in fabfile.py

Why Fabric?
+++++++++++

* choose fabric for 1) lazyness - already in Python a language he knows
* and 2) legacy - was being used already in legacy applications

How to use Fabric
+++++++++++++++++

* you can do many things with fabric.  anything you can do on the command line you can do in fabric
* Bootstrap
    * do sanity checks
    * setup virtualenv
    * install dependancies
    * setup configuration
    * will help other developers to set up the project locally and on production systems
* local() runs local and run() is on a remote machine - set by your host
* Database
    * setup database
    * start/stop database
    * create/drop database
    * sync database
    * migrate database

*Continous Integration
    * fabric can be used during CI.
    * works with Jenkins
* Deployment
    * fabric is typically used for deployment tasks as well.
