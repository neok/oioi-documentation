Glossary
========

.. _glossary-ev:

EV
    Electric Vehicle.
    A car that is powered by an electric engine rather than an internal combustion engine.

    `Wikipedia EV`_

.. _glossary-charging-station:

Charging Station
    A place where a driver of an :ref:`EV <glossary-ev>` can charge their car, can vary in size from very small to pretty large.
    Connectors can supply electricity either as alternating current (AC) or direct current (DC).

    `Wikipedia Charging Station`_

.. _glossary-poi:

POI
    Point of Interest.
    Throughout this documentation, :ref:`charging stations <glossary-charging-station>` are referred to as POI.

.. _glossary-evse:

EVSE
    Electric Vehicle Supply Equipment.
    A :ref:`charging station <glossary-charging-station>` may have one or more EVSE IDs
    Usually, one EVSE ID uniquely identifies one connector

    There are cases where one EVSE ID identifies multiple connectors.
    In that case, all connectors always share the same status (e.g. `Available` or `Occupied`).
    That also means that only one connector of all the connectors sharing the same EVSE ID can be in use at any one point in time.

    Example: ``+49*123*E123456``
    General structure (*may* be separated by asterisks):

    * Country Code
    * CPO identifier (PlugSurfing's is usually ``8PS``, in the Netherlands ``PLU``)
    * literal ``E``
    * ID of the EVSE

    See also `Wikipedia Charging Station`_.

.. _glossary-cpo:

CPO
    Charge Point Operator.
    To access a :ref:`charging station <glossary-charging-station>` via an API, usually our server connects to the CPO's server.

.. _glossary-emp:

EMP
    E-Mobility Provider.
    Companies that provide :ref:`EV <glossary-ev>` drivers with access to charging stations.
    PlugSurfing is an EMP.

.. _glossary-evco-id:

EVCO ID
    ID of a customer of an :ref:`EMP <glossary-emp>`.
    Uniquely identifies the customer across EMPs.
    A PlugSurfing customer could have an EVCO ID like ``+49*8PS*123456*7``, although there are different formats.
    General structure (*may* be separated by asterisks):

    * Country Code
    * EMP identifier (PlugSurfing's is usually ``8PS``, in the Netherlands ``PLU``)
    * ID of the customer
    * Check digit

.. _glossary-cdr:

CDR
    Charge Detail Record.
    After a customer finished charging at a :ref:`charging station <glossary-charging-station>`,
    the :ref:`CPO <glossary-cpo>` provides us with the CDR for that session.
    Includes data like:

    * Session start date/time
    * Session end date/time
    * Consumed energy

.. note:: A CDR may be sent by a CPO before the session finished.
          For example to inform the EMP of a started session.

.. _glossary-charging-key:

Charging Key
    The charging key is an RFID token that authenticates an :ref:`EV <glossary-ev>` driver at a :ref:`charging station <glossary-charging-station>`.

.. _glossary-static-data:

Static data
    Data that doesn't change frequently
    Charging station location, address, connector type, etc.

.. _glossary-dynamic-data:

Dynamic data
    Data that may change frequently.
    Statuses of connectors.

.. _glossary-partner-identifier:

Partner Identifier
    A universally unique identifier that identifies the partner who issues an API call.
    This is different from an API key!
    The partner chooses the identifier and gives it to PlugSurfing in a secure manner.
    Must be unique and hard to guess.
    We remomend a random string that is at least 16 characters long.

    A company with one API key can use multiple partner-identifiers,
    for example to make API calls for another company.

    At the same time, multiple API keys can use the same partner identifier to act
    on behalf of that entity.

.. _wikipedia ev:  https://en.wikipedia.org/wiki/Electric_vehicle
.. _wikipedia charging station: https://en.wikipedia.org/wiki/Charging_station
