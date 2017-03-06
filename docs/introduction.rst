.. _introduction:

Introduction
============
To enhance the speed of onboarding :ref:`CPOs <glossary-cpo>` and :ref:`EMPs <glossary-emp>`,
PlugSurfing has created an open API: the OIOI.
The OIOI covers all messages between a CPO and an EMP.

Business logic
--------------
The aim of the OIOI is to allow electric car drivers access to any charging station around.
The OIOI therefore has two functions.
First, to on-board CPOs into an EMP's network.
Second, to allow communication with the charging stations from the electric car driver's point of view.

Hence, CPOs can get access to many electric car drivers and electric car drivers can get access to many charging station networks.
For both sides of the spectrum the OIOI becomes an easy gateway to more customers and more comfort.

The idea of the OIOI came up after many, many CPOs wanted to connect to Plugsurfing,
but did not have the technical means (no API) to connect.
The OIOI helps them now to connect to Plugsurfing.
On the other hand, it saves money and time of all parties that are involved;
the workload of connecting many different interface is, of course, significant.

The main difference between the OIOI and other existing API definitions is:

* it is open to anyone to use or distribute it free of charge
* it is very simple to implement

Fundamentals of OIOI
--------------------
The OIOI consists of several main functions that establish a relationship between the electric car driver,
the EMP,
and the charging station network.

The following integration is required:

Point of Interest
    :ref:`POI <glossary-poi>` includes the static and dynamic information regarding the whereabouts and properties of a charging station.
    This is necessary for an :ref:`EV <glossary-ev>` Driver to find a charging station using a smartphone app.

Charge Detail Records
    A :ref:`CDR <glossary-cdr>` informs about who has been charging at which station,
    as well as the consumption.
    A CDR provides objective, raw data allowing the payment and clearing of funds within the value chain.

Client Exchange
    In order for a CPO to allow or deny access of a customer using RFID,
    a unique identifier between the EMP and the CPO needs to be exchanged.
    The identifiers are made out of a contract ID (:ref:`EVCO ID <glossary-evco-id>`) and the unique UID of the charging key.

Remote Start/Stop
    In order to start or stop a charging session from an app,
    both partners implement the remote start/stop functionality of the OIOI.
    The EMP implements it client side, while the CPO implements it server side.

API Key
    In order to have access to an OIOI service API, you need to be in possession of an API key.
    You supply that key with every request and the receiver verifies that you have access to the requested resource.

.. note:: If you want to get an API key to connect to PlugSurfing,
          please contact the `PlugSurfing Service`_.

.. warning:: Never give your API key to anyone except as part of an OIOI request!
             No one will ever ask you for your API key!
             PlugSurfing may cancel your access if your key is associated with malicious behaviour.

.. _plugsurfing service: mailto:service@plugsurfing.com
