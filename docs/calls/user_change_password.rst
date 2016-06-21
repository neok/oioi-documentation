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

Fields
~~~~~~

password-changed
    Whether or not the the password was changed (boolean).

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
        "user": {
            "password-changed": true
        }
    }
