Django Form Processing Deep Dive
================================

**Presenter:** Nathan Yergler (@nyergler)

**Track:** V

**Description:**

    Django Form processing often takes a back seat to flashier, more visible parts of the framework. But Django forms, fully leveraged, can help developers be more productive and write more cohesive code. This talk will dive deep into the stock Django forms package, as well as discuss a strategy for abstracting validation for forms, and the use of unit and integration tests with forms.

    https://us.pycon.org/2012/schedule/presentation/420/

Eventbrite uses django forms quite extensively.

**The problem with a deep dive is that sometimes you hit your head at the bottom**

Form Basics
+++++++++++

* Wasn't obvious at first where they fit in the stack of django
* A form converts inmport into Python objects
    * Can be used even when you don't have HTML involved at all
* Forms are composed of fields, which have a widget
* Can instantiate a form with or without data
* data does not have to be request.POST, can be json, etc.
* Two ways to access a field
    * fields dictionary form.fields['name'] returns Field object
    * form['name'] returns a BoundField
* Can give forms initial data
* form['name'].value gives you the current value

Validation
++++++++++

* Only bound forms can be validated
* calling form.is_valid() starts validation
* Three phases for fields: To Python, Validation and Cleaning
* If validation raises an error, cleaning is skipped
* Django provides some basic validation rules (URL, email, max / min length, etc.)
* To clean a specific field clean_fieldname()
    * Must returned the cleaned_data
* .clean() performs cross-field validation
    * Must return cleaned_data dictionary
* inital != default data
* Track changes
    * form.has_changed()
    * formchanged_fields gives you any fields that have changed
    * show_hidden_initial=True on a form field.  will render a hidden input with the initial value

Testing
+++++++

* Testing strategies
    * initial states
    * field validation
    * final state of cleaned_data
* Unit Tests
    * Just open sourced a library called rebar
        * flattens form data into a dict

Rendering Forms
+++++++++++++++

* Class based views are nice for using forms
* Three output modes for forms
    * .as_p(), .as_ul(), .as_table()
* Can iterate over the form if you want to control form output
* Customize rendering
    * can override widgets when defining a field
    * can give the field attrs like {'class': 'custom'}
    * can also specify form-wide CSS
* Build in validators have default error messages
    * error_messages on the field let's you customize these messages
* ValidationErrors are wrapped in a class
    * by default ErrorList outputs as a UL
    * specify the error_class kwarg when consructing form to override
        * extend ErrorList from django.forms.util
* Multiple forms
    * can add the arg ``prefix`` when instantiating form to give different prefixes to each form on page

Form Sets give you a way to use multiple forms of the same type on the page.  They have the same validation structure.  Overriding clean works the same way on formsets.

localize=True can localize a form field

http://yergler.net/2012/pycon-forms