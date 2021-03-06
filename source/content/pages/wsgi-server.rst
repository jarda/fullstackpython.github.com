WSGI Server
===========

:category: page
:slug: wsgi-server
:sort-order: 06

A `Web Server Gateway Interface <http://wsgi.readthedocs.org/en/latest/>`_ 
(WSGI) server implements the web server side of the WSGI interface for 
running Python web applications. The WSGI standard v1.0 is specified in 
`PEP 0333 <http://www.python.org/dev/peps/pep-0333/>`_. As of September 2010, 
WSGI v1.0 is superseded by 
`PEP 3333 <http://www.python.org/dev/peps/pep-3333/>`_, which defines the
v1.0.1 WSGI standard.

----


.. image:: ../img/wsgi-server-browser.png
  :alt: WSGI Server <-> Web server <-> Browser

Requests from the browser that are not for static assets (this is specified
in the web server's configuration which requests are for static assets and
which are not) are passed to the WSGI server. Once the request is 
processed by the WSGI server, the request is passed back through the 
web server and onto the browser.

----

WSGI Resources
--------------
`PEP 0333 WSGI v1.0 <http://www.python.org/dev/peps/pep-0333/>`_ 
and
`PEP 3333 WSGI v1.0.1 <http://www.python.org/dev/peps/pep-3333/>`_ 
specifications.

`Green Unicorn <http://gunicorn.org/>`_, 
`mod_wsgi <http://code.google.com/p/modwsgi/>`_,
`uWSGI <https://github.com/unbit/uwsgi-docs>`_, and
`gevent <http://www.gevent.org/>`_ are common WSGI server implementations.

`Complete single server Django stack tutorial <http://www.apreche.net/complete-single-server-django-stack-tutorial/>`_ is thorough and informative for
non-paas hosting choices.
