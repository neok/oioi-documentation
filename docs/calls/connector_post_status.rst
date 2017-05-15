.. highlight:: js

.. _calls-connectorpoststatus-docs:

Connector Post Status
=====================

Request
-------

``"connector-post-status"`` identifies the call as a status update call.

Fields
~~~~~~

connector-id
    The EVSE ID of the connectors (string).
    All connectors with the given connector-id will be updated.
    See also :ref:`EVSE <glossary-evse>`.
status
    One of the following strings:

    * ``"Available"``
    * ``"Occupied"``
    * ``"Offline"``
    * ``"Reserved"``
    * ``"Unknown"``

partner-identifier
    The partner identifier of the partner that owns the connector (string).
    See also :ref:`partner identifier <glossary-partner-identifier>`

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
181
    EVSE not found

Examples
--------

Request::

    {
        "connector-post-status": {
            "connector-id": "DE*8PS*E123456",
            "partner-identifier": "123456-123456-abcdef-abc123-456def",
            "status": "Available"
        }
    }

Response::

    {
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
