.. highlight:: js

.. _calls-rfidverify-docs:

RFID Verify
===========

Request
-------

``"rfid-verify"`` identifies this call as an rfid verify call.

Fields
~~~~~~

rfid
    The UID to verify (string).

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
    However, it is possible that the RFID is known by PlugSurfing, but currently blocked.

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
