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
    The RFID (UID) to verify (string).

    .. important:: - An RFID must have a length of 8, 14 or 20 characters.
                     If necessary, the RFID must be zero-padded on the left.

                   - It should be read from left to right using big-endian format.

                   - All characters must be upper-case.

Response
--------
Fields
~~~~~~

evco-id
    EVCO ID of the RFID is returned in case of response with 0 result code (string)

HTTP Status code
~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

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
        "evco-id": "DE*8PS*D89761*2",
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
