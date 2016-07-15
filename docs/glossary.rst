Glossary
========

.. _glossary-ev:

EV
    Electric Vehicle.

    `Wikipedia EV`_

.. _glossary-charging-station:

Charging Station
    A place where a driver of an :ref:`EV <glossary-ev>` can charge their car, can vary in size from very small to pretty large.
    Connectors can supply electricity either as alternating current (AC) or direct current (DC).

    `Wikipedia Charging Station`_

.. _glossary-poi:

POI
    Point of Interest.
    POI refers to the whereabouts and attributes of a charging station, including latitude, longitude, plug type, and charging speed.
    Throughout this documentation, the terms :ref:`charging stations <glossary-charging-station>` and POI are used interchangeably.

.. _glossary-evse:

EVSE
    Electric Vehicle Supply Equipment.
    A :ref:`charging station <glossary-charging-station>` may have one or more EVSE IDs.
    Usually, one EVSE ID uniquely identifies one connector.

    There are cases where one EVSE ID identifies multiple connectors.
    In that case, all connectors with the same EVSE ID always share the same status (e.g. ``Available`` or ``Occupied``).
    That also means that only one connector of all the connectors sharing the same EVSE ID can be in use at any one point in time.

    Example: ``DE*123*E12345*A``

    An EVSE ID must be valid with respect to the following structure:

    * ``[A-Za-z]{2}\*?[A-Za-z0-9]{3}\*?E[A-Za-z0-9\*]{1,30}``
    * Country Code (international two-letter code in accordance with `ISO 3166-1 alpha-2`_)
    * The literal ``*`` (optional)
    * CPO identifier (letters and numbers; three characters unquiely identifying the CPO of the EVSE)
    * The literal ``*`` (optional)
    * The literal ``E``
    * ID of the EVSE (letters, numbers, and the literal ``*``; 1 - 30 characters)

    .. note:: When you are based in Germany, please see here for more general information and details on how to register a CPO identifier: `BDEW Codes`_.

    See also `Wikipedia Charging Station`_.

.. _glossary-cpo:

CPO
    Charge Point Operator.
    The CPO manages, operates, and maintains charging station infrastructure.

.. _glossary-emp:

EMP
    E-Mobility Provider.
    Companies that provide :ref:`EV <glossary-ev>` drivers with access to charging stations.
    PlugSurfing, as interface between electric car drivers and CPOs, is an EMP.

.. _glossary-evco-id:

EVCO ID
    Contract ID of :ref:`EMP <glossary-emp>` and :ref:`EV <glossary-ev>` driver.
    Uniquely identifies the customer across all networks.

    An EVCO ID must be valid with respect to the following structure:

    * ``[A-Za-z]{2}[\*|-]?[A-Za-z0-9]{3}[\*|-]?[A-Za-z0-9]{6}[\*|-]?[\d|X]``
    * Country Code (international two-letter code in accordance with `ISO 3166-1 alpha-2`_)
    * The literal ``*`` **or** the literal ``-`` (optional)
    * EMP identifier (letters and numbers; three characters unquiely identifying the EMP of the EVCO)
    * The literal ``*`` **or** the literal ``-`` (optional)
    * ID of the EVCO (letters and numbers; six characters)
    * The literal ``*`` **or** the literal ``-`` (optional)
    * Check digit (A number or the literal ``X``)

    .. note:: When you are based in Germany, please see here for more general information and details on how to register an EMP identifier: `BDEW Codes`_.

.. _glossary-cdr:

CDR
    Charge Detail Record.
    After a customer finished charging at a :ref:`charging station <glossary-charging-station>`,
    the :ref:`CPO <glossary-cpo>` provides the EMP with the CDR for that session.
    Includes data like:

    * Session start date/time
    * Session end date/time
    * Consumed energy
    * EVCO ID or UID

.. note:: A CDR may be sent by a CPO before the session finished.
          For example to inform the EMP of a started session.

.. _glossary-charging-key:

RFID
    An RFID token that authenticates an :ref:`EV <glossary-ev>` driver at a :ref:`charging station <glossary-charging-station>`.
    Common RFID carriers are cards (credit card format) and key hangers.

.. _glossary-static-data:

Static data
    Data on the charging station that doesn't change frequently.
    Charging station location, address, connector type, etc.

.. _glossary-dynamic-data:

Dynamic data
    Data that may change frequently,
    like the status of a connector.

.. _glossary-partner-identifier:

Partner Identifier
    A universally unique identifier that identifies the partner who issues an API call.
    This is different from an API key!
    The sending partner chooses the identifier and provides it to the receiving partner in a secure manner.
    Must be unique and hard to guess.
    Must be a random string that is at least 16 characters long.

    A company with one API key can use multiple partner identifiers,
    for example to make API calls for another company.

    At the same time, multiple API keys can use the same partner identifier to act
    on behalf of that entity.

.. _wikipedia ev:  https://en.wikipedia.org/wiki/Electric_vehicle
.. _wikipedia charging station: https://en.wikipedia.org/wiki/Charging_station
.. _iso 3166-1 alpha-2: https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2
