.. highlight:: js

.. _calls-userregister-docs:

User Register
=============

Request
-------

.. note:: The field "language" is optional.

Fields
~~~~~~

username
    The desired username of the new user (string).
email
    The email of the new user (string).
password
    The plain password of the new user (string).
language (optional)
    The locale of the new user (string).
    Expected is a lowercase, two-character string in accordance with `ISO 639-1:2002`_.
receive-newsletters (optional)
    Whether or not a user is subscribed to plugsurfing newsletters (boolean).

Response
--------

Fields
~~~~~~

token
    A token to authenticate the user in future requests (string).

    Keep this token.
    When you make future requests where the user needs to be authenticated,
    you supply this token with the request.
evco-id
    The EVCO ID of the user (string).
    See also :ref:`EVCO ID <glossary-evco-id>`

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success
143
    Authentication failed: Email already exists

Examples
--------

Request::

    {
        "user-register": {
            "username": "user",
            "email": "name@mail.com",
            "password": "plain-password",
            "language": "en",
            "receive-newsletters": true
        }
    }

Response::

    {
        "user": {
            "token": "e2af72d7a9084431ab0b1a5c42df7745",
            "evco-id": "DE*8PS*123456*7"
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }

.. _iso 639-1:2002: https://en.wikipedia.org/wiki/ISO_639-1
