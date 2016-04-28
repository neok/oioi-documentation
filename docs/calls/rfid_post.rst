.. highlight:: js

.. _calls-rfidpost-docs:

RFID Post
=========

Request
-------

``"rfid-post"`` identifies this call as an rfid-post call.

Fields
~~~~~~

rfids
    An array of strings. Each string represents one UID.
partner-identifier
    The partner identifier of the partner that shall be associated with this CDR.
    See also :ref:`partner identifier <glossary-partner-identifier>`

Response
--------

Fields
~~~~~~

success
    Whether or not the call was a success (boolean).
processed
    The number of new UIDs added by this call (integer).

Status codes
~~~~~~~~~~~~

200 OK
    Request was processed successfully

Examples
--------

Request::

    {
        "rfid-post": {
            "rfids": [
                "12345678",
                "abcdefab"
            ],
            "partner-identifier": "123456-123456-abcdef-abc123-456def"
        }
    }

Response::

    {
        "rfid": {
            "success": true,
            "processed": 2
        }
    }
