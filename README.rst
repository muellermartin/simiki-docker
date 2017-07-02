=============
Simiki Docker
=============

Building the Docker image
=========================

From this repository run:

.. code::

  docker build -t simiki .

Using the Docker image
======================

You can simply pass Simiki commands to the Docker run command.
For a full list of commands the the Simiki Quick Start guide and documentation:

- Quick Start guide: http://simiki.org/docs/usage.html
- Usage Documentation: http://simiki.org/docs/usage.html

Initializing a new wiki
-----------------------

.. code::

  docker run --rm -it -v $(PWD)/wiki:/wiki simiki init

Generate wiki pages
-------------------

.. code::

  docker run --rm -v $(PWD)/wiki:/wiki simiki g

Note: You propably need to pass the timezone via an environment variable e.g.
by adding :code:`-e TZ=UTC`. This prevents an :code:`UnknownTimeZoneError(zone)`
exception (:code:`pytz.exceptions.UnknownTimeZoneError: 'local'`) when
generating the pages.

Preview/Show the wiki
---------------------

.. code::

  docker run -v $(PWD)/wiki:/wiki -p 8000:8000 simiki p --host 0.0.0.0
