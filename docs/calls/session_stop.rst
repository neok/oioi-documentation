.. highlight:: js

.. _calls-sessionstop-docs:

Session Stop
============

Request
-------

``"session-stop"`` identifies the call as a session-stop call.

Fields
~~~~~~

user
   This field identifies the customer.
   The identifier is something that uniquely identifies the customer, depending on the identifier-type.
   The identifier field is of type string.
   The identifier-type can be one of:

   * ``"evco-id"``
   * ``"rfid"``
   * ``"username"``

   The token field is an optional field of type string and can be used to authenticate the user.
connector-id
   The EVSE ID that identifies the connector where the session should be stopped.
session-id
   A unique ID that identifies this session. Can be any string.

Response
--------

Fields
~~~~~~

success
   Whether or not the call was a success (of type boolean)

Status codes
~~~~~~~~~~~~

200 OK
   Request was processed successfully
401 Unauthorized
   The token, username or identifier type were incorrect
404 Not found
   A connector could not be found by the supplied identifier

Examples
--------

Request::

    {
        "session-stop": {
            "user": {
                "identifier-type": "username",
                "identifier": "youridentifier",
                "token": "87d4e3085af04671834ebeb127df33bf"
            },
            "connector-id": "1356",
            "session-id": "dfdf"
        }
    }

Response::

    {
        "session-stop": {
            "success": true
        }
    }
