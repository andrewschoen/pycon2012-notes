RESTful APIs With Tastypie
==========================

**Presenter:** Daniel Lindsley 

**Track:** V 

**Description:**

   Providing full-featured REST APIs is an increasingly popular request. Tastypie allows you to easily implement a customizable REST API for your Python or Django applications.


    https://us.pycon.org/2012/schedule/presentation/61/

How I learned to stop worrying and love JSON.

A REST framework for Django.  Provides a web based API off of django.

* Designed for extension
* Supports both Model and non-Model data

Philosophy
++++++++++

* Make good use of HTTP
    * Was written with servers in mind
* Tries to be "of the internet" & use the REST methods/status codes properly
* Graceful degradation - your API should be backwards compatible
* Flexible serialization - not everybody wants JSON
    * Actually flexible everything.  Customizability is a core feature
* Data can round-trip
    * Anything you can GET, you should be able to POST/PUT
* Reasonable defaults
    * But easy to extend
* URIs everywhere!

**HATEOAS - Hypermedia as teh engine of teh application state**

* the user shouldn't have to know anything in advance
* All about explore-ability
* deep linking

What about Tastypie
+++++++++++++++++++

* Build ontop of Django - is a third party app and should play nicely
* GET/POST/PUT/DELETE/PATCH 
* Any datasource (not just models)
* designed to be extended
* Supports a wide variety of serialization formats
    * json, xml, yaml, bplist
* Well tested (80% coverage) and documented

**The setup**

``pip install django-tastypie``

* once installed just add to isntalled apps and syncdb

Auth API
++++++++

* code goes in our apps, not Django
* Don't fork Django!!
* make an api directory, make a resources.py in it with __init__.py
* Set up a tastypie Resource for User
* Next, set up URLConf importing the Resource urls
* Pull up the url in a browser, you're done
    * you get lists, specific users, the user schema "/schema" and get multiple users with "/multiple"
* needs lxml, pyaml for the other formats
* pagination by default
* everyone has full read-only GET access
* To exclude fields use the exclude attr on your Resource to pass a list of excluded fields
* To add authentication, use the authentication attr
* There is a filtering meta option as well
    * filter useing a querystring

**Authorization**

* Not who you are, but can you do that
* tastypie.authorization - in class Meta add in the authorization attr
* tastypie.cache import SimpleCache - using the attr cache in class Meta for the Resource
* throttling works the same as well

Extensibility
+++++++++++++

* goal of the project was the give API developers lots of tools
* classes make extending behavior trivial
* composition > inheritance is the reason for the many classes in tastypie
* hooks, hooks, hooks
* tries to use reasonable defaults
* serialization, authorization, authentication, pagination, caching
* Resource has many methods, override or extend to your needs
* Can specify what formats are available by using the serializer attr in Meta

**HTML Serialization**

* can write a custom TemplateSerializer to output in HTML, override to_html()
* to read the data back override from_html()
* hook it up by using serializer attr in class Meta on Resource

Fields
++++++

* maybe you don't want to show your database schema, use fields for this
* use ModelResource and can define fields just like a ModelForm
* class Meta needs a queryset attr.  Use exclude just like a ModelForm as well
* you can control how data gets prepared (dehydrate) or accepted from the user (hydrate)
* Can provide methods on your resource for non-simple things
* dehydrate and hydrate work just like clean methods on ModelForms dehydrate_field_name - hydrate_field_name
* ModelResource uses introspection to find the fields for you

Caching
+++++++

* caching is very simple.  you should be using varnish

The talk got cut short, but was awesome.  Would have like to have seen the rest of it.

