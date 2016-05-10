Welcome to OIOI's documentation!
================================

.. image:: images/ps-oioi-logo-small.png

.. warning:: This is the latest version of the OIOI, **version 4.**
             The latest version is still under development and not stable.

             For other versions, e.g. **stable**,
             open the menu on the very bottom left of the screen.

.. warning:: Even though this version is marked as ``stable``,
             new fields may be added to requests and responses.

             Your service must still accept all responses.
             You may ignore the additional fields or implement an update.

             Requests will only get additional fields if they are optional.

The main documentation for the OIOI is organized into a couple of sections:

* :ref:`introduction-docs`
* :ref:`cpo-docs`
* :ref:`emp-docs`
* :ref:`calls-docs`

.. _introduction-docs:

.. toctree::
   :maxdepth: 2
   :caption: Introduction

   introduction
   request
   glossary

.. _cpo-docs:

.. toctree::
   :maxdepth: 2
   :caption: Connecting as CPO

   cpo/index
   cpo/poi
   cpo/cdr
   cpo/remote_start
   cpo/rfid_start

.. _emp-docs:

.. toctree::
   :maxdepth: 2
   :caption: Connecting as EMP

   emp/index
   emp/user
   emp/poi
   emp/cdr
   emp/remote_start
   emp/rfid_start

.. _calls-docs:

.. toctree::
  :maxdepth: 1
  :caption: HTTP Calls
  :glob:

  calls/*

.. todolist::
