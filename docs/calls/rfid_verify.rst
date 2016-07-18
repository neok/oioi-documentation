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

verified
    ``true`` if the given UID is valid, ``false`` otherwise.

Status code
~~~~~~~~~~~

200 OK
    Request was processed successfully
404 Not found
    An active RFID with the given UID could not be found.
    However, it is possible that the RFID is known, but currently blocked.

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
        "rfid-verify": {
            "verified": true
        }
    }
