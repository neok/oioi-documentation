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
        * ``"token"``

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

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success
140
    Authentication failed: No positive authentication response
144
    Authentication failed: Email does not exist
145
    Authentication failed: User token not valid
190
    EVCO ID error

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
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
