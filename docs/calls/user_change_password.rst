.. highlight:: js

.. _calls-userchangepassword-docs:

User Change Password
====================

Request
-------

``"user-change-password"`` identifies the call as a user-change-password call.

Fields
~~~~~~

username
    This field identifies the customer by username or email (string).
current-password
    Current password of the customer (string).
new-password
    New password of the customer (string).

Response
--------

HTTP Status codes
~~~~~~~~~~~~~~~~~
200 OK
    Request was processed successfully

Result codes
~~~~~~~~~~~~
0
    Success
140
    Authentication failed: No positive authentication response
144
    Authentication failed: Email does not exist

Examples
--------

Request::

    {
        "user-change-password": {
            "username": "myusername",
            "current-password": "oldpassword",
            "new-password": "mynewpassword"
        }
    }

Response::

    {
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
