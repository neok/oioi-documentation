Introduction
============

To enhance the speed of onboarding :ref:`CPOs <glossary-cpo>` and :ref:`EMPs <glossary-emp>`,
PlugSurfing has created its own API: the OIOI.
The OIOI covers all messages between the CPO/EMP and PlugSurfing.

Business logic
--------------

In order for the PlugSurfing app and :ref:`charging key <glossary-charging-key>` to function,
a server connection between EMP and CPO needs to be established to exchange the required data.
The OIOI allows for this server connection between PlugSurfing and the CPO.
The CPO can inform PlugSurfing about the :ref:`charging stations <glossary-charging-station>` and charging sessions.
With the OIOI, PlugSurfing can send requests to charge from the app and the charging key.

In order for apps and charging keys from other EMPs to access the PlugSurfing network,
a connection between that EMP and PlugSurfing's servers needs to be established.
The OIOI allows for this connection.
The EMP can get information about charging stations and charging sessions.
With the OIOI, the EMP can send requests to charge from the app and the charging key.

Fundamentals of OIOI
--------------------

The following integration is required:

Point of Interest
    :ref:`POI <glossary-poi>` includes the static and dynamic information regarding the whereabouts and properties of a charging station.
    This is necessary for an :ref:`EV <glossary-ev>` Driver to find a charging station using the PlugSurfing app.

Charge Detail Records
    A :ref:`CDR <glossary-cdr>` informs PlugSurfing about who has been charging at which station,
    as well as the consumption.
    A CDR is required for PlugSurfing to bill the customer or to manage the clearing with the EMP.

Client Exchange
    In order for a CPO to allow or deny the access of a PlugSurfing customer using the charging key,
    a unique identifier between PlugSurfing and the CPO needs to be exchanged.
    Every charging key and customer has a unique identifier to ensure the PlugSurfing customer can charge at the CPO.
    The identifiers are made out of a contract ID (:ref:`EVCO ID <glossary-evco-id>`) and the unique UID of the charging key.

Remote Start/Stop
    In order to start or stop a charging session from an app,
    PlugSurfing's partner implements the remote start/stop functionality of the OIOI.

API Key
    In order to have access to the PlugSurfing API you need to be in possession of an API key.
    You supply that key with every request and PlugSurfing verifies that you have access to the requested resource.

.. note:: If you want to get an API key to connect to PlugSurfing,
          please contact the `PlugSurfing Service`_.

.. warning:: Never give your API key to anyone!
             PlugSurfing will never ask you for your API key!
             PlugSurfing may cancel your access if your key is associated with malicious behaviour.

.. _plugsurfing service: mailto:service@plugsurfing.com
