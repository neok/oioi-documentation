.. highlight:: js

.. _calls-usergetchargingkeys-docs:

User Get Charging Keys
==========================

Request
-------

``"user-get-charging-keys"`` identifies the call as a user-get-charging-keys call.

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

Response
--------

Fields
~~~~~~

charging-keys
   An array of user charging keys (array of objects).

   uid
     Charging key UID (string).

   evco-id
     Charging key EVCO ID (string).

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

Examples
--------

Request::

    {
        "user-get-charging-keys": {
            "user": {
                "identifier-type": "username",
                "identifier": "some_user",
                "token": "b369f99e82fa097ba9cff8658c74e47c"
            }
        }
    }

Response::

    {
        "user": {
            "charging-keys": [
                {
                    "uid": "ABCDABCD",
                    "evco-id": "DE*8PS*C12345"
                },
                {
                    "uid": "ABCDABCF",
                    "evco-id": "DE*8PS*C12346"
                }
            ]
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
