.. highlight:: js

.. _cpo-cdr-docs:

Sending CDRs
============

Use this method to send CDRs.

CDRs are the basis of all billing and clearing.

This call can also be used to pass information about sessions that are still ongoing.
To do this, just omit the session interval's stop field.

Request/Response
----------------

``"session-post"`` identifies the call as a session-post call.

Request fields
~~~~~~~~~~~~~~

user
    This field identifies the customer who charged. The identifier is something that uniquely identifies the customer, depending on the identifier-type. The identifier field is of type string.
    The identifier-type can be one of:

    * ``"evco-id"``
    * ``"rfid"``
    * ``"username"``

    The token field is an optional field of type string and can be used to authenticate the user.
session-id
    A unique ID that identifies this session. Can be any string.
connector-id
    A unique ID that identifies the connector where the session took place. For example an EVSEID. Can be any string.
session-interval
    The start and, optionally, stop time of the session. For example the time the driver plugged in and out of the station. This field is of type string.
    The date/time format is RFC3339 (``Y-m-d\TH:i:sP``).
charging-interval (optional)
    The start and stop time of charging. For example the time the charging first started and last ended. This field is of type string.
    The date/time format is RFC3339 (``Y-m-d\TH:i:sP``).
energy-consumed (optional)
    The consumed energy as float in kWh.
partner-identifier
    The partner identifier of the partner that shall be associated with this CDR.
    See also :ref:`partner identifier <glossary-partner-identifier>`

Response fields
~~~~~~~~~~~~~~~

success
    Whether or not the call was a success (of type boolean).
reason
    If ``success`` was ``false``, ``reason`` explains what the problem was. This field is of type string. Will be ``null`` on success.

Example
~~~~~~~

Request::

    {
        "session-post": {
            "user": {
                "identifier": "12345678",
                "identifier-type": "rfid"
            },
            "session-id": "abcdef-123456-abc123-456def",
            "connector-id": "DE*8PS*TABCDE*1",
            "session-interval": {
                "start": "2010-01-01T11:00:00+00:00",
                "stop": "2010-01-01T17:00:00+00:00"
            },
            "charging-interval": {
                "start": "2010-01-01T12:00:00+00:00",
                "stop": "2010-01-01T16:00:00+00:00"
            },
            "energy-consumed": 16.5,
            "partner-identifier": "123456-123456-abcdef-abc123-456def"
        }
    }

Response::

    {
        "session": {
            "success": true,
            "reason": null
        }
    }

.. todo:: Section "After a Session has finished"
.. todo:: Section "While a Session is running"
