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
    This field identifies the customer (object).

    identifier-type
        How to identify the user (string).

        The identifier-type can be one of:

        * ``"evco-id"``
        * ``"rfid"``
        * ``"username"``

    identifier
        The identifier is something that uniquely identifies the customer,
        depending on the identifier-type (string).
    token (optional)
        A token can be used to authenticate the user (string).

        For example: if the identifier type is username and the identifier is the user's username,
        then token is used for authentication instead of a password.
connector-id
   The EVSE ID that identifies the connector where the session should be stopped (string).
session-id (optional)
   A unique ID that identifies this session (string).

   .. warning:: Depending on the CPO's requirements, a ``session-id`` may be mandatory.

Response
--------

Fields
~~~~~~

success
   Whether or not the call was a success (boolean).

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
