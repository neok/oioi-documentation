.. highlight:: js

.. _calls-useraddrfid-docs:

User Add RFID
=============

Request
-------

``"user-add-rfid"`` identifies the call as a user-add-rfid call.

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

rfid
    The RFID that identifies the charging key (string).

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
401
  User could not be authenticated
409
  RFID already exists for another user

Examples
--------

Request::

    {
        "user-add-rfid": {
            "user": {
                "identifier-type": "username",
                "identifier": "john",
                "token": "b3853b6d910849f3b4392555b8acb984"
            },
            "rfid": "12345678ABCDEF"
        }
    }

Response::

    {
        "user-add-rfid": {
            "success": true
        }
    }