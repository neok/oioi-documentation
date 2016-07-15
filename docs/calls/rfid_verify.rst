.. highlight:: js

.. _calls-rfidverify-docs:

RFID Verify
===========

.. note:: UIDs are read from left to right using big-endian format.

.. note:: Valid lengths of UIDs are 8, 14, and 20 characters.
          If you have shorter UIDs, you need to zero-pad them on the left.

.. note:: UIDs need to be all upper case.

Request
-------

``"rfid-verify"`` identifies this call as an rfid verify call.

Fields
~~~~~~

rfid
    The UID to verify (string).

Response
--------

HTTP Status code
~~~~~~~~~~~~~~~~

200 OK
    Request was processed successfully
404 Not found
    An active RFID with the given UID could not be found.
    However, it is possible that the RFID is known, but currently blocked.

Result code
~~~~~~~~~~~

0
    Success
191
    EVCO ID not found
192
    EVCO ID locked
193
    EVCO ID has no valid payment method

Examples
--------

Request::

    {
        "rfid-verify": {
            "rfid": "12345678ABCDEF"
        }
    }

Response::

    {
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
