.. highlight:: js

.. _calls-rfidpost-docs:

RFID Post
=========

.. note:: UIDs are read from left to right using big-endian format.

.. note:: Valid lengths of UIDs are 8, 14, and 20 characters.
          If you have shorter UIDs, you need to zero-pad them on the left.

.. note:: UIDs need to be all upper case.

Request
-------

``"rfid-post"`` identifies this call as an rfid-post call.

Fields
~~~~~~

rfids
    An array of strings. Each string represents one UID.
partner-identifier
    The partner identifier of the partner that shall be associated with these UIDs (string).
    See also :ref:`partner identifier <glossary-partner-identifier>`

Response
--------

Fields
~~~~~~

processed
    The number of new UIDs added by this call (integer).

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    Request was processed successfully

Result codes
~~~~~~~~~~~~

0
    Success

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
            "processed": 2
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
