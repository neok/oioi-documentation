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
   This field identifies the customer.
   The identifier is something that uniquely identifies the customer, depending on the identifier-type.
   The identifier field is of type string.
   The identifier-type can be one of:

   * ``"evco-id"``
   * ``"rfid"``
   * ``"username"``

   The token field is an optional field of type string and can be used to authenticate the user.

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
