.. highlight:: js

.. _calls-useraddcreditcard-docs:

User Add Credit Card
====================

Request
-------

``"user-add-creditcard"`` identifies the call as a user-add-creditcard call.

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
encrypted-data
    Encrypted credit card data (string)

    .. note:: PlugSurfing does not handle any credit card data.
              The data must be encrypted client side before it is sent so that PlugSurfing cannot access this data.
              If you need details on how to encrypt the data or the public key to do so, please contact PlugSurfing.

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
805
    This user is not allowed to use this method
870
    Credit card error

Examples
--------

Request::

    {
        "user-add-creditcard": {
            "user": {
                "identifier-type": "username",
                "identifier": "youridentifier",
                "token": "87d4e3085af04671834ebeb127df33bf"
            },
            "encrypted-data": "zpTIi0RDoCl7SzDF9dVIKhNFI0rzpTIi0RDoCl7SzDF9dVIKhNFI0rzpTIi0RDoCl7SzDF9dVIKhNFI0r"
        }
    }

Response::

    {
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
