.. highlight:: js

.. _calls-userreset-docs:

User Reset
===========

Request
-------

``"user-reset"`` identifies the call as a user-reset call.

Fields
~~~~~~

identifier
    The username or the email of the user (string).

Response
--------

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.
    The password of the user is reset and the user will receive an email with a link.
404 Not Found
    No user with the given username/email found.

Result codes
~~~~~~~~~~~~
0
    Success
144
    Authentication failed: Email does not exist

Examples
--------

Request::

    {
        "user-reset": {
            "identifier": "usernameoremail"
        }
    }

Response::

    {
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
