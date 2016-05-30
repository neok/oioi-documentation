.. highlight:: js

.. _calls-userchargingkeyactivate-docs:

User Charging Key Activate
==========================

Request
-------

``"user-charging-key-activate"`` identifies the call as a user-charging-key-activate call.

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
evco-id
   The EVCO ID that identifies the charging key (string).

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
400 Bad Request
   Wrong EVCO ID format
401 Unauthorized
   The token, username or identifier type were incorrect
500 Internal Server Error
   Charging key cannot be activated

Examples
--------

Request::

    {
        "user-charging-key-activate": {
            "user": {
                "identifier-type": "username",
                "identifier": "youridentifier",
                "token": "yourtoken"
            },
            "evco-id": "yourevcoid"
        }
    }

Response::

    {
        "user-charging-key-activate": {
            "success": true
        }
    }
