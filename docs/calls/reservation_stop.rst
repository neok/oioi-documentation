.. highlight:: js

.. _calls-reservationstop-docs:

Reservation Stop
================

Request
-------

``"reservation-stop"`` identifies the call as a reservation-stop call.

Fields
~~~~~~

identifier-type
    How to identify the user (string).

    The identifier-type can be one of:

    * ``"evco-id"``
    * ``"rfid"``

identifier
    The identifier is something that uniquely identifies the customer, depending on the identifier-type (string).

Response
--------

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success
189
    Reservation not found
190
    EVCO ID error
191
    EVCO ID unknown

Examples
--------

Request::

    {
        "reservation-stop": {
            "identifier-type": "evco-id",
            "identifier": "DE*8PS*156456730*9"
        }
    }

Response::

    {
        "result": {
            "code": 0,
            "message": "Success."
        }
    }


