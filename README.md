django-registration-withemail
=====================

This is a simple user-registration application for Django,
designed to make allowing user signups as painless as possible. It
requires a functional installation of Django 1.5 or newer, but has no
required dependencies.
django-registration-withemail is hugely inspired by the popular django-registration which 
is not yet compatible with django 1.5.

Installing
==========

To install django-registration-withemail, run on terminal: ::

    $ [sudo] pip install registration_withemail

	Add "registration_withemail" to your INSTALLED_APPS setting like this::

	INSTALLED_APPS = (
	  ...
	  'registration_withemail',
	)    

    Add AUTH_USER_MODEL = 'registration_withemail.EldonUser' to your settings.
	
	Run `python manage.py syncdb` to create the User model.



Required settings
=================

``ACCOUNT_ACTIVATION_DAYS``
    This is the number of days users will have to activate their
    accounts after registering. If a user does not activate within
    that period, the account will remain permanently inactive.

``ADD_TOS``
	Adds a term of service checkbox to the registration form

``ADD_RECAPTCHA``
	Adds recaptcha to the registration form. You must install django-recaptcha
	in order to use this setting. For further information about recaptcha
	see https://github.com/praekelt/django-recaptcha

Setting up URLs
=================

Include the registration_withemail URLconf in your project urls.py like this::

(r'^accounts/', include('registration_withemail.urls')),

Users would then be able to register by visiting the URL
``/accounts/register/``, 

and login (once activated) at

``/accounts/login/``, etc.


Required templates
=================

In the default setup, you will need to create several templates
required by django-registration-withemail, and possibly additional templates
required by views in ``django.contrib.auth``.

**registration/registration_form.html**

Used to show the form users will fill out to register. By default, has
the following context:

``form``
    The registration form.

**registration/registration_complete.html**

Used after successful completion of the registration form.

**registration/activate.html**

Used if account activation fails. With the default setup, has the following context:

``activation_key``
    The activation key used during the activation attempt.

**registration/activation_complete.html**

Used after successful account activation.

**registration/activation_email_subject.txt**

Used to generate the subject line of the activation email.

``activation_key``
    The activation key for the new account.

``expiration_days``
    The number of days remaining during which the account may be
    activated.

``site``
    An object representing the site on which the user registered;

**registration/activation_email.txt**
**registration/activation_email.html**

Used to generate the body of the activation email. Should display a
link the user can click to activate the account. This template has the
following context:

``activation_key``
    The activation key for the new account.

``expiration_days``
    The number of days remaining during which the account may be
    activated.

``site``
    An object representing the site on which the user registered;

development
===========

* Source hosted at `GitHub <https://github.com/kamagatos/django-registration-withemail>`
* Report issues on `GitHub Issues <https://github.com/kamagatos/django-registration-withemail/issues>`

Pull requests are very welcomed!

Changelog
=========

0.1
-----

* Initial commit

LICENSE
=======

Unless otherwise noted, the django-registration-withemail source files are distributed under the BSD-style license found in the LICENSE file.
