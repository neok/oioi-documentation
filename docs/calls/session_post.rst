.. highlight:: js

.. _calls-sessionpost-docs:

Session Post
============

Request
-------

``"session-post"`` identifies the call as a session-post call.

Fields
~~~~~~

user
    This field identifies the customer (object).

    identifier-type
        How to identify the user (string).

        The identifier-type can be one of:

        * ``"evco-id"``
        * ``"rfid"``
        * ``"username"``
        * ``"token"``

    identifier
        The identifier is something that uniquely identifies the customer,
        depending on the identifier-type (string).
    token (optional)
        A token can be used to authenticate the user (string).

        For example: if the identifier type is username and the identifier is the user's username,
        then token is used for authentication instead of a password.
session-id
    A unique ID that identifies this session (string).

    The session ID must be a globally unique identifier.

    .. note:: If you are the CPO and owner of the session, this identifier must be created by you.
connector-id
    The EVSE ID of the connector where the session took place (string).
session-interval
    The start and, optionally, stop time of the session (object).

    For example the time the driver plugged in and out of the station.

    start
        The time the session started (string).

        The date/time format is RFC3339 (``Y-m-d\TH:i:sP``).
    stop
        The time the session stopped (string).

        The date/time format is RFC3339 (``Y-m-d\TH:i:sP``).
charging-interval (optional)
    The start and stop time of charging (object).

    For example the time the charging first started and last ended.

    start
        The time the session started (string).

        The date/time format is RFC3339 (``Y-m-d\TH:i:sP``).
    stop
        The time the session stopped (string).

        The date/time format is RFC3339 (``Y-m-d\TH:i:sP``).
energy-consumed (optional)
    The consumed energy in kWh (float).
calculated-cost (optional)
    The cost of the session (object).

    amount
        The cost amount (float).
    currency
        The currency of the cost (string).

        E.g. ``"EUR"``.
partner-identifier
    The partner identifier of the partner that shall be associated with this CDR.
    See also :ref:`partner identifier <glossary-partner-identifier>`

Response
--------
Fields
~~~~~~

reason
    If ``success`` was ``false``, ``reason`` explains what the problem was. This field is of type string. Will be ``null`` on success.

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success
100
    System error

Examples
--------

Request::

    {
        "session-post": {
            "user": {
                "identifier": "12345678",
                "identifier-type": "rfid"
            },
            "session-id": "abcdef-123456-abc123-456def",
            "connector-id": "DE*8PS*ETABCD*1",
            "session-interval": {
                "start": "2010-01-01T11:00:00+00:00",
                "stop": "2010-01-01T17:00:00+00:00"
            },
            "charging-interval": {
                "start": "2010-01-01T12:00:00+00:00",
                "stop": "2010-01-01T16:00:00+00:00"
            },
            "energy-consumed": 16.5,
            "calculated-cost": {
                "amount": 14.32,
                "currency": "EUR"
            },
            "partner-identifier": "123456-123456-abcdef-abc123-456def"
        }
    }

Response::

    {
        "result": {
            "code": 0,
            "message": "Success."
        }
    }

.. todo:: Section "After a Session has finished"
.. todo:: Section "While a Session is running"
