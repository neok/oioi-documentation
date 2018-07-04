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
        * ``"token"``

    identifier
        The identifier is something that uniquely identifies the customer,
        depending on the identifier-type (string).

    token (optional)
        A token can be used to authenticate the user (string).

        For example: if the identifier type is username and the identifier is the user's username,
        then token is used for authentication instead of a password.

rfid
    The RFID (UID) that identifies the charging key (string).

    .. important:: - The format must be a hexadecimal string.

                   - An RFID must have a length of 8, 14 or 20 characters.
                     If necessary, the RFID must be zero-padded on the left.

                   - It should be read from left to right using big-endian format.

                   - All characters must be upper-case.

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
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
