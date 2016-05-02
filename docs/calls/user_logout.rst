.. highlight:: js

.. _calls-userlogout-docs:

User Logout
===========

Request
-------

``"user-logout"`` identifies the call as a user-logout call.

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

Response
--------

Fields
~~~~~~

success
    ``true``, if the logout was a success, ``false`` otherwise (boolean).

Status codes
~~~~~~~~~~~~

200 OK
    The request was processed successfully.
    The user is logged out.
401 Unauthorized
    The username does not exist or the username and password/token did not match.

Examples
--------

Request::

    {
        "user-logout": {
            "user": {
                "identifier-type": "username",
                "identifier": "youridentifier",
                "token": "87d4e3085af04671834ebeb127df33bf"
            }
        }
    }

Response::

    {
        "user-logout": {
            "success": true
        }
    }
