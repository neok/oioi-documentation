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

Fields
~~~~~~

password-reset
    ``true``, if the reset was a success, ``false`` otherwise (boolean).

Status codes
~~~~~~~~~~~~

200 OK
    The request was processed successfully.
    The password of the user is reset and the user will receive an email with a link.
404 Not Found
    No user with the given username/email found.

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
        "user": {
            "password-reset": true
        }
    }
