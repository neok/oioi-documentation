Welcome to OIOI's documentation!
================================

.. image:: images/ps-oioi-logo-small.png

.. warning:: This is the latest version of the OIOI, **version 4.**

             For other versions, e.g. **version 3**,
             open the menu on the very bottom left of the screen.

             Even though this version is marked as ``stable``,
             new fields may be added to requests and responses.

             Your service must still accept all responses.
             You may ignore the additional fields or implement an update.

             Requests will only get additional fields if they are optional.

.. important :: This specific release is |release|.

The main documentation for the OIOI is organized into a couple of sections:

* :ref:`introduction-docs`
* :ref:`cpo-docs`
* :ref:`oem-docs`
* :ref:`fleet-docs`
* :ref:`calls-docs`

.. _introduction-docs:

.. toctree::
   :maxdepth: 2
   :caption: Introduction

   introduction
   request
   testaccount
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
   cpo/reservation

.. _oem-docs:

.. toctree::
   :maxdepth: 2
   :caption: Connecting as OEM

   oem/index
   oem/user
   oem/poi
   oem/cdr
   oem/remote_start
   oem/rfid_start
   oem/reservation

.. _fleet-docs:

.. toctree::
   :maxdepth: 2
   :caption: Connecting as Fleet Operator

   fleet/index
   fleet/cdr

.. _calls-docs:

.. toctree::
  :maxdepth: 1
  :caption: HTTP Calls
  :glob:

  calls/*

.. todolist::
