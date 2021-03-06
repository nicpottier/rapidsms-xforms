rapidsms-xforms
===============

The RapidSMS xforms application provides an interactive web based form builder.  Created forms support data being submitted to them via freehand formatted SMS, standard XForm HTTP posts or structured SMS.  Applications can choose to use xforms to quickly prototype systems, or even use them as their primary interface, using Django signals to perform more complicated logic on new submissions.

**Distinct features**

- Interactive Web UI to build Forms
- Flexible constraint architecture to allow for validation of inputs with customized error messaging
- Ability to submit forms either via hand entered SMS's or via HTTP Posts in XForm format
- Display of submitted forms and editing of values by admin
- Signal architecture to allow you to plug in your own handler for submitted forms
- Integration with ODK Collect, an Android XForms client

The full documentation can be found at:
  http://nyaruka.github.com/rapidsms-xforms

The official source code repository is:
  http://www.github.com/nyaruka/rapidsms-xforms

A little video showing this app in use:
  http://www.youtube.com/watch?v=PyjEruT5uoU

Build by Nyaruka Ltd under contract of UNICEF:
  http://www.nyaruka.com

Installation
===========================================

You can install the latest version of the rapidsms-xforms library straight from the cheese shop::

   % pip install rapidsms-xforms

Then to use xforms, edit your ``settings.py`` to add ``rapidsms_xforms`` and ``uni_form``::

  INSTALLED_APPS = ( "rapidsms",
   		       .. other apps ..
  		     "uni_form",
  		     "rapidsms_xforms" )

You will probably also want to add XForms as one of the main RapidSMS tabs::

  TABS = [
    ('rapidsms.views.dashboard', 'Dashboard'),	
        .. other tabs ..
    ('rapidsms_xforms.views.xforms', 'XForms'),
  ]

Finally sync your database with::

    % python manage.py syncdb

Once you restart RapidSMS a new tab will created letting you create, manage and view forms and their submissions.

Getting started
---------------

Once installed, click on the XForms tab.  Here you can create a new form.  A form represents a new SMS (or XForm) endpoint, allowing users enter data into the system according to the fields you have defined.  Try creating a new form, naving it ``survey`` and add one integer field named ``age`` and a string field named ``name``.

Once saved you can submit SMS messages to the system in the forms::

     survey +age 10 +name emily
     survey + age 30   +name monty python
     survey +name eric +age 15.4

You can view submitted reports after they come in, and edit them as you like.

Now try experimenting with adding restrictions to the fields, whether they are required, their min and max values etc..  You'll find you can easily customize the error messages as they come in.

You can also submit surveys using an XForms client, like ODK Collect.  The XForms application adds the appropriate endpoints to both discover available forms, download them to the device, and submit them to the server.  This makes RapidSMS a full XForms endpoint for simple forms, giving you the choice as to whether to submit via a rich XForms client or via SMS.
