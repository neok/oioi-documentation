.. highlight:: js

.. _calls-rfidpost-docs:

RFID Post
=========

.. note:: UIDs are read from left to right using big-endian format.

.. note:: Valid lengths of UIDs are 8, 14, and 20 characters.
          If you have shorter UIDs, you need to zero-pad them on the left.

.. note:: UIDs need to be all upper case.

RFID Post acts like a complete whitelist of UIDs on every request.
Every call has to include the complete list of RFIDs that shall be active.

All RFIDs that were pushed before with the same ``"partner-identifier"`` and are not part of a request
must be made invalid on the receiver side.

Request
-------

``"rfid-post"`` identifies this call as an rfid-post call.

Fields
~~~~~~

rfids
    An array of strings. Each string represents one RFID (UID).

    .. important:: - An RFID must have a length of 8, 14 or 20 characters.
                     If necessary, the RFID must be zero-padded on the left.

                   - It should be read from left to right using big-endian format.

                   - All characters must be upper-case.

partner-identifier
    The partner identifier of the partner that shall be associated with these UIDs (string).
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
